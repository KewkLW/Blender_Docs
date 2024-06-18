# Index for video_editing

- [Index](#Index)
- [Introduction](#Introduction)
- [Index](#Index)
- [Introduction](#Introduction)
- [Editing](#Editing)
- [Index](#Index)
- [Introduction](#Introduction)
- [Meta](#Meta)
- [Selecting](#Selecting)
- [Adjustment](#Adjustment)
- [Clip](#Clip)
- [Color](#Color)
- [Image](#Image)
- [Index](#Index)
- [Introduction](#Introduction)
- [Mask](#Mask)
- [Movie](#Movie)
- [Scene](#Scene)
- [Sound](#Sound)
- [Text](#Text)
- [Add](#Add)
- [Alpha Over Under Overdrop](#Alpha-Over-Under-Overdrop)
- [Blur](#Blur)
- [Color Mix](#Color-Mix)
- [Glow](#Glow)
- [Index](#Index)
- [Multicam](#Multicam)
- [Multiply](#Multiply)
- [Speed Control](#Speed-Control)
- [Subtract](#Subtract)
- [Transform](#Transform)
- [Cross](#Cross)
- [Gamma Cross](#Gamma-Cross)
- [Index](#Index)
- [Sound Crossfade](#Sound-Crossfade)
- [Wipe](#Wipe)
- [Directory Structure](#Directory-Structure)
- [Index](#Index)
- [Introduction](#Introduction)


## Index

.. _bpy.types.Sequence:
.. _bpy.ops.sequencer:

#################
  Video Editing
#################

.. toctree::
   :maxdepth: 2

   introduction.rst
   setup/index.rst
   edit/index.rst


## Introduction


************
Introduction
************

In addition to modeling and animation, Blender can be used to edit videos.
There are two possible methods for this, one being the :doc:`Compositor </compositing/introduction>`
and the other, described in this chapter, being the Video Sequencer.
The Video Sequencer within Blender is a complete video editing system that allows you to combine multiple
video channels and add effects to them. You can use these effects to create powerful video edits,
especially when you combine it with the animation power of Blender!

To use the Video Sequencer, you load multiple video clips and lay them end-to-end (or in some cases, overlay them),
inserting fades and transitions to link the end of one clip to the beginning of another.
Finally, you can add audio and synchronize the timing of the video sequence to match it.

.. figure:: /images/video-editing_introduction_screen-layout.png

   Default Video Editing screen layout.


## Index


*****************
Edit Your Project
*****************

.. toctree::
   :maxdepth: 2

   introduction.rst
   montage/index.rst


## Introduction


************
Introduction
************

There is no single optimal workflow for editing your video projects that fits every case.
Although there certainly are some specific use cases; e.g. tutorial editing,
wedding videos, ..., some agreement exists about distinguishing four basic activities.

#. Montage: starting with your raw footage, you'll have to deliver a coherent and fluent succession
   of strips that tell your story. Clips have to be rearranged, combined, split (cut) and trimmed.
#. Effects: these can be simple transition effects between strips, e.g.
   fade or full-fledged animations, e.g. rolling end credits.
#. Color grading: because your assembled timeline consists of different shots taken
   with different cameras under different lighting conditions, colors can vary widely between them.
   With color grading and color correcting you can harmonize the color perception.
#. Sound: this ranges from adding background music and voice-over to creating special
   sound effects and using third-party software such as Audacity.


## Editing


*******
Editing
*******

Transform
=========

Options
-------

.. _bpy.types.SequencerToolSettings.overlap_mode:

Overlap Mode
^^^^^^^^^^^^

Overlap Mode defines the result of transforming a strip so that it overlaps another strip.

Shuffle
   The overlapping strip will be moved to the nearest free space so that it does not overlap.
Overwrite
   The overlapped strip will be overwritten, trimmed or split by the overlapping strip.
Expand
   All strips on the right side of (each) transformed will be shifted forward to accommodate
   the overlapping strip.


.. _bpy.types.ToolSettings.use_snap_sequencer:

Snapping
^^^^^^^^

The icon toggles snapping; you can also do this temporarily by holding :kbd:`Ctrl` after
starting to drag a strip.

The drop-down arrow offers the following options:

.. _bpy.types.SequencerToolSettings.snap_to_current_frame:
.. _bpy.types.SequencerToolSettings.snap_to_hold_offset:

Snap to
   Current Frame
      Snaps the transformed selection to the Playhead.
   Hold Offset
      Snaps the transformed selection to the :ref:`Hold Offset <sequencer-duration-hard>`.

.. _bpy.types.SequencerToolSettings.snap_ignore_muted:
.. _bpy.types.SequencerToolSettings.snap_ignore_sound:

Ignore
   Muted Strips
      Muted Strips are not considered as snap targets.
   Sound Strips
      Sound Strips are not considered as snap targets.

.. _bpy.types.SequencerToolSettings.use_snap_current_frame_to_strips:

Current Frame
   Snap to Strips
      Snaps the Playhead to all strips.

.. _bpy.ops.transform.seq_slide:

Move
----

.. reference::

   :Menu:      :menuselection:`Strip --> Transform --> Move`
   :Shortcut:  :kbd:`G`

Pressing :kbd:`G` moves all the selected strip(s).
Move your mouse horizontally (left/right) to change the strip's position in time.
Move vertically (up/down) to change channels.

Holding down :kbd:`Ctrl` while dragging enables or disables snapping.

You can also lock the direction to time with :kbd:`X` or to change the strip's channel with :kbd:`Y`.

It is possible to move strips using mouse by dragging them while holding :kbd:`LMB`.
Currently it is possible to move only one strip by dragging.


Start Frame Offset
^^^^^^^^^^^^^^^^^^

The *Start Frame Offset* for that strip can be selected by clicking :kbd:`LMB` on the left handle of the strip;
holding it down (or pressing :kbd:`G` and then moving the mouse left/right)
changes the start frame within the strip by the number of frames you move it.
The frame number label under the strip displays the start frame of the strip.

- If you have a 20-image sequence strip, and drag the left handle to the right by 10 frames,
  the strip will start at image 11 (images 1 to 10 will be skipped).
  Use this to clip off a roll-up or undesired lead-in.
- Dragging the left handle left will create a lead-in (copies) of the first frame for as many frames as you drag it.
  Use this when you want some frames for a transition at the start of the clip.


End Frame
^^^^^^^^^

The *End Frame* of the strip could be selected by clicking :kbd:`LMB` on the right handle of the strip;
holding it down (or pressing :kbd:`G`) and then moving the mouse changes the ending frame within the strip.
The frame number label over the strip displays the end frame of the strip.

- Dragging the right handle to the left shortens the clip;
  any original images at the tail are ignored. Use this to quickly clip off a roll-down.
- Dragging the right handle to the right extends the clip.
  For movies and images sequences, more of the animation is used until exhausted.
  Extending a clip beyond its length will render as a copy of the last image.
  Use this for transitions out of this clip.

.. note:: Multiple selection

   You can select several (handles of) strips by :kbd:`Shift-LMB` clicking: when you press :kbd:`G`,
   everything that is selected will move with your mouse -- this means that,
   for example, you can at the same time move a strip, shorten two others, and extend a forth one.


Move/Extend from Current Frame
------------------------------

.. reference::

   :Menu:      :menuselection:`Strip --> Transform --> Move/Extend from Current Frame`
   :Shortcut:  :kbd:`E`

With a number of strips selected, pressing :kbd:`E` lets you interactively extend the strips.
This is similar to moving but is useful for extending (or shortening) time around the current frame.

All selected strip handles to the "mouse side" of the current frame indicator will transform together,
so you can change the duration of strips at the current frame.

.. hint::

   Extend is a convenient way to adjust the time of rough edits such as an "animatic" (sequential storyboards).
   Where it's possible to select everything and adjust the length of strips around the current frame.
   This can be especially useful when adding in audio or other elements that could cause
   the timing to need adjustment.

   When performing this operation you may want to enable :menuselection:`Markers --> Sync Markers`
   so markers are updated too.

   This simply a convenience operation, instead of manually selecting strips
   on one side of the current frame, as well as handles on one side of overlapping strips.
   Then selecting and transforming markers as well.
   This avoids the manual process, so re-timing can be accessed quickly.


.. _bpy.ops.sequencer.slip:

Slip Strip Contents
-------------------

.. reference::

   :Menu:      :menuselection:`Strip --> Transform --> Slip Strip Contents`
   :Shortcut:  :kbd:`S`

The Slip tool allows you to change the position of the contents of a strip without moving the strip itself.


.. _bpy.ops.sequencer.snap:

Snap Strips to the Current Frame
--------------------------------

.. reference::

   :Menu:      :menuselection:`Strip --> Transform --> Snap Strips to the Current Frame`
   :Shortcut:  :kbd:`Shift-S`

Moves the strip or control point to the current frame.


.. _bpy.ops.sequencer.offset_clear:

Clear Strips Offset
-------------------

.. reference::

   :Menu:      :menuselection:`Strip --> Transform --> Clear Strips Offset`
   :Shortcut:  :kbd:`Alt-O`

To reset the (soft) start/end frame handles.


.. _bpy.ops.sequencer.swap:

Swap Strips
-----------

.. reference::

   :Menu:      :menuselection:`Strip --> Transform --> Swap Strips`

Left :kbd:`Alt-Left`
   Swaps the active strip with the strip to the left.
Right :kbd:`Alt-Right`
   Swaps the active strip with the strip to the right.


.. _bpy.ops.sequencer.gap_remove:

Remove Gaps
-----------

.. reference::

   :Menu:      :menuselection:`Strip --> Transform --> Insert Gaps`
   :Shortcut:  :kbd:`Backspace`

Remove blank frames between the current frame and the first strip to the left,
independent of selection or locked state of strips.

All Gaps
   Remove gaps to the right of the strip along with the left.


.. _bpy.ops.sequencer.gap_insert:

Insert Gaps
-----------

.. reference::

   :Menu:      :menuselection:`Strip --> Transform --> Insert Gaps`
   :Shortcut:  :kbd:`Equals`

Insert blank frames between the current frame and the first strips to the right,
independent of selection or locked state of strips.

Image Transform
===============

.. _bpy.ops.sequencer.strip_transform_fit:

Scale to Fit
------------

.. reference::

   :Menu:      :menuselection:`Strip --> Image Transform --> Scale to Fit`

Adjusts the strips :ref:`Scale Transforms <bpy.types.SequenceTransform.scale>`
so the visual contents of the strip to fit exactly within the project's
:ref:`Resolution <bpy.types.RenderSettings.resolution_x>`
while maintaining the original aspect ratio.

This may mean that the transparent areas may be added
along the content's border to fit the content in the rendered area.


Scale to Fill
-------------

.. reference::

   :Menu:      :menuselection:`Strip --> Image Transform --> Scale to Fill`

Adjusts the strips :ref:`Scale Transforms <bpy.types.SequenceTransform.scale>`
so the visual contents of the strip to span the project's
:ref:`Resolution <bpy.types.RenderSettings.resolution_x>`
while maintaining the original aspect ratio.

This may mean that portions of the original image no longer fit the content inside the rendered area.


Stretch to Fill
---------------

.. reference::

   :Menu:      :menuselection:`Strip --> Image Transform --> Stretch to Fill`

Adjusts the strips :ref:`Scale Transforms <bpy.types.SequenceTransform.scale>`
so the visual contents of the strip to fill the project's
:ref:`Resolution <bpy.types.RenderSettings.resolution_x>`.
Note, unlike the other two methods described above, *Stretch to Fill* does not maintaining the original aspect ratio.

This may mean that the original image becomes distorted to fit the content inside the rendered area.


.. _bpy.ops.sequencer.strip_transform_clear:

Clear Position
--------------

.. reference::

   :Menu:      :menuselection:`Strip --> Image Transform --> Clear Position`

Resets the strips :ref:`Position Transforms <bpy.types.SequenceTransform.rotation>` to a value of zero.


Clear Scale
-----------

.. reference::

   :Menu:      :menuselection:`Strip --> Image Transform --> Clear Scale`

Resets the strips :ref:`Scale Transforms <bpy.types.SequenceTransform.scale>` to a value of one.


Clear Rotation
--------------

.. reference::

   :Menu:      :menuselection:`Strip --> Image Transform --> Clear Rotation`

Resets the strips :ref:`Rotation Transform <bpy.types.SequenceTransform.rotation>` to a value of zero.


Clear All
---------

.. reference::

   :Menu:      :menuselection:`Strip --> Image Transform --> Clear All`

Resets the strips position, scale, and rotation :ref:`Transforms <bpy.types.SequenceTransform>` to
their default values.


.. _bpy.ops.sequencer.split:

Split
=====

.. reference::

   :Menu:      :menuselection:`Strip --> Split`
   :Shortcut:  :kbd:`K`

This splits the selected strip in two at the current frame.
This will result in two strips which use the same source, fitting the original strip's timing and length.

.. hint::

   This can be thought of as a quick way to duplicate the current strip,
   adjusting the start/end frames to form two non-overlapping strips showing the same content as before.


.. _bpy.ops.sequencer.hold_split:

Hold Split
==========

.. reference::

   :Menu:      :menuselection:`Strip --> Hold Split`
   :Shortcut:  :kbd:`Shift-K`

Like *Split*, it splits a strip in two distinct strips;
however you will not be able to drag the endpoints to show the frames past the split of each resulting strip.

Although you can adjust the :ref:`Hold Offset <sequencer-duration-hard>`
number fields in the *Strip Info* panel.

.. hint::

   This can be thought of as a way to simulate splitting the video file in two parts at the cut-point,
   replacing the current strip with each.


.. _bpy.ops.sequencer.duplicate_move:

Duplicate Strips
================

.. reference::

   :Menu:      :menuselection:`Strip --> Duplicate Strips`
   :Shortcut:  :kbd:`Shift-D`

Duplicate a strip to make an unlinked copy;
drag it to a time and channel, and drop it by :kbd:`LMB` click.


.. _bpy.ops.sequencer.delete:

Delete
======

.. reference::

   :Menu:      :menuselection:`Strip --> Delete`
   :Shortcut:  :kbd:`Delete`, :kbd:`X`

Delete the selected strip(s).


.. _bpy.ops.sequencer.scene_frame_range_update:

Update Scene Frame Range
========================

.. reference::

   :Menu:      :menuselection:`Strip --> Update Scene Frame Range`

For Scene strips only -- Updates the strip's :ref:`sequencer-strips-properties-time`
properties to match the referenced scene's frame range.
This operator should be used when the referenced scene's length is extended or shortened.


.. _bpy.ops.sequencer.images_separate:

Separate Images
===============

.. reference::

   :Menu:      :menuselection:`Strip --> Separate Images`
   :Shortcut:  :kbd:`Y`

For images sequence only -- Converts the strip into multiple strips, one strip for each frame.
Useful for slide shows and other cases where you want to bring in a set on non-continuous images.

Length
   You have to specify the duration you want the resulting strips will be.


Movie Strip
===========

.. _bpy.ops.sequencer.rendersize:

Set Render Size
---------------

.. reference::

   :Menu:      :menuselection:`Strip --> Set Render Size`

Sets the render resolution and aspect to match the strip's resolution.


.. _bpy.ops.sequencer.deinterlace_selected_movies:

Deinterlace Movies
------------------

.. reference::

   :Menu:      :menuselection:`Strip --> Deinterlace Movies`

Converts interlaced video into progressive video.


.. _sequencer-edit-change:

Effect Strip
============

.. _bpy.ops.sequencer.change_effect_input:

Change Effect Input
-------------------

.. reference::

   :Menu:      :menuselection:`Strip --> Effect Strip --> Change Effect Type`

Swaps which strips are the input for the effect strip.


.. _bpy.ops.sequencer.change_effect_type:

Change Effect Type
------------------

.. reference::

   :Menu:      :menuselection:`Strip --> Effect Strip --> Change Effect Type`

Switch the effects on a selected Effect strip.


.. _bpy.ops.sequencer.reassign_inputs:

Reassign Inputs
---------------

.. reference::

   :Menu:      :menuselection:`Strip --> Effect Strip --> Reassign Inputs`
   :Shortcut:  :kbd:`R`

This tool can be used to assign (reconnect) effect strips in a different way.
Select three arbitrary strips and press :kbd:`R`.
If you don't create a cycle, those will be connected to a new effect chain.


.. _bpy.ops.sequencer.swap_inputs:

Swap Inputs
-----------

.. reference::

   :Menu:      :menuselection:`Strip --> Effect Strip --> Swap Inputs`
   :Shortcut:  :kbd:`Alt-S`

Swaps the first two inputs for the effect strip.


.. _bpy.ops.sequencer.lock:
.. _bpy.ops.sequencer.unlock:

Lock/Unlock
===========

Lock Strips :kbd:`Shift-L`
   Disables the strip from being transformed.
Unlock Strips :kbd:`Shift-Alt-L`
   Enables disabled strips allowing them to be transformed.


.. _bpy.ops.sequencer.mute:
.. _bpy.ops.sequencer.unmute:

Mute/Unmute
===========

Mute/Unmute Strips :kbd:`H`, :kbd:`Alt-H`
   Mute or unmute the selected strips.
Mute/Unmute Deselected Strips :kbd:`Shift-H`, :kbd:`Ctrl-Alt-H`
   Mute or unmute all strips but the selected.


Inputs
======

.. _bpy.ops.sequencer.reload:

Reload Strips :kbd:`Alt-R`
   Reloads the strips from their external saved location.
Reload Strips and Adjust Length :kbd:`Shift-Alt-R`
   Reloads the strips from their external saved location and re-adjusts the strip duration.

.. _bpy.ops.sequencer.change_path:

Change Path/Files
   Changes the source file contained in a selected strip.

.. _bpy.ops.sequencer.swap_data:

Swap Data
   Swaps two sequence strips.


Context Menu
============

You can activate context menu by clicking :kbd:`RMB` in the Sequencer's timeline.
In this menu you can quickly access some commonly used tools.


Fades
=====

.. reference::

   :Menu:      :menuselection:`Add --> Fades`

This submenu contains tools to add or remove fades to strips.
In case of visual strips the tools will animate the opacity or volume in case of audio strips.

Clear Fades
   Removes fade animation from selected sequences.
Fade In and Out
   Fade selected strips in and out.
Fade In
   Fade in selected strips.
Fade Out
   Fade out selected strips.
From Current Frame
   Fade from the current frame to the end of overlapping sequences.
To Current Frame
   Fade from the start of sequences under the Playhead to the current frame.


.. _sequencer-editing-retiming:

Retiming
========

.. figure:: /images/video-editing-retiming.png

Strips can be sped up or, slowed down by adding and moving retiming keys. Retiming controls can be activated for
individual strips, after which keys can be selected and moved.

.. note::

   - Only strip content is retimed, existing animation is not handled by the tool.
   - Effect strips can not be retimed.

.. hint::

   To quickly change selected strip speed, press :kbd:`R` and enter desired speed.


.. rubric:: Selecting Retiming Keys

Retiming keys are always shown on strip as inactive by default.
In order to select retiming keys, :ref:`Show Retiming Keys <bpy.types.Sequence.show_retiming_keys>` must be enabled.
This property can also be enabled using :ref:`bpy.ops.sequencer.retiming_show`.

Multiple keys can be selected at once with box selection. Box select will select keys, only if a key is already
selected. Otherwise it will select strips only.

Use :kbd:`Ctrl-LMB` to select all keys to the right of the selected key.


.. rubric:: Moving Retiming Keys

Retiming key can be moved by dragging it with mouse, or by pressing :kbd:`G`. The key is mapped to particular frame
of strip content, so moving it effectively means moving a frame to a new position and therefore stretching, or
contracting time flow.

When a key is moved, this does not affect position of other keys inside of the strip. If strip has more keys inside,
multiple keys have to be selected, if only 1 segment has to be retimed. However if there are retiming keys outside
of strip boundary, these will be moved along with first or last key in strip in order to preserve
existing retiming, that is not visible.


.. _bpy.ops.sequencer.retiming_key_add:

Add Retiming Keys
-----------------

.. reference::

   :Editor:    Video Sequencer
   :Menu:      :menuselection:`Strip --> Retiming --> Add Retiming Key`

Retiming key can be added to selected strips from retiming menu
or by pressing :kbd:`I` and choosing Add Retiming Key option. This adds a key to current frame.
This operation will also create keys at strip start and end point, since these keys must be always present.

When keys are selected, strips are deselected, but it is still possible to add new keys.
In this case keys will be added to strips where any key is selected.


.. _bpy.ops.sequencer.retiming_add_freeze_frame_slide:

Add Freeze Frame and Slide
--------------------------

.. reference::

   :Editor:    Video Sequencer
   :Menu:      :menuselection:`Strip --> Retiming --> Add Freeze Frame and Slide`

Freeze frame is used to stop strip playback at particular frame for any duration.
Freeze frame can be added from strip retiming menu or context menu.

.. note::

   It is not possible to make smooth transition into or from freeze frame.


.. _bpy.ops.sequencer.retiming_add_transition_slide:

Add Speed Transition and Slide
------------------------------

.. reference::

   :Editor:    Video Sequencer
   :Menu:      :menuselection:`Strip --> Retiming --> Add Speed Transition and Slide`

It is possible to create smooth transition from one speed to another speed.
This can be done by selecting retiming key between 2 segments of different speeds,
and choosing Add Speed Transition either from strip retiming menu or context menu.
This will create 2 keys, that are linked and always move in opposite direction.
If both keys are moved at once, this changes where transition starts and ends.


Delete Retiming Keys
--------------------

.. reference::

   :Editor:    Video Sequencer
   :Menu:      :menuselection:`Strip --> Retiming --> Delete Retiming Keys`

Retiming key can be deleted by selecting and pressing :kbd:`Delete` or :kbd:`X`.
When handle is deleted, strip size will not change,
therefore speed will change to average between 2 retimed segments.

.. note::

   When transition key is removed, it will re-create simple retiming key from which transition was created.


.. _bpy.ops.sequencer.retiming_reset:

Reset Retiming
--------------

.. reference::

   :Editor:    Video Sequencer
   :Menu:      :menuselection:`Strip --> Retiming --> Reset Retiming`

Reverts all timing to the original strip.


.. _bpy.ops.sequencer.retiming_segment_speed_set:

Set Speed
---------

.. reference::

   :Editor:    Video Sequencer
   :Menu:      :menuselection:`Strip --> Retiming --> Set Speed`

Sets the speed of a retimed segment.

Speed
   The rate compared to the original time.
Preserve Current retiming
   Keeps the speed of the other retiming segments unchanged by adjusting the
   :ref:`Duration <bpy.types.Sequence.frame_final_duration>` of the strip instead.


.. _bpy.ops.sequencer.retiming_show:

Toggle Retiming Keys
--------------------

.. reference::

   :Editor:    Video Sequencer
   :Menu:      :menuselection:`Strip --> Retiming --> Toggle Retiming Keys`
   :Shortcut:  :kbd:`Ctrl-R`

Enable's the :ref:`Show Retiming Keys <bpy.types.Sequence.show_retiming_keys>` strip property.
This allows retiming keys to be shown for the first time and enables interacting with them.


## Index


*******
Montage
*******

.. toctree::
   :maxdepth: 2

   introduction.rst
   strips/index.rst
   selecting.rst
   editing.rst
   meta.rst


## Introduction


************
Introduction
************

Montage is the technique of assembling separate clips (video, audio, text, effects) into a coherent sequence.
The importance of montage was first demonstrated by the Russian filmmaker Lev Kuleshov in the 1910s and 1920s.
Famous is the Kuleshov effect: viewers derive more meaning from the
interaction of two sequential shots than from a single shot in isolation
(see the `Wikipedia article <https://en.wikipedia.org/wiki/Kuleshov_effect>`__ for a nice illustration).

Obviously, the first thing in assembling your timeline is importing or adding strips.
There are several ways to do this and each has its own advantages and disadvantages.

Before you can do anything with a strip, you have to select them. There are multiple ways of selecting strips.

Strips can be moved in time (left to right on the X axis) or in the display stack (bottom to top on the Y axis).

Splitting or cutting a strip will create two parts of the strip (before and after the split).
There are two variants: Split and Hold Split.

Trimming is the process of removing or adding a portion of the video at its head or tail.
This will result in a decrease or increase of the duration of the video.

Grouping is the creating of a meta strip whereby several strips are grouped together.

.. Hint::

   Creating a good montage is a time consuming process.
   Therefore, all basic operations (add, split, trim, ...) have an associated shortcut.
   It pays off to learn these shortcuts, even though the same result could be obtained with the menu and/or mouse.

   .. The choice of specific keys (e.g. :kbd:`X` for Delete) is of course inspired
   .. by the meaning of the operation but also by the fact that the shortcut
   .. must be easy to carry out with the left hand on a standard (Qwerty) keyboard.
   .. So, the preferred shortcut for Delete is not the :kbd:`Delete`
   .. key (which is on most keyboards on the right hand side) but the :kbd:`X` key.


## Meta

.. _bpy.types.MetaSequence:

***********
Meta Strips
***********

A Meta Strip is a strip which contain multiple strips treated as if it was one strip.
It allows you to reduce the vertical space used in the Sequencer.
You can edit it the same way as any other strips.

It is organization tool. For example, if you are using a lot of strips with
complicated arrangement, you can group them together using Meta strips.

Make Meta Strip :kbd:`Ctrl-G`
   To create a Meta strip, select all the strips you want to group, and :kbd:`Ctrl-G` to group them.
   The Meta strips will span from the beginning of the first strip to the end of the last one,
   and condenses all channels into a single strip.
UnMeta Strip :kbd:`Ctrl-Alt-G`
   Separating (ungrouping) the Meta strip restores the strips to their relative positions and channels.
   This can be used if you choose to delete a Meta strip and want to keep the strips inside.

.. figure:: /images/video-editing_sequencer_meta_example.png
   :align: center

   Example of Meta strips.

You can edit the content inside a Meta strip by pressing :kbd:`Tab`.
It will expand the strip to the whole view and hide any other strips.
To exit the Meta strip press :kbd:`Tab` again.
Meta strips can also be nested, which make editing them a little confusing.
To exit out one level of Meta Strip make sure you do not have a Meta strips selected when you press :kbd:`Tab`.

.. note::

   The default blend mode for a Meta strip is Replace. There are many cases where this alters
   the results of the animation so be sure to check the results and adjust the blend mode if necessary.

One convenient use for Meta strips is when you want to apply the same effect to multiple strips.
For example: if you have a video that was recorded in different files and want to add an effect strip.
It is much more convenient to apply a single set of effects
to one Meta strip than applying it to each individual strip.

.. seealso::

   It is also possible to do the similar task described above with
   an :doc:`Adjustment Layer </video_editing/edit/montage/strips/adjustment>` effect strip.


## Selecting


*********
Selecting
*********

The active sequence strip is displayed with a light outline.
The *entire* strip could be selected by clicking :kbd:`LMB` in the middle of the strip.


Select Menu
===========

The Select menu lets you select strips in different ways.

.. _bpy.ops.sequencer.select_all:

All :kbd:`A`
   Selects all the strips in the timeline.

None :kbd:`Alt-A`
   Deselects all the strips in the timeline.

Invert :kbd:`Ctrl-I`
   Inverts the current selection.

.. _bpy.ops.sequencer.select_box:

Box Select :kbd:`B`
   See :ref:`Box Select <bpy.ops.*.select_box>`.

Box Select (Include Handles) :kbd:`Ctrl-B`
   Works like *Box Select*, but also selects any strip handles inside the box. If a strip has only
   one handle selected, dragging it will change the strip's length. (If both handles are selected,
   the complete strip moves instead.)

.. _bpy.ops.sequencer.select_side_of_frame:

Side of Frame
   Left/Right :kbd:`[`/:kbd:`]`
      Select the strips that lie completely to the left or right of the current frame.
   Current
      Select the strips that intersect the current frame.

.. _bpy.ops.sequencer.select_handles:

Handle
   Both, Left, Right
      Select the left, right, or both handles of the selected strips.
   Both/Left/Right Neighbor
      Select the handle of the neighboring strip to the left, right, or on both sides of the selected strips.

.. _bpy.ops.sequencer.select_side:

Channel
   Select all the strips that are in the same channels as the currently selected strips.

.. _bpy.ops.sequencer.select_more:
.. _bpy.ops.sequencer.select_less:
.. _bpy.ops.sequencer.select_linked:

Linked
   All :kbd:`Ctrl-L` / Less :kbd:`Ctrl-NumpadMinus` / More :kbd:`Ctrl-NumpadPlus`
      Add/remove neighboring strips to/from the selection.

.. _bpy.ops.sequencer.select_grouped:

Grouped :kbd:`Shift-G`
   Select strips that are similar to the active strip. By default, unsimilar strips are
   deselected, but this can be changed in the :ref:`Adjust Last Operation <bpy.ops.screen.redo_last>`
   region.

   Type
      Select strips that have the same specific type as the active strip. For example,
      if the active strip is a Movie strip, this selects all Movie strips.
   Global Type
      Select strips that have the same general type (graphics or audio) as the active strip.
   Effect Type
      If the active strip is an effect strip, selects all effect strips. Otherwise,
      selects all non-effect strips. (Despite the name, this operator does not check
      the effect type.)
   Data
      Select strips that use the same source (file, scene, movie clip or mask) as the active strip.
   Effect
      Find the effect types that are applied to the active strip, and select all strips that have
      any of the same effect types applied to them. For example, if the active strip has a
      Gaussian Blur effect on it, this will select all other strips that are also blurred.
   Effect/Linked
      Select strips that are on a lower channel than a selected strip and overlap it in time;
      then, effect strips linked to the selected content strips; and finally, content strips
      linked to the selected effect strips.
   Overlap
      Select strips that partially or completely overlap the active strip in time.


## Adjustment

.. _bpy.types.AdjustmentSequence:

**********************
Adjustment Layer Strip
**********************

The Adjustment Layer strip works like a regular input file strip except for the fact,
that it considers all strips below it as its input.

Real-world use cases, you want to add some last finishing color correction on top of parts of
your final sequence, timeline without messing with meta strips around.
Just add an adjustment layer on top and activate the color balance.

Or you can stack a primary color correction and several secondary color corrections on top of
each other (probably using the new mask input for area selection).


Options
=======

This strip has no options.


## Clip

.. _bpy.types.MovieClipSequence:

**********
Clip Strip
**********

Clip can be modified within the :doc:`Movie Clip Editor </movie_clip/masking/index>`.


Options
=======

This strip has no options.


## Color

.. _bpy.types.ColorSequence:

***********
Color Strip
***********

This effect generates solid color frames.
By default, when it is created, the Color strip is 25 frames long, but
you can extend it by selecting and moving one of the ends.
Use this strip crossed with your main movie to provide a fade-in or fade-out.


Options
=======

Color
   Click on the color field in the Effect panel in the Sidebar region, to pick a different color.


## Image

.. _bpy.types.ImageSequence:

********************
Image/Sequence Strip
********************

.. tip::

   Image strips can display thumbnails in the Sequencer overlaid on their strips
   by enabling the :ref:`Thumbnails <bpy.types.SequencerTimelineOverlay.show_thumbnails>` overlay.


Single Image
============

When you add a single still image (``*.jpg``, ``*.png``, etc.),
Blender creates a 25 frames long strip which will show this image along the strips range.


Image Sequence
==============

In the case of (numbered) image sequences
(e.g. ``*-0001.jpg``, ``*-0002.jpg``, ``*-0003.jpg``, etc, of any image format), you have a choice:

Range
   Navigate into the directory and :kbd:`LMB` click and drag over a range of names to highlight multiple files.
   You can page down and continue :kbd:`Shift-LMB` click-dragging to add more to the selection.
Batch
   :kbd:`Shift-LMB` click selected non-related stills for batch processing; each image will be one frame,
   in sort order, and can be a mix of file types (``jpg``, ``png``, ``exr``, etc.).
All
   Press :kbd:`A` to select/deselect all files in the directory.

.. tip:: Dealing with Different Sizes

   Dealing with different sized images and different sized outputs is tricky.
   If you have a mismatch between the size of the input image and the render output size,
   the Video Sequencer will try to auto-scale the image to fit it entirely in the output.
   This may result in clipping. If you do not want that, use *Crop* and/or *Offset* in the Input
   panel to move and select a region of the image within the output. When you use *Crop* or *Offset*,
   the auto-scaling will be disabled and you can manually re-scale by adding the Transform effect.


.. _bpy.ops.sequencer.image_strip_add:

Add Image Strip
===============

.. reference::

   :Menu:      :menuselection:`Add --> Image/Sequence`

Relative Path
   Store the location of the image file relative to the blend-file.

Start Frame
   The :ref:`Start Frame <bpy.types.Sequence.frame_start>` to place the left handle of the strip.

End Frame
   The end frame to place the right handle of the strip.

   .. tip::

      Subtract the *Start Frame* from the *End Frame* to get the strip's duration.

Channel
   The :doc:`Channel </editors/video_sequencer/sequencer/channels>` to place the strip.

Replace Selection
   Replaces the currently selected strips with the new strip.

Fit Method
   Determines how images with an aspect ratio different than the scene's
   :ref:`Resolution <bpy.types.RenderSettings.resolution_x>` are scaled to fit inside the render area.

   :Scale to Fit:
      Adjusts the strips :ref:`Scale Transforms <bpy.types.SequenceTransform.scale>` so the visual contents of
      the strip to fit exactly within the project's :ref:`Resolution <bpy.types.RenderSettings.resolution_x>`
      while maintaining the original aspect ratio.

      This may mean that the transparent areas may be added
      along the content's border to fit the content in the rendered area.
   :Scale to Fill:
      Adjusts the strips :ref:`Scale Transforms <bpy.types.SequenceTransform.scale>`
      so the visual contents of the strip to span the project's
      :ref:`Resolution <bpy.types.RenderSettings.resolution_x>` while maintaining the original aspect ratio.

      This may mean that portions of the original image no longer fit the content inside the rendered area.
   :Stretch to Fill:
      Adjusts the strips :ref:`Scale Transforms <bpy.types.SequenceTransform.scale>` so the visual contents of
      the strip to fill the project's :ref:`Resolution <bpy.types.RenderSettings.resolution_x>`. Note, unlike
      the other two methods described above, *Stretch to Fill* does not maintaining the original aspect ratio.

      This may mean that the original image becomes distorted to fit the content inside the rendered area.

Set View Transform
   Automatically sets an appropriate :ref:`View Transform <bpy.types.ColorManagedViewSettings.view_transform>`
   based on the :term:`Color Space` of the imported media. In most cases, the *Standard* should be used;
   using the wrong transform could result in inaccurate colors or degraded rendering performance.

Use Placeholders
   Image sequences can use placeholder files.
   This works by enabling *Use Placeholders* checkbox when adding an image strip.
   The option detects the frame range of opened images using Blender's frame naming scheme
   (``filename + frame number + .extension``) and makes an image sequence
   with all files in between even if they are missing.
   This allows you to render an image sequence with a few frames missing and
   still the image strip will have the correct range to account for the missing frames displayed as black.

   When the missing frames are rendered or placed in the same folder,
   you can :ref:`refresh <bpy.ops.sequencer.refresh_all>`
   the Sequencer and get the missing frames in the strip.
   The option is also available when using the *Change Data/File* operator and
   allows you to add more images to the range.


## Index


##########
  Strips
##########

.. toctree::
   :maxdepth: 2

   introduction.rst


Types
=====

.. toctree::
   :maxdepth: 2
   :titlesonly:

   scene.rst
   clip.rst
   mask.rst
   movie.rst
   sound.rst
   image.rst
   color.rst
   text.rst
   adjustment.rst
   effects/index.rst
   transitions/index.rst


## Introduction


************
Introduction
************

A strip is a container which carries frames provided by one or more sources (input).
It is defined by a *Start Frame* and a *Length*, and is displayed as a colored horizontal rectangle.

.. figure:: /images/video-editing_sequencer_strips_introduction_strip-graphic.svg

   Strip schematic.


Adding Strips
=============

.. reference::

   :Menu:      :menuselection:`Add`
   :Shortcut:  :kbd:`Shift-A`

.. figure:: /images/video-editing_sequencer_strips_introduction_add-menu.png
   :align: right

   The Add Menu.

The Add menu is the main menu you will be using to add content to the Video Sequencer.
In general, you load up your strips, create strips of special transition effects,
and then animate out your sequence by selecting "Do Sequence" and clicking the *Animation* button.
You can use the Add menu in the header,
or hover your mouse cursor over the Sequence workspace and press :kbd:`Shift-A`.

Blender does not care which of these you use; you can freely mix and match any of them.
When you choose to add one of these, it lets you either choose a data-block or
the editor area will switch to a File Browser for you to select what you want to add.
Supported files are filtered by default.

The start frame of the newly created strips will be placed at the position of the frame indicator.
When loading multiple files (movie and sound) at the same time each will be added one after the other.


Adding Effects & Transitions
----------------------------

Blender offers a set of effects that can be added to your sequence.

To add an effect strip, select one base strip (image, movie, or scene) by :kbd:`LMB` clicking on it.
For some effects, like the Cross transition effect,
you will need to :kbd:`Shift-LMB` a second overlapping strip (it depends on the effect you want).
From Add menu pick the effect you want.
When you do, the Effect strip will be shown above the source strips. If it is an independent effect,
like the :doc:`Color Generator </video_editing/edit/montage/strips/color>`,
it will be placed at the position of the frame indicator.

.. note::

   Since most Effects strips depend on one or two source strips,
   their frame location and duration depends on their source strips. Thus,
   you may not be able to move it; you have to move the source strips in order to affect the effect strip.

With some effects, like the
:doc:`Alpha Over </video_editing/edit/montage/strips/effects/alpha_over_under_overdrop>`,
the order in which you select the strips is important.
You can also use one effect strip as the input or source strip with another strip,
thus layering effects on top of one another.

If you picked the wrong effect from the menu,
you can always exchange it using :ref:`sequencer-edit-change`.


.. _sequencer-strip-colors:

Visualization
=============

They all become a color-coded strip in the Video Sequencer:

- Scene strip: Light green.
- Clip strip: Dark blue.
- Mask strip: Red.
- Movie strip: Aquamarine.
- Image strip: Purple.
- Sound strip: Turquoise.

Each of the effect strips has its own color.

Besides each of these default colors you can also assign individual strips an alternative color in
the :ref:`Strip Properties <bpy.ops.sequencer.strip_color_tag_set>`.

.. note::

   These colors are dependent on the user interface :doc:`Theme </editors/preferences/themes>`.
   The colors described above are in reference to Blender's default theme.


## Mask

.. _bpy.types.MaskSequence:

**********
Mask Strip
**********

The Mask strip generates a mask image from the selected mask data-block generated
in the :doc:`Movie Clip Editor </movie_clip/masking/index>`.
This works similar to the :doc:`Mask Node </compositing/types/input/mask>`
but without the options available for finer control.
The mask image is always generated at the render resolution,
scaling along with different proxy levels.


Options
=======

Mask
   :ref:`Data-block menu <ui-data-block>` to select a mask.


## Movie

.. _bpy.types.MovieSequence:

***********
Movie Strip
***********

To add a movie (with or without audio) select a movie file(s) in the File Browser
e.g. in the Audio-Video Interleaved format (``*.avi`` file).

.. note:: Clips can be Huge

   A three minute QuickTime ``.mov`` file can be 140MB.
   Loading it, even over a high-speed LAN can take some time.
   Do not assume your computer or Blender has locked up if nothing happens for awhile.

.. tip::

   Movie strips can display thumbnails in the Sequencer overlaid on their strips
   by enabling the :ref:`Thumbnails <bpy.types.SequencerTimelineOverlay.show_thumbnails>` overlay.


.. _bpy.ops.sequencer.movie_strip_add:

Add Movie Strip
===============

.. reference::

   :Menu:      :menuselection:`Add --> Movie`

Relative Path
   Store the location of the image file relative to the blend-file.

Start Frame
   The :ref:`Start Frame <bpy.types.Sequence.frame_start>` to place the left handle of the strip.

Channel
   The :doc:`Channel </editors/video_sequencer/sequencer/channels>` to place the strip.

Replace Selection
   Replaces the currently selected strips with the new strip.

Fit Method
   Determines how images with an aspect ratio different than the scene's
   :ref:`Resolution <bpy.types.RenderSettings.resolution_x>` are scaled to fit inside the render area.

   :Scale to Fit:
      Adjusts the strips :ref:`Scale Transforms <bpy.types.SequenceTransform.scale>` so the visual contents of
      the strip to fit exactly within the project's :ref:`Resolution <bpy.types.RenderSettings.resolution_x>`
      while maintaining the original aspect ratio.

      This may mean that the transparent areas may be added
      along the content's border to fit the content in the rendered area.
   :Scale to Fill:
      Adjusts the strips :ref:`Scale Transforms <bpy.types.SequenceTransform.scale>`
      so the visual contents of the strip to span the project's
      :ref:`Resolution <bpy.types.RenderSettings.resolution_x>` while maintaining the original aspect ratio.

      This may mean that portions of the original image no longer fit the content inside the rendered area.
   :Stretch to Fill:
      Adjusts the strips :ref:`Scale Transforms <bpy.types.SequenceTransform.scale>` so the visual contents of
      the strip to fill the project's :ref:`Resolution <bpy.types.RenderSettings.resolution_x>`. Note, unlike
      the other two methods described above, *Stretch to Fill* does not maintaining the original aspect ratio.

      This may mean that the original image becomes distorted to fit the content inside the rendered area.

Set View Transform
   Automatically sets an appropriate :ref:`View Transform <bpy.types.ColorManagedViewSettings.view_transform>`
   based on the :term:`Color Space` of the imported media. In most cases, the *Standard* should be used;
   using the wrong transform could result in inaccurate colors or degraded rendering performance.

Adjust Playback Rate
   Automatically adjusts the video's speed to playback at the original speed regardless of the scene's framerate.

Sound
   Add a :doc:`Sound Strip </video_editing/edit/montage/strips/sound>` that contains the movie's audio track.

Use Movie Frame Rate
   Sets the :ref:`Scene Frame Rate <bpy.types.RenderSettings.fps>` to the frame rate encoded in the movie file.


Example
=======

.. figure:: /images/video-editing_sequencer_strips_movie-image_example.png

   Imported Movie strip with audio track underneath.

In the strip itself, you can see strip name, path to source file, and strip length.


## Scene

.. _bpy.types.SceneSequence:

***********
Scene Strip
***********

Scene strips are a way to insert the render output of another scene into your sequence.
Instead of rendering out a video, then inserting the video file, you can insert the scene directly.

The strip length will be determined based on the animation settings in that scene.

.. note::

   Scene strips cannot be used to reference the sequence's own scene; a secondary scene must be used instead.


Adding Scene Strips
===================

Existing scenes strips can be added from the :menuselection:`Add --> Scene --> "Scene Name"`.
New scenes can also be created directly from the add menu with :menuselection:`Add --> Scene --> New Scene`.

.. rubric:: Options

Start Frame
   The first frame to start the scene strip.
Channel
   The channel to place the strip in.
Replace Selection
   Replace the active strip with the new scene strip.

When creating a new scene you have the following options:

Type
   How the new scene is created.

   :New: Add new Strip with a new empty Scene with default settings.
   :Copy Settings: Add a new Strip, with an empty scene, and copy settings from the current scene.
   :Linked Copy: Add a Strip and link in the collections from the current scene (shallow copy).
   :Full Copy: Add a Strip and make a full copy of the current scene.


Options
=======

Scene
   A :ref:`ui-data-block` to select or create the scene to render from.

Input
   Input type to use for the Scene strip.

   :Camera:
      Use the Scene's 3D camera as input.
   :Sequencer:
      Use the scene's Sequencer timeline as input, allowing one scene to reuse
      another scene's edit (instead of taking the render output from the scene).

      This is similar to how :doc:`Meta Strips </video_editing/edit/montage/meta>` work,
      with the added advantage of supporting multiple instances of the same data.

Camera
   This can be used to override the scene's camera with any other object.

   It is useful to support switching views within a single scene.

Show
   Annotations
      Shows :doc:`Annotations </interface/annotate_tool>` while in non-render
      :ref:`Preview Shading Modes <bpy.types.RenderSettings.sequencer_gl_preview>`
      i.e. *Solid* or *Wireframe* mode.
   Transparent
      Creates a transparent background.
      This is useful for doing overlays like rendering out Grease Pencil films via the Sequencer.


Sound
-----

.. _bpy.types.SceneSequence.volume:

Strip Volume
   Volume of the audio taken from the chosen scene.


Limitations
===========

Scene strips do not render individual :doc:`Render Passes </render/layers/passes>`;
only the *Combined* render pass will be used.


## Sound

.. _bpy.types.SoundSequence:

***********
Sound Strip
***********

As well as images and movies the Video Sequencer can also edit audio tracks.
You can add Waveform Audio format ``WAV``, ``mp3`` and other audio formats files from your drive,
or from sound encoded within a movie, and mix them using an F-Curve as a volume control.

.. figure:: /images/video-editing_sequencer_strips_sound_editing.png

   Example of sound editing.


Working with Audio Tracks
=========================

A Sound strip is just like any other strip in the Video Sequencer. You can select and move it,
adjust its starting offset using :kbd:`LMB` over the strip handles,
and :kbd:`K` cut it into pieces.
A useful example is cutting out the "um's" and dead voice time.

You can have as many Sound strips as you wish and the result will be the mixing of all of them.
You can give each strip its own name and volume via the Sidebar region.

Overlapping strips are automatically mixed down during the rendering process.
For example, you can have the announcer on channel 5, background music on channel 6,
and Foley sound effects on channel 7.

.. seealso::

   In the :ref:`timeline-playback` menu of the Timeline you will find some options
   concerning audio playback behavior.


Waveform
========

The waveform of the audio is shown depending on two options:

Overlay
   The Sequencer Overlay menu has options to show all strip wave-forms, none of them, or to use the per-strip option
   described below.

Strip
   Each strip has an option *Display Waveform*.
   It is only visible when the above overlay option is set to *Use Strip Option*.

Clipping audio, i.e. values over 100% amplitude, will be shown in red in the waveform.

More strip options are documented in :ref:`Sound Sidebar Panel <vse_sidebar_strip_sound>`.


Animating Audio Track Properties
================================

To animate Sound strips simply hit :kbd:`I` over any of its values.
Examples of animating an audio strip are to fade in/out background music or to adjust volume levels.
Layered/crossed Sound strips are added together;
the lower channel does not override and cut out higher channels (unlike image and video strips).
This makes Blender an audio mixer.
By adding audio tracks and using the curves to adjust each tracks sound level,
you have an automated dynamic multi-track audio mixer!

.. seealso::

   Sounds can be cross-faded by adding a :ref:`Sound Crossfade <bpy.ops.sequencer.crossfade_sounds>` effect.


Output
======

There are two ways to render out your audio.
You can either have it encoded with a video file or in its own audio file.
Read more on how to select a proper :ref:`audio format <render-output-video-encoding-audio>`
and how to start :doc:`rendering </render/output/index>`.


.. _bpy.ops.sequencer.sound_strip_add:

Add Sound Strip
===============

.. reference::

   :Menu:      :menuselection:`Add --> Sound`

Relative Path
   Store the location of the image file relative to the blend-file.

Start Frame
   The :ref:`Start Frame <bpy.types.Sequence.frame_start>` to place the left handle of the strip.

Channel
   The :doc:`Channel </editors/video_sequencer/sequencer/channels>` to place the strip.

Replace Selection
   Replaces the currently selected strips with the new strip.

Cache
   Cache the sound in memory, enables :ref:`Caching <bpy.types.Sound.use_memory_cache>` in the Source properties.

Mono
   Merge all sound channels into one channel,
   enables :ref:`Mono <bpy.types.Sound.use_mono>` in the Sound properties.


## Text

.. _bpy.types.TextSequence:

**********
Text Strip
**********

The Text strip allows you to directly display text in the Sequence editor.
The strip will display the text inserted in its text field on the final sequence.

.. tip::

   All Text strips in a video sequence can be :ref:`exported <bpy.ops.sequencer.export_subtitles>`
   as a `SubRip <https://en.wikipedia.org/wiki/SubRip>`__ file.
   This is useful when using Text strips as subtitles.


Options
=======

Text
   The actual text displayed.

Wrap Width
   Wraps the text by the percentage of the frame width,
   setting this to zero disables word wrapping.


Style
-----

Font
   :ref:`ui-data-block` to choose which font-file is used to render the text.

   Bold
      Use a bold font face with a strong/thick visual appearance.
   Italics
      Use an italicized font face with a slanted visual appearance.
Size
   Size of the text.
Color
   The text color.
Shadow
   Creates a shadow of the specified color under the text.
Shadow Angle
   Defines the position of the shadow as an angle, 0° being to the right and 90° being below.
Shadow Offset
   Amount to shift the shadow compared to the normal text.
Shadow Blur
   Amount to blur the shadow.
Outline
   Creates a line with the defined color enclosing the shape of the text.
Outline Width
   The thickness of the outline.
Box
   Creates a background for the text to improve the readability and clarity of text in some situations.
   The color and opacity of the box can be adjusted using the color selector.
Box Margin
   The distance the box boundaries extends from the boundaries of the font glyphs.
   The distance is measured as a factor of the image's width.


Layout
------

Location X, Y
   Positions the text on the X, Y axis.
Anchor X, Y
   Horizontal (X) or vertical (Y) anchor point of the text relative to the location.


Example
=======

.. figure:: /images/video-editing_sequencer_strips_text_example.png

   Text effect.


## Add

.. _bpy.types.AddSequence:

*********
Add Strip
*********

The Add effect strip adds the colors of two strips together.
Use this effect with a base image strip, and a modifier strip.
The modifier strip is either a solid color or a black-and-white mask,
or another image entirely.

You can use this effect to increase the brightness of an image, or if you use a BW mask,
selectively increase the brightness of certain areas of the image. The Mix node, in Add mode,
does exactly the same thing as the Add SFX strip here,
and is controlled the same way by feeding the Factor input.

.. Red and Cyan (Green and Blue) make White. Red and Blue make Magenta. Red and Green make Yellow.

The :ref:`example <fig-sequencer-strips-effects-add>` shows what happens when you add gray to an image.
The image gets bright because we are adding gray
RGB(0.5, 0.5, 0.5) to say, a blue color RGB(0.1, 0.1, 0.5) resulting in RGB(0.6, 0.6, 1.0)
which retains the original hue (relationship between the colors) but is much brighter
(has a higher value). When applied to the whole image like this, it seems to flash.


Options
=======

This strip has no options.


Example
=======

.. _fig-sequencer-strips-effects-add:

.. figure:: /images/video-editing_sequencer_strips_effects_add_example.png

   Add Effect.


## Alpha Over Under Overdrop


************************************
Alpha Over, Under & Over Drop Strips
************************************

Using the alpha (transparency channel),
this effect composites a result based on transparent areas of the dominant image.
If you use a Scene strip, the areas of the image where there is not anything solid are transparent;
they have an alpha value of 0. If you use a Movie strip, that movie has an alpha value of 1 (completely opaque).

So, you can use the *Alpha Over* / *Alpha Under* effect to composite the CGI Scene on top of your movie.
The result is your model doing whatever as if it was part of the movie.
The :menuselection:`Adjust --> Compositing --> Opacity` controls how much
the foreground is mixed over the background, fading in the foreground on top of the background.
The colors of transparent foreground image areas are ignored and do not change the color of the background.


.. _bpy.types.AlphaOverSequence:

Alpha Over
==========

With *Alpha Over*, the strips are layered up in the order selected; the first strip selected is the background,
and the second one goes *over* the first one selected.
The *Opacity* controls the transparency of the *foreground*, i.e. *Opacity* of 0.0;
will only show the background, and an *Opacity* of 1.0 will completely override the background with the foreground
(except in the transparent areas of this one, of course!)

.. warning::

   By clicking the *Premultiply Alpha* button in the Sidebar of the foreground strip,
   the alpha values of the two strips are not multiplied or added together.
   Use this effect when adding a foreground strip that has a variable alpha channel
   (some opaque areas, some transparent, some in between) over a strip that has a flat opaque
   (alpha=1.0 or greater) channel. If you notice a glow around your foreground objects,
   or strange transparent areas of your foreground object when using *Alpha Over*,
   enable *Premultiply*.


Example
=======

.. figure:: /images/video-editing_sequencer_strips_effects_alpha-over-under-overdrop_example.png

   Alpha Over Effect.


.. _bpy.types.AlphaUnderSequence:

Alpha Under
===========

With *Alpha Under*, this is the contrary:
The first strip selected is the foreground, and the second one, the background.
Moreover, the *Opacity* controls the transparency of the *background*, i.e. an *Opacity* of 0.0;
will only show the foreground (the background is completely transparent),
and an *Opacity* of 1.0 will give the same results as with *Alpha Over*.


.. _bpy.types.OverDropSequence:

Over Drop
=========

*Over Drop* is between the two others: as with *Alpha Under*,
the first selected strip will be the foreground, but as with *Alpha Over*,
the *Opacity* controls the transparency of this foreground.

The *Over Drop* effect is much like the Cross,
but puts preference to the top or second image,
giving more of a gradual overlay effect than a blend like the Cross does. Of course,
all of the Alpha effects respect the alpha (transparency) channel, whereas Cross does not.

The degree of Alpha applied, and thus color mixing, can be controlled by an F-Curve.
Creating a Sine wave could have the effect of the foreground fading in and out.


## Blur

.. _bpy.types.GaussianBlurSequence:

*******************
Gaussian Blur Strip
*******************

The Gaussian Blur strip is used to blur the input strip in a defined direction.
This can be used to blur a background or to blur a transition strip.


Options
=======

Size X
   Distance of the blur effect on the X axis.
Size Y
   Distance of the blur effect on the Y axis.


Example
=======

.. figure:: /images/video-editing_sequencer_strips_effects_blur_example.png

   Gaussian Blur Effect.


## Color Mix

.. _bpy.types.ColorMixSequence:

***************
Color Mix Strip
***************

The *Color Mix* effect strip mixes two strips by working on
the individual and corresponding pixels of the two input strips.

This effect can do the exact same operation as the Add, Subtract,
or Multiply effect strips but also other color blending modes.


Options
=======

Blend
   The Blend modes can be selected in the select menu.
   See :term:`Color Blend Modes` for details on each blending mode.

   Add, Subtract, Multiply, Screen, Divide, Difference,
   Darken, Lighten, Overlay, Color Dodge, Color Burn,
   Hue, Saturation, Value, Color, Soft Light, Linear Light

Opacity
   The amount of the blend of the second image gets composed onto the first.


## Glow

.. _bpy.types.GlowSequence:

**********
Glow Strip
**********

This effect makes parts of an image glow brighter by working on
the luminance channel of an image.
The *Glow* is the superposition of the base image and a modified version,
where bright areas are blurred.

To "animate" the glow effect,
mix it with the base image using the Gamma Cross effect,
crossing from the base image to the glowing one.


Options
=======

Threshold
   Areas brighter than the *Threshold* are blurred.
Clamp
   The maximum luminosity that is added.
Boost Factor
   Multiplier of the brightness.
Blur Distance
   The size of the blur.
Quality
   Improves the quality of the glow by giving smoother results but will be slower.
Only Boost
   This checkbox allows you to only show/use
   the "modified" version of the image, without the base one.


Example
=======

.. figure:: /images/video-editing_sequencer_strips_effects_glow_example.png

   Glow effect.


## Index

.. _sequencer-effects-index:

#################
  Effect Strips
#################

.. toctree::
   :maxdepth: 1

   add.rst
   subtract.rst
   multiply.rst
   alpha_over_under_overdrop.rst
   color_mix.rst
   multicam.rst
   transform.rst
   speed_control.rst
   glow.rst
   blur.rst


## Multicam

.. _bpy.types.MulticamSequence:

***********************
Multicam Selector Strip
***********************

The Multicam Selector strip is used for multi-camera editing.
Multi-camera editing is when a scene is recorded using multiple cameras from different angles
and then edited together afterwards.


Workflow
========

The process of multi camera editing can be rather easy in the Video Sequencer if properly setup.
The following guide shows the basic steps to setup a basic multi camera editing workflow.

#. First you are going to want to add in each of your video strips.
#. Next, you will want to sync all your cameras by either using
   :doc:`Audio Waveforms </video_editing/edit/montage/strips/sound>` or by the movement of objects.

   .. tip::

      To make syncing strips easier you can group cameras, their audio,
      and their effects together using :doc:`Meta Strips </video_editing/edit/montage/meta>`.

#. Split the editor into many :doc:`Previews </editors/video_sequencer/preview/index>`, one for each input track.
   Then change the :ref:`Display Channel <bpy.types.SpaceSequenceEditor.display_channel>`
   of each of the previews to the channel number of the input track.
#. Add a Multicam Selector strip *above* all the video channel tracks.

   After completing these steps you should get something similar to the following image:

   .. figure:: /images/video-editing_sequencer_strips_effects_multicam_example.png

      Multi-camera editing setup.

#. Now select the Multicam strip, if you take a look at the strip options (in the Sidebar),
   you will notice, that Multicam is a rather simple effect strip:
   It just takes a selected channel as its input. That is all.
   The magic comes with the convenient keyboard layout.
#. When you select the Multicam strip, the keys :kbd:`1` to :kbd:`9` are mapped to the cut buttons.
   So, select the Multicam strip and start playback and press the keys
   for the correct input while watching the individual cameras.
#. You will end up with a small Multicam Selector strip for every cut.

In reality, it boils down to: watch a few seconds to see, what is coming,
watch it again and do a rough cut using the number keys.
Then fine-tune the placement by selecting the outer handles of two neighboring Multicam for A/B rolling.

.. tip::

   To improve playback performance enable :doc:`Proxies </editors/video_sequencer/sequencer/sidebar/proxy>`.


Options
=======

Source Channel
   The channel which the Multicam Selector gets its input from.
Cut To
   Cuts the Multicam strip at the current frame and
   changes the *Source Channel* automatically to the selected channels.


Workflow
========

#. First you are going to want to add in each of your video strips.
#. Next, you will want to sync all your cameras by either using
   :doc:`Audio Waveforms </video_editing/edit/montage/strips/sound>` or by the movement of objects.

   .. tip::

      To make syncing strips easier you can group cameras, their audio,
      and their effects together using :doc:`Meta Strips </video_editing/edit/montage/meta>`.

#. Split the editor into many :doc:`Previews </editors/video_sequencer/preview/index>`, one for each input track.
   Then change the :ref:`Display Channel <bpy.types.SpaceSequenceEditor.display_channel>`
   of each of the previews to the channel number of the input track.
#. Add a Multicam Selector strip *above* all the video channel tracks.

   After completing these steps you should get something similar to the following image:

   .. figure:: /images/video-editing_sequencer_strips_effects_multicam_example.png

      Multi-camera editing setup.

#. Now select the Multicam strip, if you take a look at the strip options (in the Sidebar),
   you will notice, that Multicam is a rather simple effect strip:
   It just takes a selected channel as its input. That is all.
   The magic comes with the convenient keyboard layout.
#. When you select the Multicam strip, the keys :kbd:`1` to :kbd:`9` are mapped to the cut buttons.
   So, select the Multicam strip and start playback and press the keys
   for the correct input while watching the individual cameras.
#. You will end up with a small Multicam Selector strip for every cut.

In reality, it boils down to: watch a few seconds to see, what is coming,
watch it again and do a rough cut using the number keys.
Then fine-tune the placement by selecting the outer handles of two neighboring Multicam for A/B rolling.

.. tip::

   To improve playback performance enable :doc:`Proxies </editors/video_sequencer/sequencer/sidebar/proxy>`.


## Multiply

.. _bpy.types.MultiplySequence:

**************
Multiply Strip
**************

The *Multiply* effect multiplies two colors.
Blender uses values between (0.0 to 1.0) for the colors.
This operation does not have to be normalized, the multiplication of two terms
between (0.0 to 1.0) always gives a result between (0.0 to 1.0).

(With the "traditional" representation of three bytes, like RGB(124, 255, 56),
the multiplications give far too high results, like RGB(7316, 46410, 1848),
that have to be normalized (brought back) by dividing them by 256
to fit in the range of (0 to 255)...)

This effect has two main usages:


.. rubric:: With a Mask

A mask is a black-and-white picture which, after multiplication with a "normal" image,
only show this one in the white areas of the mask (everything else is black).

The opening title sequence to James Bond movies,
where the camera is facing down the barrel of a gun at James, is a good example of this effect.


.. rubric:: With Uniform Colors

Multiplying a color with a "normal" image allows you to soften some hues of this one
(and so -- symmetrically -- to enhance the others).

For example, if you have a brown pixel RGB(0.50, 0.29, 0.05), and
you multiply it with a cyan filter (uniform color RGB(0.0, 1.0, 1.0)), you will get a color RGB(0.0, 0.29, 0.5).
Visually, the result is to zero the reds and bring up (by "symmetry" -- the real values remain unchanged!)
the blues and greens. Physically, it is the same effect as shining a cyan light onto a chocolate bar. Emotionally,
vegetation becomes more lush, water becomes more Caribbean and inviting, skies become friendlier.

.. note::

   This effect reduces the global luminosity of the picture
   (the result will always be smaller than the smallest operand).
   If one of the images is all white, the result is the other picture;
   if one of the images is all black, the result is all black!


Options
=======

This strip has no options.


Example
=======

.. figure:: /images/video-editing_sequencer_strips_effects_multiply_example.png

   Multiply Effect.


## Speed Control

.. _bpy.types.SpeedControlSequence:

*******************
Speed Control Strip
*******************

Speed Control time-warps the strip, making it play faster or slower than it normally would.
Playing faster means that some frames are skipped,
and the strip will run out of frames before the end frame.
When the strip runs out of frames to display, it will just keep repeating
the last one action that will appear to be frozen. To avoid this,
position the next strip under the original at a point where you want the motion to continue.


Options
=======

Speed Control
   The method used to adjust the speed of the strip.

   :Stretch:
      Automatically calculates the speed effect based on the length of the input strip.
      If you scale a strip to 1/2 the original size the sequence will play back at 2 times the speed.
   :Multiply:
      Multiplies the current speed of the sequence by a *Multiply Factor*.
      Thus a value of 0.5 will make the sequence half as fast while 2 would make the sequence twice as fast.
      Negative values will reverse the input while also adjusting the speed,
      so a value of negative two will play in reverse and twice as fast as normal.

      .. note::

         You will have to manually re-adjust the length of the strip accordingly.

   :Frame Number:
      Specifies a frame to remap the current frame to,
      for example, setting the *Frame Number* value to 50 displays the 50th frame.
      This can then be manually :doc:`keyframed </animation/keyframes/index>` to recreate the animation.
   :Length:
      Maps the frame range on a percentage scale. For example, using this and a value of 50%
      will select the frame halfway through the sequence.

Interpolation
   Crossfades between frames to reduce screen tearing when the speed is slower than the original frame rate.


Examples
========

Creating a Slow-Motion Effect
-----------------------------

Suppose you want to slow your strip down.
You need to affect the speed of the video clip without affecting the overall frame rate.
Select the clip and :menuselection:`Add --> Effect --> Speed Control` effect strip.

Choose the *Multiply* option in the Effect Strip panel in the Sidebar.
Set the Multiply Factor to be the factor by which you want to adjust the speed.
To cut the displayed speed by 50%, enter 0.5.
Now, a 275-frame clip will play at half speed, and thus display only the first 137 frames.

If you want the remaining frames to show in slow motion after the first set is displayed,
double the Length of the source strip
(since effects strip bounds are controlled by their source strips).
If you are using a speed factor other than 0.5 then use the formula:

``new_length = real_length / speed_factor``

That is it, set your render to animate (in this example) all 550 frames.


Keyframing the Speed Control
----------------------------

.. figure:: /images/video-editing_sequencer_strips_effects_speed-control_keyframing.png
   :align: right

   Keyframing the Frame number.

To get even finer control over your clip timing, you can use curves!
While it is possible to keyframe the Multiply factor,
usually you want to keyframe the Frame number directly.

Choose the *Frame Number* option. You now have a Frame number field which you can keyframe.
If you want the strip to animate **at all** you will have to insert some keyframes,
otherwise it will look like a still. In most cases you will want to use the Graph editor view
to set the curve interpolation to Linear since the default Bézier will rarely be what you want.

.. tip::

   If you choose to keyframe the Speed factor instead, remember to
   :ref:`Refresh All <bpy.ops.sequencer.refresh_all>` or the changes will not take effect.


.. _video_editing-change_fps:

Changing Video Frame Rates
--------------------------

You can use the speed control to change the frame rate in frames per second (fps) of a video.
If you are rendering your video to a sequence set,
you can effectively increase or decrease the number of individual image files created,
by using a Multiply value less than or greater than one, respectively.

For example, if you captured a five-minute video at 30 fps and wanted to transfer that to film,
which runs at 24 fps, you would enter a Multiply Factor of 30/24, or 1.25
(and enable *Interpolation* frame blending to create a film blur effect).
Instead of producing ``5 × 60 × 30 = 9000`` frames,
Blender would produce ``9000 / 1.25 = 7200 = 5 × 60 × 24`` frames.
In this case, you set a *start* = 1 and *end* = 7200, set your Format output to ``jpeg`` 30fps,
and image files ``0001.jpg`` through ``7200.jpg`` would be rendered out,
but those images cover the entire 9000 frames. The image file ``7200.jpg`` is the same at frame 9000.
When you read those images back into your film blend-file at 24 fps, the strip will last exactly 5 minutes.


## Subtract

.. _bpy.types.SubtractSequence:

**************
Subtract Strip
**************

This effect takes away one strip's color from the second.

Make a negative of an image using this effect,
or switch the order of the strips and just darken the strip.
Subtracting a hue of blue from a white image will make it yellow,
since red and green make yellow.


Options
=======

This strip has no options.


Example
=======

.. figure:: /images/video-editing_sequencer_strips_effects_subtract_example.png

   Subtract Effect.


## Transform

.. _bpy.types.TransformSequence:

***************
Transform Strip
***************

Transform is a swiss-army knife of image manipulation.
It moves, rotates, and scales the images within a strip.


Options
=======

.. _bpy.types.TransformSequence.interpolation:

Interpolation
   :None: No interpolation, uses nearest neighboring pixel.
   :Bilinear: Simple interpolation between adjacent pixels.
   :Bicubic: Highest quality interpolation.

.. _bpy.types.TransformSequence.translation_unit:

Translation Unit
   Control whether the input values are in *Percent* or *Pixels*.

.. _bpy.types.TransformSequence.translate_start:

Position
   Moves the input along the X and Y axis.

.. _bpy.types.TransformSequence.use_uniform_scale:

Uniform Scale
   Scale the input evenly along the X and Y axis.

.. _bpy.types.TransformSequence.scale_start:

Scale
   Scale the image on the X and Y axis.

.. _bpy.types.TransformSequence.rotation_start:

Rotation
   Rotates the input two-dimensionally along the Z axis.


Example
=======

.. figure:: /images/video-editing_sequencer_strips_effects_transform_example.png

   Transform Effect.


## Cross

.. _bpy.types.CrossSequence:

***********
Cross Strip
***********

The *Cross* transition fades from one strip to another, also known as a crossfade.
Strips can be overlapping or have a gap between them,
however, when strips contain a gap the last and first frame of each strip
is extend which can cause a pause if any of the strips are a sequence.


Options
=======

Default Fade
   Automatically calculates a linear fade over the length of the strip.

   Effect Fader
      Allows you to manually :doc:`keyframe </animation/keyframes/index>` a custom fade.
      This can be used with different :ref:`easings <editors-graph-fcurves-settings-easing>`
      to fine-tune the fade in/out.


Example
=======

.. figure:: /images/video-editing_sequencer_strips_transitions_cross_example.png

   Cross Effect.


## Gamma Cross

.. _bpy.types.GammaCrossSequence:

*****************
Gamma Cross Strip
*****************

The Gamma Cross transition is similar to the :doc:`/video_editing/edit/montage/strips/transitions/cross` transition,
however, the Gamma Cross strip transition uses color correction while transitioning between the two strips,
resulting in a smoother transition that is easier on the eyes.


Options
=======

Default Fade
   Automatically calculates a linear fade over the length of the strip.

   Effect Fader
      Allows you to manually :doc:`keyframe </animation/keyframes/index>` a custom fade.
      This can be used with different :ref:`easings <editors-graph-fcurves-settings-easing>`
      to fine-tune the fade in/out.


## Index


###############
  Transitions
###############

.. toctree::
   :maxdepth: 1

   sound_crossfade.rst
   cross.rst
   gamma_cross.rst
   wipe.rst


## Sound Crossfade

.. _bpy.ops.sequencer.crossfade_sounds:

***************
Sound Crossfade
***************

The *Sound Crossfade* transition works by animating the *Volume*
of two overlapping Sound strips to evenly fade between them.
Because this simply animates a value it does not create a strip like other effects or transitions.


## Wipe

.. _bpy.types.WipeSequence:

**********
Wipe Strip
**********

The *Wipe* transition strip can be used to transition from one strip to the next.
The wipe will have no effect if created from a single strip instead of two strips.
The duration of the wipe is the intersection of the two source strips and cannot be adjusted.
To adjust the start and end of the wipe you must adjust the temporal bounds of the source strips
in a way that alters their intersection.


Options
=======

Transition
   The type of transition used.

   Single
      Reveals the next strip by uncovering it in a straight line moving across the image.
   Double
      Similar to *Single*, but uses two lines either starting from the middle of the image or the outside.
      Like the blink of an eye.
   Iris
      Reveals the next strip through an expanding (or contracting) circle.
      Like the aperture of a camera or pupil of an eye.
      You can blur the transition, so it looks like ink bleeding through a paper.
   Clock
      Like the hands of an analog clock, it sweeps clockwise or (if Wipe In is enabled)
      counterclockwise from the 9:00 position. As it sweeps, it reveals the next strip.

Direction
   Controls whether to fade *In* or *Out*.
Blur Width
   The width of the blur used to blur the transition.
Angle
   Controls the angle of the line for *Single* and *Double* transition types.

Default Fade
   Automatically calculates a linear fade over the length of the strip.

   Effect Fader
      Allows you to manually :doc:`keyframe </animation/keyframes/index>` a custom fade.
      This can be used with different :ref:`easings <editors-graph-fcurves-settings-easing>`
      to fine-tune the fade in/out.


Example
=======

.. figure:: /images/video-editing_sequencer_strips_transitions_wipe_example.png

   Wipe Effect.


## Directory Structure


*******************
Directory Structure
*******************

A video project is most likely a combination of several different assets.
You can separate them into three broad categories.

- Video files: video clips (or movies in Blender-talk), photos, graphic files (charts, logos, ...),
  and Visual Effects (VFX) such as masks, lens flares, animation.
- Audio files: recorded dialog, voice-over, music, and Sound Effects (SFX) such as environmental sounds, swooshes, ...
- Project files: the blend files and backups, (partial) render results, documentation such as scripts and storyboards.

Together they can form rapidly an intangible heap of files.
It's good practice to collect all those assets in *one* project directory with appropriate subdirectories.
Why? It will lower the probability that you accidentally delete a file
(which will result in a 'file not found' error) or that you forget
to include a necessary file when transferring the project ('file is missing' error).
And most of all, an appropriate directory structure, will help you to keep a clear overview of your assets.

.. seealso::

   Blender can incorporate some files within the Blend file (see :doc:`Packed Data </files/blend/packed_data>`).
   However, this doesn't work with video files, which can have very huge file sizes.
   So, it's better to assure that your project directory contains all necessary files.

It's also good practice to use some kind of naming convention and add metadata.
Figure 1 shows a possible example, based on our categorization of the assets above.
The directories are numbered so that they mimic a normal workflow.

.. figure:: /images/vse_setup_project_dir-structure-example.png
   :alt: Organizing your project

   Figure 1: Organizing your project.


## Index


******************
Setup Your Project
******************

.. toctree::
   :maxdepth: 2

   introduction.rst
   directory_structure.rst


## Introduction


************
Introduction
************

The proverb "A good start is half the battle", certainly applies to video editing.
Setting up your *work environment* and *project* to your needs is key to success.
In setting up your video project, you have to distinguish between:

- Work Environment related settings and activities:

  These settings apply to all of your projects and are set at "Blender level"; for example the installation
  of add-ons. In fact, they can also influence your non-video editing projects.
  Most of these settings remain more or less stable throughout your projects and should probably only set once.
- Project related settings and activities:

  These settings vary from project to project and are very specific for your project;
  for example the output media format. For each new project, you have to evaluate these settings and activities.

Of course, many settings and activities occur at both levels.
For example, automatic proxies can be enabled globally but changed on a per project or even strip basis.
The layout of the Video Editing Workspace is defined at Blender level but can be tweaked per project.


