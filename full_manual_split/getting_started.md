# Index for getting_started

- [Help](#Help)
- [Index](#Index)
- [Community](#Community)
- [History](#History)
- [Index](#Index)
- [License](#License)
- [Defaults](#Defaults)
- [Hardware](#Hardware)
- [Index](#Index)
- [Introduction](#Introduction)
- [Index](#Index)
- [Linux](#Linux)
- [Linux Windowing Environment](#Linux-Windowing-Environment)
- [Macos](#Macos)
- [Steam](#Steam)
- [Windows](#Windows)


## Help


***********
Help System
***********

Blender has a range of built-in and web-based help options.


Tooltips
========

.. figure:: /images/getting-started_help_tooltip.png

   Tooltip of the Renderer selector in the Info Editor.

When hovering the mouse cursor over a button or setting, after a few instants a tooltip appears.


Elements
--------

The context-sensitive Tooltip might contain some of these elements:

Short Description
   Related details depending on the control.
Shortcut
   A keyboard or mouse shortcut associated to the tool.
Value
   The value of the property.

   Hovering over a color property will display a large swatch preview of the color
   and the color's hexadecimal, RGBA, and HSVA values.
Library
   Source file of the active object. See also :doc:`/files/linked_libraries/index`.
Disabled (red)
   The reason why the value is not editable.
Python
   When :ref:`Python Tooltips <bpy.types.PreferencesView.show_tooltips_python>` are enabled,
   a Python expression is displayed for :ref:`scripting <scripting-index>` (usually an operator or property).


.. _help-manual-access:
.. _bpy.ops.wm.doc_view_manual_ui_context:

Context-Sensitive Manual Access
===============================

.. reference::

   :Mode:      All modes
   :Menu:      :menuselection:`Context menu --> Online Manual`
   :Shortcut:  :kbd:`F1`

You may want to access help for a tool or area from within Blender.

To do so; hover the cursor over the tool or button you need help with and
use the keyboard shortcut or context menu item to visit pages of this reference manual from within Blender.
This opens a web page relating to the button under the cursor, supporting both tool and value buttons.

.. note::

   We do not currently have 100% coverage.
   You may see an alert in the info header if a tool does not have a link to the manual.

   Other times, buttons may link to more general sections of the documentation.


.. _help-menu:

Help Menu
=========

Web Links
---------

The first options of this menu provide direct links to Blender-related websites.
The same links can also be found in the :ref:`splash`.

:doc:`Manual </index>`
   This is a link to the Official Blender Manual (which you are now reading).
`Release Notes <https://developer.blender.org/docs/release_notes/>`__
   Link to the release notes for the current Blender version.
`Tutorials <https://www.blender.org/support/tutorials>`__
   Multiple tutorials to help you learn to use Blender.
`Support <https://www.blender.org/support>`__
   Links to various sites, providing both community and professional support.
`User Communities <https://www.blender.org/community/>`__
   Lists of many different community sites and support venues.

----

`Report a Bug <https://projects.blender.org/blender/blender/issues/new?template=.gitea%2fissue_template%2fbug.yaml>`__
   The Blender Bug Tracker (registration needed).


.. _help-system-info:

Save System Info
----------------

This extracts system information which can be useful for including in bug reports,
inspecting the configuration, or diagnosing problems.

You will be prompted to save a text file called ``system-info.txt``.

It contains the following sections:

Blender
   This section shows you the Blender version, details about the build configuration,
   and the path in which Blender is running.
Python
   The version and path of your Python installation.
Directories
   Paths used for scripts, data files, presets and temporary files.

   Those directories are configured using the :doc:`Preferences </editors/preferences/file_paths>` Editor.
GPU
   Shows the GPU vendor, version and the capabilities of your hardware and driver.
Enabled Add-Ons
   Lists add-ons currently in use.


## Index

:orphan:

###################
  Getting Started
###################

.. keep up to date with :doc:`</index>`

.. toctree::
   :maxdepth: 2

   about/index.rst
   installing/index.rst
   configuration/index.rst
   help.rst


## Community


*********************
The Blender Community
*********************

Being freely available from the start, even while it was closed source, considerably helped Blender's adoption by the
community. A large, stable, and active community of users has gathered around Blender since 1998. The community showed
its support for Blender in 2002 when they helped raise €100,000 in seven weeks to enable Blender to go Open Source
under the `GNU GPL License <https://www.gnu.org/licenses/gpl.html>`__.


Independent Sites
=================

There are `several independent websites <https://www.blender.org/community/>`__
such as forums, blogs, news, and tutorial sites dedicated to Blender.

One of the largest community forums is `Blender Artists <https://blenderartists.org/>`__,
where Blender users gather to show off their creations,
get feedback, ask and offer help and, in general, discuss Blender.


Getting Support
===============

Blender's community is one of its greatest features, so apart from this user manual,
there are many different ways to get support from other users, such as :ref:`blender-chat`,
`Stack Exchange <https://blender.stackexchange.com/>`__, and `Reddit <https://www.reddit.com/r/blender/>`__.

For studios and organizations there is `Enterprise support <https://www.blender.org/support/>`__,
and for studios looking to add Blender to their pipeline, `Blender Studio <https://studio.blender.org/>`__
contains documentation and training material around this topic.
If you think you have found an issue with Blender, please
`report a bug <https://projects.blender.org/blender/blender/issues/new?template=.gitea%2fissue_template%2fbug.yaml>`__.

More details about support can be found on the `support page <https://www.blender.org/support/>`__.


Development
===========

Being open source, Blender welcomes development from volunteers.
Communication between developers is done mostly through three platforms:

- The `projects.blender.org <https://projects.blender.org/>`__ system
- `Developer Forum <https://devtalk.blender.org/>`__
- Online Chat (see below)

If you are interested in helping develop Blender,
see the `Get Involved <https://www.blender.org/get-involved/>`__ page.


.. _blender-chat:

Blender Chat
============

For real-time discussion, we have
`blender.chat <https://blender.chat>`__ which uses
`Blender ID <https://id.blender.org>`__ for authentication.

You can join these channels:

- `#today <https://blender.chat/channel/today>`__
  For getting answers from the community.
- `#blender-coders <https://blender.chat/channel/blender-coders>`__
  For developers to discuss Blender development.
- `#python <https://blender.chat/channel/python>`__
  For support for developers using the Python API.
- `#docs <https://blender.chat/channel/docs>`__
  For discussion related to Blender's documentation.


Other Useful Links
==================

- `Blender FAQ <https://www.blender.org/support/faq/>`__ (Can I use Blender commercially? What is GPL/GNU? ...)
- `Demo and benchmark files <https://www.blender.org/download/demo-files/>`__
- Developer's `Ask Us Anything! <https://developer.blender.org/docs/handbook/new_developers/faq/>`__


## History


*****************
Blender's History
*****************

In 1988, Ton Roosendaal co-founded the Dutch animation studio NeoGeo. NeoGeo quickly became
the largest 3D animation studio in the Netherlands and one of the leading animation houses in Europe.
NeoGeo created award-winning productions (European Corporate Video Awards 1993 and 1995)
for large corporate clients such as the multinational electronics company Philips.
Within NeoGeo, Ton was responsible for both art direction and internal software development.
After careful deliberation, Ton decided that the current in-house 3D tool set for NeoGeo was
too old and cumbersome to maintain, and needed to be rewritten from scratch.
In 1995 this rewrite began and was destined to become the 3D software creation we all know as Blender.
As NeoGeo continued to refine and improve Blender, it became apparent to Ton
that Blender could be used as a tool for other artists outside of NeoGeo.

In 1998, Ton decided to found a new company called Not a Number (NaN)
as a spin-off of NeoGeo to further market and develop Blender.
At the core of NaN was a desire to create and distribute a compact,
cross-platform 3D application for free. At the time, this was a revolutionary concept as most
commercial 3D applications cost thousands of dollars. NaN hoped to bring professional
level 3D modeling and animation tools within the reach of the general computing public.
NaN's business model involved providing commercial products and services around Blender.
In 1999 NaN attended its first SIGGRAPH conference in an effort to more widely promote Blender.
Blender's first SIGGRAPH convention was a huge success and gathered a tremendous amount of
interest from both the press and attendees. Blender was a hit and its huge potential confirmed!

Following the success of the SIGGRAPH conference in early 2000, NaN secured financing of €4.5M from
venture capitalists. This large inflow of cash enabled NaN to rapidly expand its operations.
Soon NaN boasted as many as 50 employees working around the world trying to improve and promote Blender.
In the summer of 2000, Blender 2.0 was released.
This version of Blender added the integration of a game engine to the 3D application.
By the end of 2000, the number of users registered on the NaN website exceeded 250,000.

Unfortunately, NaN's ambitions and opportunities did not match the company's capabilities and
the market realities of the time. This over-extension resulted in restarting NaN with new
investor funding and a smaller company in April 2001.
Six months later NaN's first commercial software product, Blender Publisher was launched.
This product was targeted at the emerging market of interactive web-based 3D media.
Due to disappointing sales and the ongoing difficult economic climate,
the new investors decided to shut down all NaN operations.
The shutdown also included discontinuing the development of Blender.
Although there were clearly shortcomings in the then current version of Blender,
such as a complex internal software architecture,
unfinished features and a non-standard way of providing the GUI, the enthusiastic support from
the user community and customers who had purchased Blender Publisher in the past, meant that
Ton could not justify leaving Blender to fade into insignificance.
Since restarting a company with a sufficiently large team of developers was not feasible,
Ton Roosendaal founded the non-profit organization, Blender Foundation, in March 2002.

The Blender Foundation's primary goal was to find a way to continue developing and
promoting Blender as a community-based `open source <https://opensource.org/>`__ project.
In July 2002, Ton managed to get the NaN investors to agree to a unique Blender Foundation plan to
attempt to release Blender as open source. The "Free Blender" campaign sought to raise €100,000
so that the Foundation could buy the rights to the Blender source code and intellectual property
rights from the NaN investors and subsequently release Blender to the open source community.
With an enthusiastic group of volunteers, among them several ex-NaN employees,
a fundraising campaign was launched to "Free Blender".
To everyone's surprise and delight the campaign reached the €100,000 goal in only seven short weeks.
On Sunday, October 13, 2002, Blender was released to the world
under the terms of the `GNU GPL <https://www.gnu.org/licenses/gpl.html>`__.
Blender development continues to this day, driven by a team of dedicated volunteers
from around the world led by Blender's original creator, Ton Roosendaal.


Version/Revision Milestones
===========================

.. rubric:: The start!

- **1.00 -- January 1994:** Blender
  `in development <https://code.blender.org/2013/12/how-blender-started-twenty-years-ago/>`__
  at animation studio NeoGeo.
- **1.23 -- January 1998:** SGI version published on the web, IrisGL.
- **1.30 -- April 1998:** Linux and FreeBSD version, port to OpenGL and X11.
- **1.3x -- June 1998:** NaN founded.
- **1.4x -- September 1998:** Sun and Linux Alpha version released.
- **1.50 -- November 1998:** First Manual published.
- **1.60 -- April 1999:** C-key (new features behind a lock, $95), Windows version released.
- **1.6x -- June 1999:** BeOS and PPC version released.
- **1.80 -- June 2000:** End of C-key, Blender full freeware again.
- **2.00 -- August 2000:** Interactive 3D and real-time engine.
- **2.10 -- December 2000:** New engine, physics, and Python.
- **2.20 -- August 2001:** Character animation system.
- **2.21 -- October 2001:** Blender Publisher launch.
- **2.2x -- December 2001:** macOS version.


.. rubric:: Blender goes Open Source

13 October 2002:
   **Blender goes Open Source, 1st Blender Conference.**
2.25 -- October 2002:
   `Blender Publisher <https://download.blender.org/release/Publisher2.25/>`__ becomes freely available,
   and the experimental tree of Blender is created, a coder's playground.
2.26 -- February 2003:
   The first truly open source Blender release.
2.27 -- May 2003:
   The second open source Blender release.
2.28x -- July 2003:
   First of the 2.28x series.
`2.30 <https://archive.blender.org/www/development/release-logs/blender-230/>`__ -- October 2003:
   Preview release of the 2.3x UI makeover presented at the 2nd Blender Conference.
`2.31 <https://archive.blender.org/www/development/release-logs/blender-231/>`__ -- December 2003:
   Upgrade to stable 2.3x UI project.
`2.32 <https://archive.blender.org/www/development/release-logs/blender-232/>`__ -- January 2004:
   A major overhaul of internal rendering capabilities.
`2.33 <https://archive.blender.org/www/development/release-logs/blender-233/>`__ -- April 2004:
   Game Engine returns, ambient occlusion, new procedural textures.
`2.34 <https://archive.blender.org/www/development/release-logs/blender-234/>`__ -- August 2004:
   Particle interactions, LSCM UV mapping, functional YafRay integration, weighted creases in subdivision surfaces,
   ramp shaders, full OSA, and many (many) more.
`2.35 <https://archive.blender.org/www/development/release-logs/blender-235a/>`__ -- November 2004:
   Another version full of improvements: object hooks, curve deforms and curve tapers,
   particle duplicators and much more.
`2.36 <https://archive.blender.org/www/development/release-logs/blender-236/>`__ -- December 2004:
   A stabilization version, much work behind the scenes, normal and displacement mapping improvements.
`2.37 <https://archive.blender.org/www/development/release-logs/blender-237a/>`__ -- June 2005:
   Transformation tools and widgets, soft bodies, force fields, deflections,
   incremental subdivision surfaces, transparent shadows, and multi-threaded rendering.
`2.40 <https://archive.blender.org/wiki/2015/index.php/Dev:Ref/Release_Notes/2.40>`__ -- December 2005:
   Full rework of armature system, shape keys, fur with particles, fluids, and rigid bodies.
`2.41 <https://archive.blender.org/wiki/2015/index.php/Dev:Ref/Release_Notes/2.41>`__ -- January 2006:
   Lots of fixes, and some Game Engine features.
`2.42 <https://archive.blender.org/wiki/2015/index.php/Dev:Ref/Release_Notes/2.42>`__ -- July 2006:
   The nodes release, Array modifier, vector blur, new physics engine, rendering, lip sync, and many other features.
   This was the release following `Project Orange <https://orange.blender.org/>`__.
`2.43 <https://archive.blender.org/wiki/2015/index.php/Dev:Ref/Release_Notes/2.43>`__ -- February 2007:
   Multiresolution meshes, multi-layer UV textures, multi-layer images and multi-pass rendering and baking,
   sculpting, retopology, multiple additional mattes, distort and filter nodes, modeling and
   animation improvements, better painting with multiple brushes, fluid particles,
   proxy objects, Sequencer rewrite, and post-production UV texturing.
`2.44 <https://archive.blender.org/www/development/release-logs/blender-244/index.html>`__ -- May 2007:
   The big news, in addition to two new modifiers and re-awakening the 64-bit OS support, was the addition
   of subsurface scattering, which simulates light scattering beneath the surface of organic and soft objects.
`2.45 <https://archive.blender.org/www/development/release-logs/blender-245/index.html>`__ -- September 2007:
   Serious bug fixes, with some performance issues addressed.
`2.46 <https://archive.blender.org/wiki/2015/index.php/Dev:Ref/Release_Notes/2.46>`__ -- May 2008:
   The Peach release was the result of a huge effort of over 70 developers providing enhancements to
   provide hair and fur, a new particle system, enhanced image browsing, cloth, a seamless
   and non-intrusive physics cache, rendering improvements in reflections, AO, and render baking,
   a Mesh Deform modifier for muscles and such, better animation support via armature tools and
   drawing, skinning, constraints and a colorful Action Editor, and much more.
   It contained the results of `Project Peach <https://peach.blender.org/>`__.
`2.47 <https://archive.blender.org/wiki/2015/index.php/Dev:Ref/Release_Notes/2.47>`__ -- August 2008:
   Bugfix release.
`2.48 <https://archive.blender.org/www/development/release-logs/blender-248/index.html>`__ -- October 2008:
   The Apricot release, cool GLSL shaders, lights and GE improvements, snap, sky simulator,
   Shrinkwrap modifier, and Python editing improvements.
   This contained the results `Project Apricot <https://apricot.blender.org/>`__.
`2.49 <https://archive.blender.org/wiki/2015/index.php/Dev:Ref/Release_Notes/2.49>`__ -- June 2009:
   Node-based textures, armature sketching (called Etch-a-Ton), Boolean mesh operation improvements,
   JPEG2000 support, projection painting for direct transfer of images to models, and
   a significant Python script catalog. GE enhancements included video textures, where you can play movies in-game,
   upgrades to the Bullet physics engine, dome (fisheye) rendering, and more API GE calls made available.


.. rubric:: Blender 2.5x -- The Recode!

`2.5x <https://www.blender.org/download/releases/#25-series-2009-2011>`__ -- From 2009 to August 2011:
   This series released four `pre-version <https://archive.blender.org/www/development/release-logs/blender-256-beta>`__
   (from Alpha 0 in November 2009 to Beta in July 2010) and
   three stable versions (from 2.57 - April 2011 to 2.59 - August 2011).
   It was one of the most important development projects, with a total refactor of the software with new functions,
   redesign of the internal window manager and event/tool/data handling system, and new Python API.
   The final version of this project was Blender 2.59 in August 2011.


.. rubric:: Blender 2.6x to 2.7x -- Improvements & Stabilizing

`2.60 <https://archive.blender.org/wiki/2015/index.php/Dev:Ref/Release_Notes/2.60>`__ -- October 2011:
   Internationalization of the UI, improvements in the animation system and the GE,
   vertex weight groups modifiers, 3D audio and video, and bug fixes.
`2.61 <https://archive.blender.org/wiki/2015/index.php/Dev:Ref/Release_Notes/2.61>`__ -- December 2011:
   The Cycles renderer was added to the trunk, the camera tracker was added, dynamic paint for modifying textures
   with mesh contact/approximation, the Ocean modifier to simulate ocean and foam, new add-ons, bug fixes,
   and more extensions added for the Python API.
`2.62 <https://archive.blender.org/wiki/2015/index.php/Dev:Ref/Release_Notes/2.62>`__ -- February 2012:
   The `Carve library <https://code.google.com/archive/p/carve/>`__ was added to improve Boolean operations,
   support for object tracking was added, the Remesh modifier was added, many improvements in the GE,
   matrices and vectors in the Python API were improved, plus new add-ons, and many bug fixes.
`2.63 <https://archive.blender.org/wiki/2015/index.php/Dev:Ref/Release_Notes/2.63>`__ -- April 2012:
   Bmesh was merged with the trunk, with full support for n-sided polygons, sculpt hiding, a panoramic camera
   for Cycles, mirror ball environment textures and float precision textures, render layer mask layers,
   ambient occlusion and viewport display of background images and render layers.
   New import and export add-ons were added, and 150 bug fixes.
`2.64 <https://archive.blender.org/wiki/2015/index.php/Dev:Ref/Release_Notes/2.64>`__ -- October 2012:
   A mask editor was added, along with an improved motion tracker, OpenColorIO, Cycles improvements,
   Sequencer improvements, better mesh tools (Inset and Bevel were improved), new keying nodes, sculpt masking,
   Collada improvements, a new Skin modifier, a new compositing nodes backend, and the fixing of many bugs.
`2.65 <https://archive.blender.org/wiki/2015/index.php/Dev:Ref/Release_Notes/2.65>`__ -- December 2012:
   Fire and smoke improvements, anisotropic shader for Cycles, modifier improvements,
   the Bevel tool now includes rounding, new add-ons, and over 200 bug fixes.
`2.66 <https://www.blender.org/download/releases/2-66>`__ -- February 2013:
   Dynamic topology, rigid body simulation, improvements in UI and
   usability (including retina display support), Cycles now supports hair,
   the Bevel tool now supports individual vertex beveling,
   new :doc:`Mesh Cache </modeling/modifiers/modify/mesh_cache>` modifier and
   the new :doc:`UV Warp </modeling/modifiers/modify/uv_warp>` modifier,
   new SPH particle fluid solver. More than 250 bug fixes.
`2.67 <https://www.blender.org/download/releases/2-67>`__ -- May 2013:
   Freestyle was added, paint system improvements, subsurface scattering for Cycles, Ceres library
   in the motion tracker, new custom Python nodes, new mesh modeling tools, better support for UTF-8 text and
   improvements in Text editors, new add-ons for 3D printing, over 260 bug fixes.
`2.68 <https://www.blender.org/download/releases/2-68>`__ -- July 2013:
   New and improved modeling tools, three new Cycles nodes, big improvements in the motion tracker,
   Python scripts and drivers are disabled by default when loading files for security reasons,
   and over 280 bug fixes.
`2.69 <https://www.blender.org/download/releases/2-69>`__ -- October 2013:
   Even more modeling tools, Cycles improved in many areas, plane tracking is added to the motion tracker,
   better support for FBX import/export, and over 270 bugs fixed.
`2.70 <https://www.blender.org/download/releases/2-70>`__ -- March 2014:
   Cycles gets basic volumetric support on the CPU, more improvements to the motion tracker,
   two new modeling modifiers, some UI consistency improvements, and more than 560 bug fixes.
`2.71 <https://www.blender.org/download/releases/2-71>`__ -- June 2014:
   Deformation motion blur and fire/smoke support is added to Cycles, UI pop-ups are now draggable.
   There are performance optimizations for sculpting mode, new interpolation types for animation,
   many improvements to the GE, and over 400 bug fixes.
`2.72 <https://www.blender.org/download/releases/2-72>`__ -- October 2014:
   Cycles gets volume and SSS support on the GPU, pie menus are added and tooltips greatly improved,
   the Intersection modeling tool is added, new Sun Beam node for the Compositor, Freestyle now works with
   Cycles, texture painting workflow is improved, and more than 220 bug fixes.
`2.73 <https://www.blender.org/download/releases/2-73/>`__ -- January 2015:
   Cycles gets improved volumetric support, major upgrade to Grease Pencil,
   Windows gets Input Method Editors (IMEs)
   and general improvements to painting, Freestyle, Sequencer and add-ons.
`2.74 <https://www.blender.org/download/releases/2-74/>`__ -- March 2015:
   Support for custom normals, viewport compositing and improvements to hair dynamics.
`2.75 <https://www.blender.org/download/releases/2-75/>`__ -- July 2015:
   Integrated stereo/multi-view pipeline, Smooth Corrective modifier and new developmental dependency graph.
`2.76 <https://www.blender.org/download/releases/2-76/>`__ -- November 2015:
   Pixar OpenSubdiv support, Viewport and File Browser performance boost,
   node auto-offset, and a text effect strip for the Sequencer.
`2.77 <https://www.blender.org/download/releases/2-77/>`__ -- March 2016:
   OpenVDB support for caching of smoke/volumetric simulations, improved Cycles subsurface scattering,
   Grease Pencil stroke sculpting and improved workflow,
   and reworked library handling to manage missing and deleted data-blocks.
`2.78 <https://www.blender.org/download/releases/2-78/>`__ -- September 2016:
   Cycles support for spherical stereo images for VR,
   Grease Pencil works more similar to other 2D drawing software,
   Alembic import and export support, and improvements to Bendy Bones for easier and simpler rigging.
`2.79 <https://www.blender.org/download/releases/2-79/>`__ -- September 2017:
   New Cycles features: Denoising, Shadow catcher, and new Principled shader.
   Other improvements were made to Grease Pencil and Alembic. Support was also added for application templates.


.. rubric:: Blender 2.8 -- Revamped UI

`2.80 <https://www.blender.org/download/releases/2-80>`__ -- July 2019:
   A totally redesigned UI for easier navigation; improved viewport, gizmos, and tools.
   With EEVEE a new physically based real-time render engine was created.
   The Grease Pencil got a big overhaul and is now a full 2D drawing and animation system.
   Replacing the old layers, collections are a powerful way to organize objects.
   Other improvements: Cycles, Modeling, Animation, Import/Export, Dependency Graph.
`2.81 <https://www.blender.org/download/releases/2-81/>`__ -- November 2019:
   Revamped sculpting tools, Cycles OptiX accelerated rendering, denoising,
   many EEVEE improvements, library overrides, UI improvements and much more.
`2.82 <https://www.blender.org/download/releases/2-82/>`__ -- February 2020:
   UDIM and USD support, Mantaflow for fluids and smoke simulation,
   AI denoising, Grease Pencil improvements, and much more.
`2.83 <https://www.blender.org/download/releases/2-83/>`__ -- June 2020:
   3D Viewport virtual reality scene inspection, new volume object type, Cycles adaptive sampling,
   Cycles viewport denoising, sculpting improvements, and much more.


.. rubric:: Blender 2.9 -- Refining 2.8

`2.90 <https://www.blender.org/download/releases/2-90/>`__ -- August 2020:
   Improved sky texture, EEVEE motion blur, sculpting improvements,
   revamped modifier UI, improved modeling tools, and faster motion blur in Cycles.
`2.91 <https://www.blender.org/download/releases/2-91/>`__ -- November 2020:
   Outliner improvements, property search, improved mesh Boolean operations, animation curves,
   volume object and display improvements, and more refined sculpting tools.
`2.92 <https://www.blender.org/download/releases/2-92/>`__ -- February 2021:
   Geometry nodes, primitive add tool, sculpting improvements, Grease Pencil curve editing,
   Cycles Color Attribute baking, APIC fluid simulations, Video Sequencer improvements, and much more.
`2.93 <https://www.blender.org/download/releases/2-93/>`__ -- June 2021:
   New geometry nodes, sculpting improvements, Grease Pencil Line Art modifier along with other improvements,
   an improved :abbr:`DOF (Depth Of Field)` for the EEVEE render engine, redesigned Cryptomatte workflow, and more.


.. rubric:: Blender 3.0 -- Optimizing Performance

`3.0 <https://www.blender.org/download/releases/3-0/>`__ -- December 2021
   Asset Browser added, Cycles X, EEVEE Attributes, New geometry nodes,
   animation update, Grease Pencil line art improvements, pose library,
   Open Image Denoising 2-8x faster, additional support for AMD on linux.

`3.1 <https://www.blender.org/download/releases/3-1/>`__ -- March 2022
   Major point clouds improvements, Cycles Apple Metal GPU support, Subdivision GPU support,
   image editor handles larger images, Major performance gains for geometry nodes,
   context aware search for geometry nodes.

`3.2 <https://www.blender.org/download/releases/3-2/>`__ -- June 2022
   Light groups for Cycles, true Shadow caustics, volume motion blur, GLTF improvements,
   AMD GPU Rendering on Linux, painting in sculpt mode, WEBp image support.

`3.3 <https://www.blender.org/download/releases/3-3/>`__ -- September 2022
   New hair object, procedural UV nodes, line art shadow and contour,
   Intel GPU rendering support via oneAPI, and improvements to library overrides.

`3.4 <https://www.blender.org/download/releases/3-4/>`__ -- December 2022
   Cycles path guiding, sculpting auto masking improvements, even more geometry nodes,
   UV Editing improvements and Wayland support on Linux.

`3.5 <https://www.blender.org/download/releases/3-5/>`__ -- March 2023
   New generative hair assets, vector displacement maps for sculpting, viewport compositor, and Cycle's light trees.


## Index

.. _introduction-index:

#################
  About Blender
#################

Welcome to Blender! Blender is a free and open-source 3D creation suite.

With Blender, you can create 3D visualizations such as
still images, 3D animations and VFX shots. You can also edit videos.
It is well suited to individuals and small studios who
benefit from its unified pipeline and responsive development process.

Being a cross-platform application, Blender runs on Linux, macOS, as well as Windows systems.
It also has relatively small memory and drive requirements compared to other 3D creation suites.
Its interface uses OpenGL to provide a consistent experience across all supported hardware and platforms.

.. figure:: /images/getting-started_about_introduction_screenshot.jpg


Who uses Blender?
=================

Blender has a wide variety of tools making it suitable for almost any sort of media production.
Professionals, hobbyists, and studios around the world use it for creating animations, game assets,
motion graphics, TV shows, concept art, story-boarding, commercials, and feature films.

Check out the `User Stories page <https://www.blender.org/get-involved/user-stories/>`__
on the Blender website for more examples.


Key Features
============

- Blender is a fully integrated 3D content creation suite, offering a broad range of essential tools, including
  :doc:`Modeling </modeling/introduction>`,
  :doc:`Rendering </render/introduction>`,
  :doc:`Animation & Rigging </animation/introduction>`,
  :doc:`Video Editing </video_editing/index>`,
  :doc:`VFX </movie_clip/index>`,
  :doc:`Compositing </compositing/introduction>`,
  :doc:`Texturing </editors/uv/introduction>`,
  and many types of :doc:`Simulations </physics/introduction>`.
- It is cross platform, with an OpenGL GUI that is uniform on all major platforms
  (and customizable with Python scripts).
- It has a high-quality 3D architecture, enabling fast and efficient creation workflow.
- It boasts active community support. See `blender.org/community <https://www.blender.org/community>`__
  for an extensive list of sites.
- It can be installed into and run from any directory without modifying the system.

You can download the latest version of Blender `here <https://www.blender.org/download/>`__.

.. figure:: /images/getting-started_about_introduction_postprocessing.jpg

   A rendered image being post-processed.

Blender makes it possible to perform a wide range of tasks, and it may seem daunting
when first trying to grasp the basics. However, with a bit of motivation and the right learning material,
it is possible to familiarize yourself with Blender after a few hours of practice.

This manual is a good start, though it serves more as a reference.
There are also many online video tutorials from specialized websites.

Despite everything Blender can do, it remains a tool. Great artists do not create masterpieces
by pressing buttons or manipulating brushes, but by learning and practicing subjects
such as human anatomy, composition, lighting, animation principles, etc.

3D creation software such as Blender have an added technical complexity and
jargon associated with the underlying technologies.
Terms like UV maps, materials, shaders, meshes, and "subdivs" are the media of the digital artist,
and understanding them, even broadly, will help you to use Blender to its best.

So keep reading this manual, learn the great tool that Blender is, and keep your mind open to
other artistic and technological areas -- and you, too, can become a great artist.


Further Reading
===============

.. toctree::
   :maxdepth: 2

   history.rst
   license.rst
   community.rst


## License


*******************************
About Free Software and the GPL
*******************************

.. figure:: /images/getting-started_about_license_gnu-logo.png
   :align: right

When one hears about "free software", the first thing that comes to mind might be "no cost".
While this is often true, the term "free software" as used by the Free Software Foundation
(originators of the GNU Project and creators of the GNU General Public License)
is intended to mean "free as in freedom" rather than in the sense of "no cost"
(which is usually referred to as "free as in free beer" or *gratis*).
Free software in this sense is software which you are free to use, copy, modify, redistribute, with no limit.
Contrast this with the licensing of most commercial software packages,
where you are allowed to load the software on a single computer,
are allowed to make no copies, and never see the source code.
Free software allows incredible freedom to the end user.
Since the source code is universally available, there are also many more chances for bugs to be caught and fixed.

When a program is licensed under the GNU General Public License (the GPL):

- You have the right to use the program for any purpose.
- You have the right to modify the program and have access to the source codes.
- You have the right to copy and distribute the program.
- You have the right to improve the program, and release your own versions.

In return for these rights, you have some responsibilities if you distribute a GPL'd program.
These responsibilities are designed to protect your freedoms and the freedoms of others:

- You must provide a copy of the GPL with the program,
  so that recipients are aware of their rights under the license.
- You must include the source code or make the source code freely available.
- If you modify the code and distribute the modified version,
  you must license your modifications available under the GPL (or a compatible license).
- You may not restrict the licensing of the program beyond the terms of the GPL
  (you may not turn a GPL'd program into a proprietary product).

For more on the GPL, check its page on
the `GNU Project website <https://www.gnu.org/licenses/licenses.html#GPL>`__.

.. note::

   The GPL only applies to the Blender application and **not** the artwork you create with it;
   for more info see the `Blender License <https://www.blender.org/about/license/>`__.


## Defaults

.. _splash-quick-start:

********
Defaults
********

When you start Blender for the first time or update to a new version, the interactive region of
the :doc:`Splash Screen </interface/window_system/splash>` is replaced with
a couple of initial preferences to configure how you interact with Blender.

.. note::

   These options can always be changed later in the :doc:`Preferences </editors/preferences/index>`.


Import Existing Settings
========================

This is where you can copy settings from an older version of Blender.
Doing so will copy preferences and startup files from the previous version of Blender and then loads them.

The settings need to be imported from previous versions because the configuration files of each Blender version
are stored in separate folders. Refer to the :doc:`/advanced/blender_directory_layout` page
for the location of these folders.

If you would like to start fresh with the new version, continue to `Create New Settings`_.


Create New Settings
===================

Language
   The language used in the user interface.
   The list is broken up into categories determining how complete the translations are.
   More language preferences can be set in the :ref:`Translation Preferences <prefs-interface-translation>`.

Shortcuts
   Presets for the default :doc:`keymap </editors/preferences/keymap>` for Blender.
   Note that this manual assumes that you use the "Blender" keymap.

   :Blender:
      This is the default keymap.
      Read more about this keymap :doc:`here </interface/keymap/blender_default>`.
   :Blender 2.7x:
      This keymap is intended to match an older series of Blender versions
      and is designed for people upgrading who do not want to learn the updated keymap.
   :Industry Compatible:
      This keymap is intended to match common creation software
      and is intended for people who use many different such applications.
      Read more about this keymap :doc:`here </interface/keymap/industry_compatible>`.

Select With
   Controls which mouse button, either right or left, is used to select items in Blender.

Spacebar
   Controls the action of :kbd:`Spacebar`.
   These and other shortcuts can be modified in the :doc:`keymap preferences </editors/preferences/keymap>`.

   :Play:
      Starts playing through the :doc:`Timeline </editors/timeline>`.
      This option is good for animation or video editing.
   :Tools:
      Opens the Toolbar underneath the cursor to quickly change the active tool.
      This option is good if doing a lot of modeling or rigging.
   :Search:
      Opens up the :doc:`Menu Search </interface/controls/templates/operator_search>`.
      This option is good for someone who is new to Blender and is unfamiliar with its menus and shortcuts.

Theme
   Choose between a light or dark theme for Blender.
   Themes can be customized more in the :doc:`Preferences </editors/preferences/themes>`.

Save New Settings
   Saves the settings set above and opens the regular :ref:`splash`.


Saving Defaults
===============

The preferences are automatically saved when changed.

Changing the default startup file can be done via
:menuselection:`File --> Defaults --> Save Startup File`.
See :ref:`Startup File <startup-file>`.

There are two areas where Blender's defaults are stored:

Preferences
   The :ref:`Preferences <prefs-menu>` file stores keymap, add-ons theme and other options.
Startup File
   The :ref:`Startup File <startup-file>` stores the scene and UI setup which are displayed at startup
   and when creating a new file (:menuselection:`File --> New`).


Loading Factory Settings
========================

You can revert your customizations to Blender's defaults:

Preferences
   The :ref:`Preferences <prefs-menu>` Load Factory Settings.
Startup File & Preferences
   :menuselection:`File --> Defaults --> Load Factory Settings`.

.. note::

   After loading the factory settings, the preferences won't be auto-saved.

   See :ref:`prefs-menu` for details.


## Hardware


***********************
Configuring Peripherals
***********************

Displays
========

A full HD display or higher is recommended.
Multi-monitor setups are supported, and workspaces can be configured to span multiple monitors.

.. figure:: /images/getting-started_configuration_hardware_multi-monitor.jpg

   Example of Blender's multi-monitor support.


Input Devices
=============

Blender supports various types of input devices:

- Keyboard (recommended: keyboard with numeric keypad, English layout works best)
- Mouse (recommended: three button mouse with scroll wheel)
- Graphic Tablet
- Touchpad
- NDOF Device (also known as *3D Mouse*)

.. note::

   If you don't have a middle mouse button or numpad, you can emulate these
   in the :doc:`Input Preferences </editors/preferences/input>`.


Mouse
-----

Mouse Button Emulation
^^^^^^^^^^^^^^^^^^^^^^

If you do not have a 3 button mouse,
you will need to emulate it by checking the option in the :doc:`Preferences </editors/preferences/input>`.

The following table shows the combinations used:

.. list-table::
   :stub-columns: 1

   * - 3-button Mouse
     - :kbd:`LMB`
     - :kbd:`MMB`
     - :kbd:`RMB`
   * - 2-button Mouse
     - :kbd:`LMB`
     - :kbd:`Alt-LMB`
     - :kbd:`RMB`


Keyboard
--------

Numpad Emulation
^^^^^^^^^^^^^^^^

If you do not have a numpad on the side of your keyboard,
you may want to emulate one. You can then use the number row at the top of the keyboard instead,
but will no longer have access to these keys' original functions (such as switching between
vertex/edge/face selection in Edit Mode).

.. seealso::

   Read more about *Numpad Emulation* in the :doc:`Preferences </editors/preferences/input>`.


Non-English Keyboards
^^^^^^^^^^^^^^^^^^^^^

If you use a keyboard with a non-English layout, you may still benefit from switching
to the UK or US layout while working with Blender.

.. note::

   You can also change the keymap from the :doc:`Preferences </editors/preferences/input>`.
   However, this manual assumes you are using the default keymap.


.. _hardware-tablet:

Graphic Tablet
--------------

Graphics tablets can be used to provide a more traditional method of controlling the mouse cursor using a pen.
This can help provide a more familiar experience for artists
who are used to painting and drawing with similar tools,
as well as provide additional controls such as pressure sensitivity.

.. note::

   If you are using a graphic tablet instead of a mouse and pressure sensitivity does not work properly,
   try to place the mouse pointer in the Blender window and then unplug/replug your graphic tablet. This might help.


.. _hardware-ndof:

Touchpad
--------

Touchpad controls are available on Windows, macOS and Linux with Wayland.
If you are working from a laptop without a mouse,
you can emulate controls using multi-touch gestures with the trackpad from
:doc:`Preferences </editors/preferences/input>`.

.. list-table:: Supported multi-touch gestures
   :header-rows: 1

   * - Gesture
     - Effect
   * - Pan
     - Hold the :kbd:`Shift` key while dragging two fingers on the pad.
   * - Zoom
     - Hold the :kbd:`Ctrl` or :kbd:`OSKey` key while dragging two fingers on the pad.
   * - Orbit
     - Drag two fingers on the pad.
   * - Emulate right-click
     - Tap two fingers on the pad.

NDOF (3D Mouse)
---------------

3D mice or :abbr:`NDOF (N-Degrees of Freedom)` devices are hardware that you can use to navigate a scene in Blender.
Currently only devices made by 3Dconnexion are supported.
These devices allow you to explore a scene, and make :ref:`Fly/Walk Navigation <3dview-fly-walk>`
easier to control. The NDOF device can be configured in the :ref:`Preferences <editors_preferences_input_ndof>`.
These settings can also be accessed directly from the viewport using the :kbd:`NDOFMenu` button on the NDOF device.

.. seealso::

   See :doc:`Input Preference </editors/preferences/input>` for more information on configuring peripherals.


.. _hardware-head-mounted-displays:

Head-Mounted Displays (Virtual Reality)
=======================================

:abbr:`HMDs (Head-Mounted Displays)` make it possible to place users in an interactive, virtual environment.
Attached to the head, they track head movements to project a seemingly surrounding world onto small
screens in front of the user's eyes. If the system works well, they experience the virtual environment as
if they were really inside of it.


Supported Platforms
-------------------

Virtual reality support in Blender is implemented through the multi-platform OpenXR standard.
This standard is new and therefore support for it is still limited.

.. list-table:: OpenXR compatible platforms.
   :header-rows: 1

   * - Platform
     - Operating System
     - Notes
   * - `HTC Vive Cosmos`_
     - Windows
     - `Developer Preview <https://forum.htc.com/topic/9046-vive-openxr-support-for-vive-cosmos/>`__
   * - `HTC Vive Focus 3`_
     - Windows
     - `Developer Preview <https://forum.htc.com/topic/9876-focus-3-openxr-support-status/page/3/>`__
   * - `Monado`_
     - GNU/Linux
     - *Not* recommended for general use yet.
   * - `Meta (formerly Oculus)`_ (Rift and Quest)
     - Windows
     - Requires Oculus v31 Software Update. Oculus Link required for Quest.
   * - `SteamVR`_
     - Windows, GNU/Linux
     - Requires SteamVR 1.16 or greater.
   * - `Varjo`_
     - Windows
     - --
   * - `Windows Mixed Reality`_
     - Windows
     - Requires Windows 10 May 2019 Update (1903).


Getting Started
---------------

The following subsections describe how an HMD can be set up for usage with the `supported platforms`_.
If this is not done, Blender will report an error when trying to start a virtual reality session.


HTC Vive Cosmos
^^^^^^^^^^^^^^^

The dedicated platform for
the `HTC Vive Cosmos <https://www.vive.com/eu/product/#cosmos%20series>`__
is currently targeted at developers and may lack features found in other platforms.

- Follow the steps from
  the `Vive Developer Forums <https://forum.htc.com/topic/9046-vive-openxr-support-for-vive-cosmos/>`__.
- Enable the :doc:`VR Scene Inspection add-on </addons/3d_view/vr_scene_inspection>` in Blender.


HTC Vive Focus 3
^^^^^^^^^^^^^^^^

The dedicated platform for
the `HTC Vive Focus 3 <https://www.vive.com/eu/product/vive-focus3/overview/>`__
is currently targeted at developers and may lack features found in other platforms.

- Follow the steps from
  the `Vive Developer Forums <https://forum.htc.com/topic/9876-focus-3-openxr-support-status/page/3/>`__.
- Enable the :doc:`VR Scene Inspection add-on </addons/3d_view/vr_scene_inspection>` in Blender.


Monado
^^^^^^

`Monado <https://monado.dev/>`__ is a :doc:`free and open source </getting_started/about/license>` XR
platform for Linux. It is not yet ready for production usage and should only be used for testing purposes.

- Packages are available for the following distributions:

  - Ubuntu (`Eoan, Focal <https://launchpad.net/~monado-xr/+archive/ubuntu/monado>`__)
  - Debian (`bullseye <https://packages.debian.org/bullseye/libopenxr1-monado>`__,
    `sid <https://packages.debian.org/sid/libopenxr1-monado>`__)

  For other systems, it has to be compiled from source, which in this case is not
  recommended for people with little experience in compiling software.
  Follow the `Getting Started Guides <https://gitlab.freedesktop.org/monado/monado/-/blob/main/README.md>`__
  from Monado to do so nevertheless.
- Enable the :doc:`VR Scene Inspection add-on </addons/3d_view/vr_scene_inspection>` in Blender.


Meta (formerly Oculus)
^^^^^^^^^^^^^^^^^^^^^^

`Meta (formerly Oculus) <https://www.meta.com/quest/>`__ provides full support for OpenXR as of the Oculus v31
Software Update.

- Download and install the `Oculus Rift/Oculus Link software <https://www.meta.com/quest/setup/>`__.
- Set Oculus as the active OpenXR runtime via the *General* tab in the Oculus App Settings.

.. figure:: /images/getting-started_configuration_hardware_xr_runtime_oculus.jpg
   :scale: 50 %

- Enable the :doc:`VR Scene Inspection add-on </addons/3d_view/vr_scene_inspection>` in Blender.


SteamVR
^^^^^^^

`SteamVR <https://www.steamvr.com/>`__ provides full support for OpenXR as of SteamVR 1.16.

- Set SteamVR as the active OpenXR runtime via the *Developer* tab in the SteamVR Settings.

.. figure:: /images/getting-started_configuration_hardware_xr_runtime_steamvr.jpg
   :scale: 50 %

- Enable the :doc:`VR Scene Inspection add-on </addons/3d_view/vr_scene_inspection>` in Blender.

.. note::

   The SteamVR runtime can also be used for HTC Vive Cosmos, Oculus, and Windows Mixed Reality HMDs.


Varjo
^^^^^

`Varjo <https://varjo.com/>`__ includes full OpenXR support with its required Varjo Base software.

- Enable the :doc:`VR Scene Inspection add-on </addons/3d_view/vr_scene_inspection>` in Blender.


Windows Mixed Reality
^^^^^^^^^^^^^^^^^^^^^

`Windows Mixed Reality <https://www.microsoft.com/windows/windows-mixed-reality>`__ provides full
support for OpenXR. To check if a PC meets the requirements to run the software, Microsoft offers the
`Windows Mixed Reality PC Check <https://www.microsoft.com/en-us/p/windows-mixed-reality-pc-check/9nzvl19n7cnc>`__
application.

- Make sure the Windows 10 May 2019 Update (1903) is installed.
- If the system meets all requirements, the Mixed Reality Portal should already be installed.
  It is also available in
  the `Microsoft Store <https://www.microsoft.com/en-us/p/mixed-reality-portal/9ng1h8b3zc7m>`__.
- Launch the Mixed Reality Portal. Click the menu button ``...`` in the lower left corner.
  In the menu it opens, select the *Set up OpenXR*.
- Enable the :doc:`VR Scene Inspection add-on </addons/3d_view/vr_scene_inspection>` in Blender.

.. note::

   To switch to Windows Mixed Reality from another OpenXR runtime
   (e.g. SteamVR), download the OpenXR Developer Tools from the `Microsoft Store
   <https://www.microsoft.com/en-us/p/openxr-developer-tools-for-windows-mixed-reality/9n5cvvl23qbt>`__
   and set Windows Mixed Reality as the active runtime.

.. figure:: /images/getting-started_configuration_hardware_xr_runtime_wmr.jpg
   :scale: 50 %


## Index


#######################
  Configuring Blender
#######################

.. toctree::
   :maxdepth: 2

   introduction.rst
   hardware.rst
   defaults.rst

.. seealso::

   See :ref:`prefs-index` for a complete list of options.


## Introduction


************
Introduction
************

Here are some preferences that you may wish to set initially.
See the section :doc:`Preferences </editors/preferences/index>`
for the complete list of available settings.


Language
========

Enable :menuselection:`Edit --> Preferences --> Interface --> Translation`,
and choose the *Language* and what to translate from *Interface*, *Tooltips* and *New Data*.

See :ref:`prefs-interface-translation` for details.


Input
=====

If you have a compact keyboard without a separate number pad, enable
:menuselection:`Preferences --> Input --> Keyboard --> Emulate Numpad`.
This gives you the 3D view shortcuts regularly used on the number pad.

If you do not have a middle mouse button, you can enable
:menuselection:`Preferences --> Input --> Mouse --> Emulate 3 Button Mouse`.
This allows you to hold the :kbd:`Alt`  or :kbd:`OSKey` key while dragging with the mouse, to orbit.

See :doc:`Input Preferences </editors/preferences/input>` for details.


File and Paths
==============

At :menuselection:`Preferences --> File Paths`
you can set options such as what *Image Editor* (GIMP, Krita...)
and *Animation Player* to use.

The :ref:`temp-dir` sets where to store files such as temporary renders and auto-saves.

.. tip::

   The ``//`` at the start of each path in Blender means the directory of the currently opened blend-file,
   used to reference relative paths.

See :doc:`File Preferences </editors/preferences/file_paths>` for details.


Save & Load
===========

If you trust the source of your blend-files, you can enable *Auto Run Python Scripts*.
This option is meant to protect you from malicious Python scripts in blend-files that you got from someone else.
Many users turn this option on, as advanced rigs tend to use scripts of some sort.

See Save & Load :ref:`bpy.types.PreferencesFilePaths.use_scripts_auto_execute` Preference.


## Index


######################
  Installing Blender
######################

Blender is released approximately every three months.
You can keep up to date with the latest changes through
the `release notes <https://www.blender.org/download/releases/>`__.


System Requirements
===================

Blender is available for download on Windows, macOS, and Linux.
Always check that the graphics drivers are up to date and that OpenGL is well supported.
Blender has a set of `minimum and recommended requirements <https://www.blender.org/download/requirements/>`__;
so make sure these are met before trying to install Blender.

Support for other hardware such as graphic tablets and 3D mice are covered later in
:doc:`Configuring Hardware </getting_started/configuration/hardware>`.


Download Blender
================

Blender offers a variety of different binary packages to choose from depending on their level of stability.
Each package has the trade off of newest feature versus stability.
The package that is right for you depends on your requirements for those two.
A studio for example might want to have *long-term support*, while a hobbyist may want newer features,
while others may just want to test upcoming features.
Each package described below has something just right for everyone.

`Stable Release <https://www.blender.org/download/>`__
   A package that contains the latest features and is considered stable without regressions.
   A new stable version is available about every three months.

`Long-term Support <https://www.blender.org/download/lts/>`__
   A package designed for long-lasting projects requiring a very stable version of Blender.
   :abbr:`LTS (Long-Term-Support)` releases are supported for two years
   and will not have any new features, API changes or improvements.
   A new long-term support version is available every year.

`Daily Builds <https://builder.blender.org/download/>`__
   A package updated daily to include the newest changes in development.
   These versions are not as thoroughly tested as the stable release, and might break,
   although they are official and usually not highly experimental.

.. note::

   Blender's source code is available for free to either reference or
   to `Build from Source <https://developer.blender.org/docs/handbook/building_blender/>`__.
   While normal users are **not** expected to compile Blender, it does have advantages:

   - Blender is always up to date.
   - It allows access to any version or branch where a feature is being developed.
   - It can be freely customized.

The procedure for installing a binary, either the latest stable release or a daily build, is the same.
Follow the steps for your platform.

.. note::

   Blender doesn't have a built-in updating system. This means you will need to update Blender yourself
   by following the upgrade steps described in the sections below.


Installation Guides
===================

.. toctree::
   :maxdepth: 1

   linux.rst
   macos.rst
   windows.rst
   steam.rst

.. This is referenced from ``linux.rst``, include in a hidden ``toctree`` to prevent warnings.
.. toctree::
   :hidden:

   linux_windowing_environment.rst


## Linux


*******************
Installing on Linux
*******************

Check the :doc:`Downloading Blender </getting_started/installing/index>`
page to find the minimum requirements and the different versions that are available
for Blender (if you have not done so yet).


Install from blender.org
========================

Download the Linux version for your architecture and decompress the file to the desired location
(e.g. ``~/software`` or ``/usr/local``).

Blender can now be launched by double-clicking the executable.

When using this method of installation, it is possible to have multiple versions of Blender installed.

For ease of access, you can configure your system by adding a menu entry or shortcut for Blender.
You may also associate blend-files with Blender so that when selected from the file browser,
they will automatically open in Blender.
These settings are typically found in conjunction with the Window Manager settings. (Gnome or KDE.)

To make the installation and configuration fully self-contained, set up a
:ref:`Portable Installation <portable-installation>`.


Install from Package Manager
============================

Some Linux distributions may have a specific package for Blender in their repositories.

Installing Blender via the distribution's native mechanisms ensures consistency with other packages on the system
and may provide other features (given by the package manager),
such as listing of packages, update notifications and automatic menu configuration.
Be aware, though, that the package may be outdated compared to the latest official release,
or not include some features of Blender. For example, some distributions do not build Blender with
Cycles GPU rendering support, for licensing or other reasons.

If there is a specific package for your distribution, you may choose what is preferable and most convenient,
otherwise, the official binary is available on `blender.org <https://www.blender.org/download/>`__.


Install from Snap
=================

`Snap <https://snapcraft.io/>`__ is a universal package manager designed to work across a range of distributions.
Assuming snap is already installed, Blender can be installed through snap with::

   snap install blender --classic

Installing from this method has a benefit that updates to Blender are automatically installed.
Blender from Snap should have a more consistent distribution then individual package managers.


Running from the Terminal
=========================

See :doc:`Launching from the terminal </advanced/command_line/launch/linux>`.


Graphics System (X11 & Wayland)
===============================

Blender supports both X11 and Wayland, see :ref:`linux-windowing-environment` for details.


Avoiding Alt-Mouse Conflict
===========================

Some window managers default to :kbd:`Alt-LMB` and :kbd:`Alt-RMB` for moving and resizing windows.

Blender uses these for various operations, notably:

- :ref:`Emulate 3 Button Mouse <bpy.types.PreferencesInput.use_mouse_emulate_3_button>`.
- :ref:`bpy.ops.mesh.loop_multi_select`.
- :ref:`Changing multiple properties at once <keymap-common-properties>`.

To access Blender's full feature set, you can change the window manager settings to use the *Meta* key instead
(also called *Super* or *Windows* key):

Gnome
   Enter the following in a command line (effective at next login):

   .. code-block:: sh

      gsettings set org.gnome.desktop.wm.preferences mouse-button-modifier '<Super>'

KDE
   :menuselection:`System Settings --> Window Management --> Window Behavior --> Window Actions`,
   Switch from 'Alt' to 'Meta' key.


Updating on Linux
=================

On Linux there are various ways of updating Blender. This section covers the most common approaches.


Updating from blender.org
-------------------------

When an update for Blender is released, it can be downloaded directly
from the `Blender website <https://www.blender.org/download/>`__
and installed using the steps described in the section `Install from blender.org`_.


Updating with a Package Manager
-------------------------------

Many Linux distributions have packages for Blender available, which can be installed
using the distribution's package manager. After installation,
Blender can be updated using the same steps as updating any other application.

.. seealso::

   The Splash screen :doc:`/getting_started/configuration/defaults` page for information
   about importing settings from previous Blender versions and other quick settings.


## Linux Windowing Environment

.. _linux-windowing-environment:

***************************
Linux Windowing Environment
***************************

On Linux Blender supports both X11 and Wayland for official releases.

When Wayland is detected, it is the preferred system, otherwise X11 will be used.

.. hint::

   The current "Windowing Environment" is listed in :menuselection:`File --> About`.


X11
===

This is the windowing environment that has been used most widely on Linux & Unix systems.

There are no near-term plans to deprecate or remove X11 support.


Wayland
=======

Support for Wayland is a more recent addition, so there may be configurations that have not been tested yet.
Please report a bug if you experience problems.

Blender has been tested with Gnome-Shell (mutter), KDE (plasma) & SWAY (wlroots) based compositors.


Requirements
------------

Gnome-Shell
   Under Gnome-Shell the ``libdecor`` library is required.
   This is available as a package on most Linux distribution.

   If the library isn't found X11 will be used as a fallback.


Troubleshooting
---------------

Detailed Wayland output can help to track down problems.
Launch Blender from the :doc:`command-line </advanced/command_line/launch/linux>` with additional arguments:

Blender's Wayland Logging
   .. code-block:: sh

      blender --log "ghost.wl.*" --log-level 2

Wayland Built-In Logging
   .. code-block:: sh

      WAYLAND_DEBUG=1 blender

Disable Wayland (forcing X11)
   .. code-block:: sh

      WAYLAND_DISPLAY="" blender

Disable ``libdecor`` (forcing borderless windows under Gnome-Shell)
   Uninstall ``libdecor``, then run Blender with an empty X11 display variable.

   .. code-block:: sh

      DISPLAY="" blender


Environment Variables
---------------------

``XCURSOR_THEME``
   The cursor theme to use (must refer to a locally installed cursor).

``XCURSOR_SIZE``
   The cursor size, defaults to 28, you may wish to increase the size on Hi-DPI displays.


Known Limitations
-----------------

Gnome Shell's Fractional Scaling (before version 44)
   Versions of Gnome-Shell prior to 44 don't fully support fractional scaling.

   Using fractional under older versions of Gnome-Shell may result in glitches such as a
   `small cursor size <https://projects.blender.org/blender/blender/issues/105895>`__.

NVidia GPU
   Currently NVidia drivers don't fully support features needed for Wayland. Graphical glitches and flickering are
   common problems. In some cases, there can be
   `crashes on startup <https://projects.blender.org/blender/blender/issues/103999>`__.
   This is not specific to Blender, so NVidia users may want to use X11 until driver support improves.

----

Feature Comparison
==================

.. |tick|  unicode:: U+2713
.. |cross| unicode:: U+2717
.. |none|  unicode:: U+2014

.. list-table::
   :header-rows: 1
   :class: valign
   :widths: 30 5 5 60

   * - Feature
     - X11
     - Wayland
     - Notes
   * - Smooth Scroll
     - |cross|
     - |tick|
     - | Smooth scrolling with track-pads.
   * - Multi-Touch Gestures
     - |cross|
     - |tick|
     - | Track-pad and tablet support for
       | pinch to zoom, pan and orbit.
   * - Reliable Cursor Warping
     - |cross| :sup:`*1`
     - |tick|
     - | Cursor warping is used while transforming
       | and orbiting the viewport for e.g.
   * - Window Positioning
     - |tick|
     - |cross| :sup:`*2`
     - | Needed for dragging between windows and
       | restoring window positions on file load.

Other features which both systems support such as Hi-DPI, 3D-mouse, tablet input, ... etc.
have been left out of this list.

| :sup:`*1` In X11 fast cursor motion may exit the window bounds while the cursor is grabbed (transforming for e.g.).
| :sup:`*2` Wayland doesn't support setting the window position,
  as this is a design decision it's unlikely to be supported
  (see issues for `position <https://projects.blender.org/blender/blender/issues/98928>`__).


## Macos


*******************
Installing on macOS
*******************

Check the :doc:`Downloading Blender </getting_started/installing/index>`
page to find the minimum requirements and the different versions that are available
for Blender (if you have not done so yet).

.. important::

   Blender supports both Intel and Apple Silicon architectures on macOS.
   Make sure to download a variant that is compatible with your CPU's architecture.


Install from DMG
================

Blender for macOS is distributed as disk images (dmg-files).
To mount the disk image, double-click on the dmg-file.
Then drag ``Blender.app`` into the Applications folder.

Depending on the Security and Privacy preferences of your Mac,
macOS will request your approval before opening Blender for the first time.

To make the installation and configuration fully self-contained, set up a
:ref:`Portable Installation <portable-installation>`.


Updating on macOS
=================

On macOS there are various ways of updating Blender. This section covers the most common approach.


Updating with DMG
-----------------

When an update for Blender is released, it can be downloaded directly
from the `Blender website <https://www.blender.org/download/>`__.
Install the new version by overwriting the current ``Blender.app`` in the Applications folder.
You can rename ``Blender.app`` or place it in a different folder to have more than one version at a time.

.. seealso::

   The Splash screen :doc:`/getting_started/configuration/defaults` page for information
   about importing settings from previous Blender versions and other quick settings.


## Steam


*********************
Installing from Steam
*********************

Steam is a software distribution platform. Blender can be downloaded and updated
using the Steam client by following the steps described below on Linux, macOS, or Windows.

Download the `Steam client <https://store.steampowered.com/>`__ for your operating system.
Once installed, open the client and login to your Steam account, or create one if you haven't already.
Once logged in, navigate to the *Store* tab, search for "Blender", and press the green installation button.
Blender should now be available in the *Library* tab of the Steam client.

.. seealso::

   When installing Blender from Steam on Linux and Windows, the ``.blend`` filename extension will not
   be automatically associated with Blender. To associate blend-files with Blender, see the processes
   described on the :doc:`Linux </getting_started/installing/linux>` and
   :doc:`Windows </getting_started/installing/windows>` installation pages.


Updating with Steam
===================

When an update for Blender is available on Steam, Steam will automatically update Blender for you.


## Windows


*********************
Installing on Windows
*********************

Check the :doc:`Downloading Blender </getting_started/installing/index>`
page to find the minimum requirements and the different versions that are available
for Blender (if you have not done so yet).

Download the zip-file or Windows Installer File.

.. important::

   Blender supports both x64 and arm64 architectures on Windows.
   Make sure to download a variant that is compatible with your CPU's architecture.


Install from Windows Installer File
===================================

The Windows installer will let you choose an installation folder,
and will create an entry in the start menu as well as associate blend-files with Blender.
It requires administrator rights.


Install from Zip
================

When choosing the zip-file, you have to manually extract Blender to the desired folder,
where you can double-click the executable to run Blender.

No start menu item will be created and no blend-file association will be registered,
but there is also no need for administrator rights. You can register the file association
manually by clicking *Make Default* on the System tab of the
:doc:`Preferences </editors/preferences/system>`. Alternatively, you can run ``blender -r``
from the :doc:`Command Line </advanced/command_line/arguments>`.

To make the installation and configuration fully self-contained, set up a
:ref:`Portable Installation <portable-installation>`.


Install from Microsoft Store
============================

Blender can be installed from the Microsoft Store by searching for Blender in the Microsoft Store
and installing it.

Blender can now be launched from the Windows Start menu.


Updating on Windows
===================

On Windows there are various ways of updating Blender. This section covers the most common approaches.


Updating from Windows Installer File
------------------------------------

When an update for Blender is released, it can be downloaded directly
from the `Blender website <https://www.blender.org/download/>`__.
The Windows installer can then be run to install the updated version of Blender.
To remove a previously installed version of Blender,
use Windows settings or control panel to uninstall the desired version.


Updating from Zip
-----------------

When an update for Blender is released, it can be downloaded directly
from the `Blender website <https://www.blender.org/download/>`__
and extracted to the desired folder, where you can double-click the executable to run Blender.
For more information on creating a portable version of Blender, see the section `Install from Zip`_.

Note, you do not have to overwrite your existing Blender installation.
It's perfectly possible to have multiple versions installed side by side.


Updating from the Microsoft Store
---------------------------------

When an update for Blender is available on the Microsoft Store, it will be downloaded
and installed automatically.

.. seealso::

   The Splash screen :doc:`/getting_started/configuration/defaults` page for information
   about importing settings from previous Blender versions and other quick settings.


