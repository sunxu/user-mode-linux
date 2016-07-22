user mode linux
========

## Install

    wget https://github.com/sunxu/vde2-2.3.2/archive/master.zip
    ./configure && make && sudo make install

    wget https://github.com/sunxu/linux-4.4/archive/master.zip
    make ARCH=um defconfig
    ./scripts/kconfig/merge_config.sh -m .config ../um_defconfig
    sed -i "s/-lutil -lrt/-lutil -lrt -lpthread/g" scripts/link-vmlinux.sh
    LIBRARY_PATH=/usr/local/lib make ARCH=um V=1 -j 4


## Run

    ./startup


## GDB

    echo "set auto-load safe-path /" >> ~/.gdbinit
    yum -y install yum-utils
    debuginfo-install -y glibc-2.17-105.el7.x86_64
    gdb -p `pgrep linux | head -n 1`


## License

```text
            DO WHAT THE FUCK YOU WANT TO PUBLIC LICENSE
                    Version 2, December 2004

 Copyright (C) 2004 Sam Hocevar <sam@hocevar.net>

 Everyone is permitted to copy and distribute verbatim or modified
 copies of this license document, and changing it is allowed as long
 as the name is changed.

            DO WHAT THE FUCK YOU WANT TO PUBLIC LICENSE
   TERMS AND CONDITIONS FOR COPYING, DISTRIBUTION AND MODIFICATION

  0. You just DO WHAT THE FUCK YOU WANT TO.
```


## References

* [User-Mode Linux](http://user-mode-linux.sourceforge.net/)
* [VDE - Virtual Distributed Ethernet](http://vde.sourceforge.net/)
* [Network lab with User Mode Linux](https://vincent.bernat.im/en/blog/2011-uml-network-lab.html)

