# Setting up Meta Quest with WebXR - Reverse Port Forwarding

When building WebXR applications it can be a frustrating delay constantly needing to push changes to a remote server in order to access it within your headset. With Reverse port forwarding we can host the WebXR server locally on our development machine and access the local server directly with our headset saving a lot of back and forth in the long run!

### What is reverse port forwarding?
Port forwarding is a networking technique in which a device 'forwards' a network port from a device to another device accessing the network. Reverse port forwarding is the same concept but instead our device accessing the network is directing its own port to another device port we specify. In this case we'll be forwarding a port from the Quest (eg. http://localhost:8000) to a port on our computer where our webXR server is hosted. 


### Requirements
- Meta Quest Headset
- Computer with your WebXR project
- Meta Quest Developer Hub 
- USB-C 3.0 Cable 

### What to do
If you are familiar with developing for VR with Unity you should already have completed some of the steps below before.

**Download and install Meta Quest Developer Hub (MQDH)**
When using CTL laptops or PC's in SAG-04 this will already be installed however if you are using your own device head to: 
[Windows](https://developers.meta.com/vr/downloads/package/oculus-developer-hub-win)
[MacOS](https://developers.meta.com/vr/downloads/package/oculus-developer-hub-mac)

**Ensure your headset allows for USB Debugging**
Within the headset navigate to the settings window and look for 'Developer Options' ensure USB debugging is enabled -- This should be enabled by default on CTL headsets however do check!

**Connect your headset**
Open MQDH and with your headset **powered on** connect your headset via the USB-C port on the side of the headset - *you may need to unplug the extended battery to do so* - If prompted accept the connection on your computer. 

Within the headset you will need to accept the connection also and select 'Always allow for this device' when prompted to allow USB debugging with your computer.

**Setup Reverse Port Forwarding**
Within MQDH -- navigate to the device manager tab.
Locate the 'Custom ADB Commands' window and select 'Create a command'
Give your custom command an appropriate name and then enter the following:

<code>adb reverse tcp:8000 tcp:8000</code>

You can change the port number (8000) if you wish however our web server will default to port 8000 unless specified otherwise.

**Launch your WebXR server**
Launch your WebXR server ensuring the port it is hosted on matches that of the port specified in our adb command. In my case this is with python, opening a terminal where my webXR html resides and running

<code>python3 -m http.server 8000</code>

>Side note: You can also run download and run the appropriate script [here]() to launch the server provided this is in the same directory as your WebXR files. These are simple scripts which will run the command shown above. 

**Enjoy your experience**
Within your headset open your web browser (the CTL headsets will need to use Wolvic Browser) and navigate to localhost:8000 and enjoy your webXR experience!








