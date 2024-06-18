# Index for troubleshooting

- [3D View](#3D-View)
- [Crash](#Crash)
- [Index](#Index)
- [Python](#Python)
- [Recover](#Recover)
- [Startup](#Startup)
- [Index](#Index)
- [Amd](#Amd)
- [Common](#Common)
- [Intel](#Intel)
- [Nvidia](#Nvidia)
- [Other](#Other)
- [Introduction](#Introduction)
- [Laptops](#Laptops)
- [Other](#Other)
- [Amd](#Amd)
- [Intel](#Intel)
- [Nvidia](#Nvidia)
- [Other](#Other)
- [Amd](#Amd)
- [Intel](#Intel)
- [Nvidia](#Nvidia)
- [Other](#Other)


## 3D View


***********
3D Viewport
***********

Rendering
=========

.. _troubleshooting-depth:

Depth Buffer Glitches
---------------------

Sometimes when setting a large :ref:`clipping range <bpy.types.SpaceView3D.clip_start>`
will allow you to see both near and far objects,
but reduces the depth precision resulting in artifacts.

.. list-table::

   * - .. figure:: /images/troubleshooting_3d-view_graphics-z-fighting-none.png
          :width: 200px

          Model with no clipping artifacts.

     - .. figure:: /images/troubleshooting_3d-view_graphics-z-fighting-example.png
          :width: 200px

          Model with clipping artifacts.

     - .. figure:: /images/troubleshooting_3d-view_graphics-z-fighting-example-editmode.png
          :width: 200px

          Mesh with artifacts in Edit Mode.

To avoid this:

- Increase the near clipping when working on large scenes.
- Decrease the far clipping when objects are not viewed at a distance.

When perspective is disabled only the far Clip End is used, very high values can still result in artifacts.
This is **not** specific to Blender, all graphics applications have these same limitations.


Objects Invisible in Camera View
--------------------------------

If you have a large scene, viewing it through Camera View may not display all of the objects in the scene.
One possibility may be that the :ref:`clipping distance <camera-clipping>` of the camera is too low.
The camera will only show objects that fall within the clipping range.


Performance
===========

Slow Rendering
--------------

There are a couple of reasons why you may be experiencing a slow viewport.

Old Hardware
   Sometimes your hardware, mainly your graphics card, may be too slow to keep up with your model.
Upgrade Graphics Driver
   In some cases, slow selection is resolved by using updated drivers.


Slow Selection
--------------

Blender uses OpenGL for selection, some graphics card drivers are slow at performing this operation.

This becomes especially problematic on dense geometry.

Possible Solutions:

GPU Depth Picking (Preferences)
   See :menuselection:`Preferences --> Viewport --> Selection`.

   This option is enabled by default, disabling it may give a better performance at
   the cost of selection accuracy.
Upgrade Graphics Driver
   In some cases, slow selection is resolved by using updated drivers.
   *It is generally good to use recent drivers when using 3D software.*
Select Centers (Workaround)
   In *Object Mode*, holding :kbd:`Ctrl` while selecting uses the object center point.
   While this can be useful on its own, it has the side effect of not relying on OpenGL selection.
Change Display Mode (Workaround)
   Using *Wireframe* display mode can be used to more quickly select different objects.

.. note::

   Obviously, the workarounds listed here are not long term solutions,
   but it is handy to know if you are stuck using a system with poor OpenGL support.

   Ultimately, if none of these options work out it may be worth upgrading your hardware.


.. _troubleshooting-fps_limit:

Viewport Playback Frame Rate Limited
------------------------------------

Having the viewport playback clamped to a maximum of 60 FPS is typically caused by the VSYNC setting on your GPU,
for higher frame rates you may have to disable VSYNC functionality although this may be of limited us since
frames rendered may be more than your GPU and monitor are able to display.

VSYNC is configured as part of your GPU driver options which vary depending on your system & GPU combination.


Navigation
==========

Lost in Space
-------------

When navigating your scene, you may accidentally navigate away from your scene
and find yourself with a blank viewport. There are two ways to fix this:

#. Select an object in the :doc:`Outliner </editors/outliner/index>`,
   then zoom to that object with :menuselection:`View --> Frame Selected` or :kbd:`NumpadPeriod`.
#. Use :kbd:`Home` to fit all objects into the 3D Viewport.


Invisible Limit Zooming In
--------------------------

Sometimes when navigating you may be trying to zoom in but it seems that you have hit a limit
to how far you can zoom.
This is because Blender uses a central point to orbit around.

In practice this is good for modeling an object which you rotate about a lot to see from all sides
(think of a potter using a wheel).
However, this makes it awkward to explore a scene or model an object from the 'inside', for example.


Solutions
^^^^^^^^^

- Use :ref:`View Dolly <bpy.ops.view3d.dolly>`.
- Use :ref:`Walk/Fly Navigation <3dview-fly-walk>`.
- Use :ref:`Auto Depth <bpy.types.PreferencesInput.use_mouse_depth_navigate>`
  and :ref:`Zoom to Mouse Position <bpy.types.PreferencesInput.use_zoom_to_mouse>`.
  These tools will make sure the distance is always the value under the mouse cursor,
- Use :ref:`bpy.ops.view3d.zoom_border` as it also resets the center point when zooming.
- Center the view around the mouse cursor :kbd:`Alt-MMB`.
  This will take the position under the cursor and make it your viewpoint center.
- Use an :abbr:`NDOF (N-Degrees of Freedom)`, also known as a 3D mouse,
  see :ref:`configuring peripherals <hardware-ndof>` for more information.


Tools
=====

.. _troubleshooting-3dview-invalid-selection:

Invalid Selection
-----------------

There are times when selection fails under some configurations,
often this is noticeable in mesh *Edit Mode*,
selecting vertices/edges/faces where random elements are selected.

Internally Blender uses :term:`OpenGL` for selection,
so the graphics card driver relies on giving correct results.

Possible Solutions:

Disable :term:`Multisampling`
   This is by far the most common cause of selection issues.

   There are known problems with some graphics cards when using multisampling.

   You can disable this option by turning multisampling off in your graphics card driver options.

Change Anti-Aliasing Sample Settings
   Depending on your OpenGL configuration,
   some specific sample settings may work while others fail.

   Unfortunately finding working configuration involves trial & error testing.
Upgrade Graphics Driver
   As with any OpenGL-related issues, using recent drivers can resolve problems.

   However, it should be noted that this is a fairly common problem and remains unresolved with many drivers.


## Crash


*******
Crashes
*******

The most common causes of Blender crashes:

- Running out of memory.
- Issues with graphics hardware or drivers.
- Bugs in Blender.

Firstly, you may be able to recover your work with :menuselection:`File --> Recover --> Auto Save...`.

To prevent the problem from happening again, you can check that the graphics drivers are up to date
(:ref:`troubleshooting-gpu-index`), upgrade your machine's hardware (the RAM or graphics card),
and disable some options that are more memory intensive:

- Reduce undo steps
  :menuselection:`Preferences --> System --> Memory & Limits --> Undo Steps`.
- Using multisample anti-aliasing also increases the memory usage and makes the display slower.
- On Linux, the Window Manager (KDE and Gnome for example) may be using hardware accelerated effects
  (e.g. window shadows and transparency) that are using up the memory that Blender needs.
  Try disabling the desktop effects or switch to a lightweight Window Manager.

To check memory usage by Blender:

- On Windows, use Task Manager and sort by Memory.
- On macOS, use Activity Monitor.app and open Memory tab. Alternatively, run ``top -o MEM``.
- On Linux, run ``top -o %MEM``.


Crash Log
=========

When Blender crashes, it writes out a text file which contains information that may help
identify the cause of the crash. Usually, this file is written in the :ref:`temp-dir` directory.

This file contains a log of tools used up until the crash as well as some other debug information.
When reporting bugs about crashes it can be helpful to attach this file to your reports,
especially when others are unable to reproduce the crash.


Windows
-------

On a crash, a file is written based on the name of the currently loaded blend-file,
so ``test.blend`` will create a file called ``test.crash.txt``.

Batch scripts are provided in Blender installation directory which may be run to obtain
the Blender debug log and system info text files:

- ``blender_debug_log.cmd`` is used in most cases.
- ``blender_debug_gpu.cmd`` and ``blender_debug_gpu_workaround.cmd`` log GPU-related errors.
- ``blender_factory_startup.cmd`` starts Blender with default settings which is recommended for debugging.

If the crash happens in Blender module, stack trace is also written to a file named ``blender.crash.txt``.
The path to that file can be found at the end of ``blender_debug_log.txt`` file.


macOS
-----

After crash, macOS Crash Reporter shows a window with backtrace after some time, or when Blender
is opened again. Copy the text in the crash report and save it in a text file. That file should be attached
to the bug report while following other bug reporting guidelines.

Some ``.crash`` files can also be found in ``~/Library/Logs/DiagnosticReports/`` with the name of format:
``Blender_YYYY-MM-DD-HHMMSS_MACNAME.crash``. If a report is present corresponding to the time of crash,
that file can also provide hints about cause of the crash. Alternatively, Console.app can be used to
navigate all "User Reports" (see sidebar in the app).


Linux
-----

On a crash, a file named ``blender.crash.txt`` is written in ``/tmp`` directory.

.. note::

   More logs can be obtained by running Blender from Command Line and using ``--factory-startup --debug-all`` flags.
   See :ref:`command_line-launch-index` and :ref:`command_line-args`.


## Index

.. _troubleshooting-index:

###################
  Troubleshooting
###################

.. toctree::
   :maxdepth: 1

   startup.rst
   3d_view.rst
   gpu/index.rst
   crash.rst
   python.rst
   recover.rst


Compatibility
=============

Some applications which integrate themselves into your system can cause problem's with Blender.

Here is a list of `known compatibility issues <https://wiki.blender.org/wiki/Reference/Compatibility>`__.


## Python


*************
Python Errors
*************

Precompiled Libraries
=====================

While not common practice, Python add-ons can be distributed with their own precompiled libraries.
Unlike regular Python scripts, these are not portable between different platforms.

It is possible the library is incompatible with your Blender installation
(attempting to load a library built for a different version of Python,
or loading a 32-bit library on a 64-bit system).

If the add-on contains ``.pyd`` or ``.so`` files,
check that the distribution is compatible with your operating system.


Platform Specific
=================

Windows
-------

Mixed Python Libraries (DLLs)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

If Python is raising errors or you have an add-on that just fails when enabled with an error, e.g:
``... is not a valid Win32 application.``.

.. figure:: /images/troubleshooting_python_traceback.png

   A Python traceback.

This may be caused by some inconsistency in the Python libraries.
While Blender comes with its own bundled Python interpreter, duplicate, incompatible libraries can cause problems.

To find out which Python Library caused the Problem check the error message.

This is normally reported somewhere around the bottom line of the traceback.
With the error above you see the problem is caused while trying to import ``_socket``.
This corresponds to either a file named ``_socket.py`` or ``_socket.pyd``.

To help troubleshoot this problem,
the following script can be pasted into the Text editor and run to check for duplicate libraries in your search path.
(The output will show in :doc:`Command Line Window </advanced/command_line/index>`.)

.. code-block:: python

   import os
   import sys

   # Change this based on the library you wish to test
   test_lib = "_socket.pyd"

   def GetSystemDirectory():
       from ctypes import windll, create_string_buffer, sizeof
       GetSystemDirectory = windll.kernel32.GetSystemDirectoryA
       buffer = create_string_buffer(260)
       GetSystemDirectory(buffer, sizeof(buffer))
       return os.fsdecode(buffer.value)

   def library_search_paths():
       return (
           # Windows search paths
           os.path.dirname(sys.argv[0]),
           os.getcwd(),
           GetSystemDirectory(),
           os.environ["WINDIR"],  # GetWindowsDirectory
           *os.environ["PATH"].split(";"),

           # regular Python search paths
           *sys.path,
           )

   def check_library_duplicate(libname):
       paths = [p for p in library_search_paths()
                if os.path.exists(os.path.join(p, libname))]

       print("Library %r found in %d locations:" % (libname, len(paths)))
       for p in paths:
           print("- %r" % p)

   check_library_duplicate(test_lib)


## Recover


***************
Recovering Data
***************

Computer crashes, power outages, or simply forgetting to save can result in
the loss or corruption of your work. You can use Blender's *Auto Save* feature
to reduce the chance of losing files when such events occur.

There are options to save a backup of your files like
*Auto Save* that saves your file automatically over time, and *Save on Quit*,
which saves your blend-file automatically when you exit Blender.
In addition to these functions being enabled by default,
the *Save on Quit* functionality cannot be disabled.

.. note::

   For your actions, there are options like *Undo*, *Redo* and an *Undo History*,
   used to roll back from mistakes under normal operation, or return back to a specific action.
   See :doc:`/interface/undo_redo`.


.. _troubleshooting-file_recovery-save_versions:

Recovering Save Versions
========================

By default Blender keeps an additional backup when saving files.
So saving renames the previously saved file with a ``.blend1`` extension instead of overwriting it.

This file can be used to revert to a previous state.

See :ref:`Save Versions <bpy.types.PreferencesFilePaths.save_version>`
to configure the number of versions kept.


.. _troubleshooting-file_recovery-auto_save:

Recovering Auto Saves
=====================

Last Session
------------

.. reference::

   :Menu:      :menuselection:`File --> Recover --> Last Session`

The *Recover Last Session* will open the ``quit.blend`` file
that is saved into the :ref:`temp-dir` when you quit Blender under normal operation (see
:term:`Blender Session`). Note that files in your temporary directory may be deleted when you reboot
your computer (depending on your system configuration).


Auto Save
---------

.. reference::

   :Menu:      :menuselection:`File --> Recover --> Auto Save`

The *Recover Auto Save* allows you to open the *Auto Saved* file.
You will have to navigate to your :ref:`temp-dir`.
The *Auto Saved* files are named using a random number and have a blend extension.

See :ref:`Auto Save Preferences <bpy.types.PreferencesFilePaths.use_auto_save_temporary_files>`
to configure auto-save.

Trusted Source
   When enabled, Python scripts and drivers that may be included in the file will be run automatically.
   Enable this only if you created the file yourself,
   or you trust that the person who gave it to you did not include any malicious code with it.
   See :doc:`Python Security </advanced/scripting/security>` to configure default trust options.

.. tip::

   Enable the detailed list view when browsing auto-saved files to show which is the most recent.

   .. figure:: /images/troubleshooting_recover_display-file-date.png

      File Browser displaying a vertical list.

.. warning::

   When recovering an *Auto Saved* file, any changes made since the last *Auto Save* will be lost.
   Only one *Auto Saved* file exists for each ``.blend`` file, i.e. Blender does not keep older versions.
   Therefore, you will only be able to restore the most recent *Auto Save* file.


## Startup


*******
Startup
*******

Blender
=======

There are some common causes for problems when using Blender. If you cannot find a solution to your problem here,
try asking the :doc:`community </getting_started/about/community>` for help.

If Blender crashes on startup, there are a few things to check for:

- See if your computer meets the `minimum requirements <https://www.blender.org/download/requirements/>`__.
- Confirm that your graphics card is supported and that the drivers are up to date.

Known causes listed below.


Common Startup Messages
=======================

The *Blender Console Window* can display many different types of status and error messages.
Some messages simply inform the user what Blender is doing, but have no real impact on Blender's ability to function.
Other messages can indicate serious errors that will most likely prevent Blender carrying out a particular task and
may even make Blender non-responsive or shut down completely. The *Blender Console Window* messages can
also originate internally from within the Blender code or from external sources such as
:doc:`Python scripts </editors/preferences/extensions>`.

``found bundled python: {DIR}``
   This message indicates that Blender was able to find the :ref:`Python <scripting-index>`
   library for the Python interpreter embedded within Blender.
   If this folder is missing or unable to be found,
   it is likely that an error will occur, and this message will not appear.

``Read prefs: {DIR}/userpref.blend``
   The preferences use this path.


## Index

.. _troubleshooting-gpu-index:

#####################
  Graphics Hardware
#####################

.. include:: common/introduction.rst
   :start-line: 1


Windows
=======

.. toctree::
   :maxdepth: 1

   windows/nvidia.rst
   windows/amd.rst
   windows/intel.rst
   windows/other.rst


Linux
=====

.. toctree::
   :maxdepth: 1

   linux/nvidia.rst
   linux/amd.rst
   linux/intel.rst
   linux/other.rst


macOS
=====

.. toctree::
   :maxdepth: 1

   apple/nvidia.rst
   apple/amd.rst
   apple/intel.rst
   apple/other.rst


## Amd


************
macOS -- AMD
************

.. include:: ../common/introduction.rst
   :start-line: 1
.. include:: common.rst
   :start-line: 1
.. include:: ../common/other.rst
   :start-line: 1


## Common

:orphan:

On macOS graphics drivers are built into the operating system and
the only way to get newer drivers is to upgrade macOS as a whole to the latest version.


## Intel


**************
macOS -- Intel
**************

.. include:: ../common/introduction.rst
   :start-line: 1
.. include:: common.rst
   :start-line: 1
.. include:: ../common/other.rst
   :start-line: 1


## Nvidia


***************
macOS -- Nvidia
***************

.. include:: ../common/introduction.rst
   :start-line: 1
.. include:: common.rst
   :start-line: 1
.. include:: ../common/other.rst
   :start-line: 1


## Other


******************
macOS -- Other GPU
******************

.. include:: ../common/introduction.rst
   :start-line: 1
.. include:: common.rst
   :start-line: 1
.. include:: ../common/other.rst
   :start-line: 1


## Introduction

:orphan:

Blender uses of OpenGL for the 3D Viewport and user interface.
The graphics card (GPU) and driver have a big impact on Blender's behavior and performance.

This section lists possible solutions for graphics glitches, problems with EEVEE and Cycles,
and crashes related to your GPU.


Drivers
=======

Upgrading to the latest graphics drivers often solves problems.
Newer drivers have bug fixes that help Blender function correctly.


## Laptops

:orphan:

Laptops
=======

Laptops often have two GPUs for power saving purposes.
One slower onboard GPU (typically Intel) and one faster dedicated GPU for a better performance (AMD or Nvidia).

For the best performance the dedicated GPU should be used for Blender.
Which GPU to use for which application can be configured in your graphics driver settings.

If there is a graphics glitch or crash specific to the onboard GPU, then using the dedicated GPU can help avoid that.
Or vice versa, if the dedicated GPU causes issues, then using the onboard graphics can help.


## Other

:orphan:

Common Problems
===============

Unsupported Graphics Driver Error
---------------------------------

This means your graphics card and driver do not have the minimum required OpenGL 3.3 version needed by Blender.

Installing the latest driver can help upgrade the OpenGL version,
though some graphics cards are simply too old to run the latest Blender.
Using Blender 2.79 or earlier is the only option then.


Crash on Startup
----------------

Try running Blender from the :doc:`command line </advanced/command_line/index>`,
to see if any helpful error messages are printed.

On Windows, graphics drivers can sometimes get corrupted.
In this case it can help to uninstall all graphics drivers (there may be multiple from Intel, AMD and Nvidia) and
perform a clean installation with drivers from the manufacturer's website.


Poor Performance
----------------

- Update your graphics drivers (see above).
- On laptops, make sure you are using a dedicated GPU (see above).
- Try lowering quality settings in :menuselection:`Preferences --> System --> Memory & Limits`.
- Try undoing settings in your graphics drivers, if you made any changes there.


Render Errors
-------------

See :doc:`EEVEE </render/eevee/limitations/index>` and
:doc:`Cycles </render/cycles/gpu_rendering>` documentation respectively.


Wrong Selection in 3D Viewport
------------------------------

See :ref:`Invalid Selection, Disable Anti-Aliasing <troubleshooting-3dview-invalid-selection>`.


Virtual Machines
----------------

Running Blender inside a virtual machine is known to have problems
when OpenGL drawing calls are forwarded to the host operating system.

To resolve this, configure the system to use PCI passthrough.


Information
===========

To find out which graphics card and driver Blender is using,
use :menuselection:`Help --> Save System Info` inside Blender.
The OpenGL section will have information about your graphics card, vendor and driver version.


## Amd


************
Linux -- AMD
************

.. include:: ../common/introduction.rst
   :start-line: 1

On Linux, graphics drivers are usually installed as a package by your Linux
distribution. Installing the latest drivers is typically done by upgrading packages
or the distribution as a whole. Some distributions provide multiple packages
for multiple drivers versions, giving you the choice to install newer versions.

AMD drivers are open source, except for the OpenCL support which is available as
part of Pro drivers. Installing packages through your Linux distribution is
usually best. AMD also provides graphics drivers for download on their website
if you need the latest version.

`AMD Drivers and Support Website <https://www.amd.com/en/support>`__

.. include:: ../common/laptops.rst
   :start-line: 1
.. include:: ../common/other.rst
   :start-line: 1


## Intel


**************
Linux -- Intel
**************

.. include:: ../common/introduction.rst
   :start-line: 1

On Linux, graphics drivers are usually installed as a package by your Linux
distribution. Installing the latest drivers is typically done by upgrading
packages or the distribution as a whole. Some distributions provide multiple
packages for multiple drivers versions, giving you the choice to install newer
versions.

.. include:: ../common/other.rst
   :start-line: 1


## Nvidia


***************
Linux -- Nvidia
***************

.. include:: ../common/introduction.rst
   :start-line: 1

On Linux, graphics drivers are usually installed as a package by your Linux
distribution. Installing the latest drivers is typically done by upgrading packages
or the distribution as a whole. Some distributions provide multiple packages
for multiple drivers versions, giving you the choice to install newer versions.

For Nvidia there are open source (Nouveau) and closed source (by Nvidia)
graphics drivers. Blender functions best with the closed source drivers as they
are more optimized and complete. Linux graphics drivers can be downloaded from
Nvidia's website, however in most cases the ones from your Linux distribution
are fine and make things easier. Manually downloading drivers is mostly useful to get
the very latest version, for example for a GPU that was only recently released.

`NVidia Website <https://www.nvidia.com/Download/index.aspx>`__

.. include:: ../common/laptops.rst
   :start-line: 1
.. include:: ../common/other.rst
   :start-line: 1


## Other


******************
Linux -- Other GPU
******************

.. include:: ../common/introduction.rst
   :start-line: 1

On Linux, graphics drivers are usually installed as a package by your Linux distribution.
Installing the latest drivers is typically done by upgrading packages
or the distribution as a whole. Some distributions provide multiple packages
for multiple drivers versions, giving you the choice to install newer versions.

.. include:: ../common/laptops.rst
   :start-line: 1
.. include:: ../common/other.rst
   :start-line: 1


## Amd


**************
Windows -- AMD
**************

.. include:: ../common/introduction.rst
   :start-line: 1

On Windows drivers are provided by the graphics card manufacturer (AMD).
Windows update automatically installs graphics drivers, or
your computer manufacturer may provide its own version of the graphics drivers.

However, these are not always the latest version or may have been corrupted in
some way. We recommend to always use the official drivers.

`Download Latest AMD Drivers <https://www.amd.com/en/support>`__

.. include:: ../common/laptops.rst
   :start-line: 1
.. include:: ../common/other.rst
   :start-line: 1


## Intel


****************
Windows -- Intel
****************

.. include:: ../common/introduction.rst
   :start-line: 1

On Windows drivers are provided by the graphics card manufacturer (Intel).
Windows update automatically installs graphics drivers, or
your computer manufacturer may provide its own version of the graphics drivers.

However, these are not always the latest version or may have been corrupted in some way.
We recommend to use the official drivers.

`Download Latest Intel Drivers <https://www.intel.com/content/www/us/en/support/products/80939/graphics.html>`__

.. include:: ../common/laptops.rst
   :start-line: 1


Compatibility
=============

In some cases Blender may crash on startup. Running Blender in compatibility mode
can help in fixing this issue. To enable compatibility mode, :kbd:`RMB` on
the Blender executable and select :menuselection:`Properties --> Compatibility`
and enable :menuselection:`Run this program in compatibility mode`.
Confirm the changes with *Apply*.

.. include:: ../common/other.rst
   :start-line: 1


Legacy Intel HD 4000/5000
=========================

When running on Intel 3, 4 or 5th gen iGPU the latest Intel driver will crash on startup. In order
to start Blender try to install a previous version of the driver. Drivers that are known to work
are:

- 20.19.15.4835
- 20.19.15.4963
- 20.19.15.5063

Drivers that are known to fail are:

- 20.19.15.5144
- 20.19.15.5166
- 20.19.15.5171

`Download older Intel Drivers <https://www.intel.com/content/www/us/en/support/articles/000089377/graphics.html>`__


## Nvidia


*****************
Windows -- Nvidia
*****************

.. include:: ../common/introduction.rst
   :start-line: 1

On Windows drivers are provided by the graphics card manufacturer (Nvidia).
Windows update automatically installs graphics drivers, or
your computer manufacturer may provide its own version of the graphics drivers.

However, these are not always the latest version or may have been corrupted in some way.
We recommend to always use the official drivers.

`Download Latest Nvidia Drivers <https://www.nvidia.com/Download/index.aspx>`__

.. include:: ../common/laptops.rst
   :start-line: 1
.. include:: ../common/other.rst
   :start-line: 1


## Other


********************
Windows -- Other GPU
********************

.. include:: ../common/introduction.rst
   :start-line: 1

On Windows drivers are provided by the graphics card manufacturer.
Windows update automatically installs graphics drivers, or
your computer manufacturer may provide its own version of the graphics drivers.

.. include:: ../common/laptops.rst
   :start-line: 1
.. include:: ../common/other.rst
   :start-line: 1


