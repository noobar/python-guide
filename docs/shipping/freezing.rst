.. _freezing-your-code-ref:

.. ==================
.. Freezing Your Code
.. ==================

================
コードのフリーズ
================

.. "Freezing" your code is creating a single-file executable file to distribute 
.. to end-users, that contains all of your application code as well as the 
.. Python interpreter.

コードを "フリーズ" すると、アプリケーションコードとPythonインタプリタのすべてを含む、エンドユーザーに配布するための単一ファイルの実行可能ファイルが作成されます。

.. Applications such as 'Dropbox', 'Eve Online',  'Civilization IV', and
.. BitTorrent clients do this.

「Dropbox」、「Eve Online」、「Civilization IV」、BitTorrentクライアントなどのアプリケーションがこれを行います。

.. The advantage of distributing this way is that your application will "just work",
.. even if the user doesn't already have the required version of Python (or any) 
.. installed. On Windows, and even on many Linux distributions and OS X, the right
.. version of Python will not already be installed.

この方法を配布することの利点は、必要なバージョンのPython（またはいずれか）がインストールされていなくても、アプリケーションが「うまくいく」ことです。 Windowsでは、そして多くのLinuxディストリビューションやOS Xでも、適切なバージョンのPythonはまだインストールされていません。

.. Besides, end-user software should always be in an executable format. Files 
.. ending in ``.py`` are for software engineers and system administrators. 

さらに、エンドユーザソフトウェアは常に実行形式でなければなりません。 ``.py`` で終わるファイルは、ソフトウェアエンジニアやシステム管理者のためのものです。

.. One disadvantage of freezing is that it will increase the size of your 
.. distribution by about 2–12MB. Also, you will be responsible for shipping
.. updated versions of your application when security vulnerabilities to 
.. Python are patched. 

フリーズの欠点の1つは、配布量を約2〜12MB増やすことです。 また、Pythonのセキュリティ上の脆弱性が修正されたときに、アプリケーションの更新版を出荷する責任があります。

.. Alternatives to Freezing
.. ------------------------

凍結の代替
----------

.. :ref:`Packaging your code <packaging-your-code-ref>` is for distributing
.. libraries or tools to other developers.

:ref:`あなたのコードをパッケージ化する <packaging-your-code-ref>` は、ライブラリやツールを他の開発者に配布するためのものです。

.. On Linux, an alternative to freezing is to
.. :ref:`create a Linux distro package <packaging-for-linux-distributions-ref>`
.. (e.g. .deb files for Debian or Ubuntu, or .rpm files for Red Hat and SuSE.)

Linuxの場合、凍結する代わりに、 :ref:`Linuxディストリビューションパッケージを作成するためのパッケージング <package-for-linux-distributions-ref>` （DebianやUbuntuでは.debファイル、Red HatやSuSEでは.rpmファイル） ）

.. .. todo:: Fill in "Freezing Your Code" stub

.. todo:: "コードをフリーズする" スタブを記入

.. Comparison of Freezing Tools
.. ----------------------------

フリーズツールの比較
--------------------

.. Solutions and platforms/features supported:

ソリューションとプラットフォーム/サポートされる機能:

=========== ======= ===== ==== ======== ======= ============= ============== ==== =====================
Solution    Windows Linux OS X Python 3 License One-file mode Zipfile import Eggs pkg_resources support
=========== ======= ===== ==== ======== ======= ============= ============== ==== =====================
bbFreeze    yes     yes   yes  no       MIT     no            yes            yes  yes
py2exe      yes     no    no   yes      MIT     yes           yes            no   no
pyInstaller yes     yes   yes  yes      GPL     yes           no             yes  no
cx_Freeze   yes     yes   yes  yes      PSF     no            yes            yes  no
py2app      no      no    yes  yes      MIT     no            yes            yes  yes
=========== ======= ===== ==== ======== ======= ============= ============== ==== =====================

.. note::
    Linux上のPythonコードをWindows実行可能ファイルにフリーズすることはPyInstaller で一度しかサポートされず、`後で廃止されました <http://stackoverflow.com/questions/2950971/cross-compiling-a-python-script-on-linux-into-a-windows-executable#comment11890276_2951046>`_ 。

