.. Your Development Environment
.. ============================

あなたの開発環境
================

.. Text Editors
.. ::::::::::::

テキストエディタ
::::::::::::::::

.. Just about anything that can edit plain text will work for writing Python code,
.. however, using a more powerful editor may make your life a bit easier.

プレーンテキストを編集できるものは、Pythonコードを書くためにはうまくいくでしょう。
しかし、より強力なエディタを使用すると、あなたの人生は少し楽になるかもしれません。

Vim
---

.. Vim is a text editor which uses keyboard shortcuts for editing instead of menus
.. or icons. There are a couple of plugins and settings for the Vim editor to
.. aid Python development. If you only develop in Python, a good start is to set
.. the default settings for indentation and line-wrapping to values compliant with
.. :pep:`8`. In your home directory, open a file called :file:`.vimrc` and add the
.. following lines::

Vimは、メニューやアイコンの代わりにキーボードショートカットを使用するテキストエディタです。
Vimエディタには、Python開発を支援するためのいくつかのプラグインと設定があります。
Pythonでのみ開発する場合は、インデントと改行のデフォルト設定を :pep:`8` に準拠した値に設定するのがよいでしょう。あなたのホームディレクトリで、 :file:`.vimrc` というファイルを開き、
次の行::

    set textwidth=79  " lines longer than 79 columns will be broken
    set shiftwidth=4  " operation >> indents 4 columns; << unindents 4 columns
    set tabstop=4     " a hard TAB displays as 4 columns
    set expandtab     " insert spaces when hitting TABs
    set softtabstop=4 " insert/delete 4 spaces when hitting a TAB/BACKSPACE
    set shiftround    " round indent to multiple of 'shiftwidth'
    set autoindent    " align the new line indent with the previous line

.. With these settings, newlines are inserted after 79 characters and indentation
.. is set to 4 spaces per tab. If you also use Vim for other languages, there is a
.. handy plugin called indent_, which handles indentation settings for Python
.. source files.

これらの設定では、改行は79文字の後に挿入され、インデントはタブごとに4スペースに設定されます。
Vimを他の言語にも使用している場合は、indent_ という便利なプラグインがあります。
これはPythonソースファイルのインデント設定を処理します。

.. There is also a handy syntax plugin called syntax_ featuring some improvements
.. over the syntax file included in Vim 6.1.

syntax_ という便利な構文プラグインもあります。
これは、Vim 6.1に含まれている構文ファイルの改良点です。

.. These plugins supply you with a basic environment for developing in Python.
.. To get the most out of Vim, you should continually check your code for syntax
.. errors and PEP8 compliance. Luckily PEP8_ and Pyflakes_ will do this for you.
.. If your Vim is compiled with :option:`+python` you can also utilize some very
.. handy plugins to do these checks from within the editor.

これらのプラグインは、Pythonで開発するための基本的な環境を提供します。
Vimを最大限に活用するには、コードの構文エラーとPEP8準拠を継続的に確認する必要があります。
幸いにも PEP8_ と Pyflakes_ があなたのためにこれを行います。
あなたのVimが :option:`+python` でコンパイルされている場合は、非常に便利なプラグインを利用してエディタ内からこれらのチェックを行うこともできます。

.. For PEP8 checking and pyflakes, you can install vim-flake8_. Now you can map the
.. function ``Flake8`` to any hotkey or action you want in Vim. The plugin will
.. display errors at the bottom of the screen, and provide an easy way to jump to
.. the corresponding line. It's very handy to call this function whenever you save
.. a file. In order to do this, add the following line to your
.. :file:`.vimrc`::

PEP8チェックとpyflakesの場合、vim-flake8_ をインストールすることができます。
これでVimに必要なホットキーやアクションに ``Flake8`` 関数をマップすることができます。
プラグインは画面の下部にエラーを表示し、対応する行にジャンプする簡単な方法を提供します。
ファイルを保存するたびにこの関数を呼び出すのは非常に便利です。
これを行うには、次の行をファイルに追加します
:file:`.vimrc`::

    autocmd BufWritePost *.py call Flake8()

.. If you are already using syntastic_, you can set it to run Pyflakes on write
.. and show errors and warnings in the quickfix window. An example configuration
.. to do that which also shows status and warning messages in the statusbar would
.. be::

