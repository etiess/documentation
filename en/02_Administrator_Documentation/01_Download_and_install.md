## I don't want to install wallabag
If you can't or don't want to install Wallabag on your server, we suggest you create a free account on Framabag wich uses our software: read the complete documentation here (TODO write Create a framabag account).

## I want to install wallabag
 
[Download the latest wallabag version](http://www.wallabag.org/download) and unpack it:

    wget http://wllbg.org/latest
    unzip latest
    mv wallabag-version-number wallabag

Copy the files on your web server. For example in Ubuntu/Debian:

    sudo mv wallabag /var/www/html/
	
## Prerequisites for your web server
* [PHP 5.3.3 or more](http://php.net/manual/en/install.php)
* [SQLite](http://php.net/manual/en/book.sqlite.php) or [MySQL](http://php.net/manual/fr/book.mysql.php) or [PostgreSQL](http://php.net/manual/en/book.pgsql.php)
* [XML for PHP](http://php.net/xml)
* [PCRE](http://php.net/pcre)
* [Data filtering](http://php.net/manual/book.filter.php)
* [Tidy for PHP](http://php.net/tidy)
* [cURL](http://php.net/curl)
* [allow_url_fopen](http://www.php.net/manual/en/filesystem.configuration.php#ini.allow-url-fopen)
* [gettext](http://php.net/manual/en/book.gettext.php)

To ensure that your server has all the prerequisites, you can run the file `wallabag_compatibility_test.php` that is located in the `install` directory of wallabag. In your browser, open http://votreserveur.com/wallabag/install/wallabag_compatibility_test.php and install the required components. For example, Tidy can be installed on Ubuntu/Debian with these commands:

    sudo apt-get install php5-tidy
    sudo service apache2 reload

## Installation of the dependencies 
In order to work properly, wallabag needs some dependencies. To install them, you have to use `composer`. Go into your wallabag folder (in Ubuntu/Debian: <code>/var/www/html/wallabag/</code>) and run the following commands:

    curl -s http://getcomposer.org/installer | php
    php composer.phar install

If you can't install `composer` (in a mutualized hosting for example), we provide a [vendor.zip](http://wllbg.org/vendor). You can either download and unpack it in your wallabag directory, or let the installation script do it for you.  

### Creation of the MySQL database
wallabag can be used with different types of database (`sqlite`, `mysql` or `postgresql`) but we advise to use MySQL, more efficient. In this case, it is necessary to create a new database (for example `wallabag`), a new user (for example `wallabag`) and a password (here `YourPassword`). You can either use 'phpMyAdmin', or execute the following commands:

    mysql -p -u root
    mysql> CREATE DATABASE wallabag;
    mysql> GRANT ALL PRIVILEGES ON `wallabag`.* TO 'wallabag'@'localhost' IDENTIFIED BY 'VotreMotdePasse';
    mysql> exit

## Permissions
Your web server needs a writing access in `assets`, `cache` and `db` directory. Otherwise, a message will report that the installation is impossible:

    sudo chown -R www-data:www-data /var/www/html/wallabag

## Installation of wallabag. Finally!
Access to wallabag from your web browser: http://votreserveur.com/wallabag . If your server is correctly configured, you'll reach the setup screen.  

Fill your database type (`sqlite`, `mysql` or `postgresql`) and finally the information for your user account. If you chose MySQL, the standard configuration will be:

    Database engine:		MySQL
    Server:					localhost
    Database				wallabag
    Username:				wallabag
    Password:				YourPassword

Then create your first user and its password (different from the ones used for the database).

wallabag is now installed. 

## Login 

From your web browser, you reach the login screen: fill your username and your password to connect to your account.

Enjoy!
