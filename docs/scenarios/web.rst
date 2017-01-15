.. ================
.. Web Applications
.. ================

===================
Webアプリケーション
===================

.. As a powerful scripting language adapted to both fast prototyping
.. and bigger projects, Python is widely used in web application
.. development.

高速プロトタイプと大きなプロジェクトの両方に対応した強力なスクリプト言語として、PythonはWebアプリケーション開発に広く使用されています。

.. Context
.. :::::::

コンテキスト
::::::::::::


WSGI
----

.. The Web Server Gateway Interface (or "WSGI" for short) is a standard
.. interface between web servers and Python web application frameworks. By
.. standardizing behavior and communication between web servers and Python web
.. frameworks, WSGI makes it possible to write portable Python web code that
.. can be deployed in any :ref:`WSGI-compliant web server <wsgi-servers-ref>`.
.. WSGI is documented in :pep:`3333`.

Webサーバーゲートウェイインターフェイス（略して "WSGI" ）は、WebサーバーとPython Webアプリケーションフレームワークの間の標準インターフェイスです。 :ref:`WSGI準拠のWebサーバ<wsgi-servers-ref>` をWebサーバやPythonのWebフレームワークとの間に動作し、通信を標準化することで、WSGIはいずれにも展開することができる携帯用のPythonのWebコードを記述することが可能となります。 WSGIは、pep:`3333` に記載されています。


.. Frameworks
.. ::::::::::

フレームワーク
::::::::::::::

.. Broadly speaking, a web framework consists of a set of libraries and a main
.. handler within which you can build custom code to implement a web application
.. (i.e. an interactive web site). Most web frameworks include patterns and
.. utilities to accomplish at least the following:

大まかに言えば、Webフレームワークは、一連のライブラリとメインハンドラで構成され、その中にWebアプリケーション（つまり、インタラクティブなWebサイト）を実装するためのカスタムコードを作成できます。 ほとんどのWebフレームワークには、少なくとも以下を達成するためのパターンとユーティリティが含まれています。

.. URL Routing
..   Matches an incoming HTTP request to a particular piece of Python code to
..   be invoked

URLルーティング
  着信するHTTP要求を特定のPythonコードに一致させて呼び出します

.. Request and Response Objects
..   Encapsulate the information received from or sent to a user's browser

要求オブジェクトと応答オブジェクト
  ユーザーのブラウザから受信した情報またはユーザーのブラウザに送信した情報をカプセル化する

.. Template Engine
..   Allows for separating Python code implementing an application's logic from
..   the HTML (or other) output that it produces

テンプレートエンジン
  アプリケーションのロジックを実装するPythonコードを、それが生成するHTML（またはその他の）出力から分離することを可能にする

.. Development Web Server
..   Runs an HTTP server on development machines to enable rapid development;
..   often automatically reloads server-side code when files are updated

開発用Webサーバ
  迅速な開発を可能にするために開発マシン上でHTTPサーバーを実行します。 ファイルが更新されると自動的にサーバー側のコードがリロードされる


Django
------

.. `Django <http://www.djangoproject.com>`_ is a "batteries included" web
.. application framework, and is an excellent choice for creating content-oriented
.. websites. By providing many utilities and patterns out of the box, Django aims
.. to make it possible to build complex, database-backed web applications quickly,
.. while encouraging best practices in code written using it.

`Django <http://www.djangoproject.com>`_ は、 "バッテリー同梱" Webアプリケーションフレームワークであり、コンテンツ指向のウェブサイトを作成するための優れた選択肢です。 Djangoは、多くのユーティリティとパターンを提供することにより、複雑なデータベースベースのWebアプリケーションを迅速に構築し、それを使用して作成されたコードのベストプラクティスを奨励することを目指しています。

.. Django has a large and active community, and many pre-built `re-usable
.. modules <http://djangopackages.com/>`_ that can be incorporated into a new
.. project as-is, or customized to fit your needs.

Djangoには大きくて活動的なコミュニティがあり、あなたのニーズに合わせてカスタマイズされた新しいプロジェクトに組み込むことができる、多くのあらかじめ構築された `再利用可能なモジュール <http://djangopackages.com/>`_ があります。

.. There are annual Django conferences `in the United States
.. <http://djangocon.us>`_ and `in Europe <http://djangocon.eu>`_.

毎年Djangoカンファレンスが `米国 <http://djangocon.us>`_ と `欧州 <http://djangocon.eu>`_ で開催されています。