syntastic_ を既に使用している場合は、書き込み時にPyflakesを実行し、クイックフィックスウィンドウでエラーと警告を表示するように設定できます。
ステータスバーにステータスと警告メッセージを表示する設定例は、次のとおりです::

    set statusline+=%#warningmsg#
    set statusline+=%{SyntasticStatuslineFlag()}
    set statusline+=%*
    let g:syntastic_auto_loc_list=1
    let g:syntastic_loc_list_height=5


.. Python-mode
.. ^^^^^^^^^^^

Pythonモード
^^^^^^^^^^^^

.. Python-mode_ is a complex solution for working with Python code in Vim.
.. It has:

Python-mode_ は、VimでPythonコードを操作するための複雑なソリューションです。
それは：

.. - Asynchronous Python code checking (``pylint``, ``pyflakes``, ``pep8``, ``mccabe``) in any combination
.. - Code refactoring and autocompletion with Rope
.. - Fast Python folding
.. - Virtualenv support
.. - Search through Python documentation and run Python code
.. - Auto PEP8_ error fixes

- 任意の組み合わせの非同期Pythonコード検査 (``pylint``、``pyflakes``、``pep8``、``mccabe``)
- Rope によるコードリファクタリングとオートコンプリート
- 高速Python折りたたみ
- Virtualenvのサポート
- Pythonのドキュメントを検索し、Pythonコードを実行する
- 自動PEP8_ のエラー修正

.. And more.

そしてさらに。

.. SuperTab
.. ^^^^^^^^

SuperTab
^^^^^^^^

.. SuperTab_ is a small Vim plugin that makes code completion more convenient by
.. using ``<Tab>`` key or any other customized keys.

SuperTab_ は、``<Tab>`` キーや他のカスタマイズされたキーを使って、コード補完をより便利にする小さなVimプラグインです。

.. _indent: http://www.vim.org/scripts/script.php?script_id=974
.. _syntax: http://www.vim.org/scripts/script.php?script_id=790
.. _Pyflakes: http://pypi.python.org/pypi/pyflakes/
.. _PEP8: http://pypi.python.org/pypi/pep8/
.. _syntastic: https://github.com/scrooloose/syntastic
.. _Python-mode: https://github.com/klen/python-mode
.. _SuperTab: http://www.vim.org/scripts/script.php?script_id=1643
.. _vim-flake8: https://github.com/nvie/vim-flake8

Emacs
-----

.. Emacs is another powerful text editor. It is fully programmable (lisp), but
.. it can be some work to wire up correctly. A good start if you're already an
.. Emacs user is `Python Programming in Emacs`_ at EmacsWiki.

Emacsはもう一つの強力なテキストエディタです。
それは完全にプログラム可能（lisp）ですが、それは正しくワイヤリングするいくつかの仕事かもしれません。
既にEmacsのユーザであれば、EmacsWikiの `Python Programming in Emacs`_ が良いスタートです。

.. 1. Emacs itself comes with a Python mode.

1. Emacs自体にはPythonモードがあります。

.. _Python Programming in Emacs: http://emacswiki.org/emacs/PythonProgrammingInEmacs

TextMate
--------

..     `TextMate <http://macromates.com/>`_ brings Apple's approach to operating
..     systems into the world of text editors. By bridging UNIX underpinnings and
..     GUI, TextMate cherry-picks the best of both worlds to the benefit of expert
..     scripters and novice users alike.

`TextMate <http://macromates.com/>`_ は、オペレーティングシステムに対するAppleのアプローチをテキストエディタの世界にもたらします。
UNIXの基盤とGUIを橋渡しすることにより、TextMateは熟練したスクリプタや初心者ユーザの利益のために、両方の世界のベストをチェリーピックアップします。

Sublime Text
------------

..     `Sublime Text <http://www.sublimetext.com/>`_ is a sophisticated text
..     editor for code, markup and prose. You'll love the slick user interface,
..     extraordinary features and amazing performance.

`Sublime Text <http://www.sublimetext.com/>`_ は、コード、マークアップ、散文の洗練されたテキストエディタです。
すっきりとしたユーザーインターフェイス、優れた機能、素晴らしいパフォーマンスが大好きです。

.. Sublime Text has excellent support for editing Python code and uses Python for
.. its plugin API. It also has a diverse variety of plugins,
.. `some of which <https://github.com/SublimeLinter/SublimeLinter>`_ allow for
.. in-editor PEP8 checking and code "linting".

