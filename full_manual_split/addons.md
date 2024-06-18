# Index for addons

- [Index](#Index)
- [Index](#Index)
- [Vr Scene Inspection](#Vr-Scene-Inspection)
- [Copy Global Transform](#Copy-Global-Transform)
- [Index](#Index)
- [Anim Bvh](#Anim-Bvh)
- [Curve Svg](#Curve-Svg)
- [Index](#Index)
- [Mesh Uv Layout](#Mesh-Uv-Layout)
- [Scene Fbx](#Scene-Fbx)
- [Scene Gltf2](#Scene-Gltf2)
- [Index](#Index)
- [Node Wrangler](#Node-Wrangler)
- [Index](#Index)
- [Ui Translations](#Ui-Translations)


## Index

.. index:: Add-ons

###########
  Add-ons
###########

.. important::

   This is work in progress.

   Documentation might be outdated and on some pages images, videos, and links aren't added yet.


Add-ons Category Listings
=========================

.. Editor notes:

   - Note that only add-ons released in Blender are included in this section.
   - This section lists the add-ons categories in the same order they appear in Blender
   - Each subsection contains the documentation files for the related add-ons.

.. toctree::
   :maxdepth: 1

   3d_view/index.rst
   animation/index.rst
   import_export/index.rst
   node/index.rst
   system/index.rst


## Index


###########
  3D View
###########

These add-ons relate to drawing or manipulating the 3D Viewport.

.. toctree::
   :maxdepth: 1

   vr_scene_inspection.rst


## Vr Scene Inspection


*******************
VR Scene Inspection
*******************

The :abbr:`VR (Virtual Reality)` Scene Inspection add-on exposes and extends
the native virtual reality features of Blender in the user interface.
The feature set is limited to scene inspection use cases.
More advanced use cases may be enabled through further development inside of Blender.

VR support in Blender is based on the OpenXR specification and requires some set up steps.
These are explained in the :ref:`Head-Mounted Displays (HMD) <hardware-head-mounted-displays>` section.


Activation
==========

- Open Blender and go to Preferences then the Add-ons tab.
- Click 3D View then VR Scene Inspection to enable the script.


Interface
=========

Located in the :menuselection:`3D Viewport --> Sidebar --> VR tab`.

.. figure:: /images/addons_3d-view_vr-scene-inspection_interface.jpg
   :width: 220px


VR Session
----------

.. figure:: /images/addons_3d-view_vr-scene-inspection_vr-session.jpg
   :align: right
   :width: 220px

Start VR Session
   Try to set up a connection to the OpenXR platform to share the viewport with
   an :ref:`HMD <hardware-head-mounted-displays>`.
Tracking
   Positional
      Only track rotational changes of the head, do not allow the HMD
      to affect the location of the viewer in virtual space.
   Absolute
      Skip eye offsets that are normally added for placing the viewer
      exactly at landmarks. This allows the tracking origin to be defined
      independently of the HMD position.
Use Controller Actions
   Enable default controller actions for viewport navigation,
   controller tracking, and haptics.


View
----

.. figure:: /images/addons_3d-view_vr-scene-inspection_view.jpg
   :align: right
   :width: 220px

Show
   Floor
      Set visibility of the ground plane in the VR view.
   Annotations
      Set visibility of annotation strokes in the VR view.
   Selection
      Set visibility of selection outlines in the VR view.
   Controllers
      Set visibility of VR motion controllers.
      Requires enabling the `Use Controller Actions <VR Session_>`_ option.
   Custom Overlays
      Set visibility of custom operator drawing (e.g. default teleport beam).
   Object Extras
      Set visibility of object extras, including empties, lights, and cameras.
   Object Type Visibility ``👁``
      Set visibility of objects by type.
Controller Style
   Preferred visualization of VR motion controllers.
Clip Start/End
   Clipping values of the VR view, :ref:`as in the 3D Viewport <bpy.types.SpaceView3D.clip_start>`.


Landmarks
---------

Landmarks are used to store reusable base poses (position and rotation) for the viewer in the virtual space.
In addition, a base viewer reference scale can be set for landmarks of types Custom Object and Custom Pose.

.. figure:: /images/addons_3d-view_vr-scene-inspection_landmarks.jpg
   :align: right
   :width: 220px

Landmark
   A :ref:`list view <ui-list-view>`.

   Selected Landmark
      Defines which landmark's settings are shown below the list.
      Changing the selected landmark does not have an influence on the VR view.
   Activate ``〇``
      Activates a landmark, making it change the base pose of the VR view.
   Add ``+``
      Create a landmark.
   Remove ``-``
      Delete the selected landmark.
   Add from Session ``⊕``
      Create a landmark from the viewer pose of the running VR session.
   Landmark Controls ``v``
      Add Camera and VR Landmark from Session
         Create a new camera and landmark from the viewer pose of the running VR session.
      Add Landmark from Camera
         Add a new landmark from the active camera object.
      Update Custom Landmark
         Update the selected landmark from the current VR viewer pose.
      Cursor to Landmark
         Move the 3D Cursor to the selected landmark.
      Scene Camera to Landmark
         Position the scene camera at the selected landmark.
      Camera from Landmark
         Create a new camera from the selected landmark.
Type
   Scene Camera
      Follow the scene's :ref:`active camera <bpy.types.Scene.camera>`
      to define the base pose of the viewer.
   Custom Object
      Set an arbitrary object to define the base pose of the viewer.
   Custom Pose
      Manually define a position and rotation to use as the base pose of the viewer.


Action Maps
-----------

.. figure:: /images/addons_3d-view_vr-scene-inspection_action-maps.jpg
   :align: right
   :width: 220px

Gamepad
   Use input from a gamepad (Microsoft Xbox Controller) instead of motion controllers for
   VR actions such as viewport navigation.
Extensions
   Enable additional controller bindings to ensure correct input-to-action mappings.
   Note that a given extension may not be supported by all
   :ref:`VR platforms <hardware-head-mounted-displays>`.

   HP Reverb G2
      Enable bindings for the HP Reverb G2 controllers.
   HTC Vive Cosmos
      Enable bindings for the HTC Vive Cosmos controllers.
   HTC Vive Focus
      Enable bindings for the HTC Vive Focus 3 controllers.
   Huawei
      Enable bindings for the Huawei controllers.


Viewport Feedback
-----------------

.. figure:: /images/addons_3d-view_vr-scene-inspection_viewport-feedback.jpg
   :align: right
   :width: 220px

Show VR Camera
   Draw an indicator of the current VR viewer pose (location and rotation in the virtual space)
   in the current 3D Viewport.
Show VR Controllers
   Draw indicators of tracked VR motion controllers in the current 3D viewport.
   Requires enabling the `Use Controller Actions <VR Session_>`_ option.
Show Landmarks
   Draw `landmark <Landmarks_>`_ indicators in the current 3D Viewport.
Mirror VR Session
   Make the current 3D Viewport follow the perspective of the VR view.


.. reference::

   :Category: 3D View
   :Description: View the viewport with virtual reality glasses (head-mounted displays).
   :Location: :menuselection:`3D Viewport --> Sidebar --> VR tab`
   :File: viewport_vr_preview folder
   :Author: Julian Eisel, Sebastian Koenig, Peter Kim
   :Maintainer: Julian Eisel, Peter Kim
   :License: GPL
   :Support Level: Official
   :Note: This add-on is bundled with Blender.


## Copy Global Transform


*********************
Copy Global Transform
*********************

Copy and paste object and bone transforms with ease.

When copying, the global (:term:`World Space`) transform is placed on the
clipboard. This can then be pasted onto any object or bone, at the current frame
or at another one.

Since the transform is placed on the clipboard as text, you can even copy-paste
it into an instant messenger and send it to someone else.


Activation
==========

- Open Blender and go to Preferences then the Add-ons tab.
- Click Animation then Copy Global Transform to enable the add-on.


Interface
=========

.. figure:: copy_global_transform-main.webp
   :align: right

Located in :menuselection:`3D Viewport --> N-panel --> Animation tab`.

The figure on the right shows the main functionality of the Copy Global
Transform panel. The collapsed panels are described each in their own section
below.

Description
===========

Copy
   Inspects the active Object (in Object mode) or Bone (in Pose mode) and places
   its current global transform onto the clipboard as a matrix.

Paste
   Takes the copied global transform and applies it to the active Object or
   Bone. This is done by **adjusting its location, rotation, and scale properties**.

Mirrored
   Same as 'Paste' above, but then mirrored relative to some other object or
   bone. This can be useful, for example, to copy the foot position of one foot
   to the other. See :ref:`copy-global-transform-mirror-options` below.

Paste to Selected Keys
   Paste as described above and additionally use auto-keying to update one or
   more frames. The key selection is used to tell Blender *which frames* this
   should happen on; it does not influence which parts of the transform are
   keyed. *What* is keyed is determined by the active keying set.

Paste and Bake
   Almost the same as *Paste to Selected Keys*. Instead of only pasting on the
   selected keys, *Paste and Bake* will paste & auto-key on every frame between
   the first and last selected keys.

.. _copy-global-transform-mirror-options:

Mirror Options
++++++++++++++

.. figure:: copy_global_transform-mirror_options.webp
   :align: right

The copied transform can be mirrored relative to an object or a :term:`Bone`.
This requires choosing that object or bone first.

Armature + Bone
   Choosing an :term:`Armature` object as mirror object will show the bone
   selector. You can use that to pick the bone to use as mirror. This will
   always use the named bone on that specific armature object.
Bone Only
   When you choose *no mirror object* at all, you can still choose a *bone
   name*. This is used for mirroring against a bone in the *active armature*.
   This can be useful to mirror bone transforms relative to the 'chest' bone
   of the active character.
Object Only
   This will just mirror relative to the chosen object.

After pasting with 'Paste Mirrored', the mirror axes can be chosen in the
:ref:`redo panel <bpy.ops.screen.redo_last>`.


.. _copy-global-transform-fix-to-camera:

Fix to Camera
+++++++++++++

.. figure:: copy_global_transform-fix_to_camera.webp
   :align: right

Also known as "bake to camera", this operator will ensure selected objects/bones
remain static (relative to the camera) on unkeyed frames.

This is done by generating new keys. These keys will be of :ref:`type
'Generated' <keyframe-type>` so that it remains clear which keys were manually
created, and which were generated. This way the tool can be re-run to
re-generate the keys.

1. Ensure your animation is keyed using constant interpolation. If this is not
   the case yet, bake your animation (at least the transform channels). This
   tool does _not_ work with the :ref:`"Stepped" F-Curve modifier <bpy.types.FModifierStepped>`
2. Choose which of the Location/Rotation/Scale channels you want to fix to the
   camera. When unsure, make sure they are all checked.
3. Press the "Fix to Camera" button.

To undo the effect of the "Fix to Camera" operator, click on the trash bin
button. That will remove all the generated keys in either the scene range or the
frame range.

The tool operates on the scene frame range, or on the preview range if that is
active. Keys outside that range are ignored, both when fixing to the camera and
when removing generated keys.

.. warning::

   This tool assumes that *all* keys with type 'Generated' are equal. It will
   overwrite them (or remove them, depending on which button you press).


Relative Copy-Paste
+++++++++++++++++++

.. figure:: copy_global_transform-relative.webp
   :align: right

The "Relative" panel has copy/paste buttons that work relative to a chosen
object. When copying, the world-space transform is determined, and then adjusted
to become relative to the world-space transform of the chosen object. When
pasting, this happens in reverse.

If no object is chosen, the copy/paste will happen relative to the active scene
camera. What is the active scene camera is determined for every action, so when
you paste it can be different from when you copied. This can help to keep an
object visually in the same place when switching cameras, or when switching
between scenes.


Limitations
===========

Pasting a transform adjusts the Object/Bone's location, rotation, and
scale. This means that when copying a skewed transform, this skew is lost.

If there are constraints on the Object/Bone, the resulting visual transformation
may not be the same as the pasted one. To give a concrete example: if you have a
constraint that adds a rotation, it will always add that rotation on top of the
pasted transform.


.. seealso::

   :doc:`/animation/armatures/posing/editing/pose_library` for a way to manage
   and share entire poses.

.. reference::

   :Category: Animation
   :Description: Simple add-on for copying world-space transforms.
   :Location: :menuselection:`3D Viewport --> N-panel --> Animation tab`
   :File: copy_global_transform.py
   :Author: Sybren A. Stüvel
   :Maintainer: Sybren A. Stüvel
   :License: GPL 2+
   :Support Level: Official
   :Note: This add-on is bundled with Blender.


## Index


#############
  Animation
#############

These add-ons relate to helper tools for the animation process and animation.

.. toctree::
   :maxdepth: 1

   copy_global_transform.rst


## Anim Bvh


******************************
BioVision Motion Capture (BVH)
******************************

.. reference::

   :Category:  Import-Export
   :Menu:      :menuselection:`File --> Import/Export --> Motion Capture (.bvh)`

Imports or exports bvh-files or files with BioVision Hierarchical data
or data of a skeleton (rig) including its animation.
Useful for importing data from motion capture devices.


Properties
==========

Import
------

Target
   The motion capture data type.

   :Armature: The bvh-file contains an animated rigged skeleton such as a walking motion capture.
   :Object: The bvh-file contains a static (not animated) mesh object such as a character model.


Transform
^^^^^^^^^

Scale
   Factor to increase the physical size of the BVH.
Rotation
   Rotation order of the BVH.
Forward / Up
   Since many applications use a different axis for pointing upwards, these are axis conversion for these settings,
   Forward and up axes -- By mapping these to different axes you can convert rotations
   between applications default up and forward axes.

   Blender uses Y forward, Z up (since the front view looks along the +Y direction).
   For example, its common for applications to use Y as the up axis, in that case -Z forward, Y up is needed.


Animation
^^^^^^^^^

Start Frame
   The start frame, in Blender, to start playback of the BVH animation.
Scale FPS
   Scales the frame rate from the BVH file to the scene frame rate set in Blender,
   otherwise each BVH frame maps directly to a frame in Blender.
Loop
   Cycles the animation playback.
Update Scene FPS
   Set the scene's frame rate to match the frame rate of the BVH file.
Update Scene Duration
   Extend the scene's duration to match the BVH's duration.


Export
------

Transform
^^^^^^^^^

Scale
   Factor to increase the physical size of the BVH.
Rotation
   Rotation order of the BVH.
Root Translation Only
   Only write the translation animation channels for the root bone.


Animation
^^^^^^^^^

Start / End
   Sets the range of animation to export to the BVH file.


## Curve Svg


******************************
Scalable Vector Graphics (SVG)
******************************

.. reference::

   :Category:  Import-Export
   :Menu:      :menuselection:`File --> Import --> Scalable Vector Graphics (.svg)`

.. note::

   Currently the script allows only importing and is limited to path geometry only.


Properties
==========

This add-on does not have any properties.


Usage
=====

Todo.


## Index


#################
  Import-Export
#################

.. toctree::
   :maxdepth: 1
   :name: addons-io

   anim_bvh.rst
   scene_fbx
   curve_svg.rst
   mesh_uv_layout.rst
   scene_gltf2.rst


## Mesh Uv Layout


*********
UV Layout
*********

.. reference::

   :Category:  Import-Export
   :Menu:      :menuselection:`UV Editor --> UV --> Export UV Layout`


Usage
=====

Using your favorite image painting program, you could use an exported UV layout to create a texture.
Then save your changes, and back in Blender, use the :menuselection:`Image --> Open`
to load it as your UV image for the mesh in Edit Mode for the desired (and active) UV map.

As a way of communicating to an artist who is painting your UV Texture for you,
Blender has a tool called *UV Layout* (:menuselection:`UV Editor --> UV --> Export UV Layout`)
that saves an image as a ``Targa`` (``.tga``), ``EPS``, or ``SVG`` format for the object you have selected.

The image will be lines defining the UV edges that are within the image area of the UV mapping area.
Edges outside the boundary, even if selected, will not be shown in the saved graphic.
The artist will use this as a transparent layer in their paint program as a guide when painting your texture.
The example below shows Blender in the background, and the Gimp working on the texture,
using the saved layout as a guide. Note that ``targa`` format supports the Alpha channel,
so you can paint transparent areas of the mesh. For using images as textures, see the page on
:doc:`Image Textures </render/materials/legacy_textures/types/image_movie>`.

.. list-table::

   * - .. figure:: /images/addons_import-export_mesh-uv-layout_uv-editor.png
          :width: 320px

          A UV layout in the UV Editor.

     - .. figure:: /images/addons_import-export_mesh-uv-layout_export.png
          :width: 320px

          A UV layout in a paint program.


Properties
==========

.. figure:: /images/addons_import-export_mesh-uv-layout_export-panel.png

   Export options.

All UVs
   if disabled, then only the UV faces selected will be outlined.
Modified
   Export UVs from the modified mesh.
Format
   Select the type of image file to save (``.png``, ``.eps``, ``.svg``).
Size
   Select the size of the image in pixels.
Fill Opacity
   Set the opacity of the fill.


## Scene Fbx


***
FBX
***

.. reference::

   :Category:  Import-Export
   :Menu:      :menuselection:`File --> Import/Export --> FBX (.fbx)`


Usage
=====

This format is mainly use for interchanging character animations between applications
and is supported by applications such as Cinema4D, Maya, Autodesk 3ds Max, Wings3D and
engines such as Unity3D, Unreal Engine 3/UDK and Unreal Engine 4.

The exporter can bake mesh modifiers and animation into the FBX so the final result looks the same as in Blender.

.. note::

   - Bones would need to get a correction to their orientation
     (FBX bones seems to be -X aligned, Blender's are Y aligned),
     this does not affect skinning or animation, but imported bones in other applications will look wrong.
   - Animations (FBX AnimStacks, Blender actions) **are not linked** to their object,
     because there is no real way to know which stack to use as 'active' action for a given object, mesh or bone.
     This may be enhanced to be smarter in the future, but it's not really considered urgent,
     so for now you'll have to link actions to objects manually.
   - Armature instances **are not supported**.

.. note::

   - Bones' orientation importing is complex, you may have to play a bit with
     related settings until you get the expected results.
   - Animation support is minimal currently, we read all curves as if they were 'baked' ones
     (i.e. a set of close keyframes with linear interpolation).
   - Imported actions are linked to their related object, bone or shape key, on a 'first one wins' basis.
     If you export a set of them for a single object, you'll have to reassign them yourself.

.. note:: Saving Just Animations

   The FBX file format supports files that only contain takes.
   It is up to you to keep track of which animation belongs to which model.
   The animation that will be exported is the currently selected action within the Action editor.
   To reduce the file size, turn off the exporting of any parts you do not want and disable *All Actions*.
   For armature animations typically you just leave the armature enabled which is necessary for
   that type of animation. Reducing what is output makes the export and future import much faster.
   Normally each action will have its own name but the current or
   only take can be forced to be named "Default Take". Typically, this option can remain off.

.. note::

   Blender now only supports complex node-based shading. FBX having a fixed pipeline-like support of materials,
   this add-on converts between them.


Properties
==========

Import
------

Include
^^^^^^^

Import Normals
   TODO.
Import Subdivision Surface
   Todo.
Import User Properties
   TODO.
Import Enums as Strings
   TODO.
Image Search
   TODO.


Transform
^^^^^^^^^

Scale
   Todo.
Decal Offset
   TODO.

Manual Orientation
   TODO.
Forward / Up Axis
   Since many applications use a different axis for 'Up', these are axis conversion for these settings,
   Forward and Up axes -- By mapping these to different axes you can convert rotations
   between applications default up and forward axes.

   Blender uses Y Forward, Z Up (since the front view looks along the +Y direction).
   For example, its common for applications to use Y as the up axis, in that case -Z Forward, Y Up is needed.
Apply Transform
   TODO.
Use Pre/Post Rotation
   TODO.


Animation
^^^^^^^^^

TODO.

Animation Offset
   TODO.


Armature
^^^^^^^^

Ignore Leaf Bones
   TODO.
Force Connect Children
   TODO.
Automatic Bone Orientation
   TODO.
Primary/Secondary Bone Axis
   TODO.


Export
------

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

   Embed Textures
      TODO.
Batch Mode
   When enabled, export each group or scene to a file.

   Group/Scene
      Choose whether to batch export groups or scenes to files.
      Note, when Group/Scene is enabled, you cannot use the animation option *Current Action*
      since it uses scene data and groups are not attached to any scenes.
      Also note, when Group/Scene is enabled you must include the armature objects
      in the group for animated actions to work.
   Batch Own Directory
      When enabled, each file is exported into its own directory,
      this is useful when using the *Copy Images* option. So each directory contains
      one model with all the images it uses. Note, this requires a full Python installation.
      If you do not have a full Python installation, this button will not be shown.


Include
^^^^^^^

Selected Objects
   Only export the selected objects. Otherwise export all objects in the scene.
   Note, this does not apply when batch exporting.
Active Collection
   Todo.
Object Types
   Enable/Disable exporting of respective object types.
Custom Properties
   TODO.


Transform
^^^^^^^^^

Scale
   Scale the exported data by this value. 10 is the default
   because this fits best with the scale most applications import FBX to.
Apply Scaling
   TODO.
Forward / Up
   Since many applications use a different axis for 'Up', these are axis conversions for Forward and
   Up axes -- By mapping these to different axes you can convert rotations between applications
   default up and forward axes.

   Blender uses Y Forward, Z Up (since the front view looks along the +Y direction).
   For example, its common for applications to use Y as the up axis, in that case -Z Forward, Y Up is needed.
Apply Unit
   TODO.
Apply Transform
   TODO.


Geometry
^^^^^^^^

Smoothing
   TODO.
Export Subdivision Surface
   Todo.
Apply Modifiers
   Export objects using the evaluated mesh, meaning the resulting mesh after all
   :doc:`Modifiers </modeling/modifiers/index>` have been calculated.
Loose Edges
   TODO.
Tangent Space
   TODO.


Armatures
^^^^^^^^^

Primary/Secondary Bone Axis
   TODO.
Armature FBXNode Type
   TODO.
Only Deform Bones
   TODO.
Add Leaf Bones
   TODO.


Bake Animation
^^^^^^^^^^^^^^

TODO.

Key All Bones
   TODO.
NLA Strips
   TODO.
All Actions
   Export all actions compatible with the selected armatures
   start/end times which are derived from the keyframe range of each action.
   When disabled only the currently assigned action is exported.
Force Start/End Keying
   TODO.
Sampling Rate
   TODO.
Simplify
   TODO.


Compatibility
=============

Import
------

Note that the importer is a new addition and lacks many features the exporter supports.

- binary FBX files only.
- Version 7.1 or newer.


Missing
^^^^^^^

- Mesh: shape keys.


Export
------

NURBS surfaces, text3D and metaballs are converted to meshes at export time.


Missing
^^^^^^^

Some of the following features are missing because they
are not supported by the FBX format, others may be added later.

- Object instancing -- exported objects do not share data,
  instanced objects will each be written with their own data.
- Material textures
- Vertex shape keys -- FBX supports them but this exporter does not write them yet.
- Animated fluid simulation -- FBX does not support this kind of animation.
  You can however use the OBJ exporter to write a sequence of files.
- Constraints -- The result of using constraints is exported as a keyframe animation
  however the constraints themselves are not saved in the FBX.
- Instanced objects -- At the moment instanced objects are only written in static scenes
  (when animation is disabled).


## Scene Gltf2


********
glTF 2.0
********

.. reference::

   :Category: Import-Export
   :Menu:      :menuselection:`File --> Import/Export --> glTF 2.0 (.glb, .gltf)`


Usage
=====

glTF™ (GL Transmission Format) is used for transmission and loading of 3D models
in web and native applications. glTF reduces the size of 3D models and
the runtime processing needed to unpack and render those models.
This format is commonly used on the web, and has support in various 3D engines
such as Unity3D, Unreal Engine 4, and Godot.

This importer/exporter supports the following glTF 2.0 features:

- Meshes
- Materials (Principled BSDF) and Shadeless (Unlit)
- Textures
- Cameras
- Punctual lights (point, spot, and directional)
- Extensions (listed below)
- Extras (custom properties)
- Animation (keyframe, shape key, and skinning)


Meshes
======

glTF's internal structure mimics the memory buffers commonly used by graphics chips
when rendering in real-time, such that assets can be delivered to desktop, web, or mobile clients
and be promptly displayed with minimal processing. As a result, quads and n-gons
are automatically converted to triangles when exporting to glTF.
Discontinuous UVs and flat-shaded edges may result in moderately higher vertex counts in glTF
compared to Blender, as such vertices are separated for export.
Likewise, curves and other non-mesh data are not preserved,
and must be converted to meshes prior to export.

GPU Instances
-------------

When the option is enable in Exporter, instances are exported using the ``EXT_mesh_gpu_instancing`` extension.
There are some limitations, at export:

- Instances must be meshes, and don't have any children themselves
- Instances must all be children of the same object.
- This extension doesn't manage material variation. That means that the generated file may include all instances with
  same materials.
- Instances detected are objects sharing the same mesh data.

At import, instances are created by creating objects sharing the same mesh data.

Materials
=========

The core material system in glTF supports a metal/rough :abbr:`PBR (Physically Based Rendering)` workflow
with the following channels of information:

- Base Color
- Metallic
- Roughness
- Baked Ambient Occlusion
- Normal Map (tangent space, +Y up)
- Emissive

Some additional material properties or types of materials can be expressed using glTF extensions.
The complete list can be found in `Extensions`_ part of this documentation.

.. figure:: /images/addons_import-export_scene-gltf2_material-channels.jpg

   An example of the various image maps available in the glTF 2.0 core format. This is
   the `water bottle sample model <https://github.com/KhronosGroup/glTF-Sample-Models/tree/master/2.0/WaterBottle>`__
   shown alongside slices of its various image maps.


Imported Materials
------------------

The glTF material system is different from Blender's own materials. When a glTF file is imported,
the add-on will construct a set of Blender nodes to replicate each glTF material as closely as possible.

The importer supports Metal/Rough PBR (core glTF), Spec/Gloss PBR (``KHR_materials_pbrSpecularGlossiness``)
and some extension materials. The complete list can be found in `Extensions`_ part of this documentation.

.. tip::

   Examining the result of the material import process is a good way to see examples of
   the types of material nodes and settings that can be exported to glTF.


Exported Materials
------------------

The exporter supports Metal/Rough PBR (core glTF) and Shadeless (``KHR_materials_unlit``) materials.
It will construct a glTF material based on the nodes it recognizes in the Blender material.
The material export process handles the settings described below.

.. note::

   When image textures are used by materials, glTF requires that images be in PNG or JPEG format.
   The add-on will automatically convert images from other formats, increasing export time.


Base Color
^^^^^^^^^^

The glTF base color is determined by looking for a Base Color input on a Principled BSDF node.
If the input is unconnected, the input's default color (the color field next to the unconnected socket)
is used as the Base Color for the glTF material.

.. figure:: /images/addons_import-export_scene-gltf2_material-base-color-solid-green.png

   A solid base color can be specified directly on the node.

If an Image Texture node is found to be connected to the Base Color input,
that image will be used as the glTF base color.

.. figure:: /images/addons_import-export_scene-gltf2_material-base-color-image-hookup.png

   An image is used as the glTF base color.


Metallic and Roughness
^^^^^^^^^^^^^^^^^^^^^^

These values are read from the Principled BSDF node. If both of these inputs are unconnected,
the node will display sliders to control their respective values between 0.0 and 1.0,
and these values will be copied into the glTF.

When using an image, glTF expects the metallic values to be encoded in the blue (``B``) channel,
and roughness to be encoded in the green (``G``) channel of the same image.
If images are connected to the Blender node in a manner that does not follow this convention,
the add-on may attempt to adapt the image to the correct form during exporting (with an increased export time).

In the Blender node tree, it is recommended to use a Separate RGB node
to separate the channels from an Image Texture node, and
connect the green (``G``) channel to Roughness, and blue (``B``) to Metallic.
The glTF exporter will recognize this arrangement as matching the glTF standard, and
that will allow it to simply copy the image texture into the glTF file during export.

The Image Texture node for this should have its *Color Space* set to Non-Color.

.. figure:: /images/addons_import-export_scene-gltf2_material-metal-rough.png

   A metallic/roughness image connected in a manner consistent with the glTF standard,
   allowing it to be used verbatim inside an exported glTF file.


Baked Ambient Occlusion
^^^^^^^^^^^^^^^^^^^^^^^

glTF is capable of storing a baked ambient occlusion map.
Currently there is no arrangement of nodes that causes Blender
to use such a map in exactly the same way as intended in glTF.
However, if the exporter finds a custom node group by the name of ``glTF Material Output``, and
finds an input named ``Occlusion`` on that node group,
it will look for an Image Texture attached there to use as the occlusion map in glTF.
The effect need not be shown in Blender, as Blender has other ways of showing ambient occlusion,
but this method will allow the exporter to write an occlusion image to the glTF.
This can be useful to real-time glTF viewers, particularly on platforms where there
may not be spare power for computing such things at render time.

.. figure:: /images/addons_import-export_scene-gltf2_material-occlusion-only.png

   A pre-baked ambient occlusion map, connected to a node that doesn't render but will export to glTF.

.. tip::

   If you enable Shader Editor Add-ons in preferences, you will be able to add this custom node group from Menu:
   Add > Output > glTF Material Output

   .. figure:: /images/addons_import-export_scene-gltf2_addon-preferences-shader.png

glTF stores occlusion in the red (``R``) channel, allowing it to optionally share
the same image with the roughness and metallic channels.

.. figure:: /images/addons_import-export_scene-gltf2_material-orm-hookup.png

   This combination of nodes mimics the way glTF packs occlusion, roughness, and
   metallic values into a single image.

.. tip::

   The Cycles render engine has a Bake panel that can be used to bake
   ambient occlusion maps. The resulting image can be saved and connected
   directly to the ``glTF Material Output`` node.


Normal Map
^^^^^^^^^^

To use a normal map in glTF, connect an Image Texture node's color output
to a Normal Map node's color input, and then connect the Normal Map normal output to
the Principled BSDF node's normal input. The Image Texture node
for this should have its *Color Space* property set to Non-Color.

The Normal Map node must remain on its default property of Tangent Space as
this is the only type of normal map currently supported by glTF.
The strength of the normal map can be adjusted on this node.
The exporter is not exporting these nodes directly, but will use them to locate
the correct image and will copy the strength setting into the glTF.

.. figure:: /images/addons_import-export_scene-gltf2_material-normal.png

   A normal map image connected such that the exporter will find it and copy it
   to the glTF file.

.. tip::

   The Cycles render engine has a Bake panel that can be used to bake
   tangent-space normal maps from almost any other arrangement of normal vector nodes.
   Switch the Bake type to Normal. Keep the default space settings
   (space: Tangent, R: +X, G: +Y, B: +Z) when using this bake panel for glTF.
   The resulting baked image can be saved and plugged into to a new material using
   the Normal Map node as described above, allowing it to export correctly.

   See: :doc:`Cycles Render Baking </render/cycles/baking>`


Emissive
^^^^^^^^

An Image Texture node can be connected to the Emission input on the Principled BSDF node
to include an emissive map with the glTF material. Alternatively, the Image Texture node
can be connected to an Emission shader node, and optionally combined with properties
from a Principled BSDF node by way of an Add Shader node.

If the emissive map is alone in the material, it is best to set the Base Color default
to black, and the Roughness default to 1.0. This minimizes the influence of the other
channels if they are not needed.

.. figure:: /images/addons_import-export_scene-gltf2_material-emissive.png

   This arrangement is supported for backwards compatibility. It is simpler to use
   the Principled BSDF node directly.

If any component of emissiveFactor is > 1.0, ``KHR_materials_emissive_strength`` extension will be used.


Clearcoat
^^^^^^^^^

When the *Clearcoat* input on the Principled BSDF node has a nonzero default value or
Image Texture node connected, the ``KHR_materials_clearcoat`` glTF extension will be
included in the export. This extension will also include a value or Image Texture
from the *Clearcoat Roughness* input if available.

If Image Textures are used, glTF requires that the clearcoat values be written to
the red (``R``) channel, and *Clearcoat Roughness* to the green (``G``) channel.
If monochrome images are connected, the exporter will remap them to these color channels.

The *Clearcoat Normal* input accepts the same kinds of inputs as the base Normal input,
specifically a tangent-space normal map with +Y up, and a user-defined strength.
This input can reuse the same normal map that the base material is using,
or can be assigned its own normal map, or can be left disconnected for a smooth coating.

All Image Texture nodes used for clearcoat shading should have their *Color Space* set to Non-Color.

.. figure:: /images/addons_import-export_scene-gltf2_material-clearcoat.png

   An example of a complex clearcoat application that will export correctly to glTF.
   A much simpler, smooth coating can be applied from just the Principled BSDF node alone.

Sheen
^^^^^

If a Sheen Roughness Texture is used, glTF requires the values be written to the alpha (``A``) channel.

.. figure:: /images/addons_import-export_scene-gltf2_material-sheen.png

.. tip::

   Sheen BSDF node is only available on Cycles render engine.
   You may have to temporary switch to Cycles to add this node, and get back to EEVEE.


Specular
^^^^^^^^

When the *Specular IOR Level* or *Specular Tint* input of Principled BSDF node have a non default value or
Image Texture node connected, the ``KHR_materials_specular`` glTF extension will be
included in the export.


Anisotropy
^^^^^^^^^^

Anisotropic textures and data need to be converted at export, and at import.

At import, some nodes are created to manage this conversion

.. figure:: /images/addons_import-export_scene-gltf2_material_anisotropy.png

At export, this exact same nodes are detected, and used to export data.

At export, you can also plug some grayscale textures for *Anisotropic* and *Anisotropic Rotation* sockets.
Then, exporter will convert these texture into a glTF compatible texture.

.. figure:: /images/addons_import-export_scene-gltf2_material_anisotropy-grayscale-texture.png

Note that the *tangent* socket must be linked to a *tangent* node, with UVMap.
The choosen UVMap must be the UVMap of the Normal Map.


Transmission
^^^^^^^^^^^^

When the Transmission input on the Principled BSDF node has a nonzero default value or
Image Texture node connected, the ``KHR_materials_transmission`` glTF extension will be
included in the export. When a texture is used, glTF stores the values in the red (``R``) channel.
The *Color Space* should be set to Non-Color.

Transmission is different from alpha blending, because transmission allows full-strength specular reflections.
In glTF, alpha blending is intended to represent physical materials that are partially missing from
the specified geometry, such as medical gauze wrap. Transmission is intended to represent physical materials
that are solid but allow non-specularly-reflected light to transmit through the material, like glass.

.. tip::

   The material's base roughness can be used to blur the transmission, like frosted glass.

.. tip::

   Typically the alpha blend mode of a transmissive material should remain "Opaque",
   the default setting, unless the material only partially covers the specified geometry.

.. note::

   In real-time engines where transmission is supported, various technical limitations in
   the engine may determine which parts of the scene are visible through the transmissive surface.
   In particular, transmissive materials may not be visible behind other transmissive materials.
   These limitations affect physically-based transmission, but not alpha-blended non-transmissive materials.

.. note::

   If you want to enable refraction on your model, ``KHR_materials_transmission`` must also
   be used in addition with ``KHR_materials_volume``. See the dedicated *Volume* part of
   the documentation.

.. warning::

   Transmission is complex for real-time rendering engines to implement,
   and support for the ``KHR_materials_transmission`` glTF extension is not yet widespread.

IOR
^^^

At import, there are two different situation:

- if ``KHR_materials_ior`` is not set, IOR value of Principled BSDF node is set to 1.5,
  that is the glTF default value of IOR.
- If set, the ``KHR_materials_ior`` is used to set the IOR value of Principled BSDF.

At export, IOR is included in the export only if one of these extensions are also used:

- ``KHR_materials_transmission``
- ``KHR_materials_volume``
- ``KHR_materials_specular``

IOR of 1.5 are not included in the export, because this is the default glTF IOR value.

Volume
^^^^^^

Volume can be exported using a Volume Absorption node, linked to Volume socket of Output node.
Data will be exported using the ``KHR_materials_volume`` extension.

- For volume to be exported, some *transmission* must be set on Principled BSDF node.
- Color of Volume Absorption node is used as glTF attenuation color. No texture is allowed for this property.
- Density of Volume Absorption node is used as inverse of glTF attenuation distance.
- Thickness can be plugged into the Thickness socket of custom group node ``glTF Material Output``.
- If a texture is used for thickness, it must be plugged on (``G``) Green channel of the image.

.. figure:: /images/addons_import-export_scene-gltf2_material-volume.png

glTF Variants
^^^^^^^^^^^^^

.. note::

   For a full Variants experience, you have to enable UI in Add-on preferences

     .. figure:: /images/addons_import-export_scene-gltf2_addon-preferences-variant.png

There are two location to manage glTF Variants in Blender

- In 3D View, on ``glTF Variants`` tab
- For advanced settings, in Mesh Material Properties (see Advanced glTF Variant checks)

The main concept to understand for using Variants,
is that each material slot will be used as equivalent of a glTF primitive.

glTF Variants switching
^^^^^^^^^^^^^^^^^^^^^^^

After importing a glTF file including ``KHR_materials_variants`` extension, all variants can be displayed.

.. figure:: /images/addons_import-export_scene-gltf2_material_variants-switch.png

You can switch Variant, by *selecting* the variant you want to display, then clicking on *Display Variant*.

You can switch to default materials (when no Variant are used), by clicking on *Reset to default*.

glTF Variants creation
^^^^^^^^^^^^^^^^^^^^^^

You can add a new Variant by clicking the ``+`` at right of the Variant list.
Then you can change the name by double-clicking.

After changing Materials in Material Slots, you can assign current materials to the active Variant using
*Assign to Variant*.

You can also set default materials using *Assign as Original*.
These materials will be exported as default material in glTF.
This are materials that will be displayed by any viewer that don't manage ``KHR_materials_variants`` extension.

Advanced glTF Variant checks
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

If you want to check primitive by primitive, what are Variants used, you can go to Mesh Material Properties.

.. figure:: /images/addons_import-export_scene-gltf2_material_variants-detail.png

The *glTF Material Variants* tab refers to the active material Slot and Material used by this slot.
You can see every Variants that are using this material for the given Slot/Primitive.

You can also assign material to Variants from this tab, but recommendation is to perform it from 3D View tab.

Double-Sided / Backface Culling
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

For materials where only the front faces will be visible, turn on *Backface Culling* in
the *Settings* panel of an EEVEE material. When using other engines (Cycles, Workbench)
you can temporarily switch to EEVEE to configure this setting, then switch back.

Leave this box unchecked for double-sided materials.

.. figure:: /images/addons_import-export_scene-gltf2_material-backface-culling.png

   The inverse of this setting controls glTF's ``DoubleSided`` flag.


Alpha Modes
^^^^^^^^^^^

glTF has three alpha modes, depending on whether the alpha value is always 1, always 0 or
1, or can be between 0 and 1. The exporter determines the alpha mode automatically from
the nodes connected to the Alpha socket.

Opaque
   In *opaque mode*, the material alpha is always 1.

  .. figure:: /images/addons_import-export_scene-gltf2_material-opaque.png

Mask
   In *mask mode*, the material alpha is always 0 or 1. This creates "cutout"
   transparency, where there is a hard edge between opaque and transparent regions, and
   can be used for things like leaves or cloth with holes. To enable this mode, use a Math
   node to round the alpha value to either 0 or 1.

   .. figure:: /images/addons_import-export_scene-gltf2_material-round-alpha.png

   Rounding snaps alpha values that are 0.5 or greater up to 1, and ones below 0.5 down to
   1. It is also possible to use a cutoff value different than 0.5 by using Math nodes to
   do ``1 - (alpha < cutoff)``.

   Mask mode is essentially the same as EEVEE's "Alpha Clip" blend mode, but is done with
   shader nodes so it works in other render engines.

Blend
   Materials that use neither of these will use *blend mode*. Blend mode allows partially
   transparent surfaces that tint the objects seen through them, like layers of colored
   film. However, partial transparency is complex to render, and glTF viewers may show
   visual artifacts in non-trivial scenes that use blend mode.

   To avoid artifacts, it may be a good idea to separate out parts of a model that can use
   opaque or mask mode, and use blend mode only on the parts where it is necessary, or to
   use only a *single* layer of transparent polygons in front of opaque objects.


UV Mapping
^^^^^^^^^^

Control over UV map selection and transformations is available by connecting a UV Map node
and a Mapping node to any Image Texture node.

Settings from the Mapping node are exported using a glTF extension named ``KHR_texture_transform``.
There is a mapping type selector across the top. *Point* is the recommended type for export.
*Texture* and *Vector* are also supported. The supported offsets are:

- *Location* - X and Y
- *Rotation* - Z only
- *Scale* - X and Y

For the *Texture* type, *Scale* X and Y must be equal (uniform scaling).

.. figure:: /images/addons_import-export_scene-gltf2_material-mapping.png

   A deliberate choice of UV mapping.

.. tip::

   These nodes are optional. Not all glTF readers support multiple UV maps or texture transforms.


Factors
^^^^^^^

Any Image Texture nodes may optionally be multiplied with a constant color or scalar.
These will be written as factors in the glTF file, which are numbers that are multiplied
with the specified image textures. These are not common.

- Use Math node (multiply) for scalar factors. Use second value as factor
- Use Mix node (color / multiply) for color factors. Set Factor to 1, and use Color2 (B) as factors

.. figure:: /images/addons_import-export_scene-gltf2_material-factors.png


Example
^^^^^^^

A single material may use all of the above at the same time, if desired. This figure shows
a typical node structure when several of the above options are applied at once:

.. figure:: /images/addons_import-export_scene-gltf2_material-principled.png

   A Principled BSDF material with an emissive texture.

UDIM
^^^^

UDIM is a way to store multiple textures in a single image file.
The UDIM system is supported by Blender, but is not supported by glTF.
When exporting a model that uses UDIM, the add-on will automatically split the
image into multiple images, one for each tile, and will update the material
nodes to use the new images.
All UDIM texture must use the same UV map to be exported.


Exporting a Shadeless (Unlit) Material
--------------------------------------

To export an unlit material, mix in a camera ray, and avoid using the Principled BSDF node.

.. figure:: /images/addons_import-export_scene-gltf2_material-unlit.png

   One of several similar node arrangements that will export
   ``KHR_materials_unlit`` and render shadeless in Blender.


Extensions
==========

The core glTF 2.0 format can be extended with extra information, using glTF extensions.
This allows the file format to hold details that were not considered universal at the time of first publication.
Not all glTF readers support all extensions, but some are fairly common.

Certain Blender features can only be exported to glTF via these extensions.
The following `glTF 2.0 extensions <https://github.com/KhronosGroup/glTF/tree/main/extensions>`__
are supported directly by this add-on:


.. rubric:: Import

- ``KHR_materials_pbrSpecularGlossiness``
- ``KHR_materials_clearcoat``
- ``KHR_materials_transmission``
- ``KHR_materials_unlit``
- ``KHR_materials_emissive_strength``
- ``KHR_materials_volume``
- ``KHR_materials_sheen``
- ``KHR_materials_specular``
- ``KHR_materials_anisotropy``
- ``KHR_materials_ior``
- ``KHR_materials_variants``
- ``KHR_lights_punctual``
- ``KHR_texture_transform``
- ``KHR_mesh_quantization``
- ``EXT_mesh_gpu_instancing``


.. rubric:: Export

- ``KHR_draco_mesh_compression``
- ``KHR_lights_punctual``
- ``KHR_materials_clearcoat``
- ``KHR_materials_transmission``
- ``KHR_materials_unlit``
- ``KHR_materials_emissive_strength``
- ``KHR_materials_volume``
- ``KHR_materials_sheen``
- ``KHR_materials_specular``
- ``KHR_materials_anisotropy``
- ``KHR_materials_ior``
- ``KHR_materials_variants``
- ``KHR_texture_transform``
- ``EXT_mesh_gpu_instancing``


Third-party glTF Extensions
---------------------------

It is possible for Python developers to add Blender support for additional glTF extensions by writing their
own third-party add-on, without modifying this glTF add-on. For more information, `see the example on GitHub
<https://github.com/KhronosGroup/glTF-Blender-IO/tree/main/example-addons/>`__ and if needed,
`register an extension prefix <https://github.com/KhronosGroup/glTF/blob/main/extensions/Prefixes.md>`__.


Custom Properties
=================

Custom properties are always imported, and will be exported from most objects
if the :menuselection:`Include --> Custom Properties` option is selected before export.
These are stored in the ``extras`` field on the corresponding object in the glTF file.

Unlike glTF extensions, custom properties (extras) have no defined namespace,
and may be used for any user-specific or application-specific purposes.


Animations
==========

A glTF animation changes the transforms of objects or pose bones, or the values of shape keys.
One animation can affect multiple objects, and there can be multiple animations in a glTF file.


Import
------

Imported models are set up so that the first animation in the file is playing automatically.
Scrub the Timeline to see it play.

When the file contains multiple animations, the rest will be organized using
the :doc:`Nonlinear Animation editor </editors/nla/tracks>`. Each animation
becomes an action stashed to an NLA track. The track name is the name of the glTF animation.
To make the animation within that track visible, click Solo (star icon) next to the track you want to play.

.. _fig-gltf-solo-track:

.. figure:: /images/addons_import-export_scene-gltf2_animation-solo-track.png

   This is the `fox sample model <https://github.com/KhronosGroup/glTF-Sample-Models/tree/master/2.0/Fox>`__
   showing its "Run" animation.

If an animation affects multiple objects, it will be broken up into multiple parts.
The part of the animation that affects one object becomes an action stashed on that object.
Use the track names to tell which actions are part of the same animation.
To play the whole animation, you need to enable Solo (star icon) for all its tracks.

.. note::

   There is currently no way to see the non-animated pose of a model that had animations.


You can also use the animation switcher that can be found in DopeSheet editor.

.. note::

   You have to enable UI in Add-on preferences for seeing the animation switcher

     .. figure:: /images/addons_import-export_scene-gltf2_addon-preferences-animation.png


You can switch all animation imported. It automatically enables Solo (star icon) for all needed tracks.
It also reset non animated object to Rest transformation.


Export
------

You can export animations using different ways. How glTF animations are made from actions / NLA is controlled by
the :menuselection:`Animation --> Mode` export option.

Actions (default)
^^^^^^^^^^^^^^^^^

An action will be exported if it is the active action on an object, or it is stashed to an NLA track
(e.g. with the *Stash* or *Push Down* buttons in the :doc:`Action Editor </editors/dope_sheet/modes/action>`).
Actions which are **not** associated with an object in one of these ways are **not exported**.
If you have multiple actions you want to export, make sure they are stashed!

A glTF animation can have a name, which is the action name by default. You can override it
by renaming its NLA track from ``NLATrack``/``[Action Stash]`` to the name you want to use.
For example, the Fig. :ref:`fox model <fig-gltf-solo-track>` will export with three animations,
"Survey", "Walk", and "Run".
If you rename two tracks on two different objects to the same name, they will become part
of the same glTF animation and will play together.

The importer organizes actions so they will be exported correctly with this mode.

This mode is useful if you are exporting for game engine, with an animation library of a character.
Each action must be on its own NLA track.


Active Actions merged
^^^^^^^^^^^^^^^^^^^^^

In this mode, the NLA organization is not used, and only one animation is exported using
the active actions on all objects.

NLA Tracks
^^^^^^^^^^

In this mode, each NLA Track will be export as an independent glTF animation.
This mode is useful if you are using Strip modifiers, or if you get multiple action on a same Track.

If you rename two tracks on two different objects to the same name, they will become part
of the same glTF animation and will play together.

Scene
^^^^^

Using `Scene`_ option, animations will be exported as you can see them in viewport.
You can choose to export a single glTF animation, or each object separately.

.. note::

   Remember only certain types of animation are supported:

   - Object transform (location, rotation, scale)
   - Pose bones
   - Shape key values

   Animation of other properties, like physics, lights, or materials, will be ignored.

.. note::

   In order to sample shape key animations controlled by drivers using bone transformations,
   they must be on a mesh object that is a direct child of the bones' armature.

.. note::

   Only `Actions (default)`_ and `Active Actions merged`_ mode can handle not sampled animations.


File Format Variations
======================

The glTF specification identifies different ways the data can be stored.
The importer handles all of these ways. The exporter will ask the user to
select one of the following forms:


glTF Binary (``.glb``)
----------------------

This produces a single ``.glb`` file with all mesh data, image textures, and
related information packed into a single binary file.

.. tip::

   Using a single file makes it easy to share or copy the model to other systems and services.


glTF Separate (``.gltf`` + ``.bin`` + textures)
-----------------------------------------------

This produces a JSON text-based ``.gltf`` file describing the overall structure,
along with a ``.bin`` file containing mesh and vector data, and
optionally a number of ``.png`` or ``.jpg`` files containing image textures
referenced by the ``.gltf`` file.

.. tip::

   Having an assortment of separate files makes it much easier for a user to
   go back and edit any JSON or images after the export has completed.

.. note::

   Be aware that sharing this format requires sharing all of these separate files
   together as a group.


glTF Embedded (``.gltf``)
-------------------------

This produces a JSON text-based ``.gltf`` file, with all mesh data and
image data encoded (using Base64) within the file. This form is useful if
the asset must be shared over a plain-text-only connection.

.. warning::

   This is the least efficient of the available forms, and should only be used when required.
   Available only when you activated it in addon preferences.


Properties
==========

Import
------

Pack Images
   Pack all images into the blend-file.
Merge Vertices
   The glTF format requires discontinuous normals, UVs, and other vertex attributes to be stored as separate vertices,
   as required for rendering on typical graphics hardware.
   This option attempts to combine co-located vertices where possible.
   Currently cannot combine verts with different normals.
Shading
   How normals are computed during import.
Guess Original Bind Pose
   Determines the pose for bones (and consequently, skinned meshes) in Edit Mode.
   When on, attempts to guess the pose that was used to compute the inverse bind matrices.
Bone Direction
   Changes the heuristic the importer uses to decide where to place bone tips.
   Note that the Fortune setting may cause inaccuracies in models that use non-uniform scaling.
   Otherwise this is purely aesthetic.
   The default value will not change axis, and is best for re-exporting from Blender.
   This default option will change display mode (adding shape and changing relationship line) to have a better view,
   even if original bones axis are not the most accurate (estheticaly speaking)
Lighting Mode
   Optional backwards compatibility for non-standard render engines. Applies to lights.
   Standard: Physically-based glTF lighting units (cd, lx, nt).
   Unitless: Non-physical, unitless lighting. Useful when exposure controls are not available
   Raw (Deprecated): Blender lighting strengths with no conversion
Import WebP textures
   If a texture exists in WebP format, loads the WebP texture instead of the fallback png/jpg one.


Export
------

Format
   See: `File Format Variations`_.
Keep Original
   For glTF Separate file format only. Keep original textures files if possible.
   Warning: if you use more than one texture, where PBR standard requires only one,
   only one texture will be used. This can lead to unexpected results
Textures
   For glTF Separate file format only. Folder to place texture files in. Relative to the gltf-file.
Copyright
   Legal rights and conditions for the model.
Remember Export Settings
   Store export settings in the blend-file,
   so they will be recalled next time the file is opened.


Include
^^^^^^^

Selected Objects
   Export selected objects only.
Visible Objects
   Export visible objects only.
Renderable Objects
   Export renderable objects only.
Active Collection
   Export objects from active collection only.
Include Nested Collections
   Only when Active Collection is On.
   When On, export recursively objects on nested active collections.
Active Scene
   Export active scene only.
Custom Properties
   Export custom properties as glTF extras.
Cameras
   Export cameras.
Punctual Lights
   Export directional, point, and spot lights. Uses the ``KHR_lights_punctual`` glTF extension.


Transform
^^^^^^^^^

Y Up
   Export using glTF convention, +Y up.


Data - Scene Graph
^^^^^^^^^^^^^^^^^^

Geometry Nodes Instances
   Export Geometry nodes instances. This feature is experimental.

GPU Instances
   Export using ``EXT_mesh_gpu_instancing`` extensions.

Flatten Object Hierarchy
   Useful in case of non-decomposable TRS matrix. Only skined meshes will stay children of armature.

Full Collection Hierarchy
   Export collections as empty, keeping full hierarchy. If an object is in multiple collections,
   it will be exported it only once, in the first collection it is found.


Data - Mesh
^^^^^^^^^^^

Apply Modifiers
   Export objects using the evaluated mesh, meaning the resulting mesh after all
   :doc:`Modifiers </modeling/modifiers/index>` have been calculated.
UVs
   Export UVs (texture coordinates) with meshes.
Normals
   Export vertex normals with meshes.
Tangents
   Export vertex tangents with meshes.
Attributes
   Export Attributes with meshes, when the name starts with underscore.
Loose Edges
   Export loose edges as lines, using the material from the first material slot.
Loose Points
   Export loose points as glTF points, using the material from the first material slot.
Shared Accessor
   For triangles, use shared accessor for indices. This is more efficient (smaller files when you have lots of
   materials).


Data - Mesh - Vertex Color
^^^^^^^^^^^^^^^^^^^^^^^^^^

Use Vertex Color
   :Material:
      Export vertex color when used in material node tree as Base Color multiplier.
      This is the default, and the most accurate regarding glTF specification.
   :Active:
      Export active vertex colors, even if not used in material node tree.
      A fully compliant glTF viewer should display this VC as Base Color multiplier.
   :None:
      Do not export vertex color.
Export all vertex colors
   Export all vertex colors, additional VC will be COLOR_1, COLOR_2, etc.
Export active vertex color when no material
   Export active vertex color when no material is assigned to the object.


Data - Material
^^^^^^^^^^^^^^^

Materials
   Export full materials, only placeholders (all primitives but without materials),
   or does not export materials. (In that last case, primitives are merged, losing material slot information).
Images
   Output format for images. PNG is lossless and generally preferred, but JPEG might be preferable for
   web applications due to the smaller file size.
   If WebP is chosen, all textures will be saved as WebP, without any png/jpg fallback.
   If None is chosen, materials are exported without textures.
Image Quality
   When exporting jpeg or WebP files, the quality of the exported file.
Create WebP
   Creates WebP textures for every textures, in addition to the existing texture.
   For already WebP textures, nothing happen.
WebP fallback
   For all WebP textures, create a png fallback texture.
Unused images
   Export images that are not used in any material.
Unused textures
   Export texture info (sampler, image, texcoord) that are not used in any material.

Data - Shape Keys
^^^^^^^^^^^^^^^^^

Export shape keys (morph targets).

Shape Key Normals
   Export vertex normals with shape keys (morph targets).
Shape Key Tangents
   Export vertex tangents with shape keys (morph targets).

Data - Shape Keys - Optimize
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Use Sparse Accessor if better
   Sparse Accessor will be used if it save space (if the exported file is smaller)
Omitting Sparse Accessor if data is empty
   If data is empty, omit to export SParce Accessor. Not all viewer managed it correctly, so this option is Off by
   default

Data - Armature
^^^^^^^^^^^^^^^

Use Rest Position Armature
   Export Armatures using rest position as joint rest pose. When Off, the current frame pose is used as rest pose.
Export Deformation Bones only
   Export Deformation bones only, not other bones.
   Animation for deformation bones are baked.
Remove Armature Object
   Remove Armature Objects if possible. If some armature(s) have multiple root bones, we can't remove them.
Flatten Bone Hierarchy
   Useful in case of non-decomposable TRS matrix.

Data - Skinning
^^^^^^^^^^^^^^^

Export skinning data

Bone influences
   How many joint verex influences will be exported. Models may appear incorrectly in many viewers with value
   different to 4 or 8.

Include All Bone Influences
   Export all joint vertex influences. Models may appear incorrectly in many viewers.

Data - Lighting
^^^^^^^^^^^^^^^

Lighting Mode
   Optional backwards compatibility for non-standard render engines. Applies to lights.
   Standard: Physically-based glTF lighting units (cd, lx, nt).
   Unitless: Non-physical, unitless lighting. Useful when exposure controls are not available
   Raw (Deprecated): Blender lighting strengths with no conversion


Data - Compression
^^^^^^^^^^^^^^^^^^

Compress meshes using Google Draco.

Compression Level
   Higher compression results in slower encoding and decoding.
Quantization Position
   Higher values result in better compression rates.
Normal
   Higher values result in better compression rates.
Texture Coordinates
   Higher values result in better compression rates.
Color
   Higher values result in better compression rates.
Generic
   Higher values result in better compression rates.


Animation
^^^^^^^^^

Animation mode
   Animation mode used for export (See `Animations`_ )
Shape Keys Animations
   Export Shape Keys Animation. Need Shape Keys to be exported (See `Data - Shape Keys`_)
Bake All Objects Animations
   Useful when some objects are constrained without being animated themselves.


Animation - Rest & Ranges
^^^^^^^^^^^^^^^^^^^^^^^^^

Use Current Frame as Object Rest Transformations
   Export the scene in the current animation frame. When off, frame 0 is used as rest transformation for objects.
Limit to Playback Range
   Clips animations to selected playback range.
Set all glTF Animation starting at 0
   Set all glTF Animation starting at 0. Can be useful for looping animation
Negative Frames
   When some frames are in negative range, slide or crop the animation.

Animation - Armature
^^^^^^^^^^^^^^^^^^^^

Export all Armature Actions
   Export all actions, bound to a single armature.
   Warning: Option does not support exports including multiple armatures.
Reset pose bones between actions
   Reset pose bones between each action exported.
   This is needed when some bones are not keyed on some animations.


Animation - Sampling
^^^^^^^^^^^^^^^^^^^^

Apply sampling to all animations. Do not sample animation can lead to wrong animation export.

Sampling Rate
   How often to evaluate animated values (in frames).

Animation - Optimize
^^^^^^^^^^^^^^^^^^^^

Optimize Animation Size
   Reduce exported file size by removing duplicate keyframes when all identical.
Force keeping channel for armature / bones
   if all keyframes are identical in a rig, force keeping the minimal animation.
Force keeping channel for objects
   if all keyframes are identical for object transformations, force keeping the minimal animation.
Disable viewport for other objects
   When exporting animations, disable viewport for other objects, for performance reasons, when possible.

Animation - Filter
^^^^^^^^^^^^^^^^^^

Restrict actions to be exported to the ones matching the filter.

Contributing
============

This importer/exporter is developed through
the `glTF-Blender-IO repository <https://github.com/KhronosGroup/glTF-Blender-IO>`__,
where you can file bug reports, submit feature requests, or contribute code.

Discussion and development of the glTF 2.0 format itself takes place on
the Khronos Group `glTF GitHub repository <https://github.com/KhronosGroup/glTF>`__,
and feedback there is welcome.


## Index

########
  Node
########

These add-ons relate to the node editors and related tools.

.. toctree::
   :maxdepth: 1

   node_wrangler.rst


## Node Wrangler


*************
Node Wrangler
*************

Node Wrangler provides various tools that help you to work with nodes quickly and efficiently.

While many of this add-on's functions work in all supported node editors (Compositor, Shader, Geometry Nodes,
and Texture Nodes) some functions only work in specific node editors, and some functions work differently per
editor.
Functions that only work in specific editors are marked with labels (:guilabel:`Compositor`, :guilabel:`Shader`,
:guilabel:`Geometry Nodes`, :guilabel:`Texture Nodes`). Functions without labels should work for all node editors.


Activation
==========

- Open Blender and go to the Preferences, then the Add-ons tab.
- Find Node Wrangler and enable the add-on.


Usage
=====

Use the panel in Sidebar of the node editor or press :kbd:`Shift-W` to bring up the quick access menu. You can also
look up the shortcut list in the add-on preferences panel.

.. figure:: /images/addons_node_node-wrangler_menu.png

   You can access most functions from the sidebar panel or quick access menu.


Description
===========

Lazy Connect
------------

.. reference::

   :Shortcut:  :kbd:`Alt-RMB`-drag, :kbd:`Shift-Alt-RMB`-drag

Connect two nodes without even clicking the sockets. Just drag the cursor from one node to another while
holding :kbd:`Alt-RMB`.
It will select the nodes nearest the start and end points of the drag for connection, so you don't even have
to click on the nodes.

.. figure:: /images/addons_node_node-wrangler_lazy-connect.png

   Selection can be lazy.

It tries to connect the best-matched sockets possible, based on their names, types, and whether they are
open or not.

For a more precise connection, you can alternatively use :kbd:`Shift-Alt-RMB`. It brings up menus of
available inputs and outputs before connection, so you can select the exact sockets to connect.
It's especially useful when working with a large node tree since you can make connections without
frequently zooming in and out.


Lazy Mix
--------

.. reference::

   :Shortcut:  :kbd:`Shift-Ctrl-RMB`-drag

Connect the outputs of two nodes into an appropriate "mix" type of node. This is the "lazy" way of selecting
nodes and executing the *Mix* function from `Merge with Automatic Type Detection`_.


Merge
-----

.. reference::

   :Menu:   :menuselection:`Node Wrangler --> Merge Selected Nodes`

Connect outputs of the selected nodes into a "mix" type of node (Mix, Math, Z-Combine, Alpha Over, Mix Shader, Add
Shader, Join Geometry).

.. note::

   Merge currently does not support outputs of Integer, String, or Boolean types from Geometry Nodes.

There are automatic and manual ways of merging. The automatic ways let the add-on determine which "mix" node
to use based on the types of outputs to merge. The manual ways let you decide and force connections even if the
types of outputs and the "mix" node are not compatible.

.. note::

   Generally, the modifier part of the shortcut signifies the type of "mix" node you want to use (:kbd:`Ctrl`
   for automatic detection, :kbd:`Ctrl-Alt` for the Mix node, and :kbd:`Shift-Ctrl` for the Math node),
   the non-modifier part signifies the mode of "mix" node you want to set (:kbd:`NumpadPlus` for add,
   :kbd:`NumpadMinus` for subtract, :kbd:`NumpadSlash` for divide, and :kbd:`NumpadAsterisk` for multiply).


Merge with Automatic Type Detection
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The automatic merge functions determine the type of "mix" node to use based on the types of outputs to merge. If
it has a Color output, it will use the Mix node. It will use the Math node if both outputs are of Value type.
Add Shader, Mix Shader, and Join Geometry nodes will also be used for specific cases.

Modes
   Add :kbd:`Ctrl-=`, :kbd:`Ctrl-NumpadPlus`
      Merge into Mix or Math nodes, then set blend mode or math operation as Add. If the outputs are Shaders,
      it will use Add Shader node instead.
   Multiply :kbd:`Ctrl-8`, :kbd:`Ctrl-NumpadAsterisk`
      Merge into Mix or Math nodes, then set blend mode or math operation as Multiply.
   Subtract :kbd:`Ctrl-Minus`, :kbd:`Ctrl-NumpadMinus`
      Merge into Mix or Math nodes, then set blend mode or math operation as Subtract.
   Divide :kbd:`Ctrl-Slash`, :kbd:`Ctrl-NumpadSlash`
      Merge into Mix or Math nodes, then set blend mode or math operation as Divide.
   Mix :kbd:`Ctrl-0`, :kbd:`Ctrl-Numpad0`
      Merge into Mix node, then set blend mode as Mix. If the outputs are Shaders, it will use Mix Shader node
      instead. If the outputs are Geometry, it will use Join Geometry node.


Merge Using Mix Node
^^^^^^^^^^^^^^^^^^^^

.. reference::

   :Menu:   :menuselection:`Node Wrangler --> Merge Selected Nodes --> Use Mix Nodes`

Use the Mix nodes for merging, regardless of the selected nodes. You can choose the mode of the node via the menu.
You can quickly set some operations by using corresponding shortcuts.

- Add: :kbd:`Ctrl-Alt-=`, :kbd:`Ctrl-Alt-=`
- Substract: :kbd:`Ctrl-Alt-Minus`, :kbd:`Ctrl-Alt-NumpadMinus`
- Multiply: :kbd:`Ctrl-Alt-8`, :kbd:`Ctrl-Alt-NumpadAsterisk`
- Divide: :kbd:`Ctrl-Alt-Slash`, :kbd:`Ctrl-Alt-NumpadSlash`


Merge Using Math Node
^^^^^^^^^^^^^^^^^^^^^

.. reference::

   :Menu:   :menuselection:`Node Wrangler --> Merge Selected Nodes --> Use Math Nodes`

Use the Math nodes for merging, regardless of the selected nodes. You can choose the mode of the node via the menu.
You can quickly set some operations by using corresponding shortcuts.

- Add: :kbd:`Shift-Ctrl-=`, :kbd:`Shift-Ctrl-=`
- Substract: :kbd:`Shift-Ctrl-Minus`, :kbd:`Shift-Ctrl-NumpadMinus`
- Multiply: :kbd:`Shift-Ctrl-8`, :kbd:`Shift-Ctrl-NumpadAsterisk`
- Divide: :kbd:`Shift-Ctrl-Slash`, :kbd:`Shift-Ctrl-NumpadSlash`
- Greater than: :kbd:`Ctrl-Comma`
- Less than: :kbd:`Ctrl-Period`


Merge Using Z-Combine Node
^^^^^^^^^^^^^^^^^^^^^^^^^^

:guilabel:`Compositor`

.. reference::

   :Menu:   :menuselection:`Node Wrangler --> Merge Selected Nodes --> Use Z-Combine Nodes`
   :Shortcut:  :kbd:`Ctrl-NumpadPeriod`

Use the Z-Combine nodes for merging. If possible, Image and Z-Depth outputs will be linked. If the current
node editor is not Compositor, this will execute the *Mix* function from the automatic merge.


Merge Using Alpha Over Node
^^^^^^^^^^^^^^^^^^^^^^^^^^^

:guilabel:`Compositor`

.. reference::

   :Menu:   :menuselection:`Node Wrangler --> Merge Selected Nodes --> Use Alpha Over Nodes`
   :Shortcut:  :kbd:`Ctrl-Alt-0`

Use the Alpha Over nodes for merging. If the current node editor is not Compositor, this will execute the *Mix*
function from the automatic merge.


Batch Change Blend Mode / Math Operation
----------------------------------------

.. reference::

   :Menu:   :menuselection:`Node Wrangler --> Batch Change`

Change the blend mode or math operation of the selected Mix and Math nodes at once.
You can use :kbd:`Alt-Up` or :kbd:`Alt-Down` to cycle through previous or next blend modes or math operations.
You can also quickly set some operations by using corresponding shortcuts.

- Add: :kbd:`Alt-=`, :kbd:`Alt-=`
- Substract: :kbd:`Alt-Minus`, :kbd:`Alt-NumpadMinus`
- Multiply: :kbd:`Alt-8`, :kbd:`Alt-NumpadAsterisk`
- Divide: :kbd:`Alt-Slash`, :kbd:`Alt-NumpadSlash`
- Greater than: :kbd:`Alt-Comma`
- Less than: :kbd:`Alt-Period`

Change Mix Factor
-----------------

.. reference::

   :Shortcut:
      :kbd:`Alt-Left`, :kbd:`Shift-Alt-Left`, :kbd:`Alt-Right`, :kbd:`Shift-Alt-Right`,
      :kbd:`Shift-Ctrl-Alt-Left`, :kbd:`Shift-Ctrl-Alt-0`, :kbd:`Shift-Ctrl-Alt-Right`, :kbd:`Shift-Ctrl-Alt-1`

Change the Factor value of the selected Mix and Mix Shader nodes with shortcuts.

- Increase Factor by 0.1: :kbd:`Alt-Right`
- Decrease Factor by 0.1: :kbd:`Alt-Left`
- Increase Factor by 0.01: :kbd:`Shift-Alt-Right`
- Decrease Factor by 0.01: :kbd:`Shift-Alt-Left`
- Set Factor to 0.0: :kbd:`Shift-Ctrl-Alt-Left`, :kbd:`Shift-Ctrl-Alt-0`
- Set Factor to 1.0: :kbd:`Shift-Ctrl-Alt-Right`, :kbd:`Shift-Ctrl-Alt-1`


Delete Unused Nodes
-------------------

.. reference::

   :Menu:   :menuselection:`Node Wrangler --> Delete Unused Nodes`
   :Shortcut:  :kbd:`Alt-X`

Clean up your node tree. Delete all nodes that don't contribute to the final result.


Swap Links
----------

.. reference::

   :Menu:   :menuselection:`Node Wrangler --> Swap Links`
   :Shortcut:  :kbd:`Alt-S`

When two nodes are selected, this swaps each other's output link.
Note that some output connections can be lost if the two nodes have a different number of connected
outputs.

With one node selected, if the node has one linked input, it cycles the link through the available input
sockets. If the node has two linked inputs, it swaps those two links. If there are more than two inputs linked,
it swaps the two inputs with matching types (the Mix node's two Color inputs, for example).

.. figure:: /images/addons_node_node-wrangler_swap_links.png

   Swap works differently depending on the selected nodes and their links.


Reset Backdrop
--------------

:guilabel:`Compositor`

.. reference::

   :Menu:   :menuselection:`Node Wrangler --> Reset Backdrop`
   :Shortcut:  :kbd:`Z`

Reset the position and scale of the backdrop.


Add Attribute Node
------------------

:guilabel:`Shader`

.. reference::

   :Menu:      :menuselection:`Header --> Add --> Input --> Attributes`

Add an Attribute node with the selected attribute.


Preview Node Output
-------------------

:guilabel:`Shader` :guilabel:`Geometry Nodes`

.. reference::

   :Shortcut:  :kbd:`Shift-Ctrl-LMB` for :guilabel:`Shader`, :kbd:`Shift-Alt-LMB` for :guilabel:`Geometry Nodes`

Connect an output of the selected node to the final output of the node tree (the Material Output or World Output
for Shader, the final Group Output for Geometry Nodes) to preview its output in the viewport.
You can cycle through the available outputs by clicking it again while holding the modifier keys.

.. seealso::

   While in Shader, any output can be connected to the final output, in Geometry Nodes, only Geometry outputs
   can be connected to the final output.
   To preview other types of outputs in Geometry Nodes,
   use its own :doc:`Viewer Node </modeling/geometry_nodes/output/viewer>`.

.. seealso::

   Also check out *Connect to Output*. It is a similar function but has different behaviors.
   It also works in all node editors.


Frame Selected
--------------

.. reference::

   :Menu:   :menuselection:`Node Wrangler --> Frame Selected`
   :Shortcut:  :kbd:`Shift-P`

Insert the selected nodes into a Frame node.


Reload Images
-------------

:guilabel:`Compositor` :guilabel:`Shader` :guilabel:`Texture Nodes`

.. reference::

   :Menu:   :menuselection:`Node Wrangler --> Reload Images`
   :Shortcut:  :kbd:`Alt-R`

Reload all of the images used in the node tree. This lets you reload the images without using the Image Editor.


Copy Settings
-------------

.. reference::

   :Menu:   :menuselection:`Node Wrangler --> Copy to Selected --> Settings from Active`
   :Shortcut:  :kbd:`Shift-C`

Copy the settings of the active node to all selected nodes of the same type.


Reset Nodes
-----------

.. reference::

   :Shortcut:  :kbd:`Backspace`

Revert the settings of the selected nodes to default while maintaining connections.


Copy Label
----------

.. reference::

   :Menu:   :menuselection:`Node Wrangler --> Copy to Selected --> Copy Label`
   :Shortcut:  :kbd:`Shift-V`, :kbd:`Shift-C`

Copy custom labels to all of the selected nodes. You can copy them from the active node (:kbd:`Shift-V`),
from the nodes that are linked to the selected ones, or from the names of the sockets that the selected nodes
are linked to.
:kbd:`Shift-C` will bring up a submenu with all available options.


Clear Label
-----------

.. reference::

   :Menu:   :menuselection:`Node Wrangler --> Clear Label`
   :Shortcut:  :kbd:`Alt-L`

Clear the custom labels of selected nodes and revert them back to their default node names.


Modify Labels
-------------

.. reference::

   :Menu:   :menuselection:`Node Wrangler --> Modify Labels`
   :Shortcut:  :kbd:`Shift-Alt-L`

Batch rename the custom labels of selected nodes. You can add text to the beginning and the end and replace parts
of the text.


Add Texture Setup
-----------------

:guilabel:`Shader`

.. reference::

   :Menu:   :menuselection:`Node Wrangler --> Add Texture Setup`
   :Shortcut:  :kbd:`Ctrl-T`

Add a setup of a texture node, Texture Coordinate, and Mapping nodes to any shader node.
If you select a texture node, it will only add the Texture Coordinate and Mapping nodes.
For a background shader it will add an Environment Texture node.


Add Principled Texture Setup
----------------------------

:guilabel:`Shader`

.. reference::

   :Menu:   :menuselection:`Node Wrangler --> Add Principled Setup`
   :Shortcut:  :kbd:`Shift-Ctrl-T`

Add a principled texture setup from the selected texture files. Select a Principled BSDF node,
select *Add Principled Setup* from the quick access menu (or press :kbd:`Shift-Ctrl-T`), and select texture files.
It automates the process of adding Image Texture nodes, loading images, selecting the appropriate Color Space,
and connecting their outputs to the Principled BSDF node.

It detects the type of textures by looking at their file names. You can edit the tags used for this matching
process in the add-on preferences.

.. figure:: /images/addons_node_node-wrangler_swap_pbr-setup.jpg

   Setting up these textures can take dozens of clicks, even with Node Wrangler's other tools.
   With Principled Texture Setup, you can reduce that to a few clicks.


Add Reroutes to Outputs
-----------------------

.. reference::

   :Menu:   :menuselection:`Node Wrangler --> Add Reroutes`
   :Shortcut:  :kbd:`Slash`

Add reroute nodes to each output of the selected nodes.


Link Active to Selected
-----------------------

.. reference::

   :Menu:   :menuselection:`Node Wrangler --> Link Active to Selected`
   :Shortcut:  :kbd:`Backslash`

Link the active node to the selected nodes based on various criteria.

To All Selected
   Link the active node to all selected nodes. (:kbd:`K`) You can force it to replace existing links.
   (:kbd:`Shift-K`)

Use Node Name/Label
   Link only to the selected nodes that have the same label as the active node. (:kbd:`'`) You can force it to
   replace existing links. (:kbd:`Shift-'`)

Use Outputs Names
   Link only when the name of the outputs matches the name or label of the selected nodes. (:kbd:`;`) You can
   force it to replace existing links. (:kbd:`Shift-;`) This is handy for replacing sources at the same time.
   (For example, connecting outputs from Render Layer to image (multi-layer EXR) in Compositor.)


Align Nodes
-----------

.. reference::

   :Menu:   :menuselection:`Node Wrangler --> Align Nodes`
   :Shortcut:  :kbd:`Shift-=`

Align the selected nodes horizontally or vertically. The effect is similar to scaling nodes on an axis
(:kbd:`S X 0` or :kbd:`S Y 0`), but it places the nodes at an even distance.


Select within Frame (Parent/Children)
-------------------------------------

- :kbd:`]` -- Select all direct child nodes of the selected frame.
- :kbd:`[` -- Select the direct parent frame node of the selected nodes.


Detach Outputs
--------------

.. reference::

   :Menu:   :menuselection:`Node Wrangler --> Detach Outputs`
   :Shortcut:  :kbd:`Shift-Alt-D`

Detach the selected node's outputs while leaving linked inputs intact.


Connect to Output
-----------------

.. reference::

   :Menu:   :menuselection:`Node Wrangler --> Connect to Output`
   :Shortcut:  :kbd:`O`

Connect the output of the selected node to the final output of the node tree (Composite in Compositor,
Material Output or World Output in Shader, the final Group Output in Geometry Nodes, Output in Texture Nodes),
or, if the node is inside a group, to the Group Output.


Add Image Sequence
------------------

:guilabel:`Compositor` :guilabel:`Shader`

.. reference::

   :Menu:      :menuselection:`Add --> Input` for :guilabel:`Compositor`,
               or :menuselection:`Add --> Texture` for :guilabel:`Shader`

Add an Image Sequence by only selecting one image from a sequence of image files. It will automatically detect
the length of the sequence and set the node appropriately.


Add Multiple Images
-------------------

:guilabel:`Compositor` :guilabel:`Shader`

.. reference::


   :Menu:      :menuselection:`Add --> Input` for :guilabel:`Compositor`,
               or :menuselection:`Add --> Texture` for :guilabel:`Shader`

Select multiple images and add a node for each image.
(Useful for importing multiple render passes or renders for image stacking.)


.. seealso::

   Please see the
   `old Wiki <https://archive.blender.org/wiki/2015/index.php/Extensions:2.6/Py/Scripts/Nodes/Nodes_Efficiency_Tools/>`__
   for the archived original docs.


.. reference::

   :Category: Node
   :Description: Various tools to enhance and speed up node-based workflow.
   :Location: :menuselection:`Node editor --> Sidebar` or see the shortcuts of individual tools.
   :File: node_wrangler.py
   :Author: Bartek Skorupa, Greg Zaal, Sebastian Koenig, Christian Brinkmann, Florian Meyer
   :License: GPL
   :Note: This add-on is bundled with Blender.


## Index


##########
  System
##########

.. important::

   Work In Progress

These add-ons relate to showing information about objects and scenes.

.. toctree::
   :maxdepth: 1

   ui_translations.rst


## Ui Translations


**********************
Manage UI Translations
**********************

Todo


Activation
==========

- Open Blender and go to Preferences then the Add-ons tab.
- Click System then Manage UI translations to enable the script.


Description
===========

See `Blender translation guide
<https://developer.blender.org/docs/handbook/translating/translator_guide/#manage-ui-translations-add-on>`__
in the Developer Handbook.

.. reference::

   :Category: System
   :Description: Allows managing UI translations directly from within Blender
                 (update main po-files, update scripts' translations, etc.).
   :Location: :menuselection:`Topbar --> File menu`, Text editor, any UI control
   :File: ui_translate folder
   :Author: Bastien Montagne
   :Note: This add-on is bundled with Blender.


