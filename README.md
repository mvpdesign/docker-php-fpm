# Docker PHP-FPM

A lightweight PHP-FPM container built off of WordPress's starting point.

## Hosts within your environment

You'll need to configure your application to use any services you enabled:

| Service | Hostname | Port number |
| ------- | -------- | ----------- |
| php-fpm | php-fpm  | 9000        |

## XDebug

Xdebug is installed as part of the php-fpm Dockerfile. Currently, the `xdebug-beta` is installed on the container due to issues with stable version of XDebug and PHP 7.3.x. Below you will find the default xdebug configuration.

```
xdebug.remote_enable=1
xdebug.idekey=docker
xdebug.remote_autostart=1
xdebug.remote_host=docker.for.mac.localhost
```

### XDebug and Visual Studio Code

A `.vscode/launch.json` file is include in the repo, however for reference the needed VSCode launch.json` config is attached below.

```
{
    "name": "Listen for XDebug",
    "type": "php",
    "request": "launch",
    "port": 9000,
    "log": true,
    "pathMappings": {
        "/application": "${workspaceFolder}"
    }
}
```

## Docker compose cheatsheet

**Note:** you need to cd first to where your docker-compose.yml file lives.

-   Start containers in the background: `docker-compose up -d`
-   Start containers on the foreground: `docker-compose up`. You will see a stream of logs for every container running.
-   Stop containers: `docker-compose stop`
-   Kill containers: `docker-compose kill`
-   View container logs: `docker-compose logs`
-   Execute command inside of container: `docker-compose exec SERVICE_NAME COMMAND` where `COMMAND` is whatever you want to run. All project files are found in the `/var/www/html` folder in the container.
