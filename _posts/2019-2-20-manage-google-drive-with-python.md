---
header:
  image: /assets/images/post/2019-2-20-manage-google-drive-with-python/cover-photo.jpg
  teaser: /assets/images/post/2019-2-20-manage-google-drive-with-python/teaser-photo.jpg
title: "How to manage files in Google Drive with Python"
categories:
  - learning
tags:
  - google API
  - pydrive
  - google drive
  - python
---

As a Data Analyst, most of the time I need to share my extracted data to my product manager/stakeholder and Google Drive is always my first choice. One major issue over here is I have to do it on weekly or even daily basis, which is very boring. All of us hate repetitive tasks, including me.


Fortunately, Google provides API for most of its service. We are going to use [Google Drive API](https://developers.google.com/drive/) and [PyDrive](https://pythonhosted.org/PyDrive/) to manage our files in Google Drive.


## Using Google Drive API

Before going into coding, you should get Google Drive API access ready. I have wrote an [article](https://chingjunetao.github.io//learning/simple-way-to-access-google-api/) on how to get your **Google Service Access through Client ID**. You should be able to get JSON file that contain the secret key to access your Google Drive.


## Getting Started with PyDrive

### Installing PyDrive
We will use the python package manager to install PyDrive

`pip install pydrive`

### Connecting to Google Drive
PyDrive has made the authentication very easy with just 2 lines of code.

```python
from pydrive.auth import GoogleAuth
from pydrive.drive import GoogleDrive

gauth = GoogleAuth()
gauth.LocalWebserverAuth() # client_secrets.json need to be in the same directory as the script
drive = GoogleDrive(gauth)
```

> You have to **rename** the JSON file to **“client_secrets.json”** and place it in the same directory with your script.

`gauth.LocalWebserverAuth()` will fire up the browser and ask for your authentication. Choose the google account you want o access and authorize the app.

`drive = GoogleDrive(gauth)` create a Google Drive object to handle file. You will be using this object to list and create file.


### Listing and uploading file in Google Drive

```python
# View all folders and file in your Google Drive
fileList = drive.ListFile({'q': "'root' in parents and trashed=false"}).GetList()
for file in fileList:
  print('Title: %s, ID: %s' % (file['title'], file['id']))
  # Get the folder ID that you want
  if(file['title'] == "To Share"):
      fileID = file['id']

file1 = drive.CreateFile({"mimeType": "text/csv", "parents": [{"kind": "drive#fileLink", "id": fileID}]})
file1.SetContentFile("small_file.csv")
file1.Upload() # Upload the file.
print('Created file %s with mimeType %s' % (file1['title'], file1['mimeType']))   
```

Line 1 to line 4 will get you the list of files/folders in your Google Drive. It will also give you the detail of those files/folders. We capture the **file ID** of the folder you would like to upload files to. In this case, `To Share` is the folder I would upload the files to.

> **File ID** is important as Google Drive uses file ID to specific the location instead of using file path.

`drive.CreateFile()` accepts **metadata**(dict.) as input to initialize a GoogleDriveFile. I initialized a file with `"mimeType" : "text/csv"` and `"id" : fileID`. This `id` will specific where the file will be uploaded to. In this case, the file will be uploaded to the folder `To Share`.

`file1.SetContentFile("small_file.csv")` will open the specified file name and set the content of the file to the GoogleDriveFile object. At this moment, the file is still not uploaded. You will need `file1.Upload()` to complete the upload process.


### Accessing files in folders

```python
fileList = drive.ListFile({'q': "'2mavWSQhVfr7GnX2JHa45Qd43bTaYCHXE' in parents and trashed=false"}).GetList()
for file in fileList:
  print('Title: %s, ID: %s' % (file['title'], file['id']))
   # Get the folder ID that you want
  if(file['title'] == "picture"):
      fileID = file['id']

# Initialize GoogleDriveFile instance with file id.
file2 = drive.CreateFile({'id': fileID})
file2.Trash()  # Move file to trash.
file2.UnTrash()  # Move file out of trash.
file2.Delete()  # Permanently delete the file.
```

How if you would like to upload files into folder inside a folder? Yes, again you would need the **File ID**! You can use the `ListFile` to get the files but this time change the `root` to `file ID`.

```python
file_list = drive.ListFile({'q': "'<folder ID>' in parents and trashed=false"}).GetList()
```

Now we can get into folder `picture` inside the folder `To Share`.

Other than uploading files to Google Drive, we can delete them too. First, create a GoogleDriveFile with the specified file ID. Use `Trash()` to move file to trash. You can also use `Delete()` to delete the file permanently.

Now you have learnt how to manage your Google Drive files with Python. I hope this article is useful to you. Do drop me a comment if I made any mistake or typo.

You can view the complete script in my [Github](https://github.com/chingjunetao/google-service-with-python/tree/master/google-drive-with-python).

Cheers!
