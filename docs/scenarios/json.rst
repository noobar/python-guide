JSON
====

.. The `json <https://docs.python.org/2/library/json.html>`_ library can parse
.. JSON from strings or files. The library parses JSON into a Python dictionary
.. or list. It can also convert Python dictionaries or lists into JSON strings.

`json <https://docs.python.org/2/library/json.html>`_ ライブラリは文字列やファイルからJSONを解析できます。 ライブラリは、JSONをPythonの辞書またはリストに解析します。 また、Pythonの辞書やリストをJSON文字列に変換することもできます。

.. Parsing JSON
.. ------------

JSONの解析
----------

.. Take the following string containing JSON data:

JSONデータを含む次の文字列を取得します。

.. code-block:: python

    json_string = '{"first_name": "Guido", "last_name":"Rossum"}'

.. It can be parsed like this:

これは次のように解析できます:

.. code-block:: python

    import json
    parsed_json = json.loads(json_string)

.. and can now be used as a normal dictionary:

今すぐ通常の辞書として使用することができます:

.. code-block:: python

    print(parsed_json['first_name'])
    "Guido"

.. You can also convert the following to JSON:

次のものをJSONに変換することもできます:

.. code-block:: python

    d = {
        'first_name': 'Guido',
        'second_name': 'Rossum',
        'titles': ['BDFL', 'Developer'],
    }

    print(json.dumps(d))
    '{"first_name": "Guido", "last_name": "Rossum", "titles": ["BDFL", "Developer"]}'


simplejson
----------

.. The JSON library was added to Python in version 2.6.
.. If you're using an earlier version of Python, the
.. `simplejson <https://simplejson.readthedocs.io/en/latest/>`_ library is
.. available via PyPI.

JSONライブラリはPython 2.6に追加されました。 以前のバージョンのPythonを使用している場合、 `simplejson <https://simplejson.readthedocs.io/en/latest/>`_ ライブラリはPyPI経由で利用できます。

.. simplejson mimics the json standard library. It is available so that developers
.. that use older versions of Python can use the latest features available in the
.. json lib.

simplejsonはjson標準ライブラリを模倣しています。 古いバージョンのPythonを使用する開発者がjsonのlibで利用可能な最新の機能を使用できるように、これを利用できます。

.. You can start using simplejson when the json library is not available by
.. importing simplejson under a different name:

simplejsonを別の名前でインポートして、jsonライブラリが利用できないときにsimplejsonを使用することができます:

.. code-block:: python
    
    import simplejson as json

.. After importing simplejson as json, the above examples will all work as if you
.. were using the standard json library.

simplejsonをjsonとしてインポートした後、上記の例はすべて、標準のjsonライブラリを使用しているかのように動作します。