.. The majority of new Python web applications today are built with Django.

今日の新しいPython Webアプリケーションの大部分は、Djangoで構築されています。

Flask
-----

.. `Flask <http://flask.pocoo.org/>`_ is a "microframework" for Python, and is
.. an excellent choice for building smaller applications, APIs, and web services.

`Flask <http://flask.pocoo.org/>`_ はPythonの "マイクロフレームワーク" であり、小さなアプリケーション、API、およびWebサービスの構築に最適です。

.. Building an app with Flask is a lot like writing standard Python modules,
.. except some functions have routes attached to them. It's really beautiful.

Flaskを使ってアプリケーションをビルドするのは、標準のPythonモジュールを書くのと似ていますが、いくつかの関数にはルートが付けられています。 それは本当に美しいです。

.. Rather than aiming to provide everything you could possibly need, Flask
.. implements the most commonly-used core components of a web application
.. framework, like URL routing, request and response objects, and templates.

おそらく必要なものをすべて提供することを目指すのではなく、URLルーティング、リクエストとレスポンスオブジェクト、テンプレートなど、Webアプリケーションフレームワークの中で最も一般的に使用されるコアコンポーネントを実装します。

.. If you use Flask, it is up to you to choose other components for your
.. application, if any. For example, database access or form generation and
.. validation are not built-in functions of Flask.

Flaskを使用している場合は、アプリケーションの他のコンポーネントがあればそれを選択する必要があります。 たとえば、データベースへのアクセスやフォームの生成と検証は、Flaskの組み込み関数ではありません。

.. This is great, because many web applications don't need those features.
.. For those that do, there are many
.. `Extensions <http://flask.pocoo.org/extensions/>`_ available that may
.. suit your needs. Or, you can easily use any library you want yourself!

多くのWebアプリケーションにはこれらの機能が必要ないので、これは素晴らしいことです。 そういう人には、あなたのニーズに合った `Extensions <http://flask.pocoo.org/extensions/>`_ がたくさんあります。 または、あなたが望む任意のライブラリを簡単に使用できます。

.. Flask is default choice for any Python web application that isn't a good
.. fit for Django.

Flaskは、Djangoには適していないPython Webアプリケーションのデフォルトの選択です。


Tornado
--------

.. `Tornado <http://www.tornadoweb.org/>`_ is an asyncronous web framework
.. for Python that has its own event loop. This allows it to natively support
.. WebSockets, for example. Well-written Tornado applications are known to
.. have excellent performance characteristics.

`Tornado <http://www.tornadoweb.org/>`_ は独自のイベントループを持つPython用の非同期Webフレームワークです。これにより、例えばWebSocketをネイティブにサポートすることができます。よく書かれたTornadoのアプリケーションは、優れた性能特性を持つことが知られています。

.. I do not recommend using Tornado unless you think you need it.

必要があると思わない限り、Tornadoの使用をお勧めしません。

Pyramid
--------

.. `Pyramid <https://trypyramid.com/>`_ is a very flexible framework with a heavy
.. focus on modularity. It comes with a small number of libraries ("batteries")
.. built-in, and encourages users to extend its base functionality.

`Pyramid <https://trypyramid.com/>`_ は、モジュール性に重点を置いた非常に柔軟なフレームワークです。 少数のライブラリ ("電池") が内蔵されており、ユーザが基本機能を拡張するように促します。

.. Pyramid does not have a large user base, unlike Django and Flask. It's a
.. capable framework, but not a very popular choice for new Python web
.. applications today.

DjangoやFlaskとは異なり、Pyramidには大きなユーザーベースはありません。 これは有能なフレームワークですが、今日の新しいPython Webアプリケーションにとってはあまり一般的ではありません。

Web Servers
:::::::::::

.. _nginx-ref:

Nginx
-----

.. `Nginx <http://nginx.org/>`_ (pronounced "engine-x") is a web server and
.. reverse-proxy for HTTP, SMTP and other protocols. It is known for its
.. high performance, relative simplicity, and compatibility with many
.. application servers (like WSGI servers). It also includes handy features
.. like load-balancing, basic authentication, streaming, and others. Designed
.. to serve high-load websites, Nginx is gradually becoming quite popular.

