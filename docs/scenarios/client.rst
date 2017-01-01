.. Network Applications
.. ====================

ネットワークアプリケーション
============================



HTTP
::::

.. The Hypertext Transfer Protocol (HTTP) is an application protocol for
.. distributed, collaborative, hypermedia information systems. HTTP is the
.. foundation of data communication for the World Wide Web.

ハイパーテキスト転送プロトコル（HTTP）は、分散された共同のハイパーメディア情報システムのアプリケーションプロトコルです。 HTTPはWorld Wide Webのデータ通信の基盤です。

Requests
--------

.. Python’s standard urllib2 module provides most of the HTTP capabilities you
.. need, but the API is thoroughly broken. It was built for a different time —
.. and a different web. It requires an enormous amount of work (even method
.. overrides) to perform the simplest of tasks.

Pythonの標準urllib2モジュールは必要なHTTP機能のほとんどを提供しますが、APIは完全に壊れています。 それは別の時間と別のウェブのために建てられました。 最も単純なタスクを実行するには、膨大な作業（メソッドのオーバーライドさえ）が必要です。

.. Requests takes all of the work out of Python HTTP — making your integration
.. with web services seamless. There’s no need to manually add query strings to
.. your URLs, or to form-encode your POST data. Keep-alive and HTTP connection
.. pooling are 100% automatic, powered by urllib3, which is embedded within
.. Requests.

リクエストはPython HTTPからすべての作業を取り除き、Webサービスとの統合をシームレスにします。 クエリ文字列をURLに手動で追加したり、POSTデータをフォームエンコードする必要はありません。 キープアライブとHTTP接続プーリングは、リクエスト内に埋め込まれたurllib3によって100％自動化されます。

- `Documentation <http://docs.python-requests.org/en/latest/index.html>`_
- `PyPi <http://pypi.python.org/pypi/requests>`_
- `GitHub <https://github.com/kennethreitz/requests>`_


Distributed Systems
::::::::::::::::::::


ZeroMQ
------

.. ØMQ (also spelled ZeroMQ, 0MQ or ZMQ) is a high-performance asynchronous
.. messaging library aimed at use in scalable distributed or concurrent
.. applications. It provides a message queue, but unlike message-oriented
.. middleware, a ØMQ system can run without a dedicated message broker. The
.. library is designed to have a familiar socket-style API.

ØMQ（スペルのあるZeroMQ、0MQ、またはZMQ）は、スケーラブルな分散アプリケーションまたは並行アプリケーションでの使用を目的とした高性能非同期メッセージングライブラリです。 メッセージキューを提供しますが、メッセージ指向のミドルウェアとは異なり、専用メッセージブローカなしでØMQシステムを実行できます。 ライブラリは使い慣れたソケットスタイルのAPIを持つように設計されています。

RabbitMQ
--------

.. RabbitMQ is an open source message broker software that implements the Advanced
.. Message Queuing Protocol (AMQP).  The RabbitMQ server is written in the Erlang
.. programming language and is built on the Open Telecom Platform framework for
.. clustering and failover. Client libraries to interface with the broker are
.. available for all major programming languages.

RabbitMQは、AMQP（Advanced Message Queuing Protocol）を実装したオープンソースのメッセージブローカーソフトウェアです。 RabbitMQサーバーはErlangプログラミング言語で書かれており、クラスタリングとフェールオーバーのためにOpen Telecom Platformフレームワーク上に構築されています。 ブローカとのインターフェイスをとるクライアントライブラリは、すべての主要なプログラミング言語で使用できます。

- `Homepage <http://www.rabbitmq.com/>`_
- `GitHub Organization <https://github.com/rabbitmq?page=1>`_
