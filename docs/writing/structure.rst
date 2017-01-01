.. Structuring Your Project
.. ========================

プロジェクトの構造化
====================

.. By "structure" we mean the decisions you make concerning
.. how your project best meets its objective. We need to consider how to
.. best leverage Python's features to create clean, effective code.
.. In practical terms, "structure" means making clean code whose logic and
.. dependencies are clear as well as how the files and folders are organized
.. in the filesystem.

「構造」とは、プロジェクトがその目的をどのように最も満たしているかについての決定を意味します。 クリーンで効果的なコードを作成するために、Pythonの機能を最大限に活用する方法を検討する必要があります。 実際には、 "構造"とは、ロジックと依存関係が明確なクリーンなコードと、ファイルとフォルダがファイルシステムにどのように編成されているかを意味します。

.. Which functions should go into which modules? How does data flow through
.. the project? What features and functions can be grouped together and
.. isolated? By answering questions like these you can begin to plan, in
.. a broad sense, what your finished product will look like.

どの機能をどのモジュールに入れる必要がありますか？ プロジェクトを通じてデータはどのように流れますか？ グループ化して分離できる機能は何ですか？ このような質問に答えることで、完成した製品がどのように見えるかを広義で計画し始めることができます。

.. In this section we take a closer look at Python's module and import
.. systems as they are the central elements to enforcing structure in your
.. project. We then discuss various perspectives on how to build code which
.. can be extended and tested reliably.

このセクションでは、Pythonのモジュールとインポートシステムを詳しく見ていきます。プロジェクトの構造を強化するための中心的な要素です。 次に、コードを拡張して確実にテストできるようにするためのさまざまな方法について議論します。



.. Structure of the Repository
.. ---------------------------

リポジトリの構造
----------------

.. It's Important.
.. :::::::::::::::

それは重要です。
::::::::::::::::

.. Just as Code Style, API Design, and Automation are essential for a
.. healthy development cycle, Repository structure is a crucial part of
.. your project's
.. `architecture <http://www.amazon.com/gp/product/1257638017/ref=as_li_ss_tl?ie=UTF8&tag=bookforkind-20&linkCode=as2&camp=1789&creative=39095&creativeASIN=1257638017>`__.

コードスタイル、APIデザイン、オートメーションが健全な開発サイクルに欠かせないのと同様に、リポジトリ構造はプロジェクトの `architecture <http://www.amazon.com/gp/product/1257638017/ref=as_li_ss_tl?ie=UTF8&tag=bookforkind-20&linkCode=as2&camp=1789&creative=39095&creativeASIN=1257638017>`_ 。

.. When a potential user or contributor lands on your repository's page,
.. they see a few things:

潜在的なユーザーまたは投稿者があなたのリポジトリのページにアクセスすると、いくつかのことが表示されます。

.. -  Project Name
.. -  Project Description
.. -  Bunch O' Files

- プロジェクト名
- プロジェクトの説明
- Bunch O 'ファイル

.. Only when they scroll below the fold will the user see your project's
.. README.

フォールドの下にスクロールするときだけ、ユーザーはあなたのプロジェクトのREADMEを見ることができます。

.. If your repo is a massive dump of files or a nested mess of directories,
.. they might look elsewhere before even reading your beautiful
.. documentation.

あなたのレポがファイルの大量ダンプやディレクトリのネストされた混乱である場合、彼らはあなたの美しいドキュメントを読む前に他の場所を見るかもしれません。

..     Dress for the job you want, not the job you have.

    あなたの仕事ではなく、あなたが望む仕事のためのドレス。

.. Of course, first impressions aren't everything. You and your colleagues
.. will spend countless hours working with this repository, eventually
.. becoming intimately familiar with every nook and cranny. The layout of
.. it is important.

もちろん、最初の印象はすべてではありません。 あなたとあなたの同僚は、このリポジトリで何時間も過ごし、最終的にはすべての隅々まで親しみを感じるようになります。 そのレイアウトは重要です。

.. Sample Repository
.. :::::::::::::::::

サンプルリポジトリ
::::::::::::::::::

.. **tl;dr**: This is what `Kenneth Reitz <http://kennethreitz.org>`_ recommends.

**tl;dr**: これは、 `Kenneth Reitz <http://kennethreitz.org>`_ が推奨するものです。

.. This repository is `available on
.. GitHub <https://github.com/kennethreitz/samplemod>`__.

このリポジトリは `GitHubで利用可能 <https://github.com/kennethreitz/samplemod>`__ です。

::

    README.rst
    LICENSE
    setup.py
    requirements.txt
    sample/__init__.py
    sample/core.py
    sample/helpers.py
    docs/conf.py
    docs/index.rst
    tests/test_basic.py
    tests/test_advanced.py

.. Let's get into some specifics.

いくつかの具体的なことを考えてみましょう。

.. The Actual Module
.. :::::::::::::::::

実際のモジュール
::::::::::::::::

.. csv-table::
   :widths: 20, 40

   "Location", "``./sample/`` or ``./sample.py``"
   "Purpose", "The code of interest"


.. Your module package is the core focus of the repository. It should not
.. be tucked away:

あなたのモジュールパッケージはリポジトリの中心です。 それは遠ざけてはいけません:

::

    ./sample/

.. If your module consists of only a single file, you can place it directly
.. in the root of your repository:

モジュールが1つのファイルのみで構成されている場合、リポジトリのルートに直接置くことができます:

::

    ./sample.py

.. Your library does not belong in an ambiguous src or python subdirectory.

あなたのライブラリはあいまいなsrcまたはpythonサブディレクトリに属していません。

.. License
.. :::::::

ライセンス
::::::::::


.. csv-table::
   :widths: 20, 40

   "Location", "``./LICENSE``"
   "Purpose", "Lawyering up."


.. This is arguably the most important part of your repository, aside from
.. the source code itself. The full license text and copyright claims
.. should exist in this file.

おそらくソースコード自体を除いて、リポジトリの最も重要な部分です。 完全なライセンステキストと著作権表示がこのファイルに存在している必要があります。

.. If you aren't sure which license you should use for your project, check
.. out `choosealicense.com <http://choosealicense.com>`_.

プロジェクトに使用するライセンスが不明な場合は、 `choosealicense.com <http://choosealicense.com>`_ を参照してください。

.. Of course, you are also free to publish code without a license, but this
.. would prevent many people from potentially using your code.

もちろん、ライセンスなしでコードを公開することも自由ですが、これによって多くの人が潜在的にコードを使用することを防ぐことができます。

