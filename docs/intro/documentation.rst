.. Documentation
.. =============

ドキュメンテーション
====================

.. Official Documentation
.. ----------------------

公式文書
--------

.. The official Python Language and Library documentation can be found here:

公式のPython言語とライブラリのドキュメントは、次の場所にあります。

    - `Python 2.x <https://docs.python.org/2/>`_
    - `Python 3.x <https://docs.python.org/3/>`_


Read the Docs
-------------

.. Read the Docs is a popular community project that hosts documentation
.. for open source software. It holds documentation for many Python modules,
.. both popular and exotic.

Read the Docsは、オープンソースソフトウェアのドキュメントをホストする一般的なコミュニティプロジェクトです。 一般的なものとエキゾチックなものの両方のPythonモジュールのドキュメントがあります。

    `Read the Docs <https://readthedocs.org/>`_


pydoc
-----

.. :program:`pydoc` is a utility that is installed when you install Python.
.. It allows you to quickly retrieve and search for documentation from your
.. shell. For example, if you needed a quick refresher on the
.. :mod:`time` module, pulling up documentation would be as simple as

:program:`pydoc` は、Pythonをインストールするときにインストールされるユーティリティです。 シェルからドキュメントをすばやく検索して検索することができます。 たとえば、:mod:`time` モジュールを素早くリフレッシュする必要がある場合、ドキュメントを引き上げるのは次のように簡単です

    .. code-block:: console

       $ pydoc time

.. The above command is essentially equivalent to opening the Python REPL
.. and running

上記のコマンドは、基本的にはPython REPLを開いて実行することと同じです

    .. code-block:: pycon

       >>> help(time)
