---
header:
  teaser: /assets/images/post/2019-2-10-simple-way-to-access-google-api/cover-photo.png
title: "Simple way to access to Google Service API"
categories:
  - learning
tags:
  - google
  - api
  - google drive
  - python
---

<figure>
  <a href="/assets/images/post/2019-2-10-simple-way-to-access-google-api/cover-photo.png"><img src="/assets/images/post/2019-2-10-simple-way-to-access-google-api/cover-photo.png"></a>
  <figcaption></figcaption>
</figure>

Most of us definitely use at least one of the service provided by Google. Since I became a Data Analyst in a internet company, I have worked with more Google service such as Big Query, Google Search Console, Google Analytics etc.

Those Google Services would be more interesting if you can use programming to manage or play around with them. Today we are going to learn how to get authentication for Google Service API through *[client ID](https://developers.google.com/identity/protocols/OAuth2)*.

At the end of this tutorial, you will get a JSON file which contains secret key and client key that enable you to access your Google service. With this JSON file, you can use Python or any programming language to play around with your Google Service.

## Google Cloud Platform
Before starting to use any Google Service API, you need to create a project in [Google Developer Console](https://console.cloud.google.com/), this is where your can manage your Google Service, create API to link with your account and track your service usage.

### 1. Create a new project

<figure>
<img src="{{ site.url }}{{ site.baseurl }}/assets/images/post/2019-2-10-simple-way-to-access-google-api/google-api-1.PNG"  alt="">
</figure>
Go to *“Select a project”* and click the *“New Project”* to create a new project.

<figure>
<img src="{{ site.url }}{{ site.baseurl }}/assets/images/post/2019-2-10-simple-way-to-access-google-api/google-api-2.PNG"  alt="">
</figure>
Give your project a name. It doesn’t matter if you do not have an organisation. You will be redirected to your project dashboard after creating the project.


### 2. Enable Service API

<figure>
<img src="{{ site.url }}{{ site.baseurl }}/assets/images/post/2019-2-10-simple-way-to-access-google-api/google-api-3.PNG"  alt="">
</figure>
Go to the hamburger menu and click the *“Library”* in *“APIs & Services”*.

<figure>
<img src="{{ site.url }}{{ site.baseurl }}/assets/images/post/2019-2-10-simple-way-to-access-google-api/google-api-4.PNG"  alt="">
</figure>
Search for the API you want to activate. At this case, let’s try Google Drive API.

<figure>
<img src="{{ site.url }}{{ site.baseurl }}/assets/images/post/2019-2-10-simple-way-to-access-google-api/google-api-5.PNG"  alt="">
</figure>
Click *“Enable”* to enable the Google Drive API.

<figure>
<img src="{{ site.url }}{{ site.baseurl }}/assets/images/post/2019-2-10-simple-way-to-access-google-api/google-api-6.PNG"  alt="">
</figure>
As you can see, we need to create **credentials** to use the API.


### 3. Create Client ID credential

<figure>
<img src="{{ site.url }}{{ site.baseurl }}/assets/images/post/2019-2-10-simple-way-to-access-google-api/google-api-7.PNG"  alt="">
</figure>
At this case, we will choose the *“client ID”* as we already know what we want to do.

<figure>
<img src="{{ site.url }}{{ site.baseurl }}/assets/images/post/2019-2-10-simple-way-to-access-google-api/google-api-8.PNG"  alt="">
</figure>
Sometime you will get into this page. You will need to configure a consent name before proceeding.

<figure>
<img src="{{ site.url }}{{ site.baseurl }}/assets/images/post/2019-2-10-simple-way-to-access-google-api/google-api-9.PNG"  alt="">
</figure>

**_Hint: Do not use “Google” in your Application name._**

As long as your application name doesn’t contain “Google” or other sensitive word, it will be passed.


### 4. Download the JSON file

<figure>
<img src="{{ site.url }}{{ site.baseurl }}/assets/images/post/2019-2-10-simple-way-to-access-google-api/google-api-10.PNG"  alt="">
</figure>
Select application type based on your use case. Select “other” if you are going to use the credential in your script.

<figure>
<img src="{{ site.url }}{{ site.baseurl }}/assets/images/post/2019-2-10-simple-way-to-access-google-api/google-api-11.PNG"  alt="">
</figure>
Download the JSON file and you are ready to go!


That’s all how you get the JSON file to access your Google Service. I will write another article on how to manage your files on Google Drive by using Python and this JSON file.

Cheers!