`Nginx <http://nginx.org/>`_ ("engine-x"と発音) は、HTTP、SMTPなどのプロトコル用のWebサーバーとリバースプロキシです。 高性能で、比較的シンプルで、多くのアプリケーションサーバー（WSGIサーバーなど）との互換性があることが知られています。 また、ロードバランシング、基本認証、ストリーミングなどの便利な機能も含まれています。 高負荷のウェブサイトに対応するように設計されたNginxは、徐々に普及しています。


.. _wsgi-servers-ref:

WSGI Servers
::::::::::::

.. Stand-alone WSGI servers typically use less resources than traditional web
.. servers and provide top performance [3]_.

スタンドアロンのWSGIサーバーは、通常、従来のWebサーバーよりも少ないリソースを使用し、最高のパフォーマンス [3]_ を提供します。

.. _gunicorn-ref:

Gunicorn
--------

.. `Gunicorn <http://gunicorn.org/>`_ (Green Unicorn) is a pure-python WSGI
.. server used to serve Python applications. Unlike other Python web servers,
.. it has a thoughtful user-interface, and is extremely easy to use and
.. configure.

`Gunicorn <http://gunicorn.org/>`_ (Green Unicorn) はPythonアプリケーションを提供するために使われる純粋なPythonのWSGIサーバーです。 他のPython Webサーバーとは異なり、思慮深いユーザーインターフェイスがあり、使いやすく構成が簡単です。

.. Gunicorn has sane and reasonable defaults for configurations. However, some
.. other servers, like uWSGI, are tremendously more customizable, and therefore,
.. are much more difficult to effectively use.

Gunicornは、構成に対して正気で合理的なデフォルトを持っています。 しかし、uWSGIのような他のサーバーは、大幅にカスタマイズ可能であるため、効果的に使用するのがはるかに困難です。

.. Gunicorn is the recommended choice for new Python web applications today.

Gunicornは今日の新しいPython Webアプリケーションの推奨選択肢です。


Waitress
--------

.. `Waitress <https://waitress.readthedocs.io>`_ is a pure-python WSGI server
.. that claims "very acceptable performance". Its documentation is not very
.. detailed, but it does offer some nice functionality that Gunicorn doesn't have
.. (e.g. HTTP request buffering).

`Waitress <https://waitress.readthedocs.io>`_ は、"非常に許容可能なパフォーマンス" を主張する純粋なpython WSGIサーバーです。 そのドキュメントはあまり詳細ではありませんが、Gunicornにはない優れた機能（HTTPリクエストバッファリングなど）があります。

.. Waitress is gaining popularity within the Python web development community.

WaitressはPython Web開発コミュニティで人気を博しています。

.. _uwsgi-ref:

uWSGI
-----

.. `uWSGI <https://uwsgi-docs.readthedocs.io>`_ is a full stack for building
.. hosting services.  In addition to process management, process monitoring,
.. and other functionality, uWSGI acts as an application server for various
.. programming languages and protocols - including Python and WSGI. uWSGI can
.. either be run as a stand-alone web router, or be run behind a full web
.. server (such as Nginx or Apache).  In the latter case, a web server can
.. configure uWSGI and an application's operation over the
.. `uwsgi protocol <https://uwsgi-docs.readthedocs.io/en/latest/Protocol.html>`_.
.. uWSGI's web server support allows for dynamically configuring
.. Python, passing environment variables and further tuning.  For full details,
.. see `uWSGI magic
.. variables <https://uwsgi-docs.readthedocs.io/en/latest/Vars.html>`_.

`uWSGI <https://uwsgi-docs.readthedocs.io>`_ は、ホスティングサービスを構築するための完全なスタックです。 プロセス管理、プロセス監視、およびその他の機能に加えて、uWSGIは、PythonやWSGIなど、さまざまなプログラミング言語とプロトコルのアプリケーションサーバーとして機能します。 uWSGIは、スタンドアロンのWebルーターとして実行することも、完全なWebサーバー（NginxやApacheなど）の背後で実行することもできます。 後者の場合、WebサーバーはuWSGIとアプリケーションの操作を `uwsgi protocol <https://uwsgi-docs.readthedocs.io/en/latest/Protocol.html>`_ で設定できます。 uWSGIのWebサーバーサポートにより、Pythonを動的に構成し、環境変数を渡し、さらにチューニングすることができます。 詳細については、 `uWSGIマジック変数 <https://uwsgi-docs.readthedocs.io/en/latest/Vars.html>`_ を参照してください。