..     Freezing Python code on Linux into a Windows executable was only once
..     supported in PyInstaller `and later dropped.
..     <http://stackoverflow.com/questions/2950971/cross-compiling-a-python-script-on-linux-into-a-windows-executable#comment11890276_2951046>`_.

.. note::
    すべてのソリューションは、py2appを除くターゲットマシンにMS Visual C++ dllをインストールする必要があります。 Pyinstallerだけが :option:`--onefile` を渡すときにdllをバンドルする自己実行可能なexeを作成します :file:`Configure.py` 。

..     All solutions need MS Visual C++ dll to be installed on target machine, except py2app.
..     Only Pyinstaller makes self-executable exe that bundles the dll when
..     passing :option:`--onefile` to :file:`Configure.py`.

Windows
-------

bbFreeze
~~~~~~~~

.. Prerequisite is to install :ref:`Python, Setuptools and pywin32 dependency on Windows <install-windows>`.

前提条件は :ref:`Python、Setuptoolsとpywin32の依存関係をWindows <install-windows>` にインストールすることです。

.. .. todo:: Write steps for most basic .exe

.. todo:: 最も基本的な .exeのステップを書く

py2exe
~~~~~~

.. Prerequisite is to install :ref:`Python on Windows <install-windows>`.

前提条件は :ref:`Python on Windows <install-windows>` をインストールすることです。

.. 1. Download and install http://sourceforge.net/projects/py2exe/files/py2exe/

1. http://sourceforge.net/projects/py2exe/files/py2exe/ をダウンロードしてインストールします。

.. 2. Write :file:`setup.py` (`List of configuration options <http://www.py2exe.org/index.cgi/ListOfOptions>`_):

2. 書き込み :file:`setup.py` (`設定オプションのリスト <http://www.py2exe.org/index.cgi/ListOfOptions>`_):

.. code-block:: python

    from distutils.core import setup
    import py2exe

    setup(
        windows=[{'script': 'foobar.py'}],
    )

.. 3. (Optionally) `include icon <http://www.py2exe.org/index.cgi/CustomIcons>`_

3. (オプション) `インクルードアイコン <http://www.py2exe.org/index.cgi/CustomIcons>`_

.. 4. (Optionally) `one-file mode <http://stackoverflow.com/questions/112698/py2exe-generate-single-executable-file#113014>`_

4. (オプション) `1ファイルモード <http://stackoverflow.com/questions/112698/py2exe-generate-single-executable-file#113014>`_

.. 5. Generate :file:`.exe` into :file:`dist` directory:

5. 生成する :file:`.exe` into :file:`dist` ディレクトリ:

.. code-block:: console

   $ python setup.py py2exe

.. 6. Provide the Microsoft Visual C runtime DLL. Two options: `globally install dll on target machine <https://www.microsoft.com/en-us/download/details.aspx?id=29>`_ or `distribute dll alongside with .exe <http://www.py2exe.org/index.cgi/Tutorial#Step52>`_.

6. Microsoft Visual CランタイムDLLを提供します。 2つのオプションがあります: `ターゲットマシンにDLLをグローバルにインストールする <https://www.microsoft.com/en-us/download/details.aspx?id=29>`_ または `dllを .exe と一緒に配布する <http://www.py2exe.org/index.cgi/Tutorial#Step52>`_ 。

PyInstaller
~~~~~~~~~~~

.. Prerequisite is to have installed :ref:`Python, Setuptools and pywin32 dependency on Windows <install-windows>`.

前提条件は、 :ref:`Python、Setuptoolsとpywin32依存関係をWindows <install-windows>` にインストールすることです。

- `Most basic tutorial <http://bojan-komazec.blogspot.com/2011/08/how-to-create-windows-executable-from.html>`_
- `Manual <http://www.pyinstaller.org/export/d3398dd79b68901ae1edd761f3fe0f4ff19cfb1a/project/doc/Manual.html?format=raw>`_


OS X
----


py2app
~~~~~~

PyInstaller
~~~~~~~~~~~

.. PyInstaller can be used to build Unix executables and windowed apps on Mac OS X 10.6 (Snow Leopard) or newer.

