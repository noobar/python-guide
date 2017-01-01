.. Documentation
.. =============

ドキュメンテーション
====================

.. Readability is a primary focus for Python developers, in both project
.. and code documentation. Following some simple best practices can save
.. both you and others a lot of time.

読みやすさは、プロジェクトとコードの両方のドキュメントで、Python開発者の主な焦点です。いくつかの簡単なベストプラクティスに従えば、あなたと他の人の両方に多くの時間を節約できます。

.. Project Documentation
.. ---------------------

プロジェクトのドキュメント
--------------------------

.. A :file:`README` file at the root directory should give general information
.. to both users and maintainers of a project. It should be raw text or
.. written in some very easy to read markup, such as :ref:`reStructuredText-ref`
.. or Markdown. It should contain a few lines explaining the purpose of the
.. project or library (without assuming the user knows anything about the
.. project), the URL of the main source for the software, and some basic credit
.. information. This file is the main entry point for readers of the code.

ルートディレクトリにある :file:`README` ファイルは、プロジェクトのユーザと管理者の両方に一般的な情報を与えるべきです。生のテキストでなければなりません。例えば :ref:`reStructuredText-ref` やMarkdownのような読みやすいマークアップで記述します。プロジェクトやライブラリの目的（ユーザーがプロジェクトについて知っていることを前提としない）、ソフトウェアの主なソースのURL、および基本的なクレジット情報を説明する行がいくつか含まれていなければなりません。このファイルは、コードの読者のための主要なエントリポイントです。

.. An :file:`INSTALL` file is less necessary with Python.  The installation
.. instructions are often reduced to one command, such as ``pip install
.. module`` or ``python setup.py install`` and added to the :file:`README`
.. file.

Pythonでは :file:`INSTALL` ファイルはあまり必要ありません。 インストール指示は ``pip install module`` や ``python setup.py install`` のように1つのコマンドに短縮され、:file:`README` ファイルに追加されます。

.. A :file:`LICENSE` file should *always* be present and specify the license
.. under which the software is made available to the public.

:file:`LICENSE` ファイルは常に存在し、ライセンスを指定する必要があります
その下でソフトウェアは一般に公開されます。

.. A :file:`TODO` file or a ``TODO`` section in :file:`README` should list the
.. planned development for the code.

:file:`TODO` ファイルまたは ``TODO`` セクション :file:`README` は、コードの開発予定を列挙します。

.. A :file:`CHANGELOG` file or section in :file:`README` should compile a short
.. overview of the changes in the code base for the latest versions.

:file:`CHANGELOG` ファイルまたはセクション :file:`README` は、最新バージョンのコードベースの変更の概要をコンパイルする必要があります。

.. Project Publication
.. -------------------

プロジェクト出版
----------------

.. Depending on the project, your documentation might include some or all
.. of the following components:

プロジェクトによっては、ドキュメントに次のコンポーネントの一部またはすべてが含まれている場合があります。

.. - An *introduction* should show a very short overview of what can be
..   done with the product, using one or two extremely simplified use
..   cases. This is the thirty-second pitch for your project.

- *introduction* には、1つまたは2つの非常に単純化されたユースケースを使用して、製品でできることの概要を非常に簡単に示してください。これはあなたのプロジェクトのための30秒のピッチです。

.. - A *tutorial* should show some primary use cases in more detail. The reader
..   will follow a step-by-step procedure to set-up a working prototype.

- *チュートリアル* では、いくつかの主要なユースケースをより詳細に示す必要があります。読者は、実際のプロトタイプをセットアップするための段階的な手順に従います。

.. - An *API reference* is typically generated from the code (see
..   :ref:`docstrings <docstring-ref>`). It will list all publicly available
..   interfaces, parameters, and return values.

- *APIリファレンス* は通常、コードから生成されます（参照 :ref:`docstrings <docstring-ref>`）。これは、公開されているすべてのインターフェース、パラメーター、および戻り値をリストします。

.. - *Developer documentation* is intended for potential contributors. This can
..   include code convention and general design strategy of the project.

- *開発者ドキュメント* は、潜在的な貢献者を対象としています。 これには、プロジェクトのコード規約と一般的なデザイン戦略が含まれます。

.. _sphinx-ref:

Sphinx
~~~~~~

.. Sphinx_ is far and away the most popular Python documentation
.. tool. **Use it.**  It converts :ref:`restructuredtext-ref` markup language
.. into a range of output formats including HTML, LaTeX (for printable
.. PDF versions), manual pages, and plain text.

