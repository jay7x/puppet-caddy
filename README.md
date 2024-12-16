
# Puppet module for Caddy

[![Build Status](https://travis-ci.org/voxpupuli/puppet-caddy.svg?branch=master)](https://travis-ci.org/voxpupuli/puppet-caddy)
[![Code Coverage](https://coveralls.io/repos/github/voxpupuli/puppet-caddy/badge.svg?branch=master)](https://coveralls.io/github/voxpupuli/puppet-caddy)
[![Puppet Forge](https://img.shields.io/puppetforge/v/puppet/caddy.svg)](https://forge.puppetlabs.com/puppet/caddy)
[![Puppet Forge - downloads](https://img.shields.io/puppetforge/dt/puppet/caddy.svg)](https://forge.puppetlabs.com/puppet/caddy)
[![Puppet Forge - endorsement](https://img.shields.io/puppetforge/e/puppet/caddy.svg)](https://forge.puppetlabs.com/puppet/caddy)
[![Puppet Forge - scores](https://img.shields.io/puppetforge/f/puppet/caddy.svg)](https://forge.puppetlabs.com/puppet/caddy)
[![License](https://img.shields.io/github/license/voxpupuli/puppet-caddy.svg)](https://github.com/voxpupuli/puppet-caddy/blob/master/LICENSE)

## Table of Contents

1. [Description](#description)
1. [Setup - The basics of getting started with Caddy](#setup)
    * [What Caddy affects](#what-caddy-affects)
    * [Setup requirements](#setup-requirements)
    * [Beginning with Caddy](#beginning-with-caddy)
1. [Usage - Configuration options and additional functionality](#usage)
1. [Limitations - OS compatibility, etc.](#limitations)
1. [Development - Guide for contributing to the module](#development)

## Description

This module installs and configures Caddy - The HTTP/2 web server with automatic
HTTPS.

**Important:** This module only supports the installation of Caddy 2.x. If you
want to install Caddy 1.x, you should use version v2.0.0 of this module.

## Setup

### What Caddy affects

* Caddy binary
* Caddy configuration file
* Caddy virtual hosts
* Caddy service

### Setup Requirements

This module has the following dependencies:

* [puppet/systemd](https://github.com/voxpupuli/puppet-systemd)
* [puppet/archive](https://github.com/voxpupuli/puppet-archive)
* [puppetlabs/stdlib](https://github.com/puppetlabs/puppetlabs-stdlib)

When `install_method` is set to 'repo', this module implicitly requires either
[puppetlabs-apt](https://github.com/puppetlabs/puppetlabs-apt) module for
Debian distro family, or [puppet-yum](https://github.com/voxpupuli/puppet-yum)
module for RedHat distro family.

### Beginning with Caddy

Install Caddy without any configuration:

```puppet
include caddy
```

## Usage

Install customized version of Caddy

```puppet
class { 'caddy':
  caddy_features => 'http.git,http.filter,http.ipfilter',
}
```

Install specific version of Caddy

```puppet
class { 'caddy':
  version        => '2.0.0',
  install_method => 'github',
}
```

Install Caddy and configure virtual host, based on source:

```puppet
caddy::vhost { 'example1':
  source => 'puppet:///modules/caddy/etc/caddy/config/example1.conf',
}
```

Install Caddy and configure virtual host, based on content:

```puppet
caddy::vhost { 'example2':
  content => 'localhost:2015',
}
```

## Reference

The [reference][1] documentation of this module is generated using [puppetlabs/puppetlabs-strings][2].

## Limitations

This module has been tested on:

* AlmaLinux 8/9
* CentOS 9
* Debian 11/12
* OracleLinux 8/9
* RedHat 8/9
* Rocky 8/9
* Ubuntu 20.04/22.04/24.04

For the official list of all tested distributions, please take a look at the [metadata.json](https://github.com/voxpupuli/puppet-caddy/blob/master/metadata.json#L24)

## Development

This module has grown over time based on a range of contributions from people
using it. If you follow these [contributing][3] guidelines your patch will
likely make it into a release a little more quickly.

## Author

This module is maintained by [Vox Pupuli][4]. It was originally written and
maintained by [Lukasz Rohde][5].

[1]: https://github.com/voxpupuli/puppet-caddy/blob/master/REFERENCE.md
[2]: https://github.com/puppetlabs/puppetlabs-strings
[3]: https://github.com/voxpupuli/puppet-caddy/blob/master/.github/CONTRIBUTING.md
[4]: https://voxpupuli.org
[5]: https://github.com/CommanderK5
