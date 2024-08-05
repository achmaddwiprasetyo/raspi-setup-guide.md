# Raspberry PI setup guide

## 1. Install using Raspberry PI
You can install :
1. [Install Raspberry PI and run the installer](https://github.com/achmaddwiprasetyo/raspi-install)
2. [Connecting via SSH to the Raspberry Pi](https://github.com/achmaddwiprasetyo/raspi-setup-guide.md/blob/main/README.md#2-connecting-via-ssh)
3. Install LAMP Server
4. Install Node-Red
5. Install MQTT


## 2. Connecting via SSH
1. Open CMD
2. Enter the connection command. This is SSH + your username @ the IP address or host name. (SSH <username>@<IP or Host Name>)
   
![ssh](https://jarrodstech.net/wp-content/uploads/2020/04/login.png)
3. Enter your password and you will be connected, easy as that. No additional software needed. You can now enter any commands, as if you are sitting at your PI.

![ssh](https://jarrodstech.net/wp-content/uploads/2020/04/loggedin.png)


## 3. Install LAMP using Raspberry PI
### 1. Updating and Upgrading
Before starting the installation procedure, open a Terminal window and run the following commands to update your Pi:
```bash
sudo apt update && sudo apt upgrade -y
```
### 2. Install Apache2 on Raspberry Pi
To install Apache2 on your Raspberry Pi, run the next command:
```bash
sudo apt install apache2 -y
```
![apache](https://i0.wp.com/randomnerdtutorials.com/wp-content/uploads/2019/09/0-Raspberry-Pi-Install-Apache2.png?w=749&quality=100&strip=all&ssl=1)
