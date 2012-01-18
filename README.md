# What is this spec?

Forked from imeyer's ruby-1.9.2-rpm project at https://github.com/imeyer/ruby-1.9.2-rpm and updated for 1.9.3.

This spec is an attempt to push for a stable replacement of Ruby 1.8.x with 1.9.2+ on RHEL based systems. The original author based it off of the work of [FrameOS](http://www.frameos.org) specs for Ruby 1.9.2 and Ruby Enterprise Edition.

### How to install

#### RHEL/CentOS 5/6

    yum install -y rpm-build rpmdevtools
    rpmdev-setuptree
    cd ~/rpmbuild/SOURCES
    wget http://ftp.ruby-lang.org/pub/ruby/1.9/ruby-1.9.3-p0.tar.gz
    cd ~/rpmbuild/SPECS
    curl https://raw.github.com/lnxchk/ruby-1.9.3-rpm/master/ruby193.spec > ruby193.spec
    rpmbuild -bb ruby193.spec
    rpm -Uvh ~/rpmbuild/RPMS/x86_64/ruby-1.9.3p0-1.${ARCH}.rpm

#### Amazon 64-bit Linux AMIs (as of Jan 2012)


    ##### Build tools
    yum install -y gcc gcc-c++ make automake autoconf 

    ##### Ruby building prereqs
    yum install -y readline-devel ncurses-devel gdbm-devel glibc-devel tcl-devel openssl-devel db4-devel byacc libyaml-devel

    ##### RPM building
    yum install -y rpm-build rpmdevtools
    rpmdev-setuptree
    cd rpmbuild/SOURCES
    wget http://ftp.ruby-lang.org/pub/ruby/1.9/ruby-1.9.3-p0.tar.gz
    cd ../SPECS
    curl https://raw.github.com/lnxchk/ruby-1.9.3-rpm/master/ruby193.spec > ruby193.spec
    rpmbuild -bb ruby193.spec
    rpm -Uvh ../RPMS/x86_64/ruby-1.9.3p0-1.amzn1.${ARCH}.rpm

### What it does

+ Builds
+ Installs
+ Overwrites/upgrades your currently installed ruby package (**DANGEROUS**)
+ Includes rubygems

### What it does **not** do

+ Split packages into ruby-libs, ruby-devel, etc (looking for help here)
+ Install alongside Ruby 1.8.x

### Distro support

Tested upstream working on:

* RHEL 5.6 x86_64
* RHEL 6 x86_64
* RHEL 6.1 x86_64
* RHEL 6.1 i686
* CentOS 5.6 x86_64

* I (lnxchk) have some pre-built rpms for aws amis as of 2011.09 release at http://treble.rwe40.net:8088/amzn

