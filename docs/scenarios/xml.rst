.. XML parsing
.. ===========

XML解析
=======

untangle
--------

.. `untangle <https://github.com/stchris/untangle>`_ is a simple library which
.. takes an XML document and returns a Python object which mirrors the nodes and
.. attributes in its structure.

`untangle <https://github.com/stchris/untangle>`_ は、XML文書を受け取り、構造内のノードと属性を反映するPythonオブジェクトを返す単純なライブラリです。

.. For example, an XML file like this:

たとえば、次のようなXMLファイルがあります:

.. code-block:: xml

    <?xml version="1.0"?>
    <root>
        <child name="child1">
    </root>

.. can be loaded like this:

次のようにロードすることができます:

.. code-block:: python

    import untangle
    obj = untangle.parse('path/to/file.xml')

.. and then you can get the child elements name like this:

そして次のように子要素の名前を取得できます:

.. code-block:: python

    obj.root.child['name']

.. untangle also supports loading XML from a string or an URL.

untangleは、文字列またはURLからXMLを読み込むこともサポートしています。

xmltodict
---------

.. `xmltodict <http://github.com/martinblech/xmltodict>`_ is another simple
.. library that aims at making XML feel like working with JSON.

`xmltodict <http://github.com/martinblech/xmltodict>`_ は、XMLをJSONのように扱えるようにするためのもう一つの単純なライブラリです。

.. An XML file like this:

次のようなXMLファイル:

.. code-block:: xml

    <mydocument has="an attribute">
      <and>
        <many>elements</many>
        <many>more elements</many>
      </and>
      <plus a="complex">
        element as well
      </plus>
    </mydocument>

.. can be loaded into a Python dict like this:

次のようにPython dictにロードすることができます:

.. code-block:: python

    import xmltodict

    with open('path/to/file.xml') as fd:
        doc = xmltodict.parse(fd.read())

.. and then you can access elements, attributes and values like this:

次に、次のように要素、属性、および値にアクセスできます:

.. code-block:: python

    doc['mydocument']['@has'] # == u'an attribute'
    doc['mydocument']['and']['many'] # == [u'elements', u'more elements']
    doc['mydocument']['plus']['@a'] # == u'complex'
    doc['mydocument']['plus']['#text'] # == u'element as well'

.. xmltodict also lets you roundtrip back to XML with the unparse function,
.. has a streaming mode suitable for handling files that don't fit in memory
.. and supports namespaces.

xmltodictは、未解析関数を使用してXMLへのラウンドトリップを可能にし、メモリに収まらないファイルを処理するのに適したストリーミングモードを持ち、名前空間をサポートします。
