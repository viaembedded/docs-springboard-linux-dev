.. _bsp:

Building BSP
============

Building kernel
---------------
This section will tell you how to build kernel image from source code.
To use BSP package without spending too much time on building source
code, there is a pre-build kernel image located under ``EVK\Kernel_Image\``.

Setup the kernel source
^^^^^^^^^^^^^^^^^^^^^^^

Unzip the Kernel source::
  tar -zxvf Linux_BSP_Kernel_Source_0.03.tar.gz

Then the kernel source will be located at ``Linux_BSP_Kernel_Source_0.02.tar.gz``. 
The ``ANDROID_3.0.8`` directory contains the source code.

Copy all the files under the sub-folder ``\BSP\Frame_Buffer_Driver\ANDROID_3.0.8_VE\``
to your corresponding kernel tree folder and start to build the Linux kernel.

Build 3.0.8 kernel source
^^^^^^^^^^^^^^^^^^^^^^^^^

**How to build 3.0.8 kernel source**

To use the default configurations, type the following command::

  make VAB-600_Linux_defconfig

If there is no ``VAB-600_Linux_defconfig``, copy it from
``/BSP/Kernel_Source_Codes/`` to ``${Kernel_Source}/arch/arm/configs/``

To modify the unique configurations, input this to enter the menu with the 
graphic user interface::

  make menuconfig

After selecting particular options, now it is time to build the kernel image::

  make ubin CROSS_COMPILE=arm_1103_le- -jX

X is the number threads to build the kernel image, depend on the efficiency of your
host PC. Generally choose twice the number of the available CPU cores. For
example, a quad-core CPU should sustain ``-j8``.

As shown in :num:`Figure #figure-kernel`, it takes a few minutes to get the kernel image,
uzImage.bin.

.. _figure-kernel:
.. figure:: images/kernel.*
   :align: center
   :alt: Building the kernel

   Building the kernel

The ``uzImage.bin`` is located at ``ANDROID_3.0.8``.

**How to make clean the kernel source**

Clean the kernel source and it will clean all the built binaries
in ``ANDROID_3.0.8``::

  make clean
