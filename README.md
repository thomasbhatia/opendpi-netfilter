This package is a GPL implementation of an iptables and netfilter module for
OpenDPI integration into the Linux kernel.

The prerequisites are:

- Tested on Ubuntu 16.04.4 LTS (Kernel 4.4.0)
- Following packages to compile kernel-modules:
   linux-headers
   iptables-dev >= version 1.4.8-3
   OpenDPI source package (you can get it from https://github.com/thomasbhatia/OpenDPI)


Compiled kernel features
------------------------

To install the modules follow these steps:

 - Enter OpenDPI source package folder:

        cd [path]/OpenDPI

 - Git clone:

        git clone https://github.com/thomasbhatia/opendpi-netfilter.git


 - Enter the opendpi-netfilter folder:

        cd opendpi-netfilter

 - Run Make:

        make

- Then install:

        sudo make install



Now you can read the following section to learn how to use it.


Module usage
------------

Once you have installed both modules ("libxt_opendpi.so" and "xt_opendpi.ko")
you should type (as root):

        modprobe xt_opendpi

If the module has been successfully loaded you shouldn't see any message.
After loading the kernel module you can use iptables to add a rule. To see
available protocols you can match for in every packet, type (as root):

        iptables -m opendpi --help

Note that the list is long, you best try: "iptables -m opendpi --help | more"

An example rule would be (as root):

        iptables -A OUTPUT -m opendpi --http -j REJECT

This wouldn't allow any HTTP traffic that originates from the machine where the
rule was added.

In case you want to stop using the OpenDPI kernel module, first remove every
iptables rule for OpenDPI and then type (as root):

        modprobe -r xt_opendpi

