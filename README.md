shadowsocks
===========

[![PyPI version]][PyPI]
[![Build Status]][Travis CI]

A fast tunnel proxy that helps you bypass firewalls.

Features:
- TCP & UDP support
- User management API
- TCP Fast Open
- Workers and graceful restart
- Destination IP blacklist

Server
------

### Install

Debian / Ubuntu:

    apt-get install python-pip
    pip install shadowsocks-alexforks

CentOS:

    yum install python-setuptools && easy_install pip
    pip install shadowsocks-alexforks

For CentOS 7, if you need AEAD ciphers, you need install libsodium
```
dnf install libsodium python34-pip
pip3 install  shadowsocks-alexforks
```
Linux distributions with [snap](http://snapcraft.io/):

    snap install shadowsocks

Windows:

See [Install Shadowsocks Server on Windows](https://github.com/shadowsocks/shadowsocks/wiki/Install-Shadowsocks-Server-on-Windows).

### Usage

    ssserver -p 443 -k password -m aes-256-cfb

To run in the background:

    sudo ssserver -p 443 -k password -m aes-256-cfb --user nobody -d start

To stop:

    sudo ssserver -d stop

To check the log:

    sudo less /var/log/shadowsocks.log

Check all the options via `-h`. You can also use a [Configuration] file
instead.

If you installed the [snap](http://snapcraft.io/) package, you have to prefix the commands with `shadowsocks.`,
like this:

    shadowsocks.ssserver -p 443 -k password -m aes-256-cfb
    
### Usage with Config File

[Create configuration file and run](https://github.com/shadowsocks/shadowsocks/wiki/Configuration-via-Config-File)

To start:

    ssserver -c /etc/shadowsocks.json


### Build & Publish

Build:
    # in venv pypi-py3
    pip install build

    # build the source and binary packages for py3 in the dist/ directory
    pip -m build

    # in venv pypi-py2
    pip install build

    # build the binary package for py2 in the dist/ directory
    pip -m build -w

Publish:
    # in venv pypi-py3
    pip install twine

    # publish to Test PyPi
    twine upload --repository testpypi dist/*

    # publish to PyPi
    twine upload dist/*

Test installation from Test PyPi:
    # in venv shadowsocks-py3
    # use --no-deps for the test pypi
    pip install -i https://test.pypi.org/simple/ --no-deps shadowsocks-alexforks

Test installation from PyPi:
    # in venv shadowsocks-py3
    # use --no-binary to make sure to install from source rather than the binary
    # combine with --use-pep517 to make sure to use the PEP 517 build system
    pip install --no-binary --use-pep517 shadowsocks-alexforks


Documentation
-------------

You can find all the documentation in the [Wiki](https://github.com/shadowsocks/shadowsocks/wiki).

License
-------

Apache License







[Build Status]:      https://img.shields.io/travis/shadowsocks/shadowsocks/master.svg?style=flat
[PyPI]:              https://pypi.python.org/pypi/shadowsocks
[PyPI version]:      https://img.shields.io/pypi/v/shadowsocks.svg?style=flat
[Travis CI]:         https://travis-ci.org/shadowsocks/shadowsocks

