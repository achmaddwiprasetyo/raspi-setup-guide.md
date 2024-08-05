# Raspberry PI setup guide

## Install using Imager
You can install Imager in the following ways:
- Download the latest version from [raspberrypi.com/software](https://www.raspberrypi.org/downloads/raspbian/)  and run the installer.
- Download according to the OS system you are using.

Once you’ve installed Imager, launch the application by clicking the Raspberry Pi Imager icon
![lauchApp](https://www.raspberrypi.com/documentation/computers/images/imager/welcome.png?hash=a351c2ba01f30809c2921de09be67683)
Click **Choose device** and select your Raspberry Pi model from the list.
![device](https://www.raspberrypi.com/documentation/computers/images/imager/choose-model.png?hash=0543c40612882f917cfc565caa6dc92f)
Next, click **Choose OS** and select an operating system to install. Imager always shows the recommended version of Raspberry Pi OS for your model at the top of the list.
![os](https://www.raspberrypi.com/documentation/computers/images/imager/choose-os.png?hash=9d49bdaf867704b30f177d47e72dc9b8)
Connect your preferred storage device to your computer. For example, plug a microSD card in using an external or built-in SD card reader. Then, click **Choose storage** and select your storage device.
![storage](https://www.raspberrypi.com/documentation/computers/images/imager/choose-storage.png?hash=05e6671a4cac0b1f3781448688f5d692)
Next, click **Next**.
![next](https://www.raspberrypi.com/documentation/computers/images/imager/os-customisation-prompt.png?hash=4df5658cd09684490db4c1f2352255a3)
In a popup, Imager will ask you to apply OS customisation. We strongly recommend configuring your Raspberry Pi via the OS customisation settings. Click the **Edit Settings** button to open OS customisation.

If you don’t configure your Raspberry Pi via OS customisation settings, Raspberry Pi OS will ask you for the same information at first boot during the configuration wizard. You can click the **No** button to skip OS customisation.

## OS customisation
The OS customisation menu lets you set up your Raspberry Pi before first boot. You can preconfigure:
- a username and password
- Wi-Fi credentials
- the device hostname
- the time zone
- your keyboard layout
- remote connectivity

When you first open the OS customisation menu, you might see a prompt asking for permission to load Wi-Fi credentials from your host computer. If you respond "yes", Imager will prefill Wi-Fi credentials from the network you’re currently connected to. If you respond "no", you can enter Wi-Fi credentials manually.

The **hostname** option defines the hostname your Raspberry Pi broadcasts to the network using mDNS. When you connect your Raspberry Pi to your network, other devices on the network can communicate with your computer using `<hostname>.local` or `<hostname>.lan`.

The **username and password** option defines the username and password of the admin user account on your Raspberry Pi.

The **wireless LAN** option allows you to enter an SSID (name) and password for your wireless network. If your network does not broadcast an SSID publicly, you should enable the "Hidden SSID" setting. By default, Imager uses the country you’re currently in as the "Wireless LAN country". This setting controls the Wi-Fi broadcast frequencies used by your Raspberry Pi. Enter credentials for the wireless LAN option if you plan to run a headless Raspberry Pi.

The **locale settings** option allows you to define the time zone and default keyboard layout for your Pi.
![setting](https://www.raspberrypi.com/documentation/computers/images/imager/os-customisation-general.png?hash=6509321c9eebb02e53dd711c12395571)
The **Services** tab includes settings to help you connect to your Raspberry Pi remotely.

If you plan to use your Raspberry Pi remotely over your network, check the box next to **Enable SSH**. You should enable this option if you plan to run a headless Raspberry Pi.
- Choose the **password authentication** option to SSH into your Raspberry Pi over the network using the username and password you provided in the general tab of OS customisation.
- Choose **Allow public-key authentication** only to preconfigure your Raspberry Pi for passwordless public-key SSH authentication using a private key from the computer you’re currently using. If already have an RSA key in your SSH configuration, Imager uses that public key. If you don’t, you can click **Run SSH-keygen** to generate a public/private key pair. Imager will use the newly-generated public key.

![ssh](https://www.raspberrypi.com/documentation/computers/images/imager/os-customisation-services.png?hash=bbc8c0ff2f1eb7207d43180d7694c399)

OS customisation also includes an **Options** menu that allows you to configure the behaviour of Imager during a write. These options allow you to play a noise when Imager finishes verifying an image, to automatically unmount storage media after verification, and to disable telemetry.

![option](https://www.raspberrypi.com/documentation/computers/images/imager/os-customisation-options.png?hash=eda44365c03e4184f09832f46516a41b)

## Write
When you’ve finished entering OS customisation settings, click **Save** to save your customisation.

Then, click **Yes** to apply OS customisation settings when you write the image to the storage device.

Finally, respond **Yes** to the "Are you sure you want to continue?" popup to begin writing data to the storage device.

![final](https://www.raspberrypi.com/documentation/computers/images/imager/are-you-sure.png?hash=5dce4cfcd6622b97ce741b2c168f0a3d)

If you see an admin prompt asking for permissions to read and write to your storage medium, grant Imager the permissions to proceed.

![process](https://www.raspberrypi.com/documentation/computers/images/imager/writing.png?hash=15fc8293a1c6b12fad0436e4d4aaf506)
*Grab a cup of coffee or go for a walk. This could take a few minutes.*

![load](https://www.raspberrypi.com/documentation/computers/images/imager/stop-ask-verify.png?hash=78a0e9f7a1df18d5df3ebe92b073ed97)
*If you want to live especially dangerously, you can click cancel verify to skip the verification process.*

When you see the "Write Successful" popup, your image has been completely written and verified. You’re now ready to boot a Raspberry Pi from the storage device!
![finish](https://www.raspberrypi.com/documentation/computers/images/imager/finished.png?hash=ba5031e958427e07a6c3a727d3b30021)
Next, proceed to the first boot configuration instructions to get your Raspberry Pi up and running.

[![YouTube](http://i.ytimg.com/vi/CQtliTJ41ZE/hqdefault.jpg)](https://www.youtube.com/watch?v=CQtliTJ41ZE)