.. I do not recommend using uWSGI unless you know why you need it.

なぜ必要なのか分からない限り、私はuWSGIの使用をお勧めしません。

.. _server-best-practices-ref:


.. Server Best Practices
.. :::::::::::::::::::::

サーバーのベストプラクティス
::::::::::::::::::::::::::::

.. The majority of self-hosted Python applications today are hosted with a WSGI
.. server such as :ref:`Gunicorn <gunicorn-ref>`, either directly or behind a
.. lightweight web server such as :ref:`nginx <nginx-ref>`.

現在ホストされているPythonアプリケーションの大部分は、 :ref:`nginx <nginx-ref>` のような軽量のWebサーバーの後ろにある :ref:`Gunicorn <gunicorn-ref>` のようなWSGIサーバーでホストされています。

.. The WSGI servers serve the Python applications while the web server handles
.. tasks better suited for it such as static file serving, request routing, DDoS
.. protection, and basic authentication.

WSGIサーバーはPythonアプリケーションを処理しますが、Webサーバーは静的ファイルサービス、要求ルーティング、DDoS保護、基本認証など、より適切なタスクを処理します。

.. Hosting
.. :::::::

ホスティング
::::::::::::

.. Platform-as-a-Service (PaaS) is a type of cloud computing infrastructure
.. which abstracts and manages infrastructure, routing, and scaling of web
.. applications. When using a PaaS, application developers can focus on writing
.. application code rather than needing to be concerned with deployment
.. details.

PaaS（Platform-as-a-Service）は、Webアプリケーションのインフラストラクチャ、ルーティング、およびスケーリングを抽象化して管理するクラウドコンピューティングインフラストラクチャの一種です。 PaaSを使用する場合、アプリケーション開発者はデプロイの詳細を意識する必要はなく、アプリケーションコードの作成に専念することができます。

Heroku
------

.. `Heroku <http://www.heroku.com/python>`_ offers first-class support for
.. Python 2.7–3.5 applications.

`Heroku <http://www.heroku.com/python>`_ はPython 2.7-3.5アプリケーションのための一流のサポートを提供します。

.. Heroku supports all types of Python web applications, servers, and frameworks.
.. Applications can be developed on Heroku for free. Once your application is
.. ready for production, you can upgrade to a Hobby or Professional application.

Herokuは、あらゆる種類のPython Webアプリケーション、サーバー、およびフレームワークをサポートしています。 アプリケーションは無料でHerokuで開発することができます。 アプリケーションの本稼働準備が整ったら、趣味やプロフェッショナルアプリケーションにアップグレードできます。

.. Heroku maintains `detailed articles <https://devcenter.heroku.com/categories/python>`_
.. on using Python with Heroku, as well as `step-by-step instructions
.. <https://devcenter.heroku.com/articles/getting-started-with-python>`_ on
.. how to set up your first application.

Herokuは、PythonとHerokuを使用した `詳細な記事 <https://devcenter.heroku.com/categories/python>`_ と、 `ステップバイステップの手順 <https://devcenter.heroku.com/articles/getting-started-with-python>`_ 最初のアプリケーションの設定方法について説明します。

.. Heroku is the recommended PaaS for deploying Python web applications today.

Herokuは、今日のPython Webアプリケーションの展開に推奨されるPaaSです。

Eldarion
--------

.. `Eldarion <http://eldarion.cloud/>`_ (formely known as Gondor) is a PaaS powered
.. by Kubernetes, CoreOS, and Docker. They support any WSGI application and have a
.. guide on deploying `Django projects <https://eldarion-gondor.github.io/docs/how-to/setup-deploy-first-django-project/>`_.

`Eldarion <http://eldarion.cloud/>`_ (正式にGondorとして知られています) は、Kubernetes、CoreOS、およびDockerによるPaaSです。彼らはどんなWSGIアプリケーションもサポートしており、 `Django projects <https://eldarion-gondor.github.io/docs/how-to/setup-deploy-first-django-project/>`_ の導入に関するガイドを持っています。

.. Templating
.. ::::::::::

テンプレート
::::::::::::

.. Most WSGI applications are responding to HTTP requests to serve content in HTML
.. or other markup languages. Instead of generating directly textual content from
.. Python, the concept of separation of concerns advises us to use templates. A
.. template engine manages a suite of template files, with a system of hierarchy
.. and inclusion to avoid unnecessary repetition, and is in charge of rendering
.. (generating) the actual content, filling the static content of the templates
.. with the dynamic content generated by the application.

