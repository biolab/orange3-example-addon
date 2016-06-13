Developing Orange3 Add-ons
==========================

Orange add-on is an ordinary python package, installed by running setup.py install and
distributed via pypi. Widgets, tutorials and help are registered in setup.py file using
entry points. When Orange Canvas starts, it reads this entry points, registers all the
widgets and adds them to the menu. This containts one widget (Hello World), which is
contained in a new category (My Category). The widget also displays help when you press F1.

Registering widgets
-------------------
The My Category category is registered using "orange.widgets" entry point in setup.py,
which contains category name (My Category) and package that contains the widgets
(orangecontrib.example.widgets). The packages __init__.py contains category metadata,
including category ICON, BACKGROUD color and WIDGET_HELP_PATH. The latter can be either
a local path or a url to a server which hosts the add-on documentation.

Orange Canvas will automatically discover all widget modules that are placed inside
the category package and put found widgets into the category. Widget is a class extending
Orange.widgets.widget.OWWidget and has an attribute name. Each widget should be placed in
a separate directory.

Providing Help files
--------------------
When F1 is press on open widget or on a selected widget icon, a help file is shown. Help
files are ordinary documentation pages, written in rst and placed into doc/widgets folder.

Help pages can be written in markdown or in rst. The only requirement is that the title of
the page is the same as the widget name. To allow automatic discovery of help pages, all
widget help pages should be listed on a documentation page inside a section named Widget.

The location of the documentation is set using the "orange.canvas.help" entrypoint. It
usually points to the constant WIDGET_HELP_PATH in the package containing widgets. The
constant should list the possible locations of the master page (the one that links to
all widgets). This example add-on includes three different locations:
  - Development documentation is available for developers that manually build documentation
    using sphinx
  - Locally installed documentation, which is available if the add-on was installed using
    a wheel package. Local installation has to be enabled in setup.py by calling function
    include_documentation.
  - Online documentation points to the hosted documentation such as read the docs or
    python hosted.

The locations are tried in order they are listed, the first one available will be used.

Beside widgets, add-on can also include tutorial schemas, that are shown in the Welcome
dialog. Tutorials are ordinary ows files, but often include annotations that guide the user.
Tutorial packages are registered in setup.py using "orange.widgets.tutorials" entry point.

Contents:

.. toctree::
   :maxdepth: 2

Widgets
-------

.. toctree::
   :maxdepth: 1

   widgets/mywidget

Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`

