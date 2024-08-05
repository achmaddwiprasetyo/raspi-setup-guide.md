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

## Raspbian setup
+ Torrent `raspbian jessie lite` from https://www.raspberrypi.org/downloads/raspbian/
+ Burn the .dmg file on the SD card Using `raspberry pi filler` http://ivanx.com/raspberrypi/
+ Plug the SD card, wifi usb dongle, keyboard and screen, then power up the rpi.

---

## Network / SSH setup

###### WiFi setup
<sup>https://www.raspberrypi.org/documentation/configuration/wireless/wireless-cli.md</sup>
```sh
sudo nano /etc/wpa_supplicant/wpa_supplicant.conf
```

```js
network = {
    ssid="The_ESSID_from_earlier"
    psk="Your_wifi_password"
}
```

```sh
sudo reboot
ifconfig wlan0
```

###### mDNS setup
```sh
sudo apt-get udpate
sudo apt-get install avahi-daemon
```

###### hostname setup
`sudo raspi-config` > _Advanded Options_ > _Hostname_

###### SSH setup
`sudo raspi-config` > _Advanced Options_ / _SSH_

---

## Misc packages
###### GIT setup

```sh
sudo apt-get update
sudo apt-get install git-all
```

###### Node.js setup
<sup>https://nodejs.org/en/download/package-manager/#debian-and-ubuntu-based-linux-distributions</sup>
```sh
wget http://node-arm.herokuapp.com/node_latest_armhf.deb 
sudo dpkg -i node_latest_armhf.deb
node -v
sudo npm install -g n
```

###### PM2
<sup>https://github.com/Unitech/pm2#install-pm2</sup>
```sh
sudo npm install -g pm2
```

###### ZSH / Oh My Zsh setup
<sup>https://github.com/robbyrussell/oh-my-zsh</sup>
```sh
sudo apt-get update
sudo apt-get install zsh
```

```sh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

###### Node-gyp setup
<sup>Used to build some modules like `node-serialport` or `node-canvas`</sup>
```sh
sudo npm install -g node-gyp
```

If any `npm install` fail and throw an error mentionning `node-gyp`, see https://stackoverflow.com/a/21366601

---

## Listing devices
```
ls /dev/tty*
```
An Arduino should look like `/dev/ttyUSB0`
