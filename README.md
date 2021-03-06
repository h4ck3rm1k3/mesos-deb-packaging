# Mesos packaging

Mesos is a cluster manager that provides efficient resource isolation and sharing across distributed applications, or frameworks.  See [Mesos website](http://mesos.apache.org/) for more details.

## Mesos configuration

Mesos arguments could be specified by creating files structure in `/etc/mesos-slave` or in `/etc/mesos-master`.

For specifing e.g. `--isolation=cgroups` you would create

```
  /etc
    /mesos-slave
      isolation       # with contents 'cgroups'
```

In similar manner you can restrict hardware resources used by mesos-slave:

```
  /etc
    /mesos-slave
      /resources
        cpu          # with contents e.g. '5'
```

## Building package

Build deb package for Debian/Ubuntu with following:

        ./build_mesos --repo https://git-wip-us.apache.org/repos/asf/mesos.git?ref=0.15.0 --nominal-version 0.15.0

### Requirements

  * Ruby (build scripts uses [FPM](https://github.com/jordansissel/fpm))

    ```
    $ gem install fpm
    $ sudo apt-get install python-dev autoconf automake git make libssl-dev libcurl3
    ```

  * for Mesos >= 0.16

    ```
    $ sudo apt-get install libsasl2-dev
    ```

## Puppet

Package could be automatically configured by a [Puppet module](https://github.com/deric/puppet-mesos)

## TODO

   * RedHat/CentOS RPM support

## Authors

   * Tomas Barton
   * Jason Dusek
   * Jeremy Lingmann
   * Chris Buben

