# Google::ProtocolBuffers::Dynamic not installing ... on Ubuntu (Ubuntu 18.04.5 LTS)

while running the command :

```sh
sudo cpan install Google::ProtocolBuffers::Dynamic
```
I get ...

```
Reading '$HOME/.local/share/.cpan/Metadata'
  Database was generated on Tue, 29 Sep 2020 11:17:03 GMT
Running install for module 'Google::ProtocolBuffers::Dynamic'
CPAN: Digest::SHA loaded ok (v5.96)
CPAN: Compress::Zlib loaded ok (v2.074)
Checksum for $HOME/.local/share/.cpan/sources/authors/id/M/MB/MBARBON/Google-ProtocolBuffers-Dynamic-0.29.tar.gz ok
CPAN: YAML loaded ok (v1.26)
CPAN: CPAN::Meta::Requirements loaded ok (v2.140)
CPAN: Parse::CPAN::Meta loaded ok (v2.150010)
CPAN: CPAN::Meta loaded ok (v2.150010)
CPAN: Module::CoreList loaded ok (v5.20170922_26)
Configuring M/MB/MBARBON/Google-ProtocolBuffers-Dynamic-0.29.tar.gz with Build.PL
Created MYMETA.yml and MYMETA.json
Creating new 'Build' script for 'Google-ProtocolBuffers-Dynamic' version '0.29'
  MBARBON/Google-ProtocolBuffers-Dynamic-0.29.tar.gz
  /usr/bin/perl Build.PL --installdirs site -- OK
Running Build for M/MB/MBARBON/Google-ProtocolBuffers-Dynamic-0.29.tar.gz
Building Google-ProtocolBuffers-Dynamic
Processing XS typemap files...
Generating main XS file...
g++ -I/usr/lib/x86_64-linux-gnu/perl/5.26/CORE -fPIC -xc++ -I/usr/local/share/perl/5.26.1/auto/share/dist/Alien-uPB/include -DNDEBUG -pthread -DPERL_NO_GET_CONTEXT -Isrc -Ibuildtmp -c -D_REENTRANT -D_GNU_SOURCE -DDEBIAN -fwrapv -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2 -g -o src/mapper.o src/mapper.cpp
In file included from src/mapper.cpp:2:0:
src/dynamic.h:6:10: fatal error: google/protobuf/compiler/importer.h: No such file or directory
 #include <google/protobuf/compiler/importer.h>
          ^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
compilation terminated.
error building src/mapper.o from 'src/mapper.cpp' at /usr/local/share/perl/5.26.1/ExtUtils/CBuilder/Base.pm line 185.
  MBARBON/Google-ProtocolBuffers-Dynamic-0.29.tar.gz
  ./Build -- NOT OK
```


## solution

```sh
sudo apt-get update

sudo cpan install Google::ProtocolBuffers::Dynamic
sudo apt-get remove libprotobuf-dev
sudo apt autoremove

sudo aptitude search protobuf-compiler
sudo apt-get install protobuf-compiler
#sudo apt-get remove protobuf-compiler
git clone https://github.com/protocolbuffers/protobuf.git
pwd=$(pwd -P)
sudo apt-get install libprotobuf-dev
cd /usr/include/google/protobuf/
sudo ln -s $pwd/protobuf/src/google/protobuf/compiler compiler
cd $pwd
sudo cpan install Google::ProtocolBuffers::Dynamic

```


### computer info:

```sh
uname -a
Linux localhost 4.15.0-117-generic #118-Ubuntu SMP Fri Sep 4 20:02:41 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
```

#### done on Tue Sep 29 17:23:58 CEST 2020
by michelc (via 37wtmyvnagq2q: aka Letha J. Server)