ほとんどのWSGIアプリケーションは、HTMLや他のマークアップ言語でコンテンツを提供するためにHTTP要求に応答しています。 Pythonから直接テキストコンテンツを生成するのではなく、懸念を分離するという概念は、テンプレートを使用するように私たちに助言します。テンプレートエンジンは、不必要な繰り返しを避けるための階層と包含のシステムを備えたテンプレートファイル群を管理し、実際のコンテンツのレンダリング（生成）を担当し、テンプレートの静的コンテンツをアプリケーションによって生成された動的コンテンツです。

.. As template files are
.. sometimes written by designers or front-end developers, it can be difficult to
.. handle increasing complexity.

テンプレートファイルはデザイナーやフロントエンドの開発者によって書き込まれることがあるため、増えていく複雑さに対応することは困難です。

.. Some general good practices apply to the part of the application passing
.. dynamic content to the template engine, and to the templates themselves.

一般的な良い方法は、動的コンテンツをテンプレートエンジンやテンプレート自体に渡すアプリケーションの部分に適用されます。

.. - Template files should be passed only the dynamic
..   content that is needed for rendering the template. Avoid
..   the temptation to pass additional content "just in case":
..   it is easier to add some missing variable when needed than to remove
..   a likely unused variable later.

- テンプレートファイルには、テンプレートのレンダリングに必要な動的コンテンツのみが渡されます。 「念のため」に追加のコンテンツを渡すような誘惑を避けてください。未使用の変数を後で削除するよりも必要なときに不足している変数を追加する方が簡単です。

.. - Many template engines allow for complex statements
..   or assignments in the template itself, and many
..   allow some Python code to be evaluated in the
..   templates. This convenience can lead to uncontrolled
..   increase in complexity, and often make it harder to find bugs.

- 多くのテンプレートエンジンでは、テンプレート自体に複雑なステートメントや割り当てが可能であり、多くの場合、テンプレートでPythonコードを評価できるものが多数あります。 この利便性は、制御されていない複雑さの増加につながり、しばしばバグを見つけにくくします。

.. - It is often necessary to mix JavaScript templates with
..   HTML templates. A sane approach to this design is to isolate
..   the parts where the HTML template passes some variable content
..   to the JavaScript code.

- JavaScriptテンプレートとHTMLテンプレートを混在させる必要があることがよくあります。 この設計に対する単純なアプローチは、HTMLテンプレートがいくつかの可変コンテンツをJavaScriptコードに渡す部分を分離することです。



Jinja2
------
.. `Jinja2 <http://jinja.pocoo.org/>`_ is a very well-regarded template engine.

`Jinja2 <http://jinja.pocoo.org/>`_ は非常によく評価されているテンプレートエンジンです。

.. It uses a text-based template language and can thus be used to generate any
.. type markup, not just HTML. It allows customization of filters, tags, tests
.. and globals. It features many improvements over Django's templating system.

これは、テキストベースのテンプレート言語を使用するので、HTMLだけでなく、あらゆるタイプのマークアップを生成するために使用できます。 これは、フィルタ、タグ、テスト、およびグローバルのカスタマイズを可能にします。 これは、Djangoのテンプレートシステムよりも多くの改善点があります。

.. Here some important html tags in Jinja2:

ここでJinja2の重要なHTMLタグ:

.. code-block:: html

    {# This is a comment #}

    {# The next tag is a variable output: #}
    {{title}}

    {# Tag for a block, can be replaced through inheritance with other html code #}
    {% block head %}
    <h1>This is the head!</h1>
    {% endblock %}

    {# Output of an array as an iteration #}
    {% for item in list %}
    <li>{{ item }}</li>
    {% endfor %}


.. The next listings is an example of a web site in combination with the Tornado
.. web server. Tornado is not very complicated to use.

次の一覧は、Tornado Webサーバーと組み合わせたWebサイトの例です。 Tornadoはそれほど複雑ではありません。

.. code-block:: python

    # import Jinja2
    from jinja2 import Environment, FileSystemLoader

    # import Tornado
    import tornado.ioloop
    import tornado.web

    # Load template file templates/site.html
    TEMPLATE_FILE = "site.html"
    templateLoader = FileSystemLoader( searchpath="templates/" )
    templateEnv = Environment( loader=templateLoader )
    template = templateEnv.get_template(TEMPLATE_FILE)

    # List for famous movie rendering
    movie_list = [[1,"The Hitchhiker's Guide to the Galaxy"],[2,"Back to future"],[3,"Matrix"]]

    # template.render() returns a string which contains the rendered html
    html_output = template.render(list=movie_list,
                            title="Here is my favorite movie list")

    # Handler for main page
    class MainHandler(tornado.web.RequestHandler):
        def get(self):
            # Returns rendered template string to the browser request
            self.write(html_output)

    # Assign handler to the server root  (127.0.0.1:PORT/)
    application = tornado.web.Application([
        (r"/", MainHandler),
    ])
    PORT=8884
    if __name__ == "__main__":
        # Setup the server
        application.listen(PORT)
        tornado.ioloop.IOLoop.instance().start()

.. The :file:`base.html` file can be used as base for all site pages which are
.. for example implemented in the content block.

:file:`base.html` ファイルは、例えばコンテンツブロックに実装されているすべてのサイトページのベースとして使用できます。

.. code-block:: html

    <!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN">
    <html lang="en">
    <html xmlns="http://www.w3.org/1999/xhtml">
    <head>
        <link rel="stylesheet" href="style.css" />
        <title>{{title}} - My Webpage</title>
    </head>
    <body>
    <div id="content">
        {# In the next line the content from the site.html template will be added #}
        {% block content %}{% endblock %}
    </div>
    <div id="footer">
        {% block footer %}
        &copy; Copyright 2013 by <a href="http://domain.invalid/">you</a>.
        {% endblock %}
    </div>
    </body>


.. The next listing is our site page (:file:`site.html`) loaded in the Python
.. app which extends :file:`base.html`. The content block is automatically set
.. into the corresponding block in the :file:`base.html` page.

次のリストは、 :file:`base.html` を拡張したPythonアプリケーションにロードされたサイトページ (:file:`site.html`) です。 コンテンツブロックは :file:`base.html` ページの対応するブロックに自動的に設定されます。

.. code-block:: html

    <!{% extends "base.html" %}
    {% block content %}
        <p class="important">
        <div id="content">
            <h2>{{title}}</h2>
            <p>{{ list_title }}</p>
            <ul>
                 {% for item in list %}
                 <li>{{ item[0]}} :  {{ item[1]}}</li>
                 {% endfor %}
            </ul>
        </div>
        </p>
    {% endblock %}


.. Jinja2 is the recommended templating library for new Python web applications.

Jinja2は、新しいPython Webアプリケーション用に推奨されるテンプレートライブラリです。

Chameleon
---------

.. `Chameleon <https://chameleon.readthedocs.io/>`_ Page Templates are an HTML/XML template
.. engine implementation of the `Template Attribute Language (TAL) <http://en.wikipedia.org/wiki/Template_Attribute_Language>`_,
.. `TAL Expression Syntax (TALES) <https://chameleon.readthedocs.io/en/latest/reference.html#expressions-tales>`_,
.. and `Macro Expansion TAL (Metal) <https://chameleon.readthedocs.io/en/latest/reference.html#macros-metal>`_ syntaxes.

`Chameleon <https://chameleon.readthedocs.io/>`_ ページテンプレートは、HTML/XMLテンプレートエンジンの `Template Attribute Language (TAL) <http://en.wikipedia.org/wiki/Template_Attribute_Language>`_ の実装です。 `TAL式構文 (TALES) <https://chameleon.readthedocs.io/en/latest/reference.html#expressions-tales>`_ 、 `マクロ展開TAL (Metal) <https://chameleon.readthedocs.io/en/latest/reference.html#macros-metal>`_ シンタックス。

.. Chameleon is available for Python 2.5 and up (including 3.x and pypy), and
.. is commonly used by the `Pyramid Framework <http://trypyramid.com>`_.

ChameleonはPython 2.5以降（3.xやpypyを含む）で利用可能で、 `Pyramid Framework <http://trypyramid.com>`_ で一般的に使用されています。

.. Page Templates add within your document structure special element attributes
.. and text markup. Using a set of simple language constructs, you control the
.. document flow, element repetition, text replacement and translation. Because
.. of the attribute-based syntax, unrendered page templates are valid HTML and can
.. be viewed in a browser and even edited in WYSIWYG editors. This can make
.. round-trip collaboration with designers and prototyping with static files in a
.. browser easier.

ページテンプレートは、ドキュメント構造内に特別な要素属性とテキストマークアップを追加します。 単純な言語構造のセットを使用して、文書の流れ、要素の繰り返し、テキストの置換と翻訳を制御します。 属性ベースの構文のため、未レンダリングページテンプレートは有効なHTMLであり、ブラウザで表示したり、WYSIWYGエディタで編集することもできます。 これにより、デザイナーとの往復のコラボレーションや、ブラウザ内の静的ファイルによるプロトタイプ作成が容易になります。

.. The basic TAL language is simple enough to grasp from an example:

基本的なTAL言語は、例を理解するのに十分シンプルです:

.. code-block:: html

  <html>
    <body>
    <h1>Hello, <span tal:replace="context.name">World</span>!</h1>
      <table>
        <tr tal:repeat="row 'apple', 'banana', 'pineapple'">
          <td tal:repeat="col 'juice', 'muffin', 'pie'">
             <span tal:replace="row.capitalize()" /> <span tal:replace="col" />
          </td>
        </tr>
      </table>
    </body>
  </html>


.. The `<span tal:replace="expression" />` pattern for text insertion is common
.. enough that if you do not require strict validity in your unrendered templates,
.. you can replace it with a more terse and readable syntax that uses the pattern
.. `${expression}`, as follows:

テキストを挿入するための `<span tal:replace="expression" />` パターンは、未翻訳のテンプレートで厳密な妥当性を必要としない場合は、パターンを使用するより簡潔で読みやすい構文で置き換えることができます。 `${expression}` を以下のように定義します。

.. code-block:: html

  <html>
    <body>
      <h1>Hello, ${world}!</h1>
      <table>
        <tr tal:repeat="row 'apple', 'banana', 'pineapple'">
          <td tal:repeat="col 'juice', 'muffin', 'pie'">
             ${row.capitalize()} ${col}
          </td>
        </tr>
      </table>
    </body>
  </html>


.. But keep in mind that the full `<span tal:replace="expression">Default Text</span>`
.. syntax also allows for default content in the unrendered template.

しかし、完全な `<span tal:replace="expression">Default Text</span>` の構文では、未レンダリングテンプレートのデフォルトコンテンツも使用できることに注意してください。

.. Being from the Pyramid world, Chameleon is not widely used.

Pyramidの世界からのもので、Chameleonは広く使われていません。

Mako
----

.. `Mako <http://www.makotemplates.org/>`_ is a template language that compiles to Python
.. for maximum performance. Its syntax and api is borrowed from the best parts of other
.. templating languages like Django and Jinja2 templates. It is the default template
.. language included with the `Pylons and Pyramid <http://www.pylonsproject.org/>`_ web
.. frameworks.

`Mako <http://www.makotemplates.org/>`_ はパフォーマンスを最大限に高めるためにPythonにコンパイルするテンプレート言語です。 その構文とapiは、DjangoやJinja2テンプレートのような他のテンプレート言語の最良の部分から借用されています。 これは `Pylons and Pyramid <http://www.pylonsproject.org/>`_ Webフレームワークに含まれるデフォルトのテンプレート言語です。

.. An example template in Mako looks like:

Makoのテンプレートの例は次のようになります:

.. code-block:: html

    <%inherit file="base.html"/>
    <%
        rows = [[v for v in range(0,10)] for row in range(0,10)]
    %>
    <table>
        % for row in rows:
            ${makerow(row)}
        % endfor
    </table>

    <%def name="makerow(row)">
        <tr>
        % for name in row:
            <td>${name}</td>\
        % endfor
        </tr>
    </%def>

.. To render a very basic template, you can do the following:

非常に基本的なテンプレートをレンダリングするには、次のようにします:

.. code-block:: python

    from mako.template import Template
    print(Template("hello ${data}!").render(data="world"))

.. Mako is well respected within the Python web community.

MakoはPythonのWebコミュニティで尊敬されています。

.. rubric:: References

.. [1] `The mod_python project is now officially dead <http://blog.dscpl.com.au/2010/06/modpython-project-is-now-officially.html>`_
.. [2] `mod_wsgi vs mod_python <http://www.modpython.org/pipermail/mod_python/2007-July/024080.html>`_
.. [3] `Benchmark of Python WSGI Servers <http://nichol.as/benchmark-of-python-web-servers>`_
