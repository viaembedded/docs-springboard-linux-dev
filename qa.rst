.. _qa:

Appendix A. Q&A
===============

**Q**: When trying to setup static IP address in "Network Connections", the IP
setup does not take effect.

**A**: After setting "Network Connections", user should open a console to shut
down the Ethernet adapter and then turn on by following the command
below, target Ethernet adapter is eth1::

  ifconfig eth1 down
  ifconfig eth1 up
