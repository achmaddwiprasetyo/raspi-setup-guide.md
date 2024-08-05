# Raspberry PI setup guide

## 1. Install using Raspberry PI
You can install :
1. [Install Raspberry PI and run the installer](https://github.com/achmaddwiprasetyo/raspi-install)
2. [Connecting via SSH to the Raspberry Pi](https://github.com/achmaddwiprasetyo/raspi-setup-guide.md/blob/main/README.md#2-connecting-via-ssh)
3. [Install LAMP Server using Raspberry PI](https://github.com/achmaddwiprasetyo/raspi-setup-guide.md/blob/main/README.md#3-install-lamp-using-raspberry-pi)
4. [Install Node-Red using Raspberry PI](https://github.com/achmaddwiprasetyo/raspi-setup-guide.md/blob/main/README.md#4-instal-node-red)
5. [Install MQTT using Raspberry PI](https://github.com/achmaddwiprasetyo/raspi-setup-guide.md/blob/main/README.md#5-install-mqtt-using-raspberry-pi)



## 2. Connecting via SSH
1. Open CMD
2. Enter the connection command. This is SSH + your username @ the IP address or host name. (SSH <username>@<IP or Host Name>)</br>
   ![ssh](https://jarrodstech.net/wp-content/uploads/2020/04/login.png)</br>
3. Enter your password and you will be connected, easy as that. No additional software needed. You can now enter any commands, as if you are sitting at your PI.</br>
   ![ssh](https://jarrodstech.net/wp-content/uploads/2020/04/loggedin.png)



## 3. Install LAMP Server using Raspberry PI
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
sudo rm index.html
sudo nano index.php
```
In your index.php file add the following code to echo the “hello world” message:
```bash
<?php echo "hello world"; ?>
```
![hw](https://i0.wp.com/randomnerdtutorials.com/wp-content/uploads/2019/09/3-Raspberry-Pi-Create-PHP-Test-File-Hello-World.png?w=597&quality=100&strip=all&ssl=1)</br>
To save your file: press Ctrl+X, followed by y, and press Enter to exit.

Finally, restart Apache2:
```bash
sudo service apache2 restart
```
To test if Apache2 is serving .php files, open the Raspberry Pi IP address and it should display the **“hello world”** message from the index.php script created earlier.</br>
![index](https://i0.wp.com/randomnerdtutorials.com/wp-content/uploads/2019/09/4-Raspberry-Pi-test-PHP-File-Hello-World-message-web-browser.png?w=557&quality=100&strip=all&ssl=1)</br>
If everything is working, you can remove index.php file from the /var/www/html directory:
```bash
sudo rm index.php
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
This should appear in your Terminal window:
![mysql](https://i0.wp.com/randomnerdtutorials.com/wp-content/uploads/2019/09/5-Raspberry-Pi-MySQL-MariaDB-Install-Secure-Installation.png?w=773&quality=100&strip=all&ssl=1)</br>
- You will be asked Enter **current password for root** (type a secure password): press Enter
- Type in **Y** and press **Enter** to Set root password
- Type in a password at the New password: prompt, and press Enter. Important: remember this root password, as you will need it later
- Type in **Y** to Remove anonymous users
- Type in **Y** to Disallow root login remotely
- Type in **Y** to Remove test database and access to it
- Type in **Y** to Reload privilege tables now
When the installation is completed, you’ll see the message: “Thanks for using MariaDB!”.
![mdb](https://i0.wp.com/randomnerdtutorials.com/wp-content/uploads/2019/09/6-Raspberry-Pi-MySQL-Database-MariaDB-Final-Secure-Installation.png?w=773&quality=100&strip=all&ssl=1)</br>
If you experience any error login into phpMyAdmin, you might need to create a new user to login. Those commands will create a new user with name (admin) and password (your_password).
```bash
pi@raspberrypi:/var/www/html $ sudo mysql --user=root --password
> create user admin@localhost identified by 'your_password';
> grant all privileges on *.* to admin@localhost;
> FLUSH PRIVILEGES;
> exit;
```

### 5. Install phpMyAdmin on Raspberry Pi
phpMyAdmin is a free software tool written in PHP, intended to handle the administration of MySQL using a web interface.

To install phpMyAdmin on a Raspberry Pi, type the following command into the terminal:
```bash
sudo apt install phpmyadmin -y
```
PHPMyAdmin installation program will ask you few questions. We’ll use the **dbconfig-common**.
- Select **Apache2** when prompted and press the **Enter*** key
- Configuring **phpmyadmin**? **OK**
- Configure database for phpmyadmin with **dbconfig-common**? **Yes**
- Type your **password** and press **OK**
![php](https://i0.wp.com/randomnerdtutorials.com/wp-content/uploads/2019/09/7-Raspberry-Pi-install-phpMyAdmin.png?w=773&quality=100&strip=all&ssl=1)</br>
Enable the PHP MySQLi extension and restart Apache2 for changes to take effect:
```bash
sudo phpenmod mysqli
sudo service apache2 restart
```
When you go to your RPi IP address followed by **/phpmyadmin** (in my case ``http://192.168.1.86/phpmyadmin``), you’ll probably see the “Not Found” error page in your browser:</br>
![php2](https://i0.wp.com/randomnerdtutorials.com/wp-content/uploads/2019/09/9-Failed-to-open-phpMyAdmin-Raspberry-Pi.png?w=927&quality=100&strip=all&ssl=1)</br>
If that’s the case, you’ll have to move the *phpmyadmin* folder to ``/var/www/html``, run the next command:
```bash
sudo ln -s /usr/share/phpmyadmin /var/www/html/phpmyadmin
```
Now, if you list the files, it should return the **phpmyadmin** folder:
```bash
ls
phpmyadmin
```
![php3](https://i0.wp.com/randomnerdtutorials.com/wp-content/uploads/2019/09/8-Raspberry-Pi-move-phpMyAdmin.png?w=773&quality=100&strip=all&ssl=1)</br>
Reload your web page (http://192.168.1.86/phpmyadmin), your should see the login page for phpMyAdmin web interface:</br>
![php4](https://i0.wp.com/randomnerdtutorials.com/wp-content/uploads/2019/09/10-Raspberry-Pi-Open-phpMyAdmin-Login-Page.png?w=753&quality=100&strip=all&ssl=1)</br>
Enter your defined username (it should be **Username = root**) and the password you defined during the installation.

Press the **Go** button to login. A new page loads:</br>
![php4](https://i0.wp.com/randomnerdtutorials.com/wp-content/uploads/2019/09/11-Raspberry-Pi-Open-phpMyAdmin-Logged-in-Page.png?resize=1024%2C615&quality=100&strip=all&ssl=1)</br>
That’s it! Your Raspberry Pi board is prepared with a LAMP server: Apache2, MySQL, PHP. We’ve also decided to include phpMyAdmin in this installation for an easier database management through a web interface.

### 6. Optional Step (but recommended)
To manage your web pages, you should change the permissions for your ``/var/www/html/`` folder. To do this, run the following commands:
```bash
pi@raspberrypi:~ $ ls -lh /var/www/
pi@raspberrypi:~ $ sudo chown -R pi:www-data /var/www/html/
pi@raspberrypi:~ $ sudo chmod -R 770 /var/www/html/
pi@raspberrypi:~ $ ls -lh /var/www/
```
After running these commands, you’ll see something as follows:</br>
![ops](https://i0.wp.com/randomnerdtutorials.com/wp-content/uploads/2019/09/12-Raspberry-Pi-change-var-www-html-folder.png?w=773&quality=100&strip=all&ssl=1)</br>



## 4. Instal Node-Red using Raspberry PI
###Installing and Upgrading Node-RED
We provide a script to install Node.js, npm and Node-RED onto a Raspberry Pi. The script can also be used to upgrade an existing install when a new release is available.

Running the following command will download and run the script. If you want to review the contents of the script first, you can view it on Github.
```bash
bash <(curl -sL https://raw.githubusercontent.com/node-red/linux-installers/master/deb/update-nodejs-and-nodered)
```

### Running locally
As with running Node-RED locally, you can use the node-red command to run Node-RED in a terminal. It can then be stopped by pressing Ctrl-C or by closing the terminal window.

Due to the limited memory of the Raspberry Pi, you will need to start Node-RED with an additional argument to tell the underlying Node.js process to free up unused memory sooner than it would otherwise.

To do this, you should use the alternative ``node-red-pi`` command and pass in the ``max-old-space-size`` argument.
```bash
node-red-pi --max-old-space-size=256
```

### Running as a service
The install script for the Pi also sets it up to run as a service. This means it can run in the background and be enabled to automatically start on boot.

The following commands are provided to work with the service:
- ``node-red-start`` - this starts the Node-RED service and displays its log output. Pressing Ctrl-C or closing the window does not stop the service; it keeps running in the background
- ``node-red-stop`` - this stops the Node-RED service
- ``node-red-restart`` - this stops and restarts the Node-RED service
- ``node-red-log`` - this displays the log output of the service
You can also start the Node-RED service on the Raspberry Pi OS Desktop by selecting the Menu -> Programming -> Node-RED menu option.

### Autostart on boot
If you want Node-RED to run when the Pi is turned on, or re-booted, you can enable the service to autostart by running the command:
```bash
sudo systemctl enable nodered.service
```
To disable the service, run the command:
```bash
sudo systemctl disable nodered.service
```

### Opening the editor
Once Node-RED is running you can access the editor in a browser.

If you are using the browser on the Pi desktop, you can open the address: **http://localhost:1880**.

When browsing from another machine you should use the hostname or IP-address of the Pi: ``http://<hostname>:1880``. You can find the IP address by running ``hostname -I`` on the Pi.



## 5. Install MQTT using Raspberry PI
