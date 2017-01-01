.. Logging
.. =======

ロギング
========

.. The :mod:`logging` module has been a part of Python's Standard Library since
.. version 2.3.  It is succinctly described in :pep:`282`.  The documentation
.. is notoriously hard to read, except for the `basic logging tutorial`_.

:mod:`logging` モジュールは、バージョン2.3以降のPythonの標準ライブラリの一部です。 :pep:`282` に簡潔に記述されています。 `基本的なロギングチュートリアル`_ を除いて、ドキュメントは読みにくいことはよく知られています。

.. Logging serves two purposes:

ロギングには2つの目的があります:

.. - **Diagnostic logging** records events related to the application's
..   operation. If a user calls in to report an error, for example, the logs
..   can be searched for context.
.. - **Audit logging** records events for business analysis. A user's
..   transactions can be extracted and combined with other user details for
..   reports or to optimize a business goal.

- **診断ログ** は、アプリケーションの操作に関連するイベントを記録します。たとえば、ユーザーがエラーを報告するためにコールすると、ログでコンテキストを検索できます。
- **監査ロギング** は、ビジネス分析のイベントを記録します。 ユーザーのトランザクションを抽出し、レポートの他のユーザーの詳細と組み合わせたり、ビジネス目標を最適化することができます。


.. ... or Print?
.. -------------

...またはプリント？
-------------------

.. The only time that ``print`` is a better option than logging is when
.. the goal is to display a help statement for a command line application.
.. Other reasons why logging is better than ``print``:

コマンドラインアプリケーションのヘルプ文を表示するのが目標であるときだけ、 ``print`` がロギングより良い選択肢です。 ロギングが ``print`` より優れている理由:

.. - The `log record`_, which is created with every logging event, contains
..   readily available diagnostic information such as the file name, full path,
..   function, and line number of the logging event.
.. - Events logged in included modules are automatically accessible via the root
..   logger to your application's logging stream, unless you filter them out.
.. - Logging can be selectively silenced by using the method
..   :meth:`logging.Logger.setLevel` or disabled by setting the attribute
..   :attr:`logging.Logger.disabled` to ``True``.

- ログ記録イベントごとに作成される `ログレコード`_ は、ファイル名、フルパス、関数、ロギングイベントの行番号など、すぐに利用できる診断情報を含んでいます。
- 含まれているモジュールにログインしたイベントは、フィルタリングしない限り、ルートロガーからアプリケーションのロギングストリームに自動的にアクセスできます。
- ロギングは、:meth:`logging.Logger.setLevel` メソッドを使用することによって選択的に消音することができます。または、属性 :attr:`logging.Logger.disabled` を ``True`` に設定することによって無効にすることができます。


.. Logging in a Library
.. --------------------

ライブラリのログイン
--------------------

.. Notes for `configuring logging for a library`_ are in the 
.. `logging tutorial`_.  Because the *user*, not the library, should
.. dictate what happens when a logging event occurs, one admonition bears
.. repeating:

`ライブラリのログを設定する`_ の注意は `ロギングチュートリアル`_ にあります。 ライブラリーではなく *user* がロギング・イベントが発生したときに何が起こるかを指示する必要があるため、1つの警告は繰り返されます。

.. .. note::
..     It is strongly advised that you do not add any handlers other than
..     NullHandler to your library’s loggers.  

.. note::
    NullHandler以外のハンドラをライブラリのロガーに追加しないことを強くお勧めします。


.. Best practice when instantiating loggers in a library is to only create them
.. using the ``__name__`` global variable: the :mod:`logging` module creates a
.. hierarchy of loggers using dot notation, so using ``__name__`` ensures
.. no name collisions.

ライブラリ内のロガーをインスタンス化する際のベストプラクティスは、グローバル変数 ``__name__`` を使用してロガーを作成することです。:mod:`logging` モジュールはドット表記を使用してロガーの階層を作成するので、``__name__`` を使用すると名前は保証されません 衝突。

.. Here is an example of best practice from the `requests source`_ -- place
.. this in your ``__init__.py``

ここでは、 `requests source`_ からのベストプラクティスの例を示します - これをあなたの ``__init __.py`` に置きます

.. code-block:: python

    # Set default logging handler to avoid "No handler found" warnings.
    import logging
    try:  # Python 2.7+
        from logging import NullHandler
    except ImportError:
        class NullHandler(logging.Handler):
            def emit(self, record):
                pass

    logging.getLogger(__name__).addHandler(NullHandler())



.. Logging in an Application
.. -------------------------

アプリケーションへのログイン
----------------------------

.. The `twelve factor app <http://12factor.net>`_, an authoritative reference
.. for good practice in application development, contains a section on
.. `logging best practice <http://12factor.net/logs>`_. It emphatically
.. advocates for treating log events as an event stream, and for
.. sending that event stream to standard output to be handled by the
.. application environment.

`twelve factor app <http://12factor.net>`_ は、アプリケーション開発における優れた実践の権威ある参考資料で、 `logging best practice <http://12factor.net/logs>`_ のセクションを含んでいます。ログイベントをイベントストリームとして扱い、イベントストリームを標準出力に送信してアプリケーション環境で処理することを強調しています。


.. There are at least three ways to configure a logger:

ロガーを設定するには、少なくとも3つの方法があります:

.. - Using an INI-formatted file:
..     - **Pro**: possible to update configuration while running using the
..       function :func:`logging.config.listen` to listen on a socket.
..     - **Con**: less control (*e.g.* custom subclassed filters or loggers)
..       than possible when configuring a logger in code.
.. - Using a dictionary or a JSON-formatted file:
..     - **Pro**: in addition to updating while running, it is possible to load
..       from a file using the :mod:`json` module, in the standard library since
..       Python 2.6.
..     - **Con**: less control than when configuring a logger in code.
.. - Using code:
..     - **Pro**: complete control over the configuration.
..     - **Con**: modifications require a change to source code.

- INI形式のファイルを使用する:
    - **Pro**: :func:`logging.config.listen` 関数を使って実行中に設定を更新することができます。
    - **Con**: ロガーをコードで構成するときは、できるだけコントロールしない（たとえば、カスタムサブクラスのフィルターやロガー）ことはできません。
- 辞書またはJSON形式のファイルを使用する:
    - **Pro**: 実行中に更新することに加えて、Python 2.6から標準ライブラリに :mod:`json` モジュールを使用してファイルからロードすることができます。
    - **Con**: コードでロガーを設定するよりも制御が少ない。
- コードを使う:
    - **Pro**: 設定を完全に制御します。
    - **Con**: 変更にはソースコードを変更する必要があります。


.. Example Configuration via an INI File
.. ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

INIファイルによる設定例
~~~~~~~~~~~~~~~~~~~~~~~

.. Let us say the file is named ``logging_config.ini``.
.. More details for the file format are in the `logging configuration`_
.. section of the `logging tutorial`_.

ファイルの名前が ``logging_config.ini`` であるとしましょう。 ファイル形式の詳細は、 `ロギングチュートリアル`_ の `logging configuration`_ セクションにあります。

.. code-block:: ini

    [loggers]
    keys=root
    
    [handlers]
    keys=stream_handler
    
    [formatters]
    keys=formatter
    
    [logger_root]
    level=DEBUG
    handlers=stream_handler
    
    [handler_stream_handler]
    class=StreamHandler
    level=DEBUG
    formatter=formatter
    args=(sys.stderr,)
    
    [formatter_formatter]
    format=%(asctime)s %(name)-12s %(levelname)-8s %(message)s


.. Then use :meth:`logging.config.fileConfig` in the code:

次に、コードに :meth:`logging.config.fileConfig` を使用します:

.. code-block:: python

    import logging
    from logging.config import fileConfig

    fileConfig('logging_config.ini')
    logger = logging.getLogger()
    logger.debug('often makes a very good meal of %s', 'visiting tourists')
    

.. Example Configuration via a Dictionary
.. ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

辞書による設定例
~~~~~~~~~~~~~~~~

.. As of Python 2.7, you can use a dictionary with configuration details.
.. :pep:`391` contains a list of the mandatory and optional elements in
.. the configuration dictionary.

Python 2.7では、設定の詳細を持つ辞書を使用できます。 :pep:`391` は、構成辞書の必須要素とオプション要素のリストを含んでいます。

.. code-block:: python

    import logging
    from logging.config import dictConfig

    logging_config = dict(
        version = 1,
        formatters = {
            'f': {'format':
                  '%(asctime)s %(name)-12s %(levelname)-8s %(message)s'}
            },
        handlers = {
            'h': {'class': 'logging.StreamHandler',
                  'formatter': 'f',
                  'level': logging.DEBUG}
            },
        root = {
            'handlers': ['h'],
            'level': logging.DEBUG,
            },
    )

    dictConfig(logging_config)

    logger = logging.getLogger()
    logger.debug('often makes a very good meal of %s', 'visiting tourists')


.. Example Configuration Directly in Code
.. ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

コードの直接の構成例
~~~~~~~~~~~~~~~~~~~~

.. code-block:: python

    import logging

    logger = logging.getLogger()
    handler = logging.StreamHandler()
    formatter = logging.Formatter(
            '%(asctime)s %(name)-12s %(levelname)-8s %(message)s')
    handler.setFormatter(formatter)
    logger.addHandler(handler)
    logger.setLevel(logging.DEBUG)

    logger.debug('often makes a very good meal of %s', 'visiting tourists')


.. _基本的なロギングチュートリアル: http://docs.python.org/howto/logging.html#logging-basic-tutorial
.. _logging configuration: https://docs.python.org/howto/logging.html#configuring-logging
.. _ロギングチュートリアル: http://docs.python.org/howto/logging.html
.. _ライブラリのログを設定する: https://docs.python.org/howto/logging.html#configuring-logging-for-a-library
.. _ログレコード: https://docs.python.org/library/logging.html#logrecord-attributes
.. _requests source: https://github.com/kennethreitz/requests
