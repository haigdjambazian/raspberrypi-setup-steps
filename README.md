# raspberrypi-setup-steps
Raspberry Pi  - Initial setup and testing

Raspberry Pi 2 Model B

I. Create NOOBS microSD card

   1. Get latest NOOBS (Not NOOBS Lite) from: https://www.raspberrypi.org/downloads/noobs/, I used v1.5.0, archived here: https://downloads.raspberrypi.org/NOOBS/images/NOOBS-2015-11-24/
   2. Unzip the NOOBS zip file
   3. Copy the folder to the microSD card (used an microSD to SD adapter).
   
II. First boot

   1. Insert the microSD card.
   2. plug in the Mouse, Keyboard and hdmi.
   3. Plug in the power with microUSB to start the first boot process.
   4. A window will appear with a list of different operating systems.
   5. Choose Raspbian and click install, Raspian will install.
   6. When the installation is complete click "ok".
   7. Raspian GUI will start.

III. Test 1: Using ssh to connect to the Raspberry Pi from outside

   1. Start a Raspberry Pi terminal
   2. type ifconfig
   3. Note the "inet addr" value
   4. From external computer run ssh -l pi x.x.x.x and enter the Raspberry Py password

IV. Test 2:


