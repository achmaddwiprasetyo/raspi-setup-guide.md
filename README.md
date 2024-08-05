# Raspberry PI setup guide

## 1. Install using Raspberry PI
You can install :
1. [Install Raspberry PI and run the installer](https://github.com/achmaddwiprasetyo/raspi-install)
2. [Connecting via SSH to the Raspberry Pi](https://github.com/achmaddwiprasetyo/raspi-setup-guide.md/blob/main/README.md#2-connecting-via-ssh)
3. [Install LAMP Server](https://github.com/achmaddwiprasetyo/raspi-setup-guide.md/blob/main/README.md#3-install-lamp-using-raspberry-pi)
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

That’s it! Apache is now installed. To test your installation, change to the /var/www/html directory and list the files:
```bash
pi@raspberrypi:~ $ cd /var/www/html
pi@raspberrypi:/var/www/html $ ls -al
index.html
```
You should have an index.html file in that folder. To open that page in your browser, you need to know the Raspberry Pi IP address. Use:
```bash
pi@raspberrypi:/var/www/html $ hostname -I
```
![apache2](https://i0.wp.com/randomnerdtutorials.com/wp-content/uploads/2019/09/1-Raspberry-Pi-change-directory-RPi-IP-Address.png?w=501&quality=100&strip=all&ssl=1)

In my case, the Raspberry Pi IP address is 192.168.1.86. If you open your RPi IP address in any browser in your local network, a similar web page should load **(http://192.168.1.86)**:
![apache3](https://i0.wp.com/randomnerdtutorials.com/wp-content/uploads/2019/09/2-Raspberry-Pi-Apache2-Installed.png?w=840&quality=100&strip=all&ssl=1)

### 3. Install PHP on Raspberry Pi
PHP is a server side scripting language. PHP (Hypertext Preprocessor) is used to develop dynamic web applications. A PHP file contains <?php … ?> tags and ends with the extension “.php“.

To install PHP on Raspberry Pi, run:
```bash
sudo apt install php -y
```
You can remove the index.html and create a PHP script to test the installation:
```bash
pi@raspberrypi:/var/www/html $ sudo rm index.html
pi@raspberrypi:/var/www/html $ sudo nano index.php
```
In your index.php file add the following code to echo the “hello world” message:
```bash
<?php echo "hello world"; ?>
```
![hw](https://i0.wp.com/randomnerdtutorials.com/wp-content/uploads/2019/09/3-Raspberry-Pi-Create-PHP-Test-File-Hello-World.png?w=597&quality=100&strip=all&ssl=1)</br>
To save your file: press Ctrl+X, followed by y, and press Enter to exit.

Finally, restart Apache2:
```bash
pi@raspberrypi:/var/www/html $ sudo service apache2 restart
```
To test if Apache2 is serving .php files, open the Raspberry Pi IP address and it should display the **“hello world”** message from the index.php script created earlier.</br>
![index](https://i0.wp.com/randomnerdtutorials.com/wp-content/uploads/2019/09/4-Raspberry-Pi-test-PHP-File-Hello-World-message-web-browser.png?w=557&quality=100&strip=all&ssl=1)</br>
If everything is working, you can remove index.php file from the /var/www/html directory:
```bash
pi@raspberrypi:/var/www/html $ sudo rm index.php
```

### 4. Install MySQL (MariaDB Server) on Raspberry Pi
MySQL (often pronounced My S–Q–L) is a popular open source relational database.
Install the MySQL Server (MariaDB Server) and PHP-MySQL packages by entering the following command:
```bash
sudo apt install mariadb-server php-mysql -y
sudo apt install mariadb-server php-mysql -y
```
After installing MySQL (MariaDB Server), it’s recommend to run this command to secure your MySQL installation:
```bash
sudo mysql_secure_installation
```
