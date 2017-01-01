.. _virtualenvironments-ref:

.. Virtual Environments
.. ====================

仮想環境
========

.. A Virtual Environment is a tool to keep the dependencies required by different
.. projects in separate places, by creating virtual Python environments for them.
.. It solves the "Project X depends on version 1.x but, Project Y needs 4.x"
.. dilemma, and keeps your global site-packages directory clean and manageable.

仮想環境は、異なるプロジェクトで必要とされる依存関係を別々の場所に保持するためのツールです。仮想環境は、それらのための仮想的なPython環境を作成することによって実現されます。 「Project Xはバージョン1.xに依存しますが、Project Yは4.xが必要です」というジレンマを解決し、グローバルなサイトパッケージディレクトリをきれいに管理します。

.. For example, you can work on a project which requires Django 1.10 while also
.. maintaining a project which requires Django 1.8.

例えば、Django 1.10を必要とするプロジェクトで作業し、Django 1.8を必要とするプロジェクトを維持することもできます。

virtualenv
----------

.. `virtualenv <http://pypi.python.org/pypi/virtualenv>`_ is a tool to create
.. isolated Python environments. virtualenv creates a folder which contains all the
.. necessary executables to use the packages that a Python project would need.

`virtualenv <http://pypi.python.org/pypi/virtualenv>`_ は独立したPython環境を作るためのツールです。 virtualenvは、Pythonプロジェクトが必要とするパッケージを使用するために必要なすべての実行可能ファイルを含むフォルダを作成します。

.. Install virtualenv via pip:

pip経由でvirtualenvをインストールする:

.. code-block:: console

  $ pip install virtualenv

.. Basic Usage
.. ~~~~~~~~~~~

基本的な使用法
~~~~~~~~~~~~~~

.. 1. Create a virtual environment for a project:

1.プロジェクトの仮想環境を作成します。

.. code-block:: console

   $ cd my_project_folder
   $ virtualenv venv

.. ``virtualenv venv`` will create a folder in the current directory which will
.. contain the Python executable files, and a copy of the ``pip`` library which you
.. can use to install other packages. The name of the virtual environment (in this
.. case, it was ``venv``) can be anything; omitting the name will place the files
.. in the current directory instead.

``virtualenv venv`` は現在のディレクトリにPythonの実行可能ファイルを含むフォルダを作成し、他のパッケージをインストールするために ``pip`` ライブラリのコピーを作成します。 仮想環境の名前（この場合、 ``venv`` ）は何でもかまいません。 名前を省略すると、カレントディレクトリにファイルが配置されます。

.. This creates a copy of Python in whichever directory you ran the command in,
.. placing it in a folder named :file:`venv`.

これにより、コマンドを実行したディレクトリの中にPythonのコピーが作成され、file:`venv` という名前のフォルダに置かれます。

.. You can also use the Python interpreter of your choice (like
.. ``python2.7``).

Pythonインタプリタ（ ``python2.7`` など）を使用することもできます。

.. code-block:: console

   $ virtualenv -p /usr/bin/python2.7 venv

.. or change the interpreter globally with an env variable in ``~/.bashrc``:

または ``~/.bashrc`` のenv変数でインタプリタをグローバルに変更してください:

.. code-block:: console

   $ export VIRTUALENVWRAPPER_PYTHON=/usr/bin/python2.7

.. 2. To begin using the virtual environment, it needs to be activated:

2.仮想環境の使用を開始するには、仮想環境をアクティブにする必要があります。

.. code-block:: console

   $ source venv/bin/activate

.. The name of the current virtual environment will now appear on the left of
.. the prompt (e.g. ``(venv)Your-Computer:your_project UserName$)`` to let you know
.. that it's active. From now on, any package that you install using pip will be
.. placed in the ``venv`` folder, isolated from the global Python installation.

現在の仮想環境の名前がプロンプトの左側に表示されます（例えば ``(venv)Your-Computer:your_project UserName $)`` ）。 これからpipを使ってインストールしたパッケージは、グローバルなPythonインストールから隔離された ``venv`` フォルダに置かれます。

.. Install packages as usual, for example:

パッケージを通常どおりにインストールします。例:

.. code-block:: console

    $ pip install requests

.. 3. If you are done working in the virtual environment for the moment, you can
..    deactivate it:

