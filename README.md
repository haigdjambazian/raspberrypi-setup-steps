# raspberrypi-setup-steps
Raspberry Pi  - Initial setup and testing
=========================================

Using: Raspberry Pi 2 Model B, MacBook Air (13-inch, Late 2010)

Create NOOBS microSD card
----------------------------

* Get latest NOOBS (Not NOOBS Lite) from: https://www.raspberrypi.org/downloads/noobs/  
I used v1.5.0, archived here: https://downloads.raspberrypi.org/NOOBS/images/NOOBS-2015-11-24/
* Unzip the NOOBS zip file.
* Copy the folder to the microSD card (used an microSD to SD adapter).

First boot
--------------

* Insert the microSD card.
* plug in the Mouse, Keyboard and hdmi.
* Plug in the power with microUSB to start the first boot process.
* A window will appear with a list of different operating systems.
* Choose Raspbian and click install, Raspian will install.
* When the installation is complete click "ok".
* Raspian GUI will start.

Test 1: Using ssh to connect
---------------------------------

* Start a Raspberry Pi terminal
* Run
```
ifconfig
```
* Note the "inet addr" value: 192.168.0.104
* From external computer run 
```
ssh -l pi 192.168.0.104
```
* Enter the Raspberry Py password

Test 2: Setup a web server
------------------------------

following: https://www.raspberrypi.org/documentation/remote-access/web-server/apache.md

* Update Raspberry Pi:
```
# It will install Jessie over v1.5.0
sudo apt-get update 
```
* Install apache:
```
sudo apt-get install apache2 -y
```
* If the installation succeeds you can go to: http://192.168.0.104/ and see the default apache page
* Repace the index.html: 
```
cd /var/www/html/  
sudo mv index.html index.html.apache  
printf "<html>\n<head></head>\n<body>Hello World - Haig</body>\n</html>\n" > /tmp/index.html  
sudo mv /tmp/index.html .  
```
* Visit http://192.168.0.104/

Test 3: use php with the web server
--------------------------------------

* Install php:
```
sudo apt-get install php5 libapache2-mod-php5 -y
```
* Repace the index.html with index.php:
```
cd /var/www/html/
sudo mv index.html index.html.helloworld
printf '<!DOCTYPE html>\n<html>\n<body>\n<?php echo "My first PHP script!"; ?><br>\n<?php echo date("Y-m-d H:i:s"); ?><br>\n<?php phpinfo(); ?>\n</body>\n</html>' > /tmp/index.php
sudo mv /tmp/index.php .
```
* Visit http://192.168.0.104/

Test 4: Try using game emulator
-------------------------------

* download RetroPie 2/3 from: https://retropie.org.uk/download/  
Following steps here to use a Raspberry Pi image: https://www.raspberrypi.org/documentation/installation/installing-images/mac.md
* cd to directory and run:
```
gunzip retropie-v3.8.1-rpi2_rpi3.img.gz 
```
* Insert microSD with adapter
* Go to: Apple Menu > About This Mac > System Report > USB > USB Hi-Speed Bus
* Note the name: BSD Name:	disk2s1 (note disk2, not disk2s1)
* With Disk Utility unmount disk (do not eject)
* Run:
```
sudo dd bs=1m if=retropie-v3.8.1-rpi2_rpi3.img of=/dev/rdisk2
```
* You should see displayed:
```
2670+1 records in
2670+1 records out
2800000000 bytes transferred in 604.781820 secs (4629769 bytes/sec)
```

