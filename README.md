AUGS docker server
================

This application contains the AUGS docker server sources.

Installation
------------

### Clone repository into your server

```bash
$ git clone git@github.com:i-unlu/ubitransport-docker.git .
```

### Install

```bash
$ git clone git@github.com:i-unlu/ubitransport-docker.git
$ cd ubitransport-docker
$ docker-compose up -d --build
$ docker exec -d server bin/console doc:mi:mi --no-interaction
$ docker exec -d server bin/console doc:mi:mi --env=test --no-interaction
```

#### Home page

http://127.0.0.1:8003

#### Swagger listing application page

http://127.0.0.1:8003/swagger/index.html