Setup.py
::::::::

.. csv-table::
   :widths: 20, 40

   "Location", "``./setup.py``"
   "Purpose", "Package and distribution management."


.. If your module package is at the root of your repository, this should
.. obviously be at the root as well.

あなたのモジュールパッケージがあなたのリポジトリのルートにある場合、これは明らかにルートにあるはずです。

.. Requirements File
.. :::::::::::::::::

要件ファイル
::::::::::::

.. csv-table::
   :widths: 20, 40

   "Location", "``./requirements.txt``"
   "Purpose", "Development dependencies."


.. A `pip requirements
.. file <https://pip.pypa.io/en/stable/user_guide/#requirements-files>`__
.. should be placed at the root of the repository. It should specify the
.. dependencies required to contribute to the project: testing, building,
.. and generating documentation.

`pip要件ファイル <https://pip.pypa.io/en/stable/user_guide/#requirements-files>`__ は、リポジトリのルートに置く必要があります。 プロジェクトに貢献するために必要な依存関係、つまりドキュメントのテスト、ビルド、および生成を指定する必要があります。

.. If your project has no development dependencies, or you prefer
.. development environment setup via ``setup.py``, this file may be
.. unnecessary.

あなたのプロジェクトに開発の依存関係がない場合や、 ``setup.py`` を介して開発環境を設定したい場合は、このファイルは不要です。

.. Documentation
.. :::::::::::::

ドキュメンテーション
::::::::::::::::::::


.. csv-table::
   :widths: 20, 40

   "Location", "``./docs/``"
   "Purpose", "Package reference documentation."

.. There is little reason for this to exist elsewhere.

これが他の場所に存在する理由はほとんどありません。

.. Test Suite
.. ::::::::::

テストスイート
::::::::::::::


.. csv-table::
   :widths: 20, 40

   "Location", "``./test_sample.py`` or ``./tests``"
   "Purpose", "Package integration and unit tests."

.. Starting out, a small test suite will often exist in a single file:

まず始めに、小さなテストスイートが1つのファイルに存在することがよくあります:

::

    ./test_sample.py

.. Once a test suite grows, you can move your tests to a directory, like
.. so:

テストスイートが成長したら、次のようにテストをディレクトリに移動できます:

::

    tests/test_basic.py
    tests/test_advanced.py

.. Obviously, these test modules must import your packaged module to test
.. it. You can do this a few ways:

明らかに、これらのテストモジュールはパッケージ化されたモジュールをインポートしてテストする必要があります。これにはいくつかの方法があります:

.. -  Expect the package to be installed in site-packages.
.. -  Use a simple (but *explicit*) path modification to resolve the
..    package properly.

- パッケージをサイトパッケージにインストールすることを期待してください。
- パッケージを適切に解決するには、単純な (しかし *明示的な* )パス変更を使用します。

.. I highly recommend the latter. Requiring a developer to run
.. ``setup.py develop`` to test an actively changing
.. codebase also requires them to have an isolated environment setup for
.. each instance of the codebase.

私は後者を強く勧めます。 開発者が積極的に変化するコードベースをテストするために ``setup.py develop`` を実行するように要求するためには、コードベースのインスタンスごとに独立した環境設定が必要です。

.. To give the individual tests import context, create a tests/context.py
.. file:

個々のテストにインポートコンテキストを与えるには、tests/context.py ファイルを作成します:

::

    import os
    import sys
    sys.path.insert(0, os.path.abspath('..'))

    import sample

.. Then, within the individual test modules, import the module like so:

次に、個々のテストモジュール内で、次のようにモジュールをインポートします:

::

    from .context import sample

.. This will always work as expected, regardless of installation method.

これは、インストール方法に関係なく、常に期待どおりに動作します。

.. Some people will assert that you should distribute your tests within
.. your module itself -- I disagree. It often increases complexity for your
.. users; many test suites often require additional dependencies and
.. runtime contexts.

あなた自身のモジュール内でテストを配布すべきだと主張する人もいますが、私は同意しません。 多くの場合、ユーザーの複雑さが増します。 多くのテストスイートでは、多くの場合、追加の依存関係と実行時コンテキストが必要になります。

Makefile
::::::::


.. csv-table::
   :widths: 20, 40

   "Location", "``./Makefile``"
   "Purpose", "Generic management tasks."


.. If you look at most of my projects or any Pocoo project, you'll notice a
.. Makefile laying around. Why? These projects aren't written in C... In
.. short, make is a incredibly useful tool for defining generic tasks for
.. your project.

ほとんどのプロジェクトやPocooプロジェクトを見てみると、Makefileがあることに気付くでしょう。 どうして？ これらのプロジェクトはC言語で書かれていません...要するに、makeはプロジェクトの一般的なタスクを定義するための非常に便利なツールです。

**Sample Makefile:**

::

    init:
        pip install -r requirements.txt

    test:
        py.test tests

    .PHONY: init test

.. Other generic management scripts (e.g. ``manage.py``
.. or ``fabfile.py``) belong at the root of the repository as well.

リポジトリのルートには、他の一般的な管理スクリプト（ ``manage.py`` や ``fabfile.py`` など）も属しています。

.. Regarding Django Applications
.. :::::::::::::::::::::::::::::

Djangoアプリケーションについて
::::::::::::::::::::::::::::::

.. I've noticed a new trend in Django applications since the release of
.. Django 1.4. Many developers are structuring their repositories poorly
.. due to the new bundled application templates.

私はDjango 1.4のリリース以来、Djangoアプリケーションの新しいトレンドに気付きました。 多くの開発者は、新しいバンドルされたアプリケーションテンプレートのためにリポジトリを構成していません。

.. How? Well, they go to their bare and fresh repository and run the
.. following, as they always have:

どうやって？ さて、彼らはいつものように、裸の新鮮なリポジトリに行き、以下を実行します:

::

    $ django-admin.py startproject samplesite

.. The resulting repository structure looks like this:

結果のリポジトリ構造は次のようになります:

::

    README.rst
    samplesite/manage.py
    samplesite/samplesite/settings.py
    samplesite/samplesite/wsgi.py
    samplesite/samplesite/sampleapp/models.py

.. Don't do this.

これはしないでください。

.. Repetitive paths are confusing for both your tools and your developers.
.. Unnecessary nesting doesn't help anybody (unless they're nostalgic for
.. monolithic SVN repos).

反復的なパスは、ツールと開発者の両方にとって混乱を招きます。 不要なネスティングは誰にも役立ちません（モノリシックなSVNリポジトリを懐かしくしていない限り）。

