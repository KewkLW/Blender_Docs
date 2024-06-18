# Index for sculpt_paint

- [Index](#Index)
- [Introduction](#Introduction)
- [Navigation](#Navigation)
- [Selection Visibility](#Selection-Visibility)
- [Brush](#Brush)
- [Brush Settings](#Brush-Settings)
- [Cursor](#Cursor)
- [Falloff](#Falloff)
- [Index](#Index)
- [Introduction](#Introduction)
- [Stroke](#Stroke)
- [Texture](#Texture)
- [Index](#Index)
- [Introduction](#Introduction)
- [Tools Settings](#Tools-Settings)
- [Add Curves](#Add-Curves)
- [Comb Curves](#Comb-Curves)
- [Delete Curves](#Delete-Curves)
- [Density Curves](#Density-Curves)
- [Grow Shrink Curves](#Grow-Shrink-Curves)
- [Index](#Index)
- [Pinch Curves](#Pinch-Curves)
- [Puff Curves](#Puff-Curves)
- [Selection Paint](#Selection-Paint)
- [Slide Curves](#Slide-Curves)
- [Smooth Curves](#Smooth-Curves)
- [Snake Hook Curves](#Snake-Hook-Curves)
- [Controls](#Controls)
- [Index](#Index)
- [Toolbar](#Toolbar)
- [Expand](#Expand)
- [Face Sets](#Face-Sets)
- [Index](#Index)
- [Mask](#Mask)
- [Sculpt](#Sculpt)
- [Adaptive](#Adaptive)
- [Brush](#Brush)
- [Cloth Sculpting](#Cloth-Sculpting)
- [Filters](#Filters)
- [General](#General)
- [Index](#Index)
- [Multiple Objects](#Multiple-Objects)
- [Painting](#Painting)
- [Transforming](#Transforming)
- [Visibility Masking Face Sets](#Visibility-Masking-Face-Sets)
- [Blob](#Blob)
- [Boundary](#Boundary)
- [Box Face Set](#Box-Face-Set)
- [Box Mask](#Box-Mask)
- [Box Trim](#Box-Trim)
- [Clay](#Clay)
- [Clay Strips](#Clay-Strips)
- [Clay Thumb](#Clay-Thumb)
- [Cloth](#Cloth)
- [Cloth Filter](#Cloth-Filter)
- [Color Filter](#Color-Filter)
- [Crease](#Crease)
- [Draw](#Draw)
- [Draw Facesets](#Draw-Facesets)
- [Draw Sharp](#Draw-Sharp)
- [Edit Face Set](#Edit-Face-Set)
- [Elastic Deform](#Elastic-Deform)
- [Fill](#Fill)
- [Flatten](#Flatten)
- [Grab](#Grab)
- [Index](#Index)
- [Inflate](#Inflate)
- [Lasso Face Set](#Lasso-Face-Set)
- [Lasso Mask](#Lasso-Mask)
- [Lasso Trim](#Lasso-Trim)
- [Layer](#Layer)
- [Line Mask](#Line-Mask)
- [Line Project](#Line-Project)
- [Mask](#Mask)
- [Mask By Color](#Mask-By-Color)
- [Mesh Filter](#Mesh-Filter)
- [Multiplane Scrape](#Multiplane-Scrape)
- [Multires Displacement Eraser](#Multires-Displacement-Eraser)
- [Multires Displacement Smear](#Multires-Displacement-Smear)
- [Nudge](#Nudge)
- [Paint](#Paint)
- [Pinch](#Pinch)
- [Pose](#Pose)
- [Rotate](#Rotate)
- [Scrape](#Scrape)
- [Simplify](#Simplify)
- [Slide Relax](#Slide-Relax)
- [Smear](#Smear)
- [Smooth](#Smooth)
- [Snake Hook](#Snake-Hook)
- [Thumb](#Thumb)
- [Transforms](#Transforms)
- [Brush Settings](#Brush-Settings)
- [Dyntopo](#Dyntopo)
- [Index](#Index)
- [Options](#Options)
- [Remesh](#Remesh)
- [Symmetry](#Symmetry)
- [Index](#Index)
- [Introduction](#Introduction)
- [Tools](#Tools)
- [Brush Settings](#Brush-Settings)
- [Index](#Index)
- [Mask](#Mask)
- [Options](#Options)
- [Symmetry](#Symmetry)
- [Texture Slots](#Texture-Slots)
- [Tiling](#Tiling)
- [Editing](#Editing)
- [Index](#Index)
- [Introduction](#Introduction)
- [Tools](#Tools)
- [Brush Settings](#Brush-Settings)
- [Index](#Index)
- [Symmetry](#Symmetry)
- [Editing](#Editing)
- [Index](#Index)
- [Introduction](#Introduction)
- [Tools](#Tools)
- [Usage](#Usage)
- [Brush Settings](#Brush-Settings)
- [Index](#Index)
- [Options](#Options)
- [Symmetry](#Symmetry)


## Index

.. _painting-index:
.. _bpy.ops.paint:
.. _bpy.types.Paint:

########################
  Sculpting & Painting
########################

.. toctree::
   :maxdepth: 2

   introduction.rst
   brush/index.rst
   selection_visibility.rst
   navigation.rst


Modes
=====

.. toctree::
   :maxdepth: 2

   sculpting/index.rst
   texture_paint/index.rst
   vertex_paint/index.rst
   weight_paint/index.rst
   curves_sculpting/index.rst


## Introduction


************
Introduction
************

Sculpting and painting offers a more freeform workflow of editing via :doc:`brushes </sculpt_paint/brush/index>`.
There are several :doc:`modes </editors/3dview/modes>` to do this, each with their own purpose.

- :doc:`Sculpting </sculpt_paint/sculpting/introduction/general>`:
  Change and transform the topology of your mesh.
- :doc:`Vertex Paint </sculpt_paint/vertex_paint/introduction>`:
  Change the color of vertices in the active Color Attribute.
- :doc:`Weight Paint </sculpt_paint/weight_paint/introduction>`:
  Change the weight of vertices in the active vertex group.
- :doc:`Texture Paint </sculpt_paint/texture_paint/introduction>`:
  Change the pixels of the active image texture.


## Navigation


**********
Navigation
**********

There are different preferences for navigating the 3D Viewport in Blender.
For painting and sculpting specific workflows it is recommended to use any of the following methods.

Center View to Mouse :kbd:`Alt MMB`
   Center the View on the surface directly under the mouse position.
   This way the rotation point of the viewport can be manually changed to any point you wish to orbit around.

Center on Last Stroke :kbd:`NumpadPeriod`
   Center the View on the average position of the last stroke.

Various preferences can also make navigation more convenient.
These can be found in the "Navigation" tab of the preferences.

Orbit Method = Trackball
   Tumble the view based on the mouse position in your 3D Viewport while rotating.
   This makes it very easy to tilt the viewport freely,
   instead of having the Z axis of the viewport locked.

.. Needs a visual example to make it easier to understand.

:ref:`Zoom to Mouse Position <bpy.types.PreferencesInput.use_zoom_to_mouse>`
   Use the mouse position to zoom towards and rotate around the surface that is pointed at.
   This can be an alternative to the repeated manual use of the Center View to Mouse operator.

   The disadvantage is that this navigation preference can lead to accidental navigation
   around backfacing geometry or very distant geometry.

.. Needs a visual reference of where to find both.


## Selection Visibility


**********************
Selection & Visibility
**********************

Selection Masking
=================

If you have a complex mesh, it is sometimes not easy to paint on the intended vertices.
Suppose you only want to paint on a small area of the Mesh and keep the rest untouched.
This is where "selection masking" comes into play. When this mode is enabled,
a brush will only paint on the selected vertices or faces.
The option is available from the header of the 3D Viewport
(see icons surrounded by the yellow frame):

.. figure:: /images/sculpt-paint_brush_introduction_select.webp

   You can choose between *Face Selection masking* (left button), *Vertex
   selection masking* (middle button), and *Bone selection* (right button). The
   latter is only available when the mesh has an Armature modifier.

Selection masking has some advantages over the default paint mode:

- The original mesh edges are shown, even when modifiers are active.
- You can select and deselect faces instead without the need to switch to Edit Mode.


Details About Selecting
-----------------------

The following standard selection operations are supported:

- :kbd:`Alt-LMB` -- Single faces
- :kbd:`Shift-Alt-LMB` -- Select more or remove them from the selection.
- :kbd:`A` -- All faces, :kbd:`A A` to deselect.
- :kbd:`B` -- Box selection.
- :kbd:`C` -- Circle select with brush.
- :kbd:`Ctrl-I` -- Invert selection.
- :kbd:`L` -- Pick linked (under the mouse cursor).
- :kbd:`Ctrl-L` -- Select linked.
- :kbd:`Ctrl-NumpadPlus` -- Extend Selection
- :kbd:`Ctrl-NumpadMinus` -- Shrink Selection

The following only work for face selection and with the selection tool active:

- :kbd:`Alt-LMB` -- Loop Select


Vertex Selection Masking
------------------------

.. reference::

   :Mode:      Vertex and Weight Paint Modes
   :Header:    :menuselection:`Vertex Selection`
   :Shortcut:  :kbd:`2`

In this mode you can select one or more vertices and then paint only on the selection.
All unselected vertices are protected from unintentional changes.

.. figure:: /images/sculpt-paint_brush_introduction_vertex-select.png

   Vertex Selection masking.


.. _bpy.types.Mesh.use_paint_mask:

Face Selection Masking
----------------------

.. reference::

   :Mode:      Texture, Vertex, and Weight Paint Modes
   :Header:    :menuselection:`Paint Mask`
   :Shortcut:  :kbd:`1`

The *Face Selection masking* allows you to select faces and limit the paint
tool to those faces, very similar to Vertex selection masking.

.. figure:: /images/sculpt-paint_brush_introduction_face-select.png

   Face Selection masking.

.. The visual example needs to be updated. Ideally show hard edges on painted face corners.

Hide/Unhide Faces
-----------------

.. figure:: /images/sculpt-paint_brush_introduction_face-select-hidden.png

   Hidden faces.

You also can hide selected faces as in Edit Mode with the keyboard Shortcut :kbd:`H`,
then paint on the remaining visible faces and finally unhide the hidden faces again by using
:kbd:`Alt-H`.


Hide/Unhide Vertices
--------------------

You cannot specifically hide only selected faces in vertex mask selection mode.
However, the selection is converted when switching selection modes.
So a common trick is to:

#. Switch to Face selection mask mode to have the selection converted to faces.
#. Refine your selection next or just hide the faces.
#. Switch back to Vertex Selection mask mode.

Hidig faces will make sure that vertices that belong to visible faces remain visible.


.. _clipping_region:

The Clipping Region
-------------------

To constrain the paint area further you can use the *Clipping Region*.
Press :kbd:`Alt-B` and :kbd:`LMB`-drag a rectangular area.
The selected area will be "cut out" as the area of interest.
The rest of the 3D Viewport gets hidden.

.. figure:: /images/sculpt-paint_brush_introduction_border-select.png

   The Clipping Region is used to select interesting parts for local painting.

.. This visual example could include the (Clipped) text info overlay

You make the entire mesh visible again by pressing :kbd:`Alt-B` a second time.

All paint tools that use the view respect this clipping, including box select, and of course brush strokes.

There are two helpful reminders that a Clipping Region is used:

#. The clipping region is drawn as a grey box in the 3D Viewport
#. The Text Info overlay will state that the perspective is "Clipped"


.. _bpy.ops.paint.vert_select_linked:

Select Linked
=============

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Select --> Select Linked --> Linked`
   :Shortcut:  :kbd:`Ctrl-L`, :kbd:`Shift-L`

Select geometry connected to already selected elements.
This is often useful when a mesh has disconnected, overlapping parts,
where isolating it any other way would be tedious.
Pressing :kbd:`Shift-L` will deselect linked any linked elements.

With :kbd:`L` you can also select connected geometry directly under the cursor.


## Brush

.. _bpy.types.Brush:
.. _bpy.ops.brush:
.. _bpy.types.UnifiedPaintSettings:

*******
Brushes
*******

.. reference::

   :Mode:      Sculpt Mode
   :Panel:     :menuselection:`Sidebar --> Tools --> Brushes`

For painting/sculpting modes each brush type is exposed as a tool in the toolbar.
The brush on the other hand is a saved preset of all the brush settings, including a name and thumbnail.

All these settings can be found and changed here in the tool setting (brush, texture, stroke, falloff & cursor).

.. figure:: /images/sculpt-paint_brush_brush_data-block-menu.png
   :align: right

   Brush panel in the tool settings.

Brushes
   Clicking on the brush thumbnail will open the :ref:`ui-data-block` to select a brush.

   Add Brush (Duplicate icon)
      When you add a brush, the new brush is a duplicate of the current one.
   Fake User (Shield icon)
      Enabling this button will ensure that the brush will not be deleted,
      even if it is not used by any tool.
   Unlink Data-Block (Cross icon)
      Unassign the brush from the active tool.
      Hold :kbd:`Shift` to remove the brush from all users,
      so it will be deleted upon reloading the file or purging orphan data.

   Brush Specials (Arrow button)
      Enabled Modes
         Enable the brush to be used in different (even multiple) modes.
         For example, the exact same brushes are used in both Weight Paint
         and Vertex Paint mode.
      Tool Selection
         Transfer the brush preset to be used by a different brush type.
      Reset Brush
         Reset all brush settings to the default values of the current brush type.

.. _bpy.types.Brush.use_custom_icon:
.. _bpy.types.Brush.icon_filepath:

   Custom Icon
      Define a custom brush thumbnail from an image file.


## Brush Settings


**************
Brush Settings
**************

Each mode and brush has unique brush settings.
But there is also a lot of overlap or similar settings.
This page explains general and mode specific settings that are used across various brushes in more detail.


.. _sculpt-tool-settings-brush-settings-general:

General
=======

.. _bpy.types.Brush.size:

Radius
   This option controls the size of the brush, measured in pixels.
   :kbd:`F` allows you to change the brush size interactively by
   dragging the mouse from left to right and then :kbd:`LMB` to accept.
   Meanwhile the texture of the brush will be visible inside the circle.
   You can also enter the size numerically with the number keys.

   The size can be decreased/increased using :kbd:`[` and :kbd:`]` respectfully.

   Size Pressure
      Brush size can be affected by enabling the pressure sensitivity icon,
      if you are using a :ref:`Graphics Tablet <hardware-tablet>`.
   Use Unified Radius
      Use the same brush *Radius* across all brushes.

Radius Unit :guilabel:`Sculpt Mode`
   Controls how the brush *Radius* is measured.

   :View:
      The *Radius* is measured based on how the cursor appears on the monitor i.e. "screen space".
   :Scene:
      The *Radius* is measured based on real world units.
      This means that the brush radius stays consistent, independently from zooming in and out in the viewport.
      The unit type and scaling can be configured in the :ref:`Scene Units <bpy.types.UnitSettings>`.

.. _bpy.types.Brush.strength:

Strength
   For painting brushes the *Strength* defines the maximum effect of each brush stroke.
   For example, higher values cause a *Paint* brush to give each stroke a higher opacity.
   The opacity is never stronger than the set *Strength*,
   no matter how often the same surface is painted during the same stroke.

   For sculpting brushes on the other hand the *Strength* relates to how strong each step of the stroke is,
   resulting in a slower/faster buildup towards the full brush effect during the stroke.

   You can change the brush strength interactively by pressing :kbd:`Shift-F`
   and then moving the brush and then :kbd:`LMB`.
   You can also enter the strength numerically with the number keys.

   Strength Pressure
      Brush strength can be affected by enabling the pressure sensitivity icon,
      if a supported tablet is being used.
   Use Unified Strength
      Use the same brush *Strength* across all brushes.

Blend
   Set the way the color or value is applied over the targeted Color Attribute, Vertex Group or Image Texture.
   See :term:`Color Blend Modes`.

   - Add Alpha: makes the image more opaque where painted.
   - Erase Alpha: makes the image transparent where painted,
     allowing background colors and lower-level textures to show through.
     As you "paint", the false checkerboard background will be revealed.
     Using a tablet pen's eraser end will toggle on this mode.

   .. tip::

      In order to see the effects of the Erase and Add Alpha mix modes in the Image Editor,
      the :ref:`Display Channels <bpy.types.SpaceImageEditor.display_channels>`
      must be set to *Color & Alpha* or *Alpha*.
      Transparent (no alpha) areas will then show a checkered background.

Weight :guilabel:`Weight Paint`
   The weight value that is applied to the vertex group.

   Use :kbd:`Shift-X` to sample the weight value of clicked vertex.
   :kbd:`Shift-Ctrl-X` lets you select the group from which to sample from.

.. _bpy.types.Brush.direction:

Direction :kbd:`Ctrl` :guilabel:`Sculpt Mode`
   Brush direction toggle, *Add* raises geometry towards the brush,
   *Subtract* lowers geometry away from the brush. This setting can be toggled with :kbd:`Ctrl` while sculpting.

.. _bpy.types.Brush.normal_radius_factor:

Normal Radius :guilabel:`Sculpt Mode`
   Determines the ratio of how much the brush radius is used to
   sample the normal direction of the sculpt plane of the brush.
   For example, a smaller *Normal Radius* will lead to drastic changes in the brush orientation,
   like for following the contours of hard surface meshes more closely.
   A large *Normal Radius* will lead to smoother changes in orientation,
   like for building overall forms on organic sculptures.

.. _bpy.types.Brush.area_radius_factor:

Area Radius
   The ratio between the brush radius and
   the radius that is going to be used to sample the area plane depth.

.. _bpy.types.Brush.hardness:

Hardness :guilabel:`Sculpt Mode`
   How close the brush falloff starts from the edge of the brush.

.. _bpy.types.Brush.tip_roundness:

Tip Roundness
   The factor to control how round the brush is. A value of zero will make the brush square.
   Note, the :doc:`Brush Falloff </sculpt_paint/brush/falloff>`
   is only applied to the rounded portions of the brush.

.. _bpy.types.Brush.auto_smooth_factor:

Auto-smooth :guilabel:`Sculpt Mode`
   Sets the amount of smoothing to be applied to each stroke.

.. _bpy.types.Brush.topology_rake_factor:

Topology Rake :guilabel:`Sculpt Mode`
    The higher this setting is set, the more :doc:`Dyntopo </sculpt_paint/sculpting/tool_settings/dyntopo>`
    aligns mesh edges to the brush direction while tessellating the surface.
    This generates cleaner edge flow to help define sharp features.
    *Topology Rake* can have a severe performance impact so it works best on low-poly meshes.

    .. figure:: /images/sculpt-paint_sculpting_tool-settings_dyntopo_topology-rake.jpg

Normal Weight :kbd:`Ctrl` :guilabel:`Sculpt Mode`
   Constrains brush movement along the surface normal.
   Especially useful with the *Grab* brush, can be temporarily enabled by holding :kbd:`Ctrl`.
   E.g. *Grab* brush can be used to push a depression (hole) into the mesh when *Normal Weight* is set.

   Applies to *Grab* and *Snake Hook* brushes.

Plane Offset :guilabel:`Sculpt Mode`
   Offset for planar brushes (Clay, Fill, Flatten, Scrape),
   shifts the plane that is found by averaging the faces above or below.

Plane Trim :guilabel:`Sculpt Mode`
   Ability to limit the distance that planar brushes act.
   If trim is enabled vertices that are further away from the offset plane than
   the trim distance are ignored during sculpting.

.. _bpy.types.Brush.crease_pinch_factor:

Pinch/Magnify :guilabel:`Sculpt Mode`
   Pushes the mesh towards/away from the brush center during the stroke.

.. _bpy.types.Brush.deform_target:

Deformation Target
   How the deformation of the brush will affect the object.

   :Geometry: Deform the geometry directly.
   :Cloth Simulation:
      Deform the mesh while a :doc:`cloth simulation </sculpt_paint/sculpting/tools/cloth>`
      is applied to it at the same time.


.. _sculpt-tool-settings-brush-settings-advanced:

Advanced
========

Accumulate
   Causes stroke dabs to accumulate on top of each other.

Front Faces Only
   When enabled, the brush only affects vertices that are facing the viewer.

Affect Alpha :guilabel:`2D Painting Only`
   When this is disabled, it prevents changes to the alpha channel while painting (Only in 3D Viewport).

Anti-Aliasing :guilabel:`2D Painting Only`
   Toggles :term:`Anti-Aliasing` around the brush,
   this is useful if you are working with pixel art or low resolution textures.

.. _bpy.types.Brush.use_automasking_topology:
.. _bpy.types.Brush.use_automasking_boundary_face_sets:
.. _bpy.types.Brush.use_automasking_boundary_edges:
.. _bpy.types.Brush.use_automasking_cavity:
.. _bpy.types.Brush.use_automasking_cavity_inverted:
.. _bpy.types.Brush.use_automasking_view_normal:
.. _bpy.types.Brush.use_automasking_start_normal:
.. _bpy.types.Brush.automasking:

Auto-Masking :guilabel:`Sculpt Mode`
   The auto-masking toggles in the brush settings are the same as the sculpt mode auto-masking settings.
   The difference is that these toggles can be customized per brush to create specific brush behaviors.

.. seealso::

   For more information on the Auto-Masking toggles, see :doc:`Auto-Masking </sculpt_paint/sculpting/controls>`.

.. _bpy.types.Brush.sculpt_plane:

Sculpt Plane :guilabel:`Sculpt Mode`
   Use this menu to set the plane in which the sculpting takes place.
   In other words, the primary direction that the vertices will move.

   :Area Plane:
      The movement takes place in the direction of average normal for all active vertices within the brush area.
      Essentially, this means that the direction is dependent on the surface beneath the brush.
   :View Plane:
      Sculpting in the plane of the current 3D Viewport.
   :X, Y, Z Plane:
      The movement takes place in the positive direction of one of the global axes.

.. _bpy.types.Brush.use_original_normal:
.. _bpy.types.Brush.use_original_plane:

Original :guilabel:`Sculpt Mode`
   Normal
      When locked it keeps using the normal of the surface where stroke was initiated,
      instead of the surface normal currently under the cursor.
   Plane
      When locked keep using the plane origin of surface where stroke was initiated,
      instead of the surface plane currently under the cursor.


Color Picker
============

Color
-----

The color of the brush. See :ref:`ui-color-picker`.

Press :kbd:`Shift-X` on any part of the image to sample that color and set it as the brush color.
Hold :kbd:`Ctrl` while painting to temporally paint with the secondary color.

.. _bpy.ops.paint.brush_colors_flip:

Swap Colors (cycle icon) :kbd:`X`
   Swaps the primary and secondary colors.

Use Unified Color
   Use the same brush color across all brushes.

.. note::

   Note that Vertex Paint works in sRGB :term:`space <Color Space>`, and
   the RGB representation of the same colors will be different between the paint
   tools and the materials that are in linear space.


Gradient
--------

A gradient can be used as a color source.

Gradient Colors
   The :ref:`ui-color-ramp-widget` to define the gradient colors.
Mode
   :Pressure:
      Will choose a color from the color ramp according to the stylus pressure.
   :Clamp:
      Will alter the color along the stroke and as specified by *Gradient Spacing* option.
      With *Clamp* it uses the last color of the color ramp after the specified gradient.
   :Repeat:
      Similar to *Clamp*. After the last color it resets the color to the first color in the color ramp and
      repeats the pattern.


Color Palette
=============

Color Palettes are a way of storing a brush's color so that it can be used at a later time.
This is useful when working with several colors at once.

Palette
   A :ref:`ui-data-block` to select a palette.

New ``+``
   Adds the current brush's primary *Color* to the palette.
Delete ``-``
   Removes the currently selected color from the palette.

Move (up/down arrow icon)
   Moves the selected color up/down one position.

Sort
   Sort Colors by Hue, Saturation, Value, Luminance.

Color List
   Each color that belongs to the palette is presented in a list.
   Clicking on a color will change the brush's primary *Color* to that color.


## Cursor

.. _sculpt-paint-brush-display:
.. _bpy.types.Paint.show_brush:

******
Cursor
******

.. reference::

   :Mode:      All Paint Modes
   :Header:    :menuselection:`Tool Settings --> Brush Settings --> Cursor`
   :Panel:     :menuselection:`Sidebar --> Tool --> Brush Settings --> Cursor`

.. figure:: /images/sculpt-paint_brush_cursor_panel.png
   :align: right
   :width: 400px

   Cursor options.

While painting or sculpting a special cursor is shown to display information about the active brush.
The cursor is shown as a circle in the 3D Viewport, the radius of the circle matches the size of the brush.

The cursor can be disabled by toggling the checkbox in the panel's header.

.. _bpy.types.Brush.cursor_color_add:

Cursor Color
   Set the color of the brush ring while performing an add/positive stroke.

.. _bpy.types.Brush.cursor_color_subtract:

Inverse Color
   In some paint/sculpt modes the brush can be negative and subtract information from the paint target;
   these brushes can be given a separate color.

.. _bpy.types.Brush.cursor_overlay_alpha:
.. _bpy.types.Brush.use_cursor_overlay:
.. _bpy.types.Brush.texture_overlay_alpha:
.. _bpy.types.Brush.use_primary_overlay:

Opacity Options
   Depending on the paint or sculpt mode different overlays are shown within the cursor
   to give information on how the brush is textured.
   This is most commonly used to show the brush falloff with a gradient from the circle center to the perimeter.

   Alpha
      You can change the amount of transparency used
      when showing the texture using the slider.
   Override Overlay (brush icon)
      Allows you to turn off the viewport overlay during strokes.
   View (eye icon)
      Toggles whether to show or hide the given brush texture overlay.


## Falloff


*******
Falloff
*******

The Falloff allows you to control the *Strength* falloff of the brush.
The falloff is mapped from the center of the brush (left part of the curve)
towards its borders (right part of the curve).
Changing the shape of the curve will make the brush softer or harder.
Read more about using the :ref:`ui-curve-widget`.

.. figure:: /images/sculpt-paint_brush_falloff_brush-curve.png

   Brush curve example.

.. _bpy.ops.brush.curve_preset:
.. _bpy.types.Brush.curve:

Curve Preset
   :Custom:
      You can choose how the strength of the falloff is determined from the center of the brush
      to the borders by manually manipulating the control points within the curve widget.
      There are also a couple of preset custom curves displayed at the bottom of the curve widget
      that can be used on their own or as a starting point for tweaking.

      .. list-table:: Custom Preset types.

         * - .. figure:: /images/sculpt-paint_brush_falloff_custom-smooth.png

                Smooth.

           - .. figure:: /images/sculpt-paint_brush_falloff_custom-sphere.png

                Sphere.

           - .. figure:: /images/sculpt-paint_brush_falloff_custom-root.png

                Root.

         * - .. figure:: /images/sculpt-paint_brush_falloff_custom-sharp.png

                Sharp.

           - .. figure:: /images/sculpt-paint_brush_falloff_custom-linear.png

                Linear.

           - .. figure:: /images/sculpt-paint_brush_falloff_custom-constant.png

                Constant.

   :Smooth:
      The center strength, the border strength, and the falloff transition between them are evenly distributed.
   :Smoother:
      Similar to *Smooth* but produces a wider center point of the brush before tapering off.
   :Sphere:
      The strength of the brush is predominately at its strongest point
      with a steep falloff near the border of the brush.
   :Root:
      Similar to a Sphere but the center is a more concentrated point.
   :Sharp:
      The center of the brush is the strongest point
      then exponentially tapers off to a lower strength, creating a fine point.
   :Linear:
      With the center being the strongest,
      the strength will consistently weaken as it reaches the border of the brush.
   :Sharper:
      Similar to *Sharp* but the center point is more condensed.
   :Inverse Square:
      A hybrid between *Smooth* and *Sphere*.
   :Constant:
      The strength of the brush remains unified across the entire brush.
      This will create a sharp edge at the border of the brush.

   .. figure:: /images/sculpt-paint_brush_falloff_demo.png

      (From Left to Right) Smooth, Smoother, Sphere, Root,
      Sharp, Linear, Sharper, Inverse square, Constant.

.. _bpy.types.Brush.falloff_shape:

Falloff Shape
   Use projected or spherical falloff.
   Note, this is not supported in Texture Paint Mode.

   :Sphere:
      Applies brushes influence in a sphere, outwards from the center.
   :Projected:
      This turns the brush influence into a cylinder (the depth along the view is ignored) instead of a sphere.
      It can be used along the outline of a mesh to adjust its silhouette.


Front-Face Falloff
==================

As faces point away from the view the brush strokes fade away to prevent harsh edges.

.. _bpy.types.ImagePaint.use_normal_falloff:
.. _bpy.types.Brush.use_frontface_falloff:

Normal Falloff / Front-Face Falloff
   If disabled, the normal of the surface has no effect on the falloff.

.. _bpy.types.ImagePaint.normal_angle:

Angle
   The angle at which the falloff begins.


## Index


#########
  Brush
#########

.. toctree::
   :maxdepth: 2

   introduction.rst


Brush Settings
==============

.. toctree::
   :maxdepth: 1

   brush.rst
   brush_settings.rst
   texture.rst
   stroke.rst
   falloff.rst
   cursor.rst


## Introduction


************
Introduction
************

.. figure:: /images/sculpt-paint_brush_introduction_brush-circle.png
   :align: center

   Brush cursor.

The brush is the main way of interacting with any painting and sculpting mode.
While click & dragging in the 3D Viewport it will create a :doc:`stroke </sculpt_paint/brush/stroke>`
and apply an effect depending on various brush settings.

.. tip::

   It is highly recommended to use a :ref:`Graphics Tablet <hardware-tablet>`
   for a better brush feel and additional features.


Brush Control
=============

These are the most common hotkeys for controlling the brush.

- Set brush size :kbd:`F`
- Set brush strength :kbd:`Shift-F`
- Rotate brush texture / Set brush weight :kbd:`Ctrl-F`

After pressing these hotkeys, you can then either adjust the value interactively or by typing in numbers.
Move the mouse right or left to increase/reduce the value
(additionally with precision (:kbd:`Shift`) and/or snapping (:kbd:`Ctrl`) activated).
Finally confirm (:kbd:`LMB`, :kbd:`Return`) or cancel (:kbd:`RMB`, :kbd:`Esc`).

You can also invert the brush direction/effect by holding :kbd:`Ctrl`.


## Stroke

******
Stroke
******

The stroke settings define the behavior of the sculpted/painted stroke.
Any other brush behavior and effect is applied on top of the stroke.

.. figure:: /images/sculpt-paint_brush_stroke_stroke-panel.png

   Stroke panel.

.. _bpy.types.Brush.stroke_method:

Stroke Method :kbd:`Alt-E`
   Defines the way brush strokes are applied to the canvas.

   .. container:: lead

      .. clear

   :Dots:
      Apply paint on each mouse move step. This is regardless of their distance to each other,
      and instead depends on the stroke speed.
      This means that a slower stroke will have more accumulative strength applied.
   :Drag Dot:
      Leaves only one dab on the canvas which can be placed by dragging.
   :Space:
      Creates brush stroke as a series of dots,
      whose distance (spacing) is determined by the *Spacing* setting.

      .. _bpy.types.Brush.spacing:
      .. _bpy.types.Brush.use_pressure_spacing:

      Spacing
         Limits brush application to the distance specified by the percentage of the brush radius.

   :Airbrush:
      Flow of the brush continues as long as the mouse click is held (spray),
      determined by the *Rate* setting.

      .. _bpy.types.Brush.rate:

      Rate
         Interval for how frequent the brush is applied during the stroke.
   :Anchored:
      Creates a single dab at the brush location.
      Clicking and dragging will resize the dab diameter.

      .. _bpy.types.Brush.use_edge_to_edge:

      Edge to Edge
         The brush location and orientation are determined by a two point circle,
         where the first click is one point, and dragging places the second point, opposite from the first.
   :Line:
      Clicking and dragging lets you define a line in screen space.
      The line dabs are separated by *Spacing*, similar to space strokes.
      With :kbd:`Alt` the line stroke is constrained to 45 degree increments.
   :Curve:
      Defines the stroke curve with a Bézier curve (dabs are separated according to *Spacing*).
      This Bézier curve is stored in Blender as a "Paint Curve" data-block.

      Use :kbd:`Ctrl-RMB` to create the initial control point of the curve.

      Paint Curves
         Paint Curves are reusable and can be stored and selected by using the :ref:`ui-data-block` menu.

         .. _bpy.ops.paintcurve.new:

      - **Add Points**
         You can define additional curve control points by using :kbd:`Ctrl-RMB`.
         The handles can be defined by dragging the mouse.
         The stroke flows in the direction of the first control point to the second control point, and so on.
      - **Transforming Points**
         The control points and handles can be dragged with :kbd:`RMB` (In right click select with :kbd:`LMB`).
         To make sure that the handles of a control point are symmetrical,
         drag them using :kbd:`Shift-RMB`.
         A few transform operators are supported such as moving
         (:kbd:`G`), rotating (:kbd:`R`) and scaling (:kbd:`S`).

         .. _bpy.ops.paintcurve.select:

      - **Selection**
         The handles can be selected individually by using :kbd:`LMB` (In right click select with :kbd:`RMB`),
         extend the selection by :kbd:`Shift-LMB` and deselect/select all by using :kbd:`A`.

         .. _bpy.ops.paintcurve.delete_point:

      - **Delete Points :kbd:`X`**
         To delete a curve point, use :kbd:`X`.

      .. _bpy.ops.paintcurve.draw:

      Draw Curve :kbd:`Return`
         To confirm and execute the curved stroke,
         press :kbd:`Return` or use the Draw Curve button.

.. _bpy.types.Brush.use_scene_spacing:

Spacing Distance :guilabel:`Sculpt Mode Only`
   Method used to calculate the distance to generate a new brush step.

   :View:
      Calculates the brush spacing relative to the view.
   :Scene:
      Calculates the brush spacing relative to all three dimensions of the scene using the stroke location.
      This avoids artifacts when sculpting across curved surfaces and keeps the spacing much more consistent.

.. _bpy.types.Brush.use_space_attenuation:

Adjust Strength for Spacing
   Keep the brush strength consistent, even if the spacing changes.
   Available for the *Space*, *Line*, and *Curve* stroke methods.

.. _bpy.types.Brush.dash_ratio:

Dash Ratio
   Ratio of samples in a cycle that the brush is enabled.
   This is useful to create dashed lines in texture paint or stitches in Sculpt Mode.
   Available for the *Space*, *Line*, and *Curve* stroke methods.

.. _bpy.types.Brush.dash_samples:

Dash Length
   Length of a dash cycle measured in stroke samples.
   This is useful to create dashed lines in texture paint or stitches in Sculpt Mode.
   Available for the *Space*, *Line*, and *Curve* stroke methods.

.. _bpy.types.Brush.jitter:

Jitter
   Jitter the position of each step in the brush stroke.

   .. _bpy.types.Brush.use_pressure_jitter:

   Jitter Pressure
      Brush *Jitter* can be affected by enabling the pressure sensitivity icon,
      if you are using a :ref:`Graphics Tablet <hardware-tablet>`.

.. _bpy.types.Brush.jitter_unit:

Jitter Unit
   Controls how the brush *Jitter* is measured.

   :View:
      The *Jitter* is relative to the view direction i.e. "screen space".
   :Scene:
      The *Jitter* is measured relative to all three dimensions of the scene.
      The unit type and scaling can be configured in the :ref:`Scene Units <bpy.types.UnitSettings>`.

.. _bpy.types.Paint.input_samples:

Input Samples
   Recent mouse locations (input samples) are averaged together to smooth brush strokes.

   .. _bpy.types.UnifiedPaintSettings.use_unified_input_samples:

   Use Unified Input Samples
      Use the same brush *Input Samples* across all brushes.


.. _bpy.types.Brush.use_smooth_stroke:

Stabilize Stroke
================

*Stabilize Stroke* makes the stroke lag behind the cursor
and creates a smoothed curve to the path of the cursor.
This can be enabled pressing :kbd:`Shift S` or by clicking the checkbox found in the header.

.. _bpy.types.Brush.smooth_stroke_radius:

Radius
   Minimum distance from the last point before the stroke continues.

.. _bpy.types.Brush.smooth_stroke_factor:

Factor
   A smooth factor, where higher values result in smoother strokes but the drawing sensation
   feels like as if you were pulling the stroke.


## Texture

.. _bpy.types.BrushTextureSlot:

**********************
Texture & Texture Mask
**********************

This page covers both the Texture and Texture Mask panels.
Add a Texture to the brush to control the color of the brush.
A Texture Mask is used to control the strength of the brush.
Both the Texture and Texture Mask offer the same settings.

.. figure:: /images/sculpt-paint_brush_texture_ui-example.jpg
   :width: 580px

   Example of the Texture panel and a textured brush in use.

Texture
   In paint modes the texture is used as a color source,
   while for sculpting it is used to determine the strength of the brush.

   Any image texture or procedural texture can be assigned in the texture and texture mask panels.
   Textures can be further edited in the properties editor (Click the properties icon for quick access)

.. tip::

   It's recommended to load all needed images ahead of time as image textures into Blender.
   Then they can be easily selected by clicking on the texture and picking it from the data-block popup.
   Textures can also be appended/linked from other Blender files.

.. _bpy.types.BrushTextureSlot.map_mode:
.. _bpy.types.BrushTextureSlot.mask_map_mode:

Mapping & Mask Mapping
   How the texture is applied to the brush stroke.

   .. tip::

      It is recommended to set this to *Area Plane* or *View Plane* for the most common behavior.
      Ideally match this setting with the
      :ref:`Sculpt Plane <bpy.types.Brush.sculpt_plane>` setting if in sculpt mode.

   :View Plane:
      If *View Plane* is enabled, the current viewing angle is used to project the brush texture onto the model.
      This is especially useful for projection painting.

   :Area Plane:
      Projects the brush texture along the local surface :term:`normal`,
      which keeps the texture from stretching on steep angles.
      This is an ideal default for most brushes.

   :Tiled:
      The *Tile* option repeats the texture across the screen,
      so moving the brush will not change where the texture is applied.
      The *Tile* option is most useful with tileable images, rather than procedural textures.

   :3D:
      The *3D* option allows the brush to take full advantage of procedural textures.
      This mode uses vertex coordinates rather than the brush location to determine what area of the texture to use.

      This option is not available for the Texture Mask.

   :Random:
      Picks a random texture coordinate to sample from for each step of the stroke.
   :Stencil:
      This is the ideal option for stamping textures for projection painting.
      Stencil mapping works by projecting the texture from the camera space on the mesh or canvas.
      Painting is applied only inside the boundaries of the stencil.
      The stencil is displayed as a screen space overlay on the viewport.
      To transform the stencil texture use the following shortcuts (Hold :kbd:`Alt` for the Texture Mask):

      - Move :kbd:`RMB`
      - Scale :kbd:`Shift-RMB`
      - Rotate :kbd:`Ctrl-RMB`

      While using stencil scaling, :kbd:`X` and :kbd:`Y` are used to constrain the scaling to one axis.
      Pressing one of the buttons twice reverts to unconstrained scaling.

      .. _bpy.ops.brush.stencil_fit_image_aspect:

      Image Aspect
         Restore the aspect ratio of the original image to reset stretching introduce by scaling,
         (Image textures only.) This operator can use the tiling and scale values of the brush texture
         if the relevant are enabled in :ref:`bpy.ops.screen.redo_last` panel.

      .. _bpy.ops.brush.stencil_reset_transform:

      Reset Transform
         Restores the position of the stencil.

.. _bpy.types.Brush.use_pressure_masking:

Pressure Masking
   Only available for the Texture Mask. It allows to clip the mask result based on pressure.

   :Off: Disabled.
   :Ramp: Fades out the mask effect on higher pressure.
   :Cutoff: Expands the used values from the image based on stylus pressure.

.. _bpy.types.BrushTextureSlot.angle:

Angle :kbd:`Ctrl-F`
   This is the rotation angle of the texture brush.
   It can be changed interactively via :kbd:`Ctrl-F` in the 3D Viewport.
   While rotating the angle via the hotkey you can enter a value numerically as well.

.. _bpy.types.BrushTextureSlot.use_rake:

Rake
   Texture angle follows the direction of the brush stroke.
   Useful for stamping textures repeatedly along the stroke.
   Not available with *3D*, *Tiled*, or *Stencil* Mapping types.
   The shortcut is not available in Sculpt mode.

.. _bpy.types.BrushTextureSlot.use_random:

Random
   Angle is randomized on each step of the stroke.
   Not available with *3D*, *Tiled*, or *Stencil* Mapping types.
   The shortcut is not available in Sculpt mode.

   .. _bpy.types.BrushTextureSlot.random_angle:

   Random Angle
      Constraints the random deviation to a range.

.. _bpy.types.TextureSlot.offset:

Offset X, Y, Z
   Offset the texture map placement in X, Y, and Z axes.

.. _bpy.types.TextureSlot.scale:

Size X, Y, Z
   Set the scale of the texture in each axis.

.. _bpy.types.Brush.texture_sample_bias:

Sample Bias :guilabel:`Sculpt Mode`
   Value added to texture samples.
   This can be used if the mid-level of a height map is not correct.

.. _bpy.types.Brush.use_color_as_displacement:

Vector Displacement :guilabel:`Sculpt Mode`
   Use the color channels to displace geometry in 3 vectors.

   .. note::

      This is only supported for the :doc:`Draw </sculpt_paint/sculpting/tools/draw>` brush
      with :ref:`Area Plane <bpy.types.BrushTextureSlot.map_mode>` mapping enabled.


## Index

.. _bpy.types.BrushCurvesSculptSettings:
.. _bpy.ops.sculpt_curves:

####################
  Curves Sculpting
####################

.. toctree::
   :maxdepth: 2

   introduction.rst
   tools/index.rst
   tools_settings.rst


## Introduction


************
Introduction
************

*Curves Sculpt Mode* allows working with curves using various brushes.
It is commonly used for hair grooming, but can be used with all kinds of curves.

The curves' surface object plays an important role in many curves sculpting brushes.
Most brushes such as :doc:`Add Curves </sculpt_paint/curves_sculpting/tools/add_curves>`
require the surface to be set already.

.. note::

    Curves Sculpt tools only use the original mesh of the surface object and don't take its modifiers into account.


Curves Menu
===========

.. _bpy.ops.curves.snap_curves_to_surface:

Snap to Deformed Surface
   Re-attach curves to a deformed surface using the existing attachment information.
   This only works when the topology of the surface mesh has not changed.

Snap to Nearest Surface
   Find the closest point on the surface for the root point of every curve and move the root there.
   This needs to be run after the surface mesh topology changed

.. _bpy.ops.curves.convert_to_particle_system:

Convert to Particle System
   Add a new hair particle system, or update an system on the surface object.
   The operator is used for backwards compatibility with the old
   :doc:`hair type particle system </physics/particles/hair/introduction>`.


Selection Modes
===============

.. reference::

   :Mode:      Sculpt Mode
   :Menu:      :menuselection:`3D Viewport Header --> Select Mode`
   :Shortcut:  :kbd:`1`, :kbd:`2`

Selection modes limits selection operators to certain curve domains.
This feature is makes it easy to select whole segments at once, or to give more granular control over editing.

:Control Points:
   Allows selection of individual control points.
:Curve:
   Limits selection to whole curve segments.


Select Menu
===========

All
   Select all control points or curves.

None
   Deselect all control points or curves.

Invert
   Invert the selection.

.. _bpy.ops.sculpt_curves.select_random:

Random
   Randomizes inside the existing selection or create new random selection if nothing is selected already.

.. _bpy.ops.sculpt_curves.select_ends:

Endpoints
   Select endpoints of curves.
   Only supported in the Control Point selection mode.

   Amount Start, End
      Number of points to select from the front or back of the curve.

.. _bpy.ops.sculpt_curves.select_grow:

Grow
   Select points or curves which are close to already selected elements.


Controls
========

Sculpt mode provides several properties that give advanced control of the tool's behavior.
These options can be found in the right-hand side of the 3D Viewport's Header.

.. _bpy.types.Curves.use_mirror_z:

Mirror
   Allows tools to affect curves symmetrically according to the chosen axis.

.. _bpy.types.Curves.use_sculpt_collision:

Use Sculpt Collision
   Prevents the curve segments from passing through the :ref:`Surface Object <bpy.types.Curves.surface>`.


Display
=======

Overlays
--------

.. _bpy.types.View3DOverlay.show_sculpt_curves_cage:
.. _bpy.types.View3DOverlay.sculpt_curves_cage_opacity:

Cage Opacity
   Shows the original curves that are currently being edited
   which is useful with when procedural deformations or child curves are used.


## Tools Settings


***************
Common Settings
***************

Information on brush settings for every mode can be found in these pages:

Brush
=====

See general and advanced :doc:`Brush </sculpt_paint/brush/brush_settings>` here.

Stroke
======

See the global brush settings for :doc:`Stroke </sculpt_paint/brush/stroke>` settings.


Falloff
=======

See the global brush settings for :doc:`Falloff </sculpt_paint/brush/falloff>` settings.


Cursor
======

See the global brush settings for :doc:`Cursor </sculpt_paint/brush/cursor>` settings.


## Add Curves


**********
Add Curves
**********

Used to distribute new curves on the surface mesh.
This tool requires the curve to have a :doc:`surface </sculpt_paint/curves_sculpting/introduction>` object set.

The curves follow the surface normals. Using the interpolation options allows the brush to take the characteristics
of existing curves.


Brush Settings
==============

.. _bpy.types.BrushCurvesSculptSettings.add_amount:

Count
   Number of curves added.

.. note::

   Interpolation allows to add hair which are already combed. The new curves are created
   following the previously created curves which are in the vicinity.

.. _bpy.types.BrushCurvesSculptSettings.interpolate_length:

Interpolate Length
   Use the average length of the curves in close proximity.

.. _bpy.types.BrushCurvesSculptSettings.interpolate_radius:

Interpolate Radius
   Use the average radius of the curves in close proximity.
   If there is no radius attribute, then the interpolation will skip.

.. _bpy.types.BrushCurvesSculptSettings.interpolate_shape:

Interpolate Shape
   Use the average shape of the curves in close proximity.

.. _bpy.types.BrushCurvesSculptSettings.interpolate_point_count:

Interpolate Point Count
   Use the average amount of control points of the curves in close proximity.

.. _bpy.types.BrushCurvesSculptSettings.curve_length:

Curve Length
   Length of newly added curves when not interpolated.

.. _bpy.types.BrushCurvesSculptSettings.curve_radius:

Curve Radius
   Radius of newly added curves when not interpolated.

.. _bpy.types.BrushCurvesSculptSettings.points_per_curve:

Points per Curve
  Number of Control Points for the new created curves when the point count is not interpolated.


## Comb Curves


***********
Comb Curves
***********

Shape the curves by moving their control points while preserving the initial length of every curve segment.


Brush Settings
==============

.. _bpy.ops.brush.sculpt_curves_falloff_preset:

Curve Falloff
   Falloff that is applied from the tip to the root of each curve.


## Delete Curves


*************
Delete Curves
*************

Remove existing curves. The tool deletes the entire curves,
if any of its segments fall under the brush falloff radius.


## Density Curves


*************
Density Brush
*************

Create (or remove) curves based on a target distance.
It generates a high number of points and then rejects the
ones that are too close to existing points.


Brush Settings
==============

.. _bpy.types.BrushCurvesSculptSettings.density_mode:

Density Mode
   Determines whether the brush adds or removes curves.

   :Auto:
      Either add or remove curves depending on the distance between existing curve roots under the cursor.
   :Add:
      Add new curves between existing curves, taking the minimum distance into account.
   :Remove:
      Remove curves whose root points are too close.

.. _bpy.types.BrushCurvesSculptSettings.minimum_distance:

Distance Min
   Goal distance between the curve roots.

   .. _bpy.ops.sculpt_curves.min_distance_edit:

   Edit Minimum Distance :kbd:`R`
      Interactively sets the *Distance Min* value by displaying
      a graphic inside the brush cursor, giving a representation of the density.

      The density can be adjusted by moving the mouse cursor closer or farther from the paint cursor.
      The *Distance Min* will be changed once the operator is confirmed.

.. _bpy.types.BrushCurvesSculptSettings.density_add_attempts:

Count Max
   The maximum amount of points that the brush tries to sample in the surface.


## Grow Shrink Curves


********************
Grow / Shrink Curves
********************

Change the length of existing curves preserving the amount of control points
and resampling the curve to preserve the original shape.


Brush Settings
==============

Direction
   Determines whether to grow or shrink the curves. It can be toggled holding :kbd:`Ctrl` while sculpting.

.. _bpy.types.BrushCurvesSculptSettings.scale_uniform:

Scale Uniform
   Grow or shrink curves by changing their size uniformly instead of using trimming or extrapolation.

.. _bpy.types.BrushCurvesSculptSettings.minimum_length:

Minimum Length
   Avoid shrinking curves shorter than this length.


## Index


#########
  Tools
#########

.. toctree::
   :maxdepth: 1

   selection_paint.rst
   add_curves.rst
   delete_curves.rst
   density_curves.rst
   comb_curves.rst
   snake_hook_curves.rst
   grow_shrink_curves.rst
   pinch_curves.rst
   puff_curves.rst
   smooth_curves.rst
   slide_curves.rst


## Pinch Curves


************
Pinch Curves
************

Converges adjacent curves to the location at the center of the cursor.

The pinch brush can be inverted by holding :kbd:`Ctrl`.


## Puff Curves


***********
Puff Curves
***********

Makes the curves stand up. The brush aligns the curve with the surface normal
and makes sure that points don't move closer to the root point.


## Selection Paint


***************
Selection Paint
***************

Paint curves or control paints to use as masks for the other tools.
The selection visibility can be controlled by the *Selection Opacity* option in the Viewport Overlays.

By default the selection sets a new selection. The selection paint can be extended
by holding :kbd:`Shift` and it can be subtracted by holding :kbd:`Ctrl` while painting.


Brush Settings
==============

Direction
   Determines whether to set a new selection or remove from it. It can be toggled holding :kbd:`Ctrl` while painting.


## Slide Curves


************
Slide Curves
************

Slides the curves along the surface mesh. This tool requires the curve to have a
:doc:`Surface </sculpt_paint/curves_sculpting/introduction>`.
Each curve is also rotated by the change in the surface normal.


## Smooth Curves


*************
Smooth Curves
*************

This brush makes curve segments close to one another more parallel.


## Snake Hook Curves


*****************
Snake Hook Curves
*****************

Extend existing curves in a specific direction of the brush strokes.
A curve can only be extended by its tips (the control point opposite to the root).

.. note::

   No new control points are created for the curves. Instead, existing points are sampled
   along the new curve shape.


## Controls


********
Controls
********

Auto-Masking
============

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Header --> Auto-Masking`
   :Shortcut:     :kbd:`Alt-A`

These properties automatically mask geometry based on geometric features of the mesh.
It's an quick alternative to frequent manual masking.
These masks are initialized on every new stroke or tool usage. They are also never visible as an overlay.

Note, these properties are applied across all sculpt brushes, however, they can also be configured
per brush in the :ref:`Advanced Brush Settings <sculpt-tool-settings-brush-settings-advanced>`.

These properties can be accessed via a :ref:`bpy.types.UIPieMenu` by pressing :kbd:`Alt-A`.

All auto-masking modes can be combined, which makes the generated auto-mask more specific.
For example it's possible to auto-mask a specific face set,
while excluding disconnected topology and face set boundaries,
and only affect faces that are oriented towards the view via View Normal.

.. _bpy.types.Sculpt.use_automasking_topology:

Topology
   Only vertices that are topologically connected to where you started
   the stroke/tool on are affected. So loose geometry islands will be auto-masked.

   Additionally for the :doc:`Grab </sculpt_paint/sculpting/tools/grab>` and
   :doc:`Thumb </sculpt_paint/sculpting/tools/thumb>` brushes, anything that
   is not connected within the brush radius will be auto-masked.
   So even if geometry is connected somewhere,
   it is considered separate if the connection is not within the radius.

.. _bpy.types.Sculpt.use_automasking_face_sets:

Face Sets
   Only vertices that are part of the same face set that you started the stroke/tool on are affected.

.. tip::

   If no topology or face set is visible under the cursor at the start of the stroke,
   the previously auto-masked area will be targeted.
   This is especially useful with the "Projected" falloff shape in the
   :doc:`Falloff Settings </sculpt_paint/brush/falloff>`.

.. _bpy.types.Sculpt.use_automasking_boundary_edges:

Mesh Boundary
   Vertices that are part of open boundary edges are not affected.
   This also includes boundary edges to hidden faces.

   Propagation Steps
      Increases the soft gradient towards the auto-masked boundary edges.
      Each step iterates the distance one edge further.
      This setting is used for both Mesh Boundary and Face Sets Boundary.

.. _bpy.types.Sculpt.use_automasking_boundary_face_sets:

Face Sets Boundary
   Vertices that are part of a boundary between face sets are not affected.
   This also includes boundary edges to hidden faces.
   Propagation Steps are shared with Mesh Boundary auto-masking.

.. _bpy.types.Sculpt.use_automasking_cavity:

Cavity
   Vertices that are the peaks of the surface curvature are not affected.
   While this auto-mask is primarily meant for painting,
   it can also be used for regular sculpting.

   Factor
      The overall contrast of how strong the cavity is applied. The value of 0.5 is the default,
      but better results can also be achieved on 0.2 if a Custom Curve is used as well.

   Blur
      The number of times the cavity mask is blurred. A value of 0 will give the pure cavity auto-mask.
      Anything higher than 6 will likely have a less visible effect and decrease performance.
      Even though the value is capped to 10, it can be increased up to 25 if typing in the value.

   Custom Curve
      Use a custom curve to fine tweak the cavity auto-mask.
      This is very useful if only small crevices or flat surfaces should be affected.
      Or for example if the contrast should be increased/decreased in a specific way.
   Create Mask
      This will execute the :ref:`bpy.ops.sculpt.dirty_mask` operator with the current auto-masking settings.
      This is very useful to visualize the current auto-mask, or to edit the mask further manually.

.. _bpy.types.Sculpt.use_automasking_cavity_inverted:

Cavity (Inverted)
   This is the same as "Cavity", but inverted.
   This means the valleys/crevices of the surface curvature will not be affected.
   It cannot be used at the same time as Cavity and shares all of its settings.
   Enable this to quickly invert the cavity auto-mask.

.. _bpy.types.Sculpt.use_automasking_view_normal:

View Normal
   Only vertices with a :term:`Normal` that face the viewer are affected.
   This is similar to the "Front Faces Only" toggle in the
   :doc:`Brush Setting </sculpt_paint/sculpting/tool_settings/brush_settings>`, to only affect visible geometry.
   The advantage of this auto-mask is that it has more options and works on sculpt mode as a whole.

   Occlusion
      Change the View Normal behavior to only affect vertices that are not occluded by other faces.
      This setting is incompatible with the other Limit and Falloff sliders.
      It also causes a much slower performance.

   Limit
      Determines the range of angles that will be affected. 90 degrees encompasses all that is visible.

   Falloff
      Extends the angular range of the Limit slider with a soft falloff gradient.
      This falloff will visually extend the limit range further.

.. _bpy.types.Sculpt.automasking_start_normal_falloff:
.. _bpy.types.Sculpt.automasking_start_normal_limit:
.. _bpy.types.Sculpt.use_automasking_start_normal:

Area Normal
   Very similar to the View Normal, but uses the Normal of the surface that you started the stroke/tool on.
   This way any direction can be chosen for what vertices will be affected.
   It has the same Limit and Falloff sliders as the View Normal auto-mask.


## Index

.. _painting-sculpting-index:
.. _bpy.types.Sculpt:
.. _bpy.ops.sculpt:

#############
  Sculpting
#############

.. toctree::
   :maxdepth: 2

   introduction/index.rst
   toolbar.rst
   tools/index.rst
   tool_settings/index.rst
   controls.rst
   editing/index.rst


## Toolbar


*******
Toolbar
*******

The amount of tools in sculpt mode is very extensive.
This is an overview of all of them, categorized by their general functions.


Add/Subtract Brushes
====================

.. figure:: /images/sculpt-paint_sculpting_toolbar_add_subt_brushes.png
   :align: right

Recognizable by their blue icon and cursor.
These brushes generally push vertices outwards and inwards.

:doc:`/sculpt_paint/sculpting/tools/draw`
   The standard brush for pushing vertices inwards and outwards from the surface direction.

:doc:`/sculpt_paint/sculpting/tools/draw_sharp`
   Same as *Draw* but with a much sharper :doc:`Falloff </sculpt_paint/brush/falloff>`.
   Useful for creating creases and sharp angles.

:doc:`/sculpt_paint/sculpting/tools/clay`
   Similar to the *Draw* brush but with a flattening effect and subtle smoothing.
   Useful for polishing and building volumes.

:doc:`/sculpt_paint/sculpting/tools/clay_strips`
   The same as the *Clay* brush, but more aggressive with a square falloff.
   A common standard for building rough volumes.

:doc:`/sculpt_paint/sculpting/tools/layer`
   Draw with a fixed height. Useful for adding flat layers to a surface.

:doc:`/sculpt_paint/sculpting/tools/inflate`
   Moves the mesh in multiple direction. Useful for inflating or shrinking surfaces and volumes.

:doc:`/sculpt_paint/sculpting/tools/blob`
   Magnifies the mesh as you draw. Useful for an additional inflation effect on the stroke.

:doc:`/sculpt_paint/sculpting/tools/crease`
   Same as *Blob* but with a pinching effect. Useful for creating and polishing sharp creases.

Contrast Brushes
================

.. figure:: /images/sculpt-paint_sculpting_toolbar_contrast_brushes.png
   :align: right

Recognizable by their red icon and cursor.
These brushes generally flatten or heighten the contrast of the surface.

:doc:`/sculpt_paint/sculpting/tools/smooth`
   Smooths out irregularities in the surface and shrinks volumes by averaging the vertices positions.
   An essential brush that is frequently used.

:doc:`/sculpt_paint/sculpting/tools/flatten`
   Pushes vertices to an average height to create a flat plateau.

:doc:`/sculpt_paint/sculpting/tools/fill`
   Pushes surfaces outwards. Useful for filling in holes and crevices.

:doc:`/sculpt_paint/sculpting/tools/scrape`
   Pushes surfaces inwards. This is the most common brush for flattening meshes.

:doc:`/sculpt_paint/sculpting/tools/multiplane_scrape`
   Scrapes the mesh with two angled planes at the same time, producing a sharp edge between them.


Transform Brushes
=================

.. figure:: /images/sculpt-paint_sculpting_toolbar_transform_brushes.png
   :align: right

Recognizable by their yellow icon and cursor.
These brushes generally move, pinch and magnify the mesh.

:doc:`/sculpt_paint/sculpting/tools/pinch`
   Pulls vertices towards the center of the brush. Useful for polishing angles and creases.

:doc:`/sculpt_paint/sculpting/tools/grab`
   Moves vertices along with the mouse. An essential brush for building shapes and adjusting proportions.

:doc:`/sculpt_paint/sculpting/tools/elastic_deform`
   Used to simulate realistic deformations such as grabbing or twisting of :term:`Elastic` objects.

:doc:`/sculpt_paint/sculpting/tools/snake_hook`
   Pulls vertices along with the stroke to create long, snake-like forms.

:doc:`/sculpt_paint/sculpting/tools/thumb`
   Same as *Grab* but moves vertices along the surface direction. Useful for preserving specific surfaces.

:doc:`/sculpt_paint/sculpting/tools/pose`
   Simulating an armature-like deformations. Useful for quick posing and transformations.

:doc:`/sculpt_paint/sculpting/tools/nudge`
   Similar as *Thumb* but dynamically picks up vertices like the *Snake Hook*.
   Useful for nudging something along the mesh surface.

:doc:`/sculpt_paint/sculpting/tools/rotate`
   Rotates vertices within the brush in the direction mouse.

:doc:`/sculpt_paint/sculpting/tools/slide_relax`
   Slides the topology of the mesh in the direction of the stroke
   while preserving the geometrical shape of the mesh.
   Also useful for redistributing topology where it is needed.

:doc:`/sculpt_paint/sculpting/tools/boundary`
   Transform mesh boundaries specifically with various deformations.


General Brushes
===============

.. figure:: /images/sculpt-paint_sculpting_toolbar_general_brushes.png
   :align: right

No clear color assignment.
These brushes are general purpose brushes or specific.

:doc:`/sculpt_paint/sculpting/tools/cloth`
   Simulates cloth to create folds and draping, which can be sculpted further.

:doc:`/sculpt_paint/sculpting/tools/simplify`
   Cleans up geometry by collapsing short edges.

:doc:`/sculpt_paint/sculpting/tools/mask`
   Paints a selection on parts of the mesh to be unaffected by other brushes.

:doc:`/sculpt_paint/sculpting/tools/draw_facesets`
   Paint new or extend existing face sets.

:doc:`/sculpt_paint/sculpting/tools/multires_displacement_eraser`
   Remove displacement information on a Multiresolution modifier.

:doc:`/sculpt_paint/sculpting/tools/multires_displacement_smear`
   Smear displacement information on a Multiresolution modifier.


Painting Brushes
================

.. figure:: /images/sculpt-paint_sculpting_toolbar_paint.png
   :align: right

Recognizable by their green icon.
These brushes are used for painting color attributes within sculpt mode.

:doc:`/sculpt_paint/sculpting/tools/paint`
   Paint on the vertices of your mesh via color attributes.

:doc:`/sculpt_paint/sculpting/tools/smear`
   Smears the vertex colors via color attributes.


Gesture Tools
=============

.. figure:: /images/sculpt-paint_sculpting_toolbar_gestures.png
   :align: right

General gesture tools to apply an operation via box, lasso and line shapes.

:doc:`/sculpt_paint/sculpting/tools/box_mask`
   Create a mask via a box gesture.

:doc:`/sculpt_paint/sculpting/tools/lasso_mask`
   Create a mask via a lasso gesture.

:doc:`/sculpt_paint/sculpting/tools/line_mask`
   Create a mask via on one side of a drawn line.

Box Hide
   Hides/Shows geometry via a box gesture.

:doc:`/sculpt_paint/sculpting/tools/box_face_set`
   Create a face set via a box gesture.

:doc:`/sculpt_paint/sculpting/tools/lasso_face_set`
   Create a face set via a lasso gesture.

:doc:`/sculpt_paint/sculpting/tools/box_trim`
   Perform a Boolean operation via a box gesture.

:doc:`/sculpt_paint/sculpting/tools/lasso_trim`
   Perform a Boolean operation via a lasso gesture.

:doc:`/sculpt_paint/sculpting/tools/line_project`
   Flatten the geometry towards a drawn line.


Filter Tools
============

.. figure:: /images/sculpt-paint_sculpting_toolbar_filters.png
   :align: right

Tools for applying effects on the entire unmasked and visible mesh.

:doc:`/sculpt_paint/sculpting/tools/mesh_filter`
   Apply a deformation to all unmasked vertices.

:doc:`/sculpt_paint/sculpting/tools/cloth_filter`
   Applies a cloth simulation to all unmasked vertices.

:doc:`/sculpt_paint/sculpting/tools/color_filter`
   Changes the active color attribute on all unmasked vertices.


Single Click Tools
==================

.. figure:: /images/sculpt-paint_sculpting_toolbar_singleclick.png
   :align: right

Simpler tools that apply an operation on surfaces that are clicked on.

:doc:`/sculpt_paint/sculpting/tools/edit_face_set`
   Modifies the face set under the cursor.

:doc:`/sculpt_paint/sculpting/tools/mask_by_color`
   Create a mask from any color from the color attribute by clicking on it.


General Tools
=============

.. figure:: /images/sculpt-paint_sculpting_toolbar_general.png
   :align: right

General transform and annotate tools like in other modes.

:doc:`Move </sculpt_paint/sculpting/tools/transforms>`
   Translation tool.

:doc:`Rotate </sculpt_paint/sculpting/tools/transforms>`
   Rotation tool.

:doc:`Scale </sculpt_paint/sculpting/tools/transforms>`
   Scale tool.

:doc:`Transform </sculpt_paint/sculpting/tools/transforms>`
   Adjust the objects translation, rotations and scale.

:ref:`Annotate <tool-annotate-freehand>`
   Draw free-hand annotation.

   :ref:`Annotate Line <tool-annotate-line>`
      Draw straight line annotation.
   :ref:`Annotate Polygon <tool-annotate-polygon>`
      Draw a polygon annotation.
   :ref:`Annotate Eraser <tool-annotate-eraser>`
      Erase previous drawn annotations.


## Expand

.. _bpy.ops.sculpt.mask_expand:
.. _bpy.ops.sculpt.expand:

******
Expand
******

This is a multi-purpose modal operator to intuitively create and edit masks/face sets.
When executed, it uniformly expand outwards a pattern from the vertex under the cursor.

.. note::

   These operators are meant to be used interactively through the shortcut.

There is also a `full showcase of the Expand features and use cases <https://www.youtube.com/watch?v=XT7h6lmE5bc>`__.

.. figure:: /images/sculpt-paint_sculpting_expand_example.png

      A preview of *Expand Mask by Topology*


Expand Mask by Topology
=======================

.. reference::

   :Mode:      Sculpt Mode
   :Menu:      :menuselection:`Mask --> Expand Mask by Topology`
   :Shortcut:  :kbd:`Shift-A`

Expands a mask from the active vertex.

Usage
-----

Mask from A to B
   Start the operator and expand a mask from an origin to your mouse cursor distance.
   Then confirm with :kbd:`LMB` or :kbd:`Return`

   By default the expansion will use a *Geodesic* falloff :kbd:`1`
   to create perfectly accurate distances along the surfaces.
   Use other falloff types via :kbd:`2`, :kbd:`3` & :kbd:`4` to expand via
   triangles, whole faces or scene distances instead.

   .. figure:: /images/sculpt-paint_sculpting_expand_falloff_example.png

      The typical result when using the *Diagonals* falloff to expand along the quads of the face.

   Start Expand while pointing at an open boundary to expand from the entire boundary loop.
   This will always use the *Topology* falloff mode.

   .. needs visual practical example

Fill Connected Meshes
   Move your cursor outside of the boundaries of the mesh to mask the entire connected mesh.
   This can be done repeatedly to quickly mask separate meshes.

Fill Face Sets
   Hold :kbd:`Ctrl` to snap to face sets under your cursor and fill them.
   Any face set that was already covered in the expansion will be filled as well.

Automatically Set Transform Pivot
   While using any Transform tool, the pivot point
   will automatically snap the border of an Expand result.
   This way areas (Like limbs) can be masked and then immediately rotated or otherwise transformed.

   .. figure:: /images/sculpt-paint_sculpting_expand_auto_pivot.png

Pattern Creation
   The different falloff types can be used for circular, triangular and square patterns.
   More loops can also be added/removed via :kbd:`W` & :kbd:`Q` to repeat the pattern across the mesh.

   .. figure:: /images/sculpt-paint_sculpting_expand_pattern1.png

      An example of using expand with mirror options,
      loops and a recursion to create wood carving patterns.

   .. tip::

      :doc:`Mirror options </sculpt_paint/sculpting/tool_settings/symmetry>`
      can also be combined with the expansion.

   Linear gradients :kbd:`G` or brush falloff gradients :kbd:`B` will help to add slanted surfaces
   to the patterns.

   A "Recursions" with :kbd:`R` or :kbd:`Alt-R` will start
   a new expansion along the border of the current expansion.
   Doing this multiple times, can help for increasingly random patterns
   or advanced pattern creation.

   .. figure:: /images/sculpt-paint_sculpting_expand_pattern2.png

      An example of using loops and gradients with multiple expanded masks.

   .. tip::

      Remember that Expand only affects visible geometry.
      So if a pattern should only be created on a part of the mesh,
      :doc:`hide </sculpt_paint/sculpting/editing/sculpt>` the other geometry first.

   Use the :doc:`Mesh Filter </sculpt_paint/sculpting/tools/mesh_filter>`
   to deform the geometry and the :doc:`Color Filter </sculpt_paint/sculpting/tools/color_filter>`
   to add colors, to apply the patterns on the sculpt.


Expanding Textures
   Textures can be used to affect the shape and gradients of the expanded mask.
   This feature can be combined with loops and recursion to create unique results.

   .. needs visual example with Michel fur patterns

   To use a texture, you need to assign it to your currently active brush in the
   :doc:`Texture </sculpt_paint/brush/texture>` Brush Settings. The texture can be edited/created
   in the :doc:`Texture Properties </render/materials/legacy_textures/index>`.

   .. note::

      This texture only works when the :ref:`Mapping <bpy.types.BrushTextureSlot.map_mode>` is set to *3D*.

   Use :kbd:`Y` and :kbd:`T` to increase or decrease the affect the texture has on the edge of the mask.


Controls
--------

:Invert: :kbd:`F`
   Flips between expanding a positive mask (value of one) or a negative mask (value of zero).
   In the case of face sets, this option flips between including areas inside the masked area
   or areas outside the masked area.
   .. needs visual technical examples for both
:Toggle Preserve State: :kbd:`E`
   Accumulate the new mask on top of the previous one or replace it.
   For Face Sets, this will toggle between creating Face Sets boundaries
   or replacing the existing Face Sets.
:Move Origin: :kbd:`Spacebar`
   Moves the initial vertex used for calculating the falloff.
   .. needs visual technical example
:Geodesic Falloff: :kbd:`1`
   Uses a falloff based on the :term:`Geodesic` distances from the edge boundary to the active vertex.
:Topology Falloff: :kbd:`2`
   Uses a falloff based on a flood fill using edges.
:Diagonals Falloff: :kbd:`3`
   Uses a falloff based on a flood fill using polygon diagonals and edges.
:Spherical Falloff: :kbd:`4`
   Uses a falloff based on the Euclidean distances from the edge boundary to the active vertex.
   .. needs visual technical examples
:Toggle Gradient: :kbd:`G`
   Enables linear gradient of values from the origin to the current active vertex.
:Toggle Brush Gradient: :kbd:`B`
   Similar to linear gradient but uses the current brush :doc:`Falloff </sculpt_paint/brush/falloff>`
   to define the shape of the falloff.
   .. needs visual technical examples
:Geodesic Recursive Step: :kbd:`R`
   Start a new expansion with a :term:`Geodesic` falloff from the boundary of the current falloff.
:Topology Recursive Step: :kbd:`Alt-R`
   Start a new expansion with a topology falloff from the boundary of the current falloff.
   .. needs visual technical examples
:Snap Expanded to Face Sets: :kbd:`Ctrl`
   Isolates the expanded region to the boundary of the face set under the cursor.
:Loop Count Increase: :kbd:`W`
   Increase the number of loops or iterations the operator is run;
   using four loops will split the mask into four parts.
:Loop Count Decrease: :kbd:`Q`
   Decrease the number of loops or iterations the operator is run;
   using four loops will split the mask into four parts.
   .. needs visual technical examples
:Texture Distortion Increase: :kbd:`Y`
   Increases the falloff distance when using a texture to distort the mask shape.
:Texture Distortion Decrease: :kbd:`T`
   Decreases the falloff distance when using a texture to distort the mask shape.
   ..needs visual technical examples


Expand Mask by Normals
======================

.. reference::

   :Mode:      Sculpt Mode
   :Menu:      :menuselection:`Mask --> Expand Mask by Normals`
   :Shortcut:  :kbd:`Shift-Alt-A`

Expand a mask, following the curvature of the surface.
This operator uses the same internal operator as :ref:`bpy.ops.sculpt.expand`
meaning all the shortcuts and functionality works the same as that tool.

This operator is especially useful for hard surface sculpting.

.. tip::

    If one expansion does not properly fill the entire desired surface,
    use the operator repeatedly with a different starting point.

.. needs visual practical example

.. note::

   Using any of the Falloff shortcuts :kbd:`1-4`
   will replace the curvature falloff of this operator.


.. _face_set_expand:

Expand Face Set by Topology
===========================

.. reference::

   :Mode:      Sculpt Mode
   :Menu:      :menuselection:`Face Sets --> Expand Face Set by Topology`
   :Shortcut:  :kbd:`Shift-W`

Expands a face set from the active vertex.
This operator uses the same internal operator as :ref:`bpy.ops.sculpt.expand`
meaning all the hotkeys and functionality works the same as that tool,
with the gradient features as the exception.

Usage
-----

Saving Masks
   Expanding Face Sets has all the same use cases as expanding masks.
   The advantage for this one is that they will be saved for repeated usage.
   Face sets can be filled any time with a mask,
   so assigning areas face sets will save you time.
   (And of course face sets can be used to
   :doc:`hide face sets </sculpt_paint/sculpting/editing/sculpt>`)

Pivot Points for Pose Brush
   When using the :doc:`Pose Brush </sculpt_paint/sculpting/tools/pose>` it is most predictable when using it with
   Face Sets to define the face set boundaries as pivot point locations.
   Face Sets can be expanded from a point or from a boundary between hidden face sets
   to create them quickly.
   Alternatively :ref:`Grow/Shrink Face Sets <bpy.ops.sculpt.face_set_edit>`
   or use the :ref:`Expand Active Face Set <face_set_expand_active>` to dynamically grow/shrink them.

   .. Visual examples for pose brush on fingers, expanding face set from finger segment boundary
   .. and growing face set segment.

Cloth Sculpting
   Tools like the :doc:`Cloth Filter </sculpt_paint/sculpting/tools/cloth_filter>`
   and :doc:`Cloth Brush </sculpt_paint/sculpting/tools/cloth>`
   work especially well when only simulating small areas at a time.
   Face Sets can very easily be created with Expand to assign areas of action.

   .. needs visual examples with grids & a ribbon

.. _face_set_expand_active:

Expand Active Face Set
======================

.. reference::

   :Mode:      Sculpt Mode
   :Menu:      :menuselection:`Face Sets --> Expand Face Set by Topology`
   :Shortcut:  :kbd:`Shift-Alt-W`

Expands an existing face set with a geodesic falloff.
This operator uses the same internal operator as :ref:`bpy.ops.sculpt.expand`
meaning all the hotkeys and functionality works the same as that tool.

.. note::

   Using any of the Falloff shortcuts :kbd:`1-4`
   the operator to switch to :ref:`Expand Face Set by Topology <face_set_expand>`.

Usage
-----

Resizing Face Sets
   Resize a Face Set along the surface distances.
   It is an alternative to :ref:`Grow/Shrink Face Sets <bpy.ops.sculpt.face_set_edit>`
   which follows the topology instead of geodesic distances.

   .. needs visual examples side by side

Joining Face Sets
   When holding :kbd:`Ctrl` the expansion will instead snap to other Face Sets.
   This is a fast way of joining multiple face sets into one.

   .. needs visual examples side by side


## Face Sets

.. _sculpting-editing-facesets:

*********
Face Sets
*********

This page details the face set related hotkey operators and menu operators in sculpt mode.


.. tip::

   There is a face set pie menu that can be accessed with :kbd:`Alt-W`.


.. _bpy.ops.sculpt.face_sets_create:

Face Set from Masked
====================

.. reference::

   :Mode:      Sculpt Mode
   :Menu:      :menuselection:`Face Sets --> Face Set from Masked`

Creates a new face set from :ref:`Masked Geometry <sculpt-mask-menu>`.


Face Set from Visible
=====================

.. reference::

   :Mode:      Sculpt Mode
   :Menu:      :menuselection:`Face Sets --> Face Set from Visible`

Creates a new face set from all visible geometry.


Face Set from Edit Mode Selection
=================================

.. reference::

   :Mode:      Sculpt Mode
   :Menu:      :menuselection:`Face Sets --> Face Set from Edit Mode Selection`

Creates a new face set corresponding to the Edit Mode face selection.


.. _bpy.ops.sculpt.face_sets_init:

Initialize Face Sets
====================

.. reference::

   :Mode:      Sculpt Mode
   :Menu:      :menuselection:`Face Sets --> Initialize Face Sets`

Initializes all face sets on the mesh at once based off one of several mesh attribute properties.

Mode
   The mesh data attribute used to define the boundaries for the face sets.

   :By Loose Parts: Creates a new face set per discontinuous part of the mesh.
   :By Face Set Boundaries:
      Creates a face set for each isolated face set.
      This mode is useful for splitting the patterns created by :ref:`Face Set Expand <face_set_expand>`
      into individual Face Sets for further editing.
   :By Materials: Creates a face set per :ref:`Material Slot <bpy.types.MaterialSlot>`.
   :By Normals: Creates face sets for Faces that have similar :ref:`Normals <modeling-meshes-structure-normals>`.
   :By UV Seams: Creates face sets using :doc:`UV Seams </modeling/meshes/uv/unwrapping/seams>` as boundaries.
   :By Edge Creases: Creates face sets using :ref:`Edge Creases <bpy.ops.transform.edge_crease>` as boundaries.
   :By Edge Bevel Weight:
      Creates face sets using :ref:`Bevel Weights <bpy.ops.transform.edge_bevelweight>` as boundaries.
   :By Sharp Edges: Creates face sets using :ref:`Sharp Edges <bpy.ops.mesh.mark_sharp>` as boundaries.

Threshold
   The minimum value to consider a certain attribute a boundary when creating the face sets.


.. _bpy.ops.sculpt.face_set_edit:

Grow/Shrink Face Sets
=====================

.. reference::

   :Mode:      Sculpt Mode
   :Menu:      :menuselection:`Face Sets --> Grow/Shrink Face Sets`
   :Tool:      :doc:`/sculpt_paint/sculpting/tools/edit_face_set`
   :Shortcut:  :kbd:`Ctrl-W`, :kbd:`Ctrl-Alt-W`

Expands or contracts the face set under the cursor by adding or removing surrounding faces.


.. _bpy.ops.mesh.face_set_extract:


Expand Face Set
===============

.. note::

   More info on Face Set Expand at the :ref:`Expand page <bpy.ops.sculpt.expand>`.


Extract Face Set
================

.. reference::

   :Mode:      Sculpt Mode
   :Menu:      :menuselection:`Face Sets --> Extract Face Set`

Creates a new mesh based on the selected face set.
Once the operator is initiated, hover over the face set and :kbd:`LMB` to create the new mesh.
After the operator is finished the new mesh will be selected in Object Mode.


.. _bpy.ops.sculpt.face_sets_randomize_colors:

Randomize Colors
================

.. reference::

   :Mode:      Sculpt Mode
   :Menu:      :menuselection:`Face Sets --> Randomize Colors`

Generates a new set of random colors to render the face sets in the 3D Viewport.


.. _bpy.types.Sculpt.show_face_sets:
.. _bpy.types.View3DOverlay.sculpt_mode_face_sets_opacity:

Display Settings
================

.. reference::

   :Mode:      Sculpt Mode
   :Popover:   :menuselection:`Viewport Overlays -- Sculpt --> Face Sets`

The face sets display can be toggled as a :doc:`viewport overlay </editors/3dview/display/overlays>`.
In the overlay popover, the opacity of the face sets overlay can be adjusted
to make it more or less visible on the mesh.


## Index


###########
  Editing
###########

.. toctree::
   :maxdepth: 2

   sculpt.rst
   mask.rst
   face_sets.rst
   expand.rst


## Mask

.. _sculpt-mask-menu:
.. _bpy.ops.paint.mask:

****
Mask
****

This page details the mask related shortcut operators and menu operators in sculpt mode.
Other related information to masks can also be found at the bottom of the page.


.. reference::

   :Mode:      Sculpt Mode
   :Menu:      :menuselection:`Mask`
   :Shortcut:  :kbd:`A`

Masks can be edited across all visible faces.
Using :kbd:`A` opens a pie menu to choose the most common operations.

.. _mask_invert:

Invert Mask
===========

.. reference::

   :Mode:      Sculpt Mode
   :Menu:      :menuselection:`Mask --> Invert Mask`
   :Shortcut:  :kbd:`A`, :kbd:`Ctrl-I`

Inverts the visible mask.
This is often useful when the masked vertices are the surfaces you want to sculpt/paint.
In that case create a mask and then invert it.

.. _bpy.ops.paint.mask_flood_fill:

Fill Mask
=========

.. reference::

   :Mode:      Sculpt Mode
   :Menu:      :menuselection:`Mask --> Fill Mask`

Fully masks the visible geometry.
Alternatively it is common to clear and then invert a mask via :kbd:`A`
to achieve the same effect.

.. _mask_clear:

Clear Mask
==========

.. reference::

   :Mode:      Sculpt Mode
   :Menu:      :menuselection:`Mask --> Clear Mask`
   :Shortcut:  :kbd:`A`, :kbd:`Alt-M`

Removes the mask on all visible vertices.
To completely remove the mask data, see `Clear Sculpt-Mask Data`_.


.. _bpy.ops.paint.mask_box_gesture:

Box Mask
========

.. reference::

   :Mode:      Sculpt Mode
   :Menu:      :menuselection:`Mask --> Box Mask`
   :Shortcut:  :kbd:`B`

Works like the :doc:`Box Mask </sculpt_paint/sculpting/tools/box_mask>` tool,
it creates a rectangular mask region.
Hold :kbd:`Shift` or press :kbd:`MMB` to clear the mask of the selected region.


.. _bpy.ops.paint.mask_lasso_gesture:

Lasso Mask
==========

.. reference::

   :Mode:      Sculpt Mode
   :Menu:      :menuselection:`Mask --> Lasso Mask`
   :Shortcut:  :kbd:`Shift-Ctrl-LMB`

Can be used to create a free-form mask, similar to the
:doc:`Lasso Mask </sculpt_paint/sculpting/tools/box_mask>` tool.
This is very commonly used.

.. tip::

   To clear the mask of areas with the *Lasso Mask*, first invert the mask,
   use *Lasso Mask*, and then invert the mask back.


.. _bpy.ops.sculpt.mask_filter:

Mask Filters
============

.. reference::

   :Mode:      Sculpt Mode
   :Menu:      :menuselection:`Mask --> Smooth/Sharpen Mask, Grow/Shrink Mask, Increase/Decrease Contrast`
   :Shortcut:  :kbd:`A`

Similarly to other :doc:`Filter Tools </sculpt_paint/sculpting/introduction/filters>`,
mask filters are operations that are applied to the whole mask.

Type
   Smooth/Sharpen Mask
      Changes the sharpness of the mask edge.
      Using this can be faster and more consistent than smoothing the mask
      with the :doc:`Mask </sculpt_paint/sculpting/tools/mask>` brush.
   Grow/Shrink Mask
      Further grow or shrink the mask along the surface of the mesh.
   Increase/Decrease Contrast
      Changes the contrast of the mask.

In the :ref:`Adjust Last Operation <bpy.ops.screen.redo_last>` panel there are further options
to add iterations for a stronger effect.

Iterations
   The number of times the filter is applied.

Auto Iteration Count
   Use an automatic number of iterations based on the number of vertices of the sculpt.
   Disable this option to set the Iterations manually.

.. tip::

   An alternative to Iterations is to use :ref:`Repeat Last <bpy.ops.screen.repeat_last>`
   via the shortcut :kbd:`Shift-R`.


.. _bpy.ops.mesh.paint_mask_extract:

Expand Mask
===========

.. note::

   More info on Mask Expand along Topology at the :ref:`Expand page <bpy.ops.sculpt.expand>`.

Mask Extract
============

.. reference::

   :Mode:      Sculpt Mode
   :Menu:      :menuselection:`Mask --> Mask Extract`

Creates a duplicate mesh object based on masked geometry.
The extracted geometry is also further processed by default for a cleaner result.

Threshold
   Minimum mask value to consider the vertex valid to extract a face from the original mesh.

Add Boundary Loop
   Creates and extra boundary loop on the edges of the geometry,
   making it easier smooth the boundaries and apply additional modifiers.

Smooth Iterations
   Smooth iterations applied to the extracted mesh.

Project to Sculpt
   Project the extracted mesh on to the original sculpt object.

Extract as Solid
   Adds a :doc:`Solidify Modifier </modeling/modifiers/generate/solidify>` to the newly created mesh object.


.. _bpy.ops.mesh.paint_mask_slice:

Mask Slice
==========

.. reference::

   :Mode:      Sculpt Mode
   :Menu:      :menuselection:`Mask --> Mask Slice`

Removes the masked vertices from the mesh.

Threshold
   Minimum mask value to consider the vertex valid to extract a face from the original mesh.

Fill Holes
   Fills concave holes with geometry that might have resulted from the *Mask Slice* operation.

   .. tip::

      If nothing is masked, this operation can be used to just fill all holes.
      Especially when using :doc:`Trim </sculpt_paint/sculpting/tools/lasso_trim>`
      tools and the :doc:`Voxel Remesher </sculpt_paint/sculpting/tool_settings/remesh>`

   ..
      this is a useful workaround. But once the voxel remesher automatically checks for holes
      or a dedicated Fill Holes operation is added, this tip should be removed.

Slice to New Object
   Create a new object from the masked geometry.


.. _bpy.ops.sculpt.dirty_mask:

Mask From Cavity
================

.. reference::

   :Mode:      Sculpt Mode
   :Menu:      :menuselection:`Mask --> Mask from Cavity`

Generates a mask based on the cavity of the surface. The settings of the operation can be changed
in the :doc:`Adjust Last Operation </interface/undo_redo>` panel.

Mode
   Choose how the newly created mask is mixed with the existing one. By default it will replace the old mask via
   "Mix".
Mix Factor
   The factor of the mix effect. Choose how strong the new mask is applied on the existing one.
Automask Settings
   The same settings as the :doc:`Auto-Masking </sculpt_paint/sculpting/controls>` settings are applied.
Factor
   Same as :doc:`Auto-Masking </sculpt_paint/sculpting/controls>`.
Blur
   Same as :doc:`Auto-Masking </sculpt_paint/sculpting/controls>`.
Invert
   Same as :doc:`Auto-Masking </sculpt_paint/sculpting/controls>`.
Custom Curve
   Same as :doc:`Auto-Masking </sculpt_paint/sculpting/controls>`.


.. _bpy.ops.sculpt.mask_init:

Random Mask
===========

.. reference::

   :Mode:      Sculpt Mode
   :Menu:      :menuselection:`Mask --> Random Mask`

Generates a mask with random values for the entire object based on different mesh data.

Per Vertex
   Assigns a random mask value for each vertex.
Per Face Set
   Assigns a random mask value for each :doc:`Face Set </sculpt_paint/sculpting/editing/face_sets>`.
Per Loose Mask
   Assigns a random mask value for each disjoint part of the mesh.


.. _bpy.types.Sculpt.show_mask:
.. _bpy.types.View3DOverlay.sculpt_mode_mask_opacity:
.. _Mask Display Settings:

Display Settings
================

.. reference::

   :Mode:      Sculpt Mode
   :Popover:   :menuselection:`Viewport Overlays -- Sculpt --> Mask`

The mask display can be toggled as a :doc:`viewport overlay </editors/3dview/display/overlays>`.
In the overlay popover, the opacity of the mask overlay can be adjusted to make it more or less visible on the mesh.


.. _sculpt_mask_clear-data:

Clear Sculpt-Mask Data
======================

.. reference::

   :Mode:      Object/Edit Mode
   :Menu:      :menuselection:`Properties --> Object Data --> Geometry Data --> Clear Sculpt-Mask Data`

Completely frees the mask data layer from the mesh. While not a huge benefit,
this can speed-up sculpting if the mask is no longer being used.


## Sculpt


******
Sculpt
******

This page details the general hotkey operators and menu operators in sculpt mode.


Transforms
==========

Move
   Change the position of the object.
Rotate
   Change the orientation of the mesh.
Scale
   Increase/decrease the size of the mesh.
Sphere
   Morph the mesh to a spherical shape.

.. seealso::

   :doc:`Transform Tools </sculpt_paint/sculpting/tools/transforms>`.


.. _bpy.ops.paint.hide_show:

Show & Hide
===========

.. reference::

   :Mode:      Sculpt Mode
   :Menu:      :menuselection:`Sculpt`

Some very common hotkey operators to control the visibility based on face sets.
These are not part of any menu and have to be used via the shortcuts.
More visibility operators can be found in the :doc:`Face Sets Menu </sculpt_paint/sculpting/editing/face_sets>`
and the Pie Menu shortcut :kbd:`W`. (Since visibility is often toggled via face sets.)

Box Hide
   Draw a box to hide faces of a mesh.
Box Show
   Draw a box to reveal hidden faces.
   This works similar to the :ref:`Box Select <tool-select-box>` tool.

.. _bpy.ops.sculpt.face_set_change_visibility:

Toggle Visibility :kbd:`Shift-H`
   Hide all face sets except the active one (under the cursor).
   If face sets are already hidden, then this operator will show everything.

Hide Active Face Set :kbd:`H`
   Hide the face set under the cursor. Press :kbd:`Shift-H` afterwards to show everything.

.. _bpy.ops.paint.hide_show_all:

Show All :kbd:`W`, :kbd:`Alt-H`
   Reveal all hidden geometry.

.. _bpy.ops.paint.visibility_invert:

Invert Visible
   Hides all visible geometry and makes all hidden geometry visible.

.. _bpy.ops.paint.hide_show_masked:

Hide Masked
   Hides all masked vertices.

.. seealso::

   For a more general introduction see
   :doc:`Visibility, Masking & Face Sets </sculpt_paint/sculpting/introduction/visibility_masking_face_sets>`.


Trimming
========

The trimming operators add or remove geometry from the mesh based on a gesture input.
These operators are especially useful for sketching an early base mesh for further
sculpting with the :doc:`voxel remesher </sculpt_paint/sculpting/tool_settings/remesh>`.

.. _bpy.ops.sculpt.trim_box_gesture:

:doc:`/sculpt_paint/sculpting/tools/box_trim`
   Removes geometry based on a :ref:`box selection <tool-select-box>`.

.. _bpy.ops.sculpt.trim_lasso_gesture:

:doc:`/sculpt_paint/sculpting/tools/lasso_trim`
   Removes geometry based on a :ref:`lasso selection <tool-select-lasso>`.

:doc:`Box Add </sculpt_paint/sculpting/tools/box_trim>`
   Adds geometry based on a :ref:`box selection <tool-select-box>`.

:doc:`Lasso Add </sculpt_paint/sculpting/tools/lasso_trim>`
   Adds geometry based on a :ref:`lasso selection <tool-select-lasso>`.

.. _bpy.ops.sculpt.project_line_gesture:

:doc:`/sculpt_paint/sculpting/tools/line_project`
   Flattens the geometry along a plane determined by the camera view and a drawn line.
   The region of the mesh being flattened is visualized by the side of the line that is shaded.


Fairing
=======

These operators smooths geometry patches based of a :doc:`Face set </sculpt_paint/sculpting/editing/face_sets>`.

.. seealso::

   :doc:`Edit Face Set Tool </sculpt_paint/sculpting/tools/edit_face_set>`

Fair Positions
   Creates a perfectly flat and smooth geometry patch from the face set.
   This is the ideal way to trim parts of your mesh
   if the vertex count is too high for other operations,
   or the vertex IDs must not be altered
   (Like when using :doc:`Multires </modeling/modifiers/generate/multiresolution>` sculpting).

Fair Tangency
   Creates a smooth as possible geometry patch from the face set
   by minimizing changes in vertex :term:`tangents <Tangent>`.
   This is ideal for creating smooth curved surfaces on complex topology,
   where just using the smooth brush will not lead to desired results


.. _bpy.ops.sculpt.mesh_filter:

Mesh Filters
============

Applies a deformation to all vertices in the mesh at the same time.
Masking, auto-masking and visibility will be taken into account.

To use these operators, click and drag away from left to right
or from right to left for a negative effect.

.. seealso::

   :doc:`Mesh Filter Tool </sculpt_paint/sculpting/tools/mesh_filter>`

Smooth
   Smooths the positions of the vertices to either polish surfaces or remove volume from larger shapes.
   Especially useful to fix most of the artifacts of the voxel remesher.
   This filter works similar to the :doc:`Smooth </sculpt_paint/sculpting/tools/smooth>` brush.
Surface Smooth
   Eliminates irregularities of the mesh by making the positions
   of the vertices more uniform while preserving the volume of the object.
   This filter works similar to the *Surface* deformation type of the
   :doc:`Smooth </sculpt_paint/sculpting/tools/smooth>` brush.
Inflate
   Displaces vertices uniformly along their normal.
   This filter works similar to the :doc:`Inflate </sculpt_paint/sculpting/tools/inflate>` brush.
Relax Topology
   Tries to create an even distribution of quads without deforming the volume of the mesh.
   This filter works the same as holding :kbd:`Shift` with the
   :doc:`Slide Relax </sculpt_paint/sculpting/tools/slide_relax>` brush.
Relax Face Sets
   This will remove the jagged lines visible after drawing or creating a face set.
   This filter works the same as holding :kbd:`Shift` with the
   :doc:`Draw Face Set </sculpt_paint/sculpting/tools/draw_facesets>` brush.
Sharpen
   Sharpens and smooths the mesh based on its curvature,
   resulting in pinching hard edges and polishing flat surfaces.
   Especially useful when sculpting hard surfaces and stylized models
   with creasing and flattening brushes.
Enhance Details
   Increases the high frequency surface details of the mesh
   by intensifying the difference between creases and valleys.
   This filter works similar to the inverted direction of the
   :doc:`Smooth </sculpt_paint/sculpting/tools/smooth>` brush.
Erase Displacement
   Deletes displacement information of
   the :doc:`Multires Modifier </modeling/modifiers/generate/multiresolution>`,
   resetting the mesh to a regular subdivision surface result.
   This can be used to reset parts of the sculpt or to fix reprojection artifacts
   after applying a :doc:`Shrinkwrap Modifier </modeling/modifiers/deform/shrinkwrap>`.

   Negative strokes will intensify the displacement details,
   this method works similar to *Enhance Details* and can give better results in some circumstances.
Random
   Randomly moves vertices along the vertex normal.
   This filter works similar to the :ref:`Randomize Transform <bpy.ops.object.randomize_transform>`.


.. _bpy.ops.sculpt.sample_color:

Sample Color
============

.. reference::

   :Mode:      Sculpt Mode
   :Menu:      :menuselection:`Sculpt --> Sample Color`
   :Shortcut:  :kbd:`Shift-X`


Adjust the brush color of the :doc:`/sculpt_paint/sculpting/tools/paint` tool to the color under the mouse cursor.


.. _bpy.ops.sculpt.set_pivot_position:

Set Pivot
=========

.. reference::

   :Mode:      Sculpt Mode
   :Menu:      :menuselection:`Sculpt --> Set Pivot`

Like Object and Edit Mode, Sculpt Mode also has a :term:`Pivot Point`.
This is because the basic :doc:`move, rotate and scale </sculpt_paint/sculpting/tools/transforms>`
transforms are also supported in Sculpt Mode.
But the pivot point in Sculpt Mode is unique. It always moves together with the transformed mesh
and can be both manually & automatically placed.

Origin
   Sets the pivot to the origin of the sculpt.
Unmasked
   Sets the pivot position to the average position of the unmasked vertices.
Mask Border
   Sets the pivot position to the center of the mask's border.
   This operation will automatically happen when using :ref:`bpy.ops.sculpt.expand`.
Active Vertex
   Sets the pivot position to the active vertex position.
Surface :kbd:`Shift-RMB`
   Sets the pivot position to the surface under the cursor.

.. tip::

   For more convenient placement of the pivot point it's recommended to use the shortcut assigned to *Surface*.

.. seealso::

   For a more general introduction see :doc:`Transforming </sculpt_paint/sculpting/introduction/transforming>`.


.. _bpy.ops.sculpt.optimize:

Rebuild BVH
===========

.. reference::

   :Mode:      Sculpt Mode
   :Menu:      :menuselection:`Sculpt --> Rebuild BVH`

Recalculates the :term:`BVH` used by :doc:`/sculpt_paint/sculpting/tool_settings/dyntopo`
to improve performance, which might degrade over time while using Dyntopo.

.. seealso::

   For a more general introduction see :doc:`Adaptive Resolution </sculpt_paint/sculpting/introduction/adaptive>`.


Dynamic Topology Toggle
=======================

Toggles :doc:`/sculpt_paint/sculpting/tool_settings/dyntopo`.


Transfer Sculpt Mode
====================

.. reference::

   :Mode:      Sculpt Mode
   :Menu:      :menuselection:`Sculpt --> Transfer Sculpt Mode`
   :Shortcut:  :kbd:`Alt-Q`

Switches Sculpt Mode from the :term:`Active` object to the object under the mouse.
See :ref:`bpy.ops.object.transfer_mode` for more information.

.. seealso::

   For a more general introduction see
   :doc:`Working with Multiple Objects </sculpt_paint/sculpting/introduction/multiple_objects>`.


## Adaptive


*******************
Adaptive Resolution
*******************

In order for sculpting to give accurate and predictable results, Blender needs enough geometry.
Instead of starting out with a highly subdivided mesh, add geometry dynamically
by using either of the following adaptive sculpting methods.

Voxel Remesher
--------------

"Voxel remeshing" rebuilds the geometry with a perfectly even distributed topology.
Depending on the set voxel size, this will lead to a lower or higher resolution.

This technique is especially useful to block out the initial shape of an object.
It also has the advantage of removing any overlapping geometry and creating a manifold volume as a result.

.. figure:: /images/sculpt-paint_sculpt_voxel_merge.png

Any currently used mask, face sets and color attributes will be re-projected on the remeshed result.
Reaching high vertex counts should still be achievable with this technique, depending on the used hardware.

.. note::

   This technique will not work on objects that do not have an enclosed volume.
   Make sure to fill any holes in the mesh before remeshing.
   Or avoid any holes in the mesh/volume that are larger than the defined voxel size.

.. tip::

   If in doubt, you can fill all holes in edit mode or by using the
   :ref:`Mask Slice and Fill Holes <bpy.ops.mesh.paint_mask_slice>`
   operation to fill all holes in the mesh. If nothing is masked, it only fills any holes.

   ..
      this is a useful workaround. But once the voxel remesher automatically checks for holes
      or a dedicated Fill Holes operation is added, this tip should be removed.

To more easily access this feature, use the shortcuts :kbd:`R` to define the resolution,
and :kbd:`Ctrl-R` to execute the remeshing.

.. figure:: /images/sculpt-paint_sculpt_voxel_grid.png

.. seealso::

   More information at :doc:`Remesh </sculpt_paint/sculpting/tool_settings/remesh>`.

.. _dyntopo_introduction:

Dyntopo
-------

Dynamic topology (aka Dyntopo) is a dynamic tessellation
sculpting method that automatically adds and removes topology under the brush.

.. figure:: /images/sculpt-paint_sculpt_dyntopo_example.png

Unlike the Voxel Remesher, this makes it possible to sculpt complex shapes
without thinking about the resolution or topology.
It also allows to define a different resolution wherever necessary.
Much more complex base mesh sculpting is especially useful with this technique.

The disadvantages of this technique are a slower performance and limited support for some sculpt mode features.
Custom attributes like Color Attributes, UV Maps and Face Sets are also lost or corrupted when using Dyntopo.

This feature shares the same shortcuts with voxel remeshing when enabled.
Use :kbd:`R` to define the resolution and :kbd:`Ctrl-R` to flood fill the resolution (if Constant Detail is used).

.. note::

   Because Dyntopo and the Voxel Remesher are mutually exclusive and cannot be used at the same time,
   both use the same shortcut to define the remeshing resolution.

.. figure:: /images/sculpt-paint_sculpt_dyntopo_detail.png

Brushes like :doc:`Simplify </sculpt_paint/sculpting/tools/simplify>`,
:doc:`Snake Hook </sculpt_paint/sculpting/tools/snake_hook>`
and :doc:`Clay Strips </sculpt_paint/sculpting/tools/clay_strips>` work especially well with this feature.


.. seealso::

   More information at :doc:`Dyntopo </sculpt_paint/sculpting/tool_settings/dyntopo>`.


Multiresolution
---------------

The Multiresolution Modifier can be used for subdivision based sculpting.
This means the object will be subdivided, similar to the
:doc:`Subdivision Surface Modifier </modeling/modifiers/generate/subdivision_surface>`,
only that the subdivisions can be freely sculpted for very high resolution detailing.

.. figure:: /images/sculpt-paint_sculpt_multires_example.png

.. note::

   For this technique it is highly recommended to use on a clean topology base mesh.
   This means the base mesh should be only made of quads
   and avoid non-manifold faces, as well as poles with two connected edges.
   More information at :ref:`bpy.ops.object.quadriflow_remesh` Remeshing for an automatic retopology method.

This technique has the advantage of sculpting with multiple resolutions,
meaning you have the ability to sculpt on any level of subdivision.
This allows to add a much higher resolution of details for rendering and sculpting,
while displaying lower resolutions for better viewport performance.
It also allows sculpting on lower resolutions any time for broader changes.

As an example, you can sculpt general proportions in subdivision level 1,
add high resolution details in level 4 and switch back to subdivision 1 to correct the shape further.

The disadvantages are that you may end up with some mesh distortions
because the topology is not dynamic like voxel remeshing and dyntopo.
The topology should also not be changed once already subdivided,
since any edits to the base mesh will result in corrupted subdivision details.

.. tip::

   Pay attention to the topology that you sculpt and how much it gets stretched.
   If more resolution is needed you can always subdivide another time,
   but there will be worse performance and slower level switching once more than 5 subdivisions are used.
   Alternatively use the :doc:`Slide Relax </sculpt_paint/sculpting/tools/slide_relax>`
   brush to slide topology to where it is needed.

Additional brushes like the :doc:`Multires Eraser </sculpt_paint/sculpting/tools/multires_displacement_eraser>` and
:doc:`Multires Smear </sculpt_paint/sculpting/tools/multires_displacement_smear>` are recommended for adjustments.

Here are general shortcuts to use the feature.

- Step up one multires level :kbd:`Alt-2`
- Step down one multires level :kbd:`Alt-1`
- Set multires level / Create multires modifier :kbd:`Ctrl-0` to :kbd:`Ctrl-5`

.. seealso::

   More information at :doc:`Multiresolution Modifier </modeling/modifiers/generate/multiresolution>`.


## Brush


*********
The Brush
*********

Sculpt Mode is very recognizable by the behavior and visualization of the brush.
All the usual brush controls still apply, yet the brush for sculpting is displayed in 3D.
This means that the brush will follow the curvature of the surface
by orienting the radius to match the topology :term:`Normal`.

The inner ring of the brush cursor is used to visualize the strength of the brush.

.. figure:: /images/sculpt-paint_sculpting_introduction_brush.jpg

.. note::

    How closely the cursor follows the curvature of the mesh can be changed in
    the :doc:`Brush Settings </sculpt_paint/sculpting/tool_settings/brush_settings>` with "Normal Radius".
    This can make hard surface sculpting easier, for example with the
    :doc:`Scrape </sculpt_paint/sculpting/tools/scrape>` brush.

The brush is also used for other :doc:`tools </sculpt_paint/sculpting/tools/index>` in the toolbar
to better display how that tool works.
For example, the :doc:`Box Trim </sculpt_paint/sculpting/tools/box_trim>`
and :doc:`Lasso Trim </sculpt_paint/sculpting/tools/lasso_trim>` tools are able to use the current brush radius
for how deep geometry is trimmed or added.


Common Brushes
==============

There are many brushes to choose from but these are the most common brushes to be used during sculpting.
More information on sculpting brushes in the :doc:`Toolbar </sculpt_paint/sculpting/toolbar>`.

.. figure:: /images/sculpt-paint_sculpting_introduction_common_brushes.png
    :align: left

:doc:`Clay Strips </sculpt_paint/sculpting/tools/clay_strips>`
    Block out broad shapes and build up volumes before refining them further.

:doc:`Grab </sculpt_paint/sculpting/tools/grab>`
    Move geometry across the screen for general shaping.

:doc:`Smooth </sculpt_paint/sculpting/tools/smooth>`
    Smooth and shrink surfaces to remove noise or flatten shapes.

:doc:`Draw </sculpt_paint/sculpting/tools/draw>`
    Generic adding and subtracting on surfaces.
    This brush is often customized with different stroke methods and textures for various effects.

:doc:`Scrape </sculpt_paint/sculpting/tools/scrape>`
    Scrape and fill surfaces either for hard surface sculpting or more aggressive smoothing.

:doc:`Inflate </sculpt_paint/sculpting/tools/inflate>`
    Inflate or shrink volumes or surfaces.
    Especially useful for controlling the thickness of cylindrical shapes.

:doc:`Draw Sharp </sculpt_paint/sculpting/tools/draw_sharp>`
    Same as *Draw* but with a much sharper falloff. Useful for adding creases, cracks and other sharp edges.

:doc:`Crease </sculpt_paint/sculpting/tools/crease>`
    A mix of the *Draw* and *Pinch* brushes.
    Useful for creating detailed creases or sharpening existing creases for additional polish.

:doc:`Snake Hook </sculpt_paint/sculpting/tools/snake_hook>`.
    Similar to *Grab* but this brush will dynamically let go and pick up geometry during the stroke.
    The dragged geometry is also following the angle of the stroke, making it very useful for
    pulling geometry out.
    Ideally used together with :ref:`dyntopo_introduction`.


## Cloth Sculpting


***************
Cloth Sculpting
***************

Instead of sculpting cloth manually or creating complex physics simulation setups,
there are various tools directly in sculpt mode that offer a simplified
:doc:`Cloth Physics Simulation </physics/cloth/index>`.

.. figure:: /images/sculpt-paint_sculpt_cloth_example.png

This has various advantages but is especially useful for base mesh creation and larger clothing folds and draping.
Detailing is possible, but the slower performance on high resolution meshes and simplified cloth physics
might not lead to desirable results.

The resolution of the topology is mainly responsible for the size of the folds
and detail level of the simulation. So an optimal and evenly distributed topology is important.

Many sculpting features are supported, so for example :ref:`Masked <sculpt-mask-menu>` vertices
are :doc:`pinned </physics/cloth/settings/shape>` in the simulation.
Another example is with :doc:`auto-masked </sculpt_paint/sculpting/controls>` face set boundaries.
The sculpt mode :ref:`gravity <bpy.types.Sculpt.gravity>` factor is also applied on the cloth physics.

The main brushes and tools for this feature are the :doc:`Cloth Brush </sculpt_paint/sculpting/tools/cloth>`
and :doc:`Cloth Filter </sculpt_paint/sculpting/tools/cloth_filter>`,
but other transform brushes like :doc:`Pose </sculpt_paint/sculpting/tools/pose>` and
:doc:`Boundary </sculpt_paint/sculpting/tools/boundary>` also support cloth sculpting in the brush settings.

A demo file for trying out the various brushes and tools is available
`here <https://www.blender.org/download/demo-files/#sculpting>`__.


## Filters


*******
Filters
*******

Filters are tools which provide an alternative way of sculpting, because they do not rely on a brush radius.
Instead they will affect any vertices that are visible and not masked.

.. figure:: /images/sculpt-paint_filter_example.png

The strength is controlled by click & dragging from left to right.
The position of the cursor can be used to only affect specific areas, if auto-masking is used.

Many of the same brush types are also available as a filter type.
This way much of the mesh can simultaneously be smoothed, colored or have some cloth simulation applied.

.. tip::

   A common example for using the :doc:`Mesh Filter </sculpt_paint/sculpting/tools/mesh_filter>`
   is to smooth everything after increasing the resolution with
   the :doc:`Voxel Remesher </sculpt_paint/sculpting/tool_settings/remesh>`
   or :doc:`Dyntopo </sculpt_paint/sculpting/tool_settings/dyntopo>`.

.. seealso::

   More information at :doc:`Mesh Filter </sculpt_paint/sculpting/tools/mesh_filter>`,
   :doc:`Cloth Filter </sculpt_paint/sculpting/tools/cloth_filter>`,
   :doc:`Color Filter </sculpt_paint/sculpting/tools/color_filter>`
   and :ref:`bpy.ops.sculpt.mask_filter`.


## General


*******
General
*******

*Sculpt Mode* is similar to *Edit Mode* in that it is used to alter the shape of a model,
but Sculpt Mode uses a very different workflow:
instead of dealing with individual elements (vertices, edges, and faces),
an area of the model is primarily changed using brushes.

.. figure:: /images/sculpt-paint_sculpting_introduction_example.png

   Sculpting Mode Example.

Sculpt Mode is accessed from the mode menu of the :doc:`3D Viewport header </editors/3dview/modes>`
or with the pie menu via :kbd:`Ctrl-Tab`.
Once inside Sculpt Mode, the Toolbar and Tool Settings of the 3D Viewport will change to
Sculpt Mode specific panels. The cursor will change to a circle, to indicate the size of the brush.

.. warning::

   To have predictable brush behavior,
   make sure to :doc:`apply the scale </scene_layout/object/editing/apply>` of your mesh.

The following pages will briefly explain the fundamental features and concepts of *Sculpt Mode*,
including various links to other pages for more details.


## Index

################
  Introduction
################

.. toctree::
   :maxdepth: 2

   general.rst
   brush.rst
   visibility_masking_face_sets.rst
   filters.rst
   transforming.rst
   painting.rst
   multiple_objects.rst
   adaptive.rst
   cloth_sculpting.rst


## Multiple Objects


*****************************
Working with Multiple Objects
*****************************

Unlike Edit Mode, there is no multi-object editing supported for Sculpt Mode. Since sculpting often involves editing
many separate objects, it is recommended to use the shortcut :kbd:`Alt Q` while pointing at other objects, for
:ref:`bpy.ops.object.transfer_mode` quickly.

.. figure:: /images/sculpt-paint_sculpt_multi_object_example.png

The advantage of using multiple objects is that each can have its own origin and modifiers.
Splitting the geometry among multiple objects can also improve the sculpt mode performance.
Alternatively objects can also be :doc:`joined </scene_layout/object/editing/join>`
so there is no need to switch objects.

.. figure:: /images/sculpt-paint_sculpt_joined_object_example.png

In the case that Face Sets were already used, joining objects or creating new geometry in Edit Mode will
automatically assign new Face Sets. This makes it immediately possible to target each new geometry, for example via
auto-masking. If no Face Sets are created, use the :ref:`bpy.ops.sculpt.face_sets_init` operator to create them.

Face Sets and Masked geometry can also be extracted via :ref:`bpy.ops.mesh.paint_mask_extract`
or sliced into a new object via :ref:`bpy.ops.mesh.paint_mask_slice`.


## Painting


********
Painting
********

Sculpt Mode also allows painting your geometry via
:ref:`modeling-meshes-properties-object_data-color-attributes` such as Vertex Colors. This ensures that the most
common actions related to the sculpting workflow are contained in the same mode, to avoid unnecessary mode switching.

.. figure:: /images/sculpt-paint_sculpt_paint_example.png

Other sculpt mode features such as face sets, masking and filters can also be used with painting tools.

The painting functionality in Sculpt Mode is limited to a
:doc:`Paint </sculpt_paint/sculpting/tools/paint>`
and :doc:`Smear </sculpt_paint/sculpting/tools/smear>` brush,
as well as a :doc:`Color Filter </sculpt_paint/sculpting/tools/color_filter>`
and :doc:`Mask by Color </sculpt_paint/sculpting/tools/mask_by_color>` tool.

Just like any other brush, :kbd:`Shift` can be used to smooth.
In the case of painting brushes it will blur the colors within the brush radius instead.

.. note::

   Once any painting tool is executed, the :ref:`viewport color shading <viewport_shading_solid_color>` is switched
   to "Attribute".  This ensures that color attributes are shown on all objects once painting is needed.


## Transforming


************
Transforming
************

Transform tools to :doc:`move, rotate and scale </sculpt_paint/sculpting/tools/transforms>`
are also available in Sculpt Mode,
but with an important difference to other modes. Sculpt Mode uses its own pivot point,
which can be manually positioned :kbd:`Shift-RMB`
or automatically positioned with :ref:`Mask Expand <bpy.ops.sculpt.mask_expand>`.
This ensures that the pivot point can be more freely placed and always moves with the transformed geometry.

Optionally instead of keeping the transform tools active, you can enable the
:doc:`viewport gizmos </editors/3dview/display/gizmo>` to have access to the gizmo at all times.

.. note::

   The gizmo can in some cases block areas from being sculpted on.
   In that case move the pivot point somewhere else to be able to click on the desired surface.

Apart from the transform tools there are also special brushes to move,
rotate and scale the topology like :doc:`Pose </sculpt_paint/sculpting/tools/pose>`,
:doc:`Boundary </sculpt_paint/sculpting/tools/boundary>`
and :doc:`Elastic Deform </sculpt_paint/sculpting/tools/elastic_deform>`.


## Visibility Masking Face Sets


*******************************
Visibility, Masking & Face Sets
*******************************

Visibility Control
==================

Parts of the mesh can be hidden in Sculpt Mode.
Because hidden faces cannot be sculpted, hiding makes it easier to isolate what you want to work on.
Hiding geometry also improves the viewport performance.

Hiding is shared between all modes, except Object Mode
(i.e. hiding/showing of faces in one mode will hide the same faces in other modes too).

Unlike :doc:`Selection Masking </sculpt_paint/selection_visibility>` in other painting modes,
Sculpt Mode primarily uses Masks and Face Sets to easily control the mesh visibility
and which faces can currently be edited.
The exception is the :ref:`Clipping Region <clipping_region>`, which can be used in any mode.

The most common shortcuts are :kbd:`H` to hide the face set under the cursor
and :kbd:`Shift-H` to isolate the face set under the cursor (or show everything).

:ref:`Inverting the visibility <bpy.ops.sculpt.face_set_change_visibility>`
and :ref:`showing all <bpy.ops.paint.hide_show_all>` is also available in the :kbd:`Alt-W` pie menu.

.. seealso::

   More information for controlling the visibility at :doc:`Show & Hide </sculpt_paint/sculpting/editing/sculpt>`.


.. _sculpt-masks:

Masks
=====

.. figure:: /images/sculpt-paint_sculpting_editing_mask_example.jpg

A mask is used to control which vertices of the mesh are influenced by sculpting and painting.
The mask can for example be created/edited via the :doc:`Mask Brush </sculpt_paint/sculpting/tools/mask>`,
:doc:`Box Mask </sculpt_paint/sculpting/tools/box_mask>`,
:doc:`Lasso Mask </sculpt_paint/sculpting/tools/lasso_mask>`,
:doc:`Line Mask </sculpt_paint/sculpting/tools/line_mask>`
and :doc:`Mask by Color </sculpt_paint/sculpting/tools/mask_by_color>` tools.

Internally, masks are stored using the ``sculpt_mask`` :doc:`/modeling/geometry_nodes/attributes_reference`.


Clear & Invert
--------------

Creating masks follows a slightly different mental model than selecting in other modes.
For example :kbd:`Shift-LMB` is used for smoothing instead of adding to a mask.

Masking is also conceptually inverted to selection
(i.e. You **cannot** edit masked vertices. But you **can** edit selected vertices).

Instead a mask is typically always added to the current mask with :kbd:`LMB` and subtracted with :kbd:`Ctrl-LMB`.
So if you wish to edit the masked surfaces, you'll need to use the :ref:`Invert <mask_invert>` operator,
In the case of masking everything that is visible,
the best workflow is to first :ref:`Clear <mask_clear>` and then :ref:`Invert <mask_invert>` the mask.

Both these operators can be quickly accessed in the :kbd:`A` pie menu.

.. figure:: /images/sculpt-paint_sculpting_editing_mask_pie.png

.. seealso::

   More information about editing and using masks at the :doc:`Mask Menu </sculpt_paint/sculpting/editing/mask>`


.. _face_sets:

Face Sets
=========

.. figure:: /images/sculpt-paint_sculpting_editing_face_set_example.png

Face sets are used to group your mesh into differently colored faces,
which can then be quickly hidden or shown like mentioned above.
They can also be used for fast mask creation via the :ref:`Mask Expand <bpy.ops.sculpt.expand>`.
:ref:`Face Set Expand <face_set_expand>` is also useful for creating, editing and joining face sets.

More options can be found in the :kbd:`Alt-W` pie menu.

.. figure:: /images/sculpt-paint_sculpting_editing_face_set_pie.png

Otherwise Face Sets can be created/edited with the
:doc:`Draw Face Sets </sculpt_paint/sculpting/tools/draw_facesets>` brush,
:doc:`Box Face Set </sculpt_paint/sculpting/tools/box_face_set>` and
:doc:`Lasso Face Set </sculpt_paint/sculpting/tools/lasso_face_set>`.
They can also be edited with the
:doc:`Edit Face Set </sculpt_paint/sculpting/tools/edit_face_set>` tool.

.. seealso::

   More information about editing and using face sets at the
   :doc:`Face Sets Menu </sculpt_paint/sculpting/editing/face_sets>`

Internally, face sets are stored using the ``sculpt_face_set`` :doc:`/modeling/geometry_nodes/attributes_reference`.


Auto-Masking
============

:doc:`Auto-Masking </sculpt_paint/sculpting/controls>` is also a fast way of only editing specific geometry
without having to manually create a new mask or hide geometry.
This feature is especially useful in combination with face sets.

.. figure:: /images/sculpt-paint_sculpting_automasking_panel.png


Display Settings
================

The mask and face sets display can be toggled and adjusted in the :ref:`Mask Display Settings`.

.. figure:: /images/sculpt-paint_sculpting_viewport_overlays.png

.. note::

   When Xray shading is enabled, masks and face sets will not be displayed.


## Blob


****
Blob
****

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Blob`

Similar to :doc:`Draw </sculpt_paint/sculpting/tools/clay>`,
but vertices are pushed outwards like an inverted pinching effect.
This will lead to a more consistent spherical curvature and thickening of strokes.


Brush Settings
==============

General
-------

Magnify
   By default at 0.5 to push out the mesh during the stoke.
   More info at :ref:`Pinch/Magnify <bpy.types.Brush.crease_pinch_factor>`

.. note::

   More info at :ref:`sculpt-tool-settings-brush-settings-general` brush settings
   and on :ref:`sculpt-tool-settings-brush-settings-advanced` brush settings.


## Boundary


********
Boundary
********

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Boundary`

Similar to the :doc:`Pose </sculpt_paint/sculpting/tools/pose>` brush
but deforms the open boundaries of a mesh.
The tool detects the mesh boundary closest to the active vertex and
propagates the deformation using the brush :doc:`Falloff </sculpt_paint/brush/falloff>` into the mesh.

The main use cases of this brush are the *Bend* and *Expand* geometry,
which leads to the best results on evenly distributed quad based topology.
Use the *Inflate*, *Grab*, *Twist*, and *Smooth* deformation modes,
to further adjustments and tweaks to the result
(which do not depend that much on a clean topology).

.. tip::

   Boundaries to hidden geometry will also be counted as an open boundary.

The boundary origin is displayed via a white line, which indicates the reach of the deformation.
The targeted boundary that will be deformed is highlighted in the brush cursor color.

If the :ref:`Deformation Target <bpy.types.Brush.deform_target>`
is changed, the brush can also be used for cloth sculpting.

.. note::

   Evenly distributed and quad based topology will lead to much better results.
   Triangles and N-gons are also supported but may lead to unpredictable outcomes.


Brush Settings
==============

General
-------

.. note::

   More info at :ref:`sculpt-tool-settings-brush-settings-general` brush settings
   and on :ref:`sculpt-tool-settings-brush-settings-advanced` brush settings.

Unique
------

.. _bpy.types.Brush.boundary_deform_type:

Deformation
   Deformation type that is used by the brush.

   :Bend:
      Rotates the boundary around the local Y axis.
      Useful for creating folding shapes, like sleeves.
   :Expand:
      Moves/extends the mesh boundary in the local X direction.
      Useful for extending the boundaries along the surface.
   :Inflate:
      Works similar to the :doc:`Inflate </sculpt_paint/sculpting/tools/inflate>` tool but,
      the vertices that are inflated are constrained to the mesh boundary.
   :Grab:
      Works similar to the :doc:`Grab </sculpt_paint/sculpting/tools/grab>` tool but,
      the vertices that are grabbed are constrained to the mesh boundary.
   :Twist:
      Rotates the active boundary around the local Z axis.
      Useful for creating folds like on a skirt.
   :Smooth:
      Works similar to the :doc:`Grab </sculpt_paint/sculpting/tools/smooth>` tool but,
      the vertices that are smoothed are constrained to the mesh boundary.

.. _bpy.types.Brush.boundary_falloff_type:

Boundary Falloff
   How the brush :doc:`Falloff </sculpt_paint/brush/falloff>` is applied across the boundary.

   :Constant:
      Applies the same deformation in the entire boundary.
   :Brush Radius:
      Applies the deformation only within the brush radius.
   :Loop:
      Applies the brush falloff in a loop pattern along the boundary.
   :Loop and Invert:
      Applies the falloff radius in a loop pattern,
      inverting the direction back & forth.

.. _bpy.types.Brush.boundary_offset:

Boundary Origin Offset
   Offset of the boundary origin in relation to the brush radius.


## Box Face Set


************
Box Face Set
************

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Box Face Set`

Creates a new :doc:`Face Set </sculpt_paint/sculpting/editing/face_sets>`
based on a :ref:`box selection <tool-select-box>`.


Tool Settings
=============

Front Faces Only
   Only creates a mask on the faces that face towards the view.


## Box Mask


********
Box Mask
********

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Box Mask`

Creates a new :doc:`Mask </sculpt_paint/sculpting/editing/mask>`
based on a :ref:`box selection <tool-select-box>`.
Hold :kbd:`Ctrl` to subtract from the mask instead.

This tool is also accessible as a :ref:`shortcut operator <bpy.ops.paint.mask_box_gesture>` on :kbd:`B`.


Tool Settings
=============

Front Faces Only
   Only creates a mask on the faces that face towards the view.


## Box Trim


********
Box Trim
********

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Box Trim`

Adds or removes geometry based on a :ref:`box selection <tool-select-box>`.
This tool is especially useful for sketching an early base mesh for further
sculpting with the :doc:`voxel remesher </sculpt_paint/sculpting/tool_settings/remesh>`.

.. list-table::

   * - .. figure:: /images/sculpt-paint_sculpt_trim_lasso_visual_example_a.png

          Using Lasso Trim set to *Join*

     - .. figure:: /images/sculpt-paint_sculpt_trim_lasso_visual_example_b.png

          The symmetrized mesh.

     - .. figure:: /images/sculpt-paint_sculpt_trim_lasso_visual_example_c.png

          Sculpting with voxel remeshing.

New geometry is assigned to a new :ref:`Face Set <sculpting-editing-facesets>`.
When removing geometry, the new interior geometry along the selection will be assigned
a new face set instead.

.. note::

   It is not recommended to use this tool on a mesh above 100k
   vertices when using *Difference* or *Union* as the Trim Mode
   with the *Exact* Solver.
   This tool is using a Boolean operation so it might take a long time to process.
   For higher resolution meshes it is recommended to instead use the
   :doc:`Line Project </sculpt_paint/sculpting/tools/line_project>` tool or the *Fair Positions*
   mode of the :doc:`Edit Face Set </sculpt_paint/sculpting/tools/edit_face_set>` tool to trim geometry.


Tool Settings
=============

Solver
   Algorithm used to calculate the Boolean intersections.

   :Fast:
      Uses a mathematically simple solver which offers the best performance;
      however, this solver lacks support for overlapping geometry.
   :Exact:
      Uses a mathematically complex solver which offers the best results and has full
      support for overlapping geometry; however, this solver is much slower than the
      *Fast Solver*.

Trim Mode
   Geometry can be either added or removed by choosing one of these modes.

   :Difference:
      Removes geometry, filling any holes that are created.
   :Union:
      Creates a geometry and joins any intersections with existing geometry.
   :Join:
      Similar to *Union* but joins the mesh as separate geometry,
      without performing any Boolean operations with existing geometry.

Shape Orientation
   The method used to orientate the trimming shape.

   :View:
      Use the view to orientate the trimming shape.
   :Surface:
      Use the surface normal to orientate the trimming shape.

Extrude Mode
   :Fixed:
      Aligns new geometry orthogonally for 90 degree angles in depth.
   :Project:
      Aligns new geometry with the perspective of the current view for a tapered result.

Use Cursor for Depth
   Use cursor location and radius for the dimensions and position of the trimming shape.
   If not set, the tool uses the full depth of the object from the camera view.


## Clay


****
Clay
****

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Clay`

Similar to the :doc:`Draw </sculpt_paint/sculpting/tools/draw>` brush,
but includes settings to adjust the :ref:`sculpt plane <bpy.types.Brush.sculpt_plane>`
on which the brush acts. That's because it behaves like a combination of the
:doc:`Flatten </sculpt_paint/sculpting/tools/flatten>` and *Draw* brushes.

This brush is useful for building and removing volumes and shapes like real clay,
because it flattens details as you add/subtract from the surfaces.

If used together with :ref:`Dyntopo <bpy.ops.sculpt.dynamic_topology_toggle>`
it's easy to continuously build shapes, even in a single stroke.


Brush Settings
==============

General
-------

Hardness
   Slightly higher by default. This makes the profile of the brush more noticeable.
   More info at :ref:`Hardness <bpy.types.Brush.hardness>`

Auto-Smooth
   Enabled by default for a consistent smoothing effect.
   With lower brush strength (for example with lower pen pressure) the smoothing effect will be more noticeable
   and can be used to create and then blend/polish shapes in a single stroke.
   Enable Pressure to modulate the use of auto-smooth even more with pen inputs.
   More info at :ref:`Auto-Smooth <bpy.types.Brush.auto_smooth_factor>`

.. note::

   More info at :ref:`sculpt-tool-settings-brush-settings-general` brush settings
   and on :ref:`sculpt-tool-settings-brush-settings-advanced` brush settings.


## Clay Strips


***********
Clay Strips
***********

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Clay Strips`
   :Shortcut:  :kbd:`C`

Similar to the :doc:`Clay </sculpt_paint/sculpting/tools/clay>` brush,
but it uses a square tip shape instead of a round one.

Just like the *Clay* brush, it's useful for building and removing volumes
and shapes like real clay, because it flattens details as you add/subtract from the surfaces.

Clay Strips is very commonly used for aggressive building of volumes
and deliberate control over shapes on the surface.
This brush alone can be used for a fast rough pass over the entire sculpt,
with additional smoothing or polishing often required afterwards.
This brush can be very versatile with varying stroke directions, repeated strokes
and pen pressure to achieve various results.

If used together with :ref:`Dyntopo <bpy.ops.sculpt.dynamic_topology_toggle>`
it's easy to continuously build shapes, even in a single stroke.


Brush Settings
==============

General
-------

Normal Radius
   Higher by default. This ensures that the brush does not change directions to sporadically during a stroke.
   More info at :ref:`Normal Radius <bpy.types.Brush.normal_radius_factor>`

Tip Roundness
   Very low by default for a square shape for more deliberate shaping.
   More info at :ref:`Tip Roundness <bpy.types.Brush.tip_roundness>`

.. note::

   More info at :ref:`sculpt-tool-settings-brush-settings-general` brush settings
   and on :ref:`sculpt-tool-settings-brush-settings-advanced` brush settings.


## Clay Thumb


**********
Clay Thumb
**********

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Clay Thumb`

Similar to the :doc:`/sculpt_paint/sculpting/tools/clay` brush.
It imitates the effect of deforming clay with the finger, accumulating material during the stroke.
The sculpt plane tilts during the stroke in the front part of the brush to achieve this effect.


Brush Settings
==============

.. note::

   More info at :ref:`sculpt-tool-settings-brush-settings-general` brush settings
   and on :ref:`sculpt-tool-settings-brush-settings-advanced` brush settings.


## Cloth

.. _bpy.types.Brush.cloth:

*****
Cloth
*****

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Cloth`

This brush simulates cloth physics on the mesh under the brush cursor.
There are various deformation types and settings to customize the brush.

It's also easy to sculpt the mesh with other brushes and tools
in between using the cloth brushes.

.. note::

   Using a relatively small brush size makes the calculations much faster,
   while larger brush sizes might be too slow to get a usable brush.


Brush Settings
==============

General
-------

.. note::

   More info at :ref:`sculpt-tool-settings-brush-settings-general` brush settings
   and on :ref:`sculpt-tool-settings-brush-settings-advanced` brush settings.


Unique
------

Persistent
   Allows the cloth brush to not accumulate deformation after each stroke.
   This is convenient to always simulate the cloth based on the same initial shape,
   but applying different forces to it.

   When disabled, deformations accumulate after each stroke.

Set Persistent Base
   Resets the base mesh so that you can add another layer of deformations.

.. _bpy.types.Brush.cloth_simulation_area_type:

Simulation Area
   Selects the part of the mesh that is going to be simulated when the stroke is active.
   This can greatly affect performance depending on the complexity of the mesh.

   Local
      Simulates only a specific area around the brush limited by a fixed radius.
   Global
      Simulates the entire mesh.
   Dynamic
      The active simulation area moves with the brush while still being limited by a fixed radius.

.. _bpy.types.Brush.cloth_sim_limit:

Simulation Limit
   The Factor added relative to the size of the radius to limit the cloth simulation effects.

.. _bpy.types.Brush.cloth_sim_falloff:

Simulation Falloff
   The area to apply deformation falloff to the effects of the simulation.
   This setting is a factor of the *Simulation Limit* and is shown as a dashed line around the cursor.

.. _bpy.types.Brush.use_cloth_pin_simulation_boundary:

Pin Simulation Boundary
   Lock the position of the vertices in the simulation falloff area to avoid artifacts
   and create a softer transition with unaffected areas.

.. _bpy.types.Brush.cloth_deform_type:

Deformation
   The type of cloth deformation that is used by the brush.

   :Drag:
      Simulates pulling the cloth to the cursor,
      similar to placing a finger on a table cloth and pulling.
   :Push:
      Simulates pushing the cloth away from the cursor,
      similar to placing a finger on a table cloth and pushing.
   :Pinch Point:
      Simulates pulling the cloth into a point.
   :Pinch Perpendicular:
      Simulates pulling the brush into a line.
   :Inflate:
      Simulates air being blown under the cloth so that the cloth lifts up.
   :Grab:
      Simulates picking up and moving the cloth.
   :Expand:
      Simulates stretching the cloth out.
   :Snake Hook:
      Simulates moving the cloth without producing any artifacts in the surface
      and creates more natural looking folds than any of the other deformation modes.
      This is accomplished by adjusting the strength of the deformation constraints per brush step
      to avoid affecting the results of the simulation as much as possible.

.. _bpy.types.Brush.cloth_force_falloff_type:

Force Falloff
   Shape used in the brush to apply force to the cloth.

   :Radial: Applies the force as a sphere.
   :Plane: Applies the force as a plane.

.. _bpy.types.Brush.cloth_mass:

Cloth Mass
   Mass of each simulation particle.

.. _bpy.types.Brush.cloth_damping:

Cloth Damping
   How much the applied forces are propagated through the cloth.

.. _bpy.types.Brush.cloth_constraint_softbody_strength:

Soft Body Plasticity
   The amount the cloth preserves its original shape,
   acting as a :doc:`Soft Body </physics/soft_body/index>`.

.. _bpy.types.Brush.use_cloth_collision:

Use Collisions
   Enables the detection of collisions with other objects during the simulation.
   In order for the sculpt object to collide with objects,
   the collision object must have :doc:`Collision Physics </physics/collision>` activated.


## Cloth Filter


************
Cloth Filter
************

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Cloth Filter`

This tool works similar to the :doc:`Cloth Brush </sculpt_paint/sculpting/tools/cloth>`,
however, it applies a cloth simulation to all vertices in the mesh at the same time.
Click and drag away from the object for a positive effect and towards for a negative effect.

.. tip::

   Vertices can be "pinned" by :doc:`masking </sculpt_paint/sculpting/tools/mask>` vertices
   that should remain stationary, or by using :ref:`Face Sets <sculpting-editing-facesets>`.


Tool Settings
=============

Filter Type
   Operation that is going to be applied to the mesh.

   :Gravity: Applies gravity to the simulation.
   :Inflate: Inflates the cloth.
   :Expand: Expands the cloth's dimensions.
   :Pinch: Pinches the cloth to the point where the cursor was when the filter started.
   :Scale:
      Scales the mesh as a :doc:`Soft Body </physics/soft_body/index>`
      using the distance to the origin of the object as scale.
      This creates filter produces folds in the surface.
      The orientation of the folds can be controlled using the *Force Axis* and *Orientation*.

Strength
   The amount of effect the filter has on the mesh.

Force Axis
   Apply the force along the selected axis.

Orientation
   :doc:`Orientation </editors/3dview/controls/orientation>` of the axis to limit the filter force.

   :Local: Use the local axis to limit the force and set the gravity direction.
   :World: Use the world axis to limit the force and set the gravity direction.
   :View: Use the view axis to limit the force and set the gravity direction.

Cloth Mass
   Mass of each simulation particle.

Cloth Damping
   How much the applied forces are propagated through the cloth.

Use Face Sets
   Only applies the cloth forces to the vertices assigned to the :ref:`Face Set <sculpting-editing-facesets>`
   that are under the mouse.

Use Collisions
   Enables the detection of collisions with other objects during the simulation.
   In order for the sculpt object to collide with object,
   the collision object must have :doc:`Collision Physics </physics/collision>` activated.


## Color Filter


************
Color Filter
************

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Color Filter`

Apply color corrections or effects on the active color attribute
on all vertices in the mesh at the same time.

To use this tool, click and drag away from left to right
or from right to left for a negative effect.


Tool Settings
=============

Filter Type
   :Fill: Fills in a single color.
   :Hue: Shifts the Hue of each color.
   :Saturation: Increases or decreases the saturation.
   :Value: Increases or decreases the values.
   :Brightness: Increases or decreases the brightness.
   :Contrast: Increases or decreases the contrast.
   :Smooth: Blurs or sharpens the colors.
   :Red: Increases or decreases the red channel.
   :Green: Increases or decreases the green channel.
   :Blue: Increases or decreases the blue channel.

Fill Color
   Set a color that will be used for the fill filter type.

Strength
   The amount of effect the filter has on the color attribute.


## Crease


******
Crease
******

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Crease`
   :Shortcut:  :kbd:`Shift-C`

Create sharp indents or ridges by pushing or pulling the mesh, while pinching the vertices together.

Crease can also be used to sharpen and polish existing creases.
Enable pressure sensitivity on Strength to regulate the add/subtract effect while pinching creases.


Brush Settings
==============

General
-------

Pinch
   Adds a consistent pinching effect to your stroke.
   If set to 0 it the brush will behave like the
   :doc:`Draw </sculpt_paint/sculpting/tools/draw>` brush.
   If set to 1 and the brush strength set to 0, the brush
   will behave like a :doc:`Pinch </sculpt_paint/sculpting/tools/pinch>` brush.

.. note::

   More info at :ref:`sculpt-tool-settings-brush-settings-general` brush settings
   and on :ref:`sculpt-tool-settings-brush-settings-advanced` brush settings.


## Draw

****
Draw
****

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Draw`
   :Shortcut:  :kbd:`V`

Moves vertices inward or outward, based the average vertex normals within the brush radius.
This is a very default behavior for sculpting and can be used in most cases.

It is common to use this particular brush with heavy customization for creating many custom brushes.


Brush Settings
==============

.. note::

   More info at :ref:`sculpt-tool-settings-brush-settings-general` brush settings
   and on :ref:`sculpt-tool-settings-brush-settings-advanced` brush settings.


VDM Displacement
================

*Vector Displacement Maps* are supported for the *Draw* brush to insert complex & overhanging shapes.
Unlike regular displacement, this uses all 3 color channels of the image
to displace geometry in three directions instead of just one.

.. figure:: /images/sculpt-paint_sculpt_vdm_example.png
   :width: 580px

   An example of various VDM brushes used on a smooth head from the official demo file.

`Download the demo file <https://www.blender.org/download/demo-files/#sculpting>`__
for more information and to try the feature out.

To use this feature, enable :ref:`Vector Displacement <bpy.types.Brush.use_color_as_displacement>` in the texture
panel. All :ref:`stroke methods <bpy.types.Brush.stroke_method>` are supported, but the recommended behavior is
*Anchored*.

Ideal images for vector displacement are open EXR files
with :doc:`color clamping </render/materials/legacy_textures/colors>` disabled.

.. note::

   This feature is only supported with Area Plane mapping.


## Draw Facesets


**************
Draw Face Sets
**************

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Draw Face Sets`

Draw new or extend existing :ref:`Face Sets <sculpting-editing-facesets>` with each stroke.

Holding :kbd:`Ctrl` will continue drawing the same face set as the one under the cursor.
Holding :kbd:`Shift` will relax or smooth the edges of the face sets
by modifying the underlying topology so edges flow along the perimeter of the face sets.
This will remove the jagged lines visible after drawing or creating a face set.

.. note::

   More information in the
   :doc:`Face Set Introduction </sculpt_paint/sculpting/introduction/visibility_masking_face_sets>`.


Brush Settings
==============

General
-------

While a lot of the general brush settings are supported,
it's not needed to change them from the default,
as the brush purpose is very simple.

.. note::

   More info at :ref:`sculpt-tool-settings-brush-settings-general` brush settings
   and on :ref:`sculpt-tool-settings-brush-settings-advanced` brush settings.


## Draw Sharp


**********
Draw Sharp
**********

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Draw Sharp`

Similar to the :doc:`Draw </sculpt_paint/sculpting/tools/draw>` brush,
but it always deforms the mesh from the original coordinates
and uses the *Sharper* Falloff by default.

Draw Sharp is useful on high density meshes for creating cloth wrinkles, stylized hair or hard surface edges.
To further sharpen or polish sharp edges in the case that the mesh density is not enough,
it's recommended to use the :doc:`Pinch </sculpt_paint/sculpting/tools/pinch>`,
:doc:`Crease </sculpt_paint/sculpting/tools/crease>` or
:doc:`Multiplane Scrape </sculpt_paint/sculpting/tools/multiplane_scrape>` brushes.

A limitation is that the brush does not remesh the sculpted surfaces
with :ref:`Dyntopo <bpy.ops.sculpt.dynamic_topology_toggle>` enabled.
Because of that, a better brush to use with Dyntopo can be :doc:`Crease </sculpt_paint/sculpting/tools/crease>`.


Brush Settings
==============

General
-------

Direction
   On *Subtract* by default to carve in creases. More info at :ref:`Direction <bpy.types.Brush.direction>`

.. note::

   More info at :ref:`sculpt-tool-settings-brush-settings-general` brush settings
   and on :ref:`sculpt-tool-settings-brush-settings-advanced` brush settings.


## Edit Face Set


*************
Edit Face Set
*************

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Edit Face Set`
   :Operator:  :ref:`bpy.ops.sculpt.face_set_edit`

Edits the :doc:`Face Set </sculpt_paint/sculpting/editing/face_sets>` under the cursor.


Tool Settings
=============

Mode
   The operation to apply to the face set.

   :Grow Face Set:
      Grows the face sets boundary by one face based on mesh topology.
      This is also available as a :ref:`shortcut operator <bpy.ops.sculpt.face_set_edit>`
      via :kbd:`Ctrl-W`.
   :Shrink Face Set:
      Shrinks the face sets boundary by one face based on mesh topology.
      This is also available as a :ref:`shortcut operator <bpy.ops.sculpt.face_set_edit>`
      via :kbd:`Ctrl-Alt-W`.
   :Delete Geometry:
      Deletes the faces that are assigned to the face set.
   :Fair Positions:
      Creates a perfectly flat and smooth geometry patch from the face set.
      This is the ideal way to trim parts of your mesh
      if the vertex count is too high for other operations,
      or the vertex IDs must not be altered
      (Like when using :doc:`Multires </modeling/modifiers/generate/multiresolution>` sculpting).
   :Fair Tangency:
      Creates a smooth as possible geometry patch from the face set
      by minimizing changes in vertex :term:`tangents <Tangent>`.
      This is ideal for creating smooth curved surfaces on complex topology,
      where just using the smooth brush will not lead to desired results

   .. list-table::

      * - .. figure:: /images/sculpt-paint_sculpt_fairing_none.png

            Before fairing.

        - .. figure:: /images/sculpt-paint_sculpt_fairing_positions.png

            After using Fair Positions.

        - .. figure:: /images/sculpt-paint_sculpt_fairing_tangency.png

            After using Fair Tangency.

Strength
   The amount of effect the filter has on the mesh.
   This setting is only available for the fairing operations.

Modify Hidden
   Apply the edit operation to hidden face sets.


## Elastic Deform


**************
Elastic Deform
**************

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Elastic Deform`

Used to simulate realistic deformations such as grabbing or twisting of :term:`Elastic` objects.
For example, this tool works great for modeling the shape of organic objects such as humans or animals.
When pressing :kbd:`Ctrl`, the brush deforms vertices along the normal of the active vertex.


Brush Settings
==============

General
-------

.. note::

   More info at :ref:`sculpt-tool-settings-brush-settings-general` brush settings
   and on :ref:`sculpt-tool-settings-brush-settings-advanced` brush settings.

Unique
------

.. _bpy.types.Brush.elastic_deform_type:

Deformation
   The surface alteration that is used in the brush.

   :Grab: Used to drag a group of vertices around.
   :Bi-scale Grab:
      Like *Grab* but the falloff is more localized to the center of the brush.
   :Tri-scale Grab:
      Like *Bi-scale Grab* but the falloff is more localized to the center of the brush.
   :Scale: Displaces vertices away from the active vertex.
   :Twist: Vertices are rotated around the active vertex.

.. _bpy.types.Brush.elastic_deform_volume_preservation:

Volume Preservation
   Higher values preserve volumes more, but also lead to more bulging.
   (This value determines the poisson ratio for elastic deformation)


## Fill


****
Fill
****

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Fill`

Similar to the :doc:`Flatten </sculpt_paint/sculpting/tools/flatten>` brush,
but only pushes surfaces upwards to the medium height.

Although :kbd:`Ctrl` can be held to invert the effect to a Scrape brush,
if *Invert to Scrape* is enabled.
When disabled, the inverted direction will push surfaces away.


Brush Settings
==============

General
-------

.. note::

   More info at :ref:`sculpt-tool-settings-brush-settings-general` brush settings
   and on :ref:`sculpt-tool-settings-brush-settings-advanced` brush settings.


Unique
------

.. _bpy.types.Brush.invert_to_scrape_fill:

Invert to Scrape
   When enabled, holding :kbd:`Ctrl` while sculpting
   changes the brush behavior to be the same as the *Scrape* brush.
   When disabled, holding :kbd:`Ctrl` while sculpting,
   will push vertices below the cursor downward.


## Flatten


*******
Flatten
*******

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Flatten`

Flatten or contrast surfaces by pulling and pushing them towards
(or away from) a defined medium height.
This medium height is determined via an area plane within the brush radius.

This area plane height can be further defined in the brush settings.


Brush Settings
==============

General
-------

Direction :kbd:`Ctrl`
   Invert the direction to push surfaces away from the
   :ref:`sculpt plane <bpy.types.Brush.sculpt_plane>`,
   creating more surface contrast as a result.

.. note::

   More info at :ref:`sculpt-tool-settings-brush-settings-general` brush settings
   and on :ref:`sculpt-tool-settings-brush-settings-advanced` brush settings.


## Grab


****
Grab
****

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Grab`
   :Shortcut:  :kbd:`G`

Drag geometry across the screen, following the cursor.
*Grab* only moves the vertices that are under the brush radius at the start of the stroke.
This is an essential sculpting brush to be used frequently to build shapes and adjust proportions.

.. figure:: /images/sculpt-paint_sculpting_grab_example.jpg

.. note::

   The effect is similar to moving geometry in Edit Mode with Proportional Editing enabled,
   except that *Grab* can make use of other Sculpt Mode options and brush settings.


Brush Settings
==============

General
-------

Radius
   Pressure Sensitivity is not supported for this brush type. More info at :ref:`Radius <bpy.types.Brush.size>`.

Strength
   Pressure Sensitivity is not supported for this brush type. More info at :ref:`Strength <bpy.types.Brush.strength>`.

Normal Radius
   For this brush, this setting is a purely visual change.
   It does not alter the brush behavior. More info at :ref:`Normal Radius <bpy.types.Brush.normal_radius_factor>`.

Auto-Smooth
   This setting is not supported. More info at :ref:`Auto-Smooth <bpy.types.Brush.auto_smooth_factor>`.

.. note::

   More info at :ref:`sculpt-tool-settings-brush-settings-general` brush settings
   and on :ref:`sculpt-tool-settings-brush-settings-advanced` brush settings.


Unique
------

.. _bpy.types.Brush.use_grab_active_vertex:

Grab Active Vertex
   Applies the maximum strength of the brush to the highlighted active vertex,
   making it easier to manipulate low-poly models or meshes with modifiers.

   Enabling this option also enables a white wireframe overlay within the brush radius.
   This helps to visualize the real base geometry that is being manipulated
   while sculpting with :doc:`Modifiers </modeling/modifiers/index>`.

.. figure:: /images/sculpt-paint_sculpting_grab_active_vertex.jpg

.. _bpy.types.Brush.use_grab_silhouette:

Grab Silhouette
   Preserves the object's silhouette shape by only grabbing vertices on one side of the mesh curvature.
   The shape of the silhouette is determined by the orientation of the 3D Viewport and the start of the stroke.

.. figure:: /images/sculpt-paint_sculpting_grab_silhouette.jpg

Note how in the image only the bottom side of the leg is pulled down, despite the size of the brush.

.. tip::

   This setting is also useful for grabbing a single side of a crease
   and pushing it further inwards, creating a more pinched crease.


Additional Workflows
====================

2D Grab Brush
   If the :ref:`Falloff Shape <bpy.types.Brush.falloff_shape>` is set to *Projected*,
   the brush can grab infinitely deep into the viewport.
   This is especially useful for much broader changes to a sculpt.

   .. figure:: /images/sculpt-paint_sculpting_grab_projected.jpg

   The stroke can also be started outside of the mesh (like in empty 3D space)
   and grab the vertices within the brush radius.
   This can be useful for sculpting flat and tube-like meshes.


## Index


#########
  Tools
#########

.. toctree::
   :maxdepth: 1

   draw.rst
   draw_sharp.rst
   clay.rst
   clay_strips.rst
   clay_thumb.rst
   layer.rst
   inflate.rst
   blob.rst
   crease.rst
   smooth.rst
   flatten.rst
   fill.rst
   scrape.rst
   multiplane_scrape.rst
   pinch.rst
   grab.rst
   elastic_deform.rst
   snake_hook.rst
   thumb.rst
   pose.rst
   nudge.rst
   rotate.rst
   slide_relax.rst
   boundary.rst
   cloth.rst
   simplify.rst
   mask.rst
   draw_facesets.rst
   multires_displacement_eraser.rst
   multires_displacement_smear.rst
   paint.rst
   smear.rst
   box_mask.rst
   lasso_mask.rst
   line_mask.rst
   box_face_set.rst
   lasso_face_set.rst
   box_trim.rst
   lasso_trim.rst
   line_project.rst
   mesh_filter.rst
   cloth_filter.rst
   color_filter.rst
   edit_face_set.rst
   mask_by_color.rst
   transforms.rst


## Inflate


*******
Inflate
*******

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Inflate`
   :Shortcut:  :kbd:`I`

Similar to :doc:`Draw </sculpt_paint/sculpting/tools/clay>`,
except that vertices are moved in the direction of their own normals.
Especially useful when sculpting meshes with a lot of curvature.

Also available as a :doc:`Mesh Filter </sculpt_paint/sculpting/tools/mesh_filter>`
to inflate all unmasked areas at once.


Brush Settings
==============

General
-------

Direction
   Either Inflate or Deflate sculpted areas.
   This is different from the typical Add & Subtract.

.. note::

   More info at :ref:`sculpt-tool-settings-brush-settings-general` brush settings
   and on :ref:`sculpt-tool-settings-brush-settings-advanced` brush settings.


## Lasso Face Set


**************
Lasso Face Set
**************

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Lasso Face Set`

Creates a new :doc:`Face Set </sculpt_paint/sculpting/editing/face_sets>`
based on a :ref:`lasso selection <tool-select-lasso>`.


Tool Settings
=============

Front Faces Only
   Only creates a mask on the faces that face towards the view.


## Lasso Mask


**********
Lasso Mask
**********

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Lasso Mask`

Creates a new :doc:`Mask </sculpt_paint/sculpting/editing/mask>`
based on a :ref:`lasso selection <tool-select-lasso>`.
Hold :kbd:`Ctrl` to subtract from the mask instead.

This tool is also accessible as a :ref:`shortcut operator <bpy.ops.paint.mask_box_gesture>` on
:kbd:`Shift-Ctrl-LMB` drag.


Tool Settings
=============

Front Faces Only
   Only creates a mask on the faces that face towards the view.


## Lasso Trim


**********
Lasso Trim
**********

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Lasso Trim`

Adds or removes geometry based on a :ref:`lasso selection <tool-select-lasso>`.
This tool is especially useful for sketching an early base mesh for further
sculpting with the :doc:`voxel remesher </sculpt_paint/sculpting/tool_settings/remesh>`.

.. list-table::

   * - .. figure:: /images/sculpt-paint_sculpt_trim_lasso_visual_example_a.png

          Using Lasso Trim set to *Join*

     - .. figure:: /images/sculpt-paint_sculpt_trim_lasso_visual_example_b.png

          The symmetrized mesh.

     - .. figure:: /images/sculpt-paint_sculpt_trim_lasso_visual_example_c.png

          Sculpting with voxel remeshing.

New geometry is assigned to a new :ref:`Face Set <sculpting-editing-facesets>`.
When removing geometry, the new interior geometry along the selection will be assigned
a new face set instead.

.. note::

   It is not recommended to use this tool on a mesh above 100k vertices when using *Difference*
   or *Union* as the Trim Mode with the *Exact* Solver.
   This tool is using a Boolean operation so it might take a long time to process.
   For higher resolution meshes it is recommended to instead use the
   :doc:`Line Project </sculpt_paint/sculpting/tools/line_project>` tool or the *Fair Positions*
   mode of the :doc:`Edit Face Set </sculpt_paint/sculpting/tools/edit_face_set>` tool to trim geometry.


Tool Settings
=============

Solver
   Algorithm used to calculate the Boolean intersections.

   :Fast:
      Uses a mathematically simple solver which offers the best performance;
      however, this solver lacks support for overlapping geometry.
   :Exact:
      Uses a mathematically complex solver which offers the best results and has full
      support for overlapping geometry; however, this solver is much slower than the
      *Fast Solver*.

Trim Mode
   Geometry can be either added or removed by choosing one of these modes.

   :Difference:
      Removes geometry, filling any holes that are created.
   :Union:
      Creates a geometry and joins any intersections with existing geometry.
   :Join:
      Similar to *Union* but joins the mesh as separate geometry,
      without performing any Boolean operations with existing geometry.

Shape Orientation
   The method used to orientate the trimming shape.

   :View:
      Use the view to orientate the trimming shape.
   :Surface:
      Use the surface normal to orientate the trimming shape.

Extrude Mode
   :Fixed:
      Aligns new geometry orthogonally for 90 degree angles in depth.
   :Project:
      Aligns new geometry with the perspective of the current view for a tapered result.

Use Cursor for Depth
   Use cursor location and radius for the dimensions and position of the trimming shape.
   If not set, the tool uses the full depth of the object from the camera view.


## Layer


*****
Layer
*****

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Layer`

This brush is similar to :doc:`Draw </sculpt_paint/sculpting/tools/clay>`,
except that the height capped.
This creates the appearance of a flat layer.

It is recommended to use the :ref:`Persistent <bpy.types.Brush.use_persistent>` setting
and regularly :ref:`Set Persistent Base <bpy.ops.sculpt.set_persistent_base>`,
so that multiple strokes to not add on top of each other.


Brush Settings
==============

General
-------

Hardness
   Higher by default to ensure the profile of layers is more noticeable.
   More info at :ref:`Hardness <bpy.types.Brush.hardness>`

.. note::

   More info at :ref:`sculpt-tool-settings-brush-settings-general` brush settings
   and on :ref:`sculpt-tool-settings-brush-settings-advanced` brush settings.


Unique
------

.. _bpy.types.Brush.height:

Height
   The fixed height of each stroke. This is measured using the :ref:`scene scale <bpy.types.UnitSettings.system>`,
   so it is consistent no matter the amount of zoom or or object size.

.. _bpy.types.Brush.use_persistent:

Persistent
   This will ensure that multiple strokes use the same height, as if sculpting a single layer.

.. _bpy.ops.sculpt.set_persistent_base:

Set Persistent Base
   This button resets a new base so that you can sculpt new layer.


## Line Mask


*********
Line Mask
*********

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Line Mask`

This tool creates a :doc:`Mask </sculpt_paint/sculpting/editing/mask>`
across one side of a drawn line.
The affected area is visualized by the shaded side of the line.


Usage
=====

Use the tool by:

#. Orient the 3D Viewport to define the direction in depth.
#. :kbd:`LMB` and hold while moving the cursor to define direction of the line mask.
#. Adjust the operation with extra *Controls* shortcuts.
#. Release :kbd:`LMB` to confirm.

Hold :kbd:`Ctrl` to subtract from the mask instead.


Controls
========

Flip :kbd:`F`
   Changes the side of the line that the tool creates a mask.
Snap :kbd:`Ctrl`
   Constrains the rotation of the line to 15 degree intervals.
Move :kbd:`Ctrl-Spacebar`
   Reposition the line.


Tool Settings
=============

Front Faces Only
   Only creates a mask on the faces that face towards the view.

Limit to Segment
   The affected area will not extend the length of the drawn line.
   This helps defining a smaller area instead of extending the line infinitely long.


## Line Project


************
Line Project
************

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Line Project`

This tool flattens the geometry along a plane determined by the camera view and a drawn line.
The region of the mesh being flattened is visualized by the side of the line that is shaded.

.. list-table::

   * - .. figure:: /images/sculpt-paint_sculpting_tools_line-project_before.png

          Before Line Project.

     - .. figure:: /images/sculpt-paint_sculpting_tools_line-project_after.png

          After Line Project.


Usage
=====

Use the tool by:

#. Orient the 3D Viewport to define the direction in depth.
#. :kbd:`LMB` and hold while moving the cursor to define direction of the line projection.
#. Adjust the operation with extra *Controls* shortcuts.
#. Release :kbd:`LMB` to confirm.


Controls
========

Flip :kbd:`F`
   Changes the side of the line that the tool projects geometry.
Snap :kbd:`Ctrl`
   Constrains the rotation of the line to 15 degree intervals.
Move :kbd:`Ctrl-Spacebar`
   Reposition the line.


Tool Settings
=============

Limit to Segment
   The affected area will not extend the length of the drawn line.
   This helps defining a smaller area instead of extending the line infinitely long


## Mask


****
Mask
****

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Mask`
   :Shortcut:  :kbd:`M`

Paint a selection on parts of the mesh to be unaffected by other brushes & tools.
The mask values are shown as a gray-scale overlay.

.. note::

   More information in the
   :doc:`Masking Introduction </sculpt_paint/sculpting/introduction/visibility_masking_face_sets>`.


Brush Settings
==============

General
-------

.. note::

   More info at :ref:`sculpt-tool-settings-brush-settings-general` brush settings
   and on :ref:`sculpt-tool-settings-brush-settings-advanced` brush settings.


Unique
------

.. _bpy.types.Brush.mask_tool:

Mask Tool
   The mask brush has two modes:

   :Draw: Mask drawing.
   :Smooth: Holding :kbd:`Shift` will instead smooth existing masks.


## Mask By Color


*************
Mask by Color
*************

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Mask by Color`

Click on any color on the mesh to create a new mask (based on the active color attribute).


Tool Settings
=============

Threshold
   How much changes in color affect the mask generation. A smaller threshold includes fewer similar colors.
   A larger threshold includes much more similar colors.
Contiguous
   Mask only contiguous color areas. Colors that don't touch the one that you click on will not be masked.
Invert
   Invert the generated mask.
Preserve Previous Mask
   Preserve previous mask and add or subtract the new one generated by the colors.


## Mesh Filter


***********
Mesh Filter
***********

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Mesh Filter`

Applies a deformation to all vertices in the mesh at the same time.
Masking, auto-masking and visibility will be taken into account.

To use this tool, click and drag away from left to right
or from right to left for a negative effect.


Tool Settings
=============

Filter Type
   These are all of the available filter deformations.

   :Smooth:
      Smooths the positions of the vertices to either polish surfaces or remove volume from larger shapes.
      Especially useful to fix most of the artifacts of the voxel remesher.
      This filter works similar to the :doc:`Smooth </sculpt_paint/sculpting/tools/smooth>` brush.
   :Scale:
      Increases the size of the mesh.
      This filter works similar to the :ref:`Scale Transform <bpy.ops.transform.resize>`.
   :Inflate:
      Displaces vertices uniformly along their normal.
      This filter works similar to the :doc:`Inflate </sculpt_paint/sculpting/tools/inflate>` brush.
   :Sphere:
      Morphs the mesh progressively into a sphere.
      This filter works similar to the :ref:`To Sphere Transform <bpy.ops.transform.tosphere>`.
   :Random:
      Randomly moves vertices along the vertex normal.
      This filter works similar to the :ref:`Randomize Transform <bpy.ops.object.randomize_transform>`.
   :Relax:
      Tries to create an even distribution of quads without deforming the volume of the mesh.
      This filter works the same as holding :kbd:`Shift` with the
      :doc:`Slide Relax </sculpt_paint/sculpting/tools/slide_relax>` brush.
   :Relax Face Sets:
      This will remove the jagged lines visible after drawing or creating a face set.
      This filter works the same as holding :kbd:`Shift` with the
      :doc:`Draw Face Set </sculpt_paint/sculpting/tools/draw_facesets>` brush.
   :Surface Smooth:
      Eliminates irregularities of the mesh by making the positions
      of the vertices more uniform while preserving the volume of the object.
      This filter works similar to the *Surface* deformation type of the
      :doc:`Smooth </sculpt_paint/sculpting/tools/smooth>` brush.

      Shape Preservation
         How much of the original shape is preserved when smoothing.
      Per-Vertex Displacement
         How much the position of each individual vertex influences the final result.
   :Sharpen:
      Sharpens and smooths the mesh based on its curvature,
      resulting in pinching hard edges and polishing flat surfaces.
      Especially useful when sculpting hard surfaces and stylized models
      with creasing and flattening brushes.

      Smooth Ratio
         How much smoothing is applied to polished surfaces.
      Intensify Details
         Increases the high frequency surface details of the mesh
         by intensifying the difference between creases and valleys.
      Curvature Smooth Iterations
         The number of times the smoothing operation is applied per brush step.
         Controls how much smooth the resulting shape is, ignoring high-frequency details.
   :Enhance Details:
      Increases the high frequency surface details of the mesh
      by intensifying the difference between creases and valleys.
      This filter works similar to the inverted direction of the
      :doc:`Smooth </sculpt_paint/sculpting/tools/smooth>` brush.
   :Erase Displacement:
      Deletes displacement information of
      the :doc:`Multires Modifier </modeling/modifiers/generate/multiresolution>`,
      resetting the mesh to a regular subdivision surface result.
      This can be used to reset parts of the sculpt or to fix reprojection artifacts
      after applying a :doc:`Shrinkwrap Modifier </modeling/modifiers/deform/shrinkwrap>`.

      Negative strokes will intensify the displacement details,
      this method works similar to *Enhance Details* and can give better results in some circumstances.

Strength
   The amount of effect the filter has on the mesh.
   At certain object scales it can be useful to change this value.

Deformation Axis
   Apply the deformation only on the selected axis.

Orientation
   :doc:`Orientation </editors/3dview/controls/orientation>` of the axis to limit the filter displacement.

   :Local: Use the local axis to limit the displacement.
   :World: Use the global axis to limit the displacement.
   :View: Use the view axis to limit the displacement.


## Multiplane Scrape


*****************
Multiplane Scrape
*****************

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Multiplane Scrape`

Scrapes the mesh with two angled planes at the same time, creating a sharp edge between them.
This is useful for creating & polishing hard surface objects.


Brush Settings
==============

General
-------

.. note::

   More info at :ref:`sculpt-tool-settings-brush-settings-general` brush settings
   and on :ref:`sculpt-tool-settings-brush-settings-advanced` brush settings.


Unique
------

.. _bpy.types.Brush.multiplane_scrape_angle:

Plane Angle
   The angle between the two planes of the brush, pressing :kbd:`Ctrl` inverts the angle.

.. _bpy.types.Brush.use_multiplane_scrape_dynamic:

Dynamic Mode
   When enabled, the angle is dynamically updated based on the surface under the brush.
   The *Plane Angle* then controls how much the angle will increase when applying pen pressure.
   When pressing :kbd:`Ctrl`, it locks the plane angle to 0 degrees.

.. _bpy.types.Brush.show_multiplane_scrape_planes_preview:

Show Cursor Preview
   Displays a preview of the two planes
   and the angle they form during the stroke.


## Multires Displacement Eraser


****************************
Multires Displacement Eraser
****************************

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Multires Displacement Erase`

This brush deletes displacement information of
the :doc:`Multires Modifier </modeling/modifiers/generate/multiresolution>`,
resetting the mesh to a regular subdivision surface result.

This can be used to reset parts of the sculpt or to fix reprojection artifacts
after applying a :doc:`Shrinkwrap Modifier </modeling/modifiers/deform/shrinkwrap>`.

.. tip::

   This brush works best after using :ref:`Apply Base <bpy.ops.object.multires_base_apply>`.


Brush Settings
==============

General
-------

.. note::

   More info at :ref:`sculpt-tool-settings-brush-settings-general` brush settings
   and on :ref:`sculpt-tool-settings-brush-settings-advanced` brush settings.


## Multires Displacement Smear


***************************
Multires Displacement Smear
***************************

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Multires Displacement Smear`

This tool deforms displacement information of
the :doc:`Multires Modifier </modeling/modifiers/generate/multiresolution>`,
moving the displaced vertices without affecting the base mesh.

Smearing effect can be used multiple times
over the same area without generating any artifacts in the topology.

.. tip::

   This brush works best after using :ref:`Apply Base <bpy.ops.object.multires_base_apply>`.


Brush Settings
==============

General
-------

.. note::

   More info at :ref:`sculpt-tool-settings-brush-settings-general` brush settings
   and on :ref:`sculpt-tool-settings-brush-settings-advanced` brush settings.


Unique
------

.. _bpy.types.Brush.smear_deform_type:

Deformation
   Deformation type that is used by the brush.

   :Drag: Pulls the displacement values in the direction of the brush.
   :Pinch: Pulls the displacement values towards the center of the brush,
           creating hard surface effects without pinching the topology.
   :Expand: Pushes the displacement values away from the brush center, smoothing the displacement.


## Nudge


*****
Nudge
*****

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Nudge`

Moves vertices in the direction of the brush stroke.

Similar to the :doc:`Snake Hook </sculpt_paint/sculpting/tools/snake_hook>` brush,
but instead only moves the geometry along the surface (using the area plane).
This is useful for grabbing geometry along curved surfaces,
without making too impactful changes to the overall object shape.


Brush Settings
==============

General
-------

.. note::

   More info at :ref:`sculpt-tool-settings-brush-settings-general` brush settings
   and on :ref:`sculpt-tool-settings-brush-settings-advanced` brush settings.


## Paint


*****
Paint
*****

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Paint`

Paints on the active color attribute.
Hold :kbd:`Shift` to blur painted colors instead.

Color attribute's can be managed in the pallette pop-over in the middle of the header.

.. note::

   More information in the
   :doc:`Painting Introduction </sculpt_paint/sculpting/introduction/painting>`.


Brush Settings
==============

General
-------

Strength
   This settings has a different effect on this brush.
   Instead of defining the strength of each individual step in the stroke,
   it determines the overall Opacity of the applied color.

   Use the *Flow* setting instead for faster increasing of strength.

.. note::

   More info at :ref:`sculpt-tool-settings-brush-settings-general` brush settings
   and on :ref:`sculpt-tool-settings-brush-settings-advanced` brush settings.


Unique
------

.. _bpy.types.Brush.flow:

Flow
   Amount of paint that is applied per stroke sample.
   Used to create fast/slow accumulation effect.

.. _bpy.types.Brush.wet_mix:

Wet Mix
   Amount of paint that is picked from the surface into the brush color.
   Can achieve the effect of a wet canvas.

.. _bpy.types.Brush.wet_persistence:

Wet Persistence
   Amount of wet paint that stays in the brush after applying paint to the surface.

.. _bpy.types.Brush.wet_paint_radius_factor:

Wet Paint Radius
   Ratio between the brush radius and the radius that is going to be used to sample the color to blend in wet paint.

.. _bpy.types.Brush.density:

Density
   Amount of random elements that are going to be affected by this brush.
   Use this for a more detailed airbrush effect.
   This works best on a high resolution.

.. _bpy.types.Brush.tip_scale_x:

Tip Scale X
   Scale of the brush tip in the X axis.
   This is useful for a achieving a painting stroke like a marker or paint roller.


## Pinch


*****
Pinch
*****

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Pinch`
   :Shortcut:  :kbd:`P`

Pulls geometry towards the center of the brush.
When inverted via :kbd:`Ctrl` it will *Magnify* geometry
by pushing them away from the center of the brush.


Brush Settings
==============

General
-------

.. note::

   More info at :ref:`sculpt-tool-settings-brush-settings-general` brush settings
   and on :ref:`sculpt-tool-settings-brush-settings-advanced` brush settings.


## Pose


****
Pose
****

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Pose`

Deform a model simulating armature-like workflow.
This can either be useful for posing a model without a rig,
adjusting the proportions of a mesh or other fast deformations.

The brush will automatically determine an origin point,
indicated with a while line on the brush cursor.

If the :ref:`Deformation Target <bpy.types.Brush.deform_target>`
is changed, the brush can also be used for cloth sculpting.


Brush Settings
==============

General
-------

Only Radius and Auto-Masking has an impact on the brush behavior for this brush.

.. note::

   More info at :ref:`sculpt-tool-settings-brush-settings-general` brush settings
   and on :ref:`sculpt-tool-settings-brush-settings-advanced` brush settings.


Unique
------

.. _bpy.types.Brush.pose_deform_type:

Deformation
   Deformation type that is used by the brush.

   :Rotate/Twist:
      Rotates the mesh around the pose origin.
      When pressing :kbd:`Ctrl`, the brush applies a twist rotation
      instead (and disables any IK segments that are used).
   :Scale/Translate:
      Scale the mesh based on the pose origin.
      While holding :kbd:`Ctrl` the brush moves the mesh.
   :Squash/Stretch:
      Works similar to *Scale/Translate* however, it applies different
      scale values along different axes to achieve the stretching effect.

.. _bpy.types.Brush.pose_origin_type:

Rotation Origins
   Method to set the rotation origin for the pose origin or individual IK segments.

   :Topology:
      Sets the rotation origin automatically using the topology and shape of the mesh.
   :Face Sets:
      Creates a pose segment per :ref:`Face Set <sculpting-editing-facesets>`, starting from the active face set.
      This can lead to the most accurate and desirable results.
   :Face Sets FK:
      Simulates a :term:`Forward Kinematics` deformation using the :ref:`Face Set <sculpting-editing-facesets>`
      under the cursor as control.

.. _bpy.types.Brush.pose_offset:

Pose Origin Offset
   Offset of the pose origin in relation to the brush radius.
   This is useful to manipulate areas with a lot of complex shapes like fingers.

.. _bpy.types.Brush.pose_smooth_iterations:

Smooth Iterations
   Controls the smoothness of the falloff of the deformation.

.. _bpy.types.Brush.pose_ik_segments:

Pose IK Segments
   Controls how many :ref:`IK segments <bone-constraints-inverse-kinematics>`
   are going to be created for posing.
   This can be seen by a divided white line on the cursor.
   This is also useful for making curved deformations with the pose brush,
   like hair clumps and tails.

.. _bpy.types.Brush.use_pose_lock_rotation:

Lock Rotation when Scaling
   When using *Scale/Translate Deformation*, do not rotate the segment; only scaling is applied.

.. _bpy.types.Brush.use_pose_ik_anchored:

Keep Anchor Point
   Keeps the position of the last segment in the IK chain fixed.
   If this is disabled, the mesh can be dragged around more freely,
   creating snake like shapes.

.. _bpy.types.Brush.use_connected_only:

Connected Only
   The brush will only affect topologically connected elements.
   Disabling this will allow deforming multiple disconnected meshes at the same time,
   for example characters with clothing & shoes.

   Disabling this setting can have a big impact on performance,
   as neighboring elements will be merged internally.
   Keeping the *Max Element Distance* as low as possible
   will help counteract the performance impact.

.. _bpy.types.Brush.disconnected_distance_max:

Max Element Distance
   Maximum distance to search for disconnected loose parts in the mesh.


## Rotate


******
Rotate
******

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Rotate`

Rotates geometry in the direction in which the cursor is moved.
The initial drag direction is the zero angle
and by rotating around the center you can create a vortex/swirl effect.


Brush Settings
==============

General
-------

.. note::

   More info at :ref:`sculpt-tool-settings-brush-settings-general` brush settings
   and on :ref:`sculpt-tool-settings-brush-settings-advanced` brush settings.


## Scrape


******
Scrape
******

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Scrape`
   :Shortcut:  :kbd:`Shift-T`

Similar to the :doc:`Flatten </sculpt_paint/sculpting/tools/flatten>` brush,
but only pushes surfaces downward to the medium height.

Although :kbd:`Ctrl` can be held to invert the effect to a Fill brush,
if *Invert to Fill* is enabled.
When disabled, the inverted direction will push surfaces away.


Brush Settings
==============

General
-------

.. note::

   More info at :ref:`sculpt-tool-settings-brush-settings-general` brush settings
   and on :ref:`sculpt-tool-settings-brush-settings-advanced` brush settings.


Unique
------

Invert to Fill
   When enabled, holding :kbd:`Ctrl` while sculpting
   changes the brush behavior to be the same as the *Fill* brush.
   When disabled, holding :kbd:`Ctrl` while sculpting,
   will push vertices above the cursor up away from the cursor.


## Simplify


********
Simplify
********

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Simplify`

The Simplify brush is specifically meant for use with
:doc:`/sculpt_paint/sculpting/tool_settings/dyntopo`
to remove/add detail in the mesh.

Even when the :ref:`Refine Method <bpy.types.Sculpt.detail_refine_method>`
is set to *Subdivide Edges*, this brush is always able to collapse edges.
This ensures that while focusing on adding detail to your sculpt, the *Simplify* brush
can always be used to simplify and polish surfaces.

This brush has no effect if Dyntopo is disabled.

.. tip::

   In combination with auto-smooth the brush can polish surfaces while it remeshes them.
   On tube-like geometry it can also shrink and dissolve volumes completely.


Brush Settings
==============

General
-------

.. note::

   More info at :ref:`sculpt-tool-settings-brush-settings-general` brush settings
   and on :ref:`sculpt-tool-settings-brush-settings-advanced` brush settings.


## Slide Relax


***********
Slide Relax
***********

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Slide Relax`

This brush deforms the topology of the mesh
while minimizing changes to the geometrical shape of the mesh.
By default it will drag geometry, but this can be changed in the *Deformation* settings.

This brush is especially useful for redistributing topology to areas that require more detail,
or sliding geometry to somewhere where they should be.

Holding :kbd:`Shift` changes the brush effect to Relax geometry,
creating an even distribution of topology.


Brush Settings
==============

General
-------

.. note::

   More info at :ref:`sculpt-tool-settings-brush-settings-general` brush settings
   and on :ref:`sculpt-tool-settings-brush-settings-advanced` brush settings.


Unique
------

.. _bpy.types.Brush.slide_deform_type:

Deformation
   Deformation type that is used by the brush.

   :Drag: Slides the topology of the mesh in the direction of the stroke.
   :Pinch: Slides the topology of the mesh towards the center of the stroke.
   :Expand: Slides the topology of the mesh away from the center of the stroke.


## Smear


*****
Smear
*****

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Smear`

Smears the painted colors of the active color attribute.
It takes the colors under the cursor, and blends them in the direction of your stroke.


Brush Settings
==============

General
-------

.. note::

   More info at :ref:`sculpt-tool-settings-brush-settings-general` brush settings
   and on :ref:`sculpt-tool-settings-brush-settings-advanced` brush settings.


Unique
------

Deformation
   :Drag: Smear colors along the direction of the stroke.
   :Pinch: Smear colors inwards towards your brush center.
   :Expand: Smear colors outwards away from your brush center.


## Smooth


******
Smooth
******

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Smooth`
   :Shortcut:  :kbd:`S`

Smooths the positions of the vertices to either polish surfaces or remove volume from larger shapes.
Because this brush is so essential, it's always accessible by holding :kbd:`Shift` and sculpting.

Also available as a :doc:`Mesh Filter </sculpt_paint/sculpting/tools/mesh_filter>`
to smooth all unmasked areas at once.

.. note::

   The brush called *Smooth* will be used whenever holding :kbd:`Shift` and sculpting.
   If the smoothing strength or behavior needs to be changed, switch to the *Smooth*
   brush and adjust the settings there.


Brush Settings
==============

General
-------

Strength
   The strength of the smoothing is relative to the density of the mesh.
   If the resolution is increased on the sculpted mesh,
   the strength of the smooth brush will be weaker than before and needs to be increased.

Direction :kbd:`Ctrl`
   Smooth
      Smooths the surface of the mesh.
   Enhance Details
      Enhances details on the surface of the mesh by applying a smoothing operation in the opposite direction.

.. _bpy.types.Brush.smooth_deform_type:

.. note::

   More info at :ref:`sculpt-tool-settings-brush-settings-general` brush settings
   and on :ref:`sculpt-tool-settings-brush-settings-advanced` brush settings.


Unique
------

Deformation
   There are two deformation types.

   :Laplacian:
      Smooths the surface and volumes. This is the default behavior.
   :Surface:
      Smooths only the surface of the mesh, while preserving the volume.

      .. _bpy.types.Brush.surface_smooth_shape_preservation:

      Shape Preservation
         How much of the original shape is preserved while smoothing. Increasing the value
         reduces the effect of having multiple iterations on the strength of smoothing.

      .. _bpy.types.Brush.surface_smooth_current_vertex:

      Per-Vertex Displacement
         How much the position of each individual vertex influences the final result.
         Increasing the value reduces the overall strength of smoothing.

      .. _bpy.types.Brush.surface_smooth_iterations:

      Iterations
         Number of smoothing iterations per brush step.

      .. note::

         This method works by applying regular smoothing, computing the difference between
         the original (blended between start of iteration and fully original based on *Shape Preservation*)
         and the smoothed mesh, smoothing these offsets, pushing vertices back using the smoothed offsets,
         and finally blending in the original mesh based on *Per-Vertex Displacement*.


## Snake Hook


**********
Snake Hook
**********

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Snake Hook`
   :Shortcut:  :kbd:`K`

Pulls vertices along with the movement of the brush to create long, snake-like forms.
During the stroke, geometry will be dynamically picked up & let go.

When the *Rake* setting is used,
the brush can also be used to rotate geometry via dragging.


Brush Settings
==============

General
-------

.. note::

   More info at :ref:`sculpt-tool-settings-brush-settings-general` brush settings
   and on :ref:`sculpt-tool-settings-brush-settings-advanced` brush settings.


Unique
------

Magnify
   Pulled geometry tends to lose volume along the stroke.
   With *Magnify* value greater than 0.5 this is prevented.
   More info at :ref:`Pinch/Magnify <bpy.types.Brush.crease_pinch_factor>`

.. _bpy.types.Brush.rake_factor:

Rake
   Rotates geometry along the direction of the stroke.

.. _bpy.types.Brush.snake_hook_deform_type:

Deformation
   Deformation type that is used by the brush.

   :Radius Falloff:
      Applies the brush falloff to the tip of the brush.
   :Elastic:
      Modifies the entire mesh using an :term:`Elastic` deformation.
      More info in the :doc:`Elastic Deform </sculpt_paint/sculpting/tools/elastic_deform>` brush.


## Thumb


*****
Thumb
*****

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Thumb`

Similar to the :doc:`Grab </sculpt_paint/sculpting/tools/grab>` brush,
but instead only moves the geometry along the surface (using the area plane).
This is useful for grabbing surfaces with a very specific direction,
or without making too impactful changes to the overall object shape.


Brush Settings
==============

General
-------

.. note::

   More info at :ref:`sculpt-tool-settings-brush-settings-general` brush settings
   and on :ref:`sculpt-tool-settings-brush-settings-advanced` brush settings.


## Transforms


**********
Transforms
**********

Move
====

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Move`

Translation tool.


Rotate
======

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Rotate`

Rotation tool.


Scale
=====

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Scale`

Scale tool.


Transform
=========

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Transform`

Tool to adjust the objects translation, rotations and scale.


Tool Settings
=============

Each tool has the following settings to change how the unmasked mesh will be transformed.

Transform Mode
   How the transformation is going to be applied to the target.

   :All Vertices:
      Applies the transformation to all vertices in the mesh.
   :Elastic:
      Applies the transformation while dynamically simulating elasticity.
      Instead of applying this to all vertices, it uses the radius of the cursor as the area of effect.


## Brush Settings


**************
Brush Settings
**************

.. figure:: /images/sculpt-paint_sculpting_tool-settings_brush-settings_brush-panel.png
   :align: right

   Brush settings panel.


Information on brush settings for every mode can be found in these pages:

:doc:`Brush </sculpt_paint/brush/brush_settings>`
   General and advanced settings.

:doc:`Texture </sculpt_paint/brush/texture>`
   Color and mask texture settings.

:doc:`Stroke </sculpt_paint/brush/stroke>`
   Stroke methods and settings.

:doc:`Falloff </sculpt_paint/brush/falloff>`
   Falloff curves and settings.

:doc:`Cursor </sculpt_paint/brush/cursor>`
   Cursor and appearance settings.

.. toctree::
   :hidden:

   Brush Settings </sculpt_paint/brush/brush_settings.rst>
   Texture </sculpt_paint/brush/texture.rst>
   Stroke </sculpt_paint/brush/stroke.rst>
   Falloff </sculpt_paint/brush/falloff.rst>
   Cursor </sculpt_paint/brush/cursor.rst>


## Dyntopo

.. _bpy.ops.sculpt.dynamic_topology_toggle:

*******
Dyntopo
*******

.. reference::

   :Mode:      Sculpt Mode
   :Panel:     :menuselection:`Sidebar --> Tool --> Dyntopo`

Dynamic Topology (aka Dyntopo) can be toggled with the checkbox.
With dynamic topology active, most brushes will subdivide the mesh during the stroke.

For a general explanation of dynamic topology, visit
the :doc:`Introduction </sculpt_paint/sculpting/introduction/adaptive>`.

.. _bpy.types.Sculpt.detail_size:
.. _bpy.types.Sculpt.constant_detail_resolution:
.. _bpy.types.Sculpt.detail_percent:
.. _bpy.ops.sculpt.dyntopo_detail_size_edit:

Detail Size/Percentage, Resolution :kbd:`R`
   Each Detail Type's detail is set here. Depending on the Detail Type being used
   this property will rather show as a pixel count (px), or percentage.

   Sample Detail Size (pipette icon)
      When using *Constant Detail*, it is possible to sample the detail value of a certain mesh area
      by clicking the pipette icon next to the detail setting and then clicking on the area.

      .. More on shortcut. Shift for precision. Ctrl for sampling. Only available for constant and manual size.

.. _bpy.types.Sculpt.detail_refine_method:

Refine Method
   Setting the option will determine which of the methods will be used when altering the topology.

   :Subdivide Edges:
      Just like the Subdivide tool, this method will only subdivide topology
      to match the detail given.
   :Collapse Edges:
      When topology is too dense, and is smaller than the detail given, edges will
      be collapsed to fit the detail size appropriately.
   :Subdivide Collapse:
      This method combines the two methods, subdividing edges smaller than
      the detail size, and collapsing topology.

.. _bpy.types.Sculpt.detail_type_method:

Detailing
   Dyntopo uses the following different detail methods to create dynamic detail on an object.

   :Relative Detail:
      This method uses a detail size based on the number of pixels, and in turn
      will create topology in that size. Zoom out big details, zoom in small fine details.
   :Constant Detail:
      To keep detail uniform across the entire object, Constant Detail can be used.
      The detail is based on the percentage of a single unit.
   :Brush Detail:
      Giving more control over the topology, with this method you can create topology
      based on the brush size. You can increase and lower topology by resizing the brush itself.
      The detail size is based the size of the brush itself,
      where full detail will create topology the size of the brush radius itself.
   :Manual Detail:
      Similar to constant detail, this value sets a percentage value uniform across the object, but only
      applies detailing changes when using Flood Fill.

.. _bpy.ops.sculpt.detail_flood_fill:

Detail Flood Fill :kbd:`Ctrl-R`
   When using *Constant* or *Manual* *Detailing*, this option is made available,
   allowing you to fill the entire object with a uniform detail, based on the detail size.


## Index


#################
  Tool Settings
#################

.. toctree::
   :maxdepth: 2

   /sculpt_paint/brush/brush.rst
   brush_settings.rst
   dyntopo.rst
   remesh.rst
   symmetry.rst
   options.rst


## Options


*******
Options
*******

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Options`

Display
   Fast Navigate
      For multiresolution models, shows low resolution while navigating in the viewport.
   Delay Viewport Updated
      Update the geometry when it enters view. This provides for faster navigation.
   Use Deform Only
      Limits the activated modifiers on the active object to Deform Modifiers, and Multiresolution.
      Constructive modifiers (like Subdivision Surface, Mirror and other) get deactivated,
      because they could give inaccurate results.

   .. seealso::

      See the :ref:`Display <sculpt-paint-brush-display>` options.


Gravity
=======

.. _bpy.types.Sculpt.gravity:

Factor
   Setting the factor allows you to add gravity to your brush strokes,
   giving it a draping effect.

.. _bpy.types.Sculpt.gravity_object:

Orientation
   Using another object, the gravity can be oriented to the set object's local Z axis,
   changing the direction of the gravity.


## Remesh


******
Remesh
******

.. reference::

   :Mode:      Sculpt Mode
   :Header:    :menuselection:`Tool Settings --> Remesh`
   :Panel:     :menuselection:`Sidebar --> Tool --> Remesh`
   :Shortcut:  :kbd:`Ctrl-R`

For a general explanation to remeshing, visit the :doc:`Introduction </sculpt_paint/sculpting/introduction/adaptive>`.

Voxel Size :kbd:`R`
   The resolution or the amount of detail the remeshed mesh will have.
   The value is used to define the size, in object space, of the :term:`Voxel`.
   These voxels are assembled around the mesh and are used to determine the new geometry.
   For example a value of 0.5m will create topological patches that are about 0.5m
   (assuming *Preserve Volume* is enabled).
   Lower values preserve finer details but will result in a mesh with a much more dense topology.

   The voxel size also be adjusted from the 3D Viewport using :kbd:`R`.
   Using the shortcut displays an interactive grid overlay showing the resulting voxel size.
   Moving the mouse closer to center of the grid decreases the voxel size
   while moving away from the center increase the voxel size.
   Holding :kbd:`Shift`` increases the precision; adjusting the voxel size in small increments.
   Holding :kbd:`Ctrl` adjusts the voxel size relative to the current voxel size.

   Sample Voxel Size
      Used to adjust the *Voxel Size* by picking an area of the mesh
      to match the denseness of polygons after the remesh operation.

Adaptivity
   Reduces the final face count by simplifying geometry where detail is not needed.
   This introduce triangulation to faces that do not need as much detail.
   Note, an *Adaptivity* value greater than zero disables *Fix Poles*.

Fix Poles
   Tries to produce less :term:`poles <Pole>` at the cost of some performance to produce a better topological flow.

Preserve
   Volume
      Tells the algorithm to try to preserve the original volume of the mesh.
      Enabling this could make the operator slower depending on the complexity of the mesh.
   Paint Mask
      Reprojects the :ref:`paint mask <sculpt-mask-menu>` onto the new mesh.
   Face Sets
      Reprojects :ref:`Face Sets <sculpting-editing-facesets>` onto the new mesh.
   Color Attributes
      Reprojects the :ref:`Color Attributes <modeling-meshes-properties-object_data-color-attributes>` onto the
      new mesh.

Voxel Remesh
   Performs the remeshing operation to create a new manifold mesh based on the volume of the current mesh.
   Performing this will lose all mesh object data layers associated with the original mesh.

.. seealso::

   :doc:`Remesh modifier </modeling/modifiers/generate/remesh>`


Known Limitations
=================

- Remeshing only works on the original mesh data and
  ignores generated geometry from modifiers, shape keys, rigging, etc.
- Remeshing will not work with the :doc:`/modeling/modifiers/generate/multiresolution`.


## Symmetry


********
Symmetry
********

.. reference::

   :Mode:      Sculpt Mode
   :Tool:      :menuselection:`Toolbar --> Tool --> Symmetry`

Mirror
   Mirror the brush strokes across the selected local axes.
   Note that if you want to alter the directions the axes point in,
   you must rotate the model in Edit Mode and not in Object Mode.

.. _bpy.types.Sculpt.lock:

Lock
   These three buttons allow you to block any modification/deformation
   of your model along selected local axes, while you are sculpting it.

Tiling
   Using this option allows you to seamlessly tile your strokes along the given axes.
   This allows to create repeating patterns.

Feather
   Reduces the strength of the stroke where it overlaps the planes of symmetry.

.. _bpy.types.Sculpt.radial_symmetry:

Radial X, Y, Z
   These settings allow for radial symmetry in the desired axes.
   The number determines how many times the stroke will be repeated
   within 360 degrees around the central axes.

Tile Offset X, Y, Z
   The offset allows the option to alter the tile size along all three axes.
   The default tile size is set to one unit.

.. rubric:: Symmetrize

.. _bpy.types.Sculpt.symmetrize_direction:

Direction
   Determines which direction the model will be symmetrized.

Merge Distance
   A parameter of the *Symmetrize* operator to control
   the distance within which symmetrical vertices are merged.

.. _bpy.ops.sculpt.symmetrize:

Symmetrize
   Uses direction orientation to symmetrize. Since Dyntopo adds
   details dynamically it may happen that the model becomes asymmetric,
   so this a good tool for that.


## Index

.. _bpy.types.ImagePaint:
.. _bpy.types.Material.paint:

#################
  Texture Paint
#################

.. toctree::
   :maxdepth: 2

   introduction.rst
   tools.rst
   tool_settings/index.rst


## Introduction


************
Introduction
************

A UV texture is a picture (image, sequence or movie)
that is used to color the surface of a mesh.
The UV texture is mapped to the mesh through one or more UV maps.
There are three ways to establish the image used by the UV texture:

#. Use any image editing program to create an image. In the Image Editor,
   select the UV texture and load the image. Blender will then use
   that texture's UV map to transfer the colors to the faces of the mesh.
#. Paint a flat image in the Image Editor onto the currently selected UV texture,
   using its UV map to transfer the colors to the faces of the mesh.
#. Paint the mesh in the 3D Viewport, and let Blender use
   the currently selected UV map to update the UV texture
   (as discussed below).

Blender features a built-in paint mode called *Texture Paint* which is designed
specifically to help you edit your UV textures and images quickly and
easily in either the Image Editor or the 3D Viewport.
Since a UV texture is just a special-purpose image,
you can also use any external paint program, like GIMP or Krita.

.. figure:: /images/sculpt-paint_texture-paint_introduction_example.png
   :align: right
   :width: 430px

   Texture painting in Blender.

Since a mesh can have layers of UV textures, there may be many images that color the mesh.
However, each UV texture only has one image.

*Texture Paint* works in both a 3D Viewport and the Image Editor.
In the 3D Viewport in Texture Paint Mode, you paint directly on the mesh by projecting onto the UVs.

.. tip:: Memory Optimization

   *Texture Paint* is fast and responsive when working in the 3D Viewport and
   when your image is sized as a square where the side lengths are a power of two,
   e.g. 256×256, 512×512, 1024×1024, etc.


Getting Started
===============

The object to be painted on must first be :doc:`unwrapped </modeling/meshes/uv/unwrapping/introduction>`.
UVs can be added traditionally, with standard :doc:`Unwrapping Tools </modeling/meshes/editing/uv>`,
or by adding :ref:`Simple UVs <bpy.ops.paint.add_simple_uvs>` in Texture Paint mode.

.. note::

   When no UV layers can be detected, Blender will display a warning message.

Once you have unwrapped your model to a UV map, you can begin the texturing process.
To use texture paint you may do any of the following:

- Activate the Texture Paint workspace. Here the 3D Viewport has the Texture Paint Mode enabled
  and the Image Editor is already switched to Paint mode.
- In the 3D Viewport, select Texture Paint Mode from the mode selector in the header,
  and you can paint directly onto the mesh.
- In the Image Editor, switch the mode to Paint (shown in the image to the right).

.. figure:: /images/sculpt-paint_texture-paint_introduction_paint-mode.png
   :align: right

   Enabling Paint mode.

Once you enable Texture Painting, your mouse becomes a brush.
As soon as you enable Texture Painting or switch to Texture Paint Mode,
different tools become available in the Toolbar.

In the Image Editor, you paint on a flat canvas that is wrapped around the mesh using UV coordinates.
Any changes made in the Image Editor show up immediately in the 3D Viewport, and vice versa.

To work with the UV layout (for example, to move coordinates) you must use the :doc:`/editors/uv/index`.

A full complement of brushes and colors can be selected from the Sidebar region in the Image Editor.
Brush changes made in either panel are immediately reflected in the other panel.
However, the modified texture will **not** be saved automatically;
you must explicitly do so by :menuselection:`Image Editor --> Image --> Save`.


Texture Preview
===============

If your texture is already used to color, bump map, displace, alpha-transparent, etc.,
a surface of a model in your scene (in other technical words,
is mapped to some aspect of a texture via a texture channel using UV as a map input),
you can see the effects of your painting in the context of your scene as you paint.

To do this, set up side-by-side areas, one Area in 3D Viewport set to *Texture* shading option,
and in the second Area the Image Editor loaded with your image.
Position the 3D Viewport to show the object that is UV-mapped to the loaded image.
In the image to the right, the texture being painted is mapped to the "Normal" attribute,
and is called "bump mapping", where the grayscale image is used to make the flat surface appear bumpy.
See Texture Mapping Output for more information on bump mapping.


Saving
======

If the header menu item Image has an asterisk next to it
means that the image has been changed, but not saved.
Use the :menuselection:`Image --> Save Image`
option to save your work with a different name or overwrite the original image.

.. note:: UV Textures

   Since images used as UV textures are functionally different from other images,
   you should keep them in a directory separate from other images.

The image format for saving is independent of the format for rendering.
The format for saving a UV image is selected in the header of the File Browser,
and defaults to ``PNG`` (``.png``).

If Packing is enabled in the File Browser's header, or if you manually :menuselection:`Image --> Pack Image`,
saving your images to a separate file is not necessary.


Using an External Image Editor
==============================

If you use an external program to edit your UV texture, you must:

#. Run that paint program (GIMP, Krita, etc.).
#. Load the image or create a new one.
#. Change the image.
#. And re-save it within that program.
#. Back in Blender, you reload the image in the Image Editor.

You want to use an external program if you have teams of people using different programs
that are developing the UV textures, or if you want to apply any special effects
that Texture Paint does not feature, or if you are much more familiar with
your favorite paint program.


Known Limitations
=================

UV Overlap
----------

In general overlapping UVs are not supported (as with texture baking).

However, this is only a problem when a single brush stroke paints onto multiple faces
that share a texture.


Perspective View & Faces Behind the View
----------------------------------------

When painting onto a face which is partially behind the view (in perspective mode),
the face cannot be painted on.
To avoid this, zoom out or use an orthographic viewport.


Perspective View & Low Poly
---------------------------

When painting onto a face in perspective mode onto a low-poly object with
normals pointing away from the view, painting may fail; to workaround disable
the :ref:`Normal Falloff <bpy.types.ImagePaint.use_normal_falloff>` option in the stroke settings.

Typically this happens when painting onto the side of a cube
(see `Blender bug #34665 <https://projects.blender.org/blender/blender/issues/34665>`__).


## Tools


*******************
Texture Paint Tools
*******************

Draw
   The normal brush, paints a swath of color.

Soften
   Uses a "blur effect" to soften or sharpen the image.

   Direction
      Soften
         Is used to paint a blur effect.

         Kernel Radius (2D only)
            Blur radius in pixels.
      Sharpen
         The Sharpen tool enhances the contrast of the image as you paint over it.

         Sharp Threshold
            The Threshold will only apply sharpening to only those pixels that
            differ more than the threshold value from their surrounding pixels.
         Kernel Radius (2D only)
            The kernel size controls how big an area the tool searches over is while calculating that difference.
   Blur Mode
      The blur kernel type controls how neighboring pixels are weighted when calculating the blur effect.

      :Gaussian: Gaussian will sample the pixels near the center of the brush most.
      :Box: Box samples all surrounding pixels equally.

Smear
   When you click, takes the colors under the cursor, and blends them in the direction you move the mouse.
   Similar to the "smudge" tool of *Gimp*.

Clone
   Copies the colors from the specified image (or location of the same image) to the active image.

   In 3D projective painting the clone cursor can be set with :kbd:`Ctrl-LMB`.
   In 2D painting the clone can be moved dragging it with :kbd:`RMB`.

   Clone from Paint Slot (3D projective only)
      Use another image as clone source, instead of using the 3D cursor position as the source in the same image.

      Source Clone Slot
         This allows you to select an image as a clone source.

   Image (2D only)
      Image used as a clone source.
   Alpha (2D only)
      Opacity of the clone image display.

Fill
   It can be used to fill large areas of the image with the brush color.
   The tool fills adjacent pixels that have a color value similar to the pixel you clicked on.

   Fill Threshold (2D only)
      Determines how much the color must be similar to the color of pixel you click to be filled.
      A low *Threshold* only fills very similar in color pixels.
      A higher *Threshold* fills pixels within a broader range of color.

   The *Gradient* type of the Color Picker allows the use of a gradient to fill the image.

   To apply the gradient with the *Fill* brush click :kbd:`LMB` and drag to define
   the gradient line, or radius if a radial gradient is used (depending on the *Gradient Fill Mode*).

   Gradient Fill Mode
      Linear, Radial

   .. note:: Overrides

      For projective texturing it will bypass some options for projective painting to paint the model.
      This means that occluded, backfacing and normal culled faces will always get filled,
      regardless of whether the options are activated
      in the :doc:`External </sculpt_paint/texture_paint/tool_settings/options>` panel.

Mask
   This brush paints gray-scale values on the mask texture
   specified in the :doc:`Mask panel </sculpt_paint/texture_paint/tool_settings/mask>`.
   Any masked surfaces will not be affected by other paint brushes, similar to
   :doc:`sculpt mode masking </sculpt_paint/sculpting/introduction/visibility_masking_face_sets>`.

   Mask Value
      Mask weight, a value of zero means not masked, while one is completely masked.
      Hold :kbd:`Ctrl` to invert the painted mask value.

   .. tip::

      A simpler alternative is to use the face selection mask.
      See :ref:`Face Selection Masking <bpy.types.Mesh.use_paint_mask>` for details.


## Brush Settings


**************
Brush Settings
**************

.. figure:: /images/sculpt-paint_texture-paint_tool-settings_brush-settings_popover.png
   :align: right

   Brush settings panel.

Information on brush settings for every mode can be found in these pages:

:doc:`Brush </sculpt_paint/brush/brush_settings>`
   General and advanced settings.

:doc:`Texture </sculpt_paint/brush/texture>`
   Color and mask texture settings.

:doc:`Stroke </sculpt_paint/brush/stroke>`
   Stroke methods and settings.

:doc:`Falloff </sculpt_paint/brush/falloff>`
   Falloff curves and settings.

:doc:`Cursor </sculpt_paint/brush/cursor>`
   Cursor and appearance settings.

.. toctree::
   :hidden:

   Texture </sculpt_paint/brush/texture.rst>
   Stroke </sculpt_paint/brush/stroke.rst>
   Falloff </sculpt_paint/brush/falloff.rst>
   Cursor </sculpt_paint/brush/cursor.rst>


## Index


#################
  Tool Settings
#################

.. toctree::
   :maxdepth: 2

   texture_slots.rst
   /sculpt_paint/brush/brush.rst
   brush_settings.rst
   mask.rst
   symmetry.rst
   options.rst
   tiling.rst


## Mask


****
Mask
****

.. figure:: /images/sculpt-paint_texture-paint_tool-settings_mask_panel.png
   :align: right

   Mask settings.


.. _bpy.types.ImagePaint.stencil:

Stencil Mask
============

Specify an additional image texture that defines masked surfaces.
Masked surfaces can be defined with the Mask brush
and will not be affected by painting.

The mask can be deactivated by the checkbox in the header.

Stencil Image
   Image used as a mask. See :ref:`ui-data-block`.
UV Layer
   Allows you to select the UV layer for the mask image.
Display Color
   Mask color in the viewport. See :ref:`ui-color-picker`.

   Invert Stencil (black/white icon)
      Inverts the mask.


.. _bpy.types.Paint.use_cavity:

Cavity Mask
===========

Cavity masking means that the brush will be masked if there is a cavity or a hill
on the mesh surface depending on the mesh options. The cavity algorithm is vertex-based.


## Options

.. _bpy.types.ImagePaint.dither:
.. _bpy.types.ImagePaint.use_occlude:
.. _bpy.types.ImagePaint.use_backface_culling:

*******
Options
*******

Bleed
   Seam Bleed extends the paint beyond UV island bounds to avoid visual artifacts
   (like bleed for baking).
Dither
   Amount of dithering when painting on 8-bit images.
Occlude
   With Geometry occlusion active only exposed (not hidden by other mesh parts) pixels are affected.
   This also allows for 3D stencils to be used to mask out areas of the surface too.
Backface Culling
   With backface culling enabled you can only paint on the front side of faces.

.. seealso::

   See the :ref:`Brush Display <sculpt-paint-brush-display>` options.


.. _bpy.types.ImagePaint.screen_grab_size:
.. _bpy.ops.image.project:

External
========

Screen Grab Size
   Size of the captured image for reprojecting.
Quick Edit
   Edit a snapshot of the viewport in an external image editor.
Apply
   Project edited image back onto the object.
Apply Camera Image
   Project an edited render from the active camera back onto the object.


## Symmetry


********
Symmetry
********

.. reference::

   :Mode:      Texture Paint Mode
   :Tool:      :menuselection:`Toolbar --> Tool --> Symmetry`

Mirror
   Mirror the brush strokes across the selected local axes.
   Note that if you want to alter the directions the axes point in,
   you must rotate the model in Edit Mode and not in Object Mode.


## Texture Slots

.. _bpy.types.ImagePaint.mode:
.. _bpy.types.ImagePaint.interpolation:

*************
Texture Slots
*************

.. figure:: /images/sculpt-paint_texture-paint_tool-settings_texture-slots_panel.png
   :align: right

   Texture Slots settings.

The combination of images associated with UV maps is called "slots".

Selecting a *Paint Slots* or *Canvas Image*
will also display the corresponding image in the Image Editor.

Mode
   The slot system includes two painting modes:

   Material
      This mode tries to detect the slots from the materials of the mesh.

      For the Cycles renderer, all textures (*Image Texture* node) in the material's node tree
      are added in the slots tab.

      Active Paint Texture Index
         A :ref:`List view <ui-list-view>` of slots.
         Activate a certain slot to use it for painting by :kbd:`LMB` click on it.

   Single Image
      You can just select an existing image and painting will use the active UV layer for painting.

      Image
         Allows you to select the image used as a canvas.

         New
            Create a new image.
      UV Map
         Allows you to select the UV layer for painting.
         (Same as the currently active UV map in the mesh's *UV Maps* panel.)
      Texture Filter Type
         Set the interpolation mode of the texture. This can be Linear or Closest.

Save All Images
   Repack (or save if external file) all edited images.
   Same as in the :doc:`Image Editor </editors/image/introduction>`.

.. _bpy.ops.paint.add_simple_uvs:

Add Simple UVs
   The *Add Simple UVs* does a simple cube unwrap followed by a pack operation.
   It's still recommended to make a custom unwrap.

   This operator is available when the object does not already have a UV Map.


## Tiling

.. _bpy.types.Paint.tile:

******
Tiling
******

.. reference::

   :Editor:    Image Editor
   :Mode:      Paint Mode
   :Menu:      :menuselection:`Sidebar --> Tools --> Tiling`

Wraps the stroke to the other side of the image as your brush moves off the opposite side of the canvas.
Very handy for making seamless textures.

X
   left/right
Y
   top/bottom


## Editing


*******
Editing
*******

.. _bpy.ops.paint.vertex_color_smooth:

Smooth Vertex Colors
====================

.. reference::

   :Mode:      Vertex Paint Mode
   :Menu:      :menuselection:`Paint --> Smooth Vertex Colors`

Smooth colors across vertices.


.. _bpy.ops.paint.vertex_color_dirt:

Dirty Vertex Colors
===================

.. reference::

   :Mode:      Vertex Paint Mode
   :Menu:      :menuselection:`Paint --> Dirty Vertex Colors`

Generate a dirt map gradient based on cavity.

Blur Strength
   Blur strength per iteration.
Blur Iterations
   Number of times to blur the colors (higher blurs more).
Highlight Angle
   Clamps the angle for convex areas of the mesh.
   Lower values increase the contrast but can result in clamping.
   90 means flat, 180 means infinitely pointed.
Dirt Angle
   Clamps the angle for concave areas of the mesh.
   Higher values increase the contrast but can result in clamping.
   90 means flat, 0 means infinitely deep.
Dirt Only
   When active it won't calculate cleans for convex areas.
Normalize
   Choose optimal contrast by effectively lowering
   *Highlight Angle* and increasing *Dirt Angle* automatically.
   Disabling *Normalize* allows getting consistent results across multiple objects.


.. _bpy.ops.paint.vertex_color_from_weight:

Vertex Color from Weight
========================

.. reference::

   :Mode:      Vertex Paint Mode
   :Menu:      :menuselection:`Paint --> Vertex Color from Weight`

Converts the active weight into grayscale colors.


.. _bpy.ops.paint.vertex_color_invert:

Invert
======

.. reference::

   :Mode:      Vertex Paint Mode
   :Menu:      :menuselection:`Paint --> Invert`

Invert RGB values.


.. _bpy.ops.paint.vertex_color_levels:

Levels
======

.. reference::

   :Mode:      Vertex Paint Mode
   :Menu:      :menuselection:`Paint --> Levels`

Adjust the levels of the selected vertices.


.. _bpy.ops.paint.vertex_color_hsv:

Hue/Saturation/Value
====================

.. reference::

   :Mode:      Vertex Paint Mode
   :Menu:      :menuselection:`Paint --> Hue/Saturation/Value`

Adjust the HSV values of the selected vertices.


.. _bpy.ops.paint.vertex_color_brightness_contrast:

Brightness/Contrast
===================

.. reference::

   :Mode:      Vertex Paint Mode
   :Menu:      :menuselection:`Paint --> Brightness/Contrast`

Adjust the brightness/contrast of the selected vertices.


.. _bpy.ops.paint.vertex_color_set:

Set Vertex Colors
=================

.. reference::

   :Mode:      Vertex Paint Mode
   :Menu:      :menuselection:`Paint --> Set Vertex Colors`
   :Shortcut:  :kbd:`Ctrl-X`

Fill the active Color Attribute with the current paint color.

Affect Alpha
   Set color completely opaque instead of reusing existing alpha.


.. _bpy.ops.paint.sample_color:

Sample Color
============

.. reference::

   :Mode:      Vertex Paint Mode
   :Menu:      :menuselection:`Paint --> Sample Color`
   :Shortcut:  :kbd:`Shift-X`


Adjust the brush color of the :doc:`Draw </sculpt_paint/vertex_paint/tools>`
tool to the color under the mouse cursor.


## Index

.. _painting-vertex-index:
.. _bpy.types.VertexPaint:
.. _bpy.types.VertexColors:

################
  Vertex Paint
################

.. toctree::
   :maxdepth: 2

   introduction.rst
   tools.rst
   tool_settings/index.rst
   editing.rst


## Introduction


************
Introduction
************

Vertex Painting is a simple way of painting color onto an object, by directly
manipulating the color of vertices, rather than textures, and is fairly straightforward.
Vertex Painting stores the color information as a
:ref:`Color Attribute <modeling-meshes-properties-object_data-color-attributes>`
which can be used by different render engines.

Color attribute's can be managed in the pallette pop-over in the middle of the header.

.. figure:: /images/sculpt-paint_vertex-paint_introduction_mode-menu.png

   Vertex Painting Mode.

When a vertex is painted, the color of the vertex is modified according to
the settings of the brush. The color of all visible planes and edges attached to
the vertex are then modified with a gradient to the color of the other connected vertices.
Note that the color of occluded faces is not modified.

.. seealso::

   :doc:`Dynamic Paint </physics/dynamic_paint/introduction>`
   can create Color Attribute information while using physics or animation.


Viewing Color Attributes
========================

Color Attributes can be used in a material node tree using the :doc:`/render/shader_nodes/input/vertex_color`.

Color Attributes can be viewed in the 3D viewport using the Workbench render engine.
To use such feature, set the 3D Viewport to :ref:`Solid Shading <3dview-shading-solid>`
and select the *Attribute* Color option.


## Tools


******************
Vertex Paint Tools
******************

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

:ref:`Annotate <tool-annotate-freehand>`
   Draw free-hand annotation.

   :ref:`Annotate Line <tool-annotate-line>`
      Draw straight line annotation.
   :ref:`Annotate Polygon <tool-annotate-polygon>`
      Draw a polygon annotation.
   :ref:`Annotate Eraser <tool-annotate-eraser>`
      Erase previous drawn annotations.


## Brush Settings


**************
Brush Settings
**************

.. figure:: /images/sculpt-paint_vertex-paint_tool-settings_brush-settings_tab.png
   :align: right

   Brush settings panel.

Information on brush settings for every mode can be found in these pages:

:doc:`Brush </sculpt_paint/brush/brush_settings>`
   General and advanced settings.

:doc:`Texture </sculpt_paint/brush/texture>`
   Color and mask texture settings.

:doc:`Stroke </sculpt_paint/brush/stroke>`
   Stroke methods and settings.

:doc:`Falloff </sculpt_paint/brush/falloff>`
   Falloff curves and settings.

:doc:`Cursor </sculpt_paint/brush/cursor>`
   Cursor and appearance settings.

.. toctree::
   :hidden:

   Texture </sculpt_paint/brush/texture.rst>
   Stroke </sculpt_paint/brush/stroke.rst>
   Falloff </sculpt_paint/brush/falloff.rst>
   Cursor </sculpt_paint/brush/cursor.rst>


## Index


#################
  Tool Settings
#################

.. toctree::
   :maxdepth: 2

   /sculpt_paint/brush/brush.rst
   brush_settings.rst
   symmetry.rst


## Symmetry


********
Symmetry
********

.. reference::

   :Mode:      Vertex Paint Mode
   :Tool:      :menuselection:`Toolbar --> Tool --> Symmetry`

Mirror
   Mirror the brush strokes across the selected local axes.
   Note that if you want to alter the directions the axes point in,
   you must rotate the model in Edit Mode and not in Object Mode.


## Editing


*******
Editing
*******

.. reference::

   :Mode:      Edit Mode and Weight Paint Mode
   :Menu:      :menuselection:`Weights`

.. figure:: /images/sculpt-paint_weight-paint_editing_panel.png
   :align: right

   Weight Paint Tools.

Blender provides a set of helper tools for Weight Painting.


.. _sculpt-paint_weight-paint_editing_subset:

.. rubric:: The Subset Option

Some of the tools also provide a Subset filter to restrict their functionality to only specific vertex groups
(in the :ref:`bpy.ops.screen.redo_last` panel, displayed after the tool is called)
with following options:

- Active Group
- Selected Pose Bones
- Deform Pose Bones
- All Groups

All tools also work with Vertex Selection Masking and Face Selection Masking.
In these modes the tools operate only on selected vertices or faces.


.. _bpy.ops.paint.weight_from_bones:

Assign from Bone Envelopes
==========================

Apply the envelope weight of the selected bone(s) to the selected vertex group.


Assign Automatic from Bone
==========================

Apply from the selected bone(s) to the vertex group the same "auto-weighting" methods
as available in the Parent armature menu.


.. _bpy.ops.object.vertex_group_normalize_all:

Normalize All
=============

For each vertex, this tool makes sure that the sum of the weights across
all vertex groups is equal to 1. This tool normalizes all of the vertex groups,
except for locked groups, which keep their weight values untouched.

Lock Active
   Keep the values of the active group while normalizing all the others.


.. _bpy.ops.object.vertex_group_normalize:

Normalize
=========

This tool only works on the active vertex group. All vertices keep their relative weights,
but the entire set of weights is scaled up such that the highest weight value is 1.0.

.. figure:: /images/sculpt-paint_weight-paint_editing_normalize-example.png

   Normalize example.


.. _bpy.ops.object.vertex_group_mirror:

Mirror
======

The *Mirror Vertex Group* tool mirrors the weights
from one side of a perfectly symmetrical mesh to the opposite side.
Those vertices that have no corresponding vertex on the other side will not be affected.
But note, the weights are not transferred to the corresponding opposite bone weight group.

.. note::

   Mirroring only works when the object's rest pose is perfectly symmetrical across the X axis.

.. figure:: /images/sculpt-paint_weight-paint_editing_mirror-example.png

   Mirror example.

Mirror Weights
   With this option checked, every selected vertex receives
   the weight information of its symmetrical counterpart.
   If both vertices are selected, it will be a weight information exchange;
   if only one is selected, information from the unselected will overwrite the selected one.
   Information on weight is passed for the active group only,
   unless *All Groups* is checked, in which case it is passed for all groups.
Flip Group Names
   Works with selected vertices that belong to vertex groups with "symmetrical names"
   (with components like "L", "R", "right", "left").
   All selected vertices that belong to the active group, or to the symmetrical of the active group,
   will have their assignation to that group replaced by an assignation to the symmetrical one;
   however, its weight will be preserved.
   If *All Groups* is checked, all assignations to these kind of groups
   will be replaced by the symmetrical counterpart, also keeping the old weights.
All Groups
   Operate on all vertex groups, instead of the active one.
Topology Mirror
   Mirror for meshes which are not fully symmetric (approximate mirror).
   See :ref:`here <bpy.types.Mesh.use_mirror_topology>` for more information.

.. tip:: Mirror to Opposite Bone

   If you want to create a mirrored weight group for the opposite bone
   (of a symmetric character), then you can do this:

   #. Delete the target vertex group (where the mirrored weights will be placed).
   #. Create a copy of the source bone vertex group
      (the group containing the weights which you want to copy).
   #. Rename the new vertex group to the name of the target vertex group
      (the group you deleted above).
   #. Select the target vertex group and call the Mirror tool
      (use only the Mirror weights option and optionally *Topology Mirror* if your mesh is not symmetric).


.. _bpy.ops.object.vertex_group_invert:

Invert
======

Replaces each Weight of the selected weight group by × -1.0 weight.

Examples:

- Original 1.0 converts to 0.0
- Original 0.5 remains 0.5
- Original 0.0 converts to 1.0

.. figure:: /images/sculpt-paint_weight-paint_editing_invert-example.png

   Invert.

Subset
   Restrict the tool to a subset.
   See above :ref:`The Subset Option <sculpt-paint_weight-paint_editing_subset>` about how subsets are defined.
Add Weights
   Add vertices that have no weight before inverting (these weights will all be set to 1.0).
Remove Weights
   Remove vertices from the vertex group if they are 0.0 after inverting.

.. note::

   Locked vertex groups are not affected.


.. _bpy.ops.object.vertex_group_clean:

Clean
=====

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
   Ensure that the *Clean* tool will not create completely unreferenced vertices
   (vertices which are not assigned to any vertex group), so each vertex will
   keep at least one weight, even if it is below the limit value!


.. _bpy.ops.object.vertex_group_quantize:

Quantize
========

This operator uses a process known as `Quantization <https://en.wikipedia.org/wiki/Quantization>`__
which takes the input weights and clamps each weight to a number of steps between (0 - 1),
so there is no longer a smooth gradient between values.

.. figure:: /images/sculpt-paint_weight-paint_editing_quantize-example.png

   Quantize example (Steps = 2).

Steps
   The number of steps between 0 and 1 to quantize the weights into.
   For example 5 would allow the following weights ``[0.0, 0.2, 0.4, 0.6, 0.8, 1.0]``.


.. _bpy.ops.object.vertex_group_levels:

Levels
======

Adds an offset and a scale to all weights of the selected weight groups.
with this tool you can raise or lower the overall "heat" of the weight group.

.. note::

   No weight will ever be set to values above 1.0 or below 0.0 regardless of the settings.

.. figure:: /images/sculpt-paint_weight-paint_editing_levels-example.png

   Levels example.

Subset
   Restrict the tool to a subset.
   See above :ref:`The Subset Option <sculpt-paint_weight-paint_editing_subset>` for how subsets are defined.
Offset
   A value from the range (-1.0 - 1.0) to be added to all weights in the vertex group.
Gain
   All weights in the Subset are multiplied with the gain.

.. note::

   Whichever *Gain* and *Offset* you choose,
   in all cases the final value of each weight will be clamped to the range
   (0.0 - 1.0). So you will never get negative weights or overheated areas
   (weight > 1.0) with this tool.


.. _bpy.ops.object.vertex_group_smooth:

Smooth
======

.. tip::

   The Smooth tool only works when "Vertex selection masking for painting" is enabled.
   Otherwise the tool button is grayed out.

Blends the weights of selected vertices with adjacent unselected vertices.
This tool only works in vertex select mode.

.. figure:: /images/sculpt-paint_weight-paint_editing_smooth-example-1.png

To understand what the tool really does, let us take a look at a simple example.
The selected vertex is connected to four adjacent vertices
(marked with a gray circle in the image). All adjacent vertices are unselected.
Now the tool calculates the average weight of all connected **and** unselected vertices.
In the example this is:

:math:`(1 + 0 + 0 + 0) / 4 = 0.25`

This value is multiplied by the factor given in the Operator options (see below).

- If the factor is 0.0 then actually nothing happens at all and the vertex just keeps its value.
- If the factor is 1.0 then the calculated average weight is taken (0.25 here).
- Dragging the factor from 0 to 1 gradually changes from the old value to the calculated average.

.. figure:: /images/sculpt-paint_weight-paint_editing_smooth-example-2.png

Now let us see what happens when we select all
but one of the neighbors of the selected vertex as well.
Again all connected and unselected vertices are marked with a gray circle.
When we call the Smooth tool now and set the Factor to 1.0,
then we see different results for each of the selected vertices:

- The top-most and bottom-most selected vertices:

  are surrounded by three unselected vertices, with an average weight of :math:`(1 + 0 + 0) / 3 = 0.333`
  So their color has changed to light green.

- The middle vertex:

  is connected to one unselected vertex with ``weight = 1``.
  So the average weight is 1.0 in this case, thus the selected vertex has changed to red.

- The right vertex:

  is surrounded by three unselected vertices with average weight = :math:`(0 + 0 + 0) / 3 = 0.0`
  So the average weight is 0, thus the selected vertex has not changed at all
  (it was already blue before Smooth was applied).

.. figure:: /images/sculpt-paint_weight-paint_editing_smooth-example-3.png

Finally let us look at a practical example.
The middle edge loop has been selected
and it will be used for blending the left side to the right side of the area.

- All selected vertices have two unselected adjacent vertices.
- The average weight of the unselected vertices is :math:`(1 + 0) / 2 = 0.5`
- Thus when the *Factor* is set to 1.0 then the edge loop turns to
  green and finally does blend the cold side (right) to the hot side (left).

Factor
   The effective amount of blending.
   When Factor is set to 0.0 then the `Smooth`_ tool does not do anything.
   For Factor > 0 the weights of the affected vertices gradually shift from their original value
   towards the average weight of all connected **and** unselected vertices (see examples above).
Iterations
   Number of times to repeat the smoothing operation.
Expand/Contract
   Positive values expand the selection to neighboring vertices while contract limits to the selection.
Source
   The vertices to mix with.

   :All: Smoothing will smooth both selected and deselected vertices.
   :Only Selected: Smoothing will only smooth with selected vertices.
   :Only Deselected: Smoothing will only smooth with deselected vertices.


Transfer Weights
================

Copy weights from other objects to the vertex groups of the active object.

By default this tool copies only the active (selected) vertex group of the source object
to the active vertex group of target object or creates a new one if the group does not exist.
However, you can change the tool's behavior in the :ref:`bpy.ops.screen.redo_last` panel.

For example, to transfer all existing vertex groups from the source objects to the target,
change the *Source Layers Selection* option to *By Name*.

.. note::

   This tool uses the generic "data transfer", but transfers from all selected objects to active one.
   Please refer to the :doc:`Data Transfer </scene_layout/object/editing/link_transfer/transfer_mesh_data>`
   docs for options details and explanations.


Prepare the Copy
----------------

You first select all source objects, and finally the target object
(the target object must be the active object).

It is important that the source objects and the target object are at the same location.
If they are placed side-by-side, then the weight transfer will not work. (See the *Vertex Mapping* option.)
You can place the objects on different layers,
but you have to ensure that all objects are visible when you call the tool.

Now ensure that the target object is in Weight Paint Mode.
Open the Toolbar and call the *Transfer Weights* tool in the *Weight Tools* panel.


Adjust Last Operation Panel Confusion
-------------------------------------

You may notice that the :ref:`bpy.ops.screen.redo_last` panel stays available
after the weight transfer is done. The panel only disappears
when you call another Operator that has its own :ref:`bpy.ops.screen.redo_last` panel.
This can lead to confusion when you use Transfer weights repeatedly after you changed your vertex groups.
If you then use the still-visible :ref:`bpy.ops.screen.redo_last` panel,
then Blender will reset your work to its state right before you initially called the *Transfer Weights* tool.

So when you want to call the *Transfer Weights* tool again after you made some changes to your
vertex groups, then **always** use the *Transfer Weights* button,
even if the :ref:`bpy.ops.screen.redo_last` panel is still available.
Unless you really want to reset your changes to the initial call of the tool.


.. _bpy.ops.object.vertex_group_limit_total:

Limit Total
===========

Reduce the number of weight groups per vertex to the specified Limit.
The tool removes lowest weights first until the limit is reached.

.. hint::

   The tool can only work reasonably when more than one weight group is selected.

Subset
   Restrict the tool to a subset.
   See above :ref:`The Subset Option <sculpt-paint_weight-paint_editing_subset>` for how subsets are defined.
Limit
   Maximum number of weights allowed on each vertex.


.. _bpy.ops.paint.weight_set:

Set Weight
==========

.. reference::

   :Mode:      Weight Paint Mode
   :Menu:      :menuselection:`Weight --> Set Weight`
   :Shortcut:  :kbd:`Ctrl-X`

Fill the active vertex group with the current paint weight.


Sample Weight
=============

.. reference::

   :Mode:      Weight Paint Mode
   :Menu:      :menuselection:`Weight --> Sample Weight`
   :Shortcut:  :kbd:`Shift-X`

Adjust the Weight of the :doc:`Draw </sculpt_paint/weight_paint/tools>`
tool to the weight of the vertex under the mouse cursor.


.. _bpy.ops.paint.weight_sample_group:

Sample Group
============

.. reference::

   :Mode:      Weight Paint Mode
   :Menu:      :menuselection:`Weight --> Sample Group`
   :Shortcut:  :kbd:`Shift-Ctrl-X`

Select one of the vertex groups available under current mouse position.


.. _bpy.ops.paint.weight_gradient:

Gradient (Linear)
=================

.. reference::

   :Mode:      Weight Paint Mode
   :Menu:      :menuselection:`Weights --> Gradient (Linear)`

Applies a linear weight gradient;
this is useful at times when painting gradual changes in weight becomes difficult.
Blends the weights of selected vertices with unselected vertices.

.. figure:: /images/sculpt-paint_weight-paint_tools_gradient.png

   Example of the Gradient tool being used with selected vertices.

Weight
   The gradient starts at the current selected weight value, blending out to nothing.
Strength
   Lower values can be used so the gradient mixes in with the existing weights (just like with the brush).
Type
   The shape of the gradient.

   :Linear: Create gradient that forms a straight line.
   :Radial: Create gradient that forms a circle.


Gradient (Radial)
=================

.. reference::

   :Mode:      Weight Paint Mode
   :Menu:      :menuselection:`Weights --> Gradient (Radial)`
   :Shortcut:  :kbd:`Ctrl-Alt-LMB`

Applies a radial weight gradient;
this is useful at times when painting gradual changes in weight becomes difficult.
Blends the weights of selected vertices with unselected vertices.

Weight
   The gradient starts at the current selected weight value, blending out to nothing.
Strength
   Lower values can be used so the gradient mixes in with the existing weights (just like with the brush).
Type
   The shape of the gradient.

   :Linear: Create gradient that forms a straight line.
   :Radial: Create gradient that forms a circle.


.. _bpy.ops.object.vertex_group_lock:

Locks
=====

.. reference::

   :Mode:      Edit Mode and Weight Paint Mode
   :Menu:      :menuselection:`Weights --> Locks`
   :Shortcut:  :kbd:`K`

Vertex groups can be locked to prevent undesired edits to a particular vertex group.

.. tip::

   Bones that belong to a locked vertex group are displayed in red the 3D Viewport.

Lock All
   Locks all vertex groups.
Lock Selected
   Locks selected vertex groups.
Lock Unselected
   Locks unselected vertex groups.
Lock Only Selected
   Lock selected and unlock selected vertex groups.
Lock Only Unselected
   Unlock selected and lock unselected vertex groups.

Unlock All
   Unlocks all vertex groups.
Unlock Selected
   Unlocks selected vertex groups.
Unlock Unselected
   Unlocks Unselected vertex groups.

Invert Locks
   Inverts the locks on all vertex groups.


## Index

.. _painting-weight-index:

################
  Weight Paint
################

.. toctree::
   :maxdepth: 2

   introduction.rst
   tools.rst
   tool_settings/index.rst
   usage.rst
   editing.rst


## Introduction


************
Introduction
************

Vertex Groups can potentially have a very large number of associated vertices
and thus a large number of weights (one weight per assigned vertex).
*Weight Painting* is a method to maintain large amounts of weight information
in a very intuitive way.

It is primarily used for rigging meshes, where the vertex groups are used to
define the relative bone influences on the mesh. But we use it also for
controlling particle emission, hair density, many modifiers, shape keys, etc.

.. figure:: /images/sculpt-paint_weight-paint_introduction_example.jpg

   Vertex group in Weight Paint Mode.

You can enter Weight Paint Mode from the Mode selector :kbd:`Ctrl-Tab`.
The selected mesh object is displayed slightly shaded with a rainbow color spectrum.
The color visualizes the weights associated to each vertex in the active vertex group.
By default *blue* means unweighted and *red* means fully weighted.

You can assign weights to the vertices of the object by painting on it with weight brushes.
Starting to paint on a mesh automatically adds weights to the active vertex group
(a new vertex group is created if needed).

Vertex Groups can be managed in the pallette pop-over in the middle of the header.


The Weighting Color Code
========================

Weights are visualized by a gradient using a cold/hot color system,
such that areas of low value (with weights close to 0.0) are displayed as blue (cold)
and areas of high value (with weights close to 1.0) are displayed as red (hot).
And all in-between values are displayed as rainbow colors (blue, green, yellow, orange, red).

.. figure:: /images/sculpt-paint_weight-paint_introduction_color-code.png

   The color spectrum and their respective weights.

In addition to the above described color code, Blender has a special visual notation
(as an option) for unreferenced vertices: They are displayed as black.
Thus you can see the referenced areas (displayed as cold/hot colors) and
the unreferenced areas (in black) at the same time.
This is most practicable when you look for weighting errors.
See :doc:`/sculpt_paint/weight_paint/tool_settings/options`.

.. figure:: /images/sculpt-paint_weight-paint_introduction_color-code-black.png

   Unreferenced vertices example.

.. note::

   You can customize the colors in the weight gradient by enabling
   :ref:`Custom Weight Paint Range <bpy.types.PreferencesView.use_weight_color_range>` in the *Editing* tab
   of the *Preferences*.


Normalized Weight Workflow
==========================

In order to be used for things like deformation, weights usually have to be normalized,
so that all deforming weights assigned to a single vertex add up to 1.
The *Armature* modifier in Blender does this automatically, so it is technically not necessary to
ensure that weights are normalized at the painting stage.

However, while more complicated, working with normalized weights has certain advantages,
because it allows use of certain tools designed for them, and because when weights are normalized,
understanding the final influence of the current group does not require knowing weights in
other groups on the same vertex.

These tools are provided to aid working with normalized weights:

Normalize All
   In order to start working with normalized weights it is first necessary to normalize the existing weights.
   The :ref:`Normalize All <bpy.ops.object.vertex_group_normalize_all>` tool can be used for that.
   Make sure to select the right mode and disable *Lock Active*.

Auto Normalize
   Once the weights are initially normalized,
   the :ref:`Auto Normalize <bpy.types.ToolSettings.use_auto_normalize>` option
   can be enabled to automatically maintain normalization as you paint.
   This also tells certain tools that the weights are supposed to be already normalized.

Vertex group locking
   Any vertex group can be locked to prevent changes to it. This can be done via
   the lock icon in the vertex group list, or using bone selection and
   the :ref:`locks pie menu <bpy.ops.object.vertex_group_lock>`.

   This setting prevents accidental edits to groups. However,
   since it is also respected by *Auto Normalize*, in the normalized weight workflow
   it has a more significant meaning of locking the current influence of chosen bones,
   so that when you paint other bones, the weight is redistributed only between the unlocked groups.

   In locations affected by multiple bones, this allows more precise tweaking and re-balancing of
   weights by temporarily focusing on a subset of bones. This can also be aided by
   the :ref:`Lock Relative <bpy.types.ToolSettings.use_auto_normalize>` option, which displays unlocked groups as
   though re-normalized with the locked groups deleted, thus making it appear as if the locked groups did not even
   exist.

Multi-Paint
   Finally, the :ref:`Multi-Paint <bpy.types.ToolSettings.use_auto_normalize>` option allows treating
   multiple selected bones as if they were one bone, so that the painting operations change
   the combined weight, preserving the ratio within the group. Combined with locking,
   this allows balancing between one set of bones versus the rest, excluding a third set
   that has its influence not affected in any way due to locks.

   Technically, this option does not require the normalized workflow, but since non-normalized
   weights can add to more than 1, the weight display behaves best with *Auto Normalize* enabled.

.. tip::

   For example, when dealing with a bone loop, e.g. mouth or an eye, selecting the loop with
   *Multi-Paint* exposes the falloff between the loop as a whole and surrounding bones,
   while locking the surrounding bones and using *Lock Relative* displays the falloff between bones
   within the loop. Thus the complex two-dimensional falloff of each bone can be viewed and
   edited as two independent one-dimensional gradients.


## Tools


******************
Weight Paint Tools
******************

Draw
   Paints a specified weight over the object.

   Blend
      The brush :term:`Blend Modes` defines in which way the weight value is
      applied to the vertex group while painting.

      Mix
         In this Blending mode the Weight value defines the *target weight*
         that will eventually be reached when you paint long enough on the same
         location of the mesh. And the strength determines how many strokes
         you need to place at the target weight. Note that for strength = 1.0
         the target weight is painted immediately and for Weight = 0.0 the brush just does nothing.
      Add
         In this Blending mode the specified weight value is *added* to the vertex weights.
         The strength determines which fraction of the weight gets added per stroke.
         However, the brush will not paint weight values above 1.0.
      Subtract
         In this Blending mode the specified weight value is *subtracted* from the vertex weights.
         The strength determines which fraction of the weight gets removed per stroke.
         However, the brush will not paint weight values below 0.0.
      Lighten
         In this Blending mode the specified weight value is interpreted as the target weight.
         Very similar to the Mix Blending mode, but only weights below the target weight are affected.
         Weights above the target weight remain unchanged.
      Darken
         This Blending mode is very similar to the Lighten Blending mode.
         But only weights above the target weight are affected.
         Weights below the target weight remain unchanged.
      Multiply
         Multiplies the vertex weights with the specified weight value.
         This is somewhat like subtract, but the amount of removed weight is now
         dependent on the Weight value itself.
      Blur
         Smooths out the weighting of adjacent vertices. In this mode the Weight
         Value is ignored. The strength defines how much the smoothing is applied.

Blur
   Smooths out the weighting of adjacent vertices. In this mode the Weight
   Value is ignored. The strength defines how much the smoothing is applied.

Average
   Smooths weights by painting the average resulting weight from all weights under the brush.

Smear
   Smudges weights by grabbing the weights under the brush and "dragging" them.
   This can be imagined as a finger painting tool.

Gradient
   Applies a linear/radial weight gradient;
   this is useful at times when painting gradual changes in weight becomes difficult.
   Blends the weights of selected vertices with unselected vertices.

   .. figure:: /images/sculpt-paint_weight-paint_tools_gradient.png

      Example of the Gradient tool being used with selected vertices.

   Weight
      The gradient starts at the current selected weight value, blending out to nothing.
   Strength
      Lower values can be used so the gradient mixes in with the existing weights (just like with the brush).
   Type
      The shape of the gradient.

      :Linear: Create gradient that forms a straight line. :kbd:`Shift-LMB` and drag.
      :Radial: Create gradient that forms a circle. :kbd:`Shift-Alt-LMB` and drag.

Sample
   Weights
      Sets the brush *Weight* as the weight selected under the cursor.
      The sampled weight is displayed in the tool settings.
   Vertex Group
      Displays a list of possible vertex groups to select that are under the cursor.

:ref:`Annotate <tool-annotate-freehand>`
   Draw free-hand annotation.

   :ref:`Annotate Line <tool-annotate-line>`
      Draw straight line annotation.
   :ref:`Annotate Polygon <tool-annotate-polygon>`
      Draw a polygon annotation.
   :ref:`Annotate Eraser <tool-annotate-eraser>`
      Erase previous drawn annotations.


## Usage


*******************
Using Vertex Groups
*******************

.. _weight-painting-bones:

Vertex Groups for Bones
=======================

This is one of the main uses of weight painting. While you can have Blender
generate the weights automatically (see the
:doc:`skinning section </animation/armatures/skinning/index>`),
you may want to tweak them or even create them from scratch,
especially around joints.

The process is as follows:

#. Select the armature and bring it into *Pose Mode* by pressing :kbd:`Ctrl-Tab`.
#. Make sure that :menuselection:`Edit --> Lock Object Modes` is unchecked
   in the topbar.
#. Select the mesh and bring it into *Weight Paint Mode*.
#. Make sure that *Bone Selection* is checked in the 3D Viewport's header.
#. Select a bone using :kbd:`Alt-LMB` (or :kbd:`Shift-Ctrl-LMB`).
   This will activate the bone's vertex group and display its current weights on the mesh.
#. Paint weights for the bone using :kbd:`LMB`.

.. note::

   You can only select one bone at a time in this mode.

.. tip::

   The bones are likely embedded inside the mesh, making them invisible and
   unselectable. To get around this, you can enable :ref:`In Front <bpy.types.Object.show>`
   for the armature.

If a bone doesn't have a vertex group yet when you start painting,
Blender will create one automatically.

If you have a symmetrical mesh and a symmetrical armature, you can use
:ref:`Mirror Vertex Groups <bpy.types.Mesh.use_mirror_vertex_groups>`
to automatically create vertex groups and weights for the other side.


Vertex Groups for Particles
===========================

.. figure:: /images/sculpt-paint_weight-paint_usage_particles.png
   :width: 320px

   Weight painted particle emission.

By selecting vertex groups in the :doc:`Vertex Groups </physics/particles/emitter/vertex_groups>`
panel of a :doc:`particle system </physics/particles/introduction>`'s properties,
you can have different particle densities, hair lengths etc. across different areas of the mesh.


## Brush Settings


**************
Brush Settings
**************

.. figure:: /images/sculpt-paint_weight-paint_tool-settings_brush-settings_brush-panel.png
   :align: right
   :width: 200

   Brush settings panel.

Information on brush settings for every mode can be found in these pages:

:doc:`Brush </sculpt_paint/brush/brush_settings>`
   General and advanced settings.

:doc:`Stroke </sculpt_paint/brush/stroke>`
   Stroke methods and settings.

:doc:`Falloff </sculpt_paint/brush/falloff>`
   Falloff curves and settings.

:doc:`Cursor </sculpt_paint/brush/cursor>`
   Cursor and appearance settings.

.. toctree::
   :hidden:

   Stroke </sculpt_paint/brush/stroke.rst>
   Falloff </sculpt_paint/brush/falloff.rst>
   Cursor </sculpt_paint/brush/cursor.rst>


## Index


#################
  Tool Settings
#################

.. toctree::
   :maxdepth: 2

   /sculpt_paint/brush/brush.rst
   brush_settings.rst
   symmetry.rst
   options.rst


## Options


*******
Options
*******

.. figure:: /images/sculpt-paint_weight-paint_tool-settings_options_panel.png
   :align: right

   Paint options.

The weight paint options change the overall brush behavior.

.. _bpy.types.ToolSettings.use_auto_normalize:

Auto Normalize
   Ensures that all deforming vertex groups add up to one while painting.
   When this option is turned off, then all weights of a vertex can have any value between 0 and 1.
   However, when vertex groups are used as deform groups for character animation
   then Blender always interprets the weight values relative to each other.
   That is, Blender always does a normalization over all deform bones.
   Hence in practice it is not necessary to maintain a strict normalization and
   further normalizing weights should not affect animation at all.

   This option works most intuitively when used to maintain normalization while
   painting on top of weights that are already normalized with another tool.

.. _bpy.types.ToolSettings.use_lock_relative:

Lock-Relative
   Displays bone-deforming groups as if all locked deform groups were deleted,
   and the remaining ones were re-normalized.
   This is intended for use when balancing weights within a group of bones while all other bones are locked.
   With this option you can also temporarily view non-normalized weights as if they were normalized,
   without actually changing the values.

.. _bpy.types.ToolSettings.use_multipaint:

Multi-Paint
   Paint on all selected vertex groups simultaneously, in a way that preserves their relative influence.
   This can be useful when tweaking weights in an area that is affected by more than three bones at once,
   e.g. certain areas on a character's face.

   This option is only useful in the *Armature* tab, where you can select multiple vertex groups
   by selecting multiple pose bones. Once at least two vertex groups are selected,
   viewport colors and paint logic switch to Multi-Paint mode,
   using the sum of the selected groups' weights if *Auto Normalize* is enabled,
   and the average otherwise. Any paint operations aimed at this collective weight are applied to
   individual vertex group weights in such way that their ratio stays the same.

   Since the ratio is undefined if all weights are zero, Multi-Paint cannot operate on
   vertices that do not have any weight assigned to the relevant vertex groups.
   For this reason it also does not allow reducing the weight all the way to zero.
   When used with *X Mirror*, it only guarantees completely a symmetrical result
   if weights are initially symmetrical.

   .. tip::

      While Multi-Paint cannot directly paint on zero-weight vertices,
      it is possible to use the *Smooth Weight* tool to copy a reasonable nonzero weight distribution
      from adjacent vertices without leaving Multi-Paint mode or changing bone selection.

      To do that, enable vertex selection, select target vertices, and apply one iteration of
      the tool using vertex groups from *Selected Pose Bones* with low Factor.
      After that simply paint on top to set the desired collective weight.

.. _bpy.types.VertexPaint.use_group_restrict:

Restrict
   This option limits the influence of painting to vertices (even with weight 0)
   belonging to the selected vertex group.

.. seealso::

   See the :ref:`Brush Display <sculpt-paint-brush-display>` options.


## Symmetry


********
Symmetry
********

.. reference::

   :Mode:      Vertex Paint Mode
   :Tool:      :menuselection:`Toolbar --> Tool --> Symmetry`

.. _bpy.types.Mesh.use_mirror_vertex_groups:

Mirror Vertex Groups
   Use this option for mirrored painting on groups that have symmetrical names,
   like with suffix ".R"/ ".L" or "_R" / "_L". If a group has no mirrored counterpart,
   it will paint symmetrically on the active group itself.
   You can read more about the naming convention in
   :ref:`Editing Armatures: Naming conventions <armature-editing-naming-conventions>`.
   The conventions for armatures/bones apply here as well.

Mirror X, Y, Z
   Mirror the brush strokes across the selected local axes.
   Note that if you want to alter the directions the axes point in,
   you must rotate the model in Edit Mode and not in Object Mode.

Radial X, Y, Z
   These settings allow for radial symmetry in the desired axes.
   The number determines how many times the stroke will be repeated
   within 360 degrees around the central axes.

Topology Mirror
   Use topology-based mirroring, for when both sides of a mesh have matching mirrored topology.
   See :ref:`here <bpy.types.Mesh.use_mirror_topology>` for more information.