Sublime Textは、Pythonコードの編集をサポートしており、PythonをプラグインAPIとして使用しています。
また、様々な種類のプラグインがあります。`その中には <https://github.com/SublimeLinter/SublimeLinter>`_ 、エディタ内のPEP8チェックとコード "linting" があります。

Atom
----

..     `Atom <https://atom.io/>`_ is a hackable text editor for the 21st century,
..     built on atom-shell, and based on everything we love about our favorite
..     editors.

`Atom <https://atom.io/>`_ は、atom-shell上に基づく21世紀のハック可能なテキストエディタであり、私たちがお気に入りのエディタについて愛するすべてのものに基づいています。

.. Atom is web native (HTML, CSS, JS), focusing on modular design and easy plugin
.. development. It comes with native package control and plethora of packages.
.. Recommended for Python development is
.. `Linter <https://github.com/AtomLinter/Linter>`_ combined with
.. `linter-flake8 <https://github.com/AtomLinter/linter-flake8>`_.

AtomはWebネイティブ（HTML、CSS、JS）で、モジュール設計と簡単なプラグイン開発に重点を置いています。
ネイティブのパッケージ制御と多数のパッケージが付属しています。
Pythonの開発には、`Linter <https://github.com/AtomLinter/Linter>`_ と
`linter-flake8 <https://github.com/AtomLinter/linter-flake8>`_ の組み合わせを推奨します。

IDEs
::::

PyCharm / IntelliJ IDEA
-----------------------

.. `PyCharm <http://www.jetbrains.com/pycharm/>`_ is developed by JetBrains, also
.. known for IntelliJ IDEA. Both share the same code base and most of PyCharm's
.. features can be brought to IntelliJ with the free
.. `Python Plug-In <https://plugins.jetbrains.com/plugin/?idea&pluginId=631>`_.  There are two
.. versions of PyCharm: Professional Edition (Free 30-day trial) and Community
.. Edition (Apache 2.0 License) with fewer features.

`PyCharm <http://www.jetbrains.com/pycharm/>`_ はJetBrainsによって開発されたもので、IntelliJ IDEAでも知られています。
`Python Plug-In <https://plugins.jetbrains.com/plugin/?idea&pluginId=631>`_ を使用して、Pythonプラグインと同じコードベースを共有し、PyCharmの機能のほとんどをIntelliJにもたらすことができます。
PyCharmには、プロフェッショナル版（30日間無料体験版）とコミュニティ版（Apache 2.0ライセンス）の2つのバージョンがあります。

Python (on Visual Studio Code)
-----------------------------

.. `Python for Visual Studio <https://marketplace.visualstudio.com/items?itemName=donjayamanne.python>`_ is an extension for the `Visual Studio Code IDE <https://code.visualstudio.com>`_.
.. This is a free, light weight, open source IDE, with support for Mac, Windows, and Linux.
.. Built using open source technologies such as Node.js and Python, with compelling features such as Intellisense (autocompletion), local and remote debugging, linting, and the like.

`Python for Visual Studio <https://marketplace.visualstudio.com/items?itemName=donjayamanne.python>`_ は、 `Visual Studio Code IDE <https://code.visualstudio.com>`_ の拡張です。
これはMac、Windows、Linuxをサポートする、無料の軽量オープンソースIDEです。
Node.jsやPythonなどのオープンソース技術を使用して構築され、Intellisense（オートコンプリート）、ローカルとリモートのデバッグ、lintingなどの魅力的な機能を備えています。

MIT licensed.

Enthought Canopy
----------------
.. `Enthought Canopy <https://www.enthought.com/products/canopy/>`_ is a Python
.. IDE which is focused towards Scientists and Engineers as it provides pre 
.. installed libraries for data analysis. 

`Enthought Canopy <https://www.enthought.com/products/canopy/>`_ は科学者とエンジニアに
焦点を当てたデータ分析のためのライブラリがインストールされている Python IDE です。

Eclipse
-------

.. The most popular Eclipse plugin for Python development is Aptana's
.. `PyDev <http://pydev.org>`_.

Python開発のための最も一般的なEclipseプラグインはAptanaの `PyDev <http://pydev.org>`_ です。

Komodo IDE
----------