.. Let's do it properly:

それを正しくしよう:

::

    $ django-admin.py startproject samplesite .

.. Note the "``.``".

"``.``" に注意してください。

.. The resulting structure:

結果の構造:

::

    README.rst
    manage.py
    samplesite/settings.py
    samplesite/wsgi.py
    samplesite/sampleapp/models.py




.. Structure of Code is Key
.. ------------------------

コードの構造は重要です
----------------------

.. Thanks to the way imports and modules are handled in Python, it is
.. relatively easy to structure a Python project. Easy, here, means
.. that you do not have many constraints and that the module
.. importing model is easy to grasp. Therefore, you are left with the
.. pure architectural task of crafting the different parts of your
.. project and their interactions.

インポートとモジュールをPythonで処理する方法のおかげで、Pythonプロジェクトを構造化するのは比較的簡単です。 ここで簡単に言うと、あなたは多くの制約がなく、モデルをインポートするモジュールが把握しやすいということです。 したがって、プロジェクトのさまざまな部分とその相互作用を作成するという、純粋なアーキテクチャ上の任務が残っています。

.. Easy structuring of a project means it is also easy
.. to do it poorly. Some signs of a poorly structured project
.. include:

プロジェクトの簡単な構造化は、それを貧弱にすることも容易であることを意味します。 構造の整っていないプロジェクトのいくつかの兆候は次のとおりです。

.. - Multiple and messy circular dependencies: if your classes
..   Table and Chair in :file:`furn.py` need to import Carpenter from
..   :file:`workers.py` to answer a question such as ``table.isdoneby()``,
..   and if conversely the class Carpenter needs to import Table and Chair,
..   to answer the question ``carpenter.whatdo()``, then you
..   have a circular dependency. In this case you will have to resort to
..   fragile hacks such as using import statements inside
..   methods or functions.

- 複数の乱雑な循環依存関係 :file:`furn.py` の中のクラスTableとChairが ``table.isdoneby()`` のような質問に答えるために :file:`workers.py` からCarpenterをインポートする必要がある場合 逆にCarpenterクラスがTableとChairをインポートする必要がある場合は、 ``carpenter.whatdo()`` という質問に答えるためには、循環依存関係があります。 この場合、メソッドや関数の中でimportステートメントを使うなど、脆弱なハックに頼らざるを得ません。

.. - Hidden coupling: each and every change in Table's implementation
..   breaks 20 tests in unrelated test cases because it breaks Carpenter's code,
..   which requires very careful surgery to adapt the change. This means
..   you have too many assumptions about Table in Carpenter's code or the
..   reverse.

- 非表示のカップリング: テーブルの実装の各変更は、関連のないテストケースで20回のテストを中断します。これは、カーペンターのコードを破るためです。つまり、カーペンターのコード内のテーブルについての仮定があまりにも多いか、その逆のことです。


.. - Heavy usage of global state or context: instead of explicitly
..   passing ``(height, width, type, wood)`` to each other, Table
..   and Carpenter rely on global variables that can be modified
..   and are modified on the fly by different agents. You need to
..   scrutinize all access to these global variables to understand why
..   a rectangular table became a square, and discover that remote
..   template code is also modifying this context, messing with
..   table dimensions.

- 大域的な状態や文脈の大量使用: 明示的に ``（高さ、幅、タイプ、木）`` に渡すのではなく、テーブルとカーペンターは変更可能なグローバル変数に依存しており、 。 矩形テーブルが正方形になった理由を理解するために、これらのグローバル変数へのすべてのアクセスを精査し、リモートテンプレートコードがこのコンテキストを変更してテーブル次元を混乱させていることを発見する必要があります。

.. - Spaghetti code: multiple pages of nested if clauses and for loops
..   with a lot of copy-pasted procedural code and no
..   proper segmentation are known as spaghetti code. Python's
..   meaningful indentation (one of its most controversial features) make
..   it very hard to maintain this kind of code. So the good news is that
..   you might not see too much of it.

- スパゲッティコード：入れ子にされたif節の複数のページと、多数のコピーペーストされた手続き型コードと適切なセグメンテーションのないループの場合はスパゲッティコードとして知られています。 Pythonの意味のあるインデント（最も論争の的になっている機能の1つ）は、この種のコードを維持することを非常に困難にしています。 良いニュースはあなたがあまりそれを見ないかもしれないということです。

.. - Ravioli code is more likely in Python: it consists of hundreds of
..   similar little pieces of logic, often classes or objects, without
..   proper structure. If you never can remember if you have to use
..   FurnitureTable, AssetTable or Table, or even TableNew for your
..   task at hand, you might be swimming in ravioli code.

- ラビオリのコードは、Pythonの可能性が高いです。それは、何百もの類似した小さなロジック、しばしばクラスまたはオブジェクトで構成され、適切な構造がありません。 FurnitureTable、AssetTableまたはTable、またはTableNewを使用しなければならないことを決して覚えていない場合は、ラビオリコードで泳いでいるかもしれません。


.. Modules
.. -------

モジュール
----------

.. Python modules are one of the main abstraction layers available and probably the
.. most natural one. Abstraction layers allow separating code into parts holding
.. related data and functionality.

Pythonモジュールは、利用可能な主要な抽象レイヤーの1つであり、おそらく最も自然なものです。抽象レイヤでは、コードを関連するデータと機能を保持する部分に分けることができます。

.. For example, a layer of a project can handle interfacing with user actions,
.. while another would handle low-level manipulation of data. The most natural way
.. to separate these two layers is to regroup all interfacing functionality
.. in one file, and all low-level operations in another file. In this case,
.. the interface file needs to import the low-level file. This is done with the
.. ``import`` and ``from ... import`` statements.

たとえば、プロジェクトのレイヤーはユーザーアクションとのインタフェースを処理でき、別のレイヤーはデータの低レベル操作を処理します。 これらの2つの層を分離する最も自然な方法は、1つのファイル内のすべてのインターフェース機能と、別のファイル内のすべての低レベル操作を再グループ化することです。 この場合、インターフェイスファイルは低レベルのファイルをインポートする必要があります。 これは ``import`` と ``from ... import`` 文で行います。

.. As soon as you use `import` statements you use modules. These can be either
.. built-in modules such as `os` and `sys`, third-party modules you have installed
.. in your environment, or your project's internal modules.

`import` 文を使うとすぐにモジュールを使います。 これらのモジュールは、`os` や `sys` などの組み込みモジュール、環境にインストールしたサードパーティモジュール、プロジェクトの内部モジュールのいずれかです。

