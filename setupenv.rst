.. _setupenv:

Setup Environment
=================

System requirement
------------------

**Host PC**

SD Card reader: SDHC compliant

Operation System: Ubuntu 10.04 x64 version

**Target board**

VAB-600 platform (with 4G EMMC)

SD Card: 4GB SDHC (at least). VAB-600 now supports up to class 6 SDHC.

Setup cross-compiling environment
---------------------------------

In the following command examples ``#`` denotes the system shell prompt,
do not include that in the commands given.

**Get root permission**

If you are not login as a root, use ``su`` command to get the root permission.

**Setup the Tool Chain**

Please reference 4.2.1 to connect to network. Then perform the packages
update::

  apt-get update

Install the build essential packages::

  apt-get install git-core gnupg flex bison gperf build-essential \
          zip curl zlib1g-dev libc6-dev lib32ncurses5-dev ia32-libs \
          x11proto-core-dev libx11-dev lib32readline5-dev lib32z-dev \
          libgl1-mesa-dev g++-multilib mingw32 tofrodos python-markdown \
          libxml2-utils xsltproc

Install the uboot mkimage tool::

  apt-get install uboot-mkimage

Confirm if the GNU C library version is 2.11 or newer::

  # ldd -version
  ldd (Ubuntu EGLIBC 2.1.11-0ubuntu7.11) 2.11.1
  Copyright (C) 2009 Free Software Foundation, Inc.
  This is free software; see the source for copying conditions. There is NO
  warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
  Written by Roland McGrath and Ulrich Drepper.

Unzip the Tool Chain to ``/usr/local/arm/`` (If your system doesn’t exist this
folder previously, you must create manually with ``mkdir /usr/local/arm``)::

  tar -zxvf arm_201103_gcc4.5.2.tgz -C /usr/local/arm/

As :num:`Figure #figure-toolchain` shows, the cross compiler is located at ``/usr/local/arm/arm_201103_gcc4.5.2/``.

.. _figure-toolchain:
.. figure:: images/toolchain.*
   :align: center
   :alt: The Toolchain for VAB-600

   The Toolchain for VAB-600

Export the Tool Chain to system PATH::

  export PATH=/usr/local/arm/arm_201103_gcc4.5.2/mybin/:$PATH

Next, alias the Tool Chain for best floats calculation::

  alias arm_1103_le-as='arm_1103_le-as -mcpu=cortex-a9 -mfpu=neon -mfloatabi=softfp'
  alias arm_1103_le-c++='arm_1103_le-c++ -mcpu=cortex-a9 -mfpu=neon -mfloatabi=softfp'
  alias arm_1103_le-cpp='arm_1103_le-cpp -mcpu=cortex-a9 -mfpu=neon -mfloatabi=softfp'
  alias arm_1103_le-g++='arm_1103_le-g++ -mcpu=cortex-a9 -mfpu=neon -mfloatabi=softfp'
  alias arm_1103_le-gcc='arm_1103_le-gcc -mcpu=cortex-a9 -mfpu=neon -mfloatabi=softfp'
  alias arm_1103_le-gcc-4.5.2='arm_1103_le-gcc-4.5.2 -mcpu=cortex-a9 -mfpu=neon -mfloat-abi=softfp'
