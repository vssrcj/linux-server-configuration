# Linux Server Configuration

This goal of this project is to configure a barebones linux web server

### Remote server

IP 52.35.19.236

SSH PORT: 2200

### Hosted Application

http://ec2-52-35-19-236.us-west-2.compute.amazonaws.com/sports/

### Software Installed

* libapache2-mod-wsgi python-dev
* a2enmod wsgi 
* python-pip 
* postgresql
* libpq-dev
* git
* pip: 
  * bleach
  * oauth2client
  * requests
  * httplib2
  * redis
  * passlib
  * itsdangerous
  * flask-httpauth

### Configurations

* Change to Utc time with ```sudo dpkg-reconfigure tzdata```

* Added users with ```adduser``` and gave them sudo permissions by adding the users to ```/etc/sudoers```

* Edited ```/etc/ssh/sshd_config``` to disable password access and root remote access.  The service was restarted with ```sudo service ssh restart```
 
* The public keys under root .ssh were copied to the users (```/home/user/.ssh/authorized_keys```) to allow key-based login.  Set the corresponding keys and directories to the appropriate rights.
 
* Cloned the catalog project with git into ```/var/www/catalog```

* After installing apache, configured ```/etc/apache2/sites-available/``` to connect to the above mentioned project. Started (or restarted) with ```sudo /etc/init.d/apache2 reload```

* After installing postgresql, created a user ```grader```, and created a database named ```catalog```

* Correctly set the connection strings in the cloned project, and executed the following files ```database_setup.py data.py```

### Third party resources used

* UFW
  * https://help.ubuntu.com/community/UFW
* Timezones
  * http://askubuntu.com/questions/138423/how-do-i-change-my-timezone-to-utc-gmt
* Setting up Apache and Flask 
  * http://www.bogotobogo.com/python/Flask/Python_Flask_HelloWorld_App_with_Apache_WSGI_Ubuntu14.php
  * https://www.digitalocean.com/community/tutorials/how-to-deploy-a-flask-application-on-an-ubuntu-vps
* PostgreSQL
  * https://www.digitalocean.com/community/tutorials/how-to-secure-postgresql-on-an-ubuntu-vps
  * http://www.postgresql.org/docs/9.1/static/sql-alterrole.html