.. To keep in line with the style guide, keep module names short, lowercase, and
.. be sure to avoid using special symbols like the dot (.) or question mark (?).
.. So a file name like :file:`my.spam.py` is one you should avoid! Naming this way
.. will interfere with the way Python looks for modules.

スタイルガイドと一致するように、モジュール名は小文字で、小文字にしておき、ドット (.) や疑問符 (?) などの特別な記号は使用しないでください。 したがって、:file:`my.spam.py` のようなファイル名は避けてください！ このように命名すると、Pythonがモジュールを探す方法が妨げられます。

.. In the case of `my.spam.py` Python expects to find a :file:`spam.py` file in a
.. folder named :file:`my` which is not the case. There is an
.. `example <http://docs.python.org/tutorial/modules.html#packages>`_ of how the
.. dot notation should be used in the Python docs.

`my.spam.py` の場合、Pythonは :file:`spam.py` ファイルを :file:`my` という名前のフォルダはありません。ある `example <http://docs.python.org/tutorial/modules.html#packages>`_ Pythonドキュメントではドット表記を使用するべきです。

.. If you'd like you could name your module :file:`my_spam.py`, but even our
.. friend the underscore should not be seen often in module names.

モジュール名を :file:`my_spam.py` とすることもできますが、私たちの友人でさえ、アンダースコアはモジュール名でよく見られるべきではありません。

.. Aside from some naming restrictions, nothing special is required for a Python
.. file to be a module, but you need to understand the import mechanism in order
.. to use this concept properly and avoid some issues.

いくつかの命名制限の他に、Pythonファイルがモジュールであるために特別なものは必要ありませんが、この概念を適切に使用し、いくつかの問題を避けるためには、インポートメカニズムを理解する必要があります。

.. Concretely, the ``import modu`` statement will look for the proper file, which
.. is :file:`modu.py` in the same directory as the caller if it exists.  If it is
.. not found, the Python interpreter will search for :file:`modu.py` in the "path"
.. recursively and raise an ImportError exception if it is not found.

具体的には、 ``import modu`` 文は適切なファイルを探します。これは、呼び出し側と同じディレクトリに :file:`modu.py` がある場合です。見つからなければ、Pythonインタプリタは "path"内の :file:`modu.py` を再帰的に検索し、見つからなければImportError例外を送出します。

.. Once :file:`modu.py` is found, the Python interpreter will execute the module in
.. an isolated scope. Any top-level statement in :file:`modu.py` will be executed,
.. including other imports if any. Function and class definitions are stored in
.. the module's dictionary.

一旦 :file:`modu.py` が見つかると、Pythonインタプリタはモジュールを隔離したスコープで実行します。 :file:`modu.py` 内のトップレベルのステートメントが実行されます。 関数とクラスの定義は、モジュールの辞書に格納されています。

.. Then, the module's variables, functions, and classes will be available to the
.. caller through the module's namespace, a central concept in programming that is
.. particularly helpful and powerful in Python.

次に、モジュールの変数、関数、およびクラスは、Pythonで特に有用で強力なプログラミングの中心概念である、モジュールの名前空間を通じて呼び出し元が利用できるようになります。

.. In many languages, an ``include file`` directive is used by the preprocessor to
.. take all code found in the file and 'copy' it into the caller's code. It is
.. different in Python: the included code is isolated in a module namespace, which
.. means that you generally don't have to worry that the included code could have
.. unwanted effects, e.g. override an existing function with the same name.

多くの言語では、 ``include file`` ディレクティブがプリプロセッサで使用され、ファイル内のすべてのコードを取得し、呼び出し側のコードにコピーします。 Pythonではこれが異なります。含まれているコードはモジュールの名前空間で分離されています。これは、一般的に、含まれているコードが望ましくない影響を及ぼすことを心配する必要がないことを意味します。 既存の関数を同じ名前で上書きします。

.. It is possible to simulate the more standard behavior by using a special syntax
.. of the import statement: ``from modu import *``. This is generally considered
.. bad practice. **Using** ``import *`` **makes code harder to read and makes
.. dependencies less compartmentalized**.

import文の特殊な構文を使用すると、より標準的な動作をシミュレートすることができます: ``from modu import *``。 これは一般に悪い習慣とみなされます。 ``import *`` を **使うと** 、**コードの読み込みが難しくなり、依存関係をコンパートメント化しにくくなります**。

.. Using ``from modu import func`` is a way to pinpoint the function you want to
.. import and put it in the global namespace. While much less harmful than ``import
.. *`` because it shows explicitly what is imported in the global namespace, its
.. only advantage over a simpler ``import modu`` is that it will save a little
.. typing.

``from modu import func`` は、インポートする関数を特定し、グローバル名前空間に入れる方法です。 グローバルな名前空間にインポートされるものを明示的に示しているので、 ``import *`` よりも害は少ないですが、単純な ``import modu`` より唯一の利点は、少しタイピングを省くことです。

.. **Very bad**

**ひどい**

.. code-block:: python

    [...]
    from modu import *
    [...]
    x = sqrt(4)  # Is sqrt part of modu? A builtin? Defined above?

.. **Better**

**より良い**

.. code-block:: python

    from modu import sqrt
    [...]
    x = sqrt(4)  # sqrt may be part of modu, if not redefined in between

.. **Best**

**ベスト**

.. code-block:: python

    import modu
    [...]
    x = modu.sqrt(4)  # sqrt is visibly part of modu's namespace

.. As mentioned in the :ref:`code_style` section, readability is one of the main
.. features of Python. Readability means to avoid useless boilerplate text and
.. clutter, therefore some efforts are spent trying to achieve a certain level of
.. brevity. But terseness and obscurity are the limits where brevity should stop.
.. Being able to tell immediately where a class or function comes from, as in the
.. ``modu.func`` idiom, greatly improves code readability and understandability in
.. all but the simplest single file projects.

:ref:`code_style` セクションで述べたように、読みやすさはPythonの主な機能の1つです。読みやすさとは、無用な定型文や混乱を避けることを意味します。したがって、一定のレベルの簡潔さを達成しようと努力しています。しかし、簡潔さとあいまいさは、簡潔さが止まるべき限界です。 ``modu.func`` イディオムのように、クラスや関数がどこから来ているのかをすぐに知ることができるので、最もシンプルな単一ファイルプロジェクトだけでは、コードの読みやすさとわかりやすさが大幅に向上します。


.. Packages
.. --------

