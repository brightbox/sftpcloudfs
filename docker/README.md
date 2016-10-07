sftpcloudfs Docker image
========================

First pull the image with:

    docker pull jjmartinez/sftpcloudfs

You can run the SFTP server with:

    docker run --env AUTH=YOURAUTH -d --name sftp -p 8022:8022 jjmartinez/sftpcloudfs

Replace `YOURAUTH` with the public authentication service of your Swift provider (eg. `https://auth.storage.memset.com/v1.0`).

The *ENV* variables are:

 - *AUTH*: authentication service URL (unless it is provided by a conf file by mounting the volume, this is required).
 - *PORT*: port to listen for connections (default: 8022).

For further configuration you can mount `/config/` volume and copy the following files:

 - Your own `sftpcloudfs.conf` file (eg. for Keystone 2.0 auth), see [this configuration file](https://github.com/reidrac/sftpcloudfs/blob/master/docker/sftpcloudfs.conf) as an example.
 - An existing `id_rsa` key (by default a new one will be created when the container is run).

The image already includes memcached and Keystone support.

Building the container
----------------------

Get the [docker directory](https://github.com/reidrac/sftpcloudfs/tree/master/docker) and run:

    docker build .

Maintainer
----------

Juan J. Martinez <jjm@usebox.net>

