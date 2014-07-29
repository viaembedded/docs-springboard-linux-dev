.. _debug:

Debug Message
=============

VAB-600 Linux BSP supports debugging with RS232 port.
The RS232 client software (such as putty) should configure the parameters
as follows::

  COM speed：115200
  COM parity： NONE
  COM data： 8
  COM stop-bit：1

Use `picocom` or another terminal emulator on the HOST PC to open the console::

  picocom -b 115200 /dev/ttyS0

If the picocom is not installed, use apt-get to install it::

  apt-get install picocom

After successfully connecting to VAB-600 through RS232 line, you can
enter the u-boot console and try modifying the u-boot parameters for
various configurations, such as changing display resolution and so on.

Enter U-Boot environment
------------------------

VAB-600 Linux platform can stop booting to enter u-boot environment. The
u-boot will initiate hardware at an earlier stage by those parameters.

The u-boot will wait 3 seconds to stop booting after power on by pressing
any key. When booting comes to a halt, the sign ``WMT #`` will pop up on
terminal screen.

U-Boot is similar to a tiny operation system that has its own commands.
Some important commands and parameters are described here.

Print online help::

  WMT # help

Change display U-boot logo resolution::

  WMT # setenv wmt.display.param 4:6:1:1280:1024:60

Save changed parameters::

  WMT # saveenv

Default u-boot parameters
-------------------------
The default u-boot parameters are configured in the following file::

  /update_package/bspinst/bspinst.cfg

The ``bspinst.cfg`` file structure has four segments:

1. Scenario: board model and boot method
2. Common: general setting
3. Target (board models): specific setting for each target
4. Routine: parameters of boot method

Its content will be parsed and stored into the on-board storage device
during installation procedure described in :ref:`emmc-boot`.
