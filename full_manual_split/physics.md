# Index for physics

- [Baking](#Baking)
- [Collision](#Collision)
- [Index](#Index)
- [Introduction](#Introduction)
- [Simulation Nodes](#Simulation-Nodes)
- [Examples](#Examples)
- [Index](#Index)
- [Introduction](#Introduction)
- [Cache](#Cache)
- [Collisions](#Collisions)
- [Field Weights](#Field-Weights)
- [Index](#Index)
- [Physical Properties](#Physical-Properties)
- [Property Weights](#Property-Weights)
- [Shape](#Shape)
- [Brush](#Brush)
- [Canvas](#Canvas)
- [Index](#Index)
- [Introduction](#Introduction)
- [Index](#Index)
- [Introduction](#Introduction)
- [Material](#Material)
- [Effector](#Effector)
- [Flow](#Flow)
- [Index](#Index)
- [Cache](#Cache)
- [Collections](#Collections)
- [Field Weights](#Field-Weights)
- [Guides](#Guides)
- [Index](#Index)
- [Settings](#Settings)
- [Adaptive Domain](#Adaptive-Domain)
- [Index](#Index)
- [Noise](#Noise)
- [Viewport Display](#Viewport-Display)
- [Diffusion](#Diffusion)
- [Index](#Index)
- [Mesh](#Mesh)
- [Particles](#Particles)
- [Gravity](#Gravity)
- [Index](#Index)
- [Index](#Index)
- [Introduction](#Introduction)
- [Boid](#Boid)
- [Charge](#Charge)
- [Curve Guide](#Curve-Guide)
- [Drag](#Drag)
- [Fluid Flow](#Fluid-Flow)
- [Force](#Force)
- [Harmonic](#Harmonic)
- [Lennard Jones](#Lennard-Jones)
- [Magnetic](#Magnetic)
- [Texture](#Texture)
- [Turbulence](#Turbulence)
- [Vortex](#Vortex)
- [Wind](#Wind)
- [Index](#Index)
- [Introduction](#Introduction)
- [Mode](#Mode)
- [Particle System Panel](#Particle-System-Panel)
- [Texture Influence](#Texture-Influence)
- [Cache](#Cache)
- [Children](#Children)
- [Display](#Display)
- [Emission](#Emission)
- [Force Field](#Force-Field)
- [Index](#Index)
- [Render](#Render)
- [Rotation](#Rotation)
- [Velocity](#Velocity)
- [Vertex Groups](#Vertex-Groups)
- [Boids](#Boids)
- [Fluid](#Fluid)
- [Index](#Index)
- [Introduction](#Introduction)
- [Keyed](#Keyed)
- [Newtonian](#Newtonian)
- [Children](#Children)
- [Display](#Display)
- [Dynamics](#Dynamics)
- [Emission](#Emission)
- [Index](#Index)
- [Introduction](#Introduction)
- [Render](#Render)
- [Shape](#Shape)
- [Index](#Index)
- [Introduction](#Introduction)
- [Tips](#Tips)
- [World](#World)
- [Index](#Index)
- [Introduction](#Introduction)
- [Fixed](#Fixed)
- [Generic](#Generic)
- [Generic Spring](#Generic-Spring)
- [Hinge](#Hinge)
- [Index](#Index)
- [Motor](#Motor)
- [Piston](#Piston)
- [Point](#Point)
- [Slider](#Slider)
- [Collisions](#Collisions)
- [Dynamics](#Dynamics)
- [Index](#Index)
- [Settings](#Settings)
- [Collision](#Collision)
- [Examples](#Examples)
- [Index](#Index)
- [Introduction](#Introduction)
- [Exterior](#Exterior)
- [Index](#Index)
- [Interior](#Interior)
- [Cache](#Cache)
- [Edges](#Edges)
- [Goal](#Goal)
- [Index](#Index)
- [Object](#Object)
- [Self Collision](#Self-Collision)
- [Simulation](#Simulation)
- [Solver](#Solver)


## Baking

.. _bpy.types.PointCache:
.. _bpy.ops.ptcache:

**************************
Baking Physics Simulations
**************************

:term:`Baking` refers to the act of storing or caching the results of a calculation.
The result of a simulation is automatically cached to memory when the animation is played,
so that the next time it runs, it can be replayed more quickly by reading the results from the memory.

If you bake the simulation the cache is protected,
and you will be unable to change the simulation settings
until you clear the baked frames by clicking *Free Bake*.

It is generally recommended to bake your physics simulations before rendering.
Aside from no longer needing to go through the time-consuming process of simulating again,
baking can help prevent potential glitches and ensure that the outcome of the simulation
remains exactly the same every time.

.. A screenshot of the baking interface is intentionally omitted, as it
   the available options vary slightly between different physics systems.

.. note::

   Most physics simulators in Blender use a similar system,
   but not all have exactly the same settings available. All the settings are covered here,
   but individual physics types may not provide all these options.


Options
=======

.. figure:: /images/physics_baking_multi-cache-interface.png
   :align: right

   Two different caches stored simultaneously.

Caches List
   Blender allows for storing and managing multiple caches at once for the same physics object.
   You can manage the caches with this :ref:`list view <ui-list-view>`.
   Double-click the cache entry to give it a name.

   Each cache can have a name. Double-click the cache entry to give it a name.
   If this name is given, any disk cache will be stored in files starting with that name.
   For example, a cache named ``MyCache`` will be stored in ``MyCache_xxxxxx_yy.bphys``.

   If the cache does not have a name (which is the default),
   the filename of the cache will depend on the object it is attached to,
   although this is not immediately obvious. For example, a cache on
   an object ``Cube`` will be stored in ``43756265_xxxxxx_yy.bphys``,
   where ``43756265`` is determined by the object name.

   .. warning::

      When there are multiple caches on one object, **always specify a Cache Name**. As described above,
      the filename of an unnamed cache is determined by the name of the object it is attached to.
      As a result, an object with multiple physics systems that all have an unnamed cache will cause
      conflict and **can result in losing cache files**.

External
   Allows you to read the cache from a drive using a user-specified file path.

   .. note::

      The cache name in *Caches List* and the *Index*
      has to exactly match the external cache files name in order to work.
      The cache files name format is ``name_frame_index.bphys``.

   Index
      The index number of cache files. (The last two digits of the files name.)
   Path
      Select the directory path to the cache files.

Disk Cache
   The cache of a baked simulation will be stored inside the blend-file when you save it.
   When *Disk Cache* is checked, Blender will save the cache separately to
   the drive in a folder named ``blendcache_[filename]`` alongside the blend-file.
   (The blend-file must be saved first.)

   .. note::

      When using :doc:`/files/linked_libraries/library_overrides`,
      data-blocks only support *Disk Cache* storage.

Use Library Path
   Share the disk cache when the physics object is
   :doc:`linked </files/linked_libraries/index>` into another blend-file.
   When this option is enabled, linked versions of the object will reference the same disk cache.
   Otherwise linked versions of the object will use independent caches.

Compression
   The compression level for cache files. Some physics caches can be very large,
   Blender can compress these caches in order to save space.

   None
      Do not compress the cache.
   Light
      Compression will optimize the speed of compressing/decompressing operations over file size.
   Heavy
      Compression will result in smaller cache files more than *Light*,
      however, requires more CPU time to compress/decompress.

Start
   Frame on which to start the simulation.
End
   Frame on which to stop the simulation.

   .. note::

      The simulation is only calculated for positive frames
      in between the *Start* and *End* frames of the *Cache* panel, whether you bake or not.
      So if you want a simulation that is longer than the default frame range you have to change the *End* frame.

Cache Step
   Interval for storing simulation data.

   .. note::

      Some physics systems (such as particles)
      allow for positions to be stored only on every nth frame,
      letting the positions for in-between frames be interpolated.
      Using a cache step greater than one will result in a smaller cache,
      but the result may differ from the original simulation.


.. _physics-bake:

Baking
======

Bake
   Start baking.
   Blender will become unresponsive during most baking operations.
   The cursor will display as a number representing the progress of the baking.
   You need to be in Object Mode to bake.

.. _free-physics-bake:

Free Bake
   Mark the baked cache as temporary. The data will still exist,
   but will be removed with the next object modification and frame change.
   This button is only available when the physics system has been baked.

.. _calc-physics-bake-to-frame:

Calculate to Frame
   Bake only up to the current frame. Limited by *End* frame set in the cache settings.
Current Cache to Bake
   Store any temporarily cached simulation data as a bake.
   Note that playing the animation will try to simulate any visible physics simulations.
   Depending on the physics type, this data may be temporarily cached.
   Normally such temporary caches are cleared when an object or setting is
   modified, but converting it to a bake will "save" it.

Bake All Dynamics
   Bake all physics systems in the scene, even those of different types.
   Useful for baking complex setups involving interactions between different physics types.

   See :ref:`Bake <physics-bake>`.
Free All Bakes
   Free bakes of all physics systems in the scene, even those of different types.

   See :ref:`Free Bake <free-physics-bake>`.
Update All to Frame
   Bake all physics systems in the scene to the current frame.

   See :ref:`Calculate To Frame <calc-physics-bake-to-frame>`.


## Collision

.. _bpy.types.CollisionModifier:
.. _bpy.types.CollisionSettings:

*********
Collision
*********

.. reference::

   :Mode:      Object Mode
   :Panel:     :menuselection:`Physics --> Collision`

:doc:`Particles </physics/particles/index>`, :doc:`Soft Bodies </physics/soft_body/index>`
and :doc:`Cloth objects </physics/cloth/index>` may collide with mesh objects.
:doc:`Boids </physics/particles/emitter/physics/boids>` try to avoid *Collision* objects.

- You may limit the effect on particles to a group of objects
  (in the :doc:`Field Weights panel </physics/particles/emitter/force_field>`).
- *Deflection* for soft body objects is difficult, they often penetrate the colliding objects.
- Hair particles ignore deflecting objects
  (but you can animate them as soft bodies which take deflection into account).

If you change the deflection settings for an object you have to recalculate the particle,
soft body or cloth system by *Delete Bake*, this is not done automatically.

.. figure:: /images/physics_collision_toggle.png
   :align: right

A collider object can be temporarily disabled via an animatable toggle to
the right of the button that permanently activates or deactivates it.


Options
=======

.. figure:: /images/physics_collision_panel.png

   Collision panel.


Collision
---------

Field Absorption
   A deflector can also deflect effectors. You can specify some collision/deflector objects which deflect
   a specific portion of the effector force using the *Field Absorption* value. 100% absorption results in no force
   getting through the collision/deflector object at all. If you have three collision object behind each other with
   e.g. 10%, 43% and 3%, the absorption ends up at around 50% :math:`100 × (1 - 0.1) × (1 - 0.43) × (1 - 0.03)`.


Particle
--------

Permeability
   Fraction of particles passing through the mesh.
Stickiness
   How much particles stick to the object.
Kill Particles
   Deletes Particles upon impact.

Damping
   Damping during a collision (independent of the velocity of the particles).

   Randomize
      Random variation of damping.

Friction
   Friction during movements along the surface.

   Randomize
      Random variation of friction.


.. _physics-collision-soft-bodt-cloth:

Soft Body and Cloth
-------------------

It is also important to note that this collision panel is used to tell
all simulations that this object is to participate in colliding/deflecting other objects
on a shared layer (particles, soft bodies, and cloth).

.. note::

   The object's shape deforms the cloth,
   so the cloth simulation must be inputted the "true" shape of that mesh object at that frame.
   This true shape is the basis shape as modified by shape keys or armatures. Therefore,
   the Collision Modifier must be **after** any of those.
   The image to the right shows the *Modifiers* panel for the Character mesh object
   (not the cloth object).

   .. TODO2.8:
      .. figure:: /images/physics_collision_stack.png

         Collision stack.

Damping
   Damping during a collision.
   The amount of bounce that the surfaces will have.

   - 0.0 - No damping, soft bodies will have a maximum bounciness.
   - 1.0 - Maximum damping, soft bodies will not bounce at all.

Thickness
   A padding distance is added to the inside and outside of each face, to help to prevent intersections.
   The soft body will come to rest at this distance away from the face of the colliding object.
   Outside and inside is defined by the face normal, depicted as blue arrow in Fig. :ref:`fig-collision-soft-plane`.

   Outer
      Size of the outer collision zone.
   Inner
      Size of the inner collision zone (padding distance).

.. _fig-collision-soft-plane:

.. figure:: /images/physics_collision_outer-inner.png
   :width: 380px

   A soft body vertex colliding with a plane.

Friction
   A coefficient for how slippery the cloth is when it collides with itself.
   For example, silk has a lower coefficient of friction than cotton.

Single Sided
   When enabled, the collider is considered to represent the boundary of a solid object
   rather than a thin surface, and ejects intersecting cloth in the direction of its normal.

Override Normals
   When enabled, cloth collision impulses act in the direction of the collider normals.

.. note::

   *Soft body* collisions are difficult to get perfect.
   If one of the objects move too fast, the soft body will penetrate the mesh.
   See also the section about :doc:`Soft Bodies </physics/soft_body/index>`.


Examples
========

.. figure:: /images/physics_collision_defected-particles.png

   Deflected particles.

Here is a *Meta* object, using Instancing Vertices to a particle system emitting downwards,
and deflected by a mesh cube.


Hints
=====

- Make sure that the normals of the mesh surface are facing towards the particles/points
  for correct deflection. Negative scales on the object can have a similar effect.
  Make sure to recalculate the normals after applying the scale.
- Hair particles react directly to force fields,
  so if you use a force field with a short range you do not need necessarily collision.
- Hair particles avoid their emitting mesh if you edit them in *Particle Edit Mode*.
  So you can at least model the hair with collision.


## Index

.. _physics-index:

###########
  Physics
###########

.. toctree::
   :maxdepth: 2

   introduction.rst
   rigid_body/index.rst
   cloth/index.rst
   soft_body/index.rst
   fluid/index.rst
   particles/index.rst
   dynamic_paint/index.rst
   forces/index.rst
   collision.rst
   baking.rst
   simulation_nodes.rst


## Introduction


************
Introduction
************

Blender's physics system allows you to simulate a number of different real-world physical phenomena.
You can use these systems to create a variety of static and dynamic effects such as:

- Hair, grass, and flocks
- Rain
- Smoke and dust
- Water
- Cloth
- Jello
- etc.


.. _bpy.ops.object.quick:

Quick Effects
=============

.. reference::

   :Editor:    3D Viewport
   :Mode:      Object Mode
   :Menu:      :menuselection:`Object --> Quick Effects`

Sets up a basic simulation scene or effect including the selected objects.
The tool will add essential objects like domains or particle systems both with predefined settings,
so that there will be instant viewable result.


.. _bpy.ops.object.quick_fur:

Quick Fur
---------

Adds a fur setup to the selected objects.
The fur setup is based on :doc:`/modeling/geometry_nodes/index` and built with
:doc:`Hair Node Groups </modeling/geometry_nodes/hair/index>` that come with Blender as bundled assets.

Density
   Surface density of generated hair curves.
Length
   Length of the generated hair curves.
Hair Radius
   The width of the hair, used for rendering engines.
View Percentage
   Factor applied on the density for the viewport.
Apply Hair Curves
   Applies the modifier that uses the :doc:`/modeling/geometry_nodes/hair/generation/generate_hair_curves` node group.
Noise
   Deforms hair curves using a noise texture.
   See the :doc:`/modeling/geometry_nodes/hair/deformation/hair_curves_noise` node group for more information.
Frizz
   Deforms hair curves using a random vector per point to frizz them.
   See the :doc:`/modeling/geometry_nodes/hair/deformation/frizz_hair_curves` node group for more information.


## Simulation Nodes


****************
Simulation Nodes
****************

Through the use of :doc:`Simulation Zones </modeling/geometry_nodes/simulation/simulation_zone>`,
:doc:`/modeling/geometry_nodes/index` can be used to create custom physic simulations through nodes.
Simulation zones allow the result of one frame to influence the next one.
That way even a set of simple rules can lead to complex results, with the passing of time.
The most common type of them is physics simulation, with specific solvers for physical phenomena.

.. seealso::

   Read more about :doc:`Simulation Zones </modeling/geometry_nodes/simulation/simulation_zone>`


Baking
======

The simulation is automatically cached during playback.
The valid cache can be seen as a strong yellow line in the timeline editor.
This allows for animators to quickly inspect all the previous frames of a simulation.

.. figure:: /images/modeling_geometry-nodes_simulation_baking_timeline.png
   :align: center

   Cached frames in the Timeline.

When the result is ready to be sent to a render-farm, it can be baked to disk.
This allows for the simulation to be rendered in a non-sequential order.

.. figure:: /images/modeling_geometry-nodes_simulation_baking.png
   :align: center

   Simulation and Physics, Geometry Nodes user interface.

.. note::

   Baking the simulation will bake all the simulations in all modifiers for the selected objects.

.. _bpy.ops.object.simulation_nodes_cache_calculate_to_frame:

Calculate to Frame
   Calculate simulations in geometry nodes modifiers from the start to current frame.

.. _bpy.ops.object.simulation_nodes_cache_bake:

Bake
   Bake simulations in geometry nodes modifiers.
   In order to bake the simulation, the blend-file must be saved to your computer.
   The location the file is saved determines where the baked data is also saved.
   The directory the baked data is saved to can be changed per modifier in the
   :ref:`Internal Dependencies <bpy.types.NodesModifier.simulation_bake_directory>`.

   .. _bpy.ops.object.simulation_nodes_cache_delete:

   Delete Cached Simulation
      Delete cached/baked simulations in geometry nodes modifiers

.. _bpy.types.Object.use_simulation_cache:

Cache
   For the cases where the current frame is the only one relevant,
   users can opt-out of caching the results to save memory.


Examples
========

Combined with the :doc:`/modeling/geometry_nodes/geometry/sample/index_of_nearest`,
this can be used for a number of sphere-based simulations.

.. figure:: /images/modeling_geometry-nodes_simulation_example.png
   :align: center

   Index of Nearest sample file CC-BY Sean Christofferson.


## Examples


********
Examples
********

To start with cloth, the first thing you need, of course, is some fabric. So,
let us delete the default cube and add a plane. In order to get some good floppy and flexible fabric,
you will need to subdivide it several times, about eight is a good number.
So :kbd:`Tab` into *Edit Mode* and subdivide the mesh a couple of times.

Now, we will make this cloth by going to the Physics tab.
Scroll down until you see the *Cloth* panel, and press the *Cloth* button.
Now, a lot of settings will appear, most of which we will ignore for now.

That is all you need to do to set your cloth up for animating,
but if you playback the animation, the drop of your newly created fabric will be quite unspectacular.
That is what we will cover in the next two sections about pinning and colliding.


Using Simulation to Shape/Sculpt a Mesh
=======================================

You can *Apply* the Cloth Modifier at any point to freeze the mesh in
position at that frame. You can then re-enable the cloth,
setting the start and end frames from which to run the simulation forward.

Another example of aging is a flag.
Define the flag as a simple grid shape and pin the edge against the flagpole.
Simulate for 50 frames or so, and the flag will drop to its "rest" position.
Apply the *Cloth* Modifier.
If you want the flag to flap or otherwise move in the scene,
re-enable it for the frame range when it is in camera view.


Smoothing of Cloth
==================

Now, if you followed this from the previous section, your cloth is probably looking a little blocky.
In order to make it look nice and smooth like the picture you need to apply
a Smooth and/or Subdivision Surface Modifier in the *Modifiers* tab.
Then, in the Toolbar, find the *Edit* panel and Press *Smooth*.


Cloth on Armature
=================

Clothing can be simulated and pinned to an armature.
For example, a character could have a baggy tunic pinned to the character's waist with a belt.

The typical workflow for pinning:

#. Set the armature to its bind pose.
#. Model clothing that encloses but does not penetrate the character's mesh.
#. Parent the clothing objects to the armature. The armature will now have several child meshes bound to it.
#. Create a new vertex group on each cloth object for its pinned vertices.
#. Add vertices to be pinned to this vertex group and give these vertices nonzero weights
   (you probably want weight = 1).
   For example the belt area of the tunic would be in the vertex group and have weight one.
#. Designate the clothing objects as "cloth" in the Physics tab of the Properties.
   Make sure the Cloth Modifier is below the Armature Modifier in the modifier stack.
#. In the cloth Shape panel select the vertex group.
#. Add :doc:`collision physics </physics/collision>` to the character's mesh.
#. The clothing is now ready; non-pinned vertices will be under control of the Cloth modifier.
   Pinned vertices will be under control of the Armature modifier.

.. note::

   When animating or posing the character you must begin from the bind pose.
   Move the character to its initial pose over several frames so the physics engine can simulate the clothing moving.
   Very fast movements and teleport jumps can break the physics simulation.

`Regression blend-file <https://archive.blender.org/wiki/2015/index.php/File:Cloth-regression-armature.blend>`__.


Cloth with Animated Vertex Groups
=================================

Cloth with animated pinned vertices:
`Regression blend-file <https://archive.blender.org/wiki/2015/index.php/File:Cloth_anim_vertex.blend>`__.
Unsupported: Starting with a goal of 0 and increasing it,
but still having the vertex not pinned will **not** work (e.g. from goal = 0 to goal = 0.5).


Cloth with Dynamic Paint
========================

Cloth with Dynamic Paint using animated vertex groups:
`Regression blend-file <https://archive.blender.org/wiki/2015/index.php/File:Cloth_dynamic_paint.blend>`__.
Unsupported: Starting with a goal of 0 and increasing it, but still having the vertex not pinned will **not** work
(e.g. from goal = 0 to goal = 0.5) because the necessary "goal springs" cannot be generated on-the-fly.


Using Cloth for Soft Bodies
===========================

.. figure:: /images/physics_cloth_examples_softbody1.jpg
   :width: 200px

   Using cloth for soft bodies.

Cloth can also be used to simulate soft bodies.
It is for sure not its main purpose but it works nonetheless.
The example image uses standard *Rubber* material, no fancy settings,
just :kbd:`Alt-A`.

Blend-file for the example image:
`Using Cloth for soft bodies <https://archive.blender.org/wiki/2015/index.php/File:Cloth-sb1.blend>`__.


Cloth with Wind
===============

.. figure:: /images/physics_cloth_examples_flag2.jpg
   :width: 200px

   Flag with wind applied.

Regression blend-file for Cloth with wind and self-collisions (also the blend for the image above):
`Cloth flag with wind and self-collisions <https://archive.blender.org/wiki/2015/index.php/File:Cloth-flag2.blend>`__.


## Index

.. _bpy.types.ClothModifier:
.. _bpy.ops.cloth:

#########
  Cloth
#########

.. toctree::
   :maxdepth: 2

   introduction.rst
   settings/index.rst
   examples.rst


## Introduction


************
Introduction
************

Cloth simulation is one of the hardest aspects of computer graphics,
it is a deceptively simple real-world item that is taken for granted,
but it actually has very complex internal and environmental interactions.
Cloth is commonly modeled as 2D mesh to simulate real world objects such as fabrics, flags, banners.
And yet cloth can also be used to model 3D objects such as teddy bears, pillows, balloons, or balls.

Cloth interacts with and is affected by other moving objects,
the wind and other forces, as well as a general aerodynamic model,
all of which is under your control.

.. list-table::

   * - .. figure:: /images/physics_cloth_introduction_example1.jpg

          Cloth example.

     - .. figure:: /images/physics_cloth_introduction_oncarved-wood.jpg

          Cloth on carved wooden men (made by motorsep).

     - .. figure:: /images/physics_cloth_introduction_example2.jpg

          Cloth example.

Once Cloth physics have been added to a mesh, a :doc:`/modeling/modifiers/physics/cloth`
will be added to the object's modifier stack. As a modifier then,
it can interact with other modifiers, such as *Armature* and *Smooth*. In these cases,
the ultimate shape of the mesh is computed in accordance with the order of the modifier stack.
For example, you should smooth the cloth *after* the modifier computes the shape of the cloth.

You can *Apply* the Cloth Modifier to freeze, or lock in,
the shape of the mesh at that frame, which removes the modifier. For example,
you can drape a flat cloth over a table, let the simulation run, and then apply the modifier.
In this sense, you are using the simulator to save yourself a lot of modeling time.

Results of the simulation are saved in a cache, so that the shape of the mesh,
once calculated for a frame in an animation, does not have to be recomputed again.
If changes to the simulation are made, you have full control over clearing the cache and re-running the simulation.
Running the simulation for the first time is fully automatic and no baking or separate step interrupts the workflow.

Computation of the shape of the cloth at every frame is automatic and done in the background;
thus you can continue working while the simulation is computed. However, it is CPU-intensive
and depending on the power of your PC and the complexity of the simulation,
the amount of CPU needed to compute the mesh varies, as does the lag you might notice.

.. note:: Do Not Jump Ahead

   If you set up a cloth simulation but Blender has not computed the shapes for the duration of the simulation,
   and if you jump ahead a lot of frames forward in your animation,
   the cloth simulator may not be able to compute or show you an accurate mesh shape for that frame,
   if it has not previously computed the shape for the previous frame(s).


Workflow
========

A general process for working with cloth is to:

#. Model the cloth object as a general starting shape.
#. Designate the object as a "cloth" in the *Physics* tab of the Properties.
#. Model other deflection objects that will interact with the cloth.
   Ensure the Deflection modifier is last on the modifier stack, after any other mesh deforming modifiers.
#. Light the cloth and assign materials and textures, UV unwrapping if desired.
#. If desired, give the object particles, such as steam coming off the surface.
#. Run the simulation and adjust settings to obtain satisfactory results.
   The Timeline editors playback controls are great for this step.
#. Optionally age the mesh to some point in the simulation to obtain a new default starting shape.
#. Make minor edits to the mesh on a frame-by-frame basis to correct minor tears.

.. tip::

   To avoid unstable simulation, make sure that the cloth object does not penetrate any of the deflection objects.


.. _physics-cloth-introduction-springs:

Springs
=======

Internally, cloth physics is simulated with virtual springs that connect the vertices of a mesh.
There are four types of springs that control how the cloth bends.
These four types are defined below and illustrated in the following image:

.. figure:: /images/physics_cloth_introduction_springs.png
   :align: center

   Illustration of cloth springs; tension springs (blue),
   compression springs (red), shear springs (cyan),
   and angular bending springs (green).

Tension Springs
   Control the stiffness of the cloth.
Compression Springs
   Control the amount of force required to collapse or compress the cloth.
Shear Springs
   Like compression springs but it controls the angular deformation.
Angular Bending Springs
   Control how resilient the cloth is to folding or crumpling.

All four of these spring types can be controlled independently in
the :doc:`/physics/cloth/settings/physical_properties` panel. While these settings
control surface springs, optionally, internal springs can be used for 3D meshes
and behave similarly to :doc:`Soft Bodies </physics/soft_body/index>`.


## Cache

*****
Cache
*****

.. reference::

   :Panel:     :menuselection:`Physics --> Cloth Cache`

After you have set up the deflection mesh for the frame range you intend to run the simulation
(including animating that mesh *via* armatures),
you can now tell the cloth simulation to compute (and avoid) collisions.
Select the cloth object and in the *Object* tab,
*Physics* tab, set the *Start* and *End* settings for
the simulation frames you wish to compute, and click the *Bake* button.

Cache settings for cloth are the same as with other dynamic systems.
See :doc:`Particle Cache </physics/particles/emitter/cache>` for details.

.. note::

   If you move or edit the cloth object **after** you have already run the simulations,
   you must clear the cache; otherwise, Blender will use the position of
   the current/cached mesh's vertices when trying to represent where they are.

.. note:: Subdivision Surface Modifier

   A bake/cache is done for every subdivision level so please use
   the **equal** subdivision level for render and preview.

.. note::

   You cannot change *Start* or *End* without clearing the bake simulation.
   When the simulation has finished, you will notice you have the option to free
   the bake, edit the bake and re-bake.


Editing the Cached Simulation
=============================

.. important::

   Editing the cached simulation is not currently working, see:
   `blender/blender#77114 <https://projects.blender.org/blender/blender/issues/77114>`__ for details.

.. The cache contains the shape of the mesh at each frame. You can edit the cached simulation,
   after you have baked the simulation and pressed the *Bake Editing* button.
   Just go to the frame you want to fix and :kbd:`Tab` into *Edit Mode*.
   There you can move your vertices using all of Blender's mesh shaping tools. When you exit,
   the shape of the mesh will be recorded for that frame of the animation.
   If you want Blender to resume the simulation using the new shape going forward,
   select *Rebake from next Frame* and play the animation.
   Blender will then pick up with that shape and resume the simulation.

   Edit the mesh to correct minor tears and
   places where the colliding object has punctured the cloth.

   If you add, delete, or extrude vertices in the mesh, Blender will take the new mesh as
   the starting shape of the mesh back to the *first frame* of the animation,
   replacing the original shape you started with,
   up to the frame you were on when you edited the mesh. Therefore,
   if you change the content of a mesh, when you press :kbd:`Tab` out of *Edit Mode*,
   you should unprotect and clear the cache so that Blender will make a consistent simulation.


## Collisions

.. _bpy.types.ClothCollisionSettings:

**********
Collisions
**********

.. reference::

   :Panel:     :menuselection:`Physics --> Cloth --> Collision`

In most cases, a piece of cloth does not just hang there in 3D space,
it collides with other objects in the environment. To ensure proper simulation,
there are several items that have to be set up and working together:

- The *Cloth* object must be told to participate in collisions.
- Optionally (but recommended) tell the cloth to collide with itself.
- Other objects must be visible to the *Cloth* object *via* shared layers.
- The other objects must be mesh objects.
- The other objects may move or be themselves deformed by other objects (like an armature or shape key).
- The other mesh objects must be told to deflect the cloth object.
- The blend-file must be saved in a directory so that simulation results can be saved.
- You then *Bake* the simulation. The simulator computes the shape of the cloth for a frame range.
- You can then edit the simulation results, or make adjustments to the cloth mesh, at specific frames.
- You can make adjustments to the environment or deforming objects,
  and then re-run the cloth simulation from the current frame forward.

.. figure:: /images/physics_cloth_settings_collisions_panel.png

   Cloth Collisions panel.

.. _bpy.types.ClothCollisionSettings.collision_quality:

Quality
   A general setting for how fine and good a simulation you wish.
   Higher numbers take more time but ensure less tears and penetrations through the cloth.


.. _bpy.types.ClothCollisionSettings.use_collision:

Object Collisions
-----------------

If the cloth object needs to be deflected by some other object. To deflect a cloth,
the object must be enabled as an object that collides with the cloth object.
To enable objects to collide with cloth objects enable
:ref:`collision physics <physics-collision-soft-bodt-cloth>`
for the collider object (not on the cloth object).

.. note::

   If your colliding object is not a mesh object, such as a NURBS surface, or a text object,
   you must convert it to a mesh object using :ref:`object-convert-to`.

.. _bpy.types.ClothCollisionSettings.distance_min:

Distance
   The distance another object must get to the cloth for
   the simulation to repel the cloth out of the way.
   Smaller values might give errors but gives some speed-up while
   larger will give unrealistic results if too large and can be slow.
   It is best to find a good in between value.

.. _bpy.types.ClothCollisionSettings.impulse_clamp:

Impulse Clamping
   Prevents explosions in tight and complicated collision situations
   by restricting the amount of movement after a collision.

.. _bpy.types.ClothCollisionSettings.vertex_group_object_collisions:

Vertex Group
   Faces that have all vertices assigned to this
   :doc:`Vertex Group </modeling/meshes/properties/vertex_groups/index>` are excluded from collision with objects.

.. _bpy.types.ClothCollisionSettings.collection:

Collision Collection
   Only objects that are a part of this :doc:`Collection </scene_layout/collections/index>`
   can collide with the cloth. Note that these objects must also have Collision physics enabled.


.. _bpy.types.ClothCollisionSettings.use_self_collision:

Self-Collisions
---------------

Real cloth cannot penetrate itself, so you normally want the cloth to self-collide.
Enable this to tell the cloth object that it should not penetrate itself.
This adds to the simulation's compute time, but provides more realistic results.

.. tip::

   A flag, viewed from a distance does not need this enabled,
   but a close-up of a cape or blouse on a character should have this enabled.

.. _bpy.types.ClothCollisionSettings.self_friction:

Friction
   A coefficient for how slippery the cloth is when it collides with itself.
   For example, silk has a lower coefficient of friction than cotton.

.. _bpy.types.ClothCollisionSettings.self_distance_min:

Distance
   As cloth at this distance begins to repel away from itself.
   Smaller values might give errors but gives some speed-up while
   larger will give unrealistic results if too large and can be slow.
   It is best to find a good in between value.

.. _bpy.types.ClothCollisionSettings.self_impulse_clamp:

Impulse Clamping
   Prevents explosions in tight and complicated collision situations
   by restricting the amount of movement after a collision.

.. _bpy.types.ClothCollisionSettings.vertex_group_self_collisions:

Vertex Group
   Faces that have all vertices assigned to this
   :doc:`Vertex Group </modeling/meshes/properties/vertex_groups/index>` are excluded from self-collision.

.. seealso::

   Example blend-file:
   `Cloth self-collisions <https://archive.blender.org/wiki/2015/index.php/File:Cloth-regression-selfcollisions.blend>`__.


Troubleshooting
===============

If you encounter some problems with collision detection, there are a few ways to fix them:

- The fastest solution is to increase the *Distance* for Object/Self Collisions.
  This will be the fastest way to fix the clipping; however, it will be less accurate and will not look as good.
  Using this method tends to make it look like the cloth is resting on air, and gives it a very rounded look.
- A second method is to increase the *Quality* (in the *Cloth* panel).
  This results in smaller steps for the simulator and
  therefore to a higher probability that fast-moving collisions get caught.
  You can also increase the Collisions *Quality* to perform more iterations to get collisions solved.
- If none of the methods help, you can easily edit the cached/baked result in *Edit Mode* afterwards.
- If the Cloth is torn by the deforming mesh; increase the stiffness settings.


## Field Weights


*************
Field Weights
*************

.. reference::

   :Panel:     :menuselection:`Physics --> Cloth --> Field Weights`

As other physics dynamics systems, Cloth simulation is also influenced by external force effectors.


## Index

.. _bpy.types.ClothSettings:

############
  Settings
############

.. reference::

   :Panel:     :menuselection:`Physics --> Cloth`


Presets
   Contains a number of :ref:`preset <ui-presets>` cloth examples.

.. _bpy.types.ClothSettings.quality:

Quality Steps
   Set the number of simulation steps per frame. Higher values result in better quality, but will be slower.

.. _bpy.types.ClothSettings.time_scale:

Speed Multiplier
   Adjust how fast time progresses in the cloth simulation.

.. toctree::
   :maxdepth: 2

   physical_properties.rst
   cache.rst
   shape.rst
   collisions.rst
   property_weights.rst
   field_weights.rst


## Physical Properties

.. |kg/m3| replace:: kg/m\ :sup:`3`

*******************
Physical Properties
*******************

.. reference::

   :Panel:     :menuselection:`Physics --> Cloth --> Physical Properties`

.. _bpy.types.ClothSettings.mass:

Vertex Mass
   The mass of the cloth material.

.. _bpy.types.ClothSettings.air_damping:

Air Viscosity
   Air has some thickness which slows falling things down.

.. _bpy.types.ClothSettings.bending_model:

Bending Model
   :Linear: Cloth model with linear bending springs (old).
   :Angular: Cloth model with angular bending springs.


Stiffness
=========


.. _bpy.types.ClothSettings.tension_stiffness:

Tension
   How much the material resists stretching.

.. _bpy.types.ClothSettings.compression_stiffness:

Compression
   How much the material resists compression.

Structural
   Overall stiffness of the cloth (only in linear bending model).

.. _bpy.types.ClothSettings.shear_stiffness:

Shear
   How much the material resists shearing.

.. _bpy.types.ClothSettings.bending_stiffness:

Bending
   Wrinkle coefficient. Higher creates more large folds.


Damping
=======

.. _bpy.types.ClothSettings.tension_damping:

Tension
   Amount of damping in stretching behavior.

.. _bpy.types.ClothSettings.compression_damping:

Compression
   Amount of damping in compression behavior.

Structural
   Amount of damping in stretching behavior (only in linear bending model).

.. _bpy.types.ClothSettings.shear_damping:

Shear
   Amount of damping in shearing behavior.

.. _bpy.types.ClothSettings.bending_damping:

Bending
   Amount of damping in bending behavior.


.. _bpy.types.ClothSettings.use_internal_springs:

Internal Springs
================

As stated in the introduction, cloth physics are simulated through :ref:`physics-cloth-introduction-springs`
connecting vertices on the surface of a mesh. But these springs only interact on the surface
and only apply to 2D surfaces. 3D or *Internal Springs* can be used to make a mesh behave similarly to
a :doc:`Soft Body </physics/soft_body/index>`. Internal springs can be enabled by toggling the checkbox in
the *Internal Springs* panel header.

.. _bpy.types.ClothSettings.internal_spring_max_length:

Max Spring Creation Length
   The maximum length an internal spring can have during creation.
   If the distance between internal points is greater than this,
   no internal spring will be created between these points.
   A length of zero means that there is no length limit.

.. _bpy.types.ClothSettings.internal_spring_max_diversion:

Max Creation Diversion
   The maximum angle that is allowed to use to connect the internal points can diverge from the vertex normal.

.. _bpy.types.ClothSettings.internal_spring_normal_check:

Check Surface Normals
   Requires the points the internal springs connect to have opposite normal directions.

.. _bpy.types.ClothSettings.internal_tension_stiffness:

Tension
   How much the material resists stretching.

.. _bpy.types.ClothSettings.internal_compression_stiffness:

Compression
   How much the material resists compression.

.. _bpy.types.ClothSettings.vertex_group_intern:

Vertex Group
   The *Tension* and *Compression* of internal springs can be controlled via
   a :doc:`Vertex Group </modeling/meshes/properties/vertex_groups/index>` to
   specify which the portions of the mesh have internal springs or the spring strength.

.. _bpy.types.ClothSettings.internal_tension_stiffness_max:

Max Tension
   Maximum tension stiffness value.

.. _bpy.types.ClothSettings.internal_compression_stiffness_max:

Max Compression
   Maximum Compression stiffness value.


.. _bpy.types.ClothSettings.use_pressure:

Pressure
========

Cloth pressure allows the simulation of soft-shelled objects
such as balloons or balls that are filled with a type of fluid.
This fluid is modeled as a gas; to emulate an incompressible liquid set
*Pressure Scale* as high as possible without breaking the simulation.
Cloth pressure can be enabled by toggling the checkbox in the *Pressure* panel header.

.. note::

   :term:`Non-manifold` meshes will work with cloth pressure however,
   pressure will escape out of the mesh holes and cause drifting or propulsion forces.
   One way to get around this is by using the *Vertex Group* to exclude the non-manifold portions of the mesh.

.. _bpy.types.ClothSettings.uniform_pressure_force:

Pressure
   The uniform pressure that is constantly applied to the mesh.
   This value is specified in units of *Pressure Scale*, and can be
   negative to simulate implosions or any other case where an object
   has outside pressure pushing inwards.

.. _bpy.types.ClothSettings.use_pressure_volume:

Custom Volume
   Use the *Target Volume* parameter as the initial volume for the cloth,
   instead of computing it from the mesh itself.

.. _bpy.types.ClothSettings.target_volume:

Target Volume
   The mesh volume where the inner/outer pressure will be the same.
   If set to zero, changes in the volume of the object will not affect pressure.

.. _bpy.types.ClothSettings.pressure_factor:

Pressure Scale
   Ambient pressure (in kPa) that exists both inside and outside the object,
   balancing out when the volume matches the target. Increase the value to
   make the object resist changes in volume more strongly.

.. _bpy.types.ClothSettings.fluid_density:

Fluid Density
   Specifies the density of the fluid contained inside the object
   (in kg/liter = 1000 |kg/m3|, use 1 for water), used to generate
   a hydrostatic pressure gradient that simulates the weight of the fluid.
   If the value is negative, it instead models buoyancy from a surrounding fluid.

   The fluid is not actually simulated, so while the setting helps to achieve
   a more plausible object shapes at rest, it cannot create realistic fluid dynamics effects.
   It can also be used to give more weight to a soft body like object with heavy and
   sufficiently flexible filling, even if it is not a fluid by itself.

   The volume of the object is not preserved. If that is desired it should be used
   together with *Pressure Scale*. *Fluid density* times *object size* times 50
   is a good start value for *Scale* to make sure that no more than 10% volume change
   if the object does not experience higher acceleration than standard gravity.

.. _bpy.types.ClothSettings.vertex_group_pressure:

Vertex Group
   Cloth pressure can be controlled via a :doc:`Vertex Group </modeling/meshes/properties/vertex_groups/index>`
   to specify which the portions of the mesh to apply pressure.
   Zero weight means no pressure while a weight of one means full pressure.

   Note, faces with a vertex that has zero weight will be excluded from the *Target Volume* calculation.


## Property Weights


****************
Property Weights
****************

.. reference::

   :Panel:     :menuselection:`Physics --> Cloth --> Property Weights`

This panel is used to constrain certain cloth properties to a certain vertex group.
The properties that they control can be found in a combination of the *Physical Properties* and *Shape* panels.

.. _bpy.types.ClothSettings.vertex_group_structural_stiffness:

Structural Group
   Defines a vertex group to control over structural stiffness.

.. _bpy.types.ClothSettings.tension_stiffness_max:

Max Tension
   Maximum tension stiffness value.

.. _bpy.types.ClothSettings.compression_stiffness_max:

Max Compression
   Maximum Compression stiffness value.

.. _bpy.types.ClothSettings.vertex_group_shear_stiffness:

Shear Group
   Vertex group for fine control over shear stiffness.

.. _bpy.types.ClothSettings.shear_stiffness_max:

Max Shearing
   Maximum shear scaling value.

.. _bpy.types.ClothSettings.vertex_group_bending:

Bending Group
   Vertex group for fine control over bending stiffness.

.. _bpy.types.ClothSettings.bending_stiffness_max:

Max Bending
   Maximum bending stiffness value.

.. _bpy.types.ClothSettings.vertex_group_shrink:

Shrinking Group
   Vertex group for shrinking cloth.

.. _bpy.types.ClothSettings.shrink_max:

Max Shrinking
   Max amount to shrink cloth by, specifying a negative value controls the max amount for the cloth to grow.


## Shape


*****
Shape
*****

.. reference::

   :Panel:     :menuselection:`Physics --> Cloth --> Shape`

.. figure:: /images/physics_cloth_settings_shape_pinning.png

   Cloth Shape.

.. _bpy.types.ClothSettings.vertex_group_mass:

Pin Group
   Vertex group to use for pinning.

   The shape of the cloth can be controlled by pinning cloth to
   a :doc:`Vertex Group </modeling/meshes/properties/vertex_groups/index>`.
   There are several ways of doing this including
   :doc:`Weight Painting </sculpt_paint/weight_paint/index>` areas you want to pin.
   The weight of each vertex in the group controls how strongly it is pinned.

.. _bpy.types.ClothSettings.pin_stiffness:

Stiffness
   Target position stiffness.

.. _bpy.types.ClothSettings.use_sewing_springs:

Sewing
   Another method of restraining cloth similar to pinning is sewing springs.
   Sewing springs are virtual springs that pull vertices in one part of
   a cloth mesh toward vertices in another part of the cloth mesh.
   This is different from pinning which binds vertices of the cloth mesh in place or to another object.
   A clasp on a cloak could be created with a sewing spring.
   The spring could pull two corners of a cloak about a character's neck.
   This could result in a more realistic simulation than pinning the cloak to
   the character's neck since the cloak would be free to slide about the character's neck and shoulders.

   Sewing springs are created by adding extra edges to a cloth mesh that are not included in any faces.
   They should connect vertices in the mesh that should be pulled together.
   For example the corners of a cloak.

.. _bpy.types.ClothSettings.sewing_force_max:

Max Sewing Force
   Maximum force that can be applied by sewing springs. Zero means unbounded, but it is not
   recommended to leave the field at zero in most cases, as it can cause instability due to
   extreme forces in the initial frames where the ends of the sewing springs are far apart.

.. _bpy.types.ClothSettings.shrink_min:

Shrinking Factor
   Factor by which to shrink the cloth, specifying a negative value controls the amount for the cloth to grow.

.. _bpy.types.ClothSettings.use_dynamic_mesh:

Dynamic Mesh
   Allows animating the rest shape of cloth using shape keys or
   modifiers (e.g. an Armature modifier or any deformation modifier) placed above the Cloth modifier.
   When it is enabled, the rest shape is recalculated every frame, allowing unpinned
   cloth to squash and stretch following the character with the help of shape keys or modifiers, but
   otherwise move freely under control of the physics simulation.

   Normally cloth uses the state of the object in the first frame to compute
   the natural rest shape of the cloth, and keeps that constant throughout the simulation.
   This is reasonable for fully realistic scenes, but does not quite work for clothing
   on cartoon style characters that use a lot of squash and stretch.

.. _bpy.types.ClothSettings.rest_shape_key:

Rest Shape Key
   Allows starting the cloth simulation using a specific
   :doc:`Shape Key </animation/shape_keys/index>` as the rest state,
   instead of the shape that results from evaluating shape keys and preceding modifiers
   in the regular way. This option is mutually exclusive with *Dynamic Mesh*.

   This can be used to start the simulation with the cloth in a pre-draped state without
   applying that shape as a plastic deformation that relaxes all springs as a side effect.

   This property is only visible if the mesh has shape keys.


## Brush

.. _bpy.types.DynamicPaintBrushSettings:

*****
Brush
*****

.. reference::

   :Panel:     :menuselection:`Physics --> Dynamic Paint`
   :Type:      Brush

The Brush type makes object apply paint on the canvas.

.. figure:: /images/physics_dynamic-paint_brush_main-panel.png

   Brush main panel.

From the first brush panel you can define how brush affects canvas color surfaces.

Paint Color
   Color of the paint.
Alpha
   Defines brush alpha or visibility. Final wetness is also affected by alpha.
Wetness
   Defines how "wet" new paint is. Wetness is visible on "Paint" surface "wetmap".
   Speed of "Drip" and "Spread" effects also depends on how wet the paint is.
Absolute Alpha
   This setting limits brush alpha influence.
   Without it, brush is "added" on surface over and over again each frame,
   increasing alpha and therefore influence of brush on canvas. In many cases however,
   it is preferred to not increase brush alpha if it already is on brushes level.
Erase Paint
   Makes brush dissolve existing paint instead of adding it.


Source
======

.. reference::

   :Type:      Brush
   :Panel:     :menuselection:`Physics --> Dynamic Paint --> Source`

.. TODO2.8:
   .. figure:: /images/physics_dynamic-paint_brush_source-panel.png

      Paint source panel.

*Paint* source setting lets you define how brush influence/intersection is defined.


.. rubric:: Mesh Volume

The Brush affects all surface point inside the mesh volume.

.. figure:: /images/physics_dynamic-paint_brush_source-mesh-volume.png

   Source: Mesh Volume.

.. rubric:: Proximity

Only uses defined distance to the closest point on brush mesh surface.
Note that inside of the volume is not necessarily affected because it is not close to the surface.

.. figure:: /images/physics_dynamic-paint_brush_source-proximity.png

   Source: Proximity. Brush affects all canvas pixels around it.

.. rubric:: Mesh Volume + Proximity

Same as volume type, but also has influence over defined distance.

Inner Proximity
   Applies proximity inside the mesh volume.
Negate Volume
   Negates brush alpha within mesh volume.

.. list-table::

   * - .. figure:: /images/physics_dynamic-paint_brush_source-mesh-volume-proximity-1.png

          The Volume + Proximity brush with no additional settings.

     - .. figure:: /images/physics_dynamic-paint_brush_source-mesh-volume-proximity-2.png

          Inner Proximity. Proximity falloff is now visible inside the volume.

   * - .. figure:: /images/physics_dynamic-paint_brush_source-mesh-volume-proximity-3.png

          Negate Volume. Inner side of the volume has become completely transparent.

     - .. figure:: /images/physics_dynamic-paint_brush_source-mesh-volume-proximity-4.png

          Inner Proximity and Negate Volume enabled together.

.. rubric:: Object Center

Instead of calculating proximity to the brush object mesh, which can be quite slow in some cases,
only distance to only center is calculated. This is much faster and often good enough.

.. figure:: /images/physics_dynamic-paint_brush_source-object-center.png

   Source: Object Center.

.. rubric:: Particle System

Brush influence is defined by particles from a selected particle system.

.. figure:: /images/physics_dynamic-paint_brush_solid-smooth-radius.png
   :align: right

Effect Solid Radius
   Defines the distance, inside which paint is solid color.

Use Particle Radius
   Uses the settings in the particle panel to determine solid radius size.
   Solid Radius size disabled while Particle Radius enabled.

Smooth Radius
   An additional radius outside Solid Radius to add a smooth falloff.

   If you set "Smooth Radius" to zero, particle will be painted as a solid sphere.
   If you set "Solid Radius" to zero, it gets painted as a smooth halo.

   .. figure:: /images/physics_dynamic-paint_brush_solid-smooth-radius-values.jpg
      :align: center

   .. figure:: /images/physics_dynamic-paint_brush_source-particle-system.png

      Source: Particle System.


Common Options
--------------

Paint Distance
   The maximum distance to mesh surface to affect paint.

Project
   Projects brush to the canvas from a defined direction.
   Basically this can be considered as "direction aligned" proximity.

   .. figure:: /images/physics_dynamic-paint_brush_source-project.png

      The Project option enabled. See how brush only affects canvas in normal direction.

Falloff
   :Sharp:
      Paints solid paint within the defined distance.
   :Smooth:
      Makes paint to linearly fade out until becoming completely invisible
      when it reaches the maximum distance.
   :Color Ramp:
      Allows you to manually make a custom falloff behavior.


Velocity
========

.. reference::

   :Type:      Brush
   :Panel:     :menuselection:`Physics --> Dynamic Paint --> Velocity`

.. TODO2.8:
   .. figure:: /images/physics_dynamic-paint_brush_velocity-panel.png

      Velocity panel.

This panel shows brush options that are based on object velocity.

On top you have a color ramp and several related settings.
Basically the color ramp represents brush velocity values:
left side being zero velocity and right side being the "Max velocity".
Speed is measured in "units per frame".

Checkboxes above can be used to define color ramp influence.

Multiply Alpha
   Uses color ramp's alpha value depending on current velocity and multiplies brush alpha with it.
Replace Color
   Replaces the brush color with the values from the :ref:`ui-color-ramp-widget`.
Multiply Depth
   Multiplies brushes "depth intersection" effect.
   Basically you can adjust displace and wave strength depending on brush speed.
Do Smudge
   Enabling Smudge makes the brush "smudge" (or "smear") existing colors on the surface as it moves.
   The strength of this effect can be defined from the *Smudge Strength* property.

   Even when smudge is enabled brush still does its normal paint effect.
   If you want a purely smudging brush use zero alpha.
   It is also possible to have *Erase* option enabled together with smudge.


Waves
=====

.. reference::

   :Type:      Brush
   :Panel:     :menuselection:`Physics --> Dynamic Paint --> Waves`

.. TODO2.8:
   .. figure:: /images/physics_dynamic-paint_brush_waves-panel.png

      Brush Waves panel.

This panel is used to adjust brush influence to "Wave" surfaces.

.. _bpy.types.DynamicPaintBrushSettings.wave_type:

Wave Type
   Select what effect the brush creates in the wave simulation.

   :Depth Change:
      The brush create waves when the intersection depth with the surface is *changed* on that point.
      If the brush is not moved, it will have no effect.

      Using a negative "Factor" with this type can create a nice looking "wake" for moving objects like ships.
   :Obstacle:
      Constantly affects surface whenever intersecting.
      Waves are also reflected off this brush type.
      However, due the nature of wave simulation algorithm this type creates
      an unnatural "dent" in the surface if the brush is not moved.
   :Force:
      Directly affects the velocity of wave motion.
      Therefore the effect is not one-to-one with brush intersection depth, yet the force strength depends on it.
   :Reflect Only:
      This type has no visible effect on the surface alone but reflects waves that are already on the surface.

.. _bpy.types.DynamicPaintBrushSettings.wave_factor:

Factor
   Adjusts how strongly brush "depth" affects the simulation.
   You can also use negative values to make brush pull water up instead of down.

.. _bpy.types.DynamicPaintBrushSettings.wave_clamp:

Clamp Waves
   In some cases the brush goes very deep inside the surface messing whole simulation up.
   You can use this setting to "limit" influence to only certain depth.


## Canvas

.. _bpy.types.DynamicPaintCanvasSettings:

******
Canvas
******

.. reference::

   :Panel:     :menuselection:`Physics --> Dynamic Paint`
   :Type:      Canvas

The Canvas type makes object receive paint from Dynamic Paint brushes.


Settings
========

.. figure:: /images/physics_dynamic-paint_canvas_main-panel.png
   :align: right

   Canvas main panel.

Paint Surface
   A :ref:`list <ui-list-view>` of Dynamic Paint surfaces.
   These surfaces are basically layers of paint, that work independently from each other.
   You can define individual settings for them and bake them separately.

   Is Active
      The checkbox toggles whether surface is active at all.
      If not selected no calculations are done.

Below you can set surface type and adjust quality and timing settings.

Format
   Each surface has a certain format and type.
   Format determines how data is stored and outputted.

   :Vertex:
      Dynamic Paint operates directly on mesh vertex data.
      Results are stored by point cache and can be displayed in viewports.
      However, using vertex level also requires a highly subdivided mesh to work.
   :Image Sequences:
      Dynamic Paint generates UV wrapped image files of defined resolution as output.

      Resolution
         You can adjust the output image dimensions for the *Image Sequences* surface type.
         For example using 256 will lead to 256×256 image output.
         Doubling the resolution will likely quadruple the baking time and vice versa.
      Anti-Aliasing
         :term:`Anti-Aliasing` to smooth paint edges using a 5× multisampling method.

Frame Start, End
   Defines surface processing start and end frame.

Sub-Steps
   Extra samples between frames. They are usually required when there is a very fast brush.


Surface
=======

.. reference::

   :Type:      Canvas
   :Panel:     :menuselection:`Physics --> Dynamic Paint --> Surface`

.. TODO2.8:
   .. figure:: /images/physics_dynamic-paint_canvas_advanced-panel.png

      Canvas advanced panel.

From *Surface* panel you can adjust surface type and related settings.


Surface Type
------------

Each surface has a "type" that defines what surface is used for.


Paint
^^^^^

.. figure:: /images/physics_dynamic-paint_canvas_surface-type-paint.jpg
   :width: 320px

   Paint Surface.

Paint is the basic surface type that outputs color and wetness values.
In case of vertex surfaces, results are outputted as Color Attributes.

A wetmap is a black-and-white output that visualizes paint wetness. White being maximum wetness,
black being completely dry. It is usually used as mask for rendering.
Some "paint effects" affect wet paint only.

Dry
   Completely disable drying is useful for indefinitely spreading paint.

   Color Dry
      It can be used to define wetness level when paint colors start to shift to surface "background".
      Lower values can be useful to prevent spreading paint from becoming transparent as it dries,
      while higher values give better results in general.


Displace
^^^^^^^^

.. figure:: /images/physics_dynamic-paint_canvas_surface-type-displace.jpg
   :width: 320px

   Displace Surface.

This type of surface outputs intersection depth from brush objects.

Incremental
   A new displace is added cumulatively on top of an existing displace.
Max Displace
   The maximum level of intersection depth, larger values will be clamped to this value.
Displace Factor
   The multiplier for the intersection depth.
   You can use it to adjust final displace strength or use negative values to paint bumps.

.. tip::

   If the displace output seems too rough it usually helps to add
   a Smooth Modifier after Dynamic Paint in the modifier stack.


Waves
^^^^^

.. figure:: /images/physics_dynamic-paint_canvas_surface-type-waves.jpg
   :width: 320px

   Waves Surface.

This surface type produces simulated wave motion. Like displace,
wave surface also uses brush intersection depth to define brush strength.

Open Borders
   Allows waves to pass through mesh "edges" instead of reflecting from them.
Timescale
   Directly adjusts simulation speed without affecting simulation outcome.
   Lower values make simulation go slower and otherwise.
Speed
   Affects how fast waves travel on the surface.
   This setting is also corresponds to the size of the simulation.
   Half the speed equals surface double as large.
Damping
   Reduces the wave strength over time. Basically adjusts how fast wave disappears.
Spring
   Adjusts the force that pulls water back to "zero level".
Smoothness
   Limits the maximum steepness of the wave slope between simulation points.
   This greatly helps getting rid of the "noise" that occurs
   when using objects with sharp edges (like cubes) as a brush.
   The default value should be enough to only get rid of the sharpest spikes,
   in order to get even smoother waves use higher values at the expense of reduced detail.

.. tip::

   In some cases the wave motion gets very unstable around brush.
   It usually helps to reduce wave speed, brush "wave factor" or even the resolution of mesh/surface.


Weight
^^^^^^

.. figure:: /images/physics_dynamic-paint_canvas_surface-type-weight.jpg
   :width: 320px

   Weight Surface.

This is a special surface type only available for vertex format.
It outputs vertex weight groups that can be used by other Blender modifiers and tools.

.. tip::

   It is usually preferred to use "proximity" based brushes for
   weight surfaces to allow smooth falloff between weight values.


Common Options
--------------

For each surface type there are special settings to adjust.
Most types have the settings *Dissolve* and *Brush*:

Dissolve
   Used to make the surface smoothly return to its original state during a defined *Time* period.
Brush Collection
   Used to define a specific collection to pick brush objects from.
Influence Scale, Radius Scale
   For tweaking brush settings individually for each surface.


Cache
=====

.. reference::

   :Type:      Canvas
   :Panel:     :menuselection:`Physics --> Dynamic Paint --> Cache`

.. TODO2.8:
   .. figure:: /images/physics_dynamic-paint_canvas_cache-panel.png

      Canvas cache panel.

This panel is currently only visible for *Vertex* format surfaces.
You can use it to adjust and bake point cache.


Effects
=======

.. reference::

   :Type:      Canvas
   :Panel:     :menuselection:`Physics --> Dynamic Paint --> Effects`

.. TODO2.8:
   .. figure:: /images/physics_dynamic-paint_canvas_effects-panel.png

      Effects panel.

This is a special feature for "Paint" type surface.
It generates animated movement on canvas surface.

.. (TODO) each of these effects has its own settings

Effects
   Spread
      Paint slowly spreads to surrounding points eventually filling all connected areas.
   Drip
      Paint moves in specific direction specified by Blender force fields,
      gravity and velocity with user-defined influences.
   Shrink
      Painted area slowly shrinks until disappears completely.

For spread and drip effects, only "wet paint" is affected, so as the paint dries,
movement becomes slower until it stops.


Initial Color
=============

.. reference::

   :Type:      Canvas
   :Panel:     :menuselection:`Physics --> Dynamic Paint --> Initial Color`

Allows you to define the initial color of the canvas. (Todo 2.62)

- None
- Color
- UV Texture
- Vertex Color


Output
======

.. reference::

   :Type:      Canvas
   :Panel:     :menuselection:`Physics --> Dynamic Paint --> Output`

.. TODO2.8:
   .. figure:: /images/physics_dynamic-paint_canvas_output-panel.png

      Canvas Output panel.

From Output panel you can adjust how surface outputs its results.


Vertex
------

For *Vertex* format surfaces, you can select a mesh data layer
(color/weight depending on surface type) to generate results to.
You can use the "+"/"-" icons to add/remove a data layers of given name.
If layer with given name is not found, it is shown as red.


Image Sequence
--------------

For *Image Sequence* surfaces,
you can define used UV maps and output file saving directory, filenames and image format.


## Index

.. _bpy.types.DynamicPaintModifier:
.. _bpy.ops.dpaint:

#################
  Dynamic Paint
#################

.. toctree::
   :maxdepth: 2

   introduction.rst
   brush.rst
   canvas.rst


## Introduction


************
Introduction
************

Dynamic paint is a modifier and physics system that can turn objects into paint canvases
and brushes, creating Color Attributes, image sequences, or displacement.
This makes many effects possible like, for example footsteps in the snow,
raindrops that make the ground wet, paint that sticks to walls, or objects that gradually freeze.


Activating the Modifier
=======================

.. figure:: /images/physics_dynamic-paint_introduction_activate.png

   How to activate the Dynamic Paint.

Dynamic Paint can be activated from the "Physics" tab of the "Properties" editor.


Types
=====

Modifier itself has two different types
:doc:`Canvas </physics/dynamic_paint/canvas>` and :doc:`Brush </physics/dynamic_paint/brush>`.

.. note::

   You can also enable brush and canvas simultaneously.
   In that case same object's "brush" does not influence its "canvas",
   but can still interact with other objects in the scene.

.. seealso::

   - `A step-by step introduction <https://miikahweb.com/en/articles/blender-dynamicpaint-basics>`__.
   - `A detailed guide <https://miikahweb.com/en/articles/dynamic-paint-guide>`__
     that covers every setting with images and examples (currently not up-to-date).


## Index


#########
  Fluid
#########

.. toctree::
   :maxdepth: 2

   introduction.rst
   type/index.rst
   material.rst


## Introduction


************
Introduction
************

Liquid Simulations
==================

Fluid physics are used to simulate physical properties of liquids especially water.
While creating a scene in Blender, certain objects can be marked to become a part of the fluid simulation.
For a fluid simulation you have to have a domain to define the space that the simulation takes up.
In the domain settings you will be able to define the global simulation parameters (such as viscosity
and gravity).

.. figure:: /images/physics_fluid_introduction_liquid-example.png
   :align: center

   Example of a liquid simulation.


Gas Simulations
===============

Gas or smoke simulations are a subset of the fluids system, and can be used for simulating collections
of airborne solids, liquid particulates and gases, such as those that make up smoke.
It simulates the fluid movement of air and generates animated :term:`Voxel`
textures representing the density, heat, and velocity of other fluids or suspended particles
(e.g. smoke) which can be used for rendering.

.. figure:: /images/physics_fluid_introduction_fire-example.png
   :align: center

   Example of a fire simulation.

Gases or smoke are emitted inside of a :doc:`Domain </physics/fluid/type/domain/index>` from
a mesh object or particle system. The smoke movement is controlled by airflow inside the domain,
which can be influenced by :doc:`Effector </physics/fluid/type/effector>` objects.
Smoke will also be affected by the scene's gravity and :doc:`force fields </physics/forces/force_fields/index>`.
Airflow inside the domain can affect other physics simulations
via the :doc:`Fluid Flow </physics/forces/force_fields/types/fluid_flow>` force field.


Workflow
========

At least a :doc:`Domain </physics/fluid/type/domain/index>` object and
one :doc:`Flow </physics/fluid/type/flow>` object are required to create a fluid simulation.

#. Create a :doc:`Domain object </physics/fluid/type/domain/index>`
   that defines the bounds of the simulation volume.
#. Set up :doc:`Flow </physics/fluid/type/flow>` objects which will emit fluid.
#. Set up :doc:`Effector </physics/fluid/type/effector>` objects to make
   the fluid interact with objects in the scene.
#. Assign a :doc:`material </physics/fluid/material>` to the domain object.
#. Save the blend-file.
#. :doc:`Bake the Cache </physics/fluid/type/domain/cache>` for the simulation.

.. note::

   There are :ref:`Quick Liquid and Quick Smoke <bpy.ops.object.quick>` tools
   which will automatically create a domain object with a basic liquid or smoke and fire material.


## Material


*********
Materials
*********

Smoke Material
==============

Realistic smoke can be rendered with
the :doc:`Principled Volume </render/shader_nodes/shader/volume_principled>` shader.

`Smoke Material Example Animation <https://www.youtube.com/watch?v=hxV_bHG4fl8>`__


## Effector


********
Effector
********

Effector objects are used to deflect fluids and influence the fluid flow. To define any mesh object
as an effector object, add fluid physics by clicking *Fluid* in :menuselection:`Properties --> Physics`.
Then select *Effector* as the fluid *Type*.

.. tip::

   :doc:`Force Fields </physics/forces/force_fields/index>`
   (such as wind or vortex) are supported, like in most physics systems.
   The influence individual force types have can be
   :doc:`controlled </physics/fluid/type/domain/field_weights>` per domain object.


.. _bpy.types.FluidEffectorSettings:

Settings
========

.. reference::

   :Panel:     :menuselection:`Physics --> Fluid --> Settings`
   :Type:      Effector

.. _bpy.types.FluidEffectorSettings.effector_type:

Effector Type
   Collision
      Objects of this type will collide with fluid.

   Guide
      The velocity of objects of this type will be used when baking the guiding.
      So fluid guiding objects should move and have some velocity.

      .. _bpy.types.FluidEffectorSettings.velocity_factor:

      Velocity Factor
         Multiply the guiding object velocities by this factor. This is useful when working with
         multiple guiding objects and some of them should have higher or smaller velocities.

      .. _bpy.types.FluidEffectorSettings.guide_mode:

      Guide Mode
         The mode describes how guiding velocities should be written into the global guiding velocity
         field of the domain.

         Maximize
            The guiding object will compare the existing velocity in the global velocity field with
            its own velocity. If its absolute value is greater than the absolute value in the velocity
            field the guiding velocity will be kept.

         Minimize
            A guiding object will compare the existing velocity in the global velocity field with its
            own velocity. If its absolute value is smaller than the absolute value in the velocity
            field the guiding velocity will be kept.

         Override
            The most intuitive option. A guiding object will always
            write its own current velocity into the global guiding velocity field.
            Values in the velocity field from a previous frame or guiding object
            will be overridden.

         Averaged
            A guiding object will write the average of its own current velocity and the existing
            guiding velocity at that cell into the global guiding velocity field.

.. _bpy.types.FluidEffectorSettings.subframes:

Effector Substeps
   Number of substeps used to reduce gaps in collision of fluid from fast-moving effectors.

.. _bpy.types.FluidEffectorSettings.surface_distance:

Surface Thickness
   Additional area around the effector that will be considered as an effector.

.. _bpy.types.FluidEffectorSettings.use_effector:

Use Effector
   Enables or disables the effector object effect on the fluid,
   this property is useful for animations to selectively enable and disable
   when the effector affects the fluid.

.. _bpy.types.FluidEffectorSettings.use_plane_init:

Is Planar
   Defines the effector as either a single dimension object i.e. a plane or the mesh is :term:`Non-manifold`.
   This ensures that the fluid simulator will give the most accurate results for these types of meshes.

   A :term:`Manifold` mesh can also be declared as planar. The fluid solver will then ignore the volume
   inside the mesh and just emit fluid from the mesh sides.


## Flow


****
Flow
****

Fluid *Flow* types are used to add or remove fluid to a domain object. Flow objects should be
contained within the domain's :term:`Bounding Box` in order to work.

To define any mesh object as a *Flow* object, add Fluid physics by clicking *Fluid* in
:menuselection:`Properties --> Physics`. Then select *Flow* as the fluid *Type*. Now you should have
a default fluid flow source object.


.. _bpy.types.FluidFlowSettings:

Settings
========

.. reference::

   :Panel:     :menuselection:`Physics --> Fluid --> Settings`
   :Type:      Flow

.. _bpy.types.FluidFlowSettings.flow_type:

Flow Type
   Smoke
      Emit only smoke.

   Fire + Smoke
      Emit both fire and smoke.

   Fire
      Emit only fire. Note that the domain will automatically create some smoke to simulate smoke
      left by burnt fuel.

   Liquid
      Emit liquid.

.. _bpy.types.FluidFlowSettings.flow_behavior:

Flow Behavior
   Controls if the Flow object either adds (*Inflow*), removes (*Outflow*),
   or turns the mesh itself into fluid (*Geometry*).

   Inflow
      This object will emit fluid into the simulation, like a water tap or base of a fire.

   Outflow
      Any fluid that enters the :term:`Bounding Box` of this object will be removed from
      the domain (think of a drain or a black hole). This can be useful in combination with
      an inflow to prevent the whole domain from filling up. Outflow objects can be animated
      and the area where the fluid disappears will follow the object as it moves around.

   Geometry
      All regions of this object that are inside the domain bounding box will be used as
      actual fluid in the simulation. You can place more than one fluid object inside the domain.
      Also make sure that the surface normals are pointing outwards or else they will not simulate
      properly. In contrast to domain objects, the actual mesh geometry is used for fluid objects.

.. _bpy.types.FluidFlowSettings.use_flow:

Use Flow
   Enables or disables the flow of fluid, this property is useful for animations to selectively enable and
   disable when fluid is being added to or removed from the domain.

.. _bpy.types.FluidFlowSettings.subframes:

Sampling Substeps
   Number of sub-steps used to reduce gaps in emission of fluid from fast-moving sources.

   .. list-table:: Comparison of smoke inflow quickly rising upwards at different sub-step rates.

      * - .. figure:: /images/physics_fluid_type_flow_substep-off.png

             Sampling sub-steps: 0.

        - .. figure:: /images/physics_fluid_type_flow_substep-on.png

             Sampling sub-steps: 3.

   Note that these emission sub-steps occur at every simulation step and not per frame.
   The simulation step count is controlled by the adaptive time stepping.

.. _bpy.types.FluidFlowSettings.smoke_color:

Smoke Color
   The color of emitted smoke. When smoke of different colors are mixed they will blend together,
   eventually settling into a new combined color.

.. _bpy.types.FluidFlowSettings.use_absolute:

Absolute Density
   If this checkbox is enabled, the emitter will only produce more smoke or fire if there is space for
   it in the emitter region. Otherwise smoke or fire will always be produced and add up.

.. _bpy.types.FluidFlowSettings.temperature:

Initial Temperature
   Difference between the temperature of emitted smoke and the domain's ambient temperature.
   This setting's effect on smoke depends on the domain's :ref:`Heat Buoyancy <bpy.types.FluidDomainSettings.beta>`.

.. _bpy.types.FluidFlowSettings.density:

Density
   Amount of smoke to emit at once. Larger values result in more density being produced.

.. _bpy.types.FluidFlowSettings.fuel_amount:

Fuel
   Amount of "fuel" being burned per second. Larger values result in larger flames,
   smaller values result in smaller flames:

   .. list-table:: Comparison of flames with varying fuel rates.

      * - .. figure:: /images/physics_fluid_type_flow_fuelrate-0-5.png

             Fuel: 0.5.

        - .. figure:: /images/physics_fluid_type_flow_fuelrate-1-0.png

             Fuel: 1.0.

.. _bpy.types.FluidFlowSettings.density_vertex_group:

Vertex Group
   When set, use the specified :doc:`Vertex Group </modeling/meshes/properties/vertex_groups/vertex_groups>`
   to control where smoke is emitted.


.. _bpy.types.FluidFlowSettings.use_particle_size:

Flow Source
-----------

.. _bpy.types.FluidFlowSettings.flow_source:

Flow Source
   This setting defines the method used to emit fluid.

   Mesh
      Emit fluid directly from the object's mesh.

      .. _bpy.types.FluidFlowSettings.use_plane_init:

      Is Planar
         Defines the effector as either a single dimension object i.e. a plane or the mesh is :term:`Non-manifold`.
         This ensures that the fluid simulator will give the most accurate results for these types of meshes.

      .. _bpy.types.FluidFlowSettings.surface_distance:

      Surface Emission
         Maximum distance in :term:`Voxels <Voxel>` from the surface of the mesh in which fluid is emitted.
         Since this setting uses voxels to determine the distance,
         results will vary depending on the domain's resolution.

      .. _bpy.types.FluidFlowSettings.volume_density:

      Volume Emission :guilabel:`Fire or Smoke Only`:
         Amount of fluid to emit inside the emitter mesh, where 0 is none and 1 is the full amount.
         Note that emitting fluid based on volume can have unpredictable results
         if your mesh is :term:`Non-manifold`.

   .. _bpy.types.FluidFlowSettings.particle_system:

   Particle System :guilabel:`Fire or Smoke Only`:
      Create smoke or fire from a particle system on the flow object.
      The particle system can be selected with a :ref:`ui-data-id`.

      Note that only *Emitter* type particle systems can add smoke.
      See :doc:`Particles </physics/particles/introduction>` for information on
      how to create a particle system.

      Set Size
         When this setting is enabled, it allows the *Size* setting to define the maximum distance in voxels
         at which particles can emit smoke, similar to the *Surface Emission* setting for mesh sources.

         When disabled, particles will fill the nearest :term:`Voxel` with smoke.


.. _bpy.types.FluidFlowSettings.use_initial_velocity:

Initial Velocity
----------------

When enabled, the fluid will inherit the momentum of the flow source.

.. _bpy.types.FluidFlowSettings.velocity_factor:

Source
   Factor for the inherited velocity. A value of 1 will emit fluid moving at the same speed as the source.

.. _bpy.types.FluidFlowSettings.velocity_normal:

Normal
   This option controls how much velocity fluid is given along a face :term:`Normal`.
   Note that, initial velocities will always be applied along all face normals.
   Thus with a closed flow source mesh, fluid will always be emitted in more than one direction.
   To set initial velocities along only one direction all normals need to point in the same direction.
   This is can be achieved when using a plane as the flow object.

.. _bpy.types.FluidFlowSettings.velocity_coord:

Initial X, Y, Z
   Initial velocity along X, Y, Z coordinates in world space.
   This can be used in addition to the initial velocity along
   the :ref:`Normal <bpy.types.FluidFlowSettings.velocity_normal>`.


.. _bpy.types.FluidFlowSettings.use_texture:

Texture
-------

.. reference::

   :Type:      Flow
   :Panel:     :menuselection:`Physics --> Fluid --> Settings --> Texture`

When enabled, use the specified texture and settings to control where on
the mesh smoke or fire can be emitted from. These settings have no effect on *Outflow Flow Behavior*.

.. _bpy.types.FluidFlowSettings.noise_texture:

Texture
   A :ref:`ui-data-id` selector to choose the :doc:`Texture </render/materials/legacy_textures/index>`.

.. _bpy.types.FluidFlowSettings.texture_map_type:

Mapping
   Controls whether to use :ref:`Generated UVs <properties-texture-space>` or manual UV mapping.

.. _bpy.types.FluidFlowSettings.texture_size:

Size
   Overall texture scale.

.. _bpy.types.FluidFlowSettings.texture_offset:

Offset
   Translates the texture along the Z axis.


## Index

.. _bpy.types.FluidModifier.fluid_type:

########
  Type
########

.. toctree::
   :maxdepth: 2

   domain/index.rst
   flow.rst
   effector.rst


## Cache


*****
Cache
*****

.. reference::

   :Panel:     :menuselection:`Physics --> Fluid --> Cache`
   :Type:      Domain

The *Cache* panel is used to :term:`Bake <Baking>` the fluid simulation and stores the outcome of
a simulation so it does not need to be recalculated.

Baking takes a **lot** of compute power (hence time). Depending on the scene, it is recommended
to allocate enough time for the baking process.

If the mesh has modifiers, the rendering settings are used for exporting the mesh to the fluid solver.
Depending on the setting, calculation times and memory use might exponentially increase. For example,
when using a moving mesh with *Subdivision Surface* as an obstacle, it might help to decrease simulation
time by switching it off, or to a low subdivision level. When the setup/rig is correct, you can always
increase settings to yield a more realistic result.

.. note::

   Fluid simulations use their own cache. All other physics simulations make use of
   the :doc:`General Baking </physics/baking>` operators.

.. _bpy.types.FluidDomainSettings.cache_directory:

Cache Directory
   Directory to store baked simulation files in. Inside this directory each simulation type
   (i.e. mesh, particles, noise) will have its own directory containing the simulation data.

.. _bpy.types.FluidDomainSettings.cache_type:

Type
   The type of the cache determines how the cache can be baked.

   Replay
      The cache will be baked as the simulation is being played in the viewport.

   Modular
      The cache will be baked step by step: The bake operators for this type are spread across various panels within
      the domain settings (e.g. the bake tool for the mesh can be found in the Mesh panel).

   All
      The cache will be baked with a single tool. All selected settings will be considered during this bake.
      The bake tool for this type can be found in the Cache panel.

   .. important::

      "Replay" only works when the :ref:`Playback Sync mode <bpy.types.Scene.sync_mode>` is set to "Play Every Frame".
      If you need to use "Frame Dropping" or "Sync to Audio", consider using the "Modular" or "All" options below.


.. _bpy.types.FluidDomainSettings.cache_frame_start:

Start
   Frame on which to start the simulation. This is the first frame that will be baked.

.. _bpy.types.FluidDomainSettings.cache_frame_end:

End
   Frame on which to stop the simulation. This is the last frame that will be baked.

   .. note::

      The simulation is only calculated for positive frames between the *Start* and *End* frames
      of the *Cache* panel. So if you want a simulation that is longer than the default frame range
      you have to change the *End* frame.

.. _bpy.types.FluidDomainSettings.cache_frame_offset:

Offset
   Frame offset that is used when loading the simulation from the cache.
   It is not considered when baking the simulation, only when loading it.

.. _bpy.types.FluidDomainSettings.use_resumable_cache:

Use Resumable Cache
   Extra data will be saved so that you can resumed baking after pausing. Since more data will be written
   to drive it is recommended to avoid enabling this option when baking at high resolutions.

.. _bpy.types.FluidDomainSettings.cache_data_format:

Volume File Format
   File format for volume based simulation data (i.e. grids and particles).

   Uni Cache
      Blender's own caching format with some compression.
      Each simulation object is stored in its own ``.uni`` cache file.

   OpenVDB
      Advanced and efficient storage format.
      All simulation objects (i.e. grids and particles) are stored in a single ``.vdb`` file per frame.

.. _bpy.types.FluidDomainSettings.cache_mesh_format:

Mesh File Format :guilabel:`Liquids Only`
   File format for the mesh cache files.

   Binary Object
      Mesh data files with some compression.

   Object
      Simple, standard data format for mesh data.

.. _bpy.ops.fluid.bake_all:
.. _bpy.ops.fluid.free_all:

Bake All, Free All
   This option is only available when using the :ref:`Final <bpy.types.FluidDomainSettings.cache_type>` cache type.
   *Bake All* will run the simulation considering all parameters from
   the settings (i.e. it will bake all steps that can be baked individually with
   the :ref:`Modular <bpy.types.FluidDomainSettings.cache_type>` cache type at once).

   The progress will be displayed in the status bar. Pressing :kbd:`Esc` will abort the simulation.

   Once the simulation has been baked, the cache can be deleted by pressing *Free All*.
   It is not possible to pause or resume a *Bake All* process as
   only the most essential cache files are stored on drive.


Advanced
========

.. _bpy.types.FluidDomainSettings.openvdb_cache_compress_type:

Compression Volumes :guilabel:`OpenVDB Only`
   Compression method that is used when writing OpenVDB cache files.

   None
      Cache files will be written without any compression.

   Zip
      Cache files will be written with ``Zip`` compression. Effective but slower than ``Blosc``.

   Blosc
      Cache files will be written with ``Blosc`` compression. Multithreaded compression,
      similar in size and quality to ``Zip`` compression.

.. _bpy.types.FluidDomainSettings.openvdb_data_depth:

Precision Volumes :guilabel:`OpenVDB Only`
   Precision level that is used when writing OpenVDB cache files.

   Full
      Volumetric data (e.g. grids, particles) will be written with full precision (32-bit).

   Half
      Volumetric data (e.g. grids, particles) will be written with half precision (16-bit).

   Mini
      Volumetric data (e.g. grids, particles) will be written with mini float precision (8-bit) where possible.
      For cache data where this is not possible, 16-bit floats will be used instead.

.. _bpy.types.FluidDomainSettings.export_manta_script:

Export Mantaflow Script
   Export the simulation as a standalone Mantaflow script when baking the scene (exported on "Bake Data").
   Usually, only developers and advanced users who know how to use the Mantaflow GUI will
   make use of this functionality. Use a :ref:`Debug Value <bpy.ops.wm.debug_menu>` of ``3001`` to enable.


## Collections

.. _bpy.types.FluidDomainSettings.effector_group:
.. _bpy.types.FluidDomainSettings.fluid_group:

***********
Collections
***********

.. reference::

   :Type:      Domain
   :Panel:     :menuselection:`Properties --> Physics --> Fluid --> Collections`

Flow
   If set, only objects in the specified :doc:`Collection </scene_layout/collections/collections>`
   will be allowed to act as :doc:`/physics/fluid/type/flow` objects in this domain.
Effector
   If set, only objects in the specified :doc:`Collection </scene_layout/collections/collections>`
   will be allowed to act as :doc:`/physics/fluid/type/effector` objects in this domain.


## Field Weights


*************
Field Weights
*************

.. reference::

   :Panel:     :menuselection:`Properties --> Physics --> Fluid --> Field Weights`
   :Type:      Domain

These settings determine how much gravity and
:doc:`Force Fields </physics/forces/force_fields/index>` affect the fluid.

Effector Collection
   When set, fluid can only be influenced by force fields in the specified collection.
Gravity
   How much the fluid is affected by Gravity.
All
   Overall influence of all force fields.

The other settings determine how much influence individual force field types have.


## Guides

.. _bpy.types.FluidDomainSettings.use_guide:

******
Guides
******

.. reference::

   :Panel:     :menuselection:`Physics --> Fluid --> Guides`
   :Type:      Domain

Fluid guides are used to apply forces onto the simulation. They are like simple external forces
but also seek to preserve the physically accurate flow of the fluid.
The *Guides* panel allows you to adjust guiding forces globally, i.e. for the entire domain.
Enabling the guides hints the fluid solver to use the more accurate,
but also computationally more expensive pressure solving step.

Even when there are no guiding objects baked or there is no guiding domain attached,
the fluid solver will still perform the more expensive pressure guiding algorithm
if guiding is enabled. It is
therefore recommended to only enable *Guides* when there is a clear intention to
use guiding in the simulation.

.. seealso::

   Fluid guiding is an implementation of
   `Primal-Dual Optimization for Fluids <https://ge.in.tum.de/publications/2017-cgf-eckert/>`__.

.. _bpy.types.FluidDomainSettings.guide_alpha:

Weight
   Controls the lag of the guiding. A larger value (also known as the 'alpha' guiding value)
   results in a greater lag.

.. _bpy.types.FluidDomainSettings.guide_beta:

Size
   This setting determines the size of the vortices that the guiding produces.
   A greater guiding size (also known as the blur radius or 'beta' guiding value)
   results in larger vortices.

.. _bpy.types.FluidDomainSettings.guide_vel_factor:

Velocity Factor
   All guiding velocities are multiplied by this factor. That is, every cell of the guiding grid,
   which has the same size as the domain object, is multiplied by this factor.

.. _bpy.types.FluidDomainSettings.guide_source:

Velocity Source
   Guiding velocities can either come from objects that move inside the domain or from other fluid
   domains.

   Effector
      All effector objects inside the domain will be considered for the global guiding velocity grid.
      Once effector objects have been baked it is not possible to change the fluid domain resolution
      anymore.

   Domain
      When using another fluid domain as the guiding velocity source this domain may have a different
      resolution and may also be of a different type (e.g. the guiding domain is of type *Gas*
      while the actual domain with the guiding effect in it is of type *Liquid*).

      In order to use a domain as the velocity source, this domain needs to be baked already.

.. _bpy.types.FluidDomainSettings.guide_parent:

Guide Parent
   When using *Domain* as the velocity source, this field serves to select the guiding domain object.

.. _bpy.ops.fluid.bake_guides:
.. _bpy.ops.fluid.free_guides:

Bake Guides, Free Guides
   This option is only available when using the :ref:`Modular <bpy.types.FluidDomainSettings.cache_type>` cache type
   and when using *Effector* as the :ref:`Velocity Source <bpy.types.FluidDomainSettings.guide_source>`.
   *Bake Guides* writes vertex velocities of effector objects to drive.
   It is meant to be used before baking the fluid simulation.

   The progress will be displayed in the status bar. Pressing :kbd:`Esc` will pause the simulation.

   Once the simulation has been baked, the cache can be deleted by pressing *Free Guides*.
   It is possible to pause or resume a *Bake Guides* process.


## Index

.. _bpy.types.FluidDomainSettings:

##########
  Domain
##########

.. toctree::
   :maxdepth: 2

   settings.rst
   gas/index.rst
   liquid/index.rst
   guides.rst
   collections.rst
   cache.rst
   field_weights.rst


## Settings


********
Settings
********

.. reference::

   :Panel:     :menuselection:`Physics --> Fluid --> Settings`
   :Type:      Domain

The domain object contains the entire simulation. Fluid simulations cannot leave the domain,
it will either collide with the edge or disappear, depending on the domain's settings.

Keep in mind that large domains need higher resolutions and longer bake times.
You will want to make it just large enough that the simulation will fit inside it,
but not so large that it takes too long to compute the simulation.

To create a domain, add a cube and transform it until it encloses the area where you want
the simulation to take place. Translation, rotation, and scaling are all allowed.
To turn it into a fluid domain, click *Fluid* in the :menuselection:`Properties --> Physics` tab,
then select *Domain* as the fluid *Type*.

.. note::

   You *can* use other shapes of mesh objects as domain objects,
   but the fluid simulator will use the shape's :term:`Bounding Box` as the domain bounds.
   In other words, the actual shape of the domain will still be rectangular.

.. _bpy.types.FluidDomainSettings.domain_type:

Domain Type
   A fluid domain can control either liquid or gas flows. Liquid domains take all liquid flow objects
   that intersect with the domain into consideration. Gas domains consider all
   intersecting *Smoke*, *Fire*, and *Smoke & Fire* flow objects. It is not possible to change
   the domain type dynamically.

.. _bpy.types.FluidDomainSettings.resolution_max:

Resolution Divisions
   The fluid domain is subdivided into many "cells" called :term:`Voxels <Voxel>`
   which make up "pixels" of fluid. This setting controls the number of subdivisions in the domain.
   Higher numbers of subdivisions are one way of creating higher resolution fluids.

   Since the resolution is defined in terms of "subdivisions",
   larger domains will need more divisions to get an equivalent resolution to a small domain.
   For example, a one meter cube with 64 *Resolution Divisions* will need 128 divisions to match a 2 meter cube.
   The dimension used as the base division is the longest dimension of the objects bounding box.
   To help visualize the voxel size, the *Resolution Divisions* can be previewed with a small cube
   shown in the 3D Viewport, to show the size of these divisions.

.. _bpy.types.FluidDomainSettings.time_scale:

Time Scale
   Controls the speed of the simulation. Low values result in a "slow motion" simulation,
   while higher values can be used to advance the simulation faster
   (good for generating fluids to be used in still renders).

.. _bpy.types.FluidDomainSettings.use_adaptive_timesteps:

Use Adaptive Time Steps
   Lets the solver automatically decide when to perform multiple simulation steps per frame.
   It takes into account the maximum and minimum number of time steps,
   the current *Frame Rate*, and the *Time Scale*.

.. _bpy.types.FluidDomainSettings.cfl_condition:

CFL Number
   Determines the maximum velocity per grid cell and is measured in grid cells per time step.
   Fluid is only allowed to move up to this velocity in one time step. If this threshold is
   exceeded the solver will subdivide the simulation step.

   In general, greater CFL
   (`Courant–Friedrichs–Lewy <https://en.wikipedia.org/wiki/Courant%E2%80%93Friedrichs%E2%80%93Lewy_condition>`__)
   numbers will minimize the number of simulation steps and the computation time.
   Yet it will yield less physically accurate behavior for fast fluid flows.
   Smaller CFL numbers result in more simulation steps per frame, longer simulation times
   but more accurate behavior at high velocities (e.g. fast fluid flow colliding
   with obstacle).

.. note::

   When lowering the *CFL* number it is recommended to increase the maximum number of time steps.
   Similarly, when increasing the *CFL* number the minimum number of time steps should be adjusted.

.. _bpy.types.FluidDomainSettings.timesteps_max:

Timesteps Maximum
   Maximum number of allowed time steps per frame. If needed, the solver will divide
   a simulation step up to this number of sub-steps.

.. _bpy.types.FluidDomainSettings.timesteps_min:

Timesteps Minimum
   Minimum number of allowed time steps per frame. The solver will always perform at least
   this number of simulation steps per frame.

.. _bpy.types.FluidDomainSettings.gravity:

Gravity
   By default the fluid solver will use the global scene gravity. This behavior can be disabled
   in the scene settings. Disabling the global gravity will enable the fluid gravity options.

.. _bpy.types.FluidDomainSettings.clipping:

Empty Space :guilabel:`Gas Only`
   Voxels with values under this value are considered empty space.
   More empty space optimizes rendering. With OpenVDB caching it also reduces cache sizes.

.. _bpy.types.FluidDomainSettings.delete_in_obstacle:

Delete in Obstacle
   Remover any volume of fluid that intersects with an obstacle inside the domain.


.. _bpy.types.FluidDomainSettings.use_collision_border_front:
.. _bpy.types.FluidDomainSettings.use_collision_border_back:
.. _bpy.types.FluidDomainSettings.use_collision_border_right:
.. _bpy.types.FluidDomainSettings.use_collision_border_left:
.. _bpy.types.FluidDomainSettings.use_collision_border_top:
.. _bpy.types.FluidDomainSettings.use_collision_border_bottom:

Border Collisions
=================

.. reference::

   :Panel:     :menuselection:`Physics --> Fluid --> Settings --> Border Collisions`
   :Type:      Domain (Gas)

Controls which sides of the domain will allow fluid "pass through" the domain, making it disappear
without influencing the rest of the simulation, and which sides will deflect fluids.


Gas
===

.. reference::

   :Panel:     :menuselection:`Physics --> Fluid --> Gas`
   :Type:      Domain (Gas)

.. _bpy.types.FluidDomainSettings.alpha:

Buoyancy Density
   Buoyant force based on gas density.

   - Values above 0 will cause the gas to rise (simulating gas which is lighter than ambient air).
   - Values below 0 will cause gas to sink (simulating gas which is heavier than ambient air).

.. _bpy.types.FluidDomainSettings.beta:

Buoyancy Heat
   Controls how much gas is affected by temperature.
   The effect this setting has on gas depends on the per flow object
   :ref:`Initial Temperature <bpy.types.FluidFlowSettings.temperature>`:

   - Values above 0 will result in the gas rising when the flow object *Initial Temperature* is
     set to a positive value, and gas sinking when the flow object *Initial Temperature* is
     set to a negative value.
   - Values below 0 will result in the opposite of positive values,
     i.e. gas emitted from flow objects with a positive *Initial Temperature* will sink,
     and gas from flow objects with a negative *Initial Temperature* will rise.

   Note that gas from multiple flow objects with different temperatures will mix and warm up or
   cool down until an equilibrium is reached.

.. _bpy.types.FluidDomainSettings.vorticity:

Vorticity
   Controls the amount of turbulence in the gas. Higher values will make lots of small swirls,
   while lower values make smoother shapes.

   .. list-table:: Comparison of different amounts of vorticity.

      * - .. figure:: /images/physics_fluid_type_domain_settings_vorticity-off.png

             Domain with a vorticity of 0.0.

        - .. figure:: /images/physics_fluid_type_domain_settings_vorticity-on.png

             Domain with a vorticity of 0.2.


.. _bpy.types.FluidDomainSettings.use_dissolve_smoke:

Dissolve
--------

Allow gas to dissipate over time.

.. _bpy.types.FluidDomainSettings.dissolve_speed:

Time
   Speed of gas dissipation in frames.

.. _bpy.types.FluidDomainSettings.use_dissolve_smoke_log:

Slow
   Dissolve gas in a logarithmic fashion. Dissolves quickly at first, but lingers longer.


Fire
====

.. reference::

   :Type:      Domain
   :Panel:     :menuselection:`Physics --> Fluid --> Gas --> Fire`

.. _bpy.types.FluidDomainSettings.burning_rate:

Reaction Speed
   How fast fuel burns. Larger values result in smaller flames (fuel burns before it can go very far),
   smaller values result in larger flames (fuel has time to flow farther before being fully consumed).

.. _bpy.types.FluidDomainSettings.flame_smoke:

Flame Smoke
   Amount of extra smoke created automatically to simulate burnt fuel. This smoke is best visible
   when using a "Fire + Smoke" :ref:`Flow Object <bpy.types.FluidFlowSettings.flow_type>`.

.. _bpy.types.FluidDomainSettings.flame_vorticity:

Vorticity
   Vorticity for flames in addition to the global fluid
   :ref:`Vorticity <bpy.types.FluidDomainSettings.vorticity>`.

.. _bpy.types.FluidDomainSettings.flame_max_temp:

Temperature Maximum
   Maximum temperature of flames. Larger values result in faster rising flames.

.. _bpy.types.FluidDomainSettings.flame_ignition:

Minimum
   Minimum temperature of flames. Larger values result in faster rising flames.

.. _bpy.types.FluidDomainSettings.flame_smoke_color:

Smoke Color
   Color of smoke emitted from burning fuel.


.. _bpy.types.FluidDomainSettings.use_flip_particles:

Liquid
======

.. reference::

   :Type:      Domain
   :Panel:     :menuselection:`Physics --> Fluid --> Liquid`

Liquid settings control the behavior of the particles which the simulation consists of.
Enabling the liquid checkbox will automatically create a particle system for the simulation.
This particle system visualizes the flow of the simulation. Visualizing the liquid particles is optional.
The fluid simulation will make use of all the fields without an attached particle system too.

.. note::

   Disabling the liquid checkbox will delete the attached particle system and its settings.

.. _bpy.types.FluidDomainSettings.simulation_method:

Simulation Method
   Determines the liquid particle simulation method.

   FLIP
      Produces a very splashy simulation with lots of particles dispersed in the air.

   APIC
      Produces a very energetic but also more stable simulation.
      Vortices within the liquid will be preserved better than with *FLIP*.

.. _bpy.types.FluidDomainSettings.flip_ratio:

FLIP Ratio :guilabel:`Simulation FLIP Only`:
   How much FLIP velocity to use when updating liquid particle velocities. A value of 1.0
   will result in a completely FLIP based simulation. Completely FLIP based simulations
   produce more chaotic splashes and are preferable when simulating greater quantities of liquid.
   When using smaller values the behavior will be less turbulent and splashes are more subtle.
   This is optimal when simulating scenes where the liquid is supposed to be on a small scale.

.. _bpy.types.FluidDomainSettings.sys_particle_maximum:

System Maximum
   Maximum number of fluid particles that are allowed in the simulation. If this field is set to a nonzero value
   the simulation will never contain more than this number of fluid particles. Otherwise, with a value of zero
   the solver will always sample new particles when needed.

.. _bpy.types.FluidDomainSettings.particle_radius:

Particle Radius
   The radius of one liquid particle in grid cells units. This value describes how much area is covered
   by a particle and thus determines how much area around it can be considered as liquid.
   A greater radius will let particles cover more area. This will result in more grids cell being tagged
   as liquid instead of just being empty.

   Whenever the simulation appears to leak or gain volume in an undesired, non physically accurate way it is
   a good idea to adjust this value. That is, when liquid seems to disappear this value needs to be increased.
   The inverse applies when too much liquid is being produced.

.. _bpy.types.FluidDomainSettings.particle_number:

Sampling
   Factor that is used when sampling particles. A higher value will sample more particles.
   Note that particle resampling occurs at every single simulation step.

.. _bpy.types.FluidDomainSettings.particle_randomness:

Randomness
   New particles are sampled with some randomness attached to their position
   which can be controlled by this field. Higher values will sample the liquid particles more
   randomly in inflow regions. With a value of 0.0 all new particles will be sampled uniformly inside
   their corresponding grid cells.

   When trying to create a laminar inflow (with little randomness) or more turbulent flows
   (with greater randomness) this value can be useful.

.. _bpy.types.FluidDomainSettings.particle_max:

Particles Maximum
   The maximum number of liquid particles per grid cell. During a simulation the number of liquid
   particles in a cell can fluctuate: Particles can flow into other cells or can get deleted
   if they move outside the narrow band. Resampling will add new particles considering this maximum.

   This value sets the upper threshold of particles per cell. It is also a good way to estimate how
   many particles there can be in your simulation (one needs to take grid resolution into account too).
   This can be useful before baking and when planning a simulation.

.. _bpy.types.FluidDomainSettings.particle_min:

Minimum
   The minimum number of liquid particles per grid cell. Similarly to the maximum particle threshold,
   this value ensures that there are at least a certain amount of particles per cell.

.. _bpy.types.FluidDomainSettings.particle_band_width:

Narrow Band Width
   Controls the width in grid cell units of the narrow band that liquid particles are allowed to flow in.
   A high value will result in a thicker band and can result in an inflow region completely filled
   with particles. Unless the goal of the simulation is to visualize the liquid particles it is
   recommended to not increase the band width significantly as more particles slow down the simulation.

   In some situations increasing this value can help create volume when the simulation appears to leak.
   In all other cases it is best to keep the narrow band as thin as possible since the liquid surface
   contains most details and simulating particles inside the liquid is not an optimal use of computing resources.

.. seealso::

   The narrow band is an implementation of `Narrow Band FLIP for Liquid Simulations
   <https://www.cs.cit.tum.de/cg/research/publications/2016/narrow-band-flip-for-liquid-simulations/>`__.

.. _bpy.types.FluidDomainSettings.use_fractions:

Fractional Obstacles
   Enables finer resolution in fluid / obstacle regions (second order obstacles).
   This option reduces the "stepping effect" that results when an obstacle lies inclined inside the domain.
   It also makes liquid flow more smoothly over an obstacle.

   .. _bpy.types.FluidDomainSettings.fractions_distance:

   Obstacle Distance
      Determines how far apart fluid and obstacles are. This value can be used to achieve a more fluid motion over
      inclined obstacles: Depending on the slope of the obstacle increasing this value can help liquid particles
      flow better over an obstacle.
      Setting this field to a negative value will let fluid move towards the inside of an obstacle.

   .. _bpy.types.FluidDomainSettings.fractions_threshold:

   Obstacle Threshold
      Value to control the smoothness of the fractional obstacle option. Smaller value reduce
      the "stepping effect" but may result particles sticking to the obstacle.

.. _bpy.ops.fluid.bake_data:
.. _bpy.ops.fluid.free_data:

Bake Data, Free Data
   This option is only available when using the :ref:`Modular <bpy.types.FluidDomainSettings.cache_type>` cache type.
   *Bake Data* simulates and stores the base of the fluid simulation on drive.
   Both gas and liquid simulations can add refinements on top of this
   (e.g. gas simulations can add noise, liquid simulations can add a mesh or secondary particles or both).

   The progress will be displayed in the status bar. Pressing :kbd:`Esc` will pause the simulation.

   Once the simulation has been baked, the cache can be deleted by pressing *Free Data*.
   It is possible to pause or resume a *Bake All* process.


## Adaptive Domain

.. _bpy.types.FluidDomainSettings.use_adaptive_domain:
.. _bpy.types.FluidDomainSettings.additional_res:
.. _bpy.types.FluidDomainSettings.adapt_margin:
.. _bpy.types.FluidDomainSettings.adapt_threshold:

***************
Adaptive Domain
***************

.. reference::

   :Type:      Domain
   :Panel:     :menuselection:`Physics --> Fluid --> Adaptive Domain`

When enabled, the domain will adaptively shrink to best fit the gas,
saving computation time by leaving voxels without gas out of the simulation.
Unless the *Add Resolution* is used, the adaptive domain will not exceed the bounds of the original domain.

Add Resolution
   Number of voxels to add around the outside of the domain.
Margin
   Amount of extra space to leave around gas, measured in voxels.
   With very fast-moving gas larger margins may be required to prevent the gas from being cut off
   by the adaptive boundary, but note this will increase the number of voxels which need to be computed.
Threshold
   Smallest amount of gas a voxel can contain before it is considered empty
   and the adaptive domain is allowed to cut it out of the simulation.


## Index


################
  Gas Settings
################

.. toctree::
   :maxdepth: 2

   adaptive_domain.rst
   noise.rst
   viewport_display.rst


## Noise

.. _bpy.types.FluidDomainSettings.use_noise:

*****
Noise
*****

.. reference::

   :Type:      Domain
   :Panel:     :menuselection:`Physics --> Fluid --> Noise`

Adding noise to the gas simulation creates a finer detailed looking simulation on top of the base.
This makes it possible to add more details to gases (i.e. fire or smoke or both) without changing
the overall fluid motion.

.. seealso::

   Fluid noise is an implementation of `Wavelet Turbulence for Fluid Simulation
   <http://www.cs.cornell.edu/~tedkim/WTURB/>`__.

Besides enabling parts of the interface, checking *Noise* lets the cache know
which simulation data to read. If, for example, *Noise* is enabled but
there is no noise simulation data to read it will show an empty domain.
The checkbox does not reset the cache and can be used to switch
the view between base resolution and noise view.

.. _bpy.types.FluidDomainSettings.noise_scale:

Upres Factor
   Factor by which to enhance the resolution of the noise. The scaling factor is coupled
   to the :ref:`Resolution Divisions <bpy.types.FluidDomainSettings.resolution_max>`.

.. _bpy.types.FluidDomainSettings.noise_strength:

Strength
   Strength of the noise. Higher values result in more turbulent vortices.

.. _bpy.types.FluidDomainSettings.noise_pos_scale:

Scale
   Scale of the noise. Greater values result in larger vortices.

.. _bpy.types.FluidDomainSettings.noise_time_anim:

Time
   Animation time of the noise. This value has an influence on where the noise field is evaluated.
   It can be used as a seed to give wavelet noise a slightly different look in two domains that are
   otherwise the same.

   .. list-table:: Smoke plume with varying animation time. While the fluid motion of all four smoke
      plumes are alike each example has a unique look.

      * - .. figure:: /images/physics_fluid_type_domain_gas_noise_timeanim-0-1.png

             Animation Time: 0.1

        - .. figure:: /images/physics_fluid_type_domain_gas_noise_timeanim-1-0.png

             Animation Time: 1.0

      * - .. figure:: /images/physics_fluid_type_domain_gas_noise_timeanim-2-5.png

             Animation Time: 2.5

        - .. figure:: /images/physics_fluid_type_domain_gas_noise_timeanim-10-0.png

             Animation Time: 10.0

   .. note::

      *Resolution Divisions* and *Upres Factor* are not equivalent.
      By using different combinations of these resolution settings,
      you can obtain a variety of different styles of smoke.

   .. list-table:: Comparison of fire simulations with and without noise at the same grid
      resolution.

      * - .. figure:: /images/physics_fluid_type_domain_gas_noise_base-res-1.png

             Resolution Divisions: 200, without noise

        - .. figure:: /images/physics_fluid_type_domain_gas_noise_base-res-2.png

             Resolution Divisions: 100, Noise scale: 2.

   Low division simulations with lots of *Upres Factor* divisions generally appear smaller in
   real-world scale and can be used to achieve pyroclastic plumes such as in the following image:

   .. figure:: /images/physics_fluid_type_domain_gas_noise_note-resolution.jpg
      :align: center

.. _bpy.ops.fluid.bake_noise:
.. _bpy.ops.fluid.free_noise:

Bake Noise, Free Noise
   This option is only available when using the :ref:`Modular <bpy.types.FluidDomainSettings.cache_type>` cache type.

   The progress will be displayed in the status bar. Pressing :kbd:`Esc` will pause the simulation.

   Once the simulation has been baked, the cache can be deleted by pressing *Free Noise*.
   It is possible to pause or resume a *Bake Noise* process.


## Viewport Display


****************
Viewport Display
****************

.. _bpy.types.FluidDomainSettings.display_thickness:

Thickness
   Factor that scales the thickness of the grid that is currently being displayed.

.. _bpy.types.FluidDomainSettings.display_interpolation:

Interpolation
   Interpolation method to use for the visualization of the fluid grid.

   Linear
      Linear interpolation between voxels. Gives good smoothness and speed.

   Cubic
      Cubic interpolation between voxels. Gives smoothed high quality interpolation, but is slower.

   Closest
      No interpolation between voxels. Gives raw voxels.

.. _bpy.types.FluidDomainSettings.slice_per_voxel:

Slice per Voxel
   Determines how many slices per voxel should be generated.


.. _bpy.types.FluidDomainSettings.use_slice:

Slice
=====

Renders only a single 2D section of the domain object.

.. _bpy.types.FluidDomainSettings.slice_axis:

Axis
   Auto
      Adjust slice direction according to the view direction.

   X/Y/Z
      Slice along the X/Y/Z axis.

.. _bpy.types.FluidDomainSettings.slice_depth:

Position
   Position of the slice relative to the length of the respective domain side.

.. _bpy.types.FluidDomainSettings.show_gridlines:

Gridlines :guilabel:`Closest Interpolation Only`
   Display gridlines to differentiate the underlying cells in the current slice of the fluid domain.


.. _bpy.types.FluidDomainSettings.use_color_ramp:

Grid Display
============

Use a specific color map for the visualization of the simulation field.
This comes in handy during debugging or when making more advanced
adjustments to the simulation. For instance, if the actual color of
a fire simulation is barely visible in the viewport then changing
the color profile can help to see the real size of the flame.

.. _bpy.types.FluidDomainSettings.color_ramp_field:

Field
   The simulation field used in the display options (e.g. density, fuel, heat).

   .. list-table:: Comparison of a fire simulation with and without color mapping.

      * - .. figure:: /images/physics_fluid_type_domain_gas_viewport-display_colormapping-1.png

             Slice view of "fire" grid without color mapping.

        - .. figure:: /images/physics_fluid_type_domain_gas_viewport-display_colormapping-2.png

             Slice view of "fire" grid with color mapping.

.. _bpy.types.FluidDomainSettings.color_ramp_field_scale:

Scale
   Scale the selected simulation field by this value.


.. _bpy.types.FluidDomainSettings.show_velocity:

Vector Display
==============

Visualization options for the vector fields.

.. _bpy.types.FluidDomainSettings.vector_display_type:

Display As
   Streamlines
      Choose to display the vectors as "Streamlines".

   Needle
      Choose to display the vectors as "Needles".

   MAC Grid
      Choose to display the vector field as "Marker-And-Cell Grid".

      .. _bpy.types.FluidDomainSettings.vector_show_mac_x:
      .. _bpy.types.FluidDomainSettings.vector_show_mac_y:
      .. _bpy.types.FluidDomainSettings.vector_show_mac_z:

      X/Y/Z
         Show an individual X/Y/Z component of the MAC grid.

.. _bpy.types.FluidDomainSettings.vector_scale_with_magnitude:

Magnitude :guilabel:`Streamlines or Needle Only`
   Scale the display vectors by the magnitude of the vectors they represent.

.. _bpy.types.FluidDomainSettings.vector_field:

Field
   The vector field represented by the display vectors (e.g. fluid velocity, external forces).

.. _bpy.types.FluidDomainSettings.vector_scale:

Scale
   Scale the vectors by this size in the viewport.


Advanced :guilabel:`Gridlines Only`
===================================

Advanced coloring options for gridlines.

.. _bpy.types.FluidDomainSettings.gridlines_color_field:

Color Gridlines
   Flags
      Color gridlines with flags.

   Highlight Range :guilabel:`Grid Display Only`
      Highlight the cells with values of the displayed grid within the range.
      Values between the *Lower Bound* and *Upper Bound* (inclusive) are considered to be within the range.

      .. _bpy.types.FluidDomainSettings.gridlines_lower_bound:

      Lower Bound
         Lower bound of the highlighting range.

      .. _bpy.types.FluidDomainSettings.gridlines_upper_bound:

      Upper Bound
         Upper bound of the highlighting range.

      .. _bpy.types.FluidDomainSettings.gridlines_range_color:

      Color
         Color used to highlight the cells.

      .. _bpy.types.FluidDomainSettings.gridlines_cell_filter:

      Cell Type
         Choose to highlight only a particular type of cells.


## Diffusion

.. |m2.s-1| replace:: :math:`m^{2}/s`
.. |kg.m-3| replace:: :math:`kg/m^{3}`
.. |Pa.s| replace:: :math:`Pa\cdot s`

.. _bpy.ops.fluid.preset:
.. _bpy.types.FluidDomainSettings.use_diffusion:

*********
Diffusion
*********

.. reference::

   :Type:      Domain
   :Panel:     :menuselection:`Physics --> Fluid --> Diffusion`

Liquid diffusion defines the physical properties of a liquid
and in turn define how a liquid interacts with its environment.
The main factors of diffusion are the *Viscosity* and *Surface Tension*.
These properties can be adjusted to create virtual liquids that behave like water,
oil, honey, or any other liquid. A couple presets exist to change the diffusion
for different substances are predefined and can be changed in the preset menu.
Fluid Diffusion settings can be enabled/disabled in the panel header.

Viscosity
   The viscosity refers to the "thickness" of the fluid and actually the force needed to
   move an object of a certain surface area through it at a certain speed.

   For manual entry, please note that real-world viscosity
   (the so-called dynamic viscosity) is normally measured in Pascal-seconds (|Pa.s|),
   or in Poise units (P, equal to 0.1 |Pa.s|), and commonly centiPoise units (cP, equal to 0.001 |Pa.s|).

   Blender, on the other hand, uses the kinematic viscosity which is the dynamic viscosity divided by
   the density, :math:`\frac{Pa\cdot s}{kg/m^{3}}`, which is |m2.s-1|. So for example, the viscosity
   of water at room temperature is 1.002 cP, or 0.001002 |Pa.s|; the density of water is about
   1000 |kg.m-3|, which gives a kinematic viscosity of 0.000001002 |m2.s-1| --  so the entry would be
   1.002 times 10 to the minus six (1.002×10\ :sup:`-6` in scientific notation).

   The table below gives some examples of fluids together with their dynamic and kinematic viscosities.

   .. list-table:: Blender viscosity unit conversion.
      :header-rows: 1

      * - Fluid
        - Dynamic viscosity (in cP)
        - Kinematic viscosity (Blender, in |m2.s-1|)
      * - Water (20 °C)
        - 1.002×10\ :sup:`0` (1.002)
        - 1.002×10\ :sup:`-6` (0.000001002)
      * - Oil SAE 50
        - 5.0×10\ :sup:`2` (500)
        - 5.0×10\ :sup:`-5` (0.00005)
      * - Honey (20 °C)
        - 1.0×10\ :sup:`4` (10,000)
        - 2.0×10\ :sup:`-3` (0.002)
      * - Chocolate Syrup
        - 3.0×10\ :sup:`4` (30,000)
        - 3.0×10\ :sup:`-3` (0.003)
      * - Ketchup
        - 1.0×10\ :sup:`5` (100,000)
        - 1.0×10\ :sup:`-1` (0.1)
      * - Melting Glass
        - 1.0×10\ :sup:`15`
        - 1.0×10\ :sup:`0` (1.0)

   .. tip::

      You can find the kinematic viscosity of more materials in the proper units by
      asking Wolfram Alpha, e.g. `"kinematic viscosity of alcohol in m^2/s"
      <https://www.wolframalpha.com/input?i=kinematic+viscosity+of+alcohol+in+m%5E2%2Fs>`__.

   To simplify the input of these numbers, the viscosity is changed by entering values
   in scientific notation by entering a base value and the exponent of that number.

   .. _bpy.types.FluidDomainSettings.viscosity_base:

   Base
      The base of the viscosity value (e.g. 1.002 in the case of water (20 °C)).

   .. _bpy.types.FluidDomainSettings.viscosity_exponent:

   Exponent
      The exponent of the viscosity value that will be multiplied by 10\ :sup:`-1`
      (e.g. 6 in the case of water (20 °C)).

   .. note:: Viscosity Varies

      The default values in Blender are considered typical for those types of fluids and "look right" when animated.
      However, actual viscosity of some fluids,
      especially sugar-laden fluids like chocolate syrup and honey, depend highly on temperature and concentration.
      Oil viscosity varies by :abbr:`SAE (Society of Automobile Engineers)` rating.
      Glass at room temperature is basically a solid, but glass at 1500 °C flows (nearly) like water.

   .. warning::

      The simulator is not suitable for non-fluids, such as materials that do not "flow".
      Simply setting the viscosity to very large values will not result in rigid body behavior,
      but might cause instabilities.

.. _bpy.types.FluidDomainSettings.surface_tension:

Surface Tension
   Surface tension in grid units. Higher value will produce liquids with greater surface tension.


.. _bpy.types.FluidDomainSettings.use_viscosity:

High Viscosity Solver
=====================

The high viscosity liquid solver can be used to simulate fluids with increased viscosity,
replicating the behavior of substances like honey or molasses.
This specialized solver enhances the accuracy of slow-moving and thick liquid simulations.

.. _bpy.types.FluidDomainSettings.viscosity_value:

Strength
   The viscosity of the liquid. Higher values result in more viscous fluids.

   .. note::

      A strength value of 0 will still apply some viscosity.
      Uncheck the *High Viscosity Solver* to disable the high viscosity liquid solver simulation step completely.

   .. list-table:: Rotating liquid inflow with varying viscosities.

      * - .. figure:: /images/physics_fluid_type_domain_liquid_viscosity_0-2.png

             Strength of 0.2 (at frame 65).

        - .. figure:: /images/physics_fluid_type_domain_liquid_viscosity_0-4.png

             Strength of 0.4 (at frame 200).


## Index


###################
  Liquid Settings
###################

.. toctree::
   :maxdepth: 2

   diffusion.rst
   particles.rst
   mesh.rst


## Mesh

.. _bpy.types.FluidDomainSettings.use_mesh:

****
Mesh
****

The liquid mesh is, besides the liquid particles, another way to visualize the liquid simulation.
It is generated directly from the liquid particles and often uses a higher resolution than
the base :ref:`Resolution Divisions <bpy.types.FluidDomainSettings.resolution_max>`.

Besides enabling parts of the interface, checking *Mesh* lets the cache know
which simulation data to read. If, for example, *Mesh* is enabled but
there is no mesh simulation data to read it will show the original domain.
The checkbox does not reset the cache and can be used to switch the view between
the original domain and the baked liquid mesh.

It is important to keep in mind that the shape of the mesh depends on a combination of *all* these
parameters. E.g. changing the :ref:`Particle Radius <bpy.types.FluidDomainSettings.resolution_max>`
will lead to a different interpretation of the concavity values.

.. _bpy.types.FluidDomainSettings.mesh_scale:

Upres Factor
   Factor by which to enhance the resolution of the mesh. The scaling factor is coupled to
   the :ref:`Resolution Divisions <bpy.types.FluidDomainSettings.resolution_max>`
   (i.e. the mesh is this times bigger than the base simulation).

.. _bpy.types.FluidDomainSettings.mesh_particle_radius:

Particle Radius
   The radius of one liquid particle in grid cells units. This value describes how much area is covered
   by a particle and thus determines how much area around it can be considered as liquid.
   A greater radius will let particles cover more area. This will result in meshes covering more
   volume around liquid particles.

   This property refers to the same :ref:`Particle Radius <bpy.types.FluidDomainSettings.particle_radius>`
   described in the liquid domain settings. Yet for the mesh, it is useful to interpret
   the particle radius on its own. For one, the mesh can have a resolution different from the base
   resolution through the :ref:`Upres Factor <bpy.types.FluidDomainSettings.mesh_scale>`. For another,
   it is often desirable to be able to control the mesh size around a single liquid particle.

.. _bpy.types.FluidDomainSettings.use_speed_vectors:

Use Speed Vectors
   Creates a ``velocity`` :doc:`Attribute </modeling/geometry_nodes/attributes_reference>`
   which records the velocity of each vertex per frame.
   These will be used (automatically) when rendering with motion blur enabled.

   .. note::

      In order to render motion blur with Cycles,
      :ref:`Deformation Motion Blur <bpy.types.CyclesObjectSettings.use_deform_motion>`
      must be enabled.

   .. list-table:: Comparison of a liquid splash with and without motion blur (rendered with Cycles).

      * - .. figure:: /images/physics_fluid_type_domain_liquid_mesh_motionblur-on.png

             Motion blur enabled.

        - .. figure:: /images/physics_fluid_type_domain_liquid_mesh_motionblur-off.png

             Motion blur disabled.

.. _bpy.types.FluidDomainSettings.mesh_generator:

Mesh Generator
   The mesh generator method determines the accuracy of the mesh. The *Final* option produces a higher
   quality mesh and provides more configuration option than the *Preview* option which in turn is
   faster but not as smooth.

.. _bpy.types.FluidDomainSettings.mesh_smoothen_pos:

Smoothing Positive
   Positive mesh smoothing iterations. Higher values will make the mesh outline increasingly smooth.
   Yet higher values can prevent small details (e.g. smaller liquid drops) from getting meshed.

.. _bpy.types.FluidDomainSettings.mesh_smoothen_neg:

Smoothing Negative
   Negative mesh smoothing iterations. Higher values will make the mesh outline sharper.
   High values will preserve details, however, the mesh outline will become more ragged
   (e.g. a single mesh particle will become less rounded and have more flat sides).

   .. figure:: /images/physics_fluid_type_domain_liquid_mesh_smoothing-comparison.png
      :align: center

      Comparison of a liquid drop hitting a surface (viewed from top) with varying smoothing values.
      Left: 1, 1 (Smoothing Positive, Smoothing Negative). Middle: 10, 1. Right: 1, 10.
      Note the slightly sharper corners in the right splash (compared to the left one).

.. _bpy.types.FluidDomainSettings.mesh_concave_upper:

Concavity Upper
   Upper mesh concavity bound. High values tend to smoothen and fill out concave regions.

.. _bpy.types.FluidDomainSettings.mesh_concave_lower:

Concavity Lower
   Lower mesh concavity bound. High values tend to smoothen and fill out concave regions.

   Using a lower concavity which is greater the upper concavity can result in distorted, non-manifold meshes.
   Unless the artist sees value in this kind of mesh, such concavity value combinations should be avoided.

   .. list-table:: Crown splash with varying upper and lower concavity settings. Note that setting
      the concavity values to the same value produces a very granular mesh.

      * - .. figure:: /images/physics_fluid_type_domain_liquid_mesh_concavity-01.png

             Upper: 1.0, Lower: 0.0.

        - .. figure:: /images/physics_fluid_type_domain_liquid_mesh_concavity-02.png

             Upper: 1.0, Lower: 0.5.

        - .. figure:: /images/physics_fluid_type_domain_liquid_mesh_concavity-03.png

             Upper: 1.0, Lower: 1.0.

      * - .. figure:: /images/physics_fluid_type_domain_liquid_mesh_concavity-04.png

             Upper: 1.5, Lower: 0.0.

        - .. figure:: /images/physics_fluid_type_domain_liquid_mesh_concavity-05.png

             Upper: 1.5, Lower: 0.5.

        - .. figure:: /images/physics_fluid_type_domain_liquid_mesh_concavity-06.png

             Upper: 1.5, Lower: 1.0.

      * - .. figure:: /images/physics_fluid_type_domain_liquid_mesh_concavity-07.png

             Upper: 2.0, Lower: 0.0.

        - .. figure:: /images/physics_fluid_type_domain_liquid_mesh_concavity-08.png

             Upper: 2.0, Lower: 0.5.

        - .. figure:: /images/physics_fluid_type_domain_liquid_mesh_concavity-09.png

             Upper: 2.0, Lower: 1.0.

.. _bpy.ops.fluid.bake_mesh:
.. _bpy.ops.fluid.free_mesh:

Bake Mesh, Free Mesh
   This option is only available when using the :ref:`Modular <bpy.types.FluidDomainSettings.cache_type>`
   cache type.

   The progress will be displayed in the status bar. Pressing :kbd:`Esc` will abort the simulation.

   Once the simulation has been baked, the cache can be deleted by pressing *Free Mesh*.
   It is possible to pause or resume a *Bake Mesh* process.


## Particles


*********
Particles
*********

.. _bpy.types.FluidDomainSettings.use_spray_particles:

Spray
   Create spray particles during the secondary particle simulation. Spray particles are those that
   appear to fly through the air above the liquid surface when there is a bigger splash.

.. _bpy.types.FluidDomainSettings.use_foam_particles:

Foam
   Create foam particles during the secondary particle simulation. Foam particles are those that
   solely move on the liquid surface.

.. _bpy.types.FluidDomainSettings.use_bubble_particles:

Bubbles
   Create bubble particles during the secondary particle simulation. Bubble particles are those that
   move below the liquid surface.

.. note::

   Enabling a secondary particle type will also create a particle system for that type of particles.
   Disabling a particle type will delete this particle system including its settings.

.. _bpy.types.FluidDomainSettings.sndparticle_combined_export:

Combined Export
   Select particle types that should go into the same particle system. This option has no effect
   on the outcome of the simulation. It only changes the way particle systems are allocated in
   the particle settings.

.. _bpy.types.FluidDomainSettings.particle_scale:

Upres Factor
   Factor by which to enhance the resolution of the particle simulation. The scaling factor is coupled
   to the :ref:`Resolution Divisions <bpy.types.FluidDomainSettings.resolution_max>` (i.e. the particle
   simulation is this times bigger than the base simulation).

.. _bpy.types.FluidDomainSettings.sndparticle_potential_max_wavecrest:

Wave Crest Potential Maximum
   Upper clamping threshold for marking fluid cells as wave crests. A higher value results in less
   marked cells.

.. _bpy.types.FluidDomainSettings.sndparticle_potential_min_wavecrest:

Wave Crest Potential Minimum
   Lower clamping threshold for marking fluid cells as wave crests. A lower value results in more
   marked cells.

.. _bpy.types.FluidDomainSettings.sndparticle_potential_max_trappedair:

Trapped Air Potential Maximum
   Upper clamping threshold for marking fluid cells where air is trapped.
   A higher value results in less marked cells.

.. _bpy.types.FluidDomainSettings.sndparticle_potential_min_trappedair:

Trapped Air Potential Minimum
   Lower clamping threshold for marking fluid cells where air is trapped.
   A lower value results in more marked cells.

.. _bpy.types.FluidDomainSettings.sndparticle_potential_max_energy:

Kinetic Energy Potential Maximum
   Upper clamping threshold that indicates the fluid speed where cells start to emit particles.
   A higher value results in generally less particles.

.. _bpy.types.FluidDomainSettings.sndparticle_potential_min_energy:

Kinetic Energy Potential Minimum
   Lower clamping threshold that indicates the fluid speed where cells start to emit particles.
   A lower value results in generally more particles.

.. _bpy.types.FluidDomainSettings.sndparticle_potential_radius:

Potential Radius
   Radius to compute potential for each cell. Higher values are slower but create smoother potential grids.

.. _bpy.types.FluidDomainSettings.sndparticle_update_radius:

Particle Update Radius
   Radius to compute position update for each particle.
   Higher values are slower but particles move less chaotic.

.. _bpy.types.FluidDomainSettings.sndparticle_sampling_wavecrest:

Wave Crest Particle Sampling
   Maximum number of particles generated per wave crest cell per frame.

.. _bpy.types.FluidDomainSettings.sndparticle_sampling_trappedair:

Trapper Air Particle Sampling
   Maximum number of particles generated per trapped air cell per frame.

.. _bpy.types.FluidDomainSettings.sndparticle_life_max:

Particle Life Maximum
   Highest possible particle lifetime.

.. _bpy.types.FluidDomainSettings.sndparticle_life_min:

Particle Life Minimum
   Lowest possible particle lifetime.

.. _bpy.types.FluidDomainSettings.sndparticle_bubble_buoyancy:

Bubble Buoyancy
   Amount of buoyancy force that rises bubbles. A high value results in bubble movement mainly upwards.

.. _bpy.types.FluidDomainSettings.sndparticle_bubble_drag:

Bubble Drag
   Amount of drag force that moves bubbles along with the fluid. A high value results in bubble movement
   mainly along with the fluid.

.. _bpy.types.FluidDomainSettings.sndparticle_boundary:

Particles in Boundary
   Delete
      Delete secondary particles that are inside obstacles or left the domain.

   Push Out
      Push secondary particles that left the domain back into the domain.

.. _bpy.ops.fluid.bake_particles:
.. _bpy.ops.fluid.free_particles:

Bake Particles, Free Particles
   This option is only available when using the :ref:`Modular <bpy.types.FluidDomainSettings.cache_type>` cache type.

   The progress will be displayed in the status bar. Pressing :kbd:`Esc` will pause the simulation.

   Once the simulation has been baked, the cache can be deleted by pressing *Free Particles*.
   It is possible to pause or resume a *Bake Particles* process.


## Gravity

.. _bpy.types.Scene.gravity:

*******
Gravity
*******

.. reference::

   :Panel:     :menuselection:`Scene --> Gravity`

Gravity is a global setting that is applied to all physics systems in a scene.
It can be found in the scene tab.
This value is generally fine left at its default, -9.810 on the Z axis,
which is the force of gravity in the real world.
Changing this value would simulate a lower or higher force of gravity.
Gravity denoted g, measurement *m* × *s*\ :sup:`-2`.

Gravity is applied in the same way to all physics systems.

Gravity is practically the same around the entirety of planet *Earth*.
For rendering scenes on The Moon, use -1.622 *m* × *s*\ :sup:`-2` on the Z axis.
Another popular gravity value might be for Mars which
has a gravitation acceleration of -3.69 *m* × *s*\ :sup:`-2` on the Z Axis.

.. note::

   The gravity value per physics system can be scaled down in the *Field Weights* tab.


## Index

.. _physics-forces-index:

##########
  Forces
##########

.. toctree::
   :maxdepth: 2

   gravity.rst
   force_fields/index.rst


## Index

.. _physics-force-fields-index:
.. _bpy.types.FieldSettings:

################
  Force Fields
################

.. toctree::
   :maxdepth: 2

   introduction.rst


Types
=====

.. toctree::
   :maxdepth: 1

   types/boid.rst
   types/charge.rst
   types/curve_guide.rst
   types/drag.rst
   types/fluid_flow.rst
   types/force.rst
   types/harmonic.rst
   types/lennard_jones.rst
   types/magnetic.rst
   types/texture.rst
   types/turbulence.rst
   types/vortex.rst
   types/wind.rst


## Introduction

.. index:: Force Fields

************
Introduction
************

Force fields offer a way to influence a simulation, in example to add extra movement.
:doc:`Particles </physics/particles/index>`, :doc:`Soft Bodies </physics/soft_body/index>`,
:doc:`Rigid Bodies </physics/rigid_body/index>`, and :doc:`Cloth objects </physics/cloth/index>`
can all be affected by forces fields.
Force fields automatically affect everything.
To remove a simulation or particle system from their influence,
simply turn down the influence of that type of force field in its Field Weights panel.

- All types of objects and particles can generate fields,
  but only curve object can bear a :doc:`/physics/forces/force_fields/types/curve_guide` field.
- Force fields can also be generated from particles.
  See :doc:`Particle Physics </physics/particles/emitter/physics/index>`.
- The objects need to share at least one common layer to have an effect.

You may limit the effect on particles to a group of objects
(see the :doc:`Particle Physics </physics/particles/emitter/physics/index>` page).


Creating a Force Field
======================

.. reference::

   :Mode:      Object Mode
   :Menu:      :menuselection:`Add --> Force Field`
   :Panel:     :menuselection:`Physics --> Force Field`

To create a single force field,
you can select :menuselection:`Add --> Force Field` and select the desired force field.
This method creates an empty with the force field attached.

.. list-table:: Examples of an empty with the force field attached.

   * - .. figure:: /images/physics_forces_force-fields_types_vortex_visualzation.png

          Vortex force field.

     - .. figure:: /images/physics_forces_force-fields_types_wind_visualzation.png

          Wind force field.

     - .. figure:: /images/physics_forces_force-fields_types_force_visualzation.png

          Force force field.

To create a field from an existing object you have to select the object and
change to the *Physics* tab. Select the field type in the *Fields* menu.

.. note::

   After changing the fields *Fields* panel or deflection *Collision* panel settings,
   you have to recalculate the particle, soft body or cloth system by *Free Cache*,
   this is not done automatically.

   Particles react to all kinds of force fields,
   soft bodies only to *Force*, *Wind*, *Vortex*
   (they react on *Harmonic* fields but not in a useful way).


.. _force-field-common-settings:

Common Field Settings
=====================

Most fields have the same settings, even though they act very differently.
Settings unique to a field type are described below.
Curve Guide and Texture fields have very different options.

.. _bpy.types.FieldSettings.shape:

Shape
   Sets the direction which is used to calculate the effector force.
   For force fields from an empty object only *Point*, *Line* and *Plane* shapes are available,
   as for a field from a 3D object there are additional *Surface* and *Every Point* options,
   and *Curve* for a field from a curve.

   :Point: Point with omni-directional influence. Uses the object origin as the effector point.
   :Line:
      The force only acts in the local XY plane, using the Z axis line as the effector.
   :Plane:
      The force only acts in the local Z direction, using the XY axis plane as the effector.
   :Surface:
      The force field acts on a 3D object's surface.
      In this case, the Z axis is the surface normal.
   :Every Point: Uses every vertex in the mesh object as an effector point.

.. _bpy.types.FieldSettings.strength:

Strength
   The strength of the field effect.
   This can be positive or negative to change the direction that the force operates in.
   A force field's strength is scaled with the force object's scale,
   allowing you to scale up and down the scene, keeping the same effects.

.. _bpy.types.FieldSettings.flow:

Flow
   If nonzero, this adds a drag force proportional and opposite to the point velocity.

   This effectively re-interprets the force field so that the *Strength* to *Flow* ratio
   at a certain point defines the velocity of an "air flow" field, and objects are
   encouraged to follow the flow by the resistance caused by the *Flow* drag force.

.. _bpy.types.FieldSettings.apply_to_location:
.. _bpy.types.FieldSettings.apply_to_rotation:

Affect
   Location
      Influence the location of particles and other physics entities.
   Rotation
      Influence the rotation of particles with :doc:`Dynamic Rotation </physics/particles/emitter/rotation>`.
      The option is not relevant for other types of physics systems.

   Disabling both options completely deactivates the force field.

.. _bpy.types.FieldSettings.noise:

Noise Amount
   Adds noise to the strength of the force.

.. _bpy.types.FieldSettings.seed:

Seed
   Changes the seed of the random noise.

.. _bpy.types.FieldSettings.use_absorption:

Absorption
   Force gets absorbed by collision objects.

.. _bpy.types.FieldSettings.wind_factor:

Wind Factor
   Specifies how much the force is reduced when acting parallel to a surface, e.g. cloth.
   If set to 1, only the normal component of the force is taken into account.


Falloff
-------

Here you can specify the shape of the force field
(if the falloff *Power* is greater than 0).

.. _bpy.types.FieldSettings.falloff_type:

Shape
   :Cone:
      The falloff results in a cone-shaped force field. Additional options are the same as those of *Tube* options.
   :Sphere:
      The falloff is uniform in all directions, as in a sphere.
   :Tube:
      The falloff results in a tube-shaped force field.
      The field's *Radial Power* can be adjusted,
      as well as the *Minimum* and *Maximum* distances of the field.

.. _bpy.types.FieldSettings.z_direction:

Z Direction
   The direction the force affects on the Z axis.

   :+Z: The force only has an affect on the positive Z axis.
   :-Z: The force only has an affect on the negative Z axis.
   :Both Z: The force has an affect on the positive and negative Z axis.

.. _bpy.types.FieldSettings.falloff_power:

Power
   How the power of the force field changes with the distance from the force field.
   If *r* is the distance from the origin of the object, the force changes with 1/(*r* - *min* + 1)\ :sup:`power`.
   A falloff of 2 changes the force field with 1/(*r* - *min* + 1)\ :sup:`2`,
   which is similar to the falloff of gravitational pull.

.. _bpy.types.FieldSettings.use_min_distance:
.. _bpy.types.FieldSettings.distance_min:

Min Distance
   The distance from the object's origin, up to where the force field is effective with full strength.
   If you have a falloff of 0, this parameter will have no effect,
   because the field is effective with full strength up to *Max Distance* (or infinite).
   Shown by an additional circle around the object.

.. _bpy.types.FieldSettings.use_max_distance:
.. _bpy.types.FieldSettings.distance_max:

Max Distance
   Specifies the maximum radius in which the force field affects other objects
   (shown by an additional circle around the object).


## Boid

.. index:: Force Fields; Boid

****
Boid
****

.. reference::

   :Panel:     :menuselection:`Physics --> Force Fields`
   :Type:      Boid

The *Boid* force fields do not affect physics,
and are used together with the :doc:`Boids Particles </physics/particles/emitter/physics/boids>`
to define boid predators and goals for the *Boid Brain* rules.

.. TODO2.8:
   .. figure:: /images/physics_forces_force-fields_types_boid_panel.png

      UI for a Boid force field.


## Charge

.. index:: Force Fields; Charge

******
Charge
******

.. reference::

   :Panel:     :menuselection:`Physics --> Force Fields`
   :Type:      Charge

A *Charge* force field is similar to a *Force* field except it changes it's behavior (attract/repulse)
based on the effected particles charge field (negative/positive),
like real particles with a charge.
Which means that this field has only an effect on particles that have also a *Charge* field
(else, they have no "charge", and hence are unaffected)!

.. TODO2.8:
   .. figure:: /images/physics_forces_force-fields_types_charge_panel.png

      UI for a Charge force field.


Example
=======

.. peertube:: c675e272-4972-4b6c-8e6b-d997d64434ae


## Curve Guide

.. index:: Force Fields; Curve Guide

***********
Curve Guide
***********

.. reference::

   :Panel:     :menuselection:`Physics --> Force Fields`
   :Type:      Curve Guide

The *Curve Guide* is used to force particles to follow a certain
path defined by a :doc:`Curve Object </modeling/curves/index>`.
A typical scenario would be to move a red blood cell inside a vein,
or to animate the particle flow in a motor.
You can also use *Curve Guide* to shape certain hair strands.

.. note::

   You can also use the :doc:`Particle Edit Mode </physics/particles/mode>` to define a path.

Since you can animate curves as a soft body or any other usual way,
you may build very complex animations while keeping great control and keeping the simulation time to a minimum.

To make particles point in the direction of the curve, you need to set their *Orientation Axis*
to *Velocity / Hair*, enable *Dynamic*, and set their *Angular Velocity Axis* to *Velocity*,
all in the the :doc:`/physics/particles/emitter/rotation` settings of the particle system.
The :doc:`/animation/constraints/relationship/follow_path` and the curve's legacy
:ref:`Follow <bpy.types.Curve.use_path_follow>` option won't work for this.

A *Curve Guide* force affects all particles on the same layer, independently from their distance to the curve.
If you have several guides in a layer,
their fields add up to each other (the way you may have learned it in your physics course).
But you can limit their influence radius by changing the *Minimum Distance* (see below).

A particle follows a *Curve Guide* during its lifetime,
the velocity depends on its lifetime and the length of the path.

.. note::

   The Curve Guide does not affect :doc:`soft bodies </physics/soft_body/index>`.


Options
=======

.. TODO2.8:
   .. figure:: /images/physics_forces_force-fields_types_curve-guide_panel.png

      UI for a Curve Guide force field.

.. _bpy.types.FieldSettings.guide_free:

Free
   Fraction of particle life time, that is not used for the curve.

Falloff Power
   This setting governs the strength of the guide between *Min Distance* and *Max Distance*.
   A falloff of 1 means a linear progression.

.. _bpy.types.FieldSettings.use_guide_path_add:

Additive
   If you use *Additive*, the speed of the particles is also evaluated depending on the falloff.

.. _bpy.types.FieldSettings.use_guide_path_weight:

Weights
   Use Curve weights to influence the particle influence along the curve.

.. _bpy.types.FieldSettings.guide_clump_amount:

Clumping Amount
   The particles come together at the end of the curve (1) or they drift apart (-1).

.. _bpy.types.FieldSettings.guide_clump_shape:

Shape
   Defines the form in which the particles come together.
   +0.99: the particles meet at the end of the curve.
   0: linear progression along the curve. -0.99: the particles meet at the beginning of the curve.

.. _bpy.types.FieldSettings.guide_minimum:

Min Distance
   The distance from the curve, up to where the force field is effective with full strength.
   If you have a falloff of 0, this parameter will have no effect,
   because the field is effective with full strength up to *Max Distance* (or the infinity).
   *Min Distance* is shown with a circle at the endpoints of the curve in the 3D Viewport.

Max Distance
   The maximum influence radius. Shown by an additional circle around the curve object.


Kink
----

.. warning::

   This feature is broken in the current version, see Bug Report #46776.

.. _bpy.types.FieldSettings.guide_kink_type:

Type
   Changes the shape that the particles can take.

   :None: Todo.
   :Braid: Braid.
   :Curl: The radius of the influence depends on the distance of the curve to the emitter.
   :Radial: A three-dimensional, standing wave.
   :Roll: A one-dimensional, standing wave.
   :Rotation: Todo.
   :Wave: A two-dimensional, standing wave.

   It is not so easy to describe the resulting shapes, so have a look at the example below.

   .. figure:: /images/physics_forces_force-fields_types_curve-guide_kink.jpg
      :width: 400px

      Kink options of a curve guide. From left to right: Radial, Wave, Braid, Roll.
      `Animation <https://vimeo.com/1866538>`__.

.. _bpy.types.FieldSettings.guide_kink_axis:

Axis
   Which axis to use for the offset.

.. _bpy.types.FieldSettings.guide_kink_frequency:

Frequency
   The frequency of the offset.

.. _bpy.types.FieldSettings.guide_kink_shape:

Shape
   Adjust the offset to the beginning/end.

.. _bpy.types.FieldSettings.guide_kink_amplitude:

Amplitude
   The Amplitude of the offset.


Examples
========

.. peertube:: 9d3c912f-041d-480a-a357-c906042aa0eb

.. figure:: /images/physics_forces_force-fields_types_curve-guide_example.png
   :align: center
   :width: 560px

   Curve Guide force field.


## Drag

.. index:: Force Fields; Drag

****
Drag
****

.. reference::

   :Panel:     :menuselection:`Physics --> Force Fields`
   :Type:      Drag

A *Drag* force field resists particle motion by slowing it down.


Options
=======

.. TODO2.8
   .. figure:: /images/physics_forces_force-fields_types_drag_panel.png

      UI for a Drag force field.

Linear
   Drag component proportional to velocity.
Quadratic
   Drag component proportional to the square of the velocity.


## Fluid Flow

.. index:: Force Fields; Fluid Force

**********
Fluid Flow
**********

.. reference::

   :Panel:     :menuselection:`Physics --> Force Fields`
   :Type:      Fluid Flow

The *Fluid Flow* force field creates a force based on a :doc:`Fluid simulation </physics/fluid/index>` air flow.
It applies the smoke simulation air flow velocity as a force to other simulations that use force fields.
To use it you need to add a *Fluid Flow* force field and select a domain object for it.
For example fire sparkles can realistically flow along the air turbulence near the simulated fire.


Options
=======

.. TODO2.8:
   .. figure:: /images/physics_forces_force-fields_types_fluid-flow_panel.png

      UI for a Fluid Flow force field.

Domain Object
   An object that is used as a domain for the smoke simulation.
Apply Density
   Adjust the force strength based on the smoke density.


## Force

.. index:: Force Fields; Force

*****
Force
*****

.. reference::

   :Panel:     :menuselection:`Physics --> Force Fields`
   :Type:      Force

.. figure:: /images/physics_forces_force-fields_types_force_visualzation.png

   Force force field visualization.

The *Force* field is the simplest of the fields. It gives a constant force towards
(positive strength) or away from (negative strength) the object's origin.
Newtonian particles are attracted to a field with negative strength,
and are blown away from a field with positive strength.

.. TODO2.8:
   .. figure:: /images/physics_forces_force-fields_types_force_panel.png

      UI for a Force force field.


Example
=======

.. peertube:: ea6ce3d3-b1da-4173-904f-6c4c0273eac4


## Harmonic

.. index:: Force Fields; Harmonic

********
Harmonic
********

.. reference::

   :Panel:     :menuselection:`Physics --> Force Fields`
   :Type:      Harmonic

In a *Harmonic* force field,
the source of the force field is the zero point of a harmonic oscillator (spring, pendulum).
If you set the *Damping* parameter to 1,
the movement is stopped in the moment the object is reached.
This force field is really special if you assign it to particles.


Options
=======

.. TODO2.8:
   .. figure:: /images/physics_forces_force-fields_types_harmonic_panel.png

      UI for a Harmonic force field.

Rest Length
   Controls the rest length of the harmonic force.
Multiple Springs
   Causes every point to be affected by multiple springs.

Normally every particle of the field system influences every particle of the target system.
Not with *Harmonic*! Here every target particle is assigned to a field particle.
So particles will move to the place of other particles, thus forming shapes.


Example
=======

.. peertube:: 4309e609-f7cb-4872-8614-10f686486920


## Lennard Jones

.. index:: Force Fields; Lennard-Jones

*************
Lennard-Jones
*************

.. reference::

   :Panel:     :menuselection:`Physics --> Force Fields`
   :Type:      Lennard-Jones

The *Lennard-Jones* force field is a very short range force with a behavior determined by the sizes of the effector
and effected particle. At a distance smaller than the combined sizes, the field is very
repulsive and after that distance it is attractive.
It tries to keep the particles at an equilibrium distance from each other.
Particles need to be at a close proximity to each other to be effected by this field at all.

Particles can have for example both a charge and a Lennard-Jones potential,
which is probably something for the nuclear physicists among us.

.. TODO2.8:
   .. figure:: /images/physics_forces_force-fields_types_lennard-jones_panel.png

      UI for a Lennard-Jones force field.


Example
=======

.. peertube:: 4c067375-ec7c-45dc-9d9d-e661634eedf8


## Magnetic

.. index:: Force Fields; Magnetic

********
Magnetic
********

.. reference::

   :Panel:     :menuselection:`Physics --> Force Fields`
   :Type:      Magnetic

This field depends on the speed of the particles.
It simulates the force of magnetism on magnetized objects.

.. TODO2.8:
   .. figure:: /images/physics_forces_force-fields_types_magnetic_panel.png

      UI for a Magnetic force field.


Example
=======

.. peertube:: a3e8b059-f09b-4fca-9901-f6f73eba6fb1


## Texture

.. index:: Force Fields; Texture

*******
Texture
*******

.. reference::

   :Panel:     :menuselection:`Physics --> Force Fields`
   :Type:      Texture

You can use a *Texture* force field to create an arbitrarily complicated force field,
which force in the three directions is color coded. Red is coding for the X axis,
green for the Y axis and blue for the Z axis
(like the color of the coordinate axes in the 3D Viewport). A value of 0.5 means no force,
a value larger than 0.5 acceleration in negative axis direction (like -Z),
a value smaller than 0.5 acceleration in positive axis direction (like +Z).


Options
=======

.. TODO2.8:
   .. figure:: /images/physics_forces_force-fields_types_texture_panel.png

      UI for a Texture force field.

Texture Mode
   This sets the way a force vector is derived from the texture.

   :Curl:
      Calculates the force vector from the curl of the 3D-RGB texture (rotation of RGB vectors).
      This also works only with a color texture. It can be used for example to create a nice looking
      turbulence force with a color clouds texture with Perlin noise.
   :Gradient:
      Calculates the force vector as the 3D gradient of the intensity (grayscale) of the texture.
      The gradient vector always points to the direction of increasing brightness.
   :RGB:
      Uses the color components directly as the force vector components in the color encoded directions.
      You need an RGB texture for this, e.g. an image or a color ramp.
      So a *Blend* texture without a color ramp would not suffice.

Nabla
   It is the offset used to calculate the partial derivatives needed
   for *Gradient* and *Curl* texture modes.

Use Coordinates
   Uses the emitter object coordinates (and rotation & scale) as the texture space the particles use.
   Allows for moving force fields, that have their coordinates bound to the location coordinates of an object.

Root Texture Coordinates
   This is useful for hair as it uses the texture force calculated for
   the particle root position for all parts of the hair strand.

2D
   Disregards the particles Z coordinate and only uses particles X & Y as the texture coordinates.

Remember that only procedural texture are truly 3D.


Examples
========

- A single colored texture (0.5, 0.0, 0.5) creates a force in the direction of the positive Y axis,
  e.g. hair is orientated to the Y axis.
- A blend texture with color ramp can be used to created a force "plane". E.g. on the left side (0.5, 0.5, 0.5),
  on the right side (1.0, 0.5, 0.5) you have a force plane perpendicular to XY (i.e. parallel to Z).
  If you use an object for the coordinates, you can use the object to push particles around.
- An animated wood texture can be used to create a wave like motion.

.. peertube:: 5e17a045-6f20-4fef-b63d-37ab9f79547b


## Turbulence

.. index:: Force Fields; Turbulence

**********
Turbulence
**********

.. reference::

   :Panel:     :menuselection:`Physics --> Force Fields`
   :Type:      Turbulence

A *Turbulence* force field creates a random & chaotic 3D noise effect,
similar to jets of water or geysers under the ocean.


Options
=======

.. TODO2.8:
   .. figure:: /images/physics_forces_force-fields_types_turbulence_panel.png

      UI for a Turbulence force field.

.. _bpy.types.FieldSettings.size:

Size
   Indicates the scale of the noise.
Global
   Makes the size and strength of the noise relative to the world, instead of the object it is attached to.


Example
=======

.. figure:: /images/physics_forces_force-fields_types_turbulence_example.png

   Turbulence force field affecting a particle system.


## Vortex

.. index:: Force Fields; Vortex

******
Vortex
******

.. reference::

   :Panel:     :menuselection:`Physics --> Force Fields`
   :Type:      Vortex

.. figure:: /images/physics_forces_force-fields_types_vortex_visualzation.png

   Vortex force field visualization.

The *Vortex* force field gives a spiraling force that twists the direction of points around the force
object's local Z axis. This can be useful for making a swirling sink, or tornado,
or kinks in particle hair.


Options
=======

.. TODO2.8:
   .. figure:: /images/physics_forces_force-fields_types_vortex_panel.png

      UI for a Vortex force field.

Inflow
   Inwards component of the vortex force.


Example
=======

.. peertube:: bb03c2b0-58bc-4b25-bb65-70d59d6afa8e


## Wind

.. index:: Force Fields; Wind

****
Wind
****

.. reference::

   :Panel:     :menuselection:`Physics --> Force Fields`
   :Type:      Wind

.. figure:: /images/physics_forces_force-fields_types_wind_visualzation.png

   Wind force field visualization.

The *Wind* force field gives a constant force in a single direction, along the force object's local Z axis.
The strength of the force is visualized by the spacing of the circles shown.

.. TODO2.8:
   .. figure:: /images/physics_forces_force-fields_types_wind_panel.png

      UI for a Wind force field.


Example
=======

.. peertube:: 8963507e-cf97-4dec-9d27-276126023a87


## Index

.. _bpy.types.ParticleSystemModifier:
.. _bpy.types.Particle:
.. _bpy.types.ParticleSystem:
.. _bpy.types.ParticleSettings:
.. _bpy.ops.particle:
.. _particles-index:

###################
  Particle System
###################

.. toctree::
   :maxdepth: 2

   introduction.rst
   particle_system_panel.rst
   emitter/index.rst
   hair/index.rst
   texture_influence.rst
   mode.rst


## Introduction


************
Introduction
************

Particles are lots of items emitted from mesh objects, typically in the thousands.
Each particle can be a point of light or a mesh, and be joined or dynamic.
They may react to many different influences and forces, and have the notion of a lifespan.
Dynamic particles can represent fire, smoke, mist,
and other things such as dust or magic spells.

:doc:`Hair </physics/particles/hair/index>` type particles are a subset of regular particles.
Hair systems form curves that can represent hair, fur, grass and bristles.

You see particles as a Particle Modifier,
but all settings are done in the *Particle tab*.

.. figure:: /images/physics_particles_introduction_fur-example.jpg
   :width: 300px

   Some fur made from particles.

Particles generally flow out from their mesh into space.
Their movement can be affected by many things, including:

- Initial velocity out from the mesh.
- Movement of the emitter (vertex, face or object) itself.
- Movement according to "gravity" or "air resistance".
- Influence of force fields like wind, vortexes or guided along a curve.
- Interaction with other objects like collisions.
- Partially intelligent members of a flock (herd, school, ...),
  that react to other members of their flock, while trying to reach a target or avoid predators.
- Smooth motion with soft body physics (only *Hair* particle systems).
- Or even manual transformation with :doc:`Lattices </modeling/modifiers/deform/lattice>`.

Particles may be rendered as:

- :ref:`Halos <particle-halo>` (for Flames, Smoke, Clouds).
- Meshes which in turn may be animated (e.g. fish, bees, ...).
  In these cases, each particle "carries" another object.
- :doc:`Hair curves </physics/particles/hair/shape>`, following the path of the particle.
  These hair curves can be manipulated in the 3D Viewport (combing, adding, cutting, moving, etc.).

Every object may carry many particle systems. Each particle system may contain up to
10,000,000 particles. Certain particle types (*Hair* and *Keyed*)
may have up to 10,000 children for each particle
(children move and emit more or less like their respective parents).
The size of your memory and your patience are your practical boundaries.


## Mode

.. _bpy.types.ParticleEdit:

******************
Particle Edit Mode
******************

Using *Particle Edit Mode* you can edit the keyed points (keyframes)
and paths of :doc:`Hair </physics/particles/hair/index>`,
:doc:`Particle </physics/particles/index>`, :doc:`Cloth </physics/cloth/index>`, and
:doc:`Soft Body </physics/soft_body/index>` simulations. (You can also edit and style hair before baking.)

Since working in Particle Edit Mode is pretty easy and very similar
to working with vertices in the 3D Viewport, we will show how to set up
a particle system and then give a reference of the various functions.

.. important::

   Particle Edit Mode, specifically for hair is deprecated;
   please use the new :ref:`bpy.ops.object.curves_empty_hair_add`
   object with its associated :doc:`Sculpt Mode </sculpt_paint/curves_sculpting/introduction>` instead.

.. important::

   Editing a cached cloth simulation is not currently working, see:
   `blender/blender#77114 <https://projects.blender.org/blender/blender/issues/77114>`__ for details.


Usage
=====

.. tip:: Only Frames Baked to Memory are Editable!

   If you cannot edit the particles, check that you are not baking to
   a :doc:`Disk Cache </physics/particles/emitter/cache>`.


Setup for Hair Particles
------------------------

#. Create a *Hair* particle system.
#. Give it an initial velocity in the *Normal* direction.
#. Create a simulation.
#. Check the *Hair Dynamics* box.

.. figure:: /images/physics_particles_mode_example.png

   Editing hair strands in Particle Edit Mode.


Setup for Particle, Cloth, and Soft Body Simulations
----------------------------------------------------

#. Use *Emitter* particles, or a cloth/soft body simulation.
#. Create a simulation by setting up objects and or emitters,
   set your time range (use a small range if you are just starting out and experimenting),
   set up the simulation how you want it, using :kbd:`Alt-A` to preview it.


Bake the Simulation
-------------------

Once you are happy with the general simulation, :doc:`bake </physics/particles/emitter/cache>`
the simulation from Object Mode. The simulation must be baked to enable editing.


Edit the Simulation
-------------------

Switch to *Particle Edit* from the *Mode* select menu in the header of the 3D Viewport
to edit the particle's paths/Keyframes. You may need to press :kbd:`T` from within the 3D Viewport
to see the *Particle Edit* panel. Move to the frame you want to edit and use the various *Particle Edit*
tools to edit your simulation. Work slowly, previewing your changes with :kbd:`Alt-A`,
and save often so that you can go back to the previous version should something happen,
or that you do not like the latest changes you have made.

.. tip:: To be able to clearly see what you are working on:

   #. Open the Options panel in the Toolbar.
   #. Select *Point select mode* (see below) in the header of the 3D Viewport.
      This will display key points along the particle path.


.. _particle-edit-selecting:

Selecting
=========

- Single: :kbd:`LMB`.
- All: :kbd:`A`.
- None :kbd:`Alt-A`
- Invert :kbd:`Ctrl-I`
- Box select: :kbd:`B`.
- Circle Select :kbd:`C`.
- Lasso Select :kbd:`Ctrl-Alt-LMB`.
- Select Linked: Move the mouse over a keypoint and press :kbd:`L`.
- Root/Tips: :menuselection:`Select --> Roots / Tips`.

.. tip:: Selections

   Selections are extremely useful for modifying only the particles that you want.
   Hover over a particle path and press :kbd:`L` to link-select it,
   hover over the next and press :kbd:`L` to add that path to the selection.
   To remove a path, hold :kbd:`Shift` and press :kbd:`L`. To Deselect all press :kbd:`A`.

   The method to select individual points is the same as in Edit Mode.
   :kbd:`RMB` to select, :kbd:`Shift-RMB` to add/remove a point from the selection.


.. _bpy.ops.particle.select_random:

Select Random
-------------

Randomly selects particles.

Percent
   Percent of particles to randomly select.
Random Seed
   Seed value to use for the selection.
Action
   Select random can be either used to select or deselect particles.
Type
   Selects either hair or points. Here these terms can be confusing because
   hair/point does not refer to the particle type but the path/points of the hair/particle.


.. _bpy.types.ParticleEdit.select_mode:

Select Modes
------------

.. figure:: /images/physics_particles_mode_select-modes.png

   Select Modes.

:Path: No keypoints are visible, you can select/deselect only all particles.
:Point: You see all of the keypoints.
:Tip: You can see and edit (including the brushes) only the tip of the particles, i.e. the last keypoint.


.. _bpy.types.ParticleBrush:

Tools
=====

.. reference::

   :Mode:      Particle Edit Mode
   :Tool:      :menuselection:`Toolbar`


Comb
----

Moves the keypoints (similar to the Proportional Editing tool).

Deflect Emitter
   Hair particles only -- Do not move keypoints through the emitting mesh.

   Distance
      The distance to keep from the Emitter.


Smooth
------

Parallels visually adjacent segments.


Add
---

Adds new particles.

Count
   The number of new particles per step.
Interpolate
   Interpolate the shape of new hairs from existing ones.
Steps
   Amount of brush steps.
Keys
   How many keys to make new particles with.


Length
------

Scales the segments, so it makes the hair longer with *Grow* or shorter with *Shrink*.

Grow/Shrink
   Sets the brush to add the effect or reverse it.


Puff
----

Rotates the hair around its first keypoint (root).
So it makes the hair stand up with *Add* or lay down with *Sub*.

Puff Volume
   Apply puff to unselected end points, (Helps to maintain the hair volume when puffing the root.)


Cut
---

Scales the segments until the last keypoint reaches the brush.


Weight
------

This is especially useful for soft body animations, because the weight defines the soft body *Goal*.
A keypoint with a weight of 1 will not move at all,
a keypoint with a weight of 0 subjects fully to soft body animation.
This value is scaled by the Strength *Min* to *Max* range of soft body goals...

.. Not more true, I think: "Weight is only displayed for the complete hair (i.e. with the value of the tip),
   not for each keypoint, so it's a bit difficult to paint".


Common Options
--------------

Below the brush types, their settings appear:

Radius :kbd:`F`
   Set the radius of the brush.
Strength :kbd:`Shift-F`
   Set the strength of the brush effect (not for Add brush).


Options
=======

.. reference::

   :Mode:      Particle Edit Mode
   :Panel:     :menuselection:`Tool Settings --> Options`

Auto-Velocity :guilabel:`Emitter`
   Recalculate velocities of particles according to their edited paths.
   Otherwise, the original velocities values remains unchanged
   regardless of the actual distance that the particles moves.

Mirror X
   Enable mirror editing across the local X axis.

Preserve
   Strand Length
      Keep the length of the segments between the keypoints when combing or smoothing the hair.
      This is done by moving all the other keypoints.
   Root Positions
      Keep first key unmodified, so you cannot transplant hair.


Cut Particles to Shape
----------------------

Shape Object
   A mesh object which boundary is used by the *Shape Cut* tool.

Cut
   This grooming tool trims hairs to a shape defined by the *Shape Object*.
   This is a quicker way of avoiding protruding hair sections from lengthening than using the Cutting tool.
   It works especially well for characters with extensive fur,
   where working in a single plane with the Cutting tool becomes tedious.

.. list-table:: Shape Cut example.

   * - .. figure:: /images/physics_particles_mode_shapecut-before.png

          Before.

     - .. figure:: /images/physics_particles_mode_shapecut-after.png

          After.


Viewport Display
----------------

Path Steps
   The number of steps used to draw the path; improves the smoothness of the particle path.
Children :guilabel:`Hair`
   Displays the children of the particles too.
   This allows to fine-tune the particles and see their effects on the result,
   but it may slow down your system if you have many children.
Particles :guilabel:`Emitter`
   Displays the actual particles on top of the paths.
Fade Time
   Fade out paths and keys further away from current time.

   Frames
      How many frames to fade.


Editing
=======

Moving Keypoints or Particles
-----------------------------

- To move selected keypoints press :kbd:`G`, or use one of the various other methods to move vertices.
- To move a particle root you have to turn off Keep *Root* in the Toolbar.
- You can do many of the things like with vertices, including scaling,
  rotating and removing (complete particles or single keys).
- You may not duplicate or extrude keys or particles,
  but you can subdivide particles which adds new keypoints
  :menuselection:`Particle --> Subdivide`.
- Alternatively you can re-key a particle
  :menuselection:`Particle --> Rekey`.

How smoothly the hair and particle paths are displayed depends on the *Path Steps*
setting in the Toolbar. Low settings produce blocky interpolation between points,
while high settings produce a smooth curve.


Mirror
------

.. reference::

   :Mode:      Particle Edit Mode
   :Menu:      :menuselection:`Particle --> Mirror`

If you want to create an X axis symmetrical haircut you have to do following steps:

#. Select all particles with :kbd:`A`.
#. Mirror the particles with :menuselection:`Particle --> Mirror`.
#. Turn on *X Mirror* in :menuselection:`Sidebar Region --> Tool --> Options`.

It may happen that after mirroring two particles occupy nearly the same place.
Since this would be a waste of memory and render time,
you can use *Merge by Distance* from the *Particle* menu.


Unify Length
------------

.. reference::

   :Mode:      Particle Edit Mode
   :Menu:      :menuselection:`Particle --> Unify Length`

This tool is used to make all selected hair uniform length by finding the average length.


Show/Hide
---------

.. reference::

   :Mode:      Particle Edit Mode
   :Menu:      :menuselection:`Particle --> Show/Hide`

Hiding and unhiding of particles works similar as with vertices in the 3D Viewport.
Select one or more keypoints of the particle you want to hide and press :kbd:`H`.
The particle in fact does not vanish, only the key points.

Hidden particles (i.e. particles whose keypoints are hidden)
do not react on the various brushes. But:

If you use *Mirror Editing* even particles with hidden keypoints may be moved,
if their mirrored counterpart is moved.

To unhide all hidden particles press :kbd:`Alt-H`.


## Particle System Panel


*********************
Particle System Panel
*********************

.. reference::

   :Panel:     :menuselection:`Particle System --> Particle System`

.. figure:: /images/physics_particles_particle-system-panel_panel.png

   Particle System panel.

These are the basic settings.

Active Particle System
   The :ref:`List View <ui-list-view>` of the objects Particle Modifier(s).

   Specials
      Copy Active to Selected Objects
         Copies the active particle system to all selected objects.
      Copy All to Selected Objects
         Copies all particle systems from the active object to all selected objects.
      Duplicate Particle Systems
         Duplicates the particle system within the active object.
         The *Duplicate Settings* option (in the :ref:`bpy.ops.screen.redo_last` panel) will duplicate
         settings as well, so the new particle system uses its own settings.

Particle Settings
   The :ref:`Data-Block menu <ui-data-block>` for settings.

Type
   Main selector of the system type.

   Emitter
      In such a system, particles are :doc:`emitted </physics/particles/emitter/index>` from the object.
   Hair
      Use :doc:`Hair </physics/particles/hair/index>` type, rendered as strands.

      Regrow
         Regrows the hair for each frame. This is useful when you are animating properties.
      Advanced
         Enables advanced settings which reflect the same ones as working in Emitter mode.

         .. note::

            This manual assumes that this option is enabled.

      Segments
         Controls the number of parts a hair is made of.
         Increasing this value will improve the quality of animations.


Workflow
========

The process for working with standard particles is:

#. Create the mesh which will emit the particles.
#. Create one or more Particle Systems to emit from the mesh. Many times, multiple
   particle systems interact or merge with each other to achieve the overall desired effect.
#. Tailor each Particle System's settings to achieve the desired effect.
#. Animate the base mesh and other particle meshes involved in the scene.
#. Define and shape the path and flow of the particles.
#. For :doc:`Hair </physics/particles/hair/index>` particle systems: Sculpt the emitter's flow
   (cut the hair to length and comb it for example).
#. Make final render and do physics simulation(s), and tweak as needed.


Creating a Particle System
--------------------------

.. TODO2.8:
   .. figure:: /images/physics_particles_particle-system-panel_create-new.png

      Adding a particle system.

To add a new particle system to an object, go to the *Particles* tab of the Properties
editor and click the small ``+`` button. An object can have many Particle Systems.

Each particle system has separate settings attached to it.
These settings can be shared among different particle systems, so one does not have to copy
every setting manually and can use the same effect on multiple objects.


Types of Particle Systems
^^^^^^^^^^^^^^^^^^^^^^^^^

.. _fig-particle-intro-system-type:

.. TODO2.8:
   .. figure:: /images/physics_particles_particle-system-panel_select-type.png

      Particle System Types.

After you have created a particle system,
the Properties fills with many panels and buttons.
But do not panic! There are two different types of particle systems,
and you can change between these two with the *Type* selector:
Emitter and Hair.

The settings in the *Particle System* tab are partially different for each system type.


## Texture Influence

.. https://projects.blender.org/blender/documentation/issues/46363
.. left out: Mapping Coordinates

.. _bpy.types.ParticleSettingsTextureSlot:

*****************
Texture Influence
*****************

.. reference::

   :Panel:     :menuselection:`Texture --> Influence`

.. TODO2.8:
   .. figure:: /images/physics_particles_texture-influence_panel.png
      :align: right

      Texture influence settings.

Defines the settings of a Particle system spatial with a texture.


General
=======

Time
   Affect the emission time of the particles.
Lifetime
   Affect the life time of the particles.
Density
   Affect the density of the particles.
Size
   Affect the particles size.


Physics
=======

Velocity
   Affect the particles initial velocity.
Damp
   Affect the particles velocity damping.
Gravity
   Affect the particles gravity.
Force Fields
   Affect the particles force fields.


Hair
====

Length
   Affect the child hair length.
Clump
   Affect the child clumping.
Kink
   Affect the child kink.
Rough
   Affect the child roughness.


## Cache


*****
Cache
*****

.. reference::

   :Panel:     :menuselection:`Particle System --> Cache`

In order to improve real-time response and avoid unnecessary recalculation of particles,
the particle data can be cached in memory or stored on a drive.

The *Emitter* particle system uses a unified system for caching and baking (together with Soft Body and Cloth).

.. TODO2.8:
   .. figure:: /images/physics_particles_emitter_cache_settings.png

   Particles Cache settings.

.. seealso::

   See the :doc:`General Baking </physics/baking>` docs for more information.


Hints
=====

- The simulation is only calculated for positive frames
  in between the *Start* and *End* frames of the *Cache* panel, whether you bake or not.
  So if you want a simulation that is longer than the default frame range, you have to change the *End* frame.
- When an animation is played, each physics system writes each frame to the cache.
  Note that for the cache to fill up,
  one has to start the playback before or on the frame that the simulation starts.
- The cache is cleared automatically on changes. But not on all changes,
  so it may be necessary to free it manually, e.g. if you change a force field.
- The system is protected against changes after baking.
  If for example the mesh changes the simulation is not calculated anew.
- The bake result can be cleared by clicking on the *Free Bake* button in the simulation cache settings.
- A simulation can only be edited in Particle Edit Mode when it has been baked in memory.
  And cannot be edited if the Disk Cache is used.
- If you are not allowed to write to the required subdirectory caching will not take place,
  e.g. if your blend-file path is very long and your operating system
  has a limit on the path length that is supported.
- Be careful with the sequence of modifiers in the modifier stack.
  You may have a different number of faces in the 3D Viewport and
  for rendering (e.g. when using subdivision surface), if so,
  the rendered result may be very different from what you see in
  the 3D Viewport.


## Children


********
Children
********

.. reference::

   :Panel:     :menuselection:`Particle System --> Children`

*Children* are *Hair* or *Emitter* particles originating from individual particles.
They make it possible to work primarily with a relatively low amount of Parent particles,
for whom the physics are calculated. The children are then aligned to their parents.
The number and visualization of the children can be changed without a recalculation of the physics.

If you activate children, the parents are no longer rendered. This can be enabled in the Render panel
:ref:`Parent Particles <bpy.types.ParticleSettings.use_parent_particles>`. By default, parent particles
are not rendered because the shape of the children can be quite different from that of their parents.


Common Options
==============

Child Type
   None
      No children are generated.
   Simple
      Children are emitted from the parent position.
   Interpolated
      Children are emitted between the *Parent* particles on the faces of a mesh.
      They interpolate between adjacent parents. This is especially useful for fur,
      because you can achieve an even distribution.
      Some of the children can become virtual parents, which are influencing other particles nearby.
Display Amount
   The number of children in the 3D Viewport.
Render Amount
   The number of children to be rendered.
Length
   Length of child paths.
Threshold
   Amount of particles left untouched by child path length.
Seed
   Offset in the random number table for child particles, to get a different randomized result.


Clumping
--------

.. reference::

   :Panel:     :menuselection:`Particle System --> Children --> Clumping`

Use Clump Curve
   Use :ref:`ui-curve-widget` instead of parameters.
Clump
   Clumping amount along child strands.
   The children may meet at their tip (1.0) or start together at their root (-1.0).
Shape
   Form of *Clump*. Either inverse parabolic (0.99) or exponentially (-0.99).
Twist
   Todo.
Use Twist Curve
   Todo.


Clump Noise
^^^^^^^^^^^

Creates random clumps around the parent hair.

Clump Noise Size
   The size of the clumps.


Roughness
---------

.. reference::

   :Panel:     :menuselection:`Particle System --> Children --> Roughness`

Use Roughness Curve
   Use :ref:`ui-curve-widget` instead of parameters.
Uniform, Size
   It is based on children location so it varies the paths in a similar way when the children are near.
Endpoint, Shape
   "Rough End" randomizes path ends (a bit like random negative clumping).
   Shape may be varied from <1 (parabolic) to 10.0 (hyperbolic).
Random, Size, Threshold
   It is based on a random vector so it is not the same for nearby children.
   The threshold can be specified to apply this to only a part of children.
   This is useful for creating a few stray children that will not do what others do.


Kink
----

.. reference::

   :Panel:     :menuselection:`Particle System --> Children --> Kink`

.. _fig-particle-child-kink:

.. figure:: /images/physics_particles_emitter_children_kink.png

   Child particles with Kink.

   From left to right: Curl, Radial, Wave, Braid, Spiral.

With *Kink* you can rotate the children around the parent.
See Fig. :ref:`fig-particle-child-kink` above picture for the different types of *Kink*.

Kink Type
   Nothing
      Deactivated.
   Curl
      Children grow in a spiral around the parent hairs.
   Radial
      Children form around the parent a wave shape that passes through the parent hair.
   Wave
      Children form a wave, all in the same direction.
   Braid
      Children braid themselves around the parent hair.
   Spiral
      Generates a spiral at the end of each hair.

      Radius, Resolution
         Define the overall size.
      Shape
         Makes the spiral grow in- or outward.

   .. note:: Alignment Limitations

      When hair is pointing straight up (along the chosen spiral axis, default Z), spirals may not show up!
      This is a limitation of the projection method used.
      Giving a slight tilt or random orientation to hairs fixes this.

Amplitude
   The amplitude of the offset.
Clump
   How much clump effects kink amplitude.
Flatness
   How flat the hairs are.

Frequency
   The frequency of the offset (1/total length). The higher the frequency the more rotations are done.
Shape
   Where the rotation starts (offset of rotation).


Simple
======

Size
   A multiplier for children size.
Random Size
   Random variation to the size of child particles.

Radius
   The radius in which the children are distributed around their parents.
   This is 3D, so children may be emitted higher or lower than their parents.
Roundness
   The roundness of the children around their parents. Either in a sphere (1.0) or in-plane (0.0).


Interpolated
============

Virtual Parents
   Relative amount of virtual parents.
Long Hair
   Calculate children that suit long hair well.


Parting
-------

Parting
   Creates parting in the children based on parent strands.

Min/Max
   The minimum/maximum root to tip angle (tip distance/root distance for long hair).


Example
=======

.. figure:: /images/physics_particles_emitter_children_round-clump.png

   From left to right: Round: 0.0, Round: 1.0, Clump: 1.0, Clump: -1.0, Shape: -0.99.


## Display


****************
Viewport Display
****************

.. reference::

   :Panel:     :menuselection:`Particle System --> Viewport Display`

The Display Panel controls how particles are displayed in the 3D Viewport.
This does not necessarily determine how they will appear when rendered.

Display As
   None
      The particles are not shown in the 3D Viewport and are not rendered.
      The emitter may be rendered though.
   Rendered
      Particles are displayed the way they are rendered.
   Point
      Particles are displayed as square points.
      Their size is independent of the distance from the camera.
   Circle
      Particles are displayed as circles that face the view.
      Their size is independent of the distance from the camera.
   Cross
      Particles are displayed as 6-point crosses that align to the rotation of the particles.
      Their size is independent of the distance from the camera.
   Axis
      Particles are displayed as 3-point axes.
      This is useful if you want to see the orientation and rotation of particles in the viewport.
      Increase the *Display Size* until you can clearly distinguish the axis.

   .. note::

      Particles visualized like Point, Circle, Cross and Axis do not have any special options,
      but can be very useful when you have multiple particle systems at play,
      if you do not want to confuse particles of one system from another
      (e.g. in simulations using *Boids* physics).

Color
   The Color Menu allows you to display particle's color according to certain particle properties.

   None
      Particles are black.
   Material
      Particles are colored according to the material they are given.
   Velocity
      Color particles according to their speed.
      The color is a ramp from blue to green to red, Blue being the slowest,
      and Red being velocities approaching the value of *Max* or above.
      Increasing *Max* allows for a wider range of particle velocities.
   Acceleration
      Color particles according to their acceleration.
Amount
   Specifies the percentage of all particles to show in the viewport (all particles are still rendered).
Show Emitter
   Make instancer visible in viewport.


## Emission


********
Emission
********

.. reference::

   :Panel:     :menuselection:`Particle System --> Emission`

The *Emitter* system works just like its name says: it emits/produces particles for a certain amount of time.
In such a system, particles are emitted from the selected object from the *Start*
frame to the *End* frame and have a certain lifespan.
These particles are rendered default as :ref:`Halos <particle-halo>`,
but you may also render this kind of particles as objects
(depending on the particle system's render settings,
see :doc:`Visualization </physics/particles/emitter/render>`).

.. TODO2.8:
   .. figure:: /images/physics_particles_emitter_emission_settings.png

      Particle Emission settings.

The buttons in the *Emission* panel control the way particles are emitted over time:

Number
   The maximum amount of parent particles used in the simulation.
Seed
   Blender uses this as starting point to produce random numbers during the simulation.
Frame Start
   The start frame of particle emission. You may set negative values,
   which enables you to start the simulation before the actual rendering.
End
   The end frame of particle emission.
Lifetime
   The lifespan (in frames) of the particles.
Lifetime Randomness
   A random variation of the lifetime of a given particle.
   The shortest possible lifetime is *Lifetime* × (1 - *Random*).
   Values above 1.0 are not allowed.
   For example with the default *Lifetime* value of 50 a *Random* setting of 0.5
   will give you particles with a live span ranging from 50 frames to :math:`50 × (1.0 - 0.5) = 25`
   frames, and with a *Random* setting of 0.75 you will get particles with live spans ranging
   from 50 frames to :math:`50 × (1.0 - 0.75) = 12.5` frames.


Source
======

.. reference::

   :Panel:     :menuselection:`Particle System --> Emission --> Source`

Emit From
   Defines how and where the particles are emitted,
   giving precise control over their distribution.

   .. tip::

      You may use vertex groups to confine the emission, that is done in the *Vertex Groups* panel.

   Vertices
      Emits particles from the vertices of a mesh.
   Faces
      Emits particles from the surface of a mesh's faces.
   Volume
      Emits particles from the volume of an enclosed mesh.

      .. tip::

         Your mesh must be :term:`Manifold` to emit particles from the volume.
         Some modifiers like the Edge Split Modifier break up the surface,
         in which case volume emission will not work correctly!

.. _bpy.types.ParticleSettings.use_modifier_stack:

Use Modifier Stack
   Take any :doc:`Modifiers </modeling/modifiers/introduction>` above the Particle Modifier
   in the :ref:`modifier stack <modifier-stack>` into account when emitting particles,
   else it uses the original mesh geometry.

   .. note::

      Note that particles may differ in the final render if these modifiers
      generate different geometry between the viewport and render.

Distribution
   These settings control how the emissions of particles are distributed
   throughout the emission locations when emitting from either *Faces* or *Volume*.

   Jittered
      Particles are placed at jittered intervals on the emitter elements.

      Particles/Face
         Number of emissions per face (0 = automatic).
      Jittering Amount
         Amount of jitter applied to the sampling.
   Random
      Particles are emitted from random locations in the emitter's elements.
   Grid
      Particles are set in a 3D grid and particles near/in the elements are kept.

      Invert Grid
         Invert what is considered the object and what is not.
      Hexagonal
         Uses a hexagonal-shaped grid instead of a rectangular one.
      Resolution
         Resolution of the grid.
      Random
         Add a random offset to grid locations.

Random Order
   The emitter element indices are gone through
   in a random order instead of linearly (one after the other).

   Not available for *Grid* distribution.
Even Distribution
   Particle distribution is made even based on surface area of the elements,
   i.e. small elements emit less particles than large elements, so that the particle density is even.


## Force Field


************
Force Fields
************

Field Weights
=============

.. reference::

   :Panel:     :menuselection:`Particle System --> Field Weights`

The Field Weight panel allows you to control how much influence each type of external force field, or effector,
has on the particle system. Force fields are external forces that give dynamic system's motion.
The force fields types are detailed on the :doc:`Force Field Page </physics/forces/force_fields/index>`.

Effector Group
   Limit effectors to a specified group. Only effectors in this group will have an effect on the current system.
Gravity
   Control how much the Global Gravity has an effect on the system.
All
   Scale all of the effector weights.


Force Fields Settings
=====================

.. reference::

   :Panel:     :menuselection:`Particle System --> Force Fields Settings`

The Force Field Settings panel allows you to make each individual act as a force field,
allowing them to affect other dynamic systems, or even, each other.

Self Effect
   Causes the particle force fields to have an effect on other particles within the same system.
Effector Amount
   Set how many of the particles act as force fields. 0 means all of them are effectors.

You can give particle systems up to two force fields. By default they do not have any.
Choose an effector type from the selector to enable them.
Settings are described in the :ref:`Common Settings section <force-field-common-settings>`.


## Index


###########
  Emitter
###########

.. toctree::
   :maxdepth: 2

   emission.rst
   cache.rst
   velocity.rst
   rotation.rst
   physics/index.rst
   render.rst
   display.rst
   children.rst
   force_field.rst
   vertex_groups.rst


## Render

******
Render
******

.. reference::

   :Panel:     :menuselection:`Particle System --> Render`

The Render Panel controls how particles appear when they are rendered.

.. note::

   Cycles supports only Object and Collection render types.


Common Settings
===============

Scale
   Todo.
Scale Randomness
   Todo.
Material
   Set which of the object's materials is used to shade the particles.
Coordinates System
   Use a different object's coordinates to determine the birth of particles.
Show Emitter
   When disabled, the emitter is no longer rendered. Activate the button *Emitter* to also render the mesh.


Render As
=========

None
----

When set to *None*, particles are not rendered.
This is useful if you are using the particles to duplicate objects.


.. _particle-halo:

Halo
----

Halos are rendered as glowing dots or a little cloud of light.
Although they are not really lights because they do not cast light into the scene like a light object.
They are called *Halos* because you can see them, but they do not have any substance.


.. _particle-path:

Path
----

.. TODO2.8:
   .. figure:: /images/physics_particles_emitter_render_path.png

      The Visualization panel for Path visualization.

The *Path* visualization needs a :doc:`Hair </physics/particles/hair/index>` particle system or
:doc:`Keyed </physics/particles/emitter/physics/keyed>` particles.

B-Spline
   Interpolate hair using B-splines.
   This may be an option for you if you want to use low *Render* values.
   You loose a bit of control but gain smoother paths.
Steps
   Set the number of subdivisions of the rendered paths (the value is a power of 2).
   You should set this value carefully,
   because if you increase the render value by two you need four times more memory to render.
   Also the rendering is faster if you use low render values (sometimes drastically).
   But how low you can go with this value depends on the waviness of the hair (the value is a power of 2).
   This means 0 steps give 1 subdivision,
   1 give 2 subdivisions, 2 → 4, 3 → 8, 4 → 16, ... 𝓃 → 2\ :sup:`𝓃`.


Timing
------

.. reference::

   :Panel:     :menuselection:`Particle System --> Render --> Timing`
   :Type:      Hair

Absolute Path Time
   Path timing is in absolute frames.
End
   End time of the practical path.
Random
   Give the path length a random variation.


.. _particle-object:

Object
------

.. reference::

   :Panel:     :menuselection:`Particle System --> Render --> Object`

Instance Object
   The specified object is instanced in place of each particle.

Global Coordinates
   Use object's global coordinates for instancing.
Object Rotation
   Use the rotation of the object.
Object Scale
   Use the size of the object.


.. _particle-collection:

Collection
----------

.. reference::

   :Panel:     :menuselection:`Particle System --> Render --> Collection`

Instance Collection
   The objects that belong to a collection are instanced sequentially in the place of the particles.
Whole Collection
   Use the whole group at once, instead of one of its elements, the group being displayed in place of each particle.
Pick Random
   The objects in the group are selected in a random order, and only one object is displayed in place of a particle.
   Please note that this mechanism fully replaces old Blender particles system using parentage
   and *Instancing Vertices* to replace particles with actual geometry.
   This method is fully deprecated and does not work anymore.
Global Coordinates
   Use object's global coordinates for instancing.
Object Rotation
   Use the rotation of the objects.
Object Scale
   Use the size of the objects.


Use Count
^^^^^^^^^

.. reference::

   :Panel:     :menuselection:`Particle System --> Render --> Collection --> Use Count`

Use objects multiple times in the same groups.
Specify the order and number of times to repeat each object with the :ref:`list view <ui-list-view>` that appears.
You can duplicate an object in the list with the ``+`` button, or remove a duplicate with the ``-`` button.


Extra
=====

.. reference::

   :Panel:     :menuselection:`Particle System --> Render --> Extra`

.. _bpy.types.ParticleSettings.use_parent_particles:

Parents Particles
   Render also parent particles if child particles are used.
   Children have a lot of different deformation options,
   so the straight parents would stand between their curly children.
   So by default *Parents* are not rendered if you activate *Children*.
   See :doc:`Children </physics/particles/emitter/children>`.

Unborn
   Render particles before they are born.
Dead
   Render particles after they have died.
   This is very useful if particles die in a collision *Die on hit*, so you can cover objects with particles.


## Rotation

********
Rotation
********

.. reference::

   :Panel:     :menuselection:`Particle System --> Rotation`

These parameters specify how the individual particles are rotated at the start of,
and during, their lifetime. You can visualize their orientation by setting *Display As*
to *Axis* in the :doc:`/physics/particles/emitter/display` panel.

Orientation Axis
   Aligns the X axis of new particles to:

   None
      The global X axis.
   Normal
      The emitter's surface normal.
   Normal-Tangent
      The emitter's surface normal, additionally aligning the particle's Y axis to the positive V
      direction in the emitter's active UV map. This makes it possible to deform the emitter
      while keeping particle rotation consistent.
   Velocity / Hair
      The particle's initial velocity vector/hair growth direction.
   Global X, Y, Z
      One of the global axes.
   Object X, Y, Z
      One of the emitter's local axes.
Randomize
   How much to randomize the particle's initial rotation (along all axes).
Phase
   Initial rotation around the particle's X axis, going from -1 (-180°) to 1 (180°).
Randomize Phase
   Maximum random rotation to add to the *Phase*, going from 0 (0°) to 2 (360°).
Dynamic
   Whether the particles' rotation can change over time.


Angular Velocity
================

.. reference::

   :Panel:     :menuselection:`Particle System --> Rotation --> Angular Velocity`

Lets you configure if and how particles should spin over time.
*Dynamic* needs to be enabled for this to work.

Axis
   The axis to spin around. If this is set to *Velocity*, *Horizontal*, or *Vertical*,
   particles will additionally spin to keep the same orientation relative to their
   direction of movement, even if *Amount* is zero.

   None
      Spinning is disabled.
   Velocity
      Spin around the particle's velocity vector.
   Horizontal
      Spin around the axis that's horizontal (lying in the global XY plane)
      and perpendicular to the particle's velocity. Particles moving along the
      global Z axis won't spin because no unique rotation axis exists in this case.
   Vertical
      Spin around the axis that's perpendicular to both the particle's velocity
      and the above *Horizontal* axis. Particles moving along the global Z axis
      won't spin.
   Global X, Y, Z
      Spin around the chosen global axis.
   Random
      Spin around a random axis.

   .. hint::

      If you use a :doc:`/physics/forces/force_fields/types/curve_guide` and want the
      particles to always point in the direction of the curve, you should set the
      *Orientation Axis* to *Velocity / Hair*, enable *Dynamic*, and set the
      *Angular Velocity Axis* to *Velocity*.

      (For a regular object, you'd normally use the *Follow Curve* option of a
      :doc:`/animation/constraints/relationship/follow_path` or the legacy
      :ref:`Follow <bpy.types.Curve.use_path_follow>` option of the curve itself,
      but these don't work for particles.)

Amount
   How fast to spin around the *Axis*.


## Velocity


********
Velocity
********

.. reference::

   :Panel:     :menuselection:`Particle System --> Velocity`

The initial velocity of particles can be set through different parameters,
based on the type of the particle system.
If the particle system type is Emitter or Hair,
then the following parameters give the particle an initial velocity.

Normal
   The emitter's surface normals (i.e. let the surface normal give the particle a starting speed).
Tangent
   Let the tangent speed give the particle a starting speed.
Tangent Phase
   Rotates the surface tangent.
Object Align
   Give an initial velocity in the X, Y, and Z axes.

   X, Y, Z
Object Velocity
   The emitter objects movement (i.e. let the object give the particle a starting speed).
Randomize
   Gives the starting speed a random variation.
   You can use a texture to only change the value, see Controlling Emission, Interaction and Time.


## Vertex Groups

.. _bpy.types.ParticleDupliWeight:

*************
Vertex Groups
*************

.. reference::

   :Panel:     :menuselection:`Particle System --> Vertex Groups`

The Vertex groups panel allows you to specify vertex groups to use for several child particle settings.
You can also negate the effect of each vertex group with the checkboxes.
You can affect the following attributes:

Density
   Defines the density of the particle distribution.
Length
   Defines the length of the hair.
Clump
   Controls the amount of clumping.
   The weight of 1.0 gives current *Clump* value, weight of 0.0 completely removes effect.
Kink
   Controls the frequency of the children Kink.
Roughness 1
   Adjusts the *Uniform* roughness parameter.
Roughness 2
   Adjusts the *Random* roughness parameter.
Roughness End
   Adjusts the *Endpoint* roughness parameter.
Twist
   Vertex group to control the children's *Twist* effect.
   Gives control over the direction of the twist, as well as the amount.
   The weight of 0.5 is neutral, i.e. there is no twist effect.


## Boids

.. _bpy.types.Boid:
.. _bpy.ops.boid:

*****
Boids
*****

.. reference::

   :Panel:     :menuselection:`Particle System --> Physics`
   :Type:      Boids

.. TODO2.8:
   .. figure:: /images/physics_particles_emitter_physics_boids_panel.png

      Boid Physics settings.

Boids particle systems are controlled by a limited artificial intelligence,
which can be programmed to follow basic rules and behaviors.
They are ideal for simulating flocks, swarms, herds and schools of various kind of animals,
insects and fishes or predators vs. preys simulations.
They can react on the presence of other objects and on the members of their own system.
Boids can handle only a certain amount of information,
therefore the sequence of the *Boid Brain* rules is very important.
In certain situations only the first three parameter are evaluated.


Movement
========

.. reference::

   :Panel:     :menuselection:`Particle System --> Physics --> Movement`

Boids try to avoid objects with activated Collision.
They try to reach goal objects, and fly from "predators" according to the *Boid Brain* settings.

Boids can have different physics depending on whether they are in the air,
or on land (on collision object).

Allow Flight
   Allow boids to move in the air.
Allow Land
   Allow boids to move on land.
Allow Climbing
   Allow boids to climb goal objects.

Max Air Speed
   Set the Maximum velocity in the air.
Min Air Speed
   Set the Minimum velocity in the air.
Max Air Acceleration
   Lateral acceleration in air, percentage of the max velocity (turn).
   Defines how fast a boid is able to change direction.
Max Air Angular Velocity
   Tangential acceleration in air, percent 180 degrees.
   Defines how much the boid can suddenly accelerate in order to fulfill a rule.
Air Personal Space
   Radius of boids personal space in air. Percentage of particle size.
Landing Smoothness
   How smoothly the boids land.

Max Land Speed
   Set the Maximum velocity on land.
Jump Speed
   Maximum speed for jumping.
Max Land Acceleration
   Lateral acceleration on land, percent of max velocity (turn). Defines how fast a boid is able to change direction.
Max Land Angular Velocity
   Tangential acceleration on land, percent 180 degrees.
   Defines how much the boid can suddenly accelerate in order to fulfill a rule.
Land Personal Space
   Radius of boids personal space on land. Percentage of particle size.
Land Stick Force
   How strong a force must be to start effecting a boid on land.

Collision Collection
   Only collide with objects in this collection.


Battle
======

.. reference::

   :Panel:     :menuselection:`Particle System --> Physics --> Battle`

Health
   Initial boid health when born.
Strength
   Maximum caused damage per second on attack.
Aggression
   Boid will fight this time stronger than enemy.
Accuracy
   Accuracy of attack.
Range
   Maximum distance of which a boid can attack.


Misc
====

.. reference::

   :Panel:     :menuselection:`Particle System --> Physics --> Misc`

Banking
   Amount of rotation around velocity vector on turns. Banking of 1.0 gives a natural banking effect.
Pitch
   Amount of rotation around side vector.
Height
   Boid height relative to particle size.


Relations
=========

.. reference::

   :Panel:     :menuselection:`Particle System --> Physics --> Relations`

Target
   This :ref:`list view <ui-list-view>` allows you to set up other particle systems to react with the boids.
Target Object
   A :ref:`data ID <ui-data-id>` to select an object with a particle system set on.
System
   Index of the *Object*\ 's particle system as set in the list view in the particle panel.

Mode
   Enemy
      Setting the type to *Enemy* will cause the systems to fight with each other.
   Friend
      Will make the systems work together.
   Neutral
      Will not cause them to align or fight with each other.


Deflection
----------

Boids will try to avoid deflector objects according to the Collision rule's weight.
It works best for convex surfaces (some work needed for concave surfaces).


Force Fields
------------

As other physics types, Boids is also influenced by external force fields.

In addition, special *Boid* force fields can be used with the Boids physics.
These effectors could be predators (positive Strength) that boids try to avoid,
or targets (negative Strength) that boids try to reach
according to the (respectively) *Avoid* and *Goal* rules of the *Boid Brain*.


Boid Brain
==========

.. reference::

   :Panel:     :menuselection:`Particle System --> Physics --> Boid Brain`

The Boid Brain panel controls how the boids particles will react with each other.
The boids' behavior is controlled by a list of rules.
Only a certain amount of information in the list can be evaluated.
If the memory capacity is exceeded, the remaining rules are ignored.

The rules are by default parsed from top-list to bottom-list
(thus giving explicit priorities),
and the order can be modified using the little arrows buttons on the right side.

Rule Evaluation
   There are three ways to control how rules are evaluated:

   Average
      All rules are averaged.
   Random
      A random rule is selected for each boid.
   Fuzzy
      Uses fuzzy logic to evaluate rules. Rules are gone through top to bottom.
      Only the first rule that affect above the *Rule Fuzziness* threshold is evaluated.
      The value should be considered how hard the boid will try to respect a given rule
      (a value of 1 means the Boid will always stick to it, a value of 0 means it will never).
      If the boid meets more than one conflicting condition at the same time,
      it will try to fulfill all the rules according to the respective weight of each.

   .. note::

      A given boid will try as much as it can to comply to each of the rules it is given,
      but it is more than likely that some rule will take precedence on other in some cases.
      For example, in order to avoid a predator, a boid could probably "forget" about Collision,
      Separate and Flock rules, meaning that "while panicked" it could well run into obstacles,
      e.g. even if instructed not to, most of the time.

In Air
   The current rule affects boids while they are flying.
On Land
   The current rule affects boids while they are not flying.


Goal Rule
---------

Seek goal.

Object
   Specifies the goal object. If not specified, Boid force fields with negative Strength are used as goals.
Predict
   Predict target's movements.


Avoid Rule
----------

Avoid "predators".

Object
   Specifies the object to avoid.
   If not specified, Boid force fields with positive Strength are used as predators.
Predict
   Predict target's movements.
Fear Factor
   Avoid object if danger from it is above this threshold.


Avoid Collision Rule
--------------------

Avoid objects with activated Deflection.

Boids
   Avoid collision with other boids.
Deflectors
   Avoid collision with deflector objects.
Look Ahead
   Time to look ahead in seconds.


Separate Rule
-------------

Boids move away from each other.


Flock Rule
----------

Copy movements of neighboring boids, but avoid each other.


Follow Leader Rule
------------------

Follows a leader object instead of a boid.

Distance
   Distance behind leader to follow.
Line
   Follow the leader in a line.

   Queue Size
      How many boids that are allowed to follow in a line.


Average Speed Rule
------------------

Maintain average velocity.

Speed
   Percentage of maximum speed.
Wander
   How fast velocity's direction is randomized.
Level
   How much velocity's Z component is kept constant.


Fight Rule
----------

Move toward nearby boids.

Fight Distance
   Attack boids at a maximum of this distance.
Flee Distance
   Flee to this distance.


## Fluid

.. _bpy.types.SPHFluidSettings:

*****
Fluid
*****

.. reference::

   :Panel:     :menuselection:`Particle System --> Physics`
   :Type:      Fluid

.. TODO2.8:
   .. figure:: /images/physics_particles_emitter_physics_fluid_panel.png

      Fluid Physics settings.

Fluid particles are similar to Newtonian ones but this time particles are influenced by
internal forces like pressure, surface tension, viscosity, springs, etc.
From liquids to slime, goo to sand and wispy smoke the number of possible use cases is endless.

Blender particle fluids use the SPH techniques to solve the particles fluid equations.
Smoothed-particle hydrodynamics (SPH) is a computational method used for simulating fluid flows.
It has been used in many fields of research, including astrophysics, ballistics, vulcanology,
and oceanography. It is a mesh-free Lagrangian method (where the coordinates move with the fluid),
and the resolution of the method can easily be adjusted with respect to variables such as the density.


Options
=======

Fluid physics share options with :doc:`Newtonian Physics </physics/particles/emitter/physics/newtonian>`.
These are covered on that page.


Fluid Properties
----------------

Stiffness
   How incompressible the fluid is.
Viscosity
   Linear viscosity. Use lower viscosity for thicker fluids.
Buoyancy
   Artificial buoyancy force in negative gravity direction based on pressure differences inside the fluid.


Advanced
--------

.. reference::

   :Panel:     :menuselection:`Particle System --> Physics --> Advanced`

Repulsion Factor
   How strongly the fluid tries to keep from clustering (factor of stiffness).
   Checkbox sets repulsion as a factor of stiffness.
Stiff Viscosity
   Creates viscosity for expanding fluid. Checkbox sets this to be a factor of normal viscosity.
Interaction Radius
   Fluid's interaction radius. Checkbox sets this to be a factor of 4 × *particle size*.
Rest Density
   Density of fluid when at rest. Checkbox sets this to be a factor of default density.


Springs
-------

.. reference::

   :Panel:     :menuselection:`Particle System --> Physics --> Springs`

Force
   Spring force.
Rest Length
   Rest length of springs. Factor of particle radius. Checkbox sets this to be a factor of 2 × *particle size*.

Viscoelastic Springs
   Use viscoelastic springs instead of Hooke's springs.
Elastic Limit
   How much the spring has to be stretched/compressed in order to change its rest length.
Plasticity
   How much the spring rest length can change after the elastic limit is crossed.
Initial Rest Length
   Use initial length as spring rest length instead of 2 × *particle size*.
Frames
   Create springs for this number of frames since particle's birth (0 is always).


## Index


###########
  Physics
###########

.. toctree::
   :maxdepth: 2

   introduction.rst
   newtonian.rst
   keyed.rst
   boids.rst
   fluid.rst


## Introduction


************
Introduction
************

The movement of particles may be controlled in a multitude of ways.
Here we will discuss only the particle physics in the narrower sense, i.e.
the settings in the Physics panel.

Additional ways of moving particles are:

- By soft body animation (only for Hair particle systems).
- By force fields and along curves.
- By lattices.


Common Physics Settings
=======================

Size
   Sets the size of the particles.
Random Size
   Give the particles a random size variation.
Mass
   Specify the mass of the particles.
Multiply Mass with Particle Size
   Causes larger particles to have larger masses.


No Physics
==========

The particles will be given no motion, which makes them belong to no physics system.
At first a physics type that makes the particles to be static could seem a bit strange,
but it can be very useful at times.
None physics make the particles stick to their emitter their whole life time. The initial
velocities here are for example used to give a velocity to particles that are affected
by a harmonic effector with this physics type when the effect of the effector ends.

Moreover, it can be very convenient to have particles at disposal
(whose both Unborn and Died are visible on render)
to groom vegetation and/or ecosystems using *Object* or *Group* types of visualization.


## Keyed

.. _bpy.types.ParticleHairKey:
.. _bpy.types.ParticleKey:
.. _bpy.types.ParticleTarget:

*****
Keyed
*****

.. reference::

   :Panel:     :menuselection:`Particle System --> Physics`
   :Type:      Keyed

The path of Keyed particles is determined between particles of any two (or more) particle systems.
This allows the creation of a chains of systems to create long strands or groovy moving particles.
Basically the particles have no dynamics but are interpolated from one system to the next each frame.

To setup *Keyed* particles you need at least two particle systems in the *Keys* list.


Options
=======

.. TODO2.8:
   .. figure:: /images/physics_particles_emitter_physics_keyed_panel.png
      :align: right

      Keyed Physics settings.

Loops
   Sets the number of times the entire *Keys* list is repeated. Disabled if *Use Timing* is enabled.
Use Timing
   Enabling this option allows you to specify the timing for each key independently,
   using the *Time* and *Duration* options.
   By default, the *Use Timing* option is deactivated, and the particles will pass through all keys
   for a time equal to its lifetime. A shorter lifetime means faster movement.
   The lifetime will be split equally between the keys,
   this may lead to varying particle speeds between the targets.


Relations
=========

.. reference::

   :Panel:     :menuselection:`Particle System --> Physics --> Relations`

Key Targets
   The :ref:`list view <ui-list-view>` of keys (target particle systems).
Object
   The name of a target object for the selected key. If empty it uses the current particle system.
System
   Index of particle system on the target object.
Time
   The time (frame number) at which the particles will be at the position of the selected system.
   Note also that the *Start* frame of the Keyed system adds an offset to this time.
Duration
   How long (in frames) the particles stay on this system before they start moving to the next one.


## Newtonian


*********
Newtonian
*********

.. reference::

   :Panel:     :menuselection:`Particle System --> Physics`
   :Type:      Newtonian

The particles will move according to classical (Newtonian) mechanics.
Particles start their life with the specified initial velocities and angular velocities,
and move according to external forces.
The response to environment and to forces is computed differently,
according to the given integrator chosen by the animator.

.. TODO2.8:
   .. figure:: /images/physics_particles_emitter_physics_newtonian_panel.png

      Newtonian Physics settings.


Forces
======

.. reference::

   :Panel:     :menuselection:`Particle System --> Physics --> Forces`

Brownian
   Specify the amount of Brownian motion.
   Brownian motion adds random motion to the particles based on a Brownian noise field.
   This is nice to simulate small, random wind forces.
Drag
   A force that reduces particle velocity in relation to its speed and size
   (useful in order to simulate air drag or water drag).
Damp
   Reduces particle velocity (deceleration, friction, dampening).


Integration
===========

.. reference::

   :Panel:     :menuselection:`Particle System --> Physics --> Integration`

Integrators are a set of mathematical methods available to calculate the movement of particles.
The following guidelines will help to choose a proper integrator,
according to the behavior aimed at by the animator.

Integration
   Euler
      Also known as "Forward Euler". Simplest integrator.
      Very fast but also with less exact results.
      If no dampening is used, particles get more and more energy over time.
      For example, bouncing particles will bounce higher and higher each time.
      Should not be confused with "Backward Euler" (not implemented) which has the opposite feature,
      the energy decrease over time, even with no dampening.
      Use this integrator for short simulations or simulations with a lot of
      dampening where speedy calculations are more important than accuracy.
   Verlet
      Very fast and stable integrator, energy is conserved over time with very little numerical dissipation.
   Midpoint
      Also known as "2nd order Runge-Kutta". Slower than Euler but much more stable.
      If the acceleration is constant (no drag for example), it is energy conservative.
      It should be noted that in example of the bouncing particles,
      the particles might bounce higher than they started once in a while, but this is not a trend.
      This integrator is a generally good integrator for use in most cases.
   RK4
      Short for "4th order Runge-Kutta". Similar to Midpoint but slower and in most cases more accurate.
      It is energy conservative even if the acceleration is not constant.
      Only needed in complex simulations where Midpoint is found not to be accurate enough.
Timestep
   The amount of simulation time (in seconds) that passes during each frame.
Subframes
   The number of simulation steps per frame.
   Subframes to simulate for improved stability and finer granularity in simulations.
   Use higher values for faster-moving particles.

The following options are only available for Fluid type physics:

Adaptive
   Automatically set the number of subframes.

   Threshold
      A tolerance value that allows the number of subframes to vary.
      It sets the relative distance a particle can move before requiring more subframes.

      The number of steps per frame will be at least Subframes + 1.
      More subframes may be simulated if the fluid becomes turbulent, according to the Threshold.


Deflection
==========

.. reference::

   :Panel:     :menuselection:`Particle System --> Physics --> Deflection`

Size Deflect
   Use the particle size in deflections.
Die on Hit
   Kill particle when it hits a deflector object.
Collision Collection
   If set, particles collide with objects from the collection.


## Children


********
Children
********

.. reference::

   :Panel:     :menuselection:`Particle System --> Children`

See :doc:`Children </physics/particles/emitter/children>`.


## Display


****************
Viewport Display
****************

.. reference::

   :Panel:     :menuselection:`Particle System --> Display`

Rendered
   Display hair as curves.
Path
   Display just the end points of the hairs.

Steps
   The number of segments (control points minus 1) of the hair strand.
   In between the control points the segments are interpolated. The number of control points is important:

   - For the soft body animation, because the control points are animated like vertices,
     so more control points mean longer calculation times.
   - For the interactive editing, because you can only move the control points
     (but you may recalculate the number of control points in *Particle Edit Mode*).

   .. hint:: Segments

      Ten Segments should be sufficient even for very long hair,
      five Segments are enough for shorter hair, and two or three segments should be enough for short fur.


## Dynamics

.. _hair-dynamics:

*************
Hair Dynamics
*************

.. reference::

   :Panel:     :menuselection:`Particle System --> Hair Dynamics`

Hair particles can have dynamic properties using physics.
To enable hair physics, click the checkbox beside *Hair Dynamics*.

Quality Steps
   Quality of the simulation in steps per frame (higher is better quality but slower).

Pin Goal Strength
   Spring stiffness of the vertex target position.

.. warning::

   If you use motion blur in your animation,
   you will need to bake one extra frame past the last frame which you will be rendering.


Collisions
==========

Quality
   A general setting for how fine and good a simulation you wish.
   Higher numbers take more time but ensure less tears and penetrations through the hair.
Distance
   The distance another object must get to the hair for
   the simulation to repel the hair out of the way.
   Smaller values might cause errors but provide some speed-up while
   larger will give unrealistic results if too large and can be slow.
   It is best to find a good in between value.
Impulse Clamping
   Prevents explosions in tight and complicated collision situations
   by restricting the amount of movement after a collision.
Collision Collection
   Only objects that are a part of this :doc:`Collection </scene_layout/collections/index>`
   can collide with the hair. Note that these objects must also have Collision physics enabled.


Structure
=========

.. reference::

   :Panel:     :menuselection:`Particle System --> Hair Dynamics --> Structure`

Vertex Mass
   Value for the mass of the hair.
Stiffness
   Controls the bending stiffness of the hair strands.

   Random
      Random stiffness of hair.

Damping
   Damping of bending motion.


Volume
======

.. reference::

   :Panel:     :menuselection:`Particle System --> Hair Dynamics --> Volume`

Some phenomena of real-world hair can be simulated more efficiently using a volumetric model instead
of the basic geometric strand model. This means constructing a regular grid such as those used in
fluid simulations and interpolating hair properties between the grid cells.

Air Drag
   Controls how thick the air is around the hair causing the hair to flow slower.
Internal Friction
   Amount of friction between individual hairs.
Voxel Grid Cell Size
   Size of the voxel grid cells for interaction effects.

Density Target
   Maximum density of the hair.
Density Strength
   The influence that the *Density Target* has on the simulation.


## Emission


********
Emission
********

.. reference::

   :Panel:     :menuselection:`Particle System --> Emission`

.. TODO2.8:
   .. figure:: /images/physics_particles_hair_emission_settings.png

      Hair particle system settings.

Number
   Sets the amount of hair strands. Use as few particles as possible
   (especially if you plan to use soft body animation later),
   but still enough to cover the surface and have good control.
   A few thousand particles is generally enough for a regular haircut.
   The hair will be made denser later on using
   :doc:`/physics/particles/emitter/children`.
Hair Length
   Controls the length of the hair.

.. seealso::

   Emitter particles :doc:`Emission panel </physics/particles/emitter/emission>`


## Index

.. _particles-hair-index:

########
  Hair
########

This page is about the end of life hair system.
Read about the new hair system on the :doc:`Hair Nodes page </modeling/geometry_nodes/hair/index>`.

.. toctree::
   :maxdepth: 2

   introduction.rst
   emission.rst
   dynamics.rst
   render.rst
   shape.rst
   children
   display.rst


## Introduction


************
Introduction
************

Hair type particle system can be used for strand-like objects,
such as hair, fur, grass, quills, etc.

.. figure:: /images/physics_particles_hair_introduction_example.jpg

   Particle hair systems example. Used for the grass and fur.


Growing
=======

The first step is to create the hair, specifying the amount of hair strands and their lengths.

The complete path of the particles is calculated in advance.
So everything a particle does a hair may do also.
A hair is as long as the particle path would be for a particle with a lifetime of 100 frames.
Instead of rendering every frame of the particle animation point by point there are calculated
control points with an interpolation, the segments.


Styling
=======

The next step is to style the hair. You can change the look of base hairs by changing
the :doc:`Physics Settings </physics/particles/emitter/physics/index>`.

A more advanced way of changing the hair appearance is to use
:doc:`Children </physics/particles/emitter/children>`.
This adds child hairs to the original ones, and has settings for giving them different types of shapes.

You can also interactively style hairs in :doc:`Particle Edit Mode </physics/particles/mode>`.
In this mode, the particle settings become disabled, and you can comb, trim, lengthen, etc. the hair curves.


Animating
=========

Hair can be made dynamic using the cloth solver.
This is covered in the :ref:`Hair Dynamics <hair-dynamics>` page.


Rendering
=========

With Cycles you can render hair with specialized hair BSDFs
:doc:`/render/shader_nodes/shader/hair` or
:doc:`/render/shader_nodes/shader/hair_principled`.

Hair can also be used as a basis for
the :doc:`Particle Instance Modifier </modeling/modifiers/physics/particle_instance>`,
which allows you to have a mesh be deformed along the curves,
which is useful for thicker strands, or things like grass, or feathers, which may have a more specific look.


## Render


******
Render
******

.. reference::

   :Panel:     :menuselection:`Particle System --> Render`

Hair can be rendered as a Path, Object, or Group.
See :doc:`Particle Visualization </physics/particles/emitter/render>` for descriptions and
the :doc:`Hair Shape </physics/particles/hair/shape>` settings.

.. seealso::

   `Blender Hair Basics <https://www.youtube.com/watch?v=kpLaxqemFU0>`__,
   a thorough overview of all of the hair particle settings.


## Shape


*****
Shape
*****

.. reference::

   :Panel:     :menuselection:`Particle System --> Hair Shape`

These settings control the shape of hair curves for rendering.

Strand Shape
   A shape parameter that controls the transition in thickness between the root and tip.
   Negative values make the primitive rounded more towards the top,
   the value of zero makes the primitive linear,
   and positive values make the primitive rounded more towards the bottom.

Diameter Root
   Multiplier of the hair width at the root.
Tip
   Multiplier of the hair width at the tip.
Radius Scale
   Multiplier for the *Root* and *Tip* values. This can be used to change the thickness of the hair.

   .. Particle width scaling relative to the object scale.

Close Tip
   Sets the thickness at the tip to zero, even when using a nonzero tip multiplier.


## Index

.. _rigid-body-index:
.. _bpy.types.RigidBodyObject:
.. _bpy.ops.rigidbody:

##############
  Rigid Body
##############

.. toctree::
   :maxdepth: 2

   introduction.rst
   properties/index.rst
   world.rst
   constraints/index.rst
   tips.rst


## Introduction


************
Introduction
************

The rigid body simulation can be used to simulate the motion of solid objects.
It affects the position and orientation of objects and does not deform them.

Unlike the other simulations in Blender, the rigid body simulation works closer with the animation system.
This means that rigid bodies can be used like regular objects and be part of parent-child relationships,
animation constraints and drivers.


Creating a Rigid Body
=====================

.. reference::

   :Mode:      All Modes
   :Panel:     :menuselection:`Properties --> Physics --> Rigid Body`
   :Menu:      :menuselection:`Object --> Rigid Body`

Only mesh objects can be part of a rigid body simulation.
To create rigid bodies, either click on the *Rigid Body* button in the *Physics* tab of
the Properties or use *Add Active*/*Add Passive* in the :menuselection:`Object --> Rigid Body` menu.

There are two types of rigid bodies: active and passive. *Active* bodies are dynamically simulated, while *passive*
bodies remain static. Both types can be driven by the animation system when using the *Animated* option.

During the simulation,
the rigid body system will override the position and orientation of dynamic rigid body objects.
Note however, that the location and rotation of the objects are not changed,
so the rigid body simulation acts similar to a constraint.
To apply the rigid body transformations you can use
the *Apply Object Transform* operator.

The scale of the rigid body object also influences the simulation, but is always controlled by the animation system.

Rigid body physics on the object can be *removed* with the *Rigid Body* button
in the *Physics* tab in the Properties or in the :menuselection:`Object --> Rigid Body` menu.


Working with Rigid Bodies
=========================

Several object operators exist for working with rigid bodies,
these operators can be found in the :doc:`/scene_layout/object/editing/rigid_body` object menu.
These operators include functions to add/remove rigid bodies, modify their properties,
and add :doc:`Rigid Body Constraints </physics/rigid_body/constraints/index>`.


## Tips


****
Tips
****

As with all physics-enabled objects, pay close attention to the *Animated* checkbox
in the *Rigid Body* panel of the *Physics* tab in the Properties.
A common mistake is to use keyframe animation on a *Passive* physics
object without checking the *Animated* box. The object will move,
but the physics engine will behave as if the *Passive* is still in its starting place, leading to disappointment.


Animation
=========

The most common trick is to
:term:`Keyframe` animate the location or rotation of an *Active* physics object as well as
the *Animated* checkbox.
When the curve on the *Animated* property switches to disabled, the physics engine takes over
using the object's last known location, rotation and velocities.

Animating the strengths of various other parameters
(a :doc:`Motor's </physics/rigid_body/constraints/types/motor>` Target Velocity,
a :doc:`Hinge's </physics/rigid_body/constraints/types/hinge>` limits, etc.)
can be used to accomplish a wide variety of interesting results.

Enabling a constraint during the physics simulation often has dramatic results
as the physics engine tries to bring into alignment two objects which are often dramatically out of alignment.
It is very common for the affected objects to build up enough kinetic energy to bounce themselves out of camera.

Rigid body dynamics can be baked to normal keyframes with *Bake To Keyframes*
in the :menuselection:`Object --> Rigid Body` menu.


Simulation Stability
====================

The simplest way of improving simulation stability is to increase the steps per second.
However, care has to be taken since making too many steps can cause problems and
make the simulation even less stable
(if you need more than 1000 steps, you should look at other ways to improve stability).

Increasing the number of solver iterations helps making constraints stronger and
also improves object stacking stability.

It is best to avoid small objects, as they are currently unstable.
Ideally, objects should be at least 20 cm in diameter.
If it is still necessary, setting the collision margin to 0,
while generally not recommended, can help making small object behave more naturally.

When objects are small and/or move very fast, they can pass through each other.
Besides what is mentioned above it's also good to avoid using mesh shapes in this case.
Mesh shapes consist of individual triangles and therefore do not
really have any thickness, so objects can pass through more easily.
You can give them some thickness by increasing the collision margin.


Combining Rigid Bodies with Other Simulations
=============================================

Since the rigid body simulation is part of the animation system,
it can influence other simulations just like the animation system can.

In order for this to work, the rigid body object needs to have a Collision Modifier.
Simply click on *Collision* in the *Physics* tab.


Scaling Rigid Bodies
====================

Rigid body objects can be scaled, also during the simulation.
This work well in most cases, but can sometimes cause problems.

If dynamic scaling is not needed, rigid body objects should have the scale applied by
using the *Apply Scale* tool :kbd:`Ctrl-A`.


## World

.. _bpy.types.RigidBodyWorld:
.. _bpy.ops.rigidbody.world:

****************
Rigid Body World
****************

.. reference::

   :Panel:     :menuselection:`Scene --> Rigid Body World`

The *Rigid Body World* is a group of rigid body objects,
which holds settings that apply to all rigid bodies in this simulation.

When you add rigid body physics to an object,
primary there is created a group of objects with default "RigidBodyWorld" name.
Rigid body objects automatically are added to this group when you add rigid body physics for them.
You can create several Rigid Body World :doc:`Collections </scene_layout/collections/collections>`
and allocate the rigid body objects with the :ref:`Collections panel <scene-layout_collections_collections_panel>`.

Rigid body objects and constraints are only taken into account by the simulation
if they are in the collection specified in the *Collection* field of the *Rigid Body World* panel in the *Scene* tab.


Settings
========

Rigid Body World
   Enable/disable evaluation of the rigid body simulation based on the rigid body objects
   participating in the specified group of Rigid Body World.
Remove Rigid Body World
   Remove rigid body simulation from the current scene.
Collection
   Containing rigid body objects participating in this simulation.
Constraints
   Containing rigid body object constraints participating in the simulation.

Simulation quality and timing settings:

Speed
   Can be used to speed up/slow down the simulation.
Split Impulse
   Enable/disable reducing extra velocity that can build up when objects collide
   (lowers the simulation stability a little so use only when necessary).
   Limits the force with which objects are separated on collision, generally produces nicer
   results, but makes the simulation less stable (especially when stacking many objects).
Substeps Per Frame
   Number of simulation steps taken per frame (higher values are more accurate but slower).
   This only influences the accuracy and not the speed of the simulation.
Solver Iterations
   Amount of constraint solver iterations made per simulation step (higher values are more accurate but slower).
   Increasing this makes constraints and object stacking more stable.


Rigid Body Cache
================

.. reference::

   :Panel:     :menuselection:`Scene --> Rigid Body World --> Cache`

The *Cache* subpanel specifies the frame range in which the simulation is active.
Can be used to bake the simulation.

Start/End
   First and last frame of the simulation.
Bake
   Calculates the simulation and protects the cache. You need to be in *Object Mode* to bake.

   Free Bake
      Active after the baking of simulation. Clears the baked cache.

Calculate to Frame
   Bake physics to current frame.
Current Cache to Bake
   Bake from Cache.
Bake All Dynamics
   Bake all physics.
Free All Bakes
   Free all baked caches of all objects in the current scene.
Update All to Frame
   Update cache to current frame.

If you have not saved the blend-file, the cache is created in memory,
so save your file first or the cache may be lost.


Rigid Body Field Weights
========================

.. reference::

   :Panel:     :menuselection:`Scene --> Rigid Body World --> Field Weights`

As other physics dynamics systems, rigid body simulation are also influenced by external force effectors.


## Index

.. _rigid-body-constraints-index:
.. _bpy.types.RigidBodyConstraint:

##########################
  Rigid Body Constraints
##########################

.. toctree::
   :maxdepth: 2

   introduction.rst
   types/index.rst


## Introduction

.. index:: Constraint; Rigid Body Constraints
.. index:: Rigid Body Constraints

************
Introduction
************

:term:`Constraints <Constraint>` (also known as joints) for rigid bodies connect two rigid bodies.
The physics constraints are meant to be attached to an :term:`Empty` object.
The constraint then has fields which can be pointed at the two physics-enabled object
which will be bound by the constraint.
The empty object provides a location and axis for the constraint distinct from the two constrained objects.
The location of the entity hosting the physics constraint marks a location and
set of axes on each of the two constrained objects.
These two anchor points are calculated at the beginning of the animation and their position and
orientation remain fixed in the *local* coordinate system of the object for the duration of the animation.
The objects can move far from the constraint object, but the constraint anchor moves with the object.
If this feature seems limiting, consider using multiple objects with a non-physics *Child of* constraint and
animate the relative location of the child.


Connect
=======

The quickest way to constrain two objects is to select both and
click the *Connect* button in :menuselection:`Object --> Rigid Body`.
This creates a new empty object (named "Constraint") with a physics constraint
already attached and pointing at the two selected objects.


Physics Menu
============

Also you can create *Rigid Body Constraint* on one of the two constrained objects with
*Rigid Body Constraint* button of the *Physics* tab in the Properties.
This constraint is dependent on the object location and rotation on which it was created.
This way, there are no empty object created for the constraint.
The role of the empty object is put on this object.
The constrained object can be then be set as a *Passive* type for better driving of the constraint.

Additional parameters appear in the *Rigid Body Constraint* panel of the *Physics* tab in the Properties
for the selected empty object or the one of the two constrained objects with the created constraint.


Common Options
==============

.. reference::

   :Panel:     :menuselection:`Physics --> Rigid Body Constraint`


Settings
--------

.. _bpy.types.RigidBodyConstraint.enabled:

Enabled
   Specifies whether the constraint is active during the simulation.

.. _RigidBodyConstraint.disable_collisions:

Disable Collisions
   Allows constrained objects to pass through one another.

.. _bpy.types.RigidBodyConstraint.RigidBodyConstraint.use_breaking:

Breakable
   Allows constraint to break during simulation. Disabled for the *Motor* constraint.
   This can be used to simulate destruction.

.. _bpy.types.RigidBodyConstraint.breaking_threshold:

Threshold
   Impulse strength that needs to be reached before the constraint breaks.


.. _bpy.types.RigidBodyConstraint.use_limit:
.. _bpy.types.RigidBodyConstraint.limit:

Limits
------

By using limits you can constrain objects even more by specifying a translation/rotation range on/around
respectively one axis (see below for each one individually). To lock one axis, set both limits to 0.


.. _bpy.types.RigidBodyConstraint.object1:
.. _bpy.types.RigidBodyConstraint.object2:

Objects
-------

First
   First object to be constrained.
Second
   Second object to be constrained.


.. _bpy.types.RigidBodyConstraint.use_override_solver_iterations:
.. _bpy.types.RigidBodyConstraint.solver_iterations:

Override Iterations
-------------------

Allows making constraints stronger (more iterations) or weaker (less iterations)
than specified in the rigid body world.

Iterations
   Number of constraint solver iterations made per simulation step for this constraint.


## Fixed

.. index:: Rigid Body Constraints; Fixed Constraint

****************
Fixed Constraint
****************

.. reference::

   :Panel:     :menuselection:`Physics --> Rigid Body Constraint`
   :Type:      Fixed

This constraint cause the two objects to move as one.
Since the physics system does have a tiny bit of slop in it,
the objects do not move as rigidly as they would if they were part of the same mesh.

.. TODO2.8:

   .. figure:: /images/physics_rigid-body_constraints_types_fixed_panel-example.png

      *Fixed* constraint options.


## Generic

.. index:: Rigid Body Constraints; Generic Constraint

******************
Generic Constraint
******************

.. reference::

   :Panel:     :menuselection:`Physics --> Rigid Body Constraint`
   :Type:      Generic

The generic constraint has a lot of available parameters.

The X, Y, and Z axis constraints can be used to limit the amount of translation between the objects.
Clamping the min/max to zero has the same effect as the Point constraint.

Clamping the relative rotation to zero keeps the objects in alignment.
Combining an absolute rotation and translation clamp would behave much like the Fixed constraint.

Using a nonzero spread on any parameter allows it to oscillate
in that range throughout the course of the simulation.


Options
=======

Limits
   Angular
     X Angle, Y Angle, Z Angle
         Enables/disables limit rotation around X, Y or Z axis respectively.

         Lower
            Lower limit of rotation for X, Y or Z axis respectively.
         Upper
            Upper limit of rotation for X, Y or Z axis respectively.
   Linear
      X Axis, Y Axis, Z Axis
         Enables/disables limit translation on X, Y or Z axis respectively.

         Lower
            Lower limit of translation for X, Y or Z axis respectively.
         Upper
            Upper limit of translation for X, Y or Z axis respectively.


## Generic Spring

.. index:: Rigid Body Constraints; Generic Spring Constraint

*************************
Generic Spring Constraint
*************************

.. reference::

   :Panel:     :menuselection:`Physics --> Rigid Body Constraint`
   :Type:      Generic Spring

The generic spring constraint adds some spring parameters for the X/Y/Z axes
to all the options available on the Generic constraint.
Using the spring alone allows the objects to bounce around as if attached
with a spring anchored at the constraint object.
This is usually a little too much freedom,
so most applications will benefit from enabling translation or rotation constraints.

If the damping on the springs is set to 1, then the spring forces are prevented from realigning the anchor points,
leading to strange behavior. If your springs are acting weird, check the damping.


Options
=======

.. TODO2.8:
   .. figure:: /images/physics_rigid-body_constraints_types_generic-spring_panel.png
      :align: right

      *Generic Spring* constraint options.

Limits
   X/Y/Z Axis
      Enables/disables limit translation on X, Y or Z axis respectively.

      Lower
         Lower limit of translation for X, Y or Z axis respectively.
      Upper
         Upper limit of translation for X, Y or Z axis respectively.
   X/Y/Z Angle
      Enables/disables limit rotation around the X, Y or Z axis respectively.

      Lower
         Lower limit of rotation for X, Y or Z axis respectively.
      Upper
         Upper limit of rotation for X, Y or Z axis respectively.

Springs
   X/Y/Z Axis
      Enables/disables springs translation on X, Y or Z axis respectively.

      Stiffness
         Spring Stiffness of the translation on X, Y or Z axis respectively. Specifies how "bendy" the spring is.
      Damping
         Spring Damping of the translation on X, Y or Z axis respectively. Amount of damping the spring has.
   X/Y/Z Angle
      Enables/disables springs rotation around the X, Y or Z axis respectively.

      Stiffness
         Spring Stiffness of the rotation around the X, Y or Z axis respectively.
         Specifies how "bendy" the spring is.
      Damping
         Spring Damping of the rotation around the X, Y or Z axis respectively. Amount of damping the spring has.


## Hinge

.. index:: Rigid Body Constraints; Hinge Constraint

****************
Hinge Constraint
****************

.. reference::

   :Panel:     :menuselection:`Physics --> Rigid Body Constraint`
   :Type:      Hinge

The hinge permits one degree of freedom between two objects. Translation is completely constrained.
Rotation is permitted about the Z axis of the object hosting the Physics constraint
(usually an :term:`Empty`, distinct from the two objects that are being linked).
Adjusting the position and rotation of the object hosting the constraint allows you to
control the anchor and axis of the hinge.

The Hinge is the only single-axis rotational constraint that uses the Z axis instead of the X axis.
If something is wrong with your hinge, check your other constraints to see if this might be the problem.

.. TODO2.8:
   .. figure:: /images/physics_rigid-body_constraints_types_hinge_panel-example.png

      *Hinge* constraint options.


Options
=======

Limits
   Z Angle
      Enables/disables limit rotation around Z axis.

      Lower
         Lower limit of Z axis rotation.
      Upper
         Upper limit of Z axis rotation.


## Index

.. _rigid-body-constraints-types-index:

#########
  Types
#########

.. toctree::
   :maxdepth: 2

   fixed.rst
   point.rst
   hinge.rst
   slider.rst
   piston.rst
   generic.rst
   generic_spring.rst
   motor.rst


## Motor

.. index:: Rigid Body Constraints; Motor Constraint

****************
Motor Constraint
****************

.. reference::

   :Panel:     :menuselection:`Physics --> Rigid Body Constraint`
   :Type:      Motor

The motor constraint causes translation and/or rotation between two entities.
It can drive two objects apart or together.
It can drive simple rotation, or rotation and translation
(although it will not be constrained like a screw since the translation
can be blocked by other physics without preventing rotation).

The rotation axis is the X axis of the object hosting the constraint.
This is in contrast with the Hinge which uses the Z axis.
Since the Motor is vulnerable to confusing perturbations without a matching Hinge constraint,
special care must be taken to align the axes.
Without proper alignment, the motor will appear to have no effect
(because the hinge is preventing the motion of the motor).

.. TODO2.8:
   .. figure:: /images/physics_rigid-body_constraints_types_motor_panel-example.png

      *Motor* constraint options.


Options
=======

Linear Motor/Angular Motor
   Enable
      Enable linear or angular motor respectively.

      Target Velocity
         Target linear or angular motor velocity respectively.
      Max Impulse
         Maximum linear or angular motor impulse respectively.


## Piston

.. index:: Rigid Body Constraints; Piston Constraint

*****************
Piston Constraint
*****************

.. reference::

   :Panel:     :menuselection:`Physics --> Rigid Body Constraint`
   :Type:      Piston

A piston permits translation along the X axis of the constraint object.
It also allows rotation around the X axis of the constraint object.
It is like a combination of the freedoms of a slider with the freedoms of a hinge
(neither of which is very free alone).


Options
=======

Limits
   X Axis
      Enables/disables limit translation around X axis.

      Lower
         Lower limit of X axis translation.
      Upper
         Upper limit of X axis translation.
   X Angle
      Enables/disables limit rotation around X axis.

      Lower
         Lower limit of X axis rotation.
      Upper
         Upper limit of X axis rotation.


## Point

.. index:: Rigid Body Constraints; Point Constraint

****************
Point Constraint
****************

.. reference::

   :Panel:     :menuselection:`Physics --> Rigid Body Constraint`
   :Type:      Point

The objects are linked by a point bearing allowing any kind of rotation around the location of the constraint object,
but no relative translation is permitted. The physics engine will do its best to make sure that the two points
designated by the constraint object on the two constrained objects are coincident.

.. TODO2.8:

   .. figure:: /images/physics_rigid-body_constraints_types_point_panel-example.png

      *Point* constraint options.


## Slider

.. index:: Rigid Body Constraints; Slider Constraint

*****************
Slider Constraint
*****************

.. reference::

   :Panel:     :menuselection:`Physics --> Rigid Body Constraint`
   :Type:      Slider

The Slider constraint allows relative translation along the X axis of the constraint object,
but permits no relative rotation, or relative translation along other axes.


Options
=======

Limits
   X Axis
      Enables/disables limit translation around X axis.

      Lower
         Lower limit of X axis translation.
      Upper
         Upper limit of X axis translation.


## Collisions


**********
Collisions
**********

.. reference::

   :Panel:     :menuselection:`Physics --> Rigid Body --> Collisions`

.. TODO2.8:
   .. figure:: /images/physics_rigid-body_properties_collisions_panel.png

      Rigid Body Collisions panel.

.. _bpy.types.RigidBodyObject.collision_shape:

Shape
   Determines the collision shape of the object;
   these can be broken into two categories: primitive shapes and mesh based shapes.

   Primitive shapes (*Box*, *Sphere*, *Capsule*, *Cylinder*, and *Cone*)
   are best in terms of memory and performance but do not
   necessarily reflect the actual shape of the object.
   They are calculated based on the object's bounding box.
   The center of gravity is always in the geometric center of the shape.
   Primitive shapes can be shown in the 3D Viewport by enabling :ref:`Bounds <bpy.types.Object.show_bounds>`.

   Mesh based shapes (*Convex Hull* and *Mesh*) are calculated based on the geometry of the object
   so they are a better representation of the object.
   The center of gravity for these shapes is the object origin.

   :Box:
      Box-like shapes (e.g. cubes), including planes (e.g. ground planes).
      The size per axis is calculated from the bounding box.
   :Sphere:
      Sphere-like shapes. The radius is the largest axis of the bounding box.
   :Capsule:
      This points up the Z axis.
   :Cylinder:
      This points up the Z axis.
      The height is taken from the Z axis, while the radius is the larger of the X or Y axes.
   :Cone:
      This points up the Z axis.
      The height is taken from the Z axis, while the radius is the larger of the X or Y axes.
   :Convex Hull:
      A mesh-like surface encompassing (e.g. shrink-wrapped over) all vertices (best results with fewer vertices).
      A convex approximation of the object, which has good performance and stability.
   :Mesh:
      :term:`Mesh` consisting of triangles only, allowing for more detailed interactions than convex hulls.
      Allows simulating concave objects, but is rather slow and unstable.
   :Compound Parent:
      Takes the collision shapes from the object's :doc:`children </scene_layout/object/editing/parent>`
      and combines them. This makes it possible to create concave shapes from primitive shapes.
      This usually results in a faster simulation than the *Mesh* collision shape
      while also being generally more stable.

.. _bpy.types.RigidBodyObject.mesh_source:

Source
   Source of the mesh used to create the collision shape.

   :Base:
      The base mesh of the object.
   :Deform:
      Includes any deformations added to the mesh (shape keys, deform modifiers).
   :Final:
      Includes all deformations and modifiers.

.. _bpy.types.RigidBodyObject.use_deform:

Deforming
   Mesh shapes can deform during simulation.


Surface Response
================

.. _bpy.types.RigidBodyObject.friction:

Friction
   Resistance of object to movement. Specifies how much velocity is lost when objects collide with each other.

.. _bpy.types.RigidBodyObject.restitution:

Bounciness
   Tendency of object to bounce after colliding with another (0 to 1) (rigid to perfectly elastic).
   Specifies how much objects can bounce after collisions.


Sensitivity
===========

The collision margin is used to improve the performance and stability of rigid bodies.
Depending on the shape, it behaves differently: some shapes embed it,
while others have a visible gap around them.

The margin is *embedded* for these shapes:

- Sphere
- Box
- Capsule
- Cylinder
- Convex Hull: Only allows for uniform scale when embedded.

The margin is *not embedded* for these shapes:

- Cone
- Active Triangle Mesh
- Passive Triangle Mesh: Can be set to 0 most of the time.

.. _bpy.types.RigidBodyObject.collision_margin:

Margin
   Threshold of distance near the surface where collisions are still considered (best results when nonzero).


.. _bpy.types.RigidBodyObject.collision_collections:

Collections
===========

Allows rigid body collisions allocate on different groups (maximum 20).


## Dynamics


********
Dynamics
********

.. reference::

   :Panel:     :menuselection:`Physics --> Rigid Body --> Dynamics`

.. TODO2.8:
   .. figure:: /images/physics_rigid-body_properties_dynamics_panel.png

      Rigid Body Dynamics panel.

Used to control the physics of the rigid body simulation.
This panel is available only for *Active* type of rigid bodies.

Damping Translation
   Amount of linear velocity that is lost over time.

Rotation
   Amount of angular velocity that is lost over time.


Deactivation
============

Enable deactivation of resting rigid bodies. Allows the object to be deactivated during the simulation
(improves the performance and stability, but can cause glitches).

Start Deactivated
   The rigid body starts deactivated. It will be activated when in proximity of
   moving active rigid body objects. The proximity check uses the object's
   bounding box to determine if a moving object is close enough to activate it.

Linear Velocity
   Specifies the linear deactivation velocity below which the rigid body
   is deactivated and the simulation stops simulating the object.

Angular Velocity
   Specifies the angular deactivation velocity below which the rigid body
   is deactivated and the simulation stops simulating the object.


## Index


##############
  Properties
##############

.. reference::

   :Panel:     :menuselection:`Physics --> Rigid Body`

Type
   Role of the rigid body in the simulation.

   :Active:
      The object is dynamic and is directly controlled by simulation results.
   :Passive:
      The object remains static and is directly controlled by animation system,
      thus does not have :doc:`/physics/rigid_body/properties/dynamics` properties.

.. toctree::
   :maxdepth: 2

   settings.rst
   collisions.rst
   dynamics.rst


## Settings


********
Settings
********

.. reference::

   :Panel:     :menuselection:`Physics --> Rigid Body --> Settings`

.. TODO2.8:
   .. figure:: /images/physics_rigid-body_properties_settings_panel.png

      Default rigid body panel.

.. _bpy.types.RigidBodyObject.mass:

Mass
   Specifies how heavy the object is and "weights" irrespective of gravity.

   .. tip::

      There are predefined mass presets available with the :ref:`bpy.ops.rigidbody.mass_calculate` operator.

.. _bpy.types.RigidBodyObject.enabled:

Dynamic
   Enables/disables rigid body simulation for the object.

.. _bpy.types.RigidBodyObject.kinematic:

Animated
   Allows the rigid body to additionally be controlled by the animation system.


## Collision


*********
Collision
*********

There are two different collision types that you may use:
collision between different objects and internal collision.
We should set one thing straight from the start --
the primary targets of the collision calculation are the vertices of a soft body.
So if you have too few vertices too few collision takes place.
Secondarily, you can use edges and faces to improve the collision calculation.


Collisions with Other Objects
=============================

For a soft body to collide with another object there are a few prerequisites:

- If *Collision Collection* is set, the object must belong to the collection.
- The collision object has to be a mesh object.
- You have to activate the *Collision* in the *Physics* tab for the collision object.
  The collision object may also be a soft body.


Examples
--------

A soft body cube colliding with a plane (Fig. :ref:`fig-softbody-collision-plane1`)
works pretty well, but a soft body plane falls right through a cube
that it is supposed to collide with (Fig. :ref:`fig-softbody-collision-plane2`).

.. list-table::

   * - .. _fig-softbody-collision-plane1:

       .. figure:: /images/physics_soft-body_collision_cube-plane-1.png

          A soft body cube colliding with a plane.

     - .. _fig-softbody-collision-plane2:

       .. figure:: /images/physics_soft-body_collision_cube-plane-2.png

          A soft body plane colliding with a cube, so no interaction at all.

Why is that? Because the default method of calculation only checks to see if the four vertices
of the soft body plane collides with the cube as the plane is pulled down by gravity.
You can activate *Collision: Face* (in the *Soft Body Edges* panel) to enable collision between
the face of the plane and the object instead, but this type of calculation takes much longer.

Let us have a closer look at the collision calculation, so you can get an idea of how we might optimize it.


Calculating Collisions
----------------------

Soft body simulations are by default done on a per-vertex basis. If the vertices of the soft body
do not collide with the collision object, there will be no interaction between the two objects.

In the video below, you can see the vertices colliding with a plane.
If a vertex penetrates the zone between *Outer* and *Inner*, it is repulsed by a force in
the direction of the face normal. The position that a vertex finally ends up in is dependent
on the forces that act upon it. In the example (the first vertex on the left in the video below)
gravity and the repulsion force of the face balance out.
The speed at which the vertex is pulled out of the collision zone is influenced by the *Choke* parameter
in the :ref:`Soft Body Solver settings <physics-softbody-settings-solver>`.

.. peertube:: fe40b174-484d-4715-82ac-70e10fa5bba5

.. seealso::

   Download the `blend-file <https://archive.blender.org/wiki/2015/uploads/8/8d/CollidingVertices.blend>`__.

Now let's see what happens if we make vertices heavier and let them travel at a faster speed.
In the video above, you can see vertices traveling at different speeds.
The two on the far right (fifth and sixth) are traveling so fast that they pass right through
the collision zone (this is because of the default solver precision, which we can fix later).
You will notice that the fourth vertex also travels quite fast and because it is heavier
it breaches the inner zone. The first three vertices collide correctly.

You can set up your collision so that edges and even faces are included in the collision calculation
in the *Soft Body Edges* panel with the Collision *Face* and *Edge* options.
The collision is then calculated differently. It is checked whether the edge or face
intersects with the collision object, the collision zones are not used.


Good Collisions
---------------

If the collision you have set up is not behaving properly, you can try the following:

- The soft body object must have more subdivisions than the collision object.
  Add loop cuts to the soft body object in strategic areas that
  you know are most likely to be involved in a collision.
- Check the direction of the face normals.
- If the collision object has sharp spikes, they might penetrate the soft body.
- The resolution of the solver must match the speed at which soft body vertices are traveling.
  Lower the parameter *Error Limit* and carefully increase *Min Step*.
- *Outer* and *Inner* should be large enough, but zones of opposite faces should not overlap,
  or you have forces in opposite directions.
- If you use strong forces you should use large zones.
- Set *Choke* to a high enough value (all the way up if necessary) if you have difficulties with repelled vertices.
- Colliding faces are difficult to control and need long calculation times. Try not to use them.

Often it is better to create a simplified mesh to use as your collision object,
however, this may be difficult if you are using an animated mesh.


Self-Collisions
===============

For information on self-collision please refer to
the :doc:`/physics/soft_body/settings/self_collision` settings.


## Examples


********
Examples
********

Here are some simple examples showing the power of soft body physics.


A Bouncing Cube
===============

The Process
-----------

First, change your start and end frames to 1 and 150.

Then, add a plane, and scale it five times. Next, go to the physics tab, and add a collision.
The default settings are fine for this example.

Now add a cube, or use the default cube, then enter *Edit Mode* to subdivide it three times.
Add a Bevel Modifier to it to smoothen the edges and then to add a little more,
press :kbd:`R` twice, and move your cursor a bit.

When finished, your scene should look like this:

.. figure:: /images/physics_soft-body_examples_scene-ready.png
   :width: 520px

   The scene, ready for soft body physics.

Everything is ready to add the soft body physics.
Go to :menuselection:`Properties --> Physics` and choose *Soft Body*.
Uncheck the *Soft Body Goal*, and check *Soft Body Self Collision*.
Also, under *Soft Body Edges*, increase the Bending to 10.

Playing the animation will now give a slow animation of a bouncing cube.
To speed things up, we need to bake the soft body physics.

Under *Soft Body Cache* change the values of your start and end frames. In this case 1 and 150.
Now, to test if everything is working, you can take a cache step of 5 or 10,
but for the final animation it is better to reduce it to 1, to cache everything.

.. TODO2.8:
   When finished, your physics panel should look like this:

   .. figure:: /images/physics_soft-body_examples_physics-settings.png

      The physics settings.

You can now bake the simulation, give the cube materials and textures and render the animation.


The Result
----------

`The rendered bouncing cube <https://www.youtube.com/watch?v=3PzgB9jw9iA>`__


## Index

.. _soft-body-index:
.. _bpy.types.SoftBodyModifier:

#############
  Soft Body
#############

.. toctree::
   :maxdepth: 2

   introduction.rst
   settings/index.rst
   forces/index.rst
   collision.rst
   examples.rst


## Introduction


************
Introduction
************

Soft body simulation is used for simulating soft deformable objects.
It was designed primarily for adding secondary motion to animation,
like jiggle for body parts of a moving character.

It also works for simulating more general soft objects that bend, deform and
react to forces like gravity and wind, or collide with other objects.

While it can simulate cloth and other stiff types of deformable objects to
an extent, the :doc:`Cloth Simulation </physics/cloth/index>` can do it better
with a solver specifically designed for this purpose.

The simulation works by combining existing animation on the object with forces
acting on it. There are exterior forces like gravity or force fields and
interior forces that hold the vertices together.
This way you can simulate the shapes that an object would take on in reality if it had volume,
was filled with something, and was acted on by real forces.

Soft bodies can interact with other objects through *Collision*.
They can interact with themselves through *Self-Collision*.

The result of the soft body simulation can be converted to a static object.
You can also *bake edit* the simulation, i.e.
edit intermediate results and run the simulation from there.


Typical Scenarios for using Soft Bodies
=======================================

.. _fig-softbody-intro-cone:

.. figure:: /images/physics_soft-body_introduction_windcone.jpg
   :width: 300px

   The wind cone is a soft body, as the suspension.

   `Animation <https://vimeo.com/1865817>`__

Soft bodies are well suited for:

- Jiggle on moving characters.
- Elastic and deformable objects made of materials like rubber or gelatin.
- Tree branches moving in the wind, swinging ropes, and the like.
- Flags, wide sleeves, cushions or other simple fabric reacting to forces.

The following videos may give you some more ideas:

- `New Penguoen <https://www.youtube.com/watch?v=hLnY-OFUBzM>`__.
- `Blender Softbody Simulations <https://www.youtube.com/watch?v=qdusMZlBbQ4>`__.


Creating a Soft Body
====================

Soft body simulation works for all objects that have vertices or control points
(meshes, curves, surfaces, and lattices).

To add a soft body simulation to an object,
go to the *Physics* tab in the Properties and activate the *Soft Body* button.
For a reference of all the settings see :doc:`this page </physics/soft_body/settings/index>`.

You start a soft body simulation by playback animation with :kbd:`Alt-A`,
and stop the simulation with :kbd:`Esc` or :kbd:`Alt-A`.


Interaction in Real-Time
========================

To work with a soft body simulation, you will find it handy to use the Timeline editor.
You can change between frames and the simulation will always be shown in the actual state.
You can interact in real-time with the simulation,
e.g. by moving collision objects or shaking a soft body object.

You can then select the soft body object while running the simulation and *Apply*
the modifier in the *Modifiers* tab of the Properties.
This makes the deformation permanent.


Tips
====

- Soft bodies work especially well if the objects have an even vertex distribution.
  You need enough vertices for good collisions. You change the deformation
  (the stiffness) if you add more vertices in a certain region.
- The calculation of collisions may take a long time. If something is not visible, why calculate it?
- To speed up the collision calculation it is often useful to collide with an additional,
  simpler, invisible, somewhat larger object.
- Use soft bodies only where it makes sense.
  If you try to cover a body mesh with a tight piece of cloth and animate solely with soft body,
  you will have no success. Self-collision of soft body hair may be activated,
  but that is a path that you have to wander alone. We will deal with
  :doc:`Collisions </physics/soft_body/collision>` in detail later.
- Try and use a *Lattice* or a *Curve Guide* soft body instead of the object itself. This may be magnitudes faster.


## Exterior


********
Exterior
********

Exterior forces are applied to the vertices (and nearly exclusively to the vertices)
of soft body objects. This is done using Newton's Laws of Physics:

- If there is no force on a vertex, it stays either unmoved or moves with constant speed in a straight line.
- The acceleration of a vertex depends on its mass and the force.
  The heavier the mass of a vertex the slower the acceleration. The larger the force the greater the acceleration.
- For every action there is an equal and opposite reaction.

Well, this is done only in the range of computing accurateness,
there is always a little damping to avoid overshoot of the calculation.


Example
=======

We will begin with a very simple example: the default cube.

- To judge the effect of the external forces you should at first turn off the *Goal*,
  so that the vertices are not retracted to their original position.
- Start playback to run the simulation.

What happens? The cube moves in negative Z direction.
Each of its eight vertices is affected by a global, constant force -- the gravitation.
Gravitation without friction is independent from the weight of an object,
so each object you would use as a soft body here would fall with the same acceleration.
The object does not deform, because every vertex moves with the same speed in the same direction.


Force Fields
============

Soft body vertices interact with all the :doc:`Force Fields </physics/forces/force_fields/index>`
applied (usually to particles) in the layer, such as wind, force fields,
and what ever physics field effect is on a common layer.


Soft Body Field Weights
-----------------------

.. reference::

   :Panel:     :menuselection:`Physics --> Soft Body --> Field Weights`

The *Soft Body Field Weights* panel allows you to control how much influence
each type of external force field has on the soft body system.

Effector Collection
   Limit effectors to a specified group. Only effectors in this group will have an effect on the current system.
Gravity
   Control how much the Global Gravity has an effect on the system.
All
   Scale all of the effector weights.


.. _physics-softbody-forces-exterior-aerodynamics:

Aerodynamics
============

Edges can be affected by wind as they move, and sail or flutter in a breeze.
A simple aerodynamic model of a flag sailing in the wind.

This special exterior force is not applied to the vertices but to the connecting edges.
Technically, a force perpendicular to the edge is applied.
The force scales with the projection of the relative speed on the edge (dot product).
Note that the force is the same if wind is blowing or if you drag the edge through the air
with the same speed. That means that an edge moving in its own direction subject to no force,
and an edge moving perpendicular to its own direction is subjected to maximum force.

The angle and the relative speed between medium and edge is used to calculate the force on the edge.
This force results that vertices with few connecting edges (front of a plane)
fall faster than vertices with more connecting edges (middle of a plane).
If all vertices have the same amount of edges in a direction they fall with equal speed.

The *Aerodynamics* settings are set in the :ref:`Soft Body Edges <physics-softbody-settings-aerodynamics>` panel.


.. _physics-softbody-forces-exterior-goal:

Goal
====

A "goal" is a shape that a soft body object tries to conform to.
It acts like a pin on a chosen set of vertices, controlling how much of an effect soft body has on them.

Enabling *Soft Body Goal* tells Blender to use the position (or animated position) of a vertex in the simulation.
Animating the vertices can be done in all the usual ways (F-Curves, armatures, parents, lattices, etc.)
before the soft body simulation is applied. The "goal" is the desired end position for vertices.
How a soft body tries to achieve this goal can be defined using stiffness forces and damping.

See the :doc:`Goal Settings </physics/soft_body/settings/goal>` for details.


Goal Strength
-------------

The *Goal Strength* defines how much motion from an animation system gets applied.

A *Goal* value of 1.0 means no soft body simulation,
the object act like any regular animated object (i.e. the vertex is kept at its original position).
When setting *Goal* to 0.0 (or no goal), the vertex is only influenced by physical laws
according to soft body simulation.

By setting goal values between 0.0 and 1.0,
you can blend between having the object affected only by the animation system,
and having the object affected only by the soft body effect.

Goal also serves as a memory, to make sure soft objects don't deform too much,
ending up in the non-soft animated shape. Using the *Vertex Group* weight system,
you can define a *Goal* weight per vertex. To make this look more natural,
spring forces can be defined to control how far vertices can move from their original position.

Often :ref:`painting-weight-index` is used to adjust the weight comfortably.
For non-mesh objects the *Weight* parameter of their vertices/control points is used instead;
Use the Context menu in Edit Mode or the *Transform* panel in the Sidebar region.
The weight of *Hair* particles can also be painted in :doc:`Particle Edit Mode </physics/particles/mode>`.


Technical Details
=================

In the Soft Body world, vertices of meshes are treated as particles having a mass.
Their movement is determined by the forces affecting them. Beside other forces
the individual particles can interact with another along edges using a physical model
which is very close to shock absorbers used in cars. The working parts are:

- A spring trying to keep the particles at a certain distance.
  How hard the spring tries to do that is controlled by the soft body parameter *Stiffness*.
- A damping element to calm the movement down.
  The resistance the element builds up against motion is controlled by the soft body parameter *Damping*.


## Index


##########
  Forces
##########

.. toctree::
   :maxdepth: 2

   exterior.rst
   interior.rst


## Interior


********
Interior
********

By default, the edges of a soft-body mesh act like springs. This means that,
like a mechanical spring, they can stretch under tension and squeeze under pressure.
Their initial length is also their "ideal" or "rest" length, which they try to return to.

Having edges act like springs is what holds the mesh together. If you were to disable this
behavior (as well as the :doc:`/physics/soft_body/settings/goal`), each vertex would be free
to go anywhere independently of the others, which would stretch the mesh until it's
no longer recognizable.

Having springs along edges alone typically isn't enough, however:
vertices in quads are still free to move towards their diagonal opposite,
potentially collapsing the quad into a line.

You could solve this by creating diagonal edges everywhere, but fortunately,
you don't have to: simply enable the *Stiffness* option to have Blender create
diagonal springs internally. This way, you don't have to change your mesh.

.. list-table::

   * - .. _fig-softbody-force-interior-connection:

       .. figure:: /images/physics_soft-body_forces_interior_theory-1.svg
          :width: 180px
          :figwidth: 180px

          Base springs along edges.

     - .. _fig-softbody-force-interior-stiff:

       .. figure:: /images/physics_soft-body_forces_interior_theory-2.svg
          :width: 180px
          :figwidth: 180px

          Additional springs when Stiffness is enabled.

Another method of preventing mesh collapse is applying *Bending Stiffness*,
which adds rotational resistance: making edges try to keep their relative angles.

Both of these methods are described in more detail below. You can configure them,
as well as other settings, in the :doc:`Soft Body Edges panel </physics/soft_body/settings/edges>`.


Stiffness
=========

To show the effect of the Stiffness setting, we will drop two cubes onto a plane
(see :doc:`Collisions </physics/soft_body/collision>`). The blue cube uses quads,
while the red one uses tris. Both cubes have their Goal setting disabled.

If *Stiffness* is disabled, the quad-only cube will collapse completely,
while the tri cube only temporarily deforms from the impact:

.. _fig-softbody-force-interior-without:

.. list-table:: Without Stiffness.

   * - .. figure:: /images/physics_soft-body_forces_interior_quadvstri-sb-001.png
          :width: 200px

          Frame 1.

     - .. figure:: /images/physics_soft-body_forces_interior_quadvstri-sb-036.png
          :width: 200px

          Frame 36.

     - .. figure:: /images/physics_soft-body_forces_interior_quadvstri-sb-401.png
          :width: 200px

          Frame 401.

If *Stiffness* is enabled, the quad cube maintains its shape as well thanks to the
extra springs:

.. _fig-softbody-force-interior-with:

.. list-table:: With Stiffness.

   * - .. figure:: /images/physics_soft-body_forces_interior_quadvstri-sb-001.png
          :width: 200px

          Frame 1.

     - .. figure:: /images/physics_soft-body_forces_interior_quadvstri-sb-sq-036.png
          :width: 200px

          Frame 36.

     - .. figure:: /images/physics_soft-body_forces_interior_quadvstri-sb-sq-401.png
          :width: 200px

          Frame 401.


Bending Stiffness
=================

The second method to stop an object from collapsing is to give it *Bending Stiffness.*
Just like the other settings, this can be combined with *Stiffness* to add bending
resistance to the diagonal springs as well.

We first do the same cube experiment as before, using only *Bending Stiffness*:

.. _fig-softbody-force-interior-bending:

.. list-table:: Bending Stiffness.

   * - .. figure:: /images/physics_soft-body_forces_interior_quadvstri-sb-001.png
          :width: 200px

          Frame 1.

     - .. figure:: /images/physics_soft-body_forces_interior_quadvstri-sb-bs-036.png
          :width: 200px

          Frame 36.

     - .. figure:: /images/physics_soft-body_forces_interior_quadvstri-sb-bs-401.png
          :width: 200px

          Frame 401.

Both cubes keep their shape. Now, we try the same thing with subdivided planes,
again a quad-based one and a triangulated one:

.. list-table::

   * - .. figure:: /images/physics_soft-body_forces_interior_quadvstri-bending-001.png
          :width: 200px

          Two planes falling.

     - .. _fig-softbody-force-interior-no-bending:

       .. figure:: /images/physics_soft-body_forces_interior_quadvstri-bending-101.png
          :width: 200px

          No bending stiffness.

     - .. figure:: /images/physics_soft-body_forces_interior_quadvstri-bending-high-101.png
          :width: 200px

          High bending stiffness (10).

Without any *Bending Stiffness*, the faces can rotate freely as though their edges were hinges.
Enabling *Stiffness* to add diagional springs would not change this (just as triangulating doesn't).

With a high *Bending Stiffness*, however, the edges resist this rotation, and the planes
act more like planks than towels.


## Cache


*****
Cache
*****

.. reference::

   :Panel:     :menuselection:`Physics --> Soft Body --> Cache`

Soft Body physics simulations use a unified system for caching and baking.
See :doc:`Particle Cache </physics/particles/emitter/cache>` and
:doc:`General Baking </physics/baking>` documentation for reference.


## Edges

.. _bpy.types.SoftBodySettings.use_edges:

*****
Edges
*****

.. reference::

   :Panel:     :menuselection:`Physics --> Soft Body --> Edges`

Allow the edges in a mesh object to act like springs.
See :doc:`interior forces </physics/soft_body/forces/interior>`.

.. _bpy.types.SoftBodySettings.vertex_group_spring:

Springs
   Use a specified vertex group for spring strength values.

.. _bpy.types.SoftBodySettings.pull:

Pull
   The spring stiffness for edges (how much the edges are allowed to stretch).
   A low value means very weak springs (a very elastic material),
   a high value is a strong spring (a stiffer material) that resists being pulled apart.

   A value of 0.5 is latex, 0.9 is like a sweater, 0.999 is a highly-starched napkin or leather.
   The soft body simulation tends to get unstable if you use a value of 0.999,
   so you should lower this value a bit if that happens.

.. _bpy.types.SoftBodySettings.push:

Push
   How much the soft body resists being scrunched together, like a compression spring.
   Low values for fabric, high values for inflated objects and stiff material.

.. _bpy.types.SoftBodySettings.damping:

Damp
   The friction for edge springs. High values (max of 50) dampen the *Push*/*Pull* effect and calm down the cloth.

.. _bpy.types.SoftBodySettings.plastic:

Plasticity
   Permanent deformation of the object after a collision.
   The vertices take a new position without applying the modifier.

.. _bpy.types.SoftBodySettings.bend:

Bending
   This option creates virtual connections between a vertex and the vertices connected to its neighbors.
   This includes diagonal edges. Damping also applies to these connections.

.. _bpy.types.SoftBodySettings.spring_length:

Length
   The edges can shrink or be blown up. This value is given in percent,
   0 disables this function. 100% means no change, the body keeps 100% of its size.

.. _bpy.types.SoftBodySettings.use_edge_collision:
.. _bpy.types.SoftBodySettings.use_face_collision:

Collision
   Edge
      Checks for edges of the soft body mesh colliding.
   Face
      Checks for any portion of the face of the soft body mesh colliding (which is computationally intensive).
      While *Face* enabled can solve collision errors, there does not seem to be any dampening settings for it.
      So parts of the soft body object near a collision mesh tend to "jitter" as they bounce off and fall back,
      even when there is no motion of any meshes. Edge collision has dampening, so that can be controlled,
      but Deflection dampening value on a collision object does not seem to affect the face collision.


.. _physics-softbody-settings-aerodynamics:

Aerodynamics
============

Force from surrounding media.
See :ref:`exterior forces <physics-softbody-forces-exterior-aerodynamics>` for details.

.. _bpy.types.SoftBodySettings.aerodynamics_type:

Type
   :Simple:
      Edges receive a drag force from the surrounding media.
   :Lift Force:
      Edges receive a lift force when passing through the surrounding media.

.. _bpy.types.SoftBodySettings.aero:

Factor
   How much aerodynamic force to use. Try a value of 30 at first.


.. _bpy.types.SoftBodySettings.use_stiff_quads:

Stiffness
=========

For quad faces, the diagonal edges are used as springs.
This stops quad faces to collapse completely on collisions (what they would do otherwise).

.. _bpy.types.SoftBodySettings.shear:

Shear
   Stiffness of the virtual springs created for quad faces.


## Goal

.. _bpy.types.SoftBodySettings.use_goal:

****
Goal
****

.. reference::

   :Panel:     :menuselection:`Physics --> Soft Body --> Goal`

Enabling this tells Blender to use the motion from animations
(F-Curves, armatures, parents, lattices, etc.) in the simulation.
The "goal" is the desired end position for vertices based on this animation.

See :ref:`exterior forces <physics-softbody-forces-exterior-goal>` for details.

.. _bpy.types.SoftBodySettings.vertex_group_goal:

Vertex Group
   Use a vertex group to allow per-vertex goal weights (multiplied by the *Default* goal).


Settings
========

.. _bpy.types.SoftBodySettings.goal_spring:

Stiffness
   The spring stiffness for *Goal*. A low value creates very weak springs
   (more flexible "attachment" to the goal), a high value creates a strong spring
   (a stiffer "attachment" to the goal).

.. _bpy.types.SoftBodySettings.goal_friction:

Damping
   The friction coefficient for *Goal*. Higher values give damping of the spring effect (little jiggle),
   and the movement will soon come to an end.


Strengths
=========

.. _bpy.types.SoftBodySettings.goal_default:

Default
   Goal weight/strength for all vertices when no *Vertex Group* is assigned.
   If you use a vertex group the weight of a vertex defines its goal.

.. _bpy.types.SoftBodySettings.goal_min:
.. _bpy.types.SoftBodySettings.goal_max:

Min/Max
   When you use a vertex group, you can use the *Minimum* and *Maximum* to fine-tune (clamp) the weight values.
   The lowest vertex weight will become *Minimum*, the highest value becomes *Maximum*.


## Index

.. _bpy.types.SoftBodySettings:

############
  Settings
############

.. reference::

   :Panel:     :menuselection:`Physics --> Soft Body`

Collision Collection
   If set, soft body collides with objects from the collection, instead of using objects that are on the same layer.

.. toctree::
   :maxdepth: 2

   object.rst
   simulation.rst
   cache.rst
   goal.rst
   edges.rst
   self_collision.rst
   solver.rst


## Object


******
Object
******

.. _bpy.types.SoftBodySettings.friction:

Friction
   The friction of the surrounding medium. Generally friction dampens a movement.
   The larger the friction, the more viscous is the medium.
   Friction always appears when a vertex moves relative to its surround medium.

.. _bpy.types.SoftBodySettings.mass:

Mass
   Mass value for vertices.
   Larger mass slows down acceleration, except for gravity where the motion is constant regardless of mass.
   Larger mass means larger inertia, so also braking a soft body is more difficult.

.. _bpy.types.SoftBodySettings.vertex_group_mass:

Control Point
   You can paint weights and use a specified vertex group for mass values.


## Self Collision

.. _bpy.types.SoftBodySettings.use_self_collision:

**************
Self Collision
**************

.. reference::

   :Panel:     :menuselection:`Physics --> Soft Body --> Self Collision`

.. note::

   *Self-Collision* is working only if you have activated *Use Edges*.

When enabled, allows you to control how Blender will prevent the soft body from intersecting with itself.
Every vertex is surrounded with an elastic virtual ball.
Vertices may not penetrate the balls of other vertices.
If you want a good result you may have to adjust the size of these balls.
Normally it works pretty well with the default options.

.. _bpy.types.SoftBodySettings.collision_type:

Calculation Type
   :Manual:
      The *Ball Size* directly sets the ball size.
   :Average:
      The average length of all edges attached to the vertex is calculated and then multiplied
      with the *Ball Size* setting. Works well with evenly distributed vertices.
   :Minimal/Maximal:
      The ball size is as large as the smallest/largest spring length of the vertex multiplied with the *Ball Size*.
   :Average Min Max:
      Size = ((Min + Max)/2) × *Ball Size*.

.. _bpy.types.SoftBodySettings.ball_size:

Ball Size
   Fraction of the length of attached edges.
   The edge length is computed based on the chosen algorithm.
   This setting is the factor that is multiplied by the spring length.
   It is a spherical distance (radius) within which, if another vertex of the same mesh enters,
   the vertex starts to deflect in order to avoid a self-collision.

   Set this value to the fractional distance between vertices that you want them to have their own "space".
   Too high of a value will include too many vertices at all times and slow down the calculation.
   Too low of a level will let other vertices get too close and thus possibly intersect because
   there will not be enough time to slow them down.

.. _bpy.types.SoftBodySettings.ball_stiff:

Stiffness
   How elastic that ball of personal space is.
   A high stiffness means that the vertex reacts immediately to another vertex enters their space.

.. _bpy.types.SoftBodySettings.ball_damp:

Dampening
   How the vertex reacts.
   A low value just slows down the vertex as it gets too close. A high value repulses it.

.. note::

   Collisions with other objects are set in the (other) :doc:`Collision panel </physics/collision>`.
   To collide with another object they have to share at least one common layer.


## Simulation


**********
Simulation
**********

.. _bpy.types.SoftBodySettings.speed:

Speed
   You can control the internal timing of the soft body system with this value.
   It sets the correlation between frame rate and tempo of the simulation.
   A free falling body should cover a distance of about five meters after
   one second and travel at a speed of ten meters per seconds.

   You can adjust the scale of your scene and simulation with this correlation.
   If you render with 25 frames per second, you will have to set *Speed* to 1.3.


## Solver

.. _physics-softbody-settings-solver:

******
Solver
******

.. reference::

   :Panel:     :menuselection:`Physics --> Soft Body --> Solver`

The settings in the *Soft Body Solver* panel determine the accuracy of the simulation.

.. _bpy.types.SoftBodySettings.step_min:

Step Size Min
   Minimum simulation steps per frame. Increase this value, if the soft body misses fast-moving collision objects.

.. _bpy.types.SoftBodySettings.step_max:

Max
   Maximum simulation steps per frame.
   Normally the number of simulation steps is set dynamically
   (with the *Error Limit*) but you have probably a good reason to change it.

.. _bpy.types.SoftBodySettings.use_auto_step:

Auto-Step
   Use velocities for automatic step sizes.
   Helps the Solver figure out how much work it needs to do based on how fast things are moving.

.. _bpy.types.SoftBodySettings.error_threshold:

Error Limit
   Rules the overall quality of the solution delivered.
   The most critical setting that defines how precise the solver should check for collisions.
   Start with a value that is half the average edge length.
   If there are visible errors, jitter, or over-exaggerated responses, decrease the value.
   The solver keeps track of how "bad" it is doing and the *Error Limit* causes the solver to
   do some "adaptive step sizing".


Diagnostics
===========

.. _bpy.types.SoftBodySettings.use_diagnose:

Print Performance to Console
   Prints on the console how the solver is doing.

.. _bpy.types.SoftBodySettings.use_estimate_matrix:

Estimate Transforms
   Estimate matrix, split to ``COM``, ``ROT``, ``SCALE``.

.. (TODO) explain what it is, when it can be useful

   Center of mass -- Location of the center of mass.
   Rot Matrix -- Estimated the rotation matrix.
   Scale Matrix -- Estimated the scale matrix.


Helpers
=======

These settings control how the soft body will react (deform)
once it either gets close to or actually intersects (cuts into) another collision object on the same layer.

.. _bpy.types.SoftBodySettings.choke:

Choke
   Calms down (reduces the exit velocity of) a vertex or edge once it penetrates a collision mesh.

.. _bpy.types.SoftBodySettings.fuzzy:

Fuzzy
   Fuzziness while on collision, high values make collision handling faster but less stable.
   Simulation is faster, but less accurate.


