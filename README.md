## SensorLogger for OwnCloud Development

### Install
1. your@machine:$ `git clone https://github.com/alexstocker/owncloud-docker-development.git`
2. your@machine:$ `cd owncloud-docker-development`
3. your@machine:...owncloud-docker-development$ `composer install`
4. your@machine:...owncloud-docker-development$ `composer docker-up`
5. your@machine:...owncloud-docker-development$ `sudo chown -Rf [USER]:[GROUP] vendor/` (adjust [USER] and [GROUP] to fit your needs)
6. open browser goto http://localhost:8080/ (have a look at .env for user credentials) and login

### Setup a device
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



