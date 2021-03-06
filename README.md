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

### Where is the data of the typo3temp folder?

The folder `/var/www/private/typo3temp` inside of the container is
mapped to a `tmpfs` filesystem (RAM-Drive). This will increase the
speed of the setup dramatically but you are not able to see the files
inside of that folder on your local hard drive. If you need to see
the `typo3temp` folder you can just comment out the line in the
`docker-compose.yml`.

This will only work if your `typo3temp` folder is in the `private`
folder which is the case if you use `helhum/typo3-secure-web` in your
setup with the default configuration. You can simply adjust the path
to the `typo3temp` folder if it is not correct in your setup.

### Enable Xdebug

To enable xdebug you have to set the environment variable
`DOCKER_XDEBUG_CONFIG`. Xdebug will be startet on port 9001.

*Please note that the setup is very slow if Xdebug is enabled!*

Example:
`DOCKER_XDEBUG_CONFIG="remote_port=9001 remote_enable=1 remote_host=host.docker.internal remote_autostart=Off" docker-compose up -d --force-recreate`