パッケージ
----------

.. Python provides a very straightforward packaging system, which is simply an
.. extension of the module mechanism to a directory.

Pythonは非常に単純なパッケージシステムを提供しています。これは単純にモジュール機構をディレクトリに拡張したものです。

.. Any directory with an :file:`__init__.py` file is considered a Python package.
.. The different modules in the package are imported in a similar manner as plain
.. modules, but with a special behavior for the :file:`__init__.py` file, which is
.. used to gather all package-wide definitions.

:file:`__init __.py` ファイルを持つディレクトリはPythonパッケージとみなされます。パッケージ内のさまざまなモジュールは、普通のモジュールと同様にインポートされますが、パッケージ全体の定義を集めるために使用される :file:`__init __.py` ファイルの特殊な動作を伴います。

.. A file :file:`modu.py` in the directory :file:`pack/` is imported with the
.. statement ``import pack.modu``. This statement will look for an
.. :file:`__init__.py` file in :file:`pack`, execute all of its top-level
.. statements. Then it will look for a file named :file:`pack/modu.py` and
.. execute all of its top-level statements. After these operations, any variable,
.. function, or class defined in :file:`modu.py` is available in the pack.modu
.. namespace.

ディレクトリ :file:`pack/` のファイル :file:`modu.py` は、``import pack.modu`` というステートメントでインポートされます。 この文は :file:`__init __.py` ファイルを :file:`pack` で探し、すべての最上位レベルの文を実行します。 それから、:file:`pack/modu.py` という名前のファイルを探し、すべてのトップレベルのステートメントを実行します。 これらの操作の後で、:file:`modu.py` で定義された変数、関数、またはクラスは、pack.modu名前空間で使用できます。

.. A commonly seen issue is to add too much code to :file:`__init__.py`
.. files. When the project complexity grows, there may be sub-packages and
.. sub-sub-packages in a deep directory structure. In this case, importing a
.. single item from a sub-sub-package will require executing all
.. :file:`__init__.py` files met while traversing the tree.

よく見られる問題は、:file:`__init __.py` ファイルにあまりにも多くのコードを追加することです。 プロジェクトの複雑さが増すと、深いディレクトリ構造にサブパッケージとサブサブパッケージが存在する可能性があります。 この場合、サブサブパッケージから単一の項目をインポートするには、ツリーを走査中にall :file:`__init __.py` ファイルを実行する必要があります。

.. Leaving an :file:`__init__.py` file empty is considered normal and even a good
.. practice, if the package's modules and sub-packages do not need to share any
.. code.

パッケージのモジュールとサブパッケージがコードを共有する必要がない場合、:file:`__init __.py` ファイルを空のままにしておくのは正常であり、良い習慣でもあります。

.. Lastly, a convenient syntax is available for importing deeply nested packages:
.. ``import very.deep.module as mod``. This allows you to use `mod` in place of the
.. verbose repetition of ``very.deep.module``.

最後に、深くネストされたパッケージをインポートするための便利な構文があります: ``import very.deep.module as mod``。これにより、 ``very.deep.module`` の冗長な繰り返しの代わりに `mod` を使うことができます。

.. Object-oriented programming
.. ---------------------------

オブジェクト指向プログラミング
------------------------------

.. Python is sometimes described as an object-oriented programming language. This
.. can be somewhat misleading and needs to be clarified.

Pythonは、オブジェクト指向プログラミング言語として記述されることがあります。これはやや誤解を招く可能性があり、明確にする必要があります。

.. In Python, everything is an object, and can be handled as such. This is what is
.. meant when we say, for example, that functions are first-class objects.
.. Functions, classes, strings, and even types are objects in Python: like any
.. object, they have a type, they can be passed as function arguments, and they
.. may have methods and properties. In this understanding, Python is an
.. object-oriented language.

Pythonでは、すべてがオブジェクトであり、そのように扱うことができます。これは、たとえば、関数がファーストクラスのオブジェクトであると言うときに意味するものです。関数、クラス、文字列、さらには型はPythonのオブジェクトです。どんなオブジェクトと同様、型を持ち、関数の引数として渡すことができ、メソッドとプロパティを持つことができます。この理解では、Pythonはオブジェクト指向言語です。

.. However, unlike Java, Python does not impose object-oriented programming as the
.. main programming paradigm. It is perfectly viable for a Python project to not
.. be object-oriented, i.e. to use no or very few class definitions, class
.. inheritance, or any other mechanisms that are specific to object-oriented
.. programming.

しかし、Javaとは異なり、Pythonはオブジェクト指向プログラミングを主なプログラミングパラダイムとして課していません。 Pythonプロジェクトがオブジェクト指向ではないこと、すなわち、クラス定義、クラス継承、またはオブジェクト指向プログラミングに特有の他のメカニズムを使用しないこと、またはごくわずかしか使用しないことは、完全に実行可能です。

.. Moreover, as seen in the modules_ section, the way Python handles modules and
.. namespaces gives the developer a natural way to ensure the
.. encapsulation and separation of abstraction layers, both being the most common
.. reasons to use object-orientation. Therefore, Python programmers have more
.. latitude to not use object-orientation, when it is not required by the business
.. model.

さらに、モジュール_ セクションに見られるように、Pythonがモジュールと名前空間を扱う方法は、開発者に抽象レイヤのカプセル化と分離を保証する自然な方法です。どちらもオブジェクト指向を使用する最も一般的な理由です。 したがって、Pythonプログラマーは、ビジネスモデルで必要とされないときに、オブジェクト指向を使用しないという自由度があります。

.. There are some reasons to avoid unnecessary object-orientation. Defining
.. custom classes is useful when we want to glue together some state and some
.. functionality. The problem, as pointed out by the discussions about functional
.. programming, comes from the "state" part of the equation.

不要なオブジェクト指向を避ける理由はいくつかあります。 カスタムクラスを定義することは、いくつかの状態といくつかの機能を結合する場合に便利です。 関数型プログラミングに関する議論で指摘されているように、問題は方程式の "状態" の部分から来ています。

.. In some architectures, typically web applications, multiple instances of Python
.. processes are spawned to respond to external requests that can happen at the
.. same time. In this case, holding some state into instantiated objects, which
.. means keeping some static information about the world, is prone to concurrency
.. problems or race-conditions. Sometimes, between the initialization of the state
.. of an object (usually done with the ``__init__()`` method) and the actual use
.. of the object state through one of its methods, the world may have changed, and
.. the retained state may be outdated. For example, a request may load an item in
.. memory and mark it as read by a user. If another request requires the deletion
.. of this item at the same time, it may happen that the deletion actually occurs
.. after the first process loaded the item, and then we have to mark as read a
.. deleted object.

