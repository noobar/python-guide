.. ==================
.. Image Manipulation
.. ==================
========
画像操作
========

.. Most image processing and manipulation techniques can be carried out
.. effectively using two libraries: Python Imaging Library (PIL)  and OpenSource
.. Computer Vision (OpenCV).
ほとんどの画像処理および操作技術は、Python Imaging Library（PIL）とOpenSource Computer Vision（OpenCV）の2つのライブラリを使用して効果的に実行できます。

.. A brief description of both is given below.
両方の簡単な説明を以下に示します。

Python Imaging Library
----------------------

.. The `Python Imaging Library <http://www.pythonware.com/products/pil/>`_, or PIL
.. for short, is one of the core libraries for image manipulation in Python. Unfortunately,
.. its development has stagnated, with its last release in 2009.
`Python Imaging Library <http://www.pythonware.com/products/pil/>`_ またはPILは、Pythonでの画像操作のためのコアライブラリの1つです。 残念ながら、2009年の最後のリリースでは、その開発は停滞しています。

.. Luckily for you, there's an actively-developed fork of PIL called
.. `Pillow <http://python-pillow.github.io/>`_ - it's easier to install, runs on
.. all operating systems, and supports Python 3.
幸いなことに、積極的に開発されたPILのフォーク `Pillow <http://python-pillow.github.io/>`_ があります。インストールが簡単で、すべてのオペレーティングシステムで動作し、Python 3をサポートしています。

.. Installation
.. ~~~~~~~~~~~~
インストール
~~~~~~~~~~~~

.. Before installing Pillow, you'll have to install Pillow's prerequisites. Find
.. the instructions for your platform in the
.. `Pillow installation instructions <https://pillow.readthedocs.io/en/3.0.0/installation.html>`_.
Pillowをインストールする前に、Pillowの前提条件をインストールする必要があります。 `Pillowのインストール手順 <https://pillow.readthedocs.io/ja/3.0.0/installation.html>`_ でお使いのプラットフォームの手順を見つけてください。

.. After that, it's straightforward:
その後、それは簡単です:

.. code-block:: console

    $ pip install Pillow

.. Example
.. ~~~~~~~
例
~~

.. code-block:: python

    from PIL import Image, ImageFilter
    #Read image
    im = Image.open( 'image.jpg' )
    #Display image
    im.show()

    #Applying a filter to the image
    im_sharp = im.filter( ImageFilter.SHARPEN )
    #Saving the filtered image to a new file
    im_sharp.save( 'image_sharpened.jpg', 'JPEG' )

    #Splitting the image into its respective bands, i.e. Red, Green,
    #and Blue for RGB
    r,g,b = im_sharp.split()

    #Viewing EXIF data embedded in image
    exif_data = im._getexif()
    exif_data

.. There are more examples of the Pillow library in the
.. `Pillow tutorial <https://pillow.readthedocs.io/en/3.0.x/handbook/tutorial.html>`_.
Pillowライブラリの例は、 `Pillow tutorial <https://pillow.readthedocs.io/en/3.0.x/handbook/tutorial.html>`_ にあります。


OpenSource Computer Vision
--------------------------

.. OpenSource Computer Vision, more commonly known as OpenCV, is a more advanced
.. image manipulation and processing software than PIL. It has been implemented
.. in several languages and is widely used.
OpenSource Computer Visionは、一般にOpenCVとして知られ、PILよりも高度な画像操作と処理ソフトウェアです。 いくつかの言語で実装されており、広く使用されています。

.. Installation
.. ~~~~~~~~~~~~
インストール
~~~~~~~~~~~~

.. In Python, image processing using OpenCV is implemented using the ``cv2`` and
.. ``NumPy`` modules.  The `installation instructions for OpenCV
.. <http://docs.opencv.org/2.4/doc/tutorials/introduction/table_of_content_introduction/table_of_content_introduction.html#table-of-content-introduction>`_
.. should guide you through configuring the project for yourself.
Pythonでは、OpenCVを使った画像処理は ``cv2`` と ``NumPy`` モジュールを使って実装されています。 `OpenCVのインストール手順 <http://docs.opencv.org/2.4/doc/tutorials/introduction/table_of_content_introduction/table_of_content_introduction.html#table-of-content-introduction>`_ はあなた自身でプロジェクトを設定する際の手引きです 。

.. NumPy can be downloaded from the Python Package Index(PyPI):
NumPyは、Python Package Index（PyPI）からダウンロードできます。

.. code-block:: console

    $ pip install numpy


Example
~~~~~~~

.. code-block:: python

    from cv2 import *
    import numpy as np
    #Read Image
    img = cv2.imread('testimg.jpg')
    #Display Image
    cv2.imshow('image',img)
    cv2.waitKey(0)
    cv2.destroyAllWindows()

    #Applying Grayscale filter to image
    gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)

    #Saving filtered image to new file
    cv2.imwrite('graytest.jpg',gray)

.. There are more Python-implemented examples of OpenCV in this `collection of
.. tutorials
.. <https://opencv-python-tutroals.readthedocs.io/en/latest/py_tutorials/py_tutorials.html>`_.
この `チュートリアルのコレクション <https://opencv-python-tutroals.readthedocs.io/en/latest/py_tutorials/py_tutorials.html>`_ には、Pythonで実装されたOpenCVの例がたくさんあります
