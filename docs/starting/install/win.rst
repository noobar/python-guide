.. _install-windows:

.. Installing Python on Windows
.. ============================

WindowsでのPythonのインストール
===============================

.. First, download the `latest version <https://www.python.org/ftp/python/2.7.12/python-2.7.12.msi>`_
.. of Python 2.7 from the official Website. If you want to be sure you are installing a fully
.. up-to-date version, click the Downloads > Windows link from the home page of the
.. `Python.org web site <http://python.org>`_ .

まず、`Python 2.7の最新バージョン <https://www.python.org/ftp/python/2.7.12/python-2.7.12.msi>`_ を公式サイトからダウンロードしてください。完全に最新のバージョンをインストールしたい場合は、`Python.orgのWebサイト <http://python.org>`_ のホームページからDownloads > Windowsのリンクをクリックしてください。

.. The Windows version is provided as an MSI package. To install it manually, just
.. double-click the file. The MSI package format allows Windows administrators to
.. automate installation with their standard tools.

Windows版はMSIパッケージとして提供されています。 手動でインストールするには、ファイルをダブルクリックしてください。 MSIパッケージ形式により、Windows管理者は標準ツールを使用してインストールを自動化できます。

.. By design, Python installs to a directory with the version number embedded,
.. e.g. Python version 2.7 will install at :file:`C:\\Python27\\`, so that you can
.. have multiple versions of Python on the
.. same system without conflicts. Of course, only one interpreter can be the
.. default application for Python file types. It also does not automatically
.. modify the :envvar:`PATH` environment variable, so that you always have control over
.. which copy of Python is run.

仕様上、Pythonはバージョン番号が埋め込まれたディレクトリにインストールされます。 Pythonバージョン2.7は :file:`C:\\Python27\\` にインストールされます。これにより、同じシステム上に複数のバージョンのPythonを競合することなく使用できます。 もちろん、Pythonファイルタイプのデフォルトアプリケーションは、1つのインタプリタだけです。 :envvar:`PATH` 環境変数も自動的には変更されません。そのため、あなたは常にPythonのコピーが実行されるかどうかを制御できます。

.. Typing the full path name for a Python interpreter each time quickly gets
.. tedious, so add the directories for your default Python version to the :envvar:`PATH`.
.. Assuming that your Python installation is in :file:`C:\\Python27\\`, add this to your
.. :envvar:`PATH`:

Pythonインタプリタのフルパス名を入力するたびに退屈になるので、デフォルトのPythonバージョンのディレクトリを :envvar:`PATH` に追加してください。 あなたのPythonのインストールが :file:`C:\\Python27\\` にあると仮定して、これをあなたの :envvar:`PATH` に追加してください:

.. code-block:: console

    C:\Python27\;C:\Python27\Scripts\

.. You can do this easily by running the following in ``powershell``:

これを簡単に行うには、 ``powershell`` で以下を実行します:

.. code-block:: console

    [Environment]::SetEnvironmentVariable("Path", "$env:Path;C:\Python27\;C:\Python27\Scripts\", "User")

.. The second (:file:`Scripts`) directory receives command files when certain
.. packages are installed, so it is a very useful addition.
.. You do not need to install or configure anything else to use Python. Having
.. said that, I would strongly recommend that you install the tools and libraries
.. described in the next section before you start building Python applications for
.. real-world use. In particular, you should always install Setuptools, as it
.. makes it much easier for you to use other third-party Python libraries.

2番目の (:file:`Scripts`) ディレクトリは、特定のパッケージがインストールされているときにコマンドファイルを受け取りますので、非常に便利です。 Pythonを使用するために何か他のものをインストールしたり設定したりする必要はありません。しかし、実際の使用のためにPythonアプリケーションを構築する前に、次のセクションで説明するツールとライブラリをインストールすることを強くお勧めします。特に、他のサードパーティのPythonライブラリを使うのがはるかに簡単なので、Setuptoolsを常にインストールしてください。

Setuptools + Pip
----------------

.. The most crucial third-party Python software of all is Setuptools, which
.. extends the packaging and installation facilities provided by the distutils in
.. the standard library. Once you add Setuptools to your Python system you can
.. download and install any compliant Python software product with a single
.. command. It also enables you to add this network installation capability to
.. your own Python software with very little work.

最も重要な第三者のPythonソフトウェアはSetutoolです。これは標準ライブラリのdistutilsによって提供されるパッケージとインストール機能を拡張します。 SetuptoolsをPythonシステムに追加すると、単一のコマンドで対応するPythonソフトウェア製品をダウンロードしてインストールすることができます。 また、このネットワークインストール機能をごくわずかな作業で独自のPythonソフトウェアに追加することもできます。

.. To obtain the latest version of Setuptools for Windows, run the Python script
.. available here: `ez_setup.py <https://bootstrap.pypa.io/ez_setup.py>`_

Windows用のSetuptoolsの最新版を入手するには、ここの利用できるPythonスクリプトを実行してください: `ez_setup.py <https://bootstrap.pypa.io/ez_setup.py>`_


.. You'll now have a new command available to you: **easy_install**. It is
.. considered by many to be deprecated, so we will install its replacement:
.. **pip**. Pip allows for uninstallation of packages, and is actively maintained,
.. unlike easy_install.

新しいコマンドを利用できるようになりました: **easy_install**。 多くの人には推奨されていないと考えられているので、その置き換えをインストールします: **pip**。 Pipは、パッケージのアンインストールを可能にし、easy_installとは異なり、積極的にメンテナンスされます。

.. To install pip, run the Python script available here:
.. `get-pip.py <https://raw.github.com/pypa/pip/master/contrib/get-pip.py>`_

pipをインストールするには、ここの利用できるPythonスクリプトを実行してください: `get-pip.py <https://raw.github.com/pypa/pip/master/contrib/get-pip.py>`_


.. Virtual Environments
.. --------------------

仮想環境
--------

.. A Virtual Environment is a tool to keep the dependencies required by different projects 
.. in separate places, by creating virtual Python environments for them. It solves the 
.. "Project X depends on version 1.x but, Project Y needs 4.x" dilemma, and keeps 
.. your global site-packages directory clean and manageable.

仮想環境は、異なるプロジェクトで必要とされる依存関係を別々の場所に保持するためのツールです。仮想環境は、それらのための仮想的なPython環境を作成することによって実現されます。 「Project Xはバージョン1.xに依存しますが、Project Yは4.xが必要です」というジレンマを解決し、グローバルなサイトパッケージディレクトリをきれいに管理します。

.. For example, you can work on a project which requires Django 1.10 while also
.. maintaining a project which requires Django 1.8.

例えば、Django 1.10を必要とするプロジェクトで作業し、Django 1.8を必要とするプロジェクトを維持することもできます。

.. To start using this and see more information: :ref:`Virtual Environments <virtualenvironments-ref>` docs. 

これを使い始め、さらに詳しい情報を参照する :ref:`Virtual Environments <virtualenvironments-ref>` docs。


--------------------------------

.. This page is a remixed version of `another guide <http://www.stuartellis.eu/articles/python-development-windows/>`_,
.. which is available under the same license.

このページは、`別のガイド <http://www.stuartellis.eu/articles/python-development-windows/>`_ のリミックス版です。これは、同じライセンスで入手できます。