いくつかのアーキテクチャ、通常はWebアプリケーションでは、複数のインスタンスのPythonプロセスが生成され、同時に発生する可能性のある外部要求に応答します。この場合、いくつかの状態をインスタンス化されたオブジェクトに保持することは、世界に関するいくつかの静的情報を保持することを意味し、並行性の問題または競合状態になりがちです。時には、オブジェクトの状態の初期化（通常は ``__init __()`` メソッドで行われます）とそのメソッドの1つによるオブジェクト状態の実際の使用の間に、世界が変更された可能性があります。時代遅れである。例えば、要求はメモリ内のアイテムをロードし、ユーザによってそれを読み取りとしてマークすることができる。別のリクエストで同時にこのアイテムの削除が必要な場合は、最初のプロセスがアイテムをロードした後に実際に削除が行われ、削除されたオブジェクトを読み取り済みとしてマークする必要があります。

.. This and other issues led to the idea that using stateless functions is a
.. better programming paradigm.

これと他の問題は、ステートレス関数の使用がより良いプログラミングパラダイムであるという考えにつながりました。

.. Another way to say the same thing is to suggest using functions and procedures
.. with as few implicit contexts and side-effects as possible. A function's
.. implicit context is made up of any of the global variables or items in the
.. persistence layer that are accessed from within the function. Side-effects are
.. the changes that a function makes to its implicit context. If a function saves
.. or deletes data in a global variable or in the persistence layer, it is said to
.. have a side-effect.

同じことを言うもう一つの方法は、できるだけ暗黙的なコンテキストと副作用の少ない関数とプロシージャを使用することを提案することです。関数の暗黙のコンテキストは、関数内からアクセスされる永続化層のグローバル変数または項目のいずれかで構成されます。副作用とは、関数がその暗黙のコンテキストに対して行う変更です。関数がグローバル変数または永続化層にデータを保存または削除する場合、それは副作用を伴うと言われています。

.. Carefully isolating functions with context and side-effects from functions with
.. logic (called pure functions) allow the following benefits:

文脈や副作用を伴う関数をロジックを持つ関数（純関数と呼ぶ）から慎重に分離することで、次のような利点が得られます。

.. - Pure functions are deterministic: given a fixed input,
..   the output will always be the same.

- 純粋な関数は確定的です: 固定された入力が与えられると、出力は常に同じになります。

.. - Pure functions are much easier to change or replace if they need to
..   be refactored or optimized.

- リファクタリングや最適化が必要な場合は、純関数を簡単に変更または置換することができます。

.. - Pure functions are easier to test with unit-tests: There is less
..   need for complex context setup and data cleaning afterwards.

- 純粋な関数は単体テストでテストする方が簡単です。後で複雑なコンテキストの設定やデータのクリーニングが不要になります。

.. - Pure functions are easier to manipulate, decorate, and pass around.

- 純粋な関数は、操作、飾り付け、渡しが簡単です。

.. In summary, pure functions are more efficient building blocks than classes
.. and objects for some architectures because they have no context or side-effects.

要約すると、純粋な関数は、コンテキストや副作用がないため、クラスやオブジェクトよりも効率的なビルディングブロックです。

.. Obviously, object-orientation is useful and even necessary in many cases, for
.. example when developing graphical desktop applications or games, where the
.. things that are manipulated (windows, buttons, avatars, vehicles) have a
.. relatively long life of their own in the computer's memory.

明らかに、オブジェクト指向は、操作されるもの（ウィンドウ、ボタン、アバター、車両）がコンピュータで比較的長生きするグラフィカルデスクトップアプリケーションやゲームを開発する場合など、多くの場合、 メモリ。


.. Decorators
.. ----------

デコレータ
----------

.. The Python language provides a simple yet powerful syntax called 'decorators'.
.. A decorator is a function or a class that wraps (or decorates) a function
.. or a method. The 'decorated' function or method will replace the original
.. 'undecorated' function or method. Because functions are first-class objects
.. in Python, this can be done 'manually', but using the @decorator syntax is
.. clearer and thus preferred.

Python言語は、シンプルで強力な構文で、「デコレータ」と呼ばれています。デコレータは、関数またはメソッドをラップする（または装飾する）関数またはクラスです。 「装飾された」機能または方法は、元の「装飾されていない」機能または方法を置き換える。関数はPythonのファーストクラスのオブジェクトであるため、これは '手動で'行うことができますが、@デコレータの構文を使用する方が明確であり、したがって好ましいものです。

.. code-block:: python

    def foo():
        # do something

    def decorator(func):
        # manipulate func
        return func

    foo = decorator(foo)  # Manually decorate

    @decorator
    def bar():
        # Do something
    # bar() is decorated

.. This mechanism is useful for separating concerns and avoiding
.. external un-related logic 'polluting' the core logic of the function
.. or method. A good example of a piece of functionality that is better handled
.. with decoration is `memoization <https://en.wikipedia.org/wiki/Memoization#Overview>`__ or caching: you want to store the results of an
.. expensive function in a table and use them directly instead of recomputing
.. them when they have already been computed. This is clearly not part
.. of the function logic.

このメカニズムは、懸念を分離し、関数またはメソッドのコアロジックを「汚染する」外部の関連しないロジックを回避するのに便利です。 デコレーションでうまく処理される機能の良い例は `memoization <https://en.wikipedia.org/wiki/Memoization#Overview>`__ またはキャッシングです：高価な関数の結果を 既に計算されているときにそれらを再計算する代わりに直接使用することができます。 これは明らかに関数ロジックの一部ではありません。

.. Context Managers
.. ----------------

コンテキストマネージャ
----------------------

.. A context manager is a Python object that provides extra contextual information
.. to an action. This extra information takes the form of running a callable upon
.. initiating the context using the ``with`` statement, as well as running a callable
.. upon completing all the code inside the ``with`` block. The most well known
.. example of using a context manager is shown here, opening on a file:

コンテキストマネージャは、アクションに余分なコンテキスト情報を提供するPythonオブジェクトです。 この余分な情報は、 ``with`` 文を使って文脈を開始すると同時に、 ``with`` ブロック内のすべてのコードを完了したときに呼び出し可能なものを実行するという形で呼び出すことができます。 コンテキストマネージャを使用する最もよく知られている例をここに示し、ファイルを開きます:

