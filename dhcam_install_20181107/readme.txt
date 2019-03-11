System Requirements
===================
GigE Vision Camera:

Linux 32bit:
   1)kernel version: 3.16.0-30-generic        default kernel by Ubuntu-14.04.2 
   2)kernel version: 4.2.0-27-generic         default kernel by Ubuntu-14.04.4
Linux 64bit: 
   1)kernel version: 3.13.0-117-generic       
   2)kernel version: 3.19.0-25-generic        default kernel by Ubuntu-14.04.3
   3)kernel version: 4.2.0-27-generic         default kernel by Ubuntu-14.04.4
   4)kernel version: 4.8.0-36-generic         default kernel by Ubuntu-16.04.2
   5)kernel version: 4.13.0-32-generic        

USB3.0 Vision Camera:
   For best performance and stability we highly recommend a kernel version >= 3.5.0.23

Installation
====================

1. Installation shell command: sudo ./dhmercam_install.bin .

2. After Installation, a work directory will be created under folder 'usr/local'.

3. After Installation, these environment path, contains GENICAM_ROOT_V2_3, LD_LIBRARY_PATH, GENICAM_GENTLxx_PATH,
   GENICAM_CACHE_V2_3, will be created.

4. After Installation, The driver for GigE Vision Camera will be loaded automatically, so you can open GigE Vision camera successfully. But you maybe can't open GigE Vision camera successfully after restart your System, you must open the 'driver' folder and load the driver manually.

5. Your installation is successful When you see these notes:
   "SDK install successs!"
   "Please restart the current terminal..."
   Then restart terminal and use it.

6. If you rename your installation folder, you must reinstall it.

7.When using USB3.0 Vision Camera,If you need grab image from 4 or more U3V cameras, or you need increasing the package(URB) size or count, you will likely run out of kernel space and see corresponding error messages on the console. Because of the default value of USB Kernel Space set by the kernel is 16 MB. To set the value (in this example to 1000 MB) you can
  execute as root:
      echo 1000 > /sys/module/usbcore/parameters/usbfs_memory_mb
  or execute ./SetUSBStack.sh as root.
  This would assign a maximum of 1000 MB to the USB stack.

8.Performance Optimization
To increase performance and to minimize CPU usage when grabbing images, the following settings should be considered:

1)GigE Vision Camera
    First, Enable Jumbo Frames. Many GigE network adapters support so-called jumbo frames, i.e., network packets larger than the usual 1500 bytes. To enable jumbo frames, the maximum transfer unit (MTU) size of the PC's network adapter must be set to a high value. We recommend using a value of 8192.
    Then Increase the packet size.When jumbo frames are enabled, the camera's packet size must be increased to benefit from the larger packets.

2)USB3.0 vision Camera
 Increasing Packet Size
 For faster USB transfers you should increase the packet size. You can do this by changing the "Stream" -> "Settings" -> "StreamTransferSize" value from inside GalaxyViewer or by setting the corresponding value via the API.


Notes:
    1. After your installation, the environment paths that created automatically will be available until you restart current terminal. 
    2. Don't install the SDK in a folder which path has chinese characters, or SDK will not work. 