3.仮想環境で作業が完了した場合は、仮想環境を非アクティブにすることができます。

.. code-block:: console

   $ deactivate

.. This puts you back to the system's default Python interpreter with all its
.. installed libraries.

これにより、インストールされているすべてのライブラリを持つ、システムのデフォルトのPythonインタプリタに戻ります。

.. To delete a virtual environment, just delete its folder. (In this case,
.. it would be ``rm -rf venv``.)

仮想環境を削除するには、そのフォルダを削除するだけです。 （この場合、 ``rm -rf venv`` となります。）

.. After a while, though, you might end up with a lot of virtual environments
.. littered across your system, and its possible you'll forget their names or
.. where they were placed.

しかし、しばらくすると、システム全体に散在する多くの仮想環境に陥る可能性があり、名前や場所などを忘れる可能性があります。

.. Other Notes
.. ~~~~~~~~~~~

その他の注意事項
~~~~~~~~~~~~~~~~

.. Running ``virtualenv`` with the option :option:`--no-site-packages` will not
.. include the packages that are installed globally. This can be useful
.. for keeping the package list clean in case it needs to be accessed later.
.. [This is the default behavior for ``virtualenv`` 1.7 and later.]

:option:`--no-site-packages` オプションで ``virtualenv`` を実行すると、グローバルにインストールされたパッケージは含まれません。 後でアクセスする必要がある場合に備えてパッケージリストをきれいに保つのに便利です。 [これは1.7以降の ``virtualenv`` のデフォルト動作です。]

.. In order to keep your environment consistent, it's a good idea to "freeze"
.. the current state of the environment packages. To do this, run

環境を一貫性を保つために、環境パッケージの現在の状態を「フリーズ」することは良い考えです。 これを行うには、

.. code-block:: console

    $ pip freeze > requirements.txt

.. This will create a :file:`requirements.txt` file, which contains a simple
.. list of all the packages in the current environment, and their respective
.. versions. You can see the list of installed packages without the requirements
.. format using "pip list". Later it will be easier for a different developer
.. (or you, if you need to re-create the environment) to install the same packages
.. using the same versions:

これにより :file:`requirements.txt` ファイルが作成されます。このファイルには、現在の環境内のすべてのパッケージとそれぞれのバージョンの単純なリストが含まれています。 "pip list"を使用して、インストールされたパッケージのリストを要件書式なしで見ることができます。 後で同じバージョンを使用して同じパッケージをインストールするために、別の開発者（または環境を再作成する必要がある場合）が簡単になります。

.. code-block:: console

    $ pip install -r requirements.txt

.. This can help ensure consistency across installations, across deployments,
.. and across developers.

これにより、インストール全体、展開全体、および開発者間の一貫性を確保できます。

.. Lastly, remember to exclude the virtual environment folder from source
.. control by adding it to the ignore list.

最後に、ignoreリストに仮想環境フォルダを追加することによって、仮想環境フォルダをソース管理から除外することを忘れないでください。

.. _virtualenvwrapper-ref:

virtualenvwrapper
-----------------

.. `virtualenvwrapper <https://virtualenvwrapper.readthedocs.io/en/latest/index.html>`_
.. provides a set of commands which makes working with virtual environments much
.. more pleasant. It also places all your virtual environments in one place.

`virtualenvwrapper <https://virtualenvwrapper.readthedocs.io/en/latest/index.html>`_ は、仮想環境での作業をはるかに楽にする一連のコマンドを提供します。 また、すべての仮想環境を1か所に配置します。

.. To install (make sure **virtualenv** is already installed):

インストールするには（**virtualenv** が既にインストールされていることを確認してください）:

.. code-block:: console

  $ pip install virtualenvwrapper
  $ export WORKON_HOME=~/Envs
  $ source /usr/local/bin/virtualenvwrapper.sh

.. (`Full virtualenvwrapper install instructions <https://virtualenvwrapper.readthedocs.io/en/latest/install.html>`_.)