.. `Komodo IDE <http://www.activestate.com/komodo-ide>`_ is developed by
.. ActiveState and is a commercial IDE for Windows, Mac, and Linux.
.. `KomodoEdit <https://github.com/Komodo/KomodoEdit>`_ is the open source
.. alternative.

`Komodo IDE <http://www.activestate.com/komodo-ide>`_ はActiveStateによって開発され、
Windows、Mac、Linux用の商用IDEです。
`KomodoEdit <https://github.com/Komodo/KomodoEdit>`_ はオープンソースの代替手段です。

Spyder
------

.. `Spyder <https://github.com/spyder-ide/spyder>`_ is an IDE specifically geared
.. toward working with scientific Python libraries (namely
.. `Scipy <http://www.scipy.org/>`_). It includes integration with pyflakes_,
.. `pylint <http://www.logilab.org/857>`_ and
.. `rope <https://github.com/python-rope/rope>`_.

`Spyder <https://github.com/spyder-ide/spyder>`_ は、特に科学的なPythonライブラリ（すなわち、 `Scipy <http://www.scipy.org/>`_ ）を扱うためのIDEです。 pyflakes_、`pylint <http://www.logilab.org/857>`_ と `rope <https://github.com/python-rope/rope>`_ との統合も含まれています。 

.. Spyder is open-source (free), offers code completion, syntax highlighting,
.. a class and function browser, and object inspection.

Spyderはオープンソース（無料）で、コード補完、構文強調表示、クラスと機能のブラウザー、オブジェクト検査を提供します。


WingIDE
-------

.. `WingIDE <http://wingware.com/>`_ is a Python specific IDE. It runs on Linux,
.. Windows and Mac (as an X11 application, which frustrates some Mac users).

`WingIDE <http://wingware.com/>`_ はPython固有のIDEです。 これは、Linux、Windows、Macで動作します（X11アプリケーションとして、一部のMacユーザーを苛立たせます）。

.. WingIDE offers code completion, syntax highlighting, source browser, graphical
.. debugger and support for version control systems.

WingIDEは、コード補完、構文強調表示、ソースブラウザ、グラフィカルデバッガ、バージョン管理システムのサポートを提供します。


NINJA-IDE
---------

