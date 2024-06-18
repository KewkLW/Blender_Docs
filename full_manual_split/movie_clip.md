# Index for movie_clip

- [Index](#Index)
- [Editing](#Editing)
- [Index](#Index)
- [Introduction](#Introduction)
- [Scurve](#Scurve)
- [Selecting](#Selecting)
- [Sidebar](#Sidebar)
- [Dope Sheet](#Dope-Sheet)
- [Graph](#Graph)
- [Index](#Index)
- [Introduction](#Introduction)
- [Index](#Index)
- [Introduction](#Introduction)
- [Marker](#Marker)
- [Selecting](#Selecting)
- [Clip](#Clip)
- [Index](#Index)
- [Reconstruction](#Reconstruction)
- [Track](#Track)
- [Index](#Index)
- [View](#View)
- [Index](#Index)
- [Introduction](#Introduction)
- [Panel](#Panel)
- [Workflow](#Workflow)
- [Camera](#Camera)
- [Index](#Index)
- [Marker](#Marker)
- [Objects](#Objects)
- [Plane Track](#Plane-Track)
- [Track](#Track)
- [Index](#Index)
- [Solve](#Solve)
- [Track](#Track)


## Index

.. _bpy.types.SpaceClipEditor:
.. _bpy.types.MovieClip:
.. _bpy.ops.clip:
.. _editors-movieclip-index:

#############################
  Motion Tracking & Masking
#############################

You perform masking and tracking with the Movie Clip Editor.

.. figure:: /images/editors_clip_introduction_example.png

   The Movie Clip Editor.

See :doc:`/editors/clip/index` for more information on the Movie Clip Editor.

.. toctree::
   :maxdepth: 2

   tracking/index.rst
   masking/index.rst


## Editing


*******
Editing
*******

The tools and panels available to edit masks are the same in both editors.
Editing of mask splines happens in a way similar to editing Bézier curves or paths in GIMP or other curve editors.

.. tip::

   To get interactive feedback on the resulting mask,
   a Mask node can be connected directly to a Viewer node in the Compositor,
   which will then keep updating the compositing result while editing.


Transform
=========

.. reference::

   :Mode:      Mask Mode
   :Menu:      :menuselection:`Mask --> Transform`

:doc:`Move </scene_layout/object/editing/transform/move>` :kbd:`G`
   Change the location of control points. Control points can also be moved with :kbd:`LMB`.
   The whole spline can be moved by dragging the center dot with :kbd:`LMB`.
:doc:`Rotate </scene_layout/object/editing/transform/rotate>` :kbd:`R`
   Change the location of control points by rotating about a pivot point.
:doc:`Scale </scene_layout/object/editing/transform/scale>` :kbd:`S`
   Change the location of control points by expanding the distance between points.

:doc:`To Sphere </modeling/meshes/editing/mesh/transform/to_sphere>` :kbd:`Shift-Alt-S`
   Morphs the control points to the shape of a circle.
:doc:`Shear </modeling/meshes/editing/mesh/transform/shear>` :kbd:`Shift-Ctrl-Alt-S`
   Shifts control points along a defined axis so parallel control points move past one another.
:doc:`Push/Pull </modeling/meshes/editing/mesh/transform/push_pull>`
   Moves the control points closer together (Push) or further apart (Pull).

Scale Feather :kbd:`Alt-S`
   Will scale the feather size.


.. _bpy.ops.mask.feather_weight_clear:

Clear Feather Weight
====================

.. reference::

   :Mode:      Mask Mode
   :Menu:      :menuselection:`Mask --> Clear Feather Weight`

Resets the feather weight to zero.


.. _bpy.ops.mask.cyclic_toggle:

Toggle Cyclic
=============

.. reference::

   :Mode:      Mask Mode
   :Menu:      :menuselection:`Mask --> Toggle Cyclic`
   :Shortcut:  :kbd:`Alt-C`

Toggle to create a closed curve or open it again.
Close the mask by joining the last control point to the first.


.. _bpy.ops.mask.handle_type_set:

Set Handle Type
===============

.. reference::

   :Mode:      Mask Mode
   :Menu:      :menuselection:`Mask --> Set Handle Type`
   :Shortcut:  :kbd:`V`

Set handle type for selected spline points.


.. _bpy.ops.mask.normals_make_consistent:

Recalculate Handles
===================

.. reference::

   :Mode:      Mask Mode
   :Menu:      :menuselection:`Mask --> Recalculate Handles`
   :Shortcut:  :kbd:`Shift-N`

Make normals (handle directions) consistent.


.. _bpy.ops.mask.switch_direction:

Switch Direction
================

.. reference::

   :Mode:      Mask Mode
   :Menu:      :menuselection:`Mask --> Switch Direction`

Switch Direction handle directions in/out.


.. _bpy.ops.mask.copy_splines:
.. _bpy.ops.mask.paste_splines:

Copy Paste
==========

Todo.


.. _bpy.ops.mask.parent_clear:

Clear Parent
============

.. reference::

   :Mode:      Mask Mode
   :Menu:      :menuselection:`Mask --> Clear Parent`
   :Shortcut:  :kbd:`Alt-P`

Clears any parenting relationship for the selected spline points.


.. _bpy.ops.mask.parent_set:

Make Parent
===========

.. reference::

   :Mode:      Mask Mode
   :Menu:      :menuselection:`Mask --> Make Parent`
   :Shortcut:  :kbd:`Ctrl-P`

Parents one or more selected spline points to the active motion tracker.


.. _bpy.ops.mask.shape_key_clear:
.. _bpy.ops.mask.shape_key_insert:

Animation
=========

.. reference::

   :Mode:      Mask Mode
   :Menu:      :menuselection:`Mask --> Animation`

Masks can be animated with the shape keying system.
This can be useful when there are not enough good feature points to track in the footage,
or the mask is not based on footage.
Mask animation timing can be edited from the *Dope Sheet's* :ref:`Mask Mode <dope-sheet-mask>`.

Insert Shape Key :kbd:`I`
   Will insert a shape key for the active mask layer at the current frame.
   This works on the level of mask layers,
   so inserting a shape key will keyframe all the splines and points contained in it.
Clear Shape Key :kbd:`Alt-I`
   Will clear the shape key for the active mask layer at the current frame.
Feather Reset Animation
   Resets the feather offset across all animated frames.
Re-Key Points of Selected Shapes
   Re-interpolate selected points on across the range of keys selected in the *Dope Sheet*.


.. _bpy.ops.mask.hide_view_clear:
.. _bpy.ops.mask.hide_view_set:

Show/Hide
=========

.. reference::

   :Mode:      Mask Mode
   :Menu:      :menuselection:`Mask --> Show/Hide`

- Hide Selected :kbd:`H`
- Hide Unselected :kbd:`Shift-H`
- Clear Restricted View :kbd:`Alt-H`


.. _bpy.ops.mask.delete:

Delete
======

.. reference::

   :Mode:      Mask Mode
   :Menu:      :menuselection:`Mask --> Delete`
   :Shortcut:  :kbd:`X`

Removes control points.


.. _bpy.ops.mask.slide_spline_curvature:
.. _bpy.ops.mask.add_vertex_slide:
.. _bpy.ops.mask.add_feather_vertex_slide:

Miscellaneous
=============

Slide Spline Curvature :kbd:`LMB`
   Moves the curve and/or control points by clicking on them and dragging.

Add Vertex and Slide :kbd:`Ctrl-LMB`
   Inserts new control points and defines handle orientations by a continued mouse drag.
   If the last point was selected, double-click will also close the curve.

Add Feather Vertex and Slide :kbd:`Shift-Ctrl-LMB`
   Inserts new feather control points that can be transformed independently of the main spline curve.
   If no feather mask is in use this will create a basic feather mask to the curve.


## Index

.. _bpy.types.Mask:
.. _bpy.ops.mask:

###########
  Masking
###########

.. toctree::
   :maxdepth: 2

   introduction.rst
   scurve.rst
   selecting.rst
   editing.rst
   sidebar.rst


## Introduction


************
Introduction
************

Masks can be created in the *Image* and *Movie Clip* editors, by changing the mode to *Mask* in the header.
This will add various tools and properties to the editor panels,
while hiding others that are not needed for interacting with masks.

Masks have many purposes. They can be used in a motion tracking workflow to mask out,
or influence a particular object in the footage.
They can be used for manual rotoscoping to pull a particular object out of the footage,
or as a rough matte for green-screen keying. Masks are independent from a particular image of movie clip,
and so they can just as well be used for creating motion graphics or other effects in the Compositor.

.. figure:: /images/compositing_types_input_mask_example.png

   Using the Mask node to isolate an object in compositing.

While the *Movie Clip Editor* and *Image Editor* are used to edit masks,
the *Compositor* and *Sequencer* are just using already created mask.

Masks can be animated over the time so that they follow some object from the footage,
e.g. a running actor. This can be achieved with shape keys or parenting the mask to tracking markers.


Mask Data-block
===============

Mask data-block containing multiple mask layers and splines.
They are the most high-level entities used for masking purposes.
Masks can be reused in different places, and hold global parameters for all the entities they consist of.


Header
======

.. figure:: /images/movie-clip_masking_introduction_header.png

   The Movie Clip Editor header in Mask mode.


Menus
-----

View
   Center View to Cursor
      Move the view so that the 2D cursor is at the center of the editor.
Add
   Use to add primitive shapes.
Mask
   Operators used to :doc:`Edit </movie_clip/masking/editing>` masks.


Controls
--------

Mask
   Once set to Mask mode, a mask data-block can be added with a :ref:`data-block menu <ui-data-block>`.
   Any image, movie clip, render or compositing result can be used as a backdrop to display masks over.

   New ``+`` :kbd:`Alt-N`

Mask Display
   See :doc:`/editors/clip/display/mask_display`.


## Scurve

.. _mask-feather:

********
S-Curves
********

The curve type used for creating mask splines is almost a Bézier curve, but with some differences.
Smooth edges of the mask are defined by feathering.
The curve needed to support feathering in a way that stuck to the curve as you edited it,
for ease of editing an animation. These are called S-curves.

Besides the handles, every control point also has points that define the feather between
the current point and the next point on the spline.
Each feather point is stored in UW space,
where U means position across spline segment, and W (weight) means distance between main spline and feather points.

.. figure:: /images/movie-clip_masking_scurve_schematic.svg
   :width: 420px

   S-Curve explained.

This allows for deforming the main spline in almost any way,
and the feather will be updated automatically to reflect that change.

For example if there is just rotation of the spline,
feather would stay completely unchanged. If one point's feather is moved,
the other feathers will be automatically stretched uniformly along that segment
and the overall shape will be almost the same as artists would want it to be.


.. _bpy.ops.mask.primitive_circle_add:
.. _bpy.ops.mask.primitive_square_add:

Primitives
==========

.. reference::

   :Mode:      Mask Mode
   :Tool:      :menuselection:`Add`
   :Shortcut:  :kbd:`Shift-A`

There are two primitives available: a Bézier Circle and a Square with vector handles.


## Selecting

.. _bpy.ops.mask.select_more:
.. _bpy.ops.mask.select_less:

*********
Selecting
*********

.. _bpy.ops.mask.select_all:

All
===

.. reference::

   :Mode:      All modes
   :Menu:      :menuselection:`Select --> All`
   :Shortcut:  :kbd:`A`

Selects all items.


None
====

.. reference::

   :Mode:      All modes
   :Menu:      :menuselection:`Select --> None`
   :Shortcut:  :kbd:`Alt-A`

Resets the selection to nothing.


Invert
======

.. reference::

   :Mode:      All modes
   :Menu:      :menuselection:`Select --> Inverse`
   :Shortcut:  :kbd:`Ctrl-I`

Selects non-selected items and deselects existing selection.


.. _bpy.ops.mask.select_box:

Box Select
==========

.. reference::

   :Mode:      All modes
   :Menu:      :menuselection:`Select --> Box Select`
   :Shortcut:  :kbd:`B`

See :ref:`tool-select-box`.


.. _bpy.ops.mask.select_circle:

Circle Select
=============

.. reference::

   :Mode:      All modes
   :Menu:      :menuselection:`Select --> Circle Select`
   :Shortcut:  :kbd:`C`

See :ref:`tool-select-circle`.


.. _bpy.ops.mask.select_lasso:

Lasso Select
============

.. reference::

   :Mode:      All modes
   :Menu:      :menuselection:`Select --> Lasso Select`
   :Shortcut:  :kbd:`Ctrl-Alt-LMB`

See :ref:`tool-select-lasso`.


.. _bpy.ops.mask.select_linked:

Select Linked
=============

.. reference::

   :Mode:      All modes
   :Menu:      :menuselection:`Select --> Select Linked`
   :Shortcut:  :kbd:`Ctrl-L`

Select all curve points linked to already selected ones.


## Sidebar


*******
Sidebar
*******

Mask Settings
=============

.. _bpy.types.Mask.frame_start:
.. _bpy.types.Mask.frame_end:

Start Frame, End Frame
   Set the frame range of the mask for *Sequencer*.


.. _bpy.types.MaskLayer:

Mask Layers
===========

.. figure:: /images/movie-clip_masking_sidebar_mask-layer-panel.png
   :align: right

   Mask Layer panel.

Mask layers consists of one or several splines and used to "grouped" operation on splines.
Layers can be used to create complex shapes and to define how the splines interact with each other.
Splines belonging to the same layer can be animated together, for example by an item
from motion tracker footage.
Example of such tools might be parenting the whole set of splines to single motion tracking data or
simple to transform all of them together.

Opacity
   Used to set the opacity of the mask layer.
Invert (black/white icon)
   Inverts the values (colors) in the mask layer.
Blend
   The layer blending operation to perform. See :term:`Color Blend Modes`.

   Modes *Merge Add* and *Merge Subtract*
   give better results when using a *Feather* on overlapping masks
   than straightforward mathematical addition and subtraction.
Falloff
   Type of the *Feather* falloff, controls the shape of the transition between black and white.
Overlap
   Fills the self-intersecting areas.
Holes
   Overlapping splines from the same layer will generate holes in the mask.

.. list-table::

   * - .. figure:: /images/movie-clip_masking_sidebar_example-overlap.png
          :width: 320px

          The Overlap option example.

     - .. figure:: /images/movie-clip_masking_sidebar_example-holes.png
          :width: 320px

          The Holes option example.


Example
-------

The purpose of mask layers can be explained with an example.
Suppose there are two unwanted people in the footage, and one of them goes from left to right, and
the other in the opposite direction. Two mask layers can then be used to mask them separately by
using a single mask data-block. At the point of intersection of these shapes they will be added together rather than
creating a hole, as would happen if they were on the same layer. If the motion is simple enough,
a single motion tracked point can be used to drive the location of the entire mask layer.


.. _bpy.types.MaskSpline:

Active Spline
=============

.. figure:: /images/movie-clip_masking_sidebar_active-spline-panel.png
   :align: right

   Active Spline panel.

Feather Offset
   The method used for calculating the offset of the mask spline feather.

   :Even:
      Preserves the thickness of the feather, but can give undesirable loops of the feather curve.
   :Smooth:
      Gives a nicer and smoother shape,
      but can also give an undesirable sharp feather when a curve segment forms an S-shape.

Weight Interpolation
   The type of weight (thickness of feather) interpolation between points.
   *Linear* or *Ease* (i.e. changes occur slowly at the beginning and at the end).

Cyclic
   If the spline is closed or not.
Fill
   Creates splines with filled areas.
   If disabled, Blender will create curves with a thickness to mask out thin objects such as wires or hair.
Self Intersection Check
   Prevent the feather (not the curve itself) from intersecting with itself.


Active Point
============

.. figure:: /images/movie-clip_masking_sidebar_active-point-panel.png
   :align: right

   Active Point panel.

This panel is shown when both a tracking marker and mask is selected.


.. _bpy.types.MaskParent:

Parent
------

In the *Movie Clip Editor* it is possible to link the whole mask or its points to motion tracks.
This way the mask or points will follow the tracks.

Parent
   :ref:`Data ID <ui-data-id>` to which the mask or spline is parented to
   in case of parenting to movie tracking data set to Movie Clip data-block.
Parent Type
   Point Track, Plane Track
Object
   :ref:`Object <movie-clip-tracking-properties-object>` to parent to.
Track
   Name of individual tracks.


## Dope Sheet


***************
Dope Sheet View
***************

.. figure:: /images/movie-clip_tracking_dope-sheet_example.png

   Dope Sheet View.

The Dope Sheet View is used to visualize motion tracking data,
it is implemented as separate view of the Movie Clip editor just like the Graph View.

It displays channels for selected tracks and each channel visualizes tracked
segments of tracks as dark bars and keyframed positions of tracks as small diamonds.

The background is highlighted depending on the number of tracks in a frame.
This means that if for a frame (or sequence of frames) there are less than eight tracks,
the background will turn red;
if there are from eight to sixteen tracks, the background will be yellow.

This is only a visual feedback, which doesn't mean that the camera motion will not
reconstruct with less than eight tracks. It only means that you should pay attention to those frames and
check if all possible good feature points are tracked there. Remember, if there are no good feature points in
the frame and there are less than 16 tracks in the frame, it doesn't mean the solution won't be accurate.
Rather, adding more tracks on bad feature points will reduce the accuracy of solution.


Header
======

.. figure:: /images/movie-clip_tracking_dope-sheet_sort.png
   :align: right

   Sort order of the channels.

Show Only Selected (mouse cursor icon)
   Limits Dope Sheet channels to only information about selected tracks.
Hidden (ghost icon)
   Includes information from hidden tracks.

.. _bpy.types.MovieTrackingDopesheet.sort_method:

Sort Method
   Sort order of the tracks.

   :Name: Sort selected tracks in alphabetical order based on their names.
   :Longest: Sort tracks by longest tracked segment length.
   :Total: Sort tracks by overall amount of frames.
   :Average Error: Sort tracks by their average reprojection error after solving camera or object motion.
   :Start Frame: Sort channels by first frame number.
   :End Frame: Sort channels by last frame number.

.. _bpy.types.MovieTrackingDopesheet.use_invert_sort:

Invert
   To change the sort order from ascending to descending.


Usage
=====

The Dope Sheet View is for visualization and does not have any tools to actually edit data.


## Graph


**********
Graph View
**********

.. figure:: /images/movie-clip_tracking_graph_example.png

   Graph View.


Introduction
============

The graph or curves view has numerous purposes based on the color of the lines.
The red and green lines on the graph show you the speed of the trackers at a given frame.
Green is vertical movement, Red is horizontal. Therefore the first frames will always be at zero.

The blue line is the line that comes out when you click on the film strip is the average per-frame error.
This curve is available only after pressing camera solve and is not editable.
This is the one line that you want to be as flat as possible and as closer to zero as you can.
The high points will show you where in your shot you are having inaccurate tracking.

Frames outside of scene frame range are darkened.


Header
======

Show Selected (mouse cursor icon)
   Displays the graph for only selected trackers.

Display Hidden (ghost icon)
   Displays channels from objects that are hidden.
Filter
   Display options, defines what curves are visible.

   Frames
      Visualizes per-frame average reprojection error of all tracks in the active tracking object.
   Motion
      Shows curves for X and Y speed of tracks.
   Error
      Per-frame reprojection error of tracks.


Usage
=====

The curves are useful to see if particular trackers are moving differently than the average.
A line that spikes from the rest of the curve usually means a tracking error.

You can manually edit the curve by selecting a point in the curve and dragging it or deleting,
that will affect the corresponding tracker on that particular frame.

Lock to Selection :kbd:`L`
   Locks the view to selected markers during playback.


## Index

.. _bpy.types.MovieTracking:

###################
  Motion Tracking
###################

.. toctree::
   :maxdepth: 2

   introduction.rst
   clip/index.rst
   graph.rst
   dope_sheet.rst


## Introduction


************
Introduction
************

Motion Tracking is used to track the motion of objects and/or a camera and, through the constraints,
to apply this tracking data to 3D objects (or just one), which have either been created in Blender or
imported into the application. Blender's motion tracker supports a couple of very powerful tools for 2D tracking and
3D motion reconstruction, including camera tracking and object tracking, as well as some special features like
the plane track for compositing. Tracks can also be used to move and deform masks for rotoscoping in the Mask Editor,
which is available as a special mode in the Movie Clip Editor.


Views
=====

In Tracking Mode there are three different views available. You can toggle between view modes using
the View selector, which is located in the header.
When you selected a view in the whole area of the Movie Clip editor will change.
Hence, to display a curve or dope sheet view, the editor must be split into two,
with one switched to the curve or dope sheet view.


Manual Lens Calibration
=======================

All cameras record distorted video.
Nothing can be done about this because of the manner in which optical lenses work.
For accurate camera motion,
the exact value of the focal length and the "strength" of distortion are needed.

Currently, focal length can be automatically obtained only from the camera's settings or from the EXIF information.
There are some external tools which can help to find approximate values to compensate for distortion.
There are also fully manual tools where you can use a grid which is getting affected by distortion model and
deformed cells defines straight lines in the footage.

Within Blender you can use the Annotation tool for this -- just draw a line which should be straight on
the footage using poly line brush and adjust the distortion values
to make the annotations match lines on the footage.

To calibrate your camera more accurately, use the Grid calibration tool from OpenCV.
OpenCV is using the same distortion model, so it should not be a problem.


Camera and Object Motion Solving
================================

Blender not only supports the solving of camera motion, including tripod shots,
but also the solving of object motion in relation to the motion of the camera.
In addition to that there is the Plane Track, which solves the motion of all markers on one plane.


Tools for Scene Orientation and Stabilization
=============================================

After solve, you need to orient the real scene in the 3D scene for more convenient compositing.
There are tools to define the floor, the scene origin, and the X/Y axes to perform scene orientation.

Sometimes, the video footage includes spurious jumps and tilting movements, like e.g. when using a hand-held camera.
Based on some tracked image elements,
the :doc:`/movie_clip/tracking/clip/sidebar/stabilization/index`
is able to detect and compensate such movements to improve the quality of the final result.


## Index


#############
  Clip View
#############

.. toctree::
   :maxdepth: 2

   introduction.rst
   marker.rst
   toolbar/index.rst
   selecting.rst
   editing/index.rst
   sidebar/index.rst


## Introduction


************
Introduction
************

The Clip View is the main part of the Movie Clip editor;
almost all motion tracking tools are concentrated within the Clip View.

It should be mentioned that the camera solver consists of three quite separate steps:

#. 2D tracking of footage.
#. Camera intrinsics (focal length, distortion coefficients) specification/estimation/calibration.
#. Solving camera, scene orientation, and scene reconstruction.


Main View
=========

When a clip is loaded a Timeline is shown at bottom of the Preview.
It expands over the full area limited by the animation range.
You can move the Playhead by dragging with :kbd:`LMB`.

The Timeline is composed of the following visual elements:

- Blue line: Playhead
- Yellow: Motion track
- Yellow line: Keyframe
- Orange line: Shape keyframe
- Purple: Prefetched frames
- Light green line: Solve start/end keyframe


## Marker


***************
Tracking Marker
***************

Point
=====

.. figure:: /images/movie-clip_tracking_clip_marker_schematic.svg
   :align: center

   Marker schematic.

The whole marker can be moved with :kbd:`RMB` or by dragging the anchor point (black dot) with :kbd:`LMB`.
Pressing :kbd:`G` also moves the whole marker. When pressing :kbd:`G` twice the marker will be moved
while keeping the anchor in place. Note that the anchor point outside the pattern area is shown as a cross connected
with marker position with a dashed line.

:kbd:`S` scales the whole marker.
The whole pattern area only will be scaled by pressing :kbd:`S` twice;
The Pattern can also be rotated using the :kbd:`R` key which, depending on the used pivot point,
will either rotate patterns around their own centers or rotate the whole markers around e.g. the median point.

To match the perspective transformation of a marker on a plane, the individual corners must be edited manually.
Each marker corner can deform individually to define the shapes.
Corner positions can be edited by dragging them with a mouse.
Dragging with :kbd:`LMB` will change the position of an individual corner.

.. note::

   Note that deforming a pattern is not only useful for planar / affine tracking.
   Since only pixels within the pattern will be considered this can help to
   specify a better pattern to track even for simple position tracking.

The Search area can not be rotated; this is intentional. It doesn't make sense to deform the search area.


Plane
=====

The left bottom corner of the plane does have X/Y axis (X is red, Y is green) to
help distinguishing orientation of the plane in space.

It is likely that corner of the plane object need to be manually adjusted.
To do this sliding individual corners with mouse :kbd:`LMB` or general transform tools
:kbd:`G`, :kbd:`R`, :kbd:`S` could be used.

Adjusting plane corners will keep it following the plane defined by tracks it was originally created from.


## Selecting


*********
Selecting
*********

.. _bpy.ops.clip.select_box:

Box Select
==========

.. reference::

   :Mode:      All modes
   :Menu:      :menuselection:`Select --> Box Select`
   :Shortcut:  :kbd:`B`

See :ref:`tool-select-box`.


.. _bpy.ops.clip.select_circle:

Circle Select
=============

.. reference::

   :Mode:      All modes
   :Menu:      :menuselection:`Select --> Circle Select`
   :Shortcut:  :kbd:`C`

See :ref:`tool-select-circle`.


.. _bpy.ops.clip.select_lasso:

Lasso Select
============

.. reference::

   :Mode:      All modes
   :Menu:      :menuselection:`Select --> Lasso Select`
   :Shortcut:  :kbd:`Ctrl-Alt-RMB`

See :ref:`tool-select-lasso`.


.. _bpy.ops.clip.select_all:

(De)select All
==============

.. reference::

   :Mode:      All modes
   :Menu:      :menuselection:`Select --> (De)select All`
   :Shortcut:  :kbd:`A`

Selects all items.


Inverse
=======

.. reference::

   :Mode:      All modes
   :Menu:      :menuselection:`Select --> Inverse`
   :Shortcut:  :kbd:`Ctrl-I`

Selects non-selected items and deselects existing selection.


.. _bpy.ops.clip.select_grouped:

Select Grouped
==============

.. reference::

   :Mode:      All modes
   :Menu:      :menuselection:`Select --> Select Grouped`
   :Shortcut:  :kbd:`Shift-G`

Select all tracks from specified group.

Action
   The group of tracks to select.

   :Keyframed Tracks: Select all keyframed tracks.
   :Estimated Tracks: Select all estimated tracks.
   :Tracked Tracks: Select all tracked tracks.
   :Locked Tracks: Select all locked tracks.
   :Disabled Tracks: Select all disabled tracks.
   :Track with Same Color: Select all tracks with same color as active track.
   :Failed Tracks: Select all tracks which failed to be reconstructed.


.. _bpy.ops.clip.stabilize_2d_select:

Select Stabilization Tracks
===========================

.. reference::

   :Mode:      Tracking mode
   :Menu:      :menuselection:`Select --> Select Stabilization Tracks`

Select tracks which are used for translation stabilization.


.. _bpy.ops.clip.stabilize_2d_rotation_select:

Select Stabilization Rotation Tracks
====================================

.. reference::

   :Mode:      Tracking mode
   :Menu:      :menuselection:`Select --> Select Stabilization Rotation Tracks`

Select tracks which are used for rotation stabilization.


## Clip


****
Clip
****

.. _bpy.ops.clip.open:

Open Clip
=========

.. reference::

   :Mode:      All modes
   :Menu:      :menuselection:`Clip --> Open Clip`
   :Shortcut:  :kbd:`Alt-O`

Todo.


.. _bpy.ops.clip.set_scene_frames:

Set Scene Frames
================

.. reference::

   :Mode:      Tracking
   :Menu:      :menuselection:`Clip --> Set Scene Frames`

Sets end scene frame to match current clip duration.


.. _bpy.ops.clip.set_center_principal:

Set Principal to Center
=======================

.. reference::

   :Mode:      Tracking
   :Menu:      :menuselection:`Clip --> Set Principal to Center`

Changes the :ref:`Optical Center <bpy.types.MovieTrackingCamera.principal>` values to the center of image.


.. _bpy.ops.clip.prefetch:

Prefetch
========

.. reference::

   :Mode:      All modes
   :Menu:      :menuselection:`Clip --> Prefetch`
   :Shortcut:  :kbd:`P`

Fills cache with frames. As many frames as fits into cache are load form the drive.
This allows to fill in the cache as fast as possible when you really need to track something,
but this keeps CPU and drive bandwidth idle if you've got a Clip editor opened but not actually interacting with it.


.. _bpy.ops.clip.reload:

Reload Clip
===========

.. reference::

   :Mode:      All modes
   :Menu:      :menuselection:`Clip --> Open Clip`

Force reload the currently loaded movie clip. Is mainly useful when the clip gets edited outside of Blender.


Proxy
=====

Todo.


.. _bpy.ops.clip.set_viewport_background:

Set as Background
=================

.. reference::

   :Mode:      Tracking
   :Menu:      :menuselection:`Clip --> Set as Background`

Sets the clip currently being edited as the camera background for all visible 3D Viewports.
If there is no visible 3D Viewports or the Clip Editor is open in full screen, nothing will happen.


.. _bpy.ops.clip.setup_tracking_scene:

Setup Tracking Scene
====================

.. reference::

   :Mode:      Tracking
   :Menu:      :menuselection:`Clip --> Setup Tracking Scene`

Performs all usual steps to set up a VFX scene:

- Create reference objects for floor and test object.
- Create node set up for combining CG with an actual clip.


## Index


###########
  Editing
###########

.. toctree::
   :maxdepth: 2

   clip.rst
   track.rst
   reconstruction.rst


## Reconstruction


**************
Reconstruction
**************

Scene orientation tools can be used for orienting object to bundles.


.. _bpy.ops.clip.set_origin:

Set Origin
==========

.. reference::

   :Mode:      Tracking
   :Menu:      :menuselection:`Reconstruction --> Set Origin`

Transform camera in a way which makes active track to be moved to a scene origin.
Only translation is applied to the camera.


.. _bpy.ops.clip.set_plane:

Set Floor
=========

.. reference::

   :Mode:      Tracking
   :Menu:      :menuselection:`Reconstruction --> Set Floor`

Use selected three markers to define a floor.
Camera will be transformed in a way which makes the selected markers to be flat (have Z = 0).


Set Wall
========

.. reference::

   :Mode:      Tracking
   :Menu:      :menuselection:`Reconstruction --> Set Wall`

Similar to the floor orientation, but defines a wall (selected tracks are placed onto the XZ plane).


.. _bpy.ops.clip.set_axis:

Set X/Y Axis
============

.. reference::

   :Mode:      Tracking
   :Menu:      :menuselection:`Reconstruction --> Set X/Y Axis`

Transform camera in a way which makes active track to become on X or Y axis.
No translation is applied, meaning scene origin which was specified before will be preserved.


.. _bpy.ops.clip.set_scale:

Set Scale
=========

.. reference::

   :Mode:      Tracking
   :Menu:      :menuselection:`Reconstruction --> Set Scale`

Scale camera or tracking object in a way which makes distance
between two selected tracks match the given value in *Distance*.


.. _bpy.ops.clip.apply_solution_scale:

Apply Solution Scale
====================

.. reference::

   :Mode:      Tracking
   :Menu:      :menuselection:`Reconstruction --> Apply Solution Scale`

Similar to :ref:`bpy.ops.clip.set_scale`, but actually modifies the tracking data.


.. _bpy.ops.clip.track_to_empty:

Link Empty to Track
===================

.. reference::

   :Mode:      Tracking
   :Menu:      :menuselection:`Reconstruction --> Link Empty to Track`

Creates new empty in 3D Viewport and appends constraint which parts it to the active track.


.. _bpy.ops.clip.bundles_to_mesh:

3D Markers to Mesh
==================

.. reference::

   :Mode:      Tracking
   :Menu:      :menuselection:`Reconstruction --> 3D Markers to Mesh`

Creates a mesh which vertices matches positions of reconstructed tracks.
It is required to have motion solved first before using this operator.
Only tracks from the current tracking object will be used.
The intention of this operator is to give a nice starting point for a manual mesh reconstruction.


## Track


*****
Track
*****

Transform
=========

Todo.


.. _bpy.ops.clip.track_markers:

Track Motion
============

The Track Motion menu is used to perform tracking of selected tracks
(i.e. following the selected feature from frame to frame).

This operator depends on settings from the Tracking Settings panel.
If during sequence tracking the algorithm fails to track some markers,
they will be disabled and tracking will continue for the rest of the markers.
If the algorithm fails when tracking frame-by-frame, the marker is not disabled,
and the most likely position of the feature on the next frame is used.


Backwards
---------

.. reference::

   :Mode:      Tracking
   :Menu:      :menuselection:`Track --> Track Motion --> Backwards`
   :Shortcut:  :kbd:`Shift-Ctrl-T`

Tracks the motion backward along the sequence.


Frame Backwards
---------------

.. reference::

   :Mode:      Tracking
   :Menu:      :menuselection:`Track --> Track Motion --> Frame Backwards`
   :Shortcut:  :kbd:`Alt-Left`

Tracks the motion backward by one frame.


Forwards
--------

.. reference::

   :Mode:      Tracking
   :Menu:      :menuselection:`Track --> Track Motion --> Forwards`
   :Shortcut:  :kbd:`Ctrl-T`

Tracks the motion forward along the whole sequence.


Frame Forwards
--------------

.. reference::

   :Mode:      Tracking
   :Menu:      :menuselection:`Track --> Track Motion --> Frame Forwards`
   :Shortcut:  :kbd:`Alt-Right`

Tracks the motion forward one frame.


Clear
=====

.. _bpy.ops.clip.clear_track_path:

Before
------

.. reference::

   :Mode:      Tracking
   :Menu:      :menuselection:`Track --> Clear --> Before`
   :Shortcut:  :kbd:`Shift-T`

Deletes all tracked and keyframed markers after the current frame for all selected tracks.

Clear Active
   Limits clear action to only active track (as opposite to all selected ones).


After
-----

.. reference::

   :Mode:      Tracking
   :Menu:      :menuselection:`Track --> Clear --> After`
   :Shortcut:  :kbd:`Alt-T`

Deletes all tracked and keyframed markers before the current frame for all selected tracks.

Clear Active
   Limits clear action to only active track (as opposite to all selected ones).


Track Path
----------

.. reference::

   :Mode:      Tracking
   :Menu:      :menuselection:`Track --> Clear --> Track Path`
   :Shortcut:  :kbd:`Shift-Alt-T`

Clears all markers except the current one from all selected tracks.

Clear Active
   Limits clear action to only active track (as opposite to all selected ones).


Clear Solution
--------------

Todo.


.. _bpy.ops.clip.refine_markers:

Refine
======

This operator will run a tracker from previous keyframe to current frame for all selected markers.
Current markers positions are considering initial position guess
which could be updated by a tracker for better match.

Useful in cases when feature disappears from the frame and then appears again. Usage in this case is the following:

- When feature point re-appeared on frame, manually place marker on it.
- Use Refine Markers operation to allow tracker to find a better match.

Depending on direction of tracking use either *Forwards* or *Backwards* refining.
Accordingly if tracking happens forwards, use *Refine Forwards*, otherwise use *Refine Backwards*.


Backwards
---------

.. reference::

   :Mode:      Tracking
   :Menu:      :menuselection:`Track --> Refine --> Backwards`

Refine the track backwards.


Forwards
--------

.. reference::

   :Mode:      Tracking
   :Menu:      :menuselection:`Track --> Refine --> Forwards`

Refine the track forwards.


.. _bpy.ops.clip.add_marker_move:

Add Marker
==========

.. reference::

   :Mode:      Tracking
   :Menu:      :menuselection:`Track --> Add Marker`

Places a new marker at the position of the mouse
(which is under the button in this case, not ideal but it is just how things work)
and then it can be moved to the needed location. When it is moved to the desired position,
:kbd:`LMB` can be used to finish placing the new marker.
Also, :kbd:`Return` and :kbd:`Spacebar` can be used to finish placing the marker.
But it is faster to use :kbd:`Ctrl-LMB` to place markers directly on the footage.
This shortcut will place the marker in the place you have clicked.

In addition to this until you have released the mouse button,
you can adjust the marker position by moving the mouse and
using the track preview widget to control how accurately the marker is placed.


.. _bpy.ops.clip.detect_features:

Detect Features
===============

.. reference::

   :Mode:      Tracking
   :Menu:      :menuselection:`Track --> Detect Features`

Detects all possible features on the current frame and places markers at these features.
This operator does not take other frames into account,
so it might place markers on features which belong to moving objects.
If the camera is turning away from this shot,
no markers could be present within the frames after the camera moved away.

There are several properties for this operator:

Placement
   Controls where to place markers.

   Whole Frame
      Places markers throughout the whole frame.
   Inside Annotated Area
      Places markers inside the area outlined with the :ref:`tool-annotate`.
      This can be used to outline some areas with interesting features
      and place markers only inside the outlined area.
   Outside Annotated Area
      Places markers outside the area outlined with the :ref:`tool-annotate`.
      This can be used to outline areas of no interest (like trees, humans, etc.)
      and place markers outside of these areas.
Margin
   Controls the distance from the image boundary for created markers.
   If markers are placed too close to the image boundary,
   they will fail to track really quickly and they should be deleted manually.
   To reduce the amount of manual clean-up, this parameter can be used.
Threshold
   Limits minimal threshold for placing markers.
   This value comes from the feature detection algorithm and it means:
   low values means most probably this feature would fail to track very soon,
   high value means it is not much such track.
   Amount of markers to be added can be controlled with this value.
Distance
   Defines the minimal distance between placed markers.
   It is needed to prevent markers from being placed too close to each other
   (such placement can confuse the camera solver).


.. _clip-tracking-plane:
.. _bpy.ops.clip.create_plane_track:

Create Plane Track
==================

.. reference::

   :Mode:      Tracking
   :Menu:      :menuselection:`Track --> Create Plane Track`

The *Create Plane Track* operator creates a new plane track.
Planar tracking takes advantage of the fact that there are often planar surfaces in footage,
by attaching markers to points on these flat planes.
It can be used to replace things like billboards and screens on the footage with another image or video.
It also might be used for masking.

This button will create a plane object
which is deforming in the same way as plane defined by all selected point tracks.
At least four feature points tracked across the footage which belongs to
the plane you want to replace are needed. More tracks will give better estimation of plane motion.

Feature points used to estimate plane motion could be used from any place on the plane,
meaning it's not necessarily need to be corners. Corners are not always easy to be tracked,
they might be occluded. In this case you can position tracked features that lay on the same plane
far away from the actual plane which should be replaced.

This provides more information about the possible deformation of the marker in following frames,
and such markers can be tracked even if partially occluded (appear and disappear during the time).
It is only required that two neighbor frames have at least four common tracks.

An image can be projected onto the plane with
the :doc:`/compositing/types/tracking/plane_track_deform` compositing node.


.. _bpy.ops.clip.solve_camera:

Solve Solution
==============

.. reference::

   :Mode:      Tracking
   :Menu:      :menuselection:`Track --> Solve Solution`

The *Camera Motion* operator solves the motion of camera using all tracks placed
on the footage and two keyframes specified on this panel. There are some requirements:

- There should be at least eight common tracks on the both of the selected keyframes.
- There should be noticeable parallax effects between these two keyframes.

If everything goes smoothly during the solve, the average reprojection error is reported to
the information space and to the Clip editor header. Reprojection error means the average
distance between reconstructed 3D position of tracks projected back to footage and
original position of tracks. Basically, reprojection error below 0.3 means accurate reprojection,
(0.3 - 3.0) means quite nice solving which still can be used.
Values above 3 means some tracks should be tracked more accurately,
or that values for focal length or distortion coefficients were set incorrectly.

.. (todo 2.62) object solver


.. _bpy.ops.clip.join_tracks:

Join Tracks
===========

.. reference::

   :Mode:      Tracking
   :Menu:      :menuselection:`Track --> Join Tracks`
   :Shortcut:  :kbd:`Ctrl-J`

This operator joins all selected tracks into one.
Selected tracks should not have common tracked or keyframed markers at the same frame.

.. (wip)
   Joining two tracks now works better for tracks which have got intersection by frames:
   coordinates of joined track would be interpolated linearly on segments with intersection.
   This is still not perfect from accurate solving point of view,
   but this allows to prevent camera jump which is much more annoying than sight camera slide.


.. _bpy.ops.clip.average_tracks:

Average Tracks
==============

.. reference::

   :Mode:      Tracking
   :Menu:      :menuselection:`Track --> Average Tracks`

The Average Tracks operator creates a new tracking marker by averaging the data from the selected tracks.
This can be used to improve stability of tracking on blurry or non-very-sharp feature shapes.
The operator takes into account all :doc:`Marker properties </movie_clip/tracking/clip/sidebar/track/marker>`
however, disabled markers do not affect the averaging.

Gaps in the original tracks will be linearly interpolated, to reduce result track jump.
Note that this only applies to gaps "in between".
This means that if a track does not have markers in the beginning or end of it,
there is nothing to interpolate with and the resulting track will jump.

Keep Original
   When enabled, the selected tracks are *not* deleted.


Copy Tracks
===========

Todo.


Paste Tracks
============

Todo.


Animation
=========

Todo.


Show/Hide
=========

Todo.


Clean Up
========

.. _bpy.ops.clip.clean_tracks:

Clean Tracks
------------

.. reference::

   :Mode:      Tracking
   :Menu:      :menuselection:`Track --> Clean Up --> Clean Tracks`

Identifies all tracks which matches settings from above and performs desired action on them.

Tracked Frames
   Tracks or tracked segments shorter than this number of frames will be removed.
Reprojection Error
   Tracks which has reprojection error higher than this value will be removed.
Action
   Several actions can be performed for bad tracks.

   Select
      They can simply be selected.
   Delete Track
      The whole track can be deleted.
   Delete Segments
      Bad segments of tracked sequence can be removed.


.. _bpy.ops.clip.filter_tracks:

Filter Tracks
-------------

.. reference::

   :Mode:      Tracking
   :Menu:      :menuselection:`Track --> Clean Up --> Filter Tracks`

This operator deletes obviously bad tracks (for example, the ones which are too short).
Additionally, it identifies tracks which has suspicious spikes in their motion and selects them.


.. _bpy.ops.clip.delete_track:

Delete Track
============

.. reference::

   :Mode:      Tracking
   :Menu:      :menuselection:`Track --> Delete Track`
   :Shortcut:  :kbd:`X`

Delete all selected tracks.


.. _bpy.ops.clip.delete_marker:

Delete Marker
=============

.. reference::

   :Mode:      Tracking
   :Menu:      :menuselection:`Track --> Delete Marker`
   :Shortcut:  :kbd:`Shift-X`

Todo.


## Index


###########
  Sidebar
###########

.. toctree::
   :maxdepth: 2

   track/index.rst
   stabilization/index.rst
   view.rst


## View


****
View
****

Annotations
===========

Annotation tool strokes can be enabled/disabled with the checkbox in the panel header.
It is a standard annotations panel where annotation layers and frames can be controlled.
There is one difference in the behavior of the annotation tools from other areas --
when a new layer is created "on-demand" (when making a stroke without adding a layer before this)
the default color for the layer is set to pink. This heightens the color contrast to make
the stroke more noticeable on all kinds of movies.

.. _bpy.types.SpaceClipEditor.annotation_source:

Data Source
   Determines the data-block type the current annotation layer is stored.

   :Clip: Store the current annotation layer with the active *Movie Clip* data-block.
   :Track: Store the current annotation layer with the active *Track* data-block.

.. seealso::

   :ref:`tool-annotate` for more information on general annotation layers.


## Index

.. _bpy.types.MovieTrackingStabilization:

####################
  2D Stabilization
####################

.. toctree::
   :maxdepth: 2

   introduction.rst
   panel.rst
   workflow.rst


## Introduction

.. todo <2.8 fix voice: we, our

************
Introduction
************

The 2D video stabilization is a feature built on top of Blender's image feature tracking abilities:
You can use some tracking points to remove shakiness, bumps and jerks from video footage.
Typically, image stabilization is part of a 2D workflow to prepare and improve footage
prior to further processing or modeling steps. This page helps to understand how it works,
introduces related terms and concepts, describes the available interface controls in detail
and finally gives some hints about usage in practice.

Typical usage scenarios of the stabilizer:

- Fix minor deficiencies (shaky tripod, jerk in camera movement).
- "Poor man's steadycam" (when a real steadycam was not available, affordable or applicable).
- As a preparation for masking, matching and rotoscoping.

It is not uncommon for 2D stabilization to have to deal with somewhat imperfect and flawed footage.


How It Works
============

To detect spurious movement in a given shot, we'll assume a simplified model about this movement.
We then try to fit the movement of tracked features with this simplified model to derive a compensation.
Of course, this works only to the degree our model is adequate -- yet in practice, this simplified approach works
surprisingly well even with rather complicated shots, where our basic assumption was just an approximation of
much more elaborate movements.

This simplified model underlying the 2D stabilization as implemented here assumes movement
by an affine-linear transform:

- The camera is pushed up/down/sideways by some translation component.
- The image is then tilted and scaled around a pivot point (rotation center).

To compensate movement according to this simplified model, the 2D stabilizer proceeds in two steps.
First we try to detect the translation offset from the weighted average of all *translation* tracking points.
After compensating this translation component, we then use additional *rotation/scale* tracking points to detect
rotation around a given pivot point. Again, we detect rotation and scale changes through a weighted average
of all the rotation/scale tracking points given.

In the current version, the pivot point is anchored to the weight center of the translation tracking points.
So effectively the detected translation is already factored out. In some cases this is not optimal,
especially when tracks have gaps or do not cover the whole duration of the footage -- we plan further options
to better control the pivot point in future releases.


Stabilization Tracks
--------------------

Thus, as foundation for any image stabilization, we need tracked image features to derive the movements.
These tracking points or "tracks" can be established with Blender's
:doc:`image feature tracking component </movie_clip/tracking/clip/introduction>`
The right choice of points to track is somewhat tricky, yet crucial for successful image stabilization.
Often, we're here because we'll have to deal with imperfect footage. In such cases, the averaging of tracks
helps to work around image or tracking errors at some point.
Moreover, when the footage contains perspective induced movements, symmetrically placed tracking points above
and below the horizon can be used to cancel out spurious movement and get stabilization to the focal area in between.

.. figure:: /images/movie-clip_tracking_clip_sidebar_stabilization_introduction_perspective.jpg
   :align: center
   :width: 600px

   Diverging movements caused by perspective.

Tracks can be added in two groups:

#. First of all is the list of tracks to be used to compensate for jumps in the camera location.
   From all the tracking points added to this group, we calculate a weighted average.
   We then try to keep this average location constant during the whole shot.
   Thus it is a good idea to use tracking markers close to and centered around the most important subject.
#. A second selection of tracks is used to keep the rotation and scale of the image constant.
   You may use the same tracks for both selections. But usually it is best to use tracking points with large distance
   from the image center, and symmetrically, on both sides, to capture the angular movements more precisely.
   Similar to the "location" case, we calculate an average angular contribution and then try
   to keep this value constant during the whole shot.


Footage, Image & Canvas
-----------------------

When talking about the movement stabilization of video, we have to distinguish several frames of reference.
The image elements featured by the footage move around irregularly within the footage's original image boundaries --
this is the very reason why we are using the stabilizer. When our attempt at stabilization was successful,
the image elements can be considered stable now, while in exchange the footage's image boundaries have taken on
irregular movement and jump around in the opposite way.
This is the immediate consequence of the stabilizer's activity.

Since the actual image elements, i.e. the subject of our footage can be considered stable now, we may use these
as a new frame of reference: we consider them attached to a fixed backdrop, which we call the canvas.
Introducing this concept of a "canvas" helps to deal with deliberate movements of the camera. And beyond that,
it yields an additional benefit: It is very frequent for the pixels of video footage to be non-square.
So we have to stretch and expand those pixels, before we're able to perform any sensible rotation stabilization.
Thus the canvas becomes, by definition, the reference for an undistorted display of the image contents.

But when the camera was moved intentionally, we have to consider yet another frame of reference beyond the canvas:
namely the frame (or "cadre") of the final image we want to create. To understand this distinction,
let's consider a hand-held, panning shot to the right: Since our camera was turned towards the right side,
the actual image contents move towards the left side *within* the original image frame.
But let's assume the stabilizer was successful with "fixing" any image contents relative to the canvas --
which in turn means, that the original image boundaries start to move irregularly towards the right side,
and the contents of the image will begin to disappear gradually behind the left boundary of the original image.
After some amount of panning,
we'll have lost all of our original contents and just see an empty black image backdrop.
The only solution to deal with that problem is to move the final image frame along to the right,
thus following the originally intended panning movement. Of course, this time, we do want to perform this
newly added panning movement in a smooth and clean way.

.. figure:: /images/movie-clip_tracking_clip_sidebar_stabilization_introduction_panning.jpg
   :align: center
   :width: 600px

   Stabilizing a panning shot.

.. figure:: /images/movie-clip_tracking_clip_sidebar_stabilization_introduction_canvas.jpg
   :align: right
   :width: 400px

   Restoring the expected camera movement.

To allow for such a compensation and to reintroduce deliberate panning, or tilting and zoom of the resulting image,
the stabilizer offers a dedicated set of controls: *Expected position*, *Expected rotation* and *Expected scale*.
These act like the controls of a virtual camera filming the contents we have fixed onto the canvas.
By animating those parameters, we're able to perform all kinds of deliberate camera movements in a smooth fashion.

.. container:: lead

   .. clear


The "Dancing" Black Borders
---------------------------

As explained above, when we succeed with stabilizing the image contents, the boundaries of the original footage
start to jump around in the opposite direction of the movements compensated. This is inevitable -- yet very annoying,
since due to the irregular nature of these movements, these "dancing black borders" tend to distract attention
from the actual subject and introduce an annoying restlessness. Thus our goal must be to hide those dancing borders
as good as possible. A simple solution is to add a small amount of zoom. Sometimes we'll also need to animate
the parameter *Expected* position in order to keep the image centered as good as we can -- this helps to reduce
the amount of zoom necessary to remove those annoying borders.

The *Autoscale* function can be used to find the minimal amount of zoom just sufficient to remove
those black borders completely. However, if the camera jumps a lot, the autoscale function often zooms in too much,
especially since this calculation aims at finding a single, static zoom factor for the whole duration of the footage.
When this happens, you'll typically get overall better results
with animating both the zoom factor and the expected position manually.


## Panel

.. (todo move) introductory text parts to introduction.rst

**********************
2D Stabilization Panel
**********************

The purpose of 2D stabilization is to smooth out jerky camera handling on existing real-world footage.
To activate the 2D stabilizer, you need to set the toggle in the panel, and additionally you need to enable
*Show Stable* in the Clip Display pop-over.
Then you'll need to set up some tracking points to detect the image movements.

The 2D Stabilization panel is used to define the data used for 2D stabilization of the shot.
Several options are available in this panel: you may add a list of tracks to determine lateral image shifts
and another list of tracks to determine tilting and zooming movements.
Based on the average contribution of these tracks,
a compensating movement is calculated and applied to each frame.

When the footage includes panning and traveling movements,
the stabilizer tends to push the image out of the visible area.
This can be compensated by animating the parameters for the intentional,
"expected" camera movement.

.. note::

   To *activate* the 2D stabilizer, you need to set the toggle in the panel,
   and additionally you need to enable *Show Stable* in the *Clip Display* pop-over.


.. _bpy.types.MovieTrackingStabilization.use_2d_stabilization:

Options
=======

.. figure:: /images/movie-clip_tracking_clip_sidebar_stabilization_panel_panel.png
   :align: right
   :width: 213px

   2D Stabilization panel.

Anchor Frame
   Reference point to anchor stabilization:
   other frames will be adjusted relative to this frame's position, orientation and scale.
   You might want to select a frame number where your main subject is featured in an optimal way.

Stabilization Type
   Rotation
      In addition to location, stabilizes detected rotation around the *rotation pivot point*,
      which is the weighted average of all location tracking points.

   Scale
      Compensates any scale changes relative to center of rotation.

Tracks for Stabilization
   Location
      List of tracks to be used to compensate for camera jumps, or location movement.

   Rotation/Scale
      List of tracks to be used to compensate for camera tilts and scale changes.

Autoscale
   Finds smallest scale factor which, when applied to the footage,
   would eliminate all empty black borders near the image boundaries.

   Max
      Limits the amount of automatic scaling.

Expected Position X/Y
   Known relative offset of original shot, will be subtracted, e.g. for panning shots.
Expected Rotation
   Rotation present on original shot, will be compensated, e.g. for deliberate tilting.
Expected Zoom
   Explicitly scale resulting frame to compensate zoom of original shot.

Influence
   The amount of transformation applied to the footage can be controlled.
   In some cases it is not necessary to fully compensate camera jumps.
   The amount of stabilization applied to the footage can be controlled.
   In some cases you may not want to fully compensate some of the camera's jumps.
   Please note that these "\* *Influence*" parameters do control only the *compensation movements*
   calculated by the stabilizer, not the deliberate movements added through the "*Expected* \*"-parameters.

Interpolate
   The stabilizer calculates compensation movements with sub-pixel accuracy.
   Consequently, a resulting image pixel needs to be derived from several adjacent source footage pixels.
   Unfortunately, any interpolation causes some minor degree of softening and loss of image quality.

   Nearest
      No interpolation, uses nearest neighboring pixel.
      This setting basically retains the original image's sharpness.
      The downside is we also retain residual movement below the size of one pixel,
      and compensation movements are done in 1 pixel steps, which might be noticeable as irregular jumps.
   Bilinear
      Simple linear interpolation between adjacent pixels.
   Bicubic
      Highest quality interpolation, most expensive to calculate.


## Workflow

********
Workflow
********

Depending on the original footage's properties, achieving good stabilization results might be simple and easy,
or it might require some work, dedication and careful planning. This section covers some practical considerations
to help improving the results.


The Simple Case
===============

Whenever the camera is basically fixed, or at least "almost" stationary, and the footage is crisp and
without motion blur, perfect stabilization is easy to achieve. This might be the case when a tripod was used,
but wind or vibrations on the floor (e.g. on a stage) caused some minor shakes.
Shoulder camera shots done by an experienced operator also frequently fall into this category.

- Use as few points as possible. Start with a single point right on the main subject.
- Track this single point as accurate as possible. Beware of movements and shape changes of the tracked feature.
  Proceed in small increments (e.g. 50 frames), zoom in and readjust the target point manually when it drifts away.
  Another option is to use a larger target area for tracking; since we're tracking only a single point,
  the slower tracking speed might be acceptable.
- After enabling the basic (location) stabilization, consider if you really need rotation stabilization.
  Often, some minor, slow swinging movements are not really noticeable and do not warrant the additional working time
  and quality loss caused by rotation and scale stabilization.
- For rotation, start with one extra point, well spaced but preferably still attached to the main subject.
- Consider to fix some slow residual motion by manually animating the "*Expected* \*" parameters,
  before you even think of adding more tracking markers. Because doing so is often not worth the effort.
- If you need to add more points, the most important goal is to achieve *symmetry.*
  Place location tracking points symmetrically above and below the horizon.
  Place rotation tracking points into diagonally opposed direction, always centered around the main focal area.


Avoid Problematic Footage
=========================

The 2D stabilizer can not work miracles; some flaws simply can not be fixed satisfactory.
Notorious issues are motion blur, rolling shutter, pumping autofocus and moving compression artifacts.
Especially if you do succeed with basic stabilization, such image flaws become yet the more noticeable and annoying.
When on set or on location, it might be tempting to "fix matters in postpro".
Resist that deception, it rarely works out well.

- Prefer a short exposure time to avoid motion blur.
  While motion blur is good to render filmed movements more smooth and natural,
  it seriously impedes the ability to track features precisely.
  As a guideline, try to get at least to 1/250 s.
- Prefer higher frame rates. The more *temporal resolution* the stabilizer has to work on, the better the results.
  If you have the option to choose between progressive and interlaced modes, by all means use interlaced
  and deinterlace the footage to the *doubled frame rate*. This can be done with
  the `yadif <https://ffmpeg.org/ffmpeg-filters.html#yadif-1>`__ filter of FFmpeg: use the mode 1 (``send_field``).
- Beware of the :term:`Rolling Shutter` effect. Avoid fast lateral movements.
  If you can, prefer a camera which produces less rolling shutter.
  Also, using a higher frame rate reduces the amount of rolling shutter; another reason to prefer
  interlaced over progressive for the purpose at hand.
- Switch off autofocus.
  Better plan your movement beforehand, set a fixed focus and rely on depth of field through using a small aperture.
  Pumping movements might not be so noticeable to the human observer, but the feature tracking tends to slide away
  on defocused image elements; fixing this manually after the fact can cause a huge waste of time.
- Increase the lighting level, at least use a higher sensitivity.
  This helps to set a fast shutter speed plus a small aperture.
  Better lighting and good exposure also help to reduce the impact of compression artifacts.
  If you can, also select a codec with less data reduction, better color space, etc.
  Inevitably, we're loosing some quality through the interpolation necessary for stabilization.
  Plus we're loosing some quality due to color space conversion.


Elaborate Movements
===================

When the footage builds on elaborate intended movement of the camera,
the process of stabilization becomes more involved --
especially when there is a shift in the main area of interest within the shot.
When working with many tracks and fine-grained animation,
it is easy to get into a situation where additional manipulations actually decrease the quality,
while it might be hard to spot and locate the root cause of problems.
Recommendation is to proceed systematically, starting from the general outline down to tweaking of specific aspects.

#. Understand the nature of the movements in the shot, both the intended and the accidental.
#. Track some relevant features for location.
#. Establish the basic location stabilization.
   This includes the decision, which feature to use for what segment of the shot.
   Work with the track weights to get an overall consistent movement of the weight center,
   in accordance with the inherent focus of the shot.
#. Define the panning movements of the virtual camera (through animation of the *Expected Position* parameter).
#. Add tracking for rotation and zoom stabilization.
#. Fine-tuning pass:

   Break down the whole duration of the shot into logical segments to define the intended camera movement.
   Then refine those segments incrementally step-by-step, until the overall result looks satisfactory...


Animating Stabilization Parameters
==================================

Animating some parameters over duration of the shot is often necessary, at least to get the final touch,
including control of the scale factor to hide the dancing black borders.
Unfortunately there is a **known limitation** in the current version:
it is not possible to open the generic animation editors (Graph editor and Dope Sheet)
for animation data beyond the 3D scene. So, while it *is possible* to set keyframes *right within the UI controls*
of the stabilizer (either through pressing the :kbd:`I` key or with the help of the context menu),
it is not possible to manipulate the resulting curves graphically.
The only way to readjust or remove a misguided keyframe is to locate
the timeline to the very frame and then use the context menu of the animated UI control.
(Hint: the color of the UI control changes when you have located at precisely the frame number of the keyframe.)


Irregular Track Setup
=====================

It might not be possible to track a given feature over the whole duration of the shot.
The feature might be blurred or obscured; it might even move out of sight entirely,
due to deliberate camera movement.
In such a situation, we need *another tracked feature* to take on its role, and we need some *overlap time*
to get a smooth transition without visible jump.

.. figure:: /images/movie-clip_tracking_clip_sidebar_stabilization_workflow_irregular-tracks.png
   :align: right
   :width: 250px

   Irregular Tracks.

The stabilizer is able to deal with gaps and partial coverage within the given tracks.
However, the basic assumption is that each track covers a single,
fixed reference point whenever there is any usable/enabled data.
Thus, you must not "reuse" a given track to follow several different points,
rather you should disable and thus end one track, when tracking this feature is no longer feasible.
You may include "gaps", when a tracking point is temporarily disabled or unavailable,
but you should start a new track for each distinct new feature to be tracked.

Each track contributes to the overall result by the degree controlled through its *Stab Weight* parameter.
It is evaluated on a per-frame basis, which enables us to control the influence of a track by *animating* this
*Stab Weight*. You may imagine the overall working of the stabilizer as if each tracking point "drags" the image
through a flexible spring: When you turn down the *Stab Weight* of a tracking point,
you decrease the amount of "drag"
it creates. Sometimes the contribution of different tracks has to work partially counter each other.
This effect might be used to cancel out spurious movement, e.g. as caused by perspective.
But when, in such a situation, one of the involved tracks suddenly goes away,
a jump in image position or rotation might be the result. Thus, whenever we notice
a jump at the very frame where some partially covered track starts or ends, we need to soften the transition.
We do so by animating the *Stab Weight* gradually down, so that it reaches zero at the boundary point.
In a similar vein, when we plan a "handover" between several partially covered tracks, we define a *cross-fade* over
the duration where the tracks overlap, again by animating the *Stab Weight* parameters accordingly.
But even with such cross-fade smoothing, some residual movement might remain,
which then needs to be corrected with the *Expected Position*
or *Expected rotation* parameters. It is crucial to avoid "overshooting" movements in such a situation --
always strive at setting the animation keyframes onto precisely the same frame number
for all the tracks and parameters involved.


## Camera

.. _bpy.types.MovieTrackingCamera:

******
Camera
******

This panel contains all settings of the camera used for filming the movie
which is currently being edited in the Clip editor.
Different predefined settings can be used here and can be chosen from the panel header.
But such settings as distortion coefficients and principal point are not included in the presets and
should be filled in even if camera presets are used.

.. _bpy.types.MovieTrackingCamera.sensor_width:

Sensor Width
   Is the width of the CCD sensor in the camera. This value can be found in camera specifications.

.. _bpy.types.MovieTrackingCamera.pixel_aspect:

Pixel Aspect
   Is the pixel aspect of the CCD sensor. This value can be found in camera specifications,
   but can also be guessed. For example, you know that the footage should be 1920×1080,
   but the images themselves are 1280×1080. In this case, the pixel aspect is: 1920 / 1280 = 1.5.

.. _bpy.types.MovieTrackingCamera.lens:

Lens
====

.. _bpy.types.MovieTrackingCamera.focal_length:

Focal Length
   Is self-explanatory; it is the focal length with which the movie was shot.
   It can be set in millimeters or pixels.

.. _bpy.types.MovieTrackingCamera.principal:

Optical Center
   Is the optical center of the lens used in the camera. In most cases it is equal to the image center,
   but it can be different in some special cases. Check camera/lens specifications in such cases.

   .. tip:: Optical Center also know as the principal point in photogrammetry.

Set Center
   See :ref:`bpy.ops.clip.set_center_principal`.

.. _bpy.types.MovieTrackingCamera.distortion_model:

Lens Distortion
   Mathematical function to convert distorted to undistorted coordinates.

   :Polynomial:
      Polynomial radial distortion. Uses three distortion coefficients: K1, K2, and K3.
   :Division:
      It defines high distortions, which makes this model suitable much better for cameras with fisheye lenses.
      Use two distortion coefficients: K1, K2.
   :Nuke:
      Distortion model used by the Nuke compositor. Use two distortion coefficients K1, K2.
   :Brown:
      Brown-Conrady is one of most advanced mathematical lens distortion models.
      Used to model both radial and tangential distortion. Can use up to four
      radial distortion coefficients: K1 - K4 and up to two tangential distortion coefficients: P1 and P2.

Coefficients
   Coefficients are used to compensate for lens distortion when the movie was shot.
   Currently these values can be tweaked by hand only (there are no calibration tools yet)
   using tools available in Distortion mode. To do this tweak K1 until the solving is the closest to
   the known focal length (but also take grid and annotations into account
   to prevent "impossible" distortion).

   .. _bpy.types.MovieTrackingCamera.k:
   .. _bpy.types.MovieTrackingCamera.division_k:
   .. _bpy.types.MovieTrackingCamera.nuke_k:
   .. _bpy.types.MovieTrackingCamera.brown_k:

   Radial Distortion Coefficients (K1 - K4)
      The coefficients in lens distortion models work independent from each other.
      Positive values will give a barrel distortion while negative values give a pincushion distortion.
      With a mixture of both negative and positive coefficients you can define more complicated
      mustache distortions or other complex distortions, that are less common but not rare.

      .. figure:: /images/movie-clip_tracking_clip_sidebar_track_camera_lens-distortion-k.png

         Example of radial distortion for positive and negative K coefficients.

   .. _bpy.types.MovieTrackingCamera.brown_p:

   Tangential Distortion Coefficients (P1, P2)
      Works independent and allow to compensate for situations when the sensor is not
      perpendicular to a group of lens. The optical center (also called principal point)
      will be shifted (distorted) from the center of the sensor.
      P1 is used to compensate for sensor rotation in Z (vertical) axes,
      while P2 is for compensating sensor rotation in X (horizontal) axes.
      Such distortions can be found in sources from cameras with a sensor stabilization system.

      .. figure:: /images/movie-clip_tracking_clip_sidebar_track_camera_lens-distortions-p.png

         Example of tangential distortion for P coefficients.


## Index

.. _bpy.types.MovieTrackingTrack:

#########
  Track
#########

.. toctree::
   :maxdepth: 2

   track.rst
   objects.rst
   plane_track.rst
   camera.rst
   marker.rst


## Marker


******
Marker
******

.. figure:: /images/movie-clip_tracking_clip_sidebar_track_marker_parameter.svg
   :width: 520px
   :align: center

   Marker schematic.

This panel contains numerical settings for marker position,
pattern and search area dimensions, and offset of anchor point from pattern center.

Enabled
   Toggles the markers affect on the current frame.

Position X, Y
   The X/Y positions of the marker at frame in screen coordinates.

Offset X, Y
   The X/Y offset to parenting point.

Pattern Area Width, Height
   The width/height of a marker's pattern in screen coordinates.

Search Area X, Y
   The X/Y position of search at frame relative to the marker's position.

Search Area Width, Height
   The width/height of the markers search in screen coordinates.


## Objects

.. _bpy.types.MovieTracking.active_object_index:
.. _bpy.ops.clip.tracking_object_new:
.. _bpy.ops.clip.tracking_object_remove:
.. _movie-clip-tracking-properties-object:

*************
Objects Panel
*************

.. figure:: /images/movie-clip_tracking_clip_sidebar_track_objects_panel.png
   :align: right
   :width: 195px

   Objects panel.

This panel contains a :ref:`list view <ui-list-view>` with all objects which can be used for tracking,
camera or object solving.
By default there is only one object in this list which is used for camera solving.
It cannot be deleted and other objects cannot be used for camera solving;
all added objects are used for object tracking and solving only.
These objects can be referenced from Follow Track and Object Solver constraints.
Follow Track uses the camera object by default.

If some tracks were added and tracked to the wrong object, they can be copied to another
object using :menuselection:`Track --> Copy Tracks` and :menuselection:`Track --> Paste Tracks`.

The usage for all kind of objects (used for camera and object tracking) is the same:
track features, set camera data, solve motion. Camera data is sharing between all objects and
refining of camera intrinsics happens when solving camera motion only.


## Plane Track


***********
Plane Track
***********

.. figure:: /images/movie-clip_tracking_clip_sidebar_track_plane-track_panel.png
   :align: right
   :width: 195px

   Plane Track panel.

Its properties are shown only when a plane track is selected.

.. _bpy.types.MovieTrackingPlaneTrack.name:

Name
   The name of the selected plane track is shown. It can also be changed from here.

.. _bpy.types.MovieTrackingPlaneTrack.use_auto_keying:

Auto Keyframe
   Toggles the auto-keyframing for corners of the plane track.
   With this enabled, keyframes will automatically get inserted when any corner is moved.

Image
   Field to select or create an image which will be displayed inside the plane track.
   This image is for preview purposes in the Movie Clip editor only.
   To include it in your final render,
   see :doc:`Plane Track Deform node </compositing/types/tracking/plane_track_deform>`.

New Image from Plane Track
    Creates an image from the pixels of the movieclip that the plane marker "sees" at the current frame.
    This allows to create an unwarped texture of any flat surface in the footage.
    The resulting image can then be used for editing and retouching, for example to paint out certain parts
    of the footage.
Update Image from Plane Track
    Updates the pixels of the active Plane Track's image.

.. _bpy.types.MovieTrackingPlaneTrack.image_opacity:

Opacity
   Used to set the opacity of this image. Again,
   this is for display purposes only, and will not affect your final render.


## Track


*****
Track
*****

.. figure:: /images/movie-clip_tracking_clip_sidebar_track_track_panel.png
   :align: right
   :width: 195px

   Track panel.

.. _bpy.types.MovieTrackingTrack.name:

Name
   The track name can be changed with this field.
   Track names are used for linking tracking data to other areas, like a Follow Track constraint.

Enable (eye icon)
   This toggle controls if the marker is enabled.
   If a marker is disabled, its position is not used either by solver nor by constraints.

.. _bpy.types.MovieTrackingTrack.lock:

Lock (padlock icon)
   The toggle controls whether the track is locked. Locked tracks cannot be edited at all.
   This helps to prevent accidental changes to tracks which are "finished"
   (tracked accurate along the whole footage).


Track Preview Widget
====================

The widget in this panel is called "Track Preview" and it displays the content of the pattern area.
This helps to check how accurately the feature is being tracked
(controlling that there is no sliding off original position)
and also helps to move the track back to the correct position.
The track can be moved directly using this widget by mouse dragging.

If an anchor is used
(the position in the image which is tracking is different from the position which is used for parenting),
a preview widget will display the area around the anchor position.
This configuration helps in masking some things when there is no good feature at position where
the mask corner should be placed. Details of this technique will be written later.

There is small area below the preview widget which can be used to enlarge the vertical size of
preview widget (the area is highlighted with two horizontal lines).


Further Options
===============

.. _bpy.types.MovieTrackingTrack.use_red_channel:
.. _bpy.types.MovieTrackingTrack.use_green_channel:
.. _bpy.types.MovieTrackingTrack.use_blue_channel:

R, G, B
   Tracking happens in gray-scale space, so a high contrast between the feature and
   its background yields more accurate tracking.
   In such cases disabling some color channels can help.

.. _bpy.types.MovieTrackingTrack.use_grayscale_preview:

Grayscale Preview (B/W)
   Display the preview image as gray-scale even if all channels are enabled.

.. _bpy.types.MovieTrackingTrack.use_alpha_preview:

Mask Preview (black/white icon)
   Applies mask defined by an annotation tool in the preview widget.

.. _bpy.types.MovieTrackingTrack.weight:

Weight
   When several tracks are used for 3D camera reconstruction, it is possible to assign
   a reduced weight to some tracks to control their influence on the solution result.
   This parameter can (and often need to) be animated.

   Altering the weights of problem tracking markers can correct or greatly reduce undesirable jumps
   as feature disappear or become difficult to track.

   Another use of Track Weights is when you want to reconstruct a scene from your camera solution.
   In that case you can first carefully track and solve your scene, and once you are done,
   lock all your markers with :kbd:`Ctrl-L`, set the tracker weight in the Extra Settings of
   the tracker settings to zero and use the feature detection to quickly add lots of markers.
   Now track them and solve the scene again. Since their weight is zero
   they will not influence your solution at all, but you will have lots of good reference points in your scene.

.. _bpy.types.MovieTrackingTrack.weight_stab:

Stabilization Weight
   While *Weight* parameter is used for 3D reconstruction,
   the *Stabilization Weight* is used to control 2D stabilization.

.. _bpy.ops.clip.track_copy_color:
.. _bpy.types.MovieTrackingTrack.use_custom_color:

Custom Color Presets
   The preset for the *Custom Color*.

.. _bpy.types.MovieTrackingTrack.color:

Custom Color
   This setting overrides the default marker color used in the Clip editor and 3D Viewport,
   and it helps to distinguish different type of features
   (for example, features in the background vs. foreground and so on).
   Color also can be used for "grouping" tracks so a whole group of tracks can be selected by
   color using the Select Grouped operator.

.. tip::

   To select good points for tracking, use points in the middle of the footage timeline
   and track backwards and forwards from there.
   This will provide a greater chance of the marker and point staying in the camera shot.


## Index


###########
  Toolbar
###########

.. toctree::
   :maxdepth: 2

   track.rst
   solve.rst


## Solve


*****
Solve
*****

Plane Track
===========

See :ref:`bpy.ops.clip.create_plane_track`.


Solve
=====

.. _bpy.types.MovieTrackingSettings.use_tripod_solver:

Tripod
   Tripod Motion can be used for footage where the camera does not move and only rotates.
   Such footage can't be tracked with a generic solver approach, and
   it is impossible to determine the actual feature points in space due to a lack of information.
   So this solver will solve only the relative camera rotation and then reproject the feature points into a sphere,
   with the same distance between feature and camera for all feature points.

   .. note::

      This is special type of camera solver and it behaves different from regular solver.
      It means using more tracks doesn't imply more accurate solution.
      Having 5-10 tracks on frame is likely what shall be commonly used for this kind of solver.

.. _bpy.types.MovieTrackingSettings.use_keyframe_selection:

Keyframe
   Automatically select keyframes for initial reconstruction.
   This option enables complex algorithms which tries to find a keyframe pair
   with minimal reconstruction error and best scene scale guess.

.. _bpy.types.MovieTrackingObject.keyframe_a:
.. _bpy.types.MovieTrackingObject.keyframe_b:

Keyframe A/B
   Start (A) and End (B) frame of the range used for reconstruction.

Refine
   Specifies which parameters should be refined during solve.
   Such refining is useful when you are not sure about some camera intrinsics,
   and solver should try to find the best parameter for those intrinsics.
   But you still have to know approximate initial values --
   it will fail to find correct values if they were set completely incorrectly initially.

   .. _bpy.types.MovieTrackingSettings.refine_intrinsics_focal_length:

   Focal Length
      Refine the camera's :ref:`Focal Length <bpy.types.MovieTrackingCamera.focal_length>`.

   .. _bpy.types.MovieTrackingSettings.refine_intrinsics_principal_point:

   Optical Center
      Refine the camera's :ref:`Optical Center <bpy.types.MovieTrackingCamera.principal>`.

   .. _bpy.types.MovieTrackingSettings.refine_intrinsics_radial_distortion:

   Radial Distortion
      Refine the camera's :ref:`Radial Distortion Parameters <bpy.types.MovieTrackingCamera.k>`.

   .. _bpy.types.MovieTrackingSettings.refine_intrinsics_tangential_distortion:

   Tangential Distortion
      Refine the camera's :ref:`Tangential Distortion Parameters <bpy.types.MovieTrackingCamera.brown_p>`.

.. _editors-movie-clip-tracking-clip-solve-motion:

Solve Camera/Object Motion
   See :ref:`bpy.ops.clip.solve_camera`.


Cleanup
=======

This panel contains operators and their settings which are needed to clean up bad tracks:
tracks which are not tracked long enough or which failed to reconstruct accurately.

Frames
   Tracks or tracked segments shorter than this number of frames will be removed.

Error
   Tracks which has reprojection error higher than this value will be removed.

Type
   Several actions can be performed for bad tracks:

   Select
      They can simply be selected.
   Delete Track
      The whole track can be deleted.
   Delete Segments
      Bad segments of tracked sequence can be removed.

Clean Tracks
   See :ref:`bpy.ops.clip.clean_tracks`.
Filter Tracks
   See :ref:`bpy.ops.clip.filter_tracks`.


Geometry
========

3D Markers to Mesh
   See :ref:`bpy.ops.clip.bundles_to_mesh`.
Link Empty to Track
   See :ref:`bpy.ops.clip.track_to_empty`.


Orientation
===========

Scene orientation tools can be used for orienting object to bundles.

Floor
   See :ref:`bpy.ops.clip.set_origin`.
Wall
   See :ref:`bpy.ops.clip.set_plane`.
Set Origin
   See :ref:`bpy.ops.clip.set_plane`.
Set X, Y Axis
   See :ref:`bpy.ops.clip.set_axis`.
Set Scale
   See :ref:`bpy.ops.clip.set_scale`.
Apply Scale
   See :ref:`bpy.ops.clip.apply_solution_scale`.

Distance
   Distance in active scene units which is used by Set/Apply scale.


Scene Setup
===========

Set as Background
   See :ref:`bpy.ops.clip.set_viewport_background`.
Setup Tracking Scene
   See :ref:`bpy.ops.clip.setup_tracking_scene`.


## Track


*****
Track
*****

Clip
====

Set Scene Frames
   See :ref:`bpy.ops.clip.set_scene_frames`.
Prefetch
   See :ref:`bpy.ops.clip.prefetch`.
Reload
   See :ref:`bpy.ops.clip.reload`.


Marker
======

Add
   See :ref:`bpy.ops.clip.add_marker_move`.
Delete
   See :ref:`bpy.ops.clip.delete_track`.
Detect Features
   See :ref:`bpy.ops.clip.detect_features`.


.. _clip-tracking-settings:

Tracking Settings
=================

This panel contains all settings for the 2D tracking algorithms.
Preset tracking settings can be configured in the panel header.
These presets are based on tracking experience of real footage and
provides good start values to begin working with a specific footage.

Pattern Size, Search Size
   Defines size of a newly created tracks.

Motion Model
   Defines which possible motions tracking feature has. This option should be set depending on
   which motion a particular feature has and it will make tracking most accurate for such a motion.

   Location, Location & Rotation, Location & Scale, Location, Rotation & Scale, Affine

   Perspective
      Is usually used to track a planar feature,
      but often *Affine* is a good enough approximation and may have more stable tracks.

Match
   Controls which patterns get tracked; to be more precise,
   the pattern from which frame is getting tracked. Here is an example which should make things clearer.

   The tracker algorithm receives two images inside the search area and the position of a point
   to be tracked in the first image.
   The tracker tries to find the position of that point from the first image in the second image.

   Now, this is how tracking of the sequence happens.
   The second image is always from a frame at which the position of marker is not known
   (next tracking frame). But a different first image
   (instead of the one that immediately precedes the second image in the footage)
   can be sent to the tracker.

   Keyframe
      An image created from a frame on which the track was keyframed.
      This configuration prevents sliding from the original position
      (because the position which best corresponds to the original pattern is returned by the tracker),
      but it can lead to small jumps and can lead to failures when the feature point is deformed due to camera motion
      (perspective transformation, for example).
   Previous Frame
      Keyframes for tracks are creating every frames,
      and tracking between keyframed image and next image is used.
      In this configuration the pattern is tracking between two neighboring frames.
      It allows dealing with cases of large transformations of the feature point
      but can lead to sliding from the original position, so it should be controlled.

Prepass
   Enables a two pass tracking, where the first pass is a brute force tracking of location only, and
   the second pass will use tracking of the full motion model refining the first pass.

Normalize
   Means patterns will be normalized by their average intensity while tracking,
   to make them invariant to illumination changes. An example where this is useful is a scene where
   a marker moves in the shadow of an object.

R, G, B
   Defines color channels which will be used by a tracking algorithm.
   Disabling some colors might increase the contrast to enhance the feature detection.

Copy from Active Track
   Copies all settings from active track. Allows to ease creation of new tracks with the same setting.

.. (alt) Previous frame: An image created from the current frame is sent as first image to the tracker.


Tracking Extra Settings
-----------------------

Weight
   See Track :ref:`Weight <bpy.types.MovieTrackingTrack.weight>`.

Correlation
   This value defines the minimal correlation between
   a matched pattern and a reference to be considered a successful tracking.
   If the tracker is stops too early, decrease this value, or if the track is slipping too much
   when it should stop sooner, increase this value.

Margin
   Can be used disable tracks when they become too close to the image boundary.
   This slider sets "too close" in pixels.

Use Mask
   Allows to use annotation tool to mask part of a pattern, narrowing down what the tracker algorithm is
   attempting to match across frames.

Frames Limit
   Controls how many frames can be tracked when the Track Sequence operator is called.
   So, each Track Sequence operation would track maximum *Frames Limit* frames.
   This also helps to notice a slide-off of tracks and correct them.

Speed
   Marker settings only -- Can be used to control the speed of sequence tracking.
   This option does not affect the quality of tracking; it just helps to control if tracking happens accurately.
   In most cases tracking happens much faster than real-time, and it is difficult to notice when a track began
   to slide out of position. In such cases *Speed* can be set to Double or Half to add some delay between
   tracking two frames, so a slide-off would be noticed earlier and the tracking process can be canceled to
   adjust positions of tracks.


Track
=====

Track
   See :ref:`bpy.ops.clip.track_markers`.
Clear
   See :ref:`bpy.ops.clip.clear_track_path`.
Refine
   See :ref:`bpy.ops.clip.refine_markers`.
Merge
   Join Tracks
      See :ref:`bpy.ops.clip.join_tracks`.


