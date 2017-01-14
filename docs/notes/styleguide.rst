.. _guide-style-guide:

.. =====================
.. The Guide Style Guide
.. =====================

====================
ガイドスタイルガイド
====================

.. As with all documentation, having a consistent format helps make the
.. document more understandable. In order to make The Guide easier to digest,
.. all contributions should fit within the rules of this style guide where
.. appropriate.

すべてのドキュメンテーションと同様に、一貫したフォーマットを使用すると、ドキュメントがわかりやすくなります。ガイドをダイジェストしやすくするために、すべての寄稿はこのスタイルガイドのルールの中に適切に収まる必要があります。

.. The Guide is written as :ref:`restructuredtext-ref`.

ガイドは :ref:`restructuredtext-ref` と書かれています。

.. .. note:: Parts of The Guide may not yet match this style guide. Feel free
..    to update those parts to be in sync with The Guide Style Guide

.. note:: ガイドの一部がこのスタイルガイドとまだ一致していない可能性があります。 これらの部分をガイドスタイルガイドと同期して更新してください。

.. .. note:: On any page of the rendered HTML you can click "Show Source" to
..    see how authors have styled the page.

.. note:: レンダリングされたHTMLのどのページでも、「ソースの表示」をクリックして、著者がページのスタイルをどのようにしているかを見ることができます。

.. Relevancy
.. ---------

関連性
------

.. Strive to keep any contributions relevant to the :ref:`purpose of The Guide
.. <about-ref>`.

:ref:`ガイドの目的 <about-ref>` に関連する貢献を維持してください。

.. * Avoid including too much information on subjects that don't directly
..   relate to Python development.
.. * Prefer to link to other sources if the information is already out there.
..   Be sure to describe what and why you are linking.
.. * `Cite <http://sphinx.pocoo.org/rest.html?highlight=citations#citations>`_
..   references where needed.
.. * If a subject isn't directly relevant to Python, but useful in conjunction
..   with Python (e.g., Git, GitHub, Databases), reference by linking to useful
..   resources, and describe why it's useful to Python.
.. * When in doubt, ask.

* Python開発に直接関係しない科目に関する情報をあまりにも多く含むことは避けてください。
* 既に情報がある場合は、他の情報源にリンクすることをお勧めします。 何がなぜあなたがなぜリンクしているのかを記述してください。
* `サイト <http://sphinx.pocoo.org/rest.html?highlight=citations#citations>`_ は必要に応じて参照してください。
* サブジェクトがPythonに直接関係しないが、Python（例えば、Git、GitHub、Databases）と連動して役に立つ場合、有用なPythonになぜ役に立つのかを説明します。
* 不確かな場合は、尋ねてください。

.. Headings
.. --------

見出し
------

.. Use the following styles for headings.

見出しには次のスタイルを使用します。

.. Chapter title:

章のタイトル:

.. code-block:: rest

    #########
    Chapter 1
    #########

.. Page title:

ページタイトル:

.. code-block:: rest

    ===================
    Time is an Illusion
    ===================

.. Section headings:

セクション見出し:

.. code-block:: rest

    Lunchtime Doubly So
    -------------------

.. Sub section headings:

サブセクション見出し:

.. code-block:: rest

    Very Deep
    ~~~~~~~~~

.. Prose
.. -----

散文
----

.. Wrap text lines at 78 characters. Where necessary, lines may exceed 78
.. characters, especially if wrapping would make the source text more difficult
.. to read.

テキスト行を78文字で囲みます。 必要に応じて、行が78文字を超える場合があります。特に、折り返しをするとソーステキストを読みにくくする可能性があります。

.. Use of the `serial comma <https://en.wikipedia.org/wiki/Serial_comma>`_
.. (also known as the Oxford comma) is 100% non-optional. Any attempt to
.. submit content with a missing serial comma will result in permanent banishment
.. from this project, due to complete and total lack of taste.

`シリアルカンマ <https://en.wikipedia.org/wiki/Serial_comma>`_ （オックスフォードカンマとしても知られています）の使用は100％非オプションです。 シリアルカンマがないコンテンツを提出しようとすると、全体の判断が不足し完了するため、このプロジェクトは永久に追放することになります。

.. Banishment? Is this a joke? Hopefully we will never have to find out.

追放？ それは冗談ですか？ うまくいけば、私たちは決して見つけ出す必要はありません。

