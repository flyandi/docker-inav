[![Build Status](https://travis-ci.org/flyandi/docker-inav.svg?branch=master)](https://travis-ci.org/flyandi/docker-inav)

Docker Build image for iNav Flight
========================================================

Introduction
------------

This docker image is intended to provide a full build environment for [iNav Flight](http://inavflight.com) and is hosted on DockerHub.

The image contains the latest arm build toolchain.

Get Started
-------------
```shell
docker pull flyandi/docker-inav
```

Local Build Example
-------------

```shell
docker pull flyandi/docker-inav
git clone https://github.com/iNavFlight/inav
cd inav/
docker run --rm -v `pwd`:/home/src/ flyandi/inav make TARGET=OMNIBUSF4V3
```

GitLab CI Build Example
-------------

GitLab CI:

```yaml
stages:
  -build

build:
  stage: build
  image: flyandi/docker-inav
  script:
    - git clone https://github.com/iNavFlight/inav
    - cd inav/
    - docker run --rm -v `pwd`:/home/src/ flyandi/inav make TARGET=OMNIBUSF4V3
  artifacts:
    paths:
      - ./inav/obj
    expire_in: 1 day
```