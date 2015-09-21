# multiple-php-docker

This repository is an example of how to run multiple php applications inside docker behind an nginx webserver.

The php applications use fastcgi to process requests and composer to manage dependencies.

## Running

```bash
$ docker-compose up
```

Now the nginx webserver is running so we can access it via:

```bash
$ curl localhost:8000
```
