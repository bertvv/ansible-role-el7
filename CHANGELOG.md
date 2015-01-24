# Change log

This file contains al notable changes to the EL7 Ansible role. This file adheres to the guidelines of [http://keepachangelog.com/](http://keepachangelog.com/).

Versioning follows [Semantic Versioning](http://semver.org/).

## 1.0.2 - 2015-01-24

# Added

- Patched ifup scripts that don't overrule some firewalld settings after reboot. This is a workaround for CentOS [bug #7526](https://bugs.centos.org/view.php?id=7526).


## 1.0.1 - 2014-12-12

# Added

- Change log
- Testing section in the README


## 1.0.0 - 2014-12-05

First release!

# Added

- Install external repos from RPM package(s)
- Install packages not in the default installation
- Turn services on or off
- Create users and groups
- Set up SSH key for administrator account
- Apply basic security settings, like turning on SELinux and the firewall

