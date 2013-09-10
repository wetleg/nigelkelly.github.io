---
title: This will be used as the title-tag of the page head
---

<link href="http://kevinburke.bitbucket.org/markdowncss/markdown.css" rel="stylesheet"></link>	
### Background

I wrote about an issue I noted with firebase syncing last week. The article can be found here. I had observed that data created locally by a client will not necessarily make it back to the firebase servers, that there is no mechanism to warn the developer or the user when a connection is lost, firebase continues to operate as if nothing has happened and that if you do a page refresh, whilst a disconnection is in play, that data can be lost. You can download the tests here and run them yourself or you can watch this video I created of myself running the test.

### My test conditions






### Running the test via web servers

I set up a local web server using Google App Engine. I continued to observe that disconnections can occur rather quickly. I then deployed the tests to the cloud at http://testfirebase.appspot.com I continued to add objects to firebase for about 2 hours and no disconnection occurred. Everything worked great. Firebase syncing was now redeemed.
Open two web browser windows and point at them at http://testfirebase.appspot.com You should see things working fine.

### What conclusions can we draw

Communicating to firebase in a development or test environment housed on your local workstation is a bad idea. You should deploy your development and test app to an infrastructure that more closely resembles real world conditions. It is comforting to know that firebase performs under more realistic conditions.

However alot of developers, when they first try out an emerging software library, will want to test off file:// or a local web server. It's just convenient in many cases. Having to deploy to the cloud can be overkill if we just want to dip our toe in the water.

Furthermore there are a whole class of apps that may run locally off the desktop (chrome web store apps, firefox add-ons, etc) or mobile device (phonegap) that will want to talk directly to firebase. The above tests would indicate that this may be problematic for firebase.