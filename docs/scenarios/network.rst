.. Networking
.. ==========

ネットワーキング
================

Twisted
-------

.. `Twisted <http://twistedmatrix.com/trac/>`_ is an event-driven networking
.. engine. It can be used to build applications around many different networking
.. protocols, including http servers and clients, applications using SMTP, POP3,
.. IMAP or SSH protocols, instant messaging
.. and `much more <http://twistedmatrix.com/trac/wiki/Documentation>`_.

`Twisted <http://twistedmatrix.com/trac/>`_ は、イベント駆動型のネットワーキングエンジンです。 httpサーバやクライアント、SMTP、POP3、IMAP、SSHプロトコルを使用するアプリケーション、インスタントメッセージング、 `はるかに多くの <http://twistedmatrix.com/trac/wiki/Documentation>`_ 。

PyZMQ
-----

.. `PyZMQ <http://zeromq.github.com/pyzmq/>`_ is the Python binding for
.. `ZeroMQ <http://www.zeromq.org/>`_, which is a high-performance asynchronous
.. messaging library. One great advantage of ZeroMQ is that it can be used for
.. message queuing without a message broker. The basic patterns for this are:

`PyZMQ <http://zeromq.github.com/pyzmq/>`_ は、高性能非同期メッセージングライブラリである `ZeroMQ <http://www.zeromq.org/>`_ のPythonバインディングです。 ZeroMQの大きな利点の1つは、メッセージブローカなしでメッセージキューに使用できることです。 これの基本的なパターンは次のとおりです。

.. - request-reply: connects a set of clients to a set of services. This is a
..   remote procedure call and task distribution pattern.
.. - publish-subscribe: connects a set of publishers to a set of subscribers.
..   This is a data distribution pattern.
.. - push-pull (or pipeline): connects nodes in a fan-out / fan-in pattern that
..   can have multiple steps, and loops. This is a parallel task distribution
..   and collection pattern.

- 要求-応答: 一連のクライアントを一連のサービスに接続します。 これは、リモートプロシージャコールおよびタスク配布パターンです。
- publish-subscribe: 一連のパブリッシャを一連のサブスクライバに接続します。 これはデータ配布パターンです。
- プッシュプル（またはパイプライン）: ファンアウト/ファンインパターンで複数のステップとループを持つことができるノードを接続します。 これは、並行タスク配布および収集パターンです。

.. For a quick start, read the `ZeroMQ guide <http://zguide.zeromq.org/page:all>`_.

クイックスタートについては、 `ZeroMQ guide <http://zguide.zeromq.org/page:all>`_ を読んでください。

gevent
------

.. `gevent <http://www.gevent.org/>`_ is a coroutine-based Python networking
.. library that uses greenlets to provide a high-level synchronous API on top of
.. the libev event loop. 

`gevent <http://www.gevent.org/>`_ はコルーチンベースのPythonネットワーキングライブラリで、greenletを使ってlibevイベントループの上に高レベルの同期APIを提供します。
