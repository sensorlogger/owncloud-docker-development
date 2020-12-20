## SensorLogger for owncloud Development

Simple owncloud docker environment. Ready to test and develop SensorLogger for owncloud.
Created and tested for use with Ubuntu 18.04. But should work on any system supporting composer and docker.

### Requirements
* composer
* docker

### Install
1. git clone https://github.com/sensorlogger/owncloud-docker-development.git
1. cd owncloud-docker-development
1. composer install
1. composer docker-up
1. sudo chown -Rf [USER]:[GROUP] vendor/