Sphinx_ は、最も人気のあるPythonドキュメントツールです。 **それを使用する。** :ref:`restructuredtext-ref` マークアップ言語を、HTML、LaTeX（印刷可能なPDF版用）、マニュアルページ、プレーンテキストなどの出力フォーマットの範囲に変換する。

.. There is also **great**, **free** hosting for your Sphinx_ docs:
.. `Read The Docs`_. Use it. You can configure it with commit hooks to
.. your source repository so that rebuilding your documentation will
.. happen automatically.

あなたの Sphinx_ docsのための **素晴らしい**、**無料の** ホスティングもあります: `Read The Docs`_。 これを使って。 ドキュメントの再構築が自動的に行われるように、ソースリポジトリへのコミットフックを設定することができます。

.. When run, Sphinx_ will import your code and using Python's introspection 
.. features it will extract all function, method and class signatures. It will
.. also extract the accompanying docstrings, and compile it all into well
.. structured and easily readable documentation for your project.  

実行すると、Sphinx_はコードをインポートし、Pythonのイントロスペクション機能を使用して、すべての関数、メソッド、クラスのシグネチャを抽出します。 また付属のドキュメントストリングを抽出し、それをすべて構造化された、簡単に読めるドキュメントにコンパイルしてプロジェクトに合わせます。

.. note::

    SphinxはAPIの生成で有名ですが、一般的なプロジェクトのドキュメントでもうまく機能します。 このガイドはSphinx_で構築され、 `Read The Docs`_

.. .. note::
.. 
..     Sphinx is famous for its API generation, but it also works well
..     for general project documentation. This Guide is built with
..     Sphinx_ and is hosted on `Read The Docs`_

.. _Sphinx: http://sphinx.pocoo.org
.. _Read The Docs: http://readthedocs.org

.. _restructuredtext-ref:

reStructuredText
~~~~~~~~~~~~~~~~

.. Most Python documentation is written with reStructuredText_. It's like
.. Markdown with all the optional extensions built in.

ほとんどのPythonのドキュメントはreStructuredText_で書かれています。 Markdownのように、すべてのオプションの拡張が組み込まれています。

.. The `reStructuredText Primer`_ and the `reStructuredText Quick
.. Reference`_ should help you familiarize yourself with its syntax.

`reStructuredText Primer`_ と `reStructuredText Quick Reference`_ は、その構文に慣れるのに役立ちます。

.. _reStructuredText: http://docutils.sourceforge.net/rst.html
.. _reStructuredText Primer: http://sphinx.pocoo.org/rest.html
.. _reStructuredText Quick Reference: http://docutils.sourceforge.net/docs/user/rst/quickref.html


.. Code Documentation Advice
.. -------------------------

コードドキュメントのアドバイス
------------------------------

