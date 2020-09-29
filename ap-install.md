# Alien::ProtoBuf not installing ... on Ubuntu (Ubuntu 18.04.5 LTS)

while running the command :

```sh
sudo cpan install Alien::ProtoBuf
```
I get ...

```
Reading '$HOME/.local/share/.cpan/Metadata'
  Database was generated on Tue, 29 Sep 2020 11:17:03 GMT
Running install for module 'Alien::ProtoBuf'
CPAN: Digest::SHA loaded ok (v5.96)
CPAN: Compress::Zlib loaded ok (v2.074)
Checksum for $HOME/.local/share/.cpan/sources/authors/id/M/MB/MBARBON/Alien-ProtoBuf-0.09.tar.gz ok
CPAN: YAML loaded ok (v1.26)
CPAN: CPAN::Meta::Requirements loaded ok (v2.140)
CPAN: Parse::CPAN::Meta loaded ok (v2.150010)
CPAN: CPAN::Meta loaded ok (v2.150010)
CPAN: Module::CoreList loaded ok (v5.20170922_26)
Configuring M/MB/MBARBON/Alien-ProtoBuf-0.09.tar.gz with Build.PL
+ pkg-config --modversion protobuf
+ pkg-config --modversion protobuf
Could not find an installed protobuf library at inc/AP/Build.pm line 19.
No 'Build' created  MBARBON/Alien-ProtoBuf-0.09.tar.gz
  /usr/bin/perl Build.PL --installdirs site -- NOT OK
```


## solution

```sh
sudo apt autoremove
sudo apt-get update
sudo aptitude search protobuf
sudo apt-get install libprotobuf-dev
sudo cpan install Alien::ProtoBuf

```


### computer info:

```sh
uname -a
Linux localhost 4.15.0-117-generic #118-Ubuntu SMP Fri Sep 4 20:02:41 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
```


#### done on Tue Sep 29 14:32:28 CEST 2020
by michelc (via 37wtmyvnagq2q: aka Letha J. Server)
