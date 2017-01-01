.. _packaging-your-code-ref:

.. ===================
.. Packaging Your Code
.. ===================

====================
コードのパッケージ化
====================

.. Package your code to share it with other developers. For example
.. to share a library for other developers to use in their application,
.. or for development tools like 'py.test'.

コードをパッケージ化して、他の開発者と共有します。例えば、他の開発者が自分のアプリケーションで使うためのライブラリや、 'py.test' のような開発ツールを共有するためです。

.. An advantage of this method of distribution is its well established ecosystem
.. of tools such as PyPI and pip, which make it easy for other developers to
.. download and install your package either for casual experiments, or as part of
.. large, professional systems.

この配布方法の利点は、他の開発者が偶然の実験用に、または大規模で専門的なシステムの一部としてパッケージをダウンロードしてインストールすることを容易にする、PyPIやpipなどのツールの確立されたエコシステムです。

.. It is a well-established convention for Python code to be shared this way.
.. If your code isn't packaged on PyPI, then it will be harder
.. for other developers to find it, and to use it as part of their existing
.. process. They will regard such projects with substantial suspicion of being
.. either badly managed or abandoned.

この方法でPythonコードを共有するのは、定評のある規約です。コードがPyPIにパッケージ化されていない場合、他の開発者がコードを見つけて既存のプロセスの一部として使用することは難しくなります。彼らは、このようなプロジェクトについては、管理や放棄の疑いが強いとみなします。

.. The downside of distributing code like this is that it relies on the
.. recipient understanding how to install the required version of Python,
.. and being able and willing to use tools such as pip to install your code's
.. other dependencies. This is fine when distributing to other developers, but
.. makes this method unsuitable for distributing applications to end-users.

このようにコードを配布することの欠点は、必要なバージョンのPythonをインストールする方法と、pyなどのツールを使用してコードの他の依存関係をインストールすることができることを受信者が理解していることです。 これは他の開発者に配布する場合は問題ありませんが、この方法はアプリケーションをエンドユーザーに配布する場合には不適切です。

.. The `Python Packaging Guide <https://python-packaging-user-guide.readthedocs.io/>`_
.. provides an extensive guide on creating and maintaining Python packages.

`Pythonパッケージングガイド <https://python-packaging-user-guide.readthedocs.io/>`_ には、Pythonパッケージの作成と保守に関する広範なガイドがあります。

.. Alternatives to Packaging
.. :::::::::::::::::::::::::

パッケージングの代替案
::::::::::::::::::::::

.. To distribute applications to end-users, you should
.. :ref:`freeze your application <freezing-your-code-ref>`.

アプリケーションをエンドユーザに配布するには、以下を行う必要があります。 :ref:`アプリケーション <freezing-your-code-ref>` をフリーズします。

.. On Linux, you may also want to consider
.. :ref:`creating a Linux distro package <packaging-for-linux-distributions-ref>`
.. (e.g. a .deb file for Debian or Ubuntu.)

Linuxでは、:ref:`Linuxディストリビューションパッケージ<packaging-for-linux-distributions-ref>` の作成 (例：DebianやUbuntu用の.debファイル) を参考にしてください。

.. For Python Developers
.. :::::::::::::::::::::

Pythonデベロッパー向け
::::::::::::::::::::::

.. If you're writing an open source Python module, `PyPI <http://pypi.python.org>`_
.. , more properly known as *The Cheeseshop*, is the place to host it.

オープンソースのPythonモジュールを書いているなら、`PyPI <http://pypi.python.org>`_ と呼ばれ、よりよく知られている *The Cheeseshop* は、それをホストする場所です。



Pip vs. easy_install
--------------------

.. Use `pip <http://pypi.python.org/pypi/pip>`_.  More details
.. `here <http://stackoverflow.com/questions/3220404/why-use-pip-over-easy-install>`_

`pip <http://pypi.python.org/pypi/pip>`_ を使用してください。 詳細は `here <http://stackoverflow.com/questions/3220404/why-use-pip-over-easy-install>`_


.. Personal PyPI
.. -------------

パーソナルPyPI
--------------

.. If you want to install packages from a source other than PyPI, (say, if
.. your packages are *proprietary*), you can do it by hosting a simple http
.. server, running from the directory which holds those packages which need to be
.. installed.

PyPI以外のソースからパッケージをインストールする場合（例えば、パッケージが *proprietary* の場合）、インストールが必要なパッケージを保持するディレクトリから実行される単純なhttpサーバをホストすることによって実行できます。

.. **Showing an example is always beneficial**

**例を示すことは常に有益です**

.. For example, if you want to install a package called :file:`MyPackage.tar.gz`,
.. and assuming this is your directory structure:

