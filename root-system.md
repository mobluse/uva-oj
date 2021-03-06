# CERN ROOT
You can use [ROOT](https://root.cern.ch/root-user-guides-and-manuals) to develop C++ easily with a
[debugger](https://root.cern.ch/root/html/guides/users-guide/CINT.html#debugging-scripts) and
without crashes by using ROOT from CERN.
In the following you should not type $ in the beginning of a command-line -- it's a prompt.
Install in Debian, Raspbian, Ubuntu, [Ubuntu for Windows 10](https://www.microsoft.com/en-us/store/p/ubuntu/9nblggh4msv6)
etc. using:  
$ sudo apt-get install root-system

$ root #Starts ROOT -- quit using .q

You probably need *[ROOT Primer 5](https://d35c7d8c.web.cern.ch/sites/d35c7d8c.web.cern.ch/files/ROOT5Primer.pdf)* since 
most Linux distributions still ship a version from series 5 even if series 6 is avaible now from CERN. On how to use the debugger
in ROOT series 5, see *[Debugging Scripts](https://root.cern.ch/root/htmldoc/guides/users-guide/CINT.html#debugging-scripts)*.

## Installing ROOT in Elementary OS Luna i.e. Ubuntu 12.04 on x86-32
OS:es for x86-32 often doesn't have ROOT built-in, but you can compile it, but it takes several hours.
Do not use this if you can install ROOT (root-system) via your package manager.

$ wget https://root.cern.ch/download/root_v5.34.36.source.tar.gz

$ sudo apt-get install git dpkg-dev cmake g++ gcc binutils libx11-dev libxpm-dev libxft-dev libxext-dev

$ sudo apt-get install gfortran libssl-dev libpcre3-dev xlibmesa-glu-dev libglew1.5-dev libftgl-dev libmysqlclient-dev \  
libfftw3-dev graphviz-dev libavahi-compat-libdnssd-dev libldap2-dev python-dev libxml2-dev libkrb5-dev libgsl0-dev \  
libqt4-dev  

$ sudo apt-get install libcfitsio-dev  
#This is part of the optional packages, but it doesn't exist in this OS, but compiling works anyway.  
#E: Package 'libcfitsio-dev' has no installation candidate  
#You will probably need to install more packages, and need to google error messages during configure or make to find which.

$ tar -xzvpf root_v5.34.36.source.tar.gz

$ cd root

$ WHERE_TO_INSTALL_ROOT=/usr/local

$ export XPM=/usr/lib/i386-linux-gnu/

$ ./configure linux --with-x11-libdir=/usr/lib/i386-linux-gnu --with-xft-libdir=/usr/lib/i386-linux-gnu \  
--with-xext-libdir=/usr/lib/i386-linux-gnu --with-xrootd-libdir=/usr/lib/i386-linux-gnu --disable-asimage \  
--prefix=$WHERE_TO_INSTALL_ROOT

$ sudo make #Maybe sudo is not needed here.

$ sudo apt-get install checkinstall

$ sudo checkinstall --pkgname=root-framework --fstrans=no --strip=no make install
#You must enter version.

$ cd $WHERE_TO_INSTALL_ROOT

$ source bin/thisroot.sh

$ root # ROOT should start, exit with .q

I use Elementary OS Luna (Ubuntu 12.04) on a 9" screen Eee PC 900 with x86 32-bit processor.
I might upgrade to Elementary OS Freya (Ubuntu 14.04), but that is the last Elementary OS for x86 32 bits.

## References
https://askubuntu.com/questions/39363/how-do-i-install-root-cern  
https://github.com/zoglauer/megalib/issues/4  
https://root-forum.cern.ch/t/xpm-headers/11650/2  
