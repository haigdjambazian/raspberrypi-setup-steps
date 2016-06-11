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

III. Test 1: Using ssh to connect to the Raspberry Pi another computer

   1. Start a Raspberry Pi terminal
   2. type ifconfig
   3. Note the "inet addr" value: 192.168.0.104
   4. From external computer run ssh -l pi 192.168.0.104
   5. Enter the Raspberry Py password

IV. Test 2: Setup a web server (following: https://www.raspberrypi.org/documentation/remote-access/web-server/apache.md)

   1. Update Raspberry Pi: sudo apt-get update
   2. Install apache: sudo apt-get install apache2 -y
   3. If the installation succeeds you can go to: http://192.168.0.104/ and see the default page



