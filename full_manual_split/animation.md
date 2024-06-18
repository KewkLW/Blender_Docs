# Index for animation

- [Actions](#Actions)
- [Index](#Index)
- [Introduction](#Introduction)
- [Lattice](#Lattice)
- [Markers](#Markers)
- [Motion Paths](#Motion-Paths)
- [Index](#Index)
- [Introduction](#Introduction)
- [Structure](#Structure)
- [Bone Collections](#Bone-Collections)
- [Index](#Index)
- [Introduction](#Introduction)
- [Selecting](#Selecting)
- [Structure](#Structure)
- [Bone Roll](#Bone-Roll)
- [Delete](#Delete)
- [Duplicate](#Duplicate)
- [Extrude](#Extrude)
- [Fill Between Joints](#Fill-Between-Joints)
- [Index](#Index)
- [Introduction](#Introduction)
- [Naming](#Naming)
- [Parenting](#Parenting)
- [Properties](#Properties)
- [Separate Bones](#Separate-Bones)
- [Split](#Split)
- [Subdivide](#Subdivide)
- [Switch Direction](#Switch-Direction)
- [Symmetrize](#Symmetrize)
- [Transform](#Transform)
- [Bendy Bones](#Bendy-Bones)
- [Custom Properties](#Custom-Properties)
- [Deform](#Deform)
- [Display](#Display)
- [Index](#Index)
- [Inverse Kinematics](#Inverse-Kinematics)
- [Relations](#Relations)
- [Transform](#Transform)
- [Index](#Index)
- [Toolbar](#Toolbar)
- [Tool Settings](#Tool-Settings)
- [Index](#Index)
- [Introduction](#Introduction)
- [Selecting](#Selecting)
- [Tool Settings](#Tool-Settings)
- [Index](#Index)
- [Introduction](#Introduction)
- [Introduction](#Introduction)
- [Spline Ik](#Spline-Ik)
- [Apply](#Apply)
- [Clear](#Clear)
- [Copy Paste](#Copy-Paste)
- [Flip Quats](#Flip-Quats)
- [Index](#Index)
- [Introduction](#Introduction)
- [In Betweens](#In-Betweens)
- [Pose Library](#Pose-Library)
- [Propagate](#Propagate)
- [Show Hide](#Show-Hide)
- [Bone Collections](#Bone-Collections)
- [Display](#Display)
- [Index](#Index)
- [Introduction](#Introduction)
- [Index](#Index)
- [Introduction](#Introduction)
- [Parenting](#Parenting)
- [Index](#Index)
- [Introduction](#Introduction)
- [Common](#Common)
- [Header](#Header)
- [Stack](#Stack)
- [Camera Solver](#Camera-Solver)
- [Follow Track](#Follow-Track)
- [Object Solver](#Object-Solver)
- [Action](#Action)
- [Armature](#Armature)
- [Child Of](#Child-Of)
- [Floor](#Floor)
- [Follow Path](#Follow-Path)
- [Pivot](#Pivot)
- [Shrinkwrap](#Shrinkwrap)
- [Clamp To](#Clamp-To)
- [Damped Track](#Damped-Track)
- [Ik Solver](#Ik-Solver)
- [Locked Track](#Locked-Track)
- [Spline Ik](#Spline-Ik)
- [Stretch To](#Stretch-To)
- [Track To](#Track-To)
- [Copy Location](#Copy-Location)
- [Copy Rotation](#Copy-Rotation)
- [Copy Scale](#Copy-Scale)
- [Copy Transforms](#Copy-Transforms)
- [Limit Distance](#Limit-Distance)
- [Limit Location](#Limit-Location)
- [Limit Rotation](#Limit-Rotation)
- [Limit Scale](#Limit-Scale)
- [Maintain Volume](#Maintain-Volume)
- [Transformation](#Transformation)
- [Transform Cache](#Transform-Cache)
- [Drivers Panel](#Drivers-Panel)
- [Index](#Index)
- [Introduction](#Introduction)
- [Troubleshooting](#Troubleshooting)
- [Usage](#Usage)
- [Workflow Examples](#Workflow-Examples)
- [Editing](#Editing)
- [Index](#Index)
- [Introduction](#Introduction)
- [Keying Sets](#Keying-Sets)
- [Index](#Index)
- [Introduction](#Introduction)
- [Shape Keys Panel](#Shape-Keys-Panel)
- [Workflow](#Workflow)


## Actions

.. _bpy.types.Action:
.. _bpy.ops.action:

*******
Actions
*******

When animating objects and properties in Blender, Actions record and contain the data.
As everything else in Blender, Actions are data-blocks.

.. figure:: /images/animation_actions_data3.png

   Actions.

So when you animate an object by changing its location with keyframes,
the animation is saved to the Action.

Each property has a channel which it is recorded to, for example,
``Cube.location.x`` is recorded to Channel X Location.
The *X location* and *Y location* properties can be shared across multiple objects,
if all objects have *X location* and *Y location* properties beneath them.

.. figure:: /images/animation_actions_keyframes.png

   Graph Editor. Each channel has an F-Curve represented by the lines between the keyframes.

Actions
   Record and contain animation data.
Groups
   Are groups of channels.
Channels
   Record properties.
F-Curves
   :doc:`F-Curves </editors/graph_editor/fcurves/introduction>` are used to
   interpolate the difference between the keyframes.
Keyframes
   :doc:`Keyframes </animation/keyframes/introduction>` are used to
   set the values of properties bound to a point in time.

.. The hierarchy is created with the RNA data paths,


.. _actions-workflow:

Working with Actions
====================

.. figure:: /images/animation_actions_create.png
   :align: right

   The Action data-block menu.

When you first animate an object by adding keyframes,
Blender creates an *Action* to record the data.

*Actions* can be managed with the *Action data-block menu*
in the Dope Sheet :doc:`Action Editor </editors/dope_sheet/modes/action>` header,
or the Sidebar region of the :doc:`NLA Editor </editors/nla/sidebar>`.

If you are making multiple actions for the same object,
press the shield button for each action.
This will give the actions a *Fake User* and will make Blender save the unlinked actions.

Objects can only use one *Action* at a time for editing.
The :doc:`NLA Editor </editors/nla/index>` is used to blend multiple actions together.


.. _actions-properties:

Properties
==========

.. figure:: /images/animation_actions_range.png
   :align: center

   Actions with and without a Manual Frame Range in Dope Sheet.

It is possible to manually specify the intended useful frame range of an action via a panel
available in the :doc:`Dope Sheet </editors/dope_sheet/introduction>` or the :doc:`NLA Editor </editors/nla/sidebar>`
when a channel or NLA track is selected.

.. _bpy.types.Action.use_frame_range:

Manual Frame Range
   Manually specify the intended playback frame range for the action
   (this range is used by some tools, but does not affect animation evaluation).
   The manual frame range feature can be toggled with the checkbox.

   When the range is set, it is used instead of the actual range occupied by key frames
   when adding a new track based on the action to NLA. It can also be used by exporters
   to determine the range of frames to export.

   The range is displayed in the background of the editor as diagonal hash fill, to
   distinguish it from the solid fill of the current playback range.

   The frame values are most commonly expected to be integers, but can be fractional.

.. _bpy.types.Action.use_cyclic:

Cyclic Animation
   Specifies that the action is intended to be cyclic over the specified range. The first and last
   frames of the range should represent the same pose of the cycle one loop apart, i.e. the range
   should include the duplicated initial key of the loop.

   .. note::

      This option signifies intent and does **not** make the action cycle on its own. However,
      if :ref:`Cycle-Aware Keying <bpy.types.ToolSettings.use_keyframe_cycle_aware>` is enabled,
      it will automatically enable cyclic extrapolation and set up the loop period for curves
      newly added to the action.


Custom Properties
-----------------

Create and manage your own properties to store data in the action's data block.
See the :ref:`Custom Properties <files-data_blocks-custom-properties>` page for more information.


## Index

.. _animation-index:
.. _bpy.ops.anim:

#######################
  Animation & Rigging
#######################

.. toctree::
   :maxdepth: 2

   introduction.rst
   keyframes/index.rst
   armatures/index.rst
   lattice.rst
   constraints/index.rst
   actions.rst
   drivers/index.rst
   markers.rst
   shape_keys/index.rst
   motion_paths.rst


## Introduction


************
Introduction
************

Animation
=========

Animation is making an object move or change shape over time.
Objects can be animated in many ways:

Moving as a whole object
   Changing their position, orientation or size in time;
Deforming them
   Animating their vertices or control points;
Inherited animation
   Causing the object to move based on the movement of another object (e.g. its parent, hook, armature, etc.).

In this chapter, we will cover the first two,
but the basics given here are actually vital for understanding the following chapters as well.

Animation is typically achieved with the use of :doc:`keyframes </animation/keyframes/introduction>`.

.. seealso:: Related Sections

   - :doc:`Physical Simulation </physics/introduction>`
   - :doc:`Motion Tracking </movie_clip/index>`


.. _animation-state-colors:

State Colors
------------

.. figure:: /images/animation_introduction_state-colors.png

   State colors of properties.

Properties have different colors and menu items for different states.

.. object origin, 3D Viewport overlay

.. list-table::

   * - Gray
     - Not animated
   * - Yellow
     - Keyframed on the current frame
   * - Green
     - Keyframed on a different frame
   * - Orange
     - Changed from the keyframed value
   * - Purple
     - Controlled by a driver

The changed value highlight currently doesn't work with :doc:`NLA </editors/nla/introduction>`.


.. _animation-rigging:

Rigging
=======

Rigging is a general term used for adding controls to objects,
typically for the purpose of animation.

Rigging often involves using one or more of the following features:

:ref:`Armatures <armatures-index>`
   This allows mesh objects to have flexible joints and is often used for skeletal animation.
:ref:`Constraints <constraints-index>`
   To control the kinds of motions that make sense and add functionality to the rig.
:doc:`Object Modifiers </modeling/modifiers/index>`
   Mesh deformation can be quite involved, there are multiple modifiers that help control this.
:ref:`Shape Keys <animation-shape_keys-index>`
   To support different target shapes *(such as facial expressions)* to be controlled.
:ref:`Drivers <animation-drivers-index>`
   So your rig can control many different values at once,
   as well as making some properties automatically update based on changes elsewhere.

Rigging can be as advanced as your project requires,
rigs are effectively defining own user interface for the animator to use,
without having to be concerned the underlying mechanisms.

.. TODO nice images of rigged objects.


Examples
--------

- An armature is often used with a modifier to deform a mesh for character animation.
- A camera rig can be used instead of animating the camera object directly to simulate real-world camera rigs
  (with a boom arm, mounted on a rotating pedestal for example, effects such as camera jitter can be added too).

.. TODO more examples?

.. seealso::

   The content of this chapter is simply a reference to how rigging is accomplished in Blender.
   It should be paired with additional resources such as Nathan Vegdahl's excellent introduction to
   the fundamental concepts of character rigging,
   `Humane Rigging <https://www.youtube.com/playlist?list=PLE211C8C41F1AFBAB>`__.


## Lattice

.. _bpy.types.Lattice:
.. _bpy.ops.lattice:
.. _bpy.types.LatticePoint:

*******
Lattice
*******

Lattice -- or commonly called deformation cage outside of Blender.
A lattice consists of a three-dimensional non-renderable grid of vertices.
Its main use is to apply a deformation to the object it controls with a :doc:`/modeling/modifiers/deform/lattice`.
If the object is parented with *Lattice Deform* a Lattice Modifier is automatically applied.


Editing
=======

Flip (Distortion Free)
   Mirrors the vertices displacement from their base position.

   U, V, W
Make Regular
   Resets the whole lattice to a regular grid, where the cells are scaled to one cubic unit.


Properties
==========

.. figure:: /images/animation_lattice_panel.png
   :align: right

   Lattice properties.

Lattice
   A :ref:`ui-data-block`.


Lattice
-------

Points
   Rate of subdivision in the axes:

   U, V, W
Interpolation Type
   Selector for each axis. See :ref:`fig-interpolation-type`.

   Linear, Cardinal, Catmull-Rom, B-Spline
Outside
   Takes only the vertices on the surface of the lattice into account.
Vertex Group
   The strength of the influence assigned as a weight to the individual vertices in the selected vertex group.


Usage
=====

The lattice should be scaled and moved to fit around your object in Object Mode.
Any scaling applied to the object in Edit Mode will result in the object deforming.
This includes applying its scale with :kbd:`Ctrl-A` as this will achieve the same result as
scaling the lattice in Edit Mode, and therefore the object.

.. figure:: /images/animation_lattice_view.png
   :align: center

   Lattice around the cube object in Object Mode.


## Markers

.. _bpy.types.TimelineMarker:
.. _bpy.ops.marker:

*******
Markers
*******

Markers are used to denote frames with key points or significant events within an animation.
E.g. it could be that a character's animation starts, the camera changes position, or a door opens.
Markers can be given names to make them more meaningful at a quick glance.
They are available in many of Blender's editors.

.. note::

   Unlike keyframes, markers are always placed at a whole frame number, you cannot set a marker at frame 2.5.

Markers can be created and edited in the following editors:

- :doc:`Graph Editor </editors/graph_editor/introduction>`
- :doc:`Dope Sheet </editors/dope_sheet/introduction>`
- :doc:`NLA Editor </editors/nla/index>`
- :doc:`Video Sequence Editor </video_editing/index>`
- :doc:`Timeline </editors/timeline>`

.. note::

   A marker created in one of these editors will also appear in all others that support them.


Types
=====

Besides standard markers, *pose markers* are another type of markers,
which are specific to armatures and shape keys.
They are used to denote poses in the Action Editor mode and Shape Keys Editor of Dope Sheet.


Visualization
=============

In the supported editors, if at least one is created, markers are visualized
in a separate row at their bottom.
This area can be disabled per editor via the :menuselection:`View --> Show Markers` menu option.

.. note::

   While the markers area is disabled, markers operators are not available in that editor,
   and in the header the *Marker* menu is hidden.


Standard
--------

.. figure:: /images/animation_markers_standard.png
   :align: right

Regular markers are shown as small white triangles, empty if unselected or filled if selected,
and with a dashed line that covers the editor height at the corresponding frame.
If they have a name, this is shown to their right in white.


3D Viewport
-----------

.. figure:: /images/animation_markers_3d-view.png
   :align: right

The 3D Viewport does not allow you to create, edit or remove markers,
but it shows their name in the Object Info in the upper left corner,
when on their frame.


Pose Markers
------------

.. figure:: /images/animation_markers_pose.png
   :align: right

Pose markers show a diamond-shaped icon in the Dope Sheet.
In the NLA editor pose markers are shown as a red dashed line inside the relative action strip.

.. container:: lead

   .. clear


.. _bpy.ops.marker.add:

Add Marker
==========

.. reference::

   :Mode:      All modes
   :Menu:      :menuselection:`Marker --> Add Marker`
   :Shortcut:  :kbd:`M`

The simplest way to add a marker is to move to the frame where you would like it to appear,
and press :kbd:`M`.

.. hint::

   Markers can also be added during playback.


.. _marker-pose-add:

Pose Markers
------------

If *Show Pose Markers* is checked, a pose marker and
a new pose in the :ref:`Old Pose Library <pose-library-old>` are added.


.. _bpy.ops.marker.select:

Selecting
=========

.. reference::

   :Mode:      All modes
   :Shortcut:  :kbd:`LMB`

Click :kbd:`LMB` on the marker's triangle to select it.
Use :kbd:`Shift-LMB` to select multiple markers.

In the Graph Editor, Dope Sheet, NLA Editor, Timeline, and Video Sequence Editor,
you can also select all markers with :kbd:`A` while hovering the mouse over the marker row,
and apply selection tools on them like Box Select, etc.
(as usual, :kbd:`LMB` to select, :kbd:`RMB` to deselect).
The corresponding options are found in the Select menu of these editors.


.. _animation-markers-editing:

Editing
=======

.. _bpy.ops.marker.duplicate:

Duplicate Marker
----------------

.. reference::

   :Mode:      All modes
   :Menu:      :menuselection:`Marker --> Duplicate Marker`
   :Shortcut:  :kbd:`Shift-D`

You can duplicate the selected markers by pressing :kbd:`Shift-D`. Once duplicated,
the new ones are automatically placed in select mode, so you can move them to the desired location.

.. note::

   Note that unlike most other duplications in Blender,
   the names of the duplicated markers are not altered at all
   (no ``.001`` numeric counter append).


.. _bpy.ops.marker.make_links_scene:

Duplicate Marker to Scene
-------------------------

.. reference::

   :Mode:      All modes
   :Menu:      :menuselection:`Marker --> Duplicate Marker to Scene...`

Duplicates the selected markers into another scene.


.. _bpy.ops.marker.delete:

Delete Marker
-------------

.. reference::

   :Mode:      All modes
   :Menu:      :menuselection:`Marker --> Delete Marker`
   :Shortcut:  :kbd:`X`

To delete the selected markers simply press :kbd:`X`,
and confirm the pop-up message with :kbd:`LMB`.


Rename Marker
-------------

.. reference::

   :Mode:      All modes
   :Menu:      :menuselection:`Marker --> Rename Marker`
   :Shortcut:  :kbd:`F2`

Having dozens of markers scattered throughout your scene's time will not help you much unless you
know what they stand for. You can name a marker by selecting it, pressing :kbd:`F2`,
typing the name, and press :kbd:`Return`


.. _bpy.ops.marker.move:

Move Marker
-----------

.. reference::

   :Mode:      All modes
   :Menu:      :menuselection:`Marker --> Move Marker`
   :Shortcut:  :kbd:`G`

Once you have one or more markers selected, press :kbd:`G`,
while hovering with the mouse over the marker bar,
to move them, and confirm the move with :kbd:`LMB` or :kbd:`Return`
(as usual, cancel the move with :kbd:`RMB`, or :kbd:`Esc`).
Or drag them with the :kbd:`LMB`.

By default, you move the markers in one-frame steps, but if you hold :kbd:`Ctrl`,
the markers will move in steps corresponding to 1 second (according to the scene's *FPS*).


Select
------

.. reference::

   :Mode:      All modes
   :Menu:      :menuselection:`Marker --> Select`

Convenient operators for selecting Marks; see :ref:`bpy.ops.marker.select` for more information on selecting Markers.

.. _bpy.ops.marker.select_all:

All :kbd:`A`
   Selects all Markers.
None :kbd:`Ctrl-A`
   Deselects any already selected Markers.
Invert :kbd:`Ctrl-I`
   Select all unselected Markers and deselects all selected Markers.

.. _bpy.ops.marker.select_leftright:

Before Current Frame
   Selects all Markers to the left of the current frame and the Marker on the current frame if it exists.
After Current Frame
   Selects all Markers to the Right of the current frame and the Marker on the current frame if it exists.


.. _bpy.types.SpaceDopeSheetEditor.show_pose_markers:

Show Pose Markers
-----------------

.. reference::

   :Editor:    Dope Sheet
   :Mode:      Action Editor or Shape Keys Editor mode
   :Menu:      :menuselection:`Marker --> Show Pose Markers`

Shows markers belonging to the active action instead of scene markers.


.. _bpy.ops.action.markers_make_local:

Make Markers Local
------------------

.. reference::

   :Mode:      All modes
   :Menu:      :menuselection:`Marker --> Make Markers Local`

It is possible to convert standard markers into pose markers with :menuselection:`Marker --> Make Markers Local`.
Note that the original marker will be gone. If you want to keep it, make a duplicate before you convert.


.. _bpy.ops.screen.marker_jump:

Jump to Next/Previous Marker
----------------------------

.. reference::

   :Mode:      All modes
   :Menu:      :menuselection:`Marker --> Jump to Next/Previous Marker`

Moves the Playhead to the next/previous marker relative to the current frame.


.. _bpy.ops.marker.camera_bind:

Bind Camera to Markers
======================

.. reference::

   :Editor:    Timeline
   :Menu:      :menuselection:`Marker --> Bind Camera to Markers`
   :Shortcut:  :kbd:`Ctrl-B`

*Bind Camera to Markers* is a special operator only available in the *Timeline*.
The operator allows markers to be used to set the active object as the active camera.

To use this operator, select the object to become the active camera
and select a marker to bind the active camera to.
If no marker is selected when the operator is applied, a marker will be added.
When an object is bound to a marker, the marker will be renamed to the name of the active object.
These markers also have a camera icon next to the left of the name
to easily distinguish them from other informative markers.

These markers can be moved to change the frame at which
the active camera is changed to the object the marker is bound to.


## Motion Paths

.. _bpy.types.AnimVizMotionPaths:
.. _bpy.types.MotionPath:

************
Motion Paths
************

.. reference::

   :Editor:    3D Viewport, Properties
   :Mode:      Object Mode
   :Panel:     :menuselection:`Properties --> Object Properties --> Motion Paths`

.. reference::

   :Editor:    3D Viewport, Properties
   :Mode:      Pose Mode
   :Panel:     :menuselection:`Properties --> Armature --> Motion Paths`
   :Menu:      :menuselection:`Pose --> Motion Paths`

.. figure:: /images/animation_motion-paths_example-object.png
   :width: 400px

   An animated cube with its motion path displayed.

The Motion Paths tool allows you to visualize the motion of points as paths over a series of frames.
These points can be object origins and bone joints.

To create or remove motion paths, it is necessary to first select the bones. Then:

#. To show the paths (or update them, if needed), click on the *Calculate Path* button.
#. To hide the paths, click on the *Clear Paths* button.

.. note::

   Remember that only selected bones and their paths are affected by these actions!

The paths are shown in a light shade of gray for unselected points,
and a slightly bluish gray for selected ones.
Around the current frame a glow indicate the direction of movement:
blue towards future frames and green towards the past.
Each frame is displayed by a small white dot on the paths.

The paths are automatically updated when you edit your poses/keyframes,
and they are also active during animation playback. Playing the animation
affects the paths only when using the *Around Frame* type.


Options
=======

.. figure:: /images/animation_motion-paths_panel.png

   The Motion Paths panel in the Armature tab.

.. _bpy.types.AnimVizMotionPaths.type:

Paths Type
   Type of range to show for Motion Paths.

   :Around Frame:
      Display paths of points within a fixed number of frames around the current frame.
      When you enable this button, you get paths for a given number of frames before and after the current one
   :In Range:
      Display paths of points within specified range.

      .. _bpy.ops.pose.paths_range_update:

.. _bpy.types.AnimVizMotionPaths.range:

Calculation Range
   The range of the motion path. Only active when *Paths Type* is set to
   *In Range*. Changing this option only takes effect when updating the path, via
   the *Update Path* or *Update All Paths* buttons.

   :All Keys:
      Generate a motion path ranging from the first keyframe to the last. Only
      the keys of the active object / bone are considered.
   :Selected Keys:
      Same as *All Keys* except that it ranges from the first to the last
      *selected* keyframe.
   :Scene Frame Range:
      Use the start & end frames of the scene, or the
      :ref:`preview range <graph-preview-range>` if active.
   :Manual Range:
      Manually set the start and end frame.

.. _bpy.types.AnimVizMotionPaths.frame_start:
.. _bpy.types.AnimVizMotionPaths.frame_end:

Frame Range Start, End
   Starting and Ending frame of range of paths to display/calculate
   (not for the *Around Frame* type).

   Although the start and end frame are always editable, updating the motion
   path will change these according to the *Calculation Range* setting. To
   ensure your chosen frame range is maintained, choose *Manual Range* there.

.. _bpy.types.AnimVizMotionPaths.frame_before:
.. _bpy.types.AnimVizMotionPaths.frame_after:

Frame Range Before, After
   Number of frames to show before and after the current frame
   (only for the *Around Frame* type).

.. _bpy.types.AnimVizMotionPaths.frame_step:

Step
   Allows displaying one point for every *n* frames on the path.
   Mostly useful when you enable the frame number display (see below), to avoid cluttering the 3D Viewport.

.. _bpy.types.AnimVizMotionPaths.use_camera_space_bake:

Bake to Active Camera
   When enabled the motion path is calculated in screen space for the active scene camera.
   Note that the resulting motion path will only be useful for that single camera.
   Switching cameras using markers is not supported. It will only bake to the camera
   that is active when the bake was started.

.. _bpy.types.MotionPath.frame_start:
.. _bpy.types.MotionPath.frame_end:

Cache/Bone Cache From, To
   These are the start/end frames of the range in which motion paths are shown.
   You cannot modify this range without deleting the motion path first.

.. _bpy.ops.pose.paths_calculate:
.. _bpy.ops.object.paths_calculate:

Calculate
   If no paths have been calculated, Calculate Paths will create a new motion path in cache based on
   the options specified in the pop-up menu or the :ref:`bpy.ops.screen.redo_last` panel.
   Note, if the current context is an Armature calculating the objects motion paths, and not the bones,
   this operator will calculate the motion paths for all the bones within the armature as well.

   Start, End
      These are the start/end frames of the range in which motion paths are shown.
      The start frame is *inclusive*, so if you set *Start* to 1,
      you will really see the frame 1 as starting point of the paths...

   Bake Location
      Which point on the bones is used when calculating paths.
      Only available for bones while in Pose Mode.

      :Heads: Calculates the path position of the bone's heads.
      :Tails: Calculates the path position of the bone's heads.

.. _bpy.ops.pose.paths_update:
.. _bpy.ops.object.paths_update:

Update Paths
   In the case a path has already been calculated, this operator will update the path shape to the current animation.
   To change the frame range of the calculated path, you need to delete the path and calculate it again.

   .. _bpy.ops.pose.paths_clear:
   .. _bpy.ops.object.paths_clear:

   Clear Paths ``X``
      Clears paths on all objects/bones or just the selected ones when holding :kbd:`Shift`.

.. _bpy.ops.object.paths_update_visible:

Update All Paths
   Recalculates the motion paths for all visible objects and poses.


Display
-------

.. _bpy.types.AnimVizMotionPaths.show_frame_numbers:

Frame Numbers
   When enabled, a small number appears next to each frame dot on the path,
   which is of course the number of the corresponding frame.

.. _bpy.types.AnimVizMotionPaths.show_keyframe_highlight:

Keyframes
   When enabled, big yellow square dots are displayed on motion paths, showing the keyframes of their bones
   (i.e. only the paths of keyed bones at a given frame get a yellow dot at this frame).

.. _bpy.types.AnimVizMotionPaths.show_keyframe_action_all:

\+ Non-Grouped Keyframes
   For bone motion paths, it searches the whole Action for keyframes instead of
   in groups with matching name only (this is slower).

.. _bpy.types.AnimVizMotionPaths.show_keyframe_numbers:

Keyframe Numbers
   When enabled, you will see the numbers of the displayed keyframes,
   so this option is obviously only valid when *Show Keys* is enabled.

.. _bpy.types.MotionPath.lines:

Lines
   Toggles whether the lines between the points are shown.

.. _bpy.types.MotionPath.line_thickness:

Thickness
   Line thickness for motion path.

.. _bpy.types.MotionPath.use_custom_color:
.. _bpy.types.MotionPath.color:

Custom Color
   Use custom color for this motion path.


Example
=======

.. figure:: /images/animation_motion-paths_example-armature.png

   An example of a motion path of an armature.


## Index

.. _armatures-index:
.. _bpy.types.Armature:
.. _bpy.ops.armature:
.. _bpy.ops.object.armature:

#############
  Armatures
#############

.. toctree::
   :maxdepth: 2

   introduction.rst
   bones/index.rst
   properties/index.rst
   structure.rst
   skinning/index.rst
   posing/index.rst


## Introduction


************
Introduction
************

An armature in Blender can be thought of as similar to the armature of a real skeleton,
and just like a real skeleton an armature can consist of many bones.
These bones can be moved around and anything that they are attached to or
associated with will move and deform in a similar way.

An "armature" is a type of object used for rigging.
A rig is the controls and strings that move a marionette (puppet).
Armature object borrows many ideas from real-world skeletons.


Your First Armature
===================

In order to see what we are talking about, let us try to add the default armature in Blender.

(Note that armature editing details are explained in
the :doc:`armatures editing section </animation/armatures/bones/editing/index>`.)

Open a default scene, then:

#. Delete all objects in the scene.
#. Make sure the cursor is in the world origin with :kbd:`Shift-C`.
#. Press :kbd:`Numpad1` to see the world in Front view.
#. Add a *Single Bone* (:menuselection:`Add --> Armature`).
#. Press :kbd:`NumpadPeriod` to see the armature at maximum zoom.

.. figure:: /images/animation_armatures_introduction_default.png

   The default armature.


The Armature Object
===================

As you can see, an armature is like any other object type in Blender:

- It has an origin, a position, a rotation and a scale factor.
- It has an Object Data data-block, that can be edited in *Edit Mode*.
- It can be linked to other scenes, and the same armature data can be reused on multiple objects.
- All animation you do in *Object Mode* is only working on the whole object,
  not the armature's bones (use the *Pose Mode* to do this).

As armatures are designed to be posed, either for a static or animated scene,
they have a specific state, called "rest position". This is the armature's default "shape",
the default position/rotation/scale of its bones, as set in *Edit Mode*.

In *Edit Mode*, you will always see your armature in rest position,
whereas in *Object Mode* and *Pose Mode*,
you usually get the current "pose" of the armature
(unless you enable the *Rest Position* button of the *Armature* panel).


## Structure


*********
Structure
*********

.. figure:: /images/animation_armatures_structure_armature-example.png
   :align: right

   Example of a very basic armature.

Armatures mimic real skeletons. They are made out of bones, which are (by default) rigid elements.
But you have more possibilities than with real skeletons: In addition to the "natural" rotation of bones,
you can also move and even scale them! And your bones do not have to be connected to each other;
they can be completely free if you want. However,
the most natural and useful setups imply that some bones are related to others, forming so-called "chains of bones",
which create some sort of "limbs" in your armature, as detailed in `Chains of Bones`_.

.. container:: lead

   .. clear


.. _armature-bone-chain:

Chains of Bones
===============

The bones inside an armature can be completely independent from each other
(i.e. the modification of one bone does not affect the others).
But this is not often a useful set up: To create a leg,
all bones "after" the thigh bone should move "with" it in a well-coordinated manner.
This is exactly what happens in armatures by parenting a bone to the next one in the limb,
you create a "chains of bones". These chains can be ramified. For example,
five fingers attached to a single "hand" bone.

.. figure:: /images/animation_armatures_structure_chains-of-bones.png

   An armature with two chains of bones.

Bones are chained by linking the tip of the parent to the root of the child.
Root and tip can be *connected*, i.e. they are always exactly at the same point;
or they can be *free*, like in a standard parent-child object relationship.

A given bone can be the parent of several children,
and hence be part of several chains at the same time.

The bone at the beginning of a chain is called its *root bone*,
and the last bone of a chain is the *tip bone*
(do not confuse them with similar names of bones' joints!).

Chains of bones are a particularly important topic in :doc:`posing </animation/armatures/posing/index>`
(especially with the standard *forward* kinematics versus "automatic" *inverse* kinematics posing techniques).
You create/edit them in *Edit Mode*, but except in case of connected bones,
their relationships have no effect on bone transformations in this mode
(i.e. transforming a parent bone will not affect its children).

The easiest way to manage bones relationships is to use
the :ref:`Relations panel <bpy.types.EditBone.parent>` in the Bone tab.


## Bone Collections


.. _bone-collections:

****************
Bone Collections
****************

:term:`Bone Collections <Bone Collection>` group the bones of an
:term:`Armature` into named collections. The armature is the owner of these
collections, so they are available in all modes. Bone Collections are identified
by their name, which are unique within the Armature.
Bone Collections can be nested inside other Bone Collections to create an organized hierarchy for complex rigs.

In the text below, "collection" is understood to refer to "bone collection";
:term:`Scene Collections <Collection>` are not described here.

Bone Collections can be managed via :ref:`the Armature and Bone property panels <bpy.types.BoneCollection>`.


Visibility
==========

Bone Collections can be shown & hidden via the list in the Armature properties,
as well as via the list in the Bone properties. Bone visibility is determined by
the visibility of its collections, its own 'solo' and 'hidden' properties:

- If the bone itself is marked as 'hidden', it is invisible regardless of the
  bone collections.
- If a parent collection is hidden, child collections will also be hidden; same is true for soloed collections.
- A bone is visible when it is contained in any visible collection.
- If a collection is soloed, it will be visible regardless of the collection's 'hidden' property.
- A bone that is not assigned to any bone collection is visible; otherwise it
  would be impossible to select it & assign it to a collection.


.. _bone_collections_library_overrides:

Library Overrides
=================

Bone collections can be added using library overrides. For this to work, both
the armature Object and the Armature itself need to be overridden.

Limitations
-----------

There are a few limitations when it comes to bone collections & overrides:

- Only bone collections that are local to the current blend file can be edited.
- Bone collections that already existed on the linked-in Armature are read-only,
  and only their visibility can be toggled. Those visibility changes won't be
  saved, though.
- Custom properties of overridden bone collections cannot be edited in the
  properties panel. Python access is fine; this is just a current limitation of
  Blender's UI code.


How It Works
------------

Bone collections added via overrides are 'anchored' to the preceding
collection, by name. Here is an example. The *italic* collections are defined on
the linked Armature in ``armature.blend``. The **bold** ones are added by
overrides in ``armature_shot_47.blend``.

- *FK Controls*
- *IK Controls*
- **Left Pinky** (anchored to "IK Controls")
- **Right Pinky** (anchored to "Left Pinky")

Now if the Armature in ``armature.blend`` gets updated with two more collections
it might look like this:

- *FK Controls*
- *IK Controls*
- *Face Controls*
- *Face Detail Controls*

After reloading ``armature_shot_47.blend``, it will look like this:

- *FK Controls*
- *IK Controls*
- **Left Pinky** (still anchored to "IK Controls")
- **Right Pinky** (still anchored to "Left Pinky")
- *Face Controls*
- *Face Detail Controls*


.. _bpy.types.armature.layers:

Some history
============

Bone Collections were introduced in Blender 4.0, as a replacement for armature
layers and bone groups. Bone Collections are owned by the Armature, so they are
available in all modes. To contrast, bone groups were stored on the object's
pose, and thus were not available in armature edit mode.


## Index

.. _bpy.types.Bone:
.. _bpy.types.ArmatureBones:

#########
  Bones
#########

.. toctree::
   :maxdepth: 2

   introduction.rst
   bone_collections.rst
   structure.rst
   tools/index.rst
   selecting.rst
   editing/index.rst
   properties/index.rst


## Introduction


************
Introduction
************

Bones are the base elements of armatures.
The visualization of bones can be set in the Armatures :doc:`/animation/armatures/properties/display`.

.. (wip) are rigid.


.. (todo move)? to bone > properties > deform, extend control: fk

Classification
==============

Bones in an Armature can be generally classified into two different types:

#. Deforming Bones
#. Control Bones


Deforming Bones
---------------

Are bones which when transformed will result in vertices associated with
them also transforming in a similar way. Deforming Bones are directly involved in altering
the positions of vertices associated with their bones.


Control Bones
-------------

Are Bones which act in a similar way to switches,
in that, they control how other bones or objects react when they are transformed.
A Control Bone could for example act as a sliding switch control when the bone is in one
position to the left, it could indicate to other bones that they react in a particular way when
transformed, and when the Control Bone is positioned to the right,
transforming other bones or objects could do something completely different.
Control Bones are not directly used to alter the positions of vertices;
in fact, Control Bones often have no vertices directly associated with themselves.


## Selecting


*********
Selecting
*********

You can select and edit bones of armatures in *Edit Mode* and in *Pose Mode*.
Here, we will see how to select bones in *Edit Mode*.
Selecting bones in *Pose Mode* is similar to selecting in *Edit Mode*
with a few specific differences that will be detailed in
the :doc:`posing part </animation/armatures/posing/selecting>`.

Similar to :doc:`vertex/edge selection </modeling/meshes/selecting/introduction>` in meshes,
there are two ways to select whole bones in *Edit Mode*:

#. Directly, by selecting the bone's body.
#. Selecting both of its joints (root and tip).

This is an important point to understand,
because selecting bones' joints only might lead to non-obvious behavior,
with respect to which bone you actually select.

Note that unlike the mesh display type, the armature display type has no effect on selection behavior.
In other words, you can select a bone's joint or body the same way regardless of
the bone visualization chosen.


.. _bpy.ops.armature.select_all:

Selecting Bone Joints
=====================

To select bones' joints you have the :doc:`standard selection </scene_layout/object/selecting>` methods.


Inverse Selection
-----------------

As stated above, you have to remember that these selection tools are for bones' joints only,
not the bones' bodies.

For example, the *Inverse* selection option :kbd:`Ctrl-I`
inverts the selection of bones' joints, not of bones (see *Inverse selection*).

Remember that a bone is selected only if both its joints are selected. So,
when the selection status of bones' joints is inverted, a new set of bones is selected.

.. list-table:: Inverse selection.

   * - .. figure:: /images/animation_armatures_bones_selecting_two-bones.png
          :width: 320px

          Two bones selected.

     - .. figure:: /images/animation_armatures_bones_selecting_three-ends.png
          :width: 320px

          The result of the inverse selection :kbd:`Ctrl-I`:
          The bones joints selection has been inverted, and not the bones selection.


Selecting Connected Bone Joints
-------------------------------

Another example is: when you select the root of a bone connected to its parent,
you also implicitly select the tip of its parent (and vice versa).

.. note::

   Remember that when selecting bones' joints,
   the tip of the parent bone is the "same thing" as the root of its children bones.


Selecting Bones
===============

By clicking on a bone's body, you will select it
(and hence you will implicitly select its root and tip).

Using :kbd:`Shift`-click, you can add to/remove from the selection.

You also have some *advanced selection* options, based on their relations.

Pick Shortest Path :kbd:`Ctrl`-click
   Selects the path from the active bone to the bone under the mouse.


Deselecting Connected Bones
---------------------------

There is a subtlety regarding connected bones.

When you have several connected bones selected, if you deselect one bone,
its tip will be deselected, but not its root, if it is also the tip of another selected bone.

To understand this, look at Fig. :ref:`fig-rig-bone-select-deselect`.

.. _fig-rig-bone-select-deselect:

.. list-table:: Bone deselection in a selected chain.

   * - .. figure:: /images/animation_armatures_bones_selecting_whole-chain.png
          :width: 320px

          A selected chain.

     - .. figure:: /images/animation_armatures_bones_selecting_two-bones.png
          :width: 320px

          Two selected bones.

After :kbd:`Shift`-clicking "Bone.003":

- "Bone.003" 's tip (which is same as "Bone.004" 's root) is deselected.
- "Bone" is "Bone.003" 's parent. Therefore, "Bone.003" 's root is the same as the tip of "Bone".
  Since "Bone" is still selected, its tip is selected. Thus the root of "Bone.003" remains selected.


.. _bpy.ops.armature.select_mirror:

Select Mirror
=============

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Select --> Select Mirror`
   :Shortcut:  :kbd:`Shift-Ctrl-M`

Flip the selection from one side to another.


.. _bpy.ops.armature.select_more:
.. _bpy.ops.armature.select_less:

More/Less
=========

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Select --> More/Less`

More :kbd:`Ctrl-NumpadPlus`
   Expand the current selection to the connected bones.
Less :kbd:`Ctrl-NumpadMinus`
   Contrast the selection, deselect bones at the boundaries of each selection region.


.. _bpy.ops.armature.select_linked:

Select Linked
=============

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Select --> Select Linked`
   :Shortcut:  :kbd:`Ctrl-L`

Selects all the bones in the chain which the active (last selected) bone belongs to.

All Forks
   Selects all bones connected to the active bone even if the branch off from the current bone.

.. list-table:: Linked bones selection.

   * - .. figure:: /images/animation_armatures_bones_selecting_single-bone.png
          :width: 320px

          A single selected bone.

     - .. figure:: /images/animation_armatures_bones_selecting_whole-chain.png
          :width: 320px

          Its whole chain selected with Linked.


.. _bpy.ops.armature.select_similar:

Select Similar
==============

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Select --> Select Similar`
   :Shortcut:  :kbd:`Shift-G`

Children
   Extends the selection to all hierarchical descendant bones.
Immediate Children
   Extends the selection to all direct child bones.
Siblings
   Selects bones that have the same parent as the active bone.
Length
   Selects bones with a similar bone length (between tip and tail) under the specified *Threshold*.
Direction (Y axis)
   Select bones aligned on the Y axis (along the bone's length).
Prefix
   Select bones with matching name prefix (separated by ``.``).
Suffix
   Select bones with matching name suffix (separated by ``.``).
Bone Collection
   Select bones that share one or more bone collections with the active bone.
Color
   Select bones that have the same color as the active bone.
Shape
   Select bones using the same shape object (in Pose Mode).


Select Pattern
==============

.. reference::

   :Mode:      Pose & Armature Edit Modes
   :Menu:      :menuselection:`Select --> Select Pattern...`

Select bones by names, see :ref:`Object Select Pattern <bpy.ops.object.select_pattern>` for details.


.. _bpy.ops.armature.select_hierarchy:

Parent/Child
============

Parent :kbd:`[`, Child :kbd:`]`
   You can deselect the active bone and select its immediate parent or one of its children.


Extend Parent/Child
===================

Extend Parent :kbd:`Shift-[`, Extend Child :kbd:`Shift-]`
   Similar to *Parent*/*Child* but it keeps the active bone in the selection.



## Structure


*********
Structure
*********

.. figure:: /images/animation_armatures_bones_structure_bones-elements.png
   :align: right

   The elements of a bone.

They have three elements:

#. The "start joint" named *root* or *head*.
#. The "body" itself.
#. And the "end joint" named *tip* or *tail*.

With the default armature in Edit Mode,
you can select the root and the tip, and move them as you do with mesh vertices.

Both root and tip (the "joints") define the bone by their respective position.

They also have a radius property, only useful for the envelope deformation method (see below).


Roll
====

Activating the :ref:`Axes <bpy.types.Armature.show_axes>`
checkbox will show local axes for each bone's tip. The Y axis is always aligned along the bone,
oriented from root to tip, this is the "roll" axis of the bones.

.. short about envelope (move deform or to skinning) then link


.. _armature-bone-influence:

Bones Influence
===============

.. figure:: /images/animation_armatures_bones_structure_envelope-edit-mode.png
   :figwidth: 180px
   :align: right

   A bone in Envelope visualization, in Edit Mode.

Basically, a bone controls a geometry when vertices "follow" the bone. This is like how
the muscles and skin of your finger follow your finger-bone when you move a finger.

To do this, you have to define the strength of *influences* a bone has on a certain vertex.

The simplest way is to have each bone affecting those parts of the geometry that are within
a given range from it. This is called the *envelope technique*,
because each bone can control only the geometry "enveloped" by its own influence area.

If a bone is visualized as *Envelope*, in *Edit Mode* and in *Pose Mode*
you can see the area of influence, which depends on:

- The *distance* property and
- the root's radius and the tip's radius.

.. figure:: /images/animation_armatures_bones_structure_envelope-pose-mode.png
   :width: 300px

   Our armature in Envelope visualization, in Pose Mode.

All these influence parameters are further detailed
in the :doc:`skinning pages </animation/armatures/skinning/index>`.


## Bone Roll

.. _armature-bone-roll:

*********
Bone Roll
*********

In *Edit Mode*, you can control the bone roll
(i.e. the rotation around the Y axis of the bone).

However, after editing the armature, or when using :term:`Euler Rotation`,
you may want to set the bone roll.


.. _bpy.ops.armature.calculate_roll:

Recalculate Roll
================

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Armature --> Bone Roll --> Recalculate Roll`
   :Shortcut:  :kbd:`Shift-N`

Axis Orientation
   Local Tangent
      Align roll relative to the axis defined by the bone and its parent.

      X, Z
   Global Axis
      Align roll to global X, Y, Z axis.

      X, Y, Z
   Active Bone
      Follow the rotation of the active bone.
   View Axis
      Set the roll to align with the viewport.
   Cursor
      Set the roll towards the 3D cursor.
Flip Axis
   Reverse the axis direction.
Shortest Rotation
   Avoids rolling the bone over 90 degrees from its current value.


.. _tool-bone-role:

Set Roll
========

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Armature --> Bone Roll --> Set Roll`
   :Shortcut:  :kbd:`Ctrl-R`

This is a transform mode where you can edit the roll of all selected bones.


## Delete


******
Delete
******

.. _bpy.ops.armature.delete:

Bones
=====

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Armature --> Delete --> Bones`
   :Shortcut:  :kbd:`X`

This tool delete selected bones, selected *joints* are ignored.

If you delete a bone in a chain, its child(ren)
will be automatically re-parented to its own parent, but **not** connected,
to avoid deforming the whole armature.

.. list-table:: Deletion example.

   * - .. figure:: /images/animation_armatures_bones_editing_delete_example-1.png

          An armature with two selected bones, just before deletion.

     - .. figure:: /images/animation_armatures_bones_editing_delete_example-2.png

          The two bones have been deleted. Note that Bone.002,
          previously connected to the deleted Bone.001, is now parented but not connected to Bone.


.. _bpy.ops.armature.dissolve:

Dissolve
========

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Armature --> Delete --> Dissolve`
   :Shortcut:  :kbd:`Ctrl-X`

Todo 2.76.


## Duplicate

.. _bpy.ops.armature.duplicate_move:

*********
Duplicate
*********

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Armature --> Duplicate`
   :Shortcut:  :kbd:`Shift-D`

.. note::

   This tool works on selected bones; selected joints are ignored.

As in mesh editing, by pressing :kbd:`Shift-D` the selected bones will be duplicated.
The duplicates become the selected elements and they are placed in select mode,
so you can move them wherever you like.

If you select part of a chain, by duplicating it you will get a copy of the selected chain,
so the copied bones are interconnected exactly like the original ones.

The duplicate of a bone which is parented to another bone will also be parented to the same
bone, even if the root bone is not selected for the duplication. Be aware, though,
that if a bone is parented **and** connected to an unselected bone,
its copy will be parented, but **not** connected to the unselected bone
(see Fig. :ref:`fig-rig-bone-duplication`).

.. _fig-rig-bone-duplication:

.. list-table:: Duplication example.

   * - .. figure:: /images/animation_armatures_bones_editing_duplicate_example-1.png

          An armature with three selected bones and a selected single root.

     - .. figure:: /images/animation_armatures_bones_editing_duplicate_example-2.png

          The three duplicated bones. Note that the selected chain is preserved in the copy,
          and that Bone.006 is parented but not connected to Bone.001, as indicated by the black dashed line.
          Similarly, Bone.007 is parented but not connected to Bone.003.


## Extrude

.. _bpy.ops.armature.extrude_move:
.. _bpy.ops.armature.extrude_forked:

*******
Extrude
*******

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Armature --> Extrude`
   :Shortcut:  :kbd:`E`, :kbd:`Shift-E`

When you press :kbd:`E`, for each selected tip
(either explicitly or implicitly), a new bone is created.
This bone will be the child of "its" tip owner, and connected to it. As usual,
once extrusion is done, only the new bones' tips are selected, and in select mode,
so you can place them to your liking. See Fig. :ref:`fig-rig-bones-extrusion`.

.. _fig-rig-bones-extrusion:

.. list-table:: Extrusion example.

   * - .. figure:: /images/animation_armatures_bones_editing_extrude_example-1.png

          An armature with three selected tips.

     - .. figure:: /images/animation_armatures_bones_editing_extrude_example-2.png

          The three extruded bones.

You also can use the rotating/scaling extrusions,
as with meshes, by pressing respectively :kbd:`E R` and :kbd:`E S` --
as well as :doc:`locked </scene_layout/object/editing/transform/control/axis_locking>`
extrusion along a global or local axis.

.. _fig-rig-bone-mirror:

.. list-table:: Mirror extrusion example.

   * - .. figure:: /images/animation_armatures_bones_editing_extrude_mirror-1.png

          A single selected bone's tip.

     - .. figure:: /images/animation_armatures_bones_editing_extrude_mirror-2.png

          The two mirror-extruded bones.

Bones have an extra "mirror extruding" tool, called by pressing :kbd:`Shift-E`.
By default, it behaves exactly like the standard extrusion.
But once you have enabled :ref:`bpy.types.Armature.use_mirror_x` editing option,
each extruded tip will produce *two new bones*, having the same name except for the "_L"/ "_R" suffix
(for left/right, see the :ref:`naming conventions <armature-editing-naming-conventions>`).
The "_L" bone behaves like the single one produced by the default extrusion --
you can move, rotate or scale it exactly the same way.
The "_R" bone is its mirror counterpart (along the armature's local X axis),
see Fig. :ref:`fig-rig-bone-mirror`.

.. important::

   Canceling the extrude action causes the newly created bones to snap back to the source position,
   (creating zero length bones). These will be removed when exiting Edit Mode,
   however, they can cause confusion and it's unlikely you want to keep them.
   If you realize the problem immediately, undo the extrude action.

In case you are wondering, you cannot just press :kbd:`X` to solve this as you would in mesh editing,
because extrusion selects the newly created tips, and as explained below the Delete tool ignores bones' joints.
To get rid of these extruded bones without undoing, you would have to move the tips,
then select the bones and :ref:`delete <bpy.ops.armature.delete>` them.


.. _bpy.ops.armature.click_extrude:

Mouse Clicks
============

.. reference::

   :Mode:      Edit Mode
   :Shortcut:  :kbd:`Ctrl-RMB`

If at least one bone is selected, :kbd:`Ctrl-RMB`-clicking adds a new bone.

About the new bone's tip:

After you :kbd:`Ctrl-RMB`-clicked it becomes the active element in the armature,
it appears to be right where you clicked, but (as in mesh editing)
it will be on the plane parallel to the view and passing through the 3D cursor.

The position of the root and the parenting of the new bone depends on the active element:

.. TODO2.8 Update images (includes outliner)

.. figure:: /images/animation_armatures_bones_editing_extrude_mouse-clicks-1.png
   :width: 300px

   :kbd:`Ctrl`\ -clicking when the active element is a bone.

If the active element is a *bone*:

- The new bone's root is placed on the active bone's tip.
- The new bone is parented and connected to the active bone
  (check the Outliner in Fig. :ref:`fig-rig-bone-active-tip`).

.. TODO2.8 Update images (includes outliner)

.. _fig-rig-bone-active-tip:

.. figure:: /images/animation_armatures_bones_editing_extrude_mouse-clicks-2.png
   :width: 300px

   :kbd:`Ctrl`\ -clicking when the active element is a tip.

If the active element is a *tip*:

- The new bone's root is placed on the active tip.
- The new bone is parented and connected to the bone owning the active tip
  (check the Outliner in Fig. :ref:`fig-rig-bone-active-tip`).

.. TODO2.8 This doesn't seem to work as documented:
.. TODO2.8 Update images (includes outliner)

.. _fig-rig-bone-disconnected-tip:

.. figure:: /images/animation_armatures_bones_editing_extrude_mouse-clicks-3.png
   :width: 300px

   :kbd:`Ctrl`\ -clicking when the active element is a disconnected root.

If the active element is a *disconnected root*:

- The new bone's root is placed on the active root.
- The new bone is **not** parented to the bone owning the active root
  (check the Outliner in Fig. :ref:`fig-rig-bone-disconnected-tip`).

And hence the new bone will **not** be connected to any bone.

.. TODO2.8 Update images (includes outliner)

.. _fig-rig-bone-connected-root:

.. figure:: /images/animation_armatures_bones_editing_extrude_mouse-clicks-4.png
   :width: 300px

   :kbd:`Ctrl`\ -clicking when the active element is a connected root.

If the active element is a *connected root*:

- The new bone's root is placed on the active root.
- The new bone **is** parented and connected to the parent of the bone owning the active root
  (check the Outliner in Fig. :ref:`fig-rig-bone-connected-root`).

This should be obvious because if the active element is a connected root
then the active element will be also the tip of the parent bone,
so it is the same as the second case.

As the tip of the new bone becomes the active element,
you can repeat these :kbd:`Ctrl-RMB` clicks several times,
to consecutively add several bones to the end of the same chain.


## Fill Between Joints

.. _bpy.ops.armature.fill:

*******************
Fill Between Joints
*******************

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Armature --> Fill Between Joints`
   :Shortcut:  :kbd:`F`

The main use of this tool is to create one bone between two selected joints by pressing
:kbd:`F`, similar to how in mesh editing you can "create edges/faces".

If you have one root and one tip selected, the new bone:

- Will have the root placed on the selected tip.
- Will have the tip placed on the selected root.
- Will be parented and connected to the bone owning the selected tip.

.. TODO2.8 Update images (includes outliner)

.. list-table:: Fill between a tip and a root.

   * - .. figure:: /images/animation_armatures_bones_editing_fill-between-joints_example-1.png

          Active tip on the left.

     - .. figure:: /images/animation_armatures_bones_editing_fill-between-joints_example-2.png

          Active tip on the right.

If you have two tips selected, the new bone:

- Will have the root placed on the selected tip closest to the 3D cursor.
- Will have the tip placed on the other selected tip.
- Will be parented and connected to the bone owning the tip used as the new bone's root.

.. TODO2.8 Update images (includes outliner)

.. list-table:: Fill between tips.

   * - .. figure:: /images/animation_armatures_bones_editing_fill-between-joints_example-3.png

          3D cursor on the left.

     - .. figure:: /images/animation_armatures_bones_editing_fill-between-joints_example-4.png

          3D cursor on the right.

If you have two roots selected, you will face a small problem due to the event system in
Blender not updating the interface in real-time.

When clicking :kbd:`F`, similar to the previous case, you will see a new bone:

- With the root placed on the selected root closest to the 3D cursor.
- With the tip placed on the other selected root.
- Parented and connected to the bone owning the root used as the new bone's root.

If you try to move the new bone, Blender will update the interface and you will see
that the new bone's root moves to the tip of the parent bone.

.. TODO2.8 Update images (includes outliner)

.. list-table:: Fill between roots.

   * - .. figure:: /images/animation_armatures_bones_editing_fill-between-joints_example-5.png

          Before UI update (3D cursor on the left).

     - .. figure:: /images/animation_armatures_bones_editing_fill-between-joints_example-6.png

          After UI update, correct visualization.

Clicking :kbd:`F` with only one bone joint selected will create a bone from the selected
joint to the 3D cursor position, and it will not parent it to any bone in the armature.

.. TODO2.8 Update images (includes outliner)

.. list-table:: Fill with only one bone joint selected.

   * - .. figure:: /images/animation_armatures_bones_editing_fill-between-joints_example-7.png

          Fill with only one tip selected.

     - .. figure:: /images/animation_armatures_bones_editing_fill-between-joints_example-8.png

          Fill with only one root selected.

You will get an error when:

- Trying to fill two joints of the same bone.
- Trying to fill more than two bone joints.


## Index

.. _bpy.types.EditBone:
.. _bpy.types.ArmatureEditBones:

###########
  Editing
###########

.. toctree::
   :maxdepth: 2

   introduction.rst
   transform.rst
   bone_roll.rst
   extrude.rst
   duplicate.rst
   fill_between_joints.rst
   split.rst
   separate_bones.rst
   subdivide.rst
   switch_direction.rst
   symmetrize.rst
   naming.rst
   parenting.rst
   properties.rst
   delete.rst


## Introduction


************
Introduction
************

As with any other object, you edit your armature in *Edit Mode* :kbd:`Tab`.

The set of bone editing tools is quite similar to the one for
:doc:`mesh </modeling/meshes/editing/introduction>` editing.

.. important::

   One important thing to understand about armature editing is that you
   edit the *rest position* of your armature, i.e. its "default state".
   An armature in its *rest position* has all bones with *no* rotation and scaled to 1.0 in their own local space.

The different :doc:`poses </animation/armatures/posing/index>`
you might create afterwards are based on this rest position.
So if you modify it in *Edit Mode*, all the poses already existing will also be modified.
Thus you should in general be sure that your armature is definitive before starting to
:doc:`skin </animation/armatures/skinning/index>` and :doc:`pose </animation/armatures/posing/index>` it!

.. note::

   Please note that some tools work on bones' joints, while others work on bones themselves.
   Be careful not to get confused.


Add Menu
========

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Add`
   :Shortcut:  :kbd:`Shift-A`

In the 3D Viewport, :kbd:`Shift-A` to add a new bone to your armature.

This bone will be:

- Of one unit of length.
- Oriented towards the global Z axis.
- With its root placed at the 3D cursor position.
- With no relationship with any other bone of the armature.


.. _animation_armatures_bones_locking:

Locking Bones
=============

You can prevent a bone from being transformed in *Edit Mode* in several ways:

.. The active bone can be locked clicking on *Lock*
   in the *Transform* panel (3D Viewport Sidebar):

- All bones can be locked clicking on the *Lock* checkbox
  of their Transform panel in the *Bones* tab;
- Press :kbd:`Shift-W` :menuselection:`Toggle Bone Options --> Locked`
- Select :menuselection:`Armature --> Bone Settings --> Toggle a Setting`.

*If the root of a locked bone is connected to the tip of an unlocked bone, it will not be locked*,
i.e. you will be able to move it to your liking.
This means that in a chain of connected bones, when you lock one bone,
you only really lock its tip. With unconnected bones, the locking is effective on both joints of the bone.


## Naming

.. _armature-editing-naming-bones:

******
Naming
******

.. reference::

   :Mode:      All Modes
   :Panel:     :menuselection:`Properties --> Bone Properties`

You can rename your bones, either using the *Name* field in the *Bones Properties*.
It is also possible to rename by double-clicking bones in the Outliner.

Blender also provides you some tools that take advantage of bones named in a left/right
symmetry fashion, and others that automatically name the bones of an armature.


.. _armature-editing-naming-conventions:

Naming Conventions
==================

Naming conventions in Blender are not only useful for you in finding the right bone,
but also to tell Blender when any two of them are counterparts.

In case your armature can be mirrored in half (i.e. it is bilaterally symmetrical),
it is worthwhile to stick to a left/right naming convention.
This will enable you to use some tools that will probably save you time and effort
(like the *X-Axis Mirror* editing tool).

.. figure:: /images/animation_armatures_bones_editing_naming_example.png

   An example of left/right bone naming in a simple rig.

#. First you should give your bones meaningful base-names,
   like "leg", "arm", "finger", "back", "foot", etc.
#. If you have a bone that has a copy on the other side (a pair),
   like an arm, give it one of the following separators:

   - Left/right separators can be either the second position
     "L\ **_**\ calfbone" or last-but-one "calfbone\ **.**\R".
   - If there is a lower or upper case "L", "R", "left" or "right", Blender handles the counterpart correctly.
     See below for a list of valid separators.
     Pick one and stick to it as close as possible when rigging; it will pay off.

   Examples of valid separators:

   - (nothing): handLeft --> handRight
   - "_" (underscore): hand\ **_**\L --> hand\ **_**\R
   - "." (dot): hand\ **.**\l --> hand\ **.**\r
   - "-" (dash): hand\ **-**\l --> hand\ **-**\r
   - " " (space): hand LEFT --> hand RIGHT

   .. note::

      Note that all examples above are also valid with the left/right part placed before the name.
      You can only use the short "L"/ "R" code if you use a separator (e.g. "handL"/ "handR" will not work!).

#. Before Blender handles an armature for mirroring or flipping,
   it first removes the number extension, e.g. ".001".
#. You can copy a bone named "bla.L" and flip it over using :ref:`bpy.ops.armature.flip_names`.
   Blender will name the copy "bla.L.001" and flipping the name will give you "bla.R".


.. _bpy.ops.armature.autoside_names:

Auto-Name
=========

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Armature --> Names --> Auto-Name Left/Right, Front/Back, Top/Bottom`

The three *AutoName* entries of the :menuselection:`Armature --> Names` menu allow you to
automatically add a suffix to all selected bones, based on the position of their root
relative to the armature's origin and its local coordinates:

AutoName Left/Right
   Will add the ".L" suffix to all bones with a *positive* X coordinate root,
   and the ".R" suffix to all bones with a *negative* X coordinate root.
   If the root is exactly at 0.0 on the X axis, the X coordinate of the tip is used.
   If both joints are at 0.0 on the X axis, the bone will just get a period suffix, with no "L"/ "R"
   (as Blender cannot decide whether it is a left or right bone...).
AutoName Front/Back
   Will add the ".Bk" suffix to all bones with a *positive* Y coordinate root,
   and the ".Fr" suffix to all bones with a *negative* Y coordinate root.
   The same as with *AutoName Left-Right* goes for 0.0 Y coordinate bones...
AutoName Top/Bottom
   Will add the ".Top" suffix to all bones with a *positive* Z coordinate root,
   and the ".Bot" suffix to all bones with a *negative* Z coordinate root.
   The same as with *AutoName Left-Right* goes for 0.0 Z coordinate bones...


.. _bpy.ops.armature.flip_names:

Flip Names
==========

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Armature --> Names --> Flip Names`

You can flip left/right markers (see above) in selected bone names.
This can be useful if you have constructed half of a symmetrical rig
(marked for a left or right side) and duplicated and mirrored it,
and want to update the names for the new side.
Blender will swap text in bone names according to the above naming conventions,
and remove number extensions if possible.


## Parenting

.. _bpy.ops.armature.parent_set:
.. _bpy.ops.armature.parent_clear:

*********
Parenting
*********

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Armature --> Parent`
   :Panel:     :menuselection:`Properties --> Bones --> Relations`
   :Shortcut:  :kbd:`Ctrl-P`, :kbd:`Alt-P`

You can edit the relationships between bones (and hence create/modify the chains of bones)
both from the 3D Viewport and the Properties. Whatever method you prefer,
it's always a matter of deciding, for each bone, if it has to be parented to another one,
and if so, if it should be connected to it.

To parent and/or connect bones, you can:

In the *3D Viewport*, select the bone and *then* its future parent, and press :kbd:`Ctrl-P`
(or :menuselection:`Armature --> Parent --> Make Parent...`).
In the small *Make Parent* menu that pops up, choose *Connected*
if you want the child to be connected to its parent, else click on *Keep Offset*.
If you have selected more than two bones, they will all be parented to the last selected one.
If you only select one already-parented bone, or all selected bones are already parented to the last selected one,
your only choice is to connect them, if not already done.
If you select only one non-parented bone, you will get the *Need selected bone(s)* error message...

.. note::

   With this method, the newly-children bones will not be scaled nor rotated --
   they will just be moved if you choose to connect them to their parent's tip.

In the *Properties*, Bones tab, for each selected bone,
you can select its parent in the *Parent* data ID to the upper right corner of its Relations panel.
If you want them to be connected, just enable the checkbox to the right of the list.

.. note::

   With this method, the tip of the child bone will never be moved --
   so if *Connected* is enabled, the child bone will be completely transformed by the operation.

.. list-table:: Parenting example.

   * - .. figure:: /images/animation_armatures_bones_editing_parenting_start.png

          The starting armature, with Bone.005 parented and connected to Bone.004.

     - .. figure:: /images/animation_armatures_bones_editing_parenting_unconnected.png

          Bone.005 re-parented to Bone.002, but not connected to it
          (same result, using either :kbd:`Ctrl-P 2` in 3D Viewport, or the Bones tab settings).

   * - .. figure:: /images/animation_armatures_bones_editing_parenting_connected.png

          Bone.005 parented and connected to Bone.002, using :kbd:`Ctrl-P 1` in 3D Viewport.

     - .. figure:: /images/animation_armatures_bones_editing_parenting_data-id.png

          Bone.005 parented and connected to Bone.002.

          Using the Parent data ID of Bone.005 Relations panel.

To disconnect and/or free bones, you can:

- In a 3D Viewport, select the desired bones, and press :kbd:`Alt-P`
  (or :menuselection:`Armature --> Parent --> Clear Parent...`).
  In the small *Clear Parent* menu that pops up, choose *Clear Parent* to completely free all selected bones,
  or *Disconnect Bone* if you just want to break their connections.
- In the Properties, *Bones* tab, for each selected bone, you can select no parent
  in the *Parent* data ID of its Relations panel, to free it completely.
  If you just want to disconnect it from its parent, disable the *Connected* checkbox.

Note that relationships with non-selected children are never modified.


.. _bpy.ops.armature.assign_to_collection:

Bone Collections
================

.. reference::

   :Mode:      Edit Mode, Pose Mode
   :Menu:      :menuselection:`Armature --> Bone Collections`, :menuselection:`Pose --> Bone Collections`

Manages the :ref:`bpy.types.BoneCollection` the bone is assigned to.

.. _bpy.ops.armature.move_to_collection:

Move to Collection :kbd:`M`
   Move bones to a collection.

Assign to Collection :kbd:`Shift-M`
   Assign all selected bones to a collection, or unassign them,
   depending on whether the active bone is already assigned or not.

----------

.. _bpy.ops.armature.collection_show_all:

Show All :kbd:`Ctrl-AccentGrave`
   Unhides any hidden bone collections.

.. _bpy.ops.armature.collection_create_and_assign:

Assign to new Collection
   Assigns the selected bones to a new collection named "New Collection".
   This collection can be renamed in the :ref:`bpy.types.BoneCollection` panel of the Armature properties.


## Properties

.. _armature-bone-properties:

**********
Properties
**********

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Armature --> Bone Settings --> ...`
   :Shortcut:  :kbd:`Shift-W`, :kbd:`Shift-Ctrl-W`, :kbd:`Alt-W`

Most bones' properties (except the transform ones) are regrouped in each bone's panels,
in the *Bones* tab in *Edit Mode*. Let us detail them.

Note that some of them are also available in the 3D Viewport,
through the three pop-up menus within the same entry:

- *Toggle Setting*: :kbd:`Shift-W` or :menuselection:`Armature --> Bone Settings --> Toggle a Setting`
- *Enable Setting*: :kbd:`Shift-Ctrl-W` or :menuselection:`Armature --> Bone Settings --> Enable a Setting`
- *Disable Setting*: :kbd:`Alt-W` or :menuselection:`Armature --> Bone Settings --> Disable a Setting`

Display Wire
   Always display the bone as wireframe.
Deform
   (also :kbd:`Shift-W` :menuselection:`--> (Deform, ...)`).
Multiply Vertex Group by Envelope
   (also :kbd:`Shift-W` :menuselection:`--> (Multiply Vertex Group by Envelope, ...)`).

   These settings control how the bone influences its geometry, along with the bones' joints radius.
   This will be detailed in the :doc:`skinning part </animation/armatures/skinning/index>`.
Inherit Rotation
   The bone automatically rotates together with its parent in *Pose Mode*. For more details,
   see the :ref:`relations page <bpy.types.EditBone.parent>`.
Lock
   (also :kbd:`Shift-W` :menuselection:`--> (Locked, ...)`)
   This will prevent all editing of the bone in *Edit Mode*;
   see :ref:`bone locking <animation_armatures_bones_locking>`.


## Separate Bones

.. _bpy.ops.armature.separate:

**************
Separate Bones
**************

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Armature --> Separate Bones`
   :Shortcut:  :kbd:`P`

You can, as with meshes, separate the selected bones in a new armature object
:menuselection:`Armature --> Separate`, :kbd:`Ctrl-Alt-P` and of course,
in *Object Mode*, you can join all selected armatures in one
:menuselection:`Object --> Join Objects`, :kbd:`Ctrl-J`.


## Split

.. _bpy.ops.armature.split:

*****
Split
*****

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Armature --> Split`
   :Shortcut:  :kbd:`Y`

Disconnects the selection and clears the parent at the start and end.
ToDo <2.8 add.


## Subdivide

.. _bpy.ops.armature.subdivide:

*********
Subdivide
*********

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Armature --> Subdivide`

You can subdivide bones, to get two or more bones where there was just one bone.
The tool will subdivide all selected bones, preserving the existing relationships:
the bones created from a subdivision always form a connected chain of bones.

To create an arbitrary number of bones from each selected bone
in the Subdivide Multi :ref:`bpy.ops.screen.redo_last` panel.

Number of Cuts
   Specifies the number of cuts. As in mesh editing,
   if you set *n* cuts, you will get *n* + 1 bones for each selected bone.

.. list-table:: Subdivision example.

   * - .. figure:: /images/animation_armatures_bones_editing_subdivide_example-1.png

          An armature with one selected bone, just before multi-subdivision.

     - .. figure:: /images/animation_armatures_bones_editing_subdivide_example-2.png

          The selected bone has been "cut" two times, giving three sub-bones.


## Switch Direction

.. _bpy.ops.armature.switch_direction:

****************
Switch Direction
****************

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Armature --> Switch Direction`
   :Shortcut:  :kbd:`Alt-F`

This tool allows you to switch the direction of the selected bones
(i.e. their root will become their tip, and vice versa).

Switching the direction of a bone will generally break the chain(s) it belongs to.
However, if you switch a whole (part of a) chain, the switched bones will still be parented/connected,
but in "reversed order". See the Fig. :ref:`fig-rig-properties-switch`.

.. _fig-rig-properties-switch:

.. list-table:: Switching example.

   * - .. figure:: /images/animation_armatures_bones_editing_switch-direction_example-1.png

          An armature with one selected bone, and one selected chain of three bones, just before switching.

     - .. figure:: /images/animation_armatures_bones_editing_switch-direction_example-2.png

          The selected bones have been switched. Bone.005 is no more connected nor parented to anything.
          The chain of switched bones still exists, but reversed (now Bone.002 is its root, and Bone is its tip).
          Bone.003 is now a free bone.


## Symmetrize

.. _bpy.ops.armature.symmetrize:

**********
Symmetrize
**********

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Armature --> Symmetrize`

This operator will mirror the selected bones along the X axis based on
Blender's bone :ref:`naming convention <armature-editing-naming-conventions>` for symmetrical armatures,
either from left to right or right to left, depending on the selection.

.. note::

   If the side of the bone cannot be determined, it will be ignored.

Bones with the opposite names that don't yet exist will be created, and already existing ones will be overwritten.
If matching bones are selected on both sides, mirroring will happen from right to left.

Symmetrized bone and constraint properties will have the necessary changes to mirror their behaviors.
When symmetrizing bones with :doc:`Action Constraints </animation/constraints/relationship/action>`,
the necessary keyframes will be added to the target Action to result
in symmetrical movement when the Action is activated.

.. note::

   Note that bone or constraint drivers will not be created or affected in any way.


## Transform


*********
Transform
*********

.. figure:: /images/animation_armatures_bones_editing_transform_panel.png
   :align: right
   :width: 165px
   :figwidth: 165px

   The Transform panel for armatures in Edit Mode.

We will not detail here the various transformations of bones, nor things like axis locking, pivot points, and so on,
as they are common to most object editing, and already described in
the :doc:`mesh section </scene_layout/object/editing/transform/control/index>`.
The same goes for mirroring,
as it is nearly the same as with :doc:`mesh editing </modeling/meshes/editing/mesh/mirror>`.
Just keep in mind that bones' roots and tips behave more or less like meshes' vertices,
and bones themselves act like edges in a mesh.

As you know, bones can have two types of relationships: They can be parented,
and in addition connected. Parented bones behave in *Edit Mode* exactly as if they
had no relations. They can be moved, rotated, scaled, etc. without affecting their descendants.
However, connected bones must always have parent's tips connected to child's roots,
so by transforming a bone, you will affect all its connected parent/children/siblings.

While with other transform tools, the "local axes" means the object's axes,
here they are the bone's own axes (when you lock to a local axis,
by pressing the relevant key twice, the constraint is applied along the selected bone's local axis,
not the armature object's axis).

Finally, you can edit in the *Transform* panel in the Sidebar region
the positions and radius of both joints of the active selected bone,
as well as its :ref:`roll rotation <armature-bone-roll>`.


Scale Radius
============

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Armature --> Transform --> Scale Radius`
   :Shortcut:  :kbd:`Alt-S`

You can alter the radius that a bone has by selecting the head, body or tail of a bone,
and then press :kbd:`Alt-S` and move the mouse left or right.
If the body is selected the mean radius will be scaled.
And as usual, with connected bones, you scale at the same time the radius
of the parent's tip and of the children's roots.

You can also alter the bone radius by selecting the tail or head of the bone you wish to alter,
then navigate to :menuselection:`Properties --> Bone --> Deform --> Radius Section`
and entering new values for the *Tail* and *Head* number fields.

.. list-table:: Bone Scale and Scale Radius comparison.

   * - .. figure:: /images/animation_armatures_bones_selecting_single-bone.png

          A single selected bone in Octahedron visualization.

     - .. figure:: /images/animation_armatures_bones_editing_transform_scaling-bone-radius-2.png

          After normal scale.

   * - .. figure:: /images/animation_armatures_bones_editing_transform_scaling-bone-radius-3.png

          A single selected bone in Envelope visualization.

     - .. figure:: /images/animation_armatures_bones_editing_transform_scaling-bone-radius-4.png

          After Scaled Radius. Its length remains the same, but its joints' radius are bigger.

Note that, when you resize a bone (either by directly scaling it, or by moving one of its joints),
Blender automatically adjusts the end-radii of its envelope proportionally to the size of the modification.
Therefore, it is advisable to place all the bones first, and only then edit their properties.


Scale Envelope Distance
=======================

.. reference::

   :Mode:      Edit Mode and Pose Mode
   :Menu:      :menuselection:`Armature --> Transform --> Scale Envelope Distance`
   :Shortcut:  :kbd:`Ctrl-Alt-S`

You can alter the size of the Bone Envelope volume by clicking on the body of the bone you want to alter,
:kbd:`Ctrl-Alt-S` then drag your mouse left or right and the Bone Envelope volume will alter accordingly.

You can also alter the Bone Envelope volume by selecting the Bone you wish to alter and
then navigate to :menuselection:`Properties --> Bone --> Deform --> Envelope --> Distance`
then enter a new value into it.

Altering the Bone Envelope volume does not alter the size of the bone just the range
within which it can influence vertices of child objects.

.. list-table:: Envelope scaling example.

   * - .. figure:: /images/animation_armatures_bones_editing_transform_scaling-bone-radius-3.png

          A single bone selected in Envelope visualization.

     - .. figure:: /images/animation_armatures_bones_editing_transform_scaling-bone-radius-5.png

          Its envelope distance scaled.

.. list-table:: "Bone size" scaling example.

   * - .. figure:: /images/animation_armatures_bones_editing_transform_scaling-bone-size-1.png

          A single "default size" bone selected in B-Bone visualization.

     - .. figure:: /images/animation_armatures_bones_editing_transform_scaling-bone-size-2.png

          Its envelope distance scaled.

     - .. figure:: /images/animation_armatures_bones_editing_transform_scaling-bone-size-3.png

          The same armature in Object Mode and B-Bone visualization, with Bone.004's size scaled up.


.. _bpy.ops.armature.align:

Align Bones
===========

.. reference::

   :Mode:      Edit Mode
   :Menu:      :menuselection:`Armature --> Transform --> Align Bones`
   :Shortcut:  :kbd:`Ctrl-Alt-A`

Rotates the selected bones to achieve the same orientation as the active one.


## Bendy Bones

.. (todo 2.78 add) images: https://code.blender.org/2016/05/
.. an-in-depth-look-at-how-b-bones-work-including-details-of-the-new-bendy-bones/

.. _bendy-bones:

***********
Bendy Bones
***********

.. reference::

   :Mode:      All Modes
   :Panel:     :menuselection:`Bone --> Bendy Bones`

Bendy Bones (B-Bones) are an easy way to replace long chains of many small rigid bones.
A common use case for curved bones is to model spine columns or facial bones.


Technical Details
=================

Blender treats the bone as a section of a Bézier curve passing through the bones' joints.
Each of the *Segments* will bend and roll to follow this invisible curve
representing a tessellated point of the Bézier curve.
The control points at each end of the curve are the endpoints of the bone.
The shape of the B-Bones can be controlled using a series of properties or
indirectly through the neighboring bones (i.e. first child and parent).
The properties construct handles on either end of the bone to control the curvature.

.. move to constraint > common?

When using the B-bone as a constraint target :ref:`ui-data-id` offers an option to follow the curvature.

.. note::

   However, if the bone is used as a target rather than to deform geometry,
   only *Armature* and *Copy Transforms* constraints will use the full
   transformation including roll and scale.


Display
=======

You can see these segments only if bones are visualized as *B-bones*.

When not visualized as *B-Bone*\ s, bones are always shown as rigid sticks,
even though the bone segments are still present and effective.
This means that even in e.g. *Octahedron* visualization,
if some bones in a chain have several segments,
they will nonetheless smoothly deform their geometry.


Rest Pose
=========

The initial shape of a B-Bone can be defined in Edit Mode as a rest pose of that bone.
This is useful for curved facial features like curved eyebrows or mouths.

B-Bones have two sets of the Bendy Bone properties -- one for Edit Mode (i.e. the Rest Pose/Base Rig) and
another for Pose Mode -- adding or multiplying together their values to get the final transforms.


Example
=======

.. list-table::

   * - .. _fig-rig-bone-intro-bbone:

       .. figure:: /images/animation_armatures_bones_properties_bendy-bones_b-bones-1.png

          Bones with just one segment in Edit Mode.

     - .. figure:: /images/animation_armatures_bones_properties_bendy-bones_b-bones-2.png

          The Bézier curve superposed to the chain, with its handles placed at bones' joints.

   * - .. _fig-rig-bone-intro-same:

       .. figure:: /images/animation_armatures_bones_properties_bendy-bones_b-bones-3.png

          The same armature in Object Mode.

     - ..

In Fig. :ref:`fig-rig-bone-intro-bbone` we connected three bones,
each one made of five segments.

Look at Fig. :ref:`fig-rig-bone-intro-same`,
we can see how the bones' segments smoothly "blend" into each other, even for roll.

.. figure:: /images/animation_armatures_bones_properties_bendy-bones_pose-mode.png

   An armature in Pose Mode, B-Bone visualization: Bone.003 has one segment,
   Bone.004 has four, and Bone.005 has sixteen.


Options
=======

.. figure:: /images/animation_armatures_bones_properties_bendy-bones_options.png
   :align: right

   Bendy Bones panel.

.. _bpy.types.EditBone.bbone_segments:

Segments
   The number of segments, which the given bone is subdivided into.
   Segments are small, rigid linked child bones that interpolate between the root and the tip.
   The higher this setting, the smoother "bends" the bone, but the heavier the pose calculations.

.. _bpy.types.EditBone.bbone_x:
.. _bpy.types.EditBone.bbone_z:

Display Size X, Z
   Controls the visible thickness of the bone segments when the armature is rendered in the *B-Bones* mode.

.. _bpy.types.EditBone.bbone_mapping_mode:

Vertex Mapping
   Controls how vertices are weighted to the individual segments of a B-Bone for deformations:

   :Straight:
      A fast mapping that works well for B-Bones with a straight or gently curved rest pose.
   :Curved:
      A slower mapping that improves deformations for B-Bones with a strongly curved rest pose. This should
      be used selectively when needed.

   .. figure:: /images/animation_armatures_bones_properties_bendy-bones_vertex-mapping.png
      :width: 300px

      Straight vs Curved vertex mapping on a B-Bone with a strongly curved rest pose.

.. _bpy.types.EditBone.bbone_curveinx:
.. _bpy.types.EditBone.bbone_curveinz:

Curve In/Out X, Y, Z
   Applies offsets to the curve handle positions on the plane perpendicular to the bone's primary (Y) axis.
   As a result, the handle moves per axis (XZ) further from its original location, causing the curve to bend.

.. _bpy.types.EditBone.bbone_rollin:
.. _bpy.types.EditBone.bbone_rollout:

Roll In, Out
   The roll value (or twisting around the main Y axis of the bone) is interpolated per segment,
   between the start and end roll values.
   It is applied as a rotational offset on top of the rotation defined by the handle bones.

.. _bpy.types.EditBone.use_endroll_as_inroll:

Inherit End Roll
   If enabled, the *Roll Out* value of the *Start Handle* bone (connected parent by default)
   will be implicitly added to the *Roll In* setting of the current bone.

.. _bpy.types.EditBone.bbone_scalein:
.. _bpy.types.EditBone.bbone_scaleout:

Scale In/Out X, Y, Z
   Scaling factors that adjust the thickness of each segment for the X and Z axes,
   or introduce non-uniform spacing along the Y axis. Similar to *Roll* it is
   interpolated per segment.

   Since all segments are still uniformly scaled in the Y direction to fit the actual length of the curve,
   only the ratio between *Scale In Y* and *Scale Out Y* actually matters.

.. _bpy.types.EditBone.bbone_easein:
.. _bpy.types.EditBone.bbone_easeout:

Ease In, Out
   The *Ease In/Out* number fields, change the "length" of the :ref:`"auto" <curve-handle-type-auto>` Bézier handle
   to control the "root handle" and "tip handle" of the bone, respectively.
   These values are proportional to the default length,
   which of course automatically varies depending on bone length,
   angle with the reference handle, and so on.

   Although easing is a scale-like value, the Edit Mode and Pose Mode versions of the values are added,
   so they get corresponding start values of 1 and 0 by default.

   .. list-table:: Ease In/Out settings example, with a materialized Bézier curve.

      * - .. figure:: /images/animation_armatures_bones_properties_bendy-bones_curve-in-out-1.png
             :width: 320px

             Bone.004 with default In and Out (1.0).

        - .. figure:: /images/animation_armatures_bones_properties_bendy-bones_curve-in-out-2.png
             :width: 320px

             Bone.004 with In at 2.0, and Out at 0.0.

.. _bpy.types.EditBone.use_scale_easing:

Scale Easing
   If enabled, the final easing values are implicitly multiplied by the corresponding *Scale Y* values.


Custom Handles
--------------

B-Bones can use custom bones as their reference bone handles, instead of only using the connected parent/child bones.

.. _bpy.types.EditBone.bbone_handle_type_start:
.. _bpy.types.EditBone.bbone_handle_type_end:

Start/End Handle
   Specifies the type of the handle from the following choices:

   :Automatic:
      The connected parent (or first connected child) of the bone is chosen as the handle.
      Calculations are done according to the *Absolute* handle type below.
   :Absolute:
      The Bézier handle is controlled by the **position** of the head (tail)
      of the handle bone relative to the head (tail) of the current bone.
      Note that for this to work, there must be a nonzero distance between these bones.
      If the handle is also a B-Bone, additional processing is applied to further
      smooth the transition, assuming that the bones in effect form a chain.
   :Relative:
      The Bézier handle is controlled by the **offset** of the head (tail) of the handle bone from its rest pose.
      The use of this type is not recommended due to numerical stability issues near zero offset.
   :Tangent:
      The Bézier handle is controlled by the **orientation** of the handle bone, independent of its location.

.. _bpy.types.EditBone.bbone_custom_handle_start:
.. _bpy.types.EditBone.bbone_custom_handle_end:

Custom Handle
   For types other than *Automatic*, a bone to use as handle has to be manually selected.
   Switching to a custom handle type without selecting a bone can be used to effectively disable the handle.

   It is valid for two bones to refer to each other as handles -- this correlation is applied
   in connected chains with *Automatic* handles.

.. _bpy.types.EditBone.bbone_handle_use_scale_start:
.. _bpy.types.EditBone.bbone_handle_use_scale_end:
.. _bpy.types.EditBone.bbone_handle_use_ease_start:
.. _bpy.types.EditBone.bbone_handle_use_ease_end:

Scale X/Y/Z/Ease
   If enabled, the final Scale and/or Ease values are multiplied by the corresponding local scale
   channels of the handle bone. This step is applied independently of *Scale Easing* and doesn't
   interact with it, i.e. enabling *Y* and *Scale Easing* doesn't replace the *Ease* toggle.
   These toggles are a more efficient replacement for up to eight trivial drivers passing segment scale data
   from the handle bones into the B-Bone option properties.

.. tip:: Keying Set

   The "BBone Shape" :doc:`Keying Set </animation/keyframes/keying_sets>` includes all Bendy Bones properties.

.. figure:: /images/animation_armatures_bones_properties_bendy-bones_settings-demo.png

   Visualization of the Bendy Bones properties.

   From Left: 1) Curve X/Y offsets, 2) Scale In/Out, 3) Roll In/Out


## Custom Properties


*****************
Custom Properties
*****************

.. reference::

   :Mode:      Pose Mode
   :Panel:     :menuselection:`Bone --> Custom Properties`

See the :ref:`Custom Properties <files-data_blocks-custom-properties>` page for more information.


## Deform

.. _bpy.types.Bone.use_deform:

******
Deform
******

.. reference::

   :Mode:      All Modes
   :Panel:     :menuselection:`Bone --> Deform`

.. figure:: /images/animation_armatures_bones_properties_deform_panel.png

   The Deform panel.

In this panel you can set deformation options for each bone.

Toggling the checkbox in the panel header off,
prevents the bone from deforming the geometry at all,
overriding any weights that it might have been assigned before; it mutes its influence.

It also excludes the active bone in the automatic weight calculation when the mesh is
parented to the armature using the *Armature Deform* tool with the *With Automatic Weights* option.


.. _armature-bones-envelope:

Envelope
========

.. figure:: /images/animation_armatures_bones_structure_envelope-edit-mode.png
   :align: right
   :figwidth: 180px

   Bone influence areas for envelopes method.

Envelopes is the most general skinning method. It works with all available object types for
skinning (meshes, lattices, curves, surfaces and texts).
It is based on proximity between bones and their geometry,
each bone having two different areas of influence,
shown in the *Envelope* visualization:

- The inside area, materialized by the "solid" part of the bone, and controlled by both root and tip radius.
- The outside area, materialized by the lighter part around the bone,
  and controlled by the *Distance* setting.

.. container:: lead

   .. clear

.. seealso::

   The :doc:`editing pages </animation/armatures/bones/editing/transform>` for how to edit these properties.

.. _bpy.types.Bone.envelope_distance:

Envelope Distance
   The Distance defines a volume which is the range within the bone
   has an influence on vertices of the deformed object.
   The geometry is less and less affected by the bone as it goes away by following a quadratic decay.

   .. figure:: /images/animation_armatures_bones_properties_deform_envelope-distance.png

      Single bone with various envelope sizes.

.. _bpy.types.Bone.envelope_weight:

Envelope Weight
   A bone property, that controls the global influence of the bone over the deformed object,
   when using the envelopes method.

   It is only useful for the parts of geometry that are "shared",
   influenced by more than one bone (generally, at the joints...) -- a bone with a high weight will
   have more influence on the result than one with a low weight...
   Note that when set to 0.0, it has the same effect as disabling the *Deform* option.

.. _bpy.types.Bone.use_envelope_multiply:

Envelope Multiply
   This option controls how the two deforming methods interact, when they are both enabled.
   By default, when they are both active, all vertices belonging to at least one vertex group are only deformed
   through the vertex groups method. The other "orphan" vertices being handled by the envelopes one.
   When you enable this option, the "deformation influence" that this bone would have on a vertex
   (based from its envelope settings) is multiplied with this vertex's weight in the corresponding vertex group.
   In other words, the vertex groups method is further "weighted" by the envelopes method.

.. _bpy.types.Bone.head_radius:
.. _bpy.types.Bone.tail_radius:

Radius Head, Tail
   Set the radius for the head and the tail of envelope bones.
   Inside this volume, the geometry if fully affected by the bone.

   .. figure:: /images/animation_armatures_bones_properties_deform_envelope-radius.png

      Three Armature Bones all using Envelope Weight.

      The 1st with a default radius value, the two others with differing Tail and Head radius values.


## Display

.. _bpy.types.Bone.color:
.. _bpy.types.EditBone.color:
.. _bpy.types.PoseBone.color:

****************
Viewport Display
****************

.. reference::

   :Mode:      Object, Pose, and Edit Mode
   :Panel:     :menuselection:`Bone --> Viewport Display`

This panel lets you customize the look of your bones.

.. figure:: /images/animation_armatures_bones_properties_display.png

   Viewport Display panel in Object/Pose mode.

.. figure:: /images/animation_armatures_bones_properties_display_editmode.png

   Viewport Display panel in Edit mode.

General
=======

.. _bpy.types.Bone.hide:

Hide
   Hides the bone in the 3D Viewport. When this is unchecked, the bone's
   visibility is determined by the visibility of its :ref:`bone collections <bpy.types.Bone.collections>`.

.. _bpy.types.BoneColor.palette:
.. _bpy.types.BoneColor:
.. _bpy.types.ThemeBoneColorSet:

Bone Colors
===========

Bones can be individually colored. You can either choose a color set from the predefined
:ref:`theme <bpy.types.Theme>` list or define a custom one.

.. figure:: /images/animation_armatures_bones_properties_display_custom_colors.png

When selecting *Custom Color Set*, you need to define three colors:
Regular (for when the bone is not selected), Selected, and Active.

You can temporarily disable all the color assignments by unchecking
:ref:`Bone Colors <bpy.types.Armature.show>` in the armature's Viewport Display panel.

Bone Color
   The bone's primary color, affecting both Edit Mode and Pose Mode.

   This color is stored on the armature data-block, so that if you have
   multiple armature objects that share this data-block, they will all use
   the same color.

   .. _bpy.ops.armature.copy_bone_color_to_selected:

   Copy Bone Color to Selected
      Copy the bone color of the :term:`Active` bone to all selected bones.

Pose Bone Color :guilabel:`Pose Mode`
   Lets you optionally override the above *Bone Color* in Pose Mode
   (by setting it to something else than *Default Colors*).

   This color is stored on the :term:`Pose Bone`, meaning it can be different
   in every armature object -- even ones that reference the same data-block.

   Copy Bone Color to Selected
      Copy the bone color of the :term:`Active` bone to all selected bones.


.. _bpy.types.PoseBone.custom_shape:

Custom Shape
============

Apart from custom colors, bones can also have custom shapes (in *Object Mode*
and *Pose Mode*), using another object as a "template."

.. figure:: /images/animation_armatures_bones_properties_display_custom-shape-example.png

   A bone referencing a cone as its Custom Shape.

You can temporarily disable these shapes by unchecking
*Shapes* in the armature's Viewport Display panel.

Custom Object
   Object that defines the custom shape of the selected bone.

Scale X, Y, Z
   Additional scaling factor to apply to the custom shape.

Translation X, Y, Z
   Additional translation to apply to the custom shape.

Rotation X, Y, Z
   Additional rotation to apply to the custom shape.

Override Transform
   Bone that defines the display transform of the custom shape.

Scale to Bone Length
   Whether the custom shape should be scaled by a factor equal to the bone's length.


.. _bpy.types.Bone.show_wire:

Wireframe
   When enabled, the bone is displayed in wireframe mode regardless of the viewport's shading mode.

.. note::

   - Custom shapes will never be rendered. Like regular bones, they are only visible in the 3D Viewport.
   - The transforms of the template object are ignored. Moving, rotating, or scaling it will have no
     effect on its appearance in the armature.
   - The origin of each instanced shape object is at the :doc:`root </animation/armatures/bones/structure>`
     of the bone.
   - The rotation of each shape object is such that its Y axis lies along the direction of the bone.
   - For best results when *Scale to Bone Length* is enabled, make sure the template object is 1 unit
     in size along its Y axis. This will make it perfectly match the size of each bone.


## Index


##############
  Properties
##############

.. reference::

   :Mode:      Object Mode, Edit Mode and Pose Mode
   :Panel:     :menuselection:`Properties --> Bone`

When bones are selected (hence in *Edit Mode* and *Pose Mode*), their
properties are shown in the *Bone* tab of the Properties.
This shows different panels used to control features of each selected bone;
the panels change depending on which mode you are working in.

.. toctree::
   :maxdepth: 2

   transform.rst
   bendy_bones.rst
   relations.rst
   inverse_kinematics.rst
   deform.rst
   display.rst
   custom_properties.rst


## Inverse Kinematics


******************
Inverse Kinematics
******************

.. reference::

   :Mode:      Pose Mode
   :Panel:     :menuselection:`Bone --> Inverse Kinematics`

.. figure:: /images/animation_armatures_bones_properties_inverse-kinematics_panel.png

   The Inverse Kinematics panel.

This panel controls the way a bone or set of bones behave when linked in
an :doc:`inverse kinematic </animation/armatures/posing/bone_constraints/inverse_kinematics/introduction>` chain.


## Relations


.. _properties_data_bone_relations:

*********
Relations
*********

.. reference::

   :Mode:      All Modes
   :Panel:     :menuselection:`Bone --> Relations`

.. figure:: /images/animation_armatures_bones_properties_relations_panel.png

   Bone Relations panel.

In this panel you can manage the relationship of this bone with its parent bone.
It also shows the bone collections the bone is assigned to.


Parenting
=========

.. _bpy.types.EditBone.parent:

Parent
   A :ref:`ui-data-id` to select the bone to set as a parent.

.. _bpy.types.Bone.use_relative_parent:

Relative Parenting :guilabel:`Pose Mode Only`
   Changes how transformation of the bone is applied to its child Objects.

.. _bpy.types.EditBone.use_connect:

Connected
   The *Connected* checkbox set the head of the bone to be connected with its parent root.


Transformations
---------------

Bones relationships have effects on transformations behavior.

By default, children bones inherit:

- Their parent position, with their own offset of course.
- Their parent rotation (i.e. they keep a constant rotation relatively to their parent).
- Their parent scale, here again with their own offset.

.. list-table:: Examples of transforming parented/connected bones.

   * - .. figure:: /images/animation_armatures_bones_properties_relations_rest.png
          :width: 200px

          The armature in its rest position.

     - .. figure:: /images/animation_armatures_bones_properties_relations_root-rotation.png
          :width: 200px

          Rotation of a root bone.

     - .. figure:: /images/animation_armatures_bones_properties_relations_root-scale.png
          :width: 200px

          Scaling of a root bone.

Exactly like standard children objects. You can modify this behavior on a per-bone basis,
using the Relations panel in the *Bones* tab:

.. _bpy.types.EditBone.use_local_location:

Local Location
   When disabled, the location transform property is evaluated in the parent bone's local space,
   rather than using the bone's own *rest pose* local space orientation.

.. _bpy.types.EditBone.use_inherit_rotation:

Inherit Rotation
   When disabled, this will "break" the rotation relationship to the bone's parent.
   This means that the child will keep its rotation in the armature object space when its parent is rotated.

.. _bpy.types.EditBone.inherit_scale:

Inherit Scale
   Specifies which effects of parent scaling the bone inherits:

   These inheriting behaviors propagate along the bones' hierarchy.
   So when you scale down a bone, all its descendants are by default scaled down accordingly.
   However, if you disable one bone's *Inherit Scale* or *Inherit Rotation*
   property in this "family", this will break the scaling propagation,
   i.e. this bone *and all its descendants* will no longer be affected when you scale one of its ancestors.

   :Full:
      The bone inherits all effects of parent scaling and shear.
   :Fix Shear:
      Full parent effects are applied to the rest state of the child, after which any shear is
      removed in a way that preserves the bone direction, length and volume, and minimally affects
      roll on average. The result is combined with the local transformation of the child.

      If the inherited scale is non-uniform, this does not prevent shear from reappearing due to
      local rotation of the child bone, or of its children.
   :Aligned:
      Parent scaling is inherited as if the child was oriented the same as the parent, always
      applying parent X scale over child X scale, and so on.
   :Average:
      Inherits a uniform scaling factor that is the total change in the volume of the parent.
   :None:
      Ignores all scaling and shear of the parent.
   :None (Legacy):
      Ignores all scaling, provided the parent is not sheared. If it is, there are no guarantees.

      This choice replicates the behavior of the old Inherit Scale checkbox, and may be removed in a future release.

   .. tip::

      The various *Inherit Scale* options are provided as tools in avoiding shear that is caused
      by non-uniform scaling combined with parenting and rotation. There is no obvious best way
      to achieve that, so different options are useful for different situations.

      - **None** --
        Useful for gaining full control over the scaling of the child in order
        to e.g. manually overwrite it with constraints.
      - **Average** --
        Useful to block squash and stretch propagation between sub-rigs, while
        allowing uniform changes in the size and volume to pass through.
      - **Aligned** --
        Can be used within bone chains, e.g. tentacles, in order to propagate
        lengthwise scaling as lengthwise, and sideways as sideways, no matter
        how the tentacle bends. Similar to using *None* with
        :doc:`Copy Scale </animation/constraints/transform/copy_scale>` from parent.
      - **Fix Shear** --
        May be useful at the base of an appendage in order to reallocate squash and stretch
        between axes based on the difference in rest pose orientations of the parent and child.
        It behaves closest to *Full* while suppressing shear.

   .. list-table:: Examples of transforming parented/connected bones with Inherit Rotation disabled.

      * - .. figure:: /images/animation_armatures_bones_properties_relations_inherit-rot-disabled.png

             The yellow outlined Inherit Rotation disabled bone in the armature.

        - .. figure:: /images/animation_armatures_bones_properties_relations_inherit-rot-disabled-descendant.png

             Rotation of a bone with an Inherit Rotation disabled bone among its descendants.

        - .. figure:: /images/animation_armatures_bones_properties_relations_inherit-rot-disabled-scale.png

             Scaling of a bone with an Inherit Rotation disabled bone among its descendants.

Connected bones have another specificity: they cannot be moved. Indeed,
as their root must be at their parent's tip, if you do not move the parent,
you cannot move the child's root, but only its tip, which leads to a child rotation.
This is exactly what happens, when you press :kbd:`G` with a connected bone selected,
Blender automatically switches to rotation operation.

Bones relationships also have important consequences on how selections of multiple bones
behave when transformed. There are many different situations which may not be included on this list,
however, this should give a good idea of the problem:

- Non-related selected bones are transformed independently, as usual.
- When several bones of the same "family" are selected,
  *only* the "most parent" ones are really transformed --
  the descendants are just handled through the parent relationship process, as if they were not selected
  (see Fig. :ref:`fig-rig-pose-edit-scale` the third tip bone,
  outlined in yellow, was only scaled down through the parent relationship,
  exactly as the unselected ones, even though it is selected and active.
  Otherwise, it should have been twice smaller!)

  .. _fig-rig-pose-edit-scale:

  .. figure:: /images/animation_armatures_bones_properties_relations_scale-related.png
     :align: center
     :width: 320px

     Scaling bones, some of them related.

- When connected and unconnected bones are selected,
  and you start a move operation, only the unconnected bones are affected.
- When a child connected hinge bone is in the selection,
  and the "most parent" selected one is connected, when you press :kbd:`G`,
  nothing happens, because Blender remains in move operation, which of course has no effect on a connected bone.

So, when posing a chain of bones, you should always edit its elements from the root bone to the tip bone.
This process is known as :term:`Forward Kinematics` (FK).
We will see in a :ref:`later page <bone-constraints-inverse-kinematics>`
that Blender features another pose method, called :term:`Inverse Kinematics` (IK),
which allows you to pose a whole chain just by moving its tip.

.. note::

   This feature is somewhat extended/completed by
   the :doc:`pose library </animation/armatures/posing/editing/pose_library>`.


.. _bpy.types.Bone.collections:
.. _bpy.types.EditBone.collections:
.. _bpy.types.PoseBone.collections:

Bone Collections
================

This list shows the :term:`bone collections <Bone Collection>` the bone is assigned to.
Press the eye icon to show or hide the entire bone collection.
Press the star icon to show only this bone collection, and others also marked as 'solo'
Press the X icon to remove the bone from that particular collection.

To assign the bone to other bone collections, either use the :kbd:`M` or :kbd:`Shift-M` shortcuts
(see :ref:`Moving Bones Between Collections <moving_bones_between_collections>`)
or go to the :ref:`Armature properties panel <bpy.types.BoneCollection>`.


## Transform


*********
Transform
*********

.. reference::

   :Mode:      Edit Mode and Pose Mode
   :Panel:     :menuselection:`Bone --> Transform`

.. TODO2.8
   .. list-table::

      * - .. figure:: /images/animation_armatures_bones_properties_transform_panel-edit.png

             The Transform panel (Edit Mode).

        - .. figure:: /images/animation_armatures_bones_properties_transform_panel-pose.png

             The Transform panel (Pose Mode).

When in *Edit Mode* you can use this panel to control position and roll of individual bones.
Whereas in *Pose Mode* you can only set location for the main bone, and you can now set rotation and scale.

In addition, in *Pose Mode* it is possible to restrict changes in position,
rotation and scale by axis on each bone in the armature.

.. _bpy.types.EditBone.head:

Head X, Y, Z
   Location of head end of the bone.

.. _bpy.types.EditBone.tail:

Tail X, Y, Z
   Location of tail end of the bone.

.. _bpy.types.EditBone.roll:

Roll
   Bone rotation around head-tail axis.

.. _bpy.types.EditBone.lock:

Lock
   Bone is not able to be transformed when in Edit Mode.


## Index


#########
  Tools
#########

.. toctree::
   :maxdepth: 2

   toolbar.rst
   tool_settings.rst


## Toolbar


*******
Toolbar
*******

Mesh Edit Mode tools:

:ref:`Select <tool-select-tweak>`
   Select or move.

   :ref:`Select Box <tool-select-box>`
      Select geometry by dragging a box.
   :ref:`Select Circle <tool-select-circle>`
      Select geometry by dragging a circle.
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

:ref:`Roll <tool-bone-role>`
   Rotates a bone around its local Y axis.

Bone Size
   Todo.

   Bone Envelope
      Todo.

Extrude
   Creates a new bone connected to the last selected joint.

   Extrude to Cursor
      Creates a new bone between the last selected joint and the mouse position.

Shear
   Todo.


## Tool Settings


*************
Tool Settings
*************

Options
=======

.. _bpy.types.Armature.use_mirror_x:

X-Axis Mirror
-------------

See :ref:`X-Axis Mirror Pose Mode <bpy.types.Pose.use_mirror_x>`.


## Index

.. _posing-index:
.. _bpy.types.Pose:
.. _bpy.ops.pose:

##########
  Posing
##########

.. toctree::
   :maxdepth: 2

   introduction.rst
   selecting.rst
   editing/index.rst
   tool_settings.rst
   bone_constraints/index.rst


## Introduction


************
Introduction
************

Once an armature is :doc:`skinned </animation/armatures/skinning/index>` by the needed object(s),
you need a way to configure the armature into positions known as poses.
Basically, by transforming the bones, you deform or transform the skinned object(s).
However, you will notice that you cannot do this in *Edit Mode* --
remember that *Edit Mode* is used to edit the default, base, or "rest" position of an armature.
You may also notice that you cannot use *Object Mode* either, as here you can only transform whole objects.

So, armatures have a third mode dedicated to the process of posing known as *Pose Mode*.
In rest position (as edited in *Edit Mode*), each bone has its own position/rotation/scale to neutral values
(i.e. 0.0 for position and rotation, and 1.0 for scale). Hence, when you edit a bone in *Pose Mode*,
you create an offset in the transform properties, from its rest position.
This may seem quite similar if you have worked with :doc:`relative shape keys </animation/shape_keys/index>`
or :ref:`Delta Transformations <bpy.types.Object.delta>`.

Even though it might be used for completely static purposes,
posing is heavily connected with animation features and techniques.
So if you are not familiar at all with animation in Blender,
it might be a good idea to read the :doc:`animation chapter </animation/index>` first,
and then come back here.


Visualization
=============

Bone State Colors
-----------------

The color of the bones are based on their state.
There are six different color codes, ordered here by precedence
(i.e. the bone will be of the color of the bottom-most valid state):

.. hue rotation based on the bone solid.

- Gray: Default.
- Blue wire-frame: in Pose Mode.
- Green: with Constraint.
- Yellow: with :doc:`IK Solver constraint </animation/constraints/tracking/ik_solver>`.
- Orange: with Targetless Solver constraint.

.. note::

   When :ref:`bone colors <bpy.types.BoneColor>` are enabled,
   the state colors will be overridden.


## Selecting


*********
Selecting
*********

Selection in *Pose Mode* is very similar to the one in :doc:`Edit Mode </animation/armatures/bones/selecting>`,
with a few deviations:
You can only select *whole bones* in *Pose Mode*, not roots/tips...


.. _bpy.ops.pose.select_all:

All
===

.. reference::

   :Mode:      Pose Mode
   :Menu:      :menuselection:`Select --> All`
   :Shortcut:  :kbd:`A`

Select all selectable bones.


None
====

.. reference::

   :Mode:      Pose Mode
   :Menu:      :menuselection:`Select --> None`
   :Shortcut:  :kbd:`Alt-A`

Deselect all bones, but the active bone stays the same.


Invert
======

.. reference::

   :Mode:      Pose Mode
   :Menu:      :menuselection:`Select --> Invert`
   :Shortcut:  :kbd:`Ctrl-I`

Toggle the selection state of all visible bones.


Box Select
==========

.. reference::

   :Mode:      Pose Mode
   :Menu:      :menuselection:`Select --> Box Select`
   :Shortcut:  :kbd:`B`

Interactive :ref:`box selection <tool-select-box>`.


Circle Select
=============

.. reference::

   :Mode:      Pose Mode
   :Menu:      :menuselection:`Select --> Circle Select`
   :Shortcut:  :kbd:`C`

Interactive :ref:`circle selection <tool-select-circle>`.


Lasso Select
============

.. reference::

   :Mode:      Pose Mode
   :Menu:      :menuselection:`Select --> Lasso Select`
   :Shortcut:  :kbd:`Ctrl-Alt-LMB`

See :ref:`tool-select-lasso`.


.. _bpy.ops.pose.select_mirror:

Select Mirror
=============

.. reference::

   :Mode:      Pose Mode
   :Menu:      :menuselection:`Select --> Select Mirror`
   :Shortcut:  :kbd:`Shift-Ctrl-M`

Flip the selection from one side to another.


.. _bpy.ops.pose.select_hierarchy:

Select More/Less
================

.. reference::

   :Mode:      Pose Mode
   :Menu:      :menuselection:`Select --> More/Less`

Parent :kbd:`[`, Child :kbd:`]`
   You can deselect the active bone and select its immediate parent or one of its children.
Extend Parent :kbd:`Shift-[`, Extend Child :kbd:`Shift-]`
   Similar to *Parent*/*Child* but it keeps the active bone in the selection.


.. _bpy.ops.pose.select_grouped:

Select Grouped
==============

.. reference::

   :Mode:      Pose Mode
   :Menu:      :menuselection:`Select --> Select Grouped`
   :Shortcut:  :kbd:`Shift-G`

You can select bones, based on various properties, through the *Select Grouped* pop-up menu :kbd:`Shift-G`:

Collection
   Selects all bones that are share at least one bone collection with the active bone.
Color
   Selects all bones that have the same color as the active bone.
Keying Set
   All bones affected by active :doc:`Keying Set </animation/keyframes/keying_sets>`


.. _bpy.ops.pose.select_linked:

Select Linked
=============

.. reference::

   :Mode:      Pose Mode
   :Menu:      :menuselection:`Select --> Select Linked`
   :Shortcut:  :kbd:`Ctrl-L`

Selects all the bones in the chain which the active (last selected) bone belongs to.

All Forks
   Selects all bones connected to the active bone even if the branch off from the current bone.

.. list-table:: Linked bones selection.

   * - .. figure:: /images/animation_armatures_bones_selecting_single-bone.png
          :width: 320px

          A single selected bone.

     - .. figure:: /images/animation_armatures_bones_selecting_whole-chain.png
          :width: 320px

          Its whole chain selected with Linked.


Select Pattern
==============

.. reference::

   :Mode:      Pose Mode
   :Menu:      :menuselection:`Select --> Select Pattern...`

Selects all bones whose name matches a given pattern.
Supported wild-cards: \* matches everything, ? matches any single character,
[abc] matches characters in "abc", and [!abc] match any character not in "abc".
As an example \*house\* matches any name that contains "house",
while floor\* matches any name starting with "floor".

Case Sensitive
   The matching can be chosen to be case sensitive or not.
Extend
   When *Extend* checkbox is checked the selection is extended instead of generating a new one.


.. _bpy.ops.pose.select_constraint_target:

Constraint Target
=================

.. reference::

   :Mode:      Pose Mode
   :Menu:      :menuselection:`Select --> Constraint Target`

Select bones used as targets for the currently selected bones


## Tool Settings


*************
Tool Settings
*************

Pose Options
============

.. _bpy.types.Pose.use_auto_ik:

Auto IK
-------

.. reference::

   :Mode:      Pose Mode
   :Panel:     :menuselection:`Sidebar --> Tool --> Pose Options --> Auto IK`

Automatic IK is a tool for quick posing, when enabled, translating a bone will activate
inverse kinematics and rotate the parent bone, and the parent's parent, and so on, to
follow the selected bone. The IK chain can only extend from a child to a parent bone
if the child is *connected* to it.

While moving bones, the length of the chain (the number of affected bones)
can be increased or decreased using keyboard hotkeys.
Pressing :kbd:`PageUp` will increase in chain length by one
and :kbd:`PageDown` decreases the length by one.
The chain length can also be controlled with :kbd:`WheelUp` or :kbd:`WheelDown`.

The initial chain length is 0, which effectively means follow
the connections to parent bones as far as possible, with no length limit.
So pressing increasing the chain length the first time sets the length to 1 (move only the selected bone),
and at this point, decreasing the length point sets it back to 0 (unlimited) again.
Thus, you have to increase the chain length *more than once* from the initial state
to set a finite chain length greater than 1.

This is a more limited feature than using an IK constraint,
which can be configured, but it can be useful for quick posing.


.. _bpy.types.Pose.use_mirror_x:

X-Axis Mirror
-------------

.. reference::

   :Mode:      Edit and Pose Mode
   :Panel:     :menuselection:`Sidebar --> Tool --> Options --> X-Axis Mirror`

This option enables automatic mirroring of editing actions along the X axis.
You can enable this option in the :menuselection:`Tool tab --> Options panel`,
while the armature is selected in *Edit Mode*.
When you have pairs of bones of the same name with just a different "side suffix"
(e.g. ".R"/".L", or "_right"/"_left" ...), once this option is enabled,
each time you transform (move, rotate, scale...) a bone,
its "other side" counterpart will be transformed accordingly,
through a symmetry along the armature local X axis.
As most rigs have at least one axis of symmetry (animals, humans, ...),
it is an easy way to keep the model symmetrical.


Relative Mirror
---------------

.. reference::

   :Mode:      Edit and Pose Mode
   :Panel:     :menuselection:`Sidebar --> Tool --> Options --> Relative Mirror`

Accounts for any relative transformations when using *X-Axis Mirror*.

.. seealso::

   :ref:`Naming bones <armature-editing-naming-bones>`.


Known Limitations
=================

Relative Mirror is not supported with `Auto IK`_ enabled.


## Index

.. index:: Constraint; Bone Constraints
.. _bpy.types.PoseBoneConstraints:

####################
  Bone Constraints
####################

.. toctree::
   :maxdepth: 1

   introduction.rst


.. _bone-constraints-inverse-kinematics:

Inverse Kinematics
==================

.. toctree::
   :maxdepth: 1

   inverse_kinematics/introduction.rst
   inverse_kinematics/spline_ik.rst


## Introduction


************
Introduction
************

.. figure:: /images/animation_armatures_posing_bone-constraints_introduction_tab.png
   :align: right
   :figwidth: 280px
   :width: 280px

   The Bone Constraints Properties in Pose Mode,
   with an Inverse Kinematics constraint added to the active bone.

As bones behave like objects in *Pose Mode*, they can also be constrained.
This is why the *Constraints* tab is shown in both *Object Mode* and *Edit Mode*.
This panel contains the constraints *of the active bone*
(its name is displayed at the top of the panel, in the *To Bone:...* static text field).

Constraining bones can be used to control their degree of freedom
in their pose transformations, using e.g. the *Limit* constraints.
You can also use constraints to make a bone track another object/bone
(inside the same object, or in another armature), etc.
And the :ref:`inverse kinematics feature <bone-constraints-inverse-kinematics>`
is also mainly available through the *IK Solver* constraint, which is specific to bones.

For example, a human elbow cannot rotate backward (unless the character has broken their arm),
nor to the sides, and its forward and roll rotations are limited in a given range.
(E.g. depending on the rest position of your elbow, it may be from (0 to 160) or from (-45 to 135).)

So you should apply a *Limit Rotation* constraint to the forearm bone
(as the elbow movement is the result of rotating the forearm bone around its root).

Using bones in constraints, either as owners or as targets, is discussed in detail
in the :doc:`constraints pages </animation/constraints/index>`.


## Introduction


************
Introduction
************

Inverse Kinematics (IK) simplifies the animation process,
and makes it possible to make more advanced animations with lesser effort.

Inverse Kinematics allow you to position the last bone in a bone chain and
the other bones are positioned automatically.
This is like how moving someone's finger would cause their arm to follow it.
By normal posing techniques, you would have to start from the root bone,
and set bones sequentially until you reach the tip bone:
When each parent bone is moved, its child bone would inherit its location and rotation.
Thus making tiny precise changes in poses becomes harder farther down the chain,
as you may have to adjust all the parent bones first.

This effort is effectively avoided by use of IK.

IK is mostly done with bone constraints although there is also
a simple :ref:`bpy.types.Pose.use_auto_ik` feature in Pose Mode.
They work by the same method but the constraints offer more options and control.
Please refer to the following pages for details about these constraints:

- :doc:`IK Solver </animation/constraints/tracking/ik_solver>`
- :doc:`Spline IK </animation/constraints/tracking/spline_ik>`


Armature IK Panel
=================

.. reference::

   :Mode:      Pose Mode
   :Panel:     :menuselection:`Properties --> Armature --> Inverse Kinematics`

This panel is used to select the IK Solver type for the armature: *Standard* or *iTaSC*.
Most the time people will use the *Standard* IK solver.

.. TODO2.8
   .. figure:: /images/animation_armatures_posing_bone-constraints_inverse-kinematics_introduction_panel.png

      The armature IK panel.


Standard
--------

TODO.


.. _bpy.types.Itasc:
.. _rigging-armatures_posing_bone-constraints_ik_model_itasc:

iTaSC
-----

.. This is rather technical and can be simplified.

iTaSC stands for instantaneous Task Specification using Constraints.

iTaSC uses a different method to compute the Jacobian, which makes it able to handle other constraints than
just end effectors position and orientation: iTaSC is a generic multi-constraint IK solver.
However, this capability is not yet fully exploited in the current implementation,
only two other types of constraints can be handled: Distance in the Cartesian space,
and Joint Rotation in the joint space. The first one allows maintaining an end effector
inside, at, or outside a sphere centered on a target position,
the second one is the capability to control directly the rotation of a bone relative to its parent.
Those interested in the mathematics can find a short description of the method used to build the Jacobian here.

iTaSC accepts a mix of constraints, and multiple constraints per bone:
the solver computes the optimal pose according to the respective weights of each constraint.
This is a major improvement from the current constraint system where constraints are solved
one by one in order of definition so that conflicting constraints overwrite each other.

Precision
   The maximum variation of the end effector between two successive iterations
   at which a pose is obtained that is stable enough and the solver should stop the iterations.
   Lower values means higher precision on the end effector position.
Iterations
   The upper bound for the number of iterations.
Solver
   Selects the inverse Jacobian solver that iTaSC will use.

   :abbr:`SDLS (Selective Damped Least Square)`
      Computes the damping automatically by estimating the level of 'cancellation' in the armature kinematics.
      This method works well with the Copy Pose constraint but has the drawback of damping more than
      necessary around the singular pose, which means slower movements.
      Of course, this is only noticeable in Simulation mode.
   :abbr:`DLS (Damped Least Square)`
      Computes the damping manually which can provide more reactivity and more precision.

      Damping Max
         Maximum amount of damping. Smaller values means less damping, hence more velocity
         and better precision but also more risk of oscillation at singular pose. 0 means no damping at all.
      Damping Epsilon
         Range of the damping zone around singular pose. Smaller values means a smaller zone
         of control and greater risk of passing over the singular pose, which means oscillation.

      .. note::

         *Damping* and *Epsilon* must be tuned for each armature.
         You should use the smallest values that preserve stability.

   .. note::

      - The SDLS solver does not work together with a Distance constraint.
        You must use the DLS solver if you are going to have a singular pose
        in your animation with the Distance constraint.
      - Both solvers perform well if you do not have a singular pose.


Animation
^^^^^^^^^

In Animation mode, iTaSC operates like an IK solver:
it is stateless and uses the pose from F-Curves interpolation as the start pose before the IK convergence.
The target velocity is ignored and the solver converges until the given precision is obtained.
Still the new solver is usually faster than the old one and provides features that are inherent to iTaSC:
multiple targets per bone and multiple types of constraints.


Simulation
^^^^^^^^^^

The Simulation mode is the stateful mode of the solver: it estimates the target's velocity,
operates in a 'true time' context, ignores rotation from keyframes
(except via a joint rotation constraint) and builds up a state cache automatically.

Reiteration
   Never
      The solver starts from the rest pose and does not reiterate (converges) even for the first frame.
      This means that it will take a few frames to get to the target at the start of the animation.
   Initial
      The solver starts from the rest pose and re-iterates until the given precision is achieved,
      but only on the first frame (i.e. a frame which doesn't have any previous frame in the cache).
      This option basically allows you to choose a different start pose than the rest pose
      and it is the default value. For the subsequent frames, the solver will track the target
      by integrating the joint velocity computed by the Jacobian solver over the time interval
      that the frame represents. The precision of the tracking depends on the feedback coefficient,
      number of substeps and velocity of the target.
   Always
      The solver re-iterates on each frame until the given precision is achieved.
      This option omits most of the iTaSC dynamic behavior: the maximum joint velocity
      and the continuity between frames is not guaranteed anymore in compensation of better
      precision on the end effector positions. It is an intermediate mode
      between *Animation* and real-time *Simulation*.
Auto Step
   Use this option if you want to let the solver set how many substeps should be executed for each frame.
   A substep is a subdivision on the time between two frames for which the solver evaluates
   the IK equation and updates the joint position. More substeps means more processing but better precision
   on tracking the targets. The auto step algorithm estimates the optimal number of steps to get
   the best trade-off between processing and precision. It works by estimation of the nonlinearity
   of the pose and by limiting the amplitude of joint variation during a substep.
   It can be configured with next two parameters:

   Min
      Proposed minimum substep duration (in second).
      The auto step algorithm may reduce the substep further based on joint velocity.
   Max
      Maximum substep duration (in second). The auto step algorithm will not allow substep longer than this value.
Steps
   If Auto Step is disabled, you can choose a fixed number of substeps with this parameter.
   Substep should not be longer than 10 ms, which means the number of steps is 4 for a 25 fps animation.
   If the armature seems unstable (vibrates) between frames,
   you can improve the stability by increasing the number of steps.
Feedback
   Coefficient on end effector position error to set corrective joint velocity.
   The time constant of the error correction is the inverse of this value.
   However, this parameter has little effect on the dynamic of the armature
   since the algorithm evaluates the target velocity in any case.
   Setting this parameter to 0 means 'opening the loop':
   the solver tracks the velocity but not the position; the error will accumulate rapidly.
   Setting this value too high means an excessive amount of correction and risk of instability.
   The value should be in the range 20-100. Default value is 20, which means that tracking errors
   are corrected in a typical time of 100-200 ms.
   The feedback coefficient is the reason why the armature continues to move slightly
   in Simulation mode even if the target has stopped moving: the residual error
   is progressively suppressed frame after frame.
Max Velocity
   Indicative maximum joint velocity in radian per second.
   This parameter has an important effect on the armature dynamic.
   Smaller value will cause the armature to move slowly and lag behind if the targets are moving rapidly.
   You can simulate an inertia by setting this parameter to a low value.


.. _bpy.types.PoseBone.ik:

Bone IK Panel
=============

.. reference::

   :Mode:      Pose Mode
   :Panel:     :menuselection:`Properties --> Bone --> Inverse Kinematics`

This panel is used to control how the *Pose Bones* work in the IK chain.

.. TODO2.8
   .. figure:: /images/animation_armatures_bones_properties_inverse-kinematics_panel.png

      The bone IK panel.

IK Stretch
   Stretch influence to IK target.
Lock
   Disallow movement around the axis.
Stiffness
   Stiffness around the axis. Influence disabled if using *Lock*.
Limit
   Limit movement around the axis.


.. _bpy.types.PoseBone.use_ik_rotation_control:
.. _bpy.types.PoseBone.ik_rotation_weight:

iTaSC Solver
------------

If the :ref:`iTaSC IK Solver <rigging-armatures_posing_bone-constraints_ik_model_itasc>`
is used, the bone IK panel changes to add these additional parameters.

Control Rotation
   Activates a joint rotation constraint on that bone.
   The pose rotation computed from Action or UI interaction will be converted
   into a joint value and passed to the solver as target for the joint.
   This will give you control over the joint while the solver still tracks the other IK targets.
   You can use this feature to give a preferred pose for joints (e.g. rest pose)
   or to animate a joint angle by playing an action on it.

   Weight
      The importance of the joint rotation constraint based on the constraints weight
      in case all constraints cannot be achieved at the same time.
      For example, if you want to enforce strongly the joint rotation,
      set a high weight on the joint rotation constraint and a low weight on the IK constraints.


Arm Rig Example
===============

This arm uses two bones to overcome the twist problem for the forearm.
IK locking is used to stop the forearm from bending,
but the forearm can still be twisted manually by pressing :kbd:`R Y Y` in *Pose Mode*,
or by using other constraints.

.. figure:: /images/animation_armatures_posing_bone-constraints_inverse-kinematics_introduction_example.png
   :align: center

   `IK Arm Example <https://archive.blender.org/wiki/2015/index.php/File:IK_Arm_Example.blend>`__.

Note that, if a *Pole Target* is used, IK locking will not work on the root bone.


## Spline Ik


*********
Spline IK
*********

Spline IK is a constraint which aligns a chain of bones along a curve. By leveraging the ease
and flexibility of achieving aesthetically pleasing shapes offered by curves and
the predictability and well-integrated control offered by bones,
Spline IK is an invaluable tool in the riggers' toolbox.
It is particularly well suited for rigging flexible body parts such as tails, tentacles,
and spines, as well as inorganic items such as ropes.

Full description of the settings for the spline IK can be found on
the :doc:`Spline IK </animation/constraints/tracking/spline_ik>` page.


Basic Setup
===========

The Spline IK Constraint is not strictly an *Inverse Kinematics* method (i.e. IK Constraint),
but rather a *Forward Kinematics* method (i.e. normal bone posing). However,
it still shares some characteristics of the IK Constraint,
such as operating on multiple bones, not being usable for Objects,
and being evaluated after all other constraints have been evaluated. It should be noted that
if a Standard IK chain and a Spline IK chain both affect a bone at the same time the Standard
IK chain takes priority. Such setups are best avoided though,
since the results may be difficult to control.

To setup Spline IK,
it is necessary to have a chain of connected bones and a curve to constrain these bones to:

#. With the last bone in the chain selected,
   add a :doc:`Spline IK </animation/constraints/tracking/spline_ik>`
   Constraint from the Bone Constraints tab in the Properties.
#. Set the *Chain Length* setting to the number of bones in the chain
   (starting from and including the selected bone) that should be influenced by the curve.
#. Finally, set the *Target* field to the curve that should control the curve.

Congratulations, the bone chain is now controlled by the curve.


Settings and Controls
=====================

For the precise list of options, see :doc:`Spline IK </animation/constraints/tracking/spline_ik>` constraint.
This section is intended to introduce the workflow.


Roll Control
------------

To control the :term:`Roll` of the Spline IK chain,
the standard methods of rotating the bones in the chain along their local Y axes still apply.
For example, start at the farthest bone and simply rotate the bones in the chain around their
local Y axes to adjust the roll of the chain from that point onward.

Applying Copy Rotation constraints on the bones also works.

.. note::

   There are a couple of limitations to consider:

   - Bones do not inherit a curve's :ref:`tilt <modeling-curve-tilt>` value to control their roll.

   - There is no way of automatically creating a twisting effect
     where a dampened rotation is inherited up the chain.
     Consider using :doc:`Bendy Bones </animation/armatures/bones/properties/bendy_bones>` instead.


Offset Controls
---------------

The entire bone chain can be made to follow the shape of the curve while still being able to
be placed at an arbitrary point in 3D space when the *Chain Offset* option is enabled.
By default, this option is not enabled,
and the bones will be made to follow the curve in its untransformed position.


Length Control
--------------

The *Y Scale Mode* setting can be used to choose the way bones are scaled length-wise.
The available options allow stretching the bone chain to fit the curve, using the pre-IK
scaling, or doing neither. In addition, the scale of the curve Object affects the result.


Thickness Controls
------------------

The thickness of the bones in the chain is controlled using the constraint's *XZ Scale Mode* setting.
This setting determines the method used for determining the scaling on
the X and Z axes of each bone in the chain.

The available modes are:

None
   This option keeps the X and Z scaling factors as 1.0.
Volume Preserve
   The X and Z scaling factors are taken as the inverse of the Y scaling factor (length of the bone),
   maintaining the 'volume' of the bone.
Bone Original
   This options just uses the X and Z scaling factors the bone would have after being evaluated in the standard way.

In addition to these modes, there is an option, *Use Curve Radius*.
When this option is enabled, the average radius of the radii of the points on the curve where
the joints of each bone are placed, are used to derive X and Z scaling factors.
This allows the scaling effects, determined using the modes above,
to be tweaked as necessary for artistic control.


Tips for Nice Setups
====================

- For optimal deformations, it is recommended that the bones are roughly the same length,
  and that they are not too long, to facilitate a better fit to the curve.
  Also, bones should ideally be created in a way that follows the shape of the curve in its 'rest pose' shape,
  to minimize the problems in areas where the curve has sharp bends
  which may be especially noticeable when stretching is disabled.
- For control of the curve, it is recommended that hooks (in particular, Bone Hooks)
  are used to control the control points of the curve, with one hook per control point.
  In general, only a few control points should be needed for the curve
  (e.g. one for every 3-5 bones offers decent control).
- The type of curve used does not really matter,
  as long as a path can be extracted from it that could also be used by the Follow Path Constraint.
  This really depends on the level of control required from the hooks.


## Apply

.. _bpy.ops.pose.armature_apply:

*****
Apply
*****

.. reference::

   :Mode:      Pose Mode
   :Menu:      :menuselection:`Pose --> Apply`
   :Shortcut:  :kbd:`Ctrl-A`

Pose as Rest Pose
   Conversely, you may define the current pose as the new rest pose
   (i.e. "apply" current transformations to the *Edit Mode*). When you do so,
   the skinned objects/geometry is **also** reset to its default,
   undeformed state, which generally means you will have to skin it again.

Pose Selected as Rest Pose
   Same as *Pose as Rest Pose* but only applies to selected bones.

.. _bpy.ops.pose.visual_transform_apply:

Visual Transform to Pose
   Applies the position of the bone after :doc:`/animation/constraints/index`;
   allowing the constraints to be deleted and the bones will remain in their constrained positions.

.. _bpy.ops.object.assign_property_defaults:

Assign Custom Property Values as Default
   Assign the current values of custom properties as their defaults,
   for use as part of the rest pose state in NLA track mixing.


## Clear


***************
Clear Transform
***************

.. reference::

   :Mode:      Pose Mode
   :Menu:      :menuselection:`Pose --> Clear Transform`

Once you have transformed some bones, if you want to return to their rest position,
just clear their transformations.

.. _bpy.ops.pose.transforms_clear:

All
   Resets location, rotation, and scaling of selected bones to their default values.

.. _bpy.ops.pose.loc_clear:
.. _bpy.ops.pose.rot_clear:
.. _bpy.ops.pose.scale_clear:

Location, Rotation, Scale :kbd:`Alt-G`, :kbd:`Alt-R`, :kbd:`Alt-S`
   Clears individual transforms.

   Note that in *Envelope* visualization, :kbd:`Alt-S` does not clear the scale,
   but rather scales the *Distance* influence area of the selected bones.
   (This is also available through the :menuselection:`Pose --> Scale Envelope Distance` menu entry,
   which is only effective in *Envelope* visualization, even though it is always available...)

.. _bpy.ops.pose.user_transforms_clear:

Reset Unkeyed
   Clears the transforms to their keyframe state.

   Only Selected
      Operate on just the selected or all bones.


## Copy Paste

.. |copy-paste| image:: /images/animation_armatures_posing_editing_copy-paste_buttons.png
.. _bpy.ops.pose.copy:
.. _bpy.ops.pose.paste:

***************
Copy/Paste Pose
***************

.. reference::

   :Mode:      Pose Mode
   :Menu:      :menuselection:`Pose --> Copy Pose`,
               :menuselection:`Pose --> Paste Pose`,
               :menuselection:`Pose --> Paste Pose Flipped`
   :Shortcut:  :kbd:`Ctrl-C`,
               :kbd:`Ctrl-V`,
               :kbd:`Shift-Ctrl-V`

Blender allows you to copy and paste a pose, either through the *Pose* menu, or
by using hotkeys.

Copy Pose
   Copy the current pose of selected bones into the pose buffer.
Paste Pose
   Paste the buffered pose to the currently posed armature.
Paste Pose Flipped
   Paste the *X axis mirrored* buffered pose to the currently posed armature.

Here are important points:

- This tool works at the :term:`Blender session` level, which means you can use it across
  armatures, scenes, and even files. However, the pose buffer is not saved, so you lose it when you
  close Blender.
- There is only one pose buffer.
- Only the selected bones are taken into account during copying (i.e. you copy only selected bones' pose).
- During pasting, on the other hand, bone selection has no importance.
  The copied pose is applied on a per-name basis
  (i.e. if you had a ``forearm`` bone selected when you copied the pose,
  the ``forearm`` bone of the current posed armature will get its pose when you paste it --
  and if there is no such named bone, nothing will happen...).
- What is copied and pasted is in fact the position, rotation or scale of each bone, in its own space.
  This means that the resulting pasted pose might be very different from the originally copied one, depending on:

  - The rest position of the bones.
  - And the current pose of their parents.

.. list-table::

   * - .. figure:: /images/animation_armatures_posing_editing_copy-paste_examples-1.png

          The rest position of the original armature.

     - .. figure:: /images/animation_armatures_posing_editing_copy-paste_examples-2.png

          The rest position of the destination armature.

.. list-table:: Examples of pose copy/paste.

   * - .. figure:: /images/animation_armatures_posing_editing_copy-paste_examples-3.png

          The first copied pose (note that only two bones are selected and hence copied).

     - .. figure:: /images/animation_armatures_posing_editing_copy-paste_examples-4.png

          The pose pasted on the destination armature.

     - .. figure:: /images/animation_armatures_posing_editing_copy-paste_examples-5.png

          The pose mirror-pasted on the destination armature.

   * - .. figure:: /images/animation_armatures_posing_editing_copy-paste_examples-6.png

          The same pose as above is copied, but this time with all bones selected.

     - .. figure:: /images/animation_armatures_posing_editing_copy-paste_examples-7.png

          The pose pasted on the destination armature.

     - .. figure:: /images/animation_armatures_posing_editing_copy-paste_examples-8.png

          The pose mirror-pasted on the destination armature.


## Flip Quats

.. _bpy.ops.pose.quaternions_flip:

**********
Flip Quats
**********

.. reference::

   :Mode:      Pose Mode
   :Menu:      :menuselection:`Pose --> Flip Quats`
   :Shortcut:  :kbd:`Alt-F`

Flip quaternion values to achieve desired rotations, while maintaining the same orientations.

.. todo add example


## Index


###########
  Editing
###########

.. toctree::
   :maxdepth: 2

   introduction.rst
   clear.rst
   apply.rst
   in_betweens.rst
   propagate.rst
   copy_paste.rst
   pose_library.rst
   flip_quats.rst
   show_hide.rst


## Introduction


************
Introduction
************

.. TODO2.8
   .. figure:: /images/animation_armatures_posing_editing_introduction_tools.png
      :align: right

      Pose Tools.

In *Pose Mode*, bones behave like objects. So the transform actions
(move, rotate, scale, etc.) are very similar to the same ones in Object Mode
(all available ones are regrouped in the :menuselection:`Pose --> Transform` submenu). However,
there are some important specifics:

- Bones' relationships are crucial (see :ref:`Bone Parenting <bpy.types.EditBone.parent>`).
- The "transform center" of a given bone
  (i.e. its default pivot point, when it is the only selected one) is *its root*.
  Note by the way that some pivot point options seem to not work properly. In fact,
  except for the *3D Cursor* one, all others appear to always use the median point of the selection
  (and not e.g. the active bone's root when *Active Object* is selected, etc.).


Basic Posing
============

As previously noted, bones' transformations are performed based on the *Rest Position* of
the armature, which is its state as defined in *Edit Mode*. This means that in
rest position, in *Pose Mode*, each bone has a scale of 1.0, and null rotation
and position (as you can see it in the *Transform* panel, in the 3D Viewport's Sidebar).

.. TODO2.8 Maybe update the images (color & style)

.. figure:: /images/animation_armatures_posing_editing_introduction_local-rotation.png

   An example of a rotation locked to the local Y axis, with two bones selected.

   Note that the two green lines materializing the axes are centered on the armature's center,
   and not each bone's root...

Moreover, the local space for these actions is the bone's own one
(visible when you enable the *Axes* option of the *Armature* panel).
This is especially important when using axis locking, for example,
there is no specific "bone roll" tool in *Pose Mode*,
as you can rotate around the bone's main axis just by locking on the local Y axis
:kbd:`R Y Y`... This also works with several bones selected;
each one is locked to its own local axis!

When you pose your armature,
you are supposed to have one or more objects skinned on it! And obviously,
when you transform a bone in *Pose Mode*,
its related objects or object's shape is moved/deformed accordingly, in real-time.
Unfortunately, if you have a complex rig set-up and/or a heavy skin object,
this might produce lag during interactive editing.
If you experience such troubles, try enabling the *Delay Deform* button in
the *Armature* panel the skin objects will only be updated once you confirm
the transform operation.


## In Betweens


***********
In-Betweens
***********

.. figure:: /images/animation_armatures_posing_editing_in-betweens_tools.png
   :align: right

   In-Betweens Tools.

There are several tools for editing poses in an animation.

There are also in *Pose Mode* a bunch of armature-specific editing options/tools,
like :ref:`auto-bones naming <armature-editing-naming-bones>`,
:ref:`properties switching/enabling/disabling <armature-bone-properties>`, etc.,
that were already described in the armature editing pages. See the links above...


.. _bpy.ops.pose.push_rest:

Push Pose from Rest Pose
========================

.. reference::

   :Mode:      Pose Mode
   :Menu:      :menuselection:`Pose --> In-Betweens --> Push Pose from Rest Pose`

Similar to *Push Pose from Breakdown* but interpolates the pose to the rest position instead.
Only one keyframe is needed for this tool unlike two for the other.


.. _bpy.ops.pose.relax_rest:

Relax Pose to Rest Pose
=======================

.. reference::

   :Mode:      Pose Mode
   :Menu:      :menuselection:`Pose --> In-Betweens --> Relax Pose to Rest Pose`

Similar to *Relax Pose to Breakdown* but works to bring the pose back to the rest position instead.
Only one keyframe is needed for this tool unlike two for the other.


.. _bpy.ops.pose.push:

Push Pose from Breakdown
========================

.. reference::

   :Mode:      Pose Mode
   :Tool:      :menuselection:`Toolbar --> In-Betweens Tools --> Push`
   :Menu:      :menuselection:`Pose --> In-Betweens --> Push Pose from Breakdown`
   :Shortcut:  :kbd:`Ctrl-E`

*Push Pose* interpolates the current pose by making it closer to the next keyframed position.


.. _bpy.ops.pose.relax:

Relax Pose to Breakdown
=======================

.. reference::

   :Mode:      Pose Mode
   :Tool:      :menuselection:`Toolbar --> In-Betweens Tools --> Relax`
   :Menu:      :menuselection:`Pose --> In-Betweens --> Relax Pose to Breakdown`
   :Shortcut:  :kbd:`Alt-E`

Relax pose is somewhat related to the above topic, but it is only useful with keyframed bones.
When you edit such a bone (and hence take it "away" from its "keyed position"),
using this tool will progressively "bring it back" to its "keyed position",
with smaller and smaller steps as it comes near it.


.. _bpy.ops.pose.breakdown:

Pose Breakdowner
================

.. reference::

   :Mode:      Pose Mode
   :Tool:      :menuselection:`Toolbar region --> In-Betweens Tools --> Breakdowner`
   :Menu:      :menuselection:`Pose --> In-Betweens --> Pose Breakdowner`
   :Shortcut:  :kbd:`LMB`-drag

Creates a suitable breakdown pose on the current frame.

The Breakdowner tool can be constrained to work on specific transforms and axes,
by pressing the following keys while the tool is active:

- :kbd:`G`, :kbd:`R`, :kbd:`S`: move, rotate, scale
- :kbd:`B`: Bendy bones
- :kbd:`C`: custom properties
- :kbd:`X`, :kbd:`Y`, :kbd:`Z`: to the corresponding axes


.. _bpy.ops.pose.blend_to_neighbor:

Blend to Neighbor
=================

.. reference::

   :Mode:      Pose Mode
   :Menu:      :menuselection:`Pose --> In-Betweens --> Blend to Neighbor`
   :Shortcut:  :kbd:`Shift-Alt-E`

Transitions the current pose with the neighboring keyframes in the timeline.
In order for this operator to work, there must be a keyframe before and after the current frame.


## Pose Library


.. _bpy.ops.poselib:

************
Pose Library
************

This section describes the pose library, which is based on the :doc:`/editors/asset_browser`.
For an overview of the asset system, see the :doc:`/files/asset_libraries/index` section.
The pose library is meant to be used in Pose Mode. In other words, it only works
when posing an armature, and not for general object animation.

.. note::

   The pose library is implemented as an add-on. This add-on is enabled by
   default; disabling it will remove the pose library from Blender's user
   interface.

   The "building blocks" of the pose library are actually implemented in Blender
   itself. The add-on only contains the user interface and the logic that
   determines what is stored in a pose asset. This was intentionally put into an
   add-on, so that artists or studios who want to change the behavior can do
   so with an add-on of their own.

What is a Pose Asset?
=====================

A *pose asset* is an action that has been :ref:`marked as asset <asset-create>`,
and that contains exactly **one frame of animation** data.
Usually these are created via the *Create Pose Asset* button (see below),
but any action that is keyed on exactly one frame can be seen as pose asset.

Each pose in the library is stored in its own action data-block.
This means that it can get its own name, its own preview image,
and can be organized in :doc:`/files/asset_libraries/catalogs`.


.. _bpy.ops.poselib.create_pose_asset:

Creating a Pose Library
=======================

A *pose library file* is typically a blend-file that is dedicated to poses.
It can link in a character, props, etc., which can then not only be used to create the poses,
but also for :ref:`rendering previews <poselib-preview-images>`.

.. figure:: /images/asset_browser-pose_library_ellie.png

   Example pose library of the Sprite Fright character Ellie.


Pose Creation via Action Editor
-------------------------------

To create a pose in the library from the Action Editor, **pose the character,
select the relevant bones**, and click the *Create Pose Asset* button.
This will create the new pose Action, which will contain keys for the current value of
each bone's location, rotation, scale, and Bendy Bone properties.

.. figure:: /images/asset_browser-pose_library-create_from_action_editor.png

   To create a new pose asset, use the Create Pose Asset button in the Action editor.

**The created Action is now assigned to the armature.**
This makes it possible to inspect which bones are included and to tweak anything.
In that respect, it's an Action like any other, and you can add or remove keys as usual.
Just make sure that the keys are all on the same frame, in order to keep this a "pose"
instead of an "animation snippet"; the latter isn't supported at the moment.

True to its name, the *Create Pose Asset* button automatically marks the Action as Asset.
Not only does this make it available in the pose library, it will also act as a *fake user*
to ensure the Action isn't lost after you unassign it from the armature.

The pose asset can be renamed in the Asset Browser. There you can also right
click on the thumbnail, then choose Assign Action to assign the Action to the
active Object (see description above).

.. note::

   The **Create Pose Asset** button creates a new Action. To make sure that this
   is actually visible in the user interface, so that you know that something happened,
   it tries to make sure that the Asset Browser shows the newly created pose asset.
   Because of this, it **requires that there is an Asset Browser visible,
   and that it's set to show the Current File asset library**.

   This is especially relevant to pose assets, compared to other assets.
   You cannot mark an object as asset multiple times, but you can create ten pose assets
   from the same character pose.


.. _bpy.ops.poselib.restore_previous_action:

Pose Creation from Existing Animation
-------------------------------------

Animators eat and breathe time, so there is a fair chance that you already have
some poses lined up on the timeline. Creating a pose asset from existing animation
is pretty much the same as described above, with a few subtle differences:

- Go to the frame with the pose you want to turn into an asset.
- Select the relevant bones and click the **Create Pose Asset button** in the Action Editor.
- This creates an Action as before, but this time
  **it also includes any bone property that was keyed on the current frame**.
  In other words: any bone property (regular and custom) that's displayed in
  yellow in the user interface will be included in the pose asset.
  This makes it possible to also include properties that control IK/FK switching,
  for example. As with the pose, the current value is copied into the pose asset,
  and not the keyed value.
- Blender saves which action was previously assigned to the armature.
- The new pose Action is assigned to the armature so you can give it a name and
  inspect/adjust its contents.
- Click the *Restore Previous Action* button (back arrow icon) that appeared
  next to the Create Pose Asset button. This **reassigns the previous Action**,
  so that you're back at the animation you had before.


.. _bpy.ops.poselib.copy_as_asset:

Pose Creation by Copying from Other File
----------------------------------------

As described in :ref:`asset-libraries-design-limitations`, Blender only writes
data to the currently open blend-file. To copy a pose from some other file into
a pose library file, see the following steps:

- Pose the character and select the relevant bones.
- Click the **Copy Pose as Asset button**, which is available in the Action Editor. This will create the pose asset
  (including its thumbnail) and store it in a temporary file somewhere.
- Choose an existing pose asset, and open its context menu. Click the **Open Blend File** option.
- A new Blender process will start, and automatically open the asset library
  file that contains the chosen pose. By the way, this works for all assets, not just poses!
- In the Asset Browser, click the **Paste as New Asset button**. This will load that temporary file,
  and load all the assets it can find in there. In our case, it will only find a single pose,
  but future versions of Blender may extend this for other asset types.
  This is why the button is named so generically -- it is not pose-specific.
- Give the pose a name, and click on the "refresh" button in the preview image panel
  to render a new preview if you want.
- **Save the file and quit Blender**.
- The original Blender is still running in the background and notices that the new Blender has quit.
  It **automatically refreshes the Asset Browser** to show the newly added pose.


Automatically Assigned Catalog
------------------------------

When you create a pose asset, Blender may automatically assign it to an asset catalog.
This only works if there is an Asset Browser visible;
Blender then assigns the pose asset to its active asset catalog.
If there are multiple Asset Browsers open, it performs the following steps:

- If the current window has one Asset Browser, it uses that one.
- If the current window has multiple Asset Browsers, it uses the biggest one.
- Otherwise Blender goes over the other windows (if there are any), and do a similar search.
  The first window it sees that has an Asset Browser wins.


.. _poselib-preview-images:

Controlling the Look of Preview Images
--------------------------------------

The pose library preview images are rendered with the active :ref:`Scene camera <bpy.types.Scene.camera>`.
This approach was preferred over rendering a specific 3D Viewport for two main reasons:

- There is only one scene camera active at any time, making it predictable which camera is used.
- The camera, as well as the rest of the scene, can be set up specifically for rendering the thumbnails.
  Pose library files are intended for that purpose: to contain the poses and render their preview images.

The preview images are rendered using the :doc:`Workbench Engine </render/workbench/index>`.
Switch the scene to use that as render engine, and you'll see various options to influence the look.
Select a pose asset and press the Generate Preview button to re-render the preview image with the current settings.

You can also animate settings such as MatCap rendering, light positions, and intensities, etc.
Use this to your advantage!


Scene Animation for Preview Images
----------------------------------

Sometimes it's handy to have a few different background colors or camera angles
for your poses. Many facial poses are made with a specific camera angle in mind.

- Background color can be animated by placing a plane behind the character and animating its material.
  In this case just for fun, but for more serious applications
  this could be used to indicate a certain character, or a mood, or anything else.
- The active camera can be switched by using :ref:`camera markers <bpy.ops.marker.camera_bind>`.

Both make it possible to choose a specific frame to pick the background color and camera angle.
Pose the character, click the *Create Pose Asset* button,
and the pose action will be keyed on the current frame.
This means it's easy to edit the pose and refresh its preview image,
because you know exactly which frame it was originally created on.


Using the Pose Library
======================

The pose library can be used to pose a character in a few different ways.
In short, you can fully apply a pose or blend it into the character's current pose interactively.
How exactly these operations work depends on where you use them.
This section will explain the use from both the Asset Browser and the 3D Viewport.


Use from the Asset Browser
--------------------------

The pose library can be used directly from the Asset Browser.
The **Pose Library panels will appear** when the active object is an armature
and in Pose Mode. The :doc:`catalog system </files/asset_libraries/catalogs>`
and the filter bar at the top can be used to search for specific poses.


The following operators can be accessed by :kbd:`RMB` on a pose:

.. _bpy.ops.poselib.apply_pose_asset:

Apply Pose
   Applies the pose to the character. If there are any bones selected,
   the pose will be applied only to those bones. This makes it possible to
   create a "finger guns" pose by applying a fist pose to the hand,
   and then an "open hand" pose for only the index finger and thumb.
   Double-clicking a pose will also apply it.

Apply Pose Flipped
   Will mirror the pose from left to right and vice versa. This makes it
   possible, for example, to apply a left-hand pose to the right hand, reducing
   the number of poses you have to put into the library. This can of course also
   be applied for asymmetrical facial expressions that depend on the camera
   angle. While blending (see below), keep :kbd:`Ctrl` pressed to blend the flipped pose.

.. _bpy.ops.poselib.blend_pose_asset:

Blend Pose
   Allows you to gradually blend a pose from the library into the character's pose.
   Click the button, then move the mouse left/right to determine the desired blend.
   A pose asset can be "subtracted" while blending. Drag to the right to blend as usual, drag to the left to subtract
   the pose. While blending, you can use :kbd:`Tab` to toggle between the original and the blended pose.
   As usual in Blender, :kbd:`LMB` or press :kbd:`Return` to confirm; :kbd:`RMB` or press :kbd:`Esc` to cancel the
   operator. Blending can also exaggerate a pose, by pressing :kbd:`E` (for Extrapolate) and applying a pose for more
   than 100%.

.. _bpy.ops.poselib.pose_asset_select_bones:

Select/Deselect Pose Bones
   Select or deselect the bones that are used in the pose. This can be used to create a selection set,
   or simply show what was part of the pose and what wasn't.


.. _pose-library-from-viewport:

Use from 3D Viewport
--------------------

.. figure:: /images/asset_browser-pose_library-use_from_viewport.png

   The pose library in use from the Asset Shelf.

.. note::

  The pose library previously lived in the Sidebar within the Pose Library panel.
  The panel still exists, but now contains a button to open the asset shelf.

In the 3D viewport, poses can be quickly applied from the :ref:`ui-region-asset_shelf`.
Contrary to the Asset Browser, the shelf allows you to apply poses quicker.

**Click on a pose to apply it.** A single click is enough.
You can also select and apply a pose via the cursor keys.
This allows for fast exploration of the poses,
to directly see the result on the active character.

**Drag the pose thumbnail left to right to blend it** into the character's current pose.
Just release the mouse button to confirm.


.. _pose-library-old:

Old Pose Library
================

In Blender 3.0, the Asset Browser based pose library, described above, replaced
its predecessor pose library system. This section describes how to convert poses
from the old pose library to the current system.

.. _pose-library-convert-old:
.. _bpy.ops.poselib.convert_old_poselib:

Converting Old Pose Libraries
-----------------------------

Old-style pose libraries can be converted to pose assets in the following way:

- In the Action Editor, select the Action containing the pose library you want to convert.
- Make sure the scene camera is set up correctly for rendering preview images.
- In the Action Editor's Pose Library panel, click the "Convert Old-Style Pose Library" button.
- Open the Asset Browser, and see the poses have been converted.
- If you're happy with the result, remove the old pose library Action.
- Save the blend-file.

As usual, the blend-file should be saved to a directory marked as asset library
in order to use the pose assets from other blend-files.

.. note::

   This conversion does not assign the poses to any catalog, and so they will
   appear in the "Unassigned" section of the "Current File" asset library.


## Propagate

.. _bpy.ops.pose.propagate:

*********
Propagate
*********

.. reference::

   :Mode:      Pose Mode
   :Menu:      :menuselection:`Pose --> Propagate`
   :Shortcut:  :kbd:`Alt-P`

The Propagate tool copies the pose of the selected bones on the current frame over
to the keyframes delimited by the *Termination Mode*.
It automates the process of copying and pasting.

Termination Mode
   Modes which determine how it decides when to stop overwriting keyframes.

   To Next Keyframe
      Simply copies the pose to the first keyframe after (but not including any keyframe on) the current frame.
   To Last Keyframe
      Will simply replace the last keyframe (i.e. making action cyclic).
   Before Frame
      To all keyframes between current frame and the *End frame* option.
      This option is best suited for use from scripts due to the difficulties in setting this frame value,
      though it is possible to set this manually
      via the :ref:`bpy.ops.screen.redo_last` panel if necessary.
   Before Last Keyframe
      To all keyframes from current frame until no more are found.
   On Selected Keyframes
      Will apply the pose of the selected bones to all selected keyframes.
   On Selected Markers
      To all keyframes occurring on frames with Scene Markers after the current frame.
End Frame
   Defines the upper-bound for the frame range within which keyframes
   will be affected (with the lower bound being the current frame).


## Show Hide


*********
Show/Hide
*********

.. reference::

   :Mode:      All Modes
   :Panel:     :menuselection:`Properties --> Bone --> Viewport Display`
   :Menu:      :menuselection:`... --> Show/Hide`

You do not have to use bone layers to show/hide some bones. As with objects,
vertices or control points, you can use :kbd:`H`:

- :kbd:`H` will hide the selected bone(s).
- :kbd:`Shift-H` will hide all bones *but the selected one(s)*.
- :kbd:`Alt-H` will show all hidden bones.

You can also use the *Hide* checkbox of the :menuselection:`Bone tab --> Viewport Display panel`.

Note that hidden bones are specific to a mode,
i.e. you can hide some bones in *Edit Mode*,
they will still be visible in *Pose Mode*, and vice versa.
Hidden bones in *Pose Mode* are also invisible in *Object Mode*.
And in *Edit Mode*, the bone to hide must be fully selected,
not just its root or tip.


## Bone Collections

.. _bpy.types.BoneCollection:

****************
Bone Collections
****************

.. note::

   Bone Collections were introduced in Blender 4.0 as replacement of Armature
   Layers and Bone Groups. :ref:`Bone colors <bpy.types.Bone.color>` are now
   managed directly on the bone.

.. reference::

   :Mode:      Pose & Armature Edit Modes
   :Panel:     :menuselection:`Properties --> Armature --> Bone Collections`
   :Menu:      :menuselection:`Pose --> Bone Collections --> ...`

.. figure:: /images/animation_armatures_properties_bonecollections_panel.png

   The Bone Collections panel in the Armature properties.

This panel contains a Tree View to manage :doc:`Bone Collection </animation/armatures/bones/bone_collections>`
From this panel, Bone Collections can be created, deleted, re-arranged, and more.

Collections can be renamed by double clicking on the name.
To nest a collection inside an existing collection, click and drag the name onto another collection's name.
Child collection can also be made by :kbd:`RMB` and selecting "Add Child Collection".

To the right of the name gives a few controls of the collection:

.. _bpy.types.BoneCollection.is_visible:

Visible (Eye)
   Bones in this collection will be visible in the 3D Viewport.

.. _bpy.types.BoneCollection.is_solo:

Solo (Star)
   Show only this bone collection, and others also marked as "solo".

Further more, collection that are not empty will have a dot to indicate the collection has bones assigned to it.

.. tip::

   The Bone Properties panel gives a slightly different view on the bone's collections. See
   :doc:`Bone Relations </animation/armatures/bones/properties/relations>`.


Specials
========

Show All
   Unhides any hidden bone collections.

.. _bpy.ops.armature.collection_unsolo_all:

Un-Solo All
   Clear the 'solo' setting on all bone collections

.. _bpy.ops.armature.collection_remove_unused:

Remove Unused
   Remove all bone collections that have neither bones nor children.
   This is done recursively, so bone collections that only have unused children are also removed.


Assign & Select
===============

.. _bpy.ops.armature.collection_assign:

Assign
   Assigns the selected bones to the active bone collection.

.. _bpy.ops.armature.collection_unassign:

Remove
   Removes the selected bones from the active bone collection.

.. _bpy.ops.armature.collection_select:

Select
   Selects the bones in the active bone collection.

.. _bpy.ops.armature.collection_deselect:

Deselect
   Deselects the bones in the active bone collection.

.. note::

   Individual bones can als be unassigned from their collections via the
   :ref:`Bone Relations panel <bpy.types.PoseBone.collections>`.

.. tip::

   For setting up custom selection sets of bones, take a look at the *Selection
   Sets* add-on. It is bundled with Blender.


.. _moving_bones_between_collections:

Moving Bones between Collections
================================

Blender should be in *Edit Mode* or *Pose Mode* to move bones between collections.
Note that as with objects, bones can be assigned to in several collections at once.

.. _bpy.ops.armature.move_to_collection:

Move to Bone Collection
   Shows a list of the Armature's *editable* bone collections. Choosing a bone
   collection unassign the selected bones from all other bone collections, then
   assigns them to the chosen one.

   Available as :menuselection:`Pose --> Move to Collection` (*Pose Mode*)
   :menuselection:`Armature --> Move to Collection` (*Edit Mode*), and :kbd:`M` (either mode).

Bone Collections
   Shows a list of the Armature's *editable* bone collections. The collections
   that the active bone is assigned to are prefixed with a ``-``, and choosing
   those will unassign all selected bones from that collection. Similarly,
   choosing a bone collection prefixed with a ``+`` will assign all selected bones
   to that collection.

   Available as :menuselection:`Pose --> Bone Collections` (*Pose Mode*)
   :menuselection:`Armature --> Bone Collections` (*Edit Mode*), and :kbd:`Shift-M` (either mode).

.. note::

   The above operators will only show the *editable* bone collections. When the
   Armature is linked, its bone collections will be *read-only*. New bone
   collections can still be added via library overrides; only those will be
   editable.

   See :ref:`Library Overrides of Bone Collections <bone_collections_library_overrides>`.


Custom Properties
=================

Create and manage your own properties to store data in the Bone Collection's data-block.
See the :ref:`Custom Properties <files-data_blocks-custom-properties>` page for more information.


## Display


****************
Viewport Display
****************

.. reference::

   :Mode:      All Modes
   :Panel:     :menuselection:`Armature --> Viewport Display`

.. TODO2.8
   .. figure:: /images/animation_armatures_properties_display_panel.png

      The Display panel.

.. _bpy.types.Armature.display_type:

Display As
   This controls the way the bones appear in the 3D Viewport.

   .. list-table::

      * - .. figure:: /images/animation_armatures_properties_display_octahedral.png
             :width: 320px

             Octahedral bone display.

        - .. figure:: /images/animation_armatures_properties_display_stick.png
             :width: 320px

             Stick bone display.

      * - .. figure:: /images/animation_armatures_properties_display_b-bone.png
             :width: 320px

             B-Bone bone display.

        - .. figure:: /images/animation_armatures_properties_display_envelope.png
             :width: 320px

             Envelope bone display.

   Octahedral
      This is the default visualization, well suited for most of editing tasks. It materializes:

      - The bone root ("big" joint) and tip ("small" joint).
      - The bone "size" (its thickness is proportional to its length).
      - The bone roll (as it has a square section).

      .. figure:: /images/animation_armatures_properties_display_type-octahedral.png
         :width: 300px

         Note the 40° rolled Bone.001 bone.

   Stick
      This is the simplest and most non-intrusive visualization.
      It just materializes bones by sticks of constant (and small) thickness,
      so it gives you no information about root and tip, nor bone size or roll angle.

      .. figure:: /images/animation_armatures_properties_display_type-stick.png
         :width: 300px

         Note that Bone.001 roll angle is not visible (except by its XZ axes).

   B-Bone
      This visualization shows the curves of "smooth" multi-segmented bones;
      see the :doc:`/animation/armatures/bones/properties/bendy_bones` for details.

      .. list-table::

         * - .. figure:: /images/animation_armatures_bones_properties_bendy-bones_b-bones-1.png
                :width: 320px

                An armature of B-Bones, in Edit Mode.

           - .. figure:: /images/animation_armatures_bones_properties_bendy-bones_b-bones-3.png
                :width: 320px

                The same armature in Object Mode.

   Envelope
      This visualization materializes the bone deformation influence.
      More on this in the :ref:`bone page <armature-bone-influence>`.

      .. figure:: /images/animation_armatures_bones_structure_envelope-pose-mode.png
         :width: 300px

   Wire
      This simplest visualization shows the curves of "smooth" multi-segmented bones.

      .. list-table::

         * - .. figure:: /images/animation_armatures_properties_display_type-wire-pose-mode.png
                :width: 320px

                An armature of Wire, in Pose Mode.

           - .. figure:: /images/animation_armatures_properties_display_type-wire-edit-mode.png
                :width: 320px

                The same armature in Edit Mode.

.. _bpy.types.Armature.show:

Show
   Names
      Displays the name of each bone.
   Shapes
      When enabled, the default standard bone shape is replaced,
      in *Object Mode* and *Pose Mode*, by the shape of a chosen object
      (see :doc:`Shaped Bones </animation/armatures/bones/properties/display>` for details).
   Bone Colors
      Draws bones in their configured colors. Disable to always draw bones in the default color.
      For more details see :ref:`Bone Colors <bpy.types.Bone.color>`.
   In Front
      When enabled, the bones of the armature will always be shown on top of
      the solid objects (meshes, surfaces, ...). I.e. they will always be visible and selectable
      (this is the same option as the one found in the *Display* panel of the *Object data* tab).
      Very useful when not in *Wireframe* mode.

.. _bpy.types.Armature.show_axes:

Axis
   When enabled, the (local) axes of each bone are displayed (only relevant for *Edit Mode* and *Pose Mode*).

   .. _bpy.types.Armature.axes_position:

   Position
      The position for the axes display on the bone.
      Increasing the value moves it closer to the tip; decreasing moves it closer to the root.

.. _bpy.types.Armature.relation_line_position:

Relations
   Whether the :ref:`Relationship Lines <bpy.types.View3DOverlay.show_relationship_lines>`
   overlay should be drawn from each parent's tail or head.
   The lines are always drawn towards the childrens' heads.


## Index


##############
  Properties
##############

.. toctree::
   :maxdepth: 2

   introduction.rst
   bone_collections.rst
   display.rst


## Introduction


************
Introduction
************

The *Armature* tab in Properties contains various panels gathering the armature settings.

.. figure:: /images/animation_armatures_properties_introduction_properties-editor.png

   The Armature tab in the Properties.

Pose
====

.. reference::

   :Mode:      All Modes
   :Panel:     :menuselection:`Armature --> Pose`

.. _bpy.types.Armature.pose_position:

Pose Position
   A radio button to switch between Pose Position and Rest Position.

   In *Edit Mode*, you always see armatures in their rest position,
   in *Object Mode* and *Pose Mode*, by default, you see them in *Pose Position*
   (i.e. as it was transformed in the *Pose Mode*).
   If you want to see it in the rest position in all modes, select *Rest Position*.


Bone Collections
================

See :doc:`Bone Collections </animation/armatures/properties/bone_collections>`.


Motion Paths
============

.. reference::

   :Mode:      All Modes
   :Panel:     :menuselection:`Armature --> Motion Paths`

In the :doc:`Motion Paths </animation/motion_paths>` panel you can enable visualization
of the motion path your skeleton leaves when animated.


Inverse Kinematics
==================

.. reference::

   :Mode:      All Modes
   :Panel:     :menuselection:`Armature --> Inverse Kinematics`

.. TODO2.8
   .. figure:: /images/animation_armatures_posing_bone-constraints_inverse-kinematics_introduction_panel.png

      The Inverse Kinematics panel.

Defines the type of :doc:`IK solver </animation/armatures/posing/bone_constraints/inverse_kinematics/introduction>`
used in your animation.


Custom Properties
=================

.. reference::

   :Mode:      All Modes
   :Panel:     :menuselection:`Armature --> Custom Properties`

See the :ref:`Custom Properties <files-data_blocks-custom-properties>` page for more information.


## Index

.. _skinning-index:

############
  Skinning
############

.. toctree::
   :maxdepth: 2

   introduction.rst
   parenting.rst


## Introduction


************
Introduction
************

We have seen in :doc:`previous pages </animation/armatures/index>` how to design an armature,
create chains of bones, etc.
Now, having a good rig is not the final goal, unless you want to produce a "Dance Macabre" animation,
you will likely want to put some flesh on your skeletons!
Surprisingly, "linking" an armature to the object(s)
it should transform and/or deform is called the "skinning" process...

.. figure:: /images/animation_armatures_skinning_introduction_example.png

   The human mesh skinned on its armature.

In Blender, you have two main skinning types:

#. You can :doc:`Parent/Constrain Objects to Bones </scene_layout/object/editing/parent>` --
   then, when you transform the bones in *Pose Mode*, their "children" objects are also transformed,
   exactly as with a standard parent/children relationship...
   The "children" are **never** deformed when using this method.
#. You can :doc:`Use the Armature Modifier on entire Mesh </animation/armatures/skinning/parenting>`,
   and then, some parts of this object to some bones inside this armature.
   This is the more complex and powerful method,
   and the only way to really deform the geometry of the object,
   i.e. to modify its vertices/control points relative positions.

.. hint:: Retargeting

   Retargeting, which is a way to apply motion-capture data (acquired from real world) to a rig, is available through
   add-ons and importers.


## Parenting


**********************
Armature Deform Parent
**********************

.. reference::

   :Mode:      Object Mode and Pose Mode
   :Menu:      :menuselection:`Object/Pose --> Parent --> Armature Deform`
   :Shortcut:  :kbd:`Ctrl-P`

Armature Deform Parenting is a way of creating and setting up
an :doc:`Armature Modifier </modeling/modifiers/deform/armature>`.

To use *Armature Deform Parenting* you must first select all the child objects that will be
influenced by the armature and then lastly, select the armature object itself.
Once all the child objects and the armature are selected, press :kbd:`Ctrl-P` and
select *Armature Deform* in the *Set Parent To* pop-up menu.

The armature will be the parent object of all the other child objects and each child object
will have an Armature Modifier with the armature associated (*Object* field).

.. figure:: /images/animation_armatures_skinning_parenting_deform-object-mode.png

   Bone associated with Mesh Object.


With Empty Groups
=================

When parenting it will create empty :doc:`vertex groups </modeling/meshes/properties/vertex_groups/index>`
on the child objects (if they do not already exist) for and named after each deforming bone in the armature.
The newly created vertex groups will be empty. This means they will not have any weights assigned.
Vertex groups will only be created for bones which are setup as deforming
(:menuselection:`Properties --> Bone --> Deform Panel`).

You can then manually select the vertices and assign them to a particular vertex group of your
choosing to have bones in the armature influence them.

Choose this option if you have already created (and weighted) all the vertex groups the mesh requires.


Example
-------

For example, if you have an armature which consists of three bones named "BoneA",
"BoneB" and "BoneC" and cube mesh called "Cube". If you parent the cube to
the armature, the cube will get three new vertex groups created on it called "BoneA",
"BoneB" and "BoneC". Notice that each vertex group is empty.

.. figure:: /images/animation_armatures_skinning_parenting_bone-empty-groups.png

   Cube in Edit Mode using Armature Deform with empty groups.


With Automatic Weights
======================

*With Automatic Weights* parenting works similar to *With Empty Groups*,
but it will not leave the vertex groups empty. It calculates how much influence a particular bone
would have on vertices based on the distance from those vertices to a particular bone ("bone heat" algorithm).
This influence will be assigned as weights in the vertex groups.

This method of parenting is certainly easier to setup, but it can often lead to armatures which do not deform child
objects in ways you would want. Overlaps can occur when it comes to determining which bones should
influence certain vertices when calculating influences for more complex armatures and child objects.
Symptoms of this confusion are that when transforming the armature in *Pose Mode*,
parts of the child objects do not deform as you expect;
If Blender does not give you the results you require,
you will have to manually alter the weights of vertices in relation to the vertex groups they belong to and
have influence in.


With Envelope Weights
=====================

Works in a similar way to *With Automatic Weights*. The difference is that the influences are calculated
based on the :ref:`Bone Envelopes <armature-bones-envelope>` settings.
It will assign a weight to each vertex group the vertices that is inside its bone's influence volume,
depending on their distance to this bone.

This means newly included/excluded vertices or new envelope settings will not be taken into account.
You will have to apply Armature Deform With Envelope Weights parenting again.

.. tip::

   If you want the envelope setting to be used instantly, bind the Armature Modifier to *Bone Envelopes*.

.. figure:: /images/animation_armatures_skinning_parenting_envelope-influence.png

   Two sets of armatures, each with three bones.

.. warning::

   If you had defined vertex groups using same names as skinned bones, their content will be
   completely overridden by both *Automatic* and *Envelope Weights*.
   In this case *With Empty Groups* could be used instead.

.. seealso::

   :ref:`weight-painting-bones`.


## Index

.. _constraints-index:
.. _bpy.types.Constraint:
.. _bpy.ops.constraint:

###############
  Constraints
###############

.. toctree::
   :maxdepth: 2

   introduction.rst


Interface
=========

.. toctree::
   :maxdepth: 1

   interface/header.rst
   interface/common.rst
   interface/stack.rst


.. _constraints-motion-tracking:

Motion Tracking
===============

.. toctree::
   :maxdepth: 1

   motion_tracking/camera_solver.rst
   motion_tracking/object_solver.rst
   motion_tracking/follow_track.rst


Transform
=========

.. toctree::
   :maxdepth: 1

   transform/copy_location.rst
   transform/copy_rotation.rst
   transform/copy_scale.rst
   transform/copy_transforms.rst
   transform/limit_distance.rst
   transform/limit_location.rst
   transform/limit_rotation.rst
   transform/limit_scale.rst
   transform/maintain_volume.rst
   transform/transformation.rst
   transform/transform_cache.rst


Tracking
========

.. toctree::
   :maxdepth: 1

   tracking/clamp_to.rst
   tracking/damped_track.rst
   tracking/ik_solver.rst
   tracking/locked_track.rst
   tracking/spline_ik.rst
   tracking/stretch_to.rst
   tracking/track_to.rst


Relationship
============

.. toctree::
   :maxdepth: 1

   relationship/action.rst
   relationship/armature.rst
   relationship/child_of.rst
   relationship/floor.rst
   relationship/follow_path.rst
   relationship/pivot.rst
   relationship/shrinkwrap.rst


## Introduction

.. index:: Constraint; Object Constraints
.. index:: Object Constraints

************
Introduction
************

Constraints are a way to control an object's properties
(e.g. its location, rotation, scale), using either plain static values
(like the :doc:`"limit" ones </animation/constraints/transform/limit_location>`),
or another object, called "target"
(like e.g. the :doc:`"copy" ones </animation/constraints/transform/copy_location>`).

Even though constraints are useful in static projects,
their main usage is obviously in animation.

- You can control an object's animation through the targets used by its constraints
  (this is a form of indirect animation). Indeed,
  these targets can then control the constraint's owner's properties, and hence,
  animating the targets will indirectly animate the owner.
- You can animate constraints' settings. e.g. the *Influence* or
  when using an armature's bone as target,
  animate where along this bone (between root and tip) lays the real target point.

They can make the eyes of a tennis player track a tennis ball bouncing across the court,
allow the wheels on a bus to all rotate together,
help a dinosaur's legs bend at the knee automatically, and
make it easy for a hand to grip the hilt of a sword and the sword to swing with the hand.

Constraints, in Blender, work with :term:`Objects <Object>` and :term:`Bones <Bone>`.
Read about using constraints in rigging
in the :doc:`Armature chapter </animation/armatures/posing/bone_constraints/index>`.

.. list-table::
   :widths: 1 1 5

   * - .. figure:: /images/animation_constraints_introduction_tab-object.png

          Object

     - .. figure:: /images/animation_constraints_introduction_tab-bone.png

          Bone

     - .. figure:: /images/animation_constraints_interface_stack_example.png
          :align: center

          The Constraint Stack is evaluated from top to bottom.

Constraints work in combination with each other to form a Constraint Stack.


Adding & Removing Constraints
=============================

To add a constraint click on the *Add Object Constraint* menu in the Constraints tab.
Alternatively, you can use the :ref:`bpy.ops.object.constraint_add_with_targets` operator.

To copy constraints from one object to another use :ref:`bpy.ops.object.constraints_copy`.

Any single constraint can be removed by clicking on the "X" button
in the constraint's :doc:`header </animation/constraints/interface/header>`.
To remove all constants from an object use :ref:`bpy.ops.object.constraints_clear`.

.. tip::

   Tracking constraints can be added/removed using the :doc:`Track menu </scene_layout/object/editing/track>`.


Tips
====

Constraints are a fantastic way to add sophistication and complexity to a rig.

But be careful not to rush in too quickly, piling up constraint upon constraint
until you lose all sense of how they interact with each other.

Start simply. Get to know a single constraint inside and out.
:doc:`/animation/constraints/transform/copy_location` is a good first constraint to explore it
also has an animation example. Take the time to understand every fundamental concept behind it,
and the other constraints will make far more sense.

.. TODO Add the 4x4 transform matrix vs. the transform panel.

   Also note that constraints internally work using 4×4 transformation matrices only.
   When you use settings for specific rotation or scaling constraining,
   this information is being derived from the matrix only,
   not from settings in a *Bone* or *Object*. Especially for combining
   rotations with non-uniform or negative scaling this can lead to unpredictable behavior.

.. TODO Add the blue dashed line.


## Common


******
Common
******

.. _rigging-constraints-interface-common-target:

Target
======

The Target :ref:`ui-data-id` field lets you link the constraint to a Target object of your choosing.
This link provides data to the constraint so that it can begin to function.
For example, the Copy Location Constraint needs location data to function.
Fill in the Target field, and the Copy Location constraint will begin to use location data from the Target object.

.. figure:: /images/animation_constraints_interface_common_target.png

   The Target field must be filled in for the constraint to function.

By default, the Target will use the :term:`Object Origin` as the target point.

If the Target field links to a :term:`Mesh` or :term:`Lattice` object, a :term:`Vertex Group` field will appear.
Enter the name of a vertex group and the constraint will target the median point
of this vertex group instead of the object's origin.

.. figure:: /images/animation_constraints_interface_common_target-vertex-group.png

If the Target field links to an :term:`Armature`, a :term:`Bone` field will appear
along with a *Head/Tail* slider.
Enter the name of a bone and the constraint will target the bone instead of the entire armature object origin.

.. figure:: /images/animation_constraints_interface_common_target-bone.png

The slider moves the precise position of the target between the :term:`Head` and :term:`Tail` of the bone.
Some constraints have a button next to the slider
that enables using the curved shape of :ref:`Bendy Bones <bendy-bones>`.


.. _rigging-constraints-interface-common-space:
.. _bpy.types.constraint.owner_space:
.. _bpy.types.constraint.target_space:

Space
=====

Constraints need a frame of reference in order to function.
This frame of reference is called the "space" of the constraint.
Choosing one space vs. another will change this frame of reference
and substantially alter the behavior of a constraint.

To understand how changing the space will change the behavior of the constraint,
consider experimenting with two empties.
Make sure they display as arrows so that you can see the local axes for each empty.
Make sure to size one empty a little larger than the other so that they are both always visible
even if directly on top of each other.
Then add a constraint to one empty that targets the other and experiment thoroughly by
moving, rotating and scaling the target in many different ways.

.. figure:: /images/animation_constraints_interface_common_space.png

   This constraint is set to use World Space as the frame of reference for both
   its *Target* space and its *Owner* space.


Target Space & Owner Space
--------------------------

The space used to evaluate the target of the constraint is called the *Target* space.
The space used to evaluate the constrained object (the object that owns the constraint) is called the *Owner* space.
Hover over the space select menu(s) to learn whether it affects the space of the target
or the space of the owner.

When the constraints use a *Target* and/or/nor an *Owner* space there will be no, one or two selector(s).
The Copy Location constraint in example use both Target **and** *Owner* space.

When a constraint uses both *Target* and *Owner* space,
the Target and Owner can be any combination of space types.


.. _rigging-constraints-interface-common-space-types:

Space Types
-----------

World Space
   In this space type the world is the frame of reference for the object (or bone).
   Location is relative to the world origin.
   Rotation and Scale are oriented to the world axes.
   Transformations to the object, the object's parent and any other constraints
   higher up in the constraint stack are all taken into account.

Local Space
   This space excludes all effects of the parent objects or bones, as well as the rest position
   and orientation of the bone itself. Only transformations applied to the object or bone itself
   are taken into account.

   .. warning::

      For objects without a parent Local Space has a special meaning, different from
      the normal behavior of local space for bones or objects that have a parent.
      This behavior is kept for backwards compatibility, but may be removed in the future
      and shouldn't be used.

Local with Parent :guilabel:`Bones Only`
   The bone position and orientation is evaluated relative to its rest pose location and orientation,
   thus including both its own transformations and those caused by a possible parent relationship
   (i.e. the chain's transformations above the bone).

Pose Space :guilabel:`Bones Only`
   The bone position and orientation is evaluated in the armature object local space
   (i.e. independently from the armature transformations in *Object Mode*).
   Hence, if the armature object has null transformations,
   *Pose Space* will have the same effect as *World Space*.

Custom Space
   The position and orientation is evaluated relative to the current position and
   orientation of an arbitrary object or bone that is specified via additional input fields
   that appear when this option is selected.
   This can be used to evaluate the constraint using an arbitrary coordinate system.

Local Space (Owner Orientation) :guilabel:`Bone Targets Only`
   This space works like *Local Space*, with an additional coordinate space transformation
   that compensates for the difference in the rest pose orientations of the owner and target bones.
   If applied as the *Local Space* of the owner, this will produce the same global space movement as
   the target, provided parents are still at rest pose.

   This option replaces the following setup with two additional bones:

   #. An extra child bone of the target, rotated the same as the owner in rest pose.
   #. An extra sibling bone of the target, positioned same as the child in rest pose
      and using :doc:`Copy Transforms </animation/constraints/transform/copy_transforms>`
      in *World Space* from the child.
   #. The constraint uses *Local Space* of the sibling instead of the original target.

   This video demonstrates the difference from ordinary *Local Space*:

   .. peertube:: 8d81917d-1c9d-41a7-bcbf-74f026e4e2aa


.. _bpy.types.constraint.influence:

Influence
=========

The influence slider determines how much the constraint will affect the constrained object (target).

.. figure:: /images/animation_constraints_interface_common_influence.png

An influence of 0.0 will have no effect.
An influence of 1.0 will have the full effect.

Values between (0.0 and 1.0) will have a partial effect, but be careful.
These partial effects can be difficult to control,
especially as the :doc:`constraint stack </animation/constraints/interface/stack>` grows in complexity.

The influence value is animatable, allowing constraints to be turned off, or partially on as needed.

.. _bpy.ops.constraint.disable_keep_transform:

The ``X`` button after the influence slider can be used to disable the constraint while trying to
preserve the current object position. This may not work perfectly if other constraints remain active.


## Header

.. _bpy.types.Constraint.mute:

******
Header
******

Every constraint has a header.
The interface elements of the header are explained below using a Copy Location constraint as an example.

.. figure:: /images/animation_constraints_interface_header_example.png

   A Header sits at the top of every constraint.

Expand (down/right arrow icon)
   Show or Hide the settings of the constraint.
   Tidy up the :doc:`constraint stack </animation/constraints/interface/stack>`
   by hiding constraints that do not currently need attention.
   Constraints will continue to affect the scene even when hidden.

Icon
   The constraint type icon.

.. _bpy.types.Constraint.name:

Name
   Give the constraint a meaningful name in this text field, which describes its purpose.
   Meaningful names help you and your team members understand what each constraint is supposed to do.

   The *red* background is a warning that the constraint is not yet functional.
   The background will turn *gray* when the constraint is functioning.
   When this Copy Location constraint has a valid target in the *target field*
   it will turn gray and begin to function.

.. _bpy.types.Constraint.enabled:

Mute (eye icon)
   Enable or Disable the constraint. Disabling a constraint will stop its affect on the scene.

   Disabling a constraint is useful for turning off a constraint without losing all of its settings.
   Disabling means you can enable the constraint at a later time with the settings intact.
   Disabling is similar to setting the :ref:`Influence <bpy.types.constraint.influence>` to 0.0.

.. _bpy.ops.constraint.apply:

Extras
   Apply :kbd:`Ctrl-A`
      Makes the constraint "real" by applying any transformations caused by the constraint
      to make the original object to match the results of the constraint and deletes the constraint.

      .. warning::

         Applying a constraint that is not first in the stack will ignore the stack order
         (it will be applied as if it was the first one), and may produce undesired results.

   .. _bpy.ops.constraint.copy:

   Duplicate :kbd:`Shift-D`
      Creates a duplicate of the constraint just below current one in the stack.

   .. _bpy.ops.constraint.copy_to_selected:

   Copy to Selected
      Copies the constraint from the :term:`Active` object to all selected objects.

   .. _bpy.ops.constraint.move_to_index:

   Move to First/Last
      Moves the constraint to the first or last position in the constraint stack.

.. _bpy.ops.constraint.delete:

Delete ``X`` :kbd:`X`, :kbd:`Delete`
   Delete the constraint from the stack.
   The settings will be lost.
   The constraint will no longer affect the final outcome of the stack.

Move ``::::``
   Move a constraint up or down in the :doc:`constraint stack </animation/constraints/interface/stack>`.
   Since the stack is evaluated from top to bottom,
   moving a constraint in the stack can significantly affect the final outcome of the stack.

   - If there is only one constraint in the stack, the arrows will not be displayed.
   - If the constraint is at the top of the stack, only the down arrow will be displayed.
   - If the constraint is at the bottom of the stack, only the up arrow will be displayed.


## Stack


*****
Stack
*****

The combination of all the constraints affecting an object is called the Constraints Stack.
The Stack is in the Constraints panel, below the Add Constraint menu.

Constraints in the stack are evaluated from top to bottom.
The order of each constraint has a substantial impact on the final outcome of the stack.
Changing the order of the constraints can change the behavior of the entire stack.

.. figure:: /images/animation_constraints_interface_stack_example.png

   The constraints in this example stack are evaluated from top to bottom starting with
   the "Copy Location" constraint and ending with the final "Damped Track" constraint.

To change the order of a constraint use the up/down arrows
in the :doc:`header </animation/constraints/interface/header>`.


## Camera Solver

.. index:: Object Constraints; Camera Solver Constraint
.. _bpy.types.CameraSolverConstraint:

************************
Camera Solver Constraint
************************

The *Camera Solver* constraint gives the owner of this constraint,
the location and rotation of the "solved camera motion".

The "solved camera motion" is where Blender reconstructs the position of the physical, real-world camera,
when it filmed the video footage, relative to the thing being tracked.

.. note::

   This constraint only works after you have set up a minimum of eight markers and pressed
   :ref:`Solve Camera Motion <editors-movie-clip-tracking-clip-solve-motion>`
   (:menuselection:`Movie Clip Editor --> Toolbar --> Solve --> Solve Camera Motion`).


Options
=======

.. figure:: /images/animation_constraints_motion-tracking_camera-solver_panel.png

   Camera Solver Constraint panel.

Active Clip
   Receive tracking data from the scene's :ref:`Active Clip <bpy.types.Scene.active_clip>`.
   If unchecked, an option appears to choose from the other clips.

Constraint to F-Curve
   Applies the constraint, creating Keyframes for the transforms.

Influence
   Controls the percentage of affect the constraint has on the object.
   See :ref:`common constraint properties <bpy.types.constraint.influence>` for more information.


## Follow Track

.. index:: Object Constraints; Follow Track Constraint
.. _bpy.types.FollowTrackConstraint:

***********************
Follow Track Constraint
***********************

By default the Follow Track constraint is making objects have the same position at a frame as the track has.
The motion of this object happens on a single plane defined by the camera and the original position of the object.


Options
=======

.. figure:: /images/animation_constraints_motion-tracking_follow-track_panel.png

   Follow Track Constraint panel.

Active Clip
   Receive tracking data from the scene's :ref:`Active Clip <bpy.types.Scene.active_clip>`.
   If unchecked, an option appears to choose from the other clips.

3D Position
   Use the 3D position of the track to parent to.

Undistorted
   Parent to the undistorted position of the 2D track.

Frame Method
   Defines how the footage is fitted in the camera frame.

Camera
   Select the camera to which the motion is parented to (if empty, the active scene camera is used).

Depth Object
   If this object is set, constrained objects will be projected onto the surface
   of this depth object which can be used to create facial makeup visual effects.

Constraint to F-Curve
   Creates F-Curves for the object that copies the movement caused by the constraint.

Influence
   Controls the percentage of affect the constraint has on the object.
   See :ref:`common constraint properties <bpy.types.constraint.influence>` for more information.


Example
=======

`Follow Track Example Video <https://www.youtube.com/watch?v=KZalGrjGKSA>`__


## Object Solver

.. index:: Object Constraints; Object Solver Constraint
.. _bpy.types.ObjectSolverConstraint:

************************
Object Solver Constraint
************************

The *Object Solver* constraint gives the owner of this constraint,
the location and rotation of the "solved object motion".

The "solved object motion" is where Blender thinks the physical,
real-world (tracked) object was, relative to the camera that filmed it.

Can be used to add a mesh to video for example.

.. note::

   This constraint only works after you have set up a minimum of eight markers and pressed
   :ref:`Solve object Motion <editors-movie-clip-tracking-clip-solve-motion>`.
   Located at :menuselection:`Movie Clip Editor --> Toolbar --> Solve --> Solve Camera Motion`.

   If it says *Solve Camera Motion* instead of *Solve Object Motion* then go into
   the :menuselection:`Movie Clip Editor --> Sidebar region --> Objects`
   and switch it from the camera, to an object.


Options
=======

.. figure:: /images/animation_constraints_motion-tracking_object-solver_panel.png

   Object Solver Constraint panel.

Active Clip
   Receive tracking data from the scene's :ref:`Active Clip <bpy.types.Scene.active_clip>`.
   If unchecked, an option appears to choose from the other clips.

Object
   Select a tracked object to receive transform data from.

Camera
   Select the camera to which the motion is parented to (if left empty the active scene camera is used).

Set Inverse
   Moves the origin of the object to the origin of the camera.
Clear Inverse
   Moves the origin of the object back to the spot set
   in the Movie Clip Editor :menuselection:`Toolbar --> Solve --> Orientation --> Set Origin`.

Constraint to F-Curve
   Applies the constraint, creating keyframes for the transforms.

Influence
   Controls the percentage of affect the constraint has on the object.
   See :ref:`common constraint properties <bpy.types.constraint.influence>` for more information.


## Action

.. index:: Object Constraints; Action Constraint
.. _bpy.types.ActionConstraint:

*****************
Action Constraint
*****************

The *Action* constraint is powerful.
It allows you control
an :doc:`Action </editors/dope_sheet/modes/action>` using the transformations of another object.

The underlying idea of the *Action* constraint is very similar to the one behind
the :doc:`Drivers </animation/drivers/index>`, except that the former uses a whole action
(i.e. multiple F-Curves of the same type), while the latter controls a single F-Curve of their "owner"...

Note that even if the constraint accepts the *Mesh* action type,
only the *Object*, *Pose* and *Constraint* types are really working,
as constraints can only affect objects' or bones' transform properties, and not meshes' shapes.
Also note that only the object transformation (location, rotation, scale) is affected by the action,
if the action contains keyframes for other properties they are ignored, as constraints do not influence those.

As an example, let us assume you have defined an *Object* action
(it can be assigned to any object, or even no object at all),
and have mapped it on your owner through an *Action* constraint,
so that moving the target in the (0.0 to 2.0)
range along its X axis maps the action content on the owner in the (0 to 100)
frame range. This will mean that when the target's *X* property is 0.0
the owner will be as if in frame 0 of the linked action;
with the target's *X* property at 1.0
the owner will be as if in frame 50 of the linked action, etc.


Options
=======

.. figure:: /images/animation_constraints_relationship_action_panel.png

   Action panel.

Target
   :ref:`ui-data-id` used to select the constraints target, and is not functional (red state) when it has none.
   See :ref:`common constraint properties <rigging-constraints-interface-common-target>` for more information.

Evaluation Time
   This property allows objects to be driven without a constraint target
   by interpolating between the *Action Start* and *End* frames.
   The relative position between the start and end frame can be controlled using the value slider.

   This is very helpful for more complex rigging and mechanical rigs, as it means the Action constraint
   can be controlled directly with a :doc:`Driver </animation/drivers/index>`
   or :ref:`Custom Property <files-data_blocks-custom-properties>`.

Mix
   Specifies how the keyframed transformation from the action is combined with the existing transformation.
   These modes are the same as in the :doc:`Copy Transforms </animation/constraints/transform/copy_transforms>`
   constraint.

   Before/After Original (Full)
      The keyframed transformation is added before/after the existing transformation, as if it was
      applied to an imaginary parent/child of the constraint owner. Scale is handled like in
      the most basic :ref:`Full Inherit Scale <bpy.types.EditBone.inherit_scale>` mode of bones,
      so combining non-uniform scale and rotation will create shear.

   Before/After Original (Aligned)
      The keyframed transformation is added before/after the existing transformation, as if it was
      applied to an imaginary parent/child of the constraint owner. Scale is handled like in
      the :ref:`Aligned Inherit Scale <bpy.types.EditBone.inherit_scale>` mode of bones to
      avoid creating shear.

      This is equivalent to using the *Split Channels* option, but replacing the location component with
      the result of *Full*. If only uniform scale is used, the result is identical to *Full*.

   Before/After Original (Split Channels)
      Combines location, rotation and scale components of the transformation separately, similar
      to a sequence of three :doc:`Copy Location </animation/constraints/transform/copy_location>`,
      :doc:`Copy Rotation </animation/constraints/transform/copy_rotation>` and
      :doc:`Copy Scale </animation/constraints/transform/copy_scale>` (with Offset)
      constraints bundled together in one operation; the result may be slightly different
      in case of sheared inputs.

      Unlike *Aligned*, in this mode location channels are simply added together, so rotation
      and scale components of the input transformations cannot affect the resulting location.

   .. warning::

      For technical reasons modes other than *After Original (Full)* and *After Original (Aligned)* may
      not work as expected for constraints on *objects* (not bones) without a parent.

Influence
   Controls the percentage of affect the constraint has on the object.
   See :ref:`common constraint properties <bpy.types.constraint.influence>` for more information.


Target
------

Channel
   This selector controls which transform property
   (location, rotation or scale along/around one of its axes) from the target to use as "action driver".

Target
   This constraint allows you to choose in which space to evaluate its target's transform properties.

Range Min, Max
   The lower and upper bounds of the driving transform property value.

   .. warning::

      Unfortunately, here again we find the constraint's limitations:

      - When using a rotation property as "driver",
        these values are "mapped back" to the (-180.0 to 180.0) range.
      - When using a scale property as "driver", these values are limited to null or positive values.


Action
------

Action
   Select the name of the action you want to use.

   .. warning::

      Even though it might not be in red state (UI refresh problems...),
      this constraint is obviously not functional when this field does not contain a valid action.

Object Action
   Bones **only**, when enabled,
   this option will make the constrained bone use the "object" part of the linked action,
   instead of the "same-named pose" part. This allows you to apply the action of an object to a bone.

Frame Start, End
   The starting and ending frames of the action to be mapped.

   .. note::

      - These values must be strictly positive.
      - By default, both values are set to 0, which disables the mapping
        (i.e. the owner just gets the properties defined at frame 0 of the linked action...).


.. (TODO rewrite) Notes section is a mess.

Notes
=====

- When the object or bone already has Action constraints, the next constraint using
  a newly keyframed action should be added before all others in order to get
  the same final combined transformation. This fact is not affected by the Mix mode.
- Unlike usual, you can have a *Start* value higher than the *End* one,
  or a *Min* one higher than a *Max* one: this will reverse the mapping of the action
  (i.e. it will be "played" reversed...), unless you have both sets reversed, obviously!
- When using a *Constraint* action, it is the constraint *channel's names*
  that are used to determine to which constraints of the owner apply the action.
  E.g. if you have a constraint channel named "trackto_empt1",
  its keyed *Influence* and/or *Head/Tail* values (the only ones you can key)
  will be mapped to the ones of the owner's constraint named "trackto_empt1".
- Similarly, when using a *Pose* action
  (which is obviously only meaningful and working when constraining a bone!),
  it is the bone's name that is used to determine which bone *channel's names* from the action to use
  (e.g. if the constrained bone is named "arm", it will use and only use the action's bone channel named "arm"...).
  Unfortunately, using a *Pose* action on a whole armature object
  (to affect all the keyed bones in the action at once) will not work...
- Actions can also be marked as :term:`Asset`, but with certain limitations.
  For more info, see :doc:`/animation/armatures/posing/editing/pose_library`.


Example
=======

.. peertube:: c138e7b5-34cb-49cb-af07-d5d5f27f1cfb


## Armature

.. index:: Object Constraints; Armature Constraint
.. _bpy.types.ArmatureConstraint:

*******************
Armature Constraint
*******************

*Armature* is the constraint version of the :ref:`Armature Modifier <bpy.types.ArmatureModifier>`,
exactly reproducing the weight-blended bone transformations and applying it to its owner orientation.
It can be used like a variant of the :ref:`Child Of <bpy.types.ChildOfConstraint>` constraint
that can handle multiple parents at once, but requires all of them to be bones.

.. note::

   Unlike the Armature modifier, the constraint does not take
   the :doc:`Deform </animation/armatures/bones/properties/deform>` checkbox
   of bones into account, and can use any bone as target.


Options
=======

.. figure:: /images/animation_constraints_relationship_armature_panel.png

   Armature constraint.

Preserve Volume
   Like the matching option of the modifier, it enables the use of quaternions
   for preserving the volume of the object during deformation.

Use Envelopes
   To approximate envelope-only behavior of the modifier,
   add all relevant bones with weight 1.0 and enable this option.

   .. note::

      Unlike the modifier, the constraint always requires explicitly listing all
      of its target bones with associated weights. This option merely enables
      envelopes for all bones, as if they had :ref:`Envelope Multiply <armature-bones-envelope>` enabled.

Use Current Location
   Only for constraints on bones: Instead of using the rest location,
   use the current location of the owner bone to compute envelope weights or
   binding to B-Bone segments.

   With envelope weights, this can be used to change the active "parent" bone
   of the owner bone dependent on its location. For non-bones this mode is always active,
   because they don't have a rest location.

Add Target Bone
   This button adds a new empty entry at the end of the target list.

Normalize Weights
   This button normalizes all weight values in the target list so that they add up to 1.0.

Influence
   Controls the percentage of affect the constraint has on the object.
   See :ref:`common constraint properties <bpy.types.constraint.influence>` for more information.


Bones
-----

This specifies the list of bones used by the constraint to deform its owner.
Each target bone has the following input fields and controls:

Target
   Unlike the modifier, the constraint can use bones coming from different armatures at the same time.
   See :ref:`common constraint properties <rigging-constraints-interface-common-target>` for more information.

Sub-target
   Name of the target bone.

Remove Button ``X``
   Removes the entry from the target list.

Weight
   Weight associated with the bone, equivalent to vertex groups in the modifier.


## Child Of

.. index:: Object Constraints; Child Of Constraint
.. _bpy.types.ChildOfConstraint:

*******************
Child Of Constraint
*******************

*Child Of* is the constraint version of the standard parent/children relationship between objects
(the one established through the :kbd:`Ctrl-P` shortcut, in the 3D Viewport).

Parenting with a constraint has several advantages and enhancements,
compared to the traditional method:

- You can have several different parents for the same object
  (weighting their respective influence with the *Influence* slider).
- As with any constraint, you can key (i.e. animate) its Influence setting.
  This allows the object which has a Child Of constraint upon it to change over time which
  target object will be considered the parent, and therefore have influence over it.

  .. important::

     Do not confuse this "basic" object parenting with the one that defines
     the :ref:`chains of bones <armature-bone-chain>` inside of an armature.
     This constraint is used to parent an object to a bone
     (the so-called :doc:`object skinning </scene_layout/object/editing/parent>`),
     or even bones to bones. But do not try to use it to define chains of bones.


Options
=======

.. figure:: /images/animation_constraints_relationship_child-of_panel.png

   Child Of panel.

Target
   The target object that this object will act as a child of.
   :ref:`ui-data-id` used to select the constraint's target, and is not functional (red state) when it has none.
   See :ref:`common constraint properties <rigging-constraints-interface-common-target>` for more information.

Location
   Each of these buttons will make the parent affect or not affect the location along the corresponding axis.

Rotation
   Each of these buttons will make the parent affect or not affect the rotation around the corresponding axis.

Scale
   Each of these buttons will make the parent affect or not affect the scale along the corresponding axis.

Set Inverse
   By default, when you parent your owner to your target, the target becomes the origin of the owner's space.
   This means that the location, rotation and scale of the owner are offset by the same properties of the target.
   In other words, the owner is transformed when you parent it to your target.
   This might not be desired!
   So, if you want to restore your owner to its before-parenting state, click on the *Set Inverse* button.
Clear Inverse
   This button reverses (cancels) the effects of the above one,
   restoring the owner/child to its default state regarding its target/parent.

Influence
   Controls the percentage of affect the constraint has on the object.
   See :ref:`common constraint properties <bpy.types.constraint.influence>` for more information.


Tips
====

When creating a new parent relationship using this constraint, it is usually necessary to
click on the *Set Inverse* button after assigning the parent. As noted above,
this cancels out any unwanted transform from the parent, so that the owner returns to
the location/rotation/scale it was in before the constraint was applied.
Note that you should apply *Set Inverse* with all other constraints disabled
(their *Influence* set to 0.0) for a particular *Child Of* constraint,
and before transforming the target/parent (see example below).

About the toggle buttons that control which target's (i.e. parent's)
individual transform properties affect the owner,
it is usually best to leave them all enabled, or to disable all three of the given Location,
Rotation and Scale transforms.


Technical Note
==============

If you use this constraint with all channels on,
it will use a straight matrix multiplication for the parent relationship,
not decomposing the parent matrix into loc/rot/size.
This ensures any transformation correctly gets applied,
also for combinations of rotated and non-uniform scaled parents.


Examples
========

.. list-table::

   * - .. figure:: /images/animation_constraints_relationship_child-of_example1.png

          No constraint.

          Note the position of Owner empty 1.0 unit along the X and Y axes.

     - .. figure:: /images/animation_constraints_relationship_child-of_example2.png

          Child Of just added.

          Here you can see that Owner empty is now 1.0 unit away
          from Target_1 empty along X and Y axes.

   * - .. figure:: /images/animation_constraints_relationship_child-of_example3.png

          Offset set.

          Set Inverse has been clicked, and Owner is back to its original position.

     - .. figure:: /images/animation_constraints_relationship_child-of_example4.png

          Target/parent transformed.

          Target_1 has been moved along the XY plane, rotated around the Z axis,
          and scaled along its local X axis.

   * - .. figure:: /images/animation_constraints_relationship_child-of_example5.png

          Offset cleared.

          Clear Inverse has been clicked. Owner is fully again controlled by Target_1.

     - .. figure:: /images/animation_constraints_relationship_child-of_example6.png

          Offset set again.

          Set Offset has been clicked again.
          As you can see, it does not gives the same result as in (Target/parent transformed).
          As noted above, use Set Inverse only once, before transforming your target/parent.

.. peertube:: 9b83a0d6-5a76-4e7d-8c9b-b00e0eac34ae


## Floor

.. index:: Object Constraints; Floor Constraint
.. _bpy.types.FloorConstraint:

****************
Floor Constraint
****************

The *Floor* constraint allows you to use its target position
(and optionally rotation) to specify a plane with a "forbidden side",
where the owner cannot go. This plane can have any orientation you like.
In other words, it creates a floor (or a ceiling, or a wall)!
Note that it is only capable of simulating entirely flat planes,
even if you use the *Vertex Group* option.
It cannot be used for uneven floors or walls.


Options
=======

.. figure:: /images/animation_constraints_relationship_floor_panel.png

   Floor panel.

Target
   :ref:`ui-data-id` used to select the constraints target, and is not functional (red state) when it has none.
   See :ref:`common constraint properties <rigging-constraints-interface-common-target>` for more information.

Offset
   Allows you to offset the "floor" plane from the target's origin,
   by the given number of units. Use it e.g.
   to account for the distance from a foot bone to the surface of the foot's mesh.

Max/Min
   Controls which plane will be the "floor".
   The names of the buttons correspond, indeed, to the *normal* to this plane
   (e.g. enabling Z means "XY plane", etc.).
   By default, these normals are aligned with the *global* axes.
   However, if you enable *Use Rotation* (see above), they will be aligned with the *local target's axes*.
   As the constraint does not only define an uncrossable plane,
   but also a side of it which is forbidden to the owner,
   you can choose which side by enabling either the positive or negative normal axis...
   e.g. by default Z, the owner is stuck in the positive Z coordinates.

Use Rotation
   Forces the constraint to take the target's rotation into account.
   This allows you to have a "floor" plane of any orientation you like, not just the global XY, XZ and YZ ones...

Target/Owner
   Standard conversion between spaces.
   See :ref:`common constraint properties <rigging-constraints-interface-common-space>` for more information.

Influence
   Controls the percentage of affect the constraint has on the object.
   See :ref:`common constraint properties <bpy.types.constraint.influence>` for more information.


Example
=======

.. peertube:: 03319687-56a4-460c-8b82-42b80e5b7980


## Follow Path

.. index:: Object Constraints; Follow Path Constraint
.. _bpy.types.FollowPathConstraint:

**********************
Follow Path Constraint
**********************

The *Follow Path* constraint places its owner onto a *curve* target object,
and makes it move along this curve (or path).
It can also affect its owner's rotation to follow the curve's bends,
when the *Follow Curve* option is enabled.

It could be used for complex camera traveling,
a train on its rails and most other vehicles can also use "invisible" tracks,
the links of a bicycle chain, etc.

The owner is always evaluated in the global (world) space:

- Its location (as shown in the *Transform* panel)
  is used as an offset from its normal position on the path. E.g.
  if you have an owner with the (1.0, 1.0, 0.0) location,
  it will be one unit away from its normal position on the curve, along the X and Y axis.
  Hence, if you want your owner *on* its target path, clear its location :kbd:`Alt-G`!
- This location offset is also proportionally affected by the scale of the target curve.
  Taking the same (1.0, 1.0, 0.0) offset as above,
  if the curve has a scale of (2.0, 1.0, 1.0),
  the owner will be offset two units along the X axis (and one along the Y one)...
- When the *Follow Curve* option is enabled, its rotation is also offset to the one given by the curve.
  E.g. if you want the Y axis of your object to be aligned with the curve's direction,
  it must be in rest, non-constrained state, aligned with the global Y axis.
  Here again, clearing your owner's rotation :kbd:`Alt-R` might be useful...

The movement of the owner along the target curve/path may be controlled in two different ways:

- The most simple is to define the number of frames of the movement,
  in the :ref:`Path Animation panel <curve-path-animation>` of the Curve tab,
  via the *Frames* number field, and its start frame via the constraint's Offset option
  (by default, start frame: 1 [= offset of 0], duration: 100).
- The second way, much more precise and powerful,
  is to define an *Evaluation Time* interpolation curve for the *Target* path
  (in the *Graph Editor*). See the :doc:`Graph Editor chapter </editors/graph_editor/fcurves/index>`
  to learn more about F-Curves.
- If you do not want your owner to move along the path, you can give to the target curve a flat *Speed* F-Curve
  (its value will control the position of the owner along the path).

*Follow Path* is another constraint that works well with
the :doc:`Locked Track one </animation/constraints/tracking/locked_track>`.
One example is a flying camera on a path. To control the camera's roll angle,
you can use a *Locked Track* and a target object to specify the up direction, as the camera flies along the path.

.. note:: *Follow Path* & *Clamp To*

   Do not confuse these two constraints. Both of them constraint the location of their owner along a curve,
   but *Follow Path* is an "animation-only" constraint,
   inasmuch as the position of the owner along the curve is determined by the time (i.e. current frame),
   whereas the :doc:`Clamp To </animation/constraints/tracking/clamp_to>` *constraint* determines the position of its
   owner along the curve using one of its location properties' values.

.. note::

   Note that you also need to keyframe Evaluation Time for the Path. Select the path,
   go to the *Path Animation* panel in the curve properties,
   set the overall frame to the first frame of the path (e.g. frame 1),
   set the value of Evaluation time to the first frame of the path (e.g. 1), right-click on Evaluation time,
   select create keyframe, set the overall frame to the last frame of the path (e.g. frame 100),
   set the value of Evaluation time to the last frame of the path (e.g. 100), right-click on Evaluation time,
   select create keyframe.

.. from https://overshoot.tv/node/1123
   paragraph needs cleanup but this definitely needs to be in the documentation


Options
=======

.. figure:: /images/animation_constraints_relationship_follow-path_panel.png

   Follow Path panel.

Target
   :ref:`ui-data-id` used to select the constraint's target, which *must* be a curve object,
   and is not functional (red state) when it has none.
   See :ref:`common constraint properties <rigging-constraints-interface-common-target>` for more information.

Offset
   The number of frames to offset from the "animation" defined by the path (by default, from frame 1).

Forward Axis
   The axis of the object that has to be aligned with the forward direction of the path
   (i.e. tangent to the curve at the owner's position).

Up Axis
   The axis of the object that has to be aligned (as much as possible) with the world Z axis.
   In fact, with this option activated, the behavior of the owner shares some properties with
   the one caused by a :doc:`Locked Track constraint </animation/constraints/tracking/locked_track>`,
   with the path as "axle", and the world Z axis as "magnet".

Fixed Position
   Object will stay locked to a single point somewhere along the length of the curve regardless of time.

Curve Radius
   Objects scaled by the curve radius. See :doc:`Curve Editing </modeling/curves/properties/geometry>`.

Follow Curve
   If this option is not activated, the owner's rotation is not modified by the curve; otherwise,
   it is affected depending on the Forward and Up Axes.

Animate Path
   Adds an F-Curve with options for the start and end frame. ToDo: from above.

Influence
   Controls the percentage of affect the constraint has on the object.
   See :ref:`common constraint properties <bpy.types.constraint.influence>` for more information.


Example
=======

.. peertube:: 24507160-624d-423e-a8dd-5110ff8823d1


## Pivot

.. index:: Object Constraints; Pivot Constraint
.. _bpy.types.PivotConstraint:

****************
Pivot Constraint
****************

The *Pivot* constraint allows the owner to rotate around a target object.
It was originally intended for pivot joints found in humans
e.g. fingers, feet, elbows, etc.


Options
=======

.. figure:: /images/animation_constraints_relationship_pivot_panel.png

   Pivot panel.

Target
   :ref:`ui-data-id` for the selection of the object to be used as a pivot point.
   See :ref:`common constraint properties <rigging-constraints-interface-common-target>` for more information.

Use Relative Offset
   Offset will be an absolute point in space instead of relative to the target.

Pivot Point X, Y, Z
   Offset of pivot from target.

Rotation Range
   Rotation range on which pivoting should occur.

   Always
      Use the pivot point in every rotation.
   -X/-Y/-Z/X/Y/Z Rotation
      Use the pivot point in the corresponding direction around the corresponding axis.

Influence
   Controls the percentage of affect the constraint has on the object.
   See :ref:`common constraint properties <bpy.types.constraint.influence>` for more information.


Example
=======

.. peertube:: 1505f963-e5b7-4c31-96e8-d33ff09db532


## Shrinkwrap

.. index:: Object Constraints; Shrinkwrap Constraint
.. _bpy.types.ShrinkwrapConstraint:

*********************
Shrinkwrap Constraint
*********************

The *Shrinkwrap* constraint is the "object counterpart" of
the :doc:`Shrinkwrap Modifier </modeling/modifiers/deform/shrinkwrap>`.
It moves the owner origin and therefore the owner object's location to the surface of its target.
This implies that the target *must* have a surface; thus, you can only use meshes as targets.


Options
=======

.. figure:: /images/animation_constraints_relationship_shrinkwrap_panel.png

   Shrinkwrap panel.

Target
   :ref:`ui-data-id` used to select the constraint's target, which *must* be a mesh object,
   and is not functional (red state) when it has none.
   See :ref:`common constraint properties <rigging-constraints-interface-common-target>` for more information.

Distance
   This number field controls the offset of the owner from the shrunk computed position on the target's surface.

Influence
   Controls the percentage of affect the constraint has on the object.
   See :ref:`common constraint properties <bpy.types.constraint.influence>` for more information.


Mode
----

This selector allows you to select which method to use to compute the point on
the target's surface to which to move the owner's origin. You have these options:


Nearest Surface Point
^^^^^^^^^^^^^^^^^^^^^

The chosen target's surface's point will be the nearest one to the original owner's location.
This is the default and most commonly useful option.


Projection
^^^^^^^^^^

The target's surface point is determined by projecting the owner's origin along a given axis.

Project Axis
   This axis is controlled by the radio buttons that show up when you select this type.
   This mean the projection axis can only be aligned with one of the three axes, or their opposites.
   When the projection of the owner's origin along the selected direction does not hit the target's surface,
   the owner's location is left unchanged.

   +X, +Y, +Z, -X, -Y, -Z

Space
   Coordinate space in which the axis direction is specified.

Distance
   Distance cutoff after which projection is assumed to have failed, leaving the location unchanged.

Project Opposite
   In addition to the selected projection axis, project in the opposite direction and
   choose the closest hit.

Face Cull
   This radio button allows you to prevent any projection over the "front side"
   (respectively the "back side") of the target's faces. The "side" of a face is determined
   by its normal (front being the side "from where" the normal "originates").

   Off, Front, Back

   Invert Cull
      When used with *Project Opposite* and *Face Culling*, it inverts the *Front* or *Back* cull choice
      for the opposite direction.


Nearest Vertex
^^^^^^^^^^^^^^

This method is very similar to the *Nearest Surface Point* one,
except that the owner's possible shrink locations are limited to the target's vertices.

This method doesn't support the *Snap Mode* setting described below.


Target Normal Projection
^^^^^^^^^^^^^^^^^^^^^^^^

This method is similar to *Nearest Surface Point*, but produces a much smoother
projection in return for being significantly slower.

Instead of finding the closest point, it searches for the nearest point
that has its interpolated smooth normal pointing towards or away from the original owner position.
Non-manifold boundary edges are specially handled as infinitely thin cylinders
that emit normals in all perpendicular directions; ignores flat shading.


Snap Mode
---------

Most Shrinkwrap types support an additional setting to control how the owner is moved to
the target point selected by the methods described above. Some of the choices
only differ if *Distance* is not zero.

On Surface
   The owner location is always changed. The offset is applied along the projection line
   connecting the original owner location and selected target point towards
   the original position.

Outside Surface
   Like *On Surface*, but the offset is always applied towards the outside of the target.

Above Surface
   Like *On Surface*, but the offset is applied along the smooth normal of the target.

Inside
   The owner is not moved if it is already inside the target.
   Offset shrinks the allowed volume towards the inside along the projection line.

Outside
   The owner is not moved if it is already outside the target.
   Offset expands the exclusion volume towards the outside along the projection line.

The *Inside* and *Outside* options can be used for very crude collision detection.
The inside vs outside determination is done based on the target normal and
is not always stable near 90 degree and sharper angles in the target mesh.


Align To Normal
---------------

Whenever *Snap Mode* is available, it is also possible to align the specified
local axis of the object to the smooth normal of the target at the selected
point. The axis is selected via radio buttons.

The alignment is performed via smallest rotation, like in
:doc:`Damped Track </animation/constraints/tracking/damped_track>` constraint.


Example
=======

.. peertube:: 41a7d6c3-5bd2-450e-a49e-67edf078fe3a


## Clamp To

.. index:: Object Constraints; Clamp To Constraint
.. _bpy.types.ClampToConstraint:

*******************
Clamp To Constraint
*******************

The *Clamp To* constraint clamps an object to a curve. The *Clamp To* constraint is very similar
to the :doc:`Follow Path </animation/constraints/relationship/follow_path>` constraint,
but instead of using the evaluation time of the target curve, *Clamp To*
will get the actual location properties of its owner
(those shown in the *Transform* panel),
and judge where to put it by "mapping" this location along the target curve.

One benefit is that when you are working with *Clamp To*,
it is easier to see what your owner will be doing; since you are working in the 3D Viewport,
it will just be a lot more precise than sliding keys around on an F-Curve and
playing the animation over and over.

A downside is that unlike in the :doc:`Follow Path constraint </animation/constraints/relationship/follow_path>`,
*Clamp To* does not have any option to track your owner's rotation (pitch, roll, yaw)
to the banking of the targeted curve, but you do not always need rotation on,
so in cases like this it's usually a lot handier to fire up a *Clamp To*,
and get the bits of rotation you do need some other way.

The mapping from the object's original position to its position on the curve is not perfect,
but uses the following simplified algorithm:

.. Note, this may not be 100% accurate

- A "main axis" is chosen, either by the user, or as the longest axis of the curve's bounding box (the default).
- The position of the object is compared to the bounding box of the curve in the direction of the main axis.
  So for example if X is the main axis, and the object is aligned with the curve bounding box's left side,
  the result is 0; if it is aligned with the right side, the result is 1.
- If the cyclic option is unchecked, this value is clamped in the range 0-1.
- This number is used as the curve time, to find the final position along the curve that the object is clamped to.

This algorithm does not produce exactly the desired result because curve time does not map
exactly to the main axis position. For example an object directly in the center of a curve
will be clamped to a curve time of 0.5 regardless of the shape of the curve,
because it is halfway along the curve's bounding box.
However, the 0.5 curve time position can actually be anywhere within the bounding box!


Options
=======

.. figure:: /images/animation_constraints_tracking_clamp-to_panel.png

   Clamp To panel.

Target
   The target :ref:`ui-data-id` indicates which curve object the Clamp To constraint will track along.
   The target must be a curve object type.
   See :ref:`common constraint properties <rigging-constraints-interface-common-target>` for more information.

Main Axis
   This button group controls which global axis (X, Y or Z) is the main direction of the path.
   When clamping the object to the target curve, it will not be moved significantly on this axis.
   It may move a small amount on that axis because of the inexact way this constraint functions.

   For example if you are animating a rocket launch,
   it will be the Z axis because the main direction of the launch path is up.
   The default *Auto* option chooses the axis which the curve is longest in (or X if they are equal).
   This is usually the best option.

Cyclic
   By default, once the object has reached one end of its target curve, it will be constrained there.
   When the *Cyclic* option is enabled, as soon as it reaches one end of the curve,
   it is instantaneously moved to its other end.
   This is of course primarily designed for closed curves (e.g. circles),
   as this allows your owner to go around it over and over.

Influence
   Controls the percentage of affect the constraint has on the object.
   See :ref:`common constraint properties <bpy.types.constraint.influence>` for more information.


Example
=======

.. peertube:: c3e07449-aff7-43d6-b017-5bbd888cf52c


## Damped Track

.. index:: Object Constraints; Damped Track Constraint
.. _bpy.types.DampedTrackConstraint:

***********************
Damped Track Constraint
***********************

The *Damped Track* constraint constrains one local axis of the owner to always point towards *Target*.
This constraint uses a pure :term:`Swing` rotation, i.e. the shortest possible single axis rotation.
In other 3D software you can find it with the name "Look at" constraint.

Although usually associated with bones, Damped Track can align objects to point to (and follow)
other objects or bones. It is important to note that the constraint aligns the origin's axes to
point to the target's origin point. This is illustrated in the following figure.
In each case the objects are set as Damped Track to +X.

.. figure:: /images/animation_constraints_tracking_damped-track_axis.png
   :align: center

   A: Object vertices aligned along axis origin.
   B: Object vertices aligned away from origin.


Options
=======

.. figure:: /images/animation_constraints_tracking_damped-track_panel.png

   Damped Track panel.

Target
   :ref:`ui-data-id` used to select the constraint's target, and is not functional (red state) when it has none.
   See :ref:`common constraint properties <rigging-constraints-interface-common-target>` for more information.

Track Axis
   Once the owner object has had a Damped Track constraint applied to it,
   you must then choose which axis of the object you want to point at the Target object.
   The negative axis direction cause the object to point away from
   the Target object along the selected axis direction.

   -X, -Y, -Z, X, Y, Z

Influence
   Controls the percentage of affect the constraint has on the object.
   See :ref:`common constraint properties <bpy.types.constraint.influence>` for more information.


Example
=======

.. peertube:: 7a287522-9515-44f6-a4f2-34c5b5fb5f7a


## Ik Solver

.. index:: Object Constraints; Inverse Kinematics Constraint
.. _bpy.types.KinematicConstraint:

*****************************
Inverse Kinematics Constraint
*****************************

The *Inverse Kinematics* constraint implements the *inverse kinematics* armature
posing technique. Hence, it is only available for bones.
To quickly create an IK constraint with a target, select a bone in Pose Mode,
and press :kbd:`Shift-I`.

This constraint is fully documented in
the :ref:`Inverse Kinematics <bone-constraints-inverse-kinematics>` page, part of the rigging chapter.

.. note::

   The IK constraints are special in that they modify multiple bones.
   For this reason, they ignore their position in the stack and
   always run after all other constraints on the affected bones. To apply constraints after IK,
   it is necessary to first copy the final transformation to a new bone chain,
   e.g. using :doc:`Copy Transforms </animation/constraints/transform/copy_transforms>`.


Options
=======

.. figure:: /images/animation_constraints_tracking_ik-solver_panel.png

   Inverse Kinematics panel.

Target
   :ref:`ui-data-id` used to select the an armature.
   See :ref:`common constraint properties <rigging-constraints-interface-common-target>` for more information.

Pole Target
   Object for pole rotation.

Iterations
   Maximum number of solving iterations.

Chain Length
   How many bones are included in the IK effect. Set to 0 to include all bones.

Use Tail
   Include bone's tail as last element in chain.

Stretch
   Enable IK stretching.

Weight Position
   For Tree-IK: Weight of position control for this target.

Rotation
   Chain follows rotation of target.

Target
   Disable for targetless IK.

Influence
   Controls the percentage of affect the constraint has on the object.
   See :ref:`common constraint properties <bpy.types.constraint.influence>` for more information.


iTaSC Solver
------------

If the :ref:`iTaSC IK Solver <rigging-armatures_posing_bone-constraints_ik_model_itasc>`
is used, the IK Solver Constraint changes to add these addition parameters.

IK Type
   Copy Pose
      Equivalent to the traditional end effector position and orientation constraint:
      the end effector is constrained to take the position, and optionally the orientation,
      of a given target, which is set in the target field.

      Position/Rotation Locking
         Allows to obtain various effect by not constraining the coordinates along certain axis.

         Axis Reference
            Specifies how to compute the axis coordinates.

            Bone
               The coordinates are the position and orientation of the target relative to the bone.
            Target
               The opposite of *Bone*, the coordinates are the position and
               orientation of the tip of the bone relative to the target.
   Distance
      Specify that the end effector will stay inside, at, or outside a sphere centered on the target object.

      Limit Mode
         Inside
            The end effector will stay inside of the distance from the target object.
         Outside
            The end effector will stay outside of the distance from the target object.
         On Surface
            The end effector will stay exactly at the distance from the target object.

      Distance
         The radius from the target object.

.. note::

   The *Influence* parameter is not implemented if *Pole Target* is used.


Example
=======

.. peertube:: 20f9cc94-1c52-4485-bca3-272df8a899a2


## Locked Track

.. index:: Object Constraints; Locked Track Constraint
.. _bpy.types.LockedTrackConstraint:

***********************
Locked Track Constraint
***********************

The *Locked Track* constraint is a bit tricky to explain, both graphically and textual.
Basically, it is a :doc:`Track To constraint </animation/constraints/tracking/track_to>`,
but with a locked axis, i.e.
an axis that cannot rotate (change its orientation). Hence,
the owner can only track its target by rotating around this axis,
and unless the target is in the plane perpendicular to the locked axis, and crossing the owner,
this owner cannot really point at its target.

Let us take the best real-world equivalent: a compass.
It can rotate to point in the general direction of its target
(the magnetic North, or a neighbor magnet), but it cannot point *directly at it*,
because it spins like a wheel on an axle.
If a compass is sitting on a table and there is a magnet directly above it,
the compass cannot point to it. If we move the magnet more to one side of the compass,
it still cannot point *at* the target,
but it can point in the general direction of the target,
and still obey its restrictions of the axle.

When using a *Locked Track* constraint, you can think of the target as a magnet,
and the owner as a compass.
The *Lock* axis will function as the axle around which the owner spins,
and the *To* axis will function as the compass' needle.
Which axis does what is up to you!

If you have trouble understanding the buttons of this constraint, read the tooltips,
they are pretty good. If you do not know where your object's axes are,
enable *Axis* in :menuselection:`Properties --> Armature --> Viewport Display`.
Or, if you are working with bones, turn on the *Axes* in the armature's *Viewport Display* panel.

This constraint was designed to work cooperatively with the *Track To* constraint.
If you set the axes buttons right for these two constraints,
*Track To* can be used to point the axle at a primary target,
and *Locked Track* can spin the owner around that axle to a secondary target.

This constraint also works very well for 2D billboarding.


Options
=======

.. figure:: /images/animation_constraints_tracking_locked-track_panel.png

   Locked track panel.

Target
   :ref:`ui-data-id` used to select the constraints target, and is not functional (red state) when it has none.
   See :ref:`common constraint properties <rigging-constraints-interface-common-target>` for more information.

Track Axis
   The tracking local axis, i.e. the owner's axis to point at the target.
   The negative options force the relevant axis to point away from the target.

Locked Axis
   The locked local axis, i.e. the owner's axis which cannot be re-oriented to track the target.

.. important::

   If you choose the same axis for *Tracking Axis* and *Locked Axis*,
   the constraint will no longer be functional (red state).

Influence
   Controls the percentage of affect the constraint has on the object.
   See :ref:`common constraint properties <bpy.types.constraint.influence>` for more information.


Example
=======

.. peertube:: 5ce2dc9b-de49-4977-8e1f-9ddd5c2366d7


## Spline Ik

.. index:: Object Constraints; Spline IK Constraint
.. _bpy.types.SplineIKConstraint:

********************
Spline IK Constraint
********************

The *Spline IK* constraint aligns a chain of bones along a curve.
By leveraging the ease and flexibility of achieving aesthetically
pleasing shapes offered by curves and the predictability and well-integrated
control offered by bones, *Spline IK* is an invaluable tool in the riggers' toolbox.
It is particularly well suited for rigging flexible body parts such as tails, tentacles,
and spines, as well as inorganic items such as ropes.

To set up *Spline IK*, it is necessary to have a chain of
connected bones and a curve to constrain these bones to:

- With the last bone in the chain selected,
  add a *Spline IK* constraint from the *Bone Constraints* tab in the *Properties*.
- Set the 'Chain Length' setting to the number of bones in the chain
  (starting from and including the selected bone)
  that should be influenced by the curve.
- Finally, set *Target* to the curve that should control the curve.

.. note::

   The IK constraints are special in that they modify multiple bones.
   For this reason, they ignore their position in the stack and always run after
   all other constraints on the affected bones. To apply constraints after IK,
   it is necessary to first copy the final transformation to a new bone chain,
   e.g. using :doc:`Copy Transforms </animation/constraints/transform/copy_transforms>`.


Options
=======

.. figure:: /images/animation_constraints_tracking_spline-ik_panel.png

   Spline IK panel.

Target
   :ref:`ui-data-id` used to select the target curve.
   See :ref:`common constraint properties <rigging-constraints-interface-common-target>` for more information.

Influence
   Controls the percentage of affect the constraint has on the object.
   See :ref:`common constraint properties <bpy.types.constraint.influence>` for more information.


Fitting
-------

Chain Length
   How many bones are included in the chain.

Even Division
   Ignore the relative length of the bones when fitting to the curve.

Chain Offset
   Retain the offset of the root joint from the start point of the curve.


Chain Scaling
-------------

Use Curve Radius
   Average radius of the endpoints is used to tweak the X and Z scaling of
   the bones, on top of the X and Z scale mode.

Y Scale Mode
   Specifies how the length of a bone is scaled when it is fitted to the curve,
   in addition to the effects of target curve object scale and curvature.

   None
      The bone is reset to its rest pose length.
   Fit Curve
      The bones are stretched to cover the entire length of the curve.
   Bone Original
      The original Y axis scale of the bone is used.

XZ Scale Mode
   Scaling that a bone undergoes in the other two directions.

   None
      Do not scale the X and Z axes.
   Bone Original
      Use the original scaling of the bones.
   Inverse Scale
      Scale of the X and Z axes is the inverse of the Y scale.
   Volume Preservation
      Similar to the :ref:`Stretch To <constraints-stretch-to-volume-preservation>` constraint.

Use Original Scale
   Specifies that *Inverse Scale* or *Volume Preservation* should be applied on top of
   the original scaling of the bones, like in the Stretch To constraint.

.. seealso::

   This subject is seen in-depth in
   the :doc:`Armature Posing section </animation/armatures/posing/bone_constraints/inverse_kinematics/spline_ik>`.


Example
=======

.. peertube:: c17c1489-e4ae-440a-85e5-3ca5349d0cb9


## Stretch To

.. index:: Object Constraints; Stretch To Constraint
.. _bpy.types.StretchToConstraint:

*********************
Stretch To Constraint
*********************

The *Stretch To* constraint causes its owner to rotate and scale its Y axis towards its target.
So it has the same tracking behavior as the :doc:`Track To constraint </animation/constraints/tracking/track_to>`.
However, it assumes that the Y axis will be the tracking and stretching axis,
and does not give you the option of using a different one.

It also optionally has some raw volumetric features,
so the owner can squash down as the target moves closer,
or thin out as the target moves farther away.
Note however, that it is not the real volume of the owner which is thus preserved,
but rather the virtual one defined by its scale values. Hence,
this feature works even with non-volumetric objects, like empties, 2D meshes or surfaces,
and curves.

With bones, the "volumetric" variation scales them along their own local axes
(remember that the local Y axis of a bone is aligned with it, from root to tip).


Options
=======

.. figure:: /images/animation_constraints_tracking_stretch-to_panel.png

   Stretch To panel.

Target
   :ref:`ui-data-id` used to select the constraints target, and is not functional (red state) when it has none.
   See :ref:`common constraint properties <rigging-constraints-interface-common-target>` for more information.

Original Length
   This number field sets the rest distance between the owner and its target, i.e.
   the distance at which there is no deformation (stretching) of the owner.

   Reset Original Length ``X``
      When clicked, this small button will recalculate the *Rest Length* value,
      so that it corresponds to the actual distance between the owner and its target
      (i.e. the distance before this constraint is applied).

.. _constraints-stretch-to-volume-preservation:

Volume Variation
   This number field controls the amount of "volume" variation exponentially to the stretching amount.
   Note that the 0.0 value is not allowed, if you want to disable the volume feature,
   use the *None* button (see below).

Volume Min, Max
   Limits for the volume preservation to a minimum and maximum scaling each by a *Bulge* factor.

Smooth
   Smoothness factor to make limits less visible.

Maintain Volume
   These buttons control which of the X and/or Z axes should be affected (scaled up/down)
   to preserve the virtual volume while stretching along the Y axis.
   If you enable the *none* button, the volumetric features are disabled.

Rotation
   Specifies how the owner should be rotated to track the target with its Y axis.

   XZ, ZX
      These buttons are equivalent to the *Up* ones of
      the :doc:`Track To constraint </animation/constraints/tracking/track_to>`:
      the owner is rotated around two local axes in the specified order.
   Swing
      The constraint uses a single :term:`Swing` rotation, equivalent to
      the :doc:`Damped Track constraint </animation/constraints/tracking/damped_track>`.

Influence
   Controls the percentage of affect the constraint has on the object.
   See :ref:`common constraint properties <bpy.types.constraint.influence>` for more information.


Example
=======

.. peertube:: 50ecc2bc-44e1-4c5f-a3fc-6353a4624f0d


## Track To

.. index:: Object Constraints; Track To Constraint
.. _bpy.types.TrackToConstraint:

*******************
Track To Constraint
*******************

The *Track To* constraint applies rotations to its owner,
so that it always points a given "To" axis towards its target,
with another "Up" axis permanently maintained as much aligned with the global Z axis
(by default) as possible. This tracking is similar to the "billboard tracking" in 3D
(see note below).

This is the preferred tracking constraint,
as it has a more easily controlled constraining mechanism.

This constraint shares a close relationship to
the :doc:`Inverse Kinematics constraint </animation/constraints/tracking/ik_solver>` in some ways.

.. tip:: Billboard Tracking

   The term "billboard" has a specific meaning in real-time CG programming (i.e. video games!),
   where it is used for plane objects always facing the camera
   (they are indeed "trackers", the camera being their "target").
   Their main usage is as support for tree or mist textures:
   if they were not permanently facing the camera, you would often see your trees squeezing to nothing,
   or your mist turning into a mille-feuille paste, which would be funny but not so credible.


Options
=======

.. figure:: /images/animation_constraints_tracking_track-to_panel.png

   Track To panel.

Target
   :ref:`ui-data-id` used to select the constraints target, and is not functional (red state) when it has none.
   See :ref:`common constraint properties <rigging-constraints-interface-common-target>` for more information.

Track Axis
   The tracking local axis, i.e. the owner's axis to point at the target.
   The negative options force the relevant axis to point away from the target.

Up
   The "upward-most" local axis, i.e. the owner's axis to be aligned (as much as possible)
   with the global Z axis (or target Z axis, when the *Target* button is enabled).

Target Z
   By default, the owner's *Up* axis is (as much as possible) aligned with the global Z axis,
   during the tracking rotations. When this button is enabled, the *Up* axis will be (as much as possible)
   aligned with the target's local Z axis?

Target/Owner
   Standard conversion between spaces.
   See :ref:`common constraint properties <rigging-constraints-interface-common-space>` for more information.

Influence
   Controls the percentage of affect the constraint has on the object.
   See :ref:`common constraint properties <bpy.types.constraint.influence>` for more information.

.. warning::

   If you choose the same axis for *Tracking Axis* and *Up*,
   the constraint will not be functional anymore (red state).


Example
=======

.. peertube:: 891bf27f-f782-4908-bfa0-f99e5dc46107


## Copy Location

.. index:: Object Constraints; Copy Location Constraint
.. _bpy.types.CopyLocationConstraint:

************************
Copy Location Constraint
************************

The *Copy Location* constraint forces its owner to have the same location as its target.

.. important::

   Note that if you use such a constraint on a *connected* bone, it will have
   no effect, as it is the parent's tip which controls the position of your
   owner bone's root.


Options
=======

.. figure:: /images/animation_constraints_transform_copy-location_panel.png

   Copy Location panel.

Target
   :ref:`ui-data-id` used to select the constraints target, and is not functional (red state) when it has none.
   See :ref:`common constraint properties <rigging-constraints-interface-common-target>` for more information.

Axis
   These buttons control which axes are constrained.

Invert
   Invert their respective corresponding axis coordinates.

Offset
   When enabled, this control allows the owner to be moved (using its current transform properties),
   relative to its target's position.

Target/Owner
   Standard conversion between spaces.
   See :ref:`common constraint properties <rigging-constraints-interface-common-space>` for more information.

Influence
   Controls the percentage of affect the constraint has on the object.
   See :ref:`common constraint properties <bpy.types.constraint.influence>` for more information.


Examples
========

.. peertube:: 2f3dc43b-ef61-42ae-9d8e-7924a1758411


Animation
---------

Let us animate a solar system with the *Copy Location* constraint and its *Offset* option.
You can make the owner, called "moon", describe perfect circles centered on the world origin
(using e.g. *Location X/Y* sine and cosine F-Curves, see :ref:`bpy.types.FModifierFunctionGenerator`).
Then copy the location of a target "earth" with the *Offset* checkbox enabled
to model a satellite in a (simplified) orbit around its planet.
Repeat these steps for more planets circling around its center star "sun".

Following video is a small animation of a solar system created using (among a few others)
the previously described technique:

.. peertube:: ff427260-9631-40d9-bd39-65f21f95e9ad

Note that, this 'solar' system is not realistic at all
(the wrong scale, the earth is rotating in the wrong direction around the sun, ...).

You can download
the `blend-file <https://archive.blender.org/wiki/2015/index.php/File:ManAnimationTechsUsingConstraintsExSolarSys.blend>`__
used to create this animation.

Furthermore you can also animate a few properties of each constraint using animation curves:
e.g. you can animate the *Influence* of a constraint.
It is used to first let the camera follow the moon, then the earth,
and finally using two *Copy Location* constraints with *Offset* set.


## Copy Rotation

.. index:: Object Constraints; Copy Rotation Constraint
.. _bpy.types.CopyRotationConstraint:

************************
Copy Rotation Constraint
************************

The *Copy Rotation* constraint forces its owner to match the rotation of its target.


Options
=======

.. figure:: /images/animation_constraints_transform_copy-rotation_panel.png

   Copy Rotation panel.

Target
   :ref:`ui-data-id` used to select the constraints target, and is not functional (red state) when it has none.
   See :ref:`common constraint properties <rigging-constraints-interface-common-target>` for more information.

Order
   Allows specifying which :term:`Euler` order to use during the copy operation.
   Defaults to the order of the owner.

Axis
   These buttons control which axes are constrained.

Invert
   Invert their respective corresponding axis coordinates.

Mix
   Specifies how the new rotation is combined with the existing rotation.

   Replace
      The new axis values replace existing values.
   Add
      The new axis values are added to the existing values.
   Before Original
      The new rotation is added before the existing rotation, as if it was applied to
      a parent of the constraint owner.
   After Original
      The new rotation is added after the existing rotation, as if it was applied to
      a child of the constraint owner.
   Offset (Legacy)
      This replicates the behavior of the original Offset checkbox. It was intended
      to be similar to the *Before Original* behavior, but does not work correctly
      with multiple axis rotations, and is thus deprecated.

Target/Owner
   Standard conversion between spaces.
   See :ref:`common constraint properties <rigging-constraints-interface-common-space>` for more information.

Influence
   Controls the percentage of affect the constraint has on the object.
   See :ref:`common constraint properties <bpy.types.constraint.influence>` for more information.


Example
=======

.. peertube:: e28df5a9-3947-4c26-8969-5c8e029cd52e


## Copy Scale

.. index:: Object Constraints; Copy Scale Constraint
.. _bpy.types.CopyScaleConstraint:

*********************
Copy Scale Constraint
*********************

The *Copy Scale* constraint forces its owner to have the same scale as its target.

.. note::

   Here we talk of *scale*, not of *size*! Indeed, you can have two objects,
   one much bigger than the other, and yet both of them have the same scale.
   This is also true with bones: in *Pose Mode*,
   they all have a unitary scale when they are in rest position,
   represented by their visible length.


Options
=======

.. figure:: /images/animation_constraints_transform_copy-scale_panel.png

   Copy Scale panel.

Target
   :ref:`ui-data-id` used to select the constraints target, and is not functional (red state) when it has none.
   See :ref:`common constraint properties <rigging-constraints-interface-common-target>` for more information.

Axis
   These buttons control which axes of the target scale are copied.

Power
   Allows raising the copied scale to the specified arbitrary power.

Make Uniform
   Instead of copying scale for individual axes, apply a uniform scaling factor
   to all axes of the owner that achieves the same overall change in volume.

Offset
   When enabled, the constraint combines the copied scale with the owner's scale,
   instead of overwriting it.

Additive
   Uses addition instead of multiplication in the implementation of the *Offset* option.

Target/Owner
   Standard conversion between spaces.
   See :ref:`common constraint properties <rigging-constraints-interface-common-space>` for more information.

Influence
   Controls the percentage of affect the constraint has on the object.
   See :ref:`common constraint properties <bpy.types.constraint.influence>` for more information.

.. note::

   Since scale is a multiplicative quantity, it should be combined using multiplication,
   and split into fractions or inverted via power. Thus the use of *Power* is
   more mathematically correct than *Influence*, which uses linear interpolation.
   The use of the *Additive* option is also not recommended.

.. tip::

   To copy scale from one axis of the target to all axes of the owner,
   disable other axes, enable *Make Uniform*, and set *Power* to 3.


Example
=======

.. peertube:: 2d3eab8a-cc80-4d90-a3f1-419e2aa063f3


## Copy Transforms

.. index:: Object Constraints; Copy Transforms Constraint
.. _bpy.types.CopyTransformsConstraint:

**************************
Copy Transforms Constraint
**************************

The *Copy Transforms* constraint forces its owner to have the same transforms as its target.


Options
=======

.. figure:: /images/animation_constraints_transform_copy-transforms_panel.png

   Copy Transforms panel.

Target
   :ref:`ui-data-id` used to select the constraints target, and is not functional (red state) when it has none.
   See :ref:`common constraint properties <rigging-constraints-interface-common-target>` for more information.

Remove Target Shear
   Removes shearing from the target transformation after the target space conversion,
   ensuring it consists purely of translation, rotation and scale.
   Note that :doc:`Copy Rotation </animation/constraints/transform/copy_rotation>` always does this.

Mix
   Specifies how the copied transformation is combined with the existing transformation.

   Replace
      The new transformation replaces the existing transformation.

   Before/After Original (Full)
      The new transformation is added before/after the existing transformation, as if it was
      applied to an imaginary parent/child of the constraint owner. Scale is handled like in
      the most basic :ref:`Full Inherit Scale <bpy.types.EditBone.inherit_scale>` mode of bones,
      so combining non-uniform scale and rotation will create shear.

   Before/After Original (Aligned)
      The new transformation is added before/after the existing transformation, as if it was
      applied to an imaginary parent/child of the constraint owner. Scale is handled like in
      the :ref:`Aligned Inherit Scale <bpy.types.EditBone.inherit_scale>` mode of bones to
      avoid creating shear.

      This is equivalent to using the *Split Channels* option, but replacing the location component with
      the result of *Full*. If only uniform scale is used, the result is identical to *Full*.

   Before/After Original (Split Channels)
      Combines location, rotation and scale components of the transformation separately, similar
      to a sequence of three :doc:`Copy Location </animation/constraints/transform/copy_location>`,
      :doc:`Copy Rotation </animation/constraints/transform/copy_rotation>` and
      :doc:`Copy Scale </animation/constraints/transform/copy_scale>` (with Offset)
      constraints bundled together in one operation; the result may be slightly different
      in case of sheared inputs.

      Unlike *Aligned*, in this mode location channels are simply added together, so rotation
      and scale components of the input transformations cannot affect the resulting location.

Target/Owner
   Standard conversion between spaces.
   See :ref:`common constraint properties <rigging-constraints-interface-common-space>` for more information.

Influence
   Controls the percentage of affect the constraint has on the object.
   See :ref:`common constraint properties <bpy.types.constraint.influence>` for more information.


Example
=======

This video shows the difference between the mix modes. The right input is mixed after the left one:

.. peertube:: d6b5e955-aceb-4ba8-abd2-768413efc2d9

A general demonstration of the constraint:

.. peertube:: b18eea6f-c9a1-45a4-a83b-f2fffceedfd2


## Limit Distance

.. index:: Object Constraints; Limit Distance Constraint
.. _bpy.types.LimitDistanceConstraint:

*************************
Limit Distance Constraint
*************************

The *Limit Distance* constraint forces its owner to stay either further from,
nearer to, or exactly at a given distance from its target. In other words,
the owner's location is constrained either outside, inside,
or at the surface of a sphere centered on its target.

When you specify a (new) target, the *Distance* value is automatically set to
correspond to the distance between the owner and this target.

.. important::

   Note that if you use such a constraint on a *connected* bone, it will have
   no effect, as it is the parent's tip which controls the position of your
   owner bone's root.


Options
=======

.. figure:: /images/animation_constraints_transform_limit-distance_panel.png

   Limit Distance panel.

Target
   :ref:`ui-data-id` used to select the constraint's target, and is not functional (red state) when it has none.
   See :ref:`common constraint properties <rigging-constraints-interface-common-target>` for more information.

Distance
   This number field sets the limit distance, i.e. the radius of the constraining sphere.

   Reset Distance ``X``
      When clicked, this small button will reset the *Distance* value,
      so that it corresponds to the actual distance between the owner and its target
      (i.e. the distance before this constraint is applied).

Clamp Region
   The *Limit Mode* select menu allows you to choose how to use the sphere
   defined by the *Distance* setting and target's origin:

   Inside
      The owner is constrained *inside* the sphere.
   Outside
      The owner is constrained *outside* the sphere.
   Surface
      The owner is constrained *on the surface* of the sphere.

Affect Transform
   Transform operators will take the constraint into account to immediately restrict
   the resulting transform property values.

Target/Owner
   Standard conversion between spaces.
   See :ref:`common constraint properties <rigging-constraints-interface-common-space>` for more information.

Influence
   Controls the percentage of affect the constraint has on the object.
   See :ref:`common constraint properties <bpy.types.constraint.influence>` for more information.

.. tip::

   Evaluating both owner and target in a :ref:`Custom Space <rigging-constraints-interface-common-space-types>`
   using the root bone or any other suitable parent bone will automatically scale the effective distance with
   the relevant part of the rig.


Example
=======

.. peertube:: 9e842440-3133-4550-be4f-8fe73d7dfee0


## Limit Location

.. index:: Object Constraints; Limit Location Constraint
.. _bpy.types.LimitLocationConstraint:

*************************
Limit Location Constraint
*************************

An object or *unconnected* bone can be moved around the scene along the X, Y and Z axes.
This constraint restricts the amount of allowed translations along each axis,
through lower and upper bounds.

The limits for an object are calculated from its origin, and the limits of a bone, from its root.

It is interesting to note that even though the constraint limits the visual and
rendered location of its owner, its owner's data-block still allows (by default)
the object or bone to have coordinates outside the minimum and maximum ranges.
This can be seen in its *Transform* panel.

When an owner is selected and attempted to be moved outside the limit boundaries,
it will be constrained to those boundaries visually and when rendered, but internally,
its coordinates will still be changed beyond the limits. If the constraint is removed,
its ex-owner will seem to jump to its internally specified location.

Similarly, if its owner has an internal location that is beyond the limits, dragging it back
into the limit area will appear to do nothing until the internal coordinates are back within
the limit threshold (unless you enabled the *Affect Transform* option, see below).

Setting equal the min and max values of an axis,
locks the owner's movement along that axis... Although this is possible,
using the *Transformation Properties* axis locking feature is probably easier!


Options
=======

.. figure:: /images/animation_constraints_transform_limit-location_panel.png

   Limit Location panel.

Minimum X, Y, Z
   These buttons enable the lower boundary for the location of the owner's origin along,
   respectively, the X, Y and Z axes of the chosen *Space*.
   The number field below them controls the value of their limit.
   Note that if a min value is higher than its corresponding max value,
   the constraint behaves as if it had the same value as the max one.

Maximum X, Y, Z
   These buttons enable the upper boundary for the location of the owner's origin along,
   respectively, the X, Y and Z axes of the chosen *Space*.
   Same options as above.

Affect Transform
   As pointed out before by default, even though visually constrained,
   the owner can still have coordinates out of bounds (as shown by the *Transform* panel).
   Well, when you enable this checkbox, this is no longer possible --
   the owner's transform properties are also limited by the constraint.
   However, note that, the constraint does not directly modify the coordinates:
   you have to select its owner one way or another for this to take effect...

Owner
   This constraint allows you to choose in which space to evaluate its owner's transform properties.
   See :ref:`common constraint properties <rigging-constraints-interface-common-space>` for more information.

Influence
   Controls the percentage of affect the constraint has on the object.
   See :ref:`common constraint properties <bpy.types.constraint.influence>` for more information.


Example
=======

.. peertube:: 3a78daa9-3786-4510-98ae-f0045f692f5b


## Limit Rotation

.. index:: Object Constraints; Limit Rotation Constraint
.. _bpy.types.LimitRotationConstraint:

*************************
Limit Rotation Constraint
*************************

An object or bone can be rotated around the X, Y and Z axes.
This constraint restricts the amount of allowed rotations around each axis,
through lower and upper bounds.

It is interesting to note that even though the constraint limits the visual and
rendered rotations of its owner, its owner's data-block still allows (by default)
the object or bone to have rotation values outside the minimum and maximum ranges.
This can be seen in the *Transform* panel.
When an owner is rotated and attempted to be rotated outside the limit boundaries,
it will be constrained to those boundaries visually and when rendered, but internally,
its rotation values will still be changed beyond the limits. If the constraint is removed,
its ex-owner will seem to jump to its internally specified rotation.

Similarly, if its owner has an internal rotation that is beyond the limit, rotating it back
into the limit area will appear to do nothing until the internal rotation values are back
within the limit threshold (unless you enabled the *Affect Transform* option, see below).

Setting equal the min and max values of an axis,
locks the owner's rotation around that axis... Although this is possible,
using the *Transformation Properties* axis locking feature is probably easier.

This transform does not constrain the bone if it is manipulated by the IK solver.
For constraining the rotation of a bone for IK purposes,
see :doc:`Inverse Kinematics </animation/armatures/posing/bone_constraints/inverse_kinematics/introduction>`.


Options
=======

.. figure:: /images/animation_constraints_transform_limit-rotation_panel.png

   Limit Rotation panel.

Limit X, Y, Z
   These buttons enable the rotation limit around respectively the X, Y and Z axes of the owner,
   in the chosen *Owner* space.
   The *Min* and *Max* number fields to their right control the value of
   their lower and upper boundaries, respectively.

   .. note::

      - If a min value is higher than its corresponding max value,
        the constraint behaves as if it had the same value as the max one.
      - Unlike the :doc:`Limit Location constraint </animation/constraints/transform/limit_location>`,
        you cannot separately enable lower or upper limits.
      - The constraint can be used to simply remove shear from the owner transformation
        by leaving all limits disabled.

Order
   Allows specifying which :term:`Euler` order to use when applying the limits.
   Defaults to the order of the owner.

Affect Transform
   The constraint is taken into account when the object is manually rotated using
   transformation tools in the editors. This prevents assigning transformation
   property values (as shown in the *Transform* panel) that exceed the specified limits.

Owner
   This constraint allows you to choose in which space evaluate its owner's transform properties.
   See :ref:`common constraint properties <rigging-constraints-interface-common-space>` for more information.

Influence
   Controls the percentage of affect the constraint has on the object.
   See :ref:`common constraint properties <bpy.types.constraint.influence>` for more information.


Example
=======

.. peertube:: 3ce2539e-3bb9-4caf-9911-1217a1e8907c


## Limit Scale

.. index:: Object Constraints; Limit Scale Constraint
.. _bpy.types.LimitScaleConstraint:

**********************
Limit Scale Constraint
**********************

An object or bone can be scaled along the X, Y and Z axes.
This constraint restricts the amount of allowed scaling along each axis,
through lower and upper bounds.

.. important::

   This constraint does not tolerate negative scale values
   (those you might use to mirror an object...): when you add it to an object or bone,
   even if no axis limit is enabled, nor the *Affect Transform* option,
   as soon as you scale your object,
   all negative scale values are instantaneously inverted to positive ones...
   And the boundary settings can only take strictly positive values.

It is interesting to note that even though the constraint limits the visual and rendered scale
of its owner, its owner's data-block still allows (by default)
the object or bone to have scale values outside the minimum and maximum ranges
(as long as they remain positive!).
This can be seen in its *Transform* panel.
When an owner is scaled and attempted to be moved outside the limit boundaries,
it will be constrained to those boundaries visually and when rendered, but internally,
its coordinates will still be changed beyond the limits. If the constraint is removed,
its ex-owner will seem to jump to its internally-specified scale.

Similarly, if its owner has an internal scale that is beyond the limits, scaling it back into
the limit area will appear to do nothing until the internal scale values are back
within the limit threshold (unless you enabled the *Affect Transform* option,
see below, or your owner has some negative scale values).

Setting equal the min and max values of an axis locks the owner's scaling along that axis.
Although this is possible,
using the *Transformation Properties* axis locking feature is probably easier.


Options
=======

.. figure:: /images/animation_constraints_transform_limit-scale_panel.png

   Limit Scale panel.

Minimum/Maximum X, Y, Z
   These buttons enable the lower boundary for the scale of the owner along respectively the X,
   Y and Z axes of the chosen *Space*.
   The *Min* and *Max* number fields to their right control the value of
   their lower and upper boundaries, respectively.

   .. note::

      If a min value is higher than its corresponding max value,
      the constraint behaves as if it had the same value as the max one.

Affect Transform
   As pointed out before by default, even though visually constrained, and except for the negative values,
   the owner can still have scales out of bounds (as shown by the *Transform* panel).
   When you enable this checkbox, this is no longer possible,
   the owner transform properties are also limited by the constraint.
   However, note that, the constraint does not directly modify the scale values:
   you have to scale its owner one way or another for this to take effect.

Owner
   This constraint allows you to choose in which space to evaluate its owner's transform properties.
   See :ref:`common constraint properties <rigging-constraints-interface-common-space>` for more information.

Influence
   Controls the percentage of affect the constraint has on the object.
   See :ref:`common constraint properties <bpy.types.constraint.influence>` for more information.


Example
=======

.. peertube:: b73800d7-dda8-4888-b48b-f649e9b7ae3b


## Maintain Volume

.. index:: Object Constraints; Maintain Volume Constraint
.. _bpy.types.MaintainVolumeConstraint:

**************************
Maintain Volume Constraint
**************************

The *Maintain Volume* constraint limits the volume of a mesh or
a bone to a given ratio of its original volume.

.. seealso::

   `Harkyman on the development of the Maintain Volume constraint
   <https://web.archive.org/web/20220702025853/http://www.harkyman.com/2010/03/16/
   maintaining-bone-volume-a-new-constraint/>`__.


Options
=======

.. figure:: /images/animation_constraints_transform_maintain-volume_panel.png

   Maintain Volume Constraint.

Mode
   Specifies how the constraint handles scaling of the non-free axes.

   Strict
      This mode overrides non-free axis scaling to strictly maintain the specified volume.
      Only the ratio between the scale of the non-free axes is passed through.
   Uniform
      This mode maintains the volume as specified only when the pre-constraint scaling is uniform.
      Deviations from uniform scaling on non-free axes are passed through.
   Single Axis
      This mode maintains the volume only when the object is scaled just on its free axis.
      Any additional non-free axis scaling is passed through.

Free Axis
   The free-scaling axis of the object.

Volume
   The bone's rest volume.

Owner
   This constraint allows you to choose in which space to evaluate its owner's transform properties.
   See :ref:`common constraint properties <rigging-constraints-interface-common-space>` for more information.

Influence
   Controls the percentage of affect the constraint has on the object.
   See :ref:`common constraint properties <bpy.types.constraint.influence>` for more information.


Example
=======

.. peertube:: 8f39c857-6e59-43d7-86a0-c0aa4549202f


## Transformation

.. index:: Object Constraints; Transformation Constraint
.. _bpy.types.TransformConstraint:

*************************
Transformation Constraint
*************************

This constraint is more complex and versatile than the other "transform" constraints.
It lets you set the location, rotation or scale of an object/bone based on the
location, rotation or scale of another, mixing and matching axes as you see fit.
An example could be to set a gear's X rotation based on the Y coordinate of
a rail next to it.

The constraint works with input and output value ranges, one for each axis.
It first clamps the input value to the *Map From* range, then offsets and scales it
to the corresponding *Map To* range. This lets you, say, map a Y coordinate
in the range (-3m, 3m) to an X rotation in the range (0, 180°).


Options
=======

.. figure:: /images/animation_constraints_transform_transformation_panel.png

   Transformation panel.

Target
   The reference object to read a transformation property from. If you don't select one, the constraint's
   icon will turn red and it will have no effect.

   See :ref:`common constraint properties <rigging-constraints-interface-common-target>` for more information.

Bone
   If *Target* is an :doc:`Armature </animation/armatures/introduction>`, you can optionally choose a
   bone here to use the transformation of that bone instead of the armature object as a whole.

Extrapolate
   By default, the input and output values are clamped to the *Min/Max* values.
   When you enable *Extrapolate*, they're allowed to go beyond these limits.
   This is illustrated with the graphs below, where the X axis represents the input
   (*Map From* set to *Min* = 1 and *Max* = 4) and the Y axis represents the output
   (*Map To* set to *Min* = 1 and *Max* = 2).

   .. _fig-constraints-transformation-extrapolate:

   .. list-table:: The Extrapolate option.

      * - .. figure:: /images/animation_constraints_transform_transformation_extrapolate-1.png

             Extrapolate disabled: the output values are limited to the Map To range.

        - .. figure:: /images/animation_constraints_transform_transformation_extrapolate-2.png

             Extrapolate enabled: the output values can extend beyond the limits.

Target/Owner
   Standard conversion between spaces.
   See :ref:`common constraint properties <rigging-constraints-interface-common-space>` for more information.

Influence
   Controls the percentage of effect the constraint has on the object.
   See :ref:`common constraint properties <bpy.types.constraint.influence>` for more information.


Map From
--------

The transformation to read from the *Target* (or *Bone*).

Location, Rotation, Scale
   The type of transformation to read.

Mode :guilabel:`Rotation`
   The type of rotation to use, including different :term:`Euler` orders,
   :term:`Quaternion`, and other :ref:`Rotation Channel Modes <drivers-variables-rotation-modes>`.
   Defaults to using the :term:`Euler` order of the constraint owner.

   In the *Quaternion* mode, the channels are converted to weighted angles in the same way as
   the swing angles of the :ref:`Swing and X/Y/Z Twist <drivers-variables-rotation-modes>` modes.

X/Y/Z Min, Max
   The input value range for each axis.


Map To
------

The transformation to apply to the owner.

Location, Rotation, Scale
   The type of transformation to apply.

Order :guilabel:`Rotation`
   Which :term:`Euler` order to use. Defaults to the order of the constraint owner.

X/Y/Z Source Axis
   For each of the three output axes, lets you choose the input axis that it should take
   its value from. You can select the same input axis multiple times.

Min, Max
   The output value range for each axis.

Mix
   Specifies how the result of the constraint is combined with the existing transformation.
   The set of available choices varies based on the type of transformation.

   Replace
      The result of the constraint replaces the existing transformation.
   Multiply :guilabel:`Scale`
      The new values are multiplied with the existing axis values.
   Add :guilabel:`Location` :guilabel:`Rotation`
      The new values are added to the existing axis values.
   Before Original :guilabel:`Rotation`
      The new rotation is added before the existing rotation, as if it were applied to
      a parent of the constraint owner.
   After Original :guilabel:`Rotation`
      The new rotation is added after the existing rotation, as if it were applied to
      a child of the constraint owner.

.. note::

   - For historical reasons, the *Mix* mode defaults to *Add* for location and rotation,
     and *Replace* for scale.
   - When using the rotation of the target as input,
     whatever the real values are, the constraint will always "take them back" into the (-180 to 180) range.
     E.g. if the target has a rotation of 420 degrees around its X axis,
     the values used as *X* input by the constraint will be:

     :math:`((420 + 180) modulo 360) - 180 = 60 - 180 = -120`

     As such, this constraint is not really suited for transforming an object based on a gear's rotation.
     Rotating a gear based on an object's transformation works fine, however.
   - Similarly, when using the scale transform properties of the target as input,
     whatever the real values are, the constraint will always take their absolute values (i.e. invert negative ones).
   - When a *Min* value is higher than its corresponding *Max* one,
     both are considered equal to the *Max* one. This means you cannot create "reversed" mappings.


Example
=======

In the following example, we add a constraint to a gear that sets its X rotation based on the
Y position of a rail:

- Target: Rail object

- Map From: Location

  * Y Min: -3m
  * Y Max: 3m

- Map To: Rotation

  * X Source Axis: Y
  * X Min: 0°
  * X Max: 180°

.. figure:: /images/animation_constraints_transform_example_before.png

   Before moving the rail.

.. figure:: /images/animation_constraints_transform_example_after.png

   After moving the rail.

By default, the gear will stop rotating if the rail goes outside the (-3m, 3m) range.
You can enable *Extrapolate* to change this.


## Transform Cache

.. index:: Object Constraints; Transform Cache Constraint
.. _bpy.types.TransformCacheConstraint:

**************************
Transform Cache Constraint
**************************

The *Transform Cache Constraint* is used to stream animations from
:doc:`Alembic </files/import_export/alembic>` or :doc:`USD </files/import_export/usd>`
made at the transformation matrix level (for example rigid bodies, or camera movements).

When importing an :doc:`Alembic </files/import_export/alembic>` or
:doc:`USD </files/import_export/usd>` file,
Transform Cache constraints are automatically added to objects with animated transforms.
For time-varying meshes (so deforming animations),
the :doc:`Mesh Sequence Cache modifier </modeling/modifiers/modify/mesh_sequence_cache>` is used.


Options
=======

.. figure:: /images/animation_constraints_transform_transform-cache_panel.png

   Transform Cache Constraint.

Cache File
   Data-block menu to select the Alembic or USD file.

File Path
   Path to the Alembic or USD file.

Sequence
   Whether or not the cache is separated in a series of files.

Override Frame
   Whether to use a custom frame for looking up data in the cache file,
   instead of using the current scene frame.

   The *Frame* value is the time to use for looking up the data in the cache file,
   or to determine which to use in a file sequence.

Frame Offset
   Subtracted from the current frame to use for looking up the data in the cache file,
   or to determine which file to use in a file sequence.

Manual Scale
   Value by which to enlarge or shrink the object with respect to the world's origin.

Velocity Attribute
   The name of the Alembic attribute used for generating motion blur data;
   by default, this is ``.velocities`` which is standard for most Alembic files.

   .. note:: The *Velocity Attribute* option is currently for Alembic files only.

Velocity Unit
   Defines how the velocity vectors are interpreted with regard to time.

   Frame
      The velocity unit was encoded in frames and does not need to be scaled by scene FPS.
   Second
      The velocity unit was encoded in seconds and needs to be scaled by the scene FPS (1 / FPS).

   .. note:: The *Velocity Unit* option is currently for Alembic files only.

Object Path
   The path to the Alembic or USD object inside the archive or stage.

Influence
   Controls the percentage of affect the constraint has on the object.
   See :ref:`common constraint properties <bpy.types.constraint.influence>` for more information.


## Drivers Panel


*************
Drivers Panel
*************

.. figure:: /images/animation_drivers_drivers-panel_panel.png
   :align: right

   Edit Driver popover.

.. reference::

   :Editor:    Graph editor
   :Mode:      Drivers
   :Panel:     :menuselection:`Sidebar region --> Drivers`
   :Shortcut:  :kbd:`N`

.. reference::

   :Menu:      :menuselection:`Context menu --> Edit Driver`
   :Shortcut:  :kbd:`Ctrl-D`

This panel is visible in Sidebar of the :doc:`Drivers Editor </editors/drivers_editor>`
or as a popover when adding a driver to a property.

It shows the property that is being driven, followed by a series of settings
that determine how the driver works.


Driver Settings
===============

.. _bpy.types.Driver.type:

Type
----

There are two categories of drivers:

- **Built-in functions** (*Average*, *Sum*, *Min* and *Max*)

  The driven property will have the value of the average, sum, lowest or highest (respectively)
  of the values of the referenced *Driver Variables*.
  If there is only one driver variable, these functions will yield the same result.

- **Custom** (*Scripted Expression*).

  An arbitrary Python expression that can refer to the *Driver Variables* by name. See `Expressions`_.


Driver Value
------------

The current result of the driver setup. Useful for debug purposes.


Variables
---------

See `Driver Variables`_.


Update Dependencies
-------------------

Forces an update for the Driver Value dependencies.


Show in Drivers Editor
----------------------

Opens the fully featured :doc:`Drivers Editor </editors/drivers_editor>`.
This button only appears in the popover version of the Drivers panel.


.. _drivers-variables:
.. _bpy.types.DriverTarget:

Driver Variables
================

Variables are references to properties, transformation channels, or the result of a comparison
between transformations of two objects.

Drivers should access object data via *Driver Variables*, rather than direct references in the Python expression,
in order for dependencies to be correctly tracked.

.. figure:: /images/animation_drivers_drivers-panel_add-variable.png
   :align: right

   Add, Copy, Paste buttons.

Add Input Variable
   Adds a new Driver Variable.

.. _bpy.ops.graph.driver_variables_copy:
.. _bpy.ops.graph.driver_variables_paste:

Copy/Paste Variables
   Copies the current variable list so it can be pasted into another driver's variable list.

.. _bpy.types.DriverVariable.name:

Name
   Name for use in scripted expressions.
   The name must start with a letter, and only contain letters, digits, or underscores.

.. _bpy.types.DriverVariable.type:

Variable Type
   The type of variable to use.

   Single Property
      .. figure:: /images/animation_drivers_drivers-panel_single-property.png
         :align: right
         :width: 200px

      Retrieves the value of an RNA property, specified by a data-block reference and a path string.

      In case of transform properties, this will return the exact value of the UI property,
      while Transform Channel will take parenting and/or constraints into account as needed.

      See also :ref:`files-data_blocks-custom-properties`.

      ID Type
         The ID-block type. For example: Key, Image, Object, Material.
      ID
         The ID of the ID-block type. For example: "Material.001".
      RNA Path
         The RNA name of the property, based on a subset of Python attribute access syntax.
         For example: ``location.x`` or ``location[0]`` for the X location animation channel
         value (before parenting or constraints), or ``["prop_name"]`` for a custom property.
      Fallback
         If enabled, allows specifying a fallback value to use as the variable value if the RNA Path cannot
         be resolved, instead of causing a driver evaluation failure. For more info see
         :ref:`Context Property <bpy.types.DriverVariable.type.CONTEXT_PROP>` below.

      .. tip::

         The easiest way to create a variable of this type is to use
         the :ref:`Copy As New Driver <drivers-copy-as-new>`
         context menu option of the input property, and paste the result
         into the driver via :ref:`Paste Driver Variables <drivers-variables>`.

   Transform Channel
      .. figure:: /images/animation_drivers_drivers-panel_transform-channel2.png
         :align: right
         :width: 200px

      Retrieves the value of a Transform channel from an object or bone.

      ID
         ID of the object. For example: Cube, Armature, Camera.
      Bone
         For armatures, the name of the Armature bone. For example: "Bone", "Bone.002", "Arm.r".
      Type
         For example, X Location, X Rotation, X Scale.

         The *Average Scale* option retrieves the combined scale value,
         computed as the cubic root of the total change in volume.
         Unlike *X/Y/Z Scale*, this value can be negative if the object is flipped by negative scaling.
      Mode (Rotation)
         For rotation channels, specifies the type of rotation data to use, including
         different explicit :term:`Euler` orders. Defaults to using the Euler order of
         the target. See `Rotation Channel Modes`_.
      Space
         World Space, Transform Space, Local Space.

      .. figure:: /images/animation_drivers_drivers-panel_rotational-difference.png
         :align: right
         :width: 200px

   Rotational Difference
      Provides the value of the rotational difference between two objects or bones, in radians.

      Bone
         For armatures, the name of the Armature bone. For example: "Bone", "Bone.002", "Arm.r".

   Distance
      .. figure:: /images/animation_drivers_drivers-panel_distance.png
         :align: right
         :width: 200px

      Provides the value of the distance between two objects or bones.

      Bone
         For armatures, the name of the Armature bone. For example: "Bone", "Bone.002", "Arm.r".

      Space
         World Space, Transform Space, Local Space.

   .. _bpy.types.DriverVariable.type.CONTEXT_PROP:

   Context Property
      .. figure:: /images/animation_drivers_drivers-panel_context-property.png
         :align: right
         :width: 200px

      Provides the value of a property that is implicitly referring to either a scene
      or a view layer of the currently evaluating animation system.
      This is a weak reference which does not lead to the scene or view layer
      referenced from the driver to be linked when linking animation data.

      An example when such properties comes in play is referring to a transformation
      of the active camera. It is possible to set up a driver in a character file,
      and make the driver use the set camera when the character is linked into a set.

      Context
         Active Scene, Active View Layer.

      RNA Path
         The RNA name of the property, based on a subset of Python attribute access syntax.
         For example: ``camera.location.x`` or ``camera.location[0]`` for the camera X location animation
         channel value (before parenting or constraints), or ``["prop_name"]`` for a custom property.

      Fallback
         If enabled, allows specifying a fallback value to use as the variable value if the RNA Path cannot
         be resolved, instead of causing a driver evaluation failure.

         This feature can be very useful for making drivers more robust when implementing scene-global options
         using custom properties. When the object is linked into a different scene, these custom properties may
         not exist there, and the fallbacks can be used to provide sensible default values.

         Fallbacks can also be used to :ref:`emulate <driver-attribute-node-emulation>`
         the lookup behavior of the View Layer mode of the material
         :doc:`Attribute Node </render/shader_nodes/input/attribute>`.

      .. tip::

         Although the values of the x/y/z animation channels for the camera location can be accessed
         via ``camera.location[0/1/2]``, retrieving its world space location and orientation after parenting
         and constraints currently requires using ``camera.matrix_world``. This property can be understood
         easily by viewing the matrix as an array of four vectors in *World* space:

         * ``matrix_world[0][0/1/2]`` is the *Screen Right* direction vector (camera local X).
         * ``matrix_world[1][0/1/2]`` is the *Screen Up* direction vector (camera local Y).
         * ``matrix_world[2][0/1/2]`` is the **opposite** of the direction the camera is pointing.
         * ``matrix_world[3][0/1/2]`` is the *location* of the camera.

Value
   Shows the value of the variable.


.. _drivers-variables-rotation-modes:

Rotation Channel Modes
----------------------

Rotation Transform Channels support a number of operation modes, including:

Auto Euler
   Uses the :term:`Euler` order of the target to decompose rotation into channels.
XYZ Euler, ...
   Explicitly specifies the :term:`Euler` rotation order to use.
Quaternion
   Provides the :term:`Quaternion` representation of the rotation.
Swing and X/Y/Z Twist
   Decomposes the rotation into two parts: a :term:`Swing` rotation that aims the specified
   axis in its final direction, followed by a :term:`Twist <Swing>` rotation around that axis.
   This is often necessary for driving corrective :doc:`Shape Keys </animation/shape_keys/index>`
   and bones for organic joint rotation.

   This decomposition is often produced in rigs by using a helper bone with
   a :doc:`Damped Track Constraint </animation/constraints/tracking/damped_track>`
   to extract the swing part, and its child with
   :doc:`Copy Transforms </animation/constraints/transform/copy_transforms>`
   to extract the twist component.

   The channels values for *Swing and Y Twist* are:

   .. figure:: /images/animation_drivers_drivers-panel_angle-curve.png
      :align: right

      Falloff curves for weighted angles.

   Y Rotation
      True angle of the twist rotation.
   W Rotation
      True angle of the swing rotation, independent of its direction.
   X Rotation, Z Rotation
      Weighted angles that represent the amount of swing around the X/Z axis.

      The magnitude of the angle equals *W Rotation* when the rotation is purely around
      that axis, and fades out to zero as the direction changes toward the other axis,
      following the falloff curves from the graph on the right.

   Mathematically, the swing angles are computed from quaternion components,
   using :math:`2 \arccos(w)` for *W* and :math:`2 \arcsin(x)` etc. for the others.
   The component of the swing rotation that corresponds to the twist axis is always 0,
   and is replaced by the twist angle.


Expressions
===========

.. _bpy.types.Driver.expression:

Expression
   A text field where you can enter an arbitrary Python expression that refers to
   *Driver Variables* by their names.

   The expression has access to a set of standard constants and math functions from ``math``,
   ``bl_math`` and other modules, provided in the *Driver Namespace*. For an example of adding
   a custom function to the namespace, see the :ref:`driver namespace example <driver-namespace>`.

   For performance reasons it is best to use the `Simple Expressions`_ subset as much as possible.

.. _bpy.types.Driver.use_self:

Use Self
   If this option is enabled, the variable ``self`` can be used for drivers to reference their own data.
   Useful for objects and bones to avoid having creating a *Driver Variable* pointing to itself.

   Example: ``self.location.x`` applied to the Y rotation property of the same object
   will make the object tumble when moving.

   Note that dependencies for properties accessed via ``self`` may not be fully tracked.


.. _drivers-simple-expressions:

Simple Expressions
------------------

Blender can evaluate a useful subset of Python driver expressions directly,
which significantly improves performance, especially on multi-core systems.
To take advantage of this, the driver expression must only use the following features:

Variable Names
   Use only ASCII characters.
Literals
   Floating-point and decimal integer.
Globals
   ``frame``
Constants
   ``pi``, ``True``, ``False``
Operators
   ``+``, ``-``, ``*``, ``/``,
   ``==``, ``!=``, ``<``, ``<=``, ``>``, ``>=``,
   ``and``, ``or``, ``not``, conditional operator/ ternary if
Standard Functions
   ``min``, ``max``, ``radians``, ``degrees``,
   ``abs``, ``fabs``, ``floor``, ``ceil``, ``trunc``, ``round``, ``int``,
   ``sin``, ``cos``, ``tan``, ``asin``, ``acos``, ``atan``, ``atan2``,
   ``exp``, ``log``, ``sqrt``, ``pow``, ``fmod``
Blender Provided Functions
   ``lerp``, ``clamp``, ``smoothstep``

Simple expressions are evaluated even when Python script execution is disabled.

When an expression outside of this subset is used, Blender displays a "Slow Python expression"
warning. However, as long as the majority of drivers use simple expressions, using a complex
expression in select few is OK.

.. seealso::

   - :ref:`Extending Blender with Python <scripting-index>`.

   - `Python <https://www.python.org>`__ and its `documentation <https://docs.python.org/>`__.
   - `functions.wolfram.com <https://functions.wolfram.com/>`__.


## Index

.. _animation-drivers-index:
.. _bpy.types.Driver:

###########
  Drivers
###########

.. toctree::
   :maxdepth: 2

   introduction.rst
   usage.rst
   drivers_panel.rst
   workflow_examples.rst
   troubleshooting.rst


## Introduction


************
Introduction
************

Drivers are a way to control values of properties by means of a function,
or a mathematical expression.

Effectively, drivers consist of:

- A **driver configuration** that specifies zero, one, or more input values using
  other properties or object transformation channels, and combines them using
  a predefined mathematical function or a custom Python expression.
- An **animation** :doc:`F-Curve </editors/graph_editor/fcurves/introduction>`
  that maps the output of the driver configuration to the final value to apply
  to the driven property.

As an example, the rotation of Object 1 can be controlled by the scale of Object 2.
It is then said that the scale of Object 2 *drives* the rotation of Object 1.

Not only can drivers directly set the value of a property to the value of a different one,
they can also combine multiple values using a fixed function or a Python expression
and further modulate it with a manually defined curve and/or a modifier stack.

Drivers are an extremely powerful tool for building rigs and are typically used
to drive bone transforms and the influence of shape keys, action constraints and
modifiers, often using custom properties as inputs.


Graph View
==========

.. figure:: /images/animation_drivers_introduction_fcurve.png
   :align: right

   Driver curve in the Drivers editor.

The main area of the :doc:`Drivers editor </editors/drivers_editor>`
shows an :doc:`F-Curve </editors/graph_editor/fcurves/introduction>` that
represents the driver function.

The **X axis** maps to the output value of the driver configuration. The units depend on the setup.

The **Y axis** shows the value applied to the target property. The units depend on the property.

In the example image, if the driver value is 2.0 the property value will be 0.5.

The default F-Curve is an identity map, i.e. the value produced by the driver configuration
is applied to the driven property unchanged. If the driver output value is 2.0,
the property will be 2.0.

The driver function can be defined artistically with Bézier curve handles or
mathematically with trigonometric functions or polynomial expressions such as :math:`y = a + bx`.
Furthermore, the function can also be procedurally modulated with noise or cyclic repetitions.
See :doc:`Modifiers </editors/graph_editor/fcurves/modifiers>` for more details.


Driver Configuration
====================

The :doc:`Drivers panel </animation/drivers/drivers_panel>` shows the setup for a driver.

A driver can have zero, one, or more **variables**. Variables specify which properties,
object transformation channels, or relative distances between objects, are used as inputs
by the driver.

The driver **type** determines how the variables are used. The type can be:

- a built-in function: for example, the sum of the variables' values, or
- a scripted expression: an arbitrary Python expression that refers to the variables by their names.

This driver configuration outputs a single value which changes when the variables change.
This value is then evaluated through the driver function curve to produce the result
to be applied to the driven property.


Notes on Scripted Expressions
=============================

When a driver uses a *Scripted Expression*, Blender can evaluate it without using
the fully featured Python interpreter if it is simple enough.
This means that drivers are fast to evaluate with simple divisions, additions and other "simple" expressions.
The built-in functions are always evaluated natively.

See :ref:`Simple Expressions <drivers-simple-expressions>`
for a comprehensive list of expressions that can be evaluated natively.

When the expression is not simple, it will be evaluated using Python.
As a consequence, the driver will be slower and there is a security risk
if the author of the Python code is unknown.
This is an important thing to take into consideration for heavy scenes and
when sharing files with other people.
See also: :doc:`Auto run </advanced/scripting/security>`.


## Troubleshooting


***************
Troubleshooting
***************

Some common problems people may run into when using drivers.


Scripted Expression
===================

.. figure:: /images/animation_drivers_troubleshooting_autorun-graph-editor.png

   A security warning in the Drivers panel.

.. figure:: /images/advanced_scripting_security_autorun-scripts-dialog.png

   An Auto-run warning in the Info editor's header.

By default Blender will restrict execution of Python scripts.

If using a *Scripted Expression* Driver Type that doesn't follow
the :ref:`Simple Expressions <drivers-simple-expressions>`
subset, you will have to open the file as *Trusted Source*,
or set *Auto Run Python Scripts* in :menuselection:`Preferences --> Save & Load --> Blender Files`.

.. list-table::
   :widths: 40 60

   * - .. figure:: /images/animation_drivers_troubleshooting_autorun-file-browser.png

          The Trusted Source checkbox in the File Browser.

     - .. figure:: /images/animation_drivers_troubleshooting_autorun-user-preference.png

          The Auto Run Python Scripts checkbox in the Preferences.


Rotational Properties are Radians
=================================

Parts of the User Interface may use different units of measurements for angles, rotation.
In the Graph Editor, while working with Drivers, all angles are Radians.


## Usage


*****
Usage
*****

Drivers can be added to properties via their context menu, a shortcut, copy-pasted,
or by typing an expression directly into the property's value.

After adding drivers, they are usually modified in the :doc:`Drivers editor </editors/drivers_editor>`,
or via a simplified *Edit Driver* popover invoked from the property context menu.


.. _bpy.ops.anim.driver_button_add:

Add Driver
==========

.. reference::

   :Menu:      :menuselection:`Context menu --> Add Driver`
   :Shortcut:  :kbd:`Ctrl-D`

The usual way to add a driver to a property is to :kbd:`RMB` click a property,
then choose *Add Driver* in the context menu.
Drivers can also be added by pressing :kbd:`Ctrl-D` with the mouse over the property.

This operation adds a driver with a single variable (which needs to be filled in),
and displays the *Edit Driver* popover.


Edit Driver
===========

.. reference::

   :Menu:      :menuselection:`Context menu --> Edit Driver`

Displays a popover window that allows editing the custom expression and input variables
of the driver without opening the full *Drivers Editor*.

Many drivers don't use their :doc:`F-Curve </editors/graph_editor/fcurves/introduction>`
component, so this reduced interface is sufficient.


Open Drivers Editor
===================

.. reference::

   :Menu:      :menuselection:`Context menu --> Open Drivers Editor`

Opens a new window with the *Drivers Editor* and
selects the driver associated with the property.


Copy & Paste
============

.. reference::

   :Menu:      :menuselection:`Context menu --> Copy Driver`
   :Menu:      :menuselection:`Context menu --> Paste Driver`

Drivers can be copied and pasted via the context menu.
When adding drivers with the same settings, this can save time modifying settings.


.. _drivers-copy-as-new:

Copy As New Driver
==================

.. reference::

   :Menu:      :menuselection:`Context menu --> Copy As New Driver`

A driver that sets the property value to the value of a different property can be
quickly created by using the *Copy As New Driver* context menu option of the input
property, and then pasting the result onto the output property via *Paste Driver*.

It is also possible to add the new driver variable to an existing driver using
the :ref:`Paste Driver Variables <drivers-variables>` button in the editor panel.


Expression
==========

This is a quick way to add drivers with a scripted expression.
First click the property you want to add a driver to, then type a hash ``#`` and a scripted expression.

Some examples:

- ``#frame``
- ``#frame / 20.0``
- ``#sin(frame)``
- ``#cos(frame)``


.. _bpy.ops.anim.driver_button_remove:

Removing Drivers
================

.. reference::

   :Menu:      :menuselection:`Context menu --> Delete Driver(s)`
   :Menu:      :menuselection:`Context menu --> Delete Single Driver`
   :Shortcut:  :kbd:`Ctrl-Alt-D`

Removes driver(s) associated with the property, either for the single selected property
or sub-channel, or all components of a vector.


## Workflow Examples


*******************
Workflow & Examples
*******************

Simple Drivers can be configured from the pop-over that appears when adding a new Driver.
When adding multiple Drivers or for more advanced configurations,
it is useful to have open the :doc:`Drivers Editor </editors/drivers_editor>`.


Transform Driver
================

Control a property with an object's transform.
In this example, the Y rotation of Object 2 will be driven by the X position of Object 1.
Starting from a simple setup with two objects:

#. Add a Driver to the *Rotation Y* property of the second object via the context menu or with :kbd:`Ctrl-D`.

   .. figure:: /images/animation_drivers_workflow-examples_transform-driver-1.png

#. Open the *Drivers Editor* and select the *Y Euler Rotation* property in the channels region.
#. Open the Sidebar region and select the *Drivers* tab.
#. Configure the driver to be the *Averaged Value* of a *Transform Channel* of the first object.

   .. figure:: /images/animation_drivers_workflow-examples_transform-driver-2.png

#. Experiment with moving the first object and notice how it affects the Y rotation of the second object.


Scripted Expression - Orbit a Point
===================================

Orbit an object's position around a point with a custom *Scripted Expression*.
The object's position will change when scrubbing the timeline.
Using trigonometry, circular motion can be defined in 2D using the sine and cosine functions.
(See `Unit Circle <https://en.wikipedia.org/wiki/Unit_circle>`__.)
In this example, the current frame is used as the variable that induces the motion.
``frame`` is a :ref:`Simple Expression <drivers-simple-expressions>` that corresponds to
``bpy.context.scene.frame_current``.

.. figure:: /images/animation_drivers_workflow-examples_object-rotation.png

#. Add a driver to the X Location property.

   #. Set the *Driver Type* to *Scripted Expression*.
   #. Add the expression ``0 + (sin(frame / 8) * 4)``, where:

      - ``frame/8`` : is the current frame of the animation, divided by 8 to slow the orbit down.
      - ``(sin( )*4)`` : multiplies the result of ``sin(frame/8)`` by 4 for a bigger circle.
      - ``0 +`` : is used to control the offset to the orbit center point.

#. Add a driver to the Y Location property with the expression ``0 + (cos(frame / 8) * 4)``.
#. Scrub the timeline to see the effect.
   Experiment with the variables to control the size and center of the orbit.


.. _driver-namespace:

Custom Function - Square Value
==============================

Create a custom function to get the square of a value (i.e. *value*\ :sup:`2`).
Adding the function to the *Driver Namespace* allows it to be used from driver expressions.
The *Driver Namespace* has a list of built-in functions for use in driver expressions,
as well as constants such as π and e.
These can be inspected via the Python Console::

   >>> bpy.app.driver_namespace[' <tab>
                                 acos']
                                 acosh']
                                 asin']
                                 asinh']
                                 atan']
                                 ...

To add a new function to the *Driver Namespace*, the function itself needs to be implemented
and then added to the ``bpy.app.driver_namespace``.

#. Add the following to the Text Editor inside Blender and press *Run Script*. ::

      import bpy

      def square(val):
         """Returns the square of the given value"""
         return val * val

      # Add function to driver_namespace.
      bpy.app.driver_namespace['square'] = square

#. Add a driver with a *Scripted Expression* such as ``square(frame)``.
#. Observe the effect when scrubbing the timeline.

There are more custom function examples available in Blender's Text Editor
:menuselection:`Templates --> Python --> Driver Functions`.
Since :ref:`Simple Expressions <drivers-simple-expressions>` cannot access
custom functions, using them only makes sense for complex computations.

.. warning::
   Trying to replace built-in entries of the driver namespace may result in undefined behavior.

.. _driver-attribute-node-emulation:

View Layer Attribute Lookup
===========================

The material :doc:`Attribute Node </render/shader_nodes/input/attribute>` in the View Layer mode
automatically searches for the attribute property in multiple locations. This, for example, can allow
setting a certain value of the custom attribute at the :doc:`Scene </scene_layout/scene/introduction>`
or :doc:`World </render/lights/world>` level, and then overriding it
differently for one :doc:`View Layer </scene_layout/view_layers/introduction>`.

.. figure:: /images/animation_drivers_workflow-examples_attribute-lookup.png
   :width: 200px
   :align: right

Context Properties of drivers don't implement this behavior, so if necessary it has to be manually
emulated via fallback values and a conditional expression (conditions are
:ref:`Simple Expressions <drivers-simple-expressions>`).

For an attribute named ``attr``, the node tries the following six RNA path lookups in order:

* ``["attr"]`` in the active View Layer (custom property).
* ``attr`` in the active View Layer (built-in property).
* ``["attr"]`` in the active Scene.
* ``attr`` in the active Scene.
* ``world["attr"]`` in the active Scene.
* ``world.attr`` in the active Scene.

Depending on the specific property it may be sufficient to check only a subset of these locations.
For example, the image on the right shows how to access an attribute that is known to definitely be
a custom property with a color value.

Driver variables accessing locations that are not final in the lookup chain should use fallback values that are
invalid for the attribute (e.g. negative color values), which can then be checked by the conditional expression.
The final variable should fallback to a valid default value to be used when the property is not set at all.

.. _shapekey-driver-example:

Shape Key Drivers
=================

Improved Mesh Deformation
-------------------------

Fix intersection problems that happen when using armatures and weight painting, especially at joints.
Shape keys can also be used to tweak and refine a rig, for example to suggest muscle formations.
In this example, a shape key is used to improve the deformation at the elbow of a rudimentary arm.

.. figure:: /images/animation_drivers_workflow-examples_shape-key-improved-deformation.png

   Left: Skeletal mesh deformation without correction.
   Right: Corrective shape key applied

Setup
   #. Add a mesh (in this example, a cylinder with loop cuts).
   #. Add an armature with a chain of bones.
   #. Skin the mesh to the armature using weight painting.

   (Note: to parent the mesh to the armature: select the mesh first,
   then the armature and use :kbd:`Ctrl-P` to parent with auto weights.)

Experiment with posing the armature and observe the deformation at the joint.
To fix intersection problems or angles that look unsatisfactory,
you can associate a :doc:`Shape Key </animation/shape_keys/index>` with a pose.

Shape Key
   #. Pose the armature such that the problems are visible.
      Be sure to cover the extreme poses that you want to support for the rig.
   #. With the mesh selected, add a new *Shape Key* in addition to the *Basis* key.
      :menuselection:`Properties --> Mesh tab --> Shape Keys`
   #. In order to author the shape key on top of the armature deformation,
      enable both *Edit Mode Display* and *Cage Editing* in the Armature modifier.
      :menuselection:`Properties --> Modifiers tab --> Armature Modifier --> Header`
   #. Enter Edit Mode and select the new shape key in the properties panel.
      Adjust the vertices as desired.
      Select the *Basis* key to toggle between the original mesh and your edits.
      (Note: be careful to apply edits only to your shape and not to
      the original mesh or other existing keys.)

Once you are satisfied with how the deformation looks for the problematic pose,
you'll need to configure a driver to activate the shape smoothly when entering that position.

Driver
   #. Add a driver to the *Value* of the shape key you've created.
   #. Open the Drivers Editor and select the driver.

   Method 1 -- Direct mapping to a bone rotation value
      A simple way to configure the driver is with a direct correspondence of
      the value of a bone's rotation channel to the shape key activation *Value*.
      This method has the disadvantage of relying on a single channel of a bone's
      rotation which might be insufficient to precisely express the condition
      under which the shape key should be activated.

      #. In the Drivers tab, select the *Averaged Value* of the rotation of
         the bone you are posing.

         Understand the rotation axis that you are interested in by enabling axes display
         in the armature or by observing the bone's transform values in the Properties.

         Select the rotation channel and set it to local, meaning, the bone's
         rotation value relative to its parent bone.

         .. figure:: /images/animation_drivers_workflow-examples_shape-key-method1.png

      #. Manually set points in the driver curve by selecting a handle and
         dragging it or inserting values in the *F-Curve* tab.
         The Y axis represents the shape key *Value*, which should go from 0.0 to 1.0.
         The X axis is usually the frame, but for this driver it represents the rotation value in radians.
         You can have more than two points in the curve and tweak the transitions
         with the handles in the curve view (:kbd:`G` to move).

      #. To verify that the driver behaves correctly, deselect the option to
         only show drivers for selected objects. This way, you can pose the armature
         and keep an eye on the driver.

   Method 2 -- Rotational difference to a target bone
      This method requires an additional *target* or *corrective* bone, but it
      better expresses the spatial condition in 3D space of the bone that is
      causing the problem.

      #. In armature Edit Mode, add a new bone extruded from Bone 1,
         in the position at which Bone 2 should have the shape key active.
         This type of bones usually follow a naming convention such as
         "TAR-" (target) or "COR-" (corrective).

      #. In the Drivers tab, select the *Averaged Value* of the rotational difference
         between the bone you are rotating and the target bone.
         A rotational difference is the minimum angle between two objects in World Space.
         It is therefore important that the bones have the same root,
         so that the only thing affecting the angle between the bones is the rotation of one of them.
         When the deformation bone (Bone 2) reaches the target rotation (TAR-Bone 2)
         the rotational difference will be 0°.

         .. figure:: /images/animation_drivers_workflow-examples_shape-key-method2.png

      #. Manually adjust the driver curve handles so that the shape key *Value*
         (Y axis) is 1.0 when the rotational difference (X axis) is 0°.
         The *Value* should be 0.0 when the arm is extended, at which point
         the rotational difference should be around 90° or more (in radians).

      #. See the steps in Method 1 on how to adjust the curve handles and
         confirm that the functionality is working. Pose the armature to
         verify that the ranges are correct.


Chained Relative Shape Keys
---------------------------

Activate different shape keys in succession.
In this example, moving a single bone will activate first *Key 1* and then *Key 2*.
See also :ref:`relative shape keys mix additively <animation-shapekeys-relative-vs-absolute>`.

Shape Keys
   Add two shape keys to a mesh, besides the *Basis*.

.. list-table::

   * - .. figure:: /images/animation_drivers_workflow-examples_chained-shape-keys-basis.png
          :width: 200px

          Basis.

     - .. figure:: /images/animation_drivers_workflow-examples_chained-shape-keys-key1.png
          :width: 200px

          Key 1: top faces moved up by 1 m.

     - .. figure:: /images/animation_drivers_workflow-examples_chained-shape-keys-key2.png
          :width: 200px

          Key 2: inner top moved up by 1 m.

Drivers
   Add an armature with a single bone to control the shape keys.
   The goal is to activate the keys in succession as this bone moves up.

   .. figure:: /images/animation_drivers_workflow-examples_chained-shape-keys-result.png

   As shown in the picture above, when the bone is halfway up, both *Key 1* and *Key 2* have an influence.
   It is a matter of preference if *Key 1* should be at its maximum *Value* before *Key 2* starts to become active,
   or how much they should overlap. This example shows a seamless blend.

   For a seamless blend where there is overlap, *Key 1* should have a *Value* of 0.0 when the bone
   is at the bottom and increase linearly to 1.0 until the bone is past the midpoint height.
   *Key 2* should have a value of 0.0 before the midpoint height and then increase at the same
   rate than *Key 1* until reaching *Value* 1.0 when the bone is at maximum height.

   #. Add a driver to the *Value* of *Key 1* and *Key 2*.
      In the *Drivers* tab, configure both drivers to be the *Averaged Value* of
      a variable with the bone's Z location.
   #. Determine the range of the bone's motion in the World Z axis by moving it up so that it is
      aligned with the top of the mesh when both keys are active. Here we will use [0.0, 2.5].
   #. Configure the driver functions so that the *Value* of the shape keys (Y axis) is as
      desired for the bone's height (X axis).

      The driver functions should be linear, therefore, they can be defined analytically
      with a function of type :math:`y = a + bx`,
      where :math:`a` is an offset in :math:`y` and :math:`b` is the slope.

      #. In the *Modifiers* tab, add a *Generator* of type *Extended Polynomial* for both drivers.
      #. Play with the values of :math:`a` and :math:`b` so that the curves go from [0.0, 1.0]
         in the Y axis and from [0.0, 2.5] in the X axis.
         The curves should overlap in the mid area of the X axis and they should have the same slope (:math:`b`).

         Possible values are *Key 1*: :math:`y = 0.0 + 0.6x` and *Key 2*: :math:`y = -0.5 + 0.6x`.

         .. figure:: /images/animation_drivers_workflow-examples_chained-shape-keys-driver-setup.png

         Note that the functions go outside the range [0.0, 1.0] for the shape keys' *Value*,
         but that has no effect because *Value* is clamped in a *Range* in the *Shape Keys* panel.


## Editing


*******
Editing
*******

.. _bpy.ops.anim.keyframe_insert:

Insert Keyframe
===============

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Animation --> Insert Keyframe`
   :Shortcut:  :kbd:`I`

There are several methods of adding new keys. Namely:

- In the 3D Viewport, pressing :kbd:`I` will key properties based on the
  :ref:`Default Key Channels <bpy.types.PreferencesEdit.key_insert_channels>` User Preferences.
- When a :doc:`Keying Set </animation/keyframes/keying_sets>` is active,
  it is used instead of reading the User Preferences.
- Hovering over a property and pressing :kbd:`I` or with the context menu by :kbd:`RMB`
  a property and choose *Insert Keyframe* from the menu.
- With the User Preference "Pie Menu on Drag" enabled, holding down :kbd:`I`
  and moving the cursor will bring up a pie menu to insert one of Location, Rotation, Scale, and Available.


Auto Keyframe
-------------

.. figure:: /images/editors_timeline_keyframes-auto.png

   Timeline Auto Keyframe.

Auto Keyframe is the record button in the *Timeline* header. Auto Keyframe adds
keyframes automatically to the set frame if the value for transform type properties changes.

See :ref:`Timeline Keyframe Control <bpy.types.ToolSettings.use_keyframe_insert_auto>` for more info.


.. _bpy.ops.anim.keyframe_insert_menu:

Insert Keyframe with Keying Set
===============================

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Animation --> Insert Keyframe with Keying Set`
   :Shortcut:  :kbd:`K`

Insert Keyframes for specified :doc:`Keying Set </animation/keyframes/keying_sets>`,
with menu of available Keying Sets.


.. _bpy.ops.anim.keyframe_delete:

Delete Keyframes
================

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Animation --> Delete Keyframes...`
   :Shortcut:  :kbd:`Alt-I`

There are several methods of removing keyframes:

- In the 3D Viewport press :kbd:`Alt-I` to remove keys from selected objects on the current frame.
- When the mouse is over a value, press :kbd:`Alt-I`.
- :kbd:`RMB` a value and choose *Delete Keyframe* from the menu.


.. _bpy.ops.anim.keyframe_clear:

Clear Keyframes
===============

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Animation --> Clear Keyframes...`
   :Shortcut:  :kbd:`Shift-Alt-I`

Removes all keyframes from the selected object.


Editing Keyframes
=================

Keyframes can be edited in two editors. To do so go to either
the :doc:`Graph Editor </editors/graph_editor/index>`
or the :doc:`Dope Sheet </editors/dope_sheet/index>`.


Examples
========

Keyframe Animation
------------------

This example shows you how to animate a cube's location, rotation, and scale.

#. First, in the Timeline, or other animation editors, set the frame to 1.
#. With the cube selected in Object Mode, press :kbd:`I` in the 3D Viewport.
   This will record the location, rotation, and scale, for the cube on frame 1.
#. Set the frame to 100.
#. Use Move :kbd:`G`, Rotate :kbd:`R`, Scale :kbd:`S`, to transform the cube.
#. Press :kbd:`I` in the 3D Viewport.

To test the animation, press :kbd:`Spacebar` to play.

.. TODO2.8
   .. figure:: /images/animation_keyframes_editing_keyframe-animation-examples.png
      :width: 600px

      The animation on frames 1, 50 and 100.


## Index

.. _bpy.types.Keyframe:

#############
  Keyframes
#############

.. toctree::
   :maxdepth: 2

   introduction.rst
   editing.rst
   keying_sets.rst


## Introduction


************
Introduction
************

A *Keyframe* is simply a marker of time which stores the value of a property.

For example, a Keyframe might define that the horizontal position of a cube is at 3 m on frame 1.

The purpose of a Keyframe is to allow for interpolated animation, meaning, for example,
that the user could then add another key on frame 10, specifying the cube's horizontal position at 20 m,
and Blender will automatically determine the correct position of the cube for all the frames between frame 1 and 10
depending on the chosen interpolation method (e.g. Linear, Bézier, Quadratic, etc.).

An overview of existing keyframes can be seen via the :doc:`Dope Sheet </editors/dope_sheet/index>` editor.


Visualization
=============

There are some important visualization features in the 3D Viewport that can help animation.

When the current frame is a keyframe for the current active object, the name of this object
(shown in the upper left corner of the 3D Viewport) turns yellow.

.. figure:: /images/animation_keyframes_introduction_visualization.png
   :align: center

   Top: Current frame is a keyframe for Cube. Bottom: Current frame isn't a keyframe.


Interpolation
=============

Keyframe interpolation is represented and controlled by
:doc:`animation curves </editors/graph_editor/fcurves/introduction>`,
also known as :term:`F-Curves <F-Curve>`. These curves can be viewed and modified
via the :doc:`Graph Editor </editors/graph_editor/index>`.

.. figure:: /images/animation_keyframes_introduction_curves.png
   :align: center

   Constant, Linear, Quadratic and Bézier interpolation, with Linear extrapolation.

The X axis of the curve corresponds to time, while Y represents the value of the property.
Keyframes themselves define points of the curve, while interpolation is controlled by additional parameters.

The :ref:`Interpolation Mode <editors-graph-fcurves-settings-interpolation>` is the main setting
that specifies for each keyframe how the curve is interpolated from that key to
the next one. There are a number of modes with fixed shapes,
e.g. *Constant*, *Linear*, *Quadratic* etc, and a free form *Bézier* mode.

:ref:`Extrapolation <editors-graph-fcurves-settings-extrapolation>` specifies how
the curve extends before the first, and after the last keyframe.
The main available choices are *Constant* and *Linear*;
it is also possible to configure the curve to loop.

*Bézier* interpolation is controlled by handles, which have
a :ref:`handle type <editors-graph-fcurves-settings-handles>` and position.
The position of *Free* and *Aligned* handles must be set manually from the Graph editor,
while *Vector*, *Automatic* and *Auto Clamped* handles are computed automatically from
keyframe values.

Interpolation, Extrapolation and Handle Type can also be changed from
the :doc:`Dope Sheet </editors/dope_sheet/index>` editor.

.. figure:: /images/editors_graph-editor_fcurves_sidebar_curve_auto-smoothing.png
   :align: center

   Handle smoothing modes. Yellow: *None*, Cyan: *Continuous Acceleration*.

The method how the three automatic handle types are computed is controlled by
the per-curve :ref:`Auto Handle Smoothing <bpy.types.FCurve.auto_smoothing>` setting.
The *None* mode resembles how most other software works and only considers the values
of the immediately adjacent keys. The *Continuous Acceleration* mode considers the shape
of the whole curve, which produces smoother results out of the box, but means that changes
in one key affect interpolation over a larger section of the curve; it also tends to
overshoot more with *Automatic* handles.


.. _keyframe-type:

Keyframe Types
==============

For visually distinguishing regular keyframes from different animation events or
states (extremes, breakdowns, or other in-betweens)
there is the possibility of applying different colors on them for visualization.

.. figure:: keyframe_types.webp
   :align: right

   Left: not selected; Right: selected.

Keyframe (white / yellow diamond)
   Normal keyframe.
Breakdown (small cyan diamond)
   Breakdown state. e.g. for transitions between key poses.
Moving Hold (dark gray / orange diamond)
   A keyframe that adds a small amount of motion around a holding pose.
   In the Dope Sheet it will also display a bar between them.
Extreme (big pink diamond)
   An 'extreme' state, or some other purpose as needed.
Jitter (tiny green diamond)
   A filler or baked keyframe for keying on ones, or some other purpose as needed.
Generated (dark diamond)
   A key generated by some tool, for example :ref:`Copy Global Transform: Fix to
   Camera <copy-global-transform-fix-to-camera>`. This keyframe type indicates
   to Blender and add-ons that it is safe to remove and re-generate them, so be
   careful when manually marking your hand-made animation with this type.


.. _keyframe-handle-display:

Handles & Interpolation Mode Display
====================================

Dope Sheet can display the Bézier handle type associated with the keyframe,
and mark segments with non-Bézier interpolation.
This facilitates basic editing of interpolation without the use of the Graph Editor.

The icon shape represents the type of the :ref:`Bézier Handles <editors-graph-fcurves-settings-handles>`
belonging to the keyframe.

.. figure:: /images/animation_keyframes_introduction_interpolation.png
   :align: right

   From top: summary, Bézier, linear.

.. list-table::

   * - Circle
     - Auto Clamped (default)
   * - Circle With Dot
     - Automatic
   * - Square
     - Vector
   * - Clipped Diamond
     - Aligned
   * - Diamond
     - Free

If the handles of a keyframe have different types,
or in case of summary rows representing multiple curves,
out of the available choices the icon that is furthest down the list is used.
This means that if a grouped row uses a circle icon,
it is guaranteed that none of the grouped channels have a non-auto key.

Horizontal green lines mark the use of
non-Bézier :ref:`Interpolation <editors-graph-fcurves-settings-interpolation>`.
The line is dimmed in summary rows if not all grouped channels have the same interpolation.

Display of this information can be disabled via the *Show Handles and Interpolation*
option of the Dope Sheet's :ref:`View Menu <dope-sheet-view-menu>`.


## Keying Sets


***********
Keying Sets
***********

.. figure:: /images/editors_timeline_keying-sets.png
   :align: right

   The Active Keying Sets data ID in the Timeline.

Keying Sets are a collection of animated properties that are used to animate
and keyframe multiple properties at the same time.
For example, pressing :kbd:`K` in the 3D Viewport will bring up the available Keying Sets.
Blender will then add keyframes for whichever Keying Set is chosen.
There are some built-in Keying Sets and also custom Keying Sets called "Absolute Keying Sets".


.. _bpy.types.KeyingSets:

Keying Set Panel
================

.. reference::

   :Editor:    Properties
   :Panel:     :menuselection:`Scene --> Keying Set`

This panel is used to add, select, manage "Absolute Keying Sets".

.. figure:: /images/animation_keyframes_keying-sets_scene-keying-set-panel.png

   The Keying Set panel.

.. _bpy.types.KeyingSets.active_index:

Active Keying Set
   A :ref:`List View <ui-list-view>` of Keying Sets in the active scene.
   Selecting a keying set makes it active

   .. -bpy.ops.anim.keying_set_add:

   Add ``+``
      Adds an empty Keying Set.

   .. _bpy.ops.anim.keying_set_remove:

   Remove ``-``
      Removes the active keying set.

.. _bpy.types.KeyingSet.bl_description:

Description
   A short description of the Keying Set.

.. _bpy.ops.anim.keying_set_export:

Export to File
   Export Keying Set to a Python script ``File.py``.
   To re-add the Keying Set from the ``File.py``, open then run the ``File.py`` from the Text Editor.


.. _bpy.types.KeyingSetPath:

Active Keying Set Panel
-----------------------

.. reference::

   :Editor:    Properties
   :Panel:     :menuselection:`Scene --> Active Keying Set`

This panel is used to add properties to the active Keying Set.

.. figure:: /images/animation_keyframes_keying-sets_scene-active-keying-set-panel.png

   The Active Keying Set panel.

.. _bpy.types.KeyingSetPaths.active_index:

Paths
   A collection of paths in a :ref:`List View <ui-list-view>` each with a *Data Path* to a property
   to add to the active Keying Set.

   .. _bpy.ops.anim.keying_set_path_add:

   Add ``+``
      Adds an empty path.

   .. _bpy.ops.anim.keying_set_path_remove:

   Remove ``-``
      Removes the selected path.

.. _bpy.types.KeyingSetPath.id_type:
.. _bpy.types.KeyingSetPath.id:

Target ID-Block
   Set the ID Type and the *Object IDs* data path for the property.

.. _bpy.types.KeyingSetPath.data_path:

Data Path
   Set the rest of the Data Path for the property.

.. _bpy.types.KeyingSetPath.use_entire_array:

Array All Items
   Use *All Items* from the Data Path or select the array index for a specific property.

.. _bpy.types.KeyingSetPath.group_method:

F-Curve Grouping
   This controls what group to add the channels to.

   Keying Set Name, None, Named Group


Keyframing Settings
-------------------

General Override
   These options control all properties in the Keying Set.
   Note that the same settings in *Preferences* override these settings if enabled.

Active Set Override
   These options control individual properties in the Keying Set.

.. _bpy.types.KeyingSet.use_insertkey_override_needed:
.. _bpy.types.KeyingSet.use_insertkey_override_visual:
.. _bpy.types.KeyingSetPath.use_insertkey_override_needed:
.. _bpy.types.KeyingSetPath.use_insertkey_override_visual:

Common Settings
   Needed
      Only insert keyframes where they are needed in the relevant F-Curves.
   Visual
      Insert keyframes based on the visual transformation.


.. _bpy.ops.anim.keyingset_button_add:

Adding Properties to a Keying Set
=================================

.. reference::

   :Menu:      :menuselection:`Context menu --> Add All/Single to Keying Set`
   :Shortcut:  :kbd:`K`

Some ways to add properties to Keying Sets.

:kbd:`RMB` the property in the *User Interface*, then select *Add Single to Keying Set* or *Add All to Keying Set*.
This will add the properties to the active Keying Set, or to a new Keying Set if none exist.

Hover the mouse over the properties, then press :kbd:`K`, to add *Add All to Keying Set*.


.. _bpy.ops.anim.keying_set_active_set:

Set Active Keying Set
=====================

.. reference::

   :Shortcut:  :kbd:`Shift-K`

There are several ways to designate the active keying set:

- Press :kbd:`Shift-K` in the 3D Viewport.
- Select a keying set in the :ref:`Keying Set <bpy.types.KeyingSets>` panel.
- Select a keying set in the :ref:`Keying popover <timeline-keying>` in the Timeline header,


.. _whole-character-keying-set:

Whole Character Keying Set
==========================

The built-in *Whole Character* Keying Set is made to keyframe all properties
that are likely to get animated in a character rig. It was also implicitly used by
the :ref:`Old Pose Library system <pose-library-old>`.

This keying set ignores bones whose name starts with one of the following prefixes,
as it assumes these are technical bones that are not meant to be animated directly.
The built-in Rigify addon generates such bones, for example.

- COR (Corrective)
- DEF (Deformation)
- GEO (Geometry)
- MCH (Mechanism)
- ORG (Original from meta rig)
- VIS (Visualization)


## Index

.. _animation-shape_keys-index:
.. _bpy.types.ShapeKey:
.. _bpy.types.Key:

##############
  Shape Keys
##############

.. toctree::
   :maxdepth: 2

   introduction.rst
   shape_keys_panel.rst
   workflow.rst


## Introduction


************
Introduction
************

Shape keys are used to deform objects into new shapes for animation.
In other terminology, shape keys may be called "morph targets" or "blend shapes".

The most popular use cases for shape keys are in character facial animation and
in tweaking and refining a skeletal rig.
They are particularly useful for modeling organic soft parts and muscles
where there is a need for more control over the resulting shape
than what can be achieved with combination of rotation and scale.

Shape keys can be applied on object types with vertices like mesh, curve, surface and lattice.

.. figure:: /images/animation_shape-keys_introduction_example.png

   Example of a mesh with different shape keys applied.


Workflow
========

Shape keys are authored in the :doc:`Shape Keys panel </animation/shape_keys/shape_keys_panel>`
which is accessed in the Object Data tab of the Properties (e.g. the Mesh tab for mesh objects).

A shape key is modified by first selecting a shape key in the panel,
and then moving the object's vertices to a new position in the 3D Viewport.

The panel has controls for affecting the current *Value* (influence, weight) of a shape.
It is possible to see a shape in isolation or how it combines with others.


Adding and Removing Vertices
----------------------------

It is not possible to add or remove vertices in a shape key.
The number of vertices and how they connect is specified by the mesh, curve, surface or lattice.
A shape key merely records a position for each vertex and therefore shapes always
contain all the object's vertices.

When adding a vertex, all shape keys will record it with the position in which it is created.
Workflow-wise, adding and deleting vertices after creating shape keys is possible, but it is best
to leave the creation of shape keys for when the mesh is finished or its topology is stable.


Adding Shape Keys
-----------------

When adding a new shape key with the ``+`` button next to the list,
the new shape will be a copy of the Basis shape,
independently of the current result visible in the 3D Viewport.

When adding a new shape key from :menuselection:`Specials --> New Shape from Mix`,
the shape will start of with the vertex configuration that is visible at that moment.

When doing facial animation with relative shape keys, it can be useful to first
create a shape key with a complex extreme pose (e.g. anger or surprise), and
then break this complex shape into components by applying a temporary vertex group to
the complex shape and creating a copy with *New Shape from Mix*.
This technique helps reducing conflicts between different shape keys
that would otherwise produce a double effect.


.. _animation-shapekeys-relative-vs-absolute:

Relative or Absolute Shape Keys
===============================

A mesh (curve, surface or lattice) has a stack of shape keys.
The stack may be of *Relative* or *Absolute* type.

Relative
   Mainly used for muscles, limb joints, and facial animation.

   Each shape is defined relative to the Basis or to another specified shape key.

   The resulting effect visible in the 3D Viewport, also called *Mix*,
   is the cumulative effect of each shape with its current value.
   Starting with the Basis shape, the result is obtained by **adding**
   each shape's weighted **relative** offset to its reference key.

   Value
      Represents the weight of the blend between a shape key and its reference key.

      A value of 0.0 denotes 100% influence of the reference key and 1.0 of the shape key.
      Blender can extrapolate the blend between the two shapes above 1.0 and below 0.0.

   Basis
      Basis is the name given to the first (top-most) key in the stack.

      The Basis shape represents the state of the object's vertices in their original position.
      It has no weight value and it is not keyable.
      This is the default *Reference Key* when creating other shapes.

Absolute
   Mainly used to deform the objects into different shapes over time.

   Each shape defines how the object's shape will be at *Evaluation Time* specified in its *Value*.

   The resulting shape, or *Mix*, is the interpolation of the previous and next shape
   given the current *Evaluation Time*.

   Value
      Represents the *Evaluation Time* at which that shape key will be active.

   Basis
      Basis is the name given to the first (topmost) key in the stack.

      The Basis shape represents the state of the object's vertices in their original position.


## Shape Keys Panel


****************
Shape Keys Panel
****************

.. reference::

   :Editor:    Properties
   :Mode:      All modes
   :Panel:     :menuselection:`Object Data --> Shape Keys`

.. figure:: /images/animation_shape-keys_shape-keys-panel_basis.png
   :align: right
   :width: 296px

   Shape Keys panel.


The Shape Keys panel is used for authoring shape keys.

.. container:: lead

   .. clear

.. _bpy.types.Object.active_shape_key_index:

Active Shape Key Index
   A :ref:`List View <ui-list-view>`.

   .. _bpy.types.ShapeKey.frame:

   Value/Frame (number)
      In Relative mode: Value is the current influence of the shape key used for blending between
      the shape (value=1.0) and its reference key (value=0.0). The reference key is usually the Basis shape.
      The weight of the blend can be extrapolated above 1.0 and below 0.0.

      In Absolute mode: Value is the *Evaluation Time* at which the shape will have maximum influence.

   .. _bpy.types.ShapeKey.mute:

   Mute (check mark)
      If unchecked, the shape key will not be taken into consideration when
      mixing the shape key stack into the result visible in the 3D Viewport.

   .. _bpy.types.ShapeKey.lock_shape:

   Lock Shape (lock icon)
      Shape keys can be locked to protect them from accidental modification due to inadvertently
      selecting the wrong key for editing in the list. Most common sculpt and edit mode operators
      and tools that move vertices abort with an error if the active shape key is locked.

      .. note::

         Operators that always modify all shape keys in exactly the same way, like
         :ref:`Apply Object Transforms <bpy.ops.object.transform_apply>`, don't check shape key locks.
         Neither currently do most edit mode operators that modify topology, because the topology is
         expected to usually be finalized before shape keys are created.

Shape Key Specials
   .. _bpy.ops.object.shape_key_add:

   New Shape from Mix
      Add a new shape key with the current deformed shape of the object.
      This differs from the ``+`` button of the list, as that one always copies
      the Basis shape independently of the current mix.

   .. _bpy.ops.object.shape_key_mirror:

   Mirror Shape Key
      If your mesh is symmetrical, in *Object Mode*, you can mirror the shape keys on the X axis.
      This will not work unless the mesh vertices are perfectly symmetrical.
      Use the :menuselection:`Mesh --> Symmetrize` tool in *Edit Mode*.

   Mirror Shape Key (Topology)
      Same as *Mirror Shape Key* though it detects the mirrored vertices based on the topology of the mesh.
      The mesh vertices do not have to be perfectly symmetrical for this action to work.

   .. _bpy.ops.object.join_shapes:

   Join as Shapes (Transfer Mix)
      Transfer the current resulting shape from a different object.

      Select the object to copy, then the object to copy into.
      Use this action and a new shape key will be added to the active object
      with the current mix of the first object.

   .. _bpy.ops.object.shape_key_transfer:

   Transfer Shape Key
      Transfer the active shape key from a different object
      regardless of its current influence.

      Select the object to copy, then the object to copy into.
      Use this action and a new shape key will be added to the active object
      with the active shape of the first object.

   .. _bpy.ops.object.shape_key_remove:

   Delete All Shape Keys
      Removes all Shape Keys and any effect that they had on the mesh.

   Apply All Shape Keys
      Saves the current visible shape to the mesh data and deletes all Shape Keys.

.. _bpy.types.Key.use_relative:

Relative
   Set the shape keys to *Relative* or *Absolute*.
   See :ref:`animation-shapekeys-relative-vs-absolute`.

.. _bpy.types.Object.show_only_shape_key:

Shape Key Lock (pin icon)
   Show the active shape in the 3D Viewport without blending.
   *Shape Key Lock* gets automatically enabled while the object is in *Edit Mode*.

.. _bpy.types.Object.use_shape_key_edit_mode:

Shape Key Edit Mode (edit mode icon)
   If enabled, when entering *Edit Mode* the active shape key will **not** take maximum influence as is default.
   Instead, the current blend of shape keys will be visible and can be edited from that state.

.. _bpy.types.Object.add_rest_position_attribute:

Add Rest Position
   Creates an :doc:`Attribute </modeling/geometry_nodes/attributes_reference>` in the vertex domain called
   ``rest_position`` which is a copy of the ``position`` attribute before shape keys and modifiers are evaluated.
   Only mesh objects support this option.


Relative Shape Keys
===================

.. figure:: /images/animation_shape-keys_shape-keys-panel_relative.png
   :align: right
   :width: 296px

   Relative Shape Keys options.

See :ref:`animation-shapekeys-relative-vs-absolute`.

With relative shape keys, the value shown for each shape in the list represents
the current weight or influence of that shape in the current *Mix*.

.. container:: lead

   .. clear

.. _bpy.ops.object.shape_key_clear:

Clear Shape Keys ``X``
   Set all influence values, or weights, to zero.
   Useful to quickly guarantee that the result shown in the 3D Viewport is not affected by shapes.

.. _bpy.types.ShapeKey.value:

Value
   The weight of the blend between the shape key and its reference key (usually the Basis shape).

   A value of 0.0 denotes 100% influence of the reference key and 1.0 of the shape key.

.. _bpy.types.ShapeKey.slider_min:
.. _bpy.types.ShapeKey.slider_max:

Range
   Minimum and maximum range for the influence value of the active shape key.
   Blender can extrapolate results when the *Value* goes lower than 0.0 or above 1.0.

.. _bpy.types.ShapeKey.vertex_group:

Vertex Group
   Limit the active shape key deformation to a vertex group.
   Useful to break down a complex shape into components by assigning temporary vertex groups
   to the complex shape and copying the result into new simpler shapes.

.. _bpy.types.ShapeKey.relative_key:

Relative To
   Select the shape key to deform from. This is called the *Reference Key* for that shape.

.. note::

   Rather than storing offsets directly, internally relative keys are stored as snapshots of the mesh shape.
   The relative deformation offsets are computed by subtracting *Reference Key* from that snapshot.

   Therefore, replacing the *Reference Key* has the effect of subtracting the difference between the new
   and old reference from the relative deformation of the current key.

Absolute Shape Keys
===================

.. figure:: /images/animation_shape-keys_shape-keys-panel_absolute.png
   :align: right
   :width: 296px

   Absolute Shape Keys options.

See :ref:`animation-shapekeys-relative-vs-absolute`.

With absolute shape keys, the value shown for each shape in the list represents
the *Evaluation Time* at which that shape key will be active.

.. container:: lead

   .. clear

.. _bpy.ops.object.shape_key_retime:

Re-Time Shape Keys (clock icon)
   Absolute shape keys are timed, by order in the list, at a constant interval.
   This button resets the timing for the keys. Useful if keys were removed or re-ordered.

.. _bpy.types.ShapeKey.interpolation:

Interpolation
   Controls the interpolation between shape keys.

   Linear, Cardinal, Catmull-Rom, B-Spline

   .. _fig-interpolation-type:

   .. figure:: /images/animation_shape-keys_shape-keys-panel_interpolation-types.png

      Different types of interpolation.

      The red line represents interpolated values between keys (black dots).

.. _bpy.types.Key.eval_time:

Evaluation Time
   Controls the shape key influence. Scrub to see the effect of the current configuration.
   Typically, this property is keyed for animation or rigged with a driver.


## Workflow


********
Workflow
********

Relative Shape Keys
===================

#. In *Object Mode*, add a new shape key via the *Shape Key* panel with the ``+`` button.
#. "Basis" is the rest shape. "Key 1", "Key 2", etc. will be the new shapes.
#. Switch to *Edit Mode*, select "Key 1" in the *Shape Key* panel.
#. Deform mesh as you want (do not remove or add vertices).
#. Select "Key 2", the mesh will be changed to the rest shape.
#. Transform "Key 2" and keep going for other shape keys.
#. Switch back to *Object Mode*.
#. Set the *Value* for "Key 1", "Key 2", etc. to see the transformation between the shape keys.

In the figure below, from left to right shows: "Basis", "Key 1", "Key 2"
and mix ("Key 1" ``1.0`` and "Key 2" ``0.8``) shape keys in Object Mode.

.. figure:: /images/animation_shape-keys_workflow_relative.png

   Relative shape keys example.

For more practical examples, see
:ref:`how to combine shape keys and drivers <shapekey-driver-example>`.


Absolute Shape Keys
===================

#. Add sequence of shape keys as described above for relative shape keys.
#. Uncheck the *Relative* checkbox.
#. Click the *Reset Timing* button.
#. Switch to *Object Mode*.
#. Drag *Evaluation Time* to see how the shapes succeed one to the next.

.. figure:: /images/animation_shape-keys_workflow_absolute.png

   Absolute shape keys workflow.

By adding a :doc:`driver </animation/drivers/index>` or
setting :doc:`keyframes </animation/keyframes/introduction>`
to *Evaluation Time* you can create an animation.

.. seealso:: Shape Key Operators

   There are two modeling tools used to control shape keys and
   are found in :ref:`Edit Mode <modeling-meshes-editing-vertices-shape-keys>`.


