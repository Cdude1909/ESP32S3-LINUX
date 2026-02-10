# ESP32S3-LINUX

Finally , after researching and experimenting my **ESP32S3 MCU**, i was finally able to achieve Buildroot based linux installation on my MCU. 
🚀 **[16 MB FLASH , 8 MB FLASH]**
## Steps

As described by @jcmvkbc ,

1) Make sure following packages are pre-installed : 
 
`sudo apt install autoconf automake bash bc bison build-essential cmake flex gawk git gperf help2man libncurses-dev libtool libtool-bin libusb-1.0-0 python3 python3-venv rsync texinfo unzip wget`


2) Finally run the script provided and everything will be automatic. Go for a coffee / Tea , its will be hour or two 🍵⬇️


 `./rebuild-esp32s3-linux-wifi.sh`
 

 **During Flashing stage , make sure MCU is connected and the press ENTER (ask multiple times for Partitions).it will end with 0x0b meaning SUCCESS!**


3) after running once , the work isn't over , re run it with following arguments:


```
echo "earlycon=esp32s3acm,mmio32,0x60038000 console=ttyGS3 debug rw root=mtd:rootfs no_hash_pointers" > ./build/build-buildroot-esp32s3_box3/target/etc/cmdline`

now run it with again with this :

sudo keep_toolchain=y keep_buildroot=y keep_rootfs=y keep_bootloader=y nice ./rebuild-esp32s3-linux-wifi.sh
```


4) VOILA! you can check your linux-MCU via any serial communicator like MINICOM / Putty.
   ``sudo minicom -D /dev/ttyACM0``
   
## ⚠️ NOTE: 

1) This installation and whole process can take aprrox. 2 hours depending upon your hardware. Make sure to note the PORT number of MCU Connected , generally `/dev/ttyACM0` or  `/dev/ttyS0` .
   you can check that by simply running the command , `ls /dev/tty*`
  

2) If Re-installing or re-running the script is needed , **DO NOT USE THE SCRIPT DIRECTLY OR ELSE REBUILD PROCESS WILL BE DONE WHICH WILL WASTE 2 hours of time again!**  Make sure this arguments are used :
   
`sudo keep_toolchain=y keep_buildroot=y keep_rootfs=y keep_bootloader=y nice ./rebuild-esp32s3-linux-wifi.sh`


