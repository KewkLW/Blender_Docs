# Index for contribute

- [Build](#Build)
- [Editing](#Editing)
- [Index](#Index)
- [Pull Requests](#Pull-Requests)
- [Release Cycle](#Release-Cycle)
- [Todo List](#Todo-List)
- [Commit Guide](#Commit-Guide)
- [Maintenance Guide](#Maintenance-Guide)
- [Markup Guide](#Markup-Guide)
- [Templates](#Templates)
- [Writing Guide](#Writing-Guide)
- [Index](#Index)
- [Linux](#Linux)
- [Macos](#Macos)
- [Windows](#Windows)
- [Add Language](#Add-Language)
- [Contribute](#Contribute)
- [Style Guide](#Style-Guide)


## Build

.. highlight:: sh

*******************
Building the Manual
*******************

Converting the RST-files into pretty HTML pages is simple.

Open a terminal or Command Prompt in the ``~/blender-manual`` directory and simply run::

   make

.. tip::

   On Microsoft Windows you can simply open the ``make.bat`` file to easily
   run the command without having to open the Command Prompt and typing commands.

This is the command you should use when building the docs,
however, other commands are available by typing ``make help``.
This command will convert the RST-files into HTML pages
and automatically open your default web browser to view the result.
The command will continue to run and watch for changes made to the RST-files
and refresh the HTML pages as necessary.

.. note::

   The converted pages can also be viewed manually by browsing the build directory: ``~/blender-manual/build/html``.
   For example to open the home page, open ``build/html/index.html`` to read the manual.

The building process may take several minutes the first time (or after any major changes),
but for subsequent changes it should only take a few seconds.


## Editing

.. highlight:: sh

******************
Editing the Manual
******************

You can modify the manual by editing local text files.
These files are kept in sync with those online via a repository,
based on this the server will update the online manual.

The manual is written in the `reStructuredText <https://www.sphinx-doc.org/en/master/usage/restructuredtext/basics.html>`__
(RST) markup language and can be edited using a plain text editor.
For a local preview, you convert (build) the manual source files from RST into HTML web pages.


Update
======

Firstly, make sure that your local copy of the manual is up to date with the online repository using::

   make update


Writing
=======

You can now edit the documentation files, which are the ``.rst``
files inside the ``manual`` folder using a text editor of your choice.

Be sure to check the :doc:`/contribute/guides/writing_guide`
for conventions and :doc:`/contribute/guides/markup_guide`
to learn how to write in the reStructuredText markup language.

Happy writing!


Bigger Changes
--------------

If you are going to add or overhaul a section, be sure to check carefully that it does not already exist.
In some places, the docs are so disorganized that sections may be duplicated or in a strange location.
In the case that you find a duplicate or out of place section,
`create an issue <https://projects.blender.org/blender/documentation/issues/new>`__
explaining the issue, and optionally include a revision (actual changes).

Before you make any edits that are not simple and plainly justified (for example, moving folders around),
you should verify with a manual maintainer that your contribution is along the community's vision for the manual.
This ensures the best use of your time and good will as it is otherwise possible that, for some reason,
your changes will conflict and be rejected or need time-consuming review.
For example, another person may be already working on the section you wish to change,
the section may be scheduled for deletion or to be updated according to a planned change to Blender.

:ref:`Communicating <contribute-contact>` early and frequently is the key to have a productive environment,
to not waste people's effort and to attain a better Blender manual as a result.

..
   Communication is a very important step in community development.
   Manual maintainers and the general community can also point to areas that are in need of big or small changes.


Getting Help/Answers
--------------------

If you are in doubt about functionality that you wish to document,
you should pose your questions to the Blender developers responsible for that area or ask at the unofficial user
support channel in the ``#docs`` or ``#blender-coders`` channel in :ref:`blender-chat`.

Blender itself has a system of module owners with developer and artist members who are
responsible for the design and maintenance of the assigned Blender areas.
See the `module pages <https://projects.blender.org/blender/blender/wiki>`__ for more information.


Preview
=======

To view your changes, build the manual :doc:`as instructed </contribute/build>`.
Keep in mind that you can also build only the chapter you just edited to view it quickly.
Open the generated ``.html`` files inside the ``build/html`` folder using your web browser,
or refresh the page if you have it open already.


Upload
======

When you are happy with your changes, you can upload them, so that they will be in the online manual.
At first, this is done by submitting patches so that someone can review your changes and give you feedback.
After, you can commit your changes directly. This process is described in detail in the next section.


## Index

.. _about-user-contribute:

############################
  Contribute Documentation
############################

The Blender Manual is a community driven effort to which anyone can contribute.
Whether you like to fix a tiny spelling mistake or rewrite an entire chapter,
your help with the Blender manual is most welcome!

If you find an error in the documentation, please `report the problem
<https://projects.blender.org/blender/documentation/issues/new>`__.

Get involved in discussions through any of the project `Contacts`_.


.. _about-getting-started:

Getting Started
===============

The following guides lead you through the process.

.. toctree::
   :maxdepth: 1

   install/index.rst
   build.rst
   editing.rst
   pull_requests.rst


Where to help
=============

.. toctree::
   :maxdepth: 1

   todo_list.rst


Guidelines
==========

.. toctree::
   :maxdepth: 1

   guides/writing_guide.rst
   guides/markup_guide.rst
   guides/commit_guide.rst
   guides/templates.rst
   guides/maintenance_guide.rst
   release_cycle.rst


Translations
============

.. toctree::
   :maxdepth: 1

   translations/contribute.rst
   translations/style_guide.rst


.. _contribute-contact:

Contacts
========

`Project Page <https://projects.blender.org/blender/documentation>`__
   An overview of the documentation project.
`Documentation Forum <https://devtalk.blender.org/c/documentation/12>`__
   A forum based discussions on writing and translating documentation.
   This includes the user manual, Wiki, release notes, and code docs.
:ref:`blender-chat`
   ``#docs`` channel for informal discussions in real-time.
`Project Workboard <https://projects.blender.org/blender/documentation/projects>`__
   Manage tasks such as bugs, todo lists, and future plans.


## Pull Requests

.. highlight:: sh

*************
Pull Requests
*************

This page describes the tools used for code contribution and review.

Reviews are a key measure to assure changes are of a good quality.
They help preventing bugs, design consistencies, or potential maintenance problems.
And having your work reviewed also generally keeps you on your toes.

.. note::

   Writers who have been given commit access can commit to the
   main repository without needing to fork the repository.

   See :doc:`/contribute/guides/commit_guide` if this applies to you.


One Time Setup
==============

This assumes you have the Blender manual repository already checked out on your computer,
following the :doc:`install instructions </contribute/install/index>`.


Fork
----

#. Go to Blender repository and click the Fork button.
#. Confirm the fork with the default settings.
#. Now you will have to add your personal fork as a remote in your local git repository.
   Click *SSH* to see the correct URL, and then add it like this::

      git remote add me git@projects.blender.org:<USERNAME>/blender-manual.git

.. note::

   In order to push to the fork repository, you need an SSH key.
   If you don't already have the file ``~/.ssh/id_rsa.pub``,
   there's a simple command to generate such keys which works on Linux, macOS, and in Git Bash on Windows::

      ssh-keygen

   This command will generate a private key id_rsa and a public key id_rsa.pub in ``~/.ssh``.
   The private key must never be shown or sent to anyone else to avoid compromising your account,
   but the public key is safe to share.

   The contents of ``~/.ssh/id_rsa.pub`` can be copied and pasted into
   the `account settings on projects.blender.org <https://projects.blender.org/user/settings/keys>`__,
   after clicking "Add Key". Any name for the SSH key is ok.


Workflow
========

The workflow for working with pull requests can be found in the
`Blender Developer's Documentation <https://developer.blender.org/docs/handbook/contributing/pull_requests/>`__.

Note, some text in the above guideline is focused on the main Blender repository,
however, the workflow is the same for any Blender project.


Guidelines for Reviewers
========================

- The pull request text should be usable as the git commit message
  (see the :ref:`guidelines <contribute-commit-good-message>` for details).
- Be explicit when some changes are to be addressed before committing, without the need for a review iteration.
- If the pull request is not approved the author is expected to make another iteration.
- If the change needs agreement on the design task first, put the pull request on hold by adding a
  ``WIP:`` prefix in the title, indicating the author considers the pull request not ready to be merged.
  No review is expected unless the author specifically asks for it.
- Writers are expected to reply to pull requests in 3 working days.
- Add relevant modules/projects to the labels.
- Encourage new writes to do review, it's a good way to learn and important to grow the project.


Tips
====

- To get the patch file, add .patch to the end of the URL of the pull request.
  Example::

     https://projects.blender.org/blender/blender-manual/pulls/104892.patch

- Checkout a pull request into a detached head (not leaving behind a branch).
  Example::

     git fetch -q origin +refs/pull/104892/head: ; git checkout -qf FETCH_HEAD


## Release Cycle

.. highlight:: sh

*************
Release Cycle
*************

A new Blender version is targeted to be released every 3 months.
The actual `release cycle <https://developer.blender.org/docs/handbook/release_process/release_cycle/>`__
for a specific release is longer, and overlaps the previous and next release cycle.

.. figure:: /images/about_contribute_release-cycle_diagram.png


Branches
========

Work is done in two branches:

- ``blender-v{VERSION}-release`` branch: fixes and other incremental improvements.
- ``main`` branch: documentation for new features and improvements for the release after that.

The ``blender-v{VERSION}-release`` branch will be available for 5 weeks prior to the release date.
At the same time ``main`` will be open for the next release,
giving 2 months to add documentation for new features of the next release, and another month to make improvements.


Switching Branches
------------------

To switch to the release branch use::

   git checkout blender-v{VERSION}-release

To switch back to the development branch use::

   git checkout main


Updating Branches
-----------------

To merge changes from the release branch to the development branch,
first switch to the development branch and use::

   git merge blender-v{VERSION}-release


Bcon Phases
===========

Each Blender version has its own Bcon phase,
indicating which types of changes are allowed to be committed and what writers are focusing on.

That means for example that Blender 2.90 can be in Bcon3 (wrapping up),
while Blender 2.91 is in Bcon1 (new features and changes).

.. list-table::
   :header-rows: 1
   :widths: 5 20 20 50 5

   * - Phase
     - Description
     - Duration
     - Details
     - Branch

   * - Bcon1

     - New features and changes

     - 4-5 weeks

     - The first 5 weeks overlap with the Bcon3 and Bcon4 phases of the previous release,
       Writing focus will be split on fixes for the previous release
       and writing documentation for features already added or likely to be added to Blender.
       This is also the perfect time to make any larger or more disruptive improvements to the manual.

     - ``main``

   * - Bcon2

     - Improve and stabilize

     - 4 weeks

     - Work to improve, optimize and fix bugs in new and existing features.
       All big or disruptive changes must be finished at the end of this stage.

     - ``main``

   * - Bcon3

     - Wrapping up

     - 4 weeks

     - Focus should be on fixes and other incremental improvements.
       All new Blender features should be documented by the end of this stage.

     - ``blender-v{VERSION}-release``

   * - Bcon4

     - Prepare release

     - 1 week

     - Focus should be wrapping up fixes and other incremental improvements.

     - ``blender-v{VERSION}-release``

   * - Bcon5

     - Release

     - 1-2 days

     - The manual is archived on the server and redirects / symlinks are updated.
       See the :ref:`Release Guide <about-contribute-guides-release>` for more information.

     -

   * - Bcon6

     - Long-term release

     - 2 years

     - In case a major error is found in the manual the patch will be committed to the release branch.

     - ``blender-v{VERSION}-release``


## Todo List


*********
Todo List
*********

This page provides a list of changes that need to be made to the manual.
This is a great place for new contributors to start but also check
the `documentation workboard <https://projects.blender.org/blender/documentation/projects>`__.

.. todolist::


## Commit Guide



*****************
Commit Guidelines
*****************

Access to directly submit changes is limited to people with commit access to the repository.
Once you are provided with commit access you can start committing directly instead of creating a patch file.

You can make commits from your Git client or using the Git command line tool.
The following command will create a commit and send it to the central repository::

   git commit -m "This is what I did"
   git push

If you leave out ``-m "message"``, you will be prompted to type the message in a text editor.

.. tip::

   You should make sure you are always on the latest revision before committing.
   You may not be able to commit directly if there are conflicting changes in the latest revision.

   To avoid this update your local repository before committing (run ``make update``).

.. seealso::

   `Blender's Git usage guide <https://developer.blender.org/docs/handbook/contributing/using_git/>`__

.. seealso::

   See :doc:`/contribute/release_cycle` for documentation on how to make
   commits to a specific release branch and how to create merge commits.


.. _contribute-commit-good-message:

Writing a Good Commit Message
=============================

When making changes to the manual that directly relate to a specific commit (change) in Blender,
it is helpful to make the title of the commit the same as the commit made to Blender.
It is requested that you include the commit hash of the commit made to the Blender source code.

For example, the commit `rBM8473 <https://developer.blender.org/rBM8473>`__
includes a descriptive indicative of the changes made along with the hash ``rBa71d2b260170``.
The hash can be extracted from the URL provided in the Documentation task for a specific upcoming release.

----

Other more general changes do not have to follow the above policy however,
it is still important to make the description clear about what changes you made and why.
It can be helpful to prefix the commit title with a prefix word such as ``Cleanup:`` or ``Fix:``
when you are making general cleanups or fixes respectively.

Writing good commit messages helps administrators keep track of
changes made and ensures all new features are properly documented.


## Maintenance Guide

.. highlight:: sh

***********
Maintenance
***********

Adding/Removing/Moving Files
============================

When RST-files are added or removed the corresponding locale files
are added or removed automatically by the update script.
However, if files need to be moved please use this Python script::

   python tools/utils_maintenance/rst_remap.py start

RST-files can then be freely moved and the remap script will move the locale file after::

   python tools/utils_maintenance/rst_remap.py finish

It is best to avoid moving/renaming files as this breaks URLs and
without this script translators will lose all their work in these files.
Please ask an administrator if you think something should be renamed/moved.

.. note::

   This script also works for image file names.


.. _about-contribute-guides-release:

Release Checklist
=================

- Create a release branch (``blender-3.2-release/``)
- Update the splash image: ``interface_splash_current.png`` in the release branch.
- Increase the ``conf.py: blender_version`` variable in the trunk version.


## Markup Guide

.. highlight:: rst

******************
Markup Style Guide
******************

.. Editor's Note:
   ::
   There are many detailed conventions, e.g:
   ::
   - When definition lists/bullet-points are used.
   - Word-ordering in filenames.
   - How text is wrapped.
   - The number of spaces between lines.
   - When it is/is not okay to add in Unicode characters.
   - Should comments on a page be above or below titles :)
   ::
   Having a lot of detailed text on this page is off-putting to new contributors,
   so please avoid making this page into a wall-of-text,
   many conventions can be noticed along the way by reading existing text.

This page covers the conventions for writing and use of the reStructuredText (RST) markup syntax.


Conventions
===========

- Three space indentation.
- Lines should be less than 120 characters long.
- Use italics for button/menu names.

Other loose conventions:

- Avoid Unicode characters.
- Avoid heavily wrapped text
  (i.e. sentences can have their own lines).


Headings
========

.. code-block:: rst

   #################
     Document Part
   #################

   ****************
   Document Chapter
   ****************

   Document Section
   ================

   Document Subsection
   -------------------

   Document Subsubsection
   ^^^^^^^^^^^^^^^^^^^^^^

   Document Paragraph
   """"""""""""""""""

.. note:: *Parts* should only be used for contents or index pages.

.. note:: Each ``.rst`` file should only have one chapter heading (``*``) per file.


Text Styling
============

See the `overview on ReStructuredText <https://www.sphinx-doc.org/en/master/usage/restructuredtext/basics.html>`__
for more information on how to style the various elements of the documentation and
on how to add lists, tables, pictures and code blocks.
The `Sphinx reference <https://www.sphinx-doc.org/en/master/usage/restructuredtext/index.html>`__ provides
more insight additional constructs.

The following are useful markups for text styling::

   *italic*
   **bold**
   ``literal``


Interface Elements
==================

- ``:kbd:`LMB``` -- keyboard and mouse shortcuts.
- ``*Mirror*`` -- interface labels.
- ``:menuselection:`3D Viewport --> Add --> Mesh --> Monkey``` -- menus.


Code Samples
============

There is support for syntax highlighting if the programming language is provided,
and line numbers can be optionally shown with the ``:linenos:`` option::

   .. code-block:: python
      :linenos:

      import bpy
      def some_function():
          ...


Images
======

Figures should be used to place images::

   .. figure:: /images/interface_window-system_splash_current.png

      Image caption.

For consistency, and since it would be good to ensure screenshots are
all a similar size when floated next to text,
writers should take screenshots in the following manner:

#. Prepare the area you would like to capture making sure to use the default theme and setting.
   (In some cases you may not want to use the default settings e.g. if some options are hidden behind a checkbox.)
#. Zoom to the maximum zoom level (hold :kbd:`NumpadPlus` or :kbd:`Ctrl-MMB` or similar).
#. Zoom out eight zoom levels (:kbd:`NumpadMinus` -- eight times).
#. In some cases you will want to leave a small margin around the thing you are trying to capture.
   This should be around 30px but does not have to be exact.

This can be applied to several parts of the interface but might not work for all cases.


Files
-----

No Caps, No Gaps
   Lower case filenames underscore between words.
Sort Usefully
   Order naming with specific identifiers at the end.
Format
   Use ``.png`` for images that have solid colors such as screenshots of the Blender interface,
   and ``.jpg`` for images with a high amount of color variance, such as sample renders and photographs.

   Do not use animated ``.gif`` files, these are hard to maintain, can be distracting
   and are usually large in file size. Instead use a video if needed (see `Videos`_ below).
Location
   Place the image in the ``manual/images`` folder. Use no other subfolders.
Naming
   For naming files use underscores to separate chapters and sections,
   and use dashes to separate sections that are two or more words.
   So for image files should look like: ``chapter_subsection_sub-subsection_id.png``, e.g:

   - ``interface_splash_current.png``
   - ``interface_undo-redo_last.png``
   - ``interface_undo-redo_repeat-history-menu.png``

   Do not use special characters or spaces!


Usage Guides
------------

- Avoid specifying the resolution of the image,
  so that the theme can handle the images consistently
  and provide the best layout across different screen sizes.
- When documenting a panel or section of the UI,
  it is better to use a single image that shows all of the relevant areas
  (rather than multiple images for each icon or button)
  placed at the top of the section you are writing,
  and then explain the features in the order that they appear in the image.

  .. note::

     It is important that the manual can be maintained long term,
     UI and tool options change so try to avoid having a lot of images
     (when they are not especially necessary).
     Otherwise, this becomes too much of a maintenance burden.


Videos
======

Videos can be embedded from Blender's self-hosted `PeerTube <https://joinpeertube.org/>`__ instance
which can be found at `video.blender.org <https://video.blender.org/>`__.
To embed a video using the following directive::

   .. peertube:: ID

The ``ID`` is found in the video's URL, e.g:

The ID for ``https://video.blender.org/videos/watch/47448bc1-0cc0-4bd1-b6c8-9115d8f7e08c``
is ``47448bc1-0cc0-4bd1-b6c8-9115d8f7e08c``.

To get a new video uploaded, contact
a `Documentation Project Administrator <https://projects.blender.org/blender/documentation>`__ or
include the uploaded video in your :doc:`Pull Request </contribute/pull_requests>` description.


Usage Guides
------------

- Avoid adding videos that rely on voice or words, as this is difficult to translate.
- Do not embed video tutorials as a means of explaining a feature, the writing itself should explain it adequately.
  (Though you may include a link to the video at the bottom of the page under the heading ``Tutorials``).


Useful Constructs
=================

- ``|BLENDER_VERSION|`` -- Resolves to the current Blender version.
- ``:abbr:`SSAO (Screen Space Ambient Occlusion)``` --
  Abbreviations display the full text as a tooltip for the reader.
- ``:term:`Manifold``` -- Links to an entry in the :doc:`Glossary </glossary/index>`.


Cross References and Linkage
============================

You can link to another document in the manual with::

   :doc:`The Title </section/path/to/file>`

To link to a specific section in another document (or the same one), explicit labels are available::

   .. _sample-label:

   [section or image to reference]

   Some text :ref:`Optional Title <sample-label>`

Linking to a title in the same file::

   Titles are Targets
   ==================

   Body text.

   Implicit references, like `Titles are Targets`_

Linking to the outside world::

   `Blender Website <https://www.blender.org>`__


Context Sensitive Manual Access
-------------------------------

It is possible to link to a specific part of the manual from in Blender by opening
the context menu (right click) of a property or operator and selecting *Online Manual*.
In order for this to work, this needs to be accounted for in the documentation.
To link a property or operator to a specific part of the manual you need to add
an external reference link tag whose ID matches Blender's RNA tag.
The easiest way to find out what the tag for a property is to open the context menu of
the property/operator and select *Online Python Reference* to extract the tag from the URL.
Some examples of how this looks in the RST document are given below::

   .. _bpy.types.FluidDomainSettings.use_fractions:

   Fractional Obstacles
      Enables finer resolution in fluid / obstacle regions (second order obstacles)...

      .. _bpy.types.FluidDomainSettings.fractions_distance:

      Obstacle Distance
         Determines how far apart fluid and obstacles are...

For an operator::

   .. _bpy.ops.curve.subdivide:

   Subdivide
   =========


Further Reading
===============

To learn more about reStructuredText, see:

`Sphinx RST Primer <https://www.sphinx-doc.org/en/master/usage/restructuredtext/basics.html>`__
   Good basic introduction.
`Docutils reStructuredText Reference <https://docutils.sourceforge.io/rst.html>`__
   Links to reference and user documentation.


## Templates

.. highlight:: rst

*********
Templates
*********

The following guide provides patterns for interface elements and directories.


Operator Menus
==============

Each operator should receive its own heading or page based on the length of the content.
At the start should be a reference admonition documenting the context of the operator::

   .. admonition:: Reference
      :class: refbox

      :Mode:      Edit Mode
      :Menu:      :menuselection:`Curve --> Snap`
      :Shortcut:  :kbd:`Shift-S`


Panels
======

Panels should be documented by their own heading, nested panels should use decreasing heading levels.
Each panel could have its own page based on the length of documentation and/or the amount of panels.
Expanded menus that toggle what properties are presented to the user should be treated like subpanels::

   Panel Title
   ===========

   Nested Panel Title
   ------------------


Properties
==========

Properties should be documented using definition lists.
Properties that are hidden based on other properties should used nested definitions::

   Property
      Property description.

      Hidden Property
         Hidden property description.

Select menus should be documented using the following syntax::

   Menu Label
      General description of the menu.

      :Menu Item: Menu Item Definition.
      :Menu Item: Menu Item Definition.
      :Menu Item: Menu Item Definition.


Nodes
=====

Nodes should always have three headings inputs, properties and outputs
with a note of absence if the node has none.
At the end of the page can be an optional example(s) section::

   **********
   World Node
   **********

   .. figure:: /images/render_shader-nodes_output_world_node.png
      :align: right

      The World node.

   Introduction and general use case(s).


   Inputs
   ======

   This node has no inputs.


   Properties
   ==========

   This node has no properties.


   Outputs
   =======

   This node has no outputs.


   Example
   =======


Directory Layout
================

Sections should be generally structured as follows:

- ``directory_name/``

  - ``index.rst`` (contains links to internal files)
  - ``introduction.rst``
  - ``section_1.rst``
  - ``section_2.rst``

For example:

- ``rendering/``

  - ``index.rst``
  - ``cycles/``

    - ``index.rst``
    - ``introduction.rst``
    - ``materials/``

      - ``index.rst``
      - ``introduction.rst``
      - ``volumes.rst``

The idea is to enclose all the content of a section inside of a folder. Ideally every section
should have an ``index.rst`` (containing the TOC for that section) and an ``introduction.rst``
(introducing) to the contents of the section.


Table of Contents
-----------------

By default, a table of contents should show two levels of depth::

   .. toctree::
      :maxdepth: 2

      introduction.rst
      perspective.rst
      depth_of_field.rst


## Writing Guide

.. highlight:: rst

*******************
Writing Style Guide
*******************

Primary Goals
=============

The main goals for this manual are as follows:

User Focused
   The manual is written for people educated in computer graphics,
   who understand the basics of 3D and/or know other 3D software.
   While some areas of computer graphics are highly technical,
   this manual shall be kept understandable by non-technical users.
Complete
   The manual provides detailed functional description of all features, tools and options in Blender.
   While there is a canonical source of truth for each of Blender's key areas,
   this does not mean we have to document every small detail.
   The manual should provide information on what a feature is, how to use it, and its purpose.
   More background information should be provided when necessary to give deeper understanding of a 3D pipeline.
Concise
   Computer graphics is an incredibly interesting field,
   there are many rules, exceptions to the rules, and interesting details.
   Expanding into details can add unnecessary content,
   so keep the text concise and relevant to the topic at hand.
Maintainable
   Keep in mind that Blender has frequent releases,
   so try to write content that will not have to be redone
   the moment some small change is made.
   This also helps a small documentation community to maintain the manual.


Content Guidelines
==================

In order to maintain a consistent writing style within the manual,
please keep this page in mind and only deviate from it when you have a good reason to do so.

Rules of thumb:

- Spell checking is *strongly* recommended.
- Use American English (e.g: modeling and not modelling, color and not colour)
  also for formatting numbers (e.g: 2,718.28 and not 2 718,28).
- Take care about grammar, appropriate wording and use simple English.
- Keep sentences short and clear, resulting in text that is easy to read, objective and to the point.
- Including why or how an option might be useful is a good idea.
- If you are unsure about how a feature works, ask someone else or find out who developed it and ask them.

To be avoided:

- Avoid writing in first person perspective, about yourself or your own opinions.
- Avoid `weasel words <https://en.wikipedia.org/wiki/Weasel_word>`__ and being unnecessarily vague, e.g:

  | "Reloading the file will probably fix the problem"
  | "Most people do not use this option because ..."
- Avoid including specific details such as:

  | "Blender has 23 different kinds of modifiers."
  | "Enabling previews adds 65536 bytes to the size of each blend-file (unless it is compressed)."

  These details are not useful for users to memorize and they become quickly outdated.
- Avoid documenting bugs.

  Blender often has 100's of bugs fixed between releases, so it is not realistic to reference
  even a fraction of them from the manual, while keeping this list up to date.

  Issues that are known to the developers and are not going to be resolved before the next release
  can be documented as *Known Limitations*.
  In some cases, it may be best to include them in the :doc:`troubleshooting </troubleshooting/index>` section.
- Avoid product placements, i.e. unnecessarily promoting software or hardware brands.
  Keep content vendor-neutral where possible.
- Avoid technical explanations about the mathematical/algorithmic implementation of a feature
  if there is a simpler way to explain it.

  (E.g. explaining how mesh smoothing algorithms work is unnecessary,
  but the blending types of a Mix node do need a mathematical explanation.)
- Avoid repetition of large portions of text. Simply explain it once, and from then on refer to that explanation.

  For general terminology, consider defining a ``:term:`` in the :doc:`glossary </glossary/index>`.
- Avoid enumerations of similar options, such as listing every preset or every frame rate in a select menu.

  Their contents may be summarized or simply omitted.
  -- Such lists are only showing what is already *obvious* in the interface
  and end up being a lot of text to read and maintain.
- Avoid documenting changes in Blender between releases, that is what the release notes are for.
  We only need to document the current state of Blender.
- Unless the unit a value is measured in is obscure and unpredictable, there is no need to mention it.
- Do not simply copy the tooltips from Blender.
  -- People will come to the manual to learn *more* than is provided by the UI.

  As a last resort you can add comment (which is not shown in the HTML page, but useful for other editors)::

     .. TODO, how does this tool work? ask Joe Blogg's.


Glossary
--------

This section is specifically about the :doc:`Glossary </glossary/index>` section,
where we define common terms in Blender and computer graphics.

Rules of thumb:

- Define the term before providing any further information.
- Avoid using constructs such as "it is" or "xyz is" before the definition.
- Avoid repeating the term immediately or using it in the definition.
- Avoid adding terms not found in Blender's interface or the manual.
- Avoid overly long entries.
  If an explanation of a complex term is needed, supplement with external links.
- Avoid duplicating documentation;
  if explaining the term is the primary focus of another section of the manual
  (e.g. if the term is the name of a tool),
  either just link to that section, or avoid creating a glossary entry entirely.
- URL references are to be added at the end, formatted as follows, e.g::

     See also `OpenGL <https://en.wikipedia.org/wiki/OpenGL>`__ on Wikipedia.


Examples
^^^^^^^^

This entry::

   Displacement Mapping
      Uses a grayscale heightmap, like Bump Mapping,
      but the image is used to physically move the vertices of the mesh at render time.
      This is of course only useful if the mesh has large amounts of vertices.

Would be written like this instead, putting a definition first::

   Displacement Mapping
      A method for distorting vertices based on an image.
      Similar to Bump Mapping, but instead operates on the mesh's actual geometry.
      This relies on the mesh having enough geometry.

----

This entry::

   Doppler Effect
      The Doppler effect is the change in pitch that occurs
      when a sound has a velocity relative to the listener.

Would be written more like this, avoiding the immediate repetition of the term::

   Doppler Effect
      Perceived change in pitch that occurs
      when the source of a sound is moving relative to the listener.

----

This entry::

   Curve
      It is a class of objects.
      In Blender there are Bézier curves and NURBS curves.

Would be written more like this, avoiding the "it is"::

   Curve
      A type of object defined in terms of a line interpolated between Control Vertices.
      Available types of curves include Bézier and NURBS.


## Index

.. _about-install-index:

###########################
  Installing Dependencies
###########################

This section documents how to install the software used to generate the manual.
The installation is different for each operating system, instructions have been written for:

.. toctree::
   :maxdepth: 1

   Linux <linux.rst>
   macOS <macos.rst>
   Windows <windows.rst>


## Linux

.. highlight:: sh

*********************
Installation on Linux
*********************

This guide covers the following topics:

#. `Installing Dependencies`_
#. `Downloading the Repository`_
#. `Setting up the Build Environment`_


Installing Dependencies
=======================

Below are listed the installation commands for popular Linux distributions.

For the appropriate system, run the command in a terminal:

Debian/Ubuntu::

   sudo apt-get install python3 python3-pip git git-lfs
   git lfs install --skip-repo

Redhat/Fedora::

   sudo yum install python python-pip git git-lfs
   git lfs install --skip-repo

Arch Linux::

   sudo pacman -S python python-pip git git-lfs
   git lfs install --skip-repo


Downloading the Repository
==========================

Simply check out the Blender Manual's repository using::

   cd ~
   git clone https://projects.blender.org/blender/blender-manual.git

The repository will now be downloaded which may take a few minutes depending on your internet connection.


Setting up the Build Environment
================================

.. tip::

   It is recommended to setup and activate a virtual Python environment where dependencies will be installed::

      python3 -m venv .venv
      source .venv/bin/activate

   Repeat the ``source .venv/bin/activate`` command to re-activate the virtual environment,
   whenever you open a new terminal to build the documentation.

   This step may be required on some distributions that enforce `PEP 668 <https://peps.python.org/pep-0668/>`__.


- Open a Terminal window.
- Enter the ``blender-manual`` folder which was just added by ``git clone``::

     cd ~/blender-manual

- Inside that folder is a file called ``requirements.txt`` which contains a list of all the dependencies we need.
  To install these dependencies, we can use the ``pip3`` command::

     pip3 install -r requirements.txt

.. note::

   Every now and then you may want to make sure your dependencies are up to date using::

      pip3 install -r requirements.txt --upgrade


## Macos

.. highlight:: sh

*********************
Installation on macOS
*********************

This guide covers the following topics:

#. `Installing Dependencies`_
#. `Downloading the Repository`_
#. `Setting up the Build Environment`_

.. note::

   This guide relies heavily on command-line tools.
   It assumes you are the least familiar with the macOS Terminal application.


Installing Dependencies
=======================

Install those packages or make sure you have them in your system.

- `PIP <https://pip.pypa.io/en/latest/installing/>`__
- `Git <https://git-scm.com/download/mac>`__
- `Git LFS <https://git-lfs.com>`__

When using `Homebrew <https://brew.sh>`__, run the following commands in the terminal::

   python3 -m ensurepip
   brew install git git-lfs
   git lfs install


Downloading the Repository
==========================

Simply check out the Blender Manual's repository using::

   cd ~
   git clone https://projects.blender.org/blender/blender-manual.git

The repository will now be downloaded which may take a few minutes depending on your internet connection.


Setting up the Build Environment
================================

.. tip::

   It is recommended to setup and activate a virtual Python environment where dependencies will be installed::

      python3 -m venv .venv
      source .venv/bin/activate

   Repeat the ``source .venv/bin/activate`` command to re-activate the virtual environment,
   whenever you open a new terminal to build the documentation.


- Open a Terminal window.
- Enter the ``blender-manual`` folder which was just added by ``git clone``::

     cd ~/blender-manual

- Inside that folder is a file called ``requirements.txt`` which contains a list of all the dependencies we need.
  To install these dependencies, we can use the ``pip`` command::

     pip install -r requirements.txt

.. note::

   Every now and then you may want to make sure your dependencies are up to date using::

      pip install -r requirements.txt --upgrade


## Windows

.. highlight:: sh

***********************
Installation on Windows
***********************

This guide covers the following topics:

#. `Installing Python`_ (used to "convert" the source files to HTML)
#. `Installing Git and Downloading the Repository`_
#. `Setting up the Build Environment`_


Installing Python
=================

#. Download the `Python installation package <https://www.python.org/downloads/>`__ for Windows.
   In this guide version 3.9.x is used.
#. Install Python with the installation wizard.
   Please make sure that you enable the "Add Python to PATH" option:

   .. figure:: /images/about_contribute_install_windows_installer.png

      The option must be enabled so you can build the manual with the make script.

   All other settings can remain as set by default.


Installing Git and Downloading the Repository
=============================================

In this guide, we will use the official Git client, though any Git client will do.

#. Download and install `Git <https://git-scm.com/download/win>`__ for Windows.
#. Simply check out the Blender Manual's repository using::

      cd ~
      git lfs install
      git clone https://projects.blender.org/blender/blender-manual.git

#. The repository will now be downloaded which may take a few minutes depending on your internet connection.

.. note::

   This process can be completed using a graphical Git client,
   in that case you will just use the repository address in the URL field provided by your client::

      https://projects.blender.org/blender/blender-manual.git


Setting up the Build Environment
================================

.. tip::

   It is recommended to setup and activate a virtual Python environment where dependencies will be installed::

      python3 -m venv .venv
      .venv/Scripts/activate

   Repeat the ``.venv/Scripts/activate`` command to re-activate the virtual environment,
   whenever you open a new terminal to build the documentation.


- Open a Command Prompt. (Run as Administrator)
- Enter the ``blender-manual`` folder which was just added by ``git clone``::

     cd C:\blender-manual

- Inside that folder is a file called ``requirements.txt`` which contains a list of all the dependencies we need.
  Install all the dependencies using Python's ``pip`` command::

     pip install -r requirements.txt

- If all goes well, you should see the following message when it is finished::

     Successfully installed Jinja2 MarkupSafe Pygments Sphinx docutils sphinx-rtd-theme Cleaning up...

During the setup, some warnings may be shown, but do not worry about them.
However, if any errors occur, they may cause some problems.

.. note::

   Every now and then you may want to make sure your dependencies are up to date using::

      pip install -r requirements.txt --upgrade


## Add Language

:orphan:

.. highlight:: sh

*****************
Adding a Language
*****************

Preparations
============

If the language you want to translate has not been started by someone else already and
you wish to create a set of new files for the desired language, say 'fr' (French),
then you must first use the environment you have created,
as guided in :ref:`Getting Started <about-getting-started>`,
in particular :doc:`/contribute/install/index` and :doc:`/contribute/build` sections.

This will give you a foundation environment for:

- Creating a new set of translation language from English source.
- Perform ``make`` command to turn translated texts in po files into html files for testing locally.
- Update changes in English texts which have been added by other contributors.

Below examples show the process to create a new set of files for French, language code ``fr``, on Linux platform.
Other platforms might vary slightly but should be mainly the same.

#. `Create a Blender ID <https://id.blender.org/register/>`__ if you have not done so already.
#. Log into `projects.blender.org <https://projects.blender.org/>`__ and
   `Create an Issue <https://projects.blender.org/blender/documentation/issues/new>`__
   requesting for commit access in order to transfer changes to the central repository of the translation team.
#. Open an instance of a console application.
#. Change the current working directory to the directory of ``blender-manual``,
   where the instance of ``Makefile`` resides.


Trying the Make Process to Create HTML Files in English
=======================================================

#. Ensure the previous instance of ``build`` directory is removed, if any exists::

      make clean

#. Convert all the ``rst`` files into ``pot`` translation files::

      make gettext

#. Create ``html`` files::

      make html

#. After this, you can actually view the created html files locally
   by opening the ``blender-manual/build/html/index.html`` file.


Creating the Language Entry in the HTML Menu
============================================

#. Create an entry for the language in the html menu by opening file ``./build_files/theme/js/version_switch.js``
   (assuming you are at the ``blender-manual`` subdirectory).
#. Find the table for the languages in ``var all_langs = {..};``.
#. Enter the entry: ``"fr": "Fran&ccedil;ais",``, (``"fr": "Français"``).
   (Notice the Unicode characters.)
#. Commit the updated file::

      git add ./build_files/theme/js/version_switch.js
      git commit -m "HTML: Add French to language menu"

#. Push your changes to the upstream repository::

      git push


Generating the Set of Files for the Target Language
===================================================

#. Check out the current translation repository using the command::

      git clone https://projects.blender.org/blender/blender-manual-translations.git locale

   This will download all language sets available in the repository into the ``locale`` directory of your drive.
   You can go to the ``locale`` directory to see the hidden subdirectory ``.git`` within it,
   together with directories of languages.
   You'll need to add your own set of files for the language you are trying to translating to.

#. From the ``blender-manual`` directory to generate a set of files for ``fr`` language::

      make update_po

   These files are still in English only, with all ``msgstr`` entries blank.

#. Submit new set of files to the central repository::

      cd locale
      git add fr
      git commit -m "Initial commit language set of files for French"

.. tip::

   - It is recommended you make two environment variables for these directories, in the ``.bashrc``
     to make it more convenient for changing or scripting batch/shell commands
     for the process of translation and reviewing results::

        export BLENDER_MAN_EN=$HOME/<directory to make file directory above>/blender-manual
        export BLENDER_MAN_FR=$BLENDER_MAN_EN/locale

   - Newly generated files will contain some placeholders for authors and revision dates etc.
     If you find the job of replacing them repetitive, make use of the script ``change_placeholders.sh``
     in the subdirectory ``~/blender-manual/tools/util_maintenance``, make a copy of that to your local ``bin``
     directory and replace all values that were mentioned in the file with your specific details,
     then after each change to a file, you would do following commands
     to update the file with your personal details, revision date and time,
     plus generating the html files for your language, which you can view using your Internet browser::

        $HOME/bin/change_placeholders.sh $BLENDER_MAN_FR
        make -d --trace -w -B -e SPHINXOPTS="-D language='fr'" 2>&1


## Contribute

.. highlight:: sh

**********
Contribute
**********

On this page French (``fr``) is used for examples. However, it can be replaced with other
`languages codes <https://www.gnu.org/software/gettext/manual/html_node/Usual-Language-Codes.html>`__.
So, be sure to change the ``/fr`` suffixes in this guide to the language you are translating!

To see which languages are currently available, you can check the
`online interface <https://translate.blender.org/projects/blender-manual/manual/>`__,
or browse the `underlying git repository <https://projects.blender.org/blender/blender-manual-translations>`__.


===================
Simple Contribution
===================

The preferred way to contribute to the translation effor is the use the
`web-based interface <https://translate.blender.org/projects/blender-manual/manual>`__,
currently a Weblate instance.

Simple enhancement suggestions can be contributed by any user, even without loging in.
Suggestions will be reviewed by the translating team before they get published.

Weblate also comes with new helping tools to improve coherance of translations, like the
`glossary <https://translate.blender.org/projects/blender-manual/glossary/>`__.


===================
Advanced Operations
===================

If for some reasons the web-based translation interface does not work well for you,
you can still download PO file from it, and upload back it later.

.. warning::

   You will have to deal with potential conflicts yourself if some update happened in the mean time.
   Direct commit to the git repository for translations is not possible anymore.

.. note::

   There is a known issue with the current tool behind the web interface,
   which will make heavy processing like upload and integration of a PO file
   take several minutes, with the web page staying in refresh mode for the whole time.
   If it takes more than ten minutes, it will even apparently fail
   with a server timeout error message.
   There is usually no actual problem though, so no need to re-try uploading the PO file then,
   refreshing the page after a few minutes should be enough
   to see the contribution in the web interface.

.. note::

   First of all, it is assumed that you have the manual already building.
   If you have not done this already go back too
   the :ref:`Getting Started <about-getting-started>` section.


Installing
==========

Language Files
--------------

From the directory containing your checkout of the manual run::

   make checkout_locale

You will be prompted to type in the language folder you want to download.
In the case of this example we will use ``fr``. Pressing :kbd:`Return` will confirm this selection.

It will take a few minutes to download but once complete it will create a ``locale/fr`` subdirectory.

You should have a directory layout like this::

   blender-manual
      |- locale/
      |  |- fr/
      |  |  |- LC_MESSAGES/
      |- manual/

.. note::

   When running Git from the command line (such as updating),
   you will need to change directory to ``locale`` first rather than the ``blender-manual`` directory.


The PO language files themselves can also be downloaded from the web interface, ``Files`` menu,
on each dedicated language page of the ``Manual`` comnponent.


A PO Editor
-----------

To make edit the PO files you will need to install a PO editor.
We recommend that you use `Poedit <https://poedit.net/>`__,
however any PO editor will do.

.. note::

   For Linux users, you will have to check with
   your distribution's software center for a version of Poedit.
   This editor is only a recommendation. There are others, such as Kate and Kwrite, that
   could offer syntax highlighting and basic tools for text editing, e.g. letter case transposes.
   Other platforms can use some text editors supporting the syntax highlighting for PO files,
   or allowing you to create a custom one (such as Notepad++ on Windows).


Building with Translations
==========================

Building
--------

Now you can build the manual with the translation applied:

On Linux and macOS run::

   make -e BF_LANG=fr

On Windows run::

   set BF_LANG=fr
   make html

Now you will have a build of the manual with translations applied.


Editing Translation Files
=========================

Now you can edit the PO translation files, in the ``LC_MESSAGES`` folder you have two files:

- ``blender_manual.po`` -- This is the main translation file that you will be editing.
- ``sphinx.po`` -- This translation file is much smaller and contains translations for the website theme.

To edit these files open them up in your translation editor, i.e. Poedit.
Once in your editor you will see a list of texts, each of these items represent some part of the user manual.
You may need to adjust your editor to sort the list in a way that makes sense for example "by source".

You can now select an untranslated string and your editor will have an input box to add the translation.
The modified ``.po`` files can now be submitted back to the web-based interface.

.. tip::

   Make sure that you `Building with Translations`_ to catch any syntax errors you may make while translating.
   These errors will be displayed as warnings while building the manual.


Maintenance
===========

.. _translations-fuzzy-strings:

Keeping Track of Fuzzy Strings
------------------------------

When the manual is updated, those translations which are outdated will be marked as fuzzy.
To keep track with that, you can use a tool we created for that task.

You can do this by running::

   make report_po_progress

This will only give a quick summary however, you can get more information by running::

   python tools/translations/report_translation_progress.py locale/fr/

You should get a list of all the files with information about the number of empty and fuzzy strings.
For more options see::

   python tools/translations/report_translation_progress.py --help


Updating PO Files
-----------------

As the original manual changes, the templates will need updating.
Note, doing this is not required,
as administrator usually update the files for all languages at once.
This allows all languages to be on the same version of the manual.
However, if you need to update the files yourself, it can be done as follows::

   make update_po

The updated templates can then be committed to the repository.

.. seealso::

   A guide how to add a new language can be found in the :doc:`/contribute/translations/add_language`.


## Style Guide


***********
Style Guide
***********

This page covers conventions concerning the translations.

.. note::

   - We expect our readers to use the English version of Blender, not a translated one.
   - The translations are licensed under the same :doc:`/copyright` as the original.


Should I Translate\.\.\. ?
==========================

Maybe
-----

Hyperlinks
   Can be translated, but only as an addition, not as a replacement.
   See also `Adding Text`_.

Technical Terms
   Only translate these, when the localized expression is common!
   See also `Technical Terms`_.

Text you are not sure you understood
   Simply mark the text as fuzzy and/or add a comment.
   The next translator might understand it.


Never
-----

Images
   You probably will not find the original scene if it is a screenshot of a file
   and it is too much load on the server (and too much work for you).

Menu and button names
   We expect our readers to use the English UI.

Text you do not understand
   Do not translate it! It will do more harm than good!


Technical Terms
===============

In general, the technical terms used in computer graphics are quite new or even downright
neologisms invented for the needs,
so they do not always have a translation in your language. Moreover,
a large part of Blender users use its English interface.

As a result, unless a term has an evident translation,
you should preferably use the English one, *putting it in italic*.
You can then find a translation for it, which you will use from times to times (e.g. to avoid repetitions...).
This is also valid in the other way: even when a term has a straightforward translation,
do not hesitate to use its English version from times to times, to get the reader used with it...

If a term is definitively not translatable, simply use the English one,
but make sure its glossary entry is translated.

In the glossary, the English term is written first (to maintain alphabetic order)
with the translated entry following in parenthesis, when appropriate.


Adding Text
===========

Generally, **you should always translate exactly what is in the text**,
and avoid providing updates or extra information.

But sometimes that is necessary, for example when talking about the manual itself:
To a foreign reader it is not clear, that they can contribute English text only,
whereas this is obvious to an English reader.

In these (rare) cases you can and should provide extra information.


Keeping Pages Up To Date
========================

When the manual is updated, those translations which are outdated will be marked as fuzzy.
To keep track with that, you can use a tool we created for that task,
see :ref:`How to install it <translations-fuzzy-strings>`.


