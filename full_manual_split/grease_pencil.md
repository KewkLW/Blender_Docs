# Index for grease_pencil

- [Index](#Index)
- [Introduction](#Introduction)
- [Multiframe](#Multiframe)
- [Object](#Object)
- [Primitives](#Primitives)
- [Selecting](#Selecting)
- [Structure](#Structure)
- [Index](#Index)
- [Interpolation](#Interpolation)
- [Introduction](#Introduction)
- [Tools](#Tools)
- [Index](#Index)
- [Introduction](#Introduction)
- [Properties](#Properties)
- [Drawing Planes](#Drawing-Planes)
- [Guides](#Guides)
- [Index](#Index)
- [Introduction](#Introduction)
- [Stroke Placement](#Stroke-Placement)
- [Tools](#Tools)
- [Arc](#Arc)
- [Box](#Box)
- [Circle](#Circle)
- [Curve](#Curve)
- [Cutter](#Cutter)
- [Draw](#Draw)
- [Erase](#Erase)
- [Eyedropper](#Eyedropper)
- [Fill](#Fill)
- [Index](#Index)
- [Interpolate](#Interpolate)
- [Line](#Line)
- [Polyline](#Polyline)
- [Tint](#Tint)
- [Brushes](#Brushes)
- [Brush Settings](#Brush-Settings)
- [Color](#Color)
- [Index](#Index)
- [Curve Editing](#Curve-Editing)
- [Grease Pencil Menu](#Grease-Pencil-Menu)
- [Index](#Index)
- [Introduction](#Introduction)
- [Point Menu](#Point-Menu)
- [Stroke Menu](#Stroke-Menu)
- [Tools](#Tools)
- [Convert To Geometry](#Convert-To-Geometry)
- [Index](#Index)
- [Trace Image](#Trace-Image)
- [Index](#Index)
- [Introduction](#Introduction)
- [Tools](#Tools)
- [Brush](#Brush)
- [Editing](#Editing)
- [Index](#Index)
- [Introduction](#Introduction)
- [Tools](#Tools)
- [Brush](#Brush)
- [Index](#Index)
- [Introduction](#Introduction)
- [Tools](#Tools)
- [Weights Menu](#Weights-Menu)
- [Brush](#Brush)
- [Index](#Index)
- [Options](#Options)
- [Index](#Index)
- [Introduction](#Introduction)
- [Hue Saturation](#Hue-Saturation)
- [Index](#Index)
- [Opacity](#Opacity)
- [Tint](#Tint)
- [Armature](#Armature)
- [Hook](#Hook)
- [Index](#Index)
- [Lattice](#Lattice)
- [Noise](#Noise)
- [Offset](#Offset)
- [Shrinkwrap](#Shrinkwrap)
- [Smooth](#Smooth)
- [Thickness](#Thickness)
- [Array](#Array)
- [Build](#Build)
- [Dash](#Dash)
- [Envelope](#Envelope)
- [Index](#Index)
- [Length](#Length)
- [Line Art](#Line-Art)
- [Mirror](#Mirror)
- [Multiple Strokes](#Multiple-Strokes)
- [Outline](#Outline)
- [Simplify](#Simplify)
- [Subdivide](#Subdivide)
- [Index](#Index)
- [Texture Mapping](#Texture-Mapping)
- [Time Offset](#Time-Offset)
- [Weight Angle](#Weight-Angle)
- [Weight Proximity](#Weight-Proximity)
- [Data](#Data)
- [Display](#Display)
- [Index](#Index)
- [Layers](#Layers)
- [Masks](#Masks)
- [Onion Skinning](#Onion-Skinning)
- [Strokes](#Strokes)
- [Blur](#Blur)
- [Colorize](#Colorize)
- [Flip](#Flip)
- [Glow](#Glow)
- [Index](#Index)
- [Introduction](#Introduction)
- [Pixelate](#Pixelate)
- [Rim](#Rim)
- [Shadow](#Shadow)
- [Swirl](#Swirl)
- [Wave Distortion](#Wave-Distortion)


## Index

.. _grease_pencil-index:
.. _bpy.ops.gpencil:
.. _bpy.ops.object.gpencil:

#################
  Grease Pencil
#################

.. toctree::
   :maxdepth: 2

   introduction.rst
   object.rst
   structure.rst
   primitives.rst
   selecting.rst
   multiframe.rst
   properties/index.rst
   modifiers/index.rst
   visual_effects/index.rst
   materials/index.rst
   animation/index.rst


Modes
=====

.. toctree::
   :maxdepth: 2

   modes/draw/index.rst
   modes/sculpting/index.rst
   modes/edit/index.rst
   modes/vertex_paint/index.rst
   modes/weight_paint/index.rst
   modes/object/index.rst


## Introduction


************
Introduction
************

Grease Pencil is a Blender object. It accepts the drawing information
from a mouse or pressure-sensitive stylus and places it in 3D space
as a collection of points, which are defined as a stroke.

The Grease Pencil object can be used to make traditional 2D animation, cut-out animation,
motion graphics or used it as storyboard tool among other things.

.. figure:: /images/grease-pencil_introduction_example.png

   An illustration in 3D space using the Grease Pencil object.

Strokes are created in :doc:`Draw Mode </grease_pencil/modes/draw/introduction>`,
which requires a new :doc:`keyframe <../animation/keyframes/editing>`
in the animation timeline for the Grease Pencil object.
Existing strokes can then be adjusted in :doc:`Edit Mode </grease_pencil/modes/edit/introduction>`
and :doc:`Sculpt Mode </grease_pencil/modes/sculpting/introduction>`.
Finally, artists can apply materials, modifiers, lighting, and visual effects to strokes.


Quick Start
===========

Artists can add Grease Pencil to any existing Blender scene, or start with a 2D Animation template.
The template offers some pre-configured options that are helpful for animation and storyboarding.


Create and Use Grease Pencil
----------------------------

#. From :doc:`Object Mode <../scene_layout/object/introduction>`, :menuselection:`Add --> Grease Pencil --> Blank`.
#. Create a new keyframe or turn on Auto Key. (See :doc:`Keyframe Editing <../animation/keyframes/editing>`)
#. Switch to :doc:`Draw Mode <./modes/draw/introduction>`.
#. Click and drag across the viewport to add strokes to the Grease Pencil object.


2D Animation Template
---------------------

To create a new Blender file using the "2D Animation"
project template use: :menuselection:`File --> New --> 2D Animation`.

Note the following pre-configured setup for the 2D Animation template:

* 2D Animation is the default active workspace.
* :menuselection:`World Properties --> Surface (Background) --> Color` is set to white.
* :menuselection:`Render Properties --> Color Management` is set to Standard.
* The :doc:`drawing plane <./modes/draw/drawing_planes>` is set to Front (X-Z).
* Line and Fill layers, along with some stroke materials, are configured for Grease Pencil.
* The animation timeline will automatically create a new keyframe when Grease Pencil is used on empty frames.

.. tip::

   Grease Pencil can read pressure-sensitivity information from a
   :ref:`Graphics Tablet <hardware-tablet>` or stylus.


## Multiframe

.. _bpy.types.GreasePencil.use_multiedit:
.. _bpy.types.GPencilSculptSettings.use_multiframe_falloff:

**********
Multiframe
**********

Multiframe allows you to draw, edit, sculpt, or weight painting on several frames at the same time.
Extremely useful to avoid repeating a task one frame at a time when animating.

.. figure:: /images/grease-pencil_multiframe_panel.png

   Multiframe panel.


Usage
=====

#. Select the desired keyframes to draw, edit or sculpt at the same time.
#. Activate the Multiframe tool in the 3D Viewport's header with the toggle button (faded lines icon).
#. Once activated you can:

   - Select the points in all the selected keyframes and make your editions.
   - Start sculpting. The sculpt brushes will affects all the strokes in the selected keyframes.
   - Start weight painting. The weight paint brush will affect all the strokes in the selected keyframes.
   - Start Drawing. The new strokes will be added in all the selected keyframes.
     If you are using the Fill tool then it will be applied in all the selected keyframes.
   - When interpolating you can select the stroke from the different frames in the right order.
     Interpolate tool will use the selection order to calculate the correct stroke pairs.

Use Falloff
   When enabled, the effects on the strokes start to falloff from the current frame
   as defined by a :doc:`curve widget </interface/controls/templates/curve>`.

.. note::

   Not all operators support Multiframe mode.


## Object


******
Object
******

.. _grease_pencil-object-visibility:

Visibility
==========

.. reference::

   :Panel:     :menuselection:`Object Properties --> Visibility`

.. seealso::

   There are several other :doc:`general visibility </scene_layout/object/properties/visibility>` properties.


Use Light
---------

Enables the Grease Pencil object to be affected by lights.

This property affect the whole object, for more control with lights you can enable or disable
the use of lights by layers. See :doc:`Layers </grease_pencil/properties/layers>` for more information.

.. figure:: /images/grease-pencil_object_use-light.png

   Lights disabled (left) and enabled (right).


## Primitives

.. _bpy.ops.object.gpencil_add:

**********
Primitives
**********

.. reference::

   :Mode:      Object Mode and Edit Mode
   :Menu:      :menuselection:`Add --> Grease Pencil`
   :Shortcut:  :kbd:`Shift-A`

In Object Mode, the *Add* menu provides three different Grease Pencil primitives
with preset materials and 2D layers:

.. figure:: /images/grease-pencil_primitives_all.png

   Grease Pencil primitives.


Blank
=====

Adds a Grease Pencil object without any stroke.


Stroke
======

Adds a Grease Pencil object with a simple stroke as a reference.


Monkey
======

It creates a 2D monkey head. The Monkey's name is "Suzanne" and is Blender's mascot.
2D Suzanne is very useful as a standard test.


Scene Line Art
==============

Sets up a :doc:`/grease_pencil/modifiers/generate/line_art` for the active scene
by creating an "empty" Grease Pencil object with a Line Art modifier referencing each object in the scene.


Collection Line Art
===================

Sets up a :doc:`/grease_pencil/modifiers/generate/line_art` for the active collection
by creating an "empty" Grease Pencil object with a Line Art modifier referencing each object in the collection.


Object Line Art
===============

Sets up a :doc:`/grease_pencil/modifiers/generate/line_art` for the active object
by creating an "empty" Grease Pencil object with a Line Art modifier referencing the active object.


## Selecting

.. _bpy.types.ToolSettings.gpencil_selectmode:
.. _bpy.ops.gpencil.select:
.. _bpy.ops.gpencil.selectmode_toggle:

*********
Selecting
*********

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`3D Viewport Header --> Select Mode`
   :Shortcut:  :kbd:`1`, :kbd:`2`, :kbd:`3`

.. figure:: /images/grease-pencil_selecting_mode-buttons.png
   :align: right

   Edit Mode selection buttons.

In Edit Mode there are three different selection modes.
You can enter the different modes by selecting one of the three buttons in the header.

Points
   To select individual points.

Strokes
   To select an entire stroke.

Points in Between
   To select all points that are between other strokes.

.. figure:: /images/grease-pencil_selecting_example.png

   Points, stroke and in between stroke selection sample.


Select Menu
===========

Box/Circle/All/None/Invert Select
   All these options have the same meaning and behavior as in
   :doc:`Object Mode </scene_layout/object/selecting>`.


.. _bpy.ops.gpencil.select_random:

Select Random
=============

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Select --> Select Random`

Randomly selects unselected points or strokes.

Ratio
   The likelihood of an unselected elements being selected.
   Note that, this is not the percentage amount of elements that will be selected.
Random Seed
   :term:`Seed` used by the pseudo-random number generator.
Action
   Selection or deselection of elements.
Unselect Ends
   Excludes the selection of stroke end points.


.. _bpy.ops.gpencil.select_alternate:

Select Alternated
=================

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Select --> Select Alternated`

Selects alternate points in the selected strokes.


.. _bpy.ops.gpencil.select_more:
.. _bpy.ops.gpencil.select_less:

Select More/Less
================

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Select --> More/Less`
   :Shortcut:  :kbd:`Ctrl-NumpadPlus`, :kbd:`Ctrl-NumpadMinus`

The purpose of these tools is to reduce or enlarge the current selection within a stroke
(i.e. they will never "go outside" of a stroke or "jump" to another stroke in the same object).

More
   For each selected point, select *all* its linked points (i.e. one or two...).
Less
   For each selected point, if *all* points linked to this point are selected, keep this one selected.
   Otherwise, deselect it.

.. hint::

   When *all* points of a stroke are selected, nothing will happen
   (as for *Less*, all linked points are always selected, and of course, *More* cannot add any).
   Conversely, the same goes when no points are selected.


.. _bpy.ops.gpencil.select_grouped:

Select Grouped
==============

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Select --> Select Grouped`
   :Shortcut:  :kbd:`Shift-G`

Layer
   Selects all the points/strokes on the same layer.
Material
   Selects all the points/strokes that share the same material.


.. _bpy.ops.gpencil.select_linked:

Select Linked
=============

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Select --> Select Linked`
   :Shortcut:  :kbd:`L`, :kbd:`Ctrl-L`

:kbd:`L` (or :kbd:`Ctrl-L` for all) will add to the selection the cursor's nearest control point,
and all the linked ones, i.e. all points belonging to the same stroke.


.. _bpy.ops.gpencil.select_first:
.. _bpy.ops.gpencil.select_last:

Select First/Last
=================

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Select --> First/Last`

These operators will toggle the selection of the first or last point(s) of the stroke(s) in the object.
This is useful to quickly find the start of a stroke.


.. _bpy.ops.gpencil.select_vertex_color:

Select Color Attribute
======================

.. reference::

   :Mode:      Vertex Paint Mode

Selects all points with a similar Color Attribute as the current selection.

Tolerance
   How similar colors are allowed to be; higher values select a wider range of colors.


## Structure


*********
Structure
*********

Grease Pencil object has three main basic components: *points*, *edit lines* and *strokes*.

.. figure:: /images/grease-pencil_structure_example.png

   Example of Grease Pencil structure.


Points
======

The main element used in editing Grease Pencil objects are points.
Points represent a single point in 3D space.

Each point stores all the properties that define the final appearance of the strokes
as its location, thickness, alpha, weight and UV rotation for textures.

.. note::

   Point (Grease Pencil) and Vertex (meshes) are equivalent names.


Edit Lines
==========

Points are always connected by a straight line,
which you see when you are editing in Edit Mode or when you look at a stroke in wireframe view.
They are invisible on the rendered image and are used to construct the final stroke.


Strokes
=======

The stroke is the rendered image of the points and edit lines,
using a particular :doc:`Grease Pencil material </grease_pencil/materials/introduction>`.
(Grease Pencil materials are linked at stroke level.)


## Index


#############
  Animation
#############

.. toctree::
   :maxdepth: 2

   introduction.rst
   interpolation.rst
   tools.rst


## Interpolation


*************
Interpolation
*************

Interpolate
===========

.. reference::

   :Mode:      Draw and Edit Modes
   :Tool:      :menuselection:`Toolbar --> Interpolate`
   :Shortcut:  :kbd:`Ctrl-E`

When you are animating simple shapes you can use the interpolate tool
to automatically add new breakdown keyframes.

See :ref:`Interpolate tool <tool-grease-pencil-draw-interpolate>` for more details.


Interpolate Sequence
====================

.. reference::

   :Mode:      Draw and Edit Modes
   :Menu:      :menuselection:`Header --> Interpolate`
   :Shortcut:  :kbd:`Shift-Ctrl-E`

Interpolate strokes between the previous and next keyframe by adding *multiple* keyframes.
When you are on a frame between two keyframes and click the sequence button
a breakdown keyframe will be added on every frame between the previous and next keyframe.

Step
   The number of frames between generated interpolated frames.
Layer
   Restrict the interpolation to Active or All layers.
Only Selected :guilabel:`Edit Mode`
   When enabled, only selected strokes will be interpolated.
Exclude Breakdowns
   Exclude existing :ref:`Breakdowns keyframes <keyframe-type>` as interpolation extremes.
Flip Mode
   Invert strokes start and end. Automatic will try to found the right mode for every stroke.
Smooth
   Amount of smoothing to apply to interpolated strokes for reducing jitter/noise.
Iterations
   Number of time to smooth newly created strokes.
Type
   Interpolation method to use for the sequence.


## Introduction


************
Introduction
************

Animating with Grease Pencil
============================

The main goal of Grease Pencil is to offer a 2D animation tool full immersed in a 3D environment.

.. figure:: /images/grease-pencil_animation_introduction_example.png

   Sample animation showing Grease Pencil object keyframes in the Dope Sheet with onion skinning enabled.

In Blender, Grease Pencil objects can be animated in many ways:

Moving as a whole object
   Changing their position, orientation or size in time;

Drawing frame by frame
   Drawing one frame at a time (traditional animation).

Deforming them
   Animating their points;

Inherited animation
   Causing the object to move based on the movement of another object
   (e.g. its parent, hook, armature, etc.). Useful for cut-out animation for example.

For a complete overview of animation in Blender please refer to
the :doc:`Animation & Rigging </animation/index>` chapter.


2D Traditional Animation
========================

Keyframes
---------

Traditional animation in Grease Pencil is achieved with the use of
:doc:`keyframes </animation/keyframes/introduction>`
that hold the strokes information at a particular frame or frame range.

With :ref:`Auto keyframe <bpy.types.ToolSettings.use_keyframe_insert_auto>` activated,
every time you create a stroke in Grease Pencil object Draw Mode
a new keyframe is added at the current frame on the active channel.
With Auto keyframe deactivated, you will have to add manually
a new keyframe or your new strokes will be added on the active keyframe.

See :doc:`Keyframe Editing </animation/keyframes/editing>` for more information.

.. note::

   The channels in the Dope Sheet correspond to the active 2D layer of the Grease Pencil object.

Grease Pencil has its own mode in the Dope Sheet to work with keyframes.
See Grease Pencil mode in the :doc:`Dope Sheet </editors/dope_sheet/modes/grease_pencil>`
section for more information.
There are also several tools on the Stroke menu to work with keyframes and strokes.
See :doc:`Animation tools </grease_pencil/animation/tools>` for more information.


Onion Skinning
--------------

One key element in traditional animation is the use of onion skinning.
Grease Pencil offer a lot of flexibility and options for this tool.
See :doc:`Onion Skinning </grease_pencil/properties/onion_skinning>` for more information.


Animation Options
=================

Draw Mode
---------

In Draw Mode there are three options related to the animation workflow that you can use.

.. figure:: /images/grease-pencil_animation_introduction_drawing-options.png

   General drawing/animation options.

Add Weight Data
   When enabled, new strokes weight data is added according to the current vertex group and weights.
   If there is no vertex group selected, no weight data is added.

   This is useful for example in cut-out animation for adding new drawing
   on the same vertex group without the need to creating it afterwards.

   See :doc:`Weight Paint Mode </grease_pencil/modes/weight_paint/introduction>` for more information.

Additive Drawing
   When creating new frames, the strokes from the previous/active frame are include as a basis for the new one.

Multiframe
   If you need to add new strokes to your animation on several frames you can use multiframe drawing.

   You can activate multiframe drawing with the Multiframe button next to the modes selector (faded lines icon).
   See :doc:`Multiframe </grease_pencil/multiframe>` for more information.


Edit Mode
---------

In Edit Mode there is an option related to the animation workflow that you can use.

.. figure:: /images/grease-pencil_animation_introduction_edit-options.png

   Multiframe edition.

Multiframe
   Sometimes you may need to modify several frames at the same time with edit tools,
   for example to repositioning drawings in an animation.

   You can activate multiframe edition with the Multiframe button next to the modes selector (faded lines icon).
   See :doc:`Multiframe </grease_pencil/multiframe>` for more information.


Examples
========

Traditional Animation
---------------------

This example shows you how to animate a bouncing ball
with a traditional 2D animation technique and Grease Pencil.

First, go to menu :menuselection:`File --> New --> 2D Animation` to start with a new 2D animation template.
The template is ready to quick start your animation with a Grease Pencil object already created,
Onion Skinning activated, Auto Keyframe enabled and in camera view.

#. Set the range of the animation in the Timeline from 1 to 24.
#. In the 3D Viewport draw a ball on the upper left corner with the Draw Tool (extreme).
#. Move to frame 12 and draw a squashed ball in the bottom center (breakdown).
#. Move to frame 24 and draw a ball in the top right corner of the 3D Viewport (extreme).
#. Keep drawing all the in-between frames you want using the onion skinning ghost as a reference.

To test the animation, press :kbd:`Spacebar` to play.


## Tools


***************
Animation Tools
***************

.. _bpy.ops.gpencil.blank_frame_add:

Insert Blank Keyframe
=====================

.. reference::

   :Mode:      Draw Mode, Edit Mode, Sculpt Mode
   :Menu:      :menuselection:`Stroke --> Animation --> Insert Blank Keyframe (Active Layer)`
               :menuselection:`Stroke --> Animation --> Insert Blank Keyframe (All Layers)`
   :Shortcut:  :kbd:`Shift-I`

Active Layer
   Add a new blank keyframe to the active layer at the current frame.
   If there is already a keyframe at the current frame,
   a new blank keyframe will be added on the next frame.

All Layers
   When enabled, Blank keyframe will be created on all layers, not only the active one.


.. _bpy.ops.gpencil.frame_duplicate:

Duplicate Active Keyframe
=========================

.. reference::

   :Mode:      Draw Mode, Edit Mode, Sculpt Mode
   :Menu:      :menuselection:`Stroke --> Animation --> Duplicate Active Keyframe (Active Layer)`
               :menuselection:`Stroke --> Animation --> Duplicate Active Keyframe (All Layers)`

Duplicates the strokes on the last keyframe by copying them to the current frame.

Mode
   Active
      Duplicate only the active layer.

   All
      Duplicate all the layers.


.. _bpy.ops.gpencil.active_frames_delete_all:

Delete Active Keyframe
======================

.. reference::

   :Mode:      Draw Mode, Edit Mode, Sculpt Mode
   :Menu:      :menuselection:`Stroke --> Animation --> Delete Active Keyframe (Active Layer)`
               :menuselection:`Stroke --> Animation --> Delete Active Keyframes (All Layers)`
   :Shortcut:  :kbd:`Shift-Delete`, :kbd:`Alt-I`

Deletes the last keyframe in the Dope Sheet or the current keyframe if you are on one.


.. _grease-pencil-animation-tools-interpolation:
.. _bpy.ops.gpencil.interpolate_sequence:

Interpolate Sequence
====================

.. reference::

   :Mode:      Draw Mode, Edit Mode
   :Menu:      :menuselection:`Grease Pencil --> Interpolate Sequence`
   :Shortcut:  :kbd:`Shift-Ctrl-E`

Interpolate strokes between the previous and next keyframe by adding *multiple* keyframes.
A breakdown keyframe will be added on every frame between the previous and next keyframe.


.. _bpy.ops.gpencil.mesh_bake:
.. _bpy.ops.gpencil.bake_mesh_animation:

Bake Mesh to Grease Pencil
==========================

.. reference::

   :Editor:    3D Viewport
   :Mode:      Object and Pose Modes
   :Menu:      :menuselection:`Object --> Animation --> Bake Mesh to Grease Pencil...`

Converts each frame of a mesh animation within a selected frame range to
a Grease Pencil object keyframed strokes. The *Bake Action* operator computes the final animation of
the selected objects with all those modifiers, drivers, and constraints applied, and keyframes the result.

Target Object
   Select the target Grease Pencil object for the baked animation or a new one if there is nothing yet.
Start Frame, End Frame
   Start/End frame for the baking process.
Step
   Frame steps for the baking process
Thickness
   Strokes thickness.
Threshold Angle
   Threshold value that determine the strokes end.
Stroke Offset
   Sets offset to separate strokes from filled strokes.
Only Seam Edges
   Convert only edges marked as seam.
Export Faces
   Convert faces as filled strokes.
Only Selected Keyframes
   Convert only the selected keyframes.
Target Frame
   Target destination frame for the baked animation.
Projection Type
   Sets the projection type to use for the converted strokes.


.. _bpy.ops.gpencil.bake_grease_pencil_animation:

Bake Object Transform to Grease Pencil
======================================

.. reference::

   :Editor:    3D Viewport
   :Mode:      Object and Pose Modes
   :Menu:      :menuselection:`Object --> Animation --> Bake Object Transform to Grease Pencil`

Applies all transform animation at Object level within a selected frame range to Grease Pencil object keyframes.

Start Frame, End Frame
   Start/End frame for the baking process.
Step
   Frame steps for the baking process.
Only Selected Keyframes
   Convert only the selected keyframes.
Target Frame
   Target destination frame for the baked animation.
Projection Type
   Sets the projection type to use for the converted strokes.


## Index

.. _bpy.types.MaterialGPencilStyle:

#############
  Materials
#############

.. toctree::
   :maxdepth: 2

   introduction.rst
   properties.rst


## Introduction


************
Introduction
************

Materials control the appearance of the Grease Pencil object.
They define the base color and texture of the strokes and filled areas.

There is always only one active material in the list (the selected one).
When you draw, the new strokes use the active material.

You can override the base material color using the tools in
:doc:`Vertex Mode </grease_pencil/modes/vertex_paint/introduction>`
or the Draw and Tint tool in Draw Mode.

The material always remains linked to the strokes, this means that any change in a material will change
the look of already drawn strokes.

.. figure:: /images/grease-pencil_materials_introduction_sample.png

   Same stroke linked to different materials.


Grease Pencil Shader
====================

The Grease Pencil shader creates a material that can work
with strokes and/or filled areas of a Grease Pencil object.

Stroke and fill components has it own section panel and
they can be enabled with a checkbox on the panel header.

*Stroke* only has effect on the lines and *Fill* only on the areas
determined by closed lines (by connecting the lines start and end points).

.. note::

   The shader is not yet a BSDF capable shader and can only be setting up
   on the Material Properties panel (it is not a shader node).


Setting Up Materials
====================

.. reference::

   :Mode:      Drawing Mode
   :Panel:     :menuselection:`Material --> Material Slots`
   :Shortcut:  :kbd:`U`

Grease Pencil materials can be created in the :doc:`Material properties </editors/properties_editor>`
as any other materials in Blender.
See :doc:`Material assignment </render/materials/assignment>` for more information.

The 3D Viewport can be set to Material Preview or Rendered shading,
to interactively preview how the material looks in the scene.

Grease Pencil materials are data-blocks that can be :doc:`assigned </render/materials/assignment>`
to one or more objects, and different materials can be assigned to different strokes.

In Grease Pencil the :doc:`brush </grease_pencil/modes/draw/tools/index>`
settings together with the material used will define the look and feel of the final strokes.

Materials slots in the :ref:`List view <ui-list-view>` also have some extra controls
that help to work with materials while drawing or editing lines.


Common Settings
---------------

.. figure:: /images/grease-pencil_materials_introduction_slots-panel.png
   :align: right

   Grease Pencil material slots panel.

Next to the material name there are three icons buttons that control common properties of the material:

Lock (padlock icon)
   Toggle material from being editable.

Viewport/Render Visibility (eye icon)
   Toggle material visibility in the viewport and in render.

Onion Skinning (onion skin icon)
   Toggle the use of the material for :doc:`Onion Skinning </grease_pencil/properties/onion_skinning>`.


Specials
--------

Show All
   Turns on the visibility of every material in the list.

Hide Others
   Turns off the visibility of every material in the list except the active one.

Lock All
   Locks edition of all the materials in the list.

Unlock All
   Unlocks edition of all the materials in the list.

Lock Unselected
   Locks all materials not used in the selected strokes.

Lock Unused
   Locks and hides all unused materials.

Convert Materials to Vertex Color
   Only keeps necessary materials and convert all materials base color to a Color Attribute.

Extract Palette from Vertex Color
   Add all used Color Attributes to a new Color Palette. See :ref:`bpy.types.PaletteColor`.

Copy Material to Selected
   Copy the active material to the selected Grease Pencil object.

Copy All Materials to Selected
   Copy all materials to the selected Grease Pencil object.

Merge Similar
   Combines similar materials in the list and replace the strokes that use the one of
   the merged materials with the new one.

Remove Unused Slots
   Remove all unused materials.


Lock & Visibility General Controls
----------------------------------

Lock (padlock icon)
   Toggle whether the active material is the only one that can be edited.

Visibility (screen icon)
   Toggle whether the active material is the only one that can be edited and is visible.


Grease Pencil Shader
====================

Grease Pencil materials use a special :doc:`shader </grease_pencil/materials/properties>`
that define the appearance of the surface of the stroke and fill.


## Properties


**********
Properties
**********

Surface
=======

.. figure:: /images/grease-pencil_materials_properties_panel.png
   :align: right

   Shader panel with only Stroke component activated.


.. _bpy.types.MaterialGPencilStyle.show_stroke:
.. _bpy.types.MaterialGPencilStyle.color:
.. _bpy.types.MaterialGPencilStyle.use_overlap_strokes:

Stroke
------

When enabled, the shader use the stroke component.
The *Stroke* component controls how to render the edit lines.

.. _bpy.types.MaterialGPencilStyle.mode:

Line Type
   Defines how to display or distribute the output material over the stroke.

   :Line:
      Connects every points in the strokes showing a continuous line.
   :Dots:
      Use a disk shape at each point in the stroke.
      The dots are not connected.
   :Squares:
      Use a square shape at each point in the stroke.
      The squares are not connected.

.. _bpy.types.MaterialGPencilStyle.stroke_style:

Style
   The type of the material.

   :Solid:
      Use a solid color.

      Base Color
         The base color of the stroke.

   :Texture:
      Use an image texture.

      Base Color
         The base color of the stroke.

      Image
         The image data-block used as an image source.

      Blend
         Texture and Base Color mixing amount.

      UV Factor
         The image size along the stroke.

.. _bpy.types.MaterialGPencilStyle.use_stroke_holdout:

Holdout
   Removes the color from strokes underneath the current by using it as a mask.

.. _bpy.types.MaterialGPencilStyle.alignment_mode:

Alignment
   Defines how to align the *Dots* and *Squares* along the drawing path and with the object's rotation.

   :Path:
      Aligns to the drawing path and the object's rotation.
   :Object:
      Aligns to the object's rotation; ignoring the drawing path.
   :Fixed:
      Aligns to the screen space; ignoring the drawing path and the object's rotation.

Rotation
   Rotates the points of *Dot* and *Square* strokes.

   .. note::

      The *Rotation* option is limited to a range of -90 to 90 degrees.

Self Overlap
   Disables stencil and overlap self-intersections with alpha materials.

.. list-table:: Samples of different material strokes mode types and styles.

   * - .. figure:: /images/grease-pencil_materials_properties_stroke-solid-line.png
          :width: 130px

          Mode Type: Line, Style: Solid.

     - .. figure:: /images/grease-pencil_materials_properties_stroke-texture-line.png
          :width: 130px

          Mode Type: Line, Style: Texture.

     - .. figure:: /images/grease-pencil_materials_properties_stroke-solid-dot.png
          :width: 130px

          Mode Type: Dot, Style: Solid.

     - .. figure:: /images/grease-pencil_materials_properties_stroke-texture-dot.png
          :width: 130px

          Mode Type: Dot, Style: Texture.


.. _bpy.types.MaterialGPencilStyle.show_fill:
.. _bpy.types.MaterialGPencilStyle.fill_style:
.. _bpy.types.MaterialGPencilStyle.fill_color:
.. _bpy.types.MaterialGPencilStyle.mix_color:
.. _bpy.types.MaterialGPencilStyle.mix_factor:
.. _bpy.types.MaterialGPencilStyle.flip:
.. _bpy.types.MaterialGPencilStyle.pattern:
.. _bpy.types.MaterialGPencilStyle.texture:
.. _bpy.types.MaterialGPencilStyle.use_fill_texture_mix:

Fill
----

When enabled, the shader use the fill component.
The *Fill* component control how to render the filled areas determined by closed edit lines.

Style
   The type of material.

   Solid
      Use solid color.

      Base Color
         The base color of the fill.

   Gradient
      Use a color gradient.

      Gradient Type
         Linear
            Mix the colors along a single axis.

         Radial
            Mix the colors radiating from a center point.

      Base Color
         The primary color.

      Secondary Color
         The secondary color.

      Blend
         Base Color and Secondary Color mixing amount.

      Flip Colors
         Flips the gradient, inverting the Base Color and Secondary Color.

      Location
         Shifts the gradient position.

         X, Y

      Rotation
         Rotates the gradient.

      Scale
         Scales the gradient.

         X, Y

   Texture
      Use an image texture.

      Base Color
         The base color of the fill.

      Image
         The image data-block used as an image source.

      Blend
         Texture and Base Color mixing amount.

      Location
         Shifts the image position.

         X, Y

      Rotation
         Rotates the image.

      Scale
         Scales the image.

         X, Y

      Clip Image
         When enabled, show one image instance only (do not repeat).

.. _bpy.types.MaterialGPencilStyle.use_fill_holdout:

Holdout
   Removes the color from strokes underneath the current by using it as a mask.

.. list-table:: Samples of different material fill styles.

   * - .. figure:: /images/grease-pencil_materials_properties_fill-solid.png
          :width: 130px

          Style: Solid.

     - .. figure:: /images/grease-pencil_materials_properties_fill-gradient.png
          :width: 130px

          Style: Gradient (Linear).

     - .. figure:: /images/grease-pencil_materials_properties_fill-gradient-radial.png
          :width: 130px

          Style: Gradient (Radial).

     - .. figure:: /images/grease-pencil_materials_properties_fill-texture.png
          :width: 130px

          Style: Texture.


Settings
========

.. _bpy.types.MaterialGPencilStyle.pass_index:

Pass Index
   This index can be used with some modifiers to restrict changes to only a certain material.
   See :doc:`Modifiers </grease_pencil/modifiers/introduction>` for more information.


## Drawing Planes

.. _bpy.types.GPencilSculptSettings.lock_axis:

**************
Drawing Planes
**************

.. reference::

   :Mode:      Draw Mode and Sculpt Mode
   :Header:    :menuselection:`Drawing Planes`

The Drawing Planes selector helps to select
the plane in which the newly created strokes are drawn.

To see which plane you are using when drawing strokes,
you can enable *Canvas* in :ref:`Viewport Overlays <3dview-overlay-grease-pencil>`.
See :doc:`Viewport Display </interface/controls/templates/curve>` to know more about Canvas settings.

.. note::

   The Drawing Plane selected has effect only for new strokes and does not affect the existing ones.


Plane Options
=============

.. figure:: /images/grease-pencil_modes_draw_drawing-planes_selector.png
   :align: right

   Drawing Planes selector in the 3D Viewport header.

Front
   Strokes are drawn on the plane determined by the XZ axes (front view).

Side
   Strokes are drawn on the plane determined by the YZ axes (side view).

Top
   Strokes are drawn on the plane determined by the XY axes (top view).

View
   Strokes are drawn with the current 3D Viewport orientation.

Cursor
   Strokes are drawn with the current 3D cursor orientation.


Examples
========

.. list-table:: Stroke using different Drawing Planes with Canvas overlay activated.

   * - .. figure:: /images/grease-pencil_modes_draw_drawing-planes_front.png
          :width: 200px

          Front.

     - .. figure:: /images/grease-pencil_modes_draw_drawing-planes_side.png
          :width: 200px

          Side.

     - .. figure:: /images/grease-pencil_modes_draw_drawing-planes_top.png
          :width: 200px

          Top.

     - .. figure:: /images/grease-pencil_modes_draw_drawing-planes_view.png
          :width: 200px

          View.

     - .. figure:: /images/grease-pencil_modes_draw_drawing-planes_cursor.png
          :width: 200px

          Cursor.


## Guides

.. _bpy.types.GPencilSculptGuide:

******
Guides
******

.. reference::

   :Mode:      Draw Mode
   :Header:    :menuselection:`Guides`

Guides are drawing aids that make it easier to create different types of strokes.
The Guides can be activated with the button next to the selector (grid icon).


.. _bpy.types.GPencilSculptGuide.type:

Guide Types
===========

.. figure:: /images/grease-pencil_modes_draw_guides_selector.png
   :align: right

   Guide selector activated in the 3D Viewport header.

:Circular:
   Constrains the drawing of new strokes to form rings from the selected reference point.
:Radial:
   Constrains the drawing of new strokes to form rays from the selected reference point.
:Parallel:
   Constrains the drawing of new strokes to form parallel lines.

   Angle
      Angle direction of the parallel lines.
:Grid:
   Constrains the drawing of new strokes to form parallel horizontal or vertical lines.
:Isometric:
   Constrains the drawing of new strokes to vertical or isometric lines.

   Angle
      Angle direction of the isometric lines.


Common Options
--------------

.. _bpy.types.GPencilSculptGuide.use_snapping:

Use Snapping
   When enabled, snap the drawn strokes to an angle or spacing.

   Spacing
      Guide spacing.

.. _bpy.types.GPencilSculptGuide.reference_point:

Reference Point
   Determines the origin point to use for the creation of the lines.
   Applies only for *Circular* and *Radial* guides.

   :Cursor: Use the cursor as a reference point.
   :Custom: Use a custom location as a reference point.

      Custom Location
         X, Y Z

   :Object: Use an object as a reference point.

      Object
         A :ref:`Data ID menu <ui-data-id>` to select the object (usually an empty),
         which location will be used as a reference point.


Examples
========

.. list-table:: Examples of strokes using different types of Guides.

   * - .. figure:: /images/grease-pencil_modes_draw_guides_circular.png
          :width: 200px

          Circular Guides.

     - .. figure:: /images/grease-pencil_modes_draw_guides_radial.png
          :width: 200px

          Radial Guides.

     - .. figure:: /images/grease-pencil_modes_draw_guides_parallel.png
          :width: 200px

          Parallel Guides (30° Angle).

     - .. figure:: /images/grease-pencil_modes_draw_guides_grid.png
          :width: 200px

          Grid Guides.


## Index


#############
  Draw Mode
#############

.. toctree::
   :maxdepth: 2

   introduction.rst
   tools.rst
   tools/index.rst
   tool_settings/index.rst
   stroke_placement.rst
   drawing_planes.rst
   guides.rst


## Introduction


************
Introduction
************

Draw Mode is the mode in Grease Pencil that allows you to draw in the 3D Viewport.
This mode is actually the only one in which new strokes can be created.

Already made strokes can not be selected in Draw Mode, for editing strokes you must use
the :doc:`Edit Mode </grease_pencil/modes/edit/introduction>` or
:doc:`Sculpt Mode </grease_pencil/modes/sculpting/introduction>`.


Draw Mode
=========

.. figure:: /images/grease-pencil_modes_draw_introduction_mode-selector.png

   3D Viewport Mode selector: Draw Mode.

Draw Mode is selected with the *Mode* menu in the 3D Viewport header.
Once Draw Mode is activated, the Toolbar of the 3D Viewport will change to Draw Mode specific panels.
Also a circle with the same color as the active material will appear and
follow the location of the cursor in the 3D Viewport.

To create new strokes you have to select one of the drawing tools in the Toolbar.
The most common one is the :doc:`Draw tool </grease_pencil/modes/draw/tools>`
for free-hand drawings but there are many other tools for drawing, filling areas and erasing strokes.
There are also some tools to create primitives shapes like lines, arcs, curves, boxes and circles.

See :doc:`Toolbar </grease_pencil/modes/draw/tools>` for more details.


Strokes Location and Orientation Controls
=========================================

Drawing in a 3D space is not the same as drawing on a flat canvas.
When drawing with Grease Pencil you have to define
the location and orientation of the new strokes in the 3D space.

.. figure:: /images/grease-pencil_modes_draw_introduction_header-stroke-controls.png

   3D Viewport header Controls for strokes.


Stroke Placement
----------------

The Stroke Placement selector defines the new strokes location in 3D space.

See :doc:`Stroke Placement </grease_pencil/modes/draw/stroke_placement>` for more information.


Drawing Planes
--------------

The Drawing Planes selector defines the plane (orientation) to which the new strokes will be restricted.

See :doc:`Drawing Planes </grease_pencil/modes/draw/drawing_planes>` for more information.


Guides
------

Different Guides types can be activated to assist you when drawing new strokes.

See :doc:`Guides </grease_pencil/modes/draw/guides>` for more information.


.. _bpy.types.ToolSettings.use_gpencil_draw_additive:

Drawing Options
===============

.. figure:: /images/grease-pencil_modes_draw_introduction_drawing-options.png

   General drawing options.

Draw on Back
   When enabled, new strokes are drawn below of all strokes in the layer.
   For example when you want to paint with a fill material below line strokes on a character and
   they are on the same layer.

.. _bpy.types.ToolSettings.use_gpencil_weight_data_add:

Add Weight Data
   When enabled, weight data is added to new strokes according to the current vertex group and weight.
   If there is no vertex group selected, no weight data is added.

   Useful for example in cut-out animation for adding new drawing
   on the same vertex group without the need to creating it afterwards.

   See :doc:`Weight Paint Mode </grease_pencil/modes/weight_paint/introduction>` for more information.

.. _bpy.types.ToolSettings.use_gpencil_draw_onback:

Additive Drawing
   When creating new frames adding strokes with drawing tools,
   the strokes from the previous/active frame are include as a basis for the new one.
   When erasing existing strokes using Additive Drawing a new keyframe will be added.

.. _bpy.types.ToolSettings.use_gpencil_automerge_strokes:

AutoMerge
   Joins new strokes with the beginning or end of previously drawn strokes in the active layer.

Multiframe
   Allows to draw on several frames at the same time.

   See :doc:`Multiframe </grease_pencil/multiframe>` for more information.


## Stroke Placement

.. _bpy.types.ToolSettings.gpencil_stroke_placement:

****************
Stroke Placement
****************

.. reference::

   :Mode:      Draw Mode
   :Header:    :menuselection:`Stroke Placement`

The Stroke Placement selector helps to select the location
in which the newly created strokes are drawn.

.. note::

   The Stroke Placement selected has effect only for new strokes and does not affect the existing ones.

.. figure:: /images/grease-pencil_modes_draw_stroke-placement_selector.png
   :align: right

   Stroke Placement selector on 3D Viewport header.

Origin
   Strokes are placed at Grease Pencil object origin.

3D Cursor
   Strokes are placed at 3D cursor.

Surface
   Strokes will stick on mesh surfaces.

   Offset
      Distance from the mesh surface to place the new strokes.

Stroke
   Strokes will stick on other strokes.

   Target
      :All Points:
         All the points of the new stroke sticks to other strokes.
      :End Points:
         Only the start and end points of the new stroke sticks to other strokes.
      :First Point:
         Only the start point of the new stroke sticks to other strokes.


Examples
========

.. list-table:: Stroke using different Stroke Placements.

   * - .. figure:: /images/grease-pencil_modes_draw_stroke-placement_origin.png
          :width: 200px

          Origin.

     - .. figure:: /images/grease-pencil_modes_draw_stroke-placement_3D-cursor.png
          :width: 200px

          3D Cursor.

     - .. figure:: /images/grease-pencil_modes_draw_stroke-placement_surface.png
          :width: 200px

          Surface.

     - .. figure:: /images/grease-pencil_modes_draw_stroke-placement_stroke.png
          :width: 200px

          Stroke.


## Tools

.. _gpencil_draw-toolbar-index:

*************
Drawing Tools
*************

.. figure:: /images/grease-pencil_modes_draw_tools_toolbar-tools.png
   :align: right

Cursor
   Change the location of the 3D Cursor.

:ref:`Draw <tool-grease-pencil-draw-draw>`
   Draw free-hand strokes.

:ref:`Fill <tool-grease-pencil-draw-fill>`
   Automatic fill closed strokes areas.

:ref:`Erase <tool-grease-pencil-draw-erase>`
   Erase strokes.

:ref:`Tint <tool-grease-pencil-draw-tint>`
   Colorize stroke points.

:ref:`Cutter <tool-grease-pencil-draw-cutter>`
   Cut strokes in between others.

:ref:`Eyedropper <tool-grease-pencil-draw-eyedropper>`
   Eyedropper to create new materials or palette color based on sampled colors in the 3D Viewport.

:ref:`Line <tool-grease-pencil-draw-line>`
   Draw straight lines.

:ref:`Polyline <tool-grease-pencil-draw-polyline>`
   Draw straight multiple lines.

:ref:`Arc <tool-grease-pencil-draw-arc>`
   Draw simple arcs.

:ref:`Curve <tool-grease-pencil-draw-curve>`
   Draw complex Bézier style curves.

:ref:`Box <tool-grease-pencil-draw-box>`
   Draw rectangular shapes.

:ref:`Circle <tool-grease-pencil-draw-circle>`
   Draw oval shapes.

:ref:`Interpolate <tool-grease-pencil-draw-interpolate>` :kbd:`Ctrl-E`
   Automatically create a breakdown keyframe between two normal keyframes.

:ref:`Annotate <tool-annotate-freehand>`
   Draw free-hand annotation.

   :ref:`Annotate Line <tool-annotate-line>`
      Draw straight line annotation.
   :ref:`Annotate Polygon <tool-annotate-polygon>`
      Draw a polygon annotation.
   :ref:`Annotate Eraser <tool-annotate-eraser>`
      Erase previous drawn annotations.


## Arc

.. _tool-grease-pencil-draw-arc:

********
Arc Tool
********

.. reference::

   :Mode:      Draw Mode
   :Tool:      :menuselection:`Toolbar --> Arc`

The Arc tool create simple arcs.


Tool Settings
=============

You can configure the brush main settings exposed on the Tool Settings for convenience.
For the draw brushes configuration and settings see:
:doc:`Draw Brush </grease_pencil/modes/draw/tools/draw>`.

Subdivisions
   The number of stroke points between each stroke edge.

Thickness Profile
   Use a :doc:`curve widget </interface/controls/templates/curve>` to define the stroke thickness
   from the start (left) to end (right) of the stroke.

   Use Curve
      When enabled, the stroke use a curve profile to control the thickness along the arc.

.. list-table:: Different thickness profile samples.

   * - .. figure:: /images/grease-pencil_modes_draw_tools_arc_thickness-profile-01.png
          :width: 200px

     - .. figure:: /images/grease-pencil_modes_draw_tools_arc_thickness-profile-02.png
          :width: 200px

     - .. figure:: /images/grease-pencil_modes_draw_tools_arc_thickness-profile-03.png
          :width: 200px


Usage
=====

Selecting a Brush and Material
------------------------------

In the Tool Settings select the brush, material and color type to use with the tool.
The Arc tool uses *Draw Brush* types.
See :ref:`grease-pencil-draw-common-options` for more information.


Creating Arcs
-------------

#. Click (:kbd:`LMB` or the :kbd:`Pen` tip) and drag the start point.
#. Release on the desired end point.
#. After releasing you can tweak the arc using a single cyan manipulator (hand icon).
#. Then confirm (:kbd:`Return`/:kbd:`MMB`) or cancel (:kbd:`Esc`/:kbd:`RMB`).

While dragging you can use :kbd:`Shift` to make a perfect arc,
use :kbd:`Alt` to create the arc from a center point or :kbd:`M` to flip.

:kbd:`NumpadPlus` and :kbd:`NumpadMinus` or using the mouse :kbd:`Wheel`
will increase or decrease the amount of points in the final arc.

.. list-table::

   * - .. figure:: /images/grease-pencil_modes_draw_tools_arc_example-01.png
          :width: 200px

          click and dragging the start point.

     - .. figure:: /images/grease-pencil_modes_draw_tools_arc_example-02.png
          :width: 200px

          Tweaking arc with the manipulator.

     - .. figure:: /images/grease-pencil_modes_draw_tools_arc_example-03.png
          :width: 200px

          The arc after confirming.


Extruding
---------

Before confirming you can use :kbd:`E` to extrude the end point of the arc
to generate multiple connected arcs.

.. list-table::

   * - .. figure:: /images/grease-pencil_modes_draw_tools_arc_extrude-01.png
          :width: 200px

          End point extruding.

     - .. figure:: /images/grease-pencil_modes_draw_tools_arc_extrude-02.png
          :width: 200px

          Tweaking the last arc with the manipulator.

     - .. figure:: /images/grease-pencil_modes_draw_tools_arc_extrude-03.png
          :width: 200px

          The connected arcs after confirming.


## Box

.. _tool-grease-pencil-draw-box:

********
Box Tool
********

.. reference::

   :Mode:      Draw Mode
   :Tool:      :menuselection:`Toolbar --> Box`

The Box tool create rectangular shapes.


Tool Settings
=============

You can configure the brush main settings exposed on the Tool Settings for convenience.
For the draw brushes configuration and settings see:
:doc:`Draw Brush </grease_pencil/modes/draw/tools/draw>`.

Subdivisions
   The number of stroke points between each stroke edge.

Thickness Profile
   Use a :doc:`curve widget </interface/controls/templates/curve>` to define the stroke thickness
   from the start (left) to end (right) of the stroke.

   Use Curve
      When enabled, the stroke use a curve profile to control the thickness along the line.


Usage
=====

Selecting a Brush and Material
------------------------------

In the Tool Settings select the brush, material and color type to use with the tool.
The Box tool uses *Draw Brush* types.
See :ref:`grease-pencil-draw-common-options` for more information.


Creating Boxes
--------------

#. Click (:kbd:`LMB` or the :kbd:`Pen` tip) and drag the start point.
#. Release on the desired end point.
#. After releasing you can move the start and end point by clicking and dragging on the yellow manipulators.
#. Then confirm (:kbd:`Return`/:kbd:`MMB`) or cancel (:kbd:`Esc`/:kbd:`RMB`).

While dragging you can use :kbd:`Shift` to make a perfect square
or use :kbd:`Alt` to create the box from a center point.

:kbd:`NumpadPlus` and :kbd:`NumpadMinus` or using the mouse :kbd:`Wheel`
will increase or decrease the amount of points in the final box.

.. list-table::

   * - .. figure:: /images/grease-pencil_modes_draw_tools_box_example-01.png
          :width: 200px

          click and dragging the start point.

     - .. figure:: /images/grease-pencil_modes_draw_tools_box_example-02.png
          :width: 200px

          Moving start and end points with manipulators.

     - .. figure:: /images/grease-pencil_modes_draw_tools_box_example-03.png
          :width: 200px

          The box after confirming.


## Circle

.. _tool-grease-pencil-draw-circle:

***********
Circle Tool
***********

.. reference::

   :Mode:      Draw Mode
   :Tool:      :menuselection:`Toolbar --> Circle`

The Circle tool create oval shapes.


Tool Settings
=============

You can configure the brush main settings exposed on the Tool Settings for convenience.
For the draw brushes configuration and settings see:
:doc:`Draw Brush </grease_pencil/modes/draw/tools/draw>`.

Subdivisions
   The number of stroke points between each stroke edge.

Thickness Profile
   Use a :doc:`curve widget </interface/controls/templates/curve>` to define the stroke thickness
   from the start (left) to end (right) of the stroke.

   Use Curve
      When enabled, the stroke use a curve profile to control the thickness along the line.


Usage
=====

Selecting a Brush and Material
------------------------------

In the Tool Settings select the brush, material and color type to use with the tool.
The Circle tool uses *Draw Brush* types.
See :ref:`grease-pencil-draw-common-options` for more information.


Creating Circles
----------------

#. Click (:kbd:`LMB` or the :kbd:`Pen` tip) and drag the start point.
#. Release on the desired end point.
#. After releasing you can move the start and end point by clicking and dragging on the yellow manipulators.
#. Then confirm (:kbd:`Return`/:kbd:`MMB`) or cancel (:kbd:`Esc`/:kbd:`RMB`).

While dragging you can use :kbd:`Shift` to make a perfect circle
or use :kbd:`Alt` to create the circle from a center point.

:kbd:`NumpadPlus` and :kbd:`NumpadMinus` or using the mouse :kbd:`Wheel`
will increase or decrease the amount of points in the final circle.

.. list-table::

   * - .. figure:: /images/grease-pencil_modes_draw_tools_circle_example-01.png
          :width: 200px

          Click and dragging the start point.

     - .. figure:: /images/grease-pencil_modes_draw_tools_circle_example-02.png
          :width: 200px

          Moving start and end points with manipulators.

     - .. figure:: /images/grease-pencil_modes_draw_tools_circle_example-03.png
          :width: 200px

          The circle after confirming.


## Curve

.. _tool-grease-pencil-draw-curve:

**********
Curve Tool
**********

.. reference::

   :Mode:      Draw Mode
   :Tool:      :menuselection:`Toolbar --> Curve`

The Curve tool create complex Bézier style curves.


Tool Settings
=============

You can configure the brush main settings exposed on the Tool Settings for convenience.
For the draw brushes configuration and settings see:
:doc:`Draw Brush </grease_pencil/modes/draw/tools/draw>`.

Subdivisions
   The number of stroke points between each stroke edge.

Thickness Profile
   Use a :doc:`curve widget </interface/controls/templates/curve>` to define the stroke thickness
   from the start (left) to end (right) of the stroke.

   Use Curve
      When enabled, the stroke use a curve profile to control the thickness along the curve.

.. list-table:: Different thickness profile samples.

   * - .. figure:: /images/grease-pencil_modes_draw_tools_curve_thickness-profile-01.png
          :width: 200px

     - .. figure:: /images/grease-pencil_modes_draw_tools_curve_thickness-profile-02.png
          :width: 200px

     - .. figure:: /images/grease-pencil_modes_draw_tools_curve_thickness-profile-03.png
          :width: 200px


Usage
=====

Selecting a Brush and Material
------------------------------

In the Tool Settings select the brush, material and color type to use with the tool.
The Curve tool uses *Draw Brush* types.
See :ref:`grease-pencil-draw-common-options` for more information.


Creating Curves
---------------

#. Click (:kbd:`LMB` or the :kbd:`Pen` tip) and drag the start point.
#. Release on the desired end point.
#. After releasing you can tweak the curve using two cyan Bézier like manipulators.
#. Then confirm (:kbd:`Return`/:kbd:`MMB`) or cancel (:kbd:`Esc`/:kbd:`RMB`).

While dragging you can hold :kbd:`Shift` to use only one manipulator to tweak the curve (like the Arc tool),
use :kbd:`Alt` to create the arc from a center point.

:kbd:`NumpadPlus` and :kbd:`NumpadMinus` or using the mouse :kbd:`Wheel` will increase
or decrease the amount of points in the final curve.

.. list-table::

   * - .. figure:: /images/grease-pencil_modes_draw_tools_curve_example-01.png
          :width: 200px

          click and dragging the start point.

     - .. figure:: /images/grease-pencil_modes_draw_tools_curve_example-02.png
          :width: 200px

          Tweaking curve with the manipulators.

     - .. figure:: /images/grease-pencil_modes_draw_tools_curve_example-03.png
          :width: 200px

          The curve after confirming.


Extruding
---------

Before confirming you can use :kbd:`E` to extrude the end point of the curve
to generate multiple connected curves.

.. list-table::

   * - .. figure:: /images/grease-pencil_modes_draw_tools_curve_extrude-01.png
          :width: 200px

          End point extruding.

     - .. figure:: /images/grease-pencil_modes_draw_tools_curve_extrude-02.png
          :width: 200px

          Tweaking the last curve with the manipulators.

     - .. figure:: /images/grease-pencil_modes_draw_tools_curve_extrude-03.png
          :width: 200px

          The connected curves after confirming.


## Cutter

.. _tool-grease-pencil-draw-cutter:

***********
Cutter Tool
***********

.. reference::

   :Mode:      Draw Mode
   :Tool:      :menuselection:`Toolbar --> Cutter`

The Cutter tool delete points in between intersecting strokes.


Tool Settings
=============

Flat Caps
   Mark newly created :ref:`End Caps <bpy.ops.gpencil.stroke_caps_set>` as *Flat*.

.. _bpy.types.GPencilSculptSettings.intersection_threshold:

Threshold
   Determine the threshold for stroke intersections.


Usage
=====

Draw a dotted line around the strokes you want to be cut.
After releasing the mouse button all the points on the selected strokes
will be deleted until another intersecting stroke is found.

.. list-table::

   * - .. figure:: /images/grease-pencil_modes_draw_tools_cutter_example-01.png
          :width: 200px

          Original drawing.

     - .. figure:: /images/grease-pencil_modes_draw_tools_cutter_example-02.png
          :width: 200px

          Lasso Selecting the strokes to be cut.

     - .. figure:: /images/grease-pencil_modes_draw_tools_cutter_example-03.png
          :width: 200px

          Final result.


## Draw

.. _tool-grease-pencil-draw-draw:

*********
Draw Tool
*********

.. reference::

   :Mode:      Draw Mode
   :Tool:      :menuselection:`Toolbar --> Draw`

The Draw tool allows you to draw free-hand strokes.


Brush Settings
==============

.. figure:: /images/grease-pencil_modes_draw_tools_draw_settings.png
   :width: 275px
   :align: right

Material
   Data-block selector for the :doc:`material </grease_pencil/materials/introduction>`.

Radius
   The radius of the brush in pixels.

   :kbd:`F` allows you to change the brush size interactively by dragging the pointer or
   by typing a number then confirm.

   Use Pressure (pressure sensitivity icon)
      Uses stylus pressure to control how strong the effect is.
      The gradient of the pressure can be customized using
      the :doc:`curve widget </interface/controls/templates/curve>`.

Strength
   Control the stroke transparency (alpha).
   From fully transparent (0.0) to fully opaque (1.0).

   You can change the brush strength interactively by pressing :kbd:`Shift-F`
   in the 3D Viewport and then moving the pointer and then :kbd:`LMB`.
   You can also enter the size numerically.

   Use Pressure (pressure sensitivity icon)
      Uses stylus pressure to control how strong the effect is.
      The gradient of the pressure can be customized using
      the :doc:`curve widget </interface/controls/templates/curve>`.

.. _bpy.types.BrushGpencilSettings.caps_type:

Caps Type
   The shape of the start and end of the stroke.

   :Round: Strokes start and stop with a curved shape.
   :Flat: Strokes start and stop with a straight cutoff.


Advanced
--------

.. _bpy.types.BrushGpencilSettings.input_samples:

Input Samples
   Controls how often the input device is read to generate points on the stroke.
   Higher values give a higher precision (more points) but produce an irregular stroke,
   while lower values give a lower precision (fewer points) but produce a soften stroke.
   (0 disabled extra input device samples.)

   You have to set up this value according to your input device to obtain
   the right balance between accuracy and softness for your strokes.
   See :doc:`Input Device </getting_started/configuration/hardware>` for more information.

.. _bpy.types.BrushGpencilSettings.active_smooth_factor:

Active Smooth
   The number of smoothing iterations to apply to the stroke while drawing.

.. _bpy.types.BrushGpencilSettings.angle:

Angle
   Direction of the input device that gives the maximum thickness to the stroke (0° for horizontal).

.. _bpy.types.BrushGpencilSettings.angle_factor:

Factor
   Amount of thickness reduction when the stroke is perpendicular to the *Angle* value.

.. _bpy.types.BrushGpencilSettings.hardness:

Hardness
   Amount of transparency (alpha) to apply from the border of the point to the center.
   Works only when the brush is using stroke materials of *Dot* or *Box* style.

.. _bpy.types.BrushGpencilSettings.aspect:

Aspect X, Y
   Controls the width and height of the alpha gradient.


Stroke
------

.. _bpy.types.BrushGpencilSettings.use_settings_postprocess:

Post-Processing
^^^^^^^^^^^^^^^

Post-processing methods that are executed on the strokes
when you finished drawing, right after releasing the :kbd:`LMB` or :kbd:`Pen` tip.
You can toggle the use of post-processing using the checkbox in the section panel header.

.. _bpy.types.BrushGpencilSettings.pen_smooth_factor:

Smooth
   Strength of smoothing process on the points location along the stroke.

.. _bpy.types.BrushGpencilSettings.pen_smooth_steps:

Iterations
   The number of smoothing iterations to apply to the stroke.

.. _bpy.types.BrushGpencilSettings.pen_subdivision_steps:

Subdivision Steps
   Number of subdivisions to apply to newly created strokes.

.. _bpy.types.BrushGpencilSettings.simplify_factor:

Simplify
   Reduces final points numbers in the stroke with an adaptive algorithm.

.. _bpy.types.BrushGpencilSettings.use_trim:

Trim Strokes End
   Automatically trim intersection strokes ends.

.. _bpy.types.BrushGpencilSettings.use_settings_outline:

Outline
   Activate the conversion of the newly created stroke to its outline.

   Material
      Material used for outline stroke.
   Thickness
      Thickness used for outline stroke.

.. _bpy.types.BrushGpencilSettings.use_settings_random:

Randomize
^^^^^^^^^

Adds randomness to the position of the points along the stroke.
You can toggle the use of Randomize using the checkbox in the section panel header.

.. _bpy.types.BrushGpencilSettings.use_stroke_random_radius:
.. _bpy.types.BrushGpencilSettings.use_random_press_radius:
.. _bpy.types.BrushGpencilSettings.random:

Radius
   The amount of randomness to apply using the pressure of the input device.

.. _bpy.types.BrushGpencilSettings.use_stroke_random_strength:
.. _bpy.types.BrushGpencilSettings.use_random_press_strength:
.. _bpy.types.BrushGpencilSettings.random_strength:

Strength
   The amount of randomness to apply to the stroke strength value (alpha).

.. _bpy.types.BrushGpencilSettings.use_stroke_random_uv:
.. _bpy.types.BrushGpencilSettings.use_random_press_uv:
.. _bpy.types.BrushGpencilSettings.uv_random:

UV
   The amount of randomness to apply to the UV rotation.

.. _bpy.types.BrushGpencilSettings.use_stroke_random_hue:
.. _bpy.types.BrushGpencilSettings.use_random_press_hue:
.. _bpy.types.BrushGpencilSettings.random_hue_factor:
.. _bpy.types.BrushGpencilSettings.use_stroke_random_sat:
.. _bpy.types.BrushGpencilSettings.use_random_press_sat:
.. _bpy.types.BrushGpencilSettings.random_saturation_factor:
.. _bpy.types.BrushGpencilSettings.use_stroke_random_val:
.. _bpy.types.BrushGpencilSettings.use_random_press_val:
.. _bpy.types.BrushGpencilSettings.random_value_factor:

Hue, Saturation, Value
   Randomizes the hue, saturation, and value of the stroke's :ref:`Color <grease-pencil-draw-color>`.

.. _bpy.types.BrushGpencilSettings.use_jitter_pressure:
.. _bpy.types.BrushGpencilSettings.pen_jitter:

Jitter
   The amount of jittering to add to the stroke.


.. rubric:: Common Options

Stroke Random (stroke icon)
   Use randomness only at stroke level.

Use Pressure (pressure sensitivity icon)
   Uses the stylus pressure to control how strong the effect is.
   The gradient of the pressure can be customized using
   the :doc:`curve widget </interface/controls/templates/curve>`.


.. _bpy.types.BrushGpencilSettings.use_settings_stabilizer:

Stabilize Stroke
^^^^^^^^^^^^^^^^

*Stabilize Stroke* helps to reduce jitter of the strokes while drawing by
delaying and correcting the location of points.
You can toggle the use of *Stabilize Stroke* using the checkbox in the section panel header.

Radius
   Minimum distance from the last point before the stroke continues.
Factor
   A smooth factor, where higher values result in smoother strokes but the drawing sensation
   feels like as if you were pulling the stroke.


Cursor
------

The cursor can be disabled by toggling the checkbox in the *Cursor* header.

.. _bpy.types.BrushGpencilSettings.show_lasso:

Show Fill Color while Drawing
   Shows the brush linked material color in the viewport.


Usage
=====

Selecting a Brush and Material
------------------------------

In the Tool Settings select the brush, material and color type to use with the tool.
The Draw tool uses *Draw Brush* types.
See :ref:`grease-pencil-draw-common-options` for more information.


Free-hand Drawing
-----------------

Click and hold :kbd:`LMB` or use the pen tip to make free-hand drawing on the viewport.

.. list-table:: Drawing free-hand strokes.

   * - .. figure:: /images/grease-pencil_modes_draw_tools_draw_free-hand-01.png
          :width: 200px

     - .. figure:: /images/grease-pencil_modes_draw_tools_draw_free-hand-02.png
          :width: 200px

     - .. figure:: /images/grease-pencil_modes_draw_tools_draw_free-hand-03.png
          :width: 200px


Stabilize Stroke
----------------

:kbd:`Shift-LMB` toggle the use of :ref:`Stabilize Stroke <bpy.types.BrushGpencilSettings.use_settings_stabilizer>`
on the brush to have more control while drawing and get smoother lines.

.. list-table:: Drawing strokes using *Stabilize Stroke*.

   * - .. figure:: /images/grease-pencil_modes_draw_tools_draw_stabilizer-01.png

     - .. figure:: /images/grease-pencil_modes_draw_tools_draw_stabilizer-02.png

     - .. figure:: /images/grease-pencil_modes_draw_tools_draw_stabilizer-03.png


Straight Lines
--------------

:kbd:`Alt-LMB` Constrains the drawing of the strokes to horizontal or vertical straight lines.


Switching to the Erase Tool
---------------------------

:kbd:`Ctrl-LMB` changes temporally to the active Erase tool.
See :doc:`Erase Tool </grease_pencil/modes/draw/tools/erase>` for more information.

You can also use :kbd:`B` to delete all the points in the selected drawing area.


## Erase

.. _tool-grease-pencil-draw-erase:

**********
Erase Tool
**********

.. reference::

   :Mode:      Draw Mode
   :Tool:      :menuselection:`Toolbar --> Erase`

The Erase tool erase already drawn strokes.


Brush Settings
==============

Radius
   The radius of the brush in pixels.

   :kbd:`F` allows you to change the brush size interactively by dragging the pointer or
   by typing a number then confirm.

   Use Pressure (pressure sensitivity icon)
      Uses stylus pressure to control how strong the effect is.
   Occlude Eraser (overlapping squares icon)
      Erase only strokes visible and not occluded by geometry.

   .. _bpy.types.BrushGpencilSettings.use_default_eraser:

   Default Eraser
      Use this brush when enabling the eraser tool with the fast switch key (:kbd:`Ctrl`).


.. _bpy.types.BrushGpencilSettings.eraser_mode:

Mode
   Determines how the erase tool behaves.

   :Dissolve:
      To simulate a raster type eraser, this eraser type
      affects the strength and thickness of the strokes before actually delete a point.
   :Point:
      Delete one point at a time.
   :Stroke:
      Delete an entire stroke.

.. _bpy.types.BrushGpencilSettings.pen_strength:

Strength
   Control how much will affect the eraser has on the stroke transparency (alpha).

   You can change the brush strength interactively by pressing :kbd:`Shift-F`
   in the 3D Viewport and then moving the pointer and then :kbd:`LMB`.
   You can also enter the size numerically.

   .. _bpy.types.BrushGpencilSettings.use_strength_pressure:

   Use Pressure (pressure sensitivity icon)
      Uses stylus pressure to control how strong the effect is.

.. _bpy.types.BrushGpencilSettings.eraser_strength_factor:

Affect Stroke Strength
   The amount of deletion of the stroke strength (alpha) while erasing.

.. _bpy.types.BrushGpencilSettings.eraser_thickness_factor:

Affect Stroke Thickness
   The amount of deletion of the stroke thickness while erasing.


Cursor
------

The cursor can be disabled by toggling the checkbox in the *Cursor* header.


Usage
=====

Selecting a Brush
-----------------

In the Tool Settings select the brush to use with the tool.
The Erase tool uses :ref:`Erase Brush <grease_pencil-draw-brushes-erase>` types (soft, point and stroke).


Dissolve Erasing
----------------

- Select an erase brush of type Soft/Hard.

- Adjust brush settings.

- Click and hold :kbd:`LMB` or use the :kbd:`Pen` tip to delete strokes on the viewport.

.. list-table::

   * - .. figure:: /images/grease-pencil_modes_draw_tools_erase_soft-01.png
          :width: 200px

          Original drawing.

     - .. figure:: /images/grease-pencil_modes_draw_tools_erase_soft-02.png
          :width: 200px

          The eraser affect the transparency of the strokes.

     - .. figure:: /images/grease-pencil_modes_draw_tools_erase_soft-03.png
          :width: 200px

          Final result.


Point Erasing
-------------

- Select an erase brush of type Point.

- Adjust brush settings.

- Click and hold :kbd:`LMB` or use the :kbd:`Pen` tip to delete strokes on the viewport.

.. list-table::

   * - .. figure:: /images/grease-pencil_modes_draw_tools_erase_point-01.png
          :width: 200px

          Original drawing.

     - .. figure:: /images/grease-pencil_modes_draw_tools_erase_point-02.png
          :width: 200px

          The eraser delete one point at a time.

     - .. figure:: /images/grease-pencil_modes_draw_tools_erase_point-03.png
          :width: 200px

          Final result.


Stroke Erasing
--------------

- Select an erase brush of type Stroke.

- Adjust brush settings.

- Click and hold :kbd:`LMB` or use the :kbd:`Pen` tip to delete strokes on the viewport.

.. list-table::

   * - .. figure:: /images/grease-pencil_modes_draw_tools_erase_stroke-01.png
          :width: 200px

          Original drawing.

     - .. figure:: /images/grease-pencil_modes_draw_tools_erase_stroke-02.png
          :width: 200px

          The eraser delete one stroke at a time.

     - .. figure:: /images/grease-pencil_modes_draw_tools_erase_stroke-03.png
          :width: 200px

          Final result.


## Eyedropper

.. _tool-grease-pencil-draw-eyedropper:

**********
Eyedropper
**********

.. reference::

   :Mode:      Draw Mode
   :Tool:      :menuselection:`Toolbar --> Eyedropper`

The Eyedropper tool is used to create materials or palette color based on sampled colors in the 3D Viewport.


Tool Settings
=============

:Material: Create a new material with the Stroke Base Color to be the sampled color.
:Palette: Add a new color to the color palette based on the sampled color.


Usage
=====

- :kbd:`LMB` Create a stroke material.
- :kbd:`Shift-LMB` Create a fill material.
- :kbd:`Shift-Ctrl-LMB` Create both a stroke and fill material.


## Fill

.. _tool-grease-pencil-draw-fill:

*********
Fill Tool
*********

.. reference::

   :Mode:      Draw Mode
   :Tool:      :menuselection:`Toolbar --> Fill`

The Fill tool is used to automatically fill closed strokes areas.


Brush Settings
==============

You can also configure the brush main settings exposed on the Tool Settings for convenience.

.. _bpy.types.BrushGpencilSettings.fill_direction:

Direction :kbd:`Ctrl`
   The portion of area to fill.

   :Normal:
      Fills the area inside the shape under the cursor.
   :Inverted:
      Fills the area outside the shape under the cursor.

.. _bpy.types.BrushGpencilSettings.fill_factor:

Precision
   Multiplier for fill boundary accuracy.
   Higher values are more accurate but slower.

.. _bpy.types.BrushGpencilSettings.dilate:

Dilate/Contract
   Size in pixels to expand or shrink the fill area from the strokes boundary.

Thickness
   The thickness radius of the boundary stroke in pixels.


Advanced
--------

.. _bpy.types.BrushGpencilSettings.fill_draw_mode:

Boundary
   Sets the type of fill boundary limits calculation to perform.

   :All:    Use the thickness of the strokes and the editing lines together.
   :Strokes: Use only the thickness of the strokes (ignore edit lines).
   :Edit Lines:   Use only the edit lines (ignore strokes).

   .. _bpy.types.BrushGpencilSettings.show_fill_boundary:

   Show Lines (eye icon)
      Toggle show auxiliary lines to see the fill boundary.

.. _bpy.types.BrushGpencilSettings.fill_layer_mode:

Layers
   Determines which :doc:`Layers </grease_pencil/properties/layers>` are used for boundary strokes.

   :Visible: Calculates boundaries based on all visible layers.
   :Active:  Calculates boundaries based on the active layer.
   :Layer Above: Calculates boundaries based on the layer above the active layer.
   :Layer Below: Calculates boundaries based on the layer below the active layer.
   :All Above: Calculates boundaries based on all layers above the active layer.
   :All Below: Calculates boundaries based on all layers below the active layer.

.. _bpy.types.BrushGpencilSettings.fill_simplify_level:

Simplify
   Number of simplify steps to apply to the boundary line.
   Higher values reduce the accuracy of the final filled area.

.. _bpy.types.BrushGpencilSettings.show_fill:
.. _bpy.types.BrushGpencilSettings.fill_threshold:

Ignore Transparent
   When enabled, strokes with transparency does not take into account on fill boundary calculations.

   The value slider controls the threshold to consider a material transparent.

.. _bpy.types.BrushGpencilSettings.use_fill_limit:

Limit to Viewport
   When enabled, fill only visible areas in the viewport.


Gap Closure
^^^^^^^^^^^

Gap closure lines are automatic temporarily lines that help to close gaps on the strokes.

.. _bpy.types.BrushGpencilSettings.extend_stroke_factor:

Size
   Control the Size of the line extension or the circumference to use to calculate the lines that will close the gaps.

.. _bpy.types.BrushGpencilSettings.fill_extend_mode:

Mode :kbd:`S`
   Sets the type of Gap closure method to use.

   :Radius: Uses the Radius of circumference of opened nearest points to calculate a line that close the gap.
   :Extend: Extends the opened strokes to close gaps.

.. _bpy.types.BrushGpencilSettings.show_fill_extend:

Visual Aids
   Toggle show closure lines helper.

.. _bpy.types.BrushGpencilSettings.use_collide_strokes:

Strokes Collision :kbd:`D`
   Check if extend lines collide with strokes, stopping the extension if a collision is detected.

.. _bpy.types.BrushGpencilSettings.use_collide_only:

Only Collide Lines
   Use for closing gaps only if the extend strokes collide.


Usage
=====

Selecting a Brush and Material
------------------------------

In the Tool Settings select the brush, material and color type to use with the tool.
The Fill tool uses *Fill Brush* types.
See :ref:`grease-pencil-draw-common-options` for more information.


Filling Areas
-------------

Click :kbd:`LMB` in a closed stroke area. The tool will automatically calculate
the boundary and create a new closed stroke filled with the material selected.

.. list-table::

   * - .. figure:: /images/grease-pencil_modes_draw_tools_fill_example-01.png
          :width: 200px

          Original Drawing.

     - .. figure:: /images/grease-pencil_modes_draw_tools_fill_example-02.png
          :width: 200px

          Use the fill tool to leak materials on closed areas.

     - .. figure:: /images/grease-pencil_modes_draw_tools_fill_example-03.png
          :width: 200px

          Final filled drawing.


Boundary Strokes
----------------

If you have a large gap in an area that you want fill,
you can add boundary strokes manually, a temporary auxiliary lines for closing open shapes.
To create a boundary stroke use :kbd:`Alt-LMB` and draw a line to close the desired area.

.. list-table::

   * - .. figure:: /images/grease-pencil_modes_draw_tools_fill_boundary-strokes-01.png
          :width: 200px

          Original drawing.

     - .. figure:: /images/grease-pencil_modes_draw_tools_fill_boundary-strokes-02.png
          :width: 200px

          Add boundary strokes to close open areas (red lines).

     - .. figure:: /images/grease-pencil_modes_draw_tools_fill_boundary-strokes-03.png
          :width: 200px

          Use the Fill tool to leak material on the new closed area.

When you are satisfied with the fill result you can delete the boundary strokes using
the *Clean Up* tool in the :doc:`Grease Pencil Menu </grease_pencil/modes/edit/grease_pencil_menu>` in Edit Mode.


Automatic Gap Closure
---------------------

A more automatic way to close gaps in an area that you want fill is using temporarily helper lines.
There are two method to use "Radius" or "Extend"

*Radius* use temporary auxiliary lines calculated from the radius of nearby open points to close open shapes.
Set the size more than zero to control the circle size over opened points
(the circle will disappear when the line close the gap).
Click over the area you want to be filled and change the length of the strokes using
:kbd:`PageUp` :kbd:`PageDown` or :kbd:`Wheel`.
When you are satisfied with the length and you are sure the temporarily strokes cross each other,
click again to fill the area.

.. list-table::

   * - .. figure:: /images/grease-pencil_modes_draw_tools_fill_extended-strokes-01.png
          :width: 200px

          Original Drawing.

     - .. figure:: /images/grease-pencil_modes_draw_tools_fill_radius-02.png
          :width: 200px

          Use Radius mode to close open areas (Red circles and cyan lines).

     - .. figure:: /images/grease-pencil_modes_draw_tools_fill_radius-03.png
          :width: 200px

          Use Fill Tool to leak material on the new closed area.

*Extend* use temporary auxiliary lines extending the actual strokes ends for closing open shapes.
Set the size more than zero to use the extended lines, click over the area you want to be filled
and change the length of the strokes using :kbd:`PageUp`/:kbd:`PageDown`, :kbd:`Wheel` or a pen's :kbd:`MMB`.
When you are satisfied with the length and you are sure the temporarily strokes cross each other,
click again to fill the area.

.. list-table::

   * - .. figure:: /images/grease-pencil_modes_draw_tools_fill_extended-strokes-01.png
          :width: 200px

          Original Drawing.

     - .. figure:: /images/grease-pencil_modes_draw_tools_fill_extended-strokes-02.png
          :width: 200px

          Use Extend mode to close open areas (cyan lines).

     - .. figure:: /images/grease-pencil_modes_draw_tools_fill_extended-strokes-03.png
          :width: 200px

          Use Fill Tool to leak material on the new closed area.


Switch to Draw Tool
-------------------

Use :kbd:`Ctrl-LMB` to change temporary to the active draw tool.
For example to manually cover small areas difficult to reach for the Fill tool.
See :doc:`Draw Tool </grease_pencil/modes/draw/tools/draw>` for more information.


## Index

.. _bpy.types.BrushGpencilSettings:

#########
  Tools
#########

.. toctree::
   :maxdepth: 2

   draw.rst
   fill.rst
   erase.rst
   tint.rst
   cutter.rst
   eyedropper.rst
   line.rst
   polyline.rst
   arc.rst
   curve.rst
   box.rst
   circle.rst
   interpolate.rst


## Interpolate

.. _tool-grease-pencil-draw-interpolate:
.. _bpy.ops.gpencil.interpolate:

***********
Interpolate
***********

.. reference::

   :Mode:      Draw Mode
   :Tool:      :menuselection:`Toolbar --> Interpolate`
   :Shortcut:  :kbd:`Ctrl-E`

The Interpolate tool interpolates strokes between the previous and next keyframe by adding a *single* keyframe.
When you are on a frame between two keyframes and click and drag a new breakdown keyframe will be added.
This way you define the final interpolation for the new stroke.


Usage
=====

Set the Playhead on the Timeline between the two keyframes you want to interpolate.
Click and drag from left to right to set the desired interpolation percentage
and release to confirm, a new breakdown keyframe will be added.


Tool Settings
=============

Layer
   Restrict the interpolation to Active or All layers.
Only Selected :guilabel:`Edit Mode`
   When enabled, only selected strokes will be interpolated.
Exclude Breakdowns
   Exclude existing :ref:`Breakdowns keyframes <keyframe-type>` as interpolation extremes.
Flip Mode
   Invert strokes start and end. Automatic will try to found the right mode for every stroke.
Smooth
   Amount of smoothing to apply to interpolated strokes for reducing jitter/noise.
Iterations
   Number of time to smooth newly created strokes.


## Line

.. _tool-grease-pencil-draw-line:

*********
Line Tool
*********

.. reference::

   :Mode:      Draw Mode
   :Tool:      :menuselection:`Toolbar --> Line`

The Line tool create straight lines.


Tool Settings
=============

You can configure the brush main settings exposed on the Tool Settings for convenience.
For the draw brushes configuration and settings see:
:doc:`Draw Brush </grease_pencil/modes/draw/tools/draw>`.

Subdivisions
   The number of stroke points between each stroke edge.

Thickness Profile
   Use a :doc:`curve widget </interface/controls/templates/curve>` to define the stroke thickness
   from the start (left) to end (right) of the stroke.

   Use Curve
      When enabled, the stroke use a curve profile to control the thickness along the line.

.. list-table:: Different thickness profile samples.

   * - .. figure:: /images/grease-pencil_modes_draw_tools_line_thickness-profile-01.png
          :width: 200px

     - .. figure:: /images/grease-pencil_modes_draw_tools_line_thickness-profile-02.png
          :width: 200px

     - .. figure:: /images/grease-pencil_modes_draw_tools_line_thickness-profile-03.png
          :width: 200px


Usage
=====

Selecting a Brush and Material
------------------------------

In the Tool Settings select the brush, material and color type to use with the tool.
The Line tool uses *Draw Brush* types.
See :ref:`grease-pencil-draw-common-options` for more information.


Creating Lines
--------------

#. Click (:kbd:`LMB` or the :kbd:`Pen` tip) and drag the start point.
#. Release on the desired end point.
#. After releasing you can move the start and end point by clicking and dragging on the yellow manipulators.
#. Then confirm (:kbd:`Return`/:kbd:`MMB`) or cancel (:kbd:`Esc`/:kbd:`RMB`).

While dragging you can use :kbd:`Shift` to snapping the line to horizontal, vertical or 45° angle
or use :kbd:`Alt` to create the line from a center point.

:kbd:`NumpadPlus` and :kbd:`NumpadMinus` or using the mouse :kbd:`Wheel`
will increase or decrease the amount of points in the final line.

.. list-table::

   * - .. figure:: /images/grease-pencil_modes_draw_tools_line_example-01.png
          :width: 200px

          click and dragging the start point.

     - .. figure:: /images/grease-pencil_modes_draw_tools_line_example-02.png
          :width: 200px

          Moving start and end points with manipulators.

     - .. figure:: /images/grease-pencil_modes_draw_tools_line_example-03.png
          :width: 200px

          The line after confirming.


Extruding
---------

Before confirming you can use :kbd:`E` to extrude the end point of the line
to generate multiple connected lines.

.. list-table::

   * - .. figure:: /images/grease-pencil_modes_draw_tools_line_extrude-01.png
          :width: 200px

          End point extruding.

     - .. figure:: /images/grease-pencil_modes_draw_tools_line_extrude-02.png
          :width: 200px

          Moving the end point of the last line with the manipulator.

     - .. figure:: /images/grease-pencil_modes_draw_tools_line_extrude-03.png
          :width: 200px

          The connected lines after confirming.


## Polyline

.. _tool-grease-pencil-draw-polyline:

*************
Polyline Tool
*************

.. reference::

   :Mode:      Draw Mode
   :Tool:      :menuselection:`Toolbar --> Polyline`

The Polyline tool create multiple straight lines.


Tool Settings
=============

You can configure the brush main settings exposed on the Tool Settings for convenience.
For the draw brushes configuration and settings see:
:doc:`Draw Brush </grease_pencil/modes/draw/tools/draw>`.

Subdivisions
   The number of stroke points between each stroke edge.

Thickness Profile
   Use a :doc:`curve widget </interface/controls/templates/curve>` to define the stroke thickness
   from the start (left) to end (right) of the stroke.

   Use Curve
      When enabled, the stroke use a curve profile to control the thickness along the line.

.. list-table:: Different thickness profile samples.

   * - .. figure:: /images/grease-pencil_modes_draw_tools_polyline_thickness-profile-01.png
          :width: 200px

     - .. figure:: /images/grease-pencil_modes_draw_tools_polyline_thickness-profile-02.png
          :width: 200px

     - .. figure:: /images/grease-pencil_modes_draw_tools_polyline_thickness-profile-03.png
          :width: 200px


Usage
=====

Selecting a Brush and Material
------------------------------

In the Tool Settings select the brush, material and color type to use with the tool.
The Line tool uses *Draw Brush* types.
See :ref:`grease-pencil-draw-common-options` for more information.


Creating Polylines
------------------

#. Click (:kbd:`LMB` or the :kbd:`Pen` tip) and drag the start point.
#. Release on the desired end point.
#. Click multiple times on different locations to create multiple connected lines.
#. Then confirm (:kbd:`Return`/:kbd:`MMB`) or cancel (:kbd:`Esc`/:kbd:`RMB`).

While dragging you can use :kbd:`Shift` to snapping the line to horizontal, vertical or 45° angle.

:kbd:`NumpadPlus` and :kbd:`NumpadMinus` or using the mouse :kbd:`Wheel`
will increase or decrease the amount of points in the final line.

.. list-table::

   * - .. figure:: /images/grease-pencil_modes_draw_tools_polyline_example-01.png
          :width: 200px

          click and dragging the start point.

     - .. figure:: /images/grease-pencil_modes_draw_tools_polyline_example-02.png
          :width: 200px

          Click multiple times to create multiple connected lines.

     - .. figure:: /images/grease-pencil_modes_draw_tools_polyline_example-03.png
          :width: 200px

          The polyline after confirming.


## Tint

.. _tool-grease-pencil-draw-tint:

*********
Tint Tool
*********

.. reference::

   :Mode:      Draw Mode
   :Tool:      :menuselection:`Toolbar --> Tint`

The Tint tool allows you to paint onto strokes point mixing the material base color with a selected color.


Brush Settings
==============

Mode
   Defines how Color Attributes affect to the strokes.

   :Stroke and Fill: Color Attributes affects both the Stroke and Fill materials.
   :Stroke: Color Attributes affects the Stroke material only.
   :Fill: Color Attributes affects the Fill material only.


Usage
=====

Selecting a Brush, Color & Mode
-------------------------------

In the Tool Settings select the brush, color and mode to use with the tool.

You can configure the brush main settings included in the Tool Settings for convenience.
For the vertex paint brushes configuration and settings see
:doc:`Vertex Paint Brush </grease_pencil/modes/vertex_paint/tool_settings/brush>`.

:kbd:`Ctrl-LMB` erase the Color Attribute.


Painting
--------

Click and hold :kbd:`LMB` or use the pen tip to paint onto the stroke points.

.. list-table:: Vertex painting stroke points.

   * - .. figure:: /images/grease-pencil_modes_draw_tools_tint_paint-01.png
          :width: 200px

     - .. figure:: /images/grease-pencil_modes_draw_tools_tint_paint-02.png
          :width: 200px

     - .. figure:: /images/grease-pencil_modes_draw_tools_tint_paint-03.png
          :width: 200px


## Brushes


*******
Brushes
*******

.. figure:: /images/grease-pencil_modes_draw_tool-settings_brushes_fill-brush-data-block.png
   :align: right

   Brush data-block panel.

Brush
   The :ref:`ui-data-block` to select a preset brush type or a custom brush.

   Add Brush
      When you add a brush, the new brush is a clone of the current one.

   Brush Specials
      Reset Brush
         Reset the current brush to its default settings.

      Reset All Brushes
         Reset all brushes to their default settings.

      Custom Icon
         Allows definition of a custom brush icon.

         Image Path
            Defines the path to the image to use as custom icon.

.. note::

   In order to save a custom brush in a blend-user, enable *Fake User*.


Brush Types
===========

Draw Brushes
------------

Draw brushes are the special type of brushes that uses Grease Pencil for drawing tools.
The brush can be changed in the Tool Settings.
The different draw brushes (pencil, Ink, marker, etc.) are settings variations of the same *Draw Brush*.
You can create many brushes, each with unique settings to get different artistic result while drawing.


Fill Brushes
------------

Fill brushes are the special type of brushes that uses Grease Pencil for the *Fill* tools.
The brush can be changed in the Tool Settings.
The different fill brushes are settings variations of the same *Fill Brush*.
You can create many brushes, each with unique settings to get different result when filling areas.


.. _grease_pencil-draw-brushes-erase:

Erase Brushes
-------------

Erase brushes are the special types of brushes that uses Grease Pencil for *Erase* tools.
The brush can be changed in the Tool Settings.
Soft and hard eraser brushes are settings variations of the same *Erase Brush*.
You can create many brushes, each with unique settings to get different effects while erasing.
The *Erase Brush* has also other two special eraser types: point and stroke.


## Brush Settings

.. _grease-pencil-draw-common-options:

**************
Brush Settings
**************

Material
   Data-block selector for the :doc:`material </grease_pencil/materials/introduction>`.
   Except for the *Erase* tool of course.

   Pin Material (pin icon)
      Pin the material to the brush.

      The final appearance of the strokes is a combination of the brush and material used,
      binding the material to the brush gives more control and avoids a lack of coordination between the two.


## Color

.. _grease-pencil-draw-color:

*****
Color
*****

Controls the source of the stroke color.
The mode can be pinned to the brush by enabling the Pin icon in the Tool Settings header.


Material
========

Use the stroke/fill base color material.


Color Attribute
===============

Use Color Attribute.

Color Picker
   The color of the brush. See :ref:`ui-color-picker`.

Color Palette
   Active Color Palette. See :ref:`bpy.types.PaletteColor`.

.. _bpy.types.BrushGpencilSettings.vertex_mode:

Mode
   The color transformation will be applied on the stroke and/or the fill color.

   :Stroke: Only paint over strokes.
   :Fill: Only paint over fill areas.
   :Stroke & Fill: Paint over strokes and fill areas.

.. _bpy.types.BrushGpencilSettings.vertex_color_factor:

Mix Factor
   Mixing factor between the selected color and the base material color.


## Index


##################
  Tools Settings
##################

.. toctree::
   :maxdepth: 2

   brushes.rst
   brush_settings.rst
   color.rst


## Curve Editing

.. _bpy.types.GreasePencil.use_curve_edit:

*************
Curve Editing
*************

Curve Editing allows you to edit Grease Pencil strokes using Bézier curves.


Usage
=====

#. Select the desired strokes to edit as curves.
#. Activate curve editing in the 3D Viewport's header with the toggle button (Bézier curve icon).
#. Once activated you can:

   - Edit the curves with the curve handles.
   - Select strokes to automatically convert them to curves.

.. note::

   Selecting :doc:`points in between </grease_pencil/selecting>` is disabled while in curve editing is active.

.. seealso::

   The curve editing handles display can be tweaked in
   the :ref:`Overlays <bpy.types.View3DOverlay.display_handle>` popover.


Curve Editing Popover
=====================

.. reference::

   :Mode:      Edit Mode
   :Panel:     :menuselection:`3D Viewport --> Header --> Curve Editing`

.. figure:: /images/grease-pencil_modes_edit_curve-editing_panel.png

   Curve Editing popover.

.. _bpy.types.GreasePencil.edit_curve_resolution:

Curve Resolution
   Number of points generated along each curve segment (between two handles) if *Adaptive Resolution* is disabled.

.. _bpy.types.GreasePencil.curve_edit_threshold:

Threshold
   Threshold used for curve fitting. Maximum distance the fitted curve can deviate from the target stroke.
   A threshold of 0.0 will generate a curve point for every stroke point. Higher thresholds will result in higher
   approximations of the target stroke but also smoother curve.

.. _bpy.types.GreasePencil.curve_edit_corner_angle:

Corner Angle
   Any detected corner with an angle above the specified amount will create a sharp (non-aligned) handle.

.. _bpy.types.GreasePencil.use_adaptive_curve_resolution:

Adaptive Resolution
   When activated, the *Curve Resolution* is no longer constant for all curve segments but calculated dynamically.
   The length of each segment is approximated, then multiplied by the *Curve Resolution* and rounded down.
   This will be the number of points to generate for that segment.
   With Adaptive Resolution the points will be distribute more evenly across all the strokes.
   The *Curve Resolution* option will change the point density.

   .. list-table:: Adaptive Resolution.

      * - .. figure:: /images/grease-pencil_modes_edit_curve-editing_adaptive-resolution-off.png
             :width: 320px

             Off.

        - .. figure:: /images/grease-pencil_modes_edit_curve-editing_adaptive-resolution-on.png
             :width: 320px

             On.


Curve Data
==========

Once a stroke has been converted to a curve, the data will be saved to the file.
When Curve Editing is deactivated and the curve is changed, for example using
:doc:`Sculpt Mode </grease_pencil/modes/sculpting/introduction>`,
then the curve will be refitted once Curve Editing is activated again.


Operators
=========

Curve editing is currently more limited than stroke editing.
Every operation in Edit Mode for strokes and stroke points work for curves as well except for the following:

- Duplicate
- Copy and Paste
- Snap to Cursor and Cursor to selected
- Flip
- Simplify and Simplify Fixed
- Trim
- Separate
- Split
- Interpolate


## Grease Pencil Menu


******************
Grease Pencil Menu
******************

Transform
=========

Strokes can be edited by transforming the locations of points.


Move, Rotate & Scale
--------------------

.. reference::

   :Mode:      Edit Mode
   :Tool:      :menuselection:`Toolbar --> Move, Rotate, Scale`
   :Menu:      :menuselection:`Grease Pencil --> Transform --> Move, Rotate, Scale`
   :Shortcut:  :kbd:`G`, :kbd:`R`, :kbd:`S`

Like other elements in Blender, points and strokes can be
moved :kbd:`G`, rotated :kbd:`R` or scaled :kbd:`S` as described in
the :doc:`Basic Transformations </scene_layout/object/editing/transform/introduction>` section.
When in *Edit Mode*,
:doc:`Proportional Editing </editors/3dview/controls/proportional_editing>`
is also available for the transformation actions.


Transform Snapping
------------------

Basic move, rotate and scale transformations for selected points/strokes.
See :doc:`Move, Rotate, Scale Basics </modeling/meshes/editing/mesh/transform/basic>` for more information.


Tools
-----

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Grease Pencil --> Transform`
   :Tool:      :menuselection:`Toolbar --> Bend/Shear`

The *Bend*, *Shear*, *To Sphere*, *Extrude* and *Shrink Fatten* transform tools are described
in the :doc:`Editing tools </grease_pencil/modes/edit/tools>` section.


Mirror
======

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Grease Pencil --> Mirror`
   :Shortcut:  :kbd:`Ctrl-M`

The *Mirror* tool is also available, behaving exactly the same as with
:doc:`mesh vertices </modeling/meshes/editing/mesh/mirror>`.


Snap
====

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Grease Pencil --> Snap`
   :Shortcut:  :kbd:`Shift-S`

:doc:`Mesh snapping </editors/3dview/controls/snapping>`
also works with Grease Pencil components.


Active Layer
============

.. reference::

   :Mode:      Edit Mode, Draw Mode
   :Menu:      :menuselection:`Grease Pencil --> Active Layer`
   :Shortcut:  :kbd:`Y`

Select the active layer.


Animation
=========

.. reference::

   :Mode:      Edit Mode, Draw Mode
   :Menu:      :menuselection:`Grease Pencil --> Animation`
   :Shortcut:  :kbd:`I`

The stroke animation tools are described
in the :doc:`Animation </grease_pencil/animation/tools>` section.


Interpolation
=============

.. reference::

   :Mode:      Edit Mode, Draw Mode
   :Menu:      :menuselection:`Grease Pencil --> Interpolation`

The stroke animation tools are described
in the :ref:`Animation <grease-pencil-animation-tools-interpolation>` section.


.. _bpy.ops.gpencil.duplicate_move:

Duplicate
=========

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Grease Pencil --> Duplicate`
   :Shortcut:  :kbd:`Shift-D`

Duplicates the selected elements, without creating any connections
with the rest of the strokes (unlike *Extrude*, for example),
and places the duplicate at the location of the original elements.


.. _bpy.ops.gpencil.stroke_split:

Split
=====

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Grease Pencil --> Split`
   :Shortcut:  :kbd:`V`

Splits (disconnects) the selected points from the rest of the stroke.
The separated points are left exactly at the same position as the original points but they belong to a new stroke.


.. _bpy.ops.gpencil.copy:

Copy
====

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Grease Pencil --> Copy`
   :Shortcut:  :kbd:`Ctrl-C`

Copy the selected points/strokes to the clipboard.


.. _bpy.ops.gpencil.paste:

Paste & Paste by Layer
======================

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Grease Pencil --> Paste`, :menuselection:`Grease Pencil --> Paste by Layer`
   :Shortcut:  :kbd:`Ctrl-V`

Type
   Paste to Active
      Pastes the points/strokes copied from the clipboard into the active layer.
      This is the default behavior and the mode used when using :menuselection:`Grease Pencil --> Paste`.

   Paste by Layer
      Pastes the points/strokes copied from the clipboard into the layer they were copied from.


.. _bpy.ops.gpencil.stroke_separate:

Separate
========

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Grease Pencil --> Separate`
   :Shortcut:  :kbd:`P`

Separate the selected elements into a new Grease Pencil object.

Selected Points
   Separate the selected points into a new object.

Selected Strokes
   Separate the selected strokes into a new object.
   If one point of a stroke is selected, the entire stroke will be separated.

Active Layer
   Separate all the strokes in the active layer into a new object.
   See :doc:`2D Layers </grease_pencil/properties/layers>` for more information.


Clean Up
========

These tools help to cleanup degenerate geometry on the strokes.


.. _bpy.ops.gpencil.frame_clean_fill:

Boundary Strokes
----------------

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Grease Pencil --> Clean Up --> Boundary Strokes`

Removes boundary strokes used by the *Fill* tool.
See :doc:`Fill tool </grease_pencil/modes/draw/tools/fill>` for more information.

Mode
   Active Frame Only
      Removes boundary strokes from the current frame.
   All Frames
      Removes boundary strokes from all frames.


Boundary Strokes All Frames
---------------------------

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Grease Pencil --> Clean Up --> Boundary Strokes all Frames`

Same as `Boundary Strokes`_ but *Mode* is set to *All Frames*.


.. _bpy.ops.gpencil.frame_clean_loose:

Delete Loose Points
-------------------

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Grease Pencil --> Clean Up --> Delete Loose Points`

Removes unconnected points.


.. _bpy.ops.gpencil.stroke_merge_by_distance:

Merge by Distance
-----------------

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Grease Pencil --> Clean Up --> Merge by Distance`

*Merge by Distance* is a useful tool to simplify a stroke by merging
the selected points that are closer than a specified distance to each other.
Note, unless using *Unselected*, selected points must be contiguous,
else they will not be merged.

Merge Distance
   Sets the distance threshold for merging points.
Unselected
   Allows points in selection to be merged with unselected points.
   When disabled, selected points will only be merged with other selected ones.


.. _bpy.ops.gpencil.frame_clean_duplicate:

Delete Duplicate Frames
-----------------------

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Grease Pencil --> Clean Up --> Delete Duplicate Frames`

Removes any duplicate keyframes.


.. _bpy.ops.gpencil.reproject:

Reproject
---------

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Grease Pencil --> Clean Up --> Reproject`

Sometimes you may have drawn strokes unintentionally in different locations in the 3D space
but they look right from a certain plane or from the camera view.
You can use Reproject to flatten all the selected strokes from a certain viewpoint.

Reprojected Type
   :Front: Reproject selected strokes onto the front plane (XZ).
   :Side: Reproject selected strokes onto the side plane (YZ).
   :Top: Reproject selected strokes onto the top plane (XY).
   :View: Reproject selected strokes onto the current view.
   :Surface: Reproject selected strokes onto the mesh surfaces.
   :Cursor: Reproject selected strokes onto 3D cursor rotation.

Surface Offset
   When Surface Mode is activated controls the stroke offset from the object.

Keep Original
   Maintains the original strokes after applying the tool.

.. list-table::

   * - .. figure:: /images/grease-pencil_modes_edit_grease-pencil-menu_reproject-strokes-1.png
          :width: 200px

          Original drawing from the front view.

     - .. figure:: /images/grease-pencil_modes_edit_grease-pencil-menu_reproject-strokes-2.png
          :width: 200px

          Original drawing in the 3D Viewport.

     - .. figure:: /images/grease-pencil_modes_edit_grease-pencil-menu_reproject-strokes-3.png
          :width: 200px

          Strokes reprojected onto the front plane to fix strokes misalignment.

     - .. figure:: /images/grease-pencil_modes_edit_grease-pencil-menu_reproject-strokes-1.png
          :width: 200px

          Drawing after reprojection operation from the front view.


.. _bpy.ops.gpencil.recalc_geometry:

Recalculate Geometry
====================

.. reference::

   :Mode:      Edit Mode and Draw Mode
   :Menu:      :menuselection:`Grease Pencil --> Clean Up --> Recalculate Geometry`

This operator updates all internal geometry data.
It is not intended that you will have to use this operator
but it can help in cases where strokes are drawn in a strange way or when you opened an old file.


.. _bpy.ops.gpencil.delete:
.. _bpy.ops.gpencil.dissolve:

Delete
======

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Grease Pencil --> Delete`
   :Shortcut:  :kbd:`X`, :kbd:`Delete`, :kbd:`Ctrl-X`

Options for the Erase pop-up menu:

Points
   Deletes the selected points.
   When only one point remains, there is no more visible stroke,
   and when all points are deleted, the stroke itself is deleted.

Strokes
   Deletes all the strokes that selected points belongs to.

Frames
   Deletes all the strokes at the current frame and in the current layer/channel.

Dissolve :kbd:`Ctrl-X`
   Deletes the selected points without splitting the stroke.
   The remaining points in the strokes stay connected.

Dissolve between :kbd:`Ctrl-X`
   Deletes all the points between the selected points without splitting the stroke.
   The remaining points in the strokes stay connected.

Dissolve Unselect :kbd:`Ctrl-X`
   Deletes all the points that are not selected in the stroke without splitting the stroke.
   The remaining points in the strokes stay connected.

Delete All Active Frames
   Deletes all the strokes at the current frame in all layers/channels.


## Index


#############
  Edit Mode
#############

.. toctree::
   :maxdepth: 2

   introduction.rst
   tools.rst
   curve_editing.rst
   grease_pencil_menu.rst
   stroke_menu.rst
   point_menu.rst


## Introduction


************
Introduction
************

Blender provides a variety of tools for editing Grease Pencil strokes.
These are tools used to add, duplicate, move and delete elements.


Accessing Stroke Editing Tools
==============================

These are available through the different tools in the Toolbar,
the Stroke menu in the 3D Viewport header, and context menus in the 3D Viewport,
as well as individual shortcut keys.


Toolbar
-------

When you select a stroke and :kbd:`Tab` into Edit Mode,
the :doc:`Toolbar </grease_pencil/modes/edit/tools>` changes from *Object Tools* to *Stroke editing Tools*.
These are only some of the stroke editing tools.


Menus
-----

The :doc:`Stroke Menu </grease_pencil/modes/edit/stroke_menu>` is located in the header.


Context Menu
------------

:kbd:`RMB` brings up the complete :doc:`Stroke Menu </grease_pencil/modes/edit/stroke_menu>`.


## Point Menu


**********
Point Menu
**********

.. _bpy.ops.gpencil.extrude_move:

Extrude
=======

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Point --> Extrude`
   :Tool:      :menuselection:`Toolbar --> Extrude`
   :Shortcut:  :kbd:`E`

Extrudes points by duplicating the selected points, which then can be moved.
The new points stay connected with the original points of the edit line.

.. note::

   Since Grease Pencil strokes can only have one start an end point,
   a new stroke will be created when extrude intermediate points in the strokes.


.. _bpy.ops.gpencil.stroke_smooth:

Smooth
======

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Point --> Smooth`

Softens strokes by reducing the differences in the locations of the points along the line,
while trying to maintain similar values that make the line fluid and smoother.

Repeat
   The number of times to repeat the procedure.

Factor
   The amount of the smoothness to apply.

Selected Points
   When enabled, limits the effect to only the selected points within the stroke.

Position
   When enabled, the operator affect the points location.

Thickness
   When enabled, the operator affect the points thickness.

Strength
   When enabled, the operator affect the points strength (alpha).

UVs
   When enabled, the operator affect the UV rotation on the points.


.. _bpy.ops.gpencil.stroke_merge:

Merge
=====

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Point --> Merge`

Combine all selected points into a unique stroke.
All the selected points will be connected by new edit lines when needed to create the new stroke.


## Stroke Menu


***********
Stroke Menu
***********

This page covers many of the tools in the *Strokes* menu.
These are tools that work primarily on strokes, however,
some also work with point selections.


.. _bpy.ops.gpencil.stroke_subdivide:

Subdivide
=========

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Stroke --> Subdivide`

Subdivides the strokes by inserting points between the selected points.

Number of Cuts
   The number of subdivisions to perform.

Smooth
   The amount of the smoothness on subdivided points.

Repeat
   Number of times to repeat the procedure.

Selected Points
   When enabled, limits the effect to only the selected points within the stroke.

Position
   When enabled, the operator affect the points location.

Thickness
   When enabled, the operator affect the points thickness.

Strength
   When enabled, the operator affect the points strength (alpha).

UVs
   When enabled, the operator affect the UV rotation on the points.


Simplify
========

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Stroke --> Simplify`

Reduce the amount of points in the strokes.

.. _bpy.ops.gpencil.stroke_simplify_fixed:

Fixed
-----

Deletes alternated points in the strokes, except the start and end points.

Steps
   The number of times to repeat the procedure.


.. _bpy.ops.gpencil.stroke_simplify:

Adaptive
--------

Uses the RDP algorithm (Ramer-Douglas-Peucker algorithm) for points deletion.
The algorithm tries to obtain a similar line shape with fewer points.

Factor
   Controls the amount of recursively simplifications applied by the algorithm.


.. _bpy.ops.gpencil.stroke_sample:

Sample
------

Recreates the stroke geometry with a predefined length between points.

Length
   The distance between points on the recreated stroke.
   Smaller values will require more points to recreate the stroke,
   while larger values will result in fewer points needed to recreate the curve.
Sharp Threshold
   The maximum angle between points on the recreated stroke.
   Smaller values will require more points to recreate the stroke,
   while larger values will result in fewer points needed to recreate the curve.


.. _bpy.ops.gpencil.stroke_trim:

Trim
====

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Stroke --> Trim`

Trims selected stroke to first loop or intersection.

.. list-table::

   * - .. figure:: /images/grease-pencil_modes_edit_stroke-menu_trim-1.png
          :width: 320px

          Original stroke.

     - .. figure:: /images/grease-pencil_modes_edit_stroke-menu_trim-2.png
          :width: 320px

          Result of trim operation.


.. _bpy.ops.gpencil.stroke_outline:

Outline
=======

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Stroke --> Outline`

Converts a stroke to an outline.

View
   The projection method to generate the outline

   :View: Use the viewport's view as a projection.
   :Front: Use the X-Z axes view as a projection.
   :Side: use the Y-Z axis view as a projection
   :Top: Use the X-Y axes view as a projection
   :Camera: Use the view from the active camera as a projection.
Material Mode
   How materials are assigned to the outline.

   :Active Material: The stroke outline will be assigned the active material.
   :Keep Material: The stoke outline will have the same material as before.
   :New Material: A new material will be created and assigned to the outline.
Thickness
   Thickness of the stroke perimeter.
Keep Shape
   Try to keep global shape when the stroke thickness change.
Subdivisions
   Number of subdivisions for the start and end caps.
Sample Length
   The length each resulting segment of the outline.
   Smaller values create outlines closer to the original shape.

.. list-table::

   * - .. figure:: /images/grease-pencil_modes_edit_stroke-menu_outline-1.png
          :width: 320px

          Original stroke.

     - .. figure:: /images/grease-pencil_modes_edit_stroke-menu_outline-2.png
          :width: 320px

          Generated stroke after outline operation.


.. _bpy.ops.gpencil.stroke_join:

Join
====

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Stroke --> Join --> Join, Join and Copy`
   :Shortcut:  :kbd:`Ctrl-J`, :kbd:`Shift-Ctrl-J`

Join two or more strokes into a single one.

Type
   Join :kbd:`Ctrl-J`
      Join selected strokes by connecting points.

   Join and Copy :kbd:`Shift-Ctrl-J`
      Join selected strokes by connecting points in a new stroke.

Leave Gaps
   When enabled, do not use geometry to connect the strokes.


.. _bpy.ops.gpencil.move_to_layer:

Move to Layer
=============

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Stroke --> Move to Layer`
   :Shortcut:  :kbd:`M`

A pop-up menu to move the stroke to a different layer.
You can choose the layer to move the selected strokes to
from a list of layers of the current Grease Pencil object.
You can also add a new layer to move the selected stroke to.
When creating a new layer, there is another pop-up to type in the name of the new layer.


.. _bpy.ops.gpencil.stroke_change_color:

Assign Material
===============

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Stroke --> Assign Material`

Changes the material linked to the selected stroke.
You can choose the name of the material to be used by the selected stroke
from a list of materials of the current Grease Pencil object.


.. _bpy.ops.gpencil.set_active_material:

Set as Active Material
======================

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Stroke --> Set as Active Material`

Sets the active object material based on the selected stroke material.


.. _bpy.ops.gpencil.stroke_arrange:

Arrange
=======

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Stroke --> Arrange`

Change the drawing order of the strokes in the 2D layer.

Bring to Front
   Moves to the top the selected points/strokes.

Bring Forward
   Moves the selected points/strokes upper the next one in the drawing order.

Send Backward
   Moves the selected points/strokes below the previous one in the drawing order.

Send to Back
   Moves to the bottom the selected points/strokes.


.. _bpy.ops.gpencil.stroke_cyclical_set:

Close
=====

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Stroke --> Close`
   :Shortcut:  :kbd:`F`

Close or open strokes by connecting the last and first point.

Type
   Close All
      Close all open selected strokes.

   Open All
      Open all closed selected strokes.

   Toggle
      Close or Open selected strokes as required.

Create Geometry
   When enabled, points are added for closing the strokes.
   If disabled, the operator act the same as *Toggle Cyclic*.


Toggle Cyclic
=============

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Stroke --> Toggle Cyclic`

Toggles between an open stroke and closed stroke (cyclic).

Type
   Close All
      Close all open selected strokes.

   Open All
      Open all closed selected strokes.

   Toggle
      Close or Open selected strokes as required.

   Create Geometry
      When enabled, points are added for closing the strokes like when using the *Close* tool.
      If disabled, the stroke is close without any actual geometry.


.. _bpy.ops.gpencil.stroke_caps_set:

Toggle Caps
===========

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Stroke --> Toggle Caps`

Toggle ending cap styles of the stroke.

Default
   Sets stroke start and end points to rounded (default).

Both
   Toggle stroke start and end points caps to flat or rounded.

Start
   Toggle stroke start point cap to flat or rounded.

End
   Toggle stroke end point cap to flat or rounded.

.. list-table::

   * - .. figure:: /images/grease-pencil_modes_edit_stroke-menu_cap-1.png
          :width: 200px

          Stroke ending with rounded caps.

     - .. figure:: /images/grease-pencil_modes_edit_stroke-menu_cap-2.png
          :width: 200px

          Stroke ending with flat caps.

     - .. figure:: /images/grease-pencil_modes_edit_stroke-menu_cap-3.png
          :width: 200px

          Stroke ending with combined caps.


.. _bpy.ops.gpencil.stroke_flip:

Switch Direction
================

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Stroke --> Switch Direction`

Reverse the direction of the points in the selected strokes
(i.e. the start point will become the end one, and vice versa).

.. _bpy.ops.gpencil.stroke_start_set:

Set Start Point
===============

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Stroke --> Set Start Point`

Set the start point for cyclic strokes.


Normalize Thickness
===================

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Stroke --> Normalize Thickness`

Makes the thickness equal for the entire stroke.

Mode
   Stroke Property to normalize.

Value
   Thickness value to use on all points of the stroke.


Normalize Opacity
=================

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Stroke --> Normalize Opacity`

Makes the opacity equal for the entire stroke.

Mode
   Stroke Property to normalize.

Value
   Opacity value to use on all points of the stroke.


Scale Thickness
===============

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Stroke --> Scale Thickness`

When enabled, scales the stroke thickness during scale transformations.

Reset Fill Transform
====================

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Stroke --> Reset Fill Transform`

Reset all fill translation, scaling and rotations in the selected strokes.


## Tools

.. _gpencil_edit-toolbar-index:

*************
Editing Tools
*************

.. figure:: /images/grease-pencil_modes_edit_tools_toolbar.png
   :align: right

:ref:`Select <tool-select-tweak>`
   Select or moved.

   :ref:`Select Box <tool-select-box>`
      Select geometry by dragging a box.
   :ref:`Select Circle <tool-select-circle>`
      Select geometry by painting on it.
   :ref:`Select Lasso <tool-select-lasso>`
      Select geometry by drawing a lasso.

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

Extrude :kbd:`E`
   Extrusion tools duplicate points, while keeping the new geometry connected with the original points.

Radius :kbd:`Alt-S`
   Expand or contract the thickness radius of the selected points.

Bend :kbd:`Shift-W`
   Bend selected points between the 3D cursor and the pointer.

Shear :kbd:`Shift-Ctrl-Alt-S`
   Shear selected points along the horizontal or vertical screen axis.

   To Sphere :kbd:`Shift-Alt-S`
      Move selected points outward in a spherical shape around the selected strokes' center.

Transform Fill
   Change the Translation, Rotation and scale of strokes fill.

:ref:`Interpolate <tool-grease-pencil-draw-interpolate>` :kbd:`Ctrl-E`
   Automatically create a breakdown keyframe between two normal keyframes.

:ref:`Annotate <tool-annotate-freehand>`
   Draw free-hand annotation.

   :ref:`Annotate Line <tool-annotate-line>`
      Draw straight line annotation.
   :ref:`Annotate Polygon <tool-annotate-polygon>`
      Draw a polygon annotation.
   :ref:`Annotate Eraser <tool-annotate-eraser>`
      Erase previous drawn annotations.


## Convert To Geometry

.. _bpy.ops.gpencil.convert:

*******************
Convert to Geometry
*******************

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Convert --> Path, Bézier Curve, Polygon Curve`

In the 3D Viewport, sketches on the active layer can be converted to geometry,
based on the current view settings, by transforming the points recorded when drawing
(which make up the strokes) into 3D space. Currently, all points will be used,
so it may be necessary to simplify or subdivide parts of the created geometry for standard use.
Sketches can currently be converted into curves in Object Mode.


Options
=======

Type
   The type of object to convert to.

   Path
      Create NURBS 3D curves of order 2 (i.e. behaving like polylines).
   Bézier Curve
      Create Bézier curves, with free "aligned" handles (i.e. also behaving like polylines).
   Polygon Curve
      Bézier curve with straight line segments (auto handles).

   .. note:: Converting to Mesh

      If you want to convert your sketch to a mesh,
      simply choose *NURBS* first, and then convert the created curve to a mesh.

Bevel Depth
   The :ref:`Bevel Depth <bpy.types.Curve.bevel_depth>` to use for the converted curve object.

Bevel Resolution
   The :ref:`Bevel Resolution <bpy.types.Curve.bevel_resolution>` to use for the converted curve object.

Normalize Weight
   Will scale weights value so that they fit into the (0.0 to 1.0) range.

Radius Factor
   Multiplier for the points' radii (set from the stroke's width).

Link Strokes
   Will create a single spline, i.e. curve element, from all strokes in active Grease Pencil layer.
   This is especially useful if you want to use the curve as a path.
   All the strokes are linked in the curve by "zero weights/radii" sections.


Timing
------

Grease Pencil stores "dynamic" data, i.e. how fast strokes are drawn.
When converting to curve, this data can be used to create an *Evaluate Time* F-Curve
(in other words, a path animation), that can be used
e.g. to control another object's position along that curve
(*Follow Path* constraint, or, through a driver, *Curve* modifier).
So this allows you to reproduce your drawing movements.

*Link Strokes* has to be enabled for all timing options.

Timing Mode
   This control lets you choose how timing data is used.

   No Timing
      Just create the curve, without any animation data (hence all following options will be hidden).
   Linear
      The path animation will be a linear one.
   Original
      The path animation will reflect to original timing, including for the "gaps"
      (i.e. time between strokes drawing).
   Custom Gaps
      The path animation will reflect to original timing, but the "gaps" will get custom values.
      This is especially useful if you want to shorten large pauses between some strokes.

Frame Range
   The "length" of the created path animation, in frames. In other words, the highest value of *Evaluation Time*.
Start Frame
   The starting frame of the path animation.
Realtime
   When enabled, the path animation will last exactly the same duration it has taken you to draw the strokes.
End Frame
   When *Realtime* is disabled, this defines the end frame of the path animation.
   This means that the drawing timing will be adjusted to fit into the specified range.
Gap Duration
   *Custom Gaps* only. The average duration (in frames) of each gap between strokes.
   Please note that, the value will only be exact if *Realtime* is enabled,
   otherwise it will be scaled, exactly as the strokes' timing is.


Example
=======

Here is a simple `"hand writing" video <https://www.youtube.com/watch?v=VwWEXrnQAFI>`__
created with curves converted from sketch data.

The blend-file from the above example can be found
`here <https://archive.blender.org/wiki/2015/index.php/File:ManGreasePencilConvertToCurveDynamicExample.blend>`__.


## Index


###############
  Object Mode
###############

.. toctree::
   :maxdepth: 2

   convert_to_geometry.rst
   trace_image.rst


## Trace Image

.. _bpy.ops.gpencil.trace_image:

****************************
Trace Image to Grease Pencil
****************************

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Convert --> Trace Image to Grease Pencil`

The *Trace Image to Grease Pencil* tool traces a black and white image and generates Grease Pencil strokes.
If the image is not black and white, it will be internally converted.
For better results, convert the images manually to black and white.
Also try to keep the resolution of the image small; high resolutions can produce very dense strokes.


Usage
=====

#. Add an :ref:`Image Empty <bpy.types.Object.empty_image>` to the scene.
#. Run *Trace Image to Grease Pencil*.


Options
=======

Target Object
   The Grease Pencil object name. If left empty, a new Grease Pencil object will be created.

Thickness
   The thickness of the generated Grease Pencil strokes.

Resolution
   Resolution of the generated Grease Pencil strokes i.e. how many control points the stroke will have.
   A higher resolution will preserve more detail from the original image.

Scale
   The object scale applied to the generated Grease Pencil object.

Sample
   Recreates the stroke geometry with a predefined length between points.
   Smaller values will require more points to recreate the stroke,
   while larger values will result in fewer points needed to recreate the curve.
   A value of 0 disables stroke sampling.

Color Threshold
   Determine the :term:`Luminance` threshold above which strokes are generated.

Turn Policy
   Determines how to resolve ambiguities during decomposition of an image into paths.

   :Black:    Prioritizes to connect black (foreground) components.
   :White:    Prioritizes to connect white (background) components.
   :Left:     Always take a left turn.
   :Right:    Always take a right turn.
   :Minority: Prioritizes to connect the color (black or white) that occurs
              least frequently in the local neighborhood of the current position.
   :Majority: Prioritizes to connect the color (black or white) that occurs
              most frequently in the local neighborhood of the current position.
   :Random:   Choose pseudo-randomly.

Mode
   Determines if the image being traced is a single image or image sequence.

   :Single:   The image empty is a single image or the current frame of an image sequence.
   :Sequence: The image empty is an :ref:`Image Sequence <image-sequence>`.

Start at Current Frame
   When enabled, start the tracing process at the current image frame.

Trace Frame
   Used to trace only one frame of the image sequence, set to zero to trace all.


## Index


###############
  Sculpt Mode
###############

.. toctree::
   :maxdepth: 2

   introduction.rst
   tools.rst
   tool_settings/brush.rst


## Introduction


************
Introduction
************

*Sculpt Mode* is similar to *Edit Mode* in that it is used to alter the shape of a drawing,
but Sculpt Mode uses a very different workflow:
Instead of dealing with individual elements (points and edit lines),
an area of the model is altered using a brush.
In other words, instead of selecting a group of points,
Sculpt Mode manipulates the drawing in the brush region of influence.


Sculpt Mode
===========

.. figure:: /images/grease-pencil_modes_sculpting_introduction_mode-selector.png

   3D Viewport Mode selector: Sculpt Mode.

Sculpt Mode is selected from the *Mode* menu in the 3D Viewport header.
Once Sculpt Mode is activated, the Toolbar of the 3D Viewport will change to
Sculpt Mode specific panels.
A red circle will appear and follow the location of the cursor in the 3D Viewport.


Sculpting Options
=================

.. figure:: /images/grease-pencil_modes_sculpting_introduction_sculpting-options.png

   General sculpting options.

.. _bpy.types.ToolSettings.use_gpencil_select_mask_segment:

Selection Mask
   Sculpt Mode in Grease Pencil allows you to select points or strokes to restrict the effect
   of the sculpting tools to only a certain areas of your drawing.

   You can use the selection tools in the Toolbar for a quick selection.
   You can restrict sculpting only on the selected points or strokes with the Selection mode buttons.
   The three modes can be toggled with :kbd:`1`, :kbd:`2`, or :kbd:`3` respectively.

Multiframe
   Sometimes you may need to modify several frames at the same time with the sculpting tools.

   You can activate multiframe edition with the Multiframe button next to the modes selector (faded lines icon).
   See :doc:`Multiframe </grease_pencil/multiframe>` for more information.


Auto-Masking
============

.. reference::

   :Menu:      :menuselection:`Header --> Auto-Masking`
   :Shortcut:  :kbd:`Shift-Alt-A`

.. figure:: /images/grease-pencil_modes_sculpting_introduction_auto-masking.png

   Auto-Masking settings.

These properties automatically mask geometry based on stroke, layers and materials under the cursor.
It's an quick alternative to frequent manual masking.
These masks are initialized on every new tool usage. They are also never visible as an overlay.

These properties can be accessed via a :ref:`bpy.types.UIPieMenu` by pressing :kbd:`Shift-Alt-A`.

All auto-masking modes can be combined, which makes the generated auto-mask more specific.
For example it's possible to auto-mask strokes that use specific layer and material while excluding others.

.. _bpy.types.GPencilSculptSettings.use_automasking_stroke:

Strokes
   Only strokes that are under the cursor when you started the tool are affected.

.. _bpy.types.GPencilSculptSettings.use_automasking_layer_stroke:

Layer
   Only strokes on the same layers that are under the cursor when you started the tool are affected.

.. _bpy.types.GPencilSculptSettings.use_automasking_material_stroke:

Material
   Only materials with the same material that are under the cursor when you started the tool are affected.

.. _bpy.types.GPencilSculptSettings.use_automasking_layer_active:

Active Layer
   Only the strokes on the active layer are affected.

.. _bpy.types.GPencilSculptSettings.use_automasking_material_active:

Active Material
   Only the strokes with the active material are affected.


Keyboard Shortcuts
==================

- Invert stroke toggle :kbd:`Ctrl`
- Change active material :kbd:`U`


## Tools

.. _gpencil_sculpt-toolbar-index:

***************
Sculpting Tools
***************

For Grease Pencil sculpt modes each brush type is exposed as a tool,
the brush can be changed in the Tool Settings.
See :doc:`Brush </grease_pencil/modes/sculpting/tool_settings/brush>` for more information.

.. figure:: /images/grease-pencil_modes_sculpting_tools_brushes.png
   :align: right

Smooth
   Eliminates irregularities in the area of the drawing
   within the brush's influence by smoothing the positions of the points.

Thickness
   Increase or decrease the points thickness in the area of the drawing
   within the brush's influence.

Strength
   Increase or decrease the points transparency (alpha) in the area of the drawing
   within the brush's influence.

Randomize
   Add noise to the strokes in the area of the drawing
   within the brush's influence by moving points location in a random way.

Grab
   Used to drag a group of points around. Unlike the other brushes,
   Grab does not modify different points as the brush is dragged across the model.
   Instead, Grab selects a group of points on mouse-down, and pulls them to follow the mouse.
   The effect is similar to moving a group of points in Edit Mode with Proportional Editing enabled.

Push
   Moves points in the direction of the brush stroke.

Twist
   Twist the points in counter-clockwise (CCW) or Clockwise (CW) rotation.

Pinch/Inflate
   Pulls points towards the center of the brush.
   The inverse setting is Inflate, in which points are pushed away from the center of the brush.

Clone
   Adds copies of the strokes in the clipboard in the center of the brush.
   You have to copy the selected strokes you want into the clipboard with :kbd:`Ctrl-C` before using the tool.

:ref:`Annotate <tool-annotate-freehand>`
   Draw free-hand annotation.

   :ref:`Annotate Line <tool-annotate-line>`
      Draw straight line annotation.
   :ref:`Annotate Polygon <tool-annotate-polygon>`
      Draw a polygon annotation.
   :ref:`Annotate Eraser <tool-annotate-eraser>`
      Erase previous drawn annotations.


## Brush


**************
Brush Settings
**************

.. reference::

   :Mode:      Sculpt Mode
   :Panel:     :menuselection:`Sidebar --> Tool --> Brush Settings`

Radius
   This option controls the radius of the brush, measured in pixels.
   :kbd:`F` allows you to change the brush size interactively by
   dragging the mouse and then :kbd:`LMB` (the texture of the brush should be visible inside the circle).
   Typing a number then enter while using :kbd:`F` allows you to enter the size numerically.
   Brush size can be affected by enabling the pressure sensitivity icon,
   if you are using a :ref:`Graphics Tablet <hardware-tablet>`.

Strength
   Controls how much each application of the brush affects the model.
   For example, higher values cause the *Randomize* brush to add noise to the strokes more quickly,
   and cause the *Smooth* brush to soften the strokes more quickly.

   You can change the brush strength interactively by pressing :kbd:`Shift-F`
   in the 3D Viewport and then moving the brush and then :kbd:`LMB`.
   You can enter the size numerically also while in :kbd:`Shift-F` sizing.
   Brush strength can be affected by enabling the pressure sensitivity icon,
   if a supported tablet is being used.

Use Falloff
   When enabled, use Strength falloff for the brush.
   Brush Strength decays with the distance from the center of the brush.

Sculpt Strokes
   Filters the effect of the brush over the strokes.
   Applies to *Smooth* and *Randomize* brushes only.

   .. note::

      If there is no filter selected *Affect Position* is the default behavior.

   Affect Position
      Toggles the brush effect on the position of the stroke points.

   Affect Strength
      Toggles the brush effect on the strength (alpha) of the stroke points.

   Affect Thickness
      Toggles the brush effect on the thickness of the stroke points.

   Affect UV
      Toggles the brush effect on the UV rotation of the stroke points.

Direction
   The influence direction of the brush. This can be Add or Subtract.


Advanced
========

Auto-Masking
   Strokes
      Affect only strokes under the cursor.

   Material
      Affect only the active material.

   Layer
      Affect only the active layer.

Cursor
======

The cursor can be disabled by toggling the checkbox in the *Cursor* header.

Color
   Set the color of the brush ring. Depending on the current mode there will
   be options to set a single Color or a Color for Adding/Subtracting.


## Editing


*******
Editing
*******

.. _bpy.ops.gpencil.vertex_color_set:

Set Color Attribute
===================

.. reference::

   :Mode:      Vertex Paint Mode
   :Menu:      :menuselection:`Paint --> Set Color Attribute`

Sets the :ref:`active color <grease-pencil-vertex-paint-brush-color>` to all selected vertices.


.. _bpy.ops.gpencil.stroke_reset_vertex_color:

Reset Vertex Color
==================

.. reference::

   :Mode:      Vertex Paint Mode
   :Menu:      :menuselection:`Paint --> Reset Vertex Color`

Removes the Color Attribute information of the active strokes,
if no strokes are selected, all strokes are reset.


.. _bpy.ops.gpencil.vertex_color_invert:

Invert
======

.. reference::

   :Mode:      Vertex Paint Mode
   :Menu:      :menuselection:`Paint --> Invert`

Invert RGB values.


.. _bpy.ops.gpencil.vertex_color_levels:

Levels
======

.. reference::

   :Mode:      Vertex Paint Mode
   :Menu:      :menuselection:`Paint --> Levels`

Adjust the levels of Color Attributes.


.. _bpy.ops.gpencil.vertex_color_hsv:

Hue/Saturation/Value
====================

.. reference::

   :Mode:      Vertex Paint Mode
   :Menu:      :menuselection:`Paint --> Hue/Saturation/Value`

Adjust the color's HSV values.


.. _bpy.ops.gpencil.vertex_color_brightness_contrast:

Brightness/Contrast
===================

.. reference::

   :Mode:      Vertex Paint Mode
   :Menu:      :menuselection:`Paint --> Brightness/Contrast`

Adjust the color's brightness/contrast.


## Index


#####################
  Vertex Paint Mode
#####################

.. toctree::
   :maxdepth: 2

   introduction.rst
   tools.rst
   tool_settings/brush.rst
   editing.rst


## Introduction


************
Introduction
************

Vertex Painting is a simple way of painting color onto a Grease Pencil object,
by directly manipulating the color of points/vertices, rather than use only the materials base color.

.. figure:: /images/grease-pencil_modes_vertex-paint_introduction_sample.png

   Stroke with original base material color (left) and with vertex painting (right).

When a point is painted, the color of the points is mixing with the base material color according to
the settings of the brush.

.. note::

   A vertex in Grease Pencil is called point. Point and vertex names are equivalent.


Vertex Paint Mode
=================

Vertex Paint Mode is selected from the *Mode* menu in the 3D Viewport header.
Once Vertex Paint Mode is activated, the Toolbar of the 3D Viewport will change to Vertex Paint Mode specific panels.

.. figure:: /images/grease-pencil_modes_vertex-paint_introduction_mode-selector.png

   3D Viewport Mode selector set to Vertex Paint Mode.


Vertex Paint Options
====================

.. figure:: /images/grease-pencil_modes_vertex-paint_introduction_options.png

   General Vertex Paint options.

.. _bpy.types.ToolSettings.use_gpencil_vertex_select_mask_stroke:

Selection Mask
   Vertex Paint Mode in Grease Pencil allows you to select points or strokes to restrict the effect
   of the painting tools to only a certain areas of your drawing.

   You can use the selection tools in the Toolbar for a quick selections.

   You can restrict painting only on the selected points or strokes with the Selection mode toggle.
   The three modes can be toggled with :kbd:`1`, :kbd:`2`, or :kbd:`3` respectively.

Multiframe
   Sometimes you may need to modify several frames at the same time with the painting tools.

   You can activate multiframe edition with the Multiframe button next to the modes selector (faded lines icon).
   See :doc:`Multiframe </grease_pencil/multiframe>` for more information.


## Tools


******************
Vertex Paint Tools
******************

.. figure:: /images/grease-pencil_modes_vertex-paint_tools_brushes.png
   :align: right

Draw
   Paints a specified color over the object.

Blur
   Smooths out the colors of adjacent vertices. In this mode the Color
   Value is ignored. The strength defines how much the colors are blurred.

Average
   Smooths color by painting the average resulting color from all colors under the brush.

Smear
   Smudges colors by grabbing the colors under the brush and "dragging" them.
   This can be imagined as a finger painting tool.

Replace
   Change the color only to the stroke points that already have a color applied.

:ref:`Annotate <tool-annotate-freehand>`
   Draw free-hand annotation.

   :ref:`Annotate Line <tool-annotate-line>`
      Draw straight line annotation.
   :ref:`Annotate Polygon <tool-annotate-polygon>`
      Draw a polygon annotation.
   :ref:`Annotate Eraser <tool-annotate-eraser>`
      Erase previous drawn annotations.


## Brush


**************
Brush Settings
**************

Painting needs paint brushes and Blender provides a Brush panel within the Toolbar
when in *Vertex Paint Mode*.

Brush
   In the :ref:`Data-Block menu <ui-data-block>` you find predefined Brush presets.
   And you can create your own custom presets as needed.

Radius
   This option controls the radius of the brush, measured in pixels.
   :kbd:`F` allows you to change the brush size interactively by
   dragging the mouse and then :kbd:`LMB` (the texture of the brush should be visible inside the circle).
   Typing a number then enter while using :kbd:`F` allows you to enter the size numerically.

   Pressure
      Brush size can be affected by enabling the pressure sensitivity icon,
      if you are using a :ref:`Graphics Tablet <hardware-tablet>`.

Strength
   How powerful the brush is when applied.

   Pressure
      Strength can be affected by enabling the pressure sensitivity icon,
      if you are using a :ref:`Graphics Tablet <hardware-tablet>`.

Mode
   :Stroke: Only paint over strokes.
   :Fill: Only paint over fill areas.
   :Stroke & Fill: Paint over strokes and fill areas.

Cursor
   See the global brush settings for :doc:`Cursor </sculpt_paint/brush/cursor>` settings.


.. _grease-pencil-vertex-paint-brush-color:

Color Picker
============

The color of the brush. See :ref:`ui-color-picker`.

.. note::

   Note that Vertex Paint works in sRGB :term:`space <Color Space>`
   and the RGB representation of the same colors will be different between
   the paint tools and the materials that are in linear space.


Color Palette
=============

The active Color Palette. See :ref:`bpy.types.PaletteColor`.


Falloff
=======

See the global brush settings for :doc:`Falloff </sculpt_paint/brush/falloff>` settings.


## Index


#####################
  Weight Paint Mode
#####################

.. toctree::
   :maxdepth: 2

   introduction.rst
   tools.rst
   tool_settings/index.rst
   weights_menu.rst


## Introduction


************
Introduction
************

Assigning weight to the points is primarily used for rigging strokes in cut-out animation,
where the vertex groups are used to define the relative bone influences on the strokes.
See :doc:`Using Vertex Group </sculpt_paint/weight_paint/usage>` for more information.

.. note::

   A vertex in Grease Pencil is called point. Point and vertex names are equivalent.

Weight Painting is a method to maintain large amounts of weight information in an intuitive way.
The selected Grease Pencil object is displayed slightly shaded with a rainbow color spectrum.
The color visualizes the weights associated to each point in the active vertex group.
By default blue means unweighted and red means fully weighted.

You assign weights to the points of the object by painting on it with weight brushes.
Starting to paint on a strokes automatically adds weights to the active vertex group
(a new vertex group is created if needed).


Weight Paint
============

.. figure:: /images/grease-pencil_modes_weight-paint_introduction_mode-selector.png

   3D Viewport Mode selector: Weight Paint Mode.

Weight Paint Mode is selected from the *Mode* menu in the 3D Viewport header.
Once Weight Paint Mode is activated, the Toolbar of the 3D Viewport will change to Weight Paint Mode specific panels.
A red circle will appear and follow the location of the cursor in the 3D Viewport.


Weight Options
==============

Multiframe
   Sometimes you may need to assign weight to several frames at the same time with the Weight Paint tools.

   You can activate multiframe edition with the Multiframe button next to the modes selector (faded lines icon).
   See :doc:`Multiframe </grease_pencil/multiframe>` for more information.


## Tools

.. _gpencil_weight_paint-toolbar-index:

******************
Weight Paint Tools
******************

For Grease Pencil Weight Paint modes each brush type is exposed as a tool,
the brush can be changed in the Tool Settings.
See :doc:`Brush </grease_pencil/modes/weight_paint/tool_settings/brush>` for more information.

.. figure:: /images/grease-pencil_modes_weight-paint_tools_brushes.png
   :align: right

Draw
   Paints a specified weight over the strokes.

Blur
   Smooths out the weighting of adjacent points. In this mode the Weight
   Value is ignored. The strength defines how much the smoothing is applied.

Average
   Smooths weights by painting the average resulting weight from all weights under the brush.

Smear
   Smudges weights by grabbing the weights under the brush and "dragging" them.
   This can be imagined as a finger painting tool.

:ref:`Annotate <tool-annotate-freehand>`
   Draw free-hand annotation.

   :ref:`Annotate Line <tool-annotate-line>`
      Draw straight line annotation.
   :ref:`Annotate Polygon <tool-annotate-polygon>`
      Draw a polygon annotation.
   :ref:`Annotate Eraser <tool-annotate-eraser>`
      Erase previous drawn annotations.


## Weights Menu


************
Weights Menu
************

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Weights`

This page covers many of the tools in the *Weights* menu.


.. _bpy.ops.gpencil.weight_sample:

Sample Weight
=============

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Weights --> Sample Weight`
   :Shortcut:  :kbd:`Shift-X`

Adjust the Weight of the :doc:`Draw </grease_pencil/modes/weight_paint/tools>`
tool to the weight of the vertex under the mouse cursor.


.. _bpy.ops.gpencil.vertex_group_normalize_all:

Normalize All
=============

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Weights --> Normalize All`

For each point, this tool makes sure that the sum of the weights across all vertex groups is equal to 1.
It normalizes all of the vertex groups, except for locked groups, which keep their weight values untouched.

Lock Active
   Keep the values of the active group while normalizing all the others.


.. _bpy.ops.gpencil.vertex_group_normalize:

Normalize
=========

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Weights --> Normalize`

This tool only works on the active vertex group.
All points keep their relative weights, but the entire set of weights is scaled up
such that the highest weight value is 1.0.


.. _bpy.ops.gpencil.vertex_group_invert:

Invert
======

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Weights --> Invert`

Replaces each weight of the selected vertex group by × -1.0 weight.

Examples:

- Original 1.0 converts to 0.0
- Original 0.5 remains 0.5
- Original 0.0 converts to 1.0

Subset
   Restrict the tool to a subset.
   See :ref:`The Subset Option <bpy.ops.object.vertex_group_levels>` about how subsets are defined.
Add Weights
   Add vertices that have no weight before inverting (these weights will all be set to 1.0).
Remove Weights
   Remove vertices from the vertex group if they are 0.0 after inverting.


.. _bpy.ops.gpencil.vertex_group_smooth:

Smooth
======

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Weights --> Smooth`

Smooths the weights of the active vertex group.


.. _bpy.ops.gpencil.generate_weights:

Generate Weights
================

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Weights --> Generate Weights`

Generate automatic weight for armatures (requires an Armature modifier).

With Empty Group
   When parenting it will create an empty vertex groups on the child objects (if they do not exist already)
   for and named after each deforming bone in the armature.

With Automatic Weights
   Works similar to *With Empty Groups*, but it will not leave the vertex groups empty.
   It calculates how much influence a particular bone would have on points based on the distance
   from those points to a particular bone ("bone heat" algorithm).
   This influence will be assigned as weights in the vertex groups.


## Brush

.. _tool-grease-pencil-weight-paint-weight:

**************
Brush Settings
**************

Painting needs paint brushes and Blender provides a Brush panel within the Toolbar
when in *Weight Paint Mode*.

Brush
   In the :ref:`Data-Block menu <ui-data-block>` you find predefined Brush presets.
   And you can create your own custom presets as needed.

Radius :kbd:`F`
   The radius defines the area of influence of the brush.
Strength
   This is the amount of paint to be applied per brush stroke.
Use Falloff
   When enabled, use Strength falloff for the brush.
   Brush Strength decays with the distance from the center of the brush.
Weight :kbd:`Ctrl-F`
   The weight (visualized as a color) to be used by the brush.

   Using :kbd:`Ctrl-RMB` you can set the weight to the value thats under the cursor.
Direction :kbd:`D`
   Brush direction toggle, *Add* adds weight value while *Subtract* removes weight value.
   This setting can be toggled with :kbd:`D`.


## Index


#################
  Tool Settings
#################

.. toctree::
   :maxdepth: 2

   brush.rst
   options.rst


## Options


*******
Options
*******

Auto Normalize
   Ensures that all deforming vertex groups add up to one while painting.
   When this option is turned off, then all weights of a point can have any value between 0 and 1.
   However, when vertex groups are used as deform groups for character animation
   then Blender always interprets the weight values relative to each other.
   That is, Blender always does a normalization over all deform bones.
   Hence in practice it is not necessary to maintain a strict normalization and
   further normalizing weights should not affect animation at all.

   This option works most intuitively when used to maintain normalization while
   painting on top of weights that are already normalized with another tool.


## Index

.. _bpy.ops.object.gpencil_modifier:

#############
  Modifiers
#############

.. toctree::
   :maxdepth: 2

   introduction.rst

   generate/index.rst
   deform/index.rst
   color/index.rst
   modify/index.rst


## Introduction

.. index:: Grease Pencil Modifiers
.. index:: Modifiers; Grease Pencil Modifiers

************
Introduction
************

.. reference::

   :Panel:     :menuselection:`Properties --> Modifiers`

Grease Pencil has their own set of modifiers.
Modifiers are automatic operations that affect an object in a non-destructive way.
With modifiers, you can perform many effects automatically that would otherwise be
too tedious to do manually and without affecting the base geometry of your object.

They work by changing how an object is displayed and rendered, but not the geometry which you can edit directly.
You can add several modifiers to a single object forming the modifier stack
and *Apply* a modifier if you wish to make its changes permanent.

.. figure:: /images/grease-pencil_modifiers_introduction_menu.png

   Grease Pencil Modifiers menu.

There are three types of modifiers for Grease Pencil:

Modify
   These are tools similar to the Deform ones (see below), however, they usually do not directly
   affect the geometry of the object, but some other data, such as vertex groups.
Generate
   The *Generate* group of modifiers includes constructive tools that either change
   the general appearance of or automatically add new geometry to an object.
Deform
   The *Deform* group of modifiers only changes the shape of an object without adding new geometry,
Color
   The *Color* group of modifiers change the object color output.


.. _bpy.ops.object.gpencil_modifier_apply:

Interface
=========

.. figure:: /images/grease-pencil_modifiers_introduction_interface.png

   Panel layout (Thickness modifier as an example).

Each modifier's interface shares the same basic components like modifiers for meshes.

See :ref:`Modifiers Interface <bpy.types.Modifier.show>` for more information.

.. note::

   Grease Pencil strokes, unlike meshes, still can not be edited directly in the place.


.. _grease-pencil-modifier-influence-filters:

Influence Filters
-----------------

Most of the modifiers share some special properties that restrict the effect only to certain items.

Layer
   Restricts the effect only to one layer or to any layers that share the same
   material :ref:`Pass Index <bpy.types.MaterialGPencilStyle.pass_index>`.

Material
   Restricts the effect only to material that share the same material or
   material :ref:`Pass Index <bpy.types.MaterialGPencilStyle.pass_index>`.

Vertex Group
   Restricts the effect only to a vertex group.

Custom Curve
   When enabled, use a custom curve to shape the effect along the strokes
   from start to end points.

The Invert toggle ``<->`` allows you to reverse the filters behavior.


## Hue Saturation

.. index:: Grease Pencil Modifiers; Hue/Saturation Modifier
.. _bpy.types.ColorGpencilModifier:

***********************
Hue/Saturation Modifier
***********************

The *Hue/Saturation* Modifier applies a color transformation to the object output color.


Options
=======

.. figure:: /images/grease-pencil_modifiers_color_hue-saturation_panel.png
   :align: right

   Hue/Saturation Modifier.

Mode
   The color transformation will be applied on the stroke and/or the fill color.

   Stroke & Fill, Stroke, Fill

Hue
   Specifies the hue rotation of the image. 360° are mapped to (0 to 1).
   The hue shifts of 0 (-180°) and 1 (+180°) have the same result.
Saturation
   A saturation of 0 removes hues from the image, resulting in a grayscale image.
   A shift greater than 1.0 increases saturation.
Value
   Value is the overall brightness of the image.
   De/Increasing values shift an image darker/lighter.


Influence
---------

See :ref:`grease-pencil-modifier-influence-filters`.


## Index


#########
  Color
#########

.. toctree::
   :maxdepth: 1

   hue_saturation.rst
   opacity.rst
   tint.rst


## Opacity

.. index:: Grease Pencil Modifiers; Opacity Modifier
.. _bpy.types.OpacityGpencilModifier:

****************
Opacity Modifier
****************

The *Opacity* Modifier change the opacity (alpha) value of the stroke points.

The alpha value in Grease Pencil is stored per-point.
The modifier can alter these values to go from totally transparent points to totally opaque points.


Options
=======

.. figure:: /images/grease-pencil_modifiers_color_opacity_panel.png
   :align: right

   Opacity Modifier.

Mode
   The color transformation will be applied to the stroke/fill color or stroke Hardness.
   When Hardness is selected the opacity affects the stroke's transparency (alpha) from the center to the border.

   Stroke & Fill, Stroke, Fill, or Hardness

Uniform Opacity
   When enabled, makes the opacity equal for the entire strokes.

   Strength
      Absolute opacity for the stroke points.

Opacity Factor
   Controls the opacity value of the stroke points.
   A value of 1.0 respect the original alpha value of the points,
   a shift less than 1.0 make the points more transparent than originally,
   and a shift greater than 1.0 make the points more opaque than originally.

   Sets value to 2.0 makes the points alpha fully opaque.


Influence
---------

See :ref:`grease-pencil-modifier-influence-filters`.


Example
=======

.. list-table:: Opacity Factor samples.

   * - .. figure:: /images/grease-pencil_modifiers_color_opacity_factor-03.png
          :width: 200px

          Opacity Factor: 0.3.

     - .. figure:: /images/grease-pencil_modifiers_color_opacity_factor-1.png
          :width: 200px

          Opacity Factor: 1.0 (original alpha).

     - .. figure:: /images/grease-pencil_modifiers_color_opacity_factor-2.png
          :width: 200px

          Opacity Factor: 2.0 (fully opaque).


## Tint

.. index:: Grease Pencil Modifiers; Tint Modifier
.. _bpy.types.TintGpencilModifier:

*************
Tint Modifier
*************

The *Tint* Modifier colorize the original stroke or fill with a selected color.


Options
=======

.. figure:: /images/grease-pencil_modifiers_color_tint_panel.png
   :align: right

   Tint Modifier.

Mode
   The color transformation will be applied on the stroke and/or the fill color.

   Stroke & Fill, Stroke, Fill

Strength
   Controls the amount for the color mixing.

   A value of 0 respect the original stroke's color,
   a value of 1.0 totally replace the original color with the tint color.

   A shift greater than 1.0 will make the points alpha less transparent than originally (2.0 is fully opaque).

Tint Type
   :Uniform:
      Color
         Defines the tint color for mixing with the original color.
   :Gradient:
      Color Ramp
         Defines the tint gradient color for mixing with the original color.
         For controls see :ref:`ui-color-ramp-widget`.
      Object
         A :ref:`ui-data-id` to select an object (usually an empty),
         which position and rotation will be used to define the center of the effect.
      Radius
         Defines the maximum distance of the effect.


Influence
---------

See :ref:`grease-pencil-modifier-influence-filters`.


Example
=======

.. list-table:: Tint uniform color sample.

   * - .. figure:: /images/grease-pencil_modifiers_color_tint_factor-0.png
          :width: 200px

          Strength: 0 (original color).

     - .. figure:: /images/grease-pencil_modifiers_color_tint_factor-05.png
          :width: 200px

          Strength: 0.5.

     - .. figure:: /images/grease-pencil_modifiers_color_tint_factor-1.png
          :width: 200px

          Strength: 1.0 (fully tinted).

.. list-table:: Tint gradient color sample.

   * - .. figure:: /images/grease-pencil_modifiers_color_tint_gradient-01.png
          :width: 200px

          Radius: 1, Strength: 1.

     - .. figure:: /images/grease-pencil_modifiers_color_tint_gradient-02.png
          :width: 200px

          Radius: 5, Strength: 1.

     - .. figure:: /images/grease-pencil_modifiers_color_tint_gradient-03.png
          :width: 200px

          Radius: 10, Strength: 1.


## Armature

.. index:: Grease Pencil Modifiers; Armature Modifier
.. _bpy.types.ArmatureGpencilModifier:

*****************
Armature Modifier
*****************

The *Armature* Modifier is used for building skeletal systems for animating
the poses of characters and anything else which needs to be posed.

By adding an armature to an object,
this object can be deformed accurately so that geometry does not have to be animated by hand.

.. seealso::

   For more details on armatures usage, see the :doc:`armature section </animation/armatures/index>`.

.. seealso::

   This documentation refers to the Armature Modifier specific to the Grease Pencil object.
   For uses with other object types refer to the general :doc:`/modeling/modifiers/deform/armature`.


Options
=======

.. figure:: /images/grease-pencil_modifiers_deform_armature_panel.png
   :align: right

   The Armature modifier.

Object
   The name of the armature object used by this modifier.

Vertex Group
   The name of a vertex group of the object, the weights of which will be used to determine the influence of this
   Armature Modifier's result when mixing it with the results from other *Armature* ones.

   Only meaningful when having at least two of these modifiers on the same object,
   with *Multi Modifier* activated.

   Invert ``<->``
      Inverts the influence set by the vertex group defined in previous setting
      (i.e. reverses the weight values of this group).

Bind to
   Vertex Groups
      When enabled, bones of a given name will deform points which belong to
      :doc:`vertex groups </modeling/meshes/properties/vertex_groups/index>` of the same name.
      E.g. a bone named "forearm", will only affect the points in the "forearm" vertex group.

      The influence of one bone on a given point is controlled by the weight of this point in the relevant group.
      A much more precise method than *Bone Envelopes*, but also generally longer to set up.
   Bone Envelopes
      When enabled, bones will deform points or control points near them,
      defined by each bone's envelope radius and distance.
      Enable/Disable bone :ref:`envelopes <armature-bones-envelope>` defining the deformation
      (i.e. bones deform points in their neighborhood).


## Hook

.. index:: Grease Pencil Modifiers; Hook Modifier
.. _bpy.types.HookGpencilModifier:

*************
Hook Modifier
*************

The *Hook* Modifier is used to deform stroke points using another object
(usually an empty or a bone but it can be any object).

As the hook moves, it pulls points from the strokes with it.
You can think of it as animated
:doc:`Proportional Editing </editors/3dview/controls/proportional_editing>`.

.. seealso::

   This documentation refers to the Hook Modifier specific to the Grease Pencil object.
   For uses with other object types refer to the general :doc:`/modeling/modifiers/deform/hooks`.


Options
=======

.. figure:: /images/grease-pencil_modifiers_deform_hook_panel.png
   :align: right
   :width: 300px

   The Hook modifier.

Object
   The name of the object to hook points to.

Vertex Group
   Restricts the effect only to a vertex group.

Strength
   Adjust this hooks influence on the stroke points, were (0.0 to 1.0) (no change to fully follow the hook).


Falloff
-------

Type
   This can be used to adjust the type of curve for the Strength attenuation.
   You can also define a custom curve to get a much higher level of control.

Radius
   The size of the hooks influence.

Uniform Falloff
   This setting is useful when using hooks on scaled objects,
   especially in cases where non-uniform scale would stretch the result of the hook.


Influence
---------

See :ref:`grease-pencil-modifier-influence-filters`.

.. note::

   The Hook Modifier stores points indices from the original strokes to determine what to affect;
   this means that modifiers that generate geometry, like a Subdivision Surface Modifier,
   should always be applied **after** the Hook Modifier;
   otherwise the generated geometry will be left out of the hook's influence.


Example
=======

.. figure:: /images/grease-pencil_modifiers_deform_hook_sample.png

   Empty used as a hook to manipulate a vertex group (right eye of the monkey).


## Index


##########
  Deform
##########

.. toctree::
   :maxdepth: 1

   armature.rst
   hook.rst
   lattice.rst
   noise.rst
   offset.rst
   shrinkwrap.rst
   smooth.rst
   thickness.rst


## Lattice

.. index:: Grease Pencil Modifiers; Lattice Modifier
.. _bpy.types.LatticeGpencilModifier:

****************
Lattice Modifier
****************

The Lattice modifier deforms the base object according to
the shape of a :doc:`Lattice </animation/lattice>` object.

.. tip::

   A Lattice Modifier can quickly be added to selected objects by selecting them all,
   then selecting the lattice object last and pressing :kbd:`Ctrl-P` and choosing *Lattice Deform*.
   This will both add Lattice Modifiers to the selected objects and parent them to the lattice.

.. seealso::

   This documentation refers to the Lattice Modifier specific to the Grease Pencil object.
   For uses with other object types refer to the general :doc:`/modeling/modifiers/deform/lattice`.


Options
=======

.. figure:: /images/grease-pencil_modifiers_deform_lattice_panel.png
   :align: right

   Lattice Modifier.

Object
   The :doc:`Lattice </animation/lattice>` object with which to deform the base object.

Vertex Group
   Restricts the effect only to a vertex group.

Strength
   A factor to control blending between original and deformed points positions.


Influence
---------

See :ref:`grease-pencil-modifier-influence-filters`.


Example
=======

.. list-table:: Lattice modifier example.

   * - .. figure:: /images/grease-pencil_modifiers_deform_lattice_original.png
          :width: 320px

          Original model.

     - .. figure:: /images/grease-pencil_modifiers_deform_lattice_edit.png
          :width: 320px

          After lattice edition.


## Noise

.. index:: Grease Pencil Modifiers; Noise Modifier
.. _bpy.types.NoiseGpencilModifier:

**************
Noise Modifier
**************

The *Noise* Modifier changes the value of one or more stroke/points properties like:
location, strength, thickness or UV texture position
by adding varied values that make the line unstable and noisy.

Random values can be used for the noise factor for more vivid effects.


Options
=======

.. figure:: /images/grease-pencil_modifiers_deform_noise_panel.png
   :align: right

   Noise Modifier.

Position
   Strength of the noise effect over the point location.

Strength
   Strength of the noise effect over the point strength (opacity).

Thickness
   Strength of the noise effect over the point thickness.

UV
   Strength of the noise effect over the point UV rotation.

Noise Scale
   Control the noise frequency scale.

Noise Offset
   Moves the noise along the strokes.

Seed
   :term:`Seed` used by the pseudo-random number generator.


Randomize
---------

When enabled, the noise uses a random value over time.

Mode
   :Steps:
      New random value at defined steps.

      Step
         Number of frames before using a new random value.
   :Keyframes:
      New random value only on keyframes.


Influence
---------

See :ref:`grease-pencil-modifier-influence-filters`.


## Offset

.. index:: Grease Pencil Modifiers; Offset Modifier
.. _bpy.types.OffsetGpencilModifier:

***************
Offset Modifier
***************

The *Offset* Modifier changes the strokes location, rotation or scale
starting from the object origin.


Options
=======

.. figure:: /images/grease-pencil_modifiers_deform_offset_panel.png
   :align: right

   Offset Modifier.


General
-------

Location X, Y, Z
   Sets strokes location offset from its object origin.

Rotation X, Y, Z
   Sets strokes rotation.

Scale X, Y, Z
   Sets strokes scale.


Advanced
--------

Mode
   :Random: Add random values to the individual strokes offset.
   :Layer: Offset by layers.
   :Stroke: Offset by strokes (based on the stroke draw order).
   :Material: Offset by Materials.

Offset X, Y, Z
   Sets individual element location offset.

Rotation X, Y, Z
   Sets individual element rotation.

Scale X, Y, Z
   Sets individual element scale.

Uniform Scale (Random mode)
   Use the same random *Seed* for each scale axis in the strokes for a uniform scale.

Seed (Random mode)
   :term:`Seed` used by the pseudo-random number generator.

Layer/Stroke/Material Step (For Layer, Stroke and Material mode)
   The number of elements to be grouped and offset together.

Offset (For Layer, Stroke and Material mode)
   Offset the element starting point.


Influence
---------

See :ref:`grease-pencil-modifier-influence-filters`.


## Shrinkwrap

.. index:: Grease Pencil Modifiers; Shrinkwrap Modifier
.. _bpy.types.ShrinkwrapGpencilModifier:

*******************
Shrinkwrap Modifier
*******************

The *Shrinkwrap* modifier allows a Grease Pencil object to "shrink" to the surface of another object.
It moves each point of the object being modified to the closest position on the surface of the given mesh.

.. seealso::

   :doc:`Shrinkwrap Constraint </animation/constraints/relationship/shrinkwrap>`.

.. seealso::

   This documentation refers to the Shrinkwrap Modifier specific to the Grease Pencil object.
   For uses with other object types refer to the general :doc:`/modeling/modifiers/deform/shrinkwrap`.


Options
=======

.. figure:: /images/grease-pencil_modifiers_deform_shrinkwrap_nearest-surface-point.png
   :align: right
   :width: 300px

   The Shrinkwrap modifier in Nearest Surface Point mode.

Wrap Method
   This selector specifies the method to be used to determine the nearest
   point on the target's surface for each point of the modified object.
   Some options will add some extra, specific controls to the panel.
   See `Wrap Methods`_ for an explanation of each method.

Snap Mode
   Most modes support an additional setting to control how the point
   is moved to the target point selected by the methods described above.
   Some of the choices only differ if *Offset* is not zero.

   :On Surface:
      The point is always moved. The offset is applied along the projection line
      connecting the original point and selected target point towards the original position.
   :Inside:
      The point is not moved if it is already inside the target.
      Offset shrinks the allowed volume towards the inside along the projection line.
   :Outside:
      The point is not moved if it is already outside the target.
      Offset expands the exclusion volume towards the outside along the projection line.
   :Outside Surface:
      Like *On Surface*, but the offset is always applied towards the outside of the target.
   :Above Surface:
      Like *On Surface*, but the offset is applied along the smooth normal of the target.

   .. note::

      The *Inside* and *Outside* options can be used for very crude collision detection.
      The inside vs outside determination is done based on the target normal and
      is not always stable near 90 degree and sharper angles in the target mesh.

Target
   Shrink target, the mesh to shrink to/wrap around.

Offset
   The distance that must be kept from the calculated target position.

Smooth Factor
   Amount of smoothing to apply.

Repeat
   The number of time to apply smoothing.


Influence
---------

See :ref:`grease-pencil-modifier-influence-filters`.


Wrap Methods
============

Nearest Surface Point
---------------------

This will select the nearest point over the surface of the shrunk target.


Project
-------

.. figure:: /images/grease-pencil_modifiers_deform_shrinkwrap_project.png
   :align: right
   :width: 300px

   Project mode.

This will project vertices along a chosen axis until they touch the shrink target.
Vertices that never touch the shrink target are left in their original position.

Limit
   This is a distance limit between original point and surface.
   If the distance is larger than this limit point would not be projected onto the surface.

Subdivision Levels
   This applies a (temporary) *Catmull-Clark* subdivision to the modified object's geometry,
   before computing the wrap.

Axis
   Along which local axis of the modified object the projection is done.
   These options can be combined with each other, yielding a "median axis" of projection.
   If none are selected, the normal direction is used.

Negative/Positive
   This allows you to select the allowed direction(s) of the shrink along the selected axis.
   If both options are enabled, both ways are evaluated and the closest hit is selected.

Face Cull
   Allows you to prevent any projection over the "front side"
   (respectively the "back side") of the target's faces. The "side" of a face is determined
   by its normal (front being the side "from where" the normal "originates").

Invert Cull
   If *Cull Faces* is enabled, and *Negative* direction along axis is allowed,
   this option can be used to invert the *Front* or *Back* cull choice
   for the *Negative* direction. This is useful when projecting in both directions.

Auxiliary Target
   An additional object to project over.


Nearest Vertex
--------------

This will snap vertices to the nearest vertex of the shrunk target. It adds no extra options.

This method doesn't support the *Snap Mode* setting.


Target Normal Project
---------------------

This mode is similar to *Nearest Surface Point*, but produces a much smoother
projection in return for being significantly slower.

Instead of finding the closest point, it searches for the nearest point
that has its interpolated smooth normal pointing towards or away from the original point position.
Non-manifold boundary edges are specially handled as infinitely thin cylinders
that emit normals in all perpendicular directions; ignores flat shading.


## Smooth

.. index:: Grease Pencil Modifiers; Smooth Modifier
.. _bpy.types.SmoothGpencilModifier:

***************
Smooth Modifier
***************

The *Smooth* Modifier changes the value of one or more stroke/points properties like:
location, strength, thickness or UV texture position
trying to maintain similar values that make the line fluid and smoother.


Options
=======

.. figure:: /images/grease-pencil_modifiers_deform_smooth_panel.png
   :align: right

   Smooth Modifier.

Affect
   Combination of stroke/points properties that will be affected by the smooth factor.

   :Position:
      Smooth affect the point location.
   :Strength:
      Smooth affect the point strength (opacity).
   :Thickness:
      Smooth affect the point thickness.
   :UV:
      Smooth affect the point UV rotation.

Factor
   Strength of the smooth effect.

Repeat
   The number of smoothing iterations, equivalent to executing the Smooth tool multiple times.
   High values can reduce the animation performance (FPS).

Keep Shape
   When enabled, the smoothing algorithm will try to maintain as close as possible the overall
   shape of the original stroke.


Influence
---------

See :ref:`grease-pencil-modifier-influence-filters`.


## Thickness

.. index:: Grease Pencil Modifiers; Thickness Modifier
.. _bpy.types.ThicknessGpencilModifier:

******************
Thickness Modifier
******************

The *Thickness* Modifier change the stroke points thickness.


Options
=======

.. figure:: /images/grease-pencil_modifiers_deform_thickness_panel.png
   :align: right

   Thickness Modifier.

Uniform Thickness
   When enabled, makes the thickness equal for the entire strokes.

   Thickness
      Absolute Thickness for the stroke points.

Thickness Factor
   Value to add or subtract to the actual points thickness.


Influence
---------

See :ref:`grease-pencil-modifier-influence-filters`.


## Array

.. index:: Grease Pencil Modifiers; Array Modifier
.. _bpy.types.ArrayGpencilModifier:

**************
Array Modifier
**************

The *Array* modifier creates an array of copies of the base object, with each copy being offset from
the previous one in any of a number of possible ways.

Useful for creating complex repetitive drawings.

Multiple Array modifiers may be active for an object at the same time
(e.g. to create complex three-dimensional constructs).

.. seealso::

   This documentation refers to the Array Modifier specific to the Grease Pencil object.
   For uses with other object types refer to the general :doc:`/modeling/modifiers/generate/array`.


Options
=======

.. figure:: /images/grease-pencil_modifiers_generate_array_panel.png
   :align: right

   The Array modifier.

Count
   Total number of copies.

Material Override
   Index of the material to use on duplicated strokes (0 use strokes original materials).


Relative Offset
---------------

Factor X, Y, Z
   Adds a translation equal to the object's bounding box size along each axis,
   multiplied by a scaling factor, to the offset. X, Y and Z scaling factors can be specified.


Constant Offset
---------------

Factor X, Y, Z
   Adds a constant translation component to the duplicate object's offset.
   X, Y and Z constant components can be specified.


Object Offset
-------------

Distance X, Y, Z
   Adds a transformation taken from an object (relative to the current object) to the offset.
   It is good practice to use an empty object centered or near to the initial object.


Randomize
---------

Offset X, Y, Z
   Add random offset values to the copies.

Rotation X, Y, Z
   Add random rotation values to the copies.

Scale X, Y, Z
   Add random scale values to the copies.

Uniform Scale
   Use the same random *Seed* for each scale axis in the copies for a uniform scale.

Seed
   :term:`Seed` used by the pseudo-random number generator.

.. note::

   The *Depth Order* used in the Grease Pencil object has an influence on
   the visualization of the strokes when using the Array modifier.
   See :doc:`Depth Order </grease_pencil/properties/strokes>` for more information.


Influence
---------

See :ref:`grease-pencil-modifier-influence-filters`.


## Build

.. index:: Grease Pencil Modifiers; Build Modifier
.. _bpy.types.BuildGpencilModifier:

**************
Build Modifier
**************

The *Build* modifier make strokes appear or disappear in a frame range to
create the effect of animating lines being drawn or erased.

.. seealso::

   This documentation refers to the Build Modifier specific to the Grease Pencil object.
   For uses with other object types refer to the general :doc:`/modeling/modifiers/generate/build`.


Options
=======

.. figure:: /images/grease-pencil_modifiers_generate_build_panel.png
   :align: right

   The Build modifier.

Mode
   Determines how many strokes are being animated at a time.

   :Sequential:
      Strokes appear/disappear one after the other, but only a single one changes at a time.
   :Concurrent:
      Multiple stroke appear/disappear at a time.
   :Additive:
      Builds only the strokes that are new compared to last keyframe.
      The assumption is Additive Drawing was used so that the shared strokes are the same.

Transition *(in Sequential and Concurrent Mode)*
   Determines the animation type to build the strokes.

   :Grow:
      Shows points in the order they occur in each stroke, from first to last stroke.
      (Simulating lines being drawn.)
   :Shrink:
      Hide points from the end of each stroke to the start, from last to first stroke.
      (Simulating lines being erased.)
   :Vanish:
      Hide points in the order they occur in each stroke, from first to last stroke.
      (Simulating ink fading or vanishing after getting drawn.)

Timing
   The way you want to time the building of the strokes.

   :Natural Drawing Speed:
      Use the recorded speed of the stylus when the strokes were drawn.
      Only available in Sequential and Additive Mode.

      Speed Factor
         The recorded speed is multiplied by this value.
      Maximum Gap
         The maximum gap between strokes in seconds.

   :Number of Frames:
      Set a fixed maximum number of frames for the build animation.
      (Unless another Grease Pencil keyframe occurs before this time has elapsed.)

      Frames
         The maximum number of frames used.
      Delay
         Number of frames after each Grease Pencil keyframe before the modifier has any effects.

   :Percentage Factor:
      Manually set a percentage factor to control the amount of the strokes that are visible.

      Factor
         The factor from 0 to 1.

   :Time Alignment:
      Only available in Concurrent Mode.

      Align Start
         All stroke start at the same time (i.e. shorter strokes finish earlier).
      Align End
         All stroke end at the same time (i.e. shorter strokes start later).

Object
   Use the distance to an object to define the order in which strokes appear.


Custom Range
------------

If enabled, only modify strokes during the specified frame range.

Start, End
   Determines the start and end frame for the build effect.


Fade
----

Factor
   Defines how much the stroke is fading in/out.

Thickness
   How much strength fading is applied to the stroke's thickness.

Opacity
   How much strength fading applies to the stroke's opacity.

Weight Output
   Assign a weight value to points that have started/finished the fade.


Influence Filters
-----------------

See :ref:`grease-pencil-modifier-influence-filters`.


## Dash

.. index:: Grease Pencil Modifiers; Dot Dash Modifier
.. _bpy.types.DashGpencilModifier:

*****************
Dot Dash Modifier
*****************

The *Dot Dash* modifier generates dot dash segments from the original stroke.


Options
=======

.. figure:: /images/grease-pencil_modifiers_generate_dash_panel.png
   :align: right

   The Dot Dash modifier.

Offset
   Determines the starting offset of the pattern.

Segment
   Makes up individual stroke of a dot dash pattern.

   Use the plus/minus button on the side of the list to add/remove segments.

Dash
   The number of consecutive points from the original stroke to include in this segment.
Gap
   The number of points skipped after the segment ends.
Radius
   The factor to apply to the original point's radius for the new points.
Opacity
   The factor to apply to the original point's opacity for the new points.
Material Index
   Use this index on generated segment, use -1 for existing material.
Use Cyclic
   Close the segment.


Influence Filters
-----------------

See :ref:`grease-pencil-modifier-influence-filters`.


## Envelope

.. index:: Grease Pencil Modifiers; Envelope Modifier
.. _bpy.types.EnvelopeGpencilModifier:

*****************
Envelope Modifier
*****************

The *Envelope* modifier creates a shape known as envelope over the existing strokes
connecting all the points that have n points between them.


Options
=======

.. figure:: /images/grease-pencil_modifiers_generate_envelope_panel.png
   :align: right

   The Envelope modifier.

Mode
   :Deform: Replaces the original stroke with the envelope shape.
   :Segments: Add segments to create the envelope shape keeping the original stroke.
   :Fill: Add segments to create the envelope without the original stroke.

Spread Length
   The number of points to skip when creating the straight segments that define the envelope.

Thickness
   The thickness of the generated stroke segments.

Strength
   The Opacity of the generated stroke segments.

Material Index
   Defines the material to use on the generated stroke segments.

Skip Segments
   The Number of generated stroke segments to skip to reduce complexity.


Influence Filters
-----------------

See :ref:`grease-pencil-modifier-influence-filters`.


## Index


############
  Generate
############

.. toctree::
   :maxdepth: 1

   array.rst
   build.rst
   dash.rst
   envelope.rst
   length.rst
   line_art.rst
   mirror.rst
   multiple_strokes.rst
   outline.rst
   simplify.rst
   subdivide.rst


## Length

.. index:: Grease Pencil Modifiers; Length Modifier
.. _bpy.types.LengthGpencilModifier:

***************
Length Modifier
***************

The *Length* modifier can shrink or extend strokes.


Options
=======

.. figure:: /images/grease-pencil_modifiers_generate_length_panel.png
   :align: center

   The Length modifier.

Mode
   :Absolute: Length is in geometry space.
   :Relative: Length is in ratio to the stroke's length.

Start
   Added length to the start of the stroke. Negative value will shrink the stroke.

End
   Added length to the end of the stroke. Negative value will shrink the stroke.

Used Length
   Define what portion of the stroke is used to calculate the direction of the extension.


Curvature
---------

When enabled, the extension will follow the curvature of the stroke.

Point Density
   Multiplied by Start/End for the total point count.

Segment Influence
   Factor to determine how much the length of the individual segments
   should influence the final computed curvature. Higher factors makes
   small segments influence the overall curvature less.

Filter Angle
   Ignore points on the stroke that deviate from their neighbors by more
   than this angle when determining the extrapolation shape.

Invert
   Invert the curvature of the stroke's extension.


Random Offsets
--------------

Random Offset Start/End
   Size of random length added to the start/end of each stroke.

Random Noise Offset
   Smoothly offset each stroke's random value.

Seed
   Number used to generate different noise patterns.


Randomize
^^^^^^^^^

Re-randomizes values over time.

Step
   Number of frames before recalculate random values again.


Influence Filters
-----------------

See :ref:`grease-pencil-modifier-influence-filters`.


## Line Art

.. index:: Grease Pencil Modifiers; Line Art Modifier
.. _bpy.types.LineartGpencilModifier:

*****************
Line Art Modifier
*****************

The *Line Art* modifier generates stylized line art from a scene, collection, or object.

In order for the effects of the modifier to be visible, the scene must have an active camera.
The generated lines are only generated on portions of the object that a visible from this camera.

.. note::

   Due to lack of global cache at the moment, each Line Art modifier will run the entire
   occlusion calculation for itself. So if you have multiple line art modifiers to select
   different parts of the scene (to apply different styles, etc.), the evaluation will take much longer.
   There are plans to remedy this in the future, but this is a known limitation for now.


Options
=======

.. figure:: /images/grease-pencil_modifiers_generate_line-art_panel.png
   :align: right

   The Line Art modifier.

.. _bpy.types.LineartGpencilModifier.use_cache:

Use Cache
   Optimize rendering by using cached scene data from the first line art modifier in the stack.
   This option has the disadvantage of certain settings becoming unavailable.

   This option is only available when you have more than one Line Art modifier
   in the same modifier stack and the modifier is not the first Line Art modifier in the stack.

Source Type
   What type of geometry source should line art be generated from.

   Scene, Collection, Object

Object/Collection
   Based on the source type, collection or object can be selected as source geometry.

   .. _bpy.types.LineartGpencilModifier.use_invert_collection:

   Invert Collection Filtering
      Select everything except lines from specified collection.

.. note::

   Line Art will still load and calculate the entire visible scene to produce correct occlusion result,
   unless specified to do otherwise in object or collection Line Art *Usage* property.

Layer
   The Grease Pencil :ref:`bpy.types.GPencilLayer` to put the result in.

Material
   The Grease Pencil :ref:`bpy.types.MaterialGPencilStyle` to generate strokes with.

Line Thickness
   The strokes generated by line art are given this thickness.

Opacity
   The strokes generated by line art are given this Opacity.


Edge Types
----------

Line Art can identify different edge types. Selected edge types will be included in the result.

.. _bpy.types.LineartGpencilModifier.shadow_region_filtering:

Illumination Filtering
   Select feature lines that comes from lit or shaded regions.
   Will not affect cast shadow and light contour since they are at the border.

   :None: Not filtering any lines based on illumination region.
   :Illuminated: Only selecting lines from illuminated regions.
   :Shaded: Only selecting lines from shaded regions.
   :Illuminated (Enclosed Shapes):
      Selecting lines from lit regions, and make the combination of contour,
      light contour and shadow lines into enclosed shapes.

.. rubric:: Create

.. _bpy.types.LineartGpencilModifier.use_contour:
.. _bpy.types.LineartGpencilModifier.silhouette_filtering:
.. _bpy.types.LineartGpencilModifier.use_invert_silhouette:

Contour
   Generate strokes from contour lines.
   Where the edge becomes the separation line of front/backfacing faces.
   The silhouette can also be inverted by clicking the invert button.

   :Contour: Generate lines from contour.
   :Silhouette: Only generate lines from the silhouette of the source objects as a whole.
   :Individual Silhouette: Generate lines from the individual silhouettes of the source objects.

.. _bpy.types.LineartGpencilModifier.use_crease:

Crease
   Generate strokes where the edge angle is small enough.

   .. _bpy.types.LineartGpencilModifier.crease_threshold:

   Crease Threshold
      Angles smaller than this will be treated as creases.
      Crease angle priority: object line art crease override > line art default crease.

.. _bpy.types.LineartGpencilModifier.use_intersection:

Intersections
   Generate strokes where lines intersect between faces.

.. _bpy.types.LineartGpencilModifier.use_material:

Material Borders
   Generate strokes where the edge separates faces with different materials.

.. _bpy.types.LineartGpencilModifier.use_edge_mark:

Edge Marks
   Generate strokes from freestyle edge marks.

.. _bpy.types.LineartGpencilModifier.use_loose:

Loose
   Generate strokes for edges that do not form a :term:`Face`.

.. _bpy.types.LineartGpencilModifier.use_light_contour:

Light Contour
   Generate light/shadow separation lines from a reference
   :ref:`Light Object <bpy.types.LineartGpencilModifier.light_contour_object>`.

.. _bpy.types.LineartGpencilModifier.use_shadow:

Cast Shadow
   Project contour lines using a light source object.

.. rubric:: Options

.. _bpy.types.LineartGpencilModifier.use_overlap_edge_type_support:

Allow Overlapping Types
   Allow an edge to have multiple overlapping types.
   This will create a separate stroke for each overlapping type.


Light Reference
---------------

.. _bpy.types.LineartGpencilModifier.light_contour_object:

Light Object
   Use this light object to generate :ref:`Light Contour <bpy.types.LineartGpencilModifier.use_light_contour>`.

.. _bpy.types.LineartGpencilModifier.shadow_camera_size:

Shadow Camera Size
   This value represents the "Orthographic Scale" of an ortho camera.
   If the camera is put at the lamps position with this scale, it will represent the coverage of the shadow "camera".

.. _bpy.types.LineartGpencilModifier.shadow_camera_near:

Near
   Near clipping distance of shadow camera.

.. _bpy.types.LineartGpencilModifier.shadow_camera_far:

Far
   Far clipping distance of shadow camera


Geometry Processing
-------------------

.. _bpy.types.LineartGpencilModifier.source_camera:
.. _bpy.types.LineartGpencilModifier.use_custom_camera:

Custom Camera
   Use custom camera instead of the active camera for calculating strokes.
   Useful when baking multiple shots in different angles as well as for motion graphics effects.

Overlapping Edges as Contour
   This option allows overlapping edges (e.g. from an Edge Split modifier or imported geometry where
   two edges occupy the exact same space) to be drawn as contour. Enabling this option will slow down
   the calculation slightly but it will handle edge overlapping cases without erroneous occlusion results.

Instanced Objects
   This option enables particles and other instanced objects to be loaded for line art calculation.
   There will be performance impact when there are a large amount of instanced objects in the scene.

Clipping Boundaries
   When enabled, line art will generate clipping lines as contour type at the place
   where near or far clipping planes cut the model. Otherwise there will be no lines.

.. _bpy.types.LineartGpencilModifier.use_crease_on_smooth:

Crease on Smooth
   Allow crease edges to show inside smooth surfaces.

.. _bpy.types.LineartGpencilModifier.use_crease_on_sharp:

Crease on Sharp
   Allow creases to show on sharp edges.

.. _bpy.types.LineartGpencilModifier.use_back_face_culling:

Force Backface Culling
   Remove all back faces to speed up calculation.
   Note, removing back faces will create edges in different occlusion levels than when disabled.


Occlusion
---------

.. figure:: /images/grease-pencil_modifiers_generate_line-art_occlusion-panel.png
   :align: right

   Occlusion subpanel.

Range
   If enabled, the modifier will select lines that have an occlusion level between start and end values.

Level
   Desired occlusion level to be selected as line art result. A value of 0 means visible lines (no occlusion).
   A value of 1 means selecting lines that have been occluded by exactly one layer of faces.


Material Mask
^^^^^^^^^^^^^

If enabled, Line Art will only select lines that are occluded by certain faces whose material
have specific occlusion masks set.

Masks
   To select edges that have been occluded by the selected
   :ref:`Material Mask <bpy.types.MaterialLineArt.use_material_mask_bits>`.

Exact Match
   If enabled, only lines that are occluded with the exact mask bit combination will be selected.
   Otherwise, lines that have been occluded by any one of specified material masks will be selected.

.. figure:: /images/grease-pencil_modifiers_generate_line-art_transparency-mask.png
   :align: right

   Demonstration of the usage of material masks.


Intersection
------------

Allows you to select edges that intersect between two collections.

.. _bpy.types.LineartGpencilModifier.use_intersection_mask:

Collection Mask
   Mask bits to match from :ref:`Collection Line Art <bpy.types.Collection.lineart_intersection_mask>` properties.

.. _bpy.types.LineartGpencilModifier.use_intersection_match:

Exact Match
   Require matching all intersection masks instead of just one.

.. figure:: /images/grease-pencil_modifiers_generate_line-art_collection-mask.png

   Demonstration of the usage of collection masks.


.. _bpy.types.LineartGpencilModifier.use_face_mark:

Face Mark Filtering
-------------------

.. figure:: /images/grease-pencil_modifiers_generate_line-art_face-mark-filtering-panel.png

   Face Mark Filtering subpanel.

*Face Mark Filtering* can be used to have manual control over which
feature edges produce strokes by using Freestyle face marks.

.. _bpy.types.LineartGpencilModifier.use_face_mark_invert:

Invert
   Invert face mark filtering.

.. _bpy.types.LineartGpencilModifier.use_face_mark_boundaries:

Boundaries
   Filter feature lines based on face mark boundaries.

.. _bpy.types.LineartGpencilModifier.use_face_mark_keep_contour:

Keep Contour
   Preserve contour lines while filtering.

.. figure:: /images/grease-pencil_modifiers_generate_line-art_face-mark-filtering-example.png


Chaining
--------

.. figure:: /images/grease-pencil_modifiers_generate_line-art_chaining-panel.png
   :align: right

   Chaining subpanel.

Chain
   Intersection with Contour
      Allows intersection lines to be chained together with contour lines.

      .. note::

         Enabling this option will lead to ambiguity in intersection edge types.
         Intersection lines that have not been able to chain with any nearby contour lines will remain
         as intersection lines.

   All Lines
      Enabling this option will cause all lines to have the type of contour and to be chained together.

   Loose Edges
      Allow floating Edges that do not form a face to be chained together.

   Loose Edges as Contour
      Edges that do not form a face will be classified as contour lines.

   Preserve Details
      Instead of splitting at each occlusion change, keep small details from the initial chain.
      When details are not kept, will create a much smoother result.

   Geometry Space
      Use geometry distance for chaining instead of image space.

Image Threshold
   Allow the end point of short segments to be chained together if the 2D image space distance
   between them are within the specified threshold.

.. _bpy.types.LineartGpencilModifier.smooth_tolerance:

Smooth Tolerance
   The strength of smoothing applied on jagged chains.

Angle Splitting
   Split a chain at sharp "turning" points specified by this angle.


Vertex Weight Transfer
----------------------

.. figure:: /images/grease-pencil_modifiers_generate_line-art_vertex-weight-panel.png
   :align: right

   Vertex Weight Transfer subpanel.

Filter Source
   If source mesh has vertex groups whose name starts with this text, then the vertex weight info
   will be transferred into weight groups in Grease Pencil strokes.

Match Output
   Transfer the filtered object vertex weights into Grease Pencil weight groups with the same names
   as the filtered ones.

Target
   If *Match Output* is off, then a target vertex group has to be specified.
   If there are multiple weight groups copied into target, then the highest weight value is copied into it.


Composition
-----------

.. figure:: /images/grease-pencil_modifiers_generate_line-art_composition-panel.png

   Composition subpanel.

.. _bpy.types.LineartGpencilModifier.overscan:

Overscan
   To optimize rendering, Blender only renders the strokes for edges of the object that are in the camera's view.
   This optimization however, can result in strokes ending abruptly at the edge of the image.

   This value prevents this error by adding a margin outside the camera's view to continue computing strokes.

.. _bpy.types.LineartGpencilModifier.use_image_boundary_trimming:

Image Boundary Trimming
   Trim all stroke right at the boundary of image (including overscan region).

.. _bpy.types.LineartGpencilModifier.stroke_depth_offset:

Depth Offset
   Move strokes slightly towards the camera to avoid clipping while preserve depth for the viewport.
   This option is unavailable unless :ref:`Show in Front <bpy.types.Object.show_in_front>` is disabled.

.. _bpy.types.LineartGpencilModifier.use_offset_towards_custom_camera:

Towards Custom Camera
   Offset strokes towards selected camera (see *Custom Camera* above) instead of the active camera.


Bake
----

.. figure:: /images/grease-pencil_modifiers_generate_line-art_baking-panel.png
   :align: right

   Bake options.

Bake Line Art
   Bakes Line Art strokes for active Grease Pencil object within the *start*, *end* frame range in scene.
   Bake Line Art (All) bakes all Grease Pencil objects that contains at least one Line Art modifier.
   After baking, baked Line Art modifiers will be deactivated automatically.

Clear Baked Line Art
   Clears baked line art frames within the scene frame range for active Grease Pencil object.
   Clear Baked Line Art (All) applies the same operation for all Grease Pencil objects that
   contains at least one Line Art modifier.

   .. warning::

      If you have drawn anything manually in the frame range of where line art runs,
      this operation will also clear those strokes!

Continue without Clearing
   Re-activate a specific Line Art modifier without clearing baked strokes. This is useful for working
   on multiple portions of frames separately.


## Mirror

.. index:: Grease Pencil Modifiers; Mirror Modifier
.. _bpy.types.MirrorGpencilModifier:

***************
Mirror Modifier
***************

The *Mirror* modifier mirrors the strokes along its local X, Y and/or Z axes, across the :term:`Object Origin`.
It can also use another object as the mirror center, then use that object's local axes instead of its own.

.. seealso::

   This documentation refers to the Mirror Modifier specific to the Grease Pencil object.
   For uses with other object types refer to the general :doc:`/modeling/modifiers/generate/mirror`.


Options
=======

.. figure:: /images/grease-pencil_modifiers_generate_mirror_panel.png
   :align: right

   The Mirror modifier.

Axis
   The X, Y, Z axis along which to mirror, i.e. the axis perpendicular to the mirror plane of symmetry.

   To understand how the axis applies to the mirror direction, if you were to mirror on the X axis,
   the positive X values of the original stroke would become the negative X values on the mirrored side.

   You can select more than one of these axes. And will then get more mirrored copies.
   With one axis you get a single mirror, with two axes four mirrors, and with all three axes eight mirrors.

Object
   A :ref:`ui-data-id` to select an object (usually an empty),
   which position and rotation will be used to define mirror planes
   (instead of using the ones from the modified object).


Influence
---------

See :ref:`grease-pencil-modifier-influence-filters`.


## Multiple Strokes

.. index:: Grease Pencil Modifiers; Multiple Strokes
.. _bpy.types.MultiplyGpencilModifier:

****************
Multiple Strokes
****************

The *Multiple Strokes* modifier generate multiple parallel strokes around the original ones.


Options
=======

.. figure:: /images/grease-pencil_modifiers_generate_multiple-strokes_panel.png
   :align: right

   The Multiple Strokes modifier.

Duplicates
   The number of additional strokes.

Distance
   Distance between the original and the duplicate strokes.

Offset
   Control the offset position (inner or outer) for duplicate strokes.


Fade
----

When activated, the duplicate strokes fades out using their opacity or thickness.

Center
   Control the initial position for the fading.

Thickness
   Fade influence on strokes thickness.

Opacity
   Fade influence on strokes opacity.


Influence
---------

See :ref:`grease-pencil-modifier-influence-filters`.


## Outline

.. index:: Grease Pencil Modifiers; Outline Modifier
.. _bpy.types.OutlineGpencilModifier:

****************
Outline Modifier
****************

The *Outline* modifier convert strokes to outline tracing all strokes perimeter with new strokes.


Options
=======

.. figure:: /images/grease-pencil_modifiers_generate_outline_panel.png
   :align: right

   The Outline modifier.

Thickness
   The thickness of the generated strokes outline.

   Keep shape
      The perimeter strokes are maintaining inside the original stroke perimeter trying to keep the original shape.

Subdivisions
   controls the number of subdivision of the generated strokes outline.

Sample Length
   Controls the accuracy of the perimeter conversion.

Outline Material
   Defines the material to use on the generated strokes outline.

Target Object
   Controls the origin of the cyclic strokes generated.


Influence Filters
-----------------

See :ref:`grease-pencil-modifier-influence-filters`.


## Simplify

.. index:: Grease Pencil Modifiers; Simplify Modifier
.. _bpy.types.SimplifyGpencilModifier:

*****************
Simplify Modifier
*****************

The *Simplify* modifier allows you to reduce the amount of points in the strokes.
The goal of this modifier is reduce points while maintaining the lines shape.

Apply the modifier can help to obtain a better performance (more FPS) while animating.


Options
=======

.. figure:: /images/grease-pencil_modifiers_generate_simplify_panel.png
   :align: center

   The Simplify modifier.

Mode
   Determines how to reduce points in the strokes.

   :Fixed:
      Deletes alternated points in the strokes, except the start and end points.

      Iterations
         Number of times to repeat the procedure.

   :Adaptive:
      Uses the RDP algorithm (Ramer-Douglas-Peucker algorithm) for points deletion.
      The algorithm try to obtain a similar line shape with fewer points.

      Factor
         Controls the amount of recursively simplifications applied by the algorithm.

   :Sample:
      Recreates the stroke geometry with a predefined length between points.

      Length
         The distance between points on the recreated stroke.
         Smaller values will require more points to recreate the stroke,
         while larger values will result in fewer points needed to recreate the curve.

      Sharp Threshold
         Preserve corners that have sharper angle than this threshold.

   :Merge:
      Simplifies the strokes by merging points that are closer than a specified distance to each other.

      Distance
         Sets the distance threshold for merging points.


Influence
---------

See :ref:`grease-pencil-modifier-influence-filters`.


Example
=======

.. list-table:: Fixed Mode sample.

   * - .. figure:: /images/grease-pencil_modifiers_generate_simplify_fixed-iterations-0.png
          :width: 130px

          Original Model.

     - .. figure:: /images/grease-pencil_modifiers_generate_simplify_fixed-iterations-1.png
          :width: 130px

          Iteration: 1.

     - .. figure:: /images/grease-pencil_modifiers_generate_simplify_fixed-iterations-2.png
          :width: 130px

          Iteration: 2.

     - .. figure:: /images/grease-pencil_modifiers_generate_simplify_fixed-iterations-3.png
          :width: 130px

          Iteration: 3.

.. list-table:: Adaptive Mode sample.

   * - .. figure:: /images/grease-pencil_modifiers_generate_simplify_adaptive-factor-0.png
          :width: 130px

          Original Model.

     - .. figure:: /images/grease-pencil_modifiers_generate_simplify_adaptive-factor-01.png
          :width: 130px

          Factor: 0.1.

     - .. figure:: /images/grease-pencil_modifiers_generate_simplify_adaptive-factor-02.png
          :width: 130px

          Factor: 0.5.

     - .. figure:: /images/grease-pencil_modifiers_generate_simplify_adaptive-factor-05.png
          :width: 130px

          Factor: 1.


## Subdivide

.. index:: Grease Pencil Modifiers; Subdivide Modifier
.. _bpy.types.SubdivideGpencilModifier:

******************
Subdivide Modifier
******************

The *Subdivide* modifier subdivide the strokes by
inserting points between other points to the lines.


Options
=======

.. figure:: /images/grease-pencil_modifiers_generate_subdivide_panel.png
   :align: right

   The Subdivide modifier.

Subdivision Type
   :Catmull-Clark: Subdivides and smooths the surfaces.
   :Simple: Only subdivides the surfaces, without any smoothing.

Subdivisions
   Recursively adds more points.


Influence
---------

See :ref:`grease-pencil-modifier-influence-filters`.


## Index


##########
  Modify
##########

.. toctree::
   :maxdepth: 1

   texture_mapping.rst
   time_offset.rst
   weight_angle.rst
   weight_proximity.rst


## Texture Mapping

.. index:: Grease Pencil Modifiers; Texture Mapping Modifier
.. _bpy.types.TextureGpencilModifier:

************************
Texture Mapping Modifier
************************

The *Texture Mapping* Modifier change the strokes texture UV position.


Options
=======

.. figure:: /images/grease-pencil_modifiers_color_texture-mapping_panel.png
   :align: center

   Texture Mapping.

Mode
   The texture transformation will be applied to the stroke/fill or stroke UVs.

   :Stroke:
      Stroke Fit Method
         Selects the texture fitting method.

         :Constant Length: The texture keep a consistent length along the strokes.
         :Stroke Length: The texture is normalized to fit the stroke length.

      UV Offset
         Moves the texture along the strokes.

      Rotation
         Rotates the points of the strokes.

      .. note::

         The *Rotation* option is limited to a range of -90 to 90 degrees.

      Scale
         Factor for the texture scale.

   :Fill:
      Fill Rotation
         Sets the texture angle.

      Offset
         Moves the texture origin.

         X, Y

      Scale
         Factor for the texture scale.


Influence
---------

See :ref:`grease-pencil-modifier-influence-filters`.


Example
=======

.. list-table:: Opacity Factor samples.

   * - .. figure:: /images/grease-pencil_modifiers_color_texture-mapping_1.png
          :width: 200px

          Rotation: 0°.

     - .. figure:: /images/grease-pencil_modifiers_color_texture-mapping_2.png
          :width: 200px

          Rotation: 45°.

     - .. figure:: /images/grease-pencil_modifiers_color_texture-mapping_3.png
          :width: 200px

          Rotation: 90°.


## Time Offset

.. index:: Grease Pencil Modifiers; Time Offset Modifier
.. _bpy.types.TimeGpencilModifier:

********************
Time Offset Modifier
********************

The *Time Offset* Modifier applies a temporal offset to Grease Pencil keyframes on your timeline.
If you have duplicated a Grease Pencil object you can use the Time Offset Modifier on the copies to
desynchronize their animation. This can give more natural looking results.

Using the Time Offset Modifier it's possible to have Grease Pencil frame ranges play back as repeating loops.
Traditionally, 2D animation that uses looped drawings includes characters walking, rising smoke, and falling
rain.
In Fixed Frame mode the Time Offset Modifier can display drawings on your timeline entirely independently of
the playhead position.

Using the Time Offset Modifier it's possible to have Grease Pencil frame ranges play back as repeating loops.
Traditionally, 2D animation that uses looped drawings includes characters walking, rising smoke, and falling
rain.
In Fixed Frame mode the Time Offset Modifier can display drawings on your timeline entirely independently of
the playhead position.


This can be handy for displaying drawings that will appear often in your animation. Think of switching between
predefined mouth shapes for instance.


Options
=======

.. figure:: /images/grease-pencil_modifiers_deform_time-offset_panel.png
   :align: right

   Time Offset Modifier.

Mode
   :Regular:
      Offsets keyframes in the default animation playback direction (playhead moving from left to right).
   :Reverse:
      Offsets keyframes in reversed animation playback direction (playhead moving from right to left).
   :Fixed Frame:
      The Frame parameter determines which frame is displayed. This value needs to be animated in order to
      have the displayed frame change during playback.

      Frame
         The number of the frame to display.

   :Ping Pong:
      Loop back and forth animation.
   :Chain:
      It allows to combine the different Modes consecutively.

      Repeat
         Number of cycle repeats

Frame Offset
   The number of frames to offset the original keyframes by.

Scale
   Controls the speed of the frames playback. 1 is equal to the actual frame rate, could be positive (faster)
   or negative (slower).

Keep Loop
   Moves end frame to the animation start to keep animation in a loop.


Custom Range
------------

When enabled, the animation playback is restricted only to a frame range.

Frame Start/End
   Sets the range start and end frames.


Influence
---------

See :ref:`grease-pencil-modifier-influence-filters`.


## Weight Angle


****************************
Vertex Weight Angle Modifier
****************************

This modifier sets the weights of the given vertex group,
based on a predetermined angle.

.. warning::

   This modifier does implicit clamping of weight values in the standard (0.0 to 1.0) range.
   All values below 0.0 will be set to 0.0, and all values above 1.0 will be set to 1.0.


Options
=======

.. figure:: /images/grease-pencil_modifiers_modify_weight-angle_panel.png
   :align: center

   The Vertex Weight Proximity modifier panel.

Vertex Group
   The vertex group to affect.

   Invert ``<-->``
      Inverts the influence of the selected vertex group. The setting reverses the weight values of the group.

Angle
   Sets the angle for the maximum weights value.

Axis
   The axis along which the angle affects the weights.

   X, Y, Z

Space
   Coordinate space to be used.

Minimum
   Minimum value for vertex weight.

Multiply Weights
   Multiply the calculated weights with the existing values in the vertex group.


Influence
---------

See :ref:`grease-pencil-modifier-influence-filters`.


## Weight Proximity


********************************
Vertex Weight Proximity Modifier
********************************

This modifier sets the weights of the given vertex group,
based on the distance between the object (or its vertices),
and another target object (or its geometry).

.. warning::

   This modifier does implicit clamping of weight values in the standard (0.0 to 1.0) range.
   All values below 0.0 will be set to 0.0, and all values above 1.0 will be set to 1.0.

.. seealso::

   This documentation refers to the Vertex Weight Proximity Modifier specific to the Grease Pencil object.
   For uses with other object types refer to the general :doc:`/modeling/modifiers/modify/weight_proximity`.


Options
=======

.. figure:: /images/grease-pencil_modifiers_modify_weight-proximity_panel.png
   :align: right
   :width: 300px

   The Vertex Weight Proximity modifier panel.

Vertex Group
   The vertex group to affect.

   Invert ``<-->``
      Inverts the influence of the selected vertex group. The setting reverses the weight values of the group.

Target Object
   The object from which to compute distances.

Lowest
   Distance mapping to 0.0 weight.
Highest
   Distance mapping to 1.0 weight.

Minimum
   Minimum value for vertex weight.

Multiply Weights
   Multiply the calculated weights with the existing values in the vertex group.


Influence
---------

See :ref:`grease-pencil-modifier-influence-filters`.


## Data


***********
Object Data
***********

.. figure:: /images/grease-pencil_properties_data_panel.png
   :align: right

   Grease Pencil Object Data.

Grease Pencil
   The Grease Pencil :ref:`data-block menu <ui-data-block>` can be used to link the data between objects.


2D Layers
=========

Strokes can be grouped in 2D layers, a special Grease Pencil layers
that help to organize the drawing order and visibility of the strokes.

See :doc:`2D Layers </grease_pencil/properties/layers>` for more information.


Onion Skinning
==============

Onion skinning is used in animation to see several frames at once and make decisions or
edits based on how the previous/next frames are drawn.

See :doc:`Onion Skinning </grease_pencil/properties/onion_skinning>` for more information.


Vertex Groups
=============

Vertex groups can be used to assign a group or weighted group to some operator.
An object can have several weight groups and can be assigned in
:doc:`Weight Paint Mode </grease_pencil/modes/weight_paint/index>`.

See :doc:`Vertex Groups </modeling/meshes/properties/vertex_groups/index>` for more information.


Strokes
=======

General settings for Grease Pencil strokes.

See :doc:`Strokes </grease_pencil/properties/strokes>` for more information.


## Display


****************
Viewport Display
****************

.. figure:: /images/grease-pencil_properties_display_panel.png
   :align: right

   Viewport Display panel.

Display settings for Edit Lines in *Edit Mode* and *Sculpt Mode*.

.. _bpy.types.GreasePencil.edit_line_color:

Edit Line Color
   Sets the color of the Edit Lines.


.. _bpy.types.GreasePencilGrid:

Canvas
======

In 3D space sometimes is difficult to assess on which plane are you drawing.
The Canvas is a display overlay helper that shows a grid at the current *Drawing Plane*.
You can enable the Canvas visualization in the :ref:`Viewport Overlays <3dview-overlay-grease-pencil>`.

See :doc:`Drawing Plane </grease_pencil/modes/draw/drawing_planes>` for more information.

.. _bpy.types.GreasePencilGrid.color:

Color
   Color of the Canvas grid lines.

.. _bpy.types.GreasePencilGrid.scale:

Scale X/Y
   Defines the X and Y scale of the Canvas.

.. _bpy.types.GreasePencilGrid.offset:

Offset X/Y
   Sets the Canvas position offset from the object's origin.

.. _bpy.types.GreasePencilGrid.lines:

Subdivisions
   Specifies the number of subdivisions to use for the grid.

.. figure:: /images/grease-pencil_properties_display_canvas.png
   :align: right

   Canvas example on the XZ drawing plane using a green color grid.


## Index

.. _bpy.types.GPencilSculptSettings:

##############
  Properties
##############

.. toctree::
   :maxdepth: 2

   data.rst
   layers.rst
   masks.rst
   onion_skinning.rst
   strokes.rst
   display.rst


## Layers

.. _bpy.types.GPencilLayer:

******
Layers
******

.. reference::

   :Mode:      All Modes
   :Panel:     :menuselection:`Object Data tab --> Layers`
   :Shortcut:  :kbd:`Y`


Layers List
===========

.. figure:: /images/grease-pencil_properties_layers_panel.png
   :align: right

   Grease Pencil Layers panel.

Grease Pencil objects each have a list of 2D layers for grouping and arranging strokes
in a :ref:`List view <ui-list-view>`. Any stroke can only belong to a single 2D layer.
There is always only one active layer in the list (the selected one).
When you draw, the new strokes are added to the active layer.
By default the view order of the layers in the viewport is top to bottom.

Every layer correspond to a channel in the Dope Sheet editor (in Grease Pencil mode).
See :doc:`Dope Sheet </editors/dope_sheet/modes/grease_pencil>` for more information.

Layers can also be used together with Modifiers to only affects part of your drawing.
See :doc:`Modifiers </grease_pencil/modifiers/introduction>` for more information.

.. tip::

   Sometimes the layers you are not working on can be a distraction.
   Activate *Fade Inactive Layers* in overlays to control the opacity of the non-active layers.
   See :doc:`Overlays </editors/3dview/display/overlays>` for more information.

Next to the layer name there are four icons buttons that control common properties of the layer:

.. _bpy.types.GPencilLayer.use_mask_layer:

Use Mask (mask icon)
   Toggle the affect of :doc:`Masks </grease_pencil/properties/masks>` on the layer.

.. _bpy.types.GPencilLayer.use_onion_skinning:

Onion Skinning (onion skin icon)
   Toggle using the layer for :doc:`Onion Skinning </grease_pencil/properties/onion_skinning>`.

.. _bpy.types.GPencilLayer.hide:

Hide (eye icon)
   Toggle layer visibility in the viewport and in render.

.. _bpy.types.GPencilLayer.lock:

Lock (padlock icon)
   Toggle layer from being editable.

----

Layer Specials
   Operators for working with layers.

   .. _bpy.ops.gpencil.layer_duplicate:

   Duplicate Layer
      Makes an exact copy of the selected layer appending a number to differentiate its name.

   Duplicate Empty Keyframes
      Makes a copy of the selected layer but with empty keyframes.
      Useful to easily have empty keyframes preset to work on the cleanup or filling process.

   .. _bpy.ops.gpencil.reveal:

   Show All
      Turns on the visibility of every layer in the list.

   Hide Others
      Turns off the visibility of every layer in the list except the active one.

   Lock All
      Locks edition of all the layers in the list.

   Unlock All
      Unlocks edition of all the layers in the list.

   Autolock Inactive Layer
      Locks automatically the edition of every layer in the list except the active one.
      This way you avoid to make unwanted changes in other layers without the need to lock them every time.

   Disallow Locked Materials Editing
      Avoids editing locked materials in the layer. When disabled,
      any material can be edited even if they are locked in the material list.

   .. _bpy.ops.gpencil.layer_merge:

   Merge Down :kbd:`Shift-Ctrl-M`
      Combine the selected layer with the layer below, the new layer keeps the name of the lower layer.

   Merge All
      Combine all layers into the active layer.

   Copy Layer to Selected
      Copy the active layer to the selected Grease Pencil object.

   Copy All Layers to Selected
      Copy all layers to the selected Grease Pencil object.

.. _bpy.ops.gpencil.layer_isolate:

Visibility (screen icon)
   Toggle whether the active layer is the only one that can be edited and is visible.

Isolate Lock (padlock icon)
   Toggle whether the active layer is the only one that can be edited.

----

Below the layers list there are additional common settings:

.. _bpy.types.GPencilLayer.blend_mode:

Blend
   The layer blending operation to perform. See :term:`Color Blend Modes`.

.. _bpy.types.GPencilLayer.opacity:

Opacity
   Used to set the opacity of the layer.

.. _bpy.types.GPencilLayer.use_lights:

Use Lights
   When enabled, the layer is affected by lights.


Masks
=====

In a :ref:`List view <ui-list-view>` of layers affected by a layer mask.
See :doc:`Masks </grease_pencil/properties/masks>` for more information.


.. _bpy.types.GPencilLayer.location:
.. _bpy.types.GPencilLayer.rotation:
.. _bpy.types.GPencilLayer.scale:

Transform
=========

Allows per-layer location, rotation and scale transformations.


Adjustments
===========

.. figure:: /images/grease-pencil_properties_layers_adjustment.png
   :align: right

   Layers adjustment panel.

.. _bpy.types.GPencilLayer.tint_color:

Tint Color
   Color that tint any material colors used in the layer.

.. _bpy.types.GPencilLayer.tint_factor:

Factor
   Controls the amount of tint color to apply.

.. _bpy.types.GPencilLayer.line_change:

Stroke Thickness
   Thickness value that override the strokes thickness in the layer.


Relations
=========

.. _bpy.types.GPencilLayer.parent:
.. _bpy.types.GPencilLayer.parent_type:

Parent/Type
   Select a Parent object and Type to manipulate the layer.
   The layer will inherit the transformations of the parent,
   this is especially useful when rigging for cut-out animation.

.. _bpy.types.GPencilLayer.pass_index:

Pass Index
   The layer index number can be used with some modifiers to restrict changes to only certain areas.

   See :doc:`Modifiers </grease_pencil/modifiers/introduction>` for more information.

.. _bpy.types.GPencilLayer.viewlayer_render:

View Layer
   Defines the View Layer to use for the Grease Pencil layer.
   If empty, the layer will be included in all View Layers.
   This is useful to separate drawings parts for :doc:`compositing </compositing/introduction>`.

.. _bpy.types.GPencilLayer.use_viewlayer_masks:

Disable Masks in Render
   If enabled no masks on the layer are included in the view layer render.


Display
=======

.. _bpy.types.GPencilLayer.channel_color:

Custom Channel Color
   Sets the color to use in the channel region of the :doc:`Dope Sheet </editors/dope_sheet/modes/grease_pencil>`.

.. _bpy.types.GPencilLayer.use_solo_mode:

Show Only On Keyframed
   Makes the layer visible in the viewport only if it has a keyframe in the actual frame.
   This helps for example when you are in the inking process using the *Fill* tool and want to only see
   the strokes that are in the actual frame to avoid fill in unwanted regions.


## Masks


*****
Masks
*****

Layers List
===========

.. figure:: /images/grease-pencil_properties_masks_layers-panel.png
   :align: right

   Layer list with masked layers.

In Grease Pencil there are no special mask layers, any layer can act as a mask for other layers.
The mask system is flexible enough to allow top-bottom and bottom-top masking.

Layers used as mask can use all the blend modes and different opacity values like any other layer.

.. note::

   If you want to make a full transparent masking
   you will have to set the mask layer(s) opacity to 0.

By activating the mask toggle (mask icon) next to the layer name or
using the checkbox on the masks panel header
the layer becomes prepared to be masked by other layer(s).

.. figure:: /images/grease-pencil_properties_masks_panel.png
   :align: right

   Masks list view.


Masks List
==========

The layer/s that will act as mask of the current layer could be added
to the Mask :ref:`list view <ui-list-view>`.

In the Masks list next to the layers name there are two icons buttons that control
common properties of the layer mask:

Invert (mask icon)
   Inverts the mask.

Viewport/Render Visibility (eye icon)
   Toggle layer visibility in the viewport and in render.


Example
=======

.. list-table:: Mask (green circle) samples.

   * - .. figure:: /images/grease-pencil_properties_masks_example-01.png
          :width: 200px

          Original image (Blend: Regular, Opacity: 1).

     - .. figure:: /images/grease-pencil_properties_masks_example-02.png
          :width: 200px

          Blend: Hard Light, Opacity: 1.

     - .. figure:: /images/grease-pencil_properties_masks_example-03.png
          :width: 200px

          Blend: Regular, Opacity: 1.


## Onion Skinning


**************
Onion Skinning
**************

Onion Skinning show ghosts of the keyframes before and after the current frame allowing animators
to make decisions in the animation sequence.

The main switch to show/hide Onion Skinning is in the :ref:`Viewport Overlays <3dview-overlay-grease-pencil>`,
but Grease Pencil Onion Skinning is per-layer and the visibility can be toggle in the layer list.
See :doc:`2D Layers </grease_pencil/properties/layers>` for more information.

.. figure:: /images/grease-pencil_properties_onion-skinning_panel.png
   :align: center

   Onion Skinning panel.


Options
=======

.. _bpy.types.GreasePencil.onion_mode:

Mode
   :Keyframes: Shows Keyframes in the range determined by the *Before*/*After* settings.
   :Frames: Shows Frames in the range determined by the *Before*/*After* settings.
   :Selected: Shows only on the manually selected keyframes in the Dope Sheet.

.. _bpy.types.GreasePencil.onion_factor:

Opacity
   Control the opacity of the ghost frames.

.. _bpy.types.GreasePencil.onion_keyframe_type:

Filter by Type
   Filters what type of frames to show in the Onion Skinning range.

.. _bpy.types.GreasePencil.ghost_before_range:
.. _bpy.types.GreasePencil.ghost_after_range:

Keyframes Before/After
   Sets how many frames or keyframes, depending on the *Mode*, to show before and after the current frame.


Custom Colors
=============

.. _bpy.types.GreasePencil.before_color:
.. _bpy.types.GreasePencil.after_color:

Before/After
   Color to use before and after the current frame on ghost frames.


Display
=======

.. _bpy.types.GreasePencil.use_ghosts_always:

View in Render
   Show the onion skinning in final render image e.g. for a motion blur effect.

.. _bpy.types.GreasePencil.use_onion_fade:

Fade
   Opacity of the ghosts frames decrease the further away from the current frame.

.. _bpy.types.GreasePencil.use_onion_loop:

Show Start Frame
   Help working on loop animations showing the first keyframe/frame
   as ghost when you are on the last frame of your animation.

.. figure:: /images/grease-pencil_properties_onion-skinning_example.png

   An example of Onion Skinning activated.


## Strokes


*******
Strokes
*******

General settings for Grease Pencil strokes.

.. figure:: /images/grease-pencil_properties_strokes_panel.png
   :align: center

   Strokes panel.

.. _bpy.types.GreasePencil.stroke_depth_order:

Stroke Depth Order
   Defines how the strokes are ordered in 3D space (for objects not displayed *In Front*).

   :2D Layers:
      The Strokes drawing order respect the order of the 2D layers list (top to bottom)
      and ignores the real position of the strokes in 3D space.
      See :doc:`2D Layers </grease_pencil/properties/layers>` for more information.
   :3D Location:
      The strokes drawing order is based on the stroke location in 3D space.

   .. list-table::

      * - .. figure:: /images/grease-pencil_properties_strokes_depth-order-2d.png
            :width: 320px

            Blue, Green and Red strokes in three different layers using 2D Layers depth order.

        - .. figure:: /images/grease-pencil_properties_strokes_depth-order-3d.png
             :width: 320px

             Blue, Green and Red strokes in three different layers using 3D Location depth order.

.. _bpy.types.GreasePencil.stroke_thickness_space:

Stroke Thickness
   The basis for how the stroke thickness is calculated.

   :World Space:
      The thickness is relative to world space.
      Stroke thickness change with the screen zoom factor.
   :Screen Space:
      The thickness is relative to screen space.
      Stroke thickness remains the same regardless of the screen zoom factor.

.. _bpy.types.GreasePencil.pixel_factor:

Thickness Scale
   Sets a thickness scale factor for all strokes.

Curve Resolution
   See :ref:`Curve Editing <bpy.types.GreasePencil.edit_curve_resolution>` for more information.


## Blur

.. index:: Grease Pencil Visual Effects; Blur Visual Effect
.. _bpy.types.ShaderFxBlur:

******************
Blur Visual Effect
******************

The *Blur* Visual Effect applies a Gaussian blur to the object.


Options
=======

.. figure:: /images/grease-pencil_visual-effects_blur_panel.png
   :align: right

   Blur Visual Effect.

Samples
   Number of blur samples (0 disabled the blur effect).

Use Depth of Field
   When enabled, the blur effect uses the focal plane distance of the actual camera to
   calculate the object blur. Only available in camera view.

Size
   Control the blur scale in pixels on the X and Y axis.

   X, Y

Rotation
   Control the Rotation of the blur.


Example
=======

.. list-table:: Blur Effect samples (Samples: 8).

   * - .. figure:: /images/grease-pencil_visual-effects_blur_factor-0.png
          :width: 200px

          Original Model.

     - .. figure:: /images/grease-pencil_visual-effects_blur_factor-10.png
          :width: 200px

          Factor: 10, 10.

     - .. figure:: /images/grease-pencil_visual-effects_blur_factor-50.png
          :width: 200px

          Factor: 50, 50.

     - .. figure:: /images/grease-pencil_visual-effects_blur_factor-100.png
          :width: 200px

          Factor: 100, 100.


## Colorize

.. index:: Grease Pencil Visual Effects; Colorize Visual Effect
.. _bpy.types.ShaderFxColorize:

**********************
Colorize Visual Effect
**********************

The *Colorize* Visual Effect applies different preset colorizing effects to the object.


Options
=======

.. figure:: /images/grease-pencil_visual-effects_colorize_panel.png
   :align: right

   Blur Visual Effect.

Mode
   Grayscale
      Converts to a grayscale image.
   Sepia
      Converts to a sepia tone image.
   Duotone
      Converts to a posterize image with high contrast and brightness.

      Low Color
         Primary color.

      High Color
         Secondary color.
   Transparent
      Add color transparency.
   Custom
      Allows to define a tint custom color.

      Color
         Sets the tint color.

Factor
   Control the mix value.


Example
=======

.. list-table:: Colorize Effect samples.

   * - .. figure:: /images/grease-pencil_visual-effects_colorize_grayscale.png
          :width: 200px

          Mode: Grayscale.

     - .. figure:: /images/grease-pencil_visual-effects_colorize_sepia.png
          :width: 200px

          Mode: Sepia.

     - .. figure:: /images/grease-pencil_visual-effects_colorize_duotone.png
          :width: 200px

          Mode: Duotone.

     - .. figure:: /images/grease-pencil_visual-effects_colorize_transparent.png
          :width: 200px

          Mode: Transparent.


## Flip

.. index:: Grease Pencil Visual Effects; Flip Visual Effect
.. _bpy.types.ShaderFxFlip:

******************
Flip Visual Effect
******************

The *Flip* Visual Effect shows the object flipped horizontally and/or vertically.


Options
=======

.. figure:: /images/grease-pencil_visual-effects_flip_panel.png
   :align: right

   Flip Visual Effect.

Axis
   Which axis or axes to flip the object about.

   :Horizontal: When enabled, shows the object flipped horizontally.
   :Vertical: When enabled, shows the object flipped vertically.


## Glow

.. index:: Grease Pencil Visual Effects; Glow Visual Effect
.. _bpy.types.ShaderFxGlow:

******************
Glow Visual Effect
******************

The *Glow* Visual Effect add a glowing rim around the object.


Options
=======

.. figure:: /images/grease-pencil_visual-effects_glow_panel.png
   :align: center

   Glow Visual Effect.

Mode
   Determines the mode for the glow effect.

   :Luminance:
      The glow light illuminates the entire object.
   :Color:
      The glow light only affect a single color.

      Select Color
         Allows to select a single color to apply the glow light.

Threshold
   Limits the colors affected by the glow light. (A value of 1 means no colors affected.)

Glow Color
   Defines the glow color.

Blend Mode
   The mask blending operation to perform. See :term:`Color Blend Modes`.

Opacity
   Control the Opacity of the glow over the object.

Size X, Y
   Control the glow scale in pixels on the X and Y axis.

Rotation
   Control the Rotation of the glow.

Samples
   Number of Blur samples (0 disabled the blur effect).

Glow Under
   When enabled, glow only affects alpha areas.


Example
=======

.. list-table:: Glow Effect samples.

   * - .. figure:: /images/grease-pencil_visual-effects_glow_original.png
          :width: 200px

          Original image.

     - .. figure:: /images/grease-pencil_visual-effects_glow_luminance.png
          :width: 200px

          Mode: Luminance.

     - .. figure:: /images/grease-pencil_visual-effects_glow_luminance-alpha.png
          :width: 200px

          Mode: Luminance (Glow Under).

     - .. figure:: /images/grease-pencil_visual-effects_glow_color.png
          :width: 200px

          Mode: Color (Black lines).


## Index

.. _bpy.types.ShaderFx:

##################
  Visual Effects
##################

.. toctree::
   :maxdepth: 2

   introduction.rst


Types
=====

.. toctree::
   :maxdepth: 1

   blur.rst
   colorize.rst
   flip.rst
   glow.rst
   pixelate.rst
   rim.rst
   shadow.rst
   swirl.rst
   wave_distortion.rst


## Introduction

.. index:: Grease Pencil Visual Effects

************
Introduction
************

.. reference::

   :Panel:     :menuselection:`Properties --> Visual Effects`

Grease Pencil has a special set of viewport real-time visual effects that can be apply to the object.

These effects treat the object as if it was just an image, for that reason they
have effect on the whole object and cannot limit their influence
on certain parts like layers, materials or vertex group as with modifiers.
Also unlike modifiers, they can not be applied to the object.

Their main purpose is to have a quick way to apply visual effects on your drawings
like blurring, pixelation, wave distortion, among others.

.. note::

   Visual Effects best fit for quick viewport visualization. You can use it for final renders
   but if you want more precision with effects it is still recommended to use
   the :doc:`Compositor </compositing/introduction>`.


Interface
=========

.. figure:: /images/grease-pencil_visual-effects_introduction_interface.png

   Panel layout (Blur effect as an example).

The visual effects panels and interface are similar to modifiers.
Each effect shares the same basic interface components similar to modifiers for meshes.

See :ref:`Modifiers Interface <bpy.types.Modifier.show>` for more information.


## Pixelate

.. index:: Grease Pencil Visual Effects; Pixelate Visual Effect
.. _bpy.types.ShaderFxPixelate:

**********************
Pixelate Visual Effect
**********************

The *Pixelate* Visual Effect shows the object as a pixelated image.


Options
=======

.. figure:: /images/grease-pencil_visual-effects_pixelate_panel.png
   :align: right

   Pixelate Visual Effect.

Size X, Y
   Horizontal and vertical size of the final pixels to apply.

Anti-aliasing
   Applies an anti-aliasing effect to the resulting pixels.


Example
=======

.. list-table:: Pixelate Effect samples.

   * - .. figure:: /images/grease-pencil_visual-effects_pixelate_size-0.png
          :width: 200px

          Original image.

     - .. figure:: /images/grease-pencil_visual-effects_pixelate_size-20.png
          :width: 200px

          Size: 20 px.

     - .. figure:: /images/grease-pencil_visual-effects_pixelate_size-100.png
          :width: 200px

          Size: 100 px.

     - .. figure:: /images/grease-pencil_visual-effects_pixelate_size-200.png
          :width: 200px

          Size: 200 px.


## Rim

.. index:: Grease Pencil Visual Effects; Rim Visual Effect
.. _bpy.types.ShaderFxRim:

*****************
Rim Visual Effect
*****************

The *Rim* Visual Effect shows a simulated rim light on the object contour.

For simulating the rim light, a masked color silhouette of the object is
displaced in horizontal and/or vertical direction.

Many blending modes can be applied to the resulting mask.


Options
=======

.. figure:: /images/grease-pencil_visual-effects_rim_panel.png
   :align: right

   Rim Visual Effect.

Rim Color
   Defines the rim light color.

Mask Color
   Defines a color to keep unaltered.

Blend Mode
   The mask blending operation to perform. See :term:`Color Blend Modes`.

Offset X, Y
   Control the color mask displacement in pixels on the X and Y axis.


Blur
----

Blur X, Y
   Control the blur scale in pixels on the X and Y axis.

Samples
   Number of blur samples (0 disabled the blur effect).


Example
=======

.. list-table:: Rim Effect samples (Mode: Add).

   * - .. figure:: /images/grease-pencil_visual-effects_rim_original.png
          :width: 200px

          Original image.

     - .. figure:: /images/grease-pencil_visual-effects_rim_no-blur.png
          :width: 200px

          No blur.

     - .. figure:: /images/grease-pencil_visual-effects_rim_blur.png
          :width: 200px

          Blur.

     - .. figure:: /images/grease-pencil_visual-effects_rim_mask.png
          :width: 200px

          Mask color: Black.


## Shadow

.. index:: Grease Pencil Visual Effects; Shadow Visual Effect
.. _bpy.types.ShaderFxShadow:

********************
Shadow Visual Effect
********************

The *Shadow* Visual Effect shows a simulated shadow casting by the object.

For simulating the shadow a color silhouette of the object is displaced in
horizontal and/or vertical direction on the back of the object.


Options
=======

.. figure:: /images/grease-pencil_visual-effects_shadow_panel.png
   :align: right

   Shadow Visual Effect.

Shadow Color
   Defines the shadow color.

Offset X, Y
   Control the shadow displacement in pixels on the X and Y axis.

Scale X, Y
   Control the size of the shadow on the X and Y axis.

Rotation
   Sets the shadow rotation around the Grease Pencil object center
   or another object when *Use Object As Pivot* is enabled.

Object Pivot
   When enabled, an *Object* is used by the shadow as the center of rotation.


Blur
----

Blur X, Z
   Control the blur scale in pixels on the X and Z axis.

Samples
   Number of blur samples (0 disabled the blur effect).


Wave Effect
-----------

When enabled, apply a wave distortion to the shadow.

Orientation
   Sets horizontal or vertical direction for the waves.

Amplitude
   Controls the strength and the depth of the wave.

Period
   Controls the wave period. The time it takes to complete one cycle.

Phase
   Shifts the wave pattern over the shadow.


Example
=======

.. list-table:: Shadow Effect samples.

   * - .. figure:: /images/grease-pencil_visual-effects_shadow_simple.png
          :width: 200px

          Simple Shadow.

     - .. figure:: /images/grease-pencil_visual-effects_shadow_blur.png
          :width: 200px

          Blurred Shadow.

     - .. figure:: /images/grease-pencil_visual-effects_shadow_stretch.png
          :width: 200px

          Stretched shadow with an empty as center of rotation.


## Swirl

.. index:: Grease Pencil Visual Effects; Swirl Visual Effect
.. _bpy.types.ShaderFxSwirl:

*******************
Swirl Visual Effect
*******************

The *Swirl* Visual Effect applies a swirling pattern to the object.
The effect use an object as the center of the swirl.


Options
=======

.. figure:: /images/grease-pencil_visual-effects_swirl_panel.png
   :align: right

   Swirl Visual Effect.

Object
   Sets the object to use as the center of the swirl.

Radius
   External radius size of the swirl.

Angle
   Rotation angle of the swirl. A value of 0 shows no swirl.


Example
=======

.. list-table:: Swirl Effect samples (with a Radius of 100 px).

   * - .. figure:: /images/grease-pencil_visual-effects_swirl_angle-00.png
          :width: 200px

          Angle: 0°.

     - .. figure:: /images/grease-pencil_visual-effects_swirl_angle-15.png
          :width: 200px

          Angle: 15°.

     - .. figure:: /images/grease-pencil_visual-effects_swirl_angle-45.png
          :width: 200px

          Angle: 45°.

     - .. figure:: /images/grease-pencil_visual-effects_swirl_angle-90.png
          :width: 200px

          Angle: 90°.


## Wave Distortion

.. index:: Grease Pencil Visual Effects; Wave Distortion Visual Effect
.. _bpy.types.ShaderFxWave:

*****************************
Wave Distortion Visual Effect
*****************************

The *Wave Distortion* Visual applies a wavy effects to the object.


Options
=======

.. figure:: /images/grease-pencil_visual-effects_wave-distortion_panel.png
   :align: right

   Wave Distortion Effect.

Orientation
   Sets horizontal or vertical direction for the waves.

Amplitude
   Controls the strength and the depth of the wave.

Period
   Controls the wave period. The time it takes to complete one cycle.

Phase
   Shifts the wave pattern over the Object.


Example
=======

.. list-table:: Wave Distortion Effect samples.

   * - .. figure:: /images/grease-pencil_visual-effects_wave-distortion_h10.png
          :width: 200px

          Amplitude: 10 (horizontal).

     - .. figure:: /images/grease-pencil_visual-effects_wave-distortion_h30.png
          :width: 200px

          Amplitude: 30 (horizontal).

     - .. figure:: /images/grease-pencil_visual-effects_wave-distortion_v10.png
          :width: 200px

          Amplitude: 10 (vertical).

     - .. figure:: /images/grease-pencil_visual-effects_wave-distortion_v30.png
          :width: 200px

          Amplitude: 30 (vertical).


