## Remote PHP debugging for Laravel with homestead and Phpstorm


## Start vagrant
```
vagrant up
vagrant ssh
```
## Configuring PHP
#### Get PHP version
```
php -v
```
In this case my version is **7.3**
![](images/php_version.png?raw=true)
### Open config file
```
cd /etc/php
ls
cd 7.3
```
Remember to use your PHP version.

### Find Config file
```
find ./cli/conf.d -name *debug*
```
![](images/find_config.png?raw=true)
Using the returned file path.

### Editing config file

```
nano ./cli/config.d/20-xdebug.ini
```

Make sure that the config looks like this


```
zend_extension=xdebug.so
xdebug.remote_autostart = 1
xdebug.remote_enable = 1
xdebug.remote_connect_back = 0
xdebug.remote_host=10.0.2.2
xdebug.idekey=artisan
xdebug.remote_port = 9000
xdebug.max_nesting_level = 512
```

## On to PhpStorm

- [ ] Open your project in PhpStorm
- [ ] File > Settings
- [ ] **Settings Window** > Languages & Frameworks > PHP > Servers
- [ ] Click **+**
- [ ] Check use path mappings
- [ ] Add local project directory

Should look something like this

![](images/settings_server.png?raw=true)

- [ ] Click Run > Edit Configurations
- [ ] Click **+**
- [ ] Php Remote Debug
- [ ] Name: artisan
- [ ] Server: **name of server **
- [ ] IDE Key: artisan

Should look something like this

![](images/run_config.png?raw=true)


## Enable/Disable
Run > Start/Stop Listening for PHP Debug Connections

Now you should be able to set a break point.
