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

* Added users with ```adduser``` and gave them sudo permissions by adding the users to ```/etc/sudoers```

* Edited ```/etc/ssh/sshd_config``` to disable password access and root remote access.  The service was restarted with ```sudo service ssh restart```
 
* The public keys under root .ssh were copied to the users (```/home/user/.ssh/authorized_keys```) to allow key-based login
 
* Cloned the catalog project with git into ```/var/www/catalog```

* After installing apache, configured ```/etc/apache2/sites-available/``` to connect to the above mentioned project

* After installing postgresql, created a user ```grader```, and created a database named ```catalog```

* Correctly set the connection strings in the cloned project, and executed the following files ```database_setup.py data.py```

