# Linux Server Configuration

This repository implements the fifth project (Linux Server Configuration) in the Udacity Full Stack Nanodegree program. It describes how a Linux server was configured to deploy the third project (Item Catalog) using PostgreSQL and Apache2.

Authentication is handled by Google OAuth.

# IP Address and Port
The IP address of the live application is in the reviewer notes. The SSH port is 2200.

An admin account 'grader' has been created. The private SSH key (and password to use 'sudo') is in the reviewer notes.

# Configuration Summary
## User Management
The following users exist on the server:

-  root - created by default by the operating system (used to install software but login now disabled)
-  grader - created to allow reviewer to login -- can use sudo
-  catalog - owns the catalog application files -- cannot login remotely

The files placed in /var/www/catalog are owned by user 'catalog' and have group permissions assigned to www-data. Except for .git which denies read, write, and execute permissions to the group and world. This is to ensure apache cannot read .git.

## Security
SSH is configured to deny password authentication -- keys must be used. SSH has been configured to listen on port 2200 rather than the default 22.

Account grader has a .ssh/authorized_keys file. The private key has been submitted via the reviewer notes.

## Application Functionality
The Item Catalog application can be accessed at the ip address given in the reviewer notes at standard port 80.

The database server is configured with a user 'catalog' with the following properties:

*  not a database superuser
*  owns database 'catalog'

## Software
The following packages have been installed:

 - tmux - to simplify configuring server
 - git - needed to clone software from Github repository
 - apache2 - used as web server
 - postgresql - used as database
 - python-dev & python-pip - needed to run pip to install python dependencies
 - project 3 - item catalog - flask application cloned into /var/www/catalog

## Third Party Resources
### Network Time Protocol

- https://www.digitalocean.com/community/tutorials/how-to-set-up-time-synchronization-on-ubuntu-12-04

### Flask and Apache

- https://www.digitalocean.com/community/tutorials/how-to-deploy-a-flask-application-on-an-ubuntu-vps
- http://flask.pocoo.org/snippets/99/
- http://askubuntu.com/questions/329323/problem-with-restarting-apache2

### Oauth

- https://discussions.udacity.com/t/im-getting-the-not-json-serializable-when-i-used-the-login-code-provided-from-the-oauth/16010/2