たとえば、 :file:`MyPackage.tar.gz` という名前のパッケージをインストールし、それがあなたのディレクトリ構造であると仮定すると:


- archive
   - MyPackage
       - MyPackage.tar.gz

.. Go to your command prompt and type:

コマンドプロンプトで次のように入力します:

.. code-block:: console

   $ cd archive
   $ python -m SimpleHTTPServer 9000

.. This runs a simple http server running on port 9000 and will list all packages
.. (like **MyPackage**). Now you can install **MyPackage** using any Python
.. package installer. Using Pip, you would do it like:

これは、ポート9000で実行される単純なhttpサーバーを実行し、**MyPackage** などのすべてのパッケージをリストします。 これで、Pythonパッケージインストーラを使用して **MyPackage** をインストールできます。 Pipを使用すると、次のようになります。

.. code-block:: console

   $ pip install --extra-index-url=http://127.0.0.1:9000/ MyPackage

.. Having a folder with the same name as the package name is **crucial** here.
.. I got fooled by that, one time. But if you feel that creating a folder called
.. :file:`MyPackage` and keeping :file:`MyPackage.tar.gz` inside that, is
.. *redundant*, you can still install MyPackage using:

パッケージ名と同じ名前のフォルダを持つことは、ここでは **非常に重要です**。 私はそれに騙された、一度。 しかし、:file:`MyPackage` という名前のフォルダを作成し、:file:`MyPackage.tar.gz` を *redundant* にしておくと、MyPackageをインストールすることができます:

.. code-block:: console

   $ pip install  http://127.0.0.1:9000/MyPackage.tar.gz

pypiserver
++++++++++

.. `Pypiserver <https://pypi.python.org/pypi/pypiserver>`_ is a minimal PyPI
.. compatible server.  It can be used to serve a set of packages to easy_install
.. or pip.  It includes helpful features like an administrative command
.. (:option:`-U`) which will update all its packages to their latest versions
.. found on PyPI.

`Pypiserver <https://pypi.python.org/pypi/pypiserver>`_ はPyPI互換の最小限のサーバです。 これは、easy_installまたはpipにパッケージのセットを提供するために使用することができます。 管理コマンド(:option:`-U`)のような便利な機能が含まれており、すべてのパッケージをPyPI上の最新バージョンに更新します。


S3-Hosted PyPi
++++++++++++++

.. One simple option for a personal PyPi server is to use Amazon S3. A
.. prerequisite for this is that you have an Amazon AWS account with an S3 bucket.

パーソナルPyPiサーバのための簡単なオプションの1つは、Amazon S3を使用することです。これの前提条件は、S3バケットを備えたAmazon AWSアカウントを持っていることです。

.. 1. **Install all your requirements from PyPi or another source**
.. 2. **Install pip2pi**

1. **PyPiまたは別のソースからすべての要件をインストールする**
2. **pip2piをインストールする**

* :code:`pip install git+https://github.com/wolever/pip2pi.git`

.. 3. **Follow pip2pi README for pip2tgz and dir2pi commands**

3. **pip2tgzおよびdir2piコマンドの場合はpip2pi READMEに従ってください。**

* :code:`pip2tgz packages/ YourPackage` (or :code:`pip2tgz packages/ -r requirements.txt`)
* :code:`dir2pi packages/`

.. 4. **Upload the new files**

4. **新しいファイルをアップロードする**

.. * Use a client like Cyberduck to sync the entire :file:`packages` folder to your s3 bucket
.. * Make sure you upload :code:`packages/simple/index.html` as well as all new files and directories

* Cyberduckのようなクライアントを使って :file:`packages` フォルダ全体をs3バケットに同期させます
* あなたが必ず :code:`packages/simple/index.html` と全ての新しいファイルとディレクトリをアップロードしてください

.. 5. **Fix new file permissions**

5. **新しいファイルのアクセス許可を修正する**

.. * By default, when you upload new files to the S3 bucket, they will have the wrong permissions set.
.. * Use the Amazon web console to set the READ permission of the files to EVERYONE.
.. * If you get HTTP 403 when trying to install a package, make sure you've set the permissions correctly.

* デフォルトでは、S3バケットに新しいファイルをアップロードすると、不正なアクセス権が設定されます。
* Amazon Webコンソールを使用して、ファイルのREAD権限をEVERYONEに設定します。
* パッケージをインストールしようとしたときにHTTP 403が表示された場合は、アクセス権を正しく設定してください。

.. 6. **All done**

6. **すべて完了**

.. * You can now install your package with :code:`pip install --index-url=http://your-s3-bucket/packages/simple/ YourPackage`

* あなたは今あなたのパッケージをインストールすることができます :code:`pip install --index-url=http://your-s3-bucket/packages/simple / YourPackage`

.. _packaging-for-linux-distributions-ref:

.. For Linux Distributions
.. ::::::::::::::::::::::::

Linuxディストリビューションの場合
:::::::::::::::::::::::::::::::::

.. Creating a Linux distro package is arguably the "right way" to distribute code
.. on Linux.

Linuxディストリパッケージを作成することは、間違いなくLinux上でコードを配布する「正しい方法」です。

.. Because a distribution package doesn't include the Python interpreter, it
.. makes the download and install about 2MB smaller than
.. :ref:`freezing your application <freezing-your-code-ref>`.

ディストリビューションパッケージにはPythonインタプリタが含まれていないので、ダウンロード約2MBをインストールします :ref:`アプリケーション <freezing-your-code-ref>` をフリーズします。

.. Also, if a distribution releases a new security update for Python, then your
.. application will automatically start using that new version of Python.

また、ディストリビューションがPython用の新しいセキュリティアップデートをリリースすると、その新しいバージョンのPythonを使ってアプリケーションが自動的に起動します。

.. The bdist_rpm command makes `producing an RPM file <https://docs.python.org/3/distutils/builtdist.html#creating-rpm-packages>`_
.. for use by distributions like Red Hat or SuSE is trivially easy.

bdist_rpmコマンドは、Red HatやSuSEのようなディストリビューションで使用する `RPMファイルを生成すること <https://docs.python.org/3/distutils/builtdist.html#creating-rpm-packages>`_ は簡単です。

.. However, creating and maintaining the different configurations required for
.. each distribution's format (e.g. .deb for Debian/Ubuntu, .rpm for Red
.. Hat/Fedora, etc) is a fair amount of work. If your code is an application that
.. you plan to distribute on other platforms, then you'll also have to create and
.. maintain the separate config required to freeze your application for Windows
.. and OSX. It would be much less work to simply create and maintain a single
.. config for one of the cross platform :ref:`freezing tools
.. <freezing-your-code-ref>`, which will produce stand-alone executables for all
.. distributions of Linux, as well as Windows and OSX.

しかし、各ディストリビューションのフォーマット（Debian / Ubuntuの場合は.deb、RedHat/Fedoraの場合は.rpmなど）に必要なさまざまな設定を作成し、維持することは相当量の作業です。コードが他のプラットフォームで配布する予定のアプリケーションである場合は、WindowsとOSX用にアプリケーションをフリーズするために必要な別の設定を作成して維持する必要があります。クロスプラットフォーム :ref:`フリーズツール <freezing-your-code-ref>` のいずれかのために、Linuxのすべてのディストリビューションのためのスタンドアロンの実行可能ファイルを生成する単一の設定を作成して維持するだけでは、 WindowsとOSXだけでなく、

.. Creating a distribution package is also problematic if your code is for a
.. version of Python that isn't currently supported by a distribution.
.. Having to tell *some versions* of Ubuntu end-users that they need to add `the
.. 'dead-snakes' PPA <https://launchpad.net/~fkrull/+archive/ubuntu/deadsnakes>`_
.. using `sudo apt-repository` commands before they can install your .deb file
.. makes for an extremely hostile user experience. Not only that, but you'd have
.. to maintain a custom equivalent of these instructions for every distribution,
.. and worse, have your users read, understand, and act on them.

配布パッケージを作成することは、あなたのコードが現在配布物でサポートされていないバージョンのPython用である場合にも問題になります。 Ubuntuエンドユーザの *いくつかのバージョン* に `'dead-snakes' PPA <https://launchpad.net/~fkrull/+archive/ubuntu/deadsnakes>`_ `sudo apt-repository` を追加する必要があることを伝える必要があります コマンドを使用して.debファイルをインストールする前に、非常に敵対的なユーザーエクスペリエンスを作ります。 それだけでなく、すべてのディストリビューションでこれらの手順に相当するカスタムを維持しなければならず、さらに悪いことに、ユーザーに読んで理解させ、行動させる必要があります。

.. Having said all that, here's how to do it:

すべてのことを言って、ここでそれを行う方法です:

* `Fedora <https://fedoraproject.org/wiki/Packaging:Python>`_
* `Debian and Ubuntu <http://www.debian.org/doc/packaging-manuals/python-policy/>`_
* `Arch <https://wiki.archlinux.org/index.php/Python_Package_Guidelines>`_

.. Useful Tools
.. ------------

便利なツール
------------

- `fpm <https://github.com/jordansissel/fpm>`_
- `alien <http://joeyh.name/code/alien/>`_
- `dh-virtualenv <https://dh-virtualenv.readthedocs.io/en/latest/info.html>`_ (APT/DEBオムニバスパッケージング用)
.. - `dh-virtualenv <https://dh-virtualenv.readthedocs.io/en/latest/info.html>`_ (for APT/DEB omnibus packaging)