.. Code Examples
.. -------------

コード例
--------

.. Wrap all code examples at 70 characters to avoid horizontal scrollbars.

水平スクロールバーを避けるには、すべてのコード例を70文字で囲みます。

.. Command line examples:

コマンドラインの例:

.. code-block:: rest

    .. code-block:: console

        $ run command --help
        $ ls ..

.. Be sure to include the ``$`` prefix before each line.

各行の前に ``$`` 接頭辞を必ず付けてください。

.. Python interpreter examples:

Pythonインタプリタの例:

.. code-block:: rest

    Label the example::

    .. code-block:: python

        >>> import this

.. Python examples:

Pythonの例:

.. code-block:: rest

    Descriptive title::

    .. code-block:: python

        def get_answer():
            return 42

.. Externally Linking
.. ------------------

外部リンク
----------

.. * Prefer labels for well known subjects (ex: proper nouns) when linking:

* リンク時によく知られている主題（例：固有名詞）のラベルを優先する:

  .. code-block:: rest

      SphinxはPythonを文書化するために使用されます。

..       Sphinx_ is used to document Python.

      .. _Sphinx: http://sphinx.pocoo.org

.. * Prefer to use descriptive labels with inline links instead of leaving bare
..   links:

* 空のリンクを残す代わりに、インラインリンクの説明ラベルを使用することをお勧めします。

  .. code-block:: rest

      Read the `Sphinx Tutorial <http://sphinx.pocoo.org/tutorial.html>`_

.. * Avoid using labels such as "click here", "this", etc. preferring
..   descriptive labels (SEO worthy) instead.

* 記述ラベル（SEOにふさわしい）を好む代わりに、「ここをクリック」、「これ」などのラベルを使用しないでください。

.. Linking to Sections in The Guide
.. --------------------------------

ガイドのセクションへのリンク
----------------------------

.. To cross-reference other parts of this documentation, use the `:ref:
.. <http://sphinx.pocoo.org/markup/inline.html#cross-referencing-arbitrary-locations>`_
.. keyword and labels.

このドキュメントの他の部分を相互参照するには、 `:ref: <http://sphinx.pocoo.org/markup/inline.html#cross-referencing-arbitrary-locations>`_ キーワードとラベルを使用してください。

.. To make reference labels more clear and unique, always add a ``-ref`` suffix:

参照ラベルをより明確かつユニークにするには、常に ``-ref`` 接尾辞を追加します:

.. code-block:: rest

    .. _some-section-ref:

    Some Section
    ------------

.. Notes and Warnings
.. ------------------

注釈と警告
----------

.. Make use of the appropriate `admonitions directives
.. <http://sphinx.pocoo.org/rest.html#directives>`_ when making notes.

注釈を作るときは、適切な `警告指令 <http://sphinx.pocoo.org/rest.html#directives>`_ を利用してください。

.. Notes:

注釈:

.. code-block:: rest

    .. note::
        銀河ヒッチハイク・ガイドには、タオルのテーマについていくつかのことが言及されています。 タオルは、星間のヒッチハイカーが持つことができる最も大規模で有用なものであると言います。

..     .. note::
..         The Hitchhiker’s Guide to the Galaxy has a few things to say
..         on the subject of towels. A towel, it says, is about the most
..         massively useful thing an interstellar hitch hiker can have.

.. Warnings:

警告:

.. code-block:: rest

    .. warning:: パニックに陥らないでください

..     .. warning:: DON'T PANIC

TODOs
-----

.. Please mark any incomplete areas of The Guide with a `todo directive
.. <http://sphinx.pocoo.org/ext/todo.html?highlight=todo#directive-todo>`_. To
.. avoid cluttering the :ref:`todo-list-ref`, use a single ``todo`` for stub
.. documents or large incomplete sections.

ガイドの不完全な部分は、 `todo directive <http://sphinx.pocoo.org/ext/todo.html?highlight=todo#directive-todo>`_ でマークしてください。 :ref:`todo-list-ref` が乱雑にならないようにするには、スタブドキュメントや大規模な不完全セクションに対しては単一の ``todo`` を使います。

.. code-block:: rest

    .. todo::
        生命、宇宙、そしてすべての究極の質問への究極の答えを学ぶ

..     .. todo::
..         Learn the Ultimate Answer to the Ultimate Question
..         of Life, The Universe, and Everything

