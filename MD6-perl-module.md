# MD6 Perl module fail to install (syntax error in : inc/Devel/CheckLib.pm)


### The problem:

when I run ``perl -MCPAN -Mlocal::lib=${PERL5LIB%/lib/perl5} -e "CPAN::install(Digest::MD6)"``
<br>I got this :

```log
Reading '/home/michelc/.cpan/Metadata'
  Database was generated on Tue, 06 Oct 2020 09:17:03 GMT
Running install for module 'Digest::MD6'
Fetching with LWP:
http://www.cpan.org/authors/id/A/AN/ANDYA/Digest-MD6-0.11.tar.gz
Fetching with LWP:
http://www.cpan.org/authors/id/A/AN/ANDYA/CHECKSUMS
Checksum for /home/michelc/.cpan/sources/authors/id/A/AN/ANDYA/Digest-MD6-0.11.tar.gz ok
'YAML' not installed, will not store persistent state
Configuring A/AN/ANDYA/Digest-MD6-0.11.tar.gz with Makefile.PL
"my" variable $mm_attr_key masks earlier declaration in same statement at inc/Devel/CheckLib.pm line 169.
"my" variable $arg masks earlier declaration in same statement at inc/Devel/CheckLib.pm line 177.
"my" variable $arg masks earlier declaration in same statement at inc/Devel/CheckLib.pm line 178.
"my" variable $arg masks earlier declaration in same scope at inc/Devel/CheckLib.pm line 182.
"my" variable %args masks earlier declaration in same scope at inc/Devel/CheckLib.pm line 182.
"my" variable $arg masks earlier declaration in same statement at inc/Devel/CheckLib.pm line 183.
"my" variable $arg masks earlier declaration in same statement at inc/Devel/CheckLib.pm line 184.
syntax error at inc/Devel/CheckLib.pm line 164, near "$mm_attr_key qw(LIBS INC)"
syntax error at inc/Devel/CheckLib.pm line 171, near "}"
Global symbol "%args" requires explicit package name (did you forget to declare "my %args"?) at inc/Devel/CheckLib.pm line 175.
syntax error at inc/Devel/CheckLib.pm line 179, near "}"
syntax error at inc/Devel/CheckLib.pm line 185, near "}"
Can't redeclare "my" in "my" at inc/Devel/CheckLib.pm line 189, near "my"
Global symbol "@headers" requires explicit package name (did you forget to declare "my @headers"?) at inc/Devel/CheckLib.pm line 192.
Global symbol "@libs" requires explicit package name (did you forget to declare "my @libs"?) at inc/Devel/CheckLib.pm line 223.
Global symbol "@libpaths" requires explicit package name (did you forget to declare "my @libpaths"?) at inc/Devel/CheckLib.pm line 230.
Global symbol "@libpaths" requires explicit package name (did you forget to declare "my @libpaths"?) at inc/Devel/CheckLib.pm line 236.
Global symbol "@libpaths" requires explicit package name (did you forget to declare "my @libpaths"?) at inc/Devel/CheckLib.pm line 240.
syntax error at inc/Devel/CheckLib.pm line 252, near "}"
inc/Devel/CheckLib.pm has too many errors.
Compilation failed in require at Makefile.PL line 12.
BEGIN failed--compilation aborted at Makefile.PL line 12.
Warning: No success on command[/usr/bin/perl Makefile.PL INSTALLDIRS=site]
  ANDYA/Digest-MD6-0.11.tar.gz
  /usr/bin/perl Makefile.PL INSTALLDIRS=site -- NOT OK
```

## solution:

```sh
export PERL5LIB=${PERL5LIB:-$HOME/site/lib/perl5}

#go to the cpan/build folder :
cd $(ls -1d ~/.cpan/build/Digest-MD6-0.11-*/ | head -1)
# name inc folder into in_
mv inc in_
perl -MCPAN -Mlocal::lib=${PERL5LIB%/lib/perl5} -e "CPAN::install(Devel::CheckLib)"
perl Makefile.PL
make -f Makefile
make test
sudo make install
```


### Voilà !

by: michelc (via 37wtmyvnagq2q aka Letha J. Serve)
