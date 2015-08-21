Developing Orange3 Add-ons
==========================

Orange add-on is an ordinary python package, installed by running setup.py install and
distributed via pypi. Widgets, tutorials and help are registered in setup.py file using
entry points. When Orange Canvas starts, it reads this entry points, registers all the
widgets and adds them to the menu. This containts one widget (Hello World), which is
contained in a new category (My Category). The widget also displays help when you press F1.

The My Category category is registered using "orange.widgets" entry point in setup.py,
which contains category name (My Category) and package that contains the widgets
(orangecontrib.example.widgets). The packages __init__.py contains category metadata,
including category ICON, BACKGROUD color and WIDGET_HELP_PATH. The latter can be either
a local path or a url to a server which hosts the add-on documentation.

Orange Canvas will automatically discover all widget modules that are placed inside
the category package and put found widgets into the category. Widget is a class extending
Orange.widgets.widget.OWWidget and has an attribute name. Each widget should be placed in
a separate directory. Widget help is placed inside the doc/widgets directory. It can be
written in markdown or rst, the only requirement is that the title of the page is the same
as the widget name. All widgets should be linked from the page that is listed in
WIDGET_HELP_PATH. Links should reside in section called Widgets, containing links to the
documents with widget documentation.

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

