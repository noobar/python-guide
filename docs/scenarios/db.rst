.. Databases
.. =========

データベース
============

DB-API
------

.. The Python Database API (DB-API) defines a standard interface for Python
.. database access modules. It's documented in :pep:`249`.
.. Nearly all Python database modules such as `sqlite3`, `psycopg` and
.. `mysql-python` conform to this interface.

Python Database API（DB-API）は、Pythonデータベースアクセスモジュール用の標準インタフェースを定義します。それは :pep:`249` に書かれています。 `sqlite3` 、`psycopg` 、 `mysql-python` のようなほぼすべてのPythonデータベースモジュールは、このインターフェースに準拠しています。

.. Tutorials that explain how to work with modules that conform to this interface can be found

このインタフェースに準拠したモジュールで作業する方法を説明するチュートリアルが見つかります
`here <http://halfcooked.com/presentations/osdc2006/python_databases.html>`__ and
`here <http://web.archive.org/web/20120815130844/http://www.amk.ca/python/writing/DB-API.html>`__.

SQLAlchemy
----------

.. `SQLAlchemy <http://www.sqlalchemy.org/>`_ is a commonly used database toolkit.
.. Unlike many database libraries it not only provides an ORM layer but also a
.. generalized API for writing database-agnostic code without SQL.

`SQLAlchemy <http://www.sqlalchemy.org/>`_ は、よく使われるデータベースツールキットです。 多くのデータベースライブラリとは異なり、ORMレイヤーを提供するだけでなく、SQLを使用せずにデータベースに依存しないコードを記述するための一般化されたAPIも提供します。

.. code-block:: console

    $ pip install sqlalchemy

Records
-------

.. `Records <https://github.com/kennethreitz/records>`_ is minimalist SQL library,
.. designed for sending raw SQL queries to various databases. Data can be used
.. programmatically, or exported to a number of useful data formats.

`Records <https://github.com/kennethreitz/records>`_ は、生のSQLクエリをさまざまなデータベースに送るために設計された、最小限のSQLライブラリです。 データはプログラムで使用することも、多数の有用なデータ形式にエクスポートすることもできます。

.. code-block:: console

    $ pip install records

.. Also included is a command-line tool for exporting SQL data.

SQLデータをエクスポートするためのコマンドラインツールも含まれています。

Django ORM
----------

.. The Django ORM is the interface used by `Django <http://www.djangoproject.com>`_
.. to provide database access.

Django ORMはデータベースアクセスを提供するために `Django <http://www.djangoproject.com>`_ によって使用されるインタフェースです。

.. It's based on the idea of
.. `models <https://docs.djangoproject.com/en/dev/#the-model-layer>`_,
.. an abstraction that makes it easier to manipulate data in Python.

これは `models <https://docs.djangoproject.com/en/dev/#the-model-layer>`_ の考え方に基づいています。これは、Pythonでデータを操作しやすくするための抽象です。

.. The basics:

基本:

.. - Each model is a Python class that subclasses django.db.models.Model.
.. - Each attribute of the model represents a database field.
.. - Django gives you an automatically-generated database-access API; see
..   `Making queries <https://docs.djangoproject.com/en/dev/topics/db/queries/>`__.

- 各モデルは、django.db.models.Modelをサブクラス化するPythonクラスです。
- モデルの各属性は、データベースフィールドを表します。
- Djangoは自動的に生成されたデータベースアクセスAPIを提供します。 `クエリーの作成 <https://docs.djangoproject.com/en/dev/topics/db/queries/>`__ を参照してください。

peewee
------

.. `peewee <http://docs.peewee-orm.com/en/latest/>`_ is another ORM with a focus
.. on being lightweight with support for Python 2.6+ and 3.2+ which supports
.. SQLite, MySQL and Postgres by default. The
.. `model layer <https://peewee.readthedocs.io/en/latest/peewee/quickstart.html#model-definition>`_
.. is similar to that of the Django ORM and it has
.. `SQL-like methods <https://peewee.readthedocs.io/en/latest/peewee/quickstart.html#retrieving-data>`_
.. to query data. While SQLite, MySQL and Postgres are supported out-of-the-box,
.. there is a `collection of add-ons <https://peewee.readthedocs.io/en/latest/peewee/playhouse.html#playhouse>`_
.. available.

`peewee <http://docs.peewee-orm.com/en/latest/>`_ は、デフォルトでSQLite、MySQL、PostgresをサポートするPython 2.6+と3.2+をサポートする軽量化に重点を置いた別のORMです。 `model layer <https://peewee.readthedocs.io/en/latest/peewee/quickstart.html#model-definition>`_ はDjango ORMと似ており、 `SQLのようなメソッド <https://peewee.readthedocs.io/en/latest/peewee/quickstart.html#retrieving-data>`_ を使用してデータを照会します。 SQLite、MySQL、Postgresはすぐにサポートされていますが、 `アドオンのコレクション <https://peewee.readthedocs.io/en/latest/peewee/playhouse.html#playhouse>`_ 利用可能です。

PonyORM
-------

.. `PonyORM <http://ponyorm.com/>`_ is an ORM that takes a different approach to
.. querying the database. Instead of writing an SQL-like language or boolean
.. expressions, Python's generator syntax is used. There's also an graphical
.. schema editor that can generate PonyORM entities for you. It supports Python
.. 2.6+ and Python 3.3+ and can connect to SQLite, MySQL, Postgres & Oracle

`PonyORM <http://ponyorm.com/>`_ は、データベースを照会するのに異なるアプローチをとるORMです。 SQLのような言語やブール式を書く代わりに、Pythonのジェネレータ構文が使われています。 PonyORMエンティティを生成できるグラフィカルなスキーマエディタもあります。 Python 2.6以降とPython 3.3以降をサポートし、SQLite、MySQL、Postgres、Oracleに接続できます



SQLObject
---------

.. `SQLObject <http://www.sqlobject.org/>`_ is yet another ORM. It supports a wide
.. variety of databases: Common database systems MySQL, Postgres and SQLite and
.. more exotic systems like SAP DB, SyBase and MSSQL. It only supports Python 2
.. from Python 2.6 upwards.

`SQLObject <http://www.sqlobject.org/>`_ はもう一つのORMです。 共通データベースシステムMySQL、Postgres、SQLite、SAP DB、SyBase、MSSQLなどのよりエキゾチックなシステムをサポートしています。 Python 2.6以降のPython 2しかサポートしていません。

.. .. There's no official information on this on their page, this information was gathered by looking at their source code
.. このページには正式な情報はありません。この情報はソースコードを見ることで集められました
