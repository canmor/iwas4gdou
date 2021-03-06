iwas4gdou 0.1 (2010/09/10)
Copyright (C) 2010 Cammor Lam.


Description
-----------

iwas4gdou is an IEEE802.1x wired authentication (EAP over Ethernet II) supplicant, especially for GDOU (Guangdong Ocean University). It's licensed under the GNU GPL, included in the file COPYING.


Installation
------------

First at all, iwas4gdou is base on `libpcap`, please make sure you have installed libpcap on your machine.

Run following command:

    $ make

If it succeeds, run following command with root permission:

    # make install

That's all, if it still doesn't work, please mail to me.


Uninstallation
--------------

Run following command with root permission:

    # make uninstall


Usage
-----

Cause there are many different DHCP clients of Linux, iwas4gdou just have a function to authenticate. 

### Sample:

If you want to perform authentication on interface named "eth0", and "username" and "password" is your username and password, you should run this(with root permission):

    # iwas4gdou -ar -i eth0 -u username -p password

As we know, use `-p password` to specify your password is not save enough, you may rather do like this:

    # iwas4gdou -ar -i eth0 -u username

Application will promts you to give a password without echoing password character.

If you want to quit from authenticated, you should run this:

    # iwas4gdou -d -i eth0

For more usage and information you could run `man iwas4gdou`.

Note: After authentication succeeds, you should lease IP address by you self. Unfortunately, the compatibility of DHCP server in GDOU (Guangdong Ocean University) is not good enough at the moment. You may couldn't lease any IP address by using `dhclient` or others of DHCP client. If this happen to `dhclient`, please edit configuration file `dhclient.conf` (default location is `/etc/dhcp/dhclient.conf`, create it if not existing) like this:

    # eth0 is your interface name
    interface "eth0" { 
        # this value is "1:" concats with interface HWaddr 
        send dhcp-client-identifier 1:00:e0:4c:4d:2f:34;
    }

More help could be found in the manuals of DHCP client (`man dhclient`, `man dhclient.conf`). If it still doesn't work, please mail to me.


Bugs and Advices
----------------

There probably are some bugs I don't known what they are yet, any bugs and advices could be reported to <canmor.lam@gmail.com>, thanks.
