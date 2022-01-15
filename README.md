## A Balena version of a Flux Web3 Decentralized Node

This repo installs all of the necessary bits to deploy a Flux Node, containerized and ready to be deployed with balena.  This helps automate the install process and allows you to manage and update your Flux Nodes with ease.

## Short Version of Instructions

Using an Intel x86-64 device locally is easy, just click this button:

[![balena deploy button](https://www.balena.io/deploy.svg)](https://dashboard.balena-cloud.com/deploy?repoUrl=https://github.com/dtischler/balena-flux)

Go through the balena login, Fleet creation, Device creation, OS download, and flash to your NUC or similar device.  The container will download, then just needs some Device Variables set.  See below for those.  Reminder:  Flux Nodes can take 24-48 hours to sync the first time.

## Longer, More Detailed Instructions

More specifically:

1.  Click on the Blue Button just above.
2.  Log in to balenaCloud, or create an account if you do not already have one. (It is free :-) )
3.  Create a name for the application in the pop-up modal, and choose the Intel NUC from the drop down list.
4.  Click Create and deploy.
5.  Click Add Device.
6.  You will come to the Summary page. Here, click "Add Device".
7.  Be sure to leave the OS variant set to Production, you do NOT want the Development variant of the operating system, (which is left wide open for testing purposes) sitting on the internet.
8.  At the bottom of the modal, click to arrow next to flash wtih Etcher to "Download balenaOS".
9.  After download completes, flash the file to a USB stick with Etcher.
10. Hook up a monitor, keyboard, and mouse to your device. (Unnecessary on a laptop, of course)

[WARNING: WE ARE GOING TO OVERWRITE YOUR DEVICE. BACKUP ANY DATA YOU NEED FIRST]

11. Insert the USB stick into your device, power on, and if necessary choose to boot from USB. The PC will boot up, copy the contents of the USB drive to the device's internal storage, then power off.
12. Remove the USB stick, and power the device back on. Wait a few minutes for it to register itself with balenaCloud and come online.
13. After another moment, the PC or laptop will begin downloading the pre-built Flux container, which will take a long time. Get a cup of tea while this occurs.  Or got to sleep.

Once this is done, the Node is nearly ready, but we have to add some Device Variables to tell it who you are, what your Collateral and Private Key are, inform it of your Hostname and IP Address, etc.

## Device Variables

Here are a list of the Variables that need to be entered:

```
HOSTNAME
EXTERNAL_IP
ZEL_ID
ZELNODE_PRIV_KEY
ZELNODE_OUT_POINT
ZELNODE_INDEX
RPCUSER
RPCPASSWORD
```

Adding these is easy.  In balenaCloud, click on Fleets.  Then, click on the name of your fleet.  Next, click on the name of your device.  Mine is "dreary-thunder" in this example:

![](/img/img1.png)

Make a note of your device's UUID and public IP Address.  We'll need those in a moment.  

![](/img/img2.png)

Now on the left, click on Device Variables.  Click on the blue "Add variable" button.  One by one, enter the variable and it's value from the list of variables needed.  At the end it should like this (your values will differ of course):

![](/img/img3.png)

The last step, is to wait for the blockchain to be processed by MongoDB.  This can take up to 48 hours, so no need to sit and stare at it while it builds the index.  

That's it.  :-)






