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

**Note**:

- **How to stop this instance?** Search **VM Instances** in the searching box, then click **stop**. You can click **start** to restart it.
  
  <div class='fig figcenter fighighlight'>
  <img src='/screenshot/stop instances.png'>
  </div>

- **How to reopen Jupyter Notebook in my browser?** You need start the instance first, then search **Deployment Manager** in the searching box. And then click the "**tensorflow-python-cuda-minilab-1**"", you will find out what to do next. 
  <div class='fig figcenter fighighlight'>
  <img src='/screenshot/reopen jupyter.png'>
  </div>
 

## Connect to Your Virtual Instance ##

Now that you have created your virtual GCE, you want to be able to connect to it from your computer. The rest of this tutorial goes over how to do that using the command line. First, download the Google Cloud SDK that is appropriate for your platform from [here](https://cloud.google.com/sdk/docs/ "Title") and follow their installation instructions. **NOTE: this tutorial assumes that you have performed step #4 on the website which they list as optional**. When prompted, make sure you select `us-west1-b` as the time zone. 

The easiest way to connect is using the gcloud compute command below. The tool takes care of authentication for you. On your laptop (OS X for example), run:

```
gcloud compute ssh --zone=us-west1-b <YOUR-INSTANCE-NAME>
```

If `gcloud` command is not in system path, you can also reference it by its full path `/<DIRECTORY-WHERE-GOOGLE-CLOUD-IS-INSTALLED>/bin/gcloud`. See [this page](https://cloud.google.com/compute/docs/instances/connecting-to-instance "Title") for more detailed instructions. 

## First time setup ##

Upon your first ssh, you need to run a one-time setup script and reload the `.bashrc` to activate the libraries. The exact command is

```
/home/shared/setup.sh && source ~/.bashrc
```

The command will download a git repo, patch your `.bashrc` and copy a jupyter notebook config file to your home directory. If you ever switch account/username, you will have to re-run the setup command. If you see any permission error, simply prepend `sudo` to the command. 

When the command finishes without error, run `which python` on the command line and it should report `/home/shared/anaconda3/bin/python`. See screenshot:

<div class='fig figcenter fighighlight'>
  <img src='/assets/cloud-setup-script.png'>
</div>

(don't worry about the Tensorflow warning message)

Our provided image supports the following frameworks:

- [Anaconda3](https://www.anaconda.com/what-is-anaconda/), a python package manager. You can think of it as a better alternative to `pip`. 
- Numpy, matplotlib, and tons of other common scientific computing packages.
- [Tensorflow 1.7](https://www.tensorflow.org/), both CPU and GPU. 
- [PyTorch 0.3](https://www.pytorch.org/), both CPU and GPU. 
- [Keras](https://keras.io/) that works with Tensorflow 1.7
- [Caffe2](https://caffe2.ai/), CPU only. Note that it is very different from the original Caffe. 
- Nvidia runtime: CUDA 9.0 and cuDNN 7.0. They only work when you create a Cloud GPU instance, which we will cover later.  

The `python` on our image is `3.6.4`, and has all the above libraries installed. It should work out of the box for all assignments unless noted otherwise. You don't need `virtualenv`, but if you insist, Anaconda has [its own way](https://conda.io/docs/user-guide/tasks/manage-environments.html). If you need libraries not mentioned above, you can always run `conda install <mylib>` yourself. 

You are now ready to work on the assignments on Google Cloud!


## Using Jupyter Notebook with Google Compute Engine ##
Many of the assignments will involve using Jupyter Notebook. Below, we discuss how to run Jupyter Notebook from your GCE instance and connect to it with your local browser. 

### Getting a Static IP Address ###
Change the Extenal IP address of your GCE instance to be static (see screenshot below). 
<div class='fig figcenter fighighlight'>
  <img src='/assets/cloud-external-ip.png'>
</div>

To Do this, click on the 3 line icon next to the **Google Cloud Platform** button on the top left corner of your screen, go to **VPC network** and **External IP addresses** (see screenshot below).

<div class='fig figcenter fighighlight'>
  <img src='/assets/cloud-networking-external-ip.png'>
</div>

To have a static IP address, change **Type** from **Ephemeral** to **Static**. Enter your prefered name for your static IP, ours is `cs231n-ip` (see screenshot below). And click on Reserve. Remember to release the static IP address when you are done because according to [this page](https://jeffdelaney.me/blog/running-jupyter-notebook-google-cloud-platform/ "Title") Google charges a small fee for unused static IPs. 

<div class='fig figcenter fighighlight'>
  <img src='/assets/cloud-networking-external-ip-naming.png'>
</div>

Take note of your Static IP address (circled on the screenshot below). We use 35.185.240.182 for this tutorial.

<div class='fig figcenter fighighlight'>
  <img src='/assets/cloud-networking-external-ip-address.png'>
</div>

### Adding a Firewall rule ###

One last thing you have to do is adding a new firewall rule allowing TCP acess to a particular port number. The default port we use for Jupyter is **7000**. You can find this default value in the config file generated at setup time (`~/.jupyter/jupyter_notebook_config.py`). Feel free to change it.

Click on the 3-line icon at the top of the page next to **Google Cloud Platform**. On the menu that pops up on the left column, go to **VPC network** and **Firewall rules** (see the screenshot below). 

<div class='fig figcenter fighighlight'>
  <img src='/assets/cloud-networking-firewall-rule.png'>
</div>

Click on the blue **CREATE FIREWALL RULE** button. Enter whatever name you want: we use cs231n-rule. Select "All instances in the network" for **Targets** (if the menu item exists). Enter `0.0.0.0/0` for **Source IP ranges** and `tcp:<port-number>` for **Specified protocols and ports** where `<port-number>` is the number you used above. Click on the blue **Create** button. See the screenshot below.

<div class='fig figcenter fighighlight'>
  <img src='/assets/cloud-networking-firewall-rule-create.png'>
</div>
 

### Launching and connecting to Jupyter Notebook ###

After you ssh into your GCE instance using the prior instructions, run Jupyter notebook from the folder with your assignment files. As a quick example, let's launch it from `/home/shared` folder.

```
cd /home/shared
jupyter-notebook --no-browser --port=7000
```

If you simply run `jupyter-notebook` without any command line arguments, it will pick up the default config values in `~/.jupyter/jupyter_notebook_config.py`. In our disk image, it is `no-browser` and port 7000 by default.

The command should block your stdin and display something like:

<div class='fig figcenter fighighlight'>
  <img src='/assets/cloud-jupyter-console.png'>
</div>

The important line (underscored in red) has the token for you to login from laptop. Replace the "localhost" part with your external IP address created in prior steps. In our example, the URL should be 

```
http://35.185.240.182:7000/?token=aad408a5bcc56f8a7d79db4e144507537e4cf927bd1ab6bc
```

If there is no token, simply go to `http://35.185.240.182:7000`. 

If you visit the above URL on your local browser, you should see something like the screen below. 

<div class='fig figcenter fighighlight'>
  <img src='/assets/cloud-jupyter-screen.png'>
</div>

## Submission: Transferring Files From Your Instance To Your Computer ##

When you are done with your assignments, run the submission script in your assignment folder to make a zip file. Please refer to specific instructions for each assignment.  

Once you create the zip file, e.g. `assignment1.zip`, you will transfer the file from GCE instance to your local laptop. There is an [easy command](https://cloud.google.com/sdk/gcloud/reference/compute/scp) for this purpose:

```
gcloud compute scp <user>@<instance-name>:/path/to/assignment1.zip /local/path
```

For example, to download files from our instance to the current folder:

```
gcloud compute scp tonystark@cs231:/home/shared/assignment1.zip .
```

The transfer works in both directions. To upload a file to GCE:

```
gcloud compute scp /my/local/file tonystark@cs231:/home/shared/
```

Another (perhaps easier) option proposed by a student is to directly download the zip file from Jupyter. After running the submission script and creating assignment1.zip, you can download that file directly from Jupyter. To do this, go to Jupyter Notebook and click on the zip file, which will be downloaded to your local computer. 

## BIG REMINDER: Make sure you stop your instances! ##

Don't forget to stop your instance when you are done (by clicking on the stop button at the top of the page showing your instances). You can restart your instance and the downloaded software will still be available. 

We have seen students who left their instances running for many days and ran out of credits. You will be charged per hour when your instance is running. This includes code development time. We encourage you to read up on Google Cloud, regularly keep track of your credits and not solely rely on our tutorials.