.. code-block:: python

    with open('file.txt') as f:
        contents = f.read()

.. Anyone familiar with this pattern knows that invoking ``open`` in this fashion
.. ensures that ``f``'s ``close`` method will be called at some point. This reduces
.. a developer's cognitive load and makes the code easier to read.

このパターンに精通している人は、このように ``open`` を呼び出すと、ある時点で ``f`` の ``close`` メソッドが呼び出されることが保証されます。 これにより、開発者の認知負荷が軽減され、コードが読みやすくなります。

.. There are two easy ways to implement this functionality yourself: using a class
.. or using a generator. Let's implement the above functionality ourselves, starting
.. with the class approach:

この機能を実装するには、クラスを使用する方法とジェネレータを使用する方法があります。 クラスのアプローチから始めて、上記の機能を自分で実装しましょう:

.. code-block:: python

    class CustomOpen(object):
        def __init__(self, filename):
          self.file = open(filename)

        def __enter__(self):
            return self.file

        def __exit__(self, ctx_type, ctx_value, ctx_traceback):
            self.file.close()

    with CustomOpen('file') as f:
        contents = f.read()

.. This is just a regular Python object with two extra methods that are used
.. by the ``with`` statement. CustomOpen is first instantiated and then its
.. ``__enter__`` method is called and whatever ``__enter__`` returns is assigned to
.. ``f`` in the ``as f`` part of the statement. When the contents of the ``with`` block
.. is finished executing, the ``__exit__`` method is then called.

これは単に ``with`` 文で使われる2つの余分なメソッドを持つ普通のPythonオブジェクトです。 CustomOpenが最初にインスタンス化され、 ``__enter__`` メソッドが呼び出され、 ``__enter__`` が返すものは、文の ``as`` 部分の ``f`` に代入されます。 ``with`` ブロックの内容の実行が終了すると、 ``__exit__`` メソッドが呼び出されます。

.. And now the generator approach using Python's own
.. `contextlib <https://docs.python.org/2/library/contextlib.html>`_:

そして今、Python独自の `contextlib <https://docs.python.org/2/library/contextlib.html>`_:

.. code-block:: python

    from contextlib import contextmanager

    @contextmanager
    def custom_open(filename):
        f = open(filename)
        try:
            yield f
        finally:
            f.close()

    with custom_open('file') as f:
        contents = f.read()

.. This works in exactly the same way as the class example above, albeit it's
.. more terse. The ``custom_open`` function executes until it reaches the ``yield``
.. statement. It then gives control back to the ``with`` statement, which assigns
.. whatever was ``yield``'ed to `f` in the ``as f`` portion. The ``finally`` clause
.. ensures that ``close()`` is called whether or not there was an exception inside
.. the ``with``.

これは上のクラスの例とまったく同じように動作しますが、それはもっと簡潔です。 ``custom_open`` 関数は、 ``yield`` ステートメントに達するまで実行されます。次に ``with`` 文に制御を戻し、 ``as`` 部分に ``f`` の ``yield`` を割り当てます。 ``finally`` 節は、 ``with`` の中に例外があったかどうかにかかわらず、 ``close()`` が呼び出されるようにします。

.. Since the two approaches appear the same, we should follow the Zen of Python
.. to decide when to use which. The class approach might be better if there's
.. a considerable amount of logic to encapsulate. The function approach
.. might be better for situations where we're dealing with a simple action.

2つのアプローチが同じように見えるので、PythonのZenに従っていつ使うべきかを決める必要があります。クラスのアプローチは、カプセル化するロジックが相当量ある場合には効果的です。ファンクションのアプローチは、単純なアクションを扱う場合には適しています。

.. Dynamic typing
.. --------------

動的タイピング
--------------

.. Python is dynamically typed, which means that variables do not have a fixed
.. type. In fact, in Python, variables are very different from what they are in
.. many other languages, specifically statically-typed languages. Variables are not
.. a segment of the computer's memory where some value is written, they are 'tags'
.. or 'names' pointing to objects. It is therefore possible for the variable 'a' to
.. be set to the value 1, then to the value 'a string', then to a function.

Pythonは動的に型付けされています。つまり、変数には固定型がありません。 実際、Pythonでは、変数は他の多くの言語、特に静的型の言語とは大きく異なります。 変数は、値が書き込まれるコンピュータのメモリのセグメントではなく、オブジェクトを指す「タグ」または「名前」です。 したがって、変数 'a'を値1に設定し、値 '文字列'に設定してから関数に設定することができます。

.. The dynamic typing of Python is often considered to be a weakness, and indeed
.. it can lead to complexities and hard-to-debug code. Something named 'a' can be
.. set to many different things, and the developer or the maintainer needs to track
.. this name in the code to make sure it has not been set to a completely unrelated
.. object.

Pythonの動的型付けはしばしば弱点とみなされ、実際には複雑で難しいコードにつながる可能性があります。 'a'という名前のものはさまざまなものに設定することができ、開発者や管理者は完全に無関係のオブジェクトに設定されていないことを確認するためにこの名前をコード内で追跡する必要があります。

.. Some guidelines help to avoid this issue:

この問題を回避するガイドラインがいくつかあります。

.. - Avoid using the same variable name for different things.

- 異なる変数に同じ変数名を使用しないでください。

.. **Bad**

**悪い**

.. code-block:: python

    a = 1
    a = 'a string'
    def a():
        pass  # Do something

.. **Good**

**良い**

.. code-block:: python

    count = 1
    msg = 'a string'
    def func():
        pass  # Do something

.. Using short functions or methods helps reduce the risk
.. of using the same name for two unrelated things.

短い関数やメソッドを使用すると、無関係な2つのものに対して同じ名前を使用するリスクを軽減できます。

.. It is better to use different names even for things that are related,
.. when they have a different type:

異なるタイプのものでも、関連するものであっても、異なる名前を使用する方が良いでしょう。

.. **Bad**

**悪い**

.. code-block:: python

    items = 'a b c d'  # This is a string...
    items = items.split(' ')  # ...becoming a list
    items = set(items)  # ...and then a set

.. There is no efficiency gain when reusing names: the assignments
.. will have to create new objects anyway. However, when the complexity
.. grows and each assignment is separated by other lines of code, including
.. 'if' branches and loops, it becomes harder to ascertain what a given
.. variable's type is.

名前を再利用すると効率は上がりません。割り当ては新しいオブジェクトを作成する必要があります。 しかし、複雑さが増し、それぞれの割り当てが 'if'ブランチやループを含む他のコード行で分かれている場合、与えられた変数の型が何であるかを確かめることは難しくなります。

