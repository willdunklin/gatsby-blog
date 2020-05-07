---
title: Starting a Google Clound Instance
date: "2020-04-05T22:12:03.284Z"
description: Information on Google Cloud's free trial system and turorial for creating a Google Cloud Instance 
---

The Google Cloud Platform has lots of untapped potential as a host of novice webpages and personal projects.

This is in part because of their incredibly lenient free trial system that gives users $300 of free credit and a year to use it with no strings attached.

---

###The process for singing up for the free trial is simple.

1. Sign in to Google

Go to [Google Cloud Console](https://console.cloud.google.com) and sign in with your google account.


2. Activate the Free Trial

At the top of the page there should be a banner that tells you to activate you trial. Follow the steps and billing information.

*Note: Google will __not__ automatically renew any payments or charge your card.*

3. Create a Project

Creating a project allows you to categorize different VM's and maintain organization. For now make a project with the name of your choosing by going to the top nav bar, clicking on the project list, and clicking `New Project`.

4. Creating a VM Instance

In the Hamburger menu in the top left navigate to `Compute Engine > VM Instances`.

Here, select `Create Instance`.

Next you can customize the instance name, hardware, operating system, network rules, etc. For now if you intend on making a simple website, leave the CPU/Memory at its default. However if your needs vary you may want to customize these parameters.

Change The operating system to be your preferred choice, I generally choose an LTS version of Ubuntu such as 18.04.

Next Check the boxes to allow HTTP and HTTPS traffic.

Then, expand the more options sections and go to the `Networking` tab. Click on the network interfaces section. Under `External IP` select `Create IP address` and enter a name of your choice.

Finally click `Create`.

5. SSH Into the Instance

To SSH into your GCP instance click the SSH button. This should open a new window with an SSH terminal where you can develop and deploy a site.