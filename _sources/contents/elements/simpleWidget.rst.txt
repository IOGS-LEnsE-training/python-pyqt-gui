SimpleWidget Example
====================

This section presents a simple widget that can be included in a largest window.

.. image:: ../../_static/images/simplewidget_example.png
   :alt: SimpleWidget view
   :align: center

|

The complete file :file:`SimpleWidget.py` of this example is in the :file:`interface/elements/` directory.

|

SimpleWidget class
------------------

This class inherites from the QWidget class, a container of Qt application. In the initialization function of this new class, the constructor (__init__ function) of the mother class is called (mother class is the QWidget class).

.. code-block:: python
  :linenos:

	class SimpleWidget(QWidget):
		def __init__(self, title='', background_color='#0A3250', text_color='#FFFFFF'):
			super().__init__(parent=None)

