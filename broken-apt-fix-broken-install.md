#

```sh
$ sudo apt --fix-broken install
Unpacking libjpeg62-turbo-dev:amd64 (1:1.5.2-2+deb10u1) ...
dpkg: error processing archive /var/cache/apt/archives/libjpeg62-turbo-dev_1%3a1.5.2-2+deb10u1_amd64.deb (--unpack):
 trying to overwrite '/usr/include/jerror.h', which is also in package libjpeg-turbo8-dev:amd64 2.0.3-0ubuntu2
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libjpeg62-turbo-dev_1%3a1.5.2-2+deb10u1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
