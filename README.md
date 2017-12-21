# Example docker setups

Contains a few example setups on how to use docker containers
to setup an easy webserver with php and mysql

## php-7.2-apache-mysql

This folder contains a setup with an apache webserver, a mysql database
and a php-fpm image that contains everything required for a TYPO3 website.

### Start the setup

1. Go to the folder
`cd php-7.2-apache-mysql`

2. Start the docker containers defined in the docker-compose.yml
`docker-compose up`

All required containers will be created and started.
When finished, you'll see the log output in the terminal, you
should be able to browse `http://localhost:8080` and see
a phpinfo.
You should also be able to connect to the MySQL server on
`localhost:13306`.