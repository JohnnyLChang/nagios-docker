# Docker-Nagios
Docker image for Nagios based on commit [6a309a6](https://github.com/JasonRivers/Docker-Nagios/tree/6a309a6e5d7d04bcf4201bd086f88b90f44105f0) of [Jason River's](https://github.com/JasonRivers/Docker-Nagios) Docker image. 

Build Status: [![Build Status](https://travis-ci.org/manios/nagios-docker.svg?branch=master)](https://travis-ci.org/manios/nagios-docker)

Nagios Core 4.3.4 running on Ubuntu 16.04 LTS with NagiosGraph & NRPE

### Configurations
Nagios Configuration lives in ```/opt/nagios/etc```
NagiosGraph configuration lives in ```/opt/nagiosgraph/etc```.

### Install

```sh
docker pull manios/nagios:latest
```

### Running

Run with the example configuration with the following:

```sh
docker run --name nagios4 -p 0.0.0.0:8080:80 manios/nagios:latest
```

alternatively you can use external Nagios configuration & log data with the following:

```sh
docker run --name nagios4  \
  -v /path-to-nagios/etc/:/opt/nagios/etc/ \
  -v /path-to-nagios/var:/opt/nagios/var/ \
  -v /path-to-custom-plugins:/opt/Custom-Nagios-Plugins \
  -p 0.0.0.0:8080:80 manios/nagios:latest
```

Note: The path for the custom plugins will be /opt/Custom-Nagios-Plugins, you will need to reference this directory in your configuration scripts.

For best results your Nagios image should have access to both IPv4 & IPv6 networks 

#### Credentials

The default credentials for the web interface is `nagiosadmin` / `nagios`

### Extra Plugins

* Nagios [nrpe](http://exchange.nagios.org/directory/Addons/Monitoring-Agents/NRPE--2D-Nagios-Remote-Plugin-Executor/details)
* [Nagiosgraph](http://exchange.nagios.org/directory/Addons/Graphing-and-Trending/nagiosgraph/details)
* [JR-Nagios-Plugins](https://github.com/JasonRivers/nagios-plugins) -  custom plugins from Jason Rivers
* [WL-Nagios-Plugins](https://github.com/willixix/WL-NagiosPlugins) -  custom plugins from William Leibzon
* [JE-Nagios-Plugins](https://github.com/justintime/nagios-plugins) -  custom plugins from Justin Ellison 
* [Mongodb official plugin](https://github.com/mzupan/nagios-plugin-mongodb/) with commit id [3805751](https://github.com/mzupan/nagios-plugin-mongodb/tree/38057511e1390317f9faa9a1e44ee5c2561207ef).
* [Zookeeper plugin](https://github.com/andreisavu/zookeeper-monitoring) with commit id [f0aaddd](https://github.com/andreisavu/zookeeper-monitoring/commit/f0aaddd640e3aa1cd0f2984b754b74938e383681).

