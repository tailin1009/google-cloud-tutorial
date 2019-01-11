---
layout: page
title: Google Cloud Tutorial
permalink: /gce-tutorial/

---

# Google Cloud Tutorial

## BEFORE WE BEGIN ## 
### BIG REMINDER: Make sure you stop your instances! ###
(We know you won't read until the very bottom once your assignment is running, so we are printing this at the top too since it is ***super important***)

Don't forget to ***stop your instance*** when you are done (by clicking on the stop button at the top of the page showing your instances), otherwise you will ***run out of credits*** and that will be very sad. :( 

If you follow our instructions below correctly, you should be able to restart your instance and the downloaded software will still be available.

## Create and Configure Your Account ##

Google Cloud Compute Engine is an option for developing and testing your implementations. This tutorial lists the necessary steps of working on machine learning tasks using Google Cloud. **I expect this tutorial to take about 10 minutes.**

This tutorial goes through how to set up a basic Google Compute Engine (GCE) instance to work on common machine learning tasks. When you sign up for the first time, you will receive $300(230 pounds) credits from Google by default. Please try to use the resources judiciously.

First, if you don't have a Google Cloud account already, create one by going to the [Google Cloud homepage](https://cloud.google.com/). When you get to the next page, click on the blue **TRY GCP FREE** button. If you are not logged into gmail, you will see a page that looks like the one below. Sign into your gmail account or create a new one if you do not already have an account. 

<div class='fig figcenter fighighlight'>
  <img src='/screenshot/step1.png'>
</div>

Select the option **United Kingdom** and click blue **Agree and continue** button to continue to the next page to enter the requested information (your name, billing address and credit card information). Remember to select "**Individual**" as "Account Type":

<div class='fig figcenter fighighlight'>
    <img src='/screenshot/step2.png'>
</div>

Once you have entered the required information, press the blue **Start my free trial** button. You will be greeted by a page like this: 

<div class='fig figcenter fighighlight'>
    <img src='/screenshot/GCP DASHABOARD.png'>
</div>

To change the name of your project, click on [**Go to project settings**](console.cloud.google.com/iam-admin/settings/project) under the **Project info** section.

## Launch a Virtual Instance ##

To launch a virtual instance, go to the **Compute Engine** menu on the left column of your dashboard and click on **VM instances**. 
<div class='fig figcenter fighighlight'>
  <img src='/screenshot/vm instance.png'>
  <img src='/screenshot/create.png'> 
</div>

Then click on the blue **Create** button on the next page. This will take you to a page that looks like the screenshot below.

<div class='fig figcenter fighighlight'>
  <img src='/screenshot/marketplace.png'>
</div>

Click the **Marketplace**, do as the bellow screenshot shows:


<div class='fig figcenter fighighlight'>
  <img src='/screenshot/AISE.png'>
</div>

Then click the blue **LAUNCH ON COMPUTE ENGINE** button, this will take you to a page looks like the screenshot below.**(NOTE: Please carefully read the instructions in addition to looking at the screenshots. The instructions tell you exactly what values to fill in).** 

<div class='fig figcenter fighighlight'>
  <img src='/screenshot/deploy.png'>
</div>

Because this is a GPU version instance, make sure that the **Zone** have avaliable GPU instances!!!**.

Click on the blue **Deploy** button at the bottom of the page. You should have now successfully created a Google Compute Instance, it might take a few minutes to start running. When the instance is ready, your screen should look something like the one below.

<div class='fig figcenter fighighlight'>
  <img src='/screenshot/ssh-jupyternotebook.png'>
</div>

You can use Jupyter Notebook by clicking blue **Open Jupyter Notebook** button and  type the **Jupyter Notebook password**.

**Common Questions**:

- **How to stop this instance?** Search **VM Instances** in the searching box, then click **stop**. You can click **start** to restart it.
  
  <div class='fig figcenter fighighlight'>
  <img src='/screenshot/stop instances.png'>
  </div>

- **How to reopen Jupyter Notebook in my browser?** You need start the instance first, then search **Deployment Manager** in the searching box. And then click the "**tensorflow-python-cuda-minilab-1**"", you will find out what to do next. 
  <div class='fig figcenter fighighlight'>
  <img src='/screenshot/reopen jupyter.png'>
  </div>
 
- **How to transfer files between local computer and vm instance?**

  The transfer works in both directions through Jupyter Notebook.
  <div class='fig figcenter fighighlight'>
  <img src='/screenshot/transfer files.png'>
  </div>
 
## BIG REMINDER: Make sure you stop your instances! ##

Don't forget to stop your instance when you are done (by clicking on the stop button at the top of the page showing your instances). You can restart your instance and the downloaded software will still be available. 

We have seen students who left their instances running for many days and ran out of credits. You will be charged per hour when your instance is running. This includes code development time. We encourage you to read up on Google Cloud, regularly keep track of your credits and not solely rely on our tutorials.