.. `NINJA-IDE <http://www.ninja-ide.org/>`_ (from the recursive acronym: "Ninja-IDE
.. Is Not Just Another IDE") is a cross-platform IDE, specially designed to build
.. Python applications, and runs on Linux/X11, Mac OS X and Windows desktop
.. operating systems. Installers for these platforms can be downloaded from the
.. website.

`NINJA-IDE <http://www.ninja-ide.org/>`_ (再帰的頭字語: "Ninja-IDEは単なる別のIDEではない")はクロスプラットフォームのIDEで、Pythonアプリケーションを構築するために特別に設計されています Linux / X11、Mac OS X、Windowsデスクトップオペレーティングシステムで動作します。 これらのプラットフォームのインストーラは、Webサイトからダウンロードできます。

.. NINJA-IDE is open-source software (GPLv3 licence) and is developed
.. in Python and Qt. The source files can be downloaded from
.. `GitHub <https://github.com/ninja-ide>`_.

NINJA-IDEはオープンソースのソフトウェア（GPLv3ライセンス）で、PythonとQtで開発されています。 ソースファイルは `GitHub <https://github.com/ninja-ide>`_ からダウンロードできます。


Eric (The Eric Python IDE)
--------------------------

.. `Eric <http://eric-ide.python-projects.org/>`_ is a full featured Python IDE
.. offering sourcecode autocompletion, syntax highlighting, support for version
.. control systems, python 3 support, integrated web browser, python shell,
.. integrated debugger and a flexible plug-in system. Written in python, it is
.. based on the Qt gui toolkit, integrating the Scintilla editor control. Eric
.. is an open-source software project (GPLv3 licence) with more than ten years of
.. active development.

`Eric <http://eric-ide.python-projects.org/>`_ は、ソースコードの自動補完、構文強調表示、バージョン管理システムのサポート、Python 3のサポート、統合されたWebブラウザ、Pythonシェル、 統合されたデバッガと柔軟なプラグインシステムを提供します。 Pythonで書かれていますが、Qt guiツールキットに基づいており、Scintillaエディタコントロールを統合しています。 エリックは、オープンソースのソフトウェアプロジェクト（GPLv3ライセンス）であり、10年以上の積極的な開発を行っています。


.. Interpreter Tools
.. :::::::::::::::::

インタプリタツール
::::::::::::::::::


.. Virtual Environments
.. --------------------

仮想環境
--------

.. Virtual Environments provide a powerful way to isolate project package dependencies. This means that you can use packages particular to a Python project without installing them system wide and thus avoiding potential version conflicts.
仮想環境は、プロジェクトパッケージの依存関係を分離する強力な方法を提供します。 つまり、Pythonプロジェクトに特有のパッケージをシステム全体にインストールせずに、バージョン間の競合を避けることができます。

.. To start using and see more information:
.. `Virtual Environments <http://github.com/kennethreitz/python-guide/blob/master/docs/dev/virtualenvs.rst>`_ docs.

使用を開始し、詳細情報を参照するには:
`仮想環境 <http://github.com/kennethreitz/python-guide/blob/master/docs/dev/virtualenvs.rst>`_ docs。


pyenv
-----

.. `pyenv <https://github.com/yyuu/pyenv>`_ is a tool to allow multiple versions
.. of the Python interpreter to be installed at the same time.  This solves the
.. problem of having different projects requiring different versions of Python.
.. For example, it becomes very easy to install Python 2.7 for compatibility in
.. one project, whilst still using Python 3.4 as the default interpreter.
.. pyenv isn't just limited to the CPython versions - it will also install PyPy,
.. anaconda, miniconda, stackless, jython, and ironpython interpreters.

`pyenv <https://github.com/yyuu/pyenv>`_ は複数のバージョンのPythonインタプリタを同時にインストールできるようにするためのツールです。 これにより、Pythonの異なるバージョンを必要とする異なるプロジェクトを持つという問題が解決されます。 たとえば、Python 3.4をデフォルトインタープリタとして使用しながら、あるプロジェクトでPython 2.7を互換性のためにインストールするのは非常に簡単です。 pyenvはCPythonのバージョンだけではなく、PyPy、anaconda、miniconda、stackless、jython、およびironpythonインタープリタもインストールします。

.. pyenv works by filling a ``shims`` directory with fake versions of the Python
.. interpreter (plus other tools like ``pip`` and ``2to3``).  When the system
.. looks for a program named ``python``, it looks inside the ``shims`` directory
.. first, and uses the fake version, which in turn passes the command on to
.. pyenv.  pyenv then works out which version of Python should be run based on
.. environment variables, ``.python-version`` files, and the global default.

pyenvは ``shims`` ディレクトリにPythonインタプリタの偽のバージョン (``pip`` や ``2to3 ``などの他のツール) を埋め込むことで動作します。 システムが ``python`` という名前のプログラムを探すと、最初に ``shims`` ディレクトリ内を調べ、偽のバージョンを使用してコマンドをpyenvに渡します。 pyenvは、環境変数、 ``.python-version`` ファイル、およびグローバルデフォルトに基づいてどのバージョンのPythonを実行するかを決定します。

.. pyenv isn't a tool for managing virtual environments, but there is the plugin
.. `pyenv-virtualenv <https://github.com/yyuu/pyenv-virtualenv>`_ which automates
.. the creation of different environments, and also makes it possible to use the
.. existing pyenv tools to switch to different environments based on environment
.. variables or ``.python-version`` files.

pyenvは仮想環境を管理するツールではありませんが、さまざまな環境の作成を自動化する `pyenv-virtualenv <https://github.com/yyuu/pyenv-virtualenv>`_ プラグインがあります。 既存のpyenvツールを使用して、環境変数や ``.python-version`` ファイルに基づいて異なる環境に切り替えることができます。

Other Tools
:::::::::::

IDLE
----

.. :ref:`IDLE <python:idle>` is an integrated development environment that is
.. part of Python standard library. It is completely written in Python and uses
.. the Tkinter GUI toolkit. Though IDLE is not suited for full-blown development
.. using Python, it is quite helpful to try out small Python snippets and
.. experiment with different features in Python.

:ref:`IDLE <python：idle>` は、Python標準ライブラリの一部である統合開発環境です。 これはPythonで完全に書かれており、Tkinter GUIツールキットを使用しています。 IDLEはPythonを使った本格的な開発には適していませんが、小さなPythonスニペットを試してみて、Pythonのさまざまな機能を試してみることは非常に役に立ちます。

.. It provides the following features:

以下の機能を提供します。

.. * Python Shell Window (interpreter)
.. * Multi window text editor that colorizes Python code
.. * Minimal debugging facility

* Pythonシェルウィンドウ（インタプリタ）
* Pythonコードを着色するマルチウィンドウテキストエディタ
* 最小限のデバッグ機能


IPython
-------

.. `IPython <http://ipython.org/>`_ provides a rich toolkit to help you make the
.. most out of using Python interactively. Its main components are:

`IPython <http://ipython.org/>`_ は、Pythonをインタラクティブに使いこなすための豊富なツールキットを提供します。 主なコンポーネントは次のとおりです。

.. * Powerful Python shells (terminal- and Qt-based).
.. * A web-based notebook with the same core features but support for rich media,
..   text, code, mathematical expressions and inline plots.
.. * Support for interactive data visualization and use of GUI toolkits.
.. * Flexible, embeddable interpreters to load into your own projects.
.. * Tools for high level and interactive parallel computing.

* 強力なPythonシェル（ターミナルおよびQtベース）。
* 同じコア機能を持ちながら、リッチメディア、テキスト、コード、数式、インラインプロットをサポートする
  ウェブベースのノートブック。インタラクティブなデータの視覚化とGUIツールキットの使用をサポートします。
* 柔軟で埋め込み可能な通訳者が自分のプロジェクトに読み込むことができます。
* 高水準のインタラクティブな並列コンピューティングのためのツール。

.. code-block:: console

    $ pip install ipython

.. To download and install IPython with all it's optional dependencies for the notebook, qtconsole, tests, and other functionalities

IPythonをダウンロードしてインストールするには、ノートブック、qtconsole、テスト、その他の機能のオプションの依存関係が必要です

.. code-block:: console

    $ pip install ipython[all]

BPython
-------

.. `bpython <http://bpython-interpreter.org/>`_ is an alternative interface to the
.. Python interpreter for Unix-like operating systems. It has the following
.. features:

`bpython <http://bpython-interpreter.org/>`_ はUnixライクなオペレーティングシステム用のPythonインタプリタの代替インタフェースです。 それは以下の特徴を有する：

.. * In-line syntax highlighting.
.. * Readline-like autocomplete with suggestions displayed as you type.
.. * Expected parameter list for any Python function.
.. * "Rewind" function to pop the last line of code from memory and re-evaluate.
.. * Send entered code off to a pastebin.
.. * Save entered code to a file.
.. * Auto-indentation.
.. * Python 3 support.

* インライン構文の強調表示。
* 入力時に提案が表示された、読み込みのようなオートコンプリート。
* 任意のPython関数の期待されるパラメータリスト。
* メモリから最後のコード行をポップして再評価する「巻き戻し」機能。
* 入力したコードをペーストビンに送ります。
* 入力したコードをファイルに保存します。
* 自動インデント。
* Python 3のサポート。

.. code-block:: console

    $ pip install bpython

ptpython
--------

.. `ptpython <https://github.com/jonathanslenders/ptpython/>`_ is a REPL build
.. on top of the `prompt_toolkit <http://github.com/jonathanslenders/python-prompt-toolkit>`_
.. library. It is considered to be an alternative to BPython_. Features include:

`ptpython <https://github.com/jonathanslenders/ptpython/>`_ は、 `prompt_toolkit <http://github.com/jonathanslenders/python-prompt-toolkit>`_ ライブラリの上にあるREPLビルドです。 これはBPython_ の代わりと考えられています。 機能は次のとおりです。

.. * Syntax highlighting
.. * Autocompletion
.. * Multiline editing
.. * Emacs and VIM Mode
.. * Embedding REPL inside of your code
.. * Syntax Validation
.. * Tab pages
.. * Support for integrating with IPython_'s shell, by installing IPython
..   ``pip install ipython`` and running ``ptipython``.

* シンタックスハイライト
* オートコンプリート
* マルチライン編集
* EmacsとVIMモード
* あなたのコードの中にREPLを埋め込む
* 構文の検証
* タブページ
IPythonをインストールすることで、IPython_ のシェルとの統合をサポートします。
   ``pip install ipython`` と ``ptipython`` を実行します。

.. code-block:: console

    $ pip install ptpython
