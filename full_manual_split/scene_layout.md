# Index for scene_layout

- [Index](#Index)
- [Collections](#Collections)
- [Index](#Index)
- [Introduction](#Introduction)
- [Index](#Index)
- [Introduction](#Introduction)
- [Origin](#Origin)
- [Selecting](#Selecting)
- [Types](#Types)
- [Apply](#Apply)
- [Asset](#Asset)
- [Cleanup](#Cleanup)
- [Clear](#Clear)
- [Constraints](#Constraints)
- [Convert](#Convert)
- [Delete](#Delete)
- [Duplicate](#Duplicate)
- [Duplicate Linked](#Duplicate-Linked)
- [Index](#Index)
- [Join](#Join)
- [Mirror](#Mirror)
- [Modifiers](#Modifiers)
- [Parent](#Parent)
- [Rigid Body](#Rigid-Body)
- [Shading](#Shading)
- [Show Hide](#Show-Hide)
- [Snap](#Snap)
- [Track](#Track)
- [Copy Uvmaps](#Copy-Uvmaps)
- [Index](#Index)
- [Link Data](#Link-Data)
- [Link Scene](#Link-Scene)
- [Transfer Mesh Data](#Transfer-Mesh-Data)
- [Transfer Mesh Data Layout](#Transfer-Mesh-Data-Layout)
- [Index](#Index)
- [Make Single User](#Make-Single-User)
- [Align Objects](#Align-Objects)
- [Align Transform Orientation](#Align-Transform-Orientation)
- [Index](#Index)
- [Introduction](#Introduction)
- [Move](#Move)
- [Randomize](#Randomize)
- [Rotate](#Rotate)
- [Scale](#Scale)
- [Texture Space](#Texture-Space)
- [Axis Locking](#Axis-Locking)
- [Index](#Index)
- [Numeric Input](#Numeric-Input)
- [Precision](#Precision)
- [Display](#Display)
- [Index](#Index)
- [Line Art](#Line-Art)
- [Relations](#Relations)
- [Transforms](#Transforms)
- [Visibility](#Visibility)
- [Collection](#Collection)
- [Faces](#Faces)
- [Index](#Index)
- [Verts](#Verts)
- [Index](#Index)
- [Scale Cage](#Scale-Cage)
- [Toolbar](#Toolbar)
- [Tool Settings](#Tool-Settings)
- [Index](#Index)
- [Introduction](#Introduction)
- [Properties](#Properties)
- [Index](#Index)
- [Introduction](#Introduction)


## Index

.. _scene-layout-index:

####################
  Scenes & Objects
####################

.. toctree::
   :maxdepth: 2

   scene/index.rst
   object/index.rst
   collections/index.rst
   view_layers/index.rst


## Collections

.. _bpy.types.Collection:
.. _bpy.ops.collection:

***********
Collections
***********

There can be many objects in a scene: A typical stage scene consists of furniture, props,
lights, and backdrops.
Blender helps you keep everything organized by allowing you to group like objects together.
Objects can be grouped together without any kind of transformation relationship (unlike parenting).
Collections are used to just logically organize your scene,
or to facilitate one-step appending or linking between files or across scenes.


.. _scene-layout_collections_collections_tab:

Collections Tab
===============

.. reference::

   :Menu:      :menuselection:`Properties --> Collection Properties`

Collection properties tab allows convenient access to properties for the active collection.

.. figure:: /images/scene-layout_collections_property_panel.png

   Collection properties.

Restrictions
------------

Selectable
   Toggles the ability to select the objects from the 3D Viewport.
   This is useful for if you have placed something in the scene and
   do not want to accidentally select it when working on something else.

Disable in Renders
   Enables/disables visibility of the collection in renders.

Holdout
   Objects inside this collection will generate a holdout/mask in the active view layer.

Indirect Only
   Objects inside this collection will only contribute to the final image
   indirectly through shadows and reflections.


Instancing
----------

Instance Offset X, Y Z
   Applies a spatial offset of the instanced collections from the original object's origin.


.. _collections-exporters:

Exporters
---------

Each collection can be exported to a number of various file formats.
These exporters are available globally, see :doc:`/files/import_export/index`,
however, this panel streamlines the process of re-exporting the same asset(s) repeatedly.
For example when creating glTF assets for a game and iterating on the look,
or when using Blender in a studio pipeline to create USD assets.

The following file formats are supported, see each for the documentation of export parameters:

- :doc:`/files/import_export/alembic`
- :doc:`/files/import_export/usd`
- :doc:`/files/import_export/obj`
- :doc:`/files/import_export/ply`
- :doc:`/addons/import_export/scene_fbx`
- :doc:`/addons/import_export/scene_gltf2`

.. _bpy.types.Collection.active_exporter_index:

Exporter List
   A :ref:`list view <ui-list-view>` of all the enabled exporters for the active collection.
   The selecting an exporter from the list will show it's options in a sub panel below.

.. _bpy.ops.collection.exporter_add:
.. _bpy.ops.collection.exporter_remove:

Exporters can be added/removed through the ``+`` and ``-`` icons to right of the Exporter list.

.. _bpy.ops.collection.export_all:

Export All
   Exports all exports for the active collection.

.. tip::

   Use :menuselection:`File --> Export All Collections` to export all exporters for all collections.


.. _scene_layout-collections-line-art:

Line Art
--------

.. _bpy.types.Collection.lineart_usage:

Usage
   How the collection is loaded into line art.
   Child objects of the collection can override this setting
   if they wish in :ref:`Object Properties <bpy.types.ObjectLineArt.usage>`.

   :Include: Generate feature lines for this collection.
   :Occlusion Only:
      Objects in the collection will only cause occlusion to existing feature lines
      and their geometry stay invisible.
   :Exclude:
      Objects in this collection will not be loaded into line art at all.
   :Intersection Only:
      Objects in the collection will only produce intersection lines in
      the scene and their own geometry stay invisible.
   :No Intersection: Include this collection but do not generate intersection lines.
   :Force Intersection: Generate intersection lines even with objects that disabled intersection.

.. _bpy.types.Collection.lineart_use_intersection_mask:

Collection Mask
   Use custom intersection mask for faces in this collection.
   Intersection masks can be used by the Line Art modifier to filter lines.
   See :ref:`Collection Masks <bpy.types.LineartGpencilModifier.use_intersection_mask>` for more information.

.. _bpy.types.Collection.lineart_intersection_mask:

Mask
   Intersections generated by this collection will have this mask value.

.. _bpy.types.Collection.use_lineart_intersection_priority:
.. _bpy.types.Collection.lineart_intersection_priority:

Intersection Priority
   Assigns an intersection priority value for this collection.
   The intersection line will be included into the object with the higher intersection priority value.


Custom Properties
-----------------

Create and manage your own properties to store data in the collection's data block.
See the :ref:`Custom Properties <files-data_blocks-custom-properties>` page for more information.


Collections Menu
================

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Collection`
   :Shortcut:  :kbd:`M`, :kbd:`Shift-M`, :kbd:`Ctrl-G`, etc.

Move to Collection :kbd:`M`
   Move selected objects to an existing or new collection.
Link to Collection :kbd:`Shift-M`
   Add selected objects to a collection, while keeping them in their current collection.
   This way objects can appear in multiple collections.
   A new collection can be created in the pop-up.
Create New Collection :kbd:`Ctrl-G`
   Creates a new collection and adds the selected object(s) to it.
   The name of the new collection can be specified in
   the *Create New Collection* :ref:`bpy.ops.screen.redo_last` panel.
   This collection is not linked to the active scene.
Remove from Collection :kbd:`Ctrl-Alt-G`
   Remove the selected objects from a collection. If the object belongs to more than one collection,
   a pop-up lets you select the collection and an option to remove it from all collections.
Remove from All Collections :kbd:`Shift-Ctrl-Alt-G`
   Remove the selected objects from all collections.
Add Selected to Active Collection :kbd:`Shift-Ctrl-G`
   Adds the selected objects to the collections to which the active object belongs.
Remove Selected from Active Collection :kbd:`Shift-Alt-G`
   Causes the selected objects to be removed from the collections to which the active object belongs.


.. _scene-layout_collections_collections_panel:

Collections Panel
=================

.. reference::

   :Mode:      Object Mode
   :Panel:     :menuselection:`Object tab --> Collections`

.. figure:: /images/scene-layout_collections_collections_panel.png

   Collections panel.

All collections that an object has been assigned to are listed in the Properties
:menuselection:`Object tab --> Collections panel`.

Add to Collection
   Adds the selected object to a collection.
   A pop-up lets you specify the collection to add to.
New ``+``
   Creates a new collection and adds the selected object to it.
Name
   To rename a collection, simply click in the collections name field.
Remove ``X``
   To remove an object from a collection,
   find the name of the collection from which you wish to remove the object,
   and click the ``X`` button to the right of the collection name.
Specials
   Unlink Collection, Select Collection, Set Offset from Cursor
Offset
   Applies a spatial offset of the instanced collections from the original object's origin.

.. seealso:: Appending or Linking Collections

   To append a collection from another blend-file,
   consult :doc:`this page </files/linked_libraries/index>`.
   In summary, :menuselection:`File --> Link/Append Link` Select a blend-file and then the collection.

.. tip:: Selecting Collections

   Collections can be selected, see :ref:`Select Grouped <bpy.ops.object.select_grouped>` for more information.


## Index


###############
  Collections
###############

.. toctree::
   :maxdepth: 2

   introduction.rst
   collections.rst


## Introduction


************
Introduction
************

In Blender, objects are not directly part of the scenes.
Instead, they all get stored in a main database (basically the blend-file).

.. figure:: /images/scene-layout_collections_introduction_database-preview.png

   The blend-file and its stored data.

From there they are referenced into as many Scenes as you would like to see them.

When they are stored in a scene, they are part of a so-called *scene collection*.
So ultimately all the scene objects belong to this special collection.

.. figure:: /images/scene-layout_collections_introduction_scene-collection.png

   The scene collection.


Collections
===========

While the *scene collection* contains all the Scene's objects,
the user can also make their own collections to better organize these objects.

It works like a Venn diagram, where all the objects are part of the *scene collection*,
but can also be part of multiple collections.

.. figure:: /images/scene-layout_collections_introduction_venn-diagram.png

   Venn diagram.

The result is a clear and flexible way to arrange objects together on the Scene level.

.. figure:: /images/scene-layout_collections_introduction_scene-organization.png

   Scene organization.


Naming and Nesting
==================

Collections can be named and sorted hierarchically.
Just like folders can have subfolders in any operating system,
collections can have nested collections too.

.. figure:: /images/scene-layout_collections_introduction_collections-nested.png

   Nested collections.

For example: a *house* collection can contain a *bedroom* collection,
which in turn contains a *furniture* collection referencing a bed, a cabinet and other objects.


.. _scene_layout-collections-color-tagging:

Color Tagging
=============

Collections can have a color group assigned to them; helping organize
and group different collections. This color tag is displayed as part of
the collection icon in the :doc:`Outliner </editors/outliner/index>`
and various other menus. The available colors are defined by
Blender's interface :doc:`Theme </editors/preferences/themes>`.

To assign a color to a collection,
use the :ref:`Set Color Tag <bpy.ops.outliner.collection_color_tag_set>` tool in the Outliner.


## Index

.. _bpy.types.Object:
.. _bpy.ops.object:
.. _objects-index:

###########
  Objects
###########

.. toctree::
   :maxdepth: 2

   introduction.rst
   types.rst
   origin.rst
   selecting.rst
   editing/index.rst
   properties/index.rst
   tools/index.rst


## Introduction


************
Introduction
************

The geometry of a scene is constructed from one or more objects.
These objects can range from lights to illuminate your scene, basic 2D and 3D shapes to fill it with models,
armatures to animate those models, to cameras to take pictures or make video of it all.

Each Blender :doc:`object type </scene_layout/object/types>` (mesh, light, curve, camera, etc.)
is composed from two parts: an *Object* and *Object Data* (sometimes abbreviated to "ObData"):

Object
   Holds information about the position, rotation and size of a particular element.
Object Data
   Holds everything else. For example:

   :Meshes: Store geometry, material list, vertex groups, etc.
   :Cameras: Store focal length, depth of field, sensor size, etc.

   Each object has a link to its associated :ref:`object-data <properties-data-tabs>`,
   and a single object-data may be shared by many objects.


## Origin


*************
Object Origin
*************

Each object has an origin point. The location of this point determines where the object is located in 3D space.
When an object is selected, a small circle appears, denoting the origin point.
The location of the origin point is important when translating, rotating or scaling an object.
See :doc:`Pivot Points </editors/3dview/controls/pivot_point/index>` for more.

The color of the origin changes based on the :doc:`selection </scene_layout/object/selecting>`
state of the object.

:Yellow: Object is active.
:Orange: Object is selected, but not active.
:White: Object is not linked and not selected.
:Turquoise: Object is linked.
:Light Turquoise: Object is selected, linked, but not active.

.. note::

   Colors are themeable and might appear different.
   The colors described here are from the default Dark Theme.


.. _bpy.ops.object.origin_set:

Set Origin
==========

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Set Origin`

The object origin and geometry can be moved relative to each other and to the 3D cursor.

Type
   Geometry to Origin
      Moves the model to the origin and this way the origin of the object will
      also be at the center of the object.
   Origin to Geometry
      Moves the origin to the center of the object.
   Origin to 3D Cursor
      Moves the origin of the model to the position of the 3D cursor.
   Origin to Center of Mass
      Moves the origin to the calculated center of mass of model
      (assuming the mesh has a uniform density).
Center
   Median Point Center, Bounding Box Center

.. tip::

   To transform an object's origin directly, enable
   :ref:`Affect Only Origins <bpy.types.ToolSettings.use_transform_data_origin>`
   in the *Tool Settings Options*.


## Selecting


*********
Selecting
*********

Selection determines which elements will be the target of our actions.
Selections work on the current scene visible objects.
Blender has advanced selection methods. Both in *Object Mode* and in *Edit Mode*.


.. _object-active:

Selections and the Active Object
================================

Blender distinguishes between two different states of selection:

.. figure:: /images/scene-layout_object_selecting_color.png

   Active object in yellow, selected object in orange, and unselected object in black.

In *Object Mode* the last (de)selected item is called the "Active Object"
and is outlined in yellow (the others are orange).
There is at most one active object at any time.

Many actions in Blender use the active object as a reference (for example linking operations).
If you already have a selection and need to make a different object the active one,
simply reselect it with :kbd:`Shift-LMB`.

All other selected objects are just selected. You can select any number of objects.
In order to change a property or to perform an operation on all selected objects (bones, and sequencer strips)
hold :kbd:`Alt`, while confirming.


.. _object-select-menu:

Select Menu
===========

.. _bpy.ops.object.select_all:

All
---

.. reference::

   :Mode:      All Modes
   :Menu:      :menuselection:`Select --> All`
   :Shortcut:  :kbd:`A`

Select all selectable objects.


None
----

.. reference::

   :Mode:      All Modes
   :Menu:      :menuselection:`Select --> None`
   :Shortcut:  :kbd:`Alt-A`

Deselect all objects, but the active object stays the same.


Invert
------

.. reference::

   :Mode:      All Modes
   :Menu:      :menuselection:`Select --> Invert`
   :Shortcut:  :kbd:`Ctrl-I`

Toggle the selection state of all visible objects.


Box Select
----------

.. reference::

   :Mode:      All Modes
   :Menu:      :menuselection:`Select --> Box Select`
   :Shortcut:  :kbd:`B`

Interactive :ref:`box selection <tool-select-box>`.


Circle Select
-------------

.. reference::

   :Mode:      All Modes
   :Menu:      :menuselection:`Select --> Circle Select`
   :Shortcut:  :kbd:`C`

Interactive :ref:`circle selection <tool-select-circle>`.


Lasso Select
------------

.. reference::

   :Mode:      All modes
   :Menu:      :menuselection:`Select --> Lasso Select`
   :Shortcut:  :kbd:`Ctrl-Alt-LMB`

See :ref:`tool-select-lasso`.


.. _bpy.ops.object.select_camera:

Select Active Camera
--------------------

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Select --> Select Active Camera`

Selects the active camera, this is especially handy in complex scene.


.. _bpy.ops.object.select_mirror:

Select Mirror
-------------

.. reference::

   :Mode:      All Modes
   :Menu:      :menuselection:`Select --> Select Mirror`

Select the Mirror objects of the selected object,
based on their names, e.g. "sword.L" and "sword.R".


.. _bpy.ops.object.select_random:

Select Random
-------------

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Select --> Select Random`

Randomly selects unselected objects based on percentage probability.
The percentage can be modified in the *Adjust Last Operation* panel.
It is important to note that the percentage is the likelihood of
an unselected object being selected and not the percentage amount of objects
that will be selected.


.. _bpy.ops.object.select_more:
.. _bpy.ops.object.select_less:
.. _bpy.ops.object.select_hierarchy:

Select More/Less
----------------

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Select --> More/Less`
   :Shortcut:  :kbd:`Ctrl-NumpadPlus`, :kbd:`Ctrl-NumpadMinus`

Their purpose, based on the hierarchical.

More
   Expand the selection to the immediate parent and children of the selected objects.
Less
   Contrast the selection, deselect objects at the boundaries of parent/child relationships.
Parent
   Deselects the currently selected objects and selects their immediate parents.
Child
   Deselects the currently selected objects and selects their immediate children.
Extend Parent
   Extends the selection to the immediate parents of the currently selected objects.
Extend Child
   Extends the selection to the immediate children of the currently selected objects.


.. _bpy.ops.object.select_by_type:

Select All by Type
------------------

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Select --> Select All by Type`

With this tool, it becomes possible to select objects of a certain type in one go.
For a description of all object types see :doc:`Object Types </scene_layout/object/types>`.


.. _bpy.ops.object.select_grouped:

Select Grouped
--------------

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Select --> Select Grouped`
   :Shortcut:  :kbd:`Shift-G`

There are two ways to organize the objects in relation to one another.
The first one is *parenting*, and the second is simple *grouping*.
These relationships to an artist's advantage by selecting members of respective families or groups.
*Select Grouped* uses the active object as a basis to select all others.

Children
   Selects all hierarchical descendants of the active object.
Immediate Children
   Selects all direct children of the active object.
Parent
   Selects the parent of this object if it has one.
Siblings
   Select objects that have the same parent as the active object.
   This can also be used to select all root level objects (objects with no parents).
Type
   Select objects that are the same type as the active one.
Collection
   Select all objects that are in the same collection as the active one.
   If the active object belongs to more than one collection,
   a list will pop up so that you can choose which collection to select.
Object Hooks
   Every hook that belongs to the active object.
Pass
   Select objects assigned to the same :doc:`Render Pass </render/layers/passes>`.
Color
   Select objects with same :ref:`Object Color <bpy.types.Object.color>`.
Keying Set
   Select objects included in the active :doc:`Keying Set </animation/keyframes/keying_sets>`.
Light Type
   Select matching light types.


.. _bpy.ops.object.select_linked:

Select Linked
-------------

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Select --> Select Linked`
   :Shortcut:  :kbd:`Shift-L`

Selects all objects which share a common data-block with the active object.
*Select Linked* uses the active object as a basis to select all others.

Object Data
   Selects every object that is linked to the same Object Data, i.e.
   the data-block that specifies the type (mesh, curve, etc.) and the build
   (constitutive elements like vertices, control vertices, and where they are in space) of the object.
Material
   Selects every object that is linked to the same material data-block.
Instanced Collection
   Select every object that is linked to the instanced collection.
Texture
   Selects every object that is linked to the same texture data-block.
Particle System
   Selects all objects that use the same *Particle System*.
Library
   Selects all objects that are in the same :doc:`Library </files/linked_libraries/index>`.
Library (Object Data)
   Selects all objects that are in the same :doc:`Library </files/linked_libraries/index>`
   and limited to *Object Data*.


.. _bpy.ops.object.select_pattern:

Select Pattern
--------------

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Select --> Select Pattern...`

Selects all elements whose name matches a given pattern.
Supported wild-cards: ``*`` matches everything, ``?`` matches any single character,
``[abc]`` matches characters in ``abc``, and ``[!abc]`` match any character not in ``abc``.
As an example ``*house*`` matches any name that contains ``house``,
while ``floor*`` matches any name starting with ``floor``.

Case Sensitive
   The matching can be chosen to be case sensitive or not.
Extend
   When *Extend* checkbox is checked the selection is extended instead of generating a new one.


## Types

.. _objects-types:

************
Object Types
************

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Add`
   :Shortcut:  :kbd:`Shift-A`

New objects can be created with the *Add* menu in the 3D Viewport's header.

:doc:`Mesh </modeling/meshes/introduction>`
   Objects composed of vertices, edges and polygonal faces
   and can be edited extensively with Blender's mesh editing tools.
   See :doc:`Mesh Primitives </modeling/meshes/primitives>`.
:doc:`Curve </modeling/curves/introduction>`
   Mathematically defined objects which can be manipulated with control handles
   or control points (instead of vertices), to edit their length and curvature.
   See :doc:`Curves Primitives </modeling/curves/primitives>`.
:doc:`Surface </modeling/surfaces/introduction>`
   Mathematically defined patches that are manipulated with control points.
   These are useful for simple rounded forms and organic landscapes.
   See :doc:`Surfaces Primitives </modeling/surfaces/primitives>`.
:doc:`Metaball </modeling/metas/introduction>`
   Objects formed by a mathematical function (with no vertices or control points)
   defining the 3D volume in which the object exists. Meta objects have a liquid-like quality
   where when two or more metaballs are brought together,
   they merge by smoothly rounding out the connection, appearing as one unified object.
   See :doc:`Meta Primitives </modeling/metas/primitives>`.
:doc:`Text </modeling/texts/introduction>`
   Create a two-dimensional representation of a text.
:doc:`Volume </modeling/volumes/introduction>`
   Container for OpenVDB files that is generated
   by other software or Blender's :doc:`Fluid Simulator </physics/fluid/index>`.
:doc:`Grease Pencil </grease_pencil/introduction>`
   Objects created by drawing strokes.
   See :doc:`Grease Pencil Primitives </grease_pencil/primitives>`

:doc:`Armature </animation/armatures/index>`
   Used for rigging 3D models to make them pose-able and animatable.
:doc:`Lattice </animation/lattice>`
   Non-renderable wireframes commonly used for the deformation of other objects
   with help of the :doc:`Lattice Modifier </modeling/modifiers/deform/lattice>`.

:doc:`Empty </modeling/empties>`
   Null objects that are simple visual transform nodes that do not render.
   They are useful for controlling the position or movement of other objects.
:ref:`Image <bpy.types.Object.empty_image>`
   Empty objects that display images in the 3D Viewport.
   These images can be used to aid artists in modeling or animating.

   Image Plane
      Adds a :ref:`mesh plane <bpy.ops.mesh.primitive_plane_add>` with materials and texture from an image file.
      The dimensions of the plane are calculated to match the aspect of the image file.

:doc:`Light </render/lights/light_object>`
   Empty objects that emit light and are used for lighting the scene in renders.
:doc:`Light Probe </render/eevee/light_probes/index>`
   Used by the EEVEE render engine to record lighting information for indirect lighting.

:doc:`Camera </render/cameras>`
   This is the virtual camera that is used to determine what appears in the render.

:doc:`Speaker </render/output/audio/speaker>`
   Empty objects that bring a source of sound to the scene.

:doc:`Force Field </physics/forces/force_fields/index>`
   Empty objects that give simulations external forces, creating movement,
   and are represented in the 3D Viewport as small control objects.

:doc:`Collection Instance </scene_layout/object/properties/instancing/collection>`
   Lets you select from a list of existing collections. Once selected, an empty object will be created,
   with an instance of the selected collection (collection instancing active).


.. _object-common-options:

Common Options
==============

You can change the options of the object in the :ref:`bpy.ops.screen.redo_last` panel
just after creating it:

Type
   You can change the type of some objects after their creation with a selector.
Radius/Size
   Sets the starting size.
Align
   Rotates the new object so that it is aligned in one of the following manners:

   :World:
      Aligns the object to the global space axes, i.e. the object's front faces the negative Y axis (default).
   :View:
      Aligns the object to the view space axes, i.e. the object's front faces the viewport's point of view.
   :3D Cursor:
      Aligns the object to match the rotation of the :doc:`3D Cursor </editors/3dview/3d_cursor>`.
Location
   Objects are placed, by default, at the position of the 3D Cursor.
   These values let you place the object in an other position.
Rotation
   Values let you rotate the object so that default rotation is overridden.


## Apply


*****
Apply
*****

These operations lets you apply several transformations to the selected objects.
The object transformation coordinates are transferred to the object data.
If the objects have hierarchical descendants, it also applies those transformations to their children.


.. _bpy.ops.object.transform_apply:

Transforms
==========

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Apply --> Location / Rotation / Scale / Rotation & Scale`
   :Shortcut:  :kbd:`Ctrl-A`

Applying transform values essentially resets the values of object's location, rotation or scale,
while visually keeping the object data in-place.
The object origin point is moved to the global origin, the rotation is cleared and scale values are set to 1.

For simple cases you won't notice any difference the 3D Viewport or rendered output,
yet modifiers and constraints may depend on object transformation.

.. warning:: Armature Objects

   While applying transformations to armatures is supported,
   this does **not** apply to their pose location, animation curves or constraints.
   This tool should be used before rigging and animation.

When applying transforms to an object that shares Object Data between multiple objects,
the object must first be made a :ref:`Single User <data-system-datablock-make-single-user>`
which can be performed by confirming the pop-up message.

When running *Apply Transform*, the :ref:`bpy.ops.screen.redo_last` panel lets you choose
the combination of transformations to apply.


Options
-------

Location
   Apply (set) the location of the selection.
   This will make Blender consider the current location to be equivalent to 0 in each plane
   i.e. the selection will not move, the current location will be considered to be the "default location".
   The object origin will be set to actual (0, 0, 0) (where the colored axis lines intersect in each view).
Rotation
   Apply (set) the rotation of the selection.
   This will make Blender consider the current rotation to be equivalent to 0 degrees in each plane
   i.e. the selection will not rotated, the current rotation will be considered to be the "default rotation".
Scale
   Apply (set) the scale of the selection.
   This will make Blender consider the current scale to be equivalent to 0 in each plane
   i.e. the selection will not scaled, the current scale will be considered to be the "default scale".
Rotation and Scale
   Apply (set) the rotation and scale of the selection. Do the above two applications simultaneously.
Apply Properties
   Modify properties such as curve vertex radius, font size and bone envelope
   according to the applied transformation. (Found in the :ref:`bpy.ops.screen.redo_last` panel)


.. _bpy.ops.object.transforms_to_deltas:
.. _bpy.ops.object.anim_transforms_to_deltas:

Transforms to Deltas
====================

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Apply --> Location / Rotation / Scale to Deltas`
   :Shortcut:  :kbd:`Ctrl-A`

Converts primary object transformations to :ref:`delta transforms <bpy.types.Object.delta>`,
any existing delta transforms will be included as well.

- Location to Deltas
- Rotation to Deltas
- Scale to Deltas

All Transforms to Deltas
   Converts all primary transformations to delta transforms.
Animated Transform to Deltas
   Converts the primary transformation animations
   (of the translation, scale, and, rotation values) to delta transforms.


Options
-------

Reset Values
   Clear primary transform values after transferring to deltas.


.. _bpy.ops.object.visual_transform_apply:

Visual Transform
================

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Apply --> Visual Transform`
   :Shortcut:  :kbd:`Ctrl-A`

Apply (set) the result of a constraint and apply this back to the object's location, rotation and scale.


Visual Geometry as Mesh
=======================

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Apply --> Visual Geometry to Mesh`
   :Shortcut:  :kbd:`Ctrl-A`

Apply the visual state of all selected objects (modifiers, shape keys, hooks, etc.) to object data.
This is a way to freeze all object data into static meshes, as well as converts non-mesh types to mesh.

For details, see the :ref:`object-convert-to` mesh.


.. _bpy.ops.object.duplicates_make_real:

Make Instances Real
===================

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Apply --> Make Instances Real`

*Make Instances Real* creates a new object for each
:doc:`instance </scene_layout/object/properties/instancing/index>` generated by the selected ones,
and removes any direct instancing from those.

In the end, each instance becomes a real object.

.. warning::

   This applies to both direct (from verts or faces...) and indirect (from particle system...) instancing.
   In case you have tens of thousands of instances (from particles for example),
   this can significantly slow down Blender, which does not always deal well with that many objects in a scene.


Options
-------

By default, new objects will be added to the same collection as the one containing their instancer,
without keeping any hierarchy relationships. This behavior can be altered with the following options.

Parent
   If *Keep Hierarchy* is not set, parents all the generated objects to the former instancer.

   Otherwise, parents all the generated objects *which are not already parented* to their respective instancer,
   or its matching new copy (this is important in case of recursive instancing, see the note below).

Keep Hierarchy
   Preserves internal hierarchies (i.e. parent relationships) in the newly generated objects.

.. tip::

   Usually, to get a new hierarchy as close as possible from the instancing one,
   you'll want to enable both of these options.

.. note::

   Preserving relationships in recursive instancing cases (instancers instancing other instancer objects, etc.)
   is only supported to some extent currently.

   Simple cases (like an empty instancing a collection containing instances of some other collections)
   will usually work, but more complex cases will fail to fully reproduce the whole instancing hierarchy.


.. _bpy.ops.object.parent_inverse_apply:

Parent Inverse
==============

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Apply --> Parent Inverse`

Applies the object's :ref:`parent-inverse-matrix` transform to the object data.


## Asset


*****
Asset
*****

Operations for managing the :term:`Asset` status of an object.


Mark as Asset
=============

See :ref:`bpy.ops.asset.mark`.


Clear Asset
===========

See :ref:`bpy.ops.asset.clear`.


Clear Asset (Set Fake User)
===========================

See :ref:`assets-clear-set-fake-user`.


## Cleanup


********
Clean Up
********

Clean Vertex Group Weights
==========================

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Clean Up --> Clean Vertex Group Weights`

Clean Vertex Group Weights unassigns vertices from
:doc:`Vertex Groups </modeling/meshes/properties/vertex_groups/index>`
whose weights are below the *Limit*. Removes weights below a given threshold.
This tool is useful for clearing your weight groups of very low (or zero) weights.

In the example shown, a cutoff value of 0.2 is used (see operator options below)
so all blue parts are cleaned out.

Note, the images use the *Show Zero weights* Active option
so that unreferenced Weights are shown in Black.

.. figure:: /images/sculpt-paint_weight-paint_editing_clean-example.png

   Clean example.

Subset
   Restrict the tool to a subset.
   See above :ref:`The Subset Option <sculpt-paint_weight-paint_editing_subset>` for how subsets are defined.
Limit
   This is the minimum weight value that will be kept in the group.
   Weights below this value will be removed from the group.
Keep Single
   Ensure that the *Clean Vertex Group Weights* tool will not create completely unreferenced vertices
   (which are vertices that are not assigned to any vertex group), so each vertex will
   keep at least one weight, even if it is below the limit value!


Limit Total Vertex Groups
=========================

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Clean Up --> Limit Total Vertex Groups`

Reduce the number of weight groups per vertex to the specified Limit.
The tool removes lowest weights first until the limit is reached.

.. hint::

   The tool can only work reasonably when more than one weight group is selected.

Subset
   Restrict the tool to a subset.
   See above :ref:`The Subset Option <sculpt-paint_weight-paint_editing_subset>` for how subsets are defined.
Limit
   Maximum number of weights allowed on each vertex.


.. _bpy.ops.object.material_slot_remove_unused:

Remove Unused Material Slots
============================

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Clean Up --> Remove Unused Material Slots`

Removes unused :ref:`material slots <bpy.types.MaterialSlot>`.


## Clear

.. _bpy.ops.object.*clear:

*****
Clear
*****

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Clear --> Location / Scale / Rotation / Origin`
   :Shortcut:  :kbd:`Alt-G`, :kbd:`Alt-S`, :kbd:`Alt-R`

Clearing transforms resets the transform values.
The objects location and rotation values are set to 0, and the scale to 1.

Clear Location :kbd:`Alt-G`
   Clear (reset) the location of the selection.
   This will move the selection back to the coordinates (0, 0, 0).
Clear Scale :kbd:`Alt-S`
   Clear (reset) the scale of the selection.
   This will change the scale to (1, 1, 1).
Clear Rotation :kbd:`Alt-R`
   Clear (reset) the rotation of the selection.
   This will set the rotation of the selection to 0 degrees in each plane.

.. _bpy.ops.object.origin_clear:

Clear Origin
   Clears (resets) the offset of the child objects origin from
   the :doc:`Parent </scene_layout/object/editing/parent>`.
   This will cause child objects to move to the origin of the parent.
   The relationship between the parent and child is not affected,
   you can confirm the relationship is still intact by using the *Outliner* to
   verify that the child object is still parented.


Options
=======

Clear Delta
   Clear the :ref:`delta transform <bpy.types.Object.delta>` in addition to clearing the primary transforms.
   (Appears in the :ref:`bpy.ops.screen.redo_last` panel.)


## Constraints


***********
Constraints
***********

Operators for working with an object's :doc:`/animation/constraints/index`.


.. _bpy.ops.object.constraint_add_with_targets:

Add Constraint (with Targets)
=============================

.. reference::

   :Mode:      Object Mode and Pose Mode
   :Menu:      :menuselection:`Object --> Constraint --> Add Constraint (with Targets)`

Adds a constraint to the active object.
The type of constraint must be chosen from a pop-up menu,
though it can be changed later from the *Add Constraint (with Targets)*
:ref:`bpy.ops.screen.redo_last` panel.
If there is an other object selected besides the active one,
that object will be the constraint target (if the chosen constraint accepts targets).

When using a bone from another armature as the target for a constraint, the tool
will look inside the non-active armature and use its active bone,
provided that armature is in Pose Mode.


.. _bpy.ops.object.constraints_copy:

Copy Constraints to Selected Objects
====================================

.. reference::

   :Mode:      Object Mode and Pose Mode
   :Menu:      :menuselection:`Object --> Constraint --> Copy Constraints to Selected Objects`

Copies the active object Constraints to the rest of the selected objects.


.. _bpy.ops.object.constraints_clear:

Clear Object Constraints
========================

.. reference::

   :Mode:      Object Mode and Pose Mode
   :Panel:     :menuselection:`Object --> Constraint --> Clear Object Constraints`

Removes all Constraints of the selected object(s).


## Convert

.. _object-convert-to:
.. _bpy.ops.object.convert:

*******
Convert
*******

Curve
=====

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Convert --> Curve`

Converts the selected mesh, or text object to a curve object.
For mesh objects, only edges belonging to no faces will be taken into account.
The resulting curve will be a poly curve type, but can be converted to have
smooth segments as described in :ref:`bpy.ops.curve.spline_type_set`.


Mesh
====

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Convert --> Mesh`

Converts the selected curve, metaball, surface, or text object to a mesh object.
The actual defined resolution of these objects will be taken into account for the conversion.
Note that it also keeps the faces and volumes created by closed and extruded curves.


Grease Pencil
=============

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Convert --> Grease Pencil`

Converts the selected curve, mesh or text object to a Grease Pencil object
with strokes matching the curve, mesh, or text; basic materials are also added.
When multiple curves, meshes, or texts are selected, they are all converted into
the same Grease Pencil object.


Options
-------

Keep Original
   Duplicates the original object before converting it.
Thickness
   Strokes thickness.
Threshold Angle
   Threshold value that determines the strokes end.
Stroke Offset
   Sets offset to separate strokes from filled strokes.
Only Seam Edges
   Convert only edges marked as seam.
Export Faces
   Convert faces as filled strokes.


Trace Image to Grease Pencil
============================

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Convert --> Trace Image to Grease Pencil`

See :doc:`/grease_pencil/modes/object/trace_image`.


## Delete

.. _bpy.ops.object.delete:

******
Delete
******

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Delete`
   :Shortcut:  :kbd:`X` or :kbd:`Delete`

Delete the selected objects from the current scene.


Delete Globally
===============

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Delete Globally`
   :Shortcut:  :kbd:`Shift-X` or :kbd:`Shift-Delete`

Delete the selected objects from all scenes, and any other possible usages (like e.g. from a shading node).


## Duplicate

.. _bpy.ops.object.duplicate_move:

*********
Duplicate
*********

.. reference::

   :Mode:      Edit and Object Modes
   :Menu:      :menuselection:`Object --> Duplicate Objects`
   :Shortcut:  :kbd:`Shift-D`

This will create a visually-identical copy of the selected object(s).
The copy is created at the same position as the original object and
you are automatically placed in move mode. See the examples below.

This copy is a new object, which shares data-blocks with the original object
(by default, all the materials, textures, and F-Curves), but which has copied others,
like the mesh, for example. That is why this form of duplication is sometimes called "shallow link",
because not all data-blocks are shared; some of them are "hard copied"!

.. tip::

   You can choose which types of data-block will be linked or copied when duplicating
   in the :ref:`Preferences <bpy.types.PreferencesEdit.use_duplicate>`.


Examples
========

.. figure:: /images/scene-layout_object_editing_duplicate_example.png

   The Cube object was duplicated.

The object ``Cube`` was duplicated, using :kbd:`Shift-D`. Both these cubes have
separate meshes with unique names: ``Cube`` and ``Cube.001``.

- The original left cube is being edited, the duplicated right cube remains unchanged.
  The mesh data has been copied, not linked.
- Likewise, if one cube is edited in Object Mode, the other cube remains
  unchanged. The new object's transform properties or data-block is a copy, not linked.
- When the cube was duplicated, it inherited the material of the original cube.
  The material properties were linked, not copied.

See above if you want separate copies of the data-blocks normally linked.


## Duplicate Linked

.. _bpy.ops.object.duplicate_move_linked:

****************
Duplicate Linked
****************

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Duplicate Linked`
   :Shortcut:  :kbd:`Alt-D`

You also have the choice of creating a *Linked Duplicate* rather than a *Duplicate*;
this is called a deep link. This will create a new object with **all** of its data linked to
the original object. If you modify one of the linked objects in *Edit Mode*,
all linked copies are modified. Transform properties (object data-blocks) still remain copies,
not links, so you still can rotate, scale, and move freely without affecting the other copies.
Reference the `Examples`_ for the discussions below.

If the original object was animated, the duplicate will link to the same :ref:`Action <bpy.types.Action>`.
This means that, even though each object has separate transform properties,
they will be set to the same values by the animation system.
If this is not desired, make the action a single-user copy in the :ref:`Action or NLA Editor <actions-workflow>`.

Linked
   In the *Duplicate Objects* :ref:`bpy.ops.screen.redo_last` panel the *Linked* checkbox is checked
   unlike with *Duplicate*.

.. hint::

   If you want to make changes to an object in the new linked duplicate independently of
   the original object, you will have to manually make the object a "single-user" copy
   by :kbd:`LMB` the number in the *Object Data* panel of the Properties. (See :ref:`ui-data-block`.)

.. seealso::

   :ref:`bpy.ops.object.make_single_user` for unlinking data-blocks.


Examples
========

.. figure:: /images/scene-layout_object_editing_duplicate-linked_example.png

   The Cube object was linked duplicated.

The object ``Cube`` was linked duplicated, using :kbd:`Alt-D`.
Though both these cubes are separate objects with unique names:
``Cube`` and ``Cube.001``, the single mesh named ``Cube``, is shared by both.

- As a mesh is edited in *Edit Mode* in one object, the same occurs in
  the other cube as well. The mesh data are links, not copies.
- In contrast, if one of these two cubes is rotated or scaled in *Object Mode*,
  the other remains unchanged. The transform properties are copied, not linked.
- As in the previous example, the newly created cube has inherited
  the material of the original cube. The material properties are linked, not copied.

A common table has a top and four legs. Model one leg, and then make linked duplicates
three times for each of the remaining legs. If you later make a change to the mesh,
all the legs will still match. Linked duplicates also apply to a set of drinking glasses,
wheels on a car... anywhere there is repetition or symmetry.

.. seealso:: Linked Library Duplication

   :doc:`Linked Libraries </files/linked_libraries/index>` are also a form of duplication.
   Any object or data-block in other blend-files can be reused in the current file.

.. hint::

   If you want transform properties (i.e. object data-blocks) to be "linked",
   see the page on :doc:`parenting </scene_layout/object/editing/parent>`.


## Index


###########
  Editing
###########

.. toctree::
   :maxdepth: 2
   :titlesonly:

   transform/index.rst
   mirror.rst
   clear.rst
   apply.rst
   snap.rst
   duplicate.rst
   duplicate_linked.rst
   join.rst
   asset.rst
   parent.rst
   modifiers.rst
   constraints.rst
   track.rst
   relations/index.rst
   link_transfer/index.rst
   shading.rst
   rigid_body.rst
   convert.rst
   show_hide.rst
   cleanup.rst
   delete.rst


## Join

.. _bpy.ops.object.join:
.. _object-join:

****
Join
****

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Join`
   :Shortcut:  :kbd:`Ctrl-J`

Join merges all selected objects into the last selected *Active* object.
All object data is linked to the active object (which must be selected).
All objects must be of the same type: mesh, curve, surface or armature.
If several curves are joined, each one will keep its subtype (NURBS or Bézier).

.. note::

   Object data has many attributes which may be handled when joining.

   Materials, vertex groups, UV and Vertex layers will be merged.

   Modifiers, constraints, groups and parent relationships are ignored
   when joining and will not be applied to the active object.


## Mirror

.. _bpy.ops.transform.mirror:

******
Mirror
******

.. reference::

   :Mode:      Object and Edit Modes
   :Menu:      :menuselection:`Object/Mesh --> Mirror`
   :Shortcut:  :kbd:`Ctrl-M`

Mirroring an object or mesh selection will create a reversed version of the selection.
The position of the mirrored version of the selection is determined by
the :doc:`Pivot Point </editors/3dview/controls/pivot_point/index>`.
A common use of mirroring is to model half an object, duplicate it and then use
the mirror transform to create a reversed version to complete the model.

.. note::

   Mirrored duplicates can also be created with a :doc:`Mirror Modifier </modeling/modifiers/generate/mirror>`.

.. _fig-mesh-duplicating-mirror-selection:

.. figure:: /images/scene-layout_object_editing_mirror_example.png

   Mirroring a selection.


Usage
=====

To mirror a selection along a particular global axis, press:
:kbd:`Ctrl-M`, followed by :kbd:`X`, :kbd:`Y` or :kbd:`Z`.
The image :ref:`Mirroring a Selection <fig-mesh-duplicating-mirror-selection>`
shows the results of this action after a mesh element has been duplicated.

In mesh mode, you can mirror the selection on the currently selected
:doc:`Transform Orientations </editors/3dview/controls/orientation>`
by pressing the appropriate axis key a second time. For example,
if the Transform Orientation is set to *Normal*, pressing:
:kbd:`Ctrl-M`, followed by :kbd:`X` and then :kbd:`X` again
will mirror the selection along the X axis of the *Normal Orientation*.

.. figure:: /images/scene-layout_object_editing_mirror_panel.png

   Mirror :ref:`bpy.ops.screen.redo_last` panel.

You can alternatively hold the :kbd:`MMB` to interactively mirror the object by moving
the mouse in the direction of the mirror axis.


## Modifiers


*********
Modifiers
*********

Operators for working with an object's :doc:`/modeling/modifiers/index`.


.. _bpy.ops.object.gpencil_modifier_add:
.. _bpy.ops.object.modifier_add:

Add Modifier
============

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Modifiers --> Add Modifier`

Opens a menu with a list of modifiers, selecting a modifier will add it to the bottom of :ref:`modifier-stack`.


.. _bpy.ops.object.modifiers_copy_to_selected:

Copy Modifiers to Selected Objects
==================================

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Modifiers --> Copy Modifiers to Selected Objects`

Copies all modifiers from the :term:`Active` object to the other selected objects.


.. _bpy.ops.object.modifiers_clear:

Clear Object Modifiers
======================

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Modifiers --> Clear Object Modifiers`

Deletes all modifiers from the selected objects.


## Parent

.. _bpy.types.Object.parent:

*****************
Parenting Objects
*****************

When modeling a complex object, such as a watch, you may choose to model the different parts as separate objects.
To make all the parts move as one ("the watch"), you can designate one object as the *parent* of all the other parts.
These other parts become its *children*, and any translation, rotation, or scale of the parent will also
affects its children.

Contrary to most biological lifeforms, each object or bone in Blender has at most one parent.
If an object already has a parent object and you give it another parent then Blender will remove
the previous parent relationship. When the plural "parents" is used in this chapter,
it references the hierarchy of parents, so the parent, the grandparent, great grandparent,
and so on, of an object.


.. _bpy.ops.object.parent_set:

Make Parent
===========

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Parent`
   :Shortcut:  :kbd:`Ctrl-P`

To parent objects, select at least two objects
(select the child objects first, and select the parent object last),
and press :kbd:`Ctrl-P`. The *Set Parent To* menu will pop up allowing
you to select from one of several possible different parenting types.
Selecting one of the entries in *Set Parent To* confirms,
and the child/children to parent relationship is created.
The selected objects will have their 'parent' set to the :ref:`active object <object-active>`,
and as a result will be 'siblings'.

The *Set Parent To* pop-up menu is context-sensitive, which means
the number of entries it displays can change depending on what objects are selected
when the :kbd:`Ctrl-P` shortcut is used.

Moving, rotating or scaling the parent will also usually transform the child/children.
Yet transforming the child/children of the parent will not affect the parent.
In other words, the direction of influence is from parent to child and not child to parent.

.. tip::

   You can "move" a child object back to its parent by :ref:`clearing its origin <bpy.ops.object.origin_clear>`.

Type
   Blender supports many different types of parenting, listed below.
   Besides parenting the selected objects, some types add a Modifier or Constraint to the child objects,
   with the parent as the target object or activates a parent property i.e. *Follow Path*.

   - Object
   - :doc:`Armature Deform </animation/armatures/skinning/parenting>`
   - Bone
   - :doc:`Curve Deform </modeling/modifiers/deform/curve>`
   - :ref:`Follow Path <curve-path-animation>`
   - :doc:`Path Constraint </animation/constraints/relationship/follow_path>`
   - :doc:`Lattice Deform </modeling/modifiers/deform/lattice>`
   - Vertex
   - Vertex (Triangle)

Keep Transform
   The object's current world transform (so its absolute location, rotation and scale in the world) is computed.
   The new parent is set, and then the *Parent Inverse* matrix is computed such that after setting
   the new parent the object is still at its previous world transform.

.. hint:: Use the Outliner

   There is another way to see the parent-child relationship in groups and that is to use the *Outliner* view
   of the :doc:`Outliner editor </editors/outliner/introduction>`.


.. _parent-inverse-matrix:

Parent Inverse
--------------

Blender can assign a parent without moving the child object.
This is achieved via a hidden matrix called the *Parent Inverse* matrix,
which sits between the :term:`transform <Transform>` of the parent and the child.

When objects are parented with :kbd:`Ctrl-P`, Parent Inverse matrix is updated.
Depending on the choice in the Set Parent menu, the object's local location,
rotation, and scale are also updated. For more details, see :ref:`Object Parent <object-parenting>`.

The Parent Inverse matrix can be cleared by using :ref:`Clear Parent Inverse <bpy.ops.object.parent_clear>`.

.. note::

   When setting the parent via the Object Properties panel, the Parent Inverse matrix is always reset.
   This can cause an unexpected jump in the object's position.
   To avoid this, use :kbd:`Ctrl-P` to set the new parent.


.. _object-parenting:

Object Parent
=============

*Object Parent* is the most general form of parenting that Blender supports.
It will take selected objects and make the :ref:`active object <object-active>`
the parent object of all the selected objects. Each child object will inherit
the transformations of the parent. The parent object can be of any type.

If the object has a preexisting parent, that is cleared first.
This moves the object to its own location, rotation and scale,
without its parent's influence.

There are three operators that allow you to set an object parent. They differ in
the way they compute the :ref:`Parent Inverse matrix <parent-inverse-matrix>`
and the local :term:`Transform` of the object.


Example: Object Parent (Keep Transform)
---------------------------------------

*Object Parent* with *Keep Transform* will keep any previous transformations applied to them from
the previous parent object.

Assume that we have a scene consisting of three objects, those being two empty objects named "EmptyA"
and "EmptyB", and a Monkey object. Fig. :ref:`fig-view3d-parent-scene-no` shows the three objects with
no parenting relationships active on them.

.. _fig-view3d-parent-scene-no:

.. figure:: /images/scene-layout_object_editing_parent_keep-transform-a.png

   Scene with no parenting.

If you select the Monkey object by :kbd:`LMB` click and then :kbd:`Shift-LMB`
click "EmptyA" object and press :kbd:`Ctrl-P` and finally select *Object*
from the *Set Parent To* pop-up menu.
This will result in "EmptyA" object being the parent object of the Monkey object.
With only "EmptyA" selected rotating/scaling/moving it will result in
the Monkey object being altered respectively.

Scale the "EmptyA" object, so that the Monkey becomes smaller and moves to the left a little.

.. figure:: /images/scene-layout_object_editing_parent_keep-transform-b.png

   The monkey is the child object of "EmptyA".

If you select only the Monkey object by :kbd:`LMB` click and then :kbd:`Shift-LMB`
click "EmptyB" object and press :kbd:`Ctrl-P` and select *Object* from
the *Set Parent To* pop-up menu.
This will result in "EmptyB" object being the parent object of the Monkey object.
Notice that when you change the parent of the Monkey the scale of the Monkey changed.

.. figure:: /images/scene-layout_object_editing_parent_keep-transform-c.png

   The monkey is the child object of "EmptyB".

This happens because the Monkey object never had its scale altered directly,
the change came about because it was the child of "EmptyA" which had its scale altered.
Changing the Monkey's parent to "EmptyB" resulted in those indirect changes in scale being
removed, because "EmptyB" has not had its scale altered.

This is often the required behavior, but it is also sometimes useful that
if you change your parent object that the child object keep any previous transformations
it got from the old parent object; If instead when changing the parent object of the Monkey
from "EmptyA" to "EmptyB" we had chosen parenting type *Object* and enable *Keep Transform*,
the Monkey would keep its scale information it obtained from the old parent "EmptyA"
when it is assigned to the new parent "EmptyB".

.. figure:: /images/scene-layout_object_editing_parent_keep-transform-d.png

   The Object parent with *Keep Transform*.

If you want to follow along with the above description here is the blend-file:

`File:Parent_-_Object_(Keep_Transform)_(Demo_File).blend
<https://archive.blender.org/wiki/2015/index.php/File:Parent_-_Object_(Keep_Transform)_(Demo_File).blend/>`__.


Bone Parent
===========

Bone parenting allows you to make a certain bone in an armature the parent object of another object.
This means that when transforming an armature the child object will only move
if the specific bone is the child object of moves.

.. _fig-view3d-parent-bone-parent:

.. figure:: /images/scene-layout_object_editing_parent_bone1.png

   Three pictures of armatures with four bones.

In Fig. :ref:`fig-view3d-parent-bone-parent` with the 2nd bone being the bone parent of the child object cube.
The cube is only transformed if the 1st or 2nd bones are.
Notice altering the 3rd and 4th bones has no effect on the cube.

To use bone parenting, you must first select all the child objects you wish to parent to a specific armature bone,
then :kbd:`Shift-LMB` select the armature object and switch it into Pose Mode and
then select the specific bone you wish to be the parent bone by :kbd:`LMB` selecting it.
Once done press :kbd:`Ctrl-P` and select bone from the *Set Parent To* pop-up menu.

Now transforming that bone in Pose Mode will result in the child objects also transforming.


Relative Parenting
------------------

Bone relative parenting is an option you can toggle for each bone.
This works in the same way as bone parenting with one difference.

With bone parenting if you have parented a bone to some child objects and
you select that bone and switch it into Edit Mode and then move that bone;
When you switch back into Pose Mode on that bone,
the child object which is parented to that bone will snap back to the location of the bone in Pose Mode.

.. _fig-view3d-parent-bone-parent-child:

.. figure:: /images/scene-layout_object_editing_parent_bone2.png

   Single armature bone which has a child object cube parented to it using bone parenting.

In Fig. :ref:`fig-view3d-parent-bone-parent-child` the 1st picture shows the position of the cube and
armature before the bone is moved in Edit Mode.
2nd picture shows the position of the cube and armature after the bone was selected in Edit Mode,
moved and switched back into Pose Mode. Notice that the child object moves to the new location of the pose bone.

Bone relative parenting works differently;
If you move a parent bone in Edit Mode, when you switch back to Pose Mode,
the child objects will not move to the new location of the Pose Bone.

.. _fig-view3d-parent-bone-parent-relative:

.. figure:: /images/scene-layout_object_editing_parent_bone3.png

   Single bone with bone relative parent to a cube.

In Fig. :ref:`fig-view3d-parent-bone-parent-relative` the 1st picture
shows the position of the cube and armature before the bone is moved in Edit Mode.
2nd picture shows the position of the cube and armature after the bone was selected in Edit Mode,
moved and switched back into Pose Mode.
Notice that the child object does not move to the new location of the pose bone.

.. note::

   When using :kbd:`Ctrl-P` to set parents, choosing "Bone" or "Bone Relative"
   will respectively clear and set the bone's "Relative Parenting" option.
   Since "Relative Parenting" is an option that is set per bone, this influences
   all child objects of that bone at once.


Vertex Parent
=============

For objects of type curve, surface, mesh and lattice,
there is the possibility to use one of its vertices or points as the parent of other objects.
You can parent an object to a single vertex or a group of three vertices as well;
that way the child/children will move when the parent mesh is deformed.


Vertex Parent from Edit Mode
----------------------------

In *Object Mode*, select the child/children and then the parent object.
:kbd:`Tab` into *Edit Mode* and on the parent object select either one vertex
that defines a single point, or select three vertices that define an area
(the three vertices do not have to form a complete face;
they can be any three vertices of the parent object),
and then press :kbd:`Ctrl-P` and confirm.

At this point, if a single vertex was selected,
a relationship/parenting line will be drawn from the vertex to the child/children. If three
vertices were selected then a relationship/parenting line is drawn from the averaged center of
the three points (of the parent object) to the child/children. Now,
as the parent mesh deforms and the chosen parent vertex/vertices move,
the child/children will move as well.


Vertex Parent from Object Mode
------------------------------

Vertex parenting can be performed from Object Mode,
this is done like regular object parenting,
press :kbd:`Ctrl-P` in Object Mode and select *Vertex* or *Vertex (Triangle)*.

The nearest vertices will be used from each object which is typically what you would want.

.. list-table:: Vertex Parent example.

   * - .. figure:: /images/scene-layout_object_editing_parent_object-mode-example-1.png
          :width: 320px

          The small cubes can each be automatically parented to a triad of nearby vertices on the icosphere using
          the "Vertex (Triangle)" in the set parent context menu.

     - .. figure:: /images/scene-layout_object_editing_parent_object-mode-example-2.png
          :width: 320px

          Reshaping the object in Edit Mode then means each of the cubes follows their vertex parent separately.

     - .. figure:: /images/scene-layout_object_editing_parent_object-mode-example-3.png
          :width: 320px

          Scaling the parent icosphere in Object Mode means the child cubes are also scaled as expected.

The parent context menu item means users can rapidly set up a large number of vertex parent
relationships,
and avoid the tedious effort of establishing each parent-child vertex relationship separately.

.. note::

   It is in fact a sort of "reversed" :doc:`hook </modeling/modifiers/deform/hooks>`.


.. _bpy.ops.object.parent_no_inverse_set:

Make Parent without Inverse
===========================

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Parent --> Make Parent without Inverse`

This sets the parent, and then resets the *Parent Inverse* matrix and the object's local location.
As a result, the object will move to the location of the parent, but keep its rotation and scale.

Keep Transform
   The object's current world transform (so its absolute location, rotation and scale in the world) is computed.
   The new parent is set, and then the local transform values are set in such a way that after setting
   the new parent the object is still at its previous world transform.


.. _bpy.ops.object.parent_clear:

Clear Parent
============

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Parent`
   :Shortcut:  :kbd:`Alt-P`

You can *remove* a parent-child relationship via :kbd:`Alt-P`.

Clear Parent
   If the parent in the group is selected, nothing is done.
   If a child or children are selected, they are disassociated from the parent,
   or freed, and they return to their *original* location, rotation, and size.

Clear and Keep Transformation
   Frees the children from the parent, and *keeps* the location, rotation, and size given to them by the parent.

   See `Non-Uniform Scale`_ which may apply here.

Clear Parent Inverse
   Instead of removing the hierarchical parent-child relationship, this clears
   the `Parent Inverse`_ matrix from the selected objects. With an empty matrix,
   the location, rotation and scale properties of the children are interpreted
   in the coordinate space of the parent.


Known Limitations
=================

Non-Uniform Scale
-----------------

A parent with non-uniform scale and rotation in relation to its child may cause a *shear* effect.

While this is supported by parenting, the shear will be lost when the parent is cleared since it
can't be represented by location, scale and rotation.

If *Clear and Keep Transformation* moves the object, non-uniform scale is the most likely cause.


## Rigid Body


**********
Rigid Body
**********

.. _bpy.ops.rigidbody.mass_calculate:

Calculate Mass
==============

.. reference::

   :Editor:    3D Viewport
   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Rigid Body --> Calculate Mass`

Calculate mass values for rigid body objects based on their volume and density.
The volume is calculated automatically, the density needs to be given based on the object you want to simulate.

Material Preset
   A list of preset density values for real-world materials,
   if a material is not given you can research the density and use the *Custom* preset to input the density manually.

Density
   When the *Custom* *Material Preset* is selected, this is the input density, in kg/m\ :sup:`3`, to use.


## Shading


*******
Shading
*******

.. _bpy.ops.object.shade_smooth:

Shade Smooth
============

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Shade Smooth`

The easiest way is to set an entire object as smooth or faceted by selecting a mesh object,
and in *Object Mode*, select *Shade Smooth* in the *Object* menu.
This forces the assignment of the "smoothing" attribute to each face in the mesh,
including when you add or delete geometry.

Notice that the outline of the object is still strongly faceted.
Activating the smoothing features does not actually modify the object's geometry;
it changes the way the shading is calculated across the surfaces (normals will be interpolated),
giving the illusion of a smooth surface.

Using :ref:`bpy.ops.object.shade_flat` will revert the shading back (normals will be constant)
to that shown in the first image below.

.. list-table:: Example mesh flat (left) and smooth-shaded (right).
   `Sample blend-file <https://archive.blender.org/wiki/2015/index.php/File:25-manual-meshsmooth-example.blend>`__.

   * - .. figure:: /images/scene-layout_object_editing_shading_example-flat.png
          :width: 200px

     - .. figure:: /images/scene-layout_object_editing_shading_example-smooth.png
          :width: 200px

Keep Sharp Edges
   Do not clear sharp edges (which are redundant with objects shaded as flat or smooth).
   This option is useful to not destroy data in case you want to revert changes later.


.. _bpy.ops.object.shade_smooth_by_angle:

Shade Smooth by Angle
=====================

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Shade Smooth by Angle`

Set the sharpness of mesh edges based on the angle between the neighboring faces.

Angle
   Maximum angle between face normals that will be considered as smooth.

The *Shade Flat* operator will revert the shading back to flat;
additionally, the *Shade Smooth* operator will disable all flat normals,
making the entire object appear smooth again.


.. _bpy.ops.object.shade_flat:

Shade Flat
==========

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Shade Flat`

Signify the object to render and display faces uniformly,
using the :ref:`Face Normals <modeling-meshes-structure-normals>`.
This is usually desirable for objects with flat surfaces.

Keep Sharp Edges
   Do not clear sharp edges (which are redundant with objects shaded as flat or smooth).
   This option is useful to not destroy data in case you want to revert changes later.


## Show Hide

.. _object-show-hide:
.. _bpy.ops.object.hide_view:

*********
Show/Hide
*********

.. reference::

   :Mode:      All Modes
   :Menu:      :menuselection:`Object --> Show/Hide`

Show Hidden Objects :kbd:`Alt-H`
   Reveals all hidden objects.
Hide Selected :kbd:`H`
   Hides all selected objects.
Hide Unselected :kbd:`Shift-H`
   Hides all unselected objects of the scene.


## Snap

.. _bpy.ops.view3d.snap:

****
Snap
****

.. reference::

   :Mode:      Object, Edit, and Pose Mode
   :Menu:      :menuselection:`Object/Object type --> Snap`
   :Shortcut:  :kbd:`Shift-S`

The *Snap* menu (also available from the 3D header in both *Object Mode* and *Edit Mode*
:menuselection:`Object --> Snap` and :menuselection:`Mesh --> Snap`).
This menu provides a number of options to move the cursor or your selection to a defined point
(the cursor, selection or the grid).

Selection to Grid
   Snaps the currently selected object(s) to the nearest grid point.
Selection to Cursor
   Moves each one of the currently selected object(s) to the cursor location.
Selection to Cursor (Offset)
   Places the selection at the position of the 3D cursor.
   If there are multiple objects selected, they are not moved individually at the cursor position;
   instead, they are centered around the 3D cursor, maintaining their relative distances.
Selection to Active
   Moves the selection to the origin of the active object.

Cursor to Selected
   Places the cursor to the center of the current selection, unless see below.
Cursor to World Origin
   Places the cursor to the origin of the world (location 0, 0, 0).
Cursor to Grid
   Places the cursor to the nearest grid point.
Cursor to Active
   Places the cursor to the origin of the *active* (last selected) object.

The *Cursor to Selected* option is also affected by the current :ref:`pivot-point-index`. For example:

- With the *Bounding Box Center* pivot point active,
  the *Cursor to Selected* option will snap the 3D cursor to
  the center of the bounding box surrounding the objects' origins.
- When the *Median Point* pivot point is selected,
  *Cursor to Selected* will snap the 3D cursor to
  the :doc:`median </editors/3dview/controls/pivot_point/median_point>` of the object
  origins.


## Track

.. _bpy.ops.object.track_set:

*****
Track
*****

.. reference::

   :Mode:      Object Mode
   :Panel:     :menuselection:`Object --> Track`

These tools add a tracking constraint to the selected objects;
the target object of the constraint will be the active object, which won't have a constraint added.

- :doc:`Damped Track Constraint </animation/constraints/tracking/damped_track>`
- :doc:`Track To Constraint </animation/constraints/tracking/track_to>`
- :doc:`Lock Track Constraint </animation/constraints/tracking/locked_track>`


.. _bpy.ops.object.track_clear:

Clear Track
===========

Removes all Damped Track, Track To and Lock Track Constraints from the selected objects.


Clear and Keep Transformation (Clear Track)
===========================================

Removes all Track Constraint from the selected objects, while keeping the final transform caused by them.


## Copy Uvmaps

.. _bpy.ops.object.join_uvs:

************
Copy UV Maps
************

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Link/Transfer Data --> Copy UV Maps`

The active UV map of the selected objects will be replaced by a copy of
the active UV map of the active object. If the selected object doesn't
have any UV maps, it is created. Objects must be of type mesh and
must have a matching topology.


## Index


######################
  Link/Transfer Data
######################

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Link/Transfer Data`
   :Shortcut:  :kbd:`Ctrl-L`

.. toctree::
   :maxdepth: 2

   link_scene.rst
   link_data.rst
   copy_uvmaps.rst
   transfer_mesh_data.rst
   transfer_mesh_data_layout.rst


## Link Data

.. _bpy.ops.object.make_links_data:

*********
Link Data
*********

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Link/Transfer Data...`

Links objects between scenes or data-blocks of the active object to all selected objects.
In some case (i.e. Object Data, Modifier) the target objects must be
of the same type as the active one or capable of receiving the data.
If targets already have data linked to them, it will be unlinked first.

Type
   Data-block type to link.

   - `Link Object Data`_
   - `Link Materials`_
   - `Link Animation Data`_
   - `Link Collections`_
   - `Link Instance Collection`_
   - `Link Fonts to Text`_
   - `Copy Modifiers`_
   - `Copy Grease Pencil Effects`_

.. seealso::

   :ref:`data-system-datablock-make-single-user` for unlinking data-blocks.


Link Object Data
================

Replace assigned Object Data.


Link Materials
==============

Replace assigned Materials.


Link Animation Data
===================

Replace assigned Animation Data.


Link Collections
================

Replace assigned Collections.


Link Instance Collection
========================

Replace assigned Collection Instance.


Link Fonts to Text
==================

Replace Text object Fonts.


Copy Modifiers
==============

Replace Modifiers.


Copy Grease Pencil Effects
==========================

Replace Grease Pencil Effects.


## Link Scene

.. _bpy.ops.object.make_links_scene:

*********************
Link Objects to Scene
*********************

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Link/Transfer Data --> Link Objects to Scene`

Links the selected objects into a different scene than the current one.
The *Link Objects to Scene* in the :ref:`bpy.ops.screen.redo_last` panel lets you choose between scenes.

This makes the same object exist in more than one scene at once,
including its position and animation data.
The object's origin will change its color to reflect that.


## Transfer Mesh Data

.. _bpy.ops.object.data_transfer:

******************
Transfer Mesh Data
******************

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Link/Transfer Data --> Transfer Mesh Data`

The *Data Transfer* tool transfers several types of data from one mesh to another.
Data types include vertex groups, UV maps, Color Attributes, custom normals...
Transfer works by generating a mapping between source mesh's elements (vertices, edges, etc.)
and destination ones, either on a one-to-one basis, or mapping several source elements
to a single destination one by interpolated mapping.

Transfers data layer(s) from active to selected meshes.

Freeze Operator
   Prevent changes to settings to re-run the operator.
   This is useful if you are editing several settings at once with heavy geometry.
Data Type
   Which data to transfer.

   .. figure:: /images/scene-layout_object_editing_link-transfer_transfer-mesh-data_menu.png

      Data types.

Create Data
   Add data layers on destination meshes if needed.
Vertex Mapping
   Method used to map source vertices to destination ones.
   Because the options change depending on the *Data Type*
   options are explained in `Vertex Mapping`_ below.


Vertex Mapping
==============

Topology
--------

The simplest option, expects both meshes to have identical number of elements, and match them by order (indices).
Useful e.g. between meshes that were identical copies, and got deformed differently.


One-To-One Mappings
-------------------

Those always select only one source element for each destination one, often based on shortest distance.

Vertices
   Nearest Vertex
      Uses source's nearest vertex.

   Nearest Edge Vertex
      Uses source's nearest vertex of source's nearest edge.

   Nearest Face Vertex
      Uses source's nearest vertex of source's nearest face.

Edges
   Nearest Vertices
      Uses source's edge which vertices are nearest from destination edge's vertices.

   Nearest Edge
      Uses source's nearest edge (using edge's midpoints).
   Nearest Face Edge
      Uses source's nearest edge of source's nearest face (using edge's midpoints).
Face Corners
   A face corner is not a real element by itself, it's some kind of split vertex attached to a specific face.
   Hence both vertex (location) and face (normal, ...) aspects are used to match them together.

   Nearest Corner and Best Matching Normal
      Uses source's corner having the most similar *split* normal with destination one,
      from those sharing the nearest source's vertex.
   Nearest Corner and Best Matching Face Normal
      Uses source's corner having the most similar *face* normal with destination one,
      from those sharing the nearest source's vertex.
   Nearest Corner of Nearest Face
      Uses source's nearest corner of source's nearest face.
Faces
   Nearest Face
      Uses source's nearest face.
   Best Normal-Matching:
      Uses source's face which normal is most similar with destination one.


Interpolated Mappings
---------------------

Those use several source elements for each destination one, interpolating their data during the transfer.

Vertices
   Nearest Edge Interpolated
      Uses nearest point on nearest source's edge, interpolates data from both source edge's vertices.
   Nearest Face Interpolated
      Uses nearest point on nearest source's face, interpolates data from all that source face's vertices.
   Projected Face Interpolated
      Uses point of face on source hit by projection of destination vertex along its own normal,
      interpolates data from all that source face's vertices.
Edges
   Projected Edge Interpolated
      This is a sampling process. Several rays are cast from along the destination's edge
      (interpolating both edge's vertex normals), and if enough of them hit a source's edge,
      all hit source edges' data are interpolated into destination one.
Face Corners
   A face corner is not a real element by itself, it's some kind of split vertex attached to a specific face.
   Hence both vertex (location) and face (normal, ...) aspects are used to match them together.

   Nearest Face Interpolated
      Uses nearest point of nearest source's face, interpolates data from all that source face's corners.
   Projected Face Interpolated
      Uses point of face on source hit by projection of destination corner along its own normal,
      interpolates data from all that source face's corners.
Faces
   Projected Face Interpolated
      This is a sampling process. Several rays are cast from the whole destination's face (along its own normal),
      and if enough of them hit a source's face, all hit source faces' data are interpolated into destination one.


Further Options
===============

Auto Transform
   Automatically computes the transformation to get the best possible match between source and destination meshes.

   This allows to match and transfer data between two meshes with similar shape,
   but transformed differently. Note that you'll get best results with exact copies of the same mesh.
   Otherwise, you'll likely get better results
   if you "visually" make them match in 3D space (and use *Object Transform*) instead.
Object Transform
   Evaluate source and destination meshes in global space.
Only Neighbor Geometry
   Source elements must be closer than given distance from destination one.

   Max Distance
      Maximum allowed distance between source and destination element (for non-topology mappings).

Ray Radius
   The starting ray radius to use when `Ray Casting <https://en.wikipedia.org/wiki/Ray_casting>`__
   against vertices or edges. When transferring data between meshes Blender performs a series of
   ray casts to generate mappings. Blender starts with a ray with the radius defined here,
   if that does not detect a hit then the radius is progressively
   increased until a positive hit or a limit is reached.

   This property acts as an accuracy/performance control;
   using a lower ray radius will be more accurate however,
   might take longer if Blender has to progressively increase the limit.
   Lower values will work better for dense meshes with lots of detail
   while larger values are probably better suited for simple meshes.

Mix Mode
   How to affect destination elements with source values.

   All
      Replaces everything in destination (note that *Mix Factor* is still used).
   Above Threshold
      Only replaces destination value if it is above given threshold *Mix Factor*.
      How that threshold is interpreted depends on data type,
      note that for Boolean values this option fakes a logical AND.
   Below Threshold
      Only replaces destination value if it is below given threshold *Mix Factor*.
      How that threshold is interpreted depends on data type,
      note that for Boolean values this option fakes a logical OR.
   Mix, Add, Subtract, Multiply
      Apply that operation, using mix factor to control how much of source or destination value to use.
      Only available for a few types (vertex groups, Color Attributes).
Mix Factor
   How much of the transferred data gets mixed into existing one (not supported by all data types).


## Transfer Mesh Data Layout

.. _bpy.ops.object.datalayout_transfer:

*************************
Transfer Mesh Data Layout
*************************

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Link/Transfer Data --> Transfer Mesh Data Layout`

Transfers layout of data layer(s) from active to selected meshes.

Data Type
   Which data to transfer.

   .. figure:: /images/scene-layout_object_editing_link-transfer_transfer-mesh-data_menu.png

      Data types.

Exact Match
   Also Delete some data layers from destination if necessary, so that it matches the source exactly.
Source Layers Selection
   Which layers to transfer, in case of multi-layer types.

   Active Layer
      Only transfer the active data layer.
   All Layers
      Transfer all data layers.

Destination Layers Matching
   How to match source and destination layers.

   By Name
      Match target data layers to affect by name.
   By Order
      Match target data layers to affect by order (indices).

.. seealso::

   :doc:`Data Transfer Modifier </modeling/modifiers/modify/data_transfer>`


## Index


#############
  Relations
#############

.. toctree::
   :maxdepth: 2
   :titlesonly:

   make_single_user.rst


## Make Single User

.. _bpy.ops.object.make_single_user:

****************
Make Single User
****************

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Relations --> Make Single User`

Makes the selected or all object data-blocks single users, that is, not shared
(linked) between other objects in the blend-file.

Additionally, it can also make single-user copies of its dependencies,
like meshes, curves, materials, animations...

Type
   These actions work on the selected objects, or on all the objects of the scene.

   All, Selected Objects

Data-blocks
   Lets you, in addition to the menu predefined selection, choose the type of data-blocks individually.

   :Object: Make single user objects.
   :Object Data: Make single user object data.
   :Materials: Make materials local to each data-block.
   :Object Animation:
      Make the animation of :doc:`Object Properties </scene_layout/object/properties/index>`
      data local to each object.
   :Object Data Animation: Make object data (mesh, curve etc.) animation data local to each object.

.. seealso::

   :ref:`data-system-datablock-make-single-user`


## Align Objects

.. _bpy.ops.object.align:

*************
Align Objects
*************

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Transform --> Align Objects`

The Align tool is used to align multiple selected objects so they line up on a specified axis.


Options
=======

High Quality
   Uses more precise math to better determine the locations for the objects.
   In case of positive or negative bounding box alignment,
   if one or more of the selected objects have any rotation transformations
   (or delta rotation transformations), it is recommended to check *High Quality*
   so that their bounding box is calculated with precision for all three global axes.
Align Mode
   The *Align Mode* control will define what part of the objects will be aligned:

   :Centers:
      The objects centers.
   :Positive Sides/Negative Sides:
      The positive or negative sides (on the global axes) of their respective bounding boxes.
Relative To
   The *Relative To* control will let us choose to align the objects to:

   :Active: The active object.
   :Selection: The median point of the selection.
   :3D Cursor: The current position of the 3D Cursor.
   :Scene Origin: The global origin.
Align X, Y, Z
   Chooses which axis to align the selected objects on.


## Align Transform Orientation

.. _bpy.ops.transform.transform:

******************************
Align to Transform Orientation
******************************

.. reference::

   :Mode:      Object Mode and Edit Mode
   :Menu:      :menuselection:`Object --> Transform --> Align to Transform Orientation`

Aligns (rotates) the selected objects so that their local orientation matches the active transform orientation
in the Transform orientation panel or the *Orientation* selection
in the Transform :ref:`bpy.ops.screen.redo_last` panels.


## Index

.. _bpy.ops.transform:

#############
  Transform
#############

.. toctree::
   :maxdepth: 2

   introduction.rst
   control/index.rst
   move.rst
   rotate.rst
   scale.rst
   texture_space.rst
   align_transform_orientation.rst
   randomize.rst
   align_objects.rst


## Introduction


************
Introduction
************

Transformations refer to a number of operations that can be performed on
a selected Object or Mesh that alters its position or characteristics.

Each object can be moved, rotated and scaled in *Object Mode*.
However, not all of these transformations have an effect on all objects.
For example, scaling a camera has no effect on the render dimensions.

Basic transformations include:

- :doc:`/scene_layout/object/editing/transform/move`
- :doc:`/scene_layout/object/editing/transform/rotate`
- :doc:`/scene_layout/object/editing/transform/scale`

These three transforms are the three big ones. However, more advanced transformations can be found
in the :doc:`Advanced Transformations </scene_layout/object/editing/transform/index>` section.

For making other changes to the geometry of editable objects, you should use *Edit Mode*.

Once you have added a basic object, you remain in *Object Mode*.
You can switch between *Object Mode* and *Edit Mode* by pressing :kbd:`Tab`.
The object's wireframe should now appear orange.
This means that the object is now selected and active.


## Move

.. _bpy.ops.transform.translate:

****
Move
****

.. reference::

   :Mode:      Object Mode, Edit Mode, and Pose Mode
   :Menu:      :menuselection:`Object/Mesh/Curve/Surface --> Transform --> Move`
   :Shortcut:  :kbd:`G`

In Object Mode, the move option lets you move objects.
Translation means changing location of objects. It also lets you move any elements
that make up the object within the 3D space of the active 3D Viewport.

Pressing :kbd:`G` activates "Move" transformation mode. The selected object
or element then moves freely according to the mouse pointer's location and camera.
To confirm the action, press :kbd:`LMB`.
While moving items, the amount of change along the X, Y, and Z axis is displayed in the header of the 3D Viewport.

.. figure:: /images/scene-layout_object_editing_transform_move_display-values.png

   Translation Display.

.. tip::

   Moving an object in Object Mode changes the object's origin.
   Moving the object's vertices/edges/faces in Edit Mode does not change the object's origin.

.. seealso::

   Using a combination of shortcuts gives you more control over your transformation.
   See :doc:`Transform Control </scene_layout/object/editing/transform/control/index>`.


Options
=======

Move X, Y, Z
   The amount to move the selection on the respected axis.

Orientation
   Aligns the transformation axes to a specified orientation constraint.
   See :doc:`Transform Orientations </editors/3dview/controls/orientation>` for more information.

Proportional Editing
   The extruded face will affect nearby geometry.
   See :doc:`Proportional Editing </editors/3dview/controls/proportional_editing>` for a full reference.


## Randomize

.. _bpy.ops.object.randomize_transform:

*********
Randomize
*********

.. reference::

   :Mode:      Object Mode and Edit Mode
   :Menu:      :menuselection:`Object --> Transform --> Randomize Transform`

.. figure:: /images/scene-layout_object_editing_transform_randomize_panel.png
   :figwidth: 180px
   :align: right

   Randomize transform options.

This tool randomizes the move, rotate, and scale values to an object or multiple objects.
When applied on multiple objects, each object gets its own seed value,
and will get different transform results from the rest.

Random Seed
   The random seed is an offset to the randomized transformation.
   A different seed will produce a new result.
Transform Delta
   Randomize :ref:`Delta Transform <bpy.types.Object.delta>`
   values instead of regular transform.

Randomize Location
   Randomize Location values.
Location
   The maximum distances the objects can move along each axis.

Randomize Rotation
   Randomize rotation values.
Rotation
   The maximum angle the objects can rotate on each axis.

Randomize Scale
   Randomize scale values.
Scale Even
   Use the same scale for each axis.
Scale
   The maximum scale randomization over each axis.


## Rotate

.. _bpy.ops.transform.rotate:

******
Rotate
******

.. reference::

   :Mode:      Object and Edit Modes
   :Menu:      :menuselection:`Object/Mesh/Curve/Surface --> Transform --> Rotate`
   :Shortcut:  :kbd:`R`

Rotation is also known as a spin, twist, orbit, pivot, revolve, or roll and
involves changing the orientation of elements (vertices, edges, faces, objects, etc.)
around one or more axes or
the :doc:`Pivot Point </editors/3dview/controls/pivot_point/index>`.

The angle of rotation is displayed in the header of the 3D Viewport.

.. figure:: /images/scene-layout_object_editing_transform_rotate_display-values.png

   Rotation values.

.. seealso::

   Using a combination of shortcuts gives you more control over your transformation.
   See :doc:`Transform Control </scene_layout/object/editing/transform/control/index>`.


Options
=======

Angle
   The amount of rotation.

Axis
   Used to constraint the transformation to one or more axes.

Orientation
   Aligns the transformation axes to a specified orientation constraint.
   See :doc:`Transform Orientations </editors/3dview/controls/orientation>` for more information.

Proportional Editing
   The extruded face will affect nearby geometry.
   See :doc:`Proportional Editing </editors/3dview/controls/proportional_editing>` for a full reference.


.. _view3d-transform-trackball:
.. _bpy.ops.transform.trackball:

Trackball Rotation
==================

.. reference::

   :Mode:      Object and Edit Modes
   :Shortcut:  :kbd:`R R`

A free rotation mode. Press :kbd:`R R` to enable Trackball rotation.


## Scale

.. _bpy.ops.transform.resize:

*****
Scale
*****

.. reference::

   :Mode:      Object and Edit Modes
   :Menu:      :menuselection:`Object/Mesh/Curve/Surface --> Transform --> Scale`
   :Shortcut:  :kbd:`S`

Scaling means changing proportions of objects. Pressing :kbd:`S` will enter
the *Scale* transformation mode where the selected element is scaled inward or
outward according to the mouse pointer's location. The element's scale will
increase as the mouse pointer is moved away from the Pivot Point and decrease as
the pointer is moved towards it. If the mouse pointer crosses from the original side of
the :doc:`Pivot Point </editors/3dview/controls/pivot_point/index>`
to the opposite side, the scale will continue in the negative direction and flip the element.

.. figure:: /images/scene-layout_object_editing_transform_scale_basic-usage.png

   Basic scale usage. From left to right, the panels show: the original object,
   a scaled down object, a scaled up object and a scale-flipped object.

The amount of scaling will be displayed in the header of the 3D Viewport.

.. figure:: /images/scene-layout_object_editing_transform_scale_display-values.png

   Scale values.

.. seealso::

   Using a combination of shortcuts gives you more control over your transformation.
   See :doc:`Transform Control </scene_layout/object/editing/transform/control/index>`.


Options
=======

Scale X, Y, Z
   The amount to resize the selection on the respected axis.

Orientation
   Aligns the transformation axes to a specified orientation constraint.
   See :doc:`Transform Orientations </editors/3dview/controls/orientation>` for more information.

Proportional Editing
   The extruded face will affect nearby geometry.
   See :doc:`Proportional Editing </editors/3dview/controls/proportional_editing>` for a full reference.


## Texture Space

.. _modeling_transform_edit-texture-space:

************************
Move/Scale Texture Space
************************

.. reference::

   :Mode:      Object Mode and Edit Mode
   :Menu:      :menuselection:`Object --> Transform --> Move/Scale Texture Space`

The Move/Scale Texture Space tool transforms the :ref:`Texture Space <properties-texture-space>`
of the object, instead of the object or element itself.


## Axis Locking


************
Axis Locking
************

.. figure:: /images/scene-layout_object_editing_transform_control_axis-locking_z-axis.png
   :width: 200px
   :align: right

   Axis locking.

This option limits the transformation to the specified axis.

:doc:`Transformations (translation/scale/rotation) </scene_layout/object/editing/transform/introduction>`
in *Object Mode* and *Edit Mode* (as well as extrusions in *Edit Mode*)
can be locked to a particular axis relative to
the current :doc:`transform orientation </editors/3dview/controls/orientation>`.
By locking a transformation to a particular axis you are restricting transformations to a single dimension.


Usage
=====

A locked axis will display in a brighter color than an unlocked axis. For example in the image to the right,
the Z axis is shown in light blue as movement is constrained to this axis. This example, can be achieved in two ways:


Hotkey
------

The axis of movement can be changed at any time during transformation by typing :kbd:`X`, :kbd:`Y`, :kbd:`Z`.


Pointing
--------

.. figure:: /images/scene-layout_object_editing_transform_control_axis-locking_scale-mmb.png

   Axis constraint in action.

Holding :kbd:`MMB` after starting a transformation lets you select an axis to constrain to.
A visual option to constrain the translation will be available,
showing the three axes in the 3D Viewport space. A dotted white line is used as a pointer.
The axis of choice to confirm the operation
will depend on the highlighted axis about which the :kbd:`MMB` is released.

When you already moved the mouse in the desired direction,
pressing :kbd:`MMB` will lock to the axis which was pointed at.


Axis Locking Types
==================

Axis Locking
------------

.. reference::

   :Mode:      Object and Edit Modes (move, rotate, scale, extrude)
   :Shortcut:  :kbd:`X`, :kbd:`Y`, :kbd:`Z` or :kbd:`MMB` after moving the mouse in the desired direction.

Axis locking limits the transformation to a single axis (or forbids transformations along two axes).
An object, face, vertex or other selectable item will only be able to move,
scale or rotate in a single dimension.


.. _view3d-transform-plane-lock:

Plane Locking
-------------

.. reference::

   :Mode:      Object and Edit Modes (move, scale)
   :Shortcut:  :kbd:`Shift-X`, :kbd:`Shift-Y`, :kbd:`Shift-Z` or :kbd:`Shift-MMB`
               after moving the mouse in the desired direction.

.. figure:: /images/scene-layout_object_editing_transform_control_axis-locking_plane-locking.png
   :width: 200px
   :align: right

   Plane locking.

Plane locking locks the transformation to *two* axes
(or forbids transformations along one axis),
thus creating a plane in which the element can be moved or scaled freely.
Plane locking only affects translation and scaling.

Note that for rotation, both axis and plane locking have the same effect because a rotation is
always constrained around one axis.
*Trackball* type rotations :kbd:`R R` cannot be locked at all.


Axis Locking Modes
------------------

A single key press constrains movement to the current transform orientation selection.
A second key press of the *same* key constrains movement to the corresponding *Global* axis
(except if the transform orientation is set to *Global*, in which case the *Local* orientation is used).
A third key press of the same key removes constraints.

The orientation can be set
in the :doc:`Transform Orientation </editors/3dview/controls/orientation>`
selector of the 3D Viewport header.

.. or independent in the :ref:`bpy.ops.screen.redo_last` panel?

For example, if the current transform orientation is set to *Normal*,
pressing :kbd:`G` to start translation, followed by :kbd:`Z` will lock translation
in the Z direction relative to the *Normal* orientation, pressing :kbd:`Z`
again will lock translation to the Z axis relative to the *Global* orientation.
Pressing :kbd:`Z` again will remove all constraints.
The current mode will be displayed in the left-hand side of the 3D Viewport header.

.. list-table:: Axis locking modes.

   * - .. figure:: /images/scene-layout_object_editing_transform_control_axis-locking_modes-1.png
          :width: 320px

          Z axis locking in Global orientation.

     - .. figure:: /images/scene-layout_object_editing_transform_control_axis-locking_modes-2.png
          :width: 320px

          Z axis locking in Local orientation.

     - .. figure:: /images/scene-layout_object_editing_transform_control_axis-locking_modes-3.png
          :width: 320px

          Z axis locking in Global orientation with vertex selection.

     - .. figure:: /images/scene-layout_object_editing_transform_control_axis-locking_modes-4.png
          :width: 320px

          Z axis locking in Normal orientation with vertex selection.

As can be seen in the *Axis locking modes* image,
the direction of the transform also takes into account the selection.

Note that using a locked axis does not prevent you from using the keyboard to enter
:doc:`numeric transformation </scene_layout/object/editing/transform/control/numeric_input>` values.


## Index


#####################
  Transform Control
#####################

Transform controls can be used to modify and control the effects of the available transformations.

.. toctree::
   :maxdepth: 2

   numeric_input.rst
   axis_locking.rst
   precision.rst


## Numeric Input

.. _transform-numeric-input:

*************
Numeric Input
*************

Using the mouse for transformations is convenient, but if you require more precise control,
you can also enter numeric values. After pressing the shortcut type a number
to indicate the magnitude of the transformation. Then confirm or cancel.
E.g. pressing :kbd:`S 2`, :kbd:`Return` will double the scale of an object.

Move :kbd:`G`
   By default and with no other key presses, the translation will occur along the X axis.
Rotation :kbd:`R`
   The rotation is in clockwise direction for positive values.
Scale :kbd:`S`
   Scaling works in almost identical fashion to translation.
   The primary difference is that by default, scaling applies equally to all three axes.

You can see the numbers you enter in the 3D Viewport footer.

.. figure:: /images/scene-layout_object_editing_transform_control_numeric-input_footer.png
   :align: center

   Numeric input displayed in the footer.

.. tip::

   Numeric input can also be inputted in
   the :doc:`Properties </scene_layout/object/properties/transforms>` region.


.. _transform-numeric-input-simple:

Simple Mode
===========

Blender has two "modes" a simple and an advanced one. Simple mode only accepts
simple numbers. You can use basic :ref:`text editing <ui-text-editing>` except selection.

Decimals :kbd:`Period`
   Decimals can be entered by pressing :kbd:`Period`.
Negate :kbd:`Minus`
   Negate the whole value by pressing :kbd:`Minus`.
Inverse :kbd:`Slash`
   Hitting :kbd:`Slash` during number entry switches the number being entered to
   its reciprocal, e.g. ``2 /`` results in 0.5 (1/2); ``20 /`` results in 0.05 (1/20).
Reset :kbd:`Backspace`
   Hitting :kbd:`Backspace` after having deleted all leading chars
   will first reset the edited value to initial state, and on second press,
   the whole number editing will be canceled, going back to usual transform with mouse.
Next/Previous Component :kbd:`Tab`, :kbd:`Ctrl-Tab`
   To enter numeric values for multiple axes, use :kbd:`Tab` or :kbd:`Ctrl-Tab`.
   E.g. To move an object, one unit on all three axes press: :kbd:`G 1`
   and :kbd:`Tab 1` and :kbd:`Tab 1`.

Non-number Inputs
   You can also combine numeric input with
   :doc:`Axis Locking </scene_layout/object/editing/transform/control/axis_locking>`
   to limit movement to a particular axis or tool specific shortcuts.


.. _transform-numeric-input-advanced:

Advanced Mode
=============

In advanced mode you can additionally enter expressions and units.

Use :kbd:`=` or :kbd:`NumpadAsterisk` to enable advanced mode,
and :kbd:`Ctrl-=` or :kbd:`Ctrl-NumpadAsterisk` to switch back to simple mode.

It features:

- Units (``cm``, ``"``, ``deg``, etc.).
  See :ref:`unit system <bpy.types.UnitSettings>`.
- Basic operations from Python (``+``, ``*``, ``/``, ``**``, etc.).
- Math constants and functions (``pi``, ``sin``, ``sqrt``, etc.).
  See Python's `math <https://docs.python.org/3.8/library/math.html>`__ module.

You can still use the negate and inverse shortcuts (:kbd:`Minus`, :kbd:`Slash`),
as well as non-number inputs, but you have to hold :kbd:`Ctrl` to activate them.


## Precision


*********
Precision
*********

.. reference::

   :Mode:      Object and Edit Modes
   :Shortcut:  :kbd:`Ctrl` and/or :kbd:`Shift`

Holding :kbd:`Ctrl` during a transform operation (such as move, rotate or scale)
will toggle :doc:`Transform Snapping </editors/3dview/controls/snapping>`.
When using :ref:`Increment Snap <bpy.types.ToolSettings.snap_elements_base>`
this allows the transformation to be performed in discrete amounts.

Holding :kbd:`Shift` during a transform operation will transform
the object at 1/10th the speed, allowing much finer control.

The magnitude of the transformation can be viewed in the 3D Viewport header.
Releasing :kbd:`Ctrl` or :kbd:`Shift` during the transformation will cause
the movement to revert back to its normal mode of operation.

.. note::

   The snapping behaviors described on this page **only** apply
   when :ref:`Increment Snap <bpy.types.ToolSettings.snap_elements_base>` is selected.

.. tip::

   It is possible to enable both snapping and precision mode,
   simply hold :kbd:`Ctrl` and :kbd:`Shift`. This has the following effects:

   Move
      Changes in 0.1 unit increments, regardless of zoom level.
   Rotation
      Changes in 1 unit increments.
   Scale
      Changes in 0.01 unit increments.


Usage
=====

With Hotkeys
------------

Press :kbd:`G`, :kbd:`R` or :kbd:`S` and then hold either :kbd:`Ctrl`,
:kbd:`Shift` or :kbd:`Shift-Ctrl`.


With the Transform Gizmo
------------------------

Select the gizmo handle then while moving the mouse hold :kbd:`Ctrl`, :kbd:`Shift` or :kbd:`Shift-Ctrl`
to activate precision control or snapping.

.. seealso::

   :doc:`Read more about the Transform Gizmo </editors/3dview/display/gizmo>`.

.. tip:: Combining with Other Controls

   All of the precision controls detailed on the page can be combined with
   the :doc:`Axis Locking </scene_layout/object/editing/transform/control/axis_locking>` controls and
   used with the different :doc:`Pivot Points </editors/3dview/controls/pivot_point/index>`.


Snapping
========

Move
----

.. figure:: /images/scene-layout_object_editing_transform_control_precision_units.png
   :align: right
   :width: 200px
   :figwidth: 200px

   One unit (default zoom level).

Snapping while moving objects changes the object location in 1 unit increments.
While in an :doc:`aligned view </editors/3dview/navigate/align>`,
The increment amount is changed based on the :ref:`zoom level <bpy.ops.view3d.zoom>`.
For example, at a base zoom level objects are moved in increments of 1 unit (i.e. between the two light gray lines).
Zooming in enough to see the next set of gray lines will snap in increments of 1/10 of a unit.
Zooming in further until will snap in increments of 1/100 of a unit and so on until the zoom limit is reached.
Zooming out will have the opposite effect and
cause movement to happen by increments of 10, 100 units, etc.

.. container:: lead

   .. clear


Rotation
--------

Holding :kbd:`Ctrl` will cause rotations of 5 degrees.


Scale
-----

Holding :kbd:`Ctrl` will cause size changes in increments of 0.1 units.

.. note:: Snapping Modes

   Note that when you are :ref:`Snapping To <bpy.types.ToolSettings.snap_elements_base>`
   something other than *Increment*,
   holding :kbd:`Ctrl` will cause the selection to snap to that nearest element.

   Read more about :doc:`snapping </editors/3dview/controls/snapping>`.


Precision
=========

Holding :kbd:`Shift` during transformations allows for very fine control that does not
rely on fixed increments. Rather, large movements of the mouse across
the screen only result in small transformations of the selection.

In rotation mode the selected element will be rotate in 0.01 degree increments.


## Display


****************
Viewport Display
****************

.. reference::

   :Mode:      Object Mode
   :Panel:     :menuselection:`Properties --> Object Properties --> Viewport Display`

This panel lets you configure display options for the 3D Viewport.

.. figure:: /images/scene-layout_object_properties_display_panel.png

   Viewport Display panel.

.. _bpy.types.Object.show:

Show
   Name
      Displays the object's name in the 3D Viewport.
   Axes
      Displays an object similar to an empty that shows the object's orientation.
   Wireframe
      Displays the object's wireframe on top of the solid display.
   All Edges
      Displays all wireframe edges. This overrides the
      :ref:`wireframe threshold <bpy.types.View3DOverlay.wireframe_threshold>`
      that you can set in the 3D Viewport's overlay settings.
   Texture Space
      Displays the object's :term:`Texture Space`.
   Shadow
      Allows the object to cast shadows in the viewport.

   .. _bpy.types.Object.show_in_front:

   In Front
      Makes the object display in front of others. Unsupported for instanced objects.
      Limited support in the *Material Preview* and *Rendered* shading modes
      (works for e.g. armatures, but not for meshes).

.. _bpy.types.Object.display_type:

Display As
   Lets you display the object with less detail, going from removing the textures to
   only showing a bounding box. This can be useful if you have a high-poly object
   that is slowing down the viewport.

.. _bpy.types.Object.color:

Color
   The object's color in the *Wireframe* and *Solid* viewport shading modes.
   Used when the viewport's :ref:`(Wire) Color <viewport_shading_solid_color>`
   shading option is set to *Object*.

.. _bpy.types.Object.show_bounds:
.. _bpy.types.Object.display_bounds_type:

Bounds
   Displays a bounding shape around an object. You can choose between different
   primitive shapes that might be closer to what the original object looks like.


## Index


##############
  Properties
##############

.. toctree::
   :maxdepth: 2

   transforms.rst
   relations.rst
   /scene_layout/collections/index.rst
   instancing/index.rst
   visibility.rst
   display.rst
   line_art.rst


## Line Art

.. _bpy.types.ObjectLineArt:

********
Line Art
********

.. reference::

   :Mode:      Object Mode
   :Panel:     :menuselection:`Properties --> Object Properties --> Line Art`

The *Line Art* panel is used to enable extra display options for customizing
line art rendering for a specific object.

.. figure:: /images/scene-layout_object_properties_line-art_panel.png

   Line Art panel.

.. _bpy.types.ObjectLineArt.usage:

Usage
   How the object is loaded into line art.
   This property overrides the parent collection's :ref:`scene_layout-collections-line-art` usage.

   :Inherit:
      No special loading strategy for line art.
      Loading of the object is controlled by parent collection's line art settings.
   :Include:
      Force include the object into line art calculation
      even if its parent collection specifies otherwise.
   :Intersection Only:
      The object will only produce intersection lines in the scene and its own geometry stays invisible.
   :Occlusion Only:
      The object will only cause occlusion to existing feature lines and its geometry stays invisible.
   :Exclude:
      The object will not be loaded into line art at all.
   :No Intersection:
      The object will not generate intersection lines on itself or with other objects in scene.
   :Force Intersection: Generate intersection lines even with objects that disabled intersection.

.. _bpy.types.ObjectLineArt.use_crease_override:

Override Crease
   Allows the object to have a different crease value than the global one set in the line art modifier.

   .. _bpy.types.ObjectLineArt.crease_threshold:

   Crease
      Override crease value for the object.

.. _bpy.types.ObjectLineArt.use_intersection_priority_override:
.. _bpy.types.ObjectLineArt.intersection_priority:

Intersection Priority
   Assigns an intersection priority value for this object.
   The intersection line will be included into the object with the higher intersection priority value.


## Relations


*********
Relations
*********

.. reference::

   :Mode:      Object Mode
   :Panel:     :menuselection:`Properties --> Object Properties --> Relations`

Parent
   The object to which the selected object is parented to.

.. _bpy.types.Object.parent_type:

Parent Type
   The type of parenting used. See :doc:`parenting </scene_layout/object/editing/parent>`
   for information on the different types.

.. _bpy.types.Object.use_camera_lock_parent:

Camera Parent Lock
   When the camera is locked to the view, the root parent is transformed rather than the camera.
   This is useful for camera rigs where you don't want to animate the camera directly.

.. _bpy.types.Object.track_axis:

Tracking Axis
   Axis that points in the "forward" direction.
   Applies to *Instance Vertices* when *Align to Vertex Normal* is enabled.

.. _bpy.types.Object.up_axis:

Up Axis
   Axis that points in the "upward" direction.
   Applies to *Instance Vertices* when *Align to Vertex Normal* is enabled.

.. _bpy.types.Object.pass_index:

Pass Index
   Defines the index the object will have in the Object Index render pass. See :doc:`passes </render/layers/passes>`
   and :doc:`ID mask </compositing/types/mask/id_mask>` for more information.

   .. note::

      :doc:`Volume Objects </modeling/volumes/introduction>` are not supported.


## Transforms


*********
Transform
*********

.. reference::

   :Mode:      Object Mode
   :Panel:     :menuselection:`Properties --> Object Properties --> Transform`
   :Panel:     :menuselection:`3D Viewport --> Sidebar --> Transform`

The *Transform* panel in the Sidebar region allows you to view and
manually/numerically control the position, rotation, and other properties of an object, in *Object Mode*.
Each object stores its position, orientation, and scale values.
These may need to be manipulated numerically, reset, or applied.
In *Edit Mode*. It mainly allows you to enter precise coordinates for a vertex,
or median position for a group of vertices (including an edge/face). As each type of object has a different set of
options in its *Transform* panel in *Edit Mode*,
see their respective descriptions in the :doc:`Modeling chapter </modeling/index>`.

Use this panel to either edit or display the object's transform properties such as position,
rotation and/or scaling. These fields change the object's origin and then affect the aspect of
all its *vertices* and faces.

.. figure:: /images/scene-layout_object_properties_transforms_panel.png
   :align: center

   Transform Properties.

.. _bpy.types.Object.location:

Location
   The object's origin location in local coordinates.

.. _bpy.types.Object.rotation:

Rotation
   The object's local orientation, relative to the global axes and its own origin.

.. _bpy.types.Object.rotation_mode:

Rotation Mode
   Method for calculating rotations, additional information can be found
   in the :doc:`manual's appendix </advanced/appendices/rotations>`.

   :Euler:
      The gizmo handles are aligned to the :term:`Euler` axis,
      allowing you to see the discreet XYZ axis underlying the Euler rotation,
      as well as possible :term:`Gimbal Lock`.
   :Axis Angle:
      The X, Y, and Z coordinates define a point relative to the object origin.
      This point and the origin define an axis around the W value defines the rotation.
   :Quaternion:
      X, Y, Z and W correspond to the :term:`Quaternion` components.

.. _bpy.types.Object.scale:

Scale
   The object's relative scale along the local axis
   (e.g. the *Scale X* value represents the scale along the local X axis).
   Each object (cube, sphere, etc.), when created, has a scale of one unit in each local direction.
   To make the object bigger or smaller, you scale it in the desired axis.

.. _bpy.types.Object.dimensions:

Dimensions
   The size of the object's bounding box
   (aligned with the local axes -- think of a cardboard box just big enough to hold the object).

.. _bpy.types.Object.lock:

Transform Properties Locking
   When the toggle is locked, the corresponding transformation value
   can not be changed in any interactive operation.
   But the value can still be changed using non-interactive operations,
   like editing the corresponding number field or using Python.

   For example, if you locked the *Location X* property
   then you cannot use the 3D gizmo to move the object along the global X axis.
   But you can still move it using the *Location X* number field.
   Consider the locking feature as a rigid constraint only changeable from the panel.

   To lock a property, click the padlock icon next to the button.
   The button is unlocked if the icon shows an open padlock,
   and it is locked if the icon appears as a closed padlock.


.. _bpy.types.Object.delta:

Delta Transforms
================

.. reference::

   :Mode:      Object Mode
   :Panel:     :menuselection:`Properties --> Object Properties --> Transform --> Delta Transforms`

Delta Transforms are simply transformations that are applied on top of the transforms described above.
Delta Transforms are particularly useful in animations. For example,
you can animate an object with the primary transforms then move them around with Delta Transforms.


## Visibility


**********
Visibility
**********

.. reference::

   :Mode:      Object Mode
   :Panel:     :menuselection:`Properties --> Object Properties --> Visibility`

The Visibility panel controls how objects are interacted with in the viewport and in the final render.
These visibility options can also be set in the :doc:`Outliner </editors/outliner/editing>`.

.. _bpy.types.Object.hide_select:

Selectable
   The object is able to be selected in the 3D Viewport.

.. _bpy.types.Object.hide_viewport:
.. _bpy.types.Object.hide_render:

Show In
   Viewports
      The object will be displayed in the 3D Viewport.

   Renders
      The object is able to be in the final render, note that it will still be visible in rendered shading view.

.. seealso::

   Cycles has additional :ref:`Visibility properties <render-cycles-object-settings-visibility>`
   and also Grease Pencil objects have additional :ref:`Visibility properties <grease_pencil-object-visibility>`.

.. _bpy.types.Object.is_holdout:

Mask
   Holdout
      Render objects as a holdout or matte, creating a hole in the image with zero :term:`Alpha <Alpha Channel>`,
      to fill out in :doc:`compositing </compositing/index>` with real footage or another render.


## Collection


**********
Collection
**********

.. reference::

   :Mode:      Object Mode
   :Panel:     :menuselection:`Properties --> Object Properties --> Instancing --> Collection`

*Instance Collections* allows you to create an instance of a collection for each instance of another object.
Collections may contain animations, objects with physics simulations and even other nested collections.


Basic Usage
===========

Create a Collection:
   - Create a new collection (this can be done via the Outliner).
   - Link the objects that need to be instanced as part of the newly created collection.
Create a new Collection Instance:
   - :menuselection:`Add --> Collection Instance`

At this point, an instance of the collection and an :doc:`empty object </modeling/empties>` will appear.
You can duplicate the empty, and the *Instance Collections* settings will be preserved for each empty.
This way, you can get multiple copies of linked data very easily.


Collections and Dynamic Linking
===============================

See :doc:`Appending and Linking </files/linked_libraries/index>`
to understand how to dynamically link data from another blend-file into the current file.
You can dynamically link collections from one blend-file to another.
When you do so, the linked collection does not appear anywhere in your scene
until you create an object controlling where the collection instance appears.


Making an Instanced Collection Real
===================================

If you want to make further edits on an instanced collection select the *Instance Collection*.
Then call :ref:`bpy.ops.object.duplicates_make_real` to convert
the collection into regular objects that can be transformed and animated normally.

.. note::

   Note that if the instanced collection was linked from an external file, the Object Data
   (mesh, materials, textures, transforms) will also still be linked from the original collection.
   However, the various object's parent-child relationships do not carry over.


## Faces


*****
Faces
*****

.. reference::

   :Mode:      Object Mode
   :Panel:     :menuselection:`Properties --> Object Properties --> Instancing`

*Instancing Faces* is the capability to replicate an object on each face of a parent object.
One of the best ways to explain this is through an example illustration.

Scale
   Scales each instance according to the size of its corresponding face.

   Inherit Scale
      Scale the instance faces objects.

*Make Instance Face* tool converts linked objects (that share mesh data) into instanced faces.
This tool creates the parent object (instancer) with faces where the objects were,
then it uses *Instancing Faces* to put instances at the location of every created face.

You can go back from *Instancing Faces* to multiple linked objects using
:ref:`bpy.ops.object.duplicates_make_real`.

.. seealso:: Example blend-file

   Download the blend-file used for the examples on this page
   `here <https://archive.blender.org/wiki/2015/index.php/File:Manual-2.5-Duplifaces-Example01.blend>`__.


Basic Usage
===========

In this example we will use a UV sphere with an extruded "north pole" as our base object and
a cube as our parent mesh. To parent the sphere to the cube, in *Object Mode*,
first :kbd:`LMB` select the sphere, then :kbd:`Shift-LMB` select the cube
(order is very important here), and finally :kbd:`Ctrl-P` to parent.

.. list-table::

   * - .. figure:: /images/scene-layout_object_properties_instancing_faces_cube-before.png
          :width: 320px

          A cube and a sphere.

     - .. figure:: /images/scene-layout_object_properties_instancing_faces_cube-after.png
          :width: 320px

          Instancing Faces applied to the cube.

Next, in the :menuselection:`Properties --> Object Properties --> Instancing`,
select *Faces*. The sphere is instanced, one for each face of the cube.

.. note:: Inherited properties

   The location, orientation, and scale of the instanced child(ren) matches that of the faces of the parent.
   So, if several objects are parented to the cube, they will all be instanced once for each face on the cube.
   If the cube is subdivided, every child will be instanced for each face on the cube.

Both the parent object and original are displayed as editable "templates" in 3D Viewport,
but neither is rendered.


Scale
=====

.. list-table::

   * - .. figure:: /images/scene-layout_object_properties_instancing_faces_scale-enabled.png
          :width: 320px

          Scale enabled.

     - .. figure:: /images/scene-layout_object_properties_instancing_faces_scale-changed.png
          :width: 320px

          Top face of cube scaled down.

By enabling *Scale* for the parent object,
the scale of the child objects will be adapted to the size of each face in the parent object.

Thus, by rescaling the face of the parent object,
the size of the instanced object will change accordingly.


Limitations/Considerations
==========================

The positioning of the instanced geometry relative to the face is dependent upon the position
of the child objects relative to the instancer's origin. This can lead to some visual artifacts
in the 3D Viewport as the geometry of the original objects overlaps or intersects with
the instanced geometry.
One workaround is to move the origin of the instancer mesh off of the plane of the faces.

If the geometry of the children is not symmetrical then the orientation of the face
(as determined by the order of its vertices) could matter. As of 2.70 Blender does not have
tools which allow you to adjust the ordering of the vertices on a face.

However, there is a workflow that lets you control for this. Make a single square and
enable the *Instancing Faces* so you can see the instanced geometry in the 3D Viewport.
If the orientation is not what you want, rotate the face until it is how you want.
Typically you want to do the rotation in Edit Mode, not Object Mode,
but this is not a hard rule.

Once you have the orientation correct,
Duplicate the face and move the duplicate where you want it.
Repeat this process until you have enough faces.
Since it is common for these faces to butt up against one another,
your geometry will have lots of duplicate vertices.
Use the *Merge by Distance* button in the Tools panel.


.. rubric:: Demo Video

`A short video illustrating this workflow <https://www.youtube.com/watch?v=diI8xJ9oo_8>`__


## Index


##############
  Instancing
##############

.. note::

   Geometry nodes provides a more flexible way to instance objects, with the
   :doc:`/modeling/geometry_nodes/instances/instance_on_points`.

Vertices
   This creates an instance of all children of this object on each vertex
   (for mesh objects only).
Faces
   This creates an instance of all children of this object on each face
   (for mesh objects only).
Collection
   This creates an instance of the collection with the transformation of the object.
   Collection instancers can be animated using actions,
   or can get a :doc:`Proxy </files/linked_libraries/library_proxies>`.

.. toctree::
   :maxdepth: 2

   verts.rst
   faces.rst
   collection.rst


## Verts


********
Vertices
********

.. reference::

   :Mode:      Object Mode
   :Panel:     :menuselection:`Properties --> Object Properties --> Instancing`

*Instance Vertices* allows you to replicate child objects
at the location of every vertex of the parent object.

.. note::

   The relative :doc:`Object Origin </scene_layout/object/origin>` position
   of the parent and child objects determines offset instanced geometry from parent vertex.

Align to Vertex Normal
   Rotates all instanced objects according to the corresponding vertex normals of the parent mesh.

   To change the axis of direction of the instanced objects,
   select the child object and change the :ref:`Tracking Axis <bpy.types.Object.track_axis>`.

There are actually two approaches to modeling using instanced vertices.
They can be used as an arranging tool,
allowing you to model geometrical arrangements of objects (e.g. the columns of a Greek temple,
the trees in a garden, the desks in a classroom).
The object can be of any object type which Blender supports.
The second approach is to use them to model an object starting from a single part of it
(e.g. the spikes in a club, the thorns of a sea-urchin, the tiles in a wall, the petals in a flower).

.. note:: Download Example Blend-File

   You can download a file with the examples described on this page.
   In `this blend <https://archive.blender.org/wiki/2015/index.php/File:Manual-2.5-DupliVerts-Examples.blend>`__,
   the first example, a monkey parented to a circle is on layer 1;
   while a tentacle parented to an icosphere is on layer 2.


Usage
=====

Instanced Vertices as an Arranging Tool
---------------------------------------

All you need is a base object (e.g. the *tree* or the *column*)
and a pattern mesh with its vertices following the pattern you have in mind. In this section,
we will use a simple scene for the following part. We will be using a monkey head located at
the origin of the coordinate system as our base object and a circle at the same location as
our parent mesh.

.. list-table::

   * - .. figure:: /images/scene-layout_object_properties_instancing_verts_monkey-before.png
          :width: 320px

          A monkey head and a circle.

     - .. figure:: /images/scene-layout_object_properties_instancing_verts_monkey-after.png
          :width: 320px

          Instanced monkeys on Vertices.

First, in *Object Mode*, select the base object
and :kbd:`Shift-LMB` to add the circle to the selection (order is very important here),
and :kbd:`Ctrl-P` or :menuselection:`Object --> Parent --> Object`
to parent the base object to the circle.
Now, the circle is the parent of the monkey; if you move the circle, the monkey will follow it.

With only the circle selected, enable *Instancing Vertices*;
a monkey head should be placed at every vertex of the circle.

The original monkey head at the center and the parent mesh are still shown in the 3D Viewport but
neither will be rendered. If the placement and rotation of your monkey head are odd,
you might need to clear its rotation :kbd:`Alt-R`, scale :kbd:`Alt-S`,
location :kbd:`Alt-G`, and origin :menuselection:`Object --> Clear --> Origin`.


Rearranging
^^^^^^^^^^^

If you now select the base object and modify it in either Object or Edit Mode,
all changes will also affect the shape of all instanced objects.
You can also select the parent mesh to modify the arrangement of the instances;
adding vertices will also add more base objects.

Note that the base objects will inherit changes made to the parent mesh in Object Mode,
but not in Edit Mode. So scaling the circle up in Object Mode will enlarge the monkey head,
while scaling the circle up in Edit Mode will only increase the distance between the base objects.


Orientation
^^^^^^^^^^^

The orientation of the base objects can be controlled by
enabling *Align to Vertex Normal* in the *Instancing* panel.
This will rotate all base objects according to the vertex normals of the parent mesh.

To change the orientation of the instanced objects,
select the base object and change the :ref:`Tracking Axis <bpy.types.Object.track_axis>`.

.. list-table:: Output of various orientations.

   * - .. figure:: /images/scene-layout_object_properties_instancing_verts_orientation.png
          :width: 320px

          Orientation enabled, orientation +Y.

     - .. figure:: /images/scene-layout_object_properties_instancing_verts_negy.png
          :width: 320px

          Negative Y.

   * - .. figure:: /images/scene-layout_object_properties_instancing_verts_posx.png
          :width: 320px

          Positive X.

     - .. figure:: /images/scene-layout_object_properties_instancing_verts_posz.png
          :width: 320px

          Positive Z, up X.

.. note::

   The axes of an object can be made visible in
   the :menuselection:`Properties --> Object Properties --> Viewport Display` panel.
   To display the vertex normals of the parent mesh,
   enter *Edit Mode* and enable this visualization in
   the :menuselection:`Display & Shading --> Viewport Overlays --> Normals`
   where you can also resize the displayed normals as necessary.


Instanced Vertices as a Modeling Tool
-------------------------------------

Very interesting models can be made using *Instancing Vertices* and a standard primitive.
In this example, a simple tentacle was made by extruding a cube a couple of times.
The tentacle object was then parented to an icosphere.
With *Align to Vertex Normal* enabled for the parent mesh (the icosphere),
the orientation of the base object (the tentacle)
was adapted to the vertex normals of the parent mesh
(in this case the tentacle was rotated -90° about the X axis in Edit Mode).

.. list-table::

   * - .. figure:: /images/scene-layout_object_properties_instancing_verts_tentacle.png

          A simple tentacle set to smooth.

     - .. figure:: /images/scene-layout_object_properties_instancing_verts_norot.png

          Tentacles instanced onto the parent mesh.

     - .. figure:: /images/scene-layout_object_properties_instancing_verts_rot.png

          *Align to Vertex Normal* enabled to align instanced geometry.

As in the previous example, the shape and proportions of the arrangement can now be tweaked.

To turn all instanced geometry into real objects,
select the icosphere and :ref:`bpy.ops.object.duplicates_make_real`.
To make the icosphere and the tentacle a single object,
make sure they are all selected and go to :menuselection:`Object --> Join`, :kbd:`Ctrl-J`.

.. seealso::

   Other duplication methods are listed :doc:`here </scene_layout/object/editing/duplicate>`.


## Index


#########
  Tools
#########

.. toctree::
   :maxdepth: 2

   toolbar.rst
   tool_settings.rst


Types
=====

.. toctree::
   :maxdepth: 1

   scale_cage.rst


## Scale Cage

.. _tool-scale-cage:

**********
Scale Cage
**********

.. reference::

   :Mode:      Object and Edit Modes
   :Tool:      :menuselection:`Toolbar --> Scale --> Scale Cage`

The *Scale Cage* tool is a bounding box around the object(s) which scales objects from a particular point or axis.
The tool works by selecting a scale point and dragging inwards or outwards to adjust the scale accordingly.
The origin for the scale will be from the point on the cube directly opposite from the point selected.
Selecting points on the faces of the cube scales along one axis,
selecting points on the edges of the cube scales along two axes,
and selecting points on the vertices of the cube scales along all three axes.

.. figure:: /images/scene-layout_object_tools_scale-cage_example.png
   :align: center

   Scale Cage tool.


Tool Settings
=============

Orientation
   Aligns the transformation axes to a specified orientation constraint.
   See :doc:`Transform Orientations </editors/3dview/controls/orientation>` for more information.


Options
=======

Scale X, Y, Z
   The amount to resize the selection on their respected axis.

Orientation
   Aligns the transformation axes to a specified orientation constraint.
   See :doc:`Transform Orientations </editors/3dview/controls/orientation>` for more information.

Proportional Editing
   The extruded face will affect nearby geometry.
   See :doc:`Proportional Editing </editors/3dview/controls/proportional_editing>` for a full reference.


## Toolbar


*******
Toolbar
*******

:ref:`Tweak <tool-select-tweak>`
   Select or move.

   :ref:`Select Box <tool-select-box>`
      Select objects by dragging a box.
      All objects that intersect the box will be selected.
   :ref:`Select Circle <tool-select-circle>`
      Select objects by dragging a circle. All objects that intersect the path of
      the circle will be selected.
   :ref:`Select Lasso <tool-select-lasso>`
      Select objects by drawing a lasso.

Cursor
   Change the location of the 3D Cursor.

Move
   Translation tool.

Rotate
   Rotation tool.

Scale
   Scale tool.

   :ref:`Scale Cage <tool-scale-cage>`
      Change the scale of an object by controlling its cage.

Transform
   Tool to adjust the objects translation, rotations and scale.

:ref:`Annotate <tool-annotate-freehand>`
   Draw free-hand annotation.

   :ref:`Annotate Line <tool-annotate-line>`
      Draw straight line annotation.
   :ref:`Annotate Polygon <tool-annotate-polygon>`
      Draw a polygon annotation.
   :ref:`Annotate Eraser <tool-annotate-eraser>`
      Erase previous drawn annotations.

:ref:`Measure <tool-measure>`
   Measure distances in the scene.

:ref:`Add Cube <tool-add-cube>`
   Interactively add a cube mesh object.

   :ref:`Add Cone <tool-add-cone>`
      Interactively add a cone mesh object.
   :ref:`Add Cylinder <tool-add-cylinder>`
      Interactively add a cylinder mesh object.
   :ref:`Add UV Sphere <tool-add-uvsphere>`
      Interactively add a UV sphere mesh object.
   :ref:`Add Icosphere <tool-add-icosphere>`
      Interactively add an icosphere mesh object.


## Tool Settings


*************
Tool Settings
*************

Options
=======

.. reference::

   :Mode:      Object Mode and Pose Mode
   :Header:    :menuselection:`Sidebar --> Tool --> Options`


Transform
---------

.. _bpy.types.ToolSettings.use_transform_data_origin:
.. _bpy.types.ToolSettings.use_transform_pivot_point_align:

Affect Only
   Origins :kbd:`Ctrl-Period`
      Directly transforms the object's :doc:`origin </scene_layout/object/origin>`.
      This only works for objects with data which can be transformed;
      i.e. it will not work on object lights.

      When enabled, the object axes are displayed.

      Take care using this option since it transforms the object-data which may cause linked
      duplicates to be moved unintentionally.

      .. hint::

         Changing the object location and the object-data may impact
         modifiers, constraints and keyframe animation.

         If you are only temporarily setting the pivot point,
         use the :ref:`3D cursor <editors-3dview-3d_cursor>` instead.

   Locations
      Changes the position of the object's origin relative to another point during transformation.
      In other words, the pivot point and the origin cannot share the same location.
      This will not affect the object local transforms, just its position in world space.

      In the examples below, a comparison of the scaling and rotation of objects,
      when *Location* is enabled (middle) and disabled (right).

      .. figure:: /images/scene-layout_object_tools_tool-settings_rotate.png

         Rotation example.

      .. figure:: /images/scene-layout_object_tools_tool-settings_scale.png

         Scaling example.

   Parents
      Transforms :doc:`Parent Objects </scene_layout/object/editing/parent>`
      while leaving their children objects unaffected.


## Index

.. _bpy.types.Scene:
.. _bpy.ops.scene:

##########
  Scenes
##########

.. toctree::
   :maxdepth: 2

   introduction.rst
   properties.rst


## Introduction


************
Introduction
************

Scenes are a way to organize your work.
Each blend-file can contain multiple scenes, which share other data such as objects and materials.

Scene management and library appending/linking are based on Blender's
:doc:`Library and Data System </files/index>`,
so it is a good idea to read that manual page first,
if you are not familiar with the basics of that system.


Controls
========

.. reference::

   :Menu:      :menuselection:`Topbar --> Scene`

You can select and create scenes with the *Scene* data-block menu
in the :doc:`Topbar </interface/window_system/topbar>`.

.. figure:: /images/scene-layout_scene_introduction_menu.png
   :align: right

   Scene data-block menu.

Scenes
   A list of available scenes.
Add
   New
      Creates an empty scene with default values.
   Copy Settings
      Creates an empty scene, but also copies
      the settings from the active scene into the new one.
   Linked Copy
      This option creates a new scene with the same settings and contents as the active scene.
      However, instead of copying the objects,
      the new scene contains links to the collections in the old scene.
      Therefore, changes to objects in the new scene will result in the same
      changes to the original scene, because the objects used are literally the same.
      The reverse is also true.
   Full Copy
      Using this option, nothing is shared.
      This option creates a fully independent scene with copies of the active scene's contents.
      Every object in the original scene is duplicated, and a duplicate,
      private copy of its object-data is made as well.

   .. note::

      To choose between these options,
      it is useful to understand the difference between *Object* and *Object Data*.
      The choices for adding a scene, therefore, determine just how much of this information will be
      *copied from* the active scene to the new one, and how much will be *shared* (linked).

Delete ``X``
   You can delete the current scene by clicking the *X*
   next to the name in the :doc:`Topbar </interface/window_system/topbar>`.

.. seealso:: Linking to a Scene

   You can :ref:`link <bpy.ops.object.make_links_scene>` any object from one scene to another.


## Properties


****************
Scene Properties
****************

Scene
=====

.. reference::

   :Panel:     :menuselection:`Properties --> Scene --> Scene`

.. _bpy.types.Scene.camera:

Camera
   Used to select which camera is used as the active camera.
   You can also set the active camera in the 3D Viewport with :kbd:`Ctrl-Numpad0`.

.. _bpy.types.Scene.background_set:

Background Scene
   Allows you to use a scene as a background,
   this is typically useful when you want to focus on animating the foreground for example,
   without background elements getting in the way.

   This scene can have its own animation, physics simulations, etc,
   but you will have to select it from the *Scene* data-block menu, if you want to edit any of its contents.

   Background Scenes can themselves have a Background Scene (they're recursively included).
   So you can always make additions to existing scenes by using them as a background
   to a newly created scene where your additions are made.

   .. tip::

      This can also be used in combination with :ref:`Linking to a Scene <bpy.ops.object.make_links_scene>`,
      where one blend-file contains the environment, which can be reused in many places.

.. _bpy.types.Scene.active_clip:

Active Clip
   Selects a :doc:`Movie Clip </movie_clip/index>` that can be used by
   :ref:`constraints-motion-tracking` Constraints or a camera's :ref:`bpy.types.CameraBackgroundImage`.


.. _bpy.types.UnitSettings:

Units
=====

.. reference::

   :Panel:     :menuselection:`Properties --> Scene --> Units`

.. _bpy.types.UnitSettings.system:

Unit System
   The unit system to use for user interface controls.

   :None:
      Use units that have with no relation to the real world,
      practically this is the same as *Metric* just without unit names.
   :Metric: Use the metric unit system in this scene.
   :Imperial: Use the imperial unit system in this scene.

.. _bpy.types.UnitSettings.scale_length:

Unit Scale
   Scale factor to use when converting between internal units and values displayed in the user interface.
   This can be changed when modeling at microscopic or astronomical scales.

   .. note::

      This only influences the values displayed in the user interface
      and not how things behave internally. For example, physics simulations
      don't take the unit scale into account.

.. _bpy.types.UnitSettings.use_separate:

Separate Units
   When using *Metric* or *Imperial*, display properties as multiple values.
   For example, ``2.285m`` will become ``2m 28.5cm``.

.. _bpy.types.UnitSettings.system_rotation:

Rotation
   Unit to use for displaying/editing rotation values.

   :Degrees: Use degrees for angles in the user interface.
   :Radians: Use radians for angles in the user interface.

.. _bpy.types.UnitSettings.length_unit:

Length
   Unit that will be used to display length values.

   :Adaptive:
      The unit used for a specific value depends on the magnitude of the value.
      For example, some values might be displayed as ``23cm`` while others are
      displayed as ``10km``.
   :Meters/Centimeters/Feet:
      A fixed unit that will be used for all lengths in the user interface.

.. _bpy.types.UnitSettings.mass_unit:

Mass
   See *Length*.

.. _bpy.types.UnitSettings.time_unit:

Time
   See *Length*.

.. _bpy.types.UnitSettings.temperature_unit:

Temperature
   See *Length*.

.. Normally we would avoid documenting long lists of values
   however, this is not displayed anywhere else.

.. list-table:: Imperial Length Units
   :header-rows: 1
   :stub-columns: 1

   * - Full Name
     - Short Name(s)
     - Scale of a Meter
   * - thou
     - ``mil``
     - 0.0000254
   * - inch
     - ``"``, ``in``
     - 0.0254
   * - foot, feet
     - ``'``, ``ft``
     - 0.3048
   * - yard
     - ``yd``
     - 0.9144
   * - chain
     - ``ch``
     - 20.1168
   * - furlong
     - ``fur``
     - 201.168
   * - mile
     - ``mi``, ``m``
     - 1609.344

.. list-table:: Metric Length Units
   :header-rows: 1
   :stub-columns: 1

   * - Full Name
     - Short Name(s)
     - Scale of a Meter
   * - micrometer
     - ``um``
     - 0.000001
   * - millimeter
     - ``mm``
     - 0.001
   * - centimeter
     - ``cm``
     - 0.01
   * - decimeter
     - ``dm``
     - 0.1
   * - meter
     - ``m``
     - 1.0
   * - dekameter
     - ``dam``
     - 10.0
   * - hectometer
     - ``hm``
     - 100.0
   * - kilometer
     - ``km``
     - 1000.0


Gravity
=======

.. reference::

   :Panel:     :menuselection:`Properties --> Scene --> Gravity`

Options to control global gravity used for physics effects.

See the :doc:`Physics chapter </physics/forces/gravity>` for more information.


Simulation
==========

.. _bpy.types.Scene.use_custom_simulation_range:

Simulation Range
   Use a simulation range that is different from the scene range for
   :doc:`Simulation Nodes </modeling/geometry_nodes/simulation/simulation_zone>`
   that do not override the frame range themselves.

Start, End
   The frame at which the simulation starts/ends.


Keying Sets
===========

.. reference::

   :Panel:     :menuselection:`Properties --> Scene --> Keying Sets`

See :doc:`/animation/keyframes/keying_sets`.


.. _data-scenes-audio:

Audio
=====

.. reference::

   :Panel:     :menuselection:`Properties --> Scene --> Audio`

Options to control global audio settings.
To control how sounds is played back from within Blender, see the audio settings
in the :ref:`Preferences <prefs-system-sound>`.

.. _bpy.types.Scene.audio_volume:

Volume
   Volume for the scene.

.. _bpy.types.Scene.audio_distance_model:

Distance Model
   Changes how the sound attenuation is calculated based on the distance.
   Most physically correct is the *Inverse* model,
   but it's also possible to choose a linear and an exponential falloff.
   The clamped modes limit the volume to be lower than 100% (1.0),
   that means if the distance is smaller than the reference distance, the volume is always 100%.
   For an exact description of each option
   see the `OpenAL documentation <https://www.openal.org/documentation/>`__.

.. _bpy.types.Scene.audio_doppler_speed:

Doppler Speed
   Speed of the sound for the Doppler effect calculations.
   The typical value is 343.3 m/s in air, in water for example this value is around 1560 m/s.

.. _bpy.types.Scene.audio_doppler_factor:

Doppler Factor
   Controls how strong the Doppler effect is.
   You can exaggerate or attenuate the change of pitch, but physically correct is a factor of 1.0.

.. _bpy.ops.sound.bake_animation:

Update Animation Cache
   Updates the audio animation cache. This is useful if you start noticing artifact in the audio.


Rigid Body World
================

.. reference::

   :Panel:     :menuselection:`Properties --> Scene --> Rigid Body World`

The *Rigid Body World* is a group of rigid body objects,
which holds settings that apply to all rigid bodies in this simulation.

See :doc:`Rigid Body World </physics/rigid_body/world>` for more information.


## Index


###############
  View Layers
###############

.. toctree::
   :maxdepth: 2

   introduction.rst


## Introduction


************
Introduction
************

The visibility controls are part of *view layers*, designed to help organizing
what you want to see or work on.

.. figure:: /images/scene-layout_view-layers_introduction_collections.png

   View layers and collections.

View layers reference to :doc:`collections </scene_layout/collections/introduction>`,
and allow to set their visibility, selectability and other options.
A *view layer* can have any collection enabled, and multiple *view layers*
can use the same or different collections.

.. seealso::

   Each view layer can be rendered separately as individual :doc:`Render Layers </render/layers/introduction>`
   to help composite your scene.


Outliner
========

You can edit the *view layer* collections in the :ref:`Outliner <editors-outliner-editing-collections>`.

.. figure:: /images/scene-layout_view-layers_introduction_outliner.png

   View layer and collections in the Outliner.

There you can enable and disable collections, hide them temporarily, globally, among other options.

.. seealso::

   Read more about :ref:`Collections in the Outliner <editors-outliner-editing-collections>`.


