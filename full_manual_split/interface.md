# Index for interface

- [Annotate Tool](#Annotate-Tool)
- [Index](#Index)
- [Operators](#Operators)
- [Selecting](#Selecting)
- [Tool System](#Tool-System)
- [Undo Redo](#Undo-Redo)
- [Buttons](#Buttons)
- [Decorators](#Decorators)
- [Eyedropper](#Eyedropper)
- [Fields](#Fields)
- [Menus](#Menus)
- [Arranging](#Arranging)
- [Editing](#Editing)
- [Frame](#Frame)
- [Groups](#Groups)
- [Index](#Index)
- [Introduction](#Introduction)
- [Parts](#Parts)
- [Reroute](#Reroute)
- [Selecting](#Selecting)
- [Sidebar](#Sidebar)
- [Color Palette](#Color-Palette)
- [Color Picker](#Color-Picker)
- [Color Ramp](#Color-Ramp)
- [Curve](#Curve)
- [Data Block](#Data-Block)
- [List View](#List-View)
- [Operator Search](#Operator-Search)
- [Blender Default](#Blender-Default)
- [Industry Compatible](#Industry-Compatible)
- [Introduction](#Introduction)
- [Areas](#Areas)
- [Introduction](#Introduction)
- [Regions](#Regions)
- [Splash](#Splash)
- [Status Bar](#Status-Bar)
- [Tabs Panels](#Tabs-Panels)
- [Topbar](#Topbar)
- [Workspaces](#Workspaces)


## Annotate Tool


***********
Annotations
***********

The annotation tool is available in multiple editors.
It can be used to add notes to e.g. 3D objects or node setups.
The arrow in the screenshot below is an annotation.

.. figure:: /images/interface_annotate-tool_node-editor.png
   :align: center

   Annotations tool in a node editor.


.. _tool-annotate:

Annotation Tools
================

The annotation tool can be activated in the Toolbar and has the following sub-tools:

.. _tool-annotate-freehand:

Annotate
   Draw free-hand strokes in the main area.

.. _tool-annotate-line:

Annotate Line
   Click and drag to create a line.
   Optionally, you can select the arrow style for the start and end of the line.

.. _tool-annotate-polygon:

Annotate Polygon
   Click multiple times to create multiple connected lines, then press :kbd:`Return` or :kbd:`Esc` to confirm.

.. _tool-annotate-eraser:

Annotate Eraser
   Click and drag to remove lines.
   The eraser has a *Radius* setting found in :menuselection:`Tool Settings`.


Tool Settings
=============

Common
------

Color
   Adjust the color of existing and new strokes.

Annotation Layer
   A pop-over menu, showing the name of the current layer, to access the `Annotation Layers`_.

.. _bpy.types.ToolSettings.annotation_stroke_placement_view3d:
.. _bpy.types.ToolSettings.annotation_stroke_placement_view2d:

Placement
   Determines where the annotations are drawn.

   :3D Cursor:
      Only available in the 3D Viewport. The new annotations become part of the 3D scene;
      they're drawn on an imaginary plane that goes through the :doc:`/editors/3dview/3d_cursor`
      and is aligned to your view.
   :Surface:
      Only available in the 3D Viewport. The new annotations become part of the 3D scene;
      they're drawn onto the surface of the object under the mouse. If there is no surface,
      you get the same behavior as *3D Cursor*.
   :Image:
      Only available in 2D editors such as the :doc:`Image Editor </editors/image/introduction>`.
      The annotations become part of the 2D space, meaning their position and size change as you
      pan and zoom in the editor.
   :View:
      The new annotations are 2D and get stuck to the screen. They keep the same position,
      rotation and size no matter how you pan, orbit or zoom in the editor.

Stabilize Stroke
   Helps to reduce jitter of the strokes while drawing by delaying and correcting the location of points.

   Radius
      Minimum distance from the last point before the stroke continues.
   Factor
      A smooth factor, where higher values result in smoother strokes
      but the drawing sensation feels like as if you were pulling the stroke.


Annotate Line
-------------

Style Start, End
   The decoration to use at the beginning or end of the line segment.
   This can be used for example to create arrows to point out specific details in a scene.


Annotation Layers
=================

When the annotation tool is enabled, the settings for managing multiple layers
can be found in the :menuselection:`Sidebar --> View --> Annotations` panel.

.. _bpy.types.GPencilLayer.annotation_opacity:

Opacity
   Adjusts the opacity of existing and new strokes.

Thickness
   Adjusts the thickness of existing and new strokes.


.. _bpy.types.GPencilLayer.use_annotation_onion_skinning:

Onion Skin
----------

Shows a ghosted image of strokes made in frames before and after the current frame.
Onion skinning only works in the 3D Viewport and Sequencer.
See the Grease Pencil documentation for an explanation of
:doc:`Onion Skinning </grease_pencil/properties/onion_skinning>`.

.. _bpy.types.GPencilLayer.annotation_onion_before_color:
.. _bpy.types.GPencilLayer.annotation_onion_before_range:
.. _bpy.types.GPencilLayer.annotation_onion_after_color:
.. _bpy.types.GPencilLayer.annotation_onion_after_range:

Before/After
   Color to use before and after the current frame on ghost frames.
   The number defines how many frames to show before and after the current frame.


## Index

.. index:: User Interface
.. _bpy.types.WindowManager:
.. _bpy.types.Window:
.. _bpy.types.Screen:
.. _bpy.ops.wm:
.. _bpy.ops.ui:

##################
  User Interface
##################

Window System
=============

.. toctree::
   :maxdepth: 1

   Introduction <window_system/introduction.rst>
   window_system/splash.rst
   window_system/topbar.rst
   window_system/workspaces.rst
   window_system/status_bar.rst
   window_system/areas.rst
   window_system/regions.rst
   window_system/tabs_panels.rst


Keymap
======

.. toctree::
   :maxdepth: 1

   keymap/introduction.rst
   keymap/blender_default.rst
   keymap/industry_compatible.rst


Interface Controls
==================

Buttons and Controls
--------------------

.. toctree::
   :maxdepth: 1

   controls/buttons/buttons.rst
   controls/buttons/fields.rst
   controls/buttons/menus.rst
   controls/buttons/eyedropper.rst
   controls/buttons/decorators.rst


Extended Controls
-----------------

.. toctree::
   :maxdepth: 1

   controls/templates/data_block.rst
   controls/templates/list_view.rst
   controls/templates/color_picker.rst
   controls/templates/color_ramp.rst
   controls/templates/color_palette.rst
   controls/templates/curve.rst
   controls/templates/operator_search.rst
   controls/nodes/index.rst


Tools & Operators
=================

.. toctree::
   :maxdepth: 1

   tool_system.rst
   operators.rst
   undo_redo.rst
   annotate_tool.rst
   selecting.rst


## Operators


*********
Operators
*********

Operators execute an action the moment they're activated,
which makes them different from tools (which require some sort of input).
Operators can be started from :ref:`ui-operator-buttons`,
:ref:`bpy.types.UIPopupMenu`, or :ref:`bpy.ops.wm.search_menu`.
Examples of operators include adding a new object,
deleting it, or setting its shading to smooth.


Operator Properties
===================

Most operators have properties that can be adjusted to refine their result.
First run the operator (which will use its default settings),
then adjust the properties in the :ref:`bpy.ops.screen.redo_last` region.


Modal Operators
===============

Modal operators exist as a concept in between :doc:`Tools </interface/tool_system>`
and regular operators.
They require some sort of interactive input.

The action of a modal operator can be confirmed using :kbd:`LMB` or :kbd:`Return`.
To cancel a modal operator use :kbd:`RMB` or :kbd:`Esc`.


Slider Operators
----------------

Slider operators are used to interactively adjust a percentage value
in the editor's :ref:`ui-region-header`.

You can adjust the percentage by dragging the slider left or right.
This can be made coarser (snapping in 10% increments) by holding :kbd:`Ctrl`
and more precise by holding :kbd:`Shift`.
For some sliders, you can toggle "overshoot" with :kbd:`E`, which lets
you go beyond the 0-100% range.


## Selecting


*********
Selecting
*********

By default, Blender uses :kbd:`LMB` to select items.
This can be changed to :kbd:`RMB` in the :doc:`Preferences </editors/preferences/keymap>`.

Blender has several selection tools that can be used across the different editors.

.. note::

   Some editors deviate from the keyboard shortcuts shown below. For example, most editors
   use :kbd:`Shift-LMB` to add a single item to the selection, but the
   :doc:`Outliner </editors/outliner/introduction>` uses :kbd:`Ctrl-LMB`.
   Similarly, most editors use :kbd:`Ctrl-RMB` for performing a *Lasso Select*,
   but :doc:`node editors </interface/controls/nodes/introduction>` use :kbd:`Ctrl-Alt-LMB`.

Most selection tools come in two variants, where one variant is available in the Toolbar
and the other in the *Select* menu. While the variants' names are almost identical
(such as *Select Box* in the Toolbar versus *Box Select* in the menu),
the way they work is a bit different. New users coming from other applications
will find the Toolbar variants to be the most familiar.


Toolbar Selection Tools
=======================

All the Toolbar selection tools behave the same when clicking an item: they select it
(and deselect any previously selected items). If you hold :kbd:`Shift` while clicking,
the item will be added to the selection (if it's not selected) or removed from the selection
(if it is selected).

What makes the tools different is what happens when you drag.


.. _tool-select-tweak:

Tweak
-----

.. reference::

   :Tool:      :menuselection:`Toolbar --> Tweak`
   :Shortcut:  :kbd:`W`

Dragging an item will move it around.


.. _tool-select-box:

Select Box
----------

.. reference::

   :Tool:      :menuselection:`Toolbar --> Select Box`
   :Shortcut:  :kbd:`W`

Dragging will create a rectangle, and select all the items that are partially or completely inside it
once you release. (Any other items will be deselected.)

Holding :kbd:`Shift` while dragging will add the items to the selection.
Holding :kbd:`Ctrl` will remove them.

While dragging, you can additionally hold :kbd:`Spacebar` to move the rectangle around with the mouse.

.. list-table:: Select Box example (Edit Mode).

   * - .. _fig-mesh-select-basics-start:

       .. figure:: /images/interface_selecting_border-select1.png
          :width: 200px

          Start.

     - .. _fig-mesh-select-basics-selecting:

       .. figure:: /images/interface_selecting_border-select2.png
          :width: 200px

          Selecting vertices.

     - .. _fig-mesh-select-basics-complete:

       .. figure:: /images/interface_selecting_border-select3.png
          :width: 200px

          Complete.


.. _tool-select-circle:

Select Circle
-------------

.. reference::

   :Tool:      :menuselection:`Toolbar --> Select Circle`
   :Shortcut:  :kbd:`W`

Dragging will select all the items which the circle passed over.
Items which you didn't pass over will be deselected.

Holding :kbd:`Shift` while dragging will add the items to the selection.
Holding :kbd:`Ctrl` will remove them.

You can change the radius of the circle in the tool settings (which can be found
in the area header, the Tool tab of the Sidebar :kbd:`N`, or the Active Tool tab
of the :doc:`Properties editor </editors/properties_editor>`).

.. note::

   In :doc:`Object Mode </editors/3dview/modes>`: unlike *Select Box*,
   which selects objects as soon as the box covers any part of their geometry,
   *Select Circle* only selects objects if the circle passes over their origin point.
   The origin is shown as an orange dot for selected objects but is invisible for unselected ones,
   unless "Origins (All)" is enabled in the :doc:`/editors/3dview/display/overlays`.

   This difference in behavior does not apply to the other modes
   (like Edit Mode and Pose Mode).

.. list-table:: Select Circle example (Edit Mode).

   * - .. figure:: /images/interface_selecting_circle-select1.png
          :width: 320px

          Start.

     - .. figure:: /images/interface_selecting_circle-select2.png
          :width: 320px

          Selecting vertices.

     - .. figure:: /images/interface_selecting_circle-select3.png
          :width: 320px

          Complete.


.. _tool-select-lasso:

Select Lasso
------------

.. reference::

   :Tool:      :menuselection:`Toolbar --> Select Lasso`
   :Shortcut:  :kbd:`W`

Dragging will create a freeform shape, and select all the items inside it once you release.
(Any other items will be deselected.)

Holding :kbd:`Shift` while dragging will add the items to the selection.
Holding :kbd:`Ctrl` will remove them.

While dragging, you can additionally hold :kbd:`Spacebar` to move the shape around with the mouse.

.. note::

   *Select Lasso* behaves the same as *Select Circle* in that
   it only looks at origin points in Object Mode.

.. list-table:: Select Lasso example (Edit Mode).

   * - .. figure:: /images/interface_selecting_lasso-select1.png
          :width: 200px

          Start.

     - .. figure:: /images/interface_selecting_lasso-select2.png
          :width: 200px

          Selecting vertices.

     - .. figure:: /images/interface_selecting_lasso-select3.png
          :width: 200px

          Complete.


Selection Modes
---------------

.. reference::

   :Tool:      Select Tools
   :Panel:     :menuselection:`Tool Settings --> Mode`

Each of the Toolbar selection tools has a mode to configure
how it interacts with existing selections.
Note that not every tool supports all of these modes.

Set
   Sets a new selection (the previous selection is discarded).
   This is the default.
Extend
   Adds newly selected items to the existing selection.
Subtract
   Removes newly selected items from the existing selection.
Invert :kbd:`Ctrl-I`
   Inverts the selection (unselected items become selected and vice versa).
Intersect
   Selects items that intersect with the existing selection.


Menu Selection Tools
====================

These tools are variants of the previously described ones.
They're available in the menu rather than the Toolbar
and work slightly differently.


.. _bpy.ops.*.select_box:

Box Select
----------

.. reference::

   :Menu:      :menuselection:`Select --> Box Select`
   :Shortcut:  :kbd:`B`

To use this tool, you first activate the menu item or keyboard shortcut
and then drag a box as usual. Unlike *Select Box*, the default behavior
here is to add the items inside the box to the selection.
(The ones outside the box are not deselected.)

To remove the items inside the box from the selection,
hold :kbd:`Shift`, or drag with :kbd:`MMB` instead.

While dragging, you can additionally hold :kbd:`Spacebar` to move the box around with the mouse.


.. _bpy.ops.*.select_circle:

Circle Select
-------------

.. reference::

   :Menu:      :menuselection:`Select --> Circle Select`
   :Shortcut:  :kbd:`C`

To use this tool, you first activate the menu item or keyboard shortcut
and then drag a circle around as usual. Unlike *Select Circle*, the default
behavior here is to add the items inside the circle to the selection.
(The ones outside the circle are not deselected.)

To remove the items inside the circle from the selection,
hold :kbd:`Shift`, or drag with :kbd:`MMB` instead.

You can change the radius of the circle by scrolling with the :kbd:`Wheel`
or using the :kbd:`NumpadPlus` and :kbd:`NumpadMinus` keys.

Once activated, *Circle Select* stays active: you can release the mouse button
and start dragging somewhere else without having to press :kbd:`C` again.
At the same time, however, it blocks all other parts of Blender while it's active.
To deactivate the tool again, press :kbd:`RMB`, :kbd:`Return`, or :kbd:`Esc`.


.. _bpy.ops.*.select_lasso:

Lasso Select
------------

.. reference::

   :Menu:      :menuselection:`Select --> Lasso Select`
   :Shortcut:  :kbd:`Ctrl-RMB`

To use this tool, you first activate the menu item and drag a freeform shape
around the item(s) you want to select with :kbd:`LMB`. The menu lets you choose
whether to set, extend or reduce the selection.

Alternatively, you can immediately start dragging with :kbd:`Ctrl-RMB`.
Unlike *Select Lasso*, the default behavior then is to add the items inside
the lasso to the selection. (The ones outside the lasso are not deselected.)

To remove the items inside the lasso from the selection,
drag with :kbd:`Shift-Ctrl-RMB` instead.

While dragging, you can additionally hold :kbd:`Spacebar` to move the lasso
around with the mouse.


## Tool System

.. _ui-tool_system:
.. _bpy.ops.wm.tool:

***********
Tool System
***********

Tools are accessed from the :ref:`Toolbar <ui-region-toolbar>`.

This is a general introduction to tools. Individual tools have their own documentation.

There can only be one active tool per :doc:`Workspace </interface/window_system/workspaces>`
and :doc:`mode </editors/3dview/modes>`.
This tool is remembered: if you're in Edit Mode and have the Extrude tool selected,
then switch to Object Mode (which has no Extrude tool) and back to Edit Mode,
the Extrude tool will still be active.

Most tools are controlled using just :kbd:`LMB`, though some also have modifier keys
(shown in the :doc:`Status Bar </interface/window_system/status_bar>` while using the tool).
This can all be customized in the :doc:`Keymap Preferences </editors/preferences/keymap>`.

Some tools define gizmos (*Shear* and *Spin* for example) to help control them.


.. _ui-region-toolbar:

Toolbar
=======

.. reference::

   :Shortcut:  :kbd:`T`

.. figure:: /images/interface_tool-system_buttons-popup.png
   :align: right

   Expanded tool group.

The Toolbar contains buttons for the various tools.
Buttons with a small triangle in their bottom right corner are tool groups
which can be opened by holding :kbd:`LMB` on them for a moment
(or dragging :kbd:`LMB` to open them instantly).

Hovering your cursor over a tool for a short time will show its name,
while hovering longer will show the full tooltip.

Resizing the Toolbar horizontally will display the icons with two columns.
Expanding it further will display the icon and its text.


.. _bpy.ops.wm.toolbar:

Pop-Up Toolbar
==============

.. reference::

   :Shortcut:  :kbd:`Shift-Spacebar`

Pressing :kbd:`Shift-Spacebar` will pop up a small toolbar right at
your cursor for faster access.
The shortcuts for selecting the tools are displayed on the right.

Alternatively, you can map this action to :kbd:`Spacebar` in the Keymap Preferences.
Then you'll be able use :kbd:`Spacebar` like a modifier key
(similar to holding :kbd:`Ctrl` or :kbd:`Shift`).
For example, you can press :kbd:`Spacebar T` for Transform,
:kbd:`Spacebar D` for Annotate, :kbd:`Spacebar M` for Measure and so on.
See :ref:`Spacebar Action <keymap-blender_default-spacebar_action>`.


Quick Favorites
===============

.. reference::

   :Shortcut:  :kbd:`Q`

The Quick Favorites menu gathers your favorite tools.
Any tool or menu item can be added to this pop-up menu via its context menu.


Changing Tools
==============

If you have *Alt Click Tool Prompt* enabled in the Keymap Preferences,
tapping :kbd:`Alt` will display a tool prompt in the Status Bar.
You can then press a key to select the corresponding tool, or tap :kbd:`Alt` again to cancel the prompt.


.. _bpy.ops.wm.toolbar_fallback_pie:

Fallback Tool
-------------

The fallback tool is the one that's selected by default (so the one at the top of the Toolbar).
You can change it by either holding :kbd:`LMB` on the toolbar button or pressing :kbd:`Alt-W`
to get a pie menu.


Cycling Tools
-------------

If you bind a key to a tool which is part of a group, you can enable the *Cycle* option in the keymap editor.
Successive presses will then cycle through the tools in that group.

This is enabled by default for the selection tools in the 3D Viewport, for example:
pressing :kbd:`W` will cycle between Select Box, Select Circle and so on.


Properties
==========

Tools can have their own settings, which are available from multiple places:

- The :menuselection:`Tool --> Active Tool` panel in the Sidebar :kbd:`N`.
- The *Active Tool* tab in the :doc:`Properties editor </editors/properties_editor>`.
- The *Tool Settings* region below the area header.


## Undo Redo

.. _bpy.ops.ed:

***********
Undo & Redo
***********

The tools listed below will let you roll back an accidental action,
redo your last action, or let you choose to recover to a specific point,
by picking from a list of recent actions recorded by Blender.


.. _bpy.ops.ed.undo:

Undo
====

.. reference::

   :Mode:      All Modes
   :Menu:      :menuselection:`Edit --> Undo`
   :Shortcut:  :kbd:`Ctrl-Z`

If you want to undo your last action, just press :kbd:`Ctrl-Z`.

.. seealso::

   :ref:`Memory & Limits Preferences <prefs-system-memory-and-limits>` to change undo settings.


.. _bpy.ops.ed.redo:

Redo
====

.. reference::

   :Mode:      All Modes
   :Menu:      :menuselection:`Edit --> Redo`
   :Shortcut:  :kbd:`Shift-Ctrl-Z`

To roll back the Undo action, press :kbd:`Shift-Ctrl-Z`.


.. _bpy.ops.screen.redo_last:

Adjust Last Operation
=====================

.. reference::

   :Mode:      All Modes
   :Menu:      :menuselection:`Edit --> Adjust Last Operation...`
   :Shortcut:  :kbd:`F9`

You can tweak the parameters of an :doc:`operator </interface/operators>` after running it.
In editors that support it, there is a "head-up display" panel in the bottom left
based on the last performed operation.
Alternatively, you can create a pop-up with :kbd:`F9` which does the same thing.

For example, if your last operation was a rotation in *Object Mode*,
Blender will show you the last value changed for the angle
(see Fig. :ref:`fig-interface-redo-last-object-mode` left),
where you can change your action back completely by typing :kbd:`Numpad0` in the *Angle* Field.
There are other useful options, based on the operator,
and you cannot only Undo actions, but change them completely using the available options.

If you are in *Edit Mode*,
Blender will also change its contents based on your last action taken.
In the second example (on the right), the last operation was a Move in Object Mode;
but a *Scale* on a Face in Edit Mode, and, as you can see,
the contents of *Adjust Last Operation* are different, because of the mode (Edit Mode)
(See Fig. :ref:`fig-interface-redo-last-edit-mode` right).

.. list-table:: Adjust Last Operation.

   * - .. _fig-interface-redo-last-object-mode:

       .. figure:: /images/interface_undo-redo_redo-last-object-mode.png
          :width: 310px

          Rotation (Object Mode, 60 degrees).

     - .. _fig-interface-redo-last-edit-mode:

       .. figure:: /images/interface_undo-redo_redo-last-edit-mode.png
          :width: 310px

          Scale (Edit Mode, Resize face).

.. tip::

   Some operations produce particularly useful results by using *Adjust Last Operation*.
   For example, adding a Circle in the 3D Viewport; if you reduce the *Vertices* to three,
   you get a perfect equilateral triangle.

.. tip::

   The *Adjust Last Operation* region can be hidden by :menuselection:`View --> Adjust Last Operation`.


.. _bpy.ops.ed.undo_history:

Undo History
============

.. reference::

   :Mode:      All Modes
   :Menu:      :menuselection:`Edit --> Undo History`

.. figure:: /images/interface_undo-redo_undo-history-menu.png
   :align: right

   The Undo History menu.

There is also an Undo History of the last actions taken, recorded by Blender.

The top of the list corresponds to the most recent actions.
A small icon of a dot next to one of the entries indicates the current status.
Rolling back actions using the *Undo History* feature will take you back to
the action you choose. Much like how you can alternate between going backward in
time with *Undo* and then forward with *Redo*,
you can hop around on the Undo timeline as much as you want as long as you do not make a new change.
Once you do make a new change, the Undo History is truncated at that point.
Selecting one of the entries in the list takes the current status to that position.


.. _bpy.ops.screen.repeat_last:

Repeat Last
===========

.. reference::

   :Mode:      All Modes
   :Panel:     :menuselection:`Edit --> Repeat Last`
   :Shortcut:  :kbd:`Shift-R`

The Repeat Last feature will repeat your last action when you press :kbd:`Shift-R`.

In the example images below, we duplicated a *Monkey* mesh and moved it a bit.
Using repeat :kbd:`Shift-R`, the *Monkey* was duplicated and moved a second time.

.. list-table::

   * - .. figure:: /images/interface_undo-redo_repeat-last1.png

          Suzanne.

     - .. figure:: /images/interface_undo-redo_repeat-last2.png

          After a :kbd:`Shift-D` and move.

     - .. figure:: /images/interface_undo-redo_repeat-last3.png

          After a :kbd:`Shift-R`.


.. _bpy.ops.screen.repeat_history:

Repeat History
==============

.. reference::

   :Mode:      All Modes
   :Menu:      :menuselection:`Edit --> Repeat History...`

.. figure:: /images/interface_undo-redo_repeat-history-menu.png
   :align: right

   The Repeat History menu.

The *Repeat History* feature will present you a list of the last repeated actions,
and you can choose the actions you want to repeat.
It works in the same way as the Undo History, explained above,
but the list contains only repeated actions.

.. container:: lead

   .. clear

.. important::

   When you quit Blender, the complete list of user actions will be lost, even if you save your file before quitting.

.. seealso::

   Troubleshooting section on :doc:`Recovering your lost work </troubleshooting/recover>`.


## Buttons

.. _bpy.ops.buttons:

*******
Buttons
*******

.. _ui-operator-buttons:

Operator Buttons
================

.. figure:: /images/interface_controls_buttons_buttons_operation.png
   :align: right

   Operator button.

Operator buttons execute an :doc:`Operator </interface/operators>`
which in summary execute an action when clicked with :kbd:`LMB`.
Operator buttons may be an icon, text, or text with an icon.

.. container:: lead

   .. clear


Checkboxes & Toggle Buttons
===========================

.. figure:: /images/interface_controls_buttons_buttons_checkbox.png
   :align: right
   :figwidth: 155px

   Checkboxes and Toggle buttons.

These controls are used to activate or deactivate options.
Use :kbd:`LMB` to change their state. A tick is shown on checkboxes when
the option is activated. Active status on toggle buttons is indicated
either by color on the icon background, or a change in icon graphics.


Dragging
--------

To change many values at once on or off, you can press down
:kbd:`LMB` and drag over multiple buttons.
This works for checkboxes, toggles and to select a radio button value.


Radio Buttons
=============

.. figure:: /images/interface_controls_buttons_buttons_radio.png
   :align: right

   Radio buttons.

Radio buttons are used to choose one option from a selection of options.
The active button is indicated by a colored background.


Cycling
-------

Use :kbd:`Ctrl-Wheel` while hovering the mouse over radio
buttons to cycle between the options.


.. _ui-direction-button:

Direction Buttons
=================

.. figure:: /images/interface_controls_buttons_buttons_direction.png
   :align: right

   Direction buttons.

Clicking with :kbd:`LMB` in the sphere and dragging the mouse cursor
lets the user change the direction by rotating the sphere.


Shortcuts
---------

- :kbd:`LMB` (drag) rotates the direction.
- :kbd:`Ctrl` (while dragging) snaps to vertical & diagonal directions.


## Decorators


**********
Decorators
**********

Decorators are small buttons that appear to the right of other buttons and show the state of the property.
Decorators may appear next to number fields, menus,
and checkboxes to indicate the property can be :doc:`animated </animation/index>`.

.. figure:: /images/interface_controls_buttons_decorators_ui.png
   :align: center

   Decorators indicating different property states.

Clicking on the decorator dot icon will add a :doc:`Keyframe </animation/keyframes/index>` to that property.
Clicking the rhombus icon again will remove the keyframe.
A solid rhombus icon indicates there is a keyframe on the current frame,
while a non-solid rhombus icon indicates that the property has a keyframe on another frame.
Clicking the non-solid rhombus icon will create a keyframe on the current frame with the current property value.

If a property is being :doc:`driven </animation/drivers/index>`
by another, the decorator shows the driver icon.

Decorators make it quick and easy to glance over properties and see their state.

.. seealso::

   :ref:`State Colors <animation-state-colors>`


## Eyedropper

.. _ui-eyedropper:
.. _bpy.ops.ui.eyedropper:

**********
Eyedropper
**********

The eyedropper (pipette icon) allows you to sample from anywhere in the Blender window.
The eyedropper can be used to select different kinds of data:

Color
   This is the most common usage. The eyedropper is used to sample a pixel's color from anywhere within Blender.

   .. note::

      The :ref:`View Transform <bpy.types.ColorManagedViewSettings.view_transform>` of the color management
      affects the color. In order to get consistent results, it should be set to *Standard*.
      If it's set to any other option, the eyedropper may return an inaccurate color.

Color Ramp
   Dragging the cursor over the window to sample a line which is converted into a color ramp.

Objects/Object-Data
   This is used with object buttons (such as parent, constraints or modifiers) to
   select an object from the 3D Viewport or Outliner, rather than having to select it from a drop-down.

Camera Depth
   Number fields effecting distance can also use the eyedropper.

   This is used to set the camera's depth of field so the depth chosen is in focus.

- :kbd:`E` will activate the eyedropper while hovering over a button.
- :kbd:`LMB` dragging will mix the colors you drag over, which can help when sampling noisy imagery.
- :kbd:`Spacebar` resets and starts mixing the colors again.


## Fields


******
Fields
******

.. _bpy.ops.buttons.start_filter:
.. _bpy.ops.buttons.clear_filter:

Text & Search Fields
====================

.. figure:: /images/interface_controls_buttons_fields_text-search.png
   :align: center

   A text and a search field.

Text fields show a rounded rectangular border, and optionally an icon and/or text inside the border.
Text fields store text strings, and provide the means to edit text
by :doc:`standard text editing shortcuts </interface/keymap/introduction>`.

For text fields with an icon and pop-ups, see :ref:`ui-data-id`.


Number Fields
=============

.. figure:: /images/interface_controls_buttons_fields_number-button.png
   :align: right

   Number fields.

Number fields store values and units.

The first type of number field shows triangles pointing left (<) and right (>)
on the sides of the field when mouse pointer is over the field.

Sliders, a second type of number field, have a colored bar in the background
to display values over a range, e.g. percentage values.

The value can be edited in several ways:

Incremental Steps
   To change the value in unit steps, click :kbd:`LMB` on the small triangles (not available for sliders).
   You can also use :kbd:`Ctrl-Wheel` while hovering over the field to edit the value.
Dragging
   To change the value with the mouse, hold down :kbd:`LMB` and drag to left or right.

   Hold :kbd:`Ctrl` to snap to the discrete steps while dragging or :kbd:`Shift` for precision input.
Keyboard Input
   Press :kbd:`LMB` or :kbd:`Return` to enter value by typing it with keyboard.

   When entering values by keyboard, number fields work like text fields:

   - Press :kbd:`Return` or :kbd:`LMB` outside the field to apply the change.
   - Press :kbd:`Esc` or :kbd:`RMB` to cancel.
   - Press :kbd:`Tab` to jump to the next field or :kbd:`Shift-Tab` to go to the previous field.
   - Press :kbd:`Minus` while hovering over a number field to negate the value.


Multi-Value Editing
-------------------

.. figure:: /images/interface_controls_buttons_fields_multi-value-edit.png
   :align: right

   Multi-value editing.

You can edit multiple number fields at once by pressing down
:kbd:`LMB` on the first field, and then dragging vertically over
the fields you want to edit. Finally you can either drag left or right to
adjust value with the mouse, or release the :kbd:`LMB` and type in a value.


Value Limits
------------

Most numerical values are restricted by "soft limit" and "hard limit" value ranges.
Changing values by dragging with the mouse is restricted to the "soft limit" value range.
Input via keyboard will allow the use of wider value ranges, but never wider than the "hard limit".


Expressions
-----------

.. Do not use mathjax here

You can enter mathematical expressions into any number field.
For example, enter ``3*2`` or ``10/5+4`` instead of ``6``.
Even constants like ``pi`` (3.142) or functions like ``sqrt(2)`` (square root of 2)
may be used.

.. seealso::

   These expressions are evaluated by Python; for all available math expressions see:
   `Math module reference <https://docs.python.org/3/library/math.html>`__.


Expressions as Drivers
^^^^^^^^^^^^^^^^^^^^^^

You may want your expression to be re-evaluated after it is entered.
Blender supports this using :doc:`Drivers </animation/drivers/index>` (a feature of the animation system).

Expressions beginning with ``#`` have a special use.
Instead of evaluating the value and discarding the expression,
a driver is added to the property with the expression entered.

The expression ``#frame`` is a quick way to map a value to the current frame,
but more complex expressions like ``#fmod(frame, 24) / 24`` are also supported.

This is simply a convenient shortcut to add drivers which can also be added via the :kbd:`RMB` menu.


Units
-----

As well as expressions, you can specify numbers and units.
If no unit is given, then a default unit is applied.
The unit system can be changed in :ref:`scene settings <bpy.types.UnitSettings>`.

You can use either the unit abbreviation or the full name after the value.

Examples of valid usage of length units include:

.. hlist::
   :columns: 2

   - ``1cm``
   - ``1m 3mm``
   - ``1m, 3mm``
   - ``2ft``
   - ``3ft/0.5km``
   - ``2.2mm + 5' / 3" - 2yards``

.. note:: Using Units

   - Decimal separator is optional.
   - You can mix units, e.g. metric and imperial even though you can only show one at a time.
   - Plurals of the names are recognized too, so ``meter`` and ``meters`` can both be used.


Color Fields
============

.. figure:: /images/interface_controls_buttons_fields_color.png
   :align: right
   :figwidth: 129px

   Color fields. With and without alpha.

The color field stores a color value.
Clicking on it with :kbd:`LMB` opens the :doc:`/interface/controls/templates/color_picker`.

Color fields with an alpha channel are divided in half: on the left, the color is shown without an alpha channel,
and on the right, it's shown with an alpha channel over a checker pattern.

Colors can be copied to other color fields by dragging and dropping.

Hovering over a color property will display a large swatch preview of the color
and the color's hexadecimal, RGBA, and HSVA values.


## Menus

.. _bpy.types.Menu:

*****
Menus
*****

Blender uses a variety of different menus for accessing options and :doc:`/interface/operators`.
Menus can be interacted with in the following ways:

Mouse selection
   :kbd:`LMB` on the desired item.
Numerical selection
   You can use the number keys or numpad to input an item in the list to select.
   For example, :kbd:`Numpad1` will select the first item and so on.

If a menu is too large to fit on the screen, a small
scrolling triangle appears on the top or bottom.
Scrolling is done by moving the mouse above or below this triangle.


.. rubric:: Shortcuts

- Use :kbd:`Wheel` while hovering with the mouse.
- Arrow keys can be used to navigate.
- Each menu item has an underlined character which can be pressed to activate it.
- Number keys or numpad can also be used to activate menu items.
  (:kbd:`1` for the first menu item, :kbd:`2` for the second etc.
  For larger menus, :kbd:`Alt-1` activates the 11th and so on, up to :kbd:`Alt-0` for the 20th.)
- Press :kbd:`Return` to activate the selected menu item.
- Press :kbd:`Esc` to close the menu without activating any menu item. This can also be
  done by moving the mouse cursor far away from the menu, or by :kbd:`LMB` clicking anywhere
  outside of it.


.. _bpy.types.UIPopupMenu:

Popup Menus
===========

.. figure:: /images/interface_controls_buttons_menus_menu-button.png
   :align: right

   Image menu in the Header of the Image editor.

Popup menus list :doc:`/interface/operators` which can be executed by selecting with :kbd:`LMB`
or using the generated shortcut indicated by the underlined character of the operator name.
All menu entries show any relevant shortcut keys, which can be executed without opening the menu.

.. _bpy.ops.wm.search_single_menu:

All popup menus can be searched by pressing :kbd:`Spacebar` and typing the name of the operator in the menu.
If a popup menu has "Search" as one of the items, the menu can be searched without having to press :kbd:`Spacebar`
first.

All popup menus of an editor can be searched using the :ref:`bpy.ops.wm.search_menu` feature.


Collapsing Menus
----------------

Sometimes it's helpful to gain some extra horizontal space in the header by collapsing menus.
This can be accessed from the header context menu:
click :kbd:`RMB` on the header and uncheck the *Show Menus checkbox*.

.. list-table::

   * - .. figure:: /images/interface_controls_buttons_menu_header_uncheck_show_menus_checkbox.png

          Right-click on any of the header menus.

     - .. figure:: /images/interface_controls_buttons_menus_header-menu-collapsed.png

          Access the menu from the collapsed icon.


Select Menus
============

.. figure:: /images/interface_controls_buttons_menus_select-menu.png
   :align: right
   :figwidth: 150px

   The 3D Viewport Mode Select menu.

A Select menu (or "selector" for short) lets you choose between a set of options.
It appears as an icon and/or text with a down arrow on the right side.
To use it, click the button with :kbd:`LMB` to show the available options,
then click the desired option (once selected, it'll appear inside the button).
You can also use :kbd:`Ctrl-Wheel` to cycle through the options without opening the menu.

.. container:: lead

   .. clear


.. _bpy.types.UIPopover:

Popover Menus
=============

.. figure:: /images/interface_controls_buttons_menus_popup-menu.png
   :align: right

   The Transform Orientations popover menu.

Popover menus are similar to Select Menus, but can show more varied content
such as a title, buttons, sliders, etc.


.. _bpy.ops.buttons.context_menu:
.. _bpy.ops.screen.region_context_menu:

Context Menu
============

Context menus are pop-ups that can be opened with :kbd:`RMB`.
In most editors, it's also possible to use the :kbd:`Menu` key.
The contents of the menu depend on the location of the mouse pointer.

When invoked in an editor, the menu contains a list of operators sensitive to the editor's mode.
When invoked over buttons and properties, common options include:

.. for the property associated with the control.

Single
   Apply the change to a single value of a set (e.g. only the X coordinate of an object's Location).
All
   Apply the change to all values in a set (e.g. all coordinates of an object's Location).

.. _bpy.ops.ui.reset_default_button:

Reset to Default Value(s) :kbd:`Backspace`
   Replaces the current value by the default.

.. _bpy.ops.ui.copy_data_path_button:

Copy Data Path :kbd:`Shift-Ctrl-C`
   Copies the Python property data path, relative to the data-block.
   Useful for Python scripting.

Copy Full Data Path :kbd:`Shift-Ctrl-Alt-C`
   Copies the full Python property data path including any needed context information.

Copy As New Driver
   Creates a new driver using this property as input, and copies it to the clipboard.
   Use *Paste Driver* to add the driver to a different property, or *Paste Driver Variables*
   to extend an existing driver with a new input variable.

Copy To Selected
   Copies the property value to the selected object's corresponding property.
   A use case is if the Properties context is pinned.

Assign Shortcut
   Lets you define a keyboard or mouse shortcut for an operation.
   To define the shortcut you must first move the mouse cursor over the button that pops up.
   When "Press a key" appears you must press and/or click the desired shortcut.
   Press :kbd:`Esc` to cancel.

   .. seealso::

      :doc:`/interface/keymap/introduction`.

Change Shortcut
   Lets you redefine the shortcut.

Remove Shortcut
   Unlinks the existing shortcut.

Online Manual :kbd:`F1`
   Opens an online page of the Blender Manual in a web browser.

Online Python Reference
   Context-sensitive access to
   the `Python API Reference <https://docs.blender.org/api/current/>`__.

Edit Source
   For UI development -- Creates a text data-block with the source code associated with the control,
   in case the control is based on a Python script.
   In the Text Editor it points at the code line where the element is defined.

Edit Translation
   For UI development -- Points at the translation code line.


.. |specials-button| image:: /images/interface_controls_buttons_menus_specials.png
.. _ui-specials-menu:

Specials Menu
=============

The Specials pop-up menu is similar to a context menu, but is opened
using a button consisting of a down arrow on a dark background |specials-button|.


.. _bpy.types.UIPieMenu:

Pie Menus
=========

A pie menu is a menu whose items are spread radially around the mouse.

.. figure:: /images/interface_controls_buttons_menus_pie-menu.png
   :align: center

   The 3D Viewport Mode Pie menu.

.. tip::

   The fastest way to operate a Pie menu is to press down the key(s) that
   invoke the menu, move the mouse slightly towards a selection, and
   release the key(s) to activate the selection.

Releasing the key without moving the mouse will keep the menu open so you
can click the desired item.
If you do move the mouse before releasing, the item closest to the mouse
will be activated instantly.

An open disc widget at the center of the pie menu shows
the current direction of the pie menu. The selected item is also highlighted.
A pie menu will only have a valid direction for item selection
if the mouse is touching or extending beyond the disc widget at the center of the menu.

Pie menu items support key accelerators, which are the letters underlined on each menu item.
Number keys can also be used.

If there are sub-pies available, it is indicated by a plus icon.

.. seealso::

   :ref:`Pie menu settings <prefs-pie-menu>`.


## Arranging


***************
Arranging Nodes
***************

Snapping
========

.. _bpy.types.ToolSettings.use_snap_node:

The snapping options can be found on the rightmost side
of the node editor's header.

Snap :kbd:`Shift-Tab`
   Toggle snapping on or off. You can also do this temporarily by holding :kbd:`Ctrl` after starting to drag
   one or more nodes around.

Snap Node Element :kbd:`Shift-Ctrl-Tab`
   What to snap the selected nodes to:

   :Grid: Snap to the grid in the background.
   :Node X: Snap to the X coordinate of another node's vertical border.
   :Node Y: Snap to the Y coordinate of another node's horizontal border.
   :Node X/Y: Combination of the above.

Snap Target
   Which part of the selected nodes to snap:

   :Closest: Snap closest point onto target.
   :Center: Snap center of selected nodes onto target.
   :Median: Snap median of selected nodes onto target.
   :Active: Snap active node onto target.


.. _editors-nodes-usage-auto-offset:

Auto-Offset
===========

When you drop a node with at least one input and one output socket onto an existing connection between two nodes,
*Auto-offset* will, depending on the direction setting, automatically move the left or right node away to make room
for the new node.
*Auto-offset* is a feature that helps organizing node layouts interactively without interrupting the user workflow.

.. figure:: /images/interface_controls_nodes_arranging_auto-offset.png

Auto-offset is enabled by default,
but it can be disabled in the :ref:`Preferences <preferences-editing-node-editor>`.

You can toggle the offset direction while you are moving the node by pressing :kbd:`T`.

The offset margin can be changed using the *Auto-offset Margin*
setting in the Editing section of the Preferences.

.. seealso:: Example Video:

   `Auto-Offset. A workflow enhancement for Blender's node editors <https://vimeo.com/135125839>`__.


## Editing


*******
Editing
*******

Transform
=========

.. reference::

   :Menu:      :menuselection:`Node --> Move, Rotate, Resize`
   :Shortcut:  :kbd:`G`, :kbd:`R`, :kbd:`S`

You can move the selected node(s) by simply clicking and dragging any empty part on them.
Alternatively, you can press :kbd:`G`, move the mouse, and click :kbd:`LMB` to confirm.

Dragging a node on top of an existing link will intelligently insert the selected node into the link path.
This generally works by using the first socket that matches the link type.
The automatic node attachment feature can be toggled with :kbd:`Alt`.
When a node is automatically attached the surrounding nodes
will be shifted to the right or left depending on the :kbd:`T` toggle;
see :ref:`editors-nodes-usage-auto-offset` for more information on this feature.

In general it is recommended to arrange your nodes within the view
such that the data flows from left to right, top to bottom.

The width of a node can be changed by dragging its left or right border.

Rotating (:kbd:`R`) and scaling (:kbd:`S`) only apply when you have multiple nodes selected
and only affect the nodes' positions.


Connecting Sockets
==================

:kbd:`LMB`-click on a socket and drag. You will see a line coming out of it: this is called a *link*.
Keep dragging and connect the link to an input socket of another node, then release the :kbd:`LMB`.

While multiple links can route out of an output socket, typically a single link can be attached to an input socket,
that is unless the input is a multi-socket input with looks like a pill shaped socket.

To swap multiple links of a similar type, press and hold :kbd:`Alt` while moving a link.
This feature also works when adding a new link into a pre-existing socket.

To reposition the outgoing links of a node, rather than adding a new one,
hold :kbd:`Ctrl` while dragging from an output socket.
This works for single as well as for multiple outgoing links.

Nodes that have no connections can be inserted on a link
by just move the node over the link and release when the link is highlighted.

.. _bpy.ops.node.link_make:

Make Links :kbd:`F`
   Select multiple nodes with open sockets, then use the Make Links to create links between them.
   Use Make Links again if there are other nodes which can be connected.

Make and Replace Links :kbd:`Shift-F`
   *Make and Replace Links* works similarly to *Make Links*, but it will replace existing links if any exist.


Disconnecting Sockets
=====================

Interactively
-------------

Drag the link away from its input socket and let it go, keeping it unconnected.


.. _bpy.ops.node.links_mute:

Mute Links
----------

.. reference::

   :Menu:      :menuselection:`Node --> Mute Links`
   :Shortcut:  :kbd:`Ctrl-Alt-RMB`

Activate the menu item or hold the key combination,
then draw a line across one or more links to mute/unmute them.
A muted link acts as though it's no longer there; this also means the input fields
for specifying fixed values become visible again.

When muting links on the input side of a :doc:`reroute node </interface/controls/nodes/reroute>`,
the links on its output side will be muted too.

.. figure:: /images/interface_controls_nodes_editing_mute_links.png


.. _bpy.ops.node.links_cut:

Cut Links
---------

.. reference::

   :Menu:      :menuselection:`Node --> Cut Links`
   :Shortcut:  :kbd:`Ctrl-RMB`

Activate the menu item or hold the key combination,
then draw a line across one or more links to delete them.

.. note::

   The key combination is normally reserved for :doc:`Lasso Select </interface/selecting>`.
   In node editors, lasso selection is instead performed with :kbd:`Ctrl-Alt-LMB`.


.. _bpy.ops.node.move_detach_links:

Detach Links :kbd:`Alt-LMB` drag
   Use Detach Links to cut all the links attached to the selected nodes
   and move the nodes to a new location.


.. _bpy.ops.node.clipboard_copy:
.. _bpy.ops.node.clipboard_paste:

Copy/Paste
==========

.. reference::

   :Menu:      :menuselection:`Node --> Copy`, :menuselection:`Node --> Paste`
   :Shortcut:  :kbd:`Ctrl-C`, :kbd:`Ctrl-V`

Not only the selected nodes but also the connections between them are copied to the clipboard.

.. note::

   The pasted node will be placed in the *same* position as when it was copied.
   Use the same cautions as when duplicating.


.. _bpy.ops.node.duplicate_move:

Duplicate
=========

.. reference::

   :Menu:      :menuselection:`Node --> Duplicate`
   :Shortcut:  :kbd:`Shift-D`

Select one or more nodes, activate the menu item or press the key combination,
then move the mouse to a new location and click :kbd:`LMB` (or press :kbd:`Return`)
to place the duplicated node(s).

.. note::

   When you duplicate a node, the new node will be positioned *exactly* on top of the node that was duplicated.
   If you leave it there (and it is quite easy to do so),
   you can **not** easily tell that there are *two* nodes there!
   When in doubt, select a node and move it slightly to see if something is hidden underneath.


.. _bpy.ops.node.duplicate_move_linked:

Duplicate Linked
================

.. reference::

   :Menu:      :menuselection:`Node --> Duplicate Linked`
   :Shortcut:  :kbd:`Alt-D`

Duplicate selected nodes, but not their node trees (in the case of group nodes), and move them.


.. _bpy.ops.node.delete:

Delete
======

Delete :kbd:`X`, :kbd:`Delete`
   Deletes the selected node(s).

.. _bpy.ops.node.delete_reconnect:

Delete with Reconnect :kbd:`Ctrl-X`
   Deletes the selected node(s), then creates new links connecting their former input nodes
   to their former output nodes.


.. _bpy.ops.node.mute_toggle:

Mute
====

.. reference::

   :Menu:      :menuselection:`Node --> Toggle Node Mute`
   :Shortcut:  :kbd:`M`

Muting a node removes its contribution to the node tree,
and makes all links pass through it without change.
Links will appear red as an indicator of passing through the muted node.

.. tip::

   Individual node links can be muted with :ref:`bpy.ops.node.links_mute`.


Show/Hide
=========

.. _bpy.ops.node.hide_toggle:

Hide :kbd:`H`
   Collapses the node so only the node header is visible.
   This can also be toggled by clicking the triangle on the left of the node header.

.. _bpy.ops.node.preview_toggle:

Toggle Node Preview :kbd:`Shift-H`
   Shows/Hides a preview region on the node that displays the frame
   after that node's operation has been applied. This can also be toggled
   by clicking the material ball icon in the node header.

   .. note:: This operator are only available in the :doc:`Compositor </compositing/index>`.

.. _bpy.ops.node.hide_socket_toggle:

Toggle Hidden Node Sockets :kbd:`Ctrl-H`
   Collapses/Expands any input or output sockets that have no other nodes connected to them.

.. _bpy.ops.node.options_toggle:

Toggle Node Options
   Shows/Hides all node properties.

.. _bpy.ops.node.collapse_hide_unused_toggle:

Collapse and Hide Unused Sockets
   Applies both the *Toggle Hidden Node Sockets* and *Hide* operations.


.. _bpy.ops.node.read_viewlayers:

Layers
======

Read Render Layers :kbd:`Ctrl-R`
   Reads all the current scene's render layers from cache, as needed.
   This can be used to save RAM while rendering because the render layers do not have to be saved in RAM.
   And also for recovering some information from a failed render.
   For this to work, :ref:`Cache Result <bpy.types.RenderSettings.use_render_cache>` must be enabled.

   .. note:: This operator are only available in the :doc:`Compositor </compositing/index>`.


## Frame

.. _bpy.types.NodeFrame:

**********
Frame Node
**********

The Frame node is useful for organizing nodes by collecting related nodes together in a common area.
Frames are useful when a node setup becomes large and confusing yet the re-usability of a Node Group is not required.

.. figure:: /images/interface_controls_nodes_frame_example.png


Properties
==========

.. figure:: /images/interface_controls_nodes_frame_properties.png
   :align: right

Label Size
   Font size of the label. For example, for subordinate frames to have smaller titles.
Shrink
   Once a node is placed in the Frame, the Frame shrinks around it so as to remove wasted space.
   At this point it is no longer possible to select the edge of the Frame to resize it, instead resizing occurs
   automatically when nodes within the Frame are rearranged.
   This behavior can be changed by disabling this option.
Text
   When you need to display more comprehensive text, frame nodes can display the contents of a text data-block.
   This is read-only, so you will need to use the *Text Editor* to modify the contents.


Editing
=======

.. _bpy.ops.node.join:

Join in New Frame
-----------------

.. reference::

   :Menu:      :menuselection:`Node --> Join in new Frame`
   :Shortcut:  :kbd:`Ctrl-J`

Make a new frame including the selected nodes.


.. _bpy.ops.node.parent_set:

Add to Frame
------------

.. reference::

   :Shortcut:  :kbd:`Ctrl-P`

Once a frame node is placed, nodes can be added by dropping them onto the frame or
by selecting the node(s) then the frame and using :kbd:`Ctrl-P`.
This can be thought of as Parenting the selection to the frame.


.. _bpy.ops.node.detach:

Remove from Frame
-----------------

.. reference::

   :Menu:      :menuselection:`Node --> Remove from Frame`
   :Shortcut:  :kbd:`Alt-P`

To remove nodes from a frame, select and use :kbd:`Alt-P`.
This can be thought of as unparenting the selection from the frame.


## Groups

.. _bpy.types.NodeGroup:

***********
Node Groups
***********

.. figure:: /images/interface_controls_nodes_groups_example.png
   :align: right

   Example of a node group.

Grouping nodes can simplify a node tree by hiding away complexity and reusing repetitive parts.

Conceptually, node groups allow you to treat a *set* of nodes as though it were just one node.
They're similar to functions in programming:
they can be reused (even in different node trees) and can be customized by changing their "parameters."

As an example, say you created a "Wood" material that you would like to have in different colors.
One way of doing this would be to duplicate the entire material for every color, but if you did that,
you'd have to go over all those copies again if you later wanted to change the density of the grain lines.
Instead, it would be better to move the nodes that define the wood look into a node group.
Each material can then reuse this node group and just supply it with a color.
If you then later want to change the grain line density, you only have to do it once inside the node group,
rather than for every material.

Node groups can be nested (that is, node groups can contain other node groups).

.. note::

   Recursive node groups are prohibited for all the current node systems to prevent infinite recursion.
   A node group can never contain itself (or another group that contains it).

.. tip::

   Like all data-blocks, node groups with names that start with ``.`` are normally hidden from
   :ref:`lists and menus <ui-data-block>` and can only be accessed through search.
   This can be useful for node asset authors to hide their internal sub-groups from the final user.

When a node group is created, new *Group Input* and *Group Output* nodes are generated
to represent the data flow into and out of the group. Furthermore connections to input sockets coming
from unselected nodes will become attached to new sockets on the *Group Input* node.
Similarly, outgoing connections to input sockets of unselected nodes will become attached to
the new *Group Output* node.

If you want to pass an additional parameter into the group,
a socket must be added to the *Group Input* node.
To do this, drag a connection from the hollow socket on the right side of the *Group Input* node
to the desired input socket on the node requiring an input.
The process is similar for the *Group Output* regarding data
you want to be made available outside the group.


Properties
==========

Group
-----

.. reference::

   :Panel:     :menuselection:`Sidebar --> Group --> Group`

.. figure:: /images/interface_controls_nodes_groups_interface-group-panel.png
   :align: right

   The *Group* panel.

This panel contains properties that relate the group node such as it's name and look.

Name
   The name of node as displayed in the :ref:`interface-nodes-parts-title`.

.. _bpy.types.NodeTree.description:

Description
   The message displayed when hovering over the :ref:`interface-nodes-parts-title` or in add menus.

.. _bpy.types.NodeTree.color_tag:

Color Tag
   Color tag of the node group which influences the header color.


Usage :guilabel:`Geometry Nodes`
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This panel is only visible in the :doc:`Geometry Node Editor </editors/geometry_node>`.

.. _bpy.types.GeometryNodeTree.is_modifier:

Modifier
   The node group is used as a :doc:`/modeling/modifiers/generate/geometry_nodes`.

.. _bpy.types.GeometryNodeTree.is_tool:

Tool
   The node group is used as a :doc:`/modeling/geometry_nodes/tools`.


.. _bpy.ops.node.tree_socket_add:
.. _bpy.ops.node.tree_socket_remove:
.. _bpy.ops.node.tree_socket_move:

Group Sockets
-------------

.. reference::

   :Panel:     :menuselection:`Sidebar --> Group --> Group Sockets`

.. figure:: /images/interface_controls_nodes_groups_interface-group_sockets_panel.png
   :align: right

   The *Group Sockets* panel.

This panel is used to add, remove, reorder, and edit the sockets of the group's input and output.

.. _bpy.types.NodeTreeInterfaceSocket.name:

Socket List
   A :ref:`ui-list-view` of all inputs, outputs and panels.

   Here you can name the socket which is displayed in the node's interface.

.. _bpy.types.NodeTreeInterfaceSocket.description:

Description
   The message displayed when hovering over socket properties.

.. _bpy.types.NodeTreeInterfacePanel.default_closed:

Closed by Default :guilabel:`Panels`
   Panel is closed by default on new nodes.

.. _bpy.types.NodeTreeInterfaceSocket*.default_value:

Default
   The value to use when nothing is connected to the socket.

.. _bpy.types.NodeTreeInterfaceSocket*.min_value:
.. _bpy.types.NodeTreeInterfaceSocket*.max_value:

Min, Max
   The minimum and maximum value for the UI button shown in the node interface.
   Note, this is not a minimum or maximum for the data that can pass through the node.
   If a socket passes a higher value than the maximum, it will still pass into the node unchanged.

.. rubric:: Geometry Nodes

.. _bpy.types.NodeTreeInterfaceSocket.default_input:

Default Input
   Input to use when the socket is unconnected.
   Requires *Hide Value* to be enabled.

.. _bpy.types.NodeTreeInterfaceSocket.hide_value:

Hide Value
   Hide the socket value even when the socket is not connected.

.. _bpy.types.NodeTreeInterfaceSocket.hide_in_modifier:

Hide in Modifier
   Don't show the input value in the geometry nodes modifier interface.
   This allows the input to be used in the context of a node group but not as a modifier input.

   This option is only available for geometry nodes and only for input sockets.

.. _bpy.types.NodeTreeInterfaceSocket.force_non_field:

Single Value
   Only allow single value inputs rather than :doc:`/modeling/geometry_nodes/fields`.


.. _bpy.ops.node.group_make:

Make Group
==========

.. reference::

   :Menu:      :menuselection:`Node --> Make Group`
   :Shortcut:  :kbd:`Ctrl-G`

To create a node group, select the nodes you want to include, then
press :kbd:`Ctrl-G` or click :menuselection:`Group --> Make Group`.
A node group will have a green title bar. All selected nodes will now be contained within the node group.
Default naming for the node group is "NodeGroup", "NodeGroup.001" etc.
There is a name field in the node group you can click into to change the name of the group.
Change the name of the node group to something meaningful.

When appending node groups from one blend-file to another,
Blender does not make a distinction between material node groups or composite node groups.
So it is recommended to use some naming convention that will allow you to distinguish between the two types.

.. tip::

   The "Add" menu of each node editor contains an "Output" category with node types such as "Material Output."
   These node types should not be confused with the "Group Output" node found in node groups,
   and should not be used in node groups either (only in the top-level node tree).


.. _bpy.ops.node.group_insert:

Insert Into Group
=================

.. reference::

   :Menu:      :menuselection:`Node --> Insert Into Group`

Moves the selected nodes into the :term:`active <Active>` group node.
To use, select a set of nodes, ending with the destination group node,
then, running the operation will move those nodes into that group.
The moved nodes are collected into a group of their own to preserve their connection context,
having their own group input and output nodes.
The group's existing input and output nodes are updated with new sockets, if any, from the new nodes.
The node group must be edited to contain a single *Group Input* and a single *Group Output* node.


.. _bpy.ops.node.tree_path_parent:
.. _bpy.ops.node.group_edit:

Edit Group
==========

.. reference::

   :Menu:      :menuselection:`Node --> Edit Group`
   :Header:    :menuselection:`Go to Parent Node Tree`
   :Shortcut:  :kbd:`Tab`, :kbd:`Ctrl-Tab`

With a node group selected, press :kbd:`Tab` to move into it and see its content.
Press :kbd:`Tab` again (or :kbd:`Ctrl-Tab`) to leave the group and go back to
its parent, which could be the top-level node tree or another node group.
You can refer to the breadcrumbs in the top left corner of the node editor
to see where you are in the hierarchy.

.. figure:: /images/render_cycles_optimizations_reducing-noise_glass-group.png
   :width: 620px

   Example of an expanded node group.


.. _bpy.ops.node.group_ungroup:

Ungroup
=======

.. reference::

   :Menu:      :menuselection:`Node --> Ungroup`
   :Shortcut:  :kbd:`Ctrl-Alt-G`

Removes the group and places the individual nodes into your editor workspace.
No internal connections are lost, and now you can link internal nodes to other nodes in your workspace.

Separate :kbd:`P`
   Separate selected nodes from the node group.

   Copy
      Copy to parent node tree, keep group intact.
   Move
      Move to parent node tree, remove from group.


Reusing Node Groups
===================

.. reference::

   :Menu:      :menuselection:`Add --> Group`
   :Shortcut:  :kbd:`Shift-A`

Existing node groups can be placed again after they're initially defined, be it in the same
node tree or a different one. It's also possible to import node groups from a different blend-file
using :menuselection:`File --> Link/Append`.


## Index

.. _bpy.types.Nodes:
.. _bpy.types.Node:
.. _bpy.ops.node:

#########
  Nodes
#########

.. toctree::
   :maxdepth: 2

   introduction.rst
   parts.rst
   selecting.rst
   arranging.rst
   editing.rst
   sidebar.rst
   groups.rst
   frame.rst
   reroute.rst


## Introduction

.. index:: Nodes

************
Introduction
************

Blender contains different node-based editors with different purposes,
so this section only explains how to work with nodes in general.
The list below shows the different types of nodes and where they're documented.

.. figure:: /images/interface_controls_nodes_introduction_example.jpg

   Example of a node editor.

.. _tab-node-tree-types:

.. list-table::
   :header-rows: 1
   :class: valign
   :widths: 10 30 60

   * - Icon
     - Name
     - Description
   * - .. figure:: /images/interface_controls_nodes_introduction_icons-geometry.png
     - :doc:`Geometry Nodes </modeling/geometry_nodes/index>`
     - Used for procedural modeling.
   * - .. figure:: /images/interface_controls_nodes_introduction_icons-material.png
     - :doc:`Shader Nodes </render/shader_nodes/index>`
     - Used to create materials for objects.
   * - .. figure:: /images/interface_controls_nodes_introduction_icons-render-layers.png
     - :doc:`Composite Nodes </compositing/index>`
     - Used to edit rendered images.
   * - .. figure:: /images/interface_controls_nodes_introduction_icons-texture.png
     - :doc:`Texture Nodes </editors/texture_node/introduction>`
     - Used to create custom textures.


Editor Interface
================

Header
------

The *Header* contains various menus, buttons and options, partially based on the current node tree type.

.. figure:: /images/interface_controls_nodes_introduction_header.png

   Common node editor header options.

View
   This menu changes your view of the editor.
Select
   This menu allows you to select a node or groups of nodes.
Add
   This menu allows you to add nodes.
Node
   This menu allows you to do things with selected nodes.
Use Nodes
   Tells the render engine to use the node tree when computing the material color or rendering the final image,
   or not. If not, the tree is ignored. For materials, this is mostly a legacy option, because in the past
   materials could not be created with node trees.
Pin
   When enabled, the editor will retain the material or texture, even when the user selects a different object.
   A node tree can then be edited independent of the object selection in the 3D Viewport.
Parent Node Tree
   Leaves the current :doc:`node group </interface/controls/nodes/groups>` and returns to the parent node group/tree.
Snapping
   Change options for snapping node positions to achieve a cleaner node tree layout.
   See :doc:`/interface/controls/nodes/arranging`.


.. _bpy.types.SpaceNodeOverlay.show_overlays:

Overlays
^^^^^^^^

Overlays are information that is displayed on top of the nodes and node trees.
There is a toggle to show or hide all overlays for the node editor next to the overlay popover.

.. _bpy.types.SpaceNodeOverlay.show_wire_color:

Wire Colors
   Color node links based on their connected sockets.

.. _bpy.types.SpaceNodeOverlay.show_reroute_auto_labels:

Reroute Auto Labels
   Label :doc:`Reroute Nodes </interface/controls/nodes/reroute>`
   based on the label of connected reroute nodes.

.. _bpy.types.SpaceNodeOverlay.show_context_path:

Context Path
   Display breadcrumbs in the upper left corner indicating the hierarchy location
   of the node tree/group that's currently being displayed.

.. _bpy.types.SpaceNodeEditor.show_annotation:

Annotations
   Displays :doc:`Annotations </interface/annotate_tool>` in the preview region.

.. _bpy.types.SpaceNodeOverlay.show_previews:

Previews
   Display each node's :ref:`interface-nodes-parts-preview` if the node's preview is also toggled.

.. _bpy.types.SpaceNodeOverlay.show_timing:

Timings
   Display each node's last execution time.
   This option is only available for compositing and geometry nodes.

   In the context of geometry nodes, see :ref:`modeling-geometry_nodes-inspection-timings`.


Toolbar
-------

The *Toolbar* contains a set of tools that can be used in the node editor.


Sidebar
-------

The :doc:`Sidebar </interface/controls/nodes/sidebar>` region contains properties for
the currently selected node as well as node editor-specific settings.


Navigating
==========

Navigating the node editors is done with the use of both mouse movement and keyboard shortcuts.

Pan :kbd:`MMB`
   Move the view up, down, left and right.
Zoom :kbd:`Ctrl-MMB`, :kbd:`Wheel`
   Move the camera forwards and backwards.
Frame Selected :kbd:`NumpadPeriod`
   Adjusts the zooms to fit only the selected nodes in the view.
Frame All :kbd:`Home`
   Adjusts the zoom to fit all nodes in the view.


Adding Nodes
============

.. reference::

   :Menu:      :menuselection:`Add`
   :Shortcut:  :kbd:`Shift-A`

Nodes are added via the *Add* menu in the editor's header or using a keyboard shortcut.

Nodes can also be added by dragging a connection from an existing node's input or output socket
and dropping the connection above an empty space instead of connecting to another socket.
This action will open a search menu with a list of compatible nodes
and their sockets that can be added and connected to the existing node.
Confirming the menu selection will add the node which can then be moved and placed.


## Parts

.. _bpy.types.NodeSocket:
.. _bpy.types.NodeTree:

**********
Node Parts
**********

All nodes in Blender are based on a similar construction.
This applies to :ref:`any type of node <tab-node-tree-types>`.
These parts include the title, sockets, properties and more.

.. figure:: /images/interface_controls_nodes_parts_overview.png


.. _interface-nodes-parts-title:

Title
=====

The title shows the name/type of the node;
it can be overridden by changing the node's :ref:`Label <bpy.types.Node.label>`.
On the left side of the title is the *collapse* toggle
which can be used to collapse the node. This can also be done with :kbd:`H`.

.. figure:: /images/interface_controls_nodes_parts_collapsed.png

   How a node appears when collapsed.


.. _interface-nodes-parts-preview:

Preview
-------

Previews are an overlay that shows a small image above the node displaying the node result.
Not all nodes support previews, but the ones that do can be toggled using
the icon in the top right-hand corner of the node next to the title.

Previews can be disabled for the whole node tree by using
:ref:`Previews <bpy.types.SpaceNodeOverlay.show_previews>` overlay toggle.

.. figure:: /images/interface_controls_nodes_parts_previewless.png

   Preview toggle button.


.. _bpy.types.NodeLink:

Sockets
=======

Sockets are input and output values for the node.
They appear as little colored circles on either side of the node.
Unused sockets can be hidden with :kbd:`Ctrl-H`.

Each socket is color-coded depending on what type of data it handles.

.. figure:: /images/interface_controls_nodes_parts_sockets.png

.. rubric:: Built-in

Shader (bright green)
   Used for shaders in :doc:`Cycles </render/cycles/index>` and :doc:`EEVEE </render/eevee/index>`.
Geometry (turquoise)
   Used in :doc:`Geometry Nodes </modeling/geometry_nodes/index>`.

.. rubric:: Data

Boolean (pink)
   Used to pass a true or false value.
Color (yellow)
   Indicates that the socket accepts/produces color information.
   The colors may or may not have an alpha component depending on the node tree type.
Float (gray)
   Indicates that the socket accepts/produces floating-point numbers.
   It can either be a single value or a so-called "value map".
   (You can think of a value map as a grayscale image where the brightness of a pixel represents its value.)
   If a single value is used as an input for a "value map" socket, all points of the map are set to this same value.
Integer (lime green)
   Used to pass an integer value (a number without a fractional component).
String (light blue)
   Used to pass a text value.
Vector (dark blue)
   Indicates vector, coordinate and normal information.

.. rubric:: Data-Blocks

Collection (white)
   Used to pass a collection data-block.
Object (orange)
   Used to pass an object data-block.
Material (salmon)
   Used to pass a material data-block.
Texture (pink)
   Used to pass a texture data-block.
Image (apricot)
   Used to pass an image data-block.


Inputs
------

The inputs are located on the bottom left side of the node,
and provide the data the node needs to perform its function.
Each input socket, except for the green shader input, when disconnected,
has a default value which can be edited via a color, numeric, or vector interface input.
In the screenshot of the node above, the second color option is set by a color interface input.

Some nodes have special sockets that can accept multiple inputs.
These sockets will have an ellipsis shape rather than a circle to indicate their special behavior.


Outputs
-------

The outputs are located on the top right side of the node,
and can be connected to the input of nodes further down the node tree.


Conversion
----------

Some socket types can be converted to others either implicitly or explicitly.
Implicit conversion happens automatically without the need of a conversion node.
For example, Float sockets and Color sockets can be linked to each other.

Once a socket conversion is made, data may be lost and cannot be retrieved later down the node tree.
Implicit socket conversion can sometimes change the data units as well.
When plugging a *Value* input node into an angle socket, it'll default to use radians
regardless of the scene's :ref:`bpy.types.UnitSettings`.
This happens because the Value node has no unit while the angle input does.

Valid conversions:

- Between color and vector -- mapping between color channels and vector components.
- Between color and float -- the color data is converted to its grayscale equivalent.
- Color/float/vector to Shader -- implicitly converts to color and gives the result of using an Emission node.
- Between float and integer -- integers simply become floats, floats are truncated.
- Between float and vector --  when a float becomes a vector the value is used for each component.
  When a vector becomes a float the average of the components is taken.
- Between float and boolean -- values greater than 0 are true, true maps to 1, and false maps to 0.

Explicit conversion requires the use of a conversion node such as
the :doc:`/render/shader_nodes/converter/shader_to_rgb` node
or the :doc:`/render/shader_nodes/converter/rgb_to_bw` node.
The :doc:`/render/shader_nodes/converter/math` node also contains
some functions to convert between degrees and radians.


.. _bpy.types.NodeSetting:

Properties
==========

Many nodes have settings which can affect the way they interact with inputs and outputs.
Node settings are located below the outputs and above any inputs.

.. figure:: /images/interface_controls_nodes_parts_controls.png

   An example of the controls on the Chroma Key node.


## Reroute


************
Reroute Node
************

A node used primarily for organization.
Reroute looks and behaves much like a socket on other nodes in that it supports one input
connection while allowing multiple output connections.

To quickly add a Reroute node into an existing connection, hold :kbd:`Shift` and :kbd:`RMB`
while sweeping across the link to add a *Reroute node*.

.. figure:: /images/interface_controls_nodes_reroute_node.png


Properties
==========

Input
   Input value used for unconnected sockets.


## Selecting


*********
Selecting
*********

Box Select
   Drag with :kbd:`LMB` to box-select multiple nodes.
   Alternatively, :kbd:`B` starts the bounding box selection process as well.
Lasso Select
   Drag with :kbd:`Ctrl-Alt-LMB` to perform a lasso selection. Note that this is different
   from the :kbd:`Ctrl-RMB` used in other editors.
Select All :kbd:`A`
   Select all nodes.
Deselect All :kbd:`Alt-A`
   Deselect all nodes.
Invert :kbd:`Ctrl-I`
   Invert the selection.
Select Linked From :kbd:`L`
   Expand the selection to nodes which are linked to the inputs of the currently selected nodes.
Select Linked To :kbd:`Shift-L`
   Expand the selection to nodes which are linked to the outputs of the currently selected nodes.
Select Grouped :kbd:`Shift-G`
   Selects nodes that have similar :doc:`properties </interface/controls/nodes/sidebar>`
   as the active node.

   Type
      The node type, e.g. all Math nodes.
   Color
      The node color. (Nodes can be given a custom color to visually organize them in the editor;
      this is not related to any color information they might consume or produce as part of their function.
      The color can be set in the :doc:`Sidebar </interface/controls/nodes/sidebar>`.)
   Prefix, Suffix
      Matches the name property from start/end of the text.
Activate Same Type Previous/Next :kbd:`Shift-]`/:kbd:`Shift-[`
   Finds the previous/next node of same type, activates it, and ensures it's visible.
Find Node :kbd:`Ctrl-F`
   Shows a search pop-up for finding a node by name.

Select Multiple :kbd:`Shift-LMB`
   Add/remove a node to/from the selection.


## Sidebar


*******
Sidebar
*******

Node
====

.. reference::

   :Panel:     :menuselection:`Sidebar --> Node`

.. figure:: /images/interface_controls_nodes_sidebar_item.png
   :align: center

   Node tab with a compositing Render Layers node selected.


Node
----

.. _bpy.types.Node.name:

Name
   A unique node identifier inside this node tree.

.. _bpy.types.Node.label:

Label
   Nodes can be given a title by modifying the text field.


.. _bpy.types.Node.use_custom_color:

Color
^^^^^

By default, the node's background color is defined by the user theme.
This color can be overridden by selecting a custom color in this panel.
Custom node colors can be used to provide a visual cue to help distinguish some nodes from others.
The button to the right of the checkbox lets you save colors as presets
for reusing later on (much like a palette).

.. _bpy.types.Node.color:

Color
   Color of the node background.

   Node Color Specials
      This menu contains :doc:`/interface/operators` for working with nodes with custom colors.

      .. _bpy.ops.node.node_copy_color:

      Copy Color
         Copies the color of the :term:`Active` node and applies it to all selected nodes.


Properties
----------

The properties that are shown depend on the type of node selected,
e.g. a Mix node has different properties than a Mask node.


Tool
====

.. reference::

   :Panel:     :menuselection:`Sidebar region --> Tool`


Active Tool
-----------

The info in this panel changes with the selected tool.


View
====

.. reference::

   :Panel:     :menuselection:`Sidebar region --> View`


Annotations
-----------

You can select the Annotate tool in the Toolbar to make annotations in the node editor.
See :doc:`Annotate Tool </interface/annotate_tool>` for more info.


## Color Palette

.. _bpy.ops.palette:
.. _bpy.types.PaletteColor:

*************
Color Palette
*************

.. figure:: /images/interface_controls_templates_color-palette_ui.png
   :align: right

   Color Palette.

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

.. _bpy.types.PaletteColor.color:

Color List
   Each color that belongs to the palette is presented in a list.
   Clicking on a color will change the brush's primary *Color* to that color.


Shortcuts
=========

- :kbd:`Ctrl-LMB` open the color picker to change color. See :ref:`ui-color-picker`.
- :kbd:`Backspace` reset the value.


## Color Picker

.. _ui-color-picker:

************
Color Picker
************

.. figure:: /images/interface_controls_templates_color-picker_circle-hsv.png
   :align: right

   Circle HSV.

The color picker is a pop-up that lets you define a color value.
Holding :kbd:`Ctrl` while dragging snaps the hue to make it quick to select primary colors.

Color Field
   Lets you pick the first and second color component. The shape can be changed; see `Types`_.

Color Slider
   The slider with a gradient in the background lets you define the third color component.
   It can also be controlled with the :kbd:`Wheel`.

Color Model
   Selects the :term:`Color Model` for the number fields below.

   RGB, HSV/HSL, Hex

   .. note::

      In Blender, the RGB and HSV/HSL values are in Scene Linear color space,
      and are therefore not :term:`Gamma` corrected.
      On the contrary, *Hex* are automatically :term:`Gamma` corrected
      for the :term:`sRGB Color Space <Color Space>`.
      For more information, see :doc:`Color Management </render/color_management>`.

Color Values
   Blender uses values from 0 to 1 to express colors for RGB and HSV colors.

   Hexadecimal (Hex) values are expressed as ``RRGGBB``.
   Shorthand hex colors are also supported as ``RGB``,
   e.g. dark yellow ``FFCC00`` can be written as ``FC0``.

   For operations that are capable of using the :term:`Alpha Channel`, another slider "A" is added.

.. _bpy.ops.ui.eyedropper_color:

Eyedropper (pipette icon)
   Samples a color from inside the Blender window using the :ref:`ui-eyedropper`.


Shortcuts
=========

- :kbd:`Ctrl-LMB` (drag) snaps to hue.
- :kbd:`Shift-LMB` (drag) precision motion.
- :kbd:`Wheel` adjust the brightness.
- :kbd:`Backspace` reset the value.


Types
=====

The default color picker type can be selected in the Preferences,
see: :ref:`Interface <bpy.types.PreferencesView.color_picker_type>`.

.. list-table:: Color Picker types.

   * - .. figure:: /images/interface_controls_templates_color-picker_circle-hsv.png

          Circle HSV.

     - .. figure:: /images/interface_controls_templates_color-picker_circle-hsl.png

          Circle HSL.

     - ..

   * - .. figure:: /images/interface_controls_templates_color-picker_square-sv-h.png

          Square (SV + H).

     - .. figure:: /images/interface_controls_templates_color-picker_square-hs-v.png

          Square (HS + V).

     - .. figure:: /images/interface_controls_templates_color-picker_square-hv-s.png

          Square (HV + S).


## Color Ramp

.. _ui-color-ramp-widget:
.. _bpy.types.ColorRamp:

*****************
Color Ramp Widget
*****************

*Color Ramps* specify a color gradient based on color stops. Each stop has a position and a color.
The gradient is then calculated as the interpolation between these stops using the chosen
interpolation method.

.. figure:: /images/interface_controls_templates_color-ramp_ui.png

   Color ramp.


Controls
========

Add ``+``
   Adds a new stop between the selected stop and the one before it.

Delete ``-``
   Deletes the selected color stop.

Specials ``v``
   Contains more operators for the color ramp.

   Flip Color Ramp
      Flips the gradient, mirroring the positions of the stops.
   Distribute Stops from Left
      Distribute the stops so that every step has the same space to the right.
      This is mostly useful when used with Constant interpolation mode.
   Distribute Stops Evenly
      Distribute the stops so that all neighbors have the same space between them.
   Eyedropper (pipette icon) :kbd:`E`
      An :ref:`ui-eyedropper` to sample a color or gradient from the interface to be used in the color ramp.
   Reset Color Ramp
      Resets the color ramp to its default state.

.. _bpy.types.ColorRamp.color_mode:

Color Mode
   Selection of the :term:`Color Model` used for interpolation.

   :RGB:
      Blends color by mixing each color channel and combining.
   :HSV/HSL:
      Blends colors by first converting to HSV or HSL, mixing, then combining again.
      This has the advantage of maintaining saturation between different hues,
      where RGB would de-saturate. This allows for a richer gradient.

.. _bpy.types.ColorRamp.hue_interpolation:
.. _bpy.types.ColorRamp.interpolation:

Color Interpolation
   The interpolation method to use across the ramp.

   RGB
      :B-Spline: Uses a B-spline interpolation for the color stops.
      :Cardinal: Uses a cardinal interpolation for the color stops.
      :Linear: Uses a linear interpolation for the color stops.
      :Ease: Uses an ease interpolation for the color stops.
      :Constant: Uses a constant interpolation for the color stops.

   HSV/HSL
      :Clockwise: Clockwise interpolation around the HSV/HSL wheel.
      :Counter-Clockwise: Counterclockwise around the HSV/HSL wheel.
      :Near: Nearest route around the wheel.
      :Far: Furthest route around the wheel.

      .. figure:: /images/interface_controls_templates_color-ramp_interpolation.png
         :width: 600px

         HSV and HSL interpolation options.

Active Color Stop
   Index of the active color stop (shown as a dashed line).
   Offers an alternative way of selecting a stop in case it's so close to others
   that it's hard to select it directly.

.. _bpy.types.ColorRampElement.position:

Position
   This slider controls the position of the selected color stop in the range.

.. _bpy.types.ColorRampElement.color:

Color
   A :doc:`color field </interface/controls/buttons/fields>` where you can
   specify the color and alpha of the selected stop.


Shortcuts
---------

- :kbd:`LMB` (drag) moves color stops.
- :kbd:`Ctrl-LMB` (click) adds a new color stop.


## Curve

.. _ui-curve-widget:

************
Curve Widget
************

.. figure:: /images/interface_controls_templates_curve_ui.png
   :align: right

   Curve widget.

The *Curve Widget* allows to intuitively map a range of input values to a set of output values
by adjusting a curve, where the X axis represents the input and the Y axis the output.


Control Points
==============

Like all curves in Blender, the curve of the *Curve Widget* is controlled using *control points*.

By default, there are two control points: one at (0.0, 0.0) and one at (1.0, 1.0),
meaning the input is mapped directly to the output (unchanged).

Move
   Simply click and drag it around.
Add
   Click anywhere on the curve where there is not already a control point.
Remove
   Select it and click the ``X`` button at the bottom right.


Controls
========

Above the curve graph is a row of controls. These are:

Zoom In (plus magnifying glass icon)
   Zoom into the center of the graph to show more details and provide more accurate control.
   To navigate around the curve while zoomed in, click and drag in an empty part of the graph.
Zoom Out (minus magnifying glass icon)
   Zoom out of the graph to show fewer details and view the graph as a whole.
   You cannot zoom out further than the clipping region (see *Clipping* below).

Specials ``v``
   A :ref:`Specials <ui-specials-menu>` menu with operators to edit control points or to set properties.

   Reset View
      Resets the view of the curve.

   Extend Options
      Controls how the curve is extended before the first control point and after the last control point.

      Extend Horizontal
         Causes the curve to stay horizontal before the first point and after the last point.
      Extend Extrapolated
         Causes the curve to extrapolate before the first point and after the last point,
         based on the shape of the curve.

      .. list-table::

         * - .. figure:: /images/interface_controls_templates_curve_extend-horizontal.png

                Extend Horizontal.

           - .. figure:: /images/interface_controls_templates_curve_extend-extrapolate.png

                Extend Extrapolated.

   Reset Curve
      Resets the curve to default (removes all points added to the curve).
Clipping Options (dot icon)
   Use Clipping
      Forces curve points to stay between specified values.
   Min X/Y and Max X/Y
      Set the minimum and maximum bounds of the curve points.

Below the curve are options for the selected control point:

Handle Type
   Controls how the control points affect the curve shape.
   It determines the interpolation of the curve segment at the selected control point.

   :Vector Handle:
      Vector handles create straight lines and sharp corners.
   :Auto Handle:
      Automatic handles that create smooth curves.
   :Auto-Clamped Handle:
      Automatic handles that create smooth curves while also preventing overshoot.
   :Free Handle:
      The handles can be moved completely independently, and thus can result in a sharp change of direction.
   :Aligned Free Handles:
      The two handles of the curve point are locked together to always point in exactly opposite directions.
      This results in a curve that is always smooth at the control point.

   .. list-table::

      * - .. figure:: /images/interface_controls_templates_curve_handle-vector.png

             Vector Handles.

        - .. figure:: /images/interface_controls_templates_curve_handle-auto.png

             Auto Handles.

        - .. figure:: /images/interface_controls_templates_curve_handle-auto-clamped.png

             Auto Clamped Handles.
X, Y
   The coordinates of the selected control point.
Delete ``X``
   Remove the selected control point. The first and last points cannot be deleted.
Copy/Paste :kbd:`Ctrl-C`, :kbd:`Ctrl-V`
   The whole curve can be copied from one Curve Widget to another by hovering over
   the curve graph and pressing :kbd:`Ctrl-C`, :kbd:`Ctrl-V`.


## Data Block

.. _ui-data-block:

***************
Data-Block Menu
***************

Lets you select a :doc:`Data-Block </files/data_blocks>` (such as a material)
in order to link it to something else (such as an object).

.. figure:: /images/interface_controls_templates_data-block_menu.png
   :align: right

   A data-block menu with a search field.

Type
   Shows an icon indicating the data-block type. Clicking the image or the down arrow opens the popup menu.
   Dragging the image lets you apply the data-block to something else. (For example, you can drag a
   material onto an object in the 3D Viewport to :doc:`assign </render/materials/assignment>` it.
   Dragging onto :ref:`ui-data-id` fields is also possible.)

   List
      A list of data-blocks available in the current blend-file, or a link to select an item from.
      The menu may show a preview besides the items and
      a search field to search the items in the list by name.

      .. note::

         Data-blocks with names that begin with ``.`` are hidden from the list, unless a string
         that also starts with ``.`` is entered into the search field, or the
         :ref:`Show Hidden Files/Data-Blocks <bpy.types.PreferencesFilePaths.show_hidden_files_datablocks>`
         user preference is enabled.

Name
   Displays, and allows editing of, the name of the selected data-block.
   If a name is already in use by a different data-block, Blender will append a number like ".001".
User Count
   Displays the number of :term:`users <Data User>` of the data (if there's more than one user).
   Clicking it will create a single-user copy.

   As an example, if three separate objects referenced the same material, the material's user count would be 3.
   Changing the material would affect all three objects. If you now selected an object and clicked the user count,
   the object would receive its very own copy of the material, which can be modified independently of the original
   that's still used by the other two.

Fake User (shield icon)
   If a data-block has no :term:`real users <Real User>`, it'll normally be cleaned up
   (deleted) when saving the blend-file. To prevent this, you can give it a fake user;
   that way, it's guaranteed to "survive." Data-blocks with a fake user have an "F"
   prefix in the drop-down list.

   The :doc:`Outliner </editors/outliner/introduction>` can show an overview of all data-blocks
   without real users in the blend-file. Simply change its Display Mode to Orphan Data.
New/Add (files icon)
   Creates a new data-block (or duplicates the current one) and selects it.
Open File (folder icon)
   Opens the :doc:`File Browser </editors/file_browser>`, for importing an image for example.
Unpack File (bin icon)
   :ref:`Unpack <pack-unpack-data>` the file packed into the current blend-file to an external one.
Unlink Data-block ``X``
   Clears the link. :kbd:`Shift-LMB` to set the users to zero
   allowing the data to be fully deleted from the blend-file.

Sometimes there is a :ref:`list <ui-list-view>` of applied data-blocks
(such as a list of materials used on the object).

.. seealso::

   Data-blocks are discussed further in the :doc:`Data System chapter </files/data_blocks>`.


Preview
=======

.. figure:: /images/interface_controls_templates_data-block_preview.png
   :align: right

   A Data-Block menu with preview.

Some data-block menus have large preview images in their drop-down
instead of just icons and names.

.. container:: lead

   .. clear


.. rename to selector?

.. _ui-data-id:

Data ID
=======

.. figure:: /images/interface_controls_templates_data-block_data-id.png
   :align: right

   A Data ID field.

A Data ID field is similar to a Data Block Menu, but is only for selecting
(and not for other features like creating new data or managing users).

It can show the following elements:

Type
   The icon on the left specifies the accepted data-block type.
Name
   The text field functions as a search field by matching elements in the list.
   Press :kbd:`Tab` to auto-complete names up to the level where a match is found.
   If more than one match exists, you have to continue typing.
   If you type an invalid name, the value will remain unchanged.
List
   Lets you select the data-block directly.
Eyedropper
   In some Data IDs there is an :ref:`ui-eyedropper`
   available through the pipette icon on the right side.
Remove ``X``
   Click the ``X`` button on the right to clear the reference.


Sub IDs
-------

Related types of IDs may become available to select a property or child object,
depending on the object type.

.. figure:: /images/interface_controls_templates_data-block_subids.png

   Sub ID Example.

Vertex Group
   If the selected object in the *Target* field is a mesh or a lattice,
   an additional field is displayed where a vertex group can be selected.
Bone
   If the selected object in the *Target* field is an armature,
   an additional field is displayed where a bone can be selected.

   Head/Tail
      Once a bone is selected, a numeric field becomes available for specifying a point on the bone.
      A value of 0 corresponds to the bone's head, while a value of 1 corresponds to its tail.
      Any values between these will result in linear interpolation (so a value of 0.5 matches
      the bone's center).

      Use B-Bone Shape
         If the bone is a :doc:`bendy bone </animation/armatures/bones/properties/bendy_bones>`,
         clicking on this button will make the point follow the curvature of the B-spline between head and tail,
         rather than simply going in a straight line.


## List View

.. _ui-list-view:

*********
List View
*********

.. figure:: /images/interface_controls_templates_list-presets_view-filter.png
   :align: right
   :figwidth: 268px

   List view with expanded Filtering Options panel.

This control is useful for managing lists of items.
In addition to the main list, there is a Filtering panel on the bottom
(hidden by default) and modification buttons on the right.

Select
   To select an item, click :kbd:`LMB` on it.
Rename
   By double-clicking on an item, you can edit its name via a text field.
   This can also be achieved by clicking it with :kbd:`Ctrl-LMB`.
Resize
   The list view can be resized to show more or fewer items.
   Hover the mouse over the handle (::::), then click and drag to expand or shrink the list.

.. _bpy.ops.ui.list_start_filter:

Filter
   Click the *Show filtering options* button (triangle on bottom left) to show or hide the filter option panel.

   Search :kbd:`Ctrl-F`
      Filters the list to only show items containing a certain term.
   Invert ``<->``
      Toggle between including items that match the search term and those that do not contain the search term.

   Sort by Name
      This button switches between alphabetical and non-alphabetical ordering.
   Reverse
      Sort objects in ascending or descending order. This also applies to alphabetical sorting, if selected.

On the right of the list view are list modification buttons:

Add ``+``
   Adds a new item.
Remove ``-``
   Removes the selected item.
Specials ``v``
   A :ref:`Specials <ui-specials-menu>` menu with operators to edit list entries.
Move (up/down arrow icon)
   Moves the selected item up/down one position.


## Operator Search


******
Search
******

.. _bpy.ops.wm.search_menu:

Menu Search
===========

.. reference::

   :Mode:      All Modes
   :Menu:      :menuselection:`Edit --> Menu Search`
   :Shortcut:  :kbd:`F3`

The Menu Search pop-up lets you search Blender's interface for a certain
:doc:`operator </interface/operators>` and execute it.
First narrow down the list by typing (part of) the operator's name,
then either click the operator with :kbd:`LMB`, or navigate to it with
:kbd:`Down` and :kbd:`Up` and activate it with :kbd:`Return`.

Apart from the operator names, the pop-up also shows the menus
where they're located.

.. figure:: /images/interface_controls_templates_operator-search_pop-up.png
   :align: center

   The Menu Search pop-up.

.. seealso::

   The :ref:`Spacebar Action <keymap-blender_default-spacebar_action>`
   option in the Preferences.


.. _bpy.ops.wm.search_operator:

Operator Search
===============

.. reference::

   :Mode:      All Modes
   :Menu:      :menuselection:`Edit --> Operator Search`

When :ref:`Developer Extras <bpy.types.PreferencesView.show_developer_ui>` are activated,
the Operator Search can be accessed from the Edit menu in the Topbar.
This menu searches all :doc:`/interface/operators`
within Blender, even if they are not exposed in a menu.
This is useful for Python developers for testing purposes.
Blender might also include a few advanced operators that are not
exposed in a menu and can only be accessed via this search menu.

.. seealso::

   The :ref:`User Preferences <bpy.types.Preferences.use_recent_searches>`
   has an option to change how the search results are scored.


## Blender Default


**************
Default Keymap
**************

While this isn't a comprehensive list,
this page shows common keys used in Blender's default keymap.

.. Even though this is not intended to be comprehensive,
   it could be expanded.


Global Keys
===========

.. list-table::
   :widths: 10 90

   * - :kbd:`Ctrl-O`
     - Open file.
   * - :kbd:`Ctrl-S`
     - Save file.
   * - :kbd:`Ctrl-N`
     - New file.
   * - :kbd:`Ctrl-Z`
     - Undo.
   * - :kbd:`Shift-Ctrl-Z`
     - Redo.
   * - :kbd:`Ctrl-Q`
     - Quit.
   * - :kbd:`F1`
     - Help *(context sensitive)*.
   * - :kbd:`F2`
     - Rename active item.
   * - :kbd:`F3`
     - Menu Search.
   * - :kbd:`F4`
     - File context menu.
   * - :kbd:`F5` - :kbd:`F8`
     - *Reserved for user actions.*
   * - :kbd:`F9`
     - Adjust last operation.
   * - :kbd:`F10`
     - *Reserved for user actions.*
   * - :kbd:`F11`
     - Show render window.
   * - :kbd:`F12`
     - Render the current frame.
   * - :kbd:`Q`
     - Quick access (favorites).
   * - :kbd:`Ctrl-Spacebar`
     - Toggle Maximize Area.
   * - :kbd:`Ctrl-PageUp` / :kbd:`Ctrl-PageDown`
     - Next/previous Workspace.
   * - :kbd:`Spacebar`
     - User configurable.

       :Play: Toggle animation playback.
       :Tools: Tool switching with hotkeys (:kbd:`Shift-Spacebar` for play).
       :Search: Search for actions (:kbd:`Shift-Spacebar` for play).
   * - :kbd:`Shift-Ctrl-Spacebar`
     - Playback animation (reverse).


Common Editing Keys
===================

.. list-table::
   :widths: 10 90

   * - :kbd:`X`
     - Deletes the selected item, requires a confirmation dialog.
   * - :kbd:`Delete`
     - Deletes the selected item, does not require a confirmation dialog.


Common Editor Keys
==================

These keys are shared across editors such as the 3D Viewport, UV and Graph editor.

.. list-table::
   :widths: 10 90

   * - :kbd:`A`
     - Select all.
   * - :kbd:`Alt-A`
     - Select none.
   * - :kbd:`Ctrl-I`
     - Invert selection.
   * - :kbd:`H`
     - Hide selection.
   * - :kbd:`Alt-H`
     - Reveal hidden items.
   * - :kbd:`T`
     - Toggle Toolbar.
   * - :kbd:`N`
     - Toggle Sidebar.


3D Viewport Keys
================

.. list-table::
   :widths: 10 90

   * - :kbd:`Tab`
     - Toggle Edit mode.
   * - :kbd:`Ctrl-Tab`
     - Toggle Pose mode for armatures, or show a mode switching pie menu for others.
   * - :kbd:`1` - :kbd:`3`
     - In Edit Mode, switch between editing vertices (:kbd:`1`), edges (:kbd:`2`), or faces (:kbd:`3`).

       Hold :kbd:`Shift` to toggle one of these without disabling the others.

       Hold :kbd:`Ctrl` to alter how the selection is transformed from the old mode to the new.

       See :doc:`Mesh Selection Modes </modeling/meshes/selecting/introduction>` for details.
   * - :kbd:`AccentGrave`
     - Show 3D Viewport navigation pie menu.
   * - :kbd:`Ctrl-AccentGrave`
     - Toggle gizmos.
   * - :kbd:`Shift-AccentGrave`
     - Start Walk/Fly Navigation.


Platform Specific Keys
======================

macOS
-----

The :kbd:`Cmd` key can be used instead of :kbd:`Ctrl` on macOS
for all but a few exceptions which conflict with the operating system.

List of additional macOS specific keys:

.. list-table::
   :widths: 10 90

   * - :kbd:`Cmd-Comma`
     - Preferences.


.. _keymap-blender_default-prefs:

Keymap Preferences
==================

.. _keymap-blender_default-prefs-select_with:

Select with Mouse Button
   Controls which mouse button, either left or right, is used to select items in Blender.
   If *Left* is selected, the :kbd:`RMB` will be a context sensitive menu.
   If *Right* is selected, the :kbd:`LMB` will place the 3D Cursor.

.. _keymap-blender_default-spacebar_action:

Spacebar Action
   Controls the action of :kbd:`Spacebar`.
   These and other shortcuts can be modified in the :doc:`keymap preferences </editors/preferences/keymap>`.

   :Play:
      Starts playing through the :doc:`Timeline </editors/timeline>`.
      This option is good for animation or video editing work.
   :Tools:
      Opens the Toolbar underneath the cursor to quickly change the active tool.
      This option is good if you are doing a lot of modeling or rigging work.
   :Search:
      Opens up the :doc:`Menu Search </interface/controls/templates/operator_search>`.
      This option is good for someone who is new to Blender and is unfamiliar with the menus and shortcuts.

Activate Gizmo Event
   The activation event for gizmos that support drag motion.
   This option is only available when Left click *Select with Mouse Button* is chosen.

   :Press:
      The gizmo's operation gets initiated (and additional options become available in the Status Bar)
      the moment you press down the mouse button on the gizmo.
   :Drag:
      The operation only gets initiated once you start dragging the gizmo.

Tool Keys
   The method of keys to activate tools such as move, rotate, and scale.

   :Immediate: Activate actions immediately.
   :Active Tool: Activate the tool for editors that support tools.

Alt Click Tool Prompt
   Tapping :kbd:`Alt` shows a prompt in the status bar prompting a second keystroke to activate the tool.
   Note that this option is not available when using
   :ref:`Emulate 3 Button Mouse <bpy.types.PreferencesInput.use_mouse_emulate_3_button>`.

Alt Tool Access
   Hold :kbd:`Alt` to use the :doc:`Active Tool </interface/tool_system>` when the gizmo would normally be required.
   (For example, with the Move tool selected, you can hold :kbd:`Alt` and drag the mouse anywhere in the viewport
   to move the selected object, rather than having to drag its gizmo.)
   This option is only available when *Select with Mouse Button* is set to Left click
   and :ref:`Emulate 3 Button Mouse <bpy.types.PreferencesInput.use_mouse_emulate_3_button>` is disabled.

Select All Toggles
   Causes selection shortcut :kbd:`A` to deselect all when any selection exists.

Region Toggle Pie
   :kbd:`N` opens a :ref:`pie menu <bpy.types.UIPieMenu>` to toggle :doc:`/interface/window_system/regions`,
   rather than toggling a single region.


3D Viewport
-----------

Grave Accent / Tilde Action
   :Navigate:
      Navigation pie menu, useful on systems without a numeric keypad.
   :Gizmos:
      Transform gizmos pie menu, useful for quickly switching between transform gizmos.
      Note that this doesn't apply to tools that force a certain gizmo (Move, Rotate, Scale
      and Transform); if you have such a tool selected, the gizmo will stay the same
      no matter what you choose in the pie menu.

Middle Mouse Action
   The action when :kbd:`MMB` dragging in the viewport, this also applies to trackpads.

   :Orbit:
      Rotates the view around a pivot point, :kbd:`Shift-MMB` is used for panning the view.
   :Pan:
      Shifts the view towards the mouse, :kbd:`Shift-MMB` is used for orbiting the view.

Alt Middle Mouse Drag Action
   :Relative:
      Set the view axis where each mouse direction maps to an axis relative to the current orientation.
   :Absolute:
      Set the view axis where each mouse direction always maps to the same axis.

.. _keymap-pref-py_menu_on_drag:

Tab for Pie Menu
   Causes :kbd:`Tab` to open a pie menu (swaps :kbd:`Tab` and :kbd:`Ctrl-Tab`).

Pie Menu on Drag
   This allows keys to have a secondary drag action.

   :kbd:`Tab`
      :tap: Toggles Edit Mode.
      :drag: Object Mode pie menu.
   :kbd:`Z`
      :tap: Toggles wireframe view.
      :drag: Display mode pie menu.
   :kbd:`AccentGrave`
      :tap: First person :ref:`Fly/walk Navigation <3dview-fly-walk>`.
      :drag: View axis pie menu.

Extra Shading Pie Menu Items
   Show additional items in the shading menu (:kbd:`Z` key).

Transform Navigation with Alt
   During transformations, use :kbd:`Alt` to navigate the 3D Viewport.

   When disabled, hotkeys for proportional editing, automatic constraints,
   and auto IK chain length will require holding :kbd:`Alt`.


File Browser
------------

Open Folders on Single Click
   Navigate into folders by clicking on them once instead of twice.


## Industry Compatible


**************************
Industry Compatible Keymap
**************************

While this is not a comprehensive list,
this page shows common keys used in the industry compatible keymap.


General
=======

.. list-table::
   :widths: 20 80

   * - :kbd:`1` - :kbd:`3`
     - Switch Selection mode
   * - :kbd:`4``
     - Object Mode
   * - :kbd:`5``
     - Modes Pie Menu
   * - :kbd:`RMB`
     - Context menu
   * - :kbd:`Tab`
     - Menu Search.
   * - :kbd:`Shift-Tab`
     - Quick access (favorites)
   * - :kbd:`Return`
     - Rename
   * - :kbd:`Ctrl-Return`
     - Render
   * - :kbd:`Ctrl-[`
     - Toggle Toolbar
   * - :kbd:`Ctrl-]`
     - Toggle Sidebar


Common Editing Keys
===================

.. list-table::
   :widths: 10 90

   * - :kbd:`Backspace`
     - Deletes the selected item, requires a confirmation dialog.
   * - :kbd:`Delete`
     - Deletes the selected item, does not require a confirmation dialog.
   * - :kbd:`Ctrl-D`
     - Duplicate
   * - :kbd:`P`
     - Set Parent
   * - :kbd:`B`
     - Proportional Editing / Soft Selection


Viewport
========

.. list-table::
   :widths: 20 80

   * - :kbd:`Alt-LMB`
     - Orbit View
   * - :kbd:`Alt-MMB`
     - Pan View
   * - :kbd:`Alt-RMB`
     - Zoom View
   * - :kbd:`F1` - :kbd:`F4`
     - Front/Side/Top/Camera Viewpoints
   * - :kbd:`F`
     - Frame Selected
   * - :kbd:`Shift F`
     - Center View to Mouse
   * - :kbd:`A`
     - Frame All


Selection
=========

.. list-table::
   :widths: 20 80

   * - :kbd:`LMB`
     - Select
   * - :kbd:`Ctrl-A`
     - Select All
   * - :kbd:`Shift-Ctrl-A`
     - Deselect All
   * - :kbd:`Ctrl-I`
     - Select Inverse
   * - :kbd:`Up`
     - Select More
   * - :kbd:`Down`
     - Select Less
   * - Double :kbd:`LMB`
     - Select Loop
   * - Double :kbd:`Alt-LMB`
     - Select Ring
   * - :kbd:`Ctrl L`
     - Select Linked


Tools
=====

.. list-table::
   :widths: 20 80

   * - :kbd:`W`, :kbd:`E`, :kbd:`R`
     - Transform Tools
   * - :kbd:`Q`
     - Select Tools
   * - :kbd:`D`
     - Annotate
   * - :kbd:`C`
     - Cursor Tool


Edit Mode Tools
===============

.. list-table::
   :widths: 20 80

   * - :kbd:`Ctrl-E`
     - Extrude
   * - :kbd:`Ctrl-B`
     - Bevel
   * - :kbd:`I`
     - Inset
   * - :kbd:`K`
     - Knife
   * - :kbd:`Alt-C`
     - Loop Cut


Animation
=========

.. list-table::
   :widths: 20 80

   * - :kbd:`Spacebar`
     - Play/Pause
   * - :kbd:`S`
     - Set Location + Rotation + Scale keyframe
   * - :kbd:`Shift-S`
     - Insert Keyframe menu
   * - :kbd:`Shift-W`
     - Set Location Key
   * - :kbd:`Shift-E`
     - Set Rotation Key
   * - :kbd:`Shift-R`
     - Set Scale Key


Platform Specific Keys
======================

macOS
-----

The :kbd:`Cmd` key can be used instead of :kbd:`Ctrl` on macOS
for all but a few exceptions which conflict with the operating system.


## Introduction


****************
Common Shortcuts
****************

Conventions Used in This Manual
===============================

.. Note that these conventions are for people reading the manual.
   we have more detailed list of conventions for authors under the writing style section.

Keyboards
---------

Hotkey letters are shown in this manual like they appear on a keyboard; for example:

:kbd:`G`
   refers to the lowercase ``g``.
:kbd:`Shift`, :kbd:`Ctrl`, :kbd:`Alt`
   are specified as modifier keys.
:kbd:`Ctrl-W`, :kbd:`Shift-Alt-A`, ...
   indicates that these keys should be pressed simultaneously.
:kbd:`Numpad0` to :kbd:`Numpad9`, :kbd:`NumpadPlus`
   refer to the keys on the separate numeric keypad.

Other keys are referred to by their names,
such as :kbd:`Esc`, :kbd:`Tab`, :kbd:`F1` to :kbd:`F12`.
Of special note are the arrow keys, :kbd:`Left`, :kbd:`Right` and so on.


Mouse
-----

This manual refers to mouse buttons as:

:kbd:`LMB`
   Left Mouse Button
:kbd:`RMB`
   Right Mouse Button
:kbd:`MMB`
   Middle Mouse Button
:kbd:`Wheel`, :kbd:`WheelUp` & :kbd:`WheelDown`
   Scrolling the wheel.

.. note::

   Blender has two main selection modes: left-click select and right-click select.
   See the :ref:`Select with Mouse Button <keymap-blender_default-prefs-select_with>` preference.

   While left-click select is the default as it's the most common in other applications,
   right-click select does have its advantages.
   See: `Learn the benefits of right-click select <https://vimeo.com/76335056>`__.


Hovering
========

While hovering (when the cursor is held over a button).


.. _keymap-common-properties:

Properties
----------

- :kbd:`Ctrl-C` -- Copy the (single) value of the button.
- :kbd:`Ctrl-V` -- Paste the (single) value of the button.
- :kbd:`Ctrl-Alt-C` -- Copy the entire vector or color of the field.
- :kbd:`Ctrl-Alt-V` -- Paste the entire vector or color of the field.
- :kbd:`RMB` -- Open the context menu.
- :kbd:`Backspace` -- Clear the value (sets to zero or clears a text field).
- :kbd:`Minus` -- Negate number values (multiply by -1.0).
- :kbd:`Ctrl-Wheel` -- Change the value incremental steps.

  For pop-up option menus buttons, this cycles the value.
- :kbd:`Return` -- Activates menus or toggles the value.

- :kbd:`Alt` -- Hold while editing values to apply the change to all selected items
  (objects, bones, sequence-strips).

  This can be used for number fields and toggles.


Animation
---------

- :kbd:`I` -- Insert a keyframe.
- :kbd:`Alt-I` -- Clear the keyframe.
- :kbd:`Shift-Alt-I` -- Clear all keyframes (removing all F-Curves).
- :kbd:`Ctrl-D` -- Assign a driver.
- :kbd:`Ctrl-Alt-D` -- Clear the driver.
- :kbd:`K` -- Add a Keying Set.
- :kbd:`Alt-K` -- Clear the Keying Set.


Python Scripting
----------------

- :kbd:`Ctrl-C` over any :ref:`ui-operator-buttons` copies their Python command into the clipboard.

  This can be used in the Python Console or in the Text editor when writing scripts.
- :kbd:`Shift-Ctrl-C` over property buttons copies their data path for this property
  (also available from the context menu).

  Useful when writing drivers or scripts.
- :kbd:`Shift-Ctrl-Alt-C` over property buttons copies their *full* data path for the data-block and property.

  Note that in most cases it is best to access values based on the context, instead of by name.


Dragging
========

- :kbd:`Ctrl` -- While dragging, snap to discrete steps.
- :kbd:`Shift` -- Gives precision control over the value.
- :kbd:`Shift-Ctrl` -- Precise snap will move the object with high precision
  along with the snapping constraint.


.. _ui-text-editing:

Text Editing
============

- :kbd:`Home` -- Go to the start of the line.
- :kbd:`End` -- Go to the end of the line.
- :kbd:`Left`, :kbd:`Right` -- Move the cursor a single character.
- :kbd:`Ctrl-Left`, :kbd:`Ctrl-Right` -- Move the cursor an entire word.
- :kbd:`Backspace`, :kbd:`Delete` -- Delete characters.
- :kbd:`Ctrl-Backspace`, :kbd:`Ctrl-Delete` -- Delete words.
- :kbd:`Shift` -- Select while holding the key and moving the cursor.
- :kbd:`Ctrl-A` -- Select all text.
- :kbd:`Ctrl-C` -- Copy the selected text.
- :kbd:`Ctrl-X` -- Cut the selected text.
- :kbd:`Ctrl-V` -- Paste text at the cursor position.


Confirm & Cancel
================

- :kbd:`Esc`, :kbd:`RMB` -- Cancel.
- :kbd:`Return`, :kbd:`LMB` -- Confirm.

.. (todo?) deactivation: Some controls can be disabled, in Blender deactivated controls are still editable.
   That can be due to the current state or context. In that case, they appear in a lighter color.


## Areas

.. _bpy.types.Area:
.. _bpy.types.AreaSpaces:
.. _bpy.ops.screen.actionzone:

*****
Areas
*****

.. figure:: /images/interface_window-system_areas_borders.png
   :align: right
   :width: 250px
   :figwidth: 250px

   Area boundaries are indicated by rounded corners (yellow highlights).

The Blender window is divided into a number of rectangles called Areas.
Areas reserve screen space for :doc:`/editors/index`, such as the
:doc:`3D Viewport </editors/3dview/introduction>` or the
:doc:`Outliner </editors/outliner/introduction>`.
Each editor offers a specific piece of functionality.

Areas are grouped into :doc:`Workspaces </interface/window_system/workspaces>`,
which are geared towards particular tasks (modeling, animating and so on).

.. note::

   While some keyboard shortcuts in Blender are global (such as :kbd:`Ctrl-S`
   for saving), many depend on which editor the mouse cursor is hovering over.

   As an example, say you just selected two objects in the Outliner and want
   to join them. If you pressed the shortcut for this (:kbd:`Ctrl-J`)
   while the cursor is still in the Outliner, nothing would happen as the
   shortcut isn't valid there; you first need to move your cursor
   to the 3D Viewport.


.. _bpy.ops.screen.area_move:

Resizing
========

.. figure:: /images/interface_window-system_areas_resize.png
   :align: right
   :width: 250px
   :figwidth: 250px

You can resize areas by dragging their borders with :kbd:`LMB`.
Move your mouse cursor over the border between two areas,
so that the cursor changes to a double-headed arrow, and then click and drag.


.. _bpy.ops.screen.area_split:

Splitting
=========

.. figure:: /images/interface_window-system_areas_split.png
   :align: right
   :width: 250px
   :figwidth: 250px

Splitting an area will create a new area. Placing the mouse cursor
in an area corner will change the cursor to a cross (+) to indicate that
pressing down :kbd:`LMB` will activate splitting or joining.
Dragging from an area corner **inward** will *split* the area.
You define the split direction by dragging either horizontally or vertically.


.. _bpy.ops.screen.area_join:

Joining
=======

.. figure:: /images/interface_window-system_areas_join.png
   :align: right
   :width: 250px
   :figwidth: 250px

   Properties is being joined to the Outliner.

Dragging from an area corner **outward** will *join* two areas.
The area that will be closed shows a dark overlay.
You can select which area will be closed by moving the mouse over it.
Release the :kbd:`LMB` to complete the join.
If you press :kbd:`Esc` or :kbd:`RMB` before releasing the mouse,
the operation will be canceled.

.. tip::

   The cursor will also turn into a cross when hovering over either
   end of the border between two areas. When splitting or joining,
   it's best not to start dragging from this border, but from a
   corner inside one of the areas.


.. _bpy.ops.screen.area_options:

Area Options
^^^^^^^^^^^^

:kbd:`RMB` on the border opens the *Area Options*.

Vertical/Horizontal Split
   Shows an indicator line that lets you select the area and position where to split.
   :kbd:`Tab` switches between vertical/horizontal.
Join Areas
   Shows the join direction overlay.
Swap Areas
   Swaps this area with the adjacent one.


.. _bpy.ops.screen.area_swap:

Swapping Contents
-----------------

You can swap the contents of two areas by pressing :kbd:`Ctrl-LMB`
on one of the corners of the initial area, dragging towards the target area,
and releasing the mouse there. The two areas do not need to be side-by-side,
though they must be inside the same window.


.. _bpy.ops.screen.area_dupli:

Duplicate Area into new Window
==============================

.. reference::

   :Menu:      :menuselection:`View --> Area --> Duplicate Area into new Window`

A new floating window containing an area can be created from
:menuselection:`View --> Area --> Duplicate Area into new Window`. (Not available in some editors.)

The new window is a fully functional window, which is part of the same instance of Blender.
This can be useful, e.g. if you have multiple monitors.

You can also create a new window from an existing area by pressing :kbd:`Shift-LMB`
on an area corner, then dragging outward slightly.


.. _bpy.ops.screen.screen_full_area:

Toggle Maximize Area
====================

.. reference::

   :Menu:      :menuselection:`View --> Area --> Toggle Maximize Area`
   :Shortcut:  :kbd:`Ctrl-Spacebar`

Expands the Area so it fills the whole window (while keeping the Topbar and Status Bar visible).
To return to normal size, use the keyboard shortcut again or click the *Back to Previous* button in the Topbar.


Toggle Fullscreen Area
======================

.. reference::

   :Menu:      :menuselection:`View --> Area --> Toggle Fullscreen Area`
   :Shortcut:  :kbd:`Ctrl-Alt-Spacebar`

Expands the Area so it fills the whole window, hiding the Topbar, Status Bar, and even the
secondary :doc:`regions </interface/window_system/regions>` (toolbars etc.) of the Area's own editor.
To return to normal size, use the keyboard shortcut again or click the icon in the Area's top right corner
(only becomes visible when hovering).


## Introduction


**************************
Window System Introduction
**************************

After starting Blender and closing the :ref:`Splash Screen <splash>`,
the Blender window should look similar to the image below.

.. figure:: /images/interface_window-system_introduction_default-startup.png
   :align: center

   The default startup Blender window.

Blender's interface is separated into three main parts:

- The :doc:`Topbar </interface/window_system/topbar>` at the very top, consists of the main menu,
  which is used for saving, importing and exporting files, configuring settings, and rendering among other functions.
- :doc:`Areas </interface/window_system/areas>` in the middle, which is the main workspace
- The :doc:`Status Bar </interface/window_system/status_bar>` at the bottom,
  which displays shortcut suggestions and relevant statistics.


.. figure:: /images/interface_window-system_introduction_default-screen.png

   Blender's default Screen Layout. Topbar (blue), Areas (green) and Status Bar (red).


Customization
=============

.. rubric:: Keyboard shortcuts

Blender makes heavy use of keyboard shortcuts to speed up work.
These can be customized in the :ref:`Keymap Editor <prefs-input-keymap-editor>`.


.. rubric:: Theme colors

Blender allows for most of its interface colors to be changed to suit the needs of the user.
If you find that the colors you see on screen do not match those
in the Manual, it could be that your default theme has been altered.
Creating a new theme or selecting/altering a preexisting one can be done by opening
the :doc:`Preferences </editors/preferences/index>` and clicking on the *Themes* tab.

.. rubric:: Accessibility

Blender has several options for visibility customization,
including resolution scale, and the ability to load custom fonts.
These settings can be configured in the :doc:`Interface Preferences </editors/preferences/interface>`.


## Regions

.. _bpy.types.Region:
.. _ui-region:

*******
Regions
*******

Every Editor in Blender is divided into Regions.
Regions can have smaller structuring elements like
:doc:`tabs and panels </interface/window_system/tabs_panels>`
with buttons, controls and widgets placed within them.

.. figure:: /images/interface_window-system_regions_3d-view.png

   The regions of the 3D Viewport showing the Sidebar and
   the Adjust Last Operation panel after adding a Cube.

   Header (green), Main region (yellow), Toolbar (blue),
   Sidebar (red) and Adjust Last Operation panel (pink).


.. _ui-region-window:

Main Region
===========

At least one region is always visible.
It is called the Main region and is the most prominent part of the editor.

Each editor has a specific purpose, so the main region and
the availability of additional regions are different between editors.
See specific documentation about each editor in the :doc:`Editors </editors/index>` chapter.


.. _bpy.types.Header:
.. _ui-region-header:

Header
======

A header is a small horizontal strip, which sits either at the top or bottom of an area.
All editors have a header acting as a container for menus and commonly used tools.
:ref:`Menus <bpy.types.UIPopupMenu>` and buttons will change with the editor type and
the selected object and mode.

.. figure:: /images/editors_3dview_introduction_3d-view-header-object-mode.png

   The Header of the 3D Viewport.


.. _bpy.ops.screen.header:

Context Menu
------------

:kbd:`RMB` on a header reveals a context menu with a couple options:

Show Header
   Toggles the visibility of the header.
   If a header is hidden, it can be made visible again by clicking or dragging
   the small arrow that appears at the top/bottom right of the editor.
Show Tool Settings
   Toggles the visibility of the `Tool Settings`_.
Show Menus
   Toggles whether the :ref:`Menus <bpy.types.UIPopupMenu>` are collapsed or not.
Flip to Bottom/Top
   Toggles whether the header or Tool Settings appear on the top or bottom of the editor.
Vertical/Horizontal Split
   Shows an indicator line that lets you select the area and position where to split.
   :kbd:`Tab` switches between vertical/horizontal.
Maximize/Full Screen Area
   See :ref:`bpy.ops.screen.screen_full_area`.
Duplicate Area into New Window
   See :ref:`bpy.ops.screen.area_dupli`.
Close Area
   Closes the area and replaces it with the expansion of a neighboring area.


Toolbar
=======

The :ref:`Toolbar <ui-region-toolbar>` (on the left side of the editor area)
contains a set of interactive tools. :kbd:`T` toggles the visibility of the Toolbar.


Tool Settings
=============

A horizontal strip at the top or bottom of the editor (similar to the header)
containing settings for the currently selected tool. Just like the header,
it can be hidden and moved through its context menu.


Adjust Last Operation
=====================

:ref:`Adjust Last Operation <bpy.ops.screen.redo_last>` is a region that allows
tweaking an operator after running it. For example, if you just added a cube,
you can use this region to tweak its size.


.. _ui-region-sidebar:

Sidebar
=======

The *Sidebar* (on the right side of the editor area)
contains :ref:`Panels <ui-panels>`
with settings of objects within the editor and the editor itself.
:kbd:`N` toggles the visibility of the Sidebar.


Footer
======

Some editors show a bar (on top/bottom of the editor area)
that displays information about for example the active tool or operator.


Arranging
=========

Scrolling
---------

A region can be scrolled vertically and/or horizontally by dragging it with the :kbd:`MMB`.
If the region has no zoom level, it can also be scrolled by using the :kbd:`Wheel`
while the mouse hovers over it.

.. _interface_window-system_regions_scroll_range:

Some regions, in particular animation timelines, have scrollbars with added control points
to adjust the vertical or horizontal range of the region.
These special scrollbars will have added widgets at the ends, as shown in the following image:

.. figure:: /images/interface_window-system_regions_scrollbar_widget.png
   :align: center

   Scrollbars with zoom widgets.

This can be used to stretch or compress the range to show more or less detail within the available screen space.
Simply drag one of the dots to either increase or decrease the displayed range.
You can also quickly adjust both the horizontal and vertical range by dragging in the editor with :kbd:`Ctrl-MMB`.


.. _bpy.ops.screen.region_blend:

Changing the Size and Hiding
----------------------------

Resizing regions works by dragging their border, the same way as
:doc:`/interface/window_system/areas`.

To hide a region, resize it down to nothing.
A hidden region leaves a little arrow sign.
:kbd:`LMB` on this icon to make the region reappear.

.. list-table:: Hiding and showing the Sidebar.

   * - .. figure:: /images/interface_window-system_regions_sidebar-hide.png

     - .. figure:: /images/interface_window-system_regions_sidebar-show.png


.. _bpy.ops.screen.region_scale:

Scaling
-------

The scale of certain regions (such as the Toolbar) can be changed by dragging inside them
with :kbd:`Ctrl-MMB`, or using :kbd:`NumpadPlus` and :kbd:`NumpadMinus` while hovering the
mouse cursor over them. Press :kbd:`Home` to reset the scale to the default.


.. _ui-region-asset_shelf:

Asset Shelf
===========

Search
------

To search for assets, hover your mouse over the Asset Shelf, then press Ctrl-F and type a search query.
This will filter the poses to match what you typed.


Tabs
----

.. figure:: /images/asset_shelf-tabs.png

   The usage of catalogs as tabs.

Catalogs can be shown as individual tabs. Each tab will only show its content, and the content of its children.
That makes it easy to filter down to a certain set of assets.


Display Options
---------------

.. figure:: /images/asset_shelf-options.png

   Display options available for the asset shelf.

It is possible to change the size of items on the shelf by using the size property.

By toggling on the "Names" checkbox, the asset names will be shown in the shelf. Alternatively it is also
possible to hover over an item to show its name.

By default the shelf only has a height for one item row. To allow for more rows, drag it on the upper edge to increase
its size.



## Splash

.. _bpy.ops.wm.splash:
.. _splash:

*************
Splash Screen
*************

When starting Blender, the splash screen appears in the center of the window.
It contains options to create new projects or open recent ones.
A more detailed description can be found below.

.. figure:: /images/interface_window-system_splash_current.png
   :align: center

   Blender Splash Screen.

To close the splash screen and start a new project,
click anywhere outside the splash screen (but inside the Blender window) or press :kbd:`Esc`.
The splash screen will disappear revealing the default screen.
To reopen the splash screen, click on the Blender icon in the Topbar and select *Splash Screen*.

.. note::

   When starting Blender for the first time or updating to a new version,
   the "interactive region" contains a :ref:`Quick Set Up Process <splash-quick-start>`.


Splash Image
============

The upper part of the splash screen contains the splash image with the Blender version in the top right.


Interactive Region
==================

The interactive region is the bottom half of the splash screen.

New File
   Start a new project based on a template.
Recent Files
   Your most recently opened blend-files. This gives quick and easy access to your recent projects.

Open
   Allows opening an existing blend-file.
Recover Last Session
   Blender will try to recover the last :term:`session` based on temporary files. See
   :doc:`/troubleshooting/recover`.

Donate
   Open Blender's `Development Fund <https://fund.blender.org/>`__ website.
What's New
   Open the latest release notes.


## Status Bar


**********
Status Bar
**********

The Status Bar is located at the bottom of the Blender window and displays contextual information such as
keyboard shortcuts, messages, and statistical information.
The Status Bar can be hidden by disabling *Show Status Bar* in Window menu or by dragging from the top edge down.

.. figure:: /images/interface_window-system_status-bar_ui.png

   Status Bar.


Keymap Information
==================

The left side of the Status Bar displays mouse button shortcuts and the keymap of the active tool.
In editors with a Toolbar, tapping :kbd:`Alt` (or ``Option`` on macOS)
shows the hotkeys to change to a desired tool.

.. tip::

   This functionality can be disabled with the *Alt Click Tool Prompt*
   preference in the :doc:`Keymap Preferences </editors/preferences/keymap>`).

.. figure:: /images/interface_window-system_status-bar_ui-left.png
   :align: center


Status Messages
===============

The middle of the Status Bar displays information about in-progress operations.

.. figure:: /images/interface_window-system_status-bar_ui-center.png
   :align: center

Running Task
   Shows the progress of the currently running task (such as rendering or baking).
   Hovering the mouse pointer over the progress bar will display a time estimate.
   The task can be aborted by clicking the cancel button (``X`` icon).
Report Message
   Informational messages or warnings, such as after saving a file.
   They disappear after a short time.
   Click them to show the full message in the :doc:`Info Editor </editors/info_editor>`.


Resource Information
====================

The right side of the Status Bar displays information about the Blender instance.
Which information is shown can be chosen by clicking :kbd:`RMB`.

.. figure:: /images/interface_window-system_status-bar_ui-right.png
   :align: center

Scene Statistics
   Collection
      Name of the active :doc:`Collection </scene_layout/collections/index>`.
   Active Object
      Name of the active selected object.
   Geometry
      Displays information about the current scene depending on the mode and object type.
      This can be the number of vertices, faces, triangles, or bones.
   Objects
      Number of the selected objects and the total count.

System Memory
   Estimate of Blender's RAM consumption. In a single-instance single-machine scenario,
   this estimate provides a measurement against the hardware limit of the machine.

Blender Version
   The version of Blender that is currently running.


## Tabs Panels


*************
Tabs & Panels
*************

Tabs
====

.. figure:: /images/interface_window-system_tabs-panels_tabs.png
   :align: right
   :figwidth: 300px

   Top: Horizontal Tab header in the Topbar.
   Bottom: Vertical Tab header shows tab icons in the Properties.

Tabs are used to control overlapping sections in the user interface.
The content of only one Tab is visible at a time.
Tabs are listed in a *Tab header*, which can be horizontal or vertical.


Switching/Cycling
-----------------

Vertical tabs can be switched with :kbd:`Ctrl-Wheel` from anywhere in the tab.
You can also cycle through tabs with :kbd:`Ctrl-Tab` and
:kbd:`Shift-Ctrl-Tab`, or press down :kbd:`LMB` and move the mouse over the tab header icons.
(This does not apply to Workspace tabs; see :ref:`Workspace controls <workspaces-controls>`.)

.. container:: lead

   .. clear


.. _ui-panels:
.. _bpy.types.Panel:

Panels
======

.. figure:: /images/interface_window-system_tabs-panels_panels.png
   :align: right
   :figwidth: 200px

   Panels in Properties.

   A panel is highlighted in yellow and a subpanel in red.

The smallest organizational unit in the user interface is a panel.
The panel header shows the title of the panel. It is always visible.
Some panels also include subpanels.


Collapsing and Expanding
------------------------

A panel can either be expanded to show its contents, or collapsed to hide its contents.
An expanded panel is indicated by a down-arrow (▼) in the panel header,
while a collapsed panel is shown with a right-arrow (►).

- Clicking :kbd:`LMB` on the panel header expands or collapses it.
- Pressing :kbd:`A` expands/collapses the panel under the mouse pointer.
- Clicking :kbd:`Ctrl-LMB` on the header of a collapsed panel will expand it and collapse all others.
- Clicking :kbd:`Ctrl-LMB` on the header of an expanded panel will expand/collapse all its subpanels.
- Dragging with :kbd:`LMB` over the headers will expand or collapse many at once.


Position
--------

You can change the position of a panel within its region by clicking
and dragging the grip widget (\:\:\:\:) on the right side of its header.


Pinning
-------

Sometimes it is desirable to view panels from different tabs at the same time.
Like, for instance, having access to a camera's properties, while other objects are selected.
This has been solved by making panels pinnable.

A pinned panel remains visible regardless of which tab has been selected.
You can pin a panel by clicking on the pin icon in its header.
Panels that do not have a pin icon can be pinned by :kbd:`RMB` on the panel header
and selecting *Pin*, or by pressing :kbd:`Shift-LMB`.

.. note::

   Pinning is not available for all panels. For example, it's available in the Sidebar
   but not in the Properties editor.


.. _bpy.ops.script.execute_preset:
.. _ui-presets:

Presets
-------

.. figure:: /images/interface_controls_templates_list-presets_preset.png
   :align: right

   Example Presets menu.

.. Share between properties. i.e. different nodes color presets.

Selector
   A list of available presets. A selection will override the included properties.
Add ``+``
   New presets can be added based on the currently applied set of properties, which will be saved for later reuse.
   A pop-up opens where you can set a name, after which you can select it from the list and
   in some cases additional settings.
Remove ``-``
   Deletes the selected preset.

.. saving preset: data-system?


## Topbar


******
Topbar
******

Menus
=====

.. figure:: /images/interface_window-system_topbar_menus.png


.. _topbar-blender_menu:

Blender Menu
------------

Splash Screen
   Open the :ref:`splash`.

.. _bpy.ops.wm.splash_about:

About Blender
   Opens a menu displaying the following information about Blender:

   - **Version**: The Blender version.
   - **Date**: Date when Blender was compiled.
   - **Hash**: The Git Hash of the build.
     This can be useful to give to support personnel when diagnosing a problem.
   - **Branch**: Optional branch name.
   - **Windowing Environment**: On Linux, this will show either Wayland or X11 depending
     on the windowing environment that Blender is running on.

   - **Donate**: Open Blender's `Development Fund <https://fund.blender.org/>`__ website.
   - **What's New**: Open the latest release notes.
   - **Credits**: Open the `credits <https://www.blender.org/about/credits/>`__ webpage.
   - **License**: Open the `license <https://www.blender.org/about/license/>`__ webpage.
   - **Blender Store**: Open the `Blender Store <https://store.blender.org/>`__ website.
   - **Blender Website**: Open main `Blender <https://www.blender.org/>`__ website.

Install Application Template
   Install a new :ref:`application template <app_templates>`.


File Menu
---------

The options to manage files are:

New :kbd:`Ctrl-N`
   Clears the current scene and loads the selected application template.
Open :kbd:`Ctrl-O`
   :ref:`Open <bpy.ops.wm.open_mainfile>` a blend-file.
Open Recent :kbd:`Shift-Ctrl-O`
   Displays a list of the most :ref:`recently opened <other-file-open-options>` blend-files.
   Hovering over items will show a preview, and information about the blend-file.
   Select any of the file names in the list to open that blend-file.

   Clear Recent Files List
      Removes all items from the list.
Revert
   Reopens the current file to its last saved version.
Recover
   Recover Last Session
      This will load a blend-file that Blender automatically saves just before exiting.
      So this option enables you to :doc:`recover </troubleshooting/recover>`
      your last work :term:`session`, e.g. if you closed Blender by accident.
   Recover Auto Save
      This will open an automatically saved file
      to :doc:`recover </troubleshooting/recover>` it.

-----

Save :kbd:`Ctrl-S`
   :ref:`Save <bpy.ops.wm.save_mainfile>` the current blend-file.
Save Incremental :kbd:`Ctrl-Alt-S`
   Save the current Blender file with a numerically
   incremented name that does not overwrite any existing files.
Save As... :kbd:`Shift-Ctrl-S`
   Opens the File Browser to specify file name and location of :ref:`save <bpy.ops.wm.save_mainfile>`.
Save Copy...
   :ref:`Saves <bpy.ops.wm.save_mainfile>` a copy of the current file.

----

Link...
   Links data from an external blend-file (library) to the current one.
   The editing of that data is only possible in the external library.
   *Link* and *Append* are used to load in only selected parts from another file.
   See :doc:`Linked Libraries </files/linked_libraries/index>`.
Append...
   Appends data from an external blend-file to the current one.
   The new data is copied from the external file, and completely unlinked from it.
Data Previews
   Tools for managing :doc:`data-block previews </files/blend/previews>`.

-----

Import
   Blender can use information stored in a variety of other format files which are created by
   other graphics programs. See :doc:`Import/Export </files/import_export/index>`.
Export
   Normally you save your work in a blend-file,
   but you can export some or all of your work to a format that can be processed by other graphics programs.
   See :doc:`Import/Export </files/import_export/index>`.

.. _bpy.ops.wm.collection_export_all:

Export All Collections
   Invokes all :ref:`configured exporters <collections-exporters>` for all collection.

-----

External Data
   External data, like texture images and other resources,
   can be stored inside the blend-file (packed) or as separate files (unpacked).
   Blender keeps track of all unpacked resources via a relative or absolute path.
   See :ref:`pack or unpack external data <pack-unpack-data>`.

   Automatically Pack Resources
      Pack all currently used external files into the blend-file and automatically pack any files
      that are added later. Unchecking this option will only stop the automatic packing for new files;
      it won't unpack existing ones.
   Pack Resources
      Pack all used external files into the blend-file. After running this operator and saving the
      blend-file, the external files will no longer be used -- any changes in them will no longer be
      reflected in the blend-file, and you are free to move or delete them.
   Unpack Resources
      Export previously packed files back to external ones. You can choose whether to reuse existing
      external files or overwrite them.
   Pack Linked Libraries
      Pack data-blocks that are :doc:`linked </files/linked_libraries/link_append>` from an external
      blend-file into the current one.
   Unpack Linked Libraries
      Export previously packed data-blocks back to external blend-files. Existing blend-files are
      overwritten.
   Make Paths Relative
      Make all paths to external files :ref:`relative <files-blend-relative_paths>` to the current blend-file.
   Make Paths Absolute
      Make all paths to external files absolute (= full path from the system's root).
   Report Missing Files
      This option is useful to check if there are links to unpacked files that no longer exist.
      After selecting this option, a warning message will appear in the Info editor's header.
      If no warning is shown, there are no missing external files.
   Find Missing Files
      In case you have broken links in a blend-file, this can help you to fix the problem.
      A File Browser will show up. Select the desired directory (or a file within that directory),
      and a search will be performed in it, recursively in all contained directories.
      Every missing file found in the search will be recovered.
      Those recoveries will be done as absolute paths,
      so if you want to have relative paths you will need to select *Make Paths Relative*.

      .. note::

         Recovered files might need to be reloaded. You can do that one by one, or
         you can save the blend-file and reload it again, so that all external files are reloaded at once.

Clean Up
   Unused Data-Blocks
      Remove unused data-blocks from both the current blend-file and any
      :doc:`Linked Data </files/linked_libraries/link_append>` (cannot be undone).
      See the :ref:`Outliner <bpy.ops.outliner.orphans_purge>` for more information.
   Recursive Unused Data-Blocks
      Remove all unused data-blocks from both the current blend-file and any
      :doc:`Linked Data </files/linked_libraries/link_append>`
      including any indirectly used data-blocks i.e. those only used by unused data-blocks.
   Unused Linked Data-Blocks
      Remove unused data-blocks from only :doc:`Linked Data </files/linked_libraries/link_append>`.
   Recursive Unused Linked Data-Blocks
      Remove all unused data-blocks from only :doc:`Linked Data </files/linked_libraries/link_append>`
      including any indirectly used data-blocks i.e. those only used by unused data-blocks.
   Unused Local Data-Blocks
      Remove all unused data-blocks from only the current blend-file.
   Recursive Unused Local Data-Blocks
      Remove all unused data-blocks from only the current blend-file
      including any indirectly used data-blocks i.e. those only used by unused data-blocks.

-----

.. _startup-file:

Defaults
   This menu manages the startup file which is used to store the default scene,
   workspace, and interface displayed when creating a new file.

   Initially this contains the :doc:`startup scene </editors/3dview/startup_scene>` included with Blender.
   This can be replaced by your own customized setup.

   .. _bpy.ops.wm.save_homefile:

   Save Startup File
      Saves the current blend-file as the startup file.

   .. _bpy.ops.wm.read_factory_settings:

   Load Factory Settings
      Restores the default startup file and preferences.

   When an :doc:`/advanced/app_templates` is in use the following operators are shown:

   Load Factory Blender Settings
      Loads the default settings to the original Blender settings without
      the changes made from the current application template.
   Load Factory (Application Template Name) Settings
      Loads the default settings to the original application template.

   .. seealso:: :ref:`prefs-menu`.

-----

Quit :kbd:`Ctrl-Q`
   Closes Blender. The current scene is saved to a file called "quit.blend" in Blender's temporary directory
   (which can be found on the "File Paths" tab of the :doc:`Preferences </editors/preferences/file_paths>`).


Edit Menu
---------

Undo, Redo, Undo History
   See :doc:`/interface/undo_redo`.
Adjust Last Operation, Repeat Last, Repeat History
   See :doc:`/interface/undo_redo`.
Menu Search
   Find a menu based on its name.
Operator Search
   Execute an operator based on its name (:ref:`Developer Extras <bpy.types.PreferencesView.show_developer_ui>` only).
Rename Active Item
   Rename the active object or node;
   see :ref:`Rename tool <tools_rename-active>` for more information.
Batch Rename
   Renames multiple data types at once;
   see :ref:`Batch Rename tool <bpy.ops.wm.batch_rename>` for more information.

.. _bpy.types.ToolSettings.lock_object_mode:

Lock Object Modes
   Prevents selecting objects that are in a different mode than the current one.

   .. note::

      This option can prevent accidental mode changes, such as when you're
      trying to select a bone in Pose Mode to animate it, but instead
      click a piece of background scenery (which would normally select that
      piece and switch to Object Mode).

      You may want to disable *Lock Object Modes* for example when weighting rigged objects
      or sculpting/painting where you intentionally want to switch between objects in different modes.

Preferences :kbd:`Ctrl-Comma`
   Open the :doc:`Preferences window </editors/preferences/index>`.


.. _topbar-render:

Render Menu
-----------

Render Image :kbd:`F12`
   Render the active scene at the current frame.
Render Animation :kbd:`Ctrl-F12`
   Render the animation of the active scene.

   .. seealso::

      - :doc:`Rendering Animations </render/output/animation>` for details.
Render Audio
   Mix the scene's audio to a sound file.

   .. seealso::

      - :doc:`Rendering audio </render/output/audio/introduction>` for details.
View Render :kbd:`F11`
   Show the Render window. (Press again to switch back to the main Blender window.)

.. _topbar-render-view_animation:

View Animation :kbd:`Ctrl-F11`
   Playback rendered animation in a separate player.

   .. seealso::

      - :ref:`Animation player <bpy.ops.render.play_rendered_anim>` for details.
      - :ref:`Preferences <bpy.types.PreferencesFilePaths.animation_player_preset>` for selecting a
        different animation player than the default one.
Lock Interface
   Lock interface during rendering in favor of giving more memory to the renderer.


.. _topbar-window:

Window Menu
-----------

New Window
   Create a new window by copying the current window.
New Main Window
   Create a new window with its own workspace and scene selection.
Toggle Window Fullscreen
   Toggle the current window fullscreen.
Next Workspace
   Switch to the next workspace.
Previous Workspace
   Switch to the previous workspace.

.. _bpy.types.Screen.show_statusbar:

Show Status Bar
   Choose whether the :doc:`Status Bar </interface/window_system/status_bar>`
   at the bottom of the window should be displayed.

.. _bpy.ops.screen.screenshot:

Save Screenshot
   Capture a picture of the current Blender window.
   A File Browser will open to choose where the screenshot is saved.

.. _bpy.ops.screen.screenshot_area:

Save Screenshot (Editor)
   Capture a picture of the selected Editor.
   Select the Editor by clicking :kbd:`LMB` within its area after running the operator.
   A File Browser will open to choose where the screenshot is saved.


Help Menu
---------

See :ref:`help-menu`.


Workspaces
==========

.. figure:: /images/interface_window-system_topbar_workspaces.png
   :align: center

This set of tabs is used to switch between :doc:`Workspaces </interface/window_system/workspaces>`,
which are essentially predefined window layouts.


Scenes & Layers
===============

.. figure:: /images/interface_window-system_topbar_scenes-layers.png
   :align: center

These :ref:`data-block menus <ui-data-block>` are used to select
the current :doc:`Scene </scene_layout/scene/index>` and :doc:`View Layer </scene_layout/view_layers/index>`.


## Workspaces

.. _bpy.ops.workspace:
.. _bpy.types.Window.workspace:

**********
Workspaces
**********

Workspaces are essentially predefined window layouts.
Each Workspace consists of a set of :doc:`Areas </interface/window_system/areas>`
containing :doc:`Editors </editors/index>`, and is geared towards a specific task such as
modeling, animating, or scripting. You'll typically switch between
multiple Workspaces while working on a project.

.. figure:: /images/interface_window-system_workspaces_screen.png
   :align: center

   Workspaces are located at the Topbar.


.. _workspaces-controls:
.. _bpy.ops.screen.workspace_cycle:

Controls
========

Tabs
   Click on the tabs to switch between the workspaces.
   You can also use the keyboard shortcuts :kbd:`Ctrl-PageUp` and :kbd:`Ctrl-PageDown`.
   Double-click a tab to rename the workspace.

.. _bpy.ops.workspace.add:

Add ``+``
   Click on the *Add* button to add a new workspace.
Context menu :kbd:`RMB`
   The context menu contains options to duplicate, delete and reorder workspaces.


Default Workspaces
==================

Blender's default startup shows the "Layout" workspace in the main area.
This workspace is a general workspace to preview your scene
and contains the following Editors:

- :doc:`3D Viewport </editors/3dview/introduction>` on top left.
- :doc:`Outliner </editors/outliner/introduction>` on top right.
- :doc:`Properties </editors/properties_editor>` on bottom right.
- :doc:`Timeline </editors/timeline>` on bottom left.

.. figure:: /images/interface_window-system_workspaces_layout.png
   :align: center

   Blender's 'Layout' Workspace with four editors.

   3D Viewport (yellow), Outliner (green), Properties (blue) and Timeline (red).

Blender also has several other workspaces added by default:

:Modeling: For modification of geometry by modeling tools.
:Sculpting: For modification of meshes by sculpting tools.
:UV Editing: For mapping of image texture coordinates to 3D surfaces.
:Texture Paint: For coloring image textures in the 3D Viewport.
:Shading: For specifying material properties for rendering.
:Animation: For making properties of objects dependent on time.
:Rendering: For viewing and analyzing rendering results.
:Compositing: For combining and post-processing of images and rendering information.
:Geometry Nodes: For procedural modeling using :doc:`/modeling/geometry_nodes/index`.
:Scripting: For interacting with Blender's Python API and writing scripts.


Additional Workspaces
---------------------

Blender has a couple additional Workspaces to choose from when adding a new Workspace:


.. rubric:: 2D Animation

:2D Animation: General workspace to work with Grease Pencil.
:2D Full Canvas: Similar to "2D Animation" but contains a larger canvas.


.. rubric:: VFX

:Masking: For creating 2D masks for compositing or video editing.
:Motion Tracking: For calculating camera motion and stabilizing video footage.


.. rubric:: Video Editing

:Video Editing: For sequencing together media into one video.


Save and Override
=================

The workspaces are saved in the blend-file.
When you open a file, enabling :ref:`Load UI <file-load-ui>` in the File Browser indicates that Blender should
use the file's screen layout rather than the current one.

A custom set of workspaces can be saved as a part of the :doc:`/getting_started/configuration/defaults`.


Workspace Settings
==================

.. reference::

   :Editor:    :doc:`/editors/properties_editor`
   :Panel:     :menuselection:`Tool tab --> Workspace`

Pin Scene
   When enabled, the current workspace will remember the currently selected scene.
   Then, whenever you activate the workspace, it'll automatically switch back to that scene.

.. _bpy.types.WorkSpace.object_mode:

Mode
   Switch to this :doc:`Mode </editors/3dview/modes>` when activating the workspace.


.. _bpy.ops.wm.owner_enable:
.. _bpy.ops.wm.owner_disable:
.. _bpy.types.WorkSpace.use_filter_by_owner:

Filter Add-ons
   Determines which :doc:`add-ons </addons/index>` are enabled in the active workspace.
   When unchecked, the global add-ons will be used.
   When checked, you can enable individual add-ons in the list below.


