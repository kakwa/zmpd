[![Build Status](https://travis-ci.org/kakwa/zmpd.svg)](https://travis-ci.org/kakwa/zmpd)
zmpd
====

Standalone MPD Web GUI written in C, utilizing Websockets and Bootstrap/JS

This is a fork of ympd with some UI changes (http://www.ympd.org).

Disclamer
=========

Right now, there is not a lot of changes, the fork is in its early stage.

Changes wanted:
* |[ ]| having a more finder like view of the library (like ncmpcpp)
* |[ ]| add support for a configuration file (ini file)
* |[ ]| better internationalization
* |[ ]| make the display of confusing parameters optional (like the the sound output)
* |[ ]| if possible, merge the queue and "browse database" screen for a more intuitive layout


Dependencies
------------
 - libmpdclient 2: http://www.musicpd.org/libs/libmpdclient/
 - cmake 2.6: http://cmake.org/

Unix Build Instructions
-----------------------

1. install dependencies, cmake and libmpdclient are available from all major distributions.
2. create build directory ```cd /path/to/src; mkdir build; cd build```
3. create makefile ```cmake ..  -DCMAKE_INSTALL_PREFIX:PATH=/usr```
4. build ```make```
5. install ```sudo make install``` or just run with ```./zmpd```

Run flags
---------
```
Usage: ./zmpd [OPTION]...

 -h, --host <host>          connect to mpd at host [localhost]
 -p, --port <port>          connect to mpd at port [6600]
 -w, --webport [ip:]<port>  listen interface/port for webserver [8080]
 -u, --user <username>      drop priviliges to user after socket bind
 -V, --version              get version
 --help                     this help
```

SSL Support
-----------
To run zmpd with SSL support:

- create a certificate (key and cert in the same file), example:
```
# openssl req -x509 -newkey rsa:2048 -keyout key.pem -out cert.pem -days 1000 -nodes
# cat key.pem cert.pem > ssl.pem
```
- tell zmpd to use a webport using SSL and where to find the certificate: 
```
# ./zmpd -w "ssl://8081:/path/to/ssl.pem"
```

Copyright
---------

2013-2014 <andy@ndyk.de>
