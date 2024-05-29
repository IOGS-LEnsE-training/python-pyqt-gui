SimpleWidget Example
####################

This section presents a simple widget that can be included in a largest window.

.. image:: ../../_static/images/simplewidget_example.png
   :alt: SimpleWidget view
   :align: center

|

The complete file :file:`SimpleWidget.py` of this example is in the :file:`interface/elements/` directory.

|

SimpleWidget class
******************

This class inherites from the QWidget class, a container of Qt application. In the initialization function of this new class, the constructor (__init__ function) of the mother class is called (mother class is the QWidget class).

.. code-block:: python
  :linenos:

  class SimpleWidget(QWidget):
    def __init__(self, title='', background_color='#0A3250', text_color='#FFFFFF'):
      super().__init__(parent=None)


Arguments of the class
======================

This class contains :

- a title : corresponding to the text displays in the center of the widget;
- a background color;
- a text color.

They are defined as argument of the contructor of the class.


CSS Style
=========

To make the interface more visually appealing, it is possible to add **CSS elements** (recognized by PyQt6).

.. code-block:: python
  :linenos:
  
  style_css = "background-color: "+self.background_color+";"
  style_css+= "border-radius: 10px;"
  style_css+= "border-color: black; border-width: 2px; font: bold 12px; padding: 20px;"
  style_css+= "border-style: solid;"
  style_css+= "color: "+self.text_color+";"
  self.setStyleSheet(style_css)

The CSS style is applied thanks to the :code:`setStyleSheet` of the :class:`QWidget` class.

To learn more about CSS Style, you can check this tutorial : `Start with CSS <https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/CSS_basics>`_.

Graphical objects
=================



.. code-block:: python
  :linenos:
  
  self.layout = QGridLayout()
  self.setLayout(self.layout)
   
  self.title_label = QLabel(self.title)
  style_css = "color: "+self.text_color+";"
  self.title_label.setStyleSheet(style_css)
  self.title_label.setAlignment(Qt.AlignmentFlag.AlignCenter)

  self.layout.addWidget(self.title_label, 0, 0) 


Test the class
**************

.. code-block:: python
  :linenos:

  if __name__ == '__main__':
    import sys
    from PyQt6.QtGui import QIcon

    class MyWindow(QMainWindow):
      def __init__(self):
        super().__init__()
        # Define Window title
        self.setWindowTitle("LEnsE - Window Title")
        self.setWindowIcon(QIcon('images/IOGS-LEnsE-logo.jpg'))
        self.setGeometry(50, 50, 1000, 700)    
                  
        # Widget to test
        self.main_area = SimpleWidget(title='Main Area', 
                                      background_color='white',
                                      text_color='red')
        self.setCentralWidget(self.main_area)
    
    app = QApplication(sys.argv)
    main = MyWindow()
    main.show()
    sys.exit(app.exec())
