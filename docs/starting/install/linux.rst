.. _install-linux:

.. Installing Python on Linux
.. ==========================

PythonをLinuxにインストールする
===============================

.. The latest versions of CentOS, Fedora, Redhat Enterprise (RHEL) and Ubuntu 
.. **come with Python 2.7 out of the box**.

CentOS、Fedora、Redhat Enterprise（RHEL）、Ubuntu **の最新バージョンにはPython 2.7が付属しています**。

.. To see which version of Python you have installed, open a command prompt and run

インストールしたPythonのバージョンを確認するには、コマンドプロンプトを開いて実行してください

.. code-block:: console

    $ python --version

.. Some older versions of RHEL and CentOS come with Python 2.4 which is
.. unacceptable for modern Python development. Fortunately, there are
.. `Extra Packages for Enterprise Linux`_ which include high
.. quality additional packages based on their Fedora counterparts. This
.. repository contains a Python 2.6 package specifically designed to install
.. side-by-side with the system's Python 2.4 installation.

RHELとCentOSの古いバージョンにはPython 2.4が付属していますが、これは現代のPython開発では受け入れられません。 幸いにも、Fedoraの対応物に基づいた高品質の追加パッケージを含む `Extra Packages for Enterprise Linux`_ があります。 このリポジトリには、システムのPython 2.4インストールと並行してインストールするように設計されたPython 2.6パッケージが含まれています。

.. _Extra Packages for Enterprise Linux: http://fedoraproject.org/wiki/EPEL

.. You do not need to install or configure anything else to use Python. Having
.. said that, I would strongly recommend that you install the tools and libraries
.. described in the next section before you start building Python applications
.. for real-world use. In particular, you should always install Setuptools and pip, as
.. it makes it much easier for you to use other third-party Python libraries.

Pythonを使用するために何か他のものをインストールしたり設定したりする必要はありません。 しかし、実際の使用のためにPythonアプリケーションを構築する前に、次のセクションで説明するツールとライブラリをインストールすることを強くお勧めします。 特に、他のサードパーティのPythonライブラリを使うのがはるかに簡単になるので、Setuptoolsとpipをインストールする必要があります。

Setuptools & Pip
----------------

.. The two most crucial third-party Python packages are `setuptools <https://pypi.python.org/pypi/setuptools>`_ and `pip <https://pip.pypa.io/en/stable/>`_.

最も重要な2つのサードパーティのPythonパッケージは、 `setuptools <https://pypi.python.org/pypi/setuptools>`_ と `pip <https://pip.pypa.io/en/stable/>`_ 。

.. Once installed, you can download, install and uninstall any compliant Python software 
.. product with a single command. It also enables you to add this network installation 
.. capability to your own Python software with very little work.

インストールが完了すると、単一のコマンドで、対応するPythonソフトウェア製品をダウンロード、インストール、アンインストールできます。また、このネットワークインストール機能をごくわずかな作業で独自のPythonソフトウェアに追加することもできます。

.. Python 2.7.9 and later (on the python2 series), and Python 3.4 and later include 
.. pip by default.

Python 2.7.9以降（Python2シリーズ）、Python 3.4以降にはpipがデフォルトで含まれています。

.. To see if pip is installed, open a command prompt and run

pipがインストールされているかどうかを確認するには、コマンドプロンプトを開き

.. code-block:: console

    $ command -v pip

.. To install pip, `follow the official pip installation guide <https://pip.pypa.io/en/latest/installing/>`_ - this will automatically install the latest version of setuptools.

pipをインストールするには、`公式のpipインストールガイド <https://pip.pypa.io/en/latest/installing/>`_ に従ってください。これにより、setuptoolsの最新バージョンが自動的にインストールされます。

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

.. You can also use :ref:`virtualenvwrapper <virtualenvwrapper-ref>` to make it easier to
.. manage your virtual environments.

:ref:`virtualenvwrapper <virtualenvwrapper-ref>` を使って、仮想環境の管理を容易にすることもできます。

--------------------------------

.. This page is a remixed version of `another guide <http://www.stuartellis.eu/articles/python-development-windows/>`_,
.. which is available under the same license.

このページは、`別のガイド <http://www.stuartellis.eu/articles/python-development-windows/>`_ のリミックス版です。これは、同じライセンスで入手できます。

