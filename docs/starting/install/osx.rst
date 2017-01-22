.. _install-osx:

.. Installing Python on Mac OS X
.. =============================

Mac OS X で Python をインストールする
====================================

.. note::
    :ref:`OS X 上に Python 3 をインストールするためのガイド<install3-osx>` を見てください。

.. The latest version of Mac OS X, Sierra, **comes with Python 2.7 out of the box**.

Mac OS X Sierra の最新バージョンには、**Python 2.7 が付属しています**。

.. You do not need to install or configure anything else to use Python. Having said
.. that, I would strongly recommend that you install the tools and libraries
.. described in the next section before you start building Python applications for
.. real-world use. In particular, you should always install Setuptools, as it makes
.. it much easier for you to install and manage other third-party Python libraries.

Python を使用するために何か他のものをインストールしたり設定したりする必要はありません。しかし、実際の使用のために Python アプリケーションを構築する前に、次のセクションで説明するツールとライブラリをインストールすることを強くお勧めします。特に、他のサードパーティの Python ライブラリをインストールして管理する方がはるかに簡単なので、Setuptools を常にインストールする必要があります。

.. The version of Python that ships with OS X is great for learning but it's not
.. good for development. The version shipped with OS X may be out of date from the
.. `official current Python release <https://www.python.org/downloads/mac-osx/>`_,
.. which is considered the stable production version.

OS X に同梱されている Python のバージョンは学習には最適ですが、開発には向いていません。 OS X に同梱されているバージョンは、安定したプロダクションバージョンとされている `現在の Python の公式リリース <https://www.python.org/downloads/mac-osx/>`_ から古くなっている可能性があります。

.. Doing it Right
.. --------------

正しい方法でやりましょう
-------------------

.. Let's install a real version of Python.

Python の実際のバージョンをインストールしましょう。

.. Before installing Python, you'll need to install a C compiler. The fastest way
.. is to install the Xcode Command Line Tools by running
.. ``xcode-select --install``. You can also download the full version of
.. `Xcode <http://developer.apple.com/xcode/>`_ from the Mac App Store, or the
.. minimal but unofficial
.. `OSX-GCC-Installer <https://github.com/kennethreitz/osx-gcc-installer#readme>`_
.. package.

Python をインストールする前に、Cコンパイラをインストールする必要があります。 最も速い方法は ``xcode-select --install`` を実行して Xcode コマンドラインツールをインストールすることです。 また、Mac App Store または非公式ですが `OSX-GCC-Installer <https://github.com/kennethreitz/osx-gcc-installer#readme>`_ パッケージから `Xcode <http://developer.apple.com/xcode/>`_ の完全版をダウンロードすることもできます。

.. note::
    すでに XCode がインストールされている場合は、OSX-GCC-Installer をインストールしないでください。ソフトウェアを組み合わせることで、診断が困難な問題を引き起こす可能性があります。

.. .. note::
..     If you already have XCode installed, do not install OSX-GCC-Installer.
..     In combination, the software can cause issues that are difficult to
..     diagnose.

.. note::
    XCode を新規インストールする場合は、ターミナルで ``xcode-select --install`` を実行してコマンドラインツールを追加する必要があります。

.. .. note::
..     If you perform a fresh install of XCode, you will also need to add the
..     commandline tools by running ``xcode-select --install`` on the terminal.


.. While OS X comes with a large number of UNIX utilities, those familiar with
.. Linux systems will notice one key component missing: a decent package manager.
.. `Homebrew <http://brew.sh>`_ fills this void.

OS X には多数の UNIX ユーティリティが付属していますが、Linux システムに精通している人は、欠けている1つの重要なコンポーネント、すなわちまともなパッケージマネージャに気付くでしょう。 `Homebrew <http://brew.sh>`_ がこの空白を埋めます。

.. To `install Homebrew <http://brew.sh/#install>`_, open :file:`Terminal` or
.. your favorite OSX terminal emulator and run

