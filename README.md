## SensorLogger for OwnCloud Development

### Install
1. your@machine:$ `git clone https://github.com/alexstocker/owncloud-docker-development.git`
2. your@machine:$ `cd owncloud-docker-development`
3. your@machine:...owncloud-docker-development$ `composer install`
4. your@machine:...owncloud-docker-development$ `composer docker-up`
5. your@machine:...owncloud-docker-development$ `sudo chown -Rf [USER]:[GROUP] vendor/` (adjust [USER] and [GROUP] to fit your needs)
6. open browser goto http://localhost:8080/ (have a look at .env for username and password) and login

### Usage

#### Get docker containers up and running
your@machine:...owncloud-docker-development$ `composer docker-up`

#### Stop docker containers
your@machine:...owncloud-docker-development$ `composer docker-stop`

#### Start docker containers 

> For instance: if host was rebooted
> Do NOT use `docker start|stop owncloud_[server|redis|mariadb]`. 
> for `restart` the containers. SensorLogger App will not be present if you do so.

your@machine:...owncloud-docker-development$ `composer docker-start`

### Setup a device (simple)
1. Got to Settings->Security
2. Create a new App `password/passcode`
3. Edit `sensorlogger/test/curl/post.php` using an editor or of your choice (vi, mc, pico, gedit, notepad, phpstorm, netbeans, eclipse)
4. Modify `$token` variable. Replace the existing string by the `passcode` you created two steps earlier
5. your@machine:...owncloud-docker-development$ `php ./sensorlogger/tests/curl/post.php`
   > Result/Response `{"success":true,"message":"Sensor Log successfully stored","data":null}`
   > more about the `API` please read the docs https://github.com/alexstocker/sensorlogger/wiki/API
6. Done

Now you have a fake sensor device named `Default device`. 
* to view and edit device properties such as Group and Type got to `SensorLogger->Devices`
* to view data got to `SensorLogger->List`
* to add dashboard widget got to `SensorLogger->Dashboard`
  > more about `Dashboard Widgets` please read the docs https://github.com/alexstocker/sensorlogger/wiki/Users

#### Creating fake sensor data in a loop
`while [ 1 ]; do clear; php ./sensorlogger/tests/curl/post.php; sleep 5; done;`

### Setup a device (extend)
1. Got to Settings->Security
2. Create a new App `password/passcode`
3. Edit `sensorlogger/test/curl/register_extend.php` using an editor or of your choice (vi, mc, pico, gedit, notepad, phpstorm, netbeans, eclipse)
4. Modify `$token` variable. Replace the existing string by the `passcode` you created two steps earlier
5. your@machine:...owncloud-docker-development$ `php ./sensorlogger/tests/curl/register_extend.php`
   > Result/Response `{"success":true,"message":"Device successfully registered","data":[{"id":"1","description":"Temperatur","type":"temperature","short":"\u00b0C"},{"id":"2","description":"Luftfeuchtigkeit","type":"humidity","short":"% r.F."},{"id":"3","description":"Carbon dioxide","type":"CO2","short":"ppm"}]}`
6. Edit `sensorlogger/test/curl/post_extend.php`
7. Modify `$token` variable. Replace the existing string by the `passcode` you created two steps earlier
   a. Additional: Modify `dataTypeIds` if not equal to the ids shown in the Result/Response above (5.)
8. your@machine:...owncloud-docker-development$ `php ./sensorlogger/tests/curl/post_extend.php`
   > Result/Response `{"success":true,"message":"Sensor Log successfully stored","data":[{"dataTypeId":1,"value":23.6},{"dataTypeId":2,"value":12.2},{"dataTypeId":3,"value":865.9}]}`
   > more about the `API` please read the docs https://github.com/alexstocker/sensorlogger/wiki/API
9. Done

#### Creating fake sensor data in a loop
`while [ 1 ]; do clear; php ./sensorlogger/tests/curl/post_extend.php; sleep 5; done;`


