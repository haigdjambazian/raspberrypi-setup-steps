# raspberrypi-setup-steps
Raspberry Pi  - Initial setup and testing
=========================================

Using: Raspberry Pi 2 Model B

I. Create NOOBS microSD card
----------------------------

   1. Get latest NOOBS (Not NOOBS Lite) from: https://www.raspberrypi.org/downloads/noobs/
      I used v1.5.0, archived here: https://downloads.raspberrypi.org/NOOBS/images/NOOBS-2015-11-24/
   2. Unzip the NOOBS zip file
   3. Copy the folder to the microSD card (used an microSD to SD adapter).
   
II. First boot
--------------

   1. Insert the microSD card.
   2. plug in the Mouse, Keyboard and hdmi.
   3. Plug in the power with microUSB to start the first boot process.
   4. A window will appear with a list of different operating systems.
   5. Choose Raspbian and click install, Raspian will install.
   6. When the installation is complete click "ok".
   7. Raspian GUI will start.
   
III. Test 1: Using ssh to connect
---------------------------------

   1. Start a Raspberry Pi terminal
   2. Run
      ```
      ifconfig
      ```
   3. Note the "inet addr" value: 192.168.0.104
   4. From external computer run 
      ```
      ssh -l pi 192.168.0.104
      ```
   5. Enter the Raspberry Py password

IV. Test 2: Setup a web server
------------------------------

following: https://www.raspberrypi.org/documentation/remote-access/web-server/apache.md

   1. Update Raspberry Pi:
      ```
      # It will install Jessie over v1.5.0
      sudo apt-get update 
      ```
   2. Install apache:
      ```
      sudo apt-get install apache2 -y
      ```
   3. If the installation succeeds you can go to: http://192.168.0.104/ and see the default apache page
   4. Repace the index.html: 
      ```
      cd /var/www/html/
      sudo mv index.html index.html.apache
      printf "<html>\n<head></head>\n<body>Hello World - Haig</body>\n</html>\n" > /tmp/index.html
      sudo mv /tmp/index.html .
      ```
   5. Visit http://192.168.0.104/

V. Test 3: use php with the webserver
-------------------------------------

   1. Install php:
      ```
      sudo apt-get install php5 libapache2-mod-php5 -y
      ```
   2. Repace the index.html with index.php:
      ```
      cd /var/www/html/
      sudo mv index.html index.html.helloworld
      printf '<!DOCTYPE html>\n<html>\n<body>\n<?php echo "My first PHP script!"; ?><br>\n<?php echo date("Y-m-d H:i:s"); ?><br>\n<?php phpinfo(); ?>\n</body>\n</html>' > /tmp/index.php
      sudo mv /tmp/index.php .
      ```
   3. Visit http://192.168.0.104/