`Homebrew をインストールする <http://brew.sh/#install>`_ には :file:`Terminal` かお気に入りのOSX端末エミュレータを起動して実行してください。

.. code-block:: console

    $ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

.. The script will explain what changes it will make and prompt you before the
.. installation begins.
.. Once you've installed Homebrew, insert the Homebrew directory at the top
.. of your :envvar:`PATH` environment variable. You can do this by adding the following
.. line at the bottom of your :file:`~/.profile` file

スクリプトは、インストールの開始前にどのような変更が行われ、プロンプトを表示するかを説明します。 Homebrew をインストールした後、:envvar:`PATH` 環境変数の先頭に Homebrew ディレクトリを挿入します。これを行うには、:file:`~/.profile` ファイルの一番下に次の行を追加します。

.. code-block:: console

    export PATH=/usr/local/bin:/usr/local/sbin:$PATH

.. Now, we can install Python 2.7:

Python 2.7:

.. code-block:: console

    $ brew install python

.. or Python 3:

または Python 3 をインストールできます:

.. code-block:: console

    $ brew install python3

.. This will take a minute or two.

これには1〜2分かかります。


Setuptools & Pip
----------------

.. Homebrew installs Setuptools and ``pip`` for you.

HomebrewはあなたのためにSetuptoolsと ``pip`` をインストールします。

.. Setuptools enables you to download and install any compliant Python
.. software over a network (usually the Internet) with a single command
.. (``easy_install``). It also enables you to add this network installation
.. capability to your own Python software with very little work.

Setuptools を使うと、単一のコマンド(``easy_install``)を使って、ネットワーク(通常はインターネット)上で互換性のある Python ソフトウェアをダウンロードしてインストールすることができます。 また、このネットワークインストール機能をごくわずかな作業で独自の Python ソフトウェアに追加することもできます。

.. ``pip`` is a tool for easily installing and managing Python packages,
.. that is recommended over ``easy_install``. It is superior to ``easy_install``
.. in `several ways <https://python-packaging-user-guide.readthedocs.io/pip_easy_install/#pip-vs-easy-install>`_,
.. and is actively maintained.

``pip`` は簡単に Python パッケージをインストールして管理するためのツールです。これは ``easy_install`` よりもお勧めです。 これは `多方面において <https://python-packaging-user-guide.readthedocs.io/pip_easy_install/#pip-vs-easy-install>`_ 、``easy_install`` より優れており、積極的に維持されています。


.. Virtual Environments
.. --------------------

仮想環境
--------

.. A Virtual Environment (commonly referred to as a 'virtualenv') is a tool to keep the dependencies required by different projects
.. in separate places, by creating virtual Python environments for them. It solves the
.. "Project X depends on version 1.x but, Project Y needs 4.x" dilemma, and keeps
.. your global site-packages directory clean and manageable.

仮想環境（一般に 'virtualenv' と呼ばれます）は、異なるプロジェクトが必要とする依存関係を別々の場所に保存するためのツールです。 「Project Xはバージョン1.xに依存しますが、Project Yは4.xが必要です」というジレンマを解決し、グローバルなサイトパッケージディレクトリをきれいに管理します。

.. For example, you can work on a project which requires Django 1.10 while also
.. maintaining a project which requires Django 1.8.

例えば、Django 1.10を必要とするプロジェクトで作業し、Django 1.8を必要とするプロジェクトを維持することもできます。

.. To start using this and see more information: :ref:`Virtual Environments <virtualenvironments-ref>` docs.

詳しくはこちらを参照: :ref:`Virtual Environments <virtualenvironments-ref>` docs。

--------------------------------

.. This page is a remixed version of `another guide <http://www.stuartellis.eu/articles/python-development-windows/>`_,
.. which is available under the same license.

このページは、`別のガイド <http://www.stuartellis.eu/articles/python-development-windows/>`_ のリミックス版です。これは、同じライセンスで入手できます。
