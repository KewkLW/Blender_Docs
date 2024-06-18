# Index for compositing

- [Index](#Index)
- [Introduction](#Introduction)
- [Realtime Compositor](#Realtime-Compositor)
- [Sidebar](#Sidebar)
- [Groups](#Groups)
- [Alpha Convert](#Alpha-Convert)
- [Color Ramp](#Color-Ramp)
- [Convert Colorspace](#Convert-Colorspace)
- [Index](#Index)
- [Invert Color](#Invert-Color)
- [Rgb To Bw](#Rgb-To-Bw)
- [Set Alpha](#Set-Alpha)
- [Bright Contrast](#Bright-Contrast)
- [Color Balance](#Color-Balance)
- [Color Correction](#Color-Correction)
- [Exposure](#Exposure)
- [Gamma](#Gamma)
- [Hue Correct](#Hue-Correct)
- [Hue Saturation](#Hue-Saturation)
- [Index](#Index)
- [Rgb Curves](#Rgb-Curves)
- [Tone Map](#Tone-Map)
- [Alpha Over](#Alpha-Over)
- [Combine Color](#Combine-Color)
- [Index](#Index)
- [Mix Color](#Mix-Color)
- [Separate Color](#Separate-Color)
- [Z Combine](#Z-Combine)
- [Anti Aliasing](#Anti-Aliasing)
- [Denoise](#Denoise)
- [Despeckle](#Despeckle)
- [Dilate Erode](#Dilate-Erode)
- [Filter](#Filter)
- [Glare](#Glare)
- [Index](#Index)
- [Inpaint](#Inpaint)
- [Kuwahara](#Kuwahara)
- [Pixelate](#Pixelate)
- [Posterize](#Posterize)
- [Sun Beams](#Sun-Beams)
- [Bilateral Blur](#Bilateral-Blur)
- [Blur](#Blur)
- [Bokeh Blur](#Bokeh-Blur)
- [Defocus](#Defocus)
- [Directional Blur](#Directional-Blur)
- [Index](#Index)
- [Vector Blur](#Vector-Blur)
- [Bokeh Image](#Bokeh-Image)
- [Image](#Image)
- [Index](#Index)
- [Mask](#Mask)
- [Movie Clip](#Movie-Clip)
- [Texture](#Texture)
- [Index](#Index)
- [Rgb](#Rgb)
- [Value](#Value)
- [Index](#Index)
- [Render Layers](#Render-Layers)
- [Scene Time](#Scene-Time)
- [Time Curve](#Time-Curve)
- [Channel Key](#Channel-Key)
- [Chroma Key](#Chroma-Key)
- [Color Key](#Color-Key)
- [Color Spill](#Color-Spill)
- [Difference Key](#Difference-Key)
- [Distance Key](#Distance-Key)
- [Index](#Index)
- [Keying](#Keying)
- [Keying Screen](#Keying-Screen)
- [Luminance Key](#Luminance-Key)
- [Index](#Index)
- [Box Mask](#Box-Mask)
- [Cryptomatte](#Cryptomatte)
- [Cryptomatte Legacy](#Cryptomatte-Legacy)
- [Double Edge Mask](#Double-Edge-Mask)
- [Ellipse Mask](#Ellipse-Mask)
- [Id Mask](#Id-Mask)
- [Index](#Index)
- [Composite](#Composite)
- [File Output](#File-Output)
- [Index](#Index)
- [Viewer](#Viewer)
- [Index](#Index)
- [Plane Track Deform](#Plane-Track-Deform)
- [Stabilize 2D](#Stabilize-2D)
- [Track Position](#Track-Position)
- [Corner Pin](#Corner-Pin)
- [Crop](#Crop)
- [Displace](#Displace)
- [Flip](#Flip)
- [Index](#Index)
- [Lens Distortion](#Lens-Distortion)
- [Map Uv](#Map-Uv)
- [Movie Distortion](#Movie-Distortion)
- [Rotate](#Rotate)
- [Scale](#Scale)
- [Transform](#Transform)
- [Translate](#Translate)
- [Index](#Index)
- [Levels](#Levels)
- [Map Range](#Map-Range)
- [Map Value](#Map-Value)
- [Math](#Math)
- [Normalize](#Normalize)
- [Split](#Split)
- [Switch](#Switch)
- [Switch Stereo View](#Switch-Stereo-View)
- [Combine Xyz](#Combine-Xyz)
- [Index](#Index)
- [Normal](#Normal)
- [Separate Xyz](#Separate-Xyz)
- [Vector Curves](#Vector-Curves)


## Index

.. _composite-nodes-index:
.. _bpy.types.Compositor:

###############
  Compositing
###############

.. toctree::
   :maxdepth: 2

   introduction.rst
   sidebar.rst
   realtime_compositor.rst

.. index:: Compositor Nodes

.. _compositor-nodes:

Node Types
==========

.. toctree::
   :maxdepth: 1

   types/input/index.rst
   types/output/index.rst

----------

.. toctree::
   :maxdepth: 1

   types/color/index.rst
   types/filter/index.rst

----------

.. toctree::
   :maxdepth: 1

   types/keying/index.rst
   types/mask/index.rst

----------

.. toctree::
   :maxdepth: 1

   types/tracking/index.rst

----------

.. toctree::
   :maxdepth: 1

   types/transform/index.rst
   types/utilities/index.rst
   types/vector/index.rst

----------

.. toctree::
   :maxdepth: 1

   types/groups.rst
   types/layout/index.rst


## Introduction

.. index:: Nodes; Compositing Nodes

************
Introduction
************

Compositing Nodes allow you to assemble and enhance an image (or movie). Using composition nodes,
you can glue two pieces of footage together and colorize the whole sequence all at once.
You can enhance the colors of a single image or an entire movie clip in a static manner or
in a dynamic way that changes over time (as the clip progresses). In this way,
you use composition nodes to both assemble video clips together and enhance them.

.. note:: Term: Image

   The term *Image* may refer to a single picture, a picture in
   a numbered sequence of images, or a frame of a movie clip.
   The Compositor processes one image at a time, no matter what kind of input you provide.

To process your image, you use nodes to import the image into Blender, change it,
optionally merge it with other images, and finally, save it.

.. figure:: /images/compositing_types_distort_map-uv_example-2.png

   An example of a composition.

.. figure:: /images/compositing_types_color_hue-saturation_example.jpg

   An example of color correction.


Getting Started
===============

Access the *Compositor* and activate nodes for compositing by clicking the *Use Nodes* checkbox in the header
(see :doc:`/interface/controls/nodes/introduction`).

.. note::

   After clicking *Use Nodes* the Compositor is enabled, however,
   it can also be disabled in the :ref:`render-output-postprocess`.

You now have your first node setup, from here you can add and connect many types of
:doc:`Compositing Nodes </compositing/index>`, in a sort of map layout,
to your heart's content (or physical memory constraints, whichever comes first).

.. note::

   Nodes and node concepts are explained in more detail
   in the :doc:`Nodes </interface/controls/nodes/index>` reference.


Examples
========

You can do just about anything with images using nodes.

Raw footage from a foreground actor in front of a blue screen,
or a rendered object doing something, can be layered on top of a background.
Composite both together, and you have composited footage.

You can change the mood of an image:

- To make an image 'feel' colder, a blue tinge is added.
- To convey a flashback or memory, the image may be softened.
- To convey hatred and frustration, add a red tinge or enhance the red.
- A startling event may be sharpened and contrast-enhanced.
- To convey a happy feeling add yellow (equal parts red and green, no blue).
- Dust and airborne dirt are often added as a cloud texture over the image to give a little more realism.


Image Size
==========

It is recommended to pay attention to image resolution and color depth when mixing and
matching images. :term:`Aliasing`, color *flatness*,
or distorted images can all be traced to mixing inappropriate resolutions and color depths.

The Compositor can mix images with any size,
and will only perform operations on pixels where images have an overlap.
When nodes receive inputs with differently sized Images, these rules apply:

- The first/top Image input socket defines the output size.
- The composite is centered by default,
  unless a translation has been assigned to a buffer using a *Translate* node.

So each node in a composite can operate on different sized images as defined by its inputs.
Only the *Composite* output node has a fixed size,
as defined by the settings in :menuselection:`Output Properties --> Render --> Format`.
The *Viewer* node always shows the size from its input, but when not linked
(or linked to a value) it shows a small 320×256 pixel image.


Saving your Composite Image
===========================

The *Render* button renders a single frame or image.
Save your image using :menuselection:`Image --> Save Image` or :kbd:`Alt-S`.
The image will be saved using the image format settings on the Render panel.

To save a sequence of images, for example,
if you input a movie clip or used a Time node with each frame in its own file,
use the *Animation* button and its settings. If you might want to later overlay them,
be sure to use an image format that supports an Alpha channel (such as ``PNG``).
If you might want to later arrange them front to back or create a depth of field effect,
use a format that supports a Z-depth channel (such as ``EXR``).

To save a composition as a movie clip (all frames in a single file),
use an ``AVI`` or ``QuickTime`` format, and use the *Animation* button and its settings.


## Realtime Compositor

.. _realtime-compositor:

**************
GPU Compositor
**************

The new GPU accelerated compositor introduced in Blender 3.5 and is currently used for
:ref:`viewport compositing <viewport-compositing>`.


Data
====

Dimensionality
--------------

Compositing nodes operate on data that is either an image or a dimensionless single value. For
instance, the :ref:`Levels node <bpy.types.CompositorNodeLevels>` outputs a single value, while the
:ref:`Render Layers node <bpy.types.CompositorNodeRLayers>` outputs an image. Node inputs that
expect a single value assume a default value if an image is given and ignore the image completely,
for instance, the :ref:`Transform node <bpy.types.CompositorNodeTransform>` expects single values
for its inputs and will assume default values if images were given to those inputs. The default
values are those that are considered identity and thus have no effect on the output, so for the
:ref:`Transform node <bpy.types.CompositorNodeTransform>`, the *X*, *Y*, and *Angle* inputs will
have a default value of zero, while the *Scale* input will have a default value of one. On the other
hand, if node inputs that expect an image are given a single value, the single value will be assumed
to cover the whole compositing space. For instance, the :ref:`Filter node
<bpy.types.CompositorNodeFilter>` expect its *Factor* input to be an image, but if a single value is
given, it will be assumed to be the same for all pixels.


Type
----

Three types of data exist, all of which are stored in half precision formats:

Float
  A signed floating-point number. Integer data is also stored as floats because no integer type
  exist.

Vector
  A 4D vector. While it is 4D, it can have different interpretations depending on the node that uses
  it. It can be treated as a 2D vector with the last two components ignored, for instance, the
  *Vector* input of the :ref:`Displace node <bpy.types.CompositorNodeDisplace>` is treated as a 2D
  vector. It can be treated as a 3D vector with the last component ignored, for instance, the
  *Vector* input of the :ref:`Seperate XYZ node <bpy.types.CompositorNodeSeparateXYZ>` is treated as
  a 3D vector. It can be treated as two consecutive 2D vectors. For instance the *Velocity Pass* as
  expected by the :ref:`Vector Blur node <bpy.types.CompositorNodeVecBlur>` is assumed to have the
  *2D Previous Velocity* in the X and Y components of the vector and the *2D Next Velocity* in the
  Z and W components of the vector.

Color
  A 4D vector storing the Red, Green, Blue, and Alpha of the color. The color is free form and does
  not conform to a specific color space or alpha storage model, instead, appropriate nodes will have
  settings to control the representation of their output and nodes exist to convert between the
  different representations.


Implicit Conversion
^^^^^^^^^^^^^^^^^^^

In case a node input is given data of type other than its own type, the following implicit
conversions are performed:

+---------+---------+-------------------------------------+
| Source  | Target  | Conversion                          |
+=========+=========+=====================================+
| Float   | Vector  | f => Vector(f, f, f, 0)             |
+---------+---------+-------------------------------------+
| Float   | Color   | f => Color(f, f, f, 1)              |
+---------+---------+-------------------------------------+
| Vector  | Float   | (x, y, z, w) => Average(x, y, z)    |
+---------+---------+-------------------------------------+
| Vector  | Color   | (x, y, z, w) => Color(x, y, z, 1)   |
+---------+---------+-------------------------------------+
| Color   | Float   | (r, g, b, a) => Average(r, g, b)    |
+---------+---------+-------------------------------------+
| Color   | Vector  | (r, g, b, a) => Vector(r, g, b, 0)  |
+---------+---------+-------------------------------------+

The following example demonstrates implicit conversion between a color type and a float type, since
the :ref:`Math node <bpy.types.CompositorNodeMath>` expect float inputs.

.. figure:: /images/compositing_realtime-compositor_compositing-space_data_type_implicit_conversion.png

   An example that demonstrates implicit conversion between a color type and a float type, since the
   *Math* node expects float inputs.


Compositing Space
=================

Image Domain
------------

The compositor is designed in such a way as to allow compositing in an infinite compositing space.
Consequently, images are not only represented by their size, but also by their transformation in
that space, much like 3D objects have transformations. An identity transformation represents an
image that is centered in space. The rectangular area occupied by an image in that space as defined
by its transformation and size is called the *Domain* of the image. The figure below demonstrates
the domains of two example images.

..
   \documentclass[tikz, convert]{standalone}
   \begin{document}
   \begin{tikzpicture}
     % Draw axis and grid.
     \draw[help lines, color = gray, dashed] (-4.9,-3.9) grid (4.9,3.9);
     \draw[->, thick] (-5,0) -- (5,0) node[right] {$x$};
     \draw[->, thick] (0,-4) -- (0,4) node[above] {$y$};
     % Draw bigger domain.
     \draw[ultra thick] (-4, -3) rectangle (4, 3);
     \node[above] at (-2, 3) {800px $\times$ 600px};
     % Draw smaller domain.
     \draw[ultra thick] (1, 1) rectangle (3, 2);
     \node[above] at (2, 2) {800px $\times$ 400px};
   \end{tikzpicture}
   \end{document}

.. figure:: /images/compositing_realtime-compositor_compositing-space_image-domain_example.png

   The domains of two example images are illustrated on the compositing space. One of the images is
   centered in space and the other is scaled down and translated such that it lies in the upper
   right quadrant of the space. Notice that both images have similar sizes in pixels, yet their
   apparent sizes are different.

Images can be transformed using nodes like the :ref:`Transform <bpy.types.CompositorNodeTransform>`,
:ref:`Translate <bpy.types.CompositorNodeTranslate>`, and :ref:`Rotate
<bpy.types.CompositorNodeRotate>` nodes.


Operation Domain
----------------

:ref:`Compositor Nodes <compositor-nodes>` operate on a specific rectangular area of the compositing
space called the *Operation Domain*. The nodes only consider the area of the input images that
overlap the operation domain and ignores the rest of the images. If an input image doesn't
completely overlap the operation domain, the rest of the operation domain for that input will be
assumed to be a zero value, a zero vector, or a transparent zero color depending on the type.

For instance, the figure below illustrates a case where the operation domain of a node is the large
blue area and the domain of an input image is the small red area. In that case, the input image
doesn't completely overlap the operation domain, so the rest of the blue area for that input image
is assumed to be zero.

..
   \documentclass[tikz, convert]{standalone}
   \begin{document}
   \begin{tikzpicture}
     % Draw axis and grid.
     \draw[help lines, color = gray, dashed] (-4.9,-3.9) grid (4.9,3.9);
     \draw[->, thick] (-5,0) -- (5,0) node[right] {$x$};
     \draw[->, thick] (0,-4) -- (0,4) node[above] {$y$};
     % Draw operation domain.
     \fill[opacity = 0.3, blue] (-4, -3) rectangle (4, 3);
     \draw[ultra thick] (-4, -3) rectangle (4, 3);
     % Draw input image domain.
     \fill[fill opacity = 0.3, red] (0, 0) rectangle (3, 2);
     \draw[ultra thick] (0, 0) rectangle (3, 2);
   \end{tikzpicture}
   \end{document}

.. figure:: /images/compositing_realtime-compositor_compositing-space_operation-domain_example.png

   An example case where the operation domain of a node is shown in blue and the domain of an input
   image is shown in red. Since the input image doesn't completely cover the operation domain of the
   node, the rest of the blue area for that input image is assumed to be zero.

The previous illustration is a representation of a real world example where one uses the :ref:`Alpha
Over <bpy.types.CompositorNodeAlphaOver>` node to overlay a small logo on an image, as shown in the
figure below. In that case, the operation domain covers the entirety of the viewport --- as will later
be demonstrated, but the logo covers only a small area of it, so the rest of the area is assumed to
be a zero transparent color, which is convenient for the use case.

.. figure:: /images/compositing_realtime-compositor_compositing-space_operation-domain_real-example.png

   A real world example where the Alpha Over node is used to over a small logo on an image. The logo
   only covers a small area of the operation domain, which is the whole viewport in this case, so
   the rest of the area is assumed to be a zero transparent color.


Interpolation
^^^^^^^^^^^^^

If an input image to a node is not perfectly aligned with the operation domain of the node or have a
different size in pixels, the node would typically need to do a process called Interpolation, where
the input image is read at the exact positions of the pixels of the operation domain. This can be
done using different interpolation methods, including Nearest-Neighbor, Bilinear, and Bicubic
interpolations. Those interpolation methods are demonstrated in the following
`Wikipedia gallery <https://en.wikipedia.org/wiki/Comparison_gallery_of_image_scaling_algorithms>`__.
Transformation nodes like the :ref:`Transform <bpy.types.CompositorNodeTransform>` and :ref:`Rotate
<bpy.types.CompositorNodeRotate>` nodes include an interpolation option to set how they prefer their
output image to be read and interpolated.


Determining Operation Domain
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The question remains on how nodes determine their operation domain. Different node types can have
different mechanisms for determining their operation domain. But generally, three classes of nodes
exist when it comes to the mechanism of determining the operation domain, each of which is presented
in one of the following sections.


Input Nodes
"""""""""""

The operation domain of input nodes like the :ref:`Image node <bpy.types.CompositorNodeImage>` is a
domain with an identity transformation and the same size as their outputs, so for the *Image* node,
the operation domain will be the domain whose size is the size of the image and whose transformation
is an identity one.


Output Nodes
""""""""""""

The operation domain of output nodes like the :ref:`Viewer node <bpy.types.CompositorNodeViewer>` is
a domain with an identity transformation and the same size as the final compositor output. For
:ref:`viewport compositing <viewport-compositing>`, that size would be the viewport size, and for
final render compositing, that size would be the scene render size.


Other Nodes
"""""""""""

Unless stated otherwise in their respective documentation pages, all other nodes use the following
mechanism. One of the inputs of the nodes is designated as the *Domain Input* of the node, and the
operation domain of the node is identical to the domain of that designated input. For many nodes,
the domain input can be intuitively identified as the main input of the node, for instance, the
domain input for the :ref:`Filter node <bpy.types.CompositorNodeFilter>` is the *Image* input. But
there are some caveats to note, which requires a deeper understanding of the mechanism.

Each input in the node has the so called *Domain Priority* property, the operation domain of the
node is the domain of the non single value input with the highest domain priority. So for instance,
the :ref:`Filter node <bpy.types.CompositorNodeFilter>` has two inputs, the domain priority of the
*Image* input is higher than that of the *Factor* input, and there are four possible configurations:

* Both the *Image* and factor inputs are connected to images. In this case, the *Image* input is the
  domain input because it has the highest priority and is connected to an image.

* The *Image* input is connected to an image, but the *Factor* input isn't. In this case, the
  *Image* input is the domain input because it it is the only input connected to an image regardless
  of its priority.

* The *Image* input is not connected to an image but the *Factor* input is. In this case, the
  *Factor* input is the domain input because it is the only input connected to an image regardless
  of its priority.

* Neither the *Image* nor the *Factor* inputs are connected to images, in this case, there isn't
  a domain input because the node is evaluated on single values.


Considerations
^^^^^^^^^^^^^^

The aforementioned mechanism for determining the operation domain has a number of consequences that
needs to be considered as they might be undesirable, each of which is presented in one of the
following sections.


Clipping
""""""""

The output of nodes will be intuitively clipped to the operation domain, or rather, the domain of
the domain input. For instance, if the *Foreground* input is bigger than the *Background* input in
the :ref:`Alpha Over node <bpy.types.CompositorNodeAlphaOver>`, the output will be clipped to the
*Background* input because it is the domain input, as shown in the following figure.

.. figure:: /images/compositing_realtime-compositor_compositing-space_operation-domain_considerations_clipping.png

   The *Foreground* input is bigger than the *Background* input in the *Alpha Over* node, so the
   output is intuitively clipped to the *Background* input because it is the domain input.

The :ref:`Alpha Over node <bpy.types.CompositorNodeAlphaOver>` currently doe not support changing
the domain priority for its inputs, so as a workaround, one can use a :ref:`Mix node
<bpy.types.CompositorNodeMixRGB>` to achieved the desired behavior, noting that the first *Image*
input in the *Mix* node has the highest domain priority, as shown in the following figure.

.. figure:: /images/compositing_realtime-compositor_compositing-space_operation-domain_considerations_clipping-solution.png

   Working around the clipping behavior of the *Alpha Over* node using a Mix node, noting that the
   first *Image* input in the *Mix* node has the highest domain priority


Output
======

The GPU compositor only supports a single active output target, that is, only one of the
:ref:`Composite nodes <bpy.types.CompositorNodeComposite>` or :ref:`Viewer nodes
<bpy.types.CompositorNodeViewer>` in the node tree will be considered active and the rest will be
ignored. In particular, the compositor searches the *Active Node Tree Context* and falls back to the
*Root Node Tree Context* if no active output was found in the active node tree context. The active
node tree context is the node tree of an expanded node group, that is, when the users selects a node
group node and edits its underlying tree, while the root node tree context is the top level node
tree without any expanded node groups. The compositor searches for the active *Composite* node, if
non was found, it searches for the active *Viewer* node, be it a *Viewer* or a *Split Viewer* node,
if non was found, the compositor doesn't run altogether. Consequently, note that adding a *Viewer*
node will have no effect if there is a *Composite* node, since the priority is given to *Composite*
nodes.


## Sidebar


*******
Sidebar
*******

View
====

.. reference::

   :Panel:     :menuselection:`Sidebar region --> View`


Backdrop
--------

.. figure:: /images/compositing_sidebar_view.png
   :width: 200px
   :align: right

   Backdrop panel.

The backdrop is the output of a Viewer node in the background of the Compositor.
For example, when :kbd:`Shift-Ctrl-LMB` on an Image node, it displays a preview of the image,
or on a Mix node, will show the result of the mixing.
You can toggle the backdrop by clicking the checkbox in the *Backdrop* panel title
or by clicking on the *Backdrop* button in the header.

Channels
   The color channels to display of the backdrop image.
Zoom :kbd:`Alt-V` :kbd:`V`
   Sets the size of the backdrop image.
Offset
   Change the screen space position of the backdrop.
Move :kbd:`Alt-MMB`
   Changes the position of the backdrop.
Fit
   Scales the backdrop to fit the size of the Compositor.
Reset Backdrop
   Sets back to the default values of Zoom to 1 and Offset to 0.


Options
=======

.. reference::

   :Panel:     :menuselection:`Sidebar region --> Options`


Performance
-----------

.. figure:: /images/compositing_sidebar_options.png
   :width: 200px
   :align: right

   Performance panel.

This panel helps you tweak the performance of the Compositor.

.. _bpy.types.RenderSettings.compositor_device:

Device
   The device used for compositing.

   :CPU: Use the CPU for compositing.
   :GPU: Use the GPU for compositing.

.. _bpy.types.RenderSettings.compositor_precision:

Precision
   The precision of compositor intermediate result.

   :Auto: Use full precision for final renders, half precision otherwise.
   :Full: Use full precision for final renders and viewport.

.. _bpy.types.CompositorNodeTree.use_viewer_border:

Viewer Region
   This allows to set an area of interest for the backdrop.
   Press :kbd:`Ctrl-B` and select a rectangular area in the preview
   which will become the next preview in the backdrop.
   :kbd:`Ctrl-Alt-B` discards the region back to a full preview.
   This is only a preview option, final compositing during a render ignores this region.

.. _bpy.types.SpaceNodeEditor.use_auto_render:

Auto Render
   Re-render and composite changed layer when edits to the 3D scene are made.


## Groups

.. _bpy.types.CompositorNodeGroup:
.. Editor's Note: This page gets copied into:
   - :doc:`/editors/texture_node/types/groups`
   - :doc:`/modeling/geometry_nodes/group`
   - :doc:`/render/shader_nodes/groups`
.. --- copy below this line ---

*****
Group
*****

A :doc:`Group Node </interface/controls/nodes/groups>` combines a set of nodes into a single one,
and selectively exposes inputs and outputs of those nodes.

Group nodes can simplify a node tree by hiding away complexity and reusing functionality.

Group Input
===========

Exposes the inputs of the node group. You can have multiple of these nodes in your tree to keep it clean,
bringing in each input right where you need it (rather than dragging long links all across your graph).

The input slots can be edited in the *Group* tab of the *Sidebar*.

Group Output
============

Receives the outputs of the node group. You can have multiple of these nodes in your tree to keep it clean,
outputting each result right where it's produced (rather than dragging long links all across your graph).

The output slots can be edited in the *Group* tab of the *Sidebar*.


Node Groups
===========

This section lists all the node groups, both those in the current blend-file and those
:doc:`Linked or Appended </files/linked_libraries/link_append>` from another blend-file.


## Alpha Convert

.. index:: Compositor Nodes; Alpha Convert
.. _bpy.types.CompositorNodePremulKey:

******************
Alpha Convert Node
******************

.. figure:: /images/compositing_node-types_CompositorNodePremulKey.webp
   :align: right
   :alt: Alpha Convert Node.

The *Alpha Convert Node* converts the alpha channel format of an image.

For compositing and rendering, :term:`Premultiplied Alpha` is the standard in Blender.
Render layers will be premultiplied alpha, and images loaded into rendering
or compositing will be converted to this.

If you want to do a compositing operation with straight alpha,
the *Alpha Convert* node can be used. Typically this would be a color correction operation
where it might give better results working on RGB channels without alpha.
If the alpha is converted to straight in the Compositor,
it should be converted back to premultiplied before the *Composite Output* node,
otherwise some artifacts might occur.


Inputs
======

Image
   Standard color input.


Properties
==========

Mapping
   The direction of convert alpha.
   For details on the difference between both ways to store alpha values see :term:`Alpha Channel`.

   :To Premultiplied:
      Converts from :term:`Straight Alpha` to :term:`Premultiplied Alpha`.
   :To Straight:
      Converts from :term:`Premultiplied Alpha` to :term:`Straight Alpha`.


Outputs
=======

Image
   Standard color output.


## Color Ramp

.. index:: Compositor Nodes; Color Ramp
.. _bpy.types.CompositorNodeValToRGB:
.. Editors Note: This page gets copied into:
.. - :doc:`/render/shader_nodes/converter/color_ramp`
.. - :doc:`/modeling/geometry_nodes/utilities/color/color_ramp`
.. - :doc:`/editors/texture_node/types/converter`
.. --- copy below this line ---

***************
Color Ramp Node
***************

.. figure:: /images/compositing_node-types_CompositorNodeValToRGB.webp
   :align: right
   :alt: Color Ramp Node.

The Color Ramp Node is used for mapping values to colors using a gradient.


Inputs
======

Factor
   The value to map. 0.0 results in the leftmost color, while 1.0 results in the rightmost.


Properties
==========

Color Ramp
   See :ref:`ui-color-ramp-widget`.


Outputs
=======

Image/Color
   Standard color output.
Alpha
   Standard alpha output.


Examples
========

Creating an Alpha Mask
----------------------

An often overlooked use case of the Color Ramp is to turn a black-and-white image
into a colored image with transparency.

.. figure:: /images/compositing_types_converter_color-ramp_create-alpha-mask.png
   :width: 600px

In the example above, a black-and-white swirl image, which is lacking an alpha channel,
is fed into the Color Ramp node as a *Factor*.

The Color Ramp node is set to a purely transparent color on the left end of the gradient,
and a fully red color on the right. As you can see in the Viewer node,
the Color Ramp node outputs an image that is transparent where the input is black,
and opaque where the input is white.


Colorizing an Image
-------------------

In this example, multiple colors are added to the color gradient,
converting a black-and-white image into a flaming swirl.

.. figure:: /images/compositing_types_converter_color-ramp_colorizing-image.png
   :width: 600px

The shades of gray in the input image are mapped to three colors:
blue, yellow, and red, all fully opaque. Where the image is black,
the Color Ramp substitutes blue (the first color stop). Where it is some shade of gray,
the Color Ramp outputs a corresponding color from the gradient (bluish, yellow, to reddish).
Where the image is fully white, the Color Ramp outputs red.


## Convert Colorspace

.. index:: Compositor Nodes; Color Space
.. _bpy.types.CompositorNodeConvertColorSpace:

****************
Color Space Node
****************

.. figure:: /images/compositing_node-types_CompositorNodeConvertColorSpace.webp
   :align: right
   :alt: Color Space Node.

The *Color Space Node* converts images between :term:`color spaces <Color Space>`.

.. note::

    Images are already automatically converted into linear color space unless specified in the image's
    :ref:`Color Space <bpy.types.ColorManagedInputColorspaceSettings.name>` option.


Inputs
======

Image
   Standard color input.


Properties
==========

From, To
   The color space of the input image and the color space to convert the image to.

   The list of color spaces depends on the active :ref:`OCIO config <ocio-config>`.
   The default supported color spaces are described in detail here:
   :ref:`Default OpenColorIO Configuration <ocio-config-default-color-spaces>`


Outputs
=======

Image
   Standard color output.


## Index

.. _composite-nodes-color-index:

###############
  Color Nodes
###############

These nodes adjust the image's colors, for example increasing the contrast, making it warmer,
overlaying another image, etc.

.. toctree::
   :maxdepth: 1

   adjust/index.rst

----------

.. toctree::
   :maxdepth: 1

   mix/index.rst

----------

.. toctree::
   :maxdepth: 1

   alpha_convert.rst
   color_ramp.rst
   convert_colorspace.rst
   set_alpha.rst

----------

.. toctree::
   :maxdepth: 1

   invert_color.rst
   rgb_to_bw.rst


## Invert Color

.. index:: Compositor Nodes; Invert Color
.. _bpy.types.CompositorNodeInvert:
.. Editor's Note: This page gets copied into:
.. - :doc:`</render/shader_nodes/color/invert_color>`
.. - :doc:`</editors/texture_node/types/color/invert_color>`

.. --- copy below this line ---

*****************
Invert Color Node
*****************

.. figure:: /images/compositing_node-types_CompositorNodeInvert.webp
   :align: right
   :alt: Invert Color Node.

Inverts the colors in the input image, producing a negative.


Inputs
======

Factor
   The amount of influence the node exerts on the image.
Color
   Standard color input.


Properties
==========

In the compositing context, this node has the following properties:

RGB
   Invert the color channels.
Alpha
   Invert the alpha channel.


Outputs
=======

Color
   Standard color output.


Example
=======

.. figure:: /images/compositing_types_input_mask_example.png

   The Invert node is used to invert the mask.


## Rgb To Bw

.. index:: Compositor Nodes; RGB TO BW
.. _bpy.types.CompositorNodeRGBToBW:
.. Editor's Note: This page gets copied into:
.. - :doc:`</render/shader_nodes/converter/rgb_to_bw>`
.. - :doc:`</editors/texture_node/types/converter/rgb_to_bw>`

.. --- copy below this line ---

**************
RGB to BW Node
**************

.. figure:: /images/compositing_node-types_CompositorNodeRGBToBW.webp
   :align: right
   :alt: RGB to BW Node.

The *RGB to BW Node* makes a color image black-and-white by outputting its luminance.

.. note::

   You can directly connect Color sockets to Value sockets in node graphs,
   which also converts the image to black-and-white. As such, this node is
   not always necessary.

Inputs
======

Image
   Color image input.


Properties
==========

This node has no properties.


Outputs
=======

Value
   Grayscale value output.

.. (TODO add) examples of why this might be useful


## Set Alpha

.. index:: Compositor Nodes; Set Alpha
.. _bpy.types.CompositorNodeSetAlpha:

**************
Set Alpha Node
**************

.. figure:: /images/compositing_node-types_CompositorNodeSetAlpha.webp
   :align: right
   :alt: Set Alpha Node.

The *Set Alpha Node* adds an alpha channel to an image.


Inputs
======

Image
   Standard color input.
Alpha
   The amount of Alpha can be set for the whole image by using the input field or
   per pixel by connecting to the socket.


Properties
==========

.. _bpy.types.CompositorNodeSetAlpha.mode:

Mode
   Method to mix the alpha with the input *Image*.

   :Apply Mask:
      Multiply the input images RGBA channels by the *Alpha* input value.
      In this cases, the output is using :term:`Premultiplied Alpha`.
   :Replace Alpha:
      Replace the inputs alpha channel with the *Alpha* input value.
      In this cases, the output is using :term:`Straight Alpha`.


Outputs
=======

Image
   Standard color output.

.. note::

   This is not, and is not intended to be,
   a general-purpose solution to the problem of compositing an image that does not contain alpha information.
   You might wish to use "chroma keying" or "difference keying" (as discussed elsewhere) if you can.
   This node is most often used (with a suitable input being provided by means of the socket)
   in those troublesome cases when you *cannot*, for some reason, use those techniques directly.


Example
=======

Fade To Black
-------------

To transition the audience from one scene or shot to another,
a common technique is to "fade to black". As its name implies,
the scene fades to a black screen. You can also "fade to white" or whatever color you wish,
but black is a good neutral color that is easy on the eyes and intellectually "resets" the viewer's mind.
The node tree below shows how to do this using the Set Alpha node.

.. figure:: /images/compositing_types_converter_set-alpha_fade-to-black.png

   Fade to black.

In the example above, the alpha channel of the swirl image is ignored.
Instead, a :doc:`Time Curve node </compositing/types/input/scene/time_curve>`
introduces a factor from 0.0 to 1.0 over 60 frames, or about 2 seconds,
to the Set Alpha node. Note that the time curve is exponentially-shaped,
so that the overall blackness will fade in slowly and then accelerate toward the end.
The Set Alpha node does not need an input image; instead, the flat (shadeless) black color is used.
The Set Alpha Node uses the input factor and color to create a black image that has an alpha
set which goes from 0.0 to 1.0 over 60 frames, or completely transparent to completely opaque.
Think of alpha as a multiplier for how vivid you can see that pixel.
These two images are combined by the Alpha Over node completely (a *Factor* of 1.0)
to produce the composite image. The Set Alpha node will thus, depending on the frame being rendered,
produce a black image that has some amount of transparency.
Setup and animate, and you have an image sequence that fades to black over a two-second period.

.. note:: No Scene Information Used

   This example node tree does not use the Render Layer node.
   To produce this 2-second animation, no Blender scene information was used.
   This is an example of using Blender's powerful compositing abilities
   separate from its modeling and animation capabilities.
   (A Render Layer could be substituted for the Image layer,
   and the "fade-network" effect will still produce the same effect.)


Fade In a Title
---------------

To introduce your animation,
you will want to present the title of your animation over a background.
You can have the title fly in, or fade it in. To fade it in,
use the Set Alpha node with the Time Curve node as shown below.

.. figure:: /images/compositing_types_converter_set-alpha_fade-in-title.png

   Using Set Alpha to fade in a title.

In the above example, a Time curve provides the Alpha value to the input socket.
The current Render Layer node, which has the title in view, provides the image. As before,
the Alpha Over node mixes (using the alpha values)
the background swirl and the alpha title to produce the composite image.


Colorizing a BW Image
---------------------

.. figure:: /images/compositing_types_converter_set-alpha_colorizing-image.png

   Using Set Alpha to colorize an image.

In the example above, notice how the blue tinge of the render input colors the swirl.
You can use the Set Alpha node's color field with this kind of node tree to add a consistent color to a BW image.

In the example tree to the right,
use the *Alpha* value of the Set Alpha node to give a desired degree of colorization.
Thread the input image and the Set Alpha node into an Alpha Over node to colorize
any black-and-white image in this manner.


## Bright Contrast

.. index:: Compositor Nodes; Brightness/Contrast
.. _bpy.types.CompositorNodeBrightContrast:
.. Editor's Note: This page gets copied into:
.. - :doc:`</render/shader_nodes/color/bright_contrast>`

.. --- copy below this line ---

************************
Brightness/Contrast Node
************************

.. figure:: /images/compositing_node-types_CompositorNodeBrightContrast.webp
   :align: right
   :alt: Brightness/Contrast Node.


Inputs
======

Image
   Standard color input.
Brightness
   An additive-type factor by which to increase the overall brightness
   of the image. Use a negative number to darken an image.
Contrast
   A scaling type factor by which to make brighter pixels brighter, but keeping the darker pixels dark.
   Higher values make details stand out. Use a negative number to decrease the overall contrast in the image.


Properties
==========

Convert Premultiplied
   By default, it is supposed to work in *premultiplied* alpha.
   If the *Convert Premul* checkbox is not enabled, it is supposed to work in *straight* alpha.

   See :term:`Alpha Channel`.


Outputs
=======

Image
   Standard color output.


Notes
=====

It is possible that this node will put out a value set that has values beyond the normal range,
i.e. values greater than one and less than zero.
If you will be using the output to mix with other images in the normal range,
you should clamp the values using the Map Value node (with the Min and Max enabled),
or put through a Color Ramp node (with all normal defaults).

.. figure:: /images/compositing_types_color_bright-contrast_clamp-values.png
   :width: 600px

   Clamp the values to normal range.

Either of these nodes will scale the values back to normal range.
In the example image, we want to intensify the specular pass.
The bottom thread shows what happens if we do not clamp the values;
the specular pass has a value much less than one in the dark areas;
when added to the medium gray, it makes black. Passing the brightened image through either
the Map Value or the Color Ramp node produces the desired effect.


Example
=======

.. figure:: /images/compositing_types_color_bright-contrast_basic-example.png
   :width: 600px

   A basic example.


## Color Balance

.. index:: Compositor Nodes; Color Balance
.. _bpy.types.CompositorNodeColorBalance:

******************
Color Balance Node
******************

The Color Balance node adjusts the color and values of an image.

.. figure:: /images/compositing_node-types_CompositorNodeColorBalance.webp
   :alt: Color Balance Node.


Inputs
======

Factor
   Controls the amount of influence the node exerts on the output image.
Color
   Standard color input.


Properties
==========

Two different correction formulas could be selected.

Lift/Gamma/Gain
   Lift
      Increases the value of dark colors.
   Gamma
      Adjusts midtones.
   Gain
      Adjusts highlights.

Offset/Power/Slope (ASC-CDL)
   Offset
      Summand. (Adjusts the overall brightness.)

      Basis
         Additional offset, allows to specify a negative Offset value.
   Power
      Over-all exponent. (Adjusts the midtones.)
   Slope
      Multiplier. (Adjusts the highlights.)


Outputs
=======

Color
   Standard output image.


Advanced
========

The Offset/Power/Slope Formula
------------------------------

*out* = (*i* × *s* + *o*)\ :sup:`p`

where:

- *out*: The color graded pixel code value.
- *i*: The input pixel code value (0 to 1) (black to white).
- *s*: Slope (any number 0 or greater, nominal value is 1.0).
- *o*: Offset (any number, the nominal value is 0).
- *p*: Power (any number greater than 0, nominal value is 1.0).


## Color Correction

.. index:: Compositor Nodes; Color Correction
.. _bpy.types.CompositorNodeColorCorrection:

*********************
Color Correction Node
*********************

.. figure:: /images/compositing_node-types_CompositorNodeColorCorrection.webp
   :alt: Color Balance Node.

The Color Correction node adjusts the color of an image, separately in several tonal ranges
(highlights, midtones and shadows).


Properties
==========

Red, Green, Blue
   Specifies which RGB channels will be affected by the correction.


Correction Tools (Columns)
--------------------------

Saturation
   Adjusts the image's saturation.
Contrast
   Adjust image contrast.
Gamma
   Exponential gamma correction, affecting the midtones of the image. (Works like Power in the Color Balance node.)
Gain
   Multiplier, stronger influence on the highlights. (Works like Slope in the Color Balance node.)
Lift
   This value (can be negative) will be added (+), linear lightens or darkens the image.
   (Works like *Offset* in the Color Balance node.)


Tonal Ranges (Rows)
-------------------

Master
   These sliders affect the entire tonal range.
Highlights
   These sliders only affect the highlights.
Midtones
   These sliders only affect the midtones.
Shadows
   Affects the dark tones of an image often affecting the shadows.

Midtones Start, Midtones End
   Defines the start and the end of midtones range, i.e.
   values where the whole tonal range is divided into the highlights, midtones and shadows
   (there is also a smooth transition between the ranges of width 0.2 units).


Inputs
======

Image
   Standard color input.
Mask
   Controls the amount of influence the node exerts on the output image.


Outputs
=======

Color
   Standard color output.


## Exposure

.. index:: Compositor Nodes; Exposure
.. _bpy.types.CompositorNodeExposure:

*************
Exposure Node
*************

.. figure:: /images/compositing_node-types_CompositorNodeExposure.webp
   :align: right
   :alt: Exposure Node.

The Exposure Node adjusts the brightness of an image using a camera exposure parameter.

.. seealso::

   The exposure can also be adjusted in the scene :ref:`Color Management <render-post-color-management>`.


Inputs
======

Image
   Standard color input.
Exposure
   Scalar factor to adjust the exposure of the image.


Properties
==========

This node has no properties.


Outputs
=======

Image
   Standard color output.


Examples
========

In the example below, the Exposure node is used to increase the brightness of the window area using a mask.

.. figure:: /images/compositing_types_color_exposure_example.png

   Example of an Exposure node.


## Gamma

.. index:: Compositor Nodes; Gamma
.. _bpy.types.CompositorNodeGamma:
.. Editor's Note: This page gets copied into:
.. - :doc:`</render/cycles/nodes/types/color/gamma>`

.. --- copy below this line ---

**********
Gamma Node
**********

.. figure:: /images/compositing_node-types_CompositorNodeGamma.webp
   :align: right
   :alt: Gamma Node.

Use this node to apply a gamma correction.


Inputs
======

Image
   Standard color input.
Gamma
   An exponential brightness factor.


Properties
==========

This node has no properties.


Outputs
=======

Image
   Standard color output.


Examples
========

.. figure:: /images/compositing_types_color_gamma_example.jpg
   :width: 700px

   Example of a Gamma node.


## Hue Correct

.. index:: Compositor Nodes; Hue Correct
.. _bpy.types.CompositorNodeHueCorrect:

****************
Hue Correct Node
****************

The *Hue Correct Node* adjusts the hue, saturation, and value of an image,
with an input curve.

.. figure:: /images/compositing_node-types_CompositorNodeHueCorrect.webp
   :alt: Hue Correct Node.


Inputs
======

Factor
   Controls the amount of influence the node exerts on the output image.
Image
   Standard color input.


Properties
==========

Level
   H (Hue), S (Saturation), V (Value)
Curve
   For the curve controls see: :ref:`Curve widget <ui-curve-widget>`.
   By default, the curve is a straight line, meaning there is no change.
   The spectrum allows you to raise or lower HSV levels for each range of pixel colors.
   To change an H, S, or V level, move the curve points up or down. Pixels with hue values each
   point in the horizontal position of the graph will be changed depending on the shape of the curve.


Outputs
=======

Image
   Standard color output.

.. TODO <2.8 explain all options


## Hue Saturation

.. index:: Compositor Nodes; Hue/Saturation/Value
.. _bpy.types.CompositorNodeHueSat:
.. Editor's Note: This page gets copied into:
.. - :doc:`</render/shader_nodes/color/hue_saturation>`
.. - :doc:`</editors/texture_node/types/color/hue_saturation>`

.. --- copy below this line ---

*************************
Hue/Saturation/Value Node
*************************

.. figure:: /images/compositing_node-types_CompositorNodeHueSat.webp
   :align: right
   :alt: Hue/Saturation/Value Node.

The *Hue/Saturation/Value Node* applies a color transformation in the HSV :term:`Color Model`.


Inputs
======

Factor
   The amount of influence the node exerts on the image.
Image/Color
   Standard color input.
Hue
   The hue rotation offset, from 0 (-180°) to 1 (+180°). Note that
   0 and 1 have the same result.
Saturation
   A value of 0 removes color from the image, making it black-and-white.
   A value greater than 1.0 increases saturation.
Value
   The value shift. 0 makes the color black, 1 keeps it the same, and higher
   values make it brighter.

Outputs
=======

Image/Color
   Standard color output.


Hue/Saturation Tips
===================

Some things to keep in mind that might help you use this node better:

Hues are laid out on a circle
   If you apply a Hue offset of 1 (+180°) to a blue image, you get the diametrically opposite
   color, which is yellow. If you apply a Hue offset of 1 to that yellow image, you get blue again.
Grayscale images have no hue
   Trying to change the Hue or Saturation of a grayscale image has no effect. You can only brighten
   or darken it by adjusting the Value. To add color, use the Mix node instead.
Changing the effect over time
   The different values can be animated using a *Time Curve* node or by setting keyframes.


HSV Example
===========

.. figure:: /images/compositing_types_color_hue-saturation_example.jpg
   :width: 700px

   A basic example.

.. figure:: /images/compositing_types_input_mask_example.png
   :width: 700px

   An example of using the Factor input for masking.


## Index


##########
  Adjust
##########

.. toctree::
   :maxdepth: 1

   bright_contrast.rst
   color_balance.rst
   color_correction.rst
   exposure.rst
   gamma.rst
   hue_correct.rst
   hue_saturation.rst
   rgb_curves.rst
   tone_map.rst


## Rgb Curves

.. index:: Compositor Nodes; RGB Curves
.. _bpy.types.CompositorNodeCurveRGB:

.. Editor's Note: This page gets copied into:
.. - :doc:`</render/shader_nodes/color/rgb_curves>`
.. - :doc:`</editors/texture_node/types/color/rgb_curves>`
.. - :doc:`</modeling/geometry_nodes/utilities/color/rgb_curves>`

.. --- copy below this line ---

***************
RGB Curves Node
***************

.. figure:: /images/compositing_node-types_CompositorNodeCurveRGB.webp
   :align: right
   :alt: RGB Curves Node.

The *RGB Curves Node* performs level adjustments on each color channel.


Inputs
======

Factor
   Controls the amount of influence the node exerts on the image.
Image/Color
   Standard color input.
Black Level :guilabel:`Compositor Only`
   Defines the input color that should be mapped to black.
White Level :guilabel:`Compositor Only`
   Defines the input color that should be mapped to white.

.. container:: lead

   .. clear

.. tip::

   To define the black and white levels,
   use the :ref:`eyedropper <ui-eyedropper>` to select a color sample of a displayed image.


Properties
==========

Tone :guilabel:`Compositor Only`
   :Standard: The Combined curve is applied to each channel individually, which may result in a change of hue.
   :Filmlike: Keeps the hue constant.

Channel
   The curve to show.

   :C: Combined
   :R: Red
   :G: Green
   :B: Blue

Curve
   A Bézier curve that maps each input level (X axis) to an output level (Y axis).
   For the curve controls, see :ref:`Curve widget <ui-curve-widget>`.


Outputs
=======

Image/Color
   Standard color output.


Examples
========

Below are some common curves you can use to achieve desired effects.

.. figure:: /images/compositing_types_color_rgb-curves_example-common-use.png
   :width: 600px

   From left to right: 1. Lighten shadows 2. Negative 3. Decrease contrast 4. Posterize.


Color Correction using Curves
-----------------------------

.. figure:: /images/compositing_types_color_rgb-curves_example-rgb.png
   :width: 600px

   Color correction with curves.

In this example, the image has too much red in it,
so we run it through an *RGB Curves* node and reduce the Red channel.

The documentation for the :doc:`/compositing/types/color/mix/mix_color` has an additional
example about fixing overexposure.


Color Correction using Black/White Levels
-----------------------------------------

.. figure:: /images/compositing_types_color_rgb-curves_black-white-levels.png
   :width: 600px

   Color correction with Black/White Levels.

Manually adjusting the RGB curves for color correction can be difficult.
Another option for color correction is to use the Black and White Levels instead,
which really might be their main purpose.

In this example,
the White Level is set to the color of a bright spot of the sand in the background,
and the Black Level to the color in the center of the fish's eye.
To do this efficiently it is best to bring up the Image Editor showing the original input image.
You can then use the levels' color picker to easily choose
the appropriate colors from the input image, zooming into pixel level if necessary.
The result can be fine-tuned with the R, G, and B curves like in the previous example.

The curve for C is used to compensate for the increased contrast that is a side effect of
setting Black and White Levels.


Effects
-------

.. figure:: /images/compositing_types_color_rgb-curves_ex.png
   :width: 620px

   Changing colors by inverting the red channel.


## Tone Map

.. index:: Compositor Nodes; Tone Map
.. _bpy.types.CompositorNodeTonemap:

*************
Tone Map Node
*************

.. figure:: /images/compositing_node-types_CompositorNodeTonemap.webp
   :align: right
   :alt: Tone Map Node.

Tone mapping is used to map high dynamic range colors into a more limited dynamic
range supported by the display, while preserving the appearance as much as possible.

This is a legacy node. It is recommended to use view transforms in the
color management settings instead, and output linear high dynamic range images
from the compositor instead of low dynamic range.


Inputs
======

Image
   :abbr:`HDR (High Dynamic Range)` image.


Properties
==========

Type
   Rh Simple
      Key
         The value the average luminance is mapped to.
      Offset
         Normally always 1, but can be used as an extra control to alter the brightness curve.
      Gamma
         If not used, set to 1.

   R/D Photoreceptor
      Intensity
         If less than zero, darkens image; otherwise, makes it brighter.
      Contrast
         Set to 0 to use estimate from input image.
      Adaptation
         If 0, global; if 1, based on pixel intensity.
      Color Correction
         If 0, same for all channels; if 1, each independent.


Outputs
=======

Image
   :abbr:`LDR (Low Dynamic Range)` image.


## Alpha Over

.. index:: Compositor Nodes; Alpha Over
.. _bpy.types.CompositorNodeAlphaOver:

***************
Alpha Over Node
***************

.. figure:: /images/compositing_node-types_CompositorNodeAlphaOver.webp
   :align: right
   :alt: Alpha Over Node.

The *Alpha Over* node is used to layer images on top of one another.
Where the foreground image pixels have an alpha greater than 0, it will be overlaid over the background image.


Inputs
======

Factor
   Controls the transparency of the foreground image.
   A factor less than 1 will make the foreground more transparent.
Image
   Input for the *background* image.
Image
   Input for the *foreground* image.


Properties
==========

Convert Premultiplied
   Converts foreground image to :term:`Premultiplied Alpha` format.

   The *Alpha Over* node is designed to work with premultiplied alpha color format.
   Use this checkbox when you know that your image has :term:`Straight Alpha` color values,
   to perform the correct over operation. Result will still be premultiplied alpha.

Premultiply
   Mix between using :term:`Premultiplied Alpha` or :term:`Straight Alpha`.

   When set to 1, the foreground color values will be multiplied by alpha, i.e. premultiplied;
   this is equivalent to enabling *Convert Premultiplied*.
   When set to 0, color values does not change.

   If *Premultiply* is not zero, *Convert Premultiplied* will be ignored.

   .. note:: This is a legacy option.


Outputs
=======

Image
   Standard color output.


Examples
========

Overlay
-------

In the node tree below, *Color Ramp* node is used to add an alpha channel to the black-and-white swirl image.
Then *Alpha Over* node is used to overlay it on top of another image.

.. figure:: /images/compositing_types_converter_color-ramp_create-alpha-mask.png
   :width: 600px

   Assembling a composite image using Alpha Over.


Fade In
-------

In the next example, the *Factor* is used to make a "Fade In" effect.
This effect can be animated by adding a *Time* node inputted in the *Factor* socket as shown below.
Over the course of 30 frames, the *Alpha Over* node outputs an image that
starts with the pure background image, and the title slowly appearing.

.. figure:: /images/compositing_types_color_alpha-over_example.png
   :width: 600px

   Animated fade in effect using Alpha Over.

Note the *Convert Premultiply* checkbox is enabled,
since as the foreground used a PNG image that has straight alpha.


## Combine Color

.. index:: Compositor Nodes; Combine Color
.. Editor's Note: This page gets copied into :doc:`</render/cycles/nodes/types/converter/combine_separate>`
.. _bpy.types.CompositorNodeCombineColor:

******************
Combine Color Node
******************

.. figure:: /images/node-types_FunctionNodeCombineColor.webp
   :align: right
   :alt: Combine Color Node.

The *Combine Color Node* combines an image from its composite color channels.
The node can combine multiple :term:`Color Models <Color Model>` depending on the Mode property.


Inputs
======

The outputs of this node depends on the Mode property (see below).

Alpha
   The color channel that is responsible for the image's transparency.


Properties
==========

Mode
   The color model to output.

   :RGB: Combine the three inputs: Red, Green, and Blue color channels into a single image.
   :HSV: Combine the three inputs: Hue, Saturation, and Value color channels into a single image.
   :HSL: Combine the three inputs: Hue, Saturation, and Lightness color channels into a single image.
   :YCbCrA:
      Combine the three inputs: Luminance, Chrominance Blue, and Chrominance Red color channels into a single image.

      Color Space
         ITU 601, ITU 709, JPEG
   :YUV: Combine the three inputs: Luminance, U chrominance, and V chrominance color channels into a single image.


Output
======

Image
   Standard image output.


Examples
========

Blur Alpha
----------

.. figure:: /images/compositing_types_converter_combine-separate_example-combine-rgba.png
   :width: 640px

   An example of blurring the alpha channel.

In this first example, we take the Alpha channel and blur it,
and then combine it back with the colors. When placed in a scene,
the edges of it will blend in, instead of having a hard edge.
This is almost like :term:`Anti-Aliasing` but in a three-dimensional sense.
Use this node setup, when adding CG elements to live action to remove any hard edges.
Animating this effect on a broader scale will make the object appear to "phase" in and out,
as an "out-of-phase" time-traveling sync effect.


Increase Luminance
------------------

.. figure:: /images/compositing_types_converter_math_multiply.png

   An example of the scaling the Luminance channel.

This example has a *Math (Multiply)* node increasing the luminance channel (Y)
of the image to make it brighter.

.. tip::

   If running these channels through a *Color Ramp* node to adjust value,
   use the Cardinal scale for accurate representation.
   Using the Exponential scale on the luminance channel gives a high-contrast effect.


## Index


#######
  Mix
#######

.. toctree::
   :maxdepth: 1

   alpha_over.rst

----------

.. toctree::
   :maxdepth: 1

   combine_color.rst
   separate_color.rst

----------

.. toctree::
   :maxdepth: 1

   mix_color.rst
   z_combine.rst


## Mix Color

.. index:: Compositor Nodes; Mix
.. _bpy.types.CompositorNodeMixRGB:
.. Editor's Note: This page gets copied into:
.. - :doc:`</render/shader_nodes/color/mix>`
.. - :doc:`</modeling/geometry_nodes/utilities/color/mix_rgb>`
.. - :doc:`</editors/texture_node/types/color/mix_rgb>`

.. --- copy below this line ---

********
Mix Node
********

.. figure:: /images/compositing_node-types_CompositorNodeMixRGB.webp
   :align: right
   :alt: Mix Node.

Blends two images together, much like how an image editing program blends two layers.

  .. important::

     As of Blender 3.4, this node has been updated in the Shader and Geometry node editors.
     Files saved with the new node are not backward compatible.

Inputs
======

Factor
   The opacity of the foreground image.
Image/A/Color1
   The background image. Determines the dimensions of the output.
Image/B/Color2
   The foreground image.

Keep in mind that, unlike image editing programs where the foreground layer is on top,
the foreground slot in Blender is on the bottom.

Properties
==========

Data Type :guilabel:`Shader Editor` :guilabel:`Geometry Node Editor`
   The type of data to mix: Float, Vector, or Color.
Factor Mode :guilabel:`Shader Editor` :guilabel:`Geometry Node Editor`
   Uniform
      The same single Factor is applied to all three Vector coordinates.
   Non-Uniform
      You can specify a different Factor for each Vector coordinate.
Blending Mode
   The :term:`blending mode <Color Blend Modes>` to use.

   Mix
      Regular alpha blending. Typically called *Normal* in image editing programs.
   `Darken <https://docs.krita.org/en/reference_manual/blending_modes/darken.html#bm-darken>`__
      For each color component, takes the smallest of the two values being blended.
   `Multiply <https://docs.krita.org/en/reference_manual/blending_modes/arithmetic.html#bm-multiply>`__
      Multiplies the colors component by component. Blending with a white pixel
      (value 1.0) has no effect, while blending with a black one (0.0) always
      results in black.
   `Color Burn <https://docs.krita.org/en/reference_manual/blending_modes/darken.html#bm-color-burn>`__
      Inverts the background color, divides it by the foreground color, and inverts the result.
   `Lighten <https://docs.krita.org/en/reference_manual/blending_modes/lighten.html#bm-lighten>`__
      For each color component, takes the largest of the two values being blended.
   `Screen <https://docs.krita.org/en/reference_manual/blending_modes/lighten.html#bm-screen>`__
      Inverts both colors, multiplies them, and inverts the result.
   `Color Dodge <https://docs.krita.org/en/reference_manual/blending_modes/lighten.html#bm-color-dodge>`__
      Divides the background color by the inverted foreground color.
   `Add <https://docs.krita.org/en/reference_manual/blending_modes/arithmetic.html#addition>`__
      Adds the two colors together.
   `Overlay <https://docs.krita.org/en/reference_manual/blending_modes/mix.html#overlay>`__
      Applies Multiply blending if the foreground color's lightness is below 0.5,
      or Screen blending if it's above.
   `Soft Light <https://docs.krita.org/en/reference_manual/blending_modes/lighten.html#bm-soft-light>`__
      Like Overlay, but more subtle.
   `Linear Light <https://docs.krita.org/en/reference_manual/blending_modes/lighten.html#bm-linear-light>`__
      Applies Linear Burn blending (background + foregound - 1) if the foreground color's lightness
      is below 0.5, or Linear Dodge (background + foreground) if it's above.
   `Difference <https://docs.krita.org/en/reference_manual/blending_modes/negative.html#bm-difference>`__
      For each component, subtracts the lower value from the higher value.
   `Exclusion <https://docs.krita.org/en/reference_manual/blending_modes/negative.html#bm-exclusion>`__
      Adds the two colors, then subtracts their multiple twice.
   `Subtract <https://docs.krita.org/en/reference_manual/blending_modes/arithmetic.html#subtract>`__
      Subtracts the foreground color from the background color.
   `Divide <https://docs.krita.org/en/reference_manual/blending_modes/arithmetic.html#divide>`__
      Divides the background color by the foreground color.
   `Hue <https://docs.krita.org/en/reference_manual/blending_modes/hsx.html#bm-hue>`__
      Combines the saturation and value of the background color with the hue of the foreground color.
   `Saturation <https://docs.krita.org/en/reference_manual/blending_modes/hsx.html#bm-saturation>`__
      Combines the hue and value of the background color with the saturation of the foreground color.
   `Color <https://docs.krita.org/en/reference_manual/blending_modes/hsx.html#bm-color>`__
      Combines the value of the background color with the hue and saturation of the foreground color.
   `Value <https://docs.krita.org/en/reference_manual/blending_modes/hsx.html#bm-luminosity>`__
      Combines the hue and saturation of the background color with the value of the foreground color.
Use Alpha
   Whether to use the alpha channel of the foreground image during mixing.
   The alpha channel of the background image is always used.
Clamp/Clamp Result
   Clamp the output value to the [0.0, 1.0] range.
Clamp Factor :guilabel:`Shader Editor` :guilabel:`Geometry Node Editor`
   Clamp the Factor to the [0.0, 1.0] range.

Outputs
=======

Image/Result/Color
   The result of the mixing operation.


Examples
========

Below are examples of blending modes, as well as some practical use cases.

.. figure:: /images/compositing_types_color_mix_blend-modes.png
   :width: 700px

   Blending a colored pattern with a flat color (top row) and a circular mask (bottom row).

Fixing overexposure
-------------------

The Compositing setup below shows how to fix an overexposed render by
darkening it and increasing contrast.

.. figure:: /images/compositing_types_color_mix_contrast-enhancement.png
   :width: 700px

   Example node setup showing two RGB Curves nodes and a Mix node for composition.

The top :doc:`/compositing/types/color/adjust/rgb_curves` darkens the image by linearly scaling each
color value to a smaller one.

The bottom curve node increases constract by making small values smaller and large values larger.

Finally, the Mix node blends the two together.


Watermark Images
----------------

In the old days, a pattern was pressed into the paper mush as it dried,
creating a mark that identified who made the paper and where it came from.
The mark was barely perceptible except in just the right light.
Probably the first form of subliminal advertising.

Nowadays, people watermark their images to identify them as personal intellectual property,
for subliminal advertising of the author or hosting service,
or simply to track their image's proliferation throughout the web.

Blender provides a complete set of tools for you to both encode your watermark
and to tell if an image has your watermark.


Encoding your Watermark in an Image
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

First, construct your own personal watermark.
You can use your name, a word, or a shape or image not easily replicated.
While neutral gray works best using the encoding method suggested,
you are free to use other colors or patterns.
It can be a single pixel or a whole gradient; it is up to you.

In the example below, we are encoding the watermark in a specific location
in the image using the *Translate* node;
this helps later because we only have to look at a specific location for the mark.
We then use the *RGB to BW node* to convert the color image to grayscale numbers,
which we then feed into the *Map Range* node to reduce the mark to one-tenth of
its original intensity.

The *Add* node (*Mix* node with blending mode *Add*) adds the corresponding pixels,
making the ones containing the mark ever-so-slightly brighter.

.. figure:: /images/compositing_types_color_mix_watermark-encode.png
   :width: 700px

   Embedding a watermark in an image.

Of course, if you *want* people to notice your mark, do not scale it so much,
or make it a contrasting color. There are also many other ways,
using other mix settings and fancier rigs. Feel free to experiment!


Decoding an Image for your Watermark
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

When you see an image that you think might be yours,
use the node tree below to compare it to your stock image (pre-watermarked original).
In this tree, the *Mix* node is set to Difference,
and the *Map Value* node amplifies any difference.
You can see how the original mark clearly stands out.

.. figure:: /images/compositing_types_color_mix_watermark-decode.png
   :width: 700px

   Checking an image for your watermark.


## Separate Color

.. index:: Compositor Nodes; Separate Color
.. Editor's Note: This page gets copied into :doc:`</render/cycles/nodes/types/converter/combine_separate>`
.. _bpy.types.CompositorNodeSeparateColor:

*******************
Separate Color Node
*******************

.. figure:: /images/node-types_FunctionNodeSeparateColor.webp
   :align: right
   :alt: Separate Color Node.

The *Separate Color Node* splits an image into its composite color channels.
The node can output multiple :term:`Color Models <Color Model>` depending on the Mode property.


Inputs
======

Image
   Standard image input.


Properties
==========

Mode
   The color model to output.

   :RGB: Split the input image into it's three outputs: Red, Green, and Blue color channels.
   :HSV: Split the input image into it's three outputs: Hue, Saturation, and Value color channels.
   :HSL: Split the input image into it's three outputs: Hue, Saturation, and Lightness color channels.
   :YCbCrA:
       Split the input image into it's three outputs:
       Luminance, Chrominance Blue, and Chrominance Red color channels.

      Color Space
         ITU 601, ITU 709, JPEG
   :YUV:
      Split the input image into it's three outputs:
      Luminance, U chrominance, and V chrominance color channels.


Outputs
=======

The outputs of this node depends on the Mode property (see above).

Alpha
   The color channel that is responsible for the image's transparency.


Examples
========

Blur Alpha
----------

.. figure:: /images/compositing_types_converter_combine-separate_example-combine-rgba.png
   :width: 640px

   An example of blurring the alpha channel.

In this first example, we take the Alpha channel and blur it,
and then combine it back with the colors. When placed in a scene,
the edges of it will blend in, instead of having a hard edge.
This is almost like :term:`Anti-Aliasing` but in a three-dimensional sense.
Use this node setup, when adding CG elements to live action to remove any hard edges.
Animating this effect on a broader scale will make the object appear to "phase" in and out,
as an "out-of-phase" time-traveling sync effect.


Increase Luminance
------------------

.. figure:: /images/compositing_types_converter_math_multiply.png

   An example of the scaling the Luminance channel.

This example has a *Math (Multiply)* node increasing the luminance channel (Y)
of the image to make it brighter.

.. tip::

   If running these channels through a *Color Ramp* node to adjust value,
   use the Cardinal scale for accurate representation.
   Using the Exponential scale on the luminance channel gives a high-contrast effect.


## Z Combine

.. index:: Compositor Nodes; Z Combine
.. _bpy.types.CompositorNodeZcombine:

**************
Z Combine Node
**************

.. figure:: /images/compositing_node-types_CompositorNodeZcombine.webp
   :align: right
   :alt: Z Combine Node.

The Z Combine node combines two images based on their Z-depth maps.
It overlays the images using the provided Z values to
detect which parts of one image are in front of the other.


Inputs
======

Image
   The background image.
Z
   Z depth of the background image.
Image
   The foreground image.
Z
   Z depth of the foreground image.


Properties
==========

Use Alpha
   The chosen Image pixel alpha channel is also carried over.
   If a pixel is partially or totally transparent,
   the result of the Z Combine will also be partially transparent;
   in which case the background image will show through the foreground (chosen) pixel.
Anti-Alias Z
   Applies :term:`Anti-Aliasing` to avoid artifacts at sharp edges or areas with a high contrast.


Outputs
=======

Image
   If both Z values are equal, it will use the foreground image.
   Whichever Z value is less decides which image pixel is used.
   See :term:`Z-buffer`.
Z
   The combined Z depth, which allows to thread multiple Z-combines together.


Examples
========

.. figure:: /images/compositing_types_color_z-combine_example-1.png
   :width: 700px

   Choosing closest pixels.

In the example above, the render output from two scenes are mixed using the Z Combine node,
one from a sphere of size 1.3, and the other a cube of size 1.0.
The sphere and square are located at the same place. The cube is tipped forward,
so the corner in the center is closer to the camera than the sphere surface;
so Z Combine chooses to use the cube's pixels. But the sphere is slightly larger
(a size of 1.3 versus 1.0), so it does not fit totally inside the cube. At some point,
as the cube's sides recede back away from the camera, the sphere's sides are closer.
When this happens, Z Combine uses the sphere's pixels to form the resulting picture.

This node can be used to combine a foreground with a background matte painting.
Walt Disney pioneered the use of multi-plane mattes, where three or four partial mattes were
painted on glass and placed on the left and right at different Z positions; minimal camera
moves to the right created the illusion of depth as Bambi moved through the forest.

.. note:: Valid Input

   Z Input Sockets do not accept fixed values; they must get a vector set (see Map Value node).
   Image Input Sockets will not accept a color since they do not have UV coordinates.

.. figure:: /images/compositing_types_color_z-combine_example-2.png
   :width: 700px

   Mix and match images.

The Z Combine can be used to merge two images as well.
Using the Z values from the sphere and cube scenes above, but inputting different images,
yields the example to the right.

.. figure:: /images/compositing_types_color_z-combine_example-3.png
   :width: 700px

   Z Combine in action.

In this node setup a render scene is mixed with a flat image. In the side view of the scene,
the orange cube is 10 units away from the camera, and the blue ball is 20.
The 3D cursor is about 15 units away from the camera. The image is Z-in at a location of 15,
thus inserting it in between the cube and the ball.
The resulting image appears to have the cube on the green image.

.. note:: Invisible Man Effect

   If a foreground image with a higher Alpha than the background,
   is then mixed in the Z Combine with a slightly magnified background,
   the outline of the transparent area will distort the background,
   enough to make it look like seeing a part of the background through
   an invisible yet Fresnel-lens object.


## Anti Aliasing

.. index:: Compositor Nodes; Anti-Aliasing
.. _bpy.types.CompositorNodeAntiAliasing:

******************
Anti-Aliasing Node
******************

.. figure:: /images/compositing_node-types_CompositorNodeAntiAliasing.webp
   :align: right
   :alt: Anti-Aliasing Node.

The Anti-Aliasing node smooths away jagged edges.


Inputs
======

Image
   Standard color input.


Properties
==========

Threshold
   Controls edge detection sensitivity across the whole image.

Contrast Limit
   Controls contrast level to consider when detecting edges.

   The human eye does not perceive all edges equally. For instance,
   it tends to mask low contrast edges in the presence of much higher contrasts in the surrounding area.
   Therefore, applying anti-aliasing to unperceived edges will produce artifacts.
   This option quantifies the difference between low contrast and high contrast neighboring edges.

Corner Rounding
   Detect corners to help preserve the original shape.
   Setting *Corner Rounding* to 0 means no corner detection and no corner rounding will take place.
   The higher the value the better corners will be preserved, i.e. resemble original image.


Outputs
=======

Image
   Standard color output.


Examples
========

.. list-table:: The Anti-Aliasing node has three properties shown here.

   * - .. figure:: /images/compositing_types_filter_antialiasing-node_example-1-threshold.gif
          :align: center

          Changing threshold affects all edges.

     - .. figure:: /images/compositing_types_filter_antialiasing-node_example-2-contrast_limit.gif
          :align: center

          Changing contrast limit affects neighboring edges below contrast limit.

.. list-table:: The effect of corner rounding.

   * - .. figure:: /images/compositing_types_filter_antialiasing-node_example-3-corner_rounding-off.png

          Corner detection and rounding off (set to 0).
          Notice how corners are smoothed because they are treated as artifacts.

     - .. figure:: /images/compositing_types_filter_antialiasing-node_example-3-corner_rounding-on.png

          Full corner detection and rounding preserves the sharp edges around the corner.


## Denoise

.. index:: Compositor Nodes; Denoise
.. _bpy.types.CompositorNodeDenoise:

************
Denoise Node
************

.. figure:: /images/compositing_node-types_CompositorNodeDenoise.webp
   :align: right
   :alt: Denoise Node.

The Denoise node is used to denoise renders from :doc:`Cycles </render/cycles/index>`
and other ray tracing renderers. This helps to significantly reduce render time by
rendering with fewer samples.

It uses `Open Image Denoise <https://www.openimagedenoise.org/>`__,
which transforms noisy images into clean images with machine learning.


Inputs
======

Image
   Noisy image input.
Normal
   Optional normal render pass to better preserve detail.
   For Cycles, it is recommended to use the Denoising Normal render pass,
   which is available when enabling the Denoising Data passes.
Albedo
   Optional albedo render pass to better preserve detail.
   For Cycles, it is recommended to use the Denoising Albedo render pass,
   which is available when enabling the Denoising Data passes.


Properties
==========

Prefilter
   :None:
      Does not apply any prefiltering to the input passes. This option retains the most detail and
      is the fastest, but assumes the input passes are noise free which may require a high sample
      count. If the input passes are not noise free, then noise will remain in the image after denoising.
   :Fast:
      Assumes the input passes are not noise free, yet does not apply prefiltering to the input passes.
      This option is faster than *Accurate* but produces a blurrier result.
   :Accurate:
      Prefilters the input passes before denoising to reduce noise. This option usually produces
      more detailed results than *Fast* with increased processing time.
HDR
   Preserve colors outside the 0 to 1 range.


Outputs
=======

Image
   Denoised image output.


Examples
========

.. figure:: /images/compositing_types_filter_denoise_example.jpg

   Render before and after denoising, with a very low number of samples as input.
   As more samples are used, the denoiser will be able to better preserve detail.


## Despeckle

.. index:: Compositor Nodes; Despeckle
.. _bpy.types.CompositorNodeDespeckle:

**************
Despeckle Node
**************

.. figure:: /images/compositing_node-types_CompositorNodeDespeckle.webp
   :align: right
   :alt: Despeckle Node.

The *Despeckle node* is used to smooth areas of an image in which noise is noticeable,
while leaving complex areas untouched.

This works by the standard deviation of each pixel and its neighbors is calculated to determine
if the area is one of high complexity or low complexity.
If the complexity is lower than the threshold then the area is smoothed using a simple mean filter.


Inputs
======

Factor
   Controls the amount the filter effects the image.
Image
   Standard color input.


Properties
==========

Threshold
   The threshold to control high/low complexity.
Neighbor
   The threshold to control the number of pixels that must match.


Outputs
=======

Image
   Standard color output.


## Dilate Erode

.. index:: Compositor Nodes; Dilate/Erode
.. _bpy.types.CompositorNodeDilateErode:

*****************
Dilate/Erode Node
*****************

.. figure:: /images/compositing_node-types_CompositorNodeDilateErode.webp
   :align: right
   :alt: Dilate/Erode Node.

The *Dilate/Erode node* expands and shrinks masks, using a morphological operator.


Inputs
======

Mask
   Single color channel (or a black-and-white image) input.


Properties
==========

Mode
   Step, Threshold, Distance, Feather
Distance
   The Distance is the filter radius.
   A positive value of Distance dilates (expands) the influence of a pixel on its surrounding pixels.
   A negative value erodes (shrinks) its influence.
Edge
   Edge to inset.

   .. TODO2.8 Explain.
Falloff
   Falloff type the feather.

   .. TODO2.8 Explain.


Outputs
=======

Mask
   The filtered mask output.


Example
=======

In this example, we wanted to take the rather boring array of ball bearings and
add some variation to it. So, we dilated the red and eroded the green, leaving the blue alone.
If we had dilated both red and green... (hint: red and green make yellow).
The amount of influence is increased by increasing the *Distance* values.
`Blend-file available here <https://archive.blender.org/wiki/2015/uploads/5/51/Derotest.blend>`__.

.. figure:: /images/compositing_types_filter_dilate-erode_example.png


## Filter

.. index:: Compositor Nodes; Filter
.. _bpy.types.CompositorNodeFilter:

***********
Filter Node
***********

.. figure:: /images/compositing_node-types_CompositorNodeFilter.webp
   :align: right
   :alt: Filter Node.

The Filter node implements various common image enhancement filters.


Inputs
======

Factor
   Controls the amount of influence the node exerts on the output image.
Image
   Standard color input.


Properties
==========

Type
   The Soften, Laplace, Sobel, Prewitt and Kirsch all perform edge detection
   (in slightly different ways) based on vector calculus and set theory equations.

   :Soften: Slightly blurs the image.
   :Box Sharpen: Increases the contrast, especially at edges.
   :Diamond Sharpen: Less aggressive than box sharpen, reducing sharpening artifacts.
   :Laplace: Edge highlighting filter susceptible to highlighting visual noise.
   :Sobel: Creates a negative image that highlights edges.
   :Prewitt: Produces a similar results to Sobel.
   :Kirsch: Gives better blending than Sobel or Prewitt, when approaching an edge.
   :Shadow: Performs a relief, emboss effect, darkening outside edges.


Outputs
=======

Image
   Standard color output.


Example
=======

.. list-table:: The Filter node has eight modes, shown here.

   * - .. figure:: /images/compositing_types_filter_filter-node_example-1-original.png

          Original image.

     - .. figure:: /images/compositing_types_filter_filter-node_example-2-soften.png

          Soften.

   * - .. figure:: /images/compositing_types_filter_filter-node_example-3-box-sharpen.png

          Box Sharpen.

     - .. figure:: /images/compositing_types_filter_filter-node_example-4-diamond-sharpen.png

          Diamond Sharpen.

   * - .. figure:: /images/compositing_types_filter_filter-node_example-5-laplace.png

          Laplace.

     - .. figure:: /images/compositing_types_filter_filter-node_example-6-sobel.png

          Sobel.

   * - .. figure:: /images/compositing_types_filter_filter-node_example-7-prewitt.png

          Prewitt.

     - .. figure:: /images/compositing_types_filter_filter-node_example-8-kirsch.png

          Kirsch.

   * - .. figure:: /images/compositing_types_filter_filter-node_example-9-shadow.png

          Shadow.

     -


## Glare

.. index:: Compositor Nodes; Glare
.. _bpy.types.CompositorNodeGlare:

**********
Glare Node
**********

.. figure:: /images/compositing_node-types_CompositorNodeGlare.webp
   :align: right
   :alt: Glare Node.

The *Glare node* is used to add lens flares, fog,
glows around bright parts of an image.


Inputs
======

Image
   Standard color input.


Properties
==========

Glare Type
   :Bloom:
      Simulates the glow around bright objects caused by light scattering in eyes and cameras.

      Size
         Scale of the glow relative to the size of the image. 9 means the glow can cover the
         entire image, 8 means it can only cover half the image, 7 means it can only cover quarter
         of the image, and so on.
   :Ghosts:
      Creates a haze over the image.
   :Streaks:
      Creates bright streaks used to simulate lens flares.

      Streaks
         Total number of streaks.
      Angle Offset
         The rotation offset factor of the streaks.
      Fade
         Fade out factor for the streaks.
   :Fog Glow:
      Simulates the glow around bright objects caused by light scattering in eyes and cameras.
      This is similar to the *Bloom* mode, but is more physically accurate, at the cost of much
      slower computation time.

      Size
         Scale of the glow relative to the size of the image. 9 means the glow will cover the
         entire image, 8 means it will cover half the image, 7 means it will cover quarter of the
         image, and so on.
   :Simple Star:
      Works similar to *Streaks* but gives a simpler shape looking like a star.

      Fade
         Fade out factor for the streaks.
      Rotate 45
         Rotate the streaks by 45°.

Quality
   If not set to something other the *High*,
   then the glare effect will only be applied to a low resolution copy of the image.
   This can be helpful to save render times while only doing preview renders.

Iterations
   The number of times to run through the filter algorithm.
   Higher values will give more accurate results but will take longer to compute.
   Note that, this is not available for *Fog Glow* as it does not use an iterative-based algorithm.

Color Modulation
   Used for *Streaks* and *Ghosts* to create a special dispersion effect.

   Johannes Itten describes this effect, Color Modulation, as subtle variations in tones and chroma.

Mix
   Value to control how much of the effect is added on to the image.
   A value of -1 would give just the original image, 0 gives a 50/50 mix, and 1 gives just the effect.

Threshold
   Pixels brighter than this value will be affected by the glare filter.


Outputs
=======

Image
   Standard color output.


## Index


################
  Filter Nodes
################

Filters process the pixels of an image to highlight additional details or perform some sort of
post-processing effect on the image.

.. toctree::
   :maxdepth: 1

   blur/index.rst

----------

.. toctree::
   :maxdepth: 1

   anti_aliasing.rst
   denoise.rst
   despeckle.rst

----------

.. toctree::
   :maxdepth: 1

   dilate_erode.rst
   inpaint.rst

----------

.. toctree::
   :maxdepth: 1

   filter.rst
   glare.rst
   kuwahara.rst
   pixelate.rst
   posterize.rst
   sun_beams.rst


## Inpaint

.. index:: Compositor Nodes; Inpaint
.. _bpy.types.CompositorNodeInpaint:

************
Inpaint Node
************

.. figure:: /images/compositing_node-types_CompositorNodeInpaint.webp
   :align: right
   :alt: Inpaint Node.

The *Inpaint node* is used to extend borders of an image into transparent or masked regions.
This can be useful to solve problems like "wire removal" and holes created during chroma keying.


Inputs
======

Image
   Standard color input.


Properties
==========

Distance
   The number of times to extend the image.


Outputs
=======

Image
   Standard color output.


Examples
========

The left image shows the "wire" in place and after chroma keying has been applied. You will see you are left
with a blank space -- it's shown as a black line here but it will be alpha in your Blender output.

.. figure:: /images/compositing_types_filter_inpaint_example.jpg

   Inpaint Node example.

Inpainting fills in a couple of pixels using the surrounding image and voilà... your wire is removed.

.. note::

   The wider the "hole" is, the more noticeable this effect is!
   If you use more than a few pixels of infill,
   the effect is almost as irritating as the wire and your viewers won't be impressed.

Inpainting can also cover up a multitude of other minor sins
such as control points for motion capture: use it sparingly and it will amaze.


## Kuwahara

.. index:: Compositor Nodes; Kuwahara
.. _bpy.types.CompositorNodeKuwahara:

*************
Kuwahara Node
*************

.. figure:: /images/compositing_node-types_CompositorNodeKuwahara.webp
   :align: right
   :alt: Kuwahara Node.

The Kuwahara node implements the Kuwahara filter as well as its anisotropic
variant. The Kuwahara filter is a smoothing filter that tries to preserve the
edges in the image. The smoothing effect of the anisotropic variant is similar
to brush strokes, so the node can be used to create stylized painting effects.


Inputs
======

Image
   Standard color input.

Size
   Controls the size of the smoothing neighborhood. Large values may introduce
   artifacts for highly detailed areas. For the anisotropic method, the larger
   the size, the slower the filter.

   .. list-table::

      * - .. figure:: /images/compositing_types_filter_kuwahara-node_original.webp

             Original.

        - .. figure:: /images/compositing_types_filter_kuwahara-node_size3.webp

             Size: 3.

      * - .. figure:: /images/compositing_types_filter_kuwahara-node_size6.webp

             Size: 6.

        - .. figure:: /images/compositing_types_filter_kuwahara-node_size9.webp

             Size: 9.


Properties
==========

Type
   :Classic: A simple smoothing method that averages the local square
      neighborhood of the image while preserving edges. Produces blocky results
      due to the square neighborhood and provides no tuning parameters, but is
      faster to compute.
   :Anisotropic: A complex smoothing method that averages the local
      neighborhood of the image in the direction of the flow of the edges,
      thus preserving the edges in the output. Produces painterly-like results
      and provides multiple turning parameters, while being slower to compute.

High Precision
   Uses a more precise but slower method. Use if the output contains undesirable noise.

Uniformity
   Controls the uniformity of the directions of the edges of the image. Non
   uniform directions are nearly never desirable, so this should typically be
   increased until the user notices the result is no longer changing in a
   significant way. Further increases would produces worst results and increase
   compute time.

Sharpness
   Controls the sharpness of the edges of the image.

   .. list-table::

      * - .. figure:: /images/compositing_types_filter_kuwahara-node_original.webp

             Original.

        - .. figure:: /images/compositing_types_filter_kuwahara-node_sharpness0.webp

             Sharpness: 0.

      * - .. figure:: /images/compositing_types_filter_kuwahara-node_sharpness05.webp

             Sharpness: 0.5.

        - .. figure:: /images/compositing_types_filter_kuwahara-node_sharpness1.webp

             Sharpness: 1.

Eccentricity
   Controls how thin and directional the filter is. Low eccentricity corresponds
   to circular omnidirectional features while high eccentricity corresponds to
   thin directional features.

   .. list-table::

      * - .. figure:: /images/compositing_types_filter_kuwahara-node_original.webp

             Original.

        - .. figure:: /images/compositing_types_filter_kuwahara-node_eccentricity0.webp

             Eccentricity: 0.

      * - .. figure:: /images/compositing_types_filter_kuwahara-node_eccentricity1.webp

             Eccentricity: 1.

        - .. figure:: /images/compositing_types_filter_kuwahara-node_eccentricity2.webp

             Eccentricity: 2.


Outputs
=======

Image
   Standard color output.


Notes
=====

Iterations
   The filter can be applied multiple times by chaining the node multiple times.
   This chaining can produce more flat filtering.

   .. list-table::

      * - .. figure:: /images/compositing_types_filter_kuwahara-node_original.webp

             Original.

        - .. figure:: /images/compositing_types_filter_kuwahara-node_iterations1.webp

             Iterations: 1.

      * - .. figure:: /images/compositing_types_filter_kuwahara-node_iterations2.webp

             Iterations: 2.

        - .. figure:: /images/compositing_types_filter_kuwahara-node_iterations3.webp

             Iterations: 3.

Performance
   The filter can be expensive to compute for high size input and high resolution
   images. To improve performance, consider scaling down the image, applying the
   filter, then scaling it up again. This can work well because the filter
   already attenuates low frequency details.


## Pixelate

.. index:: Compositor Nodes; Pixelate
.. _bpy.types.CompositorNodePixelate:

*************
Pixelate Node
*************

.. figure:: /images/compositing_node-types_CompositorNodePixelate.webp
   :align: right
   :alt: Pixelate Node.

The Pixelate node reduces the detail in an image by making individual pixels more prominent.
It results in a blocky or mosaic-like appearance, where the fine details of the image are obscured,
and the overall image is represented using larger, more noticeable pixels.


Inputs
======

Color
   Standard color input.


Properties
==========

Pixel Size
   The size of the pixels in the output image, measured in pixels.


Outputs
=======

Color
   Standard color output.


Example
=======

.. figure:: /images/compositing_types_filter_pixelate_example.png


## Posterize

.. index:: Compositor Nodes; Posterize
.. _bpy.types.CompositorNodePosterize:

*********
Posterize
*********

.. figure:: /images/compositing_node-types_CompositorNodePosterize.webp
   :align: right
   :alt: Posterize Node.

The *Posterize Node* reduces the number of colors in image, converting
smooth gradients into sharp transitions.
This node is useful for generating masks in particular for rotoscoping.


Inputs
======

Image
   Standard color input.
Steps
   The number of colors per channel;
   A value of 8 will result in :math:`8^3 = 512` total colors.


Properties
==========

This node has no properties.


Outputs
=======

Image
   Standard color output.


## Sun Beams

.. index:: Compositor Nodes; Sun Beams
.. _bpy.types.CompositorNodeSunBeams:

**************
Sun Beams Node
**************

.. figure:: /images/compositing_node-types_CompositorNodeSunBeams.webp
   :align: right
   :alt: Sun Beams Node.

The Sun Beams node provides a cheap way of adding sun beams based
on image brightness alone.

Sun Beams is a 2D effect for simulating the effect of bright light getting scattered in a medium
`(Crepuscular Rays) <https://en.wikipedia.org/wiki/Crepuscular_rays>`__.
This phenomenon can be created by renderers, but full volumetric lighting is
a rather arduous approach and takes a long time to render.


Inputs
======

Image
   Standard color input.


Properties
==========

Source Width, Height
   Source point of the rays as a factor of the image dimensions.
Ray Length
   Length of the rays as a factor of the image size.


Outputs
=======

Image
   Standard color output.


Example
=======

Usually, the first step is to define the area from which rays are cast.
Any diffuse reflected light from surfaces is not going to contribute to such scattering in the real world,
so should be excluded from the input data.
Possible ways to achieve this are:

- Entirely separate image as a light source.
- Brightness/contrast tweaking to leave only the brightest areas.
- Muting shadow and midtone colors, which is a bit more flexible.
- Masking for ultimate control.

After generating the sun beams from such a light source image they can then be overlaid on the original image.
Usually, a simple "Add" Mix node is sufficient,
and physically correct because the scattered light adds to the final result.

.. figure:: /images/compositing_types_filter_sun-beams_example.jpg
   :width: 400px


## Bilateral Blur

.. index:: Compositor Nodes; Bilateral Blur
.. _bpy.types.CompositorNodeBilateralblur:

*******************
Bilateral Blur Node
*******************

.. figure:: /images/compositing_node-types_CompositorNodeBilateralblur.webp
   :align: right
   :alt: Bilateral Blur Node.

The Bilateral Blur node performs a high-quality adaptive blur, blurring
the image while retaining sharp edges.

It can be used for various purposes like: smoothing noisy render passes to avoid longer computation times
in example ray-traced ambient occlusion, blurry refractions/reflections, soft shadows,
or to make non-photorealistic compositing effects.


Inputs
======

Image
   Standard color input.
   If only the image input is connected,
   the node blurs the image depending on the edges present in the source image.
Determinator
   Which is non-obligatory and if the Determinator is connected,
   it serves as the source for defining edges/borders for the blur in the image.
   This has great advantage in case the source image is too noisy,
   but normals in combination with Z-buffer can still define exact borders/edges of objects.


Properties
==========

Iterations
   Defines how many times the filter should perform the operation on the image.
   It practically defines the radius of blur.
Color Sigma
   Defines the threshold for which color differences in the image should be taken as edges.
Space Sigma
   A fine-tuning variable for blur radius.


Outputs
=======

Image
   Standard color output.


Example
=======

.. figure:: /images/compositing_types_filter_bilateral-blur_example-1.png
   :width: 600px

   Bilateral smoothed Ambient Occlusion.
   `blend-file example <https://archive.blender.org/wiki/2015/uploads/2/2a/Bilateral_blur_example_01.blend>`__

.. list-table::

   * - .. figure:: /images/compositing_types_filter_bilateral-blur_example-1-render.jpg
          :width: 320px

          Render result.

     - .. figure:: /images/compositing_types_filter_bilateral-blur_example-1-composite.jpg
          :width: 320px

          Composite.


## Blur

.. index:: Compositor Nodes; Blur
.. _bpy.types.CompositorNodeBlur:

*********
Blur Node
*********

.. figure:: /images/compositing_node-types_CompositorNodeBlur.webp
   :align: right
   :alt: Blur Node.

The Blur node blurs an image, providing several blur modes.


Inputs
======

Image
   Standard color input.
Size
   The optional Size input will be multiplied with the X and Y blur radius values.
   It also accepts a value image, to control the blur radius with a mask.
   The values should be mapped between (0 to 1) for an optimal effect.


Properties
==========

Type
   The difference between the types is in the way they handle sharp edges,
   smooth gradients and preserve the highs and the lows.

   :Flat: Simply blurs everything uniformly.
   :Tent: Preserves the high and the lows better by making a linear falloff.
   :Quadratic: Looks similar to *Gaussian* but can be a little faster but slightly worse looking.
   :Cubic: Preserve the highs, but give an almost out-of-focus blur while smoothing sharp edges.
   :Gaussian: Gives the best looking results but tends to be the slowest.
   :Fast Gaussian: An approximation of the Gaussian.
   :Catmull-Rom: Catmull-Rom keeps sharp contrast edges crisp.
   :Mitch: Preserve the highs, but give an almost out-of-focus blur while smoothing sharp edges.

Variable Size
   Allows a variable blur radius, if the size input is an image.

   Bokeh
      The Bokeh button will force the Blur node to use a circular blur filter.
      This gives higher quality results, but is slower than using a normal filter.
Gamma
   The Gamma button applies a gamma correction on the image before blurring it.
Relative
   Percentage Value of the blur radius relative to the image size.

   Aspect Correction
      None, Y, X
X, Y
   Values set the ellipsoid radius in numbers of pixels over which to spread the blur effect.
Extend Bounds
   Allows the image, that is being blurred, to extend past its original dimension.


Outputs
=======

Image
   Standard color output.


Example
=======

.. list-table:: Blur node blur modes using 20% of image size as XY, no Bokeh/Gamma.

   * - .. figure:: /images/compositing_types_filter_blur-node_example-1-original.png

          Original image.

     - .. figure:: /images/compositing_types_filter_blur-node_example-2-flat.png

          Flat.

     - .. figure:: /images/compositing_types_filter_blur-node_example-3-tent.png

          Tent.

   * - .. figure:: /images/compositing_types_filter_blur-node_example-4-quadratic.png

          Quadratic.

     - .. figure:: /images/compositing_types_filter_blur-node_example-5-cubic.png

          Cubic.

     - .. figure:: /images/compositing_types_filter_blur-node_example-6-gaussian.png

          Gaussian.

   * - .. figure:: /images/compositing_types_filter_blur-node_example-7-fast-gaussian.png

          Fast Gaussian.

     - .. figure:: /images/compositing_types_filter_blur-node_example-8-catmull-rom.png

          Catmull-Rom.

     - .. figure:: /images/compositing_types_filter_blur-node_example-9-mitch.png

          Mitch.


## Bokeh Blur

.. index:: Compositor Nodes; Bokeh Blur
.. _bpy.types.CompositorNodeBokehBlur:

***************
Bokeh Blur Node
***************

.. figure:: /images/compositing_node-types_CompositorNodeBokehBlur.webp
   :align: right
   :alt: Bokeh Blur Node.

The Bokeh Blur node generates a bokeh type blur similar to Defocus.
Unlike defocus an in-focus region is defined in the Compositor.
There is also more flexibility in the type of blur applied through
the :doc:`Bokeh Image </compositing/types/input/bokeh_image>` node.

Several performance optimizations are also available such calculation area restriction and masking.


Inputs
======

Image
   Standard color input.
Bokeh
   This is an input for the :doc:`Bokeh Image </compositing/types/input/bokeh_image>` node.
Size
   Size controls the amount of blur. Size can either be a single value across the entire image or a variable value
   controlled by an input image. In order to use the latter, the Variable Size option must be selected.
   See the examples section below for more on how to use this.
Bounding Box
   This can be used with a :doc:`Box Mask </compositing/types/mask/box_mask>`
   matte node or with a :doc:`Mask </compositing/types/input/mask>`
   input node to restrict the area of the image the blur is applied to. This could be helpful, for example,
   when developing a node system by allowing only a small area of the image to be filtered
   thus saving composite time each time adjustments are made.


Properties
==========

Variable Size
   Allows a variable blur radius, if the Size input is an image.
Max Blur
   Max Blur is intended to act as an optimization tool by
   limiting the number of pixels across which the blur is calculated.


Outputs
=======

Image
   Standard color output.


Examples
========

Three examples of how the size input may be used follow.

An :doc:`ID masked </compositing/types/mask/id_mask>`
alpha image can be used so that a background is blurred while foreground objects remain in focus.
To prevent strange edges the :doc:`Dilate Node </compositing/types/filter/dilate_erode>` should be used.

The Z pass can be visualized using a :doc:`Map Value </compositing/types/utilities/map_value>` node
and a :doc:`Color Ramp </compositing/types/color/color_ramp>` node
as described in :doc:`Render Layers </compositing/types/input/scene/render_layers>`.
A *multiply* :doc:`Math </compositing/types/utilities/math>` node can be used following the color ramp
so that a blur value greater than one is used for objects outside the focal range.

.. figure:: /images/compositing_types_filter_bokeh-blur_example-1.png
   :width: 640px

   Z pass used.

A manually created grayscale image can be used to define the sharp and blurry areas of a preexisting image.
Again, a Multiply Node can be used so that a blur value greater than one is used.

.. figure:: /images/compositing_types_filter_bokeh-blur_example-2.png
   :width: 640px

   Image used.

.. list-table::

   * - .. figure:: /images/compositing_types_filter_bokeh-blur_example-1-render.jpg

          Z pass used.

     - .. figure:: /images/compositing_types_filter_bokeh-blur_example-2-render.jpg

          Image used.


## Defocus

.. index:: Compositor Nodes; Defocus
.. _bpy.types.CompositorNodeDefocus:

************
Defocus Node
************

.. figure:: /images/compositing_node-types_CompositorNodeDefocus.webp
   :align: right
   :alt: Defocus Node.

The *Defocus Node* blurs areas of an image based on a Z depth map or mask input.

It is typically used to emulate depth of field (:term:`DOF`) using a post-processing method with a Z-buffer input.
But also allows to blur images that are not based on Z depth too.


Inputs
======

Image
   Standard color input.
Z
   Z-buffer input, but could also be a (grayscale) image used as a mask, or a single value input.


Properties
==========

Bokeh Type
   The number of iris blades of the virtual camera's diaphragm.

   Disk (to emulate a perfect circle), Triangle (3 blades), Square (4 blades),
   Pentagon (5 blades), Hexagon (6 blades), Heptagon (7 blades) or Octagon (8 blades).
Angle
   This slider is deactivated, if the Bokeh Type is set to Disk.
   It can be used to add a rotation offset to the Bokeh shape.
   The value is the angle in degrees.
Gamma Correction
   Applies a gamma correction on the image before and after blurring it.
F-Stop
   This option controls the amount of focal blur in the same way as a real camera.
   It simulates the aperture *f* of a real lens' iris, without modifying the luminosity of the picture.
   The default value 128 is assumed to be infinity:
   everything is in perfect focus. Half the value will double the amount of blur.
   This slider is deactivated, if *No Z-buffer* is enabled.
Max Blur
   This value limits the amount of blur by setting a maximum blur radius.
   Can be used to optimize the performance.
   The default value of 0 means no limit.
Threshold :guilabel:`CPU Compositor Only`
   Some artifacts, like edge bleed, may occur, if the blur difference between pixels is large.
   This value controls how large that blur difference considered to be safe.

   .. tip::

      Only change this value, if there is an occurring problem with an in-focus object.

Preview :guilabel:`CPU Compositor Only`
   If enabled a limited amount of (quasi-)random samples are used to render the preview.
   This way of sampling introduces additional noise, which will not show up in the final render.
Scene
   To select the linked scene.
No Z-buffer
   Should be activated for a non Z-buffer in the Z input.
   No Z-buffer will be enabled automatically
   whenever a node that is not image based is connected to the Z input.
Z Scale
   Only active when *No Z-buffer* is enabled. When *No Z-buffer* is used,
   the input is used directly to control the blur radius (similar to *F-Stop* when using the Z-buffer).
   This parameter can be used to scale the range of the Z input.


Outputs
=======

Image
   Standard color output.


.. Todo: review examples section

Examples
========

.. figure:: /images/compositing_types_filter_defocus_example.jpg
   :width: 300px

In this `blend-file example <https://archive.blender.org/wiki/2015/uploads/7/79/Doftest.blend>`__,
the ball array image is blurred as if it was taken by a camera with an f-stop of 2.8 resulting
in a fairly narrow depth of field centered on 7.5 units from the camera.
As the balls recede into the distance, they get blurrier.


No Z-Buffer Examples
--------------------

Sometimes might want to have more control to blur the image. For instance,
you may want to only blur one object while leaving everything else alone (or the other way around),
or you want to blur the whole image uniformly all at once.
The node, therefore, allows you to use something other than an actual Z-buffer as the Z input.
For instance, you could connect an Image node and use a grayscale image where the color designates
how much to blur the image at that point, where white is the maximum blur and black is no blur.
Or, you could use a Time node to uniformly blur the image,
where the time value controls the maximum blur for that frame.
It may also be used to obtain a possibly slightly better DoF blur,
by using a fake depth-shaded image instead of a Z-buffer.
(A typical method to create the fake depth-shaded image is by using a linear blend texture
for all objects in the scene or by using the "fog/mist" fake depth shading method.)
This also has the advantage that the fake depth image can have :term:`Anti-Aliasing`,
which is not possible with a real Z-buffer.

The parameter *No Z-buffer*, becomes then the main blur control.
The input has to be scaled, because usually the value of a texture is only in the numeric range 0.0 to 1.0.


Camera Settings
---------------

.. figure:: /images/compositing_types_filter_defocus_depth-of-field-panel.png

   Distance setting in the Camera Depth of Field panel.

The *Defocus* node uses the actual camera data in your scene if supplied by a *Render Layer* node.

To set the point of focus, the camera now has a *Distance* parameter,
which is shorthand for Depth of Field Distance.
Use this camera parameter to set the focal plane of the camera
(objects Depth of Field Distance away from the camera are in focus).
Set *Distance* in the main *Camera* edit panel;
the button is right below the *Depth of Field*.

To make the focal point visible, enable the camera *Limits* option,
the focal point is then visible as a yellow cross along the view direction of the camera.


Hints
-----

Preview
   In general, use preview mode, change parameters to your liking,
   only then disable preview mode for the final render.
Edge Artifacts
   For minimum artifacts, try to setup your scene such that differences in distances between two objects that may
   visibly overlap at some point are not too large.
"Focus Pull"
   Keep in mind that this is not real DoF, only a post-processing simulation.
   Some things cannot be done which would be no problem for real DoF at all.
   A typical example is a scene with some object very close to the camera,
   and the camera focusing on some point far behind it. In the real world, using shallow depth of field,
   it is not impossible for nearby objects to become completely invisible,
   in effect allowing the camera to see behind them.
   Hollywood cinematographers use this visual characteristic to
   achieve the popular "focus pull" effect,
   where the focus shifts from a nearby to a distant object, such that the "other" object all but disappears.
   Well, this is simply not possible to do with the current post-processing method in a single pass.
   If you really want to achieve this effect, quite satisfactorily, here is how:

   - Split up your scene into "nearby" and "far" objects, and render them in two passes.
   - Now, combine the two results, each with their own "defocus" nodes driven by the same Time node,
     but with one of them inverted (e.g. using a Map Value node with a Size of -1).
     As the defocus of one increases,
     the defocus on the other decreases at the same rate, creating a smooth transition.

Aliasing at Low f-Stop Values
   At very low values, less than 5,
   the node will start to remove any oversampling and bring the objects at DoF Distance very sharply into focus.
   If the object is against a contrasting background, this may lead to visible stair-stepping (aliasing)
   which OSA is designed to avoid. If you run into this problem:

   - Do your own OSA by rendering at twice the intended size and then scaling down,
     so that adjacent pixels are blurred together.
   - Use the Blur node with a setting of 2 for X and Y.
   - Set DoF Distance off by a little, so that the object in focus is blurred by the tiniest bit.
   - Use a higher f-stop, which will start the blur,
     and then use the Z socket to a Map Value to a Blur node to enhance the blur effect.
   - Rearrange the objects in your scene to use a lower-contrast background.

No Z-Buffer
   A final word of warning, since there is no way to detect if an actual Z-buffer is connected to the node,
   be **very** careful with the *No Z-buffer* switch. If the *Z scale* value happens to be large,
   and you forget to set it back to some low value,
   the values may suddenly be interpreted as huge blur radius values that will cause processing times to explode.


## Directional Blur

.. index:: Compositor Nodes; Directional Blur
.. _bpy.types.CompositorNodeDBlur:

*********************
Directional Blur Node
*********************

.. figure:: /images/compositing_node-types_CompositorNodeDBlur.webp
   :align: right
   :alt: Directional Blur Node.

Blurs an image along a specified direction. Can be used to fake motion blur.


Inputs
======

Image
   Standard color input.


Properties
==========

Iterations
   Controls how may times the image is duplicated to create the blur effect.
   Higher values give smoother results.
Center X, Y
   Sets the position where the blur center is.
   This makes a difference if the angle, spin, and/or zoom are used.

Distance
   How large the blur effect is.
Angle
   Image is blurred at this angle from the center.

Spin
   Rotates the image each iteration to create a spin effect, from the center point.
Zoom
   Scales the image each iteration, creating the effect of a zoom.


Outputs
=======

Image
   Standard color output.


## Index


#####################
  Blur Filter Nodes
#####################

.. toctree::
   :maxdepth: 1

   bilateral_blur.rst
   blur.rst
   bokeh_blur.rst
   defocus.rst
   directional_blur.rst
   vector_blur.rst


## Vector Blur

.. index:: Compositor Nodes; Vector Blur
.. _bpy.types.CompositorNodeVecBlur:

****************
Vector Blur Node
****************

.. figure:: /images/compositing_node-types_CompositorNodeVecBlur.webp
   :align: right
   :alt: Vector Blur Node.

The Vector Blur node is a fast method for simulating :term:`Motion Blur` in compositing.
It uses the vector speed render pass to blur the image pixels in 2D.


Inputs
======

Image
   Image input, to be linked to the "Combined" render pass.
Z
   Z depth, to be linked to the "Depth" render pass.
Speed
   Input for the "Vector" render pass.
   See :doc:`Cycles render passes </render/layers/passes>`.


Properties
==========

Samples
   Quality factor.
Blur
   Scaling factor for the motion vector (actually the "shutter speed" in frames).


Outputs
=======

Image
   Motion blurred image output.


Usage
=====

Even with a correct compositing setup with Image, Z and Speed nodes all linked to the appropriate passes,
there may still be artifacts. The 2D render passes does not contain 3D information,
and so the information what is behind a moving object or outside the camera view is lost.

Better results can be achieved by rendering the scene into multiple render layers,
applying vector blur to each render layer, and then compositing the results together.
Typically an animated character would be rendered in a separate render layer than the background set.
Especially if hair or transparency is involved this is important.

For other artifacts it can help to slightly blur the Speed pass or to set a Maximum Speed limit.
This helps to smoothen out the motion, but too much blurring leads to its own problems.


Example
=======

The *speed vector* in this example was created by animating the patterned sphere horizontally and
using a frame at the mid-point of the sequence.

.. list-table::

   * - .. figure:: /images/compositing_types_filter_vector-blur_example-base.jpg
          :width: 300px

          Render result, no post-processing.

     - .. figure:: /images/compositing_types_filter_vector-blur_example-1.jpg
          :width: 300px

          Composite, with Samples set to 32 and Blur set to 1.0.


## Bokeh Image

.. index:: Compositor Nodes; Bokeh Image
.. _bpy.types.CompositorNodeBokehImage:

****************
Bokeh Image Node
****************

.. figure:: /images/compositing_node-types_CompositorNodeBokehImage.webp
   :align: right
   :alt: Bokeh Image Node.

The *Bokeh Image* node generates a special input image for use with
the :doc:`Bokeh Blur </compositing/types/filter/blur/bokeh_blur>` filter node.

The *Bokeh Image* node is designed to create a reference image which simulates optical parameters
such as aperture shape and lens distortions which have important impacts on bokeh in real cameras.


Inputs
======

This node has no input sockets.


Properties
==========

The first three settings simulate the aperture of the camera.

Flaps
   Sets an integer number of blades for the cameras iris diaphragm.
Angle
   Gives these blades an angular offset relative to the image plane.
Rounding
   Sets the curvature of the blades with (0 to 1) from straight to bringing them to a perfect circle.

Catadioptric
   Provides a type of distortion found in mirror lenses and some telescopes.
   This can be useful to produce a visual complex bokeh.
Lens Shift
   Introduces chromatic aberration into the blur such as would be caused by a tilt-shift lens.


Outputs
=======

Image
   The generated bokeh image.


Example
=======

In the example below the *Bokeh Image* is used to define the shape of the bokeh for
the :doc:`Bokeh Blur </compositing/types/filter/blur/bokeh_blur>` node.

.. figure:: /images/compositing_types_filter_bokeh-blur_example-1.png
   :width: 640px

   Example of *Bokeh Image* node.


## Image

.. index:: Compositor Nodes; Image
.. _bpy.types.CompositorNodeImage:

**********
Image Node
**********

.. figure:: /images/compositing_node-types_CompositorNodeImage.webp
   :align: right
   :alt: Image Node.

The *Image* node injects any image :doc:`format that is supported by Blender </files/media/image_formats>`.


Inputs
======

This node has no input sockets.


Properties
==========

Image
   Selection of different types of media. For controls see :ref:`ui-data-block`.
   For the options see :doc:`/editors/image/image_settings`.

.. note::

   More options can be set in the Sidebar region.


Outputs
=======

The first two sockets are the minimum.

Image
   Standard color output.
Alpha
   Separate Alpha value.

.. note:: Multi-Layer Format

   When a multi-layer file format, like ``EXR``, is loaded,
   each layer is made available as a socket.


## Index

.. _composite-nodes-input-index:

###############
  Input Nodes
###############

Input nodes produce information from a data source.
For instance, an input can be:

- Taken directly from the active camera in a selected scene.
- A static image.
- A movie clip (such as an image sequence or video).
- A color or value.

These nodes generate the information that is passed to other nodes.
As such, they have no input sockets; only outputs.

.. toctree::
   :maxdepth: 1

   constant/index.rst

----------

.. toctree::
   :maxdepth: 1

   bokeh_image.rst
   image.rst
   mask.rst
   movie_clip.rst
   texture.rst

----------

.. toctree::
   :maxdepth: 1

   scene/index.rst


## Mask

.. index:: Compositor Nodes; Mask
.. _bpy.types.CompositorNodeMask:

*********
Mask Node
*********

.. figure:: /images/compositing_node-types_CompositorNodeMask.webp
   :align: right
   :alt: Mask Node.

The Mask node can be used to select a :doc:`Mask data-block </movie_clip/masking/index>`.
This node can be used with other nodes, for example to Invert, Multiply or Mix, or used as a factor input.


Inputs
======

This node has no input sockets.


Properties
==========

Masks
   The selectable mask data-block. If the label is left blank, the mask name will be set.
Feather
   Use or ignore feather points defined for splines see :ref:`Mask Feathers <mask-feather>` for more details.
Size
   Scene Size will give an image the size of the render resolution for the scene,
   scaling along when rendering with different resolutions. Fixed gives a fixed size in pixels.
   Fixed/Scene gives a size in pixels that still scales along
   when changing the render resolution percentage in the scene.
Motion Blur
   For animated masks, creating a motion blurred mask from the surrounding frames,
   with a given number of samples (higher gives better quality), and a camera shutter time in seconds.


Outputs
=======

Mask
   The black-and-white output of the mask.


Example
=======

.. figure:: /images/compositing_types_input_mask_example.png

   Example of the Mask node.

In the example above, the *Mask* node is used to isolate the object from the background
to preserve it from being corrected.


## Movie Clip

.. index:: Compositor Nodes; Movie Clip
.. _bpy.types.CompositorNodeMovieClip:

***************
Movie Clip Node
***************

.. figure:: /images/compositing_node-types_CompositorNodeMovieClip.webp
   :align: right
   :alt: Movie Clip node.

This node is a special node that uses some of the values taken from
footage cameras and trackings and link them to the output.
It is possible to load image sequences, but only Image and Alpha values
will be available, because the other outputs will not have any values
associated with them.
When a tracked clip is chosen, Blender will fulfill the outputs using
internal values taken from the tracking. So the controls for
start and end frames will be defined in the Movie Clip editor.


Inputs
======

This node has no input sockets.


Properties
==========

Movie Clip
   Used to select the movie clip. For controls see :ref:`ui-data-block`.


Outputs
=======

The first two sockets are the minimum output.

Image
   Outputs the entire image in the specified color space.
Alpha
   The alpha value taken from the movie or image.
Offset X
   The X offset value from the footage camera or tracking.
Offset Y
   The Y offset value from the footage camera or tracking.
Scale
   The scale of the image taken from the footage camera or tracking.
Angle
   The lens angle taken from the footage camera or tracking.


## Texture

.. index:: Compositor Nodes; Texture
.. _bpy.types.CompositorNodeTexture:

************
Texture Node
************

.. figure:: /images/compositing_node-types_CompositorNodeTexture.webp
   :align: right
   :alt: Texture Node.

The Texture node makes 3D textures available to the Compositor.


Inputs
======

Offset
   A vector (XYZ) transforming the origin of the texture.
Scale
   A vector (XYZ) to scale the texture.


Properties
==========

Texture
   The texture can be selected from a list of textures available in the current blend-file or linked-in textures.
   The textures themselves can not be edited in the Compositor,
   but in the :doc:`Texture Node Editor </editors/texture_node/index>`.


Outputs
=======

Value
   Gray-scale color values.
Color
   Color values.


## Index



############
  Constant
############

.. toctree::
   :maxdepth: 1

   rgb.rst
   value.rst


## Rgb

.. index:: Compositor Nodes; RGB
.. _bpy.types.CompositorNodeRGB:
.. Editor's Note: This page gets copied into :doc:`</render/cycles/nodes/types/input/rgb>`

.. --- copy below this line ---

********
RGB Node
********

.. figure:: /images/compositing_node-types_CompositorNodeRGB.webp
   :align: right
   :alt: RGB Node.


Inputs
======

This node has no input sockets.


Properties
==========

The RGB node uses the :ref:`color picker widget <ui-color-picker>`.


Outputs
=======

Color / RGBA
   A single RGBA color value.


## Value

.. _bpy.types.CompositorNodeValue:
.. Editor's Note: This page gets copied into:
.. - :doc:`</render/cycles/nodes/types/input/value>`
.. - :doc:`</modeling/modifiers/nodes/input/value>`

.. --- copy below this line ---

**********
Value Node
**********

.. figure:: /images/compositing_node-types_CompositorNodeValue.webp
   :align: right
   :alt: Value Node.

The *Value Node* is a simple node to input numerical values to other nodes in the tree.


Inputs
======

This node has no input sockets.


Properties
==========

Single numerical value (floating-point).


Outputs
=======

Value
   The value set in the node properties.


Example
=======

In the following example the *Value Node* is used to control multiple values at once,
this makes the node a useful organizational tool.

.. figure:: /images/compositing_types_input_value_example.png

   Example of the *Value* node.

.. tip::

   From this you can also make different values proportional to each other by adding
   a :doc:`Math Node </compositing/types/utilities/math>` in between the different links.


## Index



#########
  Scene
#########

.. toctree::
   :maxdepth: 1

   render_layers.rst
   scene_time.rst
   time_curve.rst


## Render Layers

.. index:: Compositor Nodes; Render Layers
.. _bpy.types.CompositorNodeRLayers:

******************
Render Layers Node
******************

.. figure:: /images/compositing_node-types_CompositorNodeRLayers.webp
   :align: right
   :alt: Render Layers Node.

Read render layers and passes from a scene into the compositing node graph.


Inputs
======

This node has no input sockets.


Properties
==========

Scene
   Select the scene within your blend-file. The scene information taken is the raw footage
   (pre-compositing and pre-sequencing).

   .. hint::

      To use composited footage from another scene, it has to be rendered into a multi-layer frameset
      (e.g. ``OpenEXR``) as an intermediate file store and then imported with Image input node again.

Render Layer
   A list of available :doc:`Render Layers </render/layers/index>`.
   The render button is a shorthand to re-render the active scene.


Outputs
=======

Image
   Rendered image.
Alpha
   Alpha channel.


.. rubric:: Render Passes Sockets

Depending on the Render passes that are enabled, other sockets are available.
See :doc:`render passes </render/layers/passes>`.

.. note::

   In the viewport compositor, only the Image and Alpha outputs are supported, where the Image output
   is the viewport pass and the Alpha output is the alpha channel of the viewport pass. The rest of
   the passes return a zero value, a zero vector, or a transparent color depending on their type.


## Scene Time

.. index:: Compositor Nodes; Scene Time
.. _bpy.types.CompositorNodeSceneTime:
.. DO NOT EDIT FILE. This is simply a stub which copies everything from the link below.
.. include:: /modeling/geometry_nodes/input/scene/scene_time.rst
   :start-after: .. --- copy below this line ---


## Time Curve

.. index:: Compositor Nodes; Time Curve
.. _bpy.types.CompositorNodeTime:

.. --- copy below this line ---

***************
Time Curve Node
***************

.. figure:: /images/compositing_node-types_CompositorNodeTime.webp
   :align: right
   :alt: Time Curve Node.

The *Time Curve node* generates a factor value (from 0.0 to 1.0)
between the scene start and end time, using a curve mapping.


Inputs
======

This node has no inputs.


Properties
==========

Curve
   The Y value defined by the curve is the factor output.
   For the curve controls, see :ref:`Curve widget <ui-curve-widget>`.

   .. tip::

      Flipping the curve around reverses the time input, but
      doing so is easily overlooked in the node setup.

Start, End
   Start frame and End frame of the range of time specifying the values
   the output should last. This range becomes the X axis of the graph.
   The time input could be reversed by specifying a start frame greater than the end frame.


Outputs
=======

Factor
   The Y value of the curve at the current frame.

.. hint::

   The :doc:`Map Value </compositing/types/utilities/map_value>`
   node can be used to map the output to a more appropriate value.
   With some curves, it is possible that the Time Curve node
   may output a number larger than one or less than zero.
   To be safe, use the Min/Max clamping function of the Map Value node to limit output.


Example
=======

.. figure:: /images/compositing_types_input_time_curve_example.png

   Time controls from left to right: no effect, slow down, freeze, accelerate, reverse.


## Channel Key

.. index:: Compositor Nodes; Channel Key
.. _bpy.types.CompositorNodeChannelMatte:

****************
Channel Key Node
****************

.. figure:: /images/compositing_node-types_CompositorNodeChannelMatte.webp
   :align: right
   :alt: Channel Key Node.

The *Channel Key* node determines background objects from foreground objects by
the difference in the selected channel's levels.

For example in the YUV :term:`Color Model`,
this node is useful when compositing stock footage of explosions (very bright)
which are normally shot against a solid, dark background.


Inputs
======

Image
   Standard color input.


Properties
==========

Color Space
   This button selects what color model the channels will represent.

   RGB, HSV, YUV, YCbCr

Key Channel
   This button selects the channel, defined by the *Color Space*, to use to determine the matte.

Algorithm
   Method to calculate the difference between levels.

   :Max:
      Limit by the maximum of the other two channels other than the *Key Channel*.
   :Single:
      Limit by the maximum of the selected *Limiting Channel*.

      Limiting Channel
         The channel to use when computing the maximum, the options are defined by the *Color Space*.

High
   Determines the lowest values that are considered foreground.
   (Which is supposed to be -- relatively -- high values: from this value to 1.0.)

Low
   Determines the highest values that are considered to be background objects.
   (Which is supposed to be -- relatively -- low values: from 0.0 to this value.)

.. tip::

   It is possible to have a separation between the *High* and *Low* values to allow
   for a gradient of transparency between foreground and background objects.


Outputs
=======

Image
   Image with an alpha channel adjusted for the keyed selection.
Matte
   A black-and-white alpha mask of the key.


## Chroma Key

.. index:: Compositor Nodes; Chroma Key
.. _bpy.types.CompositorNodeChromaMatte:

***************
Chroma Key Node
***************

.. figure:: /images/compositing_node-types_CompositorNodeChromaMatte.webp
   :align: right
   :alt: Chroma Key Node.

The *Chroma Key* node determines if a pixel is a foreground or background
(and thereby should be transparent) based on its chroma values.

Use this, for example, to composite images that have been shot in front of a green or blue screen.


Inputs
======

Image
   Standard color input.
Key Color
   The background color usually selected using the color picker and the original image.


Properties
==========

Acceptance
   An angle on the color wheel that represents how tolerant the keying color is. Larger angles allow for larger
   variation in the keying color to be considered background pixels.
Cutoff
   Controls the level that is considered the pure background. Higher cutoff levels mean more pixels will be
   100% transparent if they are within the angle tolerance.
Falloff
   Increase to make nearby pixels partially transparent producing a smoother blend along the edges.


Outputs
=======

Image
   Image with its alpha channel adjusted for the keyed selection.
Matte
   A black-and-white alpha mask of the key.


## Color Key

.. index:: Compositor Nodes; Color Key
.. _bpy.types.CompositorNodeColorMatte:

**************
Color Key Node
**************

.. figure:: /images/compositing_node-types_CompositorNodeColorMatte.webp
   :align: right
   :alt: Color Key node.

The Color Key node creates a matte based on a specified color of the input image.


Inputs
======

Image
   Standard color input.


Properties
==========

Color
   The sliders represent threshold values.
   Higher values in this node's context mean a wider range of colors from
   the specified will be added to the matte.

   Hue, Saturation, Value


Outputs
=======

Image
   Image with its alpha channel adjusted for the keyed selection.
Matte
   A black-and-white alpha mask of the key.


## Color Spill

.. index:: Compositor Nodes; Color Spill
.. _bpy.types.CompositorNodeColorSpill:

****************
Color Spill Node
****************

.. figure:: /images/compositing_node-types_CompositorNodeColorSpill.webp
   :align: right
   :alt: Color Spill Node.

The *Color Spill* node reduces one of the RGB channels so that it is not greater
than any of the others.

This is common when compositing images that were shot in front of a green or blue screen.
In some cases, if the foreground object is reflective, it will show the green or blue color;
that color has "spilled" onto the foreground object. If there is light from the side or back,
and the foreground actor is wearing white, it is possible to get "spill" green (or blue)
light from the background onto the foreground objects,
coloring them with a tinge of green or blue. To remove the green (or blue) light,
you use this fancy node.


Inputs
======

Image
   Standard color input.
Factor
   Standard Factor.


Properties
==========

Despill Channel
   R, G, B
Algorithm
   Simple, Average
Limiting Channel
   R, G, B
Ratio
   Scale limit by value.
Unspill
   Allows you to reduce the selected channel's input to the image
   greater than the color spill algorithm normally allows.
   This is useful for exceptionally high amounts of the color spill.

   R, G, B


Outputs
=======

Image
   The image with the corrected channels.


Example
=======

Results with the nodes applied to an image from
the `Mango Open Movie <https://mango.blender.org/>`__.

.. list-table::

   * - .. figure:: /images/compositing_types_matte_color-spill_example-before.jpg

          Before: green border and green reflections.

     - .. figure:: /images/compositing_types_matte_color-spill_example-after.jpg

          After: no unwanted green.


## Difference Key

.. index:: Compositor Nodes; Difference Key
.. _bpy.types.CompositorNodeDiffMatte:

*******************
Difference Key Node
*******************

.. figure:: /images/compositing_node-types_CompositorNodeDiffMatte.webp
   :align: right
   :alt: Difference Key Node.

This node produces a matte that isolates foreground content by comparing it with a reference background image.


Inputs
======

Image
   Contains foreground content against the background that is to be removed.
Image
   The reference background image.


Properties
==========

Tolerance
   Where pixels match the reference background to within the specified threshold, the matte is made transparent.
Falloff
   Increase to make nearby pixels partially transparent producing a smoother blend along the edges.


Outputs
=======

Image
   Image with its alpha channel adjusted for the keyed selection.
Matte
   A black-and-white alpha mask of the key.


## Distance Key

.. index:: Compositor Nodes; Distance Key
.. _bpy.types.CompositorNodeDistanceMatte:

*****************
Distance Key Node
*****************

.. figure:: /images/compositing_node-types_CompositorNodeDistanceMatte.webp
   :align: right
   :alt: Distance Key Node.

The Distance Key node determines a pixel's alpha value based on the three-dimensional
distance between the image pixel color and the key color in a 3D color space.

This key works well when trying to single out a specific color in a background
(not necessarily green).


Inputs
======

Image
   Standard color input.
Key Color
   The color that is to be keyed.


Properties
==========

Tolerance
   A threshold what the node considers a match between the key color and the foreground pixel.
   The tolerance affects how close a pixel needs to be to the background pixel
   to be considered an absolute match.
Falloff
   When the Falloff value is high, pixels that are close to the Key Color are more
   transparent than pixels that are not as close to the Key Color
   (but still considered close enough to be keyed).
   When the Falloff value is low, it does not matter how close
   the pixel color (Image) is to the Key Color, it is transparent.
Color Space
   It is also possible to work with YCbCr color space,
   but only the Cb and Cr channels are taken into consideration
   for determining the distance between the foreground and background pixels.

   RGB, YCC


Outputs
=======

Image
   The image with an alpha channel adjusted for the keyed selection.
Matte
   A black-and-white alpha mask of the key.


## Index


################
  Keying Nodes
################

These nodes give you the essential tools for creating a :term:`Matte` for images
that do not already have their own :term:`Alpha Channel`.
One usage scenario is blue-screen or green-screen footage,
where live action is shot in front of a blue or green backdrop for replacement by
a matte painting or virtual background.

In general, hook up these nodes to a viewer, set your Image Editor to show the Viewer node,
and play with the sliders in real-time using a sample image from the footage,
to get the settings right. In some cases,
small adjustments can eliminate artifacts or foreground image degradation.
Taking out too much green can result in foreground actors looking flat or bluish/purplish.

You can and should chain these nodes together,
improving your masking and color correction in successive refinements,
using each node's strengths to operate on the previous node's output.
:doc:`Keying Node </compositing/types/keying/keying>` is the closest to a "does-it-all" node
for green screens, but the best results stem from a combination of techniques.

.. note::

   Garbage Matte is not a node, but a technique selecting what to
   exclude from an image. It is a :term:`Mask` used to identify content to be
   removed from an image that cannot be removed by an automatic process like
   chroma keying. It is used either to select specific content to be removed, or
   it is the inverse of a rough selection of the subject; removing everything else.

   Some nodes accept a garbage matte directly. For those that don't, you can
   still apply one by subtracting the garbage matte from the matte generated
   by the node.

   Simple garbage mattes can be created with
   the :doc:`Box Mask </compositing/types/mask/box_mask>` or
   the :doc:`Ellipse Mask </compositing/types/mask/ellipse_mask>`.
   More complicated matte shapes using
   a :doc:`Double Edge Mask </compositing/types/mask/double_edge_mask>` or
   using a :doc:`Mask </compositing/types/input/mask>`.

.. toctree::
   :maxdepth: 1

   channel_key.rst
   chroma_key.rst
   color_key.rst
   color_spill.rst
   difference_key.rst
   distance_key.rst
   keying.rst
   keying_screen.rst
   luminance_key.rst


## Keying

.. index:: Compositor Nodes; Keying
.. _bpy.types.CompositorNodeKeying:

***********
Keying Node
***********

.. figure:: /images/compositing_node-types_CompositorNodeKeying.webp
   :align: right
   :alt: Keying Node.

The *Keying* node is a one-stop-shop for "green screen" / "blue screen" removal.
It performs both chroma keying to remove the backdrop and despill to correct color cast from the backdrop.
Additionally, you can perform common operations used to tweak the resulting matte.


Inputs
======

Image
   Standard color input.
Key Color
   The color of content to be removed. This may be a single color,
   or a reference image such as generated by
   the :doc:`Keying Screen Node </compositing/types/keying/keying_screen>`.
Garbage Matte
   An optional mask of area(s) to always *exclude* from the output.
   This is removed from the chroma key generated matte.
Core Matte
   An optional mask of area(s) to always *include* in the output.
   This is merged with the chroma key generated matte.


Properties
==========

Pre Blur
   Reduce the effects of color noise in the image by blurring only color by the given amount,
   leaving luminosity intact. This will affect matte calculation only, not the result image.

Screen Balance
   This is the balance between color channels compared with the key color.
   0.5 will average the other channels (red and blue in the case of a green screen).

   This may be tweaked in tandem with *Clip Black* and *Clip White* while
   checking the *Matte* output to create a mask with optimal separation.
Despill Factor
   Controls how much color bleed from the key color is removed from the input
   image: 0 means no despilling, 1 means all possible spilling will be removed.
   The underlying implementation is the same as adjusting the *Unspill* amount
   of the :doc:`Color Spill Node </compositing/types/keying/color_spill>`.
Despill Balance
   This controls how the color channels are compared when computing spill,
   affecting the hue and shade of the corrected colors.
   It is similar to setting the *Limiting Channel*
   in the :doc:`Color Spill Node </compositing/types/keying/color_spill>`.
Edge Kernel Radius
   Defines the radius in pixel used to detect an edge.
Edge Kernel Tolerance
   Defines threshold used to check if pixels in radius are the same as current pixel:
   if the difference between pixel colors is higher than this threshold then the point
   will be considered an edge.
Clip Black
   This sets the threshold for what becomes fully transparent in the output (black in the matte).
   It should be set as low as possible. Uneven backdrops will require this value to be increased.
   Use of the :doc:`Keying Screen Node </compositing/types/keying/keying_screen>` can help
   keep this value low. You may also use a *Garbage Matte* to exclude problematic areas.

   This value does not impact areas detected as edges to ensure edge detail is preserved.
Clip White
   This sets the threshold for what becomes fully opaque in the output (white in the matte).
   It should be set as high as possible. Colors close to green in the foreground
   may require reducing this value and/or adjusting the *Screen Balance*.
   Particularly problematic parts can fixed with a *Core Matte* instead of a low *Clip White*.

   This value does not impact areas detected as edges to ensure edge detail is preserved.
Dilate/Erode
   Enlarge (positive numbers) or shrink (negative numbers) the matte by the specified number of pixels.
   This is similar to using the :doc:`Dilate/Erode Node </compositing/types/filter/dilate_erode>` on the matte.

   This a simple way to include more or less along the edges of the matte, particularly combined with *Post Blur*.
Feather Falloff
   The rate of the falloff at the edges of the matte when feathering, to manage edge detail.
Feather Distance
   Controls how much the matte is feathered inwards (negative number) or outwards (positive number).
Post Blur
   Make the matte less sharp, for smoother transitions to the background and noise reduction.


Outputs
=======

Image
   Processed image with the *Matte* applied to the images' :term:`Alpha Channel`.
Matte
   Output matte to use for checking the quality of the key, or to manually apply
   using a :doc:`Set Alpha Node </compositing/types/color/set_alpha>` or
   :doc:`Mix Node </compositing/types/color/mix/mix_color>`.
Edges
   Shows what edges were detected on the matte.
   Useful for adjusting the *Edge Kernel Radius* and *Edge Kernel Tolerance*.

.. tip::

   If there are problems with the edges of the matte, it may help to start with
   adjusting the *Edge Kernel* parameters before adjusting feathering.
   Detected edges are not subject to *Clip Black* / *Clip White* thresholds
   to preserve fine edge detail. You can check edge detection by connecting
   a :doc:`Viewer Node </compositing/types/output/viewer>` to the *Edges* output.

   Sharper detected edges (smaller *Edge Kernel Radius*, like 2 / larger *Edge Kernel Tolerance*, like 0.4)
   will create a sharper matte, but may loose some detail like stray hairs.
   A sharp matte is good, but disappearing or flickering hairs are distracting.

   Fat edges (larger *Edge Kernel Radius*, like 8 / smaller *Edge Kernel Tolerance*, like 0.05)
   will capture more edge detail, but may also produce a halo around the subject.
   The halo can be adjusted with *Feather* controls along with *Dilate/Erode*.


## Keying Screen

.. index:: Compositor Nodes; Keying Screen
.. _bpy.types.CompositorNodeKeyingScreen:

******************
Keying Screen Node
******************

.. figure:: /images/compositing_node-types_CompositorNodeKeyingScreen.webp
   :align: right
   :alt: Keying Screen node.

The Keying Screen node creates plates for use as a color reference for keying nodes.
It generates gradients from sampled colors on motion tracking points on movie clips.
It can be used to deal with uneven colors of green screens.


Inputs
======

This node has no input sockets.


Properties
==========

Movie Clip
   The selectable clip data-block used as input for the gradient colors.
Tracking Object
   Tracking Object to generate the gradient.
   You will probably want to create new a tracking object
   in the :ref:`Object <movie-clip-tracking-properties-object>` panel,
   because tracks used for gradients can not actually be used for camera/object tracking.
   After this tracks might be placed in places where gradient colors should be sampled.
   These tracks could be tracked or moved manually,
   so gradients would be updating automatically along the movie.
   Tracks might have an offset for easier tracking of feature-less screens.


Outputs
=======

Screen
   Gradient image output.


Example
=======

Consider a node setup for green screen removal, using
a :doc:`Color Key </compositing/types/keying/color_key>`:

.. figure:: /images/compositing_types_matte_keying-screen_key-usage.png
   :width: 480px

Often, lighting is uneven across the backdrop.

.. figure:: /images/compositing_types_matte_keying-screen_source.jpg
   :width: 480px

   Example from the `Mango Open Movie <https://mango.blender.org/>`__, Tears of Steel.

That can result in a bad matte.

.. figure:: /images/compositing_types_matte_keying-screen_bad.jpg
   :width: 480px

   Example of a poor mask: Some of the backdrop is opaque,
   and some parts of the gun in the foreground are transparent.

If you increase the tolerances on the Color Key node, it will accept
more shades of green to mask out. But it may also incorrectly mask out more of
the foreground.

Instead of increasing the range of accepted shades to be masked out,
the Keying Screen node lets you change what shade of green (or other color) to used
for different parts of the image.

Start in the :doc:`Movie Clip Editor </editors/clip/index>`.
Open the Sidebar region and Toolbar to show tracking configuration.
Tracks used for gradients are not useful for camera solving, because they do not track well.
So create a new object track in the *Objects* selector.
Place tracking markers on the clip to sample different parts of the backdrop.

.. figure:: /images/compositing_types_matte_keying-screen_trackers.jpg
   :width: 480px

These tracks may be tracked or moved manually, so gradients can be updated
over time. If the marker is not enabled for a frame, it will not be used creating
the gradient. (Such as the red-colored marker on the arm in the screenshot above)

Once the tracks are created, add the node to your compositing setup,
and select the tracking object used for the backdrop.

.. figure:: /images/compositing_types_matte_keying-screen_usage.png
   :width: 480px

   Node configuration with *Keying Screen*'s generated gradient
   plate connected to the Color input of the Keying node.

.. figure:: /images/compositing_types_matte_keying-screen_generated.jpg
   :width: 480px

   Gradient plate generated by *Keying Screen*.

The resulting image now has a better matte.

.. figure:: /images/compositing_types_matte_color-spill_example-after.jpg
   :width: 480px


## Luminance Key

.. index:: Compositor Nodes; Luminance Key
.. _bpy.types.CompositorNodeLumaMatte:

******************
Luminance Key Node
******************

.. figure:: /images/compositing_node-types_CompositorNodeLumaMatte.webp
   :align: right
   :alt: Luminance Key Node.

The *Luminance Key* node determines background objects from foreground objects by
the difference in the luminance (brightness) levels.

Stock footage of explosions, smoke or debris are normally shot against a solid,
dark background rather than a green screen.
This node can separate the foreground effect from the background.
It can also be used for sky replacement for overexposed or gray skies
that aren't suitable for chroma keying.

.. tip::

   When compositing footage of something that emits light and has a dark background,
   like fire, a :doc:`Mix Node </compositing/types/color/mix/mix_color>` using a *Screen* or
   *Add* operator will produce better results.


Inputs
======

Image
   Standard color input.


Properties
==========

Limit
   High
      Determines the lowest values that are considered foreground.
      (Which is supposed to be -- relatively -- light: from this value to 1.0.)
   Low
      Determines the highest values that are considered to be background objects.
      (Which is supposed to be -- relatively -- dark: from 0.0 to this value.)

.. note::

   Brightness levels between the two values form a gradient of transparency
   between foreground and background objects.


Outputs
=======

Image
   Image with an alpha channel adjusted for the keyed selection.
Matte
   A black-and-white alpha mask of the key.


Example
=======

For this example the model was shot against a *white* background.
Using the Luminance Key node, we get a matte out where the background is white,
and the model is black; the opposite of what we want.
If we wanted to use the matte, we have to switch the white and the black.
How to do this? Color Ramp node to the rescue -- we set the left color to White Alpha 1.0,
and the right color to be Black Alpha 0.0. Thus, when the Color Ramp gets in black,
it spits out white, and vice versa. The reversed mask is shown;
its white outline is usable as an alpha mask now.

.. figure:: /images/compositing_types_matte_luminance-key_example.png

   Using Luma Key with a twist.

Now to mix, we do not really need the *Alpha Over* node;
we can just use the mask as our Factor input. In this kinda weird case,
we can use the matte directly; we just switch the input nodes. As you can see,
since the matte is white (1.0) where we do not want to use the model picture,
we feed the background photo to the bottom socket
(recall the Mix node uses the top socket where the factor is 0.0,
and the bottom socket where the factor is 1.0). Feeding our original photo into the top socket
means it will be used where the Luminance Key node has spit out Black. Voilà,
our model is teleported from Atlanta to aboard a cruise ship docked in Miami.


## Index



################
  Layout Nodes
################

These are nodes which help you control the layout and connectivity of nodes within the Compositor.



## Box Mask

.. index:: Compositor Nodes; Box Mask
.. _bpy.types.CompositorNodeBoxMask:

*************
Box Mask Node
*************

.. figure:: /images/compositing_node-types_CompositorNodeBoxMask.webp
   :align: right
   :alt: Box Mask Node.

The *Box Mask* node creates an image suitable for use as a simple matte.


Inputs
======

Mask
   An optional mask to use as the base for mask operations.
Value
   Intensity of the generated mask.


Properties
==========

X, Y
   Position of the center of the box as a fraction of the total width or height.
   (0.5, 0.5 creates a centered box; 0.0, 0.0 creates a box in the lower left.)
Width
   Width of the box as a fraction of the total image width.
Height
   Height of the box as a fraction of the total image *width*, not height.
Rotation
   Rotation of the box around its center point.
Mask Type
   Operation to use against the input mask.

   :Add:
      This yields the *union* of the input mask and the generated mask:
      Areas covered by the generated mask are set to the specified *Value*.
      Other parts of the input masked are passed through unchanged, or set to black if there is no input mask.
   :Subtract:
      Values of the input mask have the specified *Value* subtracted from them.
   :Multiply:
      This yields the *intersection* of this generated mask and the input mask:
      Values of the input mask are multiplied by the specified *Value* for the area covered by the generated mask.
      All other areas become black.
   :Not:
      Any area covered by both the input mask and the generated mask becomes black.
      Areas covered by the generated mask that are black on the input mask become the specified *Value*.
      Areas uncovered by the generated mask remain unchanged.


Outputs
=======

Mask
   A generated rectangular mask merged with the input mask.
   The created mask is the size of the current scene render dimensions.

.. tip::

   For soft edges, pass the output mask through a slight :doc:`Blur node </compositing/types/filter/blur/blur>`.


## Cryptomatte

.. index:: Compositor Nodes; Cryptomatte
.. _bpy.types.CompositorNodeCryptomatteV2:

****************
Cryptomatte Node
****************

.. figure:: /images/compositing_node-types_CompositorNodeCryptomatteV2.webp
   :align: right
   :alt: Cryptomatte Node.

The Cryptomatte node uses the Cryptomatte standard to efficiently create mattes for compositing.
Cycles and EEVEE output the required render passes, which can then be used in the Compositor
or another compositor with Cryptomatte support to create masks for specified objects.

Unlike the Material and Object Index passes, the objects to isolate are selected in compositing,
and mattes will be anti-aliased and take into account effects like motion blur and transparency.


Inputs
======

Image
   Standard color input.


Properties
==========

Source
   The source of the Cryptomatte data.

   :Render:
      Use Cryptomatte data that are stored as part of the render.
   :Image:
      Use Cryptomatte data that are stored inside a multilayered OpenEXR image.

Scene
   Scene selector.
   Only available when Render Source is selected.

Image
   Image selector.
   Only available when Image Source is selected.

Cryptomatte Layer
   Selector of the Cryptomatte layer.

Matte ID
   List of object and material crypto IDs to include in matte.
   This can be used for example to quickly clear all mattes by deleting the text
   or used to copy-and-paste crypto IDs from other software.


Outputs
=======

Image
   A colored output of the input image with the matte applied to only include selected layers.
Matte
   A black-and-white alpha mask of all the selected crypto layers.
Pick
   A colored representation of the Cryptomatte pass which can be used as a higher contrast
   image for color picking.


Usage
=====

#. Enable Cryptomatte Object render pass in the Passes panel, and render.
#. In the compositing nodes, create a Cryptomatte node and select the Cryptomatte layer.
#. Attach a Viewer node to the combined pass of the render layers.
#. Use the Cryptomatte Add/Remove button to sample objects from the Compositor backdrop.
#. Use the Matte output of the Cryptomatte node to get the alpha mask.

The Image editor, UV editor, node backdrop or Movie Clip editor can be used to pick a Cryptomatte sample.
They don't need to show any Cryptomatte layer. The node will use the sample image coordinate to
sample in the Cryptomatte layer that is selected in the node.


Example
=======

In the example below, you can see the pass output on the right side.
On the left side you can see a couple of objects that were selected through the *Cryptomatte* node.
Notice how the cube on the left has a sphere-shaped cut-out from a sphere that was not selected in the node.

.. figure:: /images/compositing_types_matte_cryptomatte_example.png


Limitations
===========

- Cryptomatte sidecars (metadata files) are not supported.
- Cryptomatte node cannot be used in node groups.
- :doc:`Volume Objects </modeling/volumes/introduction>` are not supported.


## Cryptomatte Legacy

.. index:: Compositor Nodes; Cryptomatte (Legacy)
.. _bpy.types.CompositorNodeCryptomatte:

*************************
Cryptomatte Node (Legacy)
*************************

.. figure:: /images/compositing_node-types_CompositorNodeCryptomatte.webp
   :align: right
   :alt: Cryptomatte Node.

The Cryptomatte node uses the Cryptomatte standard to efficiently create mattes for compositing.
Cycles and EEVEE output the required render passes, which can then be used in the Compositor
or another compositor with Cryptomatte support to create masks for specified objects.

Unlike the Material and Object Index passes, the objects to isolate are selected in compositing,
and mattes will be anti-aliased and take into account effects like motion blur and transparency.

.. important::

   The Cryptomatte Legacy node is deprecated and replaced by
   :doc:`Cryptomatte Node </compositing/types/mask/cryptomatte>`.
   The legacy node will be removed in a future Blender release.


Inputs
======

Image
   Standard color input.
Crypto Passes
   Each crypto layer will be given its own render pass;
   each of these render passes must be connected to one of these crypto layer inputs.
   By default there are only four layers, see `Adding/Removing Layers`_ to add more.


Properties
==========

Add/Remove
   Adds/Removes an object or material from matte, by picking a color from the *Pick* output.
Matte ID
   List of object and material crypto IDs to include in matte.
   This can be used for example to quickly clear all mattes by deleting the text
   or used to copy-and-paste crypto IDs from other software.


Outputs
=======

Image
   A colored output of the input image with the matte applied to only include selected layers.
Matte
   A black-and-white alpha mask of the all the selected crypto layers.
Pick
   A colored representation of the Cryptomatte pass which can be used
   with a Viewer node to select which crypto passes are used to create the matte image.


Usage
=====

#. Enable Cryptomatte Object render pass in the Passes panel, and render.
#. In the compositing nodes, create a Cryptomatte node and
   link the Render Layer matching Image and Cryptomatte passes to it.
#. Attach a Viewer node to the Pick output of the Cryptomatte node.
#. Use the Cryptomatte Add/Remove button to sample objects in the Pick Viewer node.
#. Use the Matte output of the Cryptomatte node to get the alpha mask.


Adding/Removing Layers
----------------------

By default there are only four crypto layers available as inputs to the Cryptomatte node.
You can add or remove layer inputs through
:menuselection:`Sidebar --> Item --> Properties --> Add/Remove Crypto Layer`.
These operators will add/remove layers from the bottom of the pass inputs.


Example
=======

In the example below, you can see the pass output on the right side.
On the left side you can see a couple of objects that were selected through the *Cryptomatte* node.
Notice how the cube on the left has a sphere-shaped cut-out from a sphere that was not selected in the node.

.. figure:: /images/compositing_types_matte_cryptomatte_example.png


## Double Edge Mask

.. index:: Compositor Nodes; Double Edge Mask
.. _bpy.types.CompositorNodeDoubleEdgeMask:

*********************
Double Edge Mask Node
*********************

.. figure:: /images/compositing_node-types_CompositorNodeDoubleEdgeMask.webp
   :align: right
   :alt: Double Edge Mask Node.

The *Double Edge Mask* node creates a gradient between two masks.


Inputs
======

Inner Mask
   A mask representing the inside shape, which will be fully white.
Outer Mask
   A mask representing the outside shape, which will fade from black at its edges
   to white at the *Inner Mask*.


Properties
==========

Inner Edge
   :All:
      All shapes in the *Inner Mask* contribute to the gradient, even ones that do
      not touch the *Outer Mask* shape.
   :Adjacent Only:
      Only shapes in the *Inner Mask* that overlap with the *Outer Mask* contribute
      to the gradient.

   .. list-table::

      * - .. figure:: /images/compositing_types_matte_double-edge-mask_all.png

             All.

        - .. figure:: /images/compositing_types_matte_double-edge-mask_adjacent.png

             Adjacent Only.

Buffer Edge
   :Keep In:
      Parts of the *Outer Mask* that touch the edge of the image are treated as if
      they stop at the edge.
   :Bleed Out:
      Parts of the *Outer Mask* that touch the edge of the image are extended
      beyond the boundary of the image.

   .. list-table::

      * - .. figure:: /images/compositing_types_matte_double-edge-mask_in.png

             Keep In.

        - .. figure:: /images/compositing_types_matte_double-edge-mask_bleed.png

             Bleed Out.


Outputs
=======

Mask
   Standard mask output.


Example
=======

`Double Edge Mask Example Video <https://www.youtube.com/watch?v=VcjEfoNIHZs>`__


## Ellipse Mask

.. index:: Compositor Nodes; Ellipse Mask
.. _bpy.types.CompositorNodeEllipseMask:

*****************
Ellipse Mask Node
*****************

.. figure:: /images/compositing_node-types_CompositorNodeEllipseMask.webp
   :align: right
   :alt: Ellipse Mask Node.

The *Ellipse Mask* node creates an image suitable for use as a simple matte or vignette mask.


Inputs
======

Mask
   An optional mask to use as the base for mask operations.
Value
   Intensity of the generated mask.


Properties
==========

X, Y
   Position of the center of the ellipse as a fraction of the total width or height.
   (0.5, 0.5 creates a centered ellipse; 0.0, 0.0 creates an ellipse with its center in the lower left.)
Width
   Width of the ellipse as a fraction of the total image width.
Height
   Height of the ellipse as a fraction of the total image *width*, not height.
   Equal *Width* and *Height* values with produce a circle.
Rotation
   Rotation of the ellipse around its center point.
Mask Type
   Operation to use against the input mask.

   :Add:
      This yields the *union* of the input mask and the generated mask:
      Areas covered by the generated mask are set to the specified *Value*.
      Other parts of the input masked are passed through unchanged, or set to black if there is no input mask.
   :Subtract:
      Values of the input mask have the specified *Value* subtracted from them.
   :Multiply:
      This yields the *intersection* of this generated mask and the input mask:
      Values of the input mask are multiplied by the specified *Value* for the area covered by the generated mask.
      All other areas become black.
   :Not:
      Any area covered by both the input mask and the generated mask becomes black.
      Areas covered by the generated mask that are black on the input mask become the specified *Value*.
      Areas uncovered by the generated mask remain unchanged.


Outputs
=======

Mask
   A generated elliptical mask merged with the input mask.
   The created mask is the size of the current scene render dimensions.

.. tip::

   For soft edges, pass the output mask through a slight :doc:`Blur node </compositing/types/filter/blur/blur>`.
   For a vignette, pass the output of this through a heavy blur.


## Id Mask

.. index:: Compositor Nodes; ID Mask
.. _bpy.types.CompositorNodeIDMask:

************
ID Mask Node
************

.. figure:: /images/compositing_node-types_CompositorNodeIDMask.webp
   :align: right
   :alt: ID Mask Node.

The *ID Mask Node* can be used to access an alpha mask per object or per material.

.. seealso::

   The ID Mask node is superseded by the :doc:`/compositing/types/mask/cryptomatte`.
   Cryptomatte is more feature complete and supported by Cycles and EEVEE.
   It is recommended to use this feature moving forward.


Inputs
======

ID Value
   Input for the *Object Index* or *Material Index* render pass.
   Which is an output of the :doc:`Render Layers node </compositing/types/input/scene/render_layers>` or
   the :doc:`Image node </compositing/types/input/scene/render_layers>` with a multi-layer format.


Properties
==========

Index
   Selection of the previously specified index.
Anti-Aliasing
   This post-processing filter smooths the mask edges. See :term:`Anti-Aliasing`.


Outputs
=======

Alpha
   The mask is white where the object is and black where it is not.
   If the object is transparent, the alpha mask represent that with gray values.


Setup
=====

An index can be specify for any object or material in the scene.
The Object Index can be set in :menuselection:`Properties --> Object Properties --> Relations --> Pass Index`
and :menuselection:`Material --> Settings --> Pass Index` for the Material Index.
To be accessible after rendering, the Render Engine must be Cycles,
and *Object Index* or *Material Index* render pass has to be enabled.

.. figure:: /images/compositing_types_converter_id-mask_relations-panel.png

   Object Pass Index.


Example
=======

In this example, the left rear red cube is assigned Pass Index 1, and the right cube Pass Index 2.
Where the two cubes intersect, there is going to be noticeable pixelation because they come together
at a sharp angle and are different colors. Using the mask from object 1,
which is smoothed (anti-aliased) at the edges, we use a *Mix Node* set on *Multiply*
to multiply the smoothed edges of the image, thus removing those nasty lines, thus, being smoothed out.

.. figure:: /images/compositing_types_converter_id-mask_example.png

   ID Mask node example.


Limitations
===========

- :doc:`Volume Objects </modeling/volumes/introduction>` are not supported.


## Index


##############
  Mask Nodes
##############

.. toctree::
   :maxdepth: 1

   cryptomatte.rst
   cryptomatte_legacy.rst

----------

.. toctree::
   :maxdepth: 1

   box_mask.rst
   ellipse_mask.rst

----------

.. toctree::
   :maxdepth: 1

   double_edge_mask.rst
   id_mask.rst


## Composite

.. index:: Compositor Nodes; Composite
.. _bpy.types.CompositorNodeComposite:

**************
Composite Node
**************

.. figure:: /images/compositing_node-types_CompositorNodeComposite.webp
   :align: right
   :alt: Composite Node.

The Composite node is where the actual output from the Compositor
is connected to the renderer.
This node is updated after each render, but also reflects changes in the node tree
(provided at least one finished input node is connected).


Inputs
======

Connecting a node to the Composite node will output the result of the prior
tree of that node to the Compositor.

Image
   RGB image. The default is black, so leaving this node unconnected will result in a black image.
Alpha
   Alpha channel.


Properties
==========

Use Alpha
   Used alpha channel, colors are treated alpha *premultiplied*.
   If disabled, alpha channel gets set to 1,
   and colors are treated as alpha *straight*, i.e. color channels does not change.


Outputs
=======

This node has no output sockets.

.. note::

   If multiple Composite nodes are added, only the active one
   (last selected, indicated by a red header) will be used.


## File Output

.. index:: Compositor Nodes; File Output
.. _bpy.types.CompositorNodeOutputFile:
.. _bpy.types.NodeOutputFileSlot:

****************
File Output Node
****************

.. figure:: /images/compositing_node-types_CompositorNodeOutputFile.webp
   :align: right
   :alt: File Output Node.

This node writes out an image, for each frame range specified,
to the filename entered, as part of a frameset sequence.

This node can be used as a way to automatically save the image after a render;
In addition, since this node can be hooked in anywhere in the node tree,
it can also save intermediate images automatically.


Inputs
======

Image
   The image(s) will be saved on rendering, writing to the current frame.
   An entire sequence of images will be saved, when an animation is rendered.


Properties
==========

Base Path
   Unlike the render output filepath, this node uses a base directory and an image name,
   by default the output path is composed of:
   ``{base path}/{file name}{frame number}.{extension}``.

   Besides being split into two settings, in all other respects,
   this setting is treated the same as the :ref:`render output path <bpy.types.RenderSettings.filepath>`.
File Format
   Label that shows the selected file format.

.. note::

   More options can be set in the Sidebar region.


Outputs
=======

This node has no output sockets.


## Index


################
  Output Nodes
################

These nodes are used to output the composited result in some way.

.. toctree::
   :maxdepth: 1

   composite.rst
   viewer.rst

----------

.. toctree::
   :maxdepth: 1

   file_output.rst


## Viewer

.. index:: Compositor Nodes; Viewer
.. _bpy.types.CompositorNodeViewer:

***********
Viewer Node
***********

.. figure:: /images/compositing_node-types_CompositorNodeViewer.webp
   :align: right
   :alt: Viewer Node.

The *Viewer* node allows temporarily visualizing data from inside a node graph.
It can be plugged in anywhere to inspect an image or value map in your node tree.

Select a view node with :kbd:`LMB` to switch between multiple viewer nodes.
It is possible to automatically plug any other node into a Viewer node
by pressing :kbd:`Shift-Ctrl-LMB` on it.


Inputs
======

Image
   RGB image. The default is black, so leaving this node unconnected will result in a black image.
Alpha
   Alpha channel.


Properties
==========

Use Alpha
   Used alpha channel, colors are treated alpha *premultiplied*.
   If disabled, alpha channel gets set to 1,
   and colors are treated as alpha *straight*, i.e. color channels does not change.


Outputs
=======

This node has no output sockets.

.. note::

   It is possible to add multiple Viewer nodes, though only the active one
   (last selected, indicated by a red header) will be shown on the backdrop or in the Image editor.


Using the Image Editor
======================

The Viewer node allows results to be displayed in the Image Editor.
The image is facilitated in the header by selecting *Viewer Node* in the linked *Image* data-block menu.
The Image Editor will display the image from the currently selected Viewer node.

To save the image being viewed,
use :menuselection:`Image --> Save As...`, :kbd:`Alt-S` to save the image to a file.

The Image Editor also has three additional options in its header to view Images with or
without Alpha, or to view the Alpha or Z itself.
Click and holding the mouse in the Image displayed allows you to sample the values.


## Index


##################
  Tracking Nodes
##################

.. toctree::
   :maxdepth: 1

   plane_track_deform.rst
   stabilize_2d.rst
   track_position.rst


## Plane Track Deform

.. index:: Compositor Nodes; Plane Track Deform
.. _bpy.types.CompositorNodePlaneTrackDeform:

***********************
Plane Track Deform Node
***********************

.. figure:: /images/compositing_node-types_CompositorNodePlaneTrackDeform.webp
   :align: right
   :alt: Plane Track Deform Node.

The Plane Track Deform Node is used replace flat planes in footage by another image,
using plane tracks from motion tracking.


Plane Track
===========

Before using this node, :ref:`plane track <clip-tracking-plane>` for the footage
should be made in the *Movie Clip Editor*.


Inputs
======

Image
   Image to put in place of the plane track, and thus, override that area in the movie clip.


Properties
==========

Movie Clip
   Used to select the movie clip whose plane track to use.
   For controls see :ref:`ui-data-block`.
Object
   Used to select the object to which the plane track is linked.
Track
   Used to select the plane track to use.
Motion Blur
   Specify whether to use blur caused by motion of the plane track or not.

   Samples
      Set the number of samples to take for each frame.
      The higher this number, the smoother the blur effect,
      but the longer the render, as each virtual intermediate frame has to be rendered.

      .. note::

         Samples are taken only from the *next* frame, not the previous one.
         Therefore the blurred object will appear to be slightly ahead of how it would look without motion blur.

   Shutter
      Time (in frames) the shutter is open.
      If you are rendering at 24 fps, and the Shutter is set to 0.5,
      the time in between frames is 41.67 ms,
      so the shutter is open for half that, 20.83 ms.


Outputs
=======

Image
   The output by perspective wrapping the image to that plane track.
Plane
   Produces a black-and-white mask of the plane track.


Examples
========

Using Image Output
------------------

This can simply be achieved by using the Alpha Over node.

.. figure:: /images/compositing_types_distort_plane-track-deform_example-image-output.png

   Image output.


Using Plane Output
------------------

This can be achieved by mixing the movie clip and the image by using the plane output as the factor.

.. figure:: /images/compositing_types_distort_plane-track-deform_example-plane-output.png

   Plane output.


Using Image Output vs Using Original Image
==========================================

Using Image output scales, moves, and skews the input image according to the track
while using the original image and mixing it with the movie clip using Plane output as factor
will display the part of the image that lies inside that mask. This image shows the difference:

.. figure:: /images/compositing_types_distort_plane-track-deform_output-comparison.png

   Comparison between image output and original image (see Viewer nodes carefully).


## Stabilize 2D

.. index:: Compositor Nodes; Stabilize 2D
.. _bpy.types.CompositorNodeStabilize:

*****************
Stabilize 2D Node
*****************

.. figure:: /images/compositing_node-types_CompositorNodeStabilize.webp
   :align: right
   :alt: Stabilize 2D Node.

Stabilizes the footage according to the settings set in
:menuselection:`Movie Clip Editor --> Properties --> Stabilization --> 2D Stabilization`.
For more information,
see :doc:`2D Stabilization </movie_clip/tracking/clip/sidebar/stabilization/index>`.


Inputs
======

Image
   Standard color input.


Properties
==========

Movie Clip
   The movie clip whose stabilization to use.

Interpolation
   Various methods for the stabilization.
   Usually, the same as used in
   :menuselection:`Movie Clip Editor --> Properties --> Stabilization --> 2D Stabilization --> Interpolate`.
   For technical details on their difference,
   `see this <https://www.mathworks.com/help/curvefit/interpolation-methods.html>`__.
   But for most purposes, default of Bilinear should suffice.

Invert
   Invert the stabilization. If the stabilization calculated is to move the movie clip up by 5 units,
   this will move the movie clip down by 5 units.


Outputs
=======

Image
   Standard color input.


## Track Position

.. index:: Compositor Nodes; Track Position
.. _bpy.types.CompositorNodeTrackPos:

*******************
Track Position Node
*******************

.. figure:: /images/compositing_node-types_CompositorNodeTrackPos.webp
   :align: right
   :alt: Track Position Node.

The *Track Position node* is used to return information about a tracking marker to the Compositor.


Inputs
======

This node as no inputs.


Properties
==========

Movie Clip
   Used to select a Movie Clip data-block to use, for controls see :ref:`ui-data-block`.

Tracking Object
   Camera object to get track information from.

Track Name
   The name of the track to get track information from.

Position
   Which marker position to use for output.

   :Absolute: Outputs an absolute position of a marker.
   :Relative Start: Outputs the positions of a marker relative to the first marker of a track.
   :Relative Frame: Outputs the positions of a marker relative to the markers of the given *Frame*.
   :Absolute Frame: Outputs the absolute positions of a marker at the given *Frame*.


Outputs
=======

X/Y
   The marker's X and Y location.
Speed
   The velocity of the marker, measured in pixels per frame.
   This could be used to fake effects like motion blur by connecting it to the Vector Blur Node.


## Corner Pin

.. index:: Compositor Nodes; Corner Pin
.. _bpy.types.CompositorNodeCornerPin:

***************
Corner Pin Node
***************

.. figure:: /images/compositing_node-types_CompositorNodeCornerPin.webp
   :align: right
   :alt: Corner Pin Node.

The Corner Pin node uses explicit corner values for a plane warp transformation.
It works like the :doc:`Plane Track Deform </compositing/types/tracking/plane_track_deform>` node,
but without using "plane track" data from the Movie Clip Editor.


Inputs
======

Image
   Standard color input.
Corners
   Four vector inputs to define the plane warping. (Z component of vector inputs is ignored.)


Properties
==========

This node has no properties.


Outputs
=======

Image
   Standard color output. (The image after distorting.)
Plane
   A black-and-white alpha mask of the plane.


Example
=======

.. figure:: /images/compositing_types_distort_corner-pin_example.png

   An example of the Corner Pin node.

.. figure:: /images/compositing_types_distort_corner-pin_example-result.jpg

   An example of the distorted image.

In the example above, the image of the bird is distorted by the vectors specified by the Corner Pin node.


## Crop

.. index:: Compositor Nodes; Crop
.. _bpy.types.CompositorNodeCrop:

*********
Crop Node
*********

.. figure:: /images/compositing_node-types_CompositorNodeCrop.webp
   :align: right
   :alt: Crop Node.

The Crop node crops an input image to a selected region
by either making the cropped area transparent or by resizing the input image.


Inputs
======

Image
   Standard color input. If no image is selected, an image filled with the selected color is used.
   You can use and crop this image in combination with another background image.


Properties
==========

Crop Image Size
   When disabled, the image remains the same size, but the cropped areas become transparent pixels.
   When enabled, the image size is cropped to the specified region and gets a new width or height or both.

   Note that this will probably reposition the image in the render output
   because the cropped image is automatically centered.

Relative
   When enabled, crop dimensions are a percentage of the input image's width and height.
   When disabled, the range of the *Crop Region Values* are the width and height of the image in pixels.

Crop Region Values
   Define borders of the crop region; *Left* or *Right* can vary between 0 and the width of the image.
   *Up* or *Down* can vary between 0 and the height of the image.

.. note::

   The terminology (*Left*, *Right*, *Up*, *Down*) can be misunderstood easily.
   First, the numbers do not represent the amount of cropping,
   e.g. *Left* is set to 50 and *Right* to 50 does not mean that you will be
   cropping the image for 50 pixels on both the left and right side.
   In fact, it will result in zero-sized image because you are cropping from pixel 50 to pixel 50.
   So, the numbers defines a position in the input image.

   Secondly, depending on which one is bigger, *Left* should be interpreted as *Right* and vice versa.
   If *Left* is greater than *Right* then both values are switched and *Left* gets the value of *Right*
   and vice versa. The same operation is done for *Up* and *Down*, where you can think of them as the top
   and bottom of the image.

   Thirdly, the terms *Up* and *Down* are ambiguous and suggest an action; e.g. "Crop down".
   The values, however, are not amounts but positions.
   The term *Down* should be interpreted as "Bottom" and *Up* as "Top".


Outputs
=======

Image
   Standard color output.


Usage
=====

The following workflow removes some possible confusion:

#. Uncheck *Crop Image Size* for this step, so that you can see the borders of the input image.
   To see this border, you have to select the Viewer node.
#. If you don't need pixel-perfect cropping, check *Relative* so that
   you do not have to consider the exact dimensions of the input image.
#. Set *Left* and *Down* to zero. Set *Right* and *Up* to one, or to the width and height of the input image.
   You should see now the entire input image in the backdrop. *Up* is thus interpreted as the top of the image.
   The origin of the image (0, 0) is at the bottom (down) left corner.
#. To crop from the left, change the *Left* value. To crop from the right, change the *Right* value.
   To crop from the top, change the *Up* value. To crop from the bottom, change the *Down* value.


## Displace

.. index:: Compositor Nodes; Displace
.. _bpy.types.CompositorNodeDisplace:

*************
Displace Node
*************

.. figure:: /images/compositing_node-types_CompositorNodeDisplace.webp
   :align: right
   :alt: Displace Node.

The *Displace Node* displaces the pixel position based on an input vector.

This node could be used to model phenomena, like hot air distortion,
refractions of uneven glass or for surreal video effects.


Inputs
======

Image
   Standard color input.
Vector
   Input of the displacement map.
   If the a color output is implicitly converted in the vector input,
   the first channel (red) value determines displacement along X axis.
   The second channel (green) the displacement along Y axis.
   If the input is a grayscale image, where both the channel values are equal,
   the input image will be displaced equally in both X and Y directions.
Scale X, Y
   Separate scaling of the vector input in X and Y direction.
   Acting as multipliers by increasing or decreasing the strength of
   the displacement along their respective axes.


Properties
==========

This node has no properties.


Outputs
=======

Image
   Standard color output.


## Flip

.. index:: Compositor Nodes; Flip
.. _bpy.types.CompositorNodeFlip:

*********
Flip Node
*********

.. figure:: /images/compositing_node-types_CompositorNodeFlip.webp
   :align: right
   :alt: Flip Node.

This node flips an image along a defined axis.

You can use this node to just flip or use it as a part of mirror setting.
Mix half of the image to be mirrored with its flipped version to produce mirrored image.


Inputs
======

Image
   Standard color input.


Properties
==========

Axis
   This can be either X or Y. Also, flipping can be done on both X and Y axis simultaneously.

   Flip X, Flip Y, Flip X & Y


Outputs
=======

Image
   Standard color output.


## Index


###################
  Transform Nodes
###################

These nodes distort the image in some fashion, operating either uniformly on the image,
or by using a mask to vary the effect over the image.

.. toctree::
   :maxdepth: 1

   rotate.rst
   scale.rst
   transform.rst
   translate.rst

----------

.. toctree::
   :maxdepth: 1

   corner_pin.rst
   crop.rst

----------

.. toctree::
   :maxdepth: 1

   displace.rst
   flip.rst
   map_uv.rst

----------

.. toctree::
   :maxdepth: 1

   lens_distortion.rst
   movie_distortion.rst


## Lens Distortion

.. index:: Compositor Nodes; Lens Distortion
.. _bpy.types.CompositorNodeLensdist:

********************
Lens Distortion Node
********************

.. figure:: /images/compositing_node-types_CompositorNodeLensdist.webp
   :align: right
   :alt: Lens Distortion Node.

Use this node to simulate distortions that real camera lenses produce.


Inputs
======

Image
   Standard color input.
Distortion
   This creates a bulging or pinching effect from the center of the image.
Dispersion
   This simulates chromatic aberrations, where different wavelengths of light refract slightly differently,
   creating a rainbow colored fringe.


Properties
==========

Projector
   Enable or disable slider projection mode.
   When on, distortion is only applied horizontally. Disables *Jitter* and *Fit*.
Jitter
   Adds jitter to the distortion. Faster, but noisier.
Fit
   Scales image so black areas are not visible. Only works for positive distortion.


Outputs
=======

Image
   Standard color output.


## Map Uv

.. index:: Compositor Nodes; Map UV
.. _bpy.types.CompositorNodeMapUV:

***********
Map UV Node
***********

.. figure:: /images/compositing_node-types_CompositorNodeMapUV.webp
   :align: right
   :alt: Map UV node.

Map a texture using UV coordinates, to apply a texture to objects in compositing.

May be used in combination with :doc:`Cryptomatte Node </compositing/types/mask/cryptomatte>`
to apply the texture only to specific objects.


Inputs
======

Image
   The new 2D texture.
UV
   The input for UV render pass.
   See :doc:`Cycles render passes </render/layers/passes>`.

.. hint::

   To store the UV pass a multi-layer OpenEXR format could be used.


Properties
==========

Filter Type
   Interpolation Methods.

   :Anisotropic:
      Enhances the clarity of textures viewed at oblique angles, addressing issues like blurring and distortion.
   :Nearest: No interpolation, uses nearest neighboring pixel.

Alpha
   Alpha threshold is used to fade out pixels on boundaries.


Outputs
=======

Image
   The resulting image is the input image texture distorted to match the UV coordinates.
   That image can then be overlay mixed with the original image to paint
   the texture on top of the original. Adjust alpha and the mix factor to control
   how much the new texture overlays the old.

.. hint::

   When painting the new texture,
   it helps to have the UV maps for the original objects in the scene,
   it is recommended to keep those UV texture outlines around even, when shooting is done.


Examples
========

In the example below,
we have overlaid a grid pattern on top of the two heads after they have been rendered.
During rendering, we enabled the UV layer in the Properties
:menuselection:`Render Layer --> Passes`. Using a Mix node ("Overlay" in figure),
we mix that new UV texture over the original face.
We can use this grid texture to help in any motion tracking that we need to do.

.. figure:: /images/compositing_types_distort_map-uv_example-1.png
   :width: 700px

   Adding a grid UV textures for motion tracking.

In the next example, we overlay a logo on top of a mesh composed of two intersecting cubes,
and we ensure that we Enable the Alpha premultiply button on the Mix node.
The logo is used as additional UV texture on top of the existing texture. Other examples include
the possibility that there was used an unauthorized product box during the initial animation,
and it is needed to substitute in a different product sponsor after rendering.

.. hint::

   Due to limits of this node, it is not recommended to rush pre-production rendering under
   the guise of "fixing it later".

.. figure:: /images/compositing_types_distort_map-uv_example-2.png
   :width: 700px

   Adding UV textures in post-production.


## Movie Distortion

.. index:: Compositor Nodes; Movie Distortion
.. _bpy.types.CompositorNodeMovieDistortion:

*********************
Movie Distortion Node
*********************

.. figure:: /images/compositing_node-types_CompositorNodeMovieDistortion.webp
   :align: right
   :alt: Movie Distortion Node.

In the real world, all camera lenses produce some or the other sort of lens distortion.
But, whatever we render has got no distortion. So, this node helps in removing distortion from movies
or adding distortion to render to make our render blend in with the movie clip.

Usually, it is used while motion tracking.


Calculating Distortion
======================

Before using this node, one has to calculate the lens distortion of the clip. This can be done by adjusting
K1, K2 and K3 values in :menuselection:`Movie Clip Editor --> Properties --> Lens`.
For more information on how to edit those values,
`check this out <https://blender.stackexchange.com/questions/15620>`__.


Inputs
======

Image
   Standard color input.


Properties
==========

Movie Clip
   Used to select the movie clip whose distortion is to be used.
   This can be useful if more than one movie clips are present, each having a different distortion setting.
   For controls see :ref:`ui-data-block`.
Distortion Method
   :Undistort:
      Used to undistort the image received, and is usually used for the raw distorted movie clip.
   :Distort:
      Used to distort the image received, and is usually used for rendered images.


Outputs
=======

Image
   The image after distorting/undistorting.


Distortion vs Undistortion
==========================

Although, both, distortion of render and undistortion of movie clip are possible, and produce similar results,
there is a difference between these two methods.

There are two kinds of lens distortion possible and, in simple terms, they can be said as:

#. When the movie clip is bulging out.
#. When the movie clip is bulging in.

For the first case, it is recommended to distort the render and leave the movie clip as it is, because,
undistorting the movie clip will require extra pixel information, which is not available to Blender.
Similarly, in the second case, it is recommended to undistort the movie clip and leave the render as it is,
because, distorting the render will require those extra unavailable pixels.
Doing the wrong method in the wrong case can create weird results around the edges, such as in the image shown.

.. figure:: /images/compositing_types_distort_movie-distortion_problems.jpg

   Problems (notice the edges?)


## Rotate

.. index:: Compositor Nodes; Rotate
.. _bpy.types.CompositorNodeRotate:

***********
Rotate Node
***********

.. figure:: /images/compositing_node-types_CompositorNodeRotate.webp
   :align: right
   :alt: Rotate Node.

This node rotates an image.


Inputs
======

Image
   Standard color input.
Degr
   Rotation angle in degree. Positive values rotate clockwise and negative ones counterclockwise.


Properties
==========

Filter
   Interpolation Methods.

   :Nearest: No interpolation, uses nearest neighboring pixel.
   :Bilinear: Simple interpolation between adjacent pixels.
   :Bicubic: Highest quality interpolation.


Outputs
=======

Image
   Standard color output.


## Scale

.. index:: Compositor Nodes; Scale
.. _bpy.types.CompositorNodeScale:

**********
Scale Node
**********

.. figure:: /images/compositing_node-types_CompositorNodeScale.webp
   :align: right
   :alt: Scale Node.

This node scales the size of an image.


Inputs
======

Image
   Standard color input.
X, Y
   Scale in the axis directions, only available if *Space* is set to *Relative* or *Absolute*.


Properties
==========

Space
   Coordinate Space to scale relative to.

   Relative
      Percentage values relative to the dimensions of the image input.
   Absolute
      Size of an image by using absolute pixel values.
   Scene Size
      Sizes an image to the size of the final render resolution for the scene.
      For example, rendering a scene at the standard 1080p resolution but setting the render percentage at 50%,
      will produce a 1080p image with the scene scaled down 50% and leaving the rest of the image as alpha.
   Render Size
      Image dimensions set in the Render panel.

      Stretch, Fit, Crop
         Stretch distorts the image so that it fits into the render size.
         Fit scales the image until the bigger axis "fits" into the render size.
         Crop cuts the image so that it is the same aspect ratio as the render size.
      X, Y
         Offset factor for the final scaled image.


Outputs
=======

Image
   Standard color output.


Examples
========

For instance X: 0.5 and Y: 0.5 would produce an image which width and
height would be half of what they used to be.

Use this node to match image sizes.
Most nodes produce an image that is the same size as the image input into their top image socket.
To uniformly combine two images of different size,
the second image has to be scaled up to match the resolution of the first.


## Transform

.. index:: Compositor Nodes; Transform
.. _bpy.types.CompositorNodeTransform:

**************
Transform Node
**************

.. figure:: /images/compositing_node-types_CompositorNodeTransform.webp
   :align: right
   :alt: Transform Node.

This node combines the functionality of three other nodes: :doc:`Scale </compositing/types/transform/scale>`,
:doc:`translate </compositing/types/transform/translate>`,
and :doc:`rotate </compositing/types/transform/rotate>` nodes.


Inputs
======

Image
   Standard color input.
X, Y
   Used to move the input image horizontally and vertically.
Angle
   Used to rotate an image around its center.
   Positive values rotate counter-clockwise and negative ones clockwise.
Scale
   Used to resize the image. The scaling is relative, meaning a value of 0.5
   gives half the size and a value of 2.0 gives twice the size of the original image.


Properties
==========

Filter
   Interpolation Methods.

   :Nearest: No interpolation, uses nearest neighboring pixel.
   :Bilinear: Simple interpolation between adjacent pixels.
   :Bicubic: Highest quality interpolation.


Outputs
=======

Image
   Standard color output.


## Translate

.. index:: Compositor Nodes; Translate
.. _bpy.types.CompositorNodeTranslate:

**************
Translate Node
**************

.. figure:: /images/compositing_node-types_CompositorNodeTranslate.webp
   :align: right
   :alt: Translate Node.

The Translate node moves an image.

Could also be used to add a 2D camera shake.


Inputs
======

Image
   Standard color input.
X, Y
   Used to move the input image horizontally and vertically.


Properties
==========

Relative
   Percentage translation values relative to the input image size.
Wrapping
   Repeat pixels on the other side when they extend over the image dimensions, making endless translating possible.

   None, X Axis, Y Axis, Both Axis
Filter
   Interpolation Methods.

   :Nearest: No interpolation, uses nearest neighboring pixel.
   :Bilinear: Simple interpolation between adjacent pixels.
   :Bicubic: Highest quality interpolation.


Outputs
=======

Image
   Standard color output.


## Index


###################
  Utilities Nodes
###################

.. toctree::
   :maxdepth: 1

   map_range.rst
   map_value.rst
   math.rst

----------

.. toctree::
   :maxdepth: 1

   levels.rst
   normalize.rst

----------

.. toctree::
   :maxdepth: 1

   split.rst
   switch.rst
   switch_stereo_view.rst


## Levels

.. index:: Compositor Nodes; Levels
.. _bpy.types.CompositorNodeLevels:

***********
Levels Node
***********

.. figure:: /images/compositing_node-types_CompositorNodeLevels.webp
   :align: right
   :alt: Levels Node.

The Levels Node read the input color channels and outputs analytical values.
The output is one-dimensional meaning the visualization will be a uniform gray color.


Inputs
======

Image
   Standard color input.


Properties
==========

Channel
   Selects which color values are used to calculate analytics.

   :Combined: Calculate values based on the red, green, and blue channels.
   :Red: Calculate values based on the red channel.
   :Green: Calculate values based on the green channel.
   :Blue: Calculate values based on the blue channel.
   :Luminance: Calculate values based on the :term:`Luminance` of the image.


Outputs
=======

Mean
   The mean is the average value of all image pixels in specified channel.
   It represents the overall brightness of the image and can be used as such
   for setups that depend on how "bright" or "dark" the input is.
Standard Deviation
   How much pixel values differ from the mean.
   A low standard deviation indicates that the pixel values tend to be very close to the mean.
   A high standard deviation indicates that the values are spread out over a large range of values.


## Map Range

.. index:: Compositor Nodes; Map Range
.. _bpy.types.CompositorNodeMapRange:

**************
Map Range Node
**************

.. figure:: /images/compositing_node-types_CompositorNodeMapRange.webp
   :align: right
   :alt: Map Range Node.

This node converts (maps) an input value range into a destination range.
By default, values outside the specified input range will be proportionally mapped as well.
This node is similar to *Map Value* node but provides a more intuitive way to specify the desired output range.


Inputs
======

Value
   The input value to be remapped.
From Min
   The lower bound of the range to remap from.
From Max
   The higher bound of the range to remap from.
To Min
   The lower bound of the target range.
To Max
   The higher bound of the target range.


Properties
==========

Clamp
   Clamps values to Min/Max of the destination range.


Outputs
=======

Value
   Standard value output.


Usage
=====

One important use case is to easily map the original range of the Z-depth channel
to a more usable range (i.e: 0.0 - 1.0) for use as a matte for colorization or filtering operations.


## Map Value

.. index:: Compositor Nodes; Map Value
.. _bpy.types.CompositorNodeMapValue:

**************
Map Value Node
**************

.. figure:: /images/compositing_node-types_CompositorNodeMapValue.webp
   :align: right
   :alt: Map Value Node.

Map Value node is used to scale, offset and clamp values.


Inputs
======

Value
   Standard Value input. (Value refers to each vector in the set.)


Properties
==========

Offset
   Factor added to the input value.
Size
   Scales (multiply) the input value.
Use Minimum, Maximum
   Enable this to activate their related operation.
Min, Max
   Defines a range between minimum and maximum to :term:`Clamp` the input value to.


Outputs
=======

Value
   Standard value output.


Example
=======

Z-Depth Map
-----------

This is particularly useful in achieving a depth of field effect,
where the Map Value node is used to map a Z value
(which can be 20 or 30 or even 500 depending on the scene) to the range between (0 to 1),
suitable for connecting to a Blur node.


Multiplying Values
------------------

The Map Value node can also be used to multiply values to achieve a desired output value.
In the mini-map to the right, the Time node outputs a value between 0.0 and 1.0 evenly scaled over 30 frames.
The *first* Map Value node multiplies the input by 2,
resulting in an output value that scales from 0.0 to 2.0 over 30 frames.
The *second* Map Value node subtracts 1 from the input,
giving working values between (-1.00 to 1.0), and multiplies that by 150,
resulting in an output value between (-150 to 150) over a 30-frame sequence.

.. figure:: /images/compositing_types_vector_map-value_example.png

   Using Map Value to multiply.


## Math

.. index:: Compositor Nodes; Math
.. _bpy.types.CompositorNodeMath:

.. Editor's Note: This page gets copied into:
.. - :doc:`</render/cycles/nodes/types/converter/math>`
.. - :doc:`</modeling/modifiers/nodes/utilities/math>`

.. --- copy below this line ---

*********
Math Node
*********

.. figure:: /images/compositing_node-types_CompositorNodeMath.webp
   :align: right
   :alt: Math node.

The *Math Node* performs math operations.


Inputs
======

The inputs of the node are dynamic. Some inputs are only available for certain operations.
For instance, the *Addend* input is only available for the *Multiply Add* operator.

Value
   Input Value. Trigonometric functions read this value as radians.

Addend
   Input Addend.

Base
   Input Base.

Exponent
   Input Exponent.

Epsilon
   Input Epsilon.

Distance
   Input Distance.

Min
   Input Minimum.

Max
   Input Maximum.

Increment
   Input Increment.

Scale
   Input Scale.

Degrees
   Input Degrees.

Radians
   Input Radians.


Properties
==========

Operation
   The mathematical operator to be applied to the input values:

   Functions
      :Add: The sum of the two values.
      :Subtract: The difference between the two values.
      :Multiply: The product of the two values.
      :Divide: The division of the first value by the second value.
      :Multiply Add: The sum of the product of the two values with *Addend*.
      :Power: The *Base* raised to the power of *Exponent*.
      :Logarithm: The log of the value with a *Base* as its base.
      :Square Root: The square root of the value.
      :Inverse Square Root: One divided by the square root of the value.
      :Absolute:
         The input value is read without regard to its sign.
         This turns negative values into positive values.
      :Exponent:
         Raises `Euler's number <https://en.wikipedia.org/wiki/E_(mathematical_constant)>`__
         to the power of the value.

   Comparison
      :Minimum: Outputs the smallest of the input values.
      :Maximum: Outputs the largest of two input values.
      :Less Than:
         Outputs 1.0 if the first value is smaller than the second value. Otherwise the output is 0.0.
      :Greater Than:
         Outputs 1.0 if the first value is larger than the second value. Otherwise the output is 0.0.
      :Sign:
         Extracts the sign of the input value. All positive numbers
         will output 1.0. All negative numbers will output -1.0. And 0.0 will output 0.0.
      :Compare: Outputs 1.0 if the difference between the two input values is less than or equal to *Epsilon*.
      :Smooth Minimum: `Smooth Minimum <https://en.wikipedia.org/wiki/Smooth_maximum>`__.
      :Smooth Maximum: `Smooth Maximum <https://en.wikipedia.org/wiki/Smooth_maximum>`__.

   Rounding
      :Round: Rounds the input value to the nearest integer.
      :Floor: Rounds the input value down to the nearest integer.
      :Ceil: Rounds the input value up to the nearest integer.
      :Truncate: Outputs the integer part of the *value*.
      :Fraction: Returns the fractional part of the *value*.
      :Truncated Modulo: Outputs the remainder once the first value is divided by the second value.
      :Floored Modulo: Returns the positive remainder of a division operation.
      :Wrap:
         Outputs a value between *Min* and *Max* based on the absolute difference between
         the input value and the nearest integer multiple of *Max* less than the value.
      :Snap: Rounds the input value down to the nearest integer multiple of *Increment*.
      :Ping-pong: Bounces back and forth between 0.0 and the *Scale* as the input value increases.

   Trigonometric
      :Sine:
         The `Sine <https://en.wikipedia.org/wiki/Sine>`__ of the input value.
      :Cosine:
         The `Cosine <https://en.wikipedia.org/wiki/Trigonometric_functions>`__ of the input value.
      :Tangent:
         The `Tangent <https://en.wikipedia.org/wiki/Trigonometric_functions>`__ of the input value.
      :Arcsine:
         The `Arcsine <https://en.wikipedia.org/wiki/Inverse_trigonometric_functions>`__ of the input value.
      :Arccosine:
         The `Arccosine <https://en.wikipedia.org/wiki/Inverse_trigonometric_functions>`__ of the input value.
      :Arctangent:
         The `Arctangent <https://en.wikipedia.org/wiki/Inverse_trigonometric_functions>`__ of the input value.
      :Arctan2:
         Outputs the `Inverse Tangent <https://en.wikipedia.org/wiki/Inverse_trigonometric_functions>`__
         of the first value divided by the second value measured in radians.
      :Hyperbolic Sine:
         The `Hyperbolic Sine <https://en.wikipedia.org/wiki/Hyperbolic_functions>`__ of the input value.
      :Hyperbolic Cosine:
         The `Hyperbolic Cosine <https://en.wikipedia.org/wiki/Hyperbolic_functions>`__ of the input value.
      :Hyperbolic Tangent:
         The `Hyperbolic Tangent <https://en.wikipedia.org/wiki/Hyperbolic_functions>`__ of the input value.

   Conversion
      :To Radians: Converts the input from degrees to radians.
      :To Degrees: Converts the input from radians to degrees.

Clamp
   Limits the output to the range (0.0 to 1.0). See :term:`Clamp`.


Outputs
=======

Value
   Numerical value output.


Examples
========

Manual Z-Mask
-------------

.. figure:: /images/compositing_types_converter_math_manual-z-mask.png

   Minimum and maximum function example.

The top *Render Layers* node has a cube that is about 10 units from the camera.
The bottom *Render Layers* node has a plane that covers the left half of the view
and is 7 units from the camera.
Both are fed through their respective *Map Value* nodes to multiply the depth value by
0.05 and clamp it to [0.0, 1.0], bringing it into a suitable range for displaying it as a color.

The Minimum node selects the smallest of the two depth values at each pixel. In the left half,
it chooses the plane (because it's closer than the cube), and in the right half,
it chooses the cube (because it's closer than the background, which is infinitely far away).

The Maximum node selects the largest of the two depth values at each pixel. In the left half,
it chooses the cube (because it's farther away than the plane), and in the right half,
it chooses the background (because it's farther away than the cube).


Using Sine Function to Pulsate
------------------------------

.. figure:: /images/compositing_types_converter_math_sine.png

   Using sine function example.

This example has a *Time* node putting out a linear sequence from 0 to 1 over the course of 101 frames.
At frame 25, the output value is 0.25.
That value is multiplied by 2 × pi (6.28) and converted to 1.0 by the Sine function,
since :math:`sin(2 × pi/ 4) = sin(pi/ 2) = +1.0`.

Since the sine function can output values between (-1.0 to 1.0),
the *Map Value* node scales that to 0.0 to 1.0 by taking the input (-1 to 1), adding 1
(making 0 to 2), and multiplying the result by 0.5 (thus scaling the output between 0 to 1).
The default *Color Ramp* converts those values to a gray-scale.
Thus, medium gray corresponds to a 0.0 output by the sine, black to -1.0,
and white to 1.0. As you can see, :math:`sin(pi/ 2) = 1.0`. Like having your own visual color calculator!
Animating this node setup provides a smooth cyclic sequence through the range of grays.

Use this function to vary, for example,
the alpha channel of an image to produce a fading in/out effect.
Alter the Z channel to move a scene in/out of focus.
Alter a color channel value to make a color "pulse".


Brightening (Scaling) a Channel
-------------------------------

.. figure:: /images/compositing_types_converter_math_multiply.png

   Scaling a channel example.

This example has a *Math (Multiply)* node increasing the luminance channel (Y)
of the image to make it brighter. Note that you should use a *Map Value node*
with min() and max() enabled to clamp the output to valid values.
With this approach, you could use a logarithmic function to make a high dynamic range image.
For this particular example,
there is also a *Brightness/Contrast node* that might give simpler control over brightness.


Restrict Color Selection (Posterization)
----------------------------------------

.. figure:: /images/compositing_types_converter_math_posterization.png

   Posterization example.

In this example, we restrict the color values to be one of the six values: 0, 0.2, 0.4, 0.6, 0.8, 1.

To split up a continuous range of values between 0 and 1 to certain set of values,
the following function is used: :math:`round(x × n - 0.5) / (n - 1)`,
where "n" is the number of possible output values, and "x" is the input pixel color.
`Read more about this function
<https://archive.blender.org/wiki/2015/index.php/Doc:2.4/Manual/Composite_Nodes/Types/Convertor/#Quantize.2FRestrict_Color_Selection>`__.

To implement this function in Blender, consider the node setup above.
We string the Math nodes into a function that takes each color (values from 0 to 1),
multiplies it up by six, the desired number of divisions (values become from 0 to 6),
offsets it by 0.5 (-0.5 to 5.5),
rounds the value to the nearest whole number (produces 0, 1, 2, 3, 4, 5),
and then divides the image pixel color by five (0.0, 0.2, 0.4, 0.6, 0.8, 1.0).

In the case of a color image,
you need to split it into separate RGB channels using *Separate/Combine Color* nodes
and perform this operation on each channel independently.


## Normalize

.. index:: Compositor Nodes; Normalize
.. _bpy.types.CompositorNodeNormalize:

**************
Normalize Node
**************

.. figure:: /images/compositing_node-types_CompositorNodeNormalize.webp
   :align: right
   :alt: Normalize Node.

Find the minimum and maximum values of a single channel.
Then map the values to a range of 0 and 1.
This is mostly useful for the Z-buffer.


Inputs
======

Value
   Standard value input.


Properties
==========

This node has no properties.


Outputs
=======

Value
   Standard value output.

.. TODO Add more info and examples.


## Split

.. index:: Compositor Nodes; Split
.. _bpy.types.CompositorNodeSplit:

**********
Split Node
**********

.. figure:: /images/compositing_node-types_CompositorNodeSplit.webp
   :align: right
   :alt: Split Viewer Node.

The *Split* node combines two images for side-by-side display. Typically
used in combination with the :doc:`Viewer Node </compositing/types/output/viewer>`.


Inputs
======

Image
   Shown on the right or top half set by the axis.
Image
   And respectively the left or bottom half.


Properties
==========

Axis
   X or Y used as the split axis.
Factor
   Percentage factor setting the space distribution between the two images.


Outputs
=======

This node has no output sockets.

.. hint::

   This node could be used to plan scene transitions by comparing the end frame of one scene
   with the start frame of another to make sure they align.


Examples
========

.. figure:: /images/compositing_types_color_gamma_example.jpg
   :width: 700px

   Example of a Split Viewer node.


## Switch

.. index:: Compositor Nodes; Switch
.. _bpy.types.CompositorNodeSwitch:

***********
Switch Node
***********

.. figure:: /images/compositing_node-types_CompositorNodeSwitch.webp
   :align: right
   :alt: Switch Node.

Switch between two images using a checkbox.


Inputs
======

Image
   First image input.
Image
   Second image input.


Properties
==========

Switch
   - When it is unchecked, the first input labeled "Off" is passed to the output.
   - When checked, the second input labeled "On" is passed to the output.


Outputs
=======

Image
   Standard color output.

.. tip::

   Switch state may be animated by adding a :doc:`keyframe </animation/keyframes/introduction>`.
   This makes the Switch node useful for bypassing nodes which are not wanted during part of a sequence.


## Switch Stereo View

.. index:: Compositor Nodes; Switch View
.. _bpy.types.CompositorNodeSwitchView:

****************
Switch View Node
****************

.. figure:: /images/compositing_node-types_CompositorNodeSwitchView.webp
   :align: right
   :alt: Switch View Node.

The *Switch View* node combines the *views* (left and right) into a single stereo 3D output.
This can be useful if for example, you need to treat the view as separate images by combining each of the views.

.. container:: lead

   .. clear

.. seealso::

   :doc:`The multi-view workflow </render/output/properties/stereoscopy/index>`.


Inputs
======

Left
   Left-eye image input.
Right
   Right-eye image input.


Properties
==========

This node has no properties.


Outputs
=======

Image
   Stereo 3D image output.


Example
=======

.. figure:: /images/render_output_properties_stereoscopy_usage_compositor.png

   Compositor, Backdrop and Split Viewer Node.

The views to render are defined in the current scene views,
in a similar way as you define the composite output resolution in the current scene render panel,
regardless of the Image nodes resolutions or Render Layers from different scenes.


## Combine Xyz

.. index:: Compositor Nodes; Combine XYZ
.. _bpy.types.CompositorNodeCombineXYZ:

****************
Combine XYZ Node
****************

.. figure:: /images/compositing_node-types_CompositorNodeCombineXYZ.webp
   :align: right
   :alt: Combine XYZ Node.

The *Combine XYZ Node* combines a vector from its individual components.


Inputs
======

- X
- Y
- Z


Properties
==========

This node has no properties.


Output
======

Vector
   Standard vector output.

.. note::

   The vector is not normalized.


## Index


################
  Vector Nodes
################

These nodes can be used to manipulate various types of vectors, such as surface normals and speed vectors.

.. toctree::
   :maxdepth: 1

   combine_xyz.rst
   separate_xyz.rst

----------

.. toctree::
   :maxdepth: 1

   normal.rst
   vector_curves.rst


## Normal

.. index:: Compositor Nodes; Normal
.. _bpy.types.CompositorNodeNormal:
.. Editor's Note: This page gets copied into :doc:`</render/cycles/nodes/types/vector/normal>`

.. --- copy below this line ---

***********
Normal Node
***********

.. figure:: /images/compositing_node-types_CompositorNodeNormal.webp
   :align: right
   :alt: Normal Node.

The Normal node generates a normal vector and a dot product.


Inputs
======

Normal
   Normal vector input.


Properties
==========

Normal Direction
   To manually set a fixed normal direction vector.
   :kbd:`LMB` click and drag on the sphere to set the direction of the normal.
   Holding :kbd:`Ctrl` while dragging snaps to 45 degree rotation increments.


Outputs
=======

Normal
   Normal vector output.
Dot
   Dot product output. The dot product is a scalar value.

   - If two normals are pointing in the same direction the dot product is 1.
   - If they are perpendicular the dot product is zero (0).
   - If they are antiparallel (facing directly away from each other) the dot product is -1.


## Separate Xyz

.. index:: Compositor Nodes; Separate XYZ
.. _bpy.types.CompositorNodeSeparateXYZ:

*****************
Separate XYZ Node
*****************

.. figure:: /images/compositing_node-types_CompositorNodeSeparateXYZ.webp
   :align: right
   :alt: Separate XYZ Node.

The *Separate XYZ Node* splits a vector into its individual components.


Input
=====

Vector
   Standard vector input.


Properties
==========

This node has no properties.


Outputs
=======

- X
- Y
- Z


## Vector Curves

.. index:: Compositor Nodes; Vector Curves
.. _bpy.types.CompositorNodeCurveVec:
.. Editor's Note: This page gets copied into :doc:`</render/cycles/nodes/types/vector/curves>`

.. --- copy below this line ---

******************
Vector Curves Node
******************

.. figure:: /images/compositing_node-types_CompositorNodeCurveVec.webp
   :align: right
   :alt: Vector Curves Node.

The Vector Curves node maps an input vector components to a curve.

Use this curve node to slow things down or speed them up from the original scene.


Inputs
======

In the shader context the node also has an additional Factor property.

Factor
   Controls the amount of influence the node exerts on the output vector.
Vector
   Standard vector input.


Properties
==========

Channel
   X, Y, Z
Curve
   For the curve controls see: :ref:`Curve widget <ui-curve-widget>`.


Outputs
=======

Vector
   Standard vector output.


