---
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

<img src="/assets/images/post/2019-2-10-simple-way-to-access-google-apigoogle-api-1.PNG">
Go to **“Select a project”** and click the **“New Project”** to create a new project.