.. Some coding practices, like functional programming, recommend never reassigning
.. a variable. In Java this is done with the `final` keyword. Python does not have
.. a `final` keyword and it would be against its philosophy anyway. However, it may
.. be a good discipline to avoid assigning to a variable more than once, and it
.. helps in grasping the concept of mutable and immutable types.

関数型プログラミングのように、変数を再割り当てすることを決して推奨していないコーディングもあります。 Javaでは、これは `final` キーワードで行います。 Pythonは `final` キーワードを持っておらず、とにかくその哲学に反するでしょう。しかし、変数に複数回代入するのを避けることは良い規律かもしれませんし、可変で不変な型の概念を理解するのに役立ちます。

.. Mutable and immutable types
.. ---------------------------

変更可能および変更不可能な型
----------------------------

.. Python has two kinds of built-in or user-defined types.

Pythonには、組み込み型とユーザー定義型の2種類があります。

.. Mutable types are those that allow in-place modification of the content. Typical
.. mutables are lists and dictionaries: All lists have mutating methods, like
.. :py:meth:`list.append` or :py:meth:`list.pop`, and can be modified in place.
.. The same goes for dictionaries.

変更可能なタイプは、コンテンツのインプレース変更を可能にするタイプです。 典型的な変数はリストと辞書です: 全てのリストには :py:meth: `list.append` や :py:meth:`list.pop` のようなメソッドの変更があります。 辞書についても同じことが言えます。

.. Immutable types provide no method for changing their content. For instance, the
.. variable x set to the integer 6 has no "increment" method. If you want to
.. compute x + 1, you have to create another integer and give it a name.

不変型は、内容を変更するためのメソッドを提供しません。 たとえば、変数xに整数6を設定すると、「インクリメント」メソッドはありません。 x + 1を計算する場合は、別の整数を作成して名前を付ける必要があります。

.. code-block:: python

    my_list = [1, 2, 3]
    my_list[0] = 4
    print my_list  # [4, 2, 3] <- The same list as changed

    x = 6
    x = x + 1  # The new x is another object

.. One consequence of this difference in behavior is that mutable
.. types are not "stable", and therefore cannot be used as dictionary
.. keys.

この動作の違いの1つの結果として、変更可能なタイプは「安定」ではないため、辞書キーとして使用することはできません。

.. Using properly mutable types for things that are mutable in nature
.. and immutable types for things that are fixed in nature
.. helps to clarify the intent of the code.

自然に変更可能なものに対しては適切に変更可能な型を使用し、性質上固定されているものに対しては変更不可能な型を使用すると、コードの意図を明確にするのに役立ちます。

.. For example, the immutable equivalent of a list is the tuple, created
.. with ``(1, 2)``. This tuple is a pair that cannot be changed in-place,
.. and can be used as a key for a dictionary.

例えば、リストの不変な等価物は ``(1, 2)`` で作られたタプルです。このタプルは、インプレースで変更できないペアであり、辞書のキーとして使用できます。

.. One peculiarity of Python that can surprise beginners is that
.. strings are immutable. This means that when constructing a string from
.. its parts, it is much more efficient to accumulate the parts in a list,
.. which is mutable, and then glue ('join') the parts together when the
.. full string is needed. One thing to notice, however, is that list
.. comprehensions are better and faster than constructing a list in a loop
.. with calls to ``append()``.

初心者を驚かせることができるPythonの特徴の1つは、文字列が不変であることです。 つまり、パーツから文字列を作成するときには、リスト内に変更可能なパーツを累積して、フルストリングが必要なときにパーツ同士を接着 ('join') する方がはるかに効率的です。 しかし、注意すべき点の1つは、リスト内包は、 ``append()`` を呼び出してループ内にリストを構築するよりも優れていて速いということです。

.. **Bad**

**悪い**

.. code-block:: python

    # create a concatenated string from 0 to 19 (e.g. "012..1819")
    nums = ""
    for n in range(20):
      nums += str(n)   # slow and inefficient
    print nums

.. **Good**

**良い**

.. code-block:: python

    # create a concatenated string from 0 to 19 (e.g. "012..1819")
    nums = []
    for n in range(20):
      nums.append(str(n))
    print "".join(nums)  # much more efficient

.. **Best**

**ベスト**

.. code-block:: python

    # create a concatenated string from 0 to 19 (e.g. "012..1819")
    nums = [str(n) for n in range(20)]
    print "".join(nums)

.. One final thing to mention about strings is that using ``join()`` is not always
.. best. In the instances where you are creating a new string from a pre-determined
.. number of strings, using the addition operator is actually faster, but in cases
.. like above or in cases where you are adding to an existing string, using
.. ``join()`` should be your preferred method.

文字列について言及する最後の1つは、 ``join()`` を使うことが必ずしも最良ではないということです。あらかじめ決められた数の文字列から新しい文字列を作成する場合は、加算演算子を使用するほうが高速ですが、上記のような場合や既存の文字列に追加する場合は ``join()`` があなたの好みの方法であるべきです。

.. code-block:: python

    foo = 'foo'
    bar = 'bar'

    foobar = foo + bar  # This is good
    foo += 'ooo'  # This is bad, instead you should do:
    foo = ''.join([foo, 'ooo'])

.. .. note::
..     You can also use the :ref:`% <python:string-formatting>` formatting operator
..     to concatenate a pre-determined number of strings besides :py:meth:`str.join`
..     and ``+``. However, :pep:`3101`, discourages the usage of the ``%`` operator
..     in favor of the :py:meth:`str.format` method.

.. note::
    また、 :ref:`％ <python:string-formatting>` フォーマット演算子を使って、:py:meth:`str.join` と ``+`` のほかにあらかじめ決められた数の文字列を連結することもできます。 しかし、:pep:`3101` は、:py:meth:`str.format` メソッドのために ``%`` 演算子の使用を奨励しています。

.. code-block:: python

    foo = 'foo'
    bar = 'bar'

    foobar = '%s%s' % (foo, bar) # It is OK
    foobar = '{0}{1}'.format(foo, bar) # It is better
    foobar = '{foo}{bar}'.format(foo=foo, bar=bar) # It is best


.. Vendorizing Dependencies
.. ------------------------

ベンダー依存の依存関係
----------------------


.. Runners
.. -------

ランナー
--------


.. Further Reading
.. ---------------

参考文献
--------

- http://docs.python.org/2/library/
- http://www.diveintopython.net/toc/index.html