.. Comments clarify the code and they are added with purpose of making the
.. code easier to understand. In Python, comments begin with a hash
.. (number sign) (``#``).

コメントはコードを明確にし、コードを分かりやすくする目的で追加されています。 Pythonでは、コメントはハッシュ (数字記号) (``#``) で始まります。

.. _docstring-ref:

.. In Python, *docstrings* describe modules, classes, and functions:

Pythonでは、*docstrings* はモジュール、クラス、関数を記述します:

.. code-block:: python

    def square_and_rooter(x):
        """Return the square root of self times self."""
        ...

.. In general, follow the comment section of :pep:`8#comments` (the "Python Style
.. Guide"). More information about docstrings can be found at :pep:`0257#specification` (The Docstring Conventions Guide).

一般的に、 :pep:`8#comments` ("Python Style Guide") のコメントセクションに従ってください。 docstringの詳細については、:pep:`0257#specification` （Docstring規約ガイド）を参照してください。

.. Commenting Sections of Code
.. ~~~~~~~~~~~~~~~~~~~~~~~~~~~

コードのセクションのコメント
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. *Do not use triple-quote strings to comment code*. This is not a good
.. practice, because line-oriented command-line tools such as grep will
.. not be aware that the commented code is inactive. It is better to add
.. hashes at the proper indentation level for every commented line. Your
.. editor probably has the ability to do this easily, and it is worth
.. learning the comment/uncomment toggle.

*トリプルクォート文字列を使用してコードにコメントを付けない*。 grepのような行指向のコマンドラインツールは、コメント付きコードが非アクティブであることを認識しないため、これは良い方法ではありません。コメント行ごとに適切なインデントレベルでハッシュを追加する方がよいでしょう。あなたのエディタはおそらくこれを簡単に実行する能力があり、コメント/コメント解除トグルを学ぶ価値があります。

.. Docstrings and Magic
.. ~~~~~~~~~~~~~~~~~~~~

ドキュメンテーションとマジック
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. Some tools use docstrings to embed more-than-documentation behavior,
.. such as unit test logic. Those can be nice, but you won't ever go
.. wrong with vanilla "here's what this does."

一部のツールでは、ドキュメントテストロジックなどのドキュメントよりも多くの動作を埋め込むためにドキュメントストリングを使用します。 それらは素晴らしいことができますが、あなたはバニラに間違って行くことはありません "ここにこれが何をしています。

.. Tools like Sphinx_ will parse your docstrings as reStructuredText and render it
.. correctly as HTML. This makes it very easy to embed snippets of example code in
.. a project's documentation.

Sphinx_ のようなツールは、ドキュメントストリングをreStructuredTextとして解析し、HTMLとして正しくレンダリングします。 これにより、サンプルコードのスニペットをプロジェクトのドキュメントに埋め込むことが非常に簡単になります。

.. Additionally, Doctest_ will read all embedded docstrings that look like input
.. from the Python commandline (prefixed with ">>>") and run them, checking to see
.. if the output of the command matches the text on the following line. This
.. allows developers to  embed real examples and usage of functions alongside
.. their source code, and as a side effect, it also ensures that their code is
.. tested and works.

さらに、Doctest_は、Pythonのコマンドライン（ ">>>"という接頭辞）の入力と同じように見える埋め込みdocstringをすべて読み込み、コマンドの出力が次の行のテキストと一致するかどうかを確認します。 これにより、開発者は実際のサンプルと関数の使用方法をソースコードとともに埋め込むことができ、副作用として、コードがテストされ、動作することが保証されます。

::
    
    def my_function(a, b):
        """
        >>> my_function(2, 3)
        6
        >>> my_function('a', 3)
        'aaa'
        """
        return a * b

.. _Doctest: https://docs.python.org/3/library/doctest.html

.. Docstrings versus Block comments
.. ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Docstringsとブロックコメント
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. These aren't interchangeable. For a function or class, the leading
.. comment block is a programmer's note. The docstring describes the
.. *operation* of the function or class:

これらは交換できません。関数またはクラスの場合、先頭のコメントブロックはプログラマーのメモです。 docstringは、関数またはクラスの *operation* を記述します:

.. code-block:: python

    # This function slows down program execution for some reason.
    def square_and_rooter(x):
        """Returns the square root of self times self."""
	...

.. Unlike block comments, docstrings are built into the Python language itself.
.. This means you can use all of Python's powerful introspection capabilities to
.. access docstrings at runtime, compared with comments which are optimised out.
.. Docstrings are accessible from both the `__doc__` dunder attribute for almost 
.. every Python object, as well as with the built in `help()` function.

ブロックコメントとは異なり、ドキュメントストリングはPython言語自体に組み込まれています。 つまり、Pythonの強力なイントロスペクション機能をすべて使用して、最適化されたコメントと比較して、実行時にドキュメントストリングにアクセスすることができます。 Docstringは、ほとんどすべてのPythonオブジェクトのための `__doc__` dunder属性と組み込みの `help()` 関数の両方からアクセスできます。

.. While block comments are usually used to explain *what* a section of code is
.. doing, or the specifics of an algorithm, docstrings are more intended for
.. explaining to other users of your code (or you in 6 months time) *how* a
.. particular function can be used and the general purpose of a function, class, 
.. or module.  

ブロックのコメントは通常、コードの何が何をしているのか、アルゴリズムの詳細を説明するために使われますが、docstringは他のユーザにあなたのコードを説明するためのものです（6ヶ月以内に） *how* 関数、クラス、モジュールの汎用目的に使用できます。

.. Writing Docstrings
.. ~~~~~~~~~~~~~~~~~~

ドキュメントストリングを書く
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. Depending on the complexity of the function, method, or class being written, a
.. one-line docstring may be perfectly appropriate. These are generally used for
.. really obvious cases, such as::

関数、メソッド、またはクラスの複雑さに応じて、1行のdocstringが完全に適切かもしれません。 これらは一般的に次のような本当の明白な場合に使用されます::

    def add(a, b):
        """Add two numbers and return the result."""
        return a + b

.. The docstring should describe the function in a way that is easy to understand.
.. For simple cases like trivial functions and classes, simply embedding the 
.. function's signature (i.e. `add(a, b) -> result`) in the docstring is 
.. unnecessary. This is because with Python's `inspect` module, it is already 
.. quite easy to find this information if needed, and it is also readily available
.. by reading the source code. 

docstringは、理解しやすい方法で関数を記述する必要があります。 簡単な関数やクラスのような簡単な場合は、関数のシグネチャ (つまり、`add(a, b) -> result`) をdocstringに埋め込むだけで済みます。 これは、Pythonの `inspect` モジュールでは、必要に応じてこの情報を見つけるのがとても簡単で、ソースコードを読むことで簡単に入手できるからです。

.. In larger or more complex projects however, it is often a good idea to give 
.. more information about a function, what it does, any exceptions it may raise, 
.. what it returns, or relevant details about the parameters.

しかし、より大規模なプロジェクトやより複雑なプロジェクトでは、関数、それが行うこと、発生する可能性のある例外、返されるもの、またはパラメータに関する関連する詳細に関する情報を多く与えることは、しばしば良い考えです。

.. For more detailed documentation of code a popular style is the one used for the
.. Numpy project, often called `Numpy style`_ docstrings. While it can take up a
.. few more lines the previous example, it allows the developer to include a lot 
.. more information about a method, function, or class. ::

コードのより詳細なドキュメンテーションについては、Numpyプロジェクトでよく使われるものがよく使われます. `Numpy style`_ と呼ばれることもあります。 これは前の例をいくつか追加していますが、開発者はメソッド、関数、またはクラスに関するさらに多くの情報を含めることができます。::

    def random_number_generator(arg1, arg2):
        """
        Summary line.

        Extended description of function.

        Parameters
        ----------
        arg1 : int
            Description of arg1
        arg2 : str
            Description of arg2

        Returns
        -------
        int
            Description of return value

        """
        return 42

.. The `sphinx.ext.napoleon`_ plugin allows Sphinx to parse this style of
.. docstrings, making it easy to incorporate NumPy style docstrings into your
.. project.

`sphinx.ext.napoleon`_ プラグインは、Sphinx がこのスタイルのドキュメントストリングを解析できるようにし、NumPyスタイルのドキュメントストリングをプロジェクトに簡単に組み込むことができます。

.. At the end of the day, it doesn't really matter what style is used for writing
.. docstrings, their purpose is to serve as documentation for anyone who may need
.. to read or make changes to your code. As long as it is correct, understandable
.. and gets the relevant points across then it has done the job it was designed to
.. do.

その日の終わりには、ドキュメントストリングを書くためにどのようなスタイルが使われているかは重要ではありません。その目的は、コードを読んだり変更したりする必要がある人のためのドキュメンテーションとして役立つことです。 それが正しい、理解できるものであれば、関連するポイントを得ることができます。


.. For further reading on docstrings, feel free to consult :pep:`257`

ドキュメントストリングをさらに読むには、相談してください :pep:`257`

.. _thomas-cokelaer.info: http://thomas-cokelaer.info/tutorials/sphinx/docstring_python.html
.. _sphinx.ext.napoleon: https://sphinxcontrib-napoleon.readthedocs.io/
.. _`NumPy style`: http://sphinxcontrib-napoleon.readthedocs.io/en/latest/example_numpy.html

.. Other Tools
.. -----------

その他のツール
--------------

.. You might see these in the wild. Use :ref:`sphinx-ref`.

あなたは野生でこれらを見るかもしれません。 :ref:`sphinx-ref` を使います。

.. Pycco_
..     Pycco is a "literate-programming-style documentation generator"
..     and is a port of the node.js Docco_. It makes code into a
..     side-by-side HTML code and documentation.

Pycco_
    Pyccoは "識字プログラミングスタイルのドキュメント生成プログラム" であり、node.js Docco_ の一部です。 それはコードをサイド・バイ・サイドのHTMLコードとドキュメントにします。

.. _Pycco: https://pycco-docs.github.io/pycco/
.. _Docco: http://jashkenas.github.com/docco

.. Ronn_
..     Ronn builds Unix manuals. It converts human readable textfiles to roff
..     for terminal display, and also to HTML for the web.

Ronn_
    RonnはUnixのマニュアルを作成しています。 これは、人間が読めるテキストファイルをターミナル表示のためにroffに、そしてウェブのHTMLに変換します。

.. _Ronn: https://github.com/rtomayko/ronn

.. Epydoc_
..     Epydoc is discontinued. Use :ref:`sphinx-ref` instead.

Epydoc_
    Epydocは廃止されました。 代わりに :ref:`sphinx-ref` を使用してください。

.. _Epydoc: http://epydoc.sourceforge.net

.. MkDocs_
..     MkDocs is a fast and simple static site generator that's geared towards
..     building project documentation with Markdown.

MkDocs_
    MkDocsは、Markdownでプロジェクトのドキュメンテーションを構築するための、高速でシンプルな静的サイト生成ツールです。

.. _MkDocs: http://www.mkdocs.org/
