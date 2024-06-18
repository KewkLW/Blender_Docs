# Index for files

- [Custom Properties](#Custom-Properties)
- [Data Blocks](#Data-Blocks)
- [Index](#Index)
- [Introduction](#Introduction)
- [Catalogs](#Catalogs)
- [Index](#Index)
- [Introduction](#Introduction)
- [Compatibility](#Compatibility)
- [Index](#Index)
- [Open Save](#Open-Save)
- [Packed Data](#Packed-Data)
- [Previews](#Previews)
- [Rename](#Rename)
- [Alembic](#Alembic)
- [Collada](#Collada)
- [Grease Pencil Pdf](#Grease-Pencil-Pdf)
- [Grease Pencil Svg](#Grease-Pencil-Svg)
- [Index](#Index)
- [Obj](#Obj)
- [Ply](#Ply)
- [Stl](#Stl)
- [Usd](#Usd)
- [Index](#Index)
- [Library Overrides](#Library-Overrides)
- [Library Proxies](#Library-Proxies)
- [Link Append](#Link-Append)
- [Image Formats](#Image-Formats)
- [Index](#Index)
- [Video Formats](#Video-Formats)


## Custom Properties

.. _files-data_blocks-custom-properties:
.. _bpy.types.bpy_struct:
.. _bpy.ops.wm.properties:

*****************
Custom Properties
*****************

.. figure:: /images/files_data-blocks_add.png
   :align: right

   Custom Properties panel.

Custom properties are a way to store your own data in Blender's data-blocks. It can be used for rigging
(where bones and objects can have custom properties driving other properties), and Python scripts,
where it's common to define new settings not available in Blender. It is also possible to access
custom properties from materials via the :doc:`Attribute Node </render/shader_nodes/input/attribute>`.

Only certain data supports custom properties:

- All :ref:`data-blocks types <data-system-datablock-types>`.
- Bones and pose bones.
- Sequence strips.

To add a custom property, search for the *Custom Properties* panel,
found at the bottom of most :doc:`Properties </editors/properties_editor>` or Sidebar region, and click *New*.
Properties can be removed from the same location with the delete icon.
Once properties are added they can be configured via the edit icon to work for a particular use case;
see `Editing Properties`_ for more information.


.. _bpy.ops.wm.properties_edit:

Editing Properties
==================

User Interface
--------------

.. figure:: /images/files_data-blocks_edit.png
   :align: right

   Custom Properties edit pop-up.

Custom properties can be edited using the panel available for data types that support it.
Editing the properties allows you to configure things such as default values,
ranges, and even add a custom tooltip.

.. container:: lead

   .. clear

Type
   The data type of the property; different data types have can only have specific data properties.

   :Float: A numeric value with decimals e.g. 3.141, 5.0, or 6.125.
   :Float Array:
      A collection of multiple float data types e.g. ``[3.141, 5.0, 6.125]`` .
      This data type can also be used for data that can be represented as a float array such as colors.
      These special float arrays can be set in the *Subtype* selector.
   :Integer: A numeric value without any decimals e.g. 1, 2, 3, or 4.
   :Integer Array: A collection of multiple integer data types e.g. ``[1, 2, 3, 4]`` .
   :Boolean: A data type that has two possible values e.g. ``True`` or ``False``.
   :Boolean Array: A collection of boolean values  e.g. ``[True, False, True]``
   :String: A sequence of characters such as "Some Text".
   :Data-Block: A reference to a Blender object, see :doc:`/files/data_blocks`.
   :Python: Edit a Python data type directly, used for unsupported data types.

Array Length
   The number of elements in the array.
   Note that if the array length is greater than 7 you cannot directly edit its elements,
   you must press *Edit Value* to edit the elements of the array.

Property Name
   The text that is displayed to the left of the value.
   This name is also used to access the property via Python.

Default Value
   This sets the default value of the property used by the
   :ref:`Reset to Default Value <bpy.ops.ui.reset_default_button>` operator.

   .. warning::

      Default values are used as the basis of :ref:`NLA blending <bpy.types.AnimData.action_blend_type>`,
      and a nonsensical default (e.g. 0 for a property used for scaling) on a property intended for
      being keyframed is likely to cause issues.

Min, Max
   The minimum/maximum value the custom property can take.

Library Overridable
   Allow the property to be :doc:`overridden </files/linked_libraries/library_overrides>`
   when the data-block is linked.

Soft Limits
   Enables limits that the *Property Value* slider can be adjusted to
   without having to input the value numerically.

   Soft Min, Max
      The minimum/maximum value for the soft limit.

Step
   A multiplier to control how much the data type is incremented at a time.
   The internal step size for floats is 0.01, so a *Step* value of 5 will
   increment at a rate of 0.05 and a *Step* value of 100 will increment by 1.0.
   For integers the internal step size is 1.

Precision
   The number of digits after the decimal to display in the user interface for float data types.

Subtype
   Specifies the type of data the property contains, which affects how it appears in the user interface.
   This option is only available for float properties and has different options for regular floats and float arrays.
   Note, the unit often depends on the :ref:`Scene Units <bpy.types.UnitSettings>`.

   For regular floats:

   :Plane Data: Data values do not have any special behavior.
   :Pixel: A measure digital image resolution.
   :Percentage: The displayed value is a percentage, typically you will want the Min and Max values to be 0 and 100.
   :Factor: A percentage between an upper and lower bound which typical have a numerical significance.
   :Angle: A measure between intersecting lines.
   :Time: Time specified in seconds.
   :Distance: Measure of space between items.
   :Power: Work as a factor of time, measured in watts. This is used in Blender to measure light intensity.
   :Temperature: Intensity of heat present.

   For float arrays:

   :Plane Data: Data values do not have any special behavior.
   :Linear Color: Color in linear color space.
   :Gamma-Corrected Color: Color in gamma corrected color space.
   :Euler Angles: :term:`Euler Rotation` angles.
   :Quaternion Angles: :term:`Quaternion Rotation` angles.

   .. note::

      For either of the color subtypes to work as expected the *Property Value* must be a vector
      with three or four values depending on the availability of an :term:`Alpha Channel`.

ID Type :guilabel:`Data-Block`
   The ID-block type. For example: Key, Image, Object, Material.
   See :ref:`data-system-datablock-types` for a full list.

Description
   Allows you to write a custom :doc:`Tooltip </getting_started/help>` for your property.


Python Access
-------------

Custom properties can be accessed in a similar way to
`dictionaries <https://docs.python.org/3/tutorial/datastructures.html#dictionaries>`__,
with the constraints that keys can only be strings,
and values can only be strings, numbers, arrays of such, or nested properties.

See the `API documentation <https://docs.blender.org/api/current/info_quickstart.html#custom-properties>`__
for details.


## Data Blocks

.. _bpy.types.ID:
.. _bpy.types.BlendData:

***********
Data-Blocks
***********

The base unit for any Blender project is the data-block. Examples of data-blocks include:
meshes, objects, materials, textures, node trees, scenes, texts, brushes, and even Workspaces.

.. figure:: /images/files_data-blocks_outliner-blender-file-view.png
   :align: right

   Blender File view of the Outliner.

A data-block is a generic abstraction of very different kinds of data,
which features a common set of basic features, properties and behaviors.

Some common characteristics:

- They are the primary contents of the blend-file.
- They can reference each other, for reuse and instancing.
  (Child/parent, object/object-data, materials/images, in modifiers or constraints too...)
- Their names are unique within a blend-file, for a given type.
- They can be added/removed/edited/duplicated.
- They can be linked between files (only enabled for a limited set of data-blocks).
- They can have their own animation data.
- They can have :doc:`/files/custom_properties`.

User will typically interact with the higher level data types (objects, meshes, etc.).
When doing more complex projects, managing data-blocks becomes more important,
especially when inter-linking blend-files.
The main editor for that is the :doc:`Outliner </editors/outliner/index>`.

Not all data in Blender is a data-block,
bones, sequence strips or vertex groups e.g. are not,
they belong to armature, scene and mesh types respectively.


.. _data-system-datablock-types:

Data-Block Types
================

.. Editor's Note:
   Mostly we want to avoid long lists of data -- but in this case,
   it is the only comprehensive list of data-blocks, and something which you cannot
   find directly just through looking at the interface.
   ::
   (TODO add) links to related docs for each type.

.. Image source Scene tab --> Active keying set panel --> ID-block (sound replaced).

.. figure:: /images/files_data-blocks_id-types.png
   :align: right

   Data-blocks types with their icon.

For reference, here is a table of data-blocks types stored in blend-files.

Link
   Library Linking, supports being linked into other blend-files.
Pack
   File Packing, supports file contents being packed into the blend-file
   (**not** applicable for most data-blocks which have no file reference).

.. Editor's Note:
   For each data-block, we have 2 lines.
   1) a terse description.
   2) how its used.
   ::
   Keep these short.

.. container:: lead

   .. clear

.. |tick|  unicode:: U+2713
.. |cross| unicode:: U+2717
.. |none|  unicode:: U+2014

.. list-table::
   :header-rows: 1
   :class: valign
   :widths: 20 5 5 70

   * - Type
     - Link
     - Pack
     - Description
   * - :doc:`Action </animation/actions>`
     - |tick|
     - |none|
     - Stores animation F-Curves.
       Used as data-block animation data, and the Nonlinear Animation editor.
   * - :doc:`Armature </animation/armatures/introduction>`
     - |tick|
     - |none|
     - Skeleton used to deform meshes.
       Used as data of armature objects, and by the Armature Modifier.
   * - :doc:`Brush </sculpt_paint/brush/brush>`
     - |tick|
     - |none|
     - Used by paint tools.
   * - :doc:`Camera </render/cameras>`
     - |tick|
     - |none|
     - Used as data by camera objects.
   * - :doc:`Cache File </modeling/modifiers/modify/mesh_sequence_cache>`
     - |tick|
     - |none|
     - Used by Mesh Cache modifiers.
   * - :doc:`Curve </modeling/curves/introduction>`
     - |tick|
     - |none|
     - Used as data by curve, font & surface objects.
   * - :doc:`Font </modeling/texts/introduction>`
     - |tick|
     - |tick|
     - References font files.
       Used by curve object-data of text objects.
   * - :doc:`Grease Pencil </grease_pencil/introduction>`
     - |tick|
     - |none|
     - 2D/3D sketch data used by Grease Pencil objects.
       Used as overlay *helper* info, by the 3D Viewport, Image, Sequencer & Movie Clip editors.
   * - :doc:`Collection </scene_layout/collections/introduction>`
     - |tick|
     - |none|
     - Group and organize objects in scenes.
       Used to instance objects, and in library linking.
   * - :doc:`Image </editors/image/introduction>`
     - |tick|
     - |tick|
     - Image files.
       Used by shader nodes and textures.
   * - :doc:`Keys (Shape Keys) </animation/shape_keys/introduction>`
     - |cross|
     - |none|
     - Geometry shape storage, which can be animated.
       Used by mesh, curve, and lattice objects.
   * - :doc:`Light </render/lights/light_object>`
     - |tick|
     - |none|
     - Used as object data by light objects.
   * - :doc:`Library </files/linked_libraries/index>`
     - |cross|
     - |tick|
     - References to an external blend-file.
       Access from the Outliner's *Blender File* view.
   * - :doc:`Line Style </render/freestyle/introduction>`
     - |tick|
     - |none|
     - Used by the Freestyle renderer.
   * - :doc:`Lattice </animation/lattice>`
     - |tick|
     - |none|
     - Grid based lattice deformation.
       Used as data of lattice objects, and by the Lattice Modifier.
   * - :doc:`Mask </movie_clip/masking/introduction>`
     - |tick|
     - |none|
     - 2D animated mask curves.
       Used by compositing nodes & sequencer strip.
   * - :doc:`Material </render/materials/introduction>`
     - |tick|
     - |none|
     - Set shading and texturing render properties.
       Used by objects, meshes & curves.
   * - :doc:`Metaball </modeling/metas/introduction>`
     - |tick|
     - |none|
     - An isosurface in 3D space.
       Used as data of metaball objects.
   * - :doc:`Mesh </modeling/meshes/introduction>`
     - |tick|
     - |none|
     - Geometry made of vertices/edges/faces.
       Used as data of mesh objects.
   * - :doc:`Movie Clip </editors/clip/introduction>`
     - |tick|
     - |cross|
     - Reference to an image sequence or video file.
       Used in the *Movie Clip* editor.
   * - :doc:`Node Tree </render/shader_nodes/groups>`
     - |tick|
     - |none|
     - Groups of re-usable nodes.
       Used in the node editors.
   * - :doc:`Object </scene_layout/object/introduction>`
     - |tick|
     - |none|
     - An entity in the scene with location, scale, rotation.
       Used by scenes & collections.
   * - :doc:`Paint Curve </sculpt_paint/brush/stroke>`
     - |tick|
     - |none|
     - Stores a paint or sculpt stroke.
       Access from the paint tools.
   * - :doc:`Palette </sculpt_paint/index>`
     - |tick|
     - |none|
     - Store color presets.
       Access from the paint tools.
   * - :doc:`Particle </physics/particles/introduction>`
     - |tick|
     - |none|
     - Particle settings.
       Used by particle systems.
   * - :doc:`Light Probe </render/eevee/light_probes/index>`
     - |tick|
     - |none|
     - Help achieve complex real-time lighting in EEVEE.
   * - :doc:`Scene </scene_layout/scene/introduction>`
     - |tick|
     - |none|
     - Primary store of all data displayed and animated.
       Used as top-level storage for objects & animation.
   * - :doc:`Sounds </render/output/audio/speaker>`
     - |tick|
     - |tick|
     - Reference to sound files.
       Used as data of speaker objects.
   * - :doc:`Speaker </render/output/audio/speaker>`
     - |tick|
     - |none|
     - Sound sources for a 3D scene.
       Used as data of speaker object.
   * - :doc:`Text </editors/text_editor>`
     - |tick|
     - |cross|
     - Text data.
       Used by Python scripts and OSL shaders.
   * - :doc:`Texture </render/materials/legacy_textures/introduction>`
     - |tick|
     - |none|
     - 2D/3D textures.
       Used by brushes and modifiers.
   * - :doc:`Window Manager </interface/window_system/introduction>`
     - |cross|
     - |none|
     - The overarching manager for all of Blender's user interface.
       Includes Workspaces, notification system, operators, and keymaps.
   * - :doc:`World </render/lights/world>`
     - |tick|
     - |none|
     - Define global render environment settings.
   * - :doc:`Workspace </interface/window_system/workspaces>`
     - |cross|
     - |none|
     - UI layout.
       Used by each window, which has its own workspace.


.. _data-system-datablock-life-time:

Life Time
=========

Every data-block has its usage counted (reference count), when there is more than one,
you can see the number of current users of a data-block to the right of its name in the interface.
Blender follows the general rule that unused data is eventually removed.

Since it is common to add and remove a lot of data while working,
this has the advantage of not having to manually manage every single data-block.
This works by skipping zero user data-blocks when writing blend-files.


.. _data-system-datablock-fake-user:

Protected
---------

Since zero user data-blocks are not saved,
there are times when you want to force the data to be kept irrespective of its users.

If you are building a blend-file to serve as a library of assets that you intend to link to and from other files,
you will need to make sure that they do not accidentally get deleted from the library file.

To protect a data-block, use the button with the shield icon next to its name.
The data-block will then never be silently deleted by Blender,
but you can still manually remove it if needed.


Sharing
=======

Data-blocks can be shared among other data-blocks.

Examples where sharing data is common:

- Sharing textures among materials.
- Sharing meshes between objects (instances).
- Sharing animated actions between objects,
  for example to make all the lights dim together.

You can also share data-blocks between files, see
:doc:`linked libraries </files/linked_libraries/index>`.


.. _data-system-datablock-make-single-user:

Making Single User
==================

When a data-block is shared between several users, you can make a copy of it for a given user.
To do so, click on the user count button to the right of its name.
This will duplicate that data-block and assign the newly created copy to that usage only.

.. note::

   Objects have a set of more advanced actions to become single-user,
   see :ref:`their documentation <bpy.ops.object.make_single_user>`.


Removing Data-Blocks
====================

As covered in `Life Time`_, data-blocks are typically removed when they are no longer used.
They can also be manually *unlinked* or *deleted*.

Unlinking a data-block means that its user won't use it anymore.
This can be achieved by clicking on the "X" icon next to a data-block's name.
If you unlink a data-block from all of its users,
it will eventually be deleted by Blender as described above (unless it is a protected one).

Deleting a data-block directly erases it from the blend-file, automatically unlinking it from all of its users.
This can be achieved by :kbd:`Shift-LMB` on the "X" icon next to its name.

.. warning::

   Deleting some data-blocks can lead to deletion of some of its users, which would become invalid without them.
   The main example is that object-data deletion (like mesh, curve, camera...) will also delete all objects using it.

Those two operations are also available in the context menu
when :kbd:`RMB`-clicking on a data-block in the *Outliner*.


## Index


################################
  Assets, Files, & Data System
################################

.. toctree::
   :maxdepth: 2

   introduction.rst
   blend/index.rst
   data_blocks.rst
   custom_properties.rst
   linked_libraries/index.rst
   asset_libraries/index.rst
   media/index.rst
   import_export/index.rst


## Introduction


************
Introduction
************

Each blend-file contains a database.
This database contains all scenes, objects, meshes, textures, etc. that are in the file.

A file can contain multiple :doc:`Scenes </scene_layout/scene/introduction>`
and each scene can contain multiple :doc:`Objects </scene_layout/object/introduction>`.
Objects can contain multiple materials which can contain many textures.
It is also possible to create links between different objects, or share data between objects.
A file can link data from other Blender files.


Outliner
========

You can easily inspect the contents of your file by using the *Outliner* editor,
which displays all of the data in your blend-file.

The *Outliner* allows you to do simple operations on objects,
such as selecting, renaming, deleting, linking and parenting.

:doc:`Read more about the Outliner </editors/outliner/index>`.


## Catalogs


**************
Asset Catalogs
**************

Asset Catalogs help you to organize your assets. They look a little bit like file directories,
but they are completely independent of the location of your blend-files.
Assign each asset in a blend-file to its own catalog, or have one big catalog
with all the assets of all the blend-files combined. It's all up to you.

Similar to :doc:`/scene_layout/collections/collections`, catalogs can be nested
i.e. you can have a main catalog that contains several nested catalogs.
For example, this allows you to have a catalog of assets for "Furniture"
with sub-catalogs of "Tables", "Chairs", "Lamps", etc...

For more technical information,
see `Asset Catalogs on the Blender Developer Documentation <https://developer.blender.org/docs/features/asset_system/backend/asset_catalogs/>`__.

.. figure:: /images/asset-browser-catalogs.png
   :width: 640px

   Example file system and catalog structures.


The Home Location of Assets
===========================

There can be as many catalogs as you want, but **an asset can be assigned to a single catalog** at a time.
This is similar to a file system, where a file is only in one directory
(ignoring advanced things like symbolic links).

Catalogs themselves can be nested and moved by dragging and dropping.
Moving a catalog will not modify the assets it contains; they will simply move along
to the new location of the catalog.

Selecting a catalog in the Asset Browser will show all assets in that catalog and in child catalogs.
So, in the preceding example, selecting ``Characters/Ellie/Poses`` will also show assets from
``Characters/Ellie/Poses/Head`` and ``Characters/Ellie/Poses/Hands``.


.. _bpy.ops.asset.catalog_new:

Creating Catalogs
=================

New catalogs can be created in the :doc:`/editors/asset_browser`
through :menuselection:`Header --> Catalog --> New Asset Catalog`.
Once the catalog is created you can double :kbd:`LMB` on it's name in the
*Source List* region of the editor to give the catalog a more descriptive name.
Catalogs can also be created in this region by clicking the plus icon found at the top of the tree view.


Assigning an Asset
==================

.. figure:: /images/asset_browser-assign_catalog.png

   Assigning a selection of "Scale material" assets to a catalog.

To assign assets to a catalog, just select and drag the assets on top of the catalog.

.. tip::

   You can assign an asset to the "Unassigned" catalog,
   this will remove it from any existing catalogs.


.. _bpy.ops.asset.catalogs_save:

Saving Catalogs
===============

Saving catalogs makes any edits to any catalogs permanent by writing the current set up to the asset library.
Catalogs can be saved in the :doc:`/editors/asset_browser`
through :menuselection:`Header --> Catalog --> Save Asset Catalog`.
Once the catalog is created you can double :kbd:`LMB` on it's name
Catalogs can also be saved in the *Source List* region of the editor
by clicking the save icon found at the top of the tree view.


Components of a Catalog
=======================

Each catalog consists of a *catalog path*, a *UUID*, and a *simple name*.
Normally you would only deal with the catalog path; the rest is for internal Blender
use and/or for emergency situations.


Catalog Path
------------

The path of a catalog determines where in the catalog hierarchy the catalog is shown.
Examples are ``Characters/Ellie/Poses/Hand`` or ``Kitbash/City/Skyscrapers``,
which would result in the following catalog tree.
The highlighted catalog has path ``Characters/Ellie/Poses/Hand``.

.. figure:: /images/asset-catalog-tree.png
   :width: 257px

   Example tree of asset catalogs.


UUID
----

Each catalog has a `UUID <https://en.wikipedia.org/wiki/Universally_unique_identifier>`__,
which is normally hidden from the user interface
(enable Developer Extras and the experimental Asset Debug Info option to see them).
This is what is stored in the asset, and what determines the "identity" of the catalog.
As a result, a catalog can be renamed or moved around (i.e. you can change its path),
and all assets that are contained in it will move along with it.
This only requires a change to the catalog itself, and not to any asset blend-file.


Simple Name
-----------

Each catalog has an optional *simple name*. This name is stored along with the UUID in each asset.
The purpose is to make it possible for humans to recognize the catalog the asset was assigned to,
even when the *catalog definition file* (see below) is lost.

Like the UUID, the simple name is normally hidden from the user interface.
Enable Developer Extras in the interface preferences to make it visible in the Asset Browser.


.. _asset-catalog-definition-file:

Catalog Definition Files
========================

Asset catalogs are stored in Catalog Definition Files (CDFs). Blender 3.0 supports a single CDF per asset library.
It is stored in ``blender_assets.cats.txt`` in the root directory of the asset library. If the file does not exist,
Blender will create it when the catalogs are saved. When catalogs are changed, Blender updates that file, but also
creates a backup of the previous state to a file named ``blender_assets.cats.txt~``.


Which File to Write To
----------------------

Asset catalogs can be saved independently of the blend-file; the catalog editor has its own "Save" button.


Format
------

Catalog Definition Files (CDFs) are relatively simple text files, encoded in UTF-8.
Each CDF consists of a version indicator, and a line of text per catalog.
Each catalog line is colon-separated, of the form ``{UUID}:{path}:{simple name}``.


Example
-------

This is an example of a valid catalog definition file::

   # This is an Asset Catalog Definition file for Blender.
   #
   # Empty lines and lines starting with `#` will be ignored.
   # The first non-ignored line should be the version indicator.
   # Subsequent lines are of the format "CATALOG_UUID:catalog/path/for/assets:simple catalog name"

   VERSION 1

   313ea471-7c81-4de6-af81-fb04c3535d0e:catalog/without/simple/name:
   ee9c7b60-02f1-4058-bed6-539b8d2a6d34:character/Ellie/poselib:character-Ellie-poselib
   cd66bf52-58f4-45cb-a4e2-dc0e0ee8f3fe:character/Ellie/poselib:character-Ellie
   4eb44ec6-3424-405b-9782-ca006953e799:character/Ellie/poselib/white space:character-Ellie-poselib-white space
   b63ed357-2511-4b96-8728-1b5a7093824c:character/Ružena/poselib:Ružena pose library
   dcdee4df-926e-4d72-b995-33106983bb9a:character/Ružena/poselib/face:Ružena face
   fb698f2e-9e2b-4146-a539-3af292d44899:character/Ružena/poselib/hand:Ružena hands


Valid Catalog Paths
-------------------

Catalog paths follow the following rules:

- All paths are absolute; there is no difference between ``/a/b`` and ``a/b``.
- Only ``/`` as separator (no ``\``; think less filesystem path and more URL).
- Not empty (it's required for a valid catalog).
- No empty components (so not ``a//b``; ``a/b`` is fine).
- Invalid characters: ``:``, ``\``.
- Paths are always interpreted as UTF-8.


## Index


###################
  Asset Libraries
###################

.. toctree::
   :maxdepth: 2

   introduction.rst
   catalogs.rst


## Introduction


************
Introduction
************

This section describes Blender's asset library system. It was introduced in Blender 3.0,
and will be improved and expanded over multiple upcoming releases.

.. seealso::

   :doc:`/editors/asset_browser`
      The main interface for organizing and using assets.

   :doc:`/files/asset_libraries/catalogs`
      For organizing assets.

   :doc:`/animation/armatures/posing/editing/pose_library`
      Build on top of the Asset Browser.

   The following blog posts were written during the design and development of the Asset Browser.
   They are linked here for historical reasons, and to give some more context to the current design.

   - `2020-03: Asset Manager <https://code.blender.org/2020/03/asset-manager/>`__
   - `2021-06: Asset Browser Project Update <https://code.blender.org/2021/06/asset-browser-project-update/>`__
   - `2021-06: Asset Browser Workshop Outcomes <https://code.blender.org/2021/06/asset-browser-workshop-outcomes/>`__


What is an Asset?
=================

**An asset is a data-block with meaning**.

A blend-file is a database with multiple :doc:`/files/data_blocks`: objects, textures, materials,
etc. When planning to re-use or share these, the data needs a meaning. What is this? What is this for?
**Assets are curated data-blocks that are meant for easy reuse**.

.. note::

   The general term "asset" often also refers to other file types, such as images, sounds, video files, etc.
   These are currently not supported as asset in Blender.

   For more info, see :ref:`asset-libraries-future-development`.


.. _what-is-asset-library:

What is an Asset Library?
=========================

An asset library is a directory on your drive that is registered in the Preferences as an asset library.
Registering it means that you give the library a name (like "Sprite Fright")
and the location on drive (like ``/home/sybren/projects/sprite-fright/assets``).

.. figure:: /images/asset_browser-asset_library_preferences.png

   Name and Location of asset libraries in the Preferences.

Once registered, you can select the asset library in the Asset Browser.
All the blend-files in the asset library will be scanned for assets,
and all those assets will be shown in the Asset Browser.

.. note::

   Loading an asset library for the first time may take a while, but the next time it is loaded should be
   significantly faster. Blender generates an index of all assets contained inside an asset library,
   and keeps it up-to-date as files are modified within it. The indices are stored in the :ref:`local-cache-dir`.

The blend-files can be directly in the top-level directory of the asset library, or in any subdirectory.
The on-drive organization of asset libraries is all up to you. Regardless of which blend-file contains the assets,
each asset can be assigned a **catalog**. For more info about how to organize your assets
this way, see :doc:`/files/asset_libraries/catalogs`.


.. _asset-types:

Asset Types
===========

Assets can be broadly divided into two types: **primitive** and **preset** assets.
Which is which depends on the :doc:`/files/data_blocks` type.

Primitive assets are data-blocks that are either **linked or appended** to the current file.
Examples are objects, materials, and worlds. These can be dragged from the Asset Browser into
the scene (objects and worlds), or onto existing objects (materials).

Preset assets are data-blocks that are loaded and then **applied** to something.
An example is a pose asset. When applying the pose, the data-block is loaded
from its blend-file, and then the pose is applied to the active armature.

In the future, the asset type definition will be expanded;
see :ref:`asset-libraries-future-development` for more info.


.. _asset-library-current-file:

The Current File Asset Library
==============================

To help with the management of assets in the current blend-file, you can set the Asset Browser
to show the **Current File asset library**. This always shows the assets in the current file,
even when the current file is not saved in an asset library.
This also makes it possible to create assets and use them in the same file,
for small single-file projects.

When the current blend-file is part of an asset library, you can also see its assets in that library, of course.
The assets that are in the current file are marked with an icon; only those are editable.


Life Cycle of an Asset
======================

This section describes how to create, edit, share, and use assets.


.. _asset-create:
.. _bpy.ops.asset.mark:

Creating an Asset
-----------------

To create an asset, first create the thing you want to turn into an asset.
That is, create the object, material, world, or pose your character.
The next step depends on the type of asset (see :ref:`asset-types` above).

For primitive assets, use the **Mark as Asset** operator. It can be found in
the data-block selector, in the Outliner, and for objects in the 3D Viewport Object menu.
When using *Mark as Asset*, an automatic preview is generated.
If you want, you can also change or replace this with an image of your own choosing;
use the folder button next to the preview image in the Asset Details region of the Asset Browser.

For preset assets, there will be a dedicated button for the different asset types.
Currently poses are the only preset assets; use the **Create Pose Asset** button in the Action editor.
This will copy the pose of the selected bones into a new Action, mark it as asset,
and put it into the currently active asset catalog if there is an Asset Browser open.

After creating the asset, make sure the current blend-file is saved in your asset library.
Blender does not copy the asset into the asset library for you.


.. _asset-edit:

Editing Assets
--------------

Since assets are regular data-blocks, with just a little bit of metadata attached,
they can be edited like any other Blender data.
Just open the file and edit the object, material, world, etc.

For poses assets, this is also possible. With the pose library file open,
just click the **Assign Action** button to assign the pose action to the currently selected armature.
Then you can use all of the animation tooling to edit the pose, remove or add keys, etc.

Editing asset metadata can be done via the :ref:`Asset Browser <editing-asset-metadata>`.


Sharing Assets
--------------

Because assets are simply stored in blend-files, they can be shared by sharing their blend-file.
Be sure to include the :ref:`Asset Catalog Definition File <asset-catalog-definition-file>` as well.

There is currently no functionality to extract selected assets and save them
(together with their catalog definitions) into a different blend-file.
This could be implemented as an add-on.


Using Assets
------------

Assets can be used from the :doc:`/editors/asset_browser`.

The pose library extends this, and adds an Asset View to the 3D Viewport.
See :ref:`pose-library-from-viewport`.


.. _bpy.ops.asset.clear:
.. _assets-clear-set-fake-user:

Removing Assets
---------------

Asset metadata can be erased by the *Clear Asset* operator.
This operator is available in data-block selectors, the Asset Browser,
and for objects in the 3D Viewport menu.

.. figure:: /images/asset_browser-clear-asset.png

   *Clear Asset* in the Asset Browser.

Clear Asset
   Removes the asset metadata (catalog, description, author, tags), effectively turning an asset into
   a regular data-block. As such, the same removal rules apply as with other data-blocks. For example,
   if a mesh object is still placed in the scene, *Clear Asset* will not remove it from the scene.
   See :ref:`data-system-datablock-life-time`. The preview will be kept inside the data-block
   and not be removed.

Clear Asset (Set Fake User)
   Performs the same operation as *Clear Asset*, and then marks the data-block
   as :ref:`protected <data-system-datablock-fake-user>`.
   This makes it possible to no longer have the data-block marked as asset,
   and still be sure it is not lost when saving the blend-file.


.. _assets-bundled:

Bundled Assets
==============

Blender includes many assets out of the box, these are contained in the "Essentials" library.

Included in this library are:

- :doc:`Hair node groups </modeling/geometry_nodes/hair/index>`
- :doc:`/modeling/geometry_nodes/normals/smooth_by_angle`


.. _asset-libraries-design-limitations:

Design Limitations
==================

Blender is **not allowed to write to other blend-files** than the one you have currently open.
This means that to edit an asset, you have to open its blend-file.
Fortunately this is only a single click away, both in the Source List region of the Asset Browser
and in the asset context menu.

This also means that **Blender does not copy assets into the asset library** for you.
You are responsible for placing the blend-file with the asset in an asset library directory,
and marking the asset as such. See :ref:`asset-pushing` for more on this topic.


.. _asset-libraries-future-development:

Future Development
==================

This section describes interesting avenues for further development.
Even though it is not an exhaustive list, it might help to better understand
the current functionality of Blender's Asset Browser.


Non-Data-Block Assets
---------------------

Non-Blender assets, such as image or audio files, will likely be supported in a future version.
For such files, asset metadata is then stored in XMP sidecar files, similar to what other software is also doing.
Importers (USD, glTF, FBX, ...) could add support for their file types as assets this way too.
Furthermore, it should become possible to enrich an asset with a Python script,
which can then provide code to be run when the asset is used.


Cross Blend-File Editing
------------------------

As described above, Blender itself is not allowed to write to other blend-files
than the currently open one. This rule helps to limit complexities; for example,
it is hard to reliably implement an undo system when manipulating other files.
The rule does get in the way of mass-updating assets when they are stored in various blend-files.

Since there is already tooling that can manipulate blend-files outside of Blender itself
(see `Blender Asset Tracer <https://projects.blender.org/blender/blender-asset-tracer>`__),
it's possible to also create an external tool for doing such edits across blend-files.
Such a tool might even be implemented via Blender's application templates system,
or as an add-on; the rule above applies to Blender itself, not to its add-ons.


.. _asset-pushing:

Asset Pushing
-------------

Asset **pushing** is a way of getting assets into the asset library, where you are working on a file
and want to copy the asset from that file into the library. This is a concept that appears deceptively simple.
In certain cases it is actually simple, but often enough it gets quite complex. For example,
when you want to push an object into an external asset library, should that also copy the materials?
What about the texture images referenced by those materials?
What about objects referenced by custom properties, constraints, or modifiers?
And in which files would they have to go?
Do they all go into one big ``assets.blend``, individual blend-files,
or into a directory per asset type? Blender should not be making such decisions for you.

For specific cases, these things are all solvable. For this reason the pose library has been created as
an add-on which is enabled by default. Studios with specific needs can disable the add-on
and implement their own functionality; the building blocks are all in Blender's core,
and thus do not need to be copied for this. Furthermore, add-ons can write to other blend-files,
so they could make the decisions for users.

Asset pushing is desirable. Because of the questions above, it is unknown how to
implement this well, in a way that still allows artists control over their assets.


## Compatibility


*************
Compatibility
*************

Blender can open blend-files saved with both older versions of the software (backward compatibility),
and newer ones (forward compatibility). This comes with some limitations though.

.. tip::

   When having issues with opening much older (or newer) blend-files, it can help to use a few
   intermediary Blender releases to perform conversions by smaller steps.

.. note::

   Here is a `more exhaustive documentation <https://developer.blender.org/docs/handbook/guidelines/compatibility_handling_for_blend_files/>`__
   about compatibility handling, in the developer's documentation.


Backward Compatibility
======================

Opening older files and converting them for the current version of Blender is usually straight-forward.
It is expected to give very good and usable results.

There can be major feature changes, for which the backward compatibility will only be ensured for
a limited amount of time. For example the changes to the animation system that happened during the
Blender 2.5x project. This will never be less than a full major release cycle (i.e. two years at least).


Forward Compatibility
=====================

Loss of Data
------------

Forward compatibility is inherently harder to ensure, and loss of feature should always be expected
when opening a blend-file saved with a more recent version of Blender.

A warning is shown in the UI when editing a more recent blend-file.
Trying to overwrite it (with a simple 'Save' operation) will also show a confirmation popup,
as this could make that loss of data permanent.


Complete Incompatibility
------------------------

When Blender switches to a new major version release (e.g. from 3.x to 4.0), there can also be major
changes that will make the blend-file fully incompatible with older versions of Blender.

In such cases, older Blender will fail opening (or appending/linking from) the newer blend-file, with a
message stating which minimal version is needed to open it.

In such cases, the last LTS release of the previous release cycle will be kept compatible with the newer
file format version, and will be usable as converter between both versions.

For example, Blender 3.6LTS can open files from Blender 4.x, and will perform the necessary conversion
such that when re-saved from 3.6, the files become compatible with all 3.x Blender versions.


## Index


################
  Blender File
################

.. toctree::
   :maxdepth: 2

   open_save.rst
   compatibility.rst
   packed_data.rst
   previews.rst
   rename.rst


## Open Save


****************
Opening & Saving
****************

Opening and saving blend-files is usually done using the :doc:`File Browser </editors/file_browser>`.

.. tip::

   Blend-files can also be opened by dragging and dropping blend-files into the Blender window.
   This method also allows to :doc:`link/append </files/linked_libraries/index>` the file.

.. note:: Unsaved Changes

   By default, when exiting Blender or loading a new blend-file, if you have unsaved changes,
   a pop-up will ask you to either confirm discarding those changes, or save them.

   This behavior can be disabled with the *Save Prompt* option in the :ref:`prefs-save-load` section
   of the *Preferences*.


.. _bpy.ops.wm.open_mainfile:

Opening Files
=============

.. reference::

   :Menu:      :menuselection:`File --> Open...`
   :Shortcut:  :kbd:`Ctrl-O`

The upper text field displays the current directory path,
and the lower text field contains the selected filename.

.. figure:: /images/files_blend_open-save_file-browser-open.png

   The File Browser in open configuration.


Options
-------

.. _file-load-ui:

Load UI
   When enabled, the screen layout saved inside each blend-file is used,
   replacing the current layout and :doc:`Workspaces </interface/window_system/workspaces>`.
   Otherwise the file screen layout is ignored.

   .. tip::

      If you want to work on a blend-file using your own defaults, start a fresh Blender,
      open the File Browser and turn off the *Load UI* button, and open the desired file.

Trusted Source
   When enabled, Python scripts and drivers that may be included in the file will be run automatically.
   Enable this only if you created the file yourself,
   or you trust that the person who gave it to you did not include any malicious code with it.
   See :doc:`Python Security </advanced/scripting/security>` to configure default trust options.


.. _other-file-open-options:

Open Recent
===========

.. reference::

   :Menu:      :menuselection:`File --> Open Recent`
   :Shortcut:  :kbd:`Shift-Ctrl-O`

Displays a list of recently opened blend-files.
Hovering over items will show a preview, and information about the blend-file.
Select any of the file names in the list to open that blend-file.

Clear Recent Files List
   Removes all items from the list.


Recover
=======

.. _bpy.ops.wm.recover_last_session:

Last Session
------------

.. reference::

   :Menu:      :menuselection:`File --> Recover --> Last Session`

This will load the ``quit.blend`` file Blender automatically saved just before exiting.
This option enables you to recover your last work :term:`session` if, for example, you closed
Blender by accident.


.. _bpy.ops.wm.recover_auto_save:

Auto Save
---------

.. reference::

   :Menu:      :menuselection:`File --> Recover --> Auto Save`

This will allow you to open an automatically saved file to recover it.

.. seealso::

   :ref:`Auto Save <troubleshooting-file_recovery-auto_save>`


.. _bpy.ops.wm.save_mainfile:

Saving Files
============

.. reference::

   :Menu:      :menuselection:`File --> Save`
   :Shortcut:  :kbd:`Ctrl-S`

Save current blend-file over itself (if it was not saved yet, this will automatically switch to *Save As...*).

.. figure:: /images/files_blend_open-save_file-browser-save.png

   The File Browser in save configuration.


Save Incremental
================

.. reference::

   :Menu:      :menuselection:`File --> Save Incremental`
   :Shortcut:  :kbd:`Ctrl-Alt-S`

Save the current Blender file with a numerically
incremented name that does not overwrite any existing files.


.. _bpy.ops.wm.save_as_mainfile:

Save As
=======

.. reference::

   :Menu:      :menuselection:`File --> Save As...`
   :Shortcut:  :kbd:`Shift-Ctrl-S`

Choose a file path to save the blend-file to.

.. warning::

   If a file with the same given name already exists,
   the text field will turn red as a warning that the file will be overwritten.

.. tip::

   Use the *plus* or *minus* buttons to the right of the file name,
   or :kbd:`NumpadPlus`, :kbd:`NumpadMinus` to increase/decrease a number at the end of the file name
   (e.g. changing ``file_01.blend`` to ``file_02.blend``).


Options
-------

.. _files-blend-compress:

Compress
   Reduces the file size of the resulting blend-file but takes longer to save and load.
   This option is useful for distributing files online and saving drive space for large projects.
   But it can cause slowdowns when quitting Blender,
   or under normal operation when auto-saving backup files.
   See :ref:`files-linked_libraries-known_limitations-compression` for more information.

   .. hint::

      The used compression algorithm is Zstandard.
      It is not unique to Blender so files can be compressed/decompressed with external tools.

   .. versionchanged:: 3.0

      Prior to this version, the compression algorithm used was Gzip.
      This means to open newer blend-files in versions prior to 3.0,
      blend-files must first be saved without compression in a newer version of Blender
      or decompressed using an external Gzip tool.

Remap Relative
   This option remaps :ref:`files-blend-relative_paths`
   (such as linked libraries and images) when saving a file in a new location.
Save Copy
   Saves a copy of the actual working state but does not make the saved file active.


Save Copy
=========

.. reference::

   :Menu:      :menuselection:`File --> Save Copy...`

Choose a file path to save the blend-file to, but return to editing the original file upon completion.
This can be used to save backups of the current working state without modifying the original file.

For options see :ref:`bpy.ops.wm.save_as_mainfile`.


.. _files-blend-relative_paths:

Relative Paths
==============

Many blend-files reference external images or other linked blend-files.
A path tells Blender where to look for these files.
If the external files are moved, the blend-file that references them will not look right.

When you specify one of these external files, the default option is to make the path relative.
Blender stores a partial path evaluated relative to the directory location of the referencing blend-file.
This choice helps when you need to reorganize folders or move your files.

With a relative path, you can move the blend-file to a new location provided
the externally linked files are moved along with it.
For example, you could send someone a folder that contains a blend-file
and a subfolder of external images that it references.

When relative paths are supported, the File Browser provides a *Relative Path* checkbox,
when entering the path into a text field, use a double slash prefix (``//``) to make it so.

Relative paths are the default but this can be changed
in the :doc:`File </editors/preferences/file_paths>` tab of the *Preferences*.

.. note::

   You cannot use relative paths into a new *untitled* blend-file.
   Save it before linking to external files.

.. hint::

   If it is necessary to relocate a blend-file relative to its linked resources,
   use Blender's File :ref:`Save As <bpy.ops.wm.save_mainfile>`
   function which has an option to *Remap Relative* file links.


## Packed Data

.. _pack-unpack-data:

***********
Packed Data
***********

Blender has the ability to encapsulate (incorporate)
various kinds of data within the blend-file that is normally saved outside of the blend-file.
For example, an image texture that is an external image file can be put "inside" the blend-file.
This allows sharing a full project as a single file,
instead of e.g. an archive containing the blend-file and all its dependencies.

You know that a data is packed when you see a little "gift box" icon displayed next to its path.

.. warning:: Not all external files can be packed

   Some typically heavy external files, like videos from the :doc:`Sequence Editor </video_editing/introduction>`
   or :doc:`Movie Clips </editors/clip/introduction>`, cannot be packed in a blend-file.


Pack Data
=========

.. _bpy.ops.file.pack_all:

Pack Resources
--------------

.. reference::

   :Panel:     :menuselection:`File --> External Data --> Pack Resources`

Mark all eligible external resource files used by the blend-file as packed.
Actual packing will happen on the next save of the blend-file.


.. _bpy.ops.file.autopack_toggle:

Automatically Pack Resources
----------------------------

.. reference::

   :Panel:     :menuselection:`File --> External Data --> Automatically Pack Resources`

When enabled, this option will ensure that all eligible external resource files, existing or added later,
are systematically marked as packed.
As with *Pack Resources*, the blend-file must be saved to the drive for this to have an effect.

Disabling that option won't unpack anything, but future external files
won't be automatically marked as packed anymore.


Selective Packing
-----------------

A single file can be packed by clicking on the little "gift box" icon to the left of its file-path UI widget.


Unpack Data
===========

.. _bpy.ops.file.unpack_all:

Unpack Resources
----------------

.. reference::

   :Panel:     :menuselection:`File --> External Data --> Unpack Resources`

Unpack all external resource files stored into a blend-file.


Options
^^^^^^^

Use files in current directory (create when necessary)
   Unpacks all files in the same directory ``//`` as the blend-file,
   grouping them in proper folders (like ''textures'' for instance).
   However, if the final file exists already, it will use that file, instead of unpacking it.
Write files to current directory (overwrite existing files)
   As with previous option, but if the final file exists already, it will overwrite it.
Use files in original location (create when necessary)
   Unpacks all files in their original location.
   However, if the final file exists already, it will use that file, instead of unpacking it.
Write files to original location (overwrite existing files)
   As with previous option, but if the final file exists already, it will overwrite it.
Disable AutoPack, keep all packed files
   Only deactivates the *Automatically Pack Resources* option.


Selective Unpacking
-------------------

A single file can be unpacked by clicking on the little "gift box" icon to the left of its file-path UI widget.


Options
^^^^^^^

Remove Pack
   Just mark the file as unpacked, without actually writing it or reloading it from the drive.
Create <local file path>
   Unpack the file at the proposed path, which is local to the current blend-file.
Use <original file path> (differs)|(identical)
   If the original file path still exists, mark it as unpacked.
   Note that it won't be automatically reloaded from the drive.
   *(differs)* or *(identical)* show difference status between the packed version
   and the one on-drive.
Overwrite <original file path>
   If the original file path still exists but differs from the packed version,
   mark it as unpacked and overwrite the on-drive file with the packed version.
Create <original file path>
   If the original file path does not exist, mark it as unpacked and write it to drive.


.. _bpy.ops.file.pack_libraries:

Pack Linked Libraries
=====================

.. reference::

   :Panel:     :menuselection:`File --> External Data --> Pack Linked Libraries`

Mark all linked library files in the current blend-file as packed.
Actual packing will happen on the next save of the blend-file.


.. _bpy.ops.file.unpack_libraries:

Unpack Linked Libraries
=======================

.. reference::

   :Panel:     :menuselection:`File --> External Data --> Unpack Linked Libraries`

Unpack all used linked library files from this blend-file.


## Previews


********************
Blend-Files Previews
********************

A blend-file can store previews, both for itself, and for some of its :doc:`data-blocks </files/data_blocks>`.
You can disable writing any previews when saving a blend-file using the *Save Preview Images* setting
from the :ref:`prefs-save-load` section of the Preferences.


Blend-File Preview
==================

Blender saves by default a small preview of current scene in the blend-file.
This will show in the *Thumbnail* view of the :doc:`File Browser </editors/file_browser>`.

During its installation, Blender also adds a small tool to your OS,
that will allow your system file browser to show those previews as file thumbnails as well.


Data-Blocks Previews
====================

Blender will automatically generate previews for some type of data, mainly the ones related to shading
(like images, textures, materials, lights and world shaders).

It can also store previews for scenes, collections and objects, but those need to be generated manually.

These previews can then be used by the *Thumbnail* view of the File Browser, when linking or appending data-blocks.


.. _bpy.ops.wm.previews_ensure:

Refresh Data-Block Previews
---------------------------

.. reference::

   :Menu:      :menuselection:`File --> Data Previews --> Refresh Data-blocks Previews`

Refresh all data-block previews that can be automatically generated by Blender (shading-related ones),
in the current blend-file. You still need to save the file if you want to write them to the drive.


.. _bpy.ops.wm.previews_batch_generate:

Batch Generate Previews
-----------------------

.. reference::

   :Menu:      :menuselection:`File --> Data Previews --> Batch Generate Previews`

Generate some data-block types' previews (you can choose which in its options),
in one or more blend-files on your drive. You should not use this operator on the file currently opened in Blender.

This is currently the only way to generate and store in blend-files previews for scenes, collections and objects.
Note that since this involves a lot of rendering, even of small sizes, the process may take some time to complete.

Scenes
   Generate previews of scenes and their collections.
Collections
   Generate previews of collections of objects.
Objects
   Generate previews of objects.
Materials & Textures
   Generates previews for materials, textures, images, and other internal data.
Trusted Blend Files
   When enabled, Python scripts and drivers that may be included in the file will be run automatically.
   Enable this only if you created the file yourself,
   or you trust that the person who gave it to you did not include any malicious code with it.
   See :doc:`Python Security </advanced/scripting/security>` to configure default trust options.
Save Backups
   Keep a :ref:`backup version <bpy.types.PreferencesFilePaths.save_version>` (``blend1-file``)
   of the files when saving with generated previews.


.. _bpy.ops.wm.previews_clear:

Clear Data-Block Previews
-------------------------

.. reference::

   :Menu:      :menuselection:`File --> Data Previews --> Clear Data-blocks Previews`

Clear all, a generic type of, or a specific data-block type of previews in the current blend-file.
You still need to save the file if you want to clear them from the drive.


.. _bpy.ops.wm.previews_batch_clear:

Batch Clear Previews
--------------------

.. reference::

   :Menu:      :menuselection:`File --> Data Previews --> Batch Clear Previews`

Clear some data-block types' previews (you can choose which in its options),
in one or more blend-files on your drive. You should not use this operator on the file currently opened in Blender.

Scenes
   Clear previews of scenes and their collections.
Collections
   Clear previews of collections of objects.
Objects
   Clear previews of objects.
Materials & Textures
   Clear previews for materials, textures, images, and other internal data.
Trusted Blend Files
   When enabled, Python scripts and drivers that may be included in the file will be run automatically.
   Enable this only if you created the file yourself,
   or you trust that the person who gave it to you did not include any malicious code with it.
   See :doc:`Python Security </advanced/scripting/security>` to configure default trust options.
Save Backups
   Keep a :ref:`backup version <bpy.types.PreferencesFilePaths.save_version>` (``blend1-file``)
   of the files when saving with cleared previews.


## Rename


******
Rename
******

.. _tools_rename-active:

Rename Active Item
==================

.. reference::

   :Menu:      :menuselection:`Edit --> Rename Active Item`
   :Shortcut:  :kbd:`F2`

The *Rename Active Item* operator renames the active
:doc:`Bone </animation/armatures/bones/index>`,
:doc:`Node </interface/controls/nodes/index>`,
:doc:`Object </scene_layout/object/index>` and
:doc:`Sequence Strip </video_editing/edit/montage/strips/index>`.

When the operator is executed, a pop-up dialog appears.
The text field shows the name of the current item and can be overwritten to rename the item.
:kbd:`Return` confirms the name while :kbd:`Esc` cancels the operator.


.. _bpy.ops.wm.batch_rename:

Batch Rename
============

.. reference::

   :Menu:      :menuselection:`Edit --> Batch Rename`
   :Shortcut:  :kbd:`Ctrl-F2`

The *Batch Rename* operator can rename many data-block names at once.
This uses a pop-up dialog with operations and their options to change the name.
These actions are applied in order, from first to last.

Data Source
   Where to look for the data-blocks that are intended to be renamed.

   :Selected: Operates on the currently selected objects.
   :All: Operates on all data in the blend file.

Data Type
   The :ref:`data-block type <data-system-datablock-types>` to perform the batch rename operations on.


Operations
----------

The *Batch Rename* has several sub Operations to change the data names.
The default operation is *Find/Replace* however, other operations can be added
to change the data names further.
Below all the operations gives a message in the status bar on how many data-blocks were renamed.


Find/Replace
^^^^^^^^^^^^

*Find/Replace* searches for a particular text in the names and optionally replaces it with a new text.
`Regular Expressions <https://en.wikipedia.org/wiki/Regular_expression>`__
can be used as a powerful way to tailor the *Find*/*Replace* texts
and can be enabled using the icon to the right of the text fields.

Find
   The text to search for in names.
Replace
   The text to replace for in matching names found from the *Find* text.
Case Sensitive
   Search results must exactly match the case of the *Find* text.


Set Name
^^^^^^^^

*Set Name* works the most similar to `Rename Active Item`_
by renaming the current data-block without having to do a find and replace operation.

Method
   :New:
      Disregards the current name replacing it with the "new" name.
   :Prefix:
      Adds text to the beginning of the current name.
      This is useful for tools that look for special text in the prefix of a data-block name.
   :Suffix:
      Adds text to the end of the current name.
      This is useful for tools that look for special text in the suffix of a data-block name.
Name
   Defines the new name or the text to add as a prefix/suffix.


Strip Characters
^^^^^^^^^^^^^^^^

*Strip Characters* cleans up names by removing certain
character types from either the beginning or the end of the name.

Characters
   :Spaces:
      Strips any space characters from the name, e.g. "Living Room   " becomes "Living Room".
   :Digits:
      Strips any numerical characters from the name, e.g. ``cube.001`` becomes ``cube.``.
   :Punctuation:
      Strips any punctuation characters (``,.?!:;`` etc.) from the name, e.g. ``cube?`` becomes ``cube``.

   .. tip::

      Multiple character types can be removed at once by :kbd:`Shift-LMB` on the types.

Strip From
   :Start: Strips any leading characters in the name.
   :End: Strips any trailing characters in the name.


Change Case
^^^^^^^^^^^

*Change Case* modifies the case of names to be one of the following:

Convert To
   Upper Case
      Changes all text to be in upper case, e.g. ``cube.001`` becomes ``CUBE.001``.
   Lower Case
      Changes all text to be in lower case, e.g. ``CUBE.001`` becomes ``cube.001``.
   Title Caps
      Changes all text to be in title case, e.g. ``living room`` becomes ``Living Room``.


## Alembic


*******
Alembic
*******

From the `Alembic home page <https://www.alembic.io/>`__:

   Alembic is an open computer graphics interchange framework. Alembic distills complex, animated
   scenes into a non-procedural, application-independent set of baked geometric results.
   This 'distillation' of scenes into baked geometry is exactly analogous to the distillation of
   lighting and rendering scenes into rendered image data.

   Alembic is focused on efficiently storing the computed results of complex procedural geometric constructions.
   It is very specifically **not** concerned with storing the complex dependency graph
   of procedural tools used to create the computed results.
   For example, Alembic will efficiently store the animated vertex positions and
   animated transforms that result from an arbitrarily complex animation and simulation process
   which could involve enveloping, corrective shapes, volume-preserving simulations,
   cloth and flesh simulations, and so on.
   Alembic will not attempt to store a representation of the network of computations (rigs, basically)
   which are required to produce the final, animated vertex positions and animated transforms.

In brief, Alembic can be used to write an animated mesh to a drive, and read it back quickly and efficiently.
This means that a mesh can be animated with a very CPU-intensive rig and then 'baked' to an Alembic file.
Finally it can be load into the shot file for shading and lighting with only moderate CPU usage.

Due to the Open Source nature of the Alembic standard as well as
the C++ library implementing that standard, **Blender can be used in a hybrid pipeline**.
For example, other software, such as Houdini or Maya, can export files to Alembic,
which can then be loaded, shaded, and rendered in Blender.
It is also possible to animate characters (or other models) in Blender, export to Alembic, and
load those files into other software for further processing.


.. _bpy.ops.wm.alembic_import:

Importing Alembic Files
=======================

When importing an Alembic file, :doc:`Mesh Sequence Cache modifiers </modeling/modifiers/modify/mesh_sequence_cache>`
are automatically added to time-varying meshes. For time-varying object transforms
(so animation of rotation, location, or scale)
the :ref:`Transform Cache Constraint <bpy.types.TransformCacheConstraint>` is used.


General
-------

Scale
   Value by which to enlarge or shrink the objects with respect to the world's origin


Options
-------

Relative Path
   Select the file relative to the blend-file.

Set Frame Range
   If checked, update scene's start and end frame to match those of the Alembic archive.

Is Sequence
   Set to true if the cache is split into separate files.

Validate Meshes
   Check the imported mesh for corrupt data and fix it if necessary.
   When disabled, erroneous data may cause crashes displaying or editing the meshes.
   This option will make the importing slower but is recommended, as data errors are not always obvious.

Always Add Cache Reader
   Add cache modifiers and constraints to imported objects even if they are
   not animated so that they can be updated when reloading the Alembic archive.


.. _bpy.ops.wm.alembic_export:

Exporting to Alembic Files
==========================

This section describes the effect of the different export options.


General
-------

.. figure:: /images/files_import-export_alembic_export-panel-general-options.png
   :align: right

   General options.

Scale
   This sets the global scale of the Alembic file. Keep it at the default value of 1.0 to use
   Blender's units.

Include
   Selected Objects
      When enabled, exports only the selected objects. When disabled, all objects are exported.
   Visible Objects
      Limits the export to scene collections that are currently visible.


Scene
-----

.. figure:: /images/files_import-export_alembic_export-panel-scene-options.png
   :align: right

   Scene options.

Frame Start, End
   Sets the frame range to export to Alembic. This defaults to the current scene frame range.

Sub-frame Sampling
   These options control the sub-frame sampling of animations.

   Samples Transform
      Transform Samples sets the number of times per frame at which animated transformations
      are sampled and written to Alembic.
   Geometry
      Geometry Samples sets the same, but then for animated geometry.
   Shutter Open, Close
      Shutter Open/Close define the interval [open, close] over which those samples are taken.
      The valid range is -1 to 1, where -1 indicates the previous frame,
      0 indicates the current frame, and 1 indicates the next frame.

      For example, if information for detailed mesh motion blur is desired, some subframes around
      the current frame can be written to Alembic by using a sample count of 5,
      Shutter Open at -0.25 and Shutter Close at 0.25.
      This mimics a "180 degree" shutter, opening 90 degrees before the frame
      and closing 90 degrees after the frame.

Use Instancing
   Exports data of :doc:`duplicated </scene_layout/object/editing/duplicate_linked>`
   or :doc:`instanced </scene_layout/object/properties/instancing/index>` objects as Alembic instances;
   speeds up the export and can be disabled for compatibility with other software.

Custom Properties
   When enabled (which it is by default), custom properties are exported to Alembic as well.
   The following custom property types are supported:

   - Numbers (``int``, ``float``) and strings. These are exported as arrays of
     a single element, so ``47`` will be exported as ``[47]`` to Alembic,
     and ``"Agent"`` to ``["Agent"]``. This matches the behavior of
     many other :abbr:`DCCs (Digital Content Creator)`.

   - Lists of numbers and strings. These are exported as-is, so ``[327, 47]`` is exported as ``[327, 47]``.

   - Matrices and nested arrays of numbers. These are flattened into one long list,
     so a 3×2 matrix of numbers will become a list of 6 numbers. Similarly,
     nested lists ``[[1, 2, 3], [4, 5], [6]]`` will be exported as ``[1, 2, 3, 4, 5, 6]``.

   - Numbers can be animated as well.

Flatten Hierarchy
   When disabled, parent/child relations between objects are exported too. Any parent object that
   is not exported itself, but with children that *are* exported, is replaced by an empty.
   When enabled, parent/child relations are not exported, and transformations are all written in world coordinates.

Settings
   Determines visibility of objects, modifier settings,
   and other areas where there are different settings for viewport and rendering.

   :Render: Use Render settings for object visibility, modifier settings, etc.
   :Viewport: Use Viewport settings for object visibility, modifier settings, etc.


Geometry
--------

.. figure:: /images/files_import-export_alembic_export-panel-geometry-options.png
   :align: right

   Geometry options.

UV Coordinates
   When enabled, UV maps are exported. Although the Alembic standard only supports
   a single UV map, Blender exports all UV maps in a way that should be readable by other software.

Merge UVs
   When enabled, UVs sharing the same vertex and location will be merged into a single UV.
   The exported file can be slightly smaller.

Normals
   When enabled, an object's :term:`Normals <Normal>` are exported.
   See `Custom Split Normals of Meshes`_ below for more information.

Color Attributes
   When enabled, exports Color Attributes.

Face Sets
   Exports the material names per face. The material data is not exported but only material names.

Subdivisions
   Apply
      Applies any :doc:`Subdivision Surface modifiers </modeling/modifiers/generate/subdivision_surface>`
      before writing to Alembic.
   Use Schema
      Writes polygonal meshes using the "SubD" Alembic schema, rather than the "PolyMesh" schema.
      This sets an import option for the program, with which the file is opened,
      to apply its form of a non-destructive subdivision.

Triangulate
   Triangulates the mesh before writing to Alembic. For more detail on the specific option see
   the :doc:`Triangulate modifier </modeling/modifiers/generate/triangulate>`.


Particle Systems
----------------

.. figure:: /images/files_import-export_alembic_export-panel-particle-systems.png
   :align: right

   Particle Systems options.

Alembic has no support for Particle Systems, in the same way that it does not support armatures.

Export Hair
   Hair is exported as animated zero-width curves.

Export Particles
   Particles are exported as animated points.


Custom Split Normals of Meshes
==============================

Blender supports the import and export of :ref:`custom normals <modeling_meshes_normals_custom>` to
Alembic files. As a basic rule of thumb, a completely smooth mesh will be exported without normals
and thus produce the smallest Alembic file. This is reflected in the importer; an Alembic mesh
without normals is loaded as a smooth mesh.

On export, for every mesh:

- If it has *Custom Loop Normals* then the loop normals are exported.
- If one or more polygons are marked flat then loop normals are also exported.
- Otherwise, no normals are exported.

On import, when the Alembic mesh contains:

- Loop normals (``kFacevaryingScope``) are used as custom loop normals.
- Vertex normals (``kVertexScope`` or ``kVaryingScope``) are convert to loop normals, and handle as above.
- If there are no normals then the mesh is marked as smooth.
- Unsupported normal types (``kConstantScope``, ``kUniformScope``, ``kUnknownScope``) are handled as *no normals*.

When an imported mesh does not contain normals, the final look can be controlled using the
:ref:`Normal's Shading <modeling-meshes-structure-normals-shading>`.


Handling Time
=============

Unlike Blender and many other applications and file formats, Alembic files don't have any concept of frames.
Alembic works purely with time, and values that are sampled over time. For example,
there is no way to distinguish 30 FPS with 2 samples per frame, and 60 FPS with 1 sample per frame.
This has caused many developers to just
`hard-coded 24 FPS <https://projects.blender.org/blender/blender/issues/55288>`__
when reading Alembic files.

Blender uses the current scene frame rate to convert a frame number (in Blender) to a time
in seconds (in Alembic). As a result, you can import an Alembic file that was produced at 120 FPS into
a Blender scene that is 30 FPS and still not see any time stretching.


## Collada


*******
Collada
*******

.. warning::

  COLLADA I/O support is now considered as a legacy feature in Blender, and will be removed
  in a future release.
  Please see the
  `official announcement <https://devtalk.blender.org/t/moving-collada-i-o-to-legacy-status/34621>`__
  for more insight on this topic.

The COLLADA™ module has been implemented as a flexible tool for exporting and importing ``.dae`` files.
A design goal is to provide a set of parameters which should make it possible
to export/import Collada files from/to a variety of tools.
But please be aware that the Collada module is still a work in progress.
So it may be possible that your particular usage scenario is not yet supported.

.. important::

   Collada support in Blender is considered deprecated and may be removed in a future version.


Collada Exporter
================

.. figure:: /images/files_import-export_collada_export.png
   :align: right


.. rubric:: Operator Presets

There are two operator presets (see top of the Sidebar) for Second Life (SL) users:

- *Second Life Static* -- is good for exporting static meshes.
- *Second Life Rigged* -- is good for exporting the SL default character.

.. note::

   Special Notes for Second Life users:

   - Please use the Operator presets. All other export settings will not work for Second Life.
   - The character orientation needs to be such that the character looks towards positive X.
   - Scale and Rotation must be applied before the export!


Main
----

Selection Only
   When *Selection Only* is enabled, then only the selected objects will be exported.
   Otherwise the entire scene is exported with all visible and all invisible objects.

Include Children
   When this option is enabled then all children of the selected objects
   will also be exported regardless of their selection state.

   .. hint::

      You can select only an armature, then using this option,
      all rigged meshes attached to the armature will also be exported.

Include Armatures
   When this option is enabled, then all armatures related to the selected objects
   will also be exported regardless of their selection state.

   .. hint::

      You can select only the objects, then in the exporter enable
      this option to export the armature data also.

Include Shape Keys
   Includes the application of shape keys by exporting meshes
   with the current shape key configuration baked in.


Global Orientation
^^^^^^^^^^^^^^^^^^

Apply
   Rotate all root objects to match the global orientation settings otherwise set the global orientation per Collada
   asset.

Forward / Up Axis
   Since many applications use a different axis for pointing upwards, these are axis conversion for these settings,
   Forward and up axes -- By mapping these to different axes you can convert rotations
   between applications default up and forward axes.

   Blender uses Y forward, Z up (since the front view looks along the +Y direction).
   For example, it is common for applications to use Y as the up axis, in that case -Z forward, Y up is needed.


Texture Options
^^^^^^^^^^^^^^^

Copy
   When you export images either material based image textures,
   then the exporter creates absolute file references in the export file.

   But if the *Copy* option is enabled, the exporter will create copies of the images instead and
   place the copies besides the export file. In that case the file references are made relative.

Only Selected UV Map
   When your mesh contains multiple UV layers, then Blender exports all layers by default.
   This option allows you to only export the active (selected) UV layer.

Geometry
--------

Export Data Options
^^^^^^^^^^^^^^^^^^^

Triangulate
   The mesh can be triangulated on-the-fly. The triangulation is based on the same function
   which is used in the *Triangulate Faces* tool for triangulating the current selection of faces.
   For full control over the triangulation you can do this manually before exporting.
   However, this option allows to apply the triangulation only on the exported data;
   the mesh itself is not affected.

Apply Modifiers
   Export objects using the evaluated mesh, meaning the resulting mesh after all
   :doc:`Modifiers </modeling/modifiers/index>` have been calculated.

   Resolution
      Controls whether to apply the 3D Viewport resolution or the render resolution
      for modifiers that provide a preview mode and a render mode.

Transform
   Collada supports two types of transformation matrix specifications.
   Either as ``<Matrix>`` or as a set of transformation decompositions (for move, rotate and scale).
   Note that the exporter will not strictly follow this option setting,
   but will rather take it as a hint to use the option if ever possible.
   This is so because some of the exported data types have specific rules
   about how the transformation matrix has to be exported.
   This is ongoing development and a less ambiguous method may be provided in the future.


Armature
--------

Armature Options
^^^^^^^^^^^^^^^^

Deform Bones Only
   When this option is enabled, then the exporter strips all non-deforming bones from the exported armatures.
   This option is useful when your armatures contain control bones
   which are not actually part of the character skeleton.
   For example you can export the Avastar rig with this option enabled.
   The resulting exported rig is compatible with Second Life.
   But please note the restrictions further below.

Export to SL/OpenSim
   When this option is enabled, some issues with bone orientation are calculated differently
   and is designed to be used to export to Second Life or OpenSim.

   This is only relevant for rigged meshes, for static meshes it just does nothing at all.


Animation
---------

Extra
-----

Collada Options
^^^^^^^^^^^^^^^

Use Object Instances
   In Blender you can reuse the same mesh for multiple objects.
   This is named "object instantiation". When you enable this option,
   then Blender will propagate object instantiation to the Collada file.

Use Blender Profile
   Collada can be extended with tool specific data (profiles). Blender has its own (unofficial) profile
   that allows to export rig information into the Collada file. Later It can be used to reconstruct the rig
   when it should ever be necessary to import a dae file back into Blender.

Sort by Object Name
   The export order of data is bound to internal object order and it can not be influenced in a reliable way.
   This option ensures that the Geometry nodes and the Object nodes are both exported in alphabetical order.

Keep Bind Info
   When a rig is imported to Blender, the rig's bind pose will be used as Blender's rest pose.
   So all Matrix information of the original rest pose is lost.
   But in some cases you may want to preserve the original rig information.
   This option checks each bone for having two arrays:

   - ``rest_mat`` -- an array of 16 floats which represent the bone's original rest-pose matrix.
   - ``bind_mat`` -- an array of 16 floats which represent the bone's original bind-pose matrix.

   If the arrays are present, then those arrays will be used instead of the current rest pose/bind pose.
   Those two arrays are either created by a previous Collada import (see `Collada Importer`_ below),
   or they can be created manually, or by an add-on (script based).


Collada Importer
================

.. figure:: /images/files_import-export_collada_import.png
   :align: right

The Collada importer is mostly driven by the imported data.
There is one option for controlling the import units:


Import Data Options
-------------------

Custom Normals
   Use the mesh normals defined in the collada file, if they are defined,
   otherwise Blender will recompute them during the import process.
Import Units
   If not enabled the imported data will be rescaled according to the currently used unit system.
   If this option is enabled, then Blender will adjust itself to the unit system as provided by the Collada file.


Armature Options
----------------

Fix Leaf Bones
   Collada only records "joints" which is mostly similar to Blender's bone heads.
   But when you import a Collada file then the bone head/tail are not defined.
   This does not matter for connected bones where the bone parent only has one child.
   In that case the parent bone's end location is adjusted to the child's joint position.
   But especially for unconnected bones and for bones with more than one child a problem arises.

   When the *Fix Leaf Bones* option is enabled then Blender tries to guess
   where the bone head/tail of unconnected bones would best be placed.
   If the option is disabled, then the bone head/tail are placed at an offset along the Y axis.
   That is why bones often point towards the Y axis.

Find Bone Chains
   When a bone has multiple children, then it is not defined which (if any)
   of the children should be connected to the bone. When the *Find Bone Chains* option is enabled,
   then Blender determines the longest bone chain (of children) for each bone.
   All bones along this chain will then be auto connected.

   If the option is disabled, then children will only be connected to parents,
   if the parent has only one child. But see the *Auto Connect* option below.

Auto Connect
   When this option is enabled, then children will automatically
   be connected to their parents, if the parent has only one child.

----

Keep Bind Info
   When this option is enabled, then the importer creates two custom properties for each bone:

   - ``rest_mat`` -- an array of 16 floats which represent the bone's original rest-pose matrix.
   - ``bind_mat`` -- an array of 16 floats which represent the bone's original bind-pose matrix.

   Those two arrays can later be used when you want to export the rig
   again and be sure the original rest pose/bind pose combination must be used.


Technical Details
=================

Mesh
----

Import
^^^^^^

Supported geometry types are:

- Tris (not tested)
- Polylist
- Polygons
- N-gons
- Tri-fans (not tested)
- Lines


Export
^^^^^^

Mesh data is exported as ``<polylist>``, ``<lines>`` and ``<vertices>``.


Light
-----

Import
^^^^^^

Blender does a best effort on importing lights from a dae-file.
If a Blender profile is detected for lights, all values from these will be used instead.
This ensures full re-import from a Blender exported dae-file. ``<extra>`` support has been added in Blender 2.57.


Export
^^^^^^

A Blender profile for lights has been added through the ``<extra>`` tag.
The entire Light struct from Blender will be exported through this profile,
with the exception of light curve falloff.


Animation
---------

Export & Import
^^^^^^^^^^^^^^^

- Support for object (mesh, camera, light) transform animations. Only Euler rotations,
  which is the default option for Objects, can be exported.
  For armature bone animations, Euler and quaternion rotation types are supported.
- Import and export of animations for the following parameters are supported:

  - Light
  - Camera
  - Material effects
- Non-skin controlling armature bone animation.
- Animations of armatures with skin deforming bones.
- Animations of armatures in Object Mode.
- Fully rigified armature animations (referring to the Rigify add-on). For export of rigified armature animations:

  - Run the :ref:`bpy.ops.nla.bake` operator.
  - If you have only the deform bones selected check *Only Selected*.
    This will give smaller dae. Otherwise uncheck *Only Selected*.
  - Check *Clear Constraints*.
  - Bake Action.
  - Select the mesh and the deform bones. Then export to Collada while checking only selected option.
    (Selecting only the Mesh and bones is not strictly necessary.
    Selecting and export only selected will give smaller dae.)
  - `Demonstration video <https://www.youtube.com/watch?v=GTlmmd13J1w>`__

For bone nodes which are leaf nodes in the armature tree,
or if a bone has more than one child, a Blender profile for tip with an ``<extra>`` tag,
is added for those joint nodes. To correctly derive the bone-to-tail location on re-import.

.. note:: Important Things to Remember

   - Object and data-block names are constrained to 21 characters (bytes).
   - UV layer names are constrained to 32 characters (bytes).
   - Only armature animation on mesh, single skin controller.
   - No support for modifiers yet.

   When importing a dae-file that has ``<instance_node>`` on exporting
   this information is essentially lost and these nodes will be ``<node>``\ s.


## Grease Pencil Pdf


***********************************************
Portable Document Format (PDF) as Grease Pencil
***********************************************

This format is use for interchanging PDFs between applications,
it support the export of Grease Pencil animation creating one page in the PDF document for each keyframe selected.

.. warning:: The exporter only works in Object Mode.


Export Options
==============

The following options are available when exporting to PDF:

Object
   Determine which objects will be included in the export.

   :Active: Export only the active Grease Pencil object.
   :Selected: Export all selected Grease Pencil objects.
   :Visible: Export all visible Grease Pencil object in the scene.

Frame
   Determine which frames will be included in the export.

   :Active: Export only the active keyframe.
   :Selected: Export all selected keyframes as different PDF pages.
   :Scene: Export all frames as different PDF pages.

.. note:: To enable multi-keyframe selection you must enable Multiframe Edition.
   See :doc:`Multiframe Edition </grease_pencil/multiframe>` for more information.

Sampling
   Precision for the stroke sampling. Low values mean a more accurate result.

Fill
   When enabled, Export the Grease Pencil strokes fill.

Normalize
   When enabled, Export strokes with constant thickness.

.. note:: The export of the Grease Pencil strokes is doing always from camera view.


## Grease Pencil Svg


***********************************************
Scalable Vector Graphics (SVG) as Grease Pencil
***********************************************

This format is use for interchanging vector based illustrations between applications
and is supported by vector graphics editors such as Inkscape, and modern browsers among others.

.. warning:: The exporter only works in Object Mode.


Import
======

Options
-------

Resolution
   Resolution for generated strokes.

Scale
   Generated strokes scale.


Export
======

Options
-------

Object
   Determine which objects include in the export.

   :Active: Export only the active Grease Pencil object.
   :Selected: Export all selected Grease Pencil objects.
   :Visible: Export all visible Grease Pencil object in the scene.

Sampling
   Precision for the stroke sampling. Low values mean a more accurate result.

Fill
   When enabled, Export the Grease Pencil strokes fill.

Normalize
   When enabled, Export strokes with constant thickness.

Clip Camera
   When enabled, and camera view is active export only the strokes clipped from camera view.


## Index

.. _bpy.ops.export:
.. _bpy.ops.import:

***************************
Importing & Exporting Files
***************************

.. reference::

   :Menu:      :menuselection:`Topbar --> File --> Import/Export`

Sometimes you may want to utilize files that either came from other 2D or 3D software,
or you may want to use the things you have made in Blender and edit them in other software.
Luckily, Blender offers a wide range of file formats (e.g. ABC, USD, OBJ, FBX, PLY, STL, etc.)
that can be used to import and export.

Popular formats are enabled by default, other formats are also supported and distributed with Blender,
these can be enabled in the Preferences through the use of :doc:`Add-ons </editors/preferences/extensions>`.

.. toctree::
   :maxdepth: 1

   alembic.rst
   collada.rst
   usd.rst
   obj.rst
   ply.rst
   stl.rst
   grease_pencil_svg.rst
   grease_pencil_pdf.rst

.. seealso::

   More information on the add-ons to import/export these file types
   can be found in the :ref:`add-ons section <addons-io>`.


## Obj


*************
Wavefront OBJ
*************

.. reference::

   :Menu:      :menuselection:`File --> Import/Export --> Wavefront (.obj)`

OBJ format is a popular plain text format, however, it has only basic geometry and material support.

.. note::

   There is no support for armatures, lights, cameras, empty objects, parenting, or transformations.
   See `Compatibility`_ for more information.


.. _bpy.ops.wm.obj_import:

Importing
=========

Import geometry and curves to the OBJ format.

If there is a matching ``.MTL`` for the OBJ then its materials will be imported too.


General
-------

Scale
   Value by which to scale the imported objects in relation to the world's origin.
Clamp Bounding Box
   OBJ-files often vary greatly in scale, this setting clamps the imported file to a fixed size.
Forward Axis, Up Axis
   Since many applications use a different axis for 'Up', these are axis conversion for these settings,
   Forward and Up axes -- By mapping these to different axes you can convert rotations
   between applications default up and forward axes.

   Blender uses Y Forward, Z Up (since the front view looks along the +Y direction).
   For example, it's common for applications to use Y as the up axis, in that case -Z Forward, Y Up is needed.


Options
-------

Split By Object
   Import each OBJ "object name" group (``o``) as a separate object.
Split By Group
   Import each OBJ "object name" group (``g``) as a separate object.
Vertex Groups
   Import OBJ groups as vertex groups.
Validate Meshes
   Check the imported mesh for corrupt data and fix it if necessary.
   When disabled, erroneous data may cause crashes displaying or editing the meshes.
   This option will make the importing slower but is recommended, as data errors are not always obvious.
Path Separator
   Character used to separate an object's name into a hierarchical
   structure using :doc:`/scene_layout/collections/index`.


.. _bpy.ops.wm.obj_export:

Exporting
=========

Export geometry and curves to the OBJ format.


General
-------

Include: Selected Only
   Only export the selected objects. Otherwise export all objects in the scene.
Scale
   Global scale to use on export.
Forward Axis, Up Axis
   Since many applications use a different axis for 'Up', there are axis conversion settings,
   Forward and Up axis -- By mapping these to different axis you can convert rotations
   between applications default up and forward axis.

   Blender uses Y Forward, Z Up (since the front view looks along the +Y direction).
   For example, its common for applications to use Y as the up axis, in that case -Z Forward, Y Up is needed.


Geometry Properties
^^^^^^^^^^^^^^^^^^^

UV Coordinates
   Write out the active UV layers coordinates from Blender.
Normals
   Write out Blender's face and vertex normals (depending on the faces smooth setting).

   Mostly this isn't needed since most applications will calculate their
   own normals but to match Blender's normal map textures you will need to write these too.
Colors
   Write out the active vertex colors attribute layer, if present. Colors are exported in
   "xyzrgb" OBJ extension format.
Curves as NURBS
   Write out NURBS curves as OBJ NURBS rather than converting to geometry.
Triangulated Mesh
   Write out quads as two triangles. Some programs only have very basic OBJ support and only support triangles.
Apply Modifiers
   Export objects using the evaluated mesh, meaning the resulting mesh after all
   :doc:`Modifiers </modeling/modifiers/index>` have been calculated.
Properties
   For properties that have different settings for the viewport/final render pick which is used for output.
   One example where this is important is the :doc:`/modeling/modifiers/generate/subdivision_surface`.

   :Viewport: Use viewport properties.
   :Render: Use final render properties.


Grouping
--------

Object Groups
   Write out each Blender object as an OBJ object.

   .. note::

      Note that as far as Blender is concerned there is no difference between OBJ Groups and Objects,
      this option is only included for applications that treat them differently.
Material Groups
   Generate an OBJ group for each part of a geometry using a different material.
Vertex Groups
   Export the name of the vertex group of a face.
   It is approximated by choosing the vertex group with the most members among the vertices of a face.
Smooth Groups
   Write Blender's sharp edges as smooth groups.
Smooth Group Bitflags
   Generate Bitflags for smooth Groups.


Materials
---------

Write out the MTL-file along with the OBJ. Most importers that support OBJ will also read the MTL-file.

PBR Extensions
   Export MTL library using PBR extensions (roughness, metallic, sheen, clearcoat, anisotropy, transmission).
Path Mode
   When referencing paths in exported files you may want some control as to the method used since absolute paths
   may only be correct on your own system. Relative paths, on the other hand, are more portable
   but mean that you have to keep your files grouped when moving about on your local file system.
   In some cases, the path doesn't matter since the target application will search
   a set of predefined paths anyway so you have the option to strip the path too.

   :Auto: Uses relative paths for files which are in a subdirectory of the exported location,
          absolute for any directories outside that.
   :Absolute: Uses full paths.
   :Relative: Uses relative paths in every case (except when on a different drive on Windows).
   :Match: Uses relative / absolute paths based on the paths used in Blender.
   :Strip Path: Only write the filename and omit the path component.
   :Copy: Copy the file on exporting and reference it with a relative path.


Animation
---------

Exports a numbered OBJ for each frame from the start to the end frame.
Please be aware that this can take quite a long time.

Frame Start, End
   The first and last frame to export, used to determine the range of exported frames.


Compatibility
-------------

NURBS surfaces, text3D and metaballs are converted to meshes at export time.


## Ply


************
Stanford PLY
************

.. reference::

   :Category:  Import-Export
   :Menu:      :menuselection:`File --> Import/Export --> Stanford (.ply)`

Use the operator to import ASCII or binary PLY-files, you can select multiple files at once.
For exporting, you can choose to enable or disable the modifiers during the export
and you can choose which data you want to export (UV textures, Color Attributes, ...).


.. _bpy.ops.wm.ply_import:

Import
======

General
-------

Scale
   Value by which to scale the imported objects in relation to the world's origin.
Scene Unit
   Apply current scene's unit (as defined by unit scale) to imported data.
Forward Axis, Up Axis
   Since many applications use a different axis for 'Up', these are axis conversion for these settings,
   Forward and Up axes -- By mapping these to different axes you can convert rotations
   between applications default up and forward axes.

   Blender uses Y Forward, Z Up (since the front view looks along the +Y direction).
   For example, it's common for applications to use Y as the up axis, in that case -Z Forward, Y Up is needed.


Options
-------

Merge Vertices
   Attempts to combine co-located vertices where possible.
Import Vertex Colors
   The color space that the color data in the ply-file was saved in.

   :None: Does not import vertex color data.
   :sRGB: Vertex colors in the file are in sRGB :term:`Color Space`
   :Linear: Vertex colors in the file are in Linear :term:`Color Space`


.. _bpy.ops.wm.ply_export:

Export
======

General
-------

Format: ASCII
   Formats the file using the simple a ASCII format.
   This option might be helpful if the program that
   will later import the file does not support the binary file format.
Include: Selected Only
   Only selected objects are exported.
   Instanced objects, for example collections that are instanced in the scene,
   are considered 'selected' when their instancer is selected.
Scale
   Value by which to scale the exported objects in relation to the world's origin.
Forward Axis, Up Axis
   Since many applications use a different axis for 'Up', these are axis conversion for these settings,
   Forward and Up axes -- By mapping these to different axes you can convert rotations
   between applications default up and forward axes.

   Blender uses Y Forward, Z Up (since the front view looks along the +Y direction).
   For example, it's common for applications to use Y as the up axis, in that case -Z Forward, Y Up is needed.


Geometry
--------

UV Coordinates
   Write out the active UV layers coordinates from Blender.
Vertex Normals
   Write out Blender's face and vertex normals (depending on the faces smooth setting).

   Mostly this isn't needed since most applications will calculate their
   own normals but to match Blender's normal map textures you will need to write these too.
Vertex Colors
   The color space that the color data in the ply-file was saved in.

   :None: Does not import vertex color data.
   :sRGB: Vertex colors in the file are in sRGB :term:`Color Space`
   :Linear: Vertex colors in the file are in Linear :term:`Color Space`
Triangulated Mesh
   All :term:`N-gons <N-gon>` with four or more vertices will be triangulated.
   Meshes in the scene will not be affected.
   Behaves like :doc:`/modeling/modifiers/generate/triangulate` with the following settings:

   - N-gon-method: "Beauty"
   - Quad-method: "Shortest Diagonal"
   - Min vertices: 4
Apply Modifiers
   Export objects using the evaluated mesh, meaning the resulting mesh after all
   :doc:`Modifiers </modeling/modifiers/index>` have been calculated.


## Stl


***
STL
***

.. reference::

   :Category:  Import-Export
   :Menu:      :menuselection:`File --> Import/Export --> Stl (.stl)`

The STL-file format is useful if you intend to import/export the files for CAD software.
It is also commonly used for loading into 3D printing software.


.. _bpy.ops.wm.stl_import:

Importing
=========

General
-------

Scale
   Value by which to scale the imported objects in relation to the world's origin.
Scene Unit
   Apply current scene's unit (as defined by unit scale) to imported data.
Forward / Up Axis
   Since many applications use a different axis for pointing upwards, these are axis conversion for these settings,
   Forward and up axes -- By mapping these to different axes you can convert rotations
   between applications default up and forward axes.

   Blender uses Y forward, Z up (since the front view looks along the +Y direction).
   For example, it is common for applications to use Y as the up axis, in that case -Z forward, Y up is needed.


Options
-------

Facet Normals
   Use (import) facet normals (note that this will still give flat shading).
Validate Mesh
   Check the imported mesh for corrupt data and fix it if necessary.
   When disabled, erroneous data may cause crashes displaying or editing the meshes.
   This option will make the importing slower but is recommended, as data errors are not always obvious.


Exporting
=========

General
-------

Format: ASCII
   Exports the stl-file in ASCII format rather than as a binary format
Batch
   Export each object as a separate STL file.
Include: Selection Only
      When checked, only selected objects are exported.
      Instanced objects, for example collections that are instanced in the scene,
      are considered 'selected' when their instancer is selected.
Scale
   Value by which to scale the exported objects in relation to the world's origin.
Scene Unit
   Apply current scene's unit (as defined by unit scale) to exported data.
Forward, Up
   Since many applications use a different axis for 'Up', these are axis conversion for these settings,
   Forward and Up axes -- By mapping these to different axes you can convert rotations
   between applications default up and forward axes.

   Blender uses Y Forward, Z Up (since the front view looks along the +Y direction).
   For example, it's common for applications to use Y as the up axis, in that case -Z Forward, Y Up is needed.


Geometry
--------

Apply Modifiers
   Export objects using the evaluated mesh, meaning the resulting mesh after all
   :doc:`Modifiers </modeling/modifiers/index>` have been calculated.


## Usd


***************************
Universal Scene Description
***************************


Importing USD Files
===================

`USD <https://graphics.pixar.com/usd/release/index.html>`__ files typically represent the scene as
a hierarchy of primitives, or `prims <https://graphics.pixar.com/usd/release/glossary.html#USDGlossary-Prim>`__.
Individual prims contain data to describe scene entities, such as geometry, lights, cameras and transform hierarchies.
Blender's USD importer converts USD prims to a hierarchy of Blender objects. Like the USD exporter,
the importer does not yet handle more advanced USD concepts, such as layers and references.

The following USD data types can be imported as Blender objects:

- Cameras
- Curves
- Lights
- Materials
- Meshes
- Primitive Shapes
- Volume

For more information on how the various data types are handled,
see the following descriptions of the `Import Options`_.

.. note::

   When importing a `USDZ archive <https://openusd.org/release/spec_usdz.html>`__, it is
   important to carefully consider the :ref:`Import Textures <usd-import-textures>` option to determine
   whether and how to copy texture files from the zip archive.


Xform and Scope Primitives
--------------------------

USD provides an ``Xform`` prim type, containing transform data, which can be
used to represent transform hierarchies and to organize the scene.
Such ``Xform`` prims are imported as Blender empty objects.

USD also supports ``Scope`` primitives, which are entities
that do not contain transform data, but which serve to group other element of the scene.
Blender doesn't have an exact counterpart to the concept of a scope,
so such primitives are imported as Blender empties located at the origin.
This is an imperfect representation, because empty objects have a transform and ``Scopes`` do not,
but this approach nonetheless helps preserve the structure of the scene hierarchy.


PointInstancer Primitives
-------------------------

USD provides a ``UsdGeomPointInstancer`` prim type,
containing instances that are scattered on a primitive's points.

These are imported into Blender as Point Clouds using a
:doc:`/modeling/modifiers/generate/geometry_nodes`
and the :doc:`/modeling/geometry_nodes/instances/instance_on_points`.


Animations
----------

The importer supports two types of animation:

- **Animating transforms**: If a USD primitive has time-varying transform data,
  a :doc:`Transform Cache </animation/constraints/transform/transform_cache>` constraint
  will be added to the imported Blender object.
- **Animating geometry**: Animating mesh and curve geometry is supported by adding
  a :doc:`Mesh Sequence Cache </modeling/modifiers/modify/mesh_sequence_cache>` modifier to the imported data.
  Geometry attribute (`USD Primvar <https://graphics.pixar.com/usd/release/glossary.html#USDGlossary-Primvar>`__)
  animation is currently supported only for Color Attributes and UVs.
  Note that USD file sequences (i.e. a unique file per frame) are not yet supported.


Materials
---------

If a USD mesh or geometry subset has a bound material, the importer will assign to
the Blender object a material with the same name as the USD material.
If a Blender material with the same name already exists in the scene, the existing material may be used,
depending on the :ref:`Material Name Collision <usd-material-name-collision>` option.
Otherwise, a new material will be created.

If the USD material has
a `USD Preview Surface <https://graphics.pixar.com/usd/release/spec_usdpreviewsurface.html>`__ shader source,
the :ref:`render-materials-settings-viewport-display` color, metallic, and roughness are set to
the corresponding USD Preview Surface input values.

There is also an *Import USD Preview* option to convert USD Preview Surface shaders
to Blender :doc:`Principled BSDF </render/shader_nodes/shader/principled>` shader nodes.
This option can be lossy, as it does not yet handle converting all shader settings and types,
but it can generate approximate visualizations of the materials.


Coordinate System Orientation
-----------------------------

If the imported USD is Y up, a rotation will be automatically applied to
root objects to convert to Blender's Z up orientation.


Import Options
==============

The following options are available when importing from USD:

Data Types
   Cameras
      Import cameras (perspective and orthographic).
   Curves
      Import curve primitives, including USD basis and NURBS curves.
      (Note that support for Bézier basis is not yet fully implemented.)
   Lights
      Import lights. Does not currently include USD dome, cylinder or geometry lights.
   Materials
      Import materials.
   Meshes
      Import meshes.
   Volumes
      Import USD OpenVDB field assets.
   Shapes
      Imports USD primitive shapes (cubes, spheres, cones, ect) as Blender meshes.
   Skeletons
      Imports USD skeletons as Blender's :doc:`/animation/armatures/index`.
   Blend Shapes
      Imports USD skeletons as Blender's :doc:`/animation/shape_keys/index`.

Path Mask
   Import only the subset of the USD scene rooted at the given primitive.

Scale
   Value by which to scale the imported objects in relation to the world's origin.

Mesh Data
   UV Coordinates
      Read mesh UV coordinates.
   Color Attributes
      Convert the USD mesh ``displayColor`` values to Blender's Color Attributes.
   Mesh attributes
      Read USD ``Primvars`` as mesh attributes.
   Validate Meshes
      Check the imported mesh for corrupt data and fix it if necessary.
      When disabled, erroneous data may cause crashes displaying or editing the meshes.
      This option will make the importing slower but is recommended, as data errors are not always obvious.

Include
   Subdivision
      Create Subdivision Surface modifiers based on the USD ``SubdivisionScheme`` attribute.
   Scene Instancing
      Import USD scene graph instances as collection instances, otherwise they are imported as copies.
   Visible Primitives Only
      Do not import invisible USD primitives. Only applies to primitives with a non-animated
      `visibility <https://graphics.pixar.com/usd/release/glossary.html#USDGlossary-Visibility>`__ attribute.
      Primitives with animated visibility will always be imported.
   Guide
      Include primitives with
      `purpose <https://graphics.pixar.com/usd/release/glossary.html#USDGlossary-Purpose>`__ ``guide``.
   Proxy
      Include primitives with purpose ``proxy``.
   Render
      Include primitives with purpose ``render``.

Options
   Set Frame Range
      Update the scene's start and end frame to match those of the USD stage.
   Relative Path
      Select the file relative to the blend-file.
   Create Collection
      Add all imported objects to a new collection.

Light Intensity Scale
   Scale for the intensity of imported lights.


Materials
---------

Import All Materials
   Also import materials that are not used by any geometry.
   Note, when this option is false, materials referenced by geometry will still be imported.

Import USD Preview
   Convert USD Preview Surface shaders to Principled BSDF shader networks.

Set Material Blend
   If the *Import USD Preview* option is enabled, the material blend method will automatically be set based on
   the ``opacity`` and ``opacityThreshold`` shader inputs, allowing for visualization of transparent objects.

.. _usd-material-name-collision:

Material Name Collision
   Behavior when the name of an imported material conflicts with an existing material.

   :Make Unique: Import each USD material as a unique Blender material.
   :Reference Existing: If a material with the same name already exists, reference that instead of importing.


Textures
--------

When importing a USDZ package, the following options specify whether and how texture asset dependencies
of the USD should be copied from the zip archive so they can be loaded into Blender.

.. _usd-import-textures:

Import Textures
   Behavior when importing textures from a USDZ archive.

   :None: Don't import textures. Note that, with this option, material textures may fail to be resolved in Blender.
   :Packed: Import textures as packed data in the Blender file.
   :Copy: Copy files to the directory specified in the **Textures Directory** option.

Textures Directory
   Path to the directory where imported textures will be copied, when the **Import Textures** mode is **Copy**.

   Note that the default textures directory is the relative path ``//textures``, which requires the
   Blender file to have been saved before importing, so the relative path can be resolved.

File Name Collision
   Behavior when the name of an imported texture file conflicts with an existing file.

   :Use Existing: If a file with the same name already exists, use that instead of copying.
   :Overwrite: Overwrite existing files.


Exporting to USD Files
======================

Universal Scene Description (USD) files can contain complex layering, overriding, and references to other files.
Blender's USD Exporter takes a much simpler approach. When exporting, all visible, supported objects in
the scene are exported, optionally limited by their selection state. Blender does not (yet) support exporting
invisible objects, USD layers, variants, etc.

The following objects can be exported to USD:

- Meshes (of different kinds, see below).
- Cameras (perspective cameras only at the moment, not orthogonal ones).
- Light (all types except area lights).
- Hair (exported as curves, and limited to parent strands).
- Volume (both static and animated volumes).
- Armatures

When exporting an animation, the final, evaluated mesh is written to USD.
This means that the following meshes can be exported:

- Static meshes.
- Deforming meshes; here the topology of the mesh does not change,
  but the locations of the vertices change over time. Examples are animated characters or
  bouncing (but not cracking) objects.
- Arbitrarily animated meshes; here the topology does change.
  An example is the result of a fluid simulation, where splashes of fluid can break off the main body.
- Metaballs are exported as animated meshes.

.. note::

   To export the Blender scene as a `USDZ archive <https://openusd.org/release/spec_usdz.html>`__, set
   the file extension of the output file to ``.usdz``.  The exported USDZ package will be a zip archive
   containing the USD and its texture file dependencies.

.. figure:: /images/files_import-export_usd_example.png

   Shot from `Spring <https://studio.blender.org/films/spring/>`__ exported to USD and opened in USDView.


.. _bpy.ops.wm.usd_export:

Export Options
==============

The following options are available when exporting to USD:

Selection Only
   When checked, only selected objects are exported.
   Instanced objects, for example collections that are instanced in the scene,
   are considered 'selected' when their instancer is selected.

Visible Only
   Only exports objects that are not :doc:`hidden </scene_layout/object/editing/show_hide>`.
   Invisible parents of exported objects are exported as empty transforms.

Animation
   When checked, the entire scene frame range is exported.
   When unchecked, only the current scene frame is exported.

Hair
   When checked, parent hair strands are exported as a curve system.
   Hair strand colors are not exported.

UV Maps
   When checked, includes UV coordinates for exported meshes.
   The name of the UV map in USD is the same as the name in Blender.
   In USD the default name is ``st`` whereas in Blender the default name is ``UVMap``.
   To export to the standard UV map name ``st``, rename the UV map in Blender to ``st``.

Normals
   When checked, includes normals for exported meshes. This includes custom loop normals.

Materials
   Exports material information of the object.
   By default the exporter approximates the :doc:`/render/shader_nodes/shader/principled`
   node tree by converting it to USD's Preview Surface format.
   If *To USD Preview Surface* is disabled, the material is set to the viewport materials of meshes.

   Additional material properties are set in the *Material* grouping of options.

   When a mesh has multiple materials assigned, a geometry subset is created for each material.
   The first material (if any) is always applied to the mesh itself as well
   (regardless of the existence of geometry subsets),
   because the Hydra viewport does not support materials on subsets.
   See `USD issue #542 <https://github.com/PixarAnimationStudios/USD/issues/542>`__
   for more information.

   Rigging
      Armatures
         Export :doc:`Armatures </animation/armatures/index>` and meshes with
         :doc:`Armature Modifiers </modeling/modifiers/deform/armature>` as USD skeletons and skinned meshes.

         Limitations:

         - Modifiers in addition to Armature modifiers will not be applied.
         - Bendy bones are not supported.
      Only Deform Bones
         Only export :ref:`deform bones <bpy.types.Bone.use_deform>` and their parents.
      Shape Keys
         Export shape keys as USD blend shapes.

         Absolute shape keys are not supported.


Root Prim
   If set, add a transform primitive with the given path to the stage as the parent of all exported data.

Use Settings for
   Determines the whether to use *Viewport* or *Render* visibility of collection, modifiers,
   or any other property that can be set for both the *Viewport* and *Render*.


Materials
---------

Additional options when *Materials* are enabled for export.

To USD Preview Surface
   When exporting materials, approximate a :doc:`/render/shader_nodes/shader/principled`
   node tree to by converting it to USD's Preview Surface format.
   If disabled, the material is set to the viewport materials of meshes.

   .. warning::

      Not all nodes are supported; currently only Diffuse,
      Principle, Image Textures, and UVMap nodes are support.

Export Textures
   Export textures referenced by shader nodes to a "textures"
   folder which in the same directory as the USD file.

Overwrite Textures
   Allow overwriting existing texture files when exporting textures.


File References
---------------

Relative Paths
   Use relative paths to reference external files (i.e. textures, volumes) in the exported USD file,
   otherwise use absolute paths.


Experimental
------------

Instancing
   As this is an experimental option. When unchecked,
   duplicated objects are exported as real objects, so a particle system with
   100 particles that is displayed with 100 meshes will have 100 individual meshes
   in the exported file. When checked, duplicated objects are exported as
   a reference to the original object. If the original object is not part of the export,
   the first duplicate is exported as real object and used as reference.


Exporter Limitations
====================

Single-sided and Double-sided Meshes
   USD seems to support neither per-material nor per-face-group double-sidedness,
   so Blender uses the flag from the first material to mark the entire mesh as single/double-sided.
   If there is no material it defaults to double-sided.

Mesh Normals
   The mesh subdivision scheme in USD is 'Catmull-Clark' by default,
   but Blender uses 'None' instead, indicating that a polygonal mesh is exported.
   This is necessary for USD to understand the custom normals;
   otherwise the mesh is always rendered smooth.

Vertex Velocities
   Currently only fluid simulations (not meshes in general) have explicit vertex velocities.
   This is the most important case for exporting velocities, though,
   as the baked mesh changes topology all the time, and
   thus computing the velocities at import time in a post-processing step is hard.

Coordinate System Orientation
   Blender uses the Z axis as up axis. Since USD supports both Y up and Z up,
   the USD files written by Blender always use Z up.

Materials
   Very simple versions of the materials are exported, using only
   the :ref:`render-materials-settings-viewport-display` color, metallic, and roughness.

   When there are multiple materials, the mesh faces are stored as geometry subset
   and each material is assigned to the appropriate subset.
   If there is only one material this is skipped. Note that the geometry subsets are not time-sampled,
   so it may break when an animated mesh changes topology.

Hair
   Only the parent strands are exported, and only with a constant color.
   No UV coordinates, and no information about the normals.

Camera
   Only perspective cameras are exported.

Lights
   USD does not directly support spot lights, so those are not exported.

Particles
   Particles are only written when they are alive, which means that they are always visible.
   There is currently no code that deals with marking them as invisible outside their lifespan.

   Objects instanced by particle system are exported by suffixing the object name with
   the particle's persistent ID, giving each particle transform a unique name.

Instancing/Referencing
   This is still an experimental feature that can be enabled when exporting to USD.
   When enabled, instanced object meshes are written to USD as references to the original mesh.
   The first copy of the mesh is written for real, and the following copies are referencing the first.
   Which mesh is considered 'the first' is chosen more or less arbitrarily.

USDZ
   Due to a current limitation in the USD library, UDIM textures cannot be include in the USDZ archive.
   This limitation will likely be addressed in a future version of USD.
   (See `USD pull request #2133 <https://github.com/PixarAnimationStudios/USD/pull/2133>`__.)


## Index

.. _bpy.types.Library:

####################
  Linked Libraries
####################

.. toctree::
   :maxdepth: 2

   link_append.rst
   library_proxies.rst
   library_overrides.rst


## Library Overrides


*****************
Library Overrides
*****************

Library Overrides is a system designed to allow editing
:doc:`linked data </files/linked_libraries/link_append>`, while keeping it in sync
with the original library data. Most types of linked data-blocks can be overridden,
and the properties of these overrides can then be edited. When the library data changes,
unmodified properties of the overridden one will be updated accordingly.

.. note::

   The old proxy system has been deprecated in Blender 3.0, and fully removed in Blender 3.2.
   Automatic conversion from proxies to library overrides happens when loading a blend-file,
   but results on complex characters are not guaranteed and may need manual fixes.

Library overrides supports:

- Multiple independent overrides of a same linked data
  (e.g. having the same character multiple times in the same scene).
- Adding new modifiers and constraints, anywhere in the stack.
- Recursively chaining overrides (i.e. link and override overrides from another library file, etc.).

.. - Overriding many more types of data-blocks, and selectively edit some of their properties
   (e.g. materials, textures...).

.. note::

   There are known issues that have to be addressed. See the `main task of the project
   <https://projects.blender.org/blender/blender/issues/73318>`__, for more details.

.. warning::

   While in most cases library overrides data is preserved across a loss of reference linked data
   (if e.g. the library file becomes unavailable or is relocated), there are some exceptions.

   The main one is probably posed (but not animated) armature objects, when their Armature obdata
   itself is not overridden. The Pose bones of an armature object are fully linked to the bones
   of its Armature obdata, if the later goes missing, the pose bones are definitively lost.


.. note:: Proper Collections Layout Matters

   For library overrides to work well, it is much better if **all** the collections needed by
   the character are children of the root (linked and instantiated) one, such that there is a
   clear hierarchy.
   Otherwise, some data may not be properly automatically overridden, and other operations
   may be less reliable.


Override Hierarchies
====================

Hierarchy is a very important concept to understand when working with library overrides.
In Blender, a real-life asset (a character, a prop, a set, etc.) is almost never made of a
single data-block, but is rather a group of data-blocks with dependency relationships to each-other.
E.g. a character will typically have an armature object, several geometry objects,
rig-controllers objects, the object data for all of these objects, materials, textures, etc.

These relationships can be represented as a tree, with a root data-block 'linking-in' all its
dependencies, recursively. With library overrides, typically, the root of the hierarchy is also
the data-block that is directly linked when importing the asset (usually a collection).

This concept of hierarchy can also be seen as some sort of super meta-data-block. It is critical
when there are several overrides of the same linked data, since it allows to clearly identify a given
data-block to one override, leaving no ambiguity to processes that affect the whole hierarchy
(e.g. resyncing overrides with their linked data). It also allows to share relationships between
data-blocks of different hierarchies, like a parenting relationships between two different overrides
of a same character.


Resyncing Overrides
===================

The relationships between linked data-blocks can change, resulting in outdated overrides.
When this happens, overrides need to be resynced to match the new structure of their hierarchy.
Overrides are automatically resynced if needed on blend-files opening. However,
it may be needed to resynced them manually sometimes, see `Troubleshoot an Override Hierarchy`_.

.. tip::

   Blender is also able to resync library overrides from external libraries, that are then linked into a
   working file. However, this is a costly process that needs to be fully redone every time the working
   file is loaded, since Blender cannot edit/modify the external library directly.

   So users linking overrides (or creating recursive overrides) should ensure that their library files are
   regularly updated, to avoid this overhead on file load (typically, opening and saving those library files
   should be enough to update them).

.. tip::

   Auto resyncing can be disabled in the :doc:`Experimental Preferences </editors/preferences/experimental>`.


Non-Editable Overrides
======================

For technical reasons (how relationships between data-blocks are stored), Blender needs to create
overrides of a lot of data-blocks, even when only one or two of them actually needs to be edited
by the user. To reduce the amount of information and risk of potential unwanted editing, most of
these data-blocks are now marked as non-editable by default. This can be changed once the
override has been created.


.. _bpy.ops.outliner.liboverride_operation:
.. _bpy.ops.object.make_override_library:
.. _bpy.ops.ui.override_idtemplate_make:

Make an Override
================

.. reference::

   :Editor:    3D Viewport, Outliner, Properties
   :Mode:      Object Mode
   :Menu:      :menuselection:`3D Viewport --> Header --> Object --> Library Override --> Make`
               :menuselection:`Outliner --> Context Menu --> Library Override --> Make`
               :menuselection:`ID Widget --> Context Menu --> Library Override --> Make`
   :Shortcut:  :kbd:`Shift-LMB` on the 'linked'/'overridden' button of an ID Widget.

Create overrides from the selected data-blocks.

Blender automatically create overrides for all required data-blocks to ensure that
valid override hierarchies are created.

Only overrides created from selected items will be user-editable.

.. warning::

   The support for the creation of library overrides from the ID Widget (mainly from within
   the *Properties* editor) is limited. While the most common usages should be supported,
   especially with Objects, meshes, etc., much remains to be implemented.


Selected Items
--------------

Depending on where from the override is created, there are several ways to
'select' items to be overridden and user-editable.

.. note::

   This also applies to the other common operations (*Reset* and *Clear*).

   The *Troubleshoot* advanced operations only available from the Outliner
   always apply to a whole override hierarchy.

3DView
______

The selected objects will be considered as selected.

When a selected object is a local *Empty* instantiating a linked collection,
the following will happen:
* The *Empty* object will be removed.
* Its linked collection will be overridden, and that override will be instanced
in the same collection in the current *View Layer*.
* If the collection contains *Armature* objects, they will be user-editable.
Otherwise, no created override will be defined as user-editable.

Outliner
________

The operation can be applied on either the selected items only, their content only, or both.

.. tip::

   Using *Selected & Content* is an easy way to get all newly created overrides immediately
   user-editable.


ID Widget
_________

Only the linked data-block in the ID Widget is considered as selected, and set as editable
once overridden.


Make Editable
-------------

That same operation can also be used to make existing overrides user-editable,
after they have been created, or :ref:`cleared <Clear Override>`


.. _bpy.ops.object.reset_override_library:
.. _bpy.ops.ui.override_idtemplate_reset:

Reset an Override
=================

.. reference::

   :Editor:    3D Viewport, Outliner, Properties
   :Mode:      Object Mode
   :Menu:      :menuselection:`3D Viewport --> Header --> Object --> Library Override --> Reset`
               :menuselection:`Outliner --> Context Menu --> Library Override --> Reset`
               :menuselection:`ID Widget --> Context Menu --> Library Override --> Reset`

Reset the selected overrides to their original values (from the linked reference data).
Unlike with the *Clear* operation, the overrides remain fully editable, and are never deleted.


.. _bpy.ops.object.clear_override_library:
.. _bpy.ops.ui.override_idtemplate_clear:
.. _Clear Override:

Clear an Override
=================

.. reference::

   :Editor:    3D Viewport, Outliner, Properties
   :Mode:      Object Mode
   :Menu:      :menuselection:`3D Viewport --> Header --> Object --> Library Override --> Clear`
               :menuselection:`Outliner --> Context Menu --> Library Override --> Clear`
               :menuselection:`ID Widget --> Context Menu --> Library Override --> Clear`
   :Shortcut:  :kbd:`Shift-LMB` on the 'overridden' button of an ID Widget.

Reset the selected overrides to their original values, and if possible without breaking the
existing hierarchy, delete them and replace them by their linked reference data.
Otherwise, keep the overrides but mark them as non-editable.


Edit an Override
================

Essentially, an override is edited the same way as a regular local data-block.
You can use operators on them, edit their properties from various editors, etc.
There are some limitations however, most notably Edit Mode is not allowed for overrides.
In most cases, as soon as you edit a property, you can see that it's overridden by its teal blue
outline/background.

You can also animate overrides, animated properties just replace/supersede overrides then.
Note that you cannot override/edit an existing animation, you'll have to create a new action.
You can manually define or remove an override from the context menu of the relevant property.
If an override is not editable, you have to make it editable first.


.. _bpy.ops.ui.override_type_set_button:

Define Overrides
----------------

.. reference::

   :Editor:    Any
   :Mode:      Object Mode
   :Property:  :menuselection:`Context Menu --> Define Overrides`
               :menuselection:`Context Menu --> Define Override`

Mark a property to be overridden in the local blend file. For array properties
all elements will be overridden.


Define Single Override
----------------------

.. reference::

   :Editor:    Any
   :Mode:      Object Mode
   :Property:  :menuselection:`Context Menu --> Define Single Override`

Mark a property to be overridden in the local blend file. For array properties only
the selected element will be overridden.


.. _bpy.ops.ui.remove_override_button:

Remove Overrides
----------------

.. reference::

   :Editor:    Any
   :Mode:      Object Mode
   :Property:  :menuselection:`Context Menu --> Remove Overrides`
               :menuselection:`Context Menu --> Remove Override`

Remove the property from the overrides. The value of the linked in data-block will be used.
For array properties all elements will be removed from the override.


Remove Single Override
----------------------

.. reference::

   :Editor:    Any
   :Mode:      Object Mode
   :Property:  :menuselection:`Context Menu --> Remove Single Override`

Remove the property from the overrides. The value of the linked in data-block will be used.
For array properties only the selected elements will be removed from the override.


.. _TroubleshootOverride:
.. _bpy.ops.outliner.liboverride_troubleshoot_operation:

Troubleshoot an Override Hierarchy
==================================

.. reference::

   :Editor:    Outliner
   :Mode:      Object Mode
   :Outliner:  :menuselection:`Context Menu --> Library override --> Troubleshoot`

These operations are only available from the Outliner contextual menu. They can help fixing a broken
override hierarchy.

Resync
------

.. reference::

   :Editor:    Outliner
   :Mode:      Object Mode
   :Outliner:  :menuselection:`Context Menu --> Library override --> Troubleshoot --> Resync`

The hierarchy of the linked data (the relationships between linked data-blocks) can change.
Overrides need to be resynced to match the new hierarchy. This operator will resync the override
to match the new hierarchy in the library.

.. warning::

   While resyncing a library override it is possible that edited overrides
   get deleted if they are changed in the original library.
   If this is the case, a warning message will be displayed stating how many overrides were deleted,
   if the deletion is undesirable the resync can be undone before saving the blend-file.

.. note:: This Process is Automatic

   Usually, this operation happens automatically when blender detects it is needed, on file load, unless
   it is disabled in the :doc:`Experimental Preferences </editors/preferences/experimental>`.


Resync Enforce
--------------

.. reference::

   :Editor:    Outliner
   :Mode:      Object Mode
   :Outliner:  :menuselection:`Context Menu --> Library override --> Troubleshoot --> Resync Enforce`

In some cases, especially with older blend-files that were saved with 'broken' (non-hierarchy-matching) overrides,
a regular resync itself cannot rebuild properly the override as expected (e.g. some objects might go missing).
To solve this issue, this operator rebuilds the local override from its linked reference,
as well as its hierarchy of dependencies, enforcing that hierarchy to match the linked data
(i.e. ignoring existing overrides on data-blocks properties).
This is similar to a regular resync, but is more forceful, aggressive,
at the cost of a potential loss of some overrides on ID pointers properties.


Delete
------

.. reference::

   :Editor:    Outliner
   :Mode:      Object Mode
   :Outliner:  :menuselection:`Context Menu --> Library override --> Troubleshoot --> Delete`

Remove the whole library override hierarchy, and replace all of these override data-blocks by
their original linked data-blocks. This fully reverts the *Make* operation.


## Library Proxies


*******
Proxies
*******

Proxies were the historical way in Blender to allow some local editing of linked data-blocks.
This was mostly aimed at character animation.

They are now fully deprecated as of Blender 3.0, replaced by the new
:doc:`Library Overrides </files/linked_libraries/library_overrides>`.

Existing proxies in older blend-files will be converted to library overrides when
opening it in Blender 3.2 and later.


## Link Append


*************
Link & Append
*************

These functions help you reuse materials, objects and other :doc:`data-blocks </files/data_blocks>`
loaded from another blend-file.
You can build libraries of common content and share them across multiple referencing files.

Newly added collections types are available in :menuselection:`Add --> Collection Instance` in the 3D Viewport.

Look in the *Outliner*, with display mode set to *Blender File*, to see all your linked and appended data-blocks.

.. note::

   It is not possible to Append or Link data from :doc:`much newer blend-files </files/blend/compatibility>`


.. _bpy.ops.wm.link:

Link
====

.. reference::

   :Editor:    Topbar
   :Mode:      All Modes
   :Menu:      :menuselection:`File --> Link`

*Link* creates a reference to the data in the source file such that
changes made there will be reflected in the referencing file the next time it is reloaded.
But linked data is not editable (to some extent, see :doc:`/files/linked_libraries/library_proxies`).

In the :doc:`File Browser </editors/file_browser>`,
navigate to the external source blend-file and select the data-block you want to reuse.

When you link an object, it will be placed in your scene at the 3D cursor position.
Many other data types, cameras, curves, and materials for example,
must be linked to an object before they become visible.


Options
-------

Relative Path
   See :ref:`files-blend-relative_paths`.
Select
   Makes the object *Active* after it is loaded.
Active Collection
   The object will be added to the active collection of the active view layer.
   Otherwise, it will be added to a new collection in the active view layer.
Instance Collections
   This option instantiates the linked collection as an object, adding it to the active scene.
   Otherwise, the linked collection is directly added to the active view layer.
Instance Object Data
   Create instances for object data which are not referenced by any objects.


.. _bpy.ops.wm.append:

Append
======

.. reference::

   :Editor:    Topbar
   :Mode:      All Modes
   :Menu:      :menuselection:`File --> Link`

*Append* makes a full copy of the data into your blend-file, without keeping any reference to the original one.
You can make further edits to your local copy of the data,
but changes in the external source file will not be reflected in the referencing file.

In the :doc:`File Browser </editors/file_browser>`,
navigate to the external source blend-file and select the data-block you want to reuse.

.. tip::

   Blend-files can also be linked/appended by dragging and dropping blend-files into the Blender window.

.. note::

   Appending data you already have linked will add objects/collections to the scene,
   but will keep them linked (and un-editable).

   This is done so existing relationships with linked data remain intact.


Options
-------

Select
   Makes the object *Active* after it is loaded.
Active Collection
   The object will be added to the active collection of the active view layer.
   Otherwise, it will be added to a new collection in the active view layer.
Instance Collections
   This option instantiates the linked collection as an object, adding it to the active scene.
   Otherwise, the linked collection is directly added to the active view layer.
Instance Object Data
   Create instances for object data which are not referenced by any objects.
Fake User
   Defines the appended data-block as :ref:`Protected <data-system-datablock-fake-user>`.
Localize All
   Appends also all indirectly linked data, instead of linking them.


.. _bpy.ops.outliner.lib_operation:

Library Reload & Relocate
=========================

Reloading is useful if you changed something in the library blend-file and want to see those changes
in your current blend-file without having to re-open it.
You can reload and relocate a whole library
from the context menu of the library items in the *Outliner*'s *Blender File* view,

Relocating allows you to reload the library from a new file path.
This can be used to either fix a broken linked library
(e.g. because the library file was moved or renamed after linking from it),
or to switch between different variations of a same set of data, in different library files.


Broken Library
--------------

While loading a blend-file, if Blender cannot find a library,
it will create placeholder data-blocks to replace missing linked ones.
That way, references to the missing data is not lost, and by relocating the missing library,
the lost data can be automatically restored.


.. _bpy.ops.object.make_local:

Make Local
==========

.. reference::

   :Editor:    3D Viewport
   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Relations --> Make Local...`

.. reference::

   :Editor:    Outliner
   :Menu:      :menuselection:`Context menu --> ID Data --> Make Local`

Makes the selected or all external objects local to the current blend-file.
Links to the original library file will be lost,
but it will make those data-blocks fully editable, just like the ones directly created in that blend-file.


Options
-------

The operation available from the *Outliner*'s context menu has no options,
and only affects the selected data-block.

The operation available from the *3D Viewport* only directly affects selected objects,
but it can also make local the objects' dependencies:

Type
   Optionally unlinks the object's Object Data and Material Data.

   Selected Objects, + Object Data, + Materials, All (i.e. including all scenes)


Known Limitations
=================

For the most part linking data will work as expected, however,
there are some corner cases which are not supported.


Circular Dependencies
---------------------

In general, dependencies should not go in both directions.
Attempting to link or append data which links back to the current file will likely result in missing links.


Object Rigid Body Constraints
-----------------------------

When linking objects *directly* into a blend-file, the *Rigid Body* settings
**will not** be linked in since they are associated with their scene's world.
As an alternative, you can link in the entire scene and set it as a
:ref:`Background Set <bpy.types.Scene.background_set>`.


.. _files-linked_libraries-known_limitations-compression:

Compression & Memory Use
------------------------

Linking to blend-files with compression enabled may significantly increase memory usage while loading files.

Reading data on demand isn't supported with compression
*(this only impacts load time, once loaded there is no difference in memory use)*.


## Image Formats

.. _bpy.types.Image:
.. _bpy.ops.image:
.. _files-media-image_formats:

**************************
Supported Graphics Formats
**************************

Image Formats
=============

This is the list of image file formats supported internally by Blender:

.. |tick|  unicode:: U+2713
.. |cross| unicode:: U+2717

.. list-table::
   :header-rows: 1
   :class: valign
   :widths: 25 25 10 10 10 20

   * - Format
     - Channel Depth
     - Alpha
     - :doc:`Metadata </render/output/properties/metadata>`
     - DPI
     - Extensions
   * - BMP
     - 8bit
     - |cross|
     - |cross|
     - |tick|
     - ``.bmp``
   * - Iris
     - 8, 16bit
     - |tick|
     - |cross|
     - |cross|
     - ``.sgi`` ``.rgb`` ``.bw``
   * - PNG
     - 8, 16bit
     - |tick|
     - |tick|
     - |tick|
     - ``.png``
   * - JPEG
     - 8bit
     - |cross|
     - |tick|
     - |tick|
     - ``.jpg`` ``.jpeg``
   * - JPEG 2000
     - 8, 12, 16bit
     - |tick|
     - |cross|
     - |cross|
     - ``.jp2`` ``.jp2`` ``.j2c``
   * - Targa
     - 8bit
     - |tick|
     - |cross|
     - |cross|
     - ``.tga``
   * - `Cineon & DPX`_
     - 8, 10, 12, 16bit
     - |tick|
     - |cross|
     - |cross|
     - ``.cin`` ``.dpx``
   * - `OpenEXR`_
     - float 16, 32bit
     - |tick|
     - |tick|
     - |tick|
     - ``.exr``
   * - `Radiance HDR`_
     - float
     - |tick|
     - |cross|
     - |cross|
     - ``.hdr``
   * - TIFF
     - 8, 16bit
     - |tick|
     - |cross|
     - |tick|
     - ``.tif`` ``.tiff``
   * - WebP
     - 8bit
     - |tick|
     - |tick|
     - |tick|
     - ``.webp``

.. hint::

   If you are not interested in technical details,
   a good rule of thumb for selecting output formats for your project is:

   Use OpenEXR
      if you intend to do compositing or color grading on these images.
   Use PNG
      if you intend on-screen output or encoding into multiple video formats.
   Use JPEG
      for on-screen output where file size is a concern and quality loss is acceptable.

   *All these formats support compression which can be important when rendering out animations.*

.. hint::

   Bit depths for image formats represent the following numbers of tonal levels per channel:

   :8: 256 levels
   :10: 1024 levels
   :12: 4096 levels
   :16: 65536 levels


Opening Images
==============

Relative Path
   Sets the file path to be relative to the currently opened blend-file.

   See :ref:`files-blend-relative_paths`.
Detect Sequences
   Automatically looks for image sequences in the selected images (based on the file name).
   Disable this when you do want to get single images that are part of a sequence.
Detect UDIMs
   Automatically looks for :doc:`UDIM </modeling/meshes/uv/workflows/udims>`
   tiles in the directory of the selected image; if matches are found they are loaded into Blender as UDIMs.
   This works by detecting if the filename has a ``.xxxx`` (four digit number) before the file extension.


.. _image-formats-open-sequence:

Opening an Image Sequence
-------------------------

To load image sequence in any of the supported image file formats,
the filename of the images must contain a digit to indicate the frame order
(e.g. ``*-0001.jpg``, ``*-0002.jpg``, ``*-0003.jpg``, etc, of any image format), indicating the frame.

The sequence could be opened by the selection of the images with any of the following methods
by the confirmation with the *Open Image* button or :kbd:`Return`.

Range
   Navigate into the directory and :kbd:`LMB` click and drag over a range of names to highlight multiple files.
   You can page down and continue :kbd:`Shift-LMB` click-dragging to add more to the selection.
Batch
   :kbd:`Shift-LMB` click selected non-related stills for batch processing; each image will be one frame,
   in sort order, and can be a mix of file types (``jpg``, ``png``, ``exr``, etc.).
All
   Press :kbd:`A` to select/deselect all files in the directory.


.. _bpy.types.ImageFormatSettings:

Saving Images
=============

File Format
   Choose what format to save the image as.

Color Mode
   Choose the color format to save the image (or video) to.
   Note that *RGBA* is not available for all image formats, check the list above for details.

   BW, RGB, RGBA
Color Depth
   Some image file formats support a varying number of bits per pixel.
   This affects the color quality and file size. Commonly used depths:

   :8-bit:
      Most common for on-screen graphics and video.
   :10, 12, 16-bit:
      Used for some formats focusing on photography and digital films
      (such as DPX and JPEG 2000).
   :16-bit Half Float:
      Since full 32bit float is often more than enough precision,
      half float can save drive space while still providing a high dynamic range.
   :32-bit Float:
      Highest quality color depth.

   .. note::

      Internally Blender's image system supports either:

      - 8 bits per channel (4 × 8 bits).
      - 32 bits float per channel (4 × 32 bits) -- *using 4 times as much memory.*

      Images higher than 8 bits per channel will be converted into a float on loading into Blender.
Compression
   Used to reduce the size of the image file.
   How this is done may vary depending on the file format and settings used.
Quality
   Similar to *Compression* but is used for JPEG based file formats.
   The quality is a percentage, 0% being the maximum amount of compression and 100% is no compression.
Save As Render
   Save image with render :doc:`color management </render/color_management>`.
   For display image formats like PNG, apply view and display transform.
   For intermediate image formats like OpenEXR, use the default render output color space.
Copy
   The Copy checkbox will define if the data-block will reference the newly created file
   or the reference will be unchanged, maintaining it with the original one.

Color Space
   To specify the color space of the source file.

   The list of color spaces depends on the active :ref:`OCIO config <ocio-config>`.
   The default supported color spaces are described in detail here:
   :ref:`Default OpenColorIO Configuration <ocio-config-default-color-spaces>`

   .. note::

      Note, *Cineon*, *DPX*, *OpenEXR*, and *Radiance HDR*
      image types default to being saved in a linear color space.


Format Details
==============

Cineon & DPX
------------

Cineon is Kodak's standard for film scanning, 10 bits per channel and logarithmic.
DPX has been derived from Cineon as the ANSI/SMPTE industry standard.
DPX supports 16-bit colors/channels, linear as well as logarithmic.
DPX is currently a widely adopted standard used in the film hardware/software industry.

DPX as well as Cineon only stores and converts the "visible" color range of values between 0.0
and 1.0 (as a result of rendering or composite).


OpenEXR
-------

`ILM's OpenEXR <https://www.openexr.com/>`__ has become a software industry standard
for HDR image files, especially because of its flexible and expandable structure.

An OpenEXR file can store multiple layers and passes.
This means OpenEXR images can be loaded into a Compositor keeping render layers and passes intact.


Output Options
^^^^^^^^^^^^^^

Available options for OpenEXR render output are:

Color Depth
   *Half* saves images in a custom 16 bits per channel floating-point format.
   This reduces the actual "bit depth" to 10-bit, with a 5-bit power value and 1-bit sign.

   Float (Half), Float (Full)
Codec
   :``PXR24``:
      Lossy algorithm from Pixar, converting 32-bit floats to 24-bit floats.
   :``ZIP``:
      Standard lossless compression using Zlib, operating on 16 scanlines at a time.
   :``PIZ``:
      Lossless wavelet compression. Compresses images with grain well.
   :``RLE``:
      Run-length encoded, lossless, works well when scanlines have same values.
   :``ZIPS``:
      Standard lossless compression using Zlib, operating on a single scanline at a time.
   :``DWAA``:
      JPEG-like lossy algorithm from DreamWorks; compresses blocks 32 scanlines together.
   :``DWAB``:
      Same as ``DWAA`` but compresses blocks of 256 scanlines.
Preview
   On rendering animations (or single frames via command line),
   Blender saves the same image also as a JPEG, for quick preview or download.


Radiance HDR
------------

Radiance is a suite of tools for lighting simulation.
Since Radiance had the first (and for a long time the only) HDR image format,
this format is supported by many other software packages.

Radiance ``.hdr`` files store colors still in 8 bits per component,
but with an additional (shared) 8-bit exponent value, making it 32 bits per pixel.


## Index

.. _files-media-index:

#################
  Media Formats
#################

.. toctree::
   :maxdepth: 2

   image_formats.rst
   video_formats.rst


## Video Formats


*******************************
Supported Video & Audio Formats
*******************************

Blender used `FFmpeg <https://ffmpeg.org/>`__ to handle video encoding/decoding various video formats.
These formats are primarily used for compressing rendered sequences into a playable movie.
Video formats are composed of a container, a codec, and sometimes audio which is stored using its own codec.
The roll of the container to encapsulate video and audio data that is compressed using a codec.

Codecs compress the channels of a video down to save space and enable continuous playback.
*Lossy* codecs make smaller files at the expense of image quality,
while *lossless* codecs compress as much as possible the video/audio, but without losing any existing data.

Some codecs, like H.264, are great for larger images. Codecs are used to encode and decode the movie,
and so must be present on both the encoding machine (Blender) and the target machine.
The results of the encoding are stored in a container file.

There are dozens, if not hundreds, of codecs, including Xvid, H.264, DivX, Microsoft,
and so on. Each has advantages and disadvantages, and compatibility with different players on
different operating systems.

.. note::

   Most codecs can only compress the RGB or YUV colors,
   but some support the Alpha channel as well. Codecs that support RGBA include:

   - `FFmpeg video codec #1 <https://en.wikipedia.org/wiki/FFV1>`__
   - `PNG <https://en.wikipedia.org/wiki/Portable_Network_Graphics>`__
   - QuickTime Animation
   - WebM/VP9 (although Blender will not import the alpha channel due to
     a `limitation of FFmpeg <https://trac.ffmpeg.org/ticket/8344>`__).


.. _files-video-containers:

FFmpeg Containers
=================

:`MPEG-1 <https://en.wikipedia.org/wiki/MPEG-1>`__:
   A standard for lossy compression of video and audio.
   It is designed to compress VHS-quality raw digital video and CD audio down to 1.5 Mbit/s.
   This container enforces the video codec, you can only define quality parameters, and the audio codec.

   File Extensions: ``.mpg``, ``.mpeg``
:`MPEG-2 <https://en.wikipedia.org/wiki/MPEG-2>`__:
   A standard for "the generic coding of moving pictures and associated audio information".
   It describes a combination of lossy video compression and lossy audio data compression
   methods which permit storage and transmission of movies using
   currently available storage media (notably DVDs) and transmission bandwidth.
   This container enforces the video codec, you can only define quality parameters, and the audio codec.

   File Extensions:  ``.dvd``, ``.vob``, ``.mpg``, ``.mpeg``
:`MPEG-4 <https://en.wikipedia.org/wiki/MPEG-4>`__:
   While being a :ref:`video codec <files-video-codecs>`, it is also a real container,
   in which you can store video and audio streams using various codecs.
   It is widely supported by many modern software and hardware players.

   File Extensions: ``.mp4``, ``.mpg``, ``.mpeg``
:`AVI <https://en.wikipedia.org/wiki/Audio_Video_Interleave>`__:
   A derivative of the Resource Interchange File Format (RIFF).
   One of the first and most widely used video container format.

   File Extension: ``.avi``
:`QuickTime <https://en.wikipedia.org/wiki/.mov>`__:
   A multi-tracks format. QuickTime and MP4 container formats can use the same codecs.
   They are mostly interchangeable in a QuickTime-only environment.
   MP4, being an international standard, has more support.

   File Extension: ``.mov``
:`DV <https://en.wikipedia.org/wiki/DV>`__:
   An intra-frame video compression scheme, used by many digital camcorders back in the days.
   It uses the discrete cosine transform (DCT, similar algorithm to JPEG)
   to compress video on a frame-by-frame basis.
   Audio is stored uncompressed.
   This container enforces the video codec, you can only define quality parameters.

   File extension: ``.dv``
:`Ogg <https://en.wikipedia.org/wiki/Ogg>`__:
   A free open-standard container format, that can hold an unlimited number of video,
   audio, picture or subtitle tracks in one file.

   File Extensions:  ``.ogg``, ``.ogv``
:`Matroska <https://en.wikipedia.org/wiki/Matroska>`__:
   A free open-standard container format, a file format that can hold an unlimited number of video,
   audio, picture or subtitle tracks in one file.

   File Extension: ``.mkv``
:`Flash <https://en.wikipedia.org/wiki/Flash_Video>`__:
   A container file format used to deliver video over the Internet using Adobe Flash Player.
   This container enforces the video codec, you can only define quality parameters.

   File Extension: ``.flv``
:`WebM <https://en.wikipedia.org/wiki/WebM>`__:
   A free open-standard container format, designed to be used for internet streaming.
   Note that this container can only hold a VP9 video codec, and Vorbis or Opus audio codecs.

   File Extension: ``.webm``


.. _files-video-codecs:

FFmpeg Video Codecs
===================

These options are not available with all :ref:`Containers <files-video-containers>`.

:No Video: For audio-only encoding.
:`DNxHD <https://en.wikipedia.org/wiki/Avid_DNxHD>`__:
   Intended to be usable as both an intermediate format suitable for use while editing,
   and as a presentation format. It can be either lossless or lossy.
:`DV <https://en.wikipedia.org/wiki/DV>`__:
   See :ref:`Containers <files-video-containers>`.
:`FFmpeg video codec #1 <https://en.wikipedia.org/wiki/FFV1>`__:
   FFV1 is a lossless intra-frame video codec.
   It can use either variable length coding or arithmetic coding for entropy coding.
   The encoder and decoder are part of the free, open-source library libavcodec in FFmpeg.
   Supports an alpha channel.
:`Flash Video <https://en.wikipedia.org/wiki/Flash_Video>`__:
   See :ref:`Containers <files-video-containers>`.
:`H.264 <https://en.wikipedia.org/wiki/H.264>`__:
   A modern variation of the MPEG-4 family, this lossy codec is very commonly used.
   It offers a very good compression/quality ratio.
:`HuffYUV <https://en.wikipedia.org/wiki/Huffyuv>`__:
   Lossless video codec created by Ben Rudiak-Gould which is
   meant to replace uncompressed YCbCr as a video capture format.
:`MPEG-1 <https://en.wikipedia.org/wiki/MPEG-1>`__:
   See :ref:`Containers <files-video-containers>`.
:`MPEG-2 <https://en.wikipedia.org/wiki/MPEG-2>`__:
   See :ref:`Containers <files-video-containers>`.
:`MPEG-4(DivX) <https://en.wikipedia.org/wiki/MPEG-4>`__:
   Inherits many of the features of MPEG-1, MPEG-2 and other related standards, but also adds new features.
:`PNG <https://en.wikipedia.org/wiki/Portable_Network_Graphics>`__:
   Lossless, this stores each frame as an independent image in the video stream.
   Compression will be poor, but as every frame is fully self-contained, scrubbing and editing can be simpler.
   Supports an alpha channel.
:`QuickTime Animation <https://en.wikipedia.org/wiki/QuickTime_Animation>`__:
   Original format of QuickTime videos. Supports an alpha channel.
:`Theora <https://en.wikipedia.org/wiki/Theora>`__:
   A free open-standard lossy codec designed together with the :ref:`Ogg container <files-video-containers>`.
:`WEBM / VP9 <https://en.wikipedia.org/wiki/VP9>`__:
   A free open-standard lossy video compression format.
   One of the most recent codecs, it is widely used for internet streaming.
:`AV1 <https://en.wikipedia.org/wiki/AV1>`__:
   A free open-standard lossy video compression format, designed as a successor to *VP9*.
   AV1 offers great compression rates and visual quality,
   *AV1* produces video files that are about 30% more space efficient than *VP9*


.. _files-audio-codecs:

FFmpeg Audio Codecs
===================

:No Audio:
   For video-only encoding.
:`AAC <https://en.wikipedia.org/wiki/Advanced_Audio_Coding>`__:
   Advanced Audio Codec, a standardized, lossy compression and encoding scheme for digital audio.
   AAC generally achieves better sound quality than MP3 at similar bit rates.
:`AC3 <https://en.wikipedia.org/wiki/Dolby_Digital>`__:
   Audio Codec 3, an audio compression technology developed by Dolby Laboratories.
:`FLAC <https://en.wikipedia.org/wiki/FLAC>`__:
   Free Lossless Audio Codec.
   Digital audio compressed by FLAC's algorithm can typically be reduced to 50-60% of its original size.
:`MP2 <https://en.wikipedia.org/wiki/MPEG-1_Audio_Layer_II>`__:
   A lossy audio compression format.
:`MP3 <https://en.wikipedia.org/wiki/MP3>`__:
   A lossy audio compression format, widely used as final audio format.
:`Opus <https://en.wikipedia.org/wiki/Opus_(audio_format)>`__:
   A lossy audio compression format, designed to encode speech or general audio
   and is intended to replace the *Vorbis* codec.
:`PCM <https://en.wikipedia.org/wiki/PCM>`__:
   Pulse Code Modulation, a method used to digitally represent sampled analog signals.
   It is the standard form for digital audio in computers and various Blu-ray,
   Compact Disc and DVD formats, as well as other uses such as digital telephone systems.
:`Vorbis <https://en.wikipedia.org/wiki/Vorbis>`__:
   An open-standard, highly-compressed format comparable to MP3 or AAC.
   Vorbis generally achieves better sound quality than MP3 at similar bit rates.


Known Limitations
=================

Video Output Size
-----------------

Some codecs impose limitations on output size,
``H.264``, for example requires both the height and width to be divisible by 2.


