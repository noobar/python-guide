.. _install3-osx:

.. Installing Python 3 on Mac OS X
.. ================================

Mac OS XでのPython 3のインストール
==================================

.. The latest version of Mac OS X, Sierra, **comes with Python 2.7 out of the box**.

Mac OS X、Sierraの最新バージョンには、**Python 2.7が付属しています**。

.. You do not need to install or configure anything else to use Python 2. These
.. instructions document the installation of Python 3.

Python 2を使用するために何か他のものをインストールしたり設定したりする必要はありません。これらの手順は、Python 3のインストールを文書化しています。

.. The version of Python that ships with OS X is great for learning but it's not
.. good for development. The version shipped with OS X may be out of date from the
.. `official current Python release <https://www.python.org/downloads/mac-osx/>`_,
.. which is considered the stable production version.

OS Xに同梱されているPythonのバージョンは学習には最適ですが、開発には向いていません。 OS Xに同梱されているバージョンは、安定したプロダクションバージョンとみなされている `現在のPythonの公式リリース <https://www.python.org/downloads/mac-osx/>`_ から古くなっている可能性があります。

.. Doing it Right
.. --------------

そうすること
------------

.. Let's install a real version of Python.

Pythonの実際のバージョンをインストールしましょう。

.. Before installing Python, you'll need to install GCC. GCC can be obtained
.. by downloading `XCode <http://developer.apple.com/xcode/>`_, the smaller
.. `Command Line Tools <https://developer.apple.com/downloads/>`_ (must have an
.. Apple account) or the even smaller `OSX-GCC-Installer <https://github.com/kennethreitz/osx-gcc-installer#readme>`_
.. package.

Pythonをインストールする前に、GCCをインストールする必要があります。 GCCは `XCode <http://developer.apple.com/xcode/>`_、より小さな `コマンドラインツール <https://developer.apple.com/downloads/>`_ をダウンロードすることで得ることができます Appleのアカウント）、さらにはより小さい `OSX-GCC-Installer <https://github.com/kennethreitz/osx-gcc-installer#readme>`_ パッケージをインストールしてください。

.. note::
    すでにXCodeがインストールされている場合は、OSX-GCC-Installerをインストールしないでください。 ソフトウェアを組み合わせることで、診断が困難な問題を引き起こす可能性があります。

.. .. note::
..     If you already have XCode installed, do not install OSX-GCC-Installer.
..     In combination, the software can cause issues that are difficult to
..     diagnose.

.. note::
    XCodeを新規インストールする場合は、ターミナルで ``xcode-select --install`` を実行してコマンドラインツールを追加する必要があります。

.. .. note::
..     If you perform a fresh install of XCode, you will also need to add the
..     commandline tools by running ``xcode-select --install`` on the terminal.

.. While OS X comes with a large number of UNIX utilities, those familiar with
.. Linux systems will notice one key component missing: a package manager.
.. `Homebrew <http://brew.sh>`_ fills this void.

OS Xには多数のUNIXユーティリティが付属していますが、Linuxシステムに精通している人なら、欠けている重要なコンポーネントの1つ、パッケージマネージャーに気付くでしょう。 `Homebrew <http://brew.sh>`_ がこの空白を埋める。

.. To `install Homebrew <http://brew.sh/#install>`_, open :file:`Terminal` or
.. your favorite OSX terminal emulator and run

`Homebrew <http://brew.sh/#install>`_ をインストールするには :file:`Terminal` かお気に入りのOSX端末エミュレータを起動して実行してください

.. code-block:: console

    $ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

.. The script will explain what changes it will make and prompt you before the
.. installation begins.
.. Once you've installed Homebrew, insert the Homebrew directory at the top
.. of your :envvar:`PATH` environment variable. You can do this by adding the following
.. line at the bottom of your :file:`~/.profile` file

スクリプトは、インストールの開始前にどのような変更が行われ、プロンプトを表示するかを説明します。 Homebrewをインストールした後、:envvar:`PATH` 環境変数の先頭にHomebrewディレクトリを挿入します。 これを行うには、:file:`~/.profile` ファイルの一番下に次の行を追加します

.. code-block:: console

    export PATH=/usr/local/bin:/usr/local/sbin:$PATH

.. Now, we can install Python 3:

今、Python 3をインストールすることができます:

.. code-block:: console

    $ brew install python3

.. This will take a minute or two.

これには1〜2分かかります。


Pip
---

.. Homebrew installs ``pip3`` for you.

Homebrewはあなたのために ``pip3`` をインストールします。

.. ``pip3`` is the alias for the Python 3 version of ``pip`` on systems with both
.. the Homebrew'd Python 2 and 3 installed.

``pip3`` は、HomebrewのPython 2とPython 3の両方がインストールされているシステム上の ``pip`` のPython 3バージョンのエイリアスです。

.. Working with Python 3
.. ---------------------

Python 3を使って作業する
------------------------

.. At this point, you have the system Python 2.7 available, potentially the
.. :ref:`Homebrew version of Python 2 <install-osx>` installed, and the Homebrew
.. version of Python 3 as well.

この時点で、システムPython 2.7が利用可能になりました。潜在的に :ref:`HomebrewバージョンのPython 2 <install-osx>` がインストールされていて、HomebrewバージョンのPython 3もあります。

.. code-block:: console

    $ python

.. will launch the Python 2 interpreter.

Python 2インタプリタを起動します。

.. code-block:: console

    $ python3

.. will launch the Python 3 interpreter

Python 3インタプリタを起動する

.. ``pip3`` and ``pip`` will both be available.  If the Homebrew version of Python
.. 2 is not installed, they will be the same.  If the Homebrew version of Python 2
.. is installed then ``pip`` will point to Python 2 and ``pip3`` will point to
.. Python 3.

``pip3`` と ``pip`` の両方が利用可能になります。 Homebrew版のPython 2がインストールされていない場合、それらは同じになります。 Homebrew版のPython 2がインストールされている場合、 ``pip`` はPython 2を指し、 ``pip3`` はPython 3を指します。


.. Virtual Environments
.. --------------------

仮想環境
--------

.. A Virtual Environment (commonly referred to as a 'virtualenv') is a tool to keep
.. the dependencies required by different projects in separate places, by creating
.. virtual Python environments for them. It solves the "Project X depends on
.. version 1.x but, Project Y needs 4.x" dilemma, and keeps your global
.. site-packages directory clean and manageable.

仮想環境（一般に 'virtualenv'と呼ばれる）は、異なるプロジェクトが必要とする依存関係を別々の場所に保存するためのツールです。 「Project Xはバージョン1.xに依存しますが、Project Yは4.xが必要です」というジレンマを解決し、グローバルなサイトパッケージディレクトリをきれいに管理します。

.. For example, you can work on a project which requires Django 1.10 while also
.. maintaining a project which requires Django 1.8.

例えば、Django 1.10を必要とするプロジェクトで作業し、Django 1.8を必要とするプロジェクトを維持することもできます。

.. To start using this and see more information: :ref:`Virtual Environments <virtualenvironments-ref>` docs.

これを使い始め、さらに詳しい情報を参照する :ref:`Virtual Environments <virtualenvironments-ref>` docs。

--------------------------------

.. This page is a remixed version of `another guide <http://www.stuartellis.eu/articles/python-development-windows/>`_,
.. which is available under the same license.

このページは、`別のガイド <http://www.stuartellis.eu/articles/python-development-windows/>`_ のリミックス版です。これは、同じライセンスで入手できます。
