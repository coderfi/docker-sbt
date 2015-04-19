docker-sbt
==========

## Summary

Scala SBT Compiler Image for Docker.

This image is meant to be used as a sbt compiler tool.

## Configuration

This docker image contains the following software stack:

- OS: busybox

- Java: Oracle JDK 1.8.0_40

- Scala: 2.11.6

- Sbt: 0.13.8

### Dependencies

* [dockerfile/java:oracle-java8](https://github.com/dockerfile/java)


### History

* 0.1 - Initial Docker

## Installation

Latest version:

   ```
   $ docker pull coderfi/sbt:latest
   ```

All versions:

   ```
   $ docker pull coderfi/sbt
   ```

Specific version:

   ```
   $ docker pull coderfi/sbt:2.11.6
   ```

## Usage

Create a data docker volume to cache third party jar downloads:

```
docker run --name=data-scala -v /root/.ivy2 -v /root/.sbt busybox
```

Start sbt shell
```
docker run --rm -it --volumes-from=data-scala coderfi/sbt
```

Run sbt package
```
docker run --rm --volumes-from=data-scala coderfi/sbt package
```

Increase memory to sbt
```
docker run --rm --volumes-from=data-scala -e SBT_OPTS="-Xms512M -Xmx2G -Xss1M -XX:+CMSClassUnloadingEnabled" coderfi/sbt package
```
