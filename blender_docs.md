# Index

- [app_templates](#app_templates)
- [blender_directory_layout](#blender_directory_layout)
- [deploying_blender](#deploying_blender)
- [index](#index)
- [keymap_editing](#keymap_editing)
- [limits](#limits)
- [operators](#operators)
- [appendices\index](#appendices-index)
- [appendices\rotations](#appendices-rotations)
- [command_line\arguments](#command_line-arguments)
- [command_line\index](#command_line-index)
- [command_line\render](#command_line-render)
- [command_line\launch\index](#command_line-launch-index)
- [command_line\launch\linux](#command_line-launch-linux)
- [command_line\launch\macos](#command_line-launch-macos)
- [command_line\launch\windows](#command_line-launch-windows)
- [extensions\addons](#extensions-addons)
- [extensions\command_line_arguments](#extensions-command_line_arguments)
- [extensions\getting_started](#extensions-getting_started)
- [extensions\index](#extensions-index)
- [extensions\licenses](#extensions-licenses)
- [extensions\python_wheels](#extensions-python_wheels)
- [extensions\tags](#extensions-tags)
- [scripting\addon_tutorial](#scripting-addon_tutorial)
- [scripting\index](#scripting-index)
- [scripting\introduction](#scripting-introduction)
- [scripting\security](#scripting-security)


## app_templates

.. _bpy.ops.wm.app_template:
.. _bpy.ops.preferences.app_template_install:
.. _app_templates:

*********************
Application Templates
*********************

Usage
=====

Application templates are a feature that allows you to define a re-usable configuration
that can be selected to replace the default configuration,
without requiring a separate Blender installation or overwriting your personal settings.

Application templates can be selected from the splash screen or :menuselection:`File --> New` submenu.
When there are no templates found the menu will not be displayed on the splash screen.

New application templates can be installed from the :ref:`topbar-blender_menu`.
If you would like to keep the current application template active on restarting Blender, save your preferences.


Motivation
----------

In some cases it's not enough to write a single script or add-on,
and expect someone to replace their preferences and startup file, install scripts and change their keymap.

The goal of application templates is to support switching to a customized configuration
without disrupting your existing settings and installation.
This means people can build their own *applications* on top of Blender that can be easily distributed.


Details
-------

An application template may define its own:

Startup File
   The default file to load with this template.
Preferences
   Only certain preferences from a template are used:

   - Themes.
   - Add-ons.
   - Keymaps.
   - Viewport lighting.
Splash Screen
   Templates may provide their own splash screen image.
Python Scripts
   While templates have access to the same functionality as any other scripts,
   typical operations include:

   - Modifying and replacing parts of the user interface.
   - Defining new menus, keymaps and tools.
   - Defining a custom add-on path for template specific add-ons.

Templates also have their own user configuration, so saving a startup file while using a template
won't overwrite your default startup file.


Directory Layout
----------------

Templates may be located in one of two locations within the ``scripts`` directory.

Template locations:
   | ``{BLENDER_USER_SCRIPTS}/startup/bl_app_templates_user``
   | ``{BLENDER_SYSTEM_SCRIPTS}/startup/bl_app_templates_system``

User configuration is stored in a subdirectory:

Without a template:
   | ``./config/startup.blend``
   | ``./config/userpref.blend``
With a template:
   | ``./config/{APP_TEMPLATE_ID}/startup.blend``
   | ``./config/{APP_TEMPLATE_ID}/userpref.blend``

See :ref:`blender-directory-layout` for details on script and configuration locations.

.. hint:: Troubleshooting Paths

   When creating an application template, you may run into issues where paths are not being found.
   To investigate this you can log output of all of Blender's path look-ups.

   Example command line arguments that load Blender with a custom application template
   (replace ``my_app_template`` with the name of your own template):

   .. code-block:: sh

      blender --log "bke.appdir.*" --log-level -1 --app-template my_app_template

   You can then check the paths where attempts to access ``my_app_template`` are made.


Command Line Access
-------------------

Using the :ref:`command-line arguments <command_line-args>` you can setup a launcher
that opens Blender with a specific app template:

.. code-block:: sh

   blender --app-template my_template


Template Contents
=================

Each of the following files can be used for application templates but are optional.

``startup.blend``
   Factory startup file to use for this template.
``userpref.blend``
   Factory preferences file to use for this template.
   When omitted preferences are shared with the default Blender configuration.

   *(As noted previously, this is only used for a subset of preferences).*

``splash.png``
   Splash screen to override Blender's default artwork (not including header text).
   Note, this image must be a ``1000x500`` image.

``__init__.py``
   A Python script which must contain ``register`` and ``unregister`` functions.

.. note::

   Bundled blend-files ``startup.blend`` and ``userpref.blend`` are considered *Factory Settings*
   and are never overwritten.

   The user may save their own startup/preferences while using this template which will be stored
   in their user configuration, but only when the template includes its own ``userpref.blend`` file.

   The original template settings can be loaded using: *Load Template Factory Settings*
   from the file menu in much the same way *Load Factory Settings* works.


Template Scripts
================

While app templates can use Python scripts,
they simply have access to the same APIs available for add-ons and any other scripts.

As noted above, you may optionally have an ``__init__.py`` in your app template.
This has the following advantages:

- Changes can be made to the startup or preferences, without having to distribute a blend-file.
- Changes can be made dynamically.

  You could for example -- configure the template to check the number of processors,
  operating system and memory, then set values based on this.

- You may enable add-ons associated with your template.

On activation a ``register`` function is called, ``unregister`` is called when another template is selected.

As these only run once, any changes to defaults must be made via handler.
Two handlers you are likely to use are:

- ``bpy.app.handlers.load_factory_preferences_post``
- ``bpy.app.handlers.load_factory_startup_post``

These allow you to define your own "factory settings", which the user may change,
just as Blender has it's own defaults when first launched.

This is an example ``__init__.py`` file which defines defaults for an app template to use.

.. code-block:: python

   import bpy
   from bpy.app.handlers import persistent

   @persistent
   def load_handler_for_preferences(_):
       print("Changing Preference Defaults!")
       from bpy import context

       prefs = context.preferences
       prefs.use_preferences_save = False

       kc = context.window_manager.keyconfigs["blender"]
       kc_prefs = kc.preferences
       if kc_prefs is not None:
           kc_prefs.select_mouse = 'RIGHT'
           kc_prefs.spacebar_action = 'SEARCH'
           kc_prefs.use_pie_click_drag = True

       view = prefs.view
       view.header_align = 'BOTTOM'


   @persistent
   def load_handler_for_startup(_):
       print("Changing Startup Defaults!")

       # Use smooth faces.
       for mesh in bpy.data.meshes:
           for poly in mesh.polygons:
               poly.use_smooth = True

       # Use material preview shading.
       for screen in bpy.data.screens:
           for area in screen.areas:
               for space in area.spaces:
                   if space.type == 'VIEW_3D':
                       space.shading.type = 'MATERIAL'
                       space.shading.use_scene_lights = True


   def register():
       print("Registering to Change Defaults")
       bpy.app.handlers.load_factory_preferences_post.append(load_handler_for_preferences)
       bpy.app.handlers.load_factory_startup_post.append(load_handler_for_startup)

   def unregister():
       print("Unregistering to Change Defaults")
       bpy.app.handlers.load_factory_preferences_post.remove(load_handler_for_preferences)
       bpy.app.handlers.load_factory_startup_post.remove(load_handler_for_startup)


## blender_directory_layout

.. _blender-directory-layout:

**************************
Blender's Directory Layout
**************************

This page documents the different directories used by Blender.

This can be helpful for troubleshooting, automation and customization.


User Directories
================

User directories store preferences, startup file, installed extensions,
presets and more. By default these use the standard configuration folders
for each operating system.

Linux
-----

.. parsed-literal:: $HOME/.config/blender/|BLENDER_VERSION|/

If the ``$XDG_CONFIG_HOME`` environment variable is set:

.. parsed-literal:: $XDG_CONFIG_HOME/blender/|BLENDER_VERSION|/

macOS
-----

.. parsed-literal:: /Users/$USER/Library/Application Support/Blender/|BLENDER_VERSION|/

Windows
-------

.. parsed-literal:: %USERPROFILE%\\AppData\\Roaming\\Blender Foundation\\Blender\\\ |BLENDER_VERSION|\\

.. _portable-installation:

Portable Installation
---------------------

When running Blender from a portable drive, it's possible to keep the configuration
files on the same drive to take with you.

To enable this, create a folder named ``portable`` at the following locations:

* Windows: Next to the Blender executable, in the unzipped folder
* Linux: Next to the Blender executable, in the unzipped folder
* macOS: Inside the application bundle at ``Blender.app/Contents/Resources``

This folder will then store preferences, startup file, installed extensions
and presets.

Environment Variables
---------------------

The ``BLENDER_USER_RESOURCES`` :ref:`environment variable <command-line-args-environment-variables>`
can be set to a custom directory to replace the default user directory.

System Directories
==================

System directories store files that come bundled with Blender and
are required for it to function. This includes scripts, presets, essential
assets and more. 

Linux
-----

Archive downloaded from blender.org:

.. parsed-literal:: ./|BLENDER_VERSION|/

Linux distribution packages:

.. parsed-literal:: /usr/share/blender/|BLENDER_VERSION|/

macOS
-----

.. parsed-literal:: ./Blender.app/Contents/Resources/|BLENDER_VERSION|/

Windows
-------

Zip file downloaded from blender.org:

.. parsed-literal:: ./|BLENDER_VERSION|/

Installer downloaded from blender.org:

.. parsed-literal:: %ProgramFiles%\\Blender Foundation\\Blender\\\ |BLENDER_VERSION|\\

Microsoft Store installation:

.. parsed-literal:: %ProgramFiles%\\WindowsApps\\BlenderFoundation.Blender<HASH>\\Blender\\\ |BLENDER_VERSION|\\


Environment Variables
---------------------

``BLENDER_SYSTEM_SCRIPTS`` and ``BLENDER_SYSTEM_EXTENSIONS``
:ref:`environment variables <command-line-args-environment-variables>`
can be used to :ref:`bundle additional scripts and extensions <deploying-blender-bundling>`,
that are not part of the regular Blender installation.

Other ``BLENDER_SYSTEM`` environment variables can override other system paths,
though are not commonly used in practice.

.. _blender-directory-path-layout:

Path Layout
===========

``./autosave``
  Autosave blend-file location. (Windows only, temp directory used for other systems.)

  Located in user directories.

``./config``
  User configuration and session info.

  Located in user directories.

  ``./config/startup.blend``
    Blend file to load on startup.

  ``./config/userpref.blend``
    User preferences.

  ``./config/bookmarks.txt``
    File Browser bookmarks.

  ``./config/recent-files.txt``
    Recent file menu list.

  ``./config/{APP_TEMPLATE_ID}/startup.blend``
    Startup file for an application template.

  ``./config/{APP_TEMPLATE_ID}/userpref.blend``
    User preferences file for an application template.

``./datafiles``
  Data files loaded at runtime.

  Located in both user and system directories. User data files either override
  or add to system data files.

  ``./datafiles/colormanagement``
    Default OpenColorIO configuration.

  ``./datafiles/fonts``
    User interface fonts.

  ``./datafiles/studiolights``
    Studio light images for 3D viewport.

``./extensions``
  Extension repositories.

  Located in both user and system directories. Repositories are loaded from
  both directories.

``./scripts``
  Add-ons, presets, templates, user interface, startup scripts.

  Located in both user and system directories. Scripts are loaded from
  both directories.

  ``./scripts/addons/*.py``
    Python add-ons which may be enabled in the Preferences include import/export format support,
    render engine integration and many handy utilities.

  ``./scripts/addons/modules/*.py``
    Modules for add-ons to use
    (added to Python's ``sys.path``).

  ``./scripts/addons_core/*.py``
    The add-ons directory which is used for bundled add-ons.

  ``./scripts/addons_core/modules/*.py``
    Modules for ``addons_core`` to use (added to Python's ``sys.path`` when it found).

  ``./scripts/modules/*.py``
    Python modules containing our core API and utility functions for other scripts to import
    (added to Python's ``sys.path``).

  ``./scripts/startup/*.py``
    Scripts which are automatically imported on startup.

    ``./scripts/startup/bl_app_templates_user/{APP_TEMPLATE_ID}``
      Application templates installed in user directories.

    ``./scripts/startup/bl_app_templates_system/{APP_TEMPLATE_ID}``
       pplication templates automatically loaded from system directories.

  ``./scripts/presets/{preset}/*.py``
    Presets used for storing user-defined settings for cloth, render formats, etc.

  ``./scripts/templates_py/*.py``
    Example scripts which can be accessed from :menuselection:`Text Editor --> Templates --> Python`.

  ``./scripts/templates_osl/*.osl``
    Example OSL shaders which can be accessed from
    :menuselection:`Text Editor --> Templates --> Open Shading Language`.

``./python``
  Bundled Python distribution.

  Located in system directories.


.. _local-cache-dir:

Local Cache Directory
=====================

The cache directory is used to store persistent caches locally. Currently it is only used for the indexing of
:ref:`Asset Libraries <what-is-asset-library>`. The operating system is not expected to clear this automatically.

The following path will be used:

- :Linux: ``$XDG_CACHE_HOME/blender/`` if ``$XDG_CACHE_HOME`` is set, otherwise ``$HOME/.cache/blender/``
- :macOS: ``/Library/Caches/Blender/``
- :Windows: ``%USERPROFILE%\AppData\Local\Blender Foundation\Blender\Cache\``


.. _temp-dir:

Temporary Directory
===================

The temporary directory is used to store various files at run-time
(including render layers, physics cache, copy-paste buffer and crash logs).

The temporary directory is selected based on the following priority:

- User Preference (see :ref:`prefs-file-paths`).
- Environment variables (``TEMP`` on Windows, ``TMP`` & ``TMP_DIR`` on other platforms).
- The ``/tmp/`` directory.


## deploying_blender

.. _deploying-blender:

*******************************
Deploying Blender in Production
*******************************

It is possible to deploy Blender in environments that are more
restricted, use automation or have other special requirements.
For example in an animation studio or for school courses.

This page contains tips setting up Blender in such environments.


Installing Blender
==================

Blender downloads can be extracted to any directory on the system, as
a self contained installation. Multiple Blender versions can easily
co-exist on the same system, and deployment can be automated using
standard file management tools.

New Blender versions may add, remove or changes functionality that
change the results of production files. For a given project, it is
advisable to use a single :abbr:`LTS (Long-Term-Support)` version
of Blender. LTS versions receive bug fixes for two years.


Working Offline
===============

For security or other reasons, workstation may not have internet access.

By default Blender does not access the internet, however this can be
enabled in the System preferences with the
:ref:`Online Access <bpy.types.PreferencesSystem.use_online_access>` option.

Working offline can be enforced by running with the ``--offline-mode``
:ref:`command line argument <command-line-args-network-options>`. Users
will then be unable to enable online access in the preferences.


.. _deploying-blender-bundling:

Bundling Extensions
===================

When working offline or in a more controlled environment, it may be useful
to provide a set of extensions to all users. These can be served from the
default read-only System repository. This can be located for example on a
network drive or in a system directory.

.. figure:: /images/advanced_deploying-blender_system-extensions.png

   System repository

The ``$BLENDER_SYSTEM_EXTENSIONS``
:ref:`environment variable <command-line-args-environment-variables>`
controls the default location. This should point to a directory, within
which a ``system`` directory should exist.

Extensions packages should be extracted in this ``system`` directory,
with a resulting path like this:

.. code-block:: bash

    $BLENDER_SYSTEM_EXTENSIONS/system/my-addon/blender_manifest.toml

In the Extensions preferences, it's possible to manually set a custom
directory of the default System repository and to create multiple
repositories.


Bundling Scripts
================

Besides extensions, it's possible to bundle scripts for presets,
application templates, legacy add-ons, as well as scripts run on startup.

Script directories can be manually added in the File Paths preferences.
The ``$BLENDER_SYSTEM_SCRIPTS`` can also be used to add a script directory
without modifying the preferences.

These script directories are expected to contain specific directories
like ``presets``, ``addons`` and ``startup`` for different types of
scripts. See :ref:`blender-directory-path-layout` for a complete list.


Startup Scripts
---------------

The Blender Python API can be used to customize Blender. This includes
changing preferences, changing the startup file and adding UI elements.

For example, a script can enable add-ons for every user.

.. code-block:: bash

    $BLENDER_SYSTEM_SCRIPTS/startup/enable_addons.py

.. code-block:: python

   def register():
       import addon_utils
       addon_utils.enable("my-addon")

   def unregister():
       pass

   if __name__ == "__main__":
       register()


Application Templates
---------------------

:ref:`app_templates` can be used to set up Blender for particular
tasks or projects, separate from the default configuration. When
creating a new file the user can choose the template.

The files are expected to be placed in the system script directories like this:

.. code-block:: bash

   $BLENDER_SYSTEM_SCRIPTS/startup/bl_app_templates_system/MyTemplate/__init__.py
   $BLENDER_SYSTEM_SCRIPTS/startup/bl_app_templates_system/MyTemplate/startup.blend


Legacy Add-ons
--------------

Add-ons that have not been converted to become an extension yet need
to be placed in the ``addons`` script directory.

For example, an add-on could be located at:

.. code-block:: bash

    $BLENDER_SYSTEM_SCRIPTS/addons/simple_addon.py
    $BLENDER_SYSTEM_SCRIPTS/addons/complex_addon/__init__.py


VFX Platform
============

Blender follows the `VFX reference platform <https://vfxplatform.com>`_,
which means it is able to run on the same systems as other VFX software
and exchange image, volume and scene files with them.


Python Version
--------------

Blender and the `by module <https://pypi.org/project/bpy/>`_ are only compatible
with a single Python version. This makes it possible for add-ons and VFX software
in general to only have to target a single Python version.

Blender bundles a complete Python installation and does not interact with the
system Python by default. This can be changed with the ``--python-use-system-env``
:ref:`command line argument <command-line-args-python-options>`, if care is
taken to set up a compatible Python version.


## index

.. _advanced-index:

############
  Advanced
############

This chapter covers advanced use (topics which may not be required for typical usage).

.. toctree::
   :maxdepth: 1

   command_line/index.rst
   scripting/index.rst
   extensions/index.rst
   app_templates.rst
   keymap_editing.rst
   limits.rst
   operators.rst
   blender_directory_layout.rst
   deploying_blender.rst
   appendices/index.rst


## keymap_editing

.. _keymap-customize:

********************
Keymap Customization
********************

Keys
====

Available Keys
--------------

When customizing keymaps it's useful to use keys which won't conflict with Blender's default keymap.

Here are keys which aren't used and aren't likely to be used in the future.

F-Keys (:kbd:`F5` - :kbd:`F8`)
   These F-keys (including modifier combination)
   have been intentionally kept free for users to bind their own keys to.
:kbd:`OSKey` (also known as the ``Windows-Key``, ``Cmd`` or ``Super``)
   Blender doesn't use this key for any bindings.

   *macOS* is an exception, where :kbd:`Cmd` replaces :kbd:`Ctrl`
   except in cases it would conflict with the system's key bindings.
Modifier Double Click
   Binding modifier keys as primary keys is supported,
   to avoid conflicts with regular usage you can bind them to double click.


Multi-Action Keys
-----------------

Click/Drag
^^^^^^^^^^

It's possible to configure a single key to perform multiple operations
using *Click* event instead of *Press*. Then you may bind *Drag* to a separate action.

This is useful for mixing actions where one uses a drag event, e.g:
Toggle a setting using with :kbd:`Tab`, drag to open a pie menu showing all options related to the setting.

This is used in the default keymap in the 3D Viewport,
:kbd:`Alt-MMB` dragging in different directions rotates the view.


Common Operations
=================

This section lists useful generic operations which can be used.


Key Bindings for Pop-Ups
------------------------

Menus and panels can be assigned key shortcuts,
even if they're only accessible from submenus elsewhere.

Open a Pop-up Menu (``wm.call_menu``)
   Open any menu on key press.
Open a Pie Menu (``wm.call_menu_pie``)
   Open any pie menu on key press.
Open a Panel (``wm.call_panel``)
   Open a pop-up panel (also known as a pop-over).


Menu & Panel Identifiers
^^^^^^^^^^^^^^^^^^^^^^^^

To find the ``name`` of a menu,
enable the preference :menuselection:`Interface --> Display --> Python Tooltips`.

Then hover the cursor over the popover button or menu item.
For submenus you will need to use the back arrow to prevent the submenu from opening and gaining focus.


Key Bindings for Properties
---------------------------

There are many properties you might want to bind a key with.
To avoid having to define operators for each property,
there are generic operators for this purpose:

Operators for adjusting properties begin with ``wm.context_``.

Some of these include:

- ``wm.context_toggle`` toggle a Boolean property.
- ``wm.context_cycle_enum`` cycle an :abbr:`enum (enumeration)` property forwards or backwards.
- ``wm.context_menu_enum`` show a pop-up menu for an enum property.
- ``wm.context_pie_enum`` show a pie menu for an enum property.
- ``wm.context_scale_float`` scale a number (used for increasing / decreasing brush size for example).
- ``wm.context_toggle_enum`` toggle between two options of an enum.
- ``wm.context_modal_mouse`` moving the cursor to interactively change a value.

See `bpy.ops.wm <https://docs.blender.org/api/current/bpy.ops.wm.html>`__ for a complete list.

Each of these operators has a ``data_path`` setting to reference the property to change.

To find the ``data_path``, basic Python knowledge is needed.

For example, you can use the Python Console to access a Boolean property you wish to map to a key::

   bpy.context.object.show_name

To bind this to a key, add a new keymap item using the operator ``wm.context_toggle``
with ``data_path`` set to ``object.show_name`` (notice the ``bpy.context`` prefix is implicit).

See `bpy.context <https://docs.blender.org/api/current/bpy.context.html>`__
for other context attributes.

The Python API documentation can be used to find properties
or you may use the Python Console's auto-complete to inspect available properties.


## limits


**************
Working Limits
**************

.. Note to editors:
   Please excuse the complicated Python scripts on this page,
   this is not something we do frequently in this manual,
   Its just for such explicit technical details,
   its useful to be able to validate its correct (or adjust the information shown).
   -- ideasman42


Space
=====

While object positions, vertex locations are not clamped, larger values become increasingly imprecise.
To get an idea of the precision you can work with using different scales.
Here's a table of scales and their associated accuracy:

.. # Python script used to generate the values below
   import ctypes
   from sys import platform as _platform
   _libm = ctypes.cdll.LoadLibrary('libm.so.6')
   _funcname_f = 'nextafterf'
   _nextafterf = getattr(_libm, _funcname_f)
   _nextafterf.restype = ctypes.c_float
   _nextafterf.argtypes = [ctypes.c_float, ctypes.c_float]
   i = 10
   while i < 10000000:
      delta = _nextafterf(i, i + 1) - i
      print(":{scale:,}: 1/{div:,}\\ :sup:`th`".format(scale=i, div=int(1 / delta)))
      i = i * 10


:10: 1/1,048,576\ :sup:`th`
:100: 1/131,072\ :sup:`th`
:1,000: 1/16,384\ :sup:`th`
:10,000: 1/1,024\ :sup:`th`
:100,000: 1/128\ :sup:`th`
:1,000,000: 1/16\ :sup:`th`

.. hint::

   For a rough rule of thumb, values within -5,000/+5,000 are typically reliable (range of 10,000).
   Internally *single precision* floating-point calculations are used.


Time
====

.. # Python script used to generate the values below
   from datetime import timedelta
   maxframe = 1048574
   for fps in (24, 25, 30, 60):
      seconds = maxframe / fps
      print(":%d fps: %d hours, %d minutes." %
            (fps, seconds // 3600, seconds % 3600 // 60))

The maximum number of frames for each scene is currently 1,048,574, and allows for continuous shots for durations of:

:24 fps: 12 hours, 8 minutes.
:25 fps: 11 hours, 39 minutes.
:30 fps: 9 hours, 42 minutes.
:60 fps: 4 hours, 51 minutes.

.. note::

   In practice, a finished work is typically composed of output from many scenes.
   So this limit does not prevent you from creating longer works.


Text Fields
===========

Fixed strings are used internally, and while it is not useful to list all limits, here are some common limits.
*Used for data-block names, modifiers, vertex groups, UV layers...*

:directory: 767
:file-name: 255
:file-path: 1023
:identifier: 63

.. note::

   Multi-byte encoding means some Unicode characters use more than a single ASCII character.


## operators


*********
Operators
*********

.. _bpy.ops.wm.operator_cheat_sheet:

Operator Cheat Sheet
====================

.. reference::

   :Menu:      :menuselection:`Help --> Operator Cheat Sheet`
   :Context:   Enable :ref:`Developer Extras <bpy.types.PreferencesView.show_developer_ui>`

Creates a text file in the Text Editor that gives a list of all operators
and their default values in Python syntax, along with the generated docs.
This is a good way to get an overview of all Blender's operators.

.. seealso::

   `Blender's API documentation <https://docs.blender.org/api/current/>`__


System Operators
================

.. _bpy.ops.script.reload:

Reload Scripts
--------------

.. reference::

   :Mode:      All Modes
   :Menu:      :menuselection:`Topbar --> Blender --> System --> Reload Scripts`

Reloads all scripts found in the scripts data folder;
any changes that have been made in the Text Editor will be lost!


.. _bpy.ops.wm.memory_statistics:

Memory Statistics
-----------------

.. reference::

   :Mode:      ``--debug-memory``
   :Menu:      :menuselection:`Topbar --> Blender --> System --> Memory Statistics`

This operator which can be found by searching "Memory Statistics"
with the :doc:`Operator Search </interface/controls/templates/operator_search>`
will print useful information about memory objects, their size and user count.

.. important::

   To fully use this operator run Blender from the console with ``--debug-memory``.


.. _bpy.ops.wm.debug_menu:

Debug Menu
----------

.. reference::

   :Mode:      All Modes
   :Menu:      :menuselection:`Topbar --> Blender --> System --> Debug Menu`

This operator brings up a menu to set Blender into a certain debug mode.

See the
`source code <https://projects.blender.org/blender/blender/src/branch/main/source/blender/blenkernel/BKE_global.h>`__
for a description of what each value does.

.. tip::

   Developers can search the code for ``G.debug_value`` to find other possible uses for this operator.

.. note::

   Additional debug options are available by launching Blender in debug mode or setting ``bpy.app.debug = True``.


.. _bpy.ops.wm.redraw_timer:

Redraw Timer
------------

.. reference::

   :Mode:      All Modes
   :Menu:      :menuselection:`Topbar --> Blender --> System --> Redraw Timer`

This operator brings up a menu with a list of tests
to benchmark UI render times along with undo/redo functions.


.. _bpy.ops.screen.spacedata_cleanup:

Clean Up Space-Data
-------------------

.. reference::

   :Mode:      All Modes
   :Menu:      :menuselection:`Topbar --> Blender --> System --> Clean Up Space-data`

Removes unused settings for invisible editors.


## appendices\index


##############
  Appendices
##############

This chapter covers far more detailed explanations about some Blender tools
(which may not be required for typical usage).

.. toctree::
   :maxdepth: 1

   rotations.rst


## appendices\rotations


**************
Rotation Modes
**************

Blender lets you define rotations in several ways. Each one of them has a series of advantages and drawbacks;
there is no best rotation mode, as each one is suitable for specific cases.

In all of these modes, positive angle values mean counter-clockwise rotation direction,
while negative values define clockwise rotation.

Though you can rotate elements using the global or local transform orientations,
these axes are not suitable to define rotations, as the effect of each of
them cannot be isolated from the other two.

Take, for instance, any three values for X, Y and Z rotation. Perform each one of these using global or local axes.
Depending on the order in which you perform these, you will end up with different final orientations.
So proper rotation coordinate systems are needed.

.. _euler mode:

Euler Modes
===========

The axes system used for performing Euler rotations is the so called Euler gimbal.
A gimbal is a particular set of three axes.
The special thing about this is that the axes have a hierarchical relationship between them:
one of the axes is at the top of the hierarchy, and has one of the other two axes as its immediate child;
at the same time, this child axis is the parent of the remaining axis, the one at the very bottom of the hierarchy.

Which axis is on top, which one in the middle and which at the bottom,
depends on the particular Euler gimbal: there are six types of them, as there
are six possible combinations: XYZ, XZY, YXZ, YZX, ZXY and ZYX Euler rotation modes.
These modes are named using the letters of the axes in order, starting from
the axis at the bottom of the hierarchy, and finishing with the one on top.

The main problem of these systems comes when they lose their relative perpendicularity.
And this happens when the axis in the middle rotates, causing the axis at the bottom to
rotate with it. It keeps getting worse when this bottom axis approaches 90° (or equivalent angles).
In that case, it will remain aligned with the axis on top of the hierarchy. In that moment
we have just lost one axis of rotation. This can cause discontinuous interpolations when animating.
This particular loss of axis is known as the "gimbal lock".

.. hint::

   The actual configuration of the gimbal axes can be seen in the 3D Viewport by enabling the *Rotate* object gizmo
   and setting it to *Gimbal* (from the gizmos button in the header).
   At the same time, rotation mode should be set to any of the Euler modes for the active object.

   Now you can perform a rotation around the axis in the middle
   (e.g. in *XYZ Euler* mode that is the Y axis), and see how easy it is to
   end up having a gimbal with just two axes. In the specific case of
   the *XYZ Euler* mode with gimbal lock, a rotation around the X axis will have
   the same effect as rotating around the Z axis, meaning, in practice,
   that no X axis rotations can be performed.

One advantage of this mode is that animation curves are easy to understand and edit.
However, special attention must be done when the middle axis approaches values close to 90° (or equivalent angles).

.. _axis angle mode:

Axis Angle Mode
===============

This mode lets us define an axis (X, Y, Z) and a rotation angle (W) around that axis.

If we define the rotation using interactive rotations (with the rotation gizmo),
the values of X, Y and Z will not exceed 1.0 in absolute value, and W will be
comprised between 0 and 180 degrees.

If you wish to define rotations above 180° (e.g. to define multiple revolutions),
you will need to edit the W value directly, but as soon as you perform an interactive rotation,
that value will be adjusted again. Same thing goes for axis values.

This system is suitable for elements revolving around a fixed axis, or to animate one of the elements at a time
(either the axis or the angle).
The problem might come when animating (interpolating) both components at the same time: axis and angle.
The resulting effect might not be as expected.

The *Gimbal* gizmo in this rotation mode shows a set of three orthogonal axes in which the Z axis goes
along the defined rotation axis, i.e. it points towards the direction defined by the (X, Y, Z) point.

The axis-angle system is free from gimbal lock, but animation curves in this mode are not intuitive at all
when animating axis and angle at the same time, in which case they are difficult to understand and edit.

.. _quaternion mode:

Quaternion Mode
===============

In this mode, rotations are also defined by four values (X, Y, Z and W).
X, Y and Z also define an axis, and W an angle, but it does it quite differently from axis-angle.
The important thing here is the relation between all four values.

To describe it in an intuitive way, let's take the effect of the X coordinate:
what it does is to rotate the element around the X axis up to 180 degrees.
The same goes for Y and Z. The effect of W is to avoid those rotations and leave
the element with zero rotation. The final orientation is a combination of
these four effects.

As the relation between components is what defines the final orientation, multiplying or dividing all four numbers
by a constant value will yield the very same rotation.

This mode is ideal for interpolating between **any** pair of orientations.
It doesn't suffer from gimbal lock or any interpolation undesired effect.
The only drawback is that you cannot interpolate between two orientations
that are at a distance greater than than 180°, as the animation will take
the shortest path between them. Thus to animate a revolving element
you must set up many intermediate keyframes, 180° from each other at most.

The *Gimbal* gizmo in this mode is equivalent to the *Local* one, and doesn't have any special meaning.

The animation curves in this mode are not intuitive, so they are also difficult to understand and edit.


More about Quaternions
----------------------

This section is not really useful for 3D artists, but it can be suitable for the curious or the scientist.

Quaternions are a number system extending the complex numbers. They represent a four component vector, whose
components are called, in Blender, X, Y, Z and W.
When rotating interactively in quaternion mode, the so called norm (length) of the quaternion will remain constant.
By definition, the norm of a quaternion equals 1.0 (that's a **normalized** quaternion). When you select
the quaternion mode in Blender, the XYZW components describe a normalized quaternion.

.. note::

   The norm of a quaternion *q* is defined mathematically as:

   .. math::

      \lvert q \rvert = \sqrt{X^2 + Y^2 + Z^2 + W^2}

However, if one of the quaternion components is locked during the interactive transformation using the proper
lock button, the norm will not remain unchanged, as that blocked component will not be able to adjust itself to
keep the unit norm.

.. hint::

   Interactive rotations with the gizmo don't change the norm of the current quaternion.
   Editing a single XYZW component individually you can change the norm.
   To make the norm 1.0 again you can switch to any rotation mode and back again into quaternion.

The rotation components of a quaternion keep a tight relation with those of axis-angle. To find a correspondence,
first of all we must deal with the normalized version of the quaternion, that is, one whose norm equals 1.0.
To normalize a quaternion, just divide each one of its components by its norm.
As we have seen before, dividing all four values by the same number gives the same orientation.

Once we have calculated the components of the normalized quaternion, the relation with the axis-angle components
is as follows:

- X, Y and Z mean exactly the same as in axis-angle: they just define an axis around which the rotation takes place.
- W can be used to retrieve the actual rotation around the defined angle.
  The following formula applies (provided that the *quaternion is normalized*):
  :math:`W = \cos(\frac{a}{2})`, where *a* is actually the rotation angle we are looking for. That is:
  :math:`a = 2 \arccos{W}`.


Other Considerations
====================

In axis-angle and quaternion modes we can lock rotations in interactive modes in a per component basis,
instead of doing it by axis. To do so we can activate this locking ability using the lock buttons next to
the corresponding *Rotation* transform buttons.

Regarding rotation animations, all keyframes must be defined in the same rotation mode,
which must be the selected rotation mode for the object throughout the entire animation.


## command_line\arguments

.. DO NOT EDIT THIS FILE, GENERATED BY 'blender_help_extract.py'

   CHANGES TO THIS FILE MUST BE MADE IN BLENDER'S SOURCE CODE, SEE:
   https://projects.blender.org/blender/blender/src/branch/main/source/creator/creator_args.cc

.. _command_line-args:

**********************
Command Line Arguments
**********************

| Blender |BLENDER_VERSION|
| Usage: ``blender [args ...] [file] [args ...]``

.. _command-line-args-render-options:

Render Options
==============

``-b``, ``--background``
   Run in background (often used for UI-less rendering).

   The audio device is disabled in background-mode by default
   and can be re-enabled by passing in ``-setaudo Default`` afterwards.

``-a``, ``--render-anim``
   Render frames from start to end (inclusive).

``-S``, ``--scene`` ``<name>``
   Set the active scene ``<name>`` for rendering.

``-f``, ``--render-frame`` ``<frame>``
   Render frame ``<frame>`` and save it.

   * ``+<frame>`` start frame relative, ``-<frame>`` end frame relative.
   * A comma separated list of frames can also be used (no spaces).
   * A range of frames can be expressed using ``..`` separator between the first and last frames (inclusive).


``-s``, ``--frame-start`` ``<frame>``
   Set start to frame ``<frame>``, supports +/- for relative frames too.

``-e``, ``--frame-end`` ``<frame>``
   Set end to frame ``<frame>``, supports +/- for relative frames too.

``-j``, ``--frame-jump`` ``<frames>``
   Set number of frames to step forward after each rendered frame.

``-o``, ``--render-output`` ``<path>``
   Set the render path and file name.
   Use ``//`` at the start of the path to render relative to the blend-file.

   The ``#`` characters are replaced by the frame number, and used to define zero padding.

   * ``animation_##_test.png`` becomes ``animation_01_test.png``
   * ``test-######.png`` becomes ``test-000001.png``

   When the filename does not contain ``#``, the suffix ``####`` is added to the filename.

   The frame number will be added at the end of the filename, eg:

   .. code-block:: sh

      blender -b animation.blend -o //render_ -F PNG -x 1 -a

   ``//render_`` becomes ``//render_####``, writing frames as ``//render_0001.png``

``-E``, ``--engine`` ``<engine>``
   Specify the render engine.
   Use ``-E help`` to list available engines.

``-t``, ``--threads`` ``<threads>``
   Use amount of ``<threads>`` for rendering and other operations
   [1-1024], 0 to use the systems processor count.

.. _command-line-args-cycles-render-options:

Cycles Render Options
=====================

Cycles add-on options must be specified following a double dash.

``--cycles-device`` ``<device>``
   Set the device used for rendering.
   Valid options are: ``CPU`` ``CUDA`` ``OPTIX`` ``HIP`` ``ONEAPI`` ``METAL``.

   Append +CPU to a GPU device to render on both CPU and GPU.

   Example:

   .. code-block:: sh

      blender -b file.blend -f 20 -- --cycles-device OPTIX

``--cycles-print-stats``
   Log statistics about render memory and time usage.

.. _command-line-args-format-options:

Format Options
==============

``-F``, ``--render-format`` ``<format>``
   Set the render format.
   Valid options are:
   ``TGA`` ``RAWTGA`` ``JPEG`` ``IRIS`` ``AVIRAW`` ``AVIJPEG`` ``PNG`` ``BMP`` ``HDR`` ``TIFF``.

   Formats that can be compiled into Blender, not available on all systems:
   ``OPEN_EXR`` ``OPEN_EXR_MULTILAYER`` ``FFMPEG`` ``CINEON`` ``DPX`` ``JP2`` ``WEBP``.

``-x``, ``--use-extension`` ``<bool>``
   Set option to add the file extension to the end of the file.


.. _command-line-args-animation-playback-options:

Animation Playback Options
==========================

``-a`` ``<options>`` ``<file(s)>``
   Instead of showing Blender's user interface, this runs Blender as an animation player,
   to view movies and image sequences rendered in Blender (ignored if ``-b`` is set).

   Playback Arguments:

   ``-p`` ``<sx>`` ``<sy>``
      Open with lower left corner at ``<sx>``, ``<sy>``.
   ``-m``
      Read from disk (Do not buffer).
   ``-f`` ``<fps>`` ``<fps_base>``
      Specify FPS to start with.
   ``-j`` ``<frame>``
      Set frame step to ``<frame>``.
   ``-s`` ``<frame>``
      Play from ``<frame>``.
   ``-e`` ``<frame>``
      Play until ``<frame>``.
   ``-c`` ``<cache_memory>``
      Amount of memory in megabytes to allow for caching images during playback.
      Zero disables (clamping to a fixed number of frames instead).


.. _command-line-args-window-options:

Window Options
==============

``-w``, ``--window-border``
   Force opening with borders.

``-W``, ``--window-fullscreen``
   Force opening in full-screen mode.

``-p``, ``--window-geometry`` ``<sx>`` ``<sy>`` ``<w>`` ``<h>``
   Open with lower left corner at ``<sx>``, ``<sy>`` and width and height as ``<w>``, ``<h>``.

``-M``, ``--window-maximized``
   Force opening maximized.

``-con``, ``--start-console``
   Start with the console window open (ignored if ``-b`` is set), (Windows only).

``--no-native-pixels``
   Do not use native pixel size, for high resolution displays (MacBook ``Retina``).

``--no-window-focus``
   Open behind other windows and without taking focus.


.. _command-line-args-python-options:

Python Options
==============

``-y``, ``--enable-autoexec``
   Enable automatic Python script execution.

``-Y``, ``--disable-autoexec``
   Disable automatic Python script execution (Python-drivers & startup scripts), (default).


``-P``, ``--python`` ``<filepath>``
   Run the given Python script file.

``--python-text`` ``<name>``
   Run the given Python script text block.

``--python-expr`` ``<expression>``
   Run the given expression as a Python script.

``--python-console``
   Run Blender with an interactive console.

``--python-exit-code`` ``<code>``
   Set the exit-code in [0..255] to exit if a Python exception is raised
   (only for scripts executed from the command line), zero disables.

``--python-use-system-env``
   Allow Python to use system environment variables such as ``PYTHONPATH`` and the user site-packages directory.

``--addons`` ``<addon(s)>``
   Comma separated list (no spaces) of add-ons to enable in addition to any default add-ons.


.. _command-line-args-network-options:

Network Options
===============

``--online-mode``
   Allow internet access, overriding the preference.

``--offline-mode``
   Disallow internet access, overriding the preference.


.. _command-line-args-logging-options:

Logging Options
===============

``--log`` ``<match>``
   Enable logging categories, taking a single comma separated argument.
   Multiple categories can be matched using a ``.*`` suffix,
   so ``--log "wm.*"`` logs every kind of window-manager message.
   Sub-string can be matched using a ``*`` prefix and suffix,
   so ``--log "*undo*"`` logs every kind of undo-related message.
   Use "^" prefix to ignore, so ``--log "*,^wm.operator.*"`` logs all except for ``wm.operators.*``
   Use "*" to log everything.

``--log-level`` ``<level>``
   Set the logging verbosity level (higher for more details) defaults to 1,
   use -1 to log all levels.

``--log-show-basename``
   Only show file name in output (not the leading path).

``--log-show-backtrace``
   Show a back trace for each log message (debug builds only).

``--log-show-timestamp``
   Show a timestamp for each log message in seconds since start.

``--log-file`` ``<filepath>``
   Set a file to output the log to.


.. _command-line-args-debug-options:

Debug Options
=============

``-d``, ``--debug``
   Turn debugging on.

   * Enables memory error detection
   * Disables mouse grab (to interact with a debugger in some cases)
   * Keeps Python's ``sys.stdin`` rather than setting it to None

``--debug-value`` ``<value>``
   Set debug value of ``<value>`` on startup.


``--debug-events``
   Enable debug messages for the event system.

``--debug-ffmpeg``
   Enable debug messages from FFmpeg library.

``--debug-handlers``
   Enable debug messages for event handling.

``--debug-libmv``
   Enable debug messages from libmv library.

``--debug-cycles``
   Enable debug messages from Cycles.

``--debug-memory``
   Enable fully guarded memory allocation and debugging.

``--debug-jobs``
   Enable time profiling for background jobs.

``--debug-python``
   Enable debug messages for Python.

``--debug-depsgraph``
   Enable all debug messages from dependency graph.

``--debug-depsgraph-eval``
   Enable debug messages from dependency graph related on evaluation.

``--debug-depsgraph-build``
   Enable debug messages from dependency graph related on graph construction.

``--debug-depsgraph-tag``
   Enable debug messages from dependency graph related on tagging.

``--debug-depsgraph-no-threads``
   Switch dependency graph to a single threaded evaluation.

``--debug-depsgraph-time``
   Enable debug messages from dependency graph related on timing.

``--debug-depsgraph-pretty``
   Enable colors for dependency graph debug messages.

``--debug-depsgraph-uid``
   Verify validness of session-wide identifiers assigned to ID data-blocks.

``--debug-ghost``
   Enable debug messages for Ghost (Linux only).

``--debug-wintab``
   Enable debug messages for Wintab.

``--debug-gpu``
   Enable GPU debug context and information for OpenGL 4.3+.

``--debug-gpu-force-workarounds``
   Enable workarounds for typical GPU issues and disable all GPU extensions.

``--debug-gpu-compile-shaders``
   Compile all statically defined shaders to test platform compatibility.

``--debug-gpu-renderdoc``
   Enable Renderdoc integration for GPU frame grabbing and debugging.

``--debug-wm``
   Enable debug messages for the window manager, shows all operators in search, shows keymap errors.

``--debug-xr``
   Enable debug messages for virtual reality contexts.
   Enables the OpenXR API validation layer, (OpenXR) debug messages and general information prints.

``--debug-xr-time``
   Enable debug messages for virtual reality frame rendering times.

``--debug-all``
   Enable all debug messages.

``--debug-io``
   Enable debug messages for I/O (Collada, ...).


``--debug-fpe``
   Enable floating-point exceptions.

``--debug-exit-on-error``
   Immediately exit when internal errors are detected.

``--debug-freestyle``
   Enable debug messages for Freestyle.

``--disable-crash-handler``
   Disable the crash handler.

``--disable-abort-handler``
   Disable the abort handler.

``--verbose`` ``<verbose>``
   Set the logging verbosity level for debug messages that support it.


.. _command-line-args-gpu-options:

GPU Options
===========

``--gpu-backend``
   Force to use a specific GPU backend. Valid options: ``vulkan`` (experimental),  ``metal``,  ``opengl``.


.. _command-line-args-misc-options:

Misc Options
============

``--open-last``
   Open the most recently opened blend file, instead of the default startup file.

``--app-template`` ``<template>``
   Set the application template (matching the directory name), use ``default`` for none.

``--factory-startup``
   Skip reading the ``startup.blend`` in the users home directory.

``--enable-event-simulate``
   Enable event simulation testing feature ``bpy.types.Window.event_simulate``.


``--env-system-datafiles``
   Set the ``BLENDER_SYSTEM_DATAFILES`` environment variable.

``--env-system-scripts``
   Set the ``BLENDER_SYSTEM_SCRIPTS`` environment variable.

``--env-system-extensions``
   Set the ``BLENDER_SYSTEM_EXTENSIONS`` environment variable.

``--env-system-python``
   Set the ``BLENDER_SYSTEM_PYTHON`` environment variable.


``-noaudio``
   Force sound system to None.

``-setaudio``
   Force sound system to a specific device.
   ``None`` ``Default`` ``SDL`` ``OpenAL`` ``CoreAudio`` ``JACK`` ``PulseAudio`` ``WASAPI``.


``-c``, ``--command`` ``<command>``
   Run a command which consumes all remaining arguments.
   Use ``-c help`` to list all other commands.
   Pass ``--help`` after the command to see its help text.

   This implies ``--background`` mode.


``-h``, ``--help``
   Print this help text and exit.

``/?``
   Print this help text and exit (Windows only).

``-r``, ``--register``
   Register blend-file extension for current user, then exit (Windows & Linux only).

``--register-allusers``
   Register blend-file extension for all users, then exit (Windows & Linux only).

``--unregister``
   Unregister blend-file extension for current user, then exit (Windows & Linux only).

``--unregister-allusers``
   Unregister blend-file extension for all users, then exit (Windows & Linux only).

``-v``, ``--version``
   Print Blender version and exit.

``--``
   End option processing, following arguments passed unchanged. Access via Python's ``sys.argv``.


.. _command-line-args-argument-parsing:

Argument Parsing
================

Arguments must be separated by white space, eg:

.. code-block:: sh

   blender -ba test.blend

...will exit since ``-ba`` is an unknown argument.

.. _command-line-args-argument-order:

Argument Order
==============

Arguments are executed in the order they are given. eg:

.. code-block:: sh

   blender --background test.blend --render-frame 1 --render-output "/tmp"

...will not render to ``/tmp`` because ``--render-frame 1`` renders before the output path is set.

.. code-block:: sh

   blender --background --render-output /tmp test.blend --render-frame 1

...will not render to ``/tmp`` because loading the blend-file overwrites the render output that was set.

.. code-block:: sh

   blender --background test.blend --render-output /tmp --render-frame 1

...works as expected.

.. _command-line-args-environment-variables:

Environment Variables
=====================

:BLENDER_USER_RESOURCES:  Replace default directory of all user files.
                         Other ``BLENDER_USER_*`` variables override when set.
:BLENDER_USER_CONFIG:     Directory for user configuration files.
:BLENDER_USER_SCRIPTS:    Directory for user scripts.
:BLENDER_USER_EXTENSIONS: Directory for user extensions.
:BLENDER_USER_DATAFILES:  Directory for user data files (icons, translations, ..).

:BLENDER_SYSTEM_RESOURCES:  Replace default directory of all bundled resource files.
:BLENDER_SYSTEM_SCRIPTS:    Directory to add more bundled scripts.
:BLENDER_SYSTEM_EXTENSIONS: Directory for system extensions repository.
:BLENDER_SYSTEM_DATAFILES:  Directory to replace bundled datafiles.
:BLENDER_SYSTEM_PYTHON:     Directory to replace bundled Python libraries.
:OCIO:                      Path to override the OpenColorIO configuration file.
:TEMP:                      Store temporary files here (MS-Windows).
:TMPDIR:                    Store temporary files here (UNIX Systems).
                           The path must reference an existing directory or it will be ignored.


## command_line\index


#######################################
  Using Blender From The Command Line
#######################################

The *Console Window*, also called a *Terminal*, is an operating system text window that displays
messages about Blender's operations, status, and internal errors.

When Blender is manually started from a terminal,
Blender output is shown in the *Console Window* it is started from.

Use Cases:

- For :ref:`rendering animation <command_line-render>`.
- For automation and batch processing which require launching Blender
  with different :doc:`arguments </advanced/command_line/arguments>`.
- For Python development, to see the output of the ``print()`` function.
- If Blender exits unexpectedly, the messages may indicate the cause or error.
- When troubleshooting, to see the output of ``--debug`` messages.

See: :ref:`command_line-launch-index`
for specific instructions on launching Blender from the command line.

.. tip:: Closing the Blender Console Window

   Closing the *Console Window* will also close Blender, losing any unsaved work.


Launching from the Command Line
===============================

.. toctree::
   :hidden:

   launch/index.rst

- :doc:`launch/linux`
- :doc:`launch/macos`
- :doc:`launch/windows`


Arguments
=========

.. toctree::
   :hidden:

   Arguments <arguments.rst>

- :ref:`command-line-args-render-options`
- :ref:`command-line-args-cycles-render-options`
- :ref:`command-line-args-format-options`
- :ref:`command-line-args-animation-playback-options`
- :ref:`command-line-args-window-options`
- :ref:`command-line-args-python-options`
- :ref:`command-line-args-network-options`
- :ref:`command-line-args-logging-options`
- :ref:`command-line-args-debug-options`
- :ref:`command-line-args-gpu-options`
- :ref:`command-line-args-misc-options`


Workflows
=========

.. toctree::

   render.rst


## command_line\render

.. _command_line-render:

*******************************
Rendering From The Command Line
*******************************

In some situations we want to increase the render speed,
access Blender remotely to render something or build scripts that use the command line.

One advantage of using the command line is that we do not need a graphical display
(no need for X server on Linux for example)
and consequently we can render via a remote shell (typically SSH).

- See :doc:`Command Line Arguments </advanced/command_line/arguments>`
  for a full list of arguments
  (for example to specify which scene to render, the end frame number, etc.), or simply run:

.. code-block:: sh

   blender --help

- See :ref:`Command Line Launching <command_line-launch-index>`
  for specific instructions on launching Blender from the command line.

.. note::

   Arguments are executed in the order they are given!

   The following command will not work, since the output and extension are set after Blender is told to render:

   .. code-block:: sh

      blender -b file.blend -a -x 1 -o //render

   The following command will behave as expected:

   .. code-block:: sh

      blender -b file.blend -x 1 -o //render -a

   **Always** position ``-f`` or ``-a`` as the last arguments.


Single Image
------------

.. code-block:: sh

   blender -b file.blend -f 10

``-b``
   Render in the background (without UI).
``file.blend``
   Path to the blend-file to render.
``-f 10``
   Render only the 10th frame.

.. code-block:: sh

   blender -b file.blend -o /project/renders/frame_##### -F OPEN_EXR -f -2

``-o /project/renders/frame_#####``
   Path of where to save the rendered image, using five padded zeros for the frame number.
``-F OPEN_EXR``
   Override the image format specified in the blend-file and save to an OpenEXR image.
``-f -2``
   Render only the second last frame.

.. warning::

   Arguments are case sensitive! ``-F`` and ``-f`` are not the same.


Animation
---------

.. code-block:: sh

   blender -b file.blend -a

``-a``
   Render the whole animation using all the settings saved in the blend-file.

.. code-block:: sh

   blender -b file.blend -E CYCLES -s 10 -e 500 -t 2 -a

``-E CYCLES``
   Use the "Cycles Render" engine.
   For a list of available render engines, run ``blender -E help``.
``-s 10 -e 500``
   Set the start frame to ``10`` and the end frame to ``500``.
``-t 2``
   Use only two threads.


Cycles
------

In addition to the options above, which apply to all render engines,
Cycles has additional options to further control its behavior.
See :ref:`Cycles Render Options <command-line-args-cycles-render-options>`


## command_line\launch\index

.. _command_line-launch-index:

###################################
  Launching from the Command Line
###################################

.. toctree::
   :maxdepth: 2

   linux.rst
   macos.rst
   windows.rst


## command_line\launch\linux


*****
Linux
*****

Quick Start
===========

Open a terminal, then go to the directory where Blender is installed,
and run Blender like this:

.. code-block:: sh

   cd <blender installation directory>
   ./blender

If you have Blender installed in your ``PATH``
(usually when Blender is installed through a distribution package), you can simply run:

.. code-block:: sh

   blender


Details
=======

Depending on your desktop environment setup, a Blender icon may appear on your desktop or
an entry for Blender is added to your menu after you install Blender.

Many desktop environments support the ability to "Run in terminal".

.. figure:: /images/advanced_command-line_launch_linux_kde.png

   Configuring the KDE menu icon to start Blender from a terminal.

This screenshot shows Blender started from a Linux Terminal and
the resulting text output written to it:

.. figure:: /images/advanced_command-line_launch_linux_console.png

   Starting Blender from a Linux terminal window.


## command_line\launch\macos


*****
macOS
*****

Quick Start
===========

Open the terminal application,
and run the executable within the app bundle, with commands like this:

.. code-block:: sh

   cd /Applications/Blender.app/Contents/MacOS
   ./Blender

If you need to do this often, you can add this directory to your ``PATH``.

For that you can run the following procedure:

#. Open up a Terminal.
#. Run the following command: ``sudo nano /etc/paths``.
#. Enter your password, when prompted.
#. Go to the bottom of the file, and enter ``/Applications/Blender.app/Contents/MacOS``.
#. Enter :kbd:`Ctrl-X` to quit.
#. Enter :kbd:`Y` to save the modified buffer.

If you then open a new terminal, the following command will work:

.. code-block:: sh

   Blender


Details
=======

macOS uses "files" with the ``.app`` extension called *applications*.
These files are actually folders that appear as files in Finder.
In order to run Blender you will have to specify that path to the Blender executable inside this folder,
to get all output printed to the terminal.
You can start a terminal from :menuselection:`Applications --> Utilities`.
The path to the executable in the ``.app`` folder is ``./Blender.app/Contents/MacOS/Blender``.

If you have Blender installed in the Applications folder, the following command can be used:

.. parsed-literal:: /Applications/Blender.app/Contents/MacOS/Blender

.. figure:: /images/advanced_command-line_launch_macos_mac.png

   Starting Blender from a macOS console window.


## command_line\launch\windows


*******
Windows
*******

Quick Start
===========

Open the Command Prompt, go to the directory where Blender is installed,
and then run Blender:

.. code-block:: bat

   cd c:\<blender installation directory>
   blender

You can also add the Blender folder to your system ``PATH`` so that you do not have to ``cd`` to it each time.


Details
=======

When Blender is started on a Microsoft Windows operating system, the *Console Window*
(called the Command Prompt) is first created as a separate window on the desktop.
The main Blender window will also appear and the *Console Window* will then be toggled off.
To display the console again, go to :menuselection:`Window --> Toggle System Console`.

To start Blender from the command line you need to open an instance of Command Prompt.
To do this, type :kbd:`OSKey-R` then type ``cmd``; this will open the Command Prompt window.
You then need to find the path to the Blender executable. If you installed Blender via the installer
then it can be found here:

.. parsed-literal:: C:\\Program Files\\Blender Foundation\\Blender\\blender.exe

.. figure:: /images/advanced_command-line_launch_windows_console.png

   Blender's Console Window on Microsoft Windows.

The screenshot shows the Blender *Console Window* on Microsoft Windows directly after starting
Blender and then a short while later after opening a file along with the relevant messages.


## extensions\addons

.. Mark as "orphan" until extensions is out of beta.

.. index:: Add-ons Extensions
.. index:: Add-ons
.. .. _bpy.types.Addon:
.. .. _bpy.ops.wm.addon:
.. .. _bpy.types.WindowManager.addon:

*******
Add-ons
*******

*Add-ons* let you extend Blender's functionality using Python.
Most of the time you can get add-ons as part of the :doc:`Extensions <index>` system.

.. tip::

   If the Add-on does not activate when enabled,
   check the :doc:`Console window </advanced/command_line/index>`
   for any errors that may have occurred.

User-Defined Add-on Path
========================

You can also create a personal directory containing new add-ons and configure your files path in
the *File Paths* section of the *Preferences*. To create a personal script directory:

#. Create an empty directory in a location of your choice (e.g. ``my_scripts``).
#. Add a subdirectory under ``my_scripts`` called ``addons``
   (it *must* have this name for Blender to recognize it).
#. Open the *File Paths* section of the *Preferences*.
#. Set the *Scripts* file path to point to your script directory (e.g. ``my_scripts``).
#. Save the preferences and restart Blender for it to recognize the new add-on location.

Now when you install add-ons you can select the *Target Path* when installing 3rd party scripts.
Blender will copy newly installed add-ons under the directory selected in your Preferences.


Internet Access
===============

If the add-on needs to use internet, it should check for the (read-only) property ``bpy.app.online_access``.
This option is controlled by Preferences, which can be overriding via command-line
(``--offline-mode`` / ``--online-mode``).

For better error messages, you can check also for ``bpy.app.online_access_overriden``,
to determine whether users can turn :ref:`Allow Online Access <bpy.types.PreferencesSystem.use_online_access>`
on the preferences, or not.

Blender itself doesn't block internet access based on this setting. It is up to the add-ons to respect it.


Bundle Dependencies
===================

For add-ons to be bundled as extensions, they must be self-contained.
That means they must come with all its dependencies. In particular 3rd party Python modules.

There are a few options for this:

Bundle with :doc:`Python Wheels <./python_wheels>`.
   This is the recommended way to bundle dependencies.

Bundle other add-ons together.
   This is recommended if an add-on depends on another add-on.

   Make sure that both the individual and the combined add-on
   check for already registered types (Operators, Panels, ...).
   This avoids duplication of operators and panels on the interface
   if the add-ons are installed as a bundle and individually.

Bundle with `Vendorize <https://pypi.org/project/vendorize>`__
   This can be used as a way to bundle a pure Python dependencies as a sub-module.

   This has the advantage of avoiding version conflicts although it requires some work to setup each package.


.. This section is reference for legacy add-on installation.
.. _bpy.ops.preferences.addon_install:

Legacy vs Extension Add-ons
===========================

With the introduction of Extensions in Blender 4.2, the old way of creating add-ons is considered deprecated.
While the changes are rather small they impact existing add-ons.

In order to allow a smooth transition process, the so-called legacy add-ons will continue to be supported by Blender.
They can be installed via :doc:`Install legacy Add-on </editors/preferences/extensions>` button in the User
Preferences.

All add-on maintainers are urged to convert the add-ons they want to share, so they are future proof and can support
features like updating from the extensions platform.


Converting a Legacy Add-on into an Extension
--------------------------------------------

#. Create a :doc:`manifest file <./getting_started>`.
#. Remove the ``bl_info`` information (this is now in the manifest).
#. Replace all references to the module name to ``__package__``.
#. Make all module imports to use relative import.
#. Use `wheels <https://pythonwheels.com/>`__ to pack your external Python dependencies.
#. Remember to test it thoroughly.

.. note::

   For testing it is import to :doc:`install the extension from disk </editors/preferences/extensions>` and check if
   everything is working well. This will get you as close to the final experience as possible.


Extensions and Namespace
------------------------

The legacy add-ons would use their module name to access the preferences. This could lead to a name clash when
extensions with the same name (from different repositories) would be installed.
To prevent this conflict, the repository name is now part of the namespace.

For example, now instead of ``kitsu`` the module name would be ``bl_ext.{repository_module_name}.kitsu`` instead.

This has a few implications for preferences and module imports.


User Preferences and ``__package__``
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Add-ons can define their own preferences which use the package name as an identifier.
This can be accessed using ``__package__``.

This was already supported in the legacy add-ons, but not reinforced.
As such this can break backward compatibility.

Before:

   .. code-block:: python

      class KitsuPreferences(bpy.types.AddonPreferences):
          bl_idname = "kitsu"
          # ... snip ...

      # Access with:
      addon_prefs = bpy.context.preferences.addons["kitsu"]

Now:

   .. code-block:: python

      class KitsuPreferences(bpy.types.AddonPreferences):
          bl_idname = __package__
          # ... snip ...

      # Access with:
      addon_prefs = bpy.context.preferences.addons[__package__]

Sub-packages
   An add-on that defines sub-packages (sub-directories with their own ``__init__.py`` file)
   that needs to use this identifier will have to import the top-level package using a relative import.

   .. code-block:: python

      from .. import __package__ as base_package

   Then ``base_package`` can be used instead of ``__package__``.
   The ``..`` imports relative to the packages parent, sub-sub-packages must use ``...`` and so on.

.. note::

   - The value of ``__package__`` will vary between systems so it should never be replaced with a literal string.
   - Extensions must not manipulate the value of ``__package__`` as this may cause unexpected behavior or errors.


Relative Imports
^^^^^^^^^^^^^^^^

   :before: ``from kitsu import utils``
   :now: ``from . import utils``

Importing packages within the add-on module need to use relative paths.
This is a standard Python feature and only applicable for add-ons that have multiple folders.

This was already supported in the legacy add-ons, but not reinforced. As such this can break backward compatibility.


## extensions\command_line_arguments

.. DO NOT EDIT THIS FILE, GENERATED BY 'blender_help_extract_extension.py'

   CHANGES TO THIS FILE MUST BE MADE IN BLENDER'S SOURCE CODE, SEE:
   https://projects.blender.org/blender/blender-addons-contrib/src/branch/main/bl_pkg/bl_extension_cli.py

.. _command_line-args-extensions:

*********************************
Extensions Command Line Arguments
*********************************

.. NOTE: usage is commented, currently unhelpful.
       blender --command extension [-h]

                                   ...

Command for managing Blender extensions.

options:
  -h, --help            show this help message and exit

subcommands:


  `Package Management`_
    :list:                List all packages.
    :sync:                Synchronize with remote repositories.
    :update:              Upgrade any outdated packages.
    :install:             Install packages.
    :install-file:        Install package from file.
    :remove:              Remove packages.

  `Repository Management`_
    :repo-list:           List repositories.
    :repo-add:            Add repository.
    :repo-remove:         Remove repository.

  `Extension Creation`_
    :build:               Build a package.
    :validate:            Validate a package.
    :server-generate:     Create a listing from all packages.


Package Management
==================

.. _command-line-args-extension-list:

Subcommand: ``list``
--------------------

usage::

       blender --command extension list [-h] [-s]

List packages from all enabled repositories.

options:
  -h, --help  show this help message and exit
  -s, --sync  Sync the remote directory before performing the action.

.. _command-line-args-extension-sync:

Subcommand: ``sync``
--------------------

usage::

       blender --command extension sync [-h]

Download package information for remote repositories.

options:
  -h, --help  show this help message and exit

.. _command-line-args-extension-update:

Subcommand: ``update``
----------------------

usage::

       blender --command extension update [-h] [-s]

Download and update any outdated packages.

options:
  -h, --help  show this help message and exit
  -s, --sync  Sync the remote directory before performing the action.

.. _command-line-args-extension-install:

Subcommand: ``install``
-----------------------

usage::

       blender --command extension install [-h] [-s] [-e] [--no-prefs]
                                           PACKAGES

positional arguments:
  :PACKAGES:      The packages to operate on (separated by ``,`` without spaces).

options:
  -h, --help    show this help message and exit
  -s, --sync    Sync the remote directory before performing the action.
  -e, --enable  Enable the extension after installation.
  --no-prefs    Treat the user-preferences as read-only,
                preventing updates for operations that would otherwise modify them.
                This means removing extensions or repositories for example, wont update the user-preferences.

.. _command-line-args-extension-install-file:

Subcommand: ``install-file``
----------------------------

usage::

       blender --command extension install-file [-h] -r REPO [-e] [--no-prefs]
                                                FILE

Install a package file into a local repository.

positional arguments:
  :FILE:                  The packages file.

options:
  -h, --help            show this help message and exit
  -r REPO, --repo REPO  The repository identifier.
  -e, --enable          Enable the extension after installation.
  --no-prefs            Treat the user-preferences as read-only,
                        preventing updates for operations that would otherwise modify them.
                        This means removing extensions or repositories for example, wont update the user-preferences.

.. _command-line-args-extension-remove:

Subcommand: ``remove``
----------------------

usage::

       blender --command extension remove [-h] [--no-prefs] PACKAGES

Disable & remove package(s).

positional arguments:
  :PACKAGES:    The packages to operate on (separated by ``,`` without spaces).

options:
  -h, --help  show this help message and exit
  --no-prefs  Treat the user-preferences as read-only,
              preventing updates for operations that would otherwise modify them.
              This means removing extensions or repositories for example, wont update the user-preferences.


Repository Management
=====================

.. _command-line-args-extension-repo-list:

Subcommand: ``repo-list``
-------------------------

usage::

       blender --command extension repo-list [-h]

List all repositories stored in Blender's preferences.

options:
  -h, --help  show this help message and exit

.. _command-line-args-extension-repo-add:

Subcommand: ``repo-add``
------------------------

usage::

       blender --command extension repo-add [-h] [--name NAME]
                                            [--directory DIRECTORY]
                                            [--url URL] [--cache BOOLEAN]
                                            [--clear-all] [--no-prefs]
                                            ID

Add a new local or remote repository.

positional arguments:
  :ID:                    The repository identifier.

options:
  -h, --help            show this help message and exit
  --name NAME           The name to display in the interface (optional).
  --directory DIRECTORY
                        The directory where the repository stores local files (optional).
                        When omitted a directory in the users directory is automatically selected.
  --url URL             The URL, for remote repositories (optional).
                        When omitted the repository is considered "local"
                        as it is not connected to an external repository,
                        where packages may be installed by file or managed manually.
  --cache BOOLEAN       Use package cache (default=1).
  --clear-all           Clear all repositories before adding, simplifies test setup.
  --no-prefs            Treat the user-preferences as read-only,
                        preventing updates for operations that would otherwise modify them.
                        This means removing extensions or repositories for example, wont update the user-preferences.

.. _command-line-args-extension-repo-remove:

Subcommand: ``repo-remove``
---------------------------

usage::

       blender --command extension repo-remove [-h] [--no-prefs] ID

Remove a repository.

positional arguments:
  :ID:          The repository identifier.

options:
  -h, --help  show this help message and exit
  --no-prefs  Treat the user-preferences as read-only,
              preventing updates for operations that would otherwise modify them.
              This means removing extensions or repositories for example, wont update the user-preferences.


Extension Creation
==================

.. _command-line-args-extension-build:

Subcommand: ``build``
---------------------

usage::

       blender --command extension build [-h] [--source-dir SOURCE_DIR]
                                         [--output-dir OUTPUT_DIR]
                                         [--output-filepath OUTPUT_FILEPATH]
                                         [--split-platforms] [--verbose]

Build a package in the current directory.

options:
  -h, --help            show this help message and exit
  --source-dir SOURCE_DIR
                        The package source directory containing a ``blender_manifest.toml`` manifest.

                        Default's to the current directory.
  --output-dir OUTPUT_DIR
                        The package output directory.

                        Default's to the current directory.
  --output-filepath OUTPUT_FILEPATH
                        The package output filepath (should include a ``.zip`` extension).

                        Defaults to a name created using the ``id`` from the manifest.
  --split-platforms     Build a separate package for each platform.
                        Adding the platform as a file name suffix (before the extension).

                        This can be useful to reduce the upload size of packages that bundle large
                        platform-specific modules (``*.whl`` files).
  --verbose             Include verbose output.

.. _command-line-args-extension-validate:

Subcommand: ``validate``
------------------------

usage::

       blender --command extension validate [-h] [SOURCE_PATH]

Validate the package meta-data in the current directory.

positional arguments:
  :SOURCE_PATH:  The package source path (either directory containing package files or the package archive).
               This path must containing a ``blender_manifest.toml`` manifest.

               Defaults to the current directory.

options:
  -h, --help   show this help message and exit

.. _command-line-args-extension-server-generate:

Subcommand: ``server-generate``
-------------------------------

usage::

       blender --command extension server-generate [-h] --repo-dir REPO_DIR

Generate a listing of all packages stored in a directory.
This can be used to host packages which only requires static-file hosting.

options:
  -h, --help           show this help message and exit
  --repo-dir REPO_DIR  The remote repository directory.


## extensions\getting_started

.. index:: Extensions

************************
How to Create Extensions
************************

Creating an extension takes only a few steps:

#. Create a directory for your extension and populate it with the add-on code or theme file.
#. Add a `blender_manifest.toml <#manifest>`__  file with all the required meta-data ``(name, maintainer, ...)``.
#. Compress the directory as a ``.zip`` file.
#. :doc:`Install from Disk </editors/preferences/extensions>` to test if everything is working well.
#. `Upload the zip file <https://extensions.blender.org/submit/>`__ (this step requires Blender ID).

The extension will be held for `review <https://extensions.blender.org/approval-queue/>`__,
and published once the moderation team approves it.

Extension files
===============

An extension is shared as a ``.zip`` archive containing a manifest file and other files.
The expected files depend on the extension type.

Add-on extension
----------------

:doc:`Add-ons <addons>` need at least the manifest and an ``__init__.py`` file,
while more complex add-ons have a few different .py files or wheels together.

.. code-block:: text

   my_extension-0.0.1.zip
   ├─ __init__.py
   ├─ blender_manifest.toml
   └─ (...)

Theme extension
---------------

A theme extension only needs the manifest and the .xml theme file.

.. code-block:: text

   my_extension-0.0.1.zip
   ├─ blender_manifest.toml
   └─ theme.xml

.. note::

   Extensions can optionally have all its files inside a folder (inside the archive).
   This is a common behavior when saving a repository as ZIP from version-control platforms.


.. _extensions-manifest:

Manifest
========

A manifest is a file with all the meta-data required for an extension to be processed.
This example is a good starting point to the ``blender_manifest.toml`` that should be inside the ``.zip``.

.. code-block:: toml

   schema_version = "1.0.0"

   # Example of manifest file for a Blender extension
   # Change the values according to your extension
   id = "my_example_extension"
   version = "1.0.0"
   name = "Test Extension"
   tagline = "This is another extension"
   maintainer = "Developer name <email@address.com>"
   # Supported types: "add-on", "theme"
   type = "add-on"

   # Optional link to documentation, support, source files, etc
   # website = "https://extensions.blender.org/add-ons/my-example-package/"

   # Optional list defined by Blender and server, see:
   # https://docs.blender.org/manual/en/dev/advanced/extensions/tags.html
   tags = ["Animation", "Sequencer"]

   blender_version_min = "4.2.0"
   # # Optional: Blender version that the extension does not support, earlier versions are supported.
   # # This can be omitted and defined later on the extensions platform if an issue is found.
   # blender_version_max = "5.1.0"

   # License conforming to https://spdx.org/licenses/ (use "SPDX: prefix)
   # https://docs.blender.org/manual/en/dev/advanced/extensions/licenses.html
   license = [
     "SPDX:GPL-2.0-or-later",
   ]
   # Optional: required by some licenses.
   # copyright = [
   #   "2002-2024 Developer Name",
   #   "1998 Company Name",
   # ]

   # Optional list of supported platforms. If omitted, the extension will be available in all operating systems.
   # platforms = ["windows-x64", "macos-arm64", "linux-x64"]
   # Other supported platforms: "windows-arm64", "macos-x64"

   # Optional: bundle 3rd party Python modules.
   # https://docs.blender.org/manual/en/dev/advanced/extensions/python_wheels.html
   # wheels = [
   #   "./wheels/hexdump-3.3-py3-none-any.whl",
   #   "./wheels/jsmin-3.0.1-py3-none-any.whl",
   # ]

   # # Optional: add-ons can list which resources they will require:
   # # * files (for access of any filesystem operations)
   # # * network (for internet access)
   # # * clipboard (to read and/or write the system clipboard)
   # # * camera (to capture photos and videos)
   # # * microphone (to capture audio)
   # #
   # # If using network, remember to also check `bpy.app.online_access`
   # # https://docs.blender.org/manual/en/dev/advanced/extensions/addons.html#internet-access
   # #
   # # For each permission it is important to also specify the reason why it is required.
   # # Keep this a single short sentence without a period (.) at the end.
   # # For longer explanations use the documentation or detail page.
   #
   # [permissions]
   # network = "Need to sync motion-capture data to server"
   # files = "Import/export FBX from/to disk"
   # clipboard = "Copy and paste bone transforms"

   # Optional: build settings.
   # https://docs.blender.org/manual/en/dev/advanced/extensions/command_line_arguments.html#command-line-args-extension-build
   # [build]
   # paths_exclude_pattern = [
   #   "__pycache__/",
   #   "/.git/",
   #   "/*.zip",
   # ]

Required values:

   :blender_version_min: Minimum supported Blender version - use at least ``4.2.0``.
   :id: Unique identifier for the extension.
   :license: List of :doc:`licenses <licenses>`, use `SPDX license identifier <https://spdx.org/licenses/>`__.
   :maintainer: Maintainer of the extension.
   :name: Complete name of the extension.
   :schema_version: Internal version of the file format - use ``1.0.0``.
   :tagline: One-line short description - cannot end with punctuation.
   :type: "add-on", "theme".
   :version: Version of the extension - must follow `semantic versioning <https://semver.org/>`__.

Optional values:

   :blender_version_max: Blender version that the extension does not support, earlier versions are supported.
   :website: Website for the extension.
   :copyright: Some licenses require a copyright, copyrights must be "Year Name" or "Year-Year Name".
   :tags: List of tags. See the :doc:`list of available tags <./tags>`.
   :platforms:
      List of supported platforms. If omitted, the extension will be available in all operating systems.
      The available options are
      ["windows-x64", "windows-arm64", "macos-x64", "macos-arm64", "linux-x64"]
   :wheels: List of relative file-paths :doc:`Python Wheels <./python_wheels>`.
   :permissions:
      Add-ons can list which resources they require. The available options are
      *files*, *network*, *clipboard*, *camera*, *microphone*.
      Each permission should be followed by an explanation (short single-sentence with no end punctuation).

Optional values for "build":

   These values are only used by the :ref:`build <command-line-args-extension-build>` sub-command.

   :paths:
      A list of file-paths relative to the manifest to include when building the package.

   :paths_exclude_pattern:
      A list of file-path patterns to exclude include when building the package.

      The pattern matching is compatible with `gitignore <https://git-scm.com/docs/gitignore>`__.

      Note that setting this value isn't supported when ``paths`` is also declared.

   If the ``[build]`` table isn't declared the following default is used:

   .. code-block:: toml

      [build]
      paths_exclude_pattern = [
        "__pycache__/",
        ".*",
        "*.zip",
      ]

Reserved:
   These values **must not** be declared in a TOML and are reserved for internal use.

   - ``[build.generated]``


.. note::

   All the values present in the manifest file must be filled
   (i.e., cannot be empty, nor text ``""``, nor list ``[]``).

   If you don't want to set one of the optional values just exclude it from the manifest altogether.

Command-line
============

Extensions can be built, validated & installed via command-line.

.. note::

   Extension commands currently require a daily build of Blender with extensions enabled in the preferences.

To build the package defined in the current directory use the following commands:

.. code:: bash

   blender --command extension build

See :ref:`build <command-line-args-extension-build>` docs.

---

To validate the manifest without building the package:

.. code:: bash

   blender --command extension validate

You may also validate a package without having to extract it first.

.. code:: bash

   blender --command extension validate add-on-package.zip

See :ref:`validate <command-line-args-extension-validate>` docs.

.. seealso::

   :ref:`command_line-args-extensions`.


Third party extension sites
===========================

Third party sites that wish to support extensions in Blender can do so in two ways:

#. Fork the entire `Extensions Website <https://projects.blender.org/infrastructure/extensions-website>`__
   as a start point; or
#. Host a JSON file listing all the packages of your repository.

To generate a valid JSON file you can use the command-line tool:

.. code:: bash

   blender --command extension server-generate --repo-dir=/path/to/packages

This creates a listing from all the packages found in the specified location.

See :ref:`server-generate <command-line-args-extension-server-generate>` docs.

Example of what the JSON is expected to look like:

.. code:: json

   {
     "version": "v1",
     "blocklist": [],
     "data": [
      {
         "id": "blender_kitsu",
         "name": "Blender Kitsu",
         "tagline": "Pipeline management for projects collaboration",
         "version": "0.1.5-alpha+f52258de",
         "type": "add-on",
         "archive_size": 856650,
         "archive_hash": "sha256:3d2972a6f6482e3c502273434ca53eec0c5ab3dae628b55c101c95a4bc4e15b2",
         "archive_url": "https://extensions.blender.org/add-ons/blender-kitsu/0.1.5-alpha+f52258de/download/",
         "blender_version_min": "4.2.0",
         "maintainer": "Blender Studio",
         "tags": ["Pipeline"],
         "license": ["SPDX:GPL-3.0-or-later"],
         "website": "https://extensions.blender.org/add-ons/blender-kitsu/",
         "schema_version": "1.0.0"
      }
      ]
  }

Just like for the manifest file, the optional fields (e.g., ``blender_version_max``) are either to have a value
or should be omitted from the entries.

For the official Extensions Platform, the ``website`` value is the page of the extension in the online platform.
Even if the manifest points to the project specific website.

.. note::

   Any remote repository is expected to follow the latest `API <https://extensions.blender.org/api/swagger/>`__.


## extensions\index

.. _extensions-index:
.. index:: Extensions

*******************
Creating Extensions
*******************

Extensions are **add-ons** or **themes** used to extend the core functionality of Blender.
They are shared in online platforms, and can be installed and updated from within Blender.

The official extensions platform for the Blender project is `extensions.blender.org <https://extensions.blender.org>`__.
Other third party sites can also be supported, as long as they follow the Extensions Platform specification.

.. seealso::

   For the extension settings, and how to manage them, refer to the
   :doc:`User Preferences </editors/preferences/extensions>`.

.. toctree::
   :maxdepth: 1

   Getting started <getting_started.rst>
   Compatible licenses <licenses.rst>
   Supported tags <tags.rst>
   Add-ons <addons.rst>
   Python Wheels <python_wheels.rst>
   Command Line Arguments <command_line_arguments.rst>


## extensions\licenses

.. index:: Licenses

******************
Extension Licenses
******************

For add-ons and themes the recommended license is
`GNU General Public License v2.0 or later <https://spdx.org/licenses/GPL-2.0-or-later.html>`__.
For assets, the required license is `Public Domain (CC0) <https://spdx.org/licenses/CC0-1.0.html>`__.

The `Blender Extensions Platform <https://extensions.blender.org>`__ only supports
free and open source extensions compatible with Blender's license:
`GNU General Public License v3.0 or later <https://spdx.org/licenses/GPL-3.0-or-later.html>`__.

This allows extensions to be packed with Blender and distributed in compliance
with the governing principles of the `Blender license <https://www.blender.org/about/license/>`__.

More GPL and LGPL Licenses
==========================

Some third-party add-on libraries may require a different compatible license.

In those cases a few variant versions of GNU GPL are also accepted:

.. list-table::
   :header-rows: 1

   * - Identifier
     - License
   * - SPDX:GPL-2.0-or-later
     - `GNU General Public License v2.0 or later <https://spdx.org/licenses/GPL-2.0-or-later.html>`__
   * - SPDX:GPL-3.0-or-later
     - `GNU General Public License v3.0 or later <https://spdx.org/licenses/GPL-3.0-or-later.html>`__
   * - SPDX:LGPL-2.1-or-later
     - `GNU Lesser General Public License v2.1 or later <https://spdx.org/licenses/LGPL-2.1-or-later.html>`__
   * - SPDX:LGPL-3.0-or-later
     - `GNU Lesser General Public License v3.0 or later <https://spdx.org/licenses/LGPL-3.0-or-later.html>`__

More Compatible Licenses
========================

In some exceptional cases other licenses may be required. Extensions are still accepted under these licenses:

.. list-table::
   :header-rows: 1

   * - Identifier
     - License
   * - SPDX:BSD-1-Clause
     - `BSD 1-Clause "Simplified" License <https://spdx.org/licenses/BSD-1-Clause.html>`__
   * - SPDX:BSD-2-Clause
     - `BSD 2-Clause "Simplified" License <https://spdx.org/licenses/BSD-2-Clause.html>`__
   * - SPDX:BSD-3-Clause
     - `BSD 3-Clause "New" or "Revised" License <https://spdx.org/licenses/BSD-3-Clause.html>`__
   * - SPDX:BSL-1.0
     - `Boost Software License 1.0 <https://spdx.org/licenses/BSL-1.0.html>`__
   * - SPDX:MIT
     - `MIT License <https://spdx.org/licenses/MIT.html>`__
   * - SPDX:MIT-0
     - `MIT No Attribution <https://spdx.org/licenses/MIT-0.html>`__
   * - SPDX:MPL-2.0
     - `Mozilla Public License 2.0 <https://spdx.org/licenses/MPL-2.0.html>`__
   * - SPDX:Pixar
     - `Pixar License <https://spdx.org/licenses/Pixar.html>`__
   * - SPDX:Zlib
     - `Zlib License <https://spdx.org/licenses/Zlib.html>`__


## extensions\python_wheels


*************
Python Wheels
*************

.. TODO:

   - Guidelines for wheel selecting the version to use.
   - Finalize a policy for how conflicting versions of a wheel are handled.


`Python wheels <https://pythonwheels.com/>`__ (``*.whl``) are the standard way of distributing Python modules.
They are supported in Blender to make self-contained Python :ref:`Extensions <extensions-index>`.


Guidelines
==========

- By convention, always locate the files under ``./wheels/``.


Requirements
============

- Wheels must be bundled unmodified from `Python's package index <https://pypi.org>`__.
- Wheels must include their dependencies.
- Wheels filenames must match Python's binary distribution specification:
  `see docs <https://packaging.python.org/en/latest/specifications/binary-distribution-format/#file-name-convention>`__.
  *Wheels downloaded from Python's package index will follow this convention.*
- Use forward slashes as path separators when listing them on the
  :ref:`manifest <extensions-manifest>`.


How to Bundle Wheels
====================

Python wheels  (``*.whl``) can be bundled using the following steps.

Downloading Wheels
   Download the wheel to the directory ``./wheels/``.

   For wheels that are platform independent this example downloads ``jsmin``:

   .. code-block:: console

      pip wheel jsmin -w ./wheels


   For wheels that contain binary compiled files, wheels for all supported platforms should be included:

   This example downloads ``pillow`` - the popular image manipulation module.

   .. code-block:: console

      pip download pillow --dest ./wheels --only-binary=:all: --python-version=3.11 --platform=macosx_11_0_arm64
      pip download pillow --dest ./wheels --only-binary=:all: --python-version=3.11 --platform=manylinux_2_28_x86_64
      pip download pillow --dest ./wheels --only-binary=:all: --python-version=3.11 --platform=win_amd64

   The available platform identifiers are listed on
   `pillow's download page <https://pypi.org/project/pillow/#files>`__.

Update the Manifest
   In ``blender_manifest.toml`` include the wheels as a list of paths, e.g.

   .. code-block:: toml

      wheels = [
         "./wheels/pillow-10.3.0-cp311-cp311-macosx_11_0_arm64.whl",
         "./wheels/pillow-10.3.0-cp311-cp311-manylinux_2_28_x86_64.whl",
         "./wheels/pillow-10.3.0-cp311-cp311-win_amd64.whl",
      ]

   Now installing the package will extract the wheel into the extensions own ``site-packages`` directory.

Running
   Once the extension has been installed you can check the module is being loaded by importing it in the
   Python console and printing it's location:

   .. code-block:: python

      import PIL
      print(PIL.__file__)


## extensions\tags

.. index:: Tags

***************
Extensions Tags
***************

A different set of tags is available for the different extensions types.
This is the list of the tags currently supported by the `Blender Extensions Platform <https://extensions.blender.org/>`_:

Add-ons
=======

* 3D View
* Add Curve
* Add Mesh
* Animation
* Bake
* Camera
* Compositing
* Development
* Game Engine
* Geometry Nodes
* Grease Pencil
* Import-Export
* Lighting
* Material
* Modeling
* Mesh
* Node
* Object
* Paint
* Pipeline
* Physics
* Render
* Rigging
* Scene
* Sculpt
* Sequencer
* System
* Text Editor
* Tracking
* User Interface
* UV

Themes
======

* Dark
* Light
* Colorful
* Inspired By
* Print
* Accessibility
* High Contrast


## scripting\addon_tutorial


.. This document is an exception to the rule of not having tutorials in the reference manual.
   Since this doesn't quite belong on the API docs either.
   It's important we have at least one place with good basic info on how to write an add-on.
   -- ideasman42

***************
Add-on Tutorial
***************

Intended Audience
=================

This tutorial is designed to help technical artists or developers learn to extend Blender.
An understanding of the basics of Python is expected for those working through this tutorial.


Prerequisites
-------------

Before going through the tutorial you should...

- Be familiar with the basics of working in Blender.
- Know how to run a script in Blender's Text editor.
- Have an understanding of Python primitive types (integer, Boolean, string, list, tuple, dictionary, and set).
- Be familiar with the concept of Python modules.
- Have a basic understanding of classes (object orientation) in Python.

Suggested reading before starting this tutorial.

- `Dive Into Python <https://finderiko.com/python-book>`__ sections (1, 2, 3, 4, and 7).
- `Blender API Quickstart <https://docs.blender.org/api/current/info_quickstart.html>`__
  to help become familiar with Blender/Python basics.

To best troubleshoot any error message Python prints while writing scripts, you run Blender from a terminal.
See `Use The Terminal <https://docs.blender.org/api/current/info_tips_and_tricks.html#use-the-terminal>`__.

.. tip::

   You can enable :ref:`Developer Extras <bpy.types.PreferencesView.show_developer_ui>`
   in the preferences to enable features that make developing add-ons easier.


Documentation Links
===================

While going through the tutorial, you may want to look into our reference documentation.

- `Blender API Overview <https://docs.blender.org/api/current/info_overview.html>`__:
  This document is rather detailed but helpful if you want to know more on a topic.
- :mod:`blender_api:bpy.context` API reference --
  Handy to have a list of available items your script may operate on.
- :class:`blender_api:bpy.types.Operator` --
  The following add-ons define operators, these docs give details and more examples of operators.


What is an Add-on?
==================

An add-on is simply a Python module with some additional requirements so Blender
can display it in a list with useful information.

To give an example, here is the simplest possible add-on::

   bl_info = {
       "name": "My Test Add-on",
       "blender": (2, 80, 0),
       "category": "Object",
   }
   def register():
       print("Hello World")
   def unregister():
       print("Goodbye World")

``bl_info``
   is a dictionary containing add-on metadata such as the title,
   version and author to be displayed in the Preferences add-on list.
   It also specifies the minimum Blender version required to run the script;
   older versions won't display the add-on in the list.
``register``
   is a function which only runs when enabling the add-on,
   this means the module can be loaded without activating the add-on.
``unregister``
   is a function to unload anything setup by ``register``,
   this is called when the add-on is disabled.

Notice this add-on does not do anything related to Blender
(the :mod:`blender_api:bpy` module is not imported for example).

This is a contrived example of an add-on that serves to illustrate the point
that the base requirements of an add-on are simple.

An add-on will typically register operators, panels, menu items, etc,
but it's worth noting that *any* script can do this,
when executed from the Text editor or even the interactive console --
there is nothing inherently different about an add-on that allows it to integrate with Blender,
such functionality is just provided by the :mod:`blender_api:bpy` module for any script to access.

So an add-on is just a way to encapsulate a Python module in a way a user can easily utilize.

.. note::

   Running this script within the Text editor won't print anything,
   to see the output it must be installed through the Preferences.
   Messages will be printed when enabling and disabling.


Your First Add-on
=================

The simplest possible add-on above is useful as an example but not much else.
This next add-on is simple but shows how to integrate a script into Blender using an ``Operator``
which is the typical way to define a tool accessed from menus, buttons and keyboard shortcuts.

For the first example we will make a script that simply moves all objects in a scene.


Write the Script
----------------

Add the following script to the Text editor in Blender::

   import bpy

   scene = bpy.context.scene
   for obj in scene.objects:
       obj.location.x += 1.0

Click the :ref:`Run Script button <editors-text-run-script>`,
all objects in the active scene are moved by 1.0 unit.


.. _advanced-scripting-write-the-add-on-simple:

Write the Add-on (Simple)
-------------------------

This add-on takes the body of the script above, and adds it to an operator's ``execute()`` function. ::

   bl_info = {
       "name": "Move X Axis",
       "blender": (2, 80, 0),
       "category": "Object",
   }

   import bpy


   class ObjectMoveX(bpy.types.Operator):
       """My Object Moving Script"""      # Use this as a tooltip for menu items and buttons.
       bl_idname = "object.move_x"        # Unique identifier for buttons and menu items to reference.
       bl_label = "Move X by One"         # Display name in the interface.
       bl_options = {'REGISTER', 'UNDO'}  # Enable undo for the operator.

       def execute(self, context):        # execute() is called when running the operator.

           # The original script
           scene = context.scene
           for obj in scene.objects:
               obj.location.x += 1.0

           return {'FINISHED'}            # Lets Blender know the operator finished successfully.

   def menu_func(self, context):
       self.layout.operator(ObjectMoveX.bl_idname)

   def register():
       bpy.utils.register_class(ObjectMoveX)
       bpy.types.VIEW3D_MT_object.append(menu_func)  # Adds the new operator to an existing menu.

   def unregister():
       bpy.utils.unregister_class(ObjectMoveX)


   # This allows you to run the script directly from Blender's Text editor
   # to test the add-on without having to install it.
   if __name__ == "__main__":
       register()

.. note::

   ``bl_info`` is split across multiple lines, this is just a style convention used to more easily add items.

.. note::

   Rather than using ``bpy.context.scene``, we use the ``context.scene`` argument passed to ``execute()``.
   In most cases these will be the same. However in some cases, operators will be passed a custom context
   so script authors should prefer the ``context`` argument passed to operators.

To test the script, you can copy and paste it into Blender's Text editor and run it.
This will execute the script directly and call register immediately.

However running the script won't move any objects. For this, you need to execute the newly registered operator.

.. figure:: /images/advanced_scripting_addon-tutorial_operator-search-menu.png

   Operator Search menu.

Open the :ref:`Operator Search <bpy.ops.wm.search_operator>` menu
and type in "Move X by One" (the ``bl_label``), then :kbd:`Return`.

The objects should move as before.

*Keep this add-on open in Blender for the next step - Installing.*


Install the Add-on
------------------

Once you have your add-on within in Blender's Text editor,
you will want to be able to install it so it can be enabled in the Preferences to load on startup.

Even though the add-on above is a test, let's go through the steps anyway so you know how to do it for later.

To install the Blender text as an add-on, you will first have to save it on drive. Take care to obey the naming
restrictions that apply to Python modules and end with a ``.py`` extension.

Once the file is on drive, you can install it as you would for an add-on downloaded online.

Open the :menuselection:`Preferences --> Add-ons --> Install...` and select the file.

Now the add-on will be listed and you can enable it by pressing the checkbox,
if you want it to be enabled on restart, press *Save as Default*. The operator
can be run in the same way as described in the :ref:`previous section <advanced-scripting-write-the-add-on-simple>`.

When the add-on is enabled, Blender executes the code and runs the ``register()`` function.
When the add-on is disabled, Blender runs the ``unregister()`` function.

.. note::

   The destination of the add-on depends on your Blender configuration.
   When installing an add-on the source and destination paths are printed in the console.
   You can also find add-on path locations by running this in the Python Console::

      import addon_utils
      print(addon_utils.paths())

   More is written on this topic here:
   :ref:`Directory Layout <blender-directory-layout>`.


Your Second Add-on
==================

For our second add-on, we will focus on object instancing -- this is -- to make linked
copies of an object in a similar way to what you may have seen with the Array modifier.


Write the Script
----------------

As before, first we will start with a script, develop it, then convert it into an add-on. ::

   import bpy
   from bpy import context

   # Get the current scene
   scene = context.scene

   # Get the 3D cursor location
   cursor = scene.cursor.location

   # Get the active object (assume we have one)
   obj = context.active_object

   # Now make a copy of the object
   obj_new = obj.copy()

   # The new object has to be added to a collection in the scene
   scene.collection.objects.link(obj_new)

   # Now we can place the object
   obj_new.location = cursor

Now try copying this script into Blender and run it on the default Cube.
Make sure you click to move the 3D cursor before running as the duplicate will appear at the cursor's location.

After running, notice that when you go into *Edit Mode* to change the Cube -- all of the copies change.
In Blender, this is known as *Linked Duplicates*.

Next, we're going to do this in a loop, to make an array of objects between the active object and the cursor. ::

   import bpy
   from bpy import context

   scene = context.scene
   cursor = scene.cursor.location
   obj = context.active_object

   # Use a fixed value for now, eventually make this user adjustable
   total = 10

   # Add 'total' objects into the scene
   for i in range(total):
       obj_new = obj.copy()
       scene.collection.objects.link(obj_new)

       # Now place the object in between the cursor
       # and the active object based on 'i'
       factor = i / total
       obj_new.location = (obj.location * factor) + (cursor * (1.0 - factor))

Try running this script with the active object and the cursor spaced apart to see the result.

With this script you'll notice we're doing some math with the object location and cursor,
this works because both are 3D :class:`blender_api:mathutils.Vector` instances,
a convenient class provided by the :mod:`blender_api:mathutils` module which
allows vectors to be multiplied by numbers and matrices.

If you are interested in this area, read into :class:`blender_api:mathutils.Vector`
-- there are many handy utility functions such as getting the angle between vectors,
cross product, dot products as well as more advanced functions in :mod:`blender_api:mathutils.geometry`
such as Bézier spline interpolation and ray-triangle intersection.

For now we will focus on making this script an add-on, but it's good to know that this
3D math module is available and can help you with more advanced functionality later on.


Write the Add-on
----------------

The first step is to convert the script as-is into an add-on::

   bl_info = {
       "name": "Cursor Array",
       "blender": (2, 80, 0),
       "category": "Object",
   }

   import bpy


   class ObjectCursorArray(bpy.types.Operator):
       """Object Cursor Array"""
       bl_idname = "object.cursor_array"
       bl_label = "Cursor Array"
       bl_options = {'REGISTER', 'UNDO'}

       def execute(self, context):
           scene = context.scene
           cursor = scene.cursor.location
           obj = context.active_object

           total = 10

           for i in range(total):
               obj_new = obj.copy()
               scene.collection.objects.link(obj_new)

               factor = i / total
               obj_new.location = (obj.location * factor) + (cursor * (1.0 - factor))

           return {'FINISHED'}

   def register():
       bpy.utils.register_class(ObjectCursorArray)


   def unregister():
       bpy.utils.unregister_class(ObjectCursorArray)


   if __name__ == "__main__":
       register()

Everything here has been covered in the previous steps, you may want to try run
the add-on still and consider what could be done to make it more useful.

The two of the most obvious missing things are -- having the total fixed at 10,
and having to access the operator with :doc:`/interface/controls/templates/operator_search` is not very convenient.

Both these additions are explained next, with the final script afterwards.


Operator Property
^^^^^^^^^^^^^^^^^

There are a variety of property types that are used for tool settings, common property types include:
int, float, vector, color, Boolean and string.

These properties are handled differently to typical Python class attributes
because Blender needs to display them in the interface,
store their settings in keymaps and keep settings for reuse.

While this is handled in a fairly Pythonic way, be mindful that you are in fact defining tool settings that
are loaded into Blender and accessed by other parts of Blender, outside of Python.

To get rid of the literal 10 for ``total``, we'll use an operator property.
Operator properties are defined via bpy.props module, this is added to the class body::

   # moved assignment from execute() to the body of the class...
   total: bpy.props.IntProperty(name="Steps", default=2, min=1, max=100)

   # and this is accessed on the class
   # instance within the execute() function as...
   self.total

These properties from :mod:`blender_api:bpy.props` are handled specially by Blender
when the class is registered so they display as buttons in the user interface.
There are many arguments you can pass to properties to set limits,
change the default and display a tooltip.

.. seealso:: :func:`blender_api:bpy.props.IntProperty`

This document doesn't go into details about using other property types.
However, the link above includes examples of more advanced property usage.


Menu Item
^^^^^^^^^

Add-ons can add to the user interface of existing panels, headers and menus defined in Python.

For this example we'll add to an existing menu.

.. figure:: /images/advanced_scripting_addon-tutorial_menu-id.png

   Menu Identifier.

To find the identifier of a menu, first enable *Python Tooltips* in the preferences.
Then you can hover your mouse over the menu item and the identifier is displayed.

The method used for adding a menu item is to append a draw function into an existing class::

   def menu_func(self, context):
       self.layout.operator(ObjectCursorArray.bl_idname)

   def register():
       bpy.utils.register_class(ObjectCursorArray)
       bpy.types.VIEW3D_MT_object.append(menu_func)

For docs on extending menus, see: :class:`blender_api:bpy.types.Menu`.


Keymap
^^^^^^

In Blender, add-ons have their own keymaps so as not to interfere with Blender's built-in keymaps.

In the example below, a new object mode :class:`blender_api:bpy.types.KeyMap` is added,
then a :class:`blender_api:bpy.types.KeyMapItem` is added to the keymap which references
our newly added operator, using :kbd:`Shift-Ctrl-T` as the key shortcut to activate it. ::

   # store keymaps here to access after registration
   addon_keymaps = []

   def register():

       # handle the keymap
       wm = bpy.context.window_manager
       km = wm.keyconfigs.addon.keymaps.new(name='Object Mode', space_type='EMPTY')

       kmi = km.keymap_items.new(ObjectCursorArray.bl_idname, 'T', 'PRESS', ctrl=True, shift=True)
       kmi.properties.total = 4

       addon_keymaps.append((km, kmi))


   def unregister():

       # handle the keymap
       for km, kmi in addon_keymaps:
           km.keymap_items.remove(kmi)
       addon_keymaps.clear()

Notice how the keymap item can have a ``total`` setting different than the default set by the operator,
this allows you to have multiple keys accessing the same operator with different settings.

.. note::

   While :kbd:`Shift-Ctrl-T` is not a default Blender key shortcut,
   it is hard to make sure add-ons will not overwrite each other's keymaps.
   Thus at least take care when assigning keys that they do not
   conflict with important functionality of Blender
   (see also `is key free add-on <https://projects.blender.org/extensions/development_iskeyfree>`__).

For API documentation on the functions listed above, see:

- :meth:`blender_api:bpy.types.KeyMaps.new`
- :class:`blender_api:bpy.types.KeyMap`
- :meth:`blender_api:bpy.types.KeyMapItems.new`
- :class:`blender_api:bpy.types.KeyMapItem`


Bringing It All Together
^^^^^^^^^^^^^^^^^^^^^^^^

::

   bl_info = {
       "name": "Cursor Array",
       "blender": (2, 80, 0),
       "category": "Object",
   }

   import bpy


   class ObjectCursorArray(bpy.types.Operator):
       """Object Cursor Array"""
       bl_idname = "object.cursor_array"
       bl_label = "Cursor Array"
       bl_options = {'REGISTER', 'UNDO'}

       total: bpy.props.IntProperty(name="Steps", default=2, min=1, max=100)

       def execute(self, context):
           scene = context.scene
           cursor = scene.cursor.location
           obj = context.active_object

           for i in range(self.total):
               obj_new = obj.copy()
               scene.collection.objects.link(obj_new)

               factor = i / self.total
               obj_new.location = (obj.location * factor) + (cursor * (1.0 - factor))

           return {'FINISHED'}


   def menu_func(self, context):
       self.layout.operator(ObjectCursorArray.bl_idname)

   # store keymaps here to access after registration
   addon_keymaps = []


   def register():
       bpy.utils.register_class(ObjectCursorArray)
       bpy.types.VIEW3D_MT_object.append(menu_func)

       # handle the keymap
       wm = bpy.context.window_manager
       # Note that in background mode (no GUI available), keyconfigs are not available either,
       # so we have to check this to avoid nasty errors in background case.
       kc = wm.keyconfigs.addon
       if kc:
           km = wm.keyconfigs.addon.keymaps.new(name='Object Mode', space_type='EMPTY')
           kmi = km.keymap_items.new(ObjectCursorArray.bl_idname, 'T', 'PRESS', ctrl=True, shift=True)
           kmi.properties.total = 4
           addon_keymaps.append((km, kmi))

   def unregister():
       # Note: when unregistering, it's usually good practice to do it in reverse order you registered.
       # Can avoid strange issues like keymap still referring to operators already unregistered...
       # handle the keymap
       for km, kmi in addon_keymaps:
           km.keymap_items.remove(kmi)
       addon_keymaps.clear()

       bpy.utils.unregister_class(ObjectCursorArray)
       bpy.types.VIEW3D_MT_object.remove(menu_func)


   if __name__ == "__main__":
       register()

.. figure:: /images/advanced_scripting_addon-tutorial_in-menu.png

   In the menu.

Run the script (or save it and add it through the Preferences like before) and it will appear in the *Object* menu.

.. figure:: /images/advanced_scripting_addon-tutorial_op-prop.png

   Operator Property.

After selecting it from the menu, you can choose how many instances of the cube you want create.

.. note::

   Directly executing the script multiple times will add the menu each time too.
   While not useful behavior, there is nothing to worry about since add-ons will not
   register themselves multiple times when enabled through the Preferences.


Conclusions
===========

Add-ons can encapsulate certain functionality neatly for writing tools
to improve your workflow or for writing utilities for others to use.

While there are limits to what Python can do within Blender,
there is certainly a lot that can be achieved without having to dive into Blender's C/C++ code.

The example given in the tutorial is limited, but shows the Blender API used
for common tasks that you can expand on to write your own tools.


Further Reading
---------------

Blender comes with commented templates which are accessible from the Text editor's header.
If you have specific areas you want to see example code for, this is a good place to start.

Here are some sites you might like to check on after completing this tutorial.

- `Blender/Python API Overview <https://docs.blender.org/api/current/info_overview.html>`__ --
  For more background details on Blender/Python integration.
- `How to Think Like a Computer Scientist <https://runestone.academy/ns/books/published/thinkcspy/index.html>`__ --
  Great info for those who are still learning Python.
- `Blender Development <https://developer.blender.org/>`__ --
  Blender Development, general information and helpful links.
- `Blender Developer Forum <https://devtalk.blender.org/tag/python>`__ --
  Forum where people ask Python development questions.


## scripting\index

.. _scripting-index:
.. _bpy.ops.script:

#################################
  Scripting & Extending Blender
#################################

.. toctree::
   :maxdepth: 2

   introduction.rst
   security.rst
   addon_tutorial.rst


## scripting\introduction


************
Introduction
************

Python is an interpreted, interactive, object-oriented programming language.
It incorporates modules, exceptions, dynamic typing, very high-level dynamic data types, and classes.
Python combines remarkable power with very clear syntax.

Python scripts are a versatile way to extend Blender functionality.
Most areas of Blender can be scripted, including animation, rendering, import and export,
object creation and automating repetitive tasks.

To interact with Blender, scripts can make use of
the tightly integrated :abbr:`API (Application Programming Interface)`.


General Information
===================

Links that are useful while writing scripts:

- `Python.org <https://www.python.org/>`__
  -- General information about Python.
- `Blender Python API <https://docs.blender.org/api/current/>`__
  -- Official API documentation. Use this for referencing while writing scripts.
- `API Introduction <https://docs.blender.org/api/current/info_quickstart.html>`__
  -- A short introduction to get you started with the API. Contains examples.

Links that deal with distributing your scripts:

- `Sharing scripts <https://developer.blender.org/docs/handbook/addons/>`__
  -- Information on how to share your scripts and get them included in the official Blender distribution.
- `Creating Add-ons <https://developer.blender.org/docs/handbook/addons/guidelines/>`__
  -- Add-ons are used to encapsulate and distribute scripts.
- `Add-ons project <https://projects.blender.org/blender/blender-addons>`__
  -- Project to maintain a central repository of extensions to Blender.


Getting Started
===============

.. rubric:: Manual links

The following links take you from the basics to the more advanced
concepts of Python scripting for Blender.

- :doc:`Text Editor </editors/text_editor>`
- :doc:`Python Console </editors/python_console>`
- :doc:`Info Editor </editors/info_editor>`


.. rubric:: External links

Here are external links containing a lot of good information
to start learning how to write scripts for Blender:

- `Python API: Quickstart <https://docs.blender.org/api/current/info_quickstart.html>`__
- `CG Cookie: Blender 2.8 Python Scripting Superpowers for Non-Programmers
  <https://cgcookie.com/posts/blender-2-8-python-scripting-superpowers-for-non-programmers>`__
- `Olav3D Tutorials: 3D Programming for Beginners Using Python
  <https://www.youtube.com/watch?v=rHzf3Dku_cE>`__
- `Blender Artists: Python Support Forum <https://blenderartists.org/c/coding/python-support>`__


Extending Blender
=================

Add-ons
-------

Add-ons are scripts that enable Blender to gain extra functionality;
they can be enabled from the :doc:`Preferences </editors/preferences/extensions>`.

Outside of the Blender executable, there are hundreds of add-ons written by many people:

- Officially supported add-ons are bundled with Blender.
- Other add-ons are provided by `Blender Extensions <https://extensions.blender.org/>`__
  which aren't part of official releases.
  Many of them work reliably and are very useful but are not yet ensured to be stable for release.

.. seealso::

   See :doc:`/addons/index` for documentation on add-ons included with Blender.


Scripts
-------

Apart from add-ons, there are several other types of scripts that extend Blender's functionality:

:Modules:
   Utility libraries for import into other scripts.
:Presets:
   Settings for Blender's tools and key configurations.
:Startup:
   These files are imported when starting Blender.
   They define most of Blender's UI, as well as some additional core operators.
:Custom Scripts:
   In contrast to add-ons, they are typically intended for one-time execution via
   the :doc:`Text Editor </editors/text_editor>`.


Saving your own Scripts
-----------------------

File Location
^^^^^^^^^^^^^

All scripts are loaded from the ``scripts`` folder of
the :ref:`local, system and user paths <blender-directory-layout>`.

You can setup an additional search path for scripts in
:ref:`prefs-file-paths` :menuselection:`Preferences --> File Paths`.


Installation
^^^^^^^^^^^^

Add-ons are conveniently installed through Blender in the :doc:`Preferences </editors/preferences/extensions>`.
Click the :menuselection:`Install...` button and select the ``.zip`` file.


## scripting\security


********************
Scripting & Security
********************

The ability to include Python scripts within blend-files is valuable for advanced tasks
such as rigging and automation. However, it poses a security risk since
Python does not restrict what a script can do.
Therefore, you should only run scripts from sources you know and trust.
Automatic execution is disabled by default;
however, some blend-files need this to function properly.

When a blend-file tries to execute a script and is not allowed, a dialog will appear.
In it, you can choose to *Allow Execution* or to *Ignore* the scripts.

.. figure:: /images/advanced_scripting_security_autorun-scripts-dialog.png

   An Auto-run warning in the Info editor's header.


Scripts in Blend-Files
======================

Auto Execution
--------------

Here are the different ways blend-files may automatically run scripts.

Registered Text-Blocks
   A text data-block can have its *Register* option enabled which means it will load on start.
Animation Drivers
   Python expressions can be used to *Drive* values and are often used in more advanced rigs and animations.


Manual Execution
----------------

There are other ways scripts in a blend-file may execute that require user
interaction (therefore will run even when auto execution is off),
but you should be aware that this is the case since it is not necessarily obvious.

- Running a script in the Text editor.
- Rendering with Freestyle, because Freestyle uses scripts to control line styles.


Controlling Script Execution
============================

Blender provides a number of ways to control whether scripts
from a blend-file are allowed to automatically execute.

First, the File Browser has the option **Trusted Source** which you can use on
a case-by-case basis to control auto execution.
Since you may forget to set this,
or may open a file without going through the File Browser,
you can change the default (described next).


Setting Defaults
----------------

In the Preferences, there is the toggle to
:ref:`Auto Run Python Scripts <bpy.types.PreferencesFilePaths.use_scripts_auto_execute>`.
This means the **Trusted Source** option in the File Browser will be enabled by default,
and scripts can run when blend-files are loaded without using the File Browser.
Once enabled you have the option to exclude certain directories;
a typical configuration would be to trust all paths except for the download directory.

.. figure:: /images/animation_drivers_troubleshooting_autorun-user-preference.png

   The Auto Run Python Scripts checkbox.


Command Line
------------

You may want to perform batch rendering or some other task from the command line,
running Blender without an interface.
In this case, the Preferences are still used but you may want to override them:

- Enable with ``-y`` or ``--enable-autoexec``
- Disable with ``-Y`` or ``--disable-autoexec``


Example
^^^^^^^

To render an animation in background mode, allowing drivers and other scripts to run:

.. code-block:: sh

   blender --background --enable-autoexec my_movie.blend --render-anim

.. note::

   These command-line arguments can be used to start a regular Blender instance and
   will still override the Preferences.