PyInstallerを使用して、Mac OS X 10.6（Snow Leopard）以降のUnix実行ファイルやウィンドウアプリケーションをビルドすることができます。

.. To install PyInstaller, use pip:

PyInstallerをインストールするには、pipを使用します:

.. code-block:: console

 $ pip install pyinstaller

.. To create a standard Unix executable, from say :code:`script.py`, use:

標準のUnix実行ファイルを作成するには、次のようにします :code:`script.py`:

.. code-block:: console

 $ pyinstaller script.py

.. This creates,

これは、

.. - a :code:`script.spec` file, analogous to a :code:`make` file
.. - a :code:`build` folder, that holds some log files
.. - a :code:`dist` folder, that holds the main executable :code:`script`, and some dependent Python libraries,

- :code:`script.spec` ファイル :code:`make` ファイルに似ています
- :code:`build` フォルダ。いくつかのログファイルを保持します。
- :code:`dist` フォルダです。メインの実行ファイル :code:`script` といくつかの依存するPythonライブラリを保持しています。

.. all in the same folder as :code:`script.py`. PyInstaller puts all the Python libraries used in :code:`script.py` into the :code:`dist` folder, so when distributing the executable, distribute the whole :code:`dist` folder.

すべて同じフォルダ内にあります :code:`script.py`。 PyInstallerは :code:`script.py` で使われているすべてのPythonライブラリを :code:`dist` フォルダに置きます。したがって、実行ファイルを配布するときには :code:`dist` フォルダ全体を配布してください。

.. The :code:`script.spec` file can be edited to `customise the build <http://pythonhosted.org/PyInstaller/#spec-file-operation>`_, with options such as

:code:`script.spec` ファイルは `ビルドをカスタマイズ <http://pythonhosted.org/PyInstaller/#spec-file-operation>`_ するために編集することができます。

.. - bundling data files with the executable
.. - including run-time libraries (:code:`.dll` or :code:`.so` files) that PyInstaller can't infer automatically
.. - adding Python run-time options to the executable,

- データファイルを実行可能ファイルにバンドルする
- PyInstallerが自動的に推論できない実行時ライブラリ (:code:`.dll` または :code:`.so` ファイル) を含みます
- Python実行時オプションを実行可能ファイルに追加する

.. Now :code:`script.spec` can be run with :code:`pyinstaller` (instead of using :code:`script.py` again):

今すぐ :code:`script.spec` は :code:`pyinstaller` で実行することができます (:code:`script.py` を再度使用するのではなく):

.. code-block:: console

  $ pyinstaller script.spec

.. To create a standalone windowed OS X application, use the :code:`--windowed` option

スタンドアロンのウィンドウズOS Xアプリケーションを作成するには、:code:`--windowed` オプションを使います

.. code-block:: console

 $ pyinstaller --windowed script.spec

.. This creates a :code:`script.app` in the :code:`dist` folder. Make sure to use GUI packages in your Python code, like `PyQt <https://riverbankcomputing.com/software/pyqt/intro>`_ or `PySide <http://wiki.qt.io/About-PySide>`_, to control the graphical parts of the app.

これは :code:`dist` フォルダに :code:`script.app` を作成します。 `PyQt <https://riverbankcomputing.com/software/pyqt/intro>`_ や `PySide <http://wiki.qt.io/About-PySide>`_ のようなPythonコードでGUIパッケージを使うようにしてください。アプリのグラフィック部分を制御する。

.. There are several options in :code:`script.spec` related to Mac OS X app bundles `here <http://pythonhosted.org/PyInstaller/#spec-file-options-for-a-mac-os-x-bundle>`_. For example, to specify an icon for the app, use the :code:`icon=\path\to\icon.icns` option. 

いくつかのオプションがあります :code:`script.spec` はMac OS Xアプリケーションバンドルに関連しています `here <http://pythonhosted.org/PyInstaller/#spec-file-options-for-a-macos-x-bundle>`_ 。 たとえば、アプリケーションのアイコンを指定するには、 :code:`icon=\ path\to\icon.icns` オプションを使用します。


Linux
-----


bbFreeze
~~~~~~~~

PyInstaller
~~~~~~~~~~~
