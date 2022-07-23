# LAMP STACK IMPLEMENTATION

## * STEP 1 — INSTALLING APACHE AND UPDATING THE FIREWALL

sudo apt update (update a list of packages in package manager)
sudo apt install apache2 ( to run apache2 package installation)
sudo systemctl status apache2 (To verify status of apache2)

curl http://localhost:80 (to access our shell on Ubuntu)

http://3.83.99.105:80 (to run on a browser)
![Screenshot from 2022-07-23 13-56-25](https://user-images.githubusercontent.com/106885875/180605901-ab983533-88dc-4b57-a498-03c946c8809e.png)

## * STEP 2- TO INSTALL MYSQL Server

sudo apt install mysql-server
$ sudo mysql

![Screenshot from 2022-07-23 14-01-45](https://user-images.githubusercontent.com/106885875/180606076-c80d28bc-7cbd-4991-b3a2-bf8ad502ea03.png)

To run a secured script
sudo mysql_secure_installation

*while trying to run mysql secured installation,i had the attached error*

![Screenshot from 2022-07-23 14-05-30](https://user-images.githubusercontent.com/106885875/180607011-1e212c51-9375-41c0-bf4f-a03e51071f0a.png)

*resolved it by:*

__running the below commands__;

sudo mysql
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'SetRootPasswordHere';
exit

I re-ran the below
sudo mysql_secure_installation
sudo mysql -p

![Screenshot from 2022-07-23 14-23-42](https://user-images.githubusercontent.com/106885875/180606999-4460d489-ef05-45d0-b28f-bb86d8a322bc.png)

## * STEP3- INSTALLING PHP

I installed i. PHP, ii. a PHP modlule that allows database interaction and iii. a module that alows Apache to hndle PHP files

sudo apt install php libapache2-mod-php php-mysql

To confirm PHP installation version
php -v

![Screenshot from 2022-07-23 14-33-06](https://user-images.githubusercontent.com/106885875/180607275-228bfec8-68a4-4e02-83c2-4b0690dd1d98.png)

## * STEP -4 CREATING A VIRTUAL HOST FOR YOUR WEBSITE USING APACHE

sudo mkdir /var/www/projectlamp
sudo chown -R $USER:$USER /var/www/projectlamp
sudo vi /etc/apache2/sites-available/projectlamp.conf
  (input and save content)
 
sudo ls /etc/apache2/sites-available
sudo a2ensite projectlamp (to enable virtual host)
sudo a2dissite 000-default (NB this should be done except you use a custom domain)

sudo apache2ctl configtest (to check for syntax errors)

## * STEP 5 — ENABLE PHP ON THE WEBSITE

sudo vim /etc/apache2/mods-enabled/dir.conf
  (input and save content)
  
sudo systemctl reload apache2 (To reload the new config) 

http://<Public-IP-Address>80

 ![Screenshot from 2022-07-23 14-55-47](https://user-images.githubusercontent.com/106885875/180608165-1d4cb002-1ada-400b-b362-55235e307dee.png)
 
  