(`Full virtualenvwrapperのインストール手順 <https://virtualenvwrapper.readthedocs.io/en/latest/install.html>`_.）

.. For Windows, you can use the `virtualenvwrapper-win <https://github.com/davidmarble/virtualenvwrapper-win/>`_.

Windowsの場合、 `virtualenvwrapper-win <https://github.com/davidmarble/virtualenvwrapper-win/>`_ を使うことができます。

.. To install (make sure **virtualenv** is already installed):

インストールするには(**virtualenv** が既にインストールされていることを確認してください):

.. code-block:: console

  $ pip install virtualenvwrapper-win

.. In Windows, the default path for WORKON_HOME is %USERPROFILE%\Envs

Windowsでは、WORKON_HOME のデフォルトパスは %USERPROFILE%\Envs です。

.. Basic Usage
.. ~~~~~~~~~~~

基本的な使用法
~~~~~~~~~~~~~~

.. 1. Create a virtual environment:

1.仮想環境を作成します。

.. code-block:: console

   $ mkvirtualenv venv

.. This creates the :file:`venv` folder inside :file:`~/Envs`.

これは :file:`~/Envs` の中に :file:`venv` フォルダを作成します。

.. 2. Work on a virtual environment:

2.仮想環境での作業:

.. code-block:: console

   $ workon venv

.. Alternatively, you can make a project, which creates the virtual environment,
.. and also a project directory inside ``$PROJECT_HOME``, which is ``cd`` -ed into
.. when you ``workon myproject``.

あるいは、仮想環境を作成するプロジェクトを作ることもできますし、 ``$PROJECT_HOME`` の中にプロジェクトディレクトリを作ることもできます。これは ``workon myproject`` を実行するときに ``cd`` されます。

.. code-block:: console

   $ mkproject myproject

.. **virtualenvwrapper** provides tab-completion on environment names. It really
.. helps when you have a lot of environments and have trouble remembering their
.. names.

**virtualenvwrapper** は環境名にタブ補完を提供します。 多くの環境があり、名前を覚えていないときには本当に役に立ちます。

.. ``workon`` also deactivates whatever environment you are currently in, so you
.. can quickly switch between environments.

``workon`` は現在の環境を無効にするので、すばやく環境を切り替えることができます。

.. 3. Deactivating is still the same:

3.非アクティブ化はまだ同じです:

.. code-block:: console

   $ deactivate

.. 4. To delete:

4.削除するには:

.. code-block:: console

   $ rmvirtualenv venv

.. Other useful commands
.. ~~~~~~~~~~~~~~~~~~~~~

その他の便利なコマンド
~~~~~~~~~~~~~~~~~~~~~~

``lsvirtualenv``
  すべての環境をリストします。
..   List all of the environments.

``cdvirtualenv``
  現在アクティブ化されている仮想環境のディレクトリに移動します。たとえば :file:`site-packages` を参照できます。
..   Navigate into the directory of the currently activated virtual environment,
..   so you can browse its :file:`site-packages`, for example.

``cdsitepackages``
  上記と同様ですが、:file:`site-packages` ディレクトリに直接入ります。
..   Like the above, but directly into :file:`site-packages` directory.

``lssitepackages``
  :file:`site-packages` ディレクトリの内容を表示します。
..   Shows contents of :file:`site-packages` directory.

.. `Full list of virtualenvwrapper commands <https://virtualenvwrapper.readthedocs.io/en/latest/command_ref.html>`_.

`virtualenvwrapperコマンドの全リスト <https://virtualenvwrapper.readthedocs.io/en/latest/command_ref.html>`_ 。

virtualenv-burrito
------------------

.. With `virtualenv-burrito <https://github.com/brainsik/virtualenv-burrito>`_, you
.. can have a working virtualenv + virtualenvwrapper environment in a single command.

`virtualenv-burrito <https://github.com/brainsik/virtualenv-burrito>`_ を使うと、単一のコマンドでvirtualenv + virtualenvwrapper環境を利用することができます。

autoenv
-------
.. When you ``cd`` into a directory containing a :file:`.env`, `autoenv <https://github.com/kennethreitz/autoenv>`_
.. automagically activates the environment.

:file:`.env` を含むディレクトリに ``cd`` を実行すると、`autoenv <https://github.com/kennethreitz/autoenv>`_ が環境を自動的に起動します。

.. Install it on Mac OS X using ``brew``:

``brew`` を使ってMac OS Xにインストールしてください:

.. code-block:: console

   $ brew install autoenv

.. And on Linux:

Linuxでは:

.. code-block:: console

   $ git clone git://github.com/kennethreitz/autoenv.git ~/.autoenv
   $ echo 'source ~/.autoenv/activate.sh' >> ~/.bashrc
