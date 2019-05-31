+++
title = "How To Setup AbterPHP for development on Linux"
date = "2019-05-31T13:36:02+02:00"
description = "It only takes a few minutes to get started with AbterPHP. If you have docker and mkcert installed."
tags = ["php", "installation"]
categories = ["setup"]
author = "Team AbterCMS"
image = "images/blog/Linux_Lite_4.0_516x334.png"
+++


This guide should help you get up and running with AbterPHP on recent Linux distros in minutes, however this may or may not work on Linux or OSX.

**Wait!** What's AbterPHP you ask? It's just the first implementation of AbterCMS which happens to be in PHP. This is also likely the only implementation
that implements both frontend and backend features.

## Pre-requisites
### Grab the source code

This should be fairly obvious if you're reading it, but feel free to download the code from Github or clone the repository.
Just use the "Clone or download" button to get you started.

### Install [docker](https://docker.com/)

The recommended way of getting started with the AbterPHP is via docker. While it is not necessarily mandatory, some of the
documentation might assume that all developers use `docker` for development. If you want to run the code, you'll have to
ensure that you have the right version of PHP, with the neccessary modules and that you have at least a supported version
of MySQL (or later PostgreSQL). While having Redis or Memcached is great, those are not mandatory.

### Install [mkcert](https://mkcert.dev/)

Since security is a top priority, pure http is not supported out of the box, therefore you'll need to install a certificate. 
The recommended way is using `mkcert`. While it is not necessarily mandatory, some of the
documentation might assume that all developers use `mkcert` for development. 

## Installation

### Basics

 * Open the project in a console. (The rest of the installation documentation will assume that `.` is the root directory of the project.)
 * Add abtercms.test as localhost in `/etc/hosts` on Linux and OSX or `???` on Windows.

```
# /etc/hosts
# [...]
127.0.0.1	abtercms.test
```

 * Create certificate: Since security is a top priority, you'll need to create a certificates

```
mkcert abtercms.test "*.abtercms.test"
mv abtercms.test+1* ./docker/nginx/certs/
```

 * Set some permissions

```
chmod -R 0777 ./tmp ./public/tmp
chmod +x apex

```

 * Spin up the containers

```
docker-compose pull
docker-compose up -d
```

 * Install the dependencies

```
docker-compose exec make install
```

#### Ensure your settings are sane

Although we try to provide a reasonable set of settings for getting started quickly, at this point you may want to edit
`config/environment/.env.app.php` to make your settings sane for your needs. Please note however that these values can
be and in some cases will be overwritten by your environment variables. This means that if you are running the system
with `docker-compose` than you might need to edit some of these values in `docker-compose.yml`.

*Note:* If you do not have the file `config/environment/.env.app.php` then something must have gone wrong in the previous step,
because it should be created during `php composer.phar install`.

#### Install the db schema and create a new admin user

You need to log into the PHP container to do this:

```
docker-compose exec php ./apex migrations:up
docker-compose exec php ./apex user:create {username} {email} {strongPassword} admin en
```

If everything went well, you should be able to log in with your new user at `https://abtercms.test/login-iddqd`.
