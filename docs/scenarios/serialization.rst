.. ==================
.. Data Serialization
.. ==================

==================
データのシリアル化
==================

.. What is data serialization?
.. ---------------------------

データのシリアル化とは何ですか？
--------------------------------

.. Data serialization is the concept of converting structured data into a format 
.. that allows it to be shared or stored in such a way that its original 
.. structure to be recovered. In some cases, the secondary intention of data 
.. serialization is to minimize the size of the serialized data which then 
.. minimizes disk space or bandwidth requirements.

データのシリアル化は、構造化されたデータを、元の構造が復元されるように共有または格納できる形式に変換する概念です。場合によっては、データの直列化の第2の目的は、直列化されたデータのサイズを最小限に抑え、ディスクのスペースまたは帯域幅の要件を最小限に抑えることです。

Pickle
------

.. The native data serialization module for Python is called `Pickle 
.. <https://docs.python.org/2/library/pickle.html>`_. 

Pythonのネイティブデータシリアライゼーションモジュールは、 `Pickle <https://docs.python.org/2/library/pickle.html>`_ と呼ばれます。

.. Here's an example:

ここに例があります:

.. code-block:: python
       
        import pickle
        
        #Here's an example dict
        grades = { 'Alice': 89, 'Bob': 72, 'Charles': 87 }
      
        #Use dumps to convert the object to a serialized string
        serial_grades = pickle.dumps( grades )
       
        #Use loads to de-serialize an object 
        received_grades = pickle.loads( serial_grades )

Protobuf
--------

.. If you're looking for a serialization module that has support in multiple 
.. languages, Google's `Protobuf 
.. <https://developers.google.com/protocol-buffers>`_ library is an option. 

複数の言語でサポートされているシリアル化モジュールを探しているなら、Googleの `Protobuf <https://developers.google.com/protocol-buffers>`_ ライブラリがオプションです。
