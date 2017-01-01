.. _pip-virtualenv:

.. Further Configuration of Pip and Virtualenv
.. ===========================================

PipとVirtualenvの詳細設定
=========================

.. Requiring an active virtual environment for ``pip``
.. ---------------------------------------------------

``pip`` にアクティブな仮想環境が必要です
----------------------------------------

.. By now it should be clear that using virtual environments is a great way to
.. keep your development environment clean and keeping different projects'
.. requirements separate.

今では、仮想環境を使用すると、開発環境をきれいに保ち、異なるプロジェクトの要件を別々に保つことができます。

.. When you start working on many different projects, it can be hard to remember to
.. activate the related virtual environment when you come back to a specific
.. project.  As a result of this, it is very easy to install packages globally
.. while thinking that you are actually installing the package for the virtual
.. environment of the project. Over time this can result in a messy global package
.. list.

多くの異なるプロジェクトで作業を開始すると、特定のプロジェクトに戻ったときに関連する仮想環境をアクティブにすることを覚えにくくなる可能性があります。 その結果、プロジェクトの仮想環境用のパッケージを実際にインストールしていると考えながら、パッケージをグローバルにインストールするのは非常に簡単です。 時間が経つにつれて、これは不吉なグローバルパッケージリストになる可能性があります。

.. In order to make sure that you install packages to your active virtual
.. environment when you use ``pip install``, consider adding the following
.. line to your :file:`~/.bashrc` file:

``pip install`` を使うときにあなたのアクティブな仮想環境にパッケージをインストールするために、あなたの :file:`~/.bashrc` ファイルに次の行を追加することを検討してください:

.. code-block:: console

    export PIP_REQUIRE_VIRTUALENV=true

.. After saving this change and sourcing the :file:`~/.bashrc` file with
.. ``source ~/.bashrc``, pip will no longer let you install packages if you are not
.. in a virtual environment.  If you try to use ``pip install`` outside of a
.. virtual environment pip will gently remind you that an activated virtual
.. environment is needed to install packages.

この変更を保存し、 :file:`~/.bashrc` ファイルを ``source ~/.bashrc`` で取得した後、仮想環境にいない場合、pipはインストールできなくなります。 仮想環境の外側で ``pip install`` を実行しようとすると、パッケージをインストールするためには、起動された仮想環境が必要であることを丁寧に思い出させます。

.. code-block:: console

    $ pip install requests
    Could not find an activated virtualenv (required).

.. You can also do this configuration by editing your :file:`pip.conf` or
.. :file:`pip.ini` file. :file:`pip.conf` is used by Unix and Mac OS X operating
.. systems and it can be found at:

:file:`pip.conf` または :file:`pip.ini` ファイルを編集することで、この設定を行うこともできます。 :file:`pip.conf` はUnixとMac OS Xのオペレーティングシステムで使われています。

.. code-block:: console

    $HOME/.pip/pip.conf

.. Similarly, the :file:`pip.ini` file is used by Windows operating systems and it
.. can be found at:

同様に、:file:`pip.ini` ファイルはWindowsオペレーティングシステムで使用されています。

.. code-block:: console

    %HOME%\pip\pip.ini

.. If you don't have a :file:`pip.conf` or :file:`pip.ini` file at these locations,
.. you can create a new file with the correct name for your operating system.

これらの場所に :file:`pip.conf` または :file:`pip.ini` ファイルがない場合は、オペレーティングシステムの正しい名前で新しいファイルを作成することができます。

.. If you already have a configuration file, just add the following line under the
.. ``[global]`` settings to require an active virtual environment:

すでに設定ファイルがある場合は、``[global]`` の設定の下に次の行を追加して、アクティブな仮想環境が必要になります:

.. code-block:: console

    require-virtualenv = true

.. If you did not have a configuration file, you will need to create a new one and
.. add the following lines to this new file:
設定ファイルがない場合は、新しいファイルを作成し、次の行をこの新しいファイルに追加する必要があります:

.. code-block:: console

    [global]
    require-virtualenv = true


.. You will of course need to install some packages globally (usually ones that
.. you use across different projects consistently) and this can be accomplished by
.. adding the following to your :file:`~/.bashrc` file:

もちろん、いくつかのパッケージをグローバルにインストールする必要があります（通常は異なるプロジェクト間で一貫して使用するパッケージをインストールする必要があります） :file:`~/.bashrc` ファイルに以下を追加することで実現できます:

.. code-block:: console

    gpip() {
        PIP_REQUIRE_VIRTUALENV="" pip "$@"
    }

.. After saving the changes and sourcing your :file:`~/.bashrc` file you can now
.. install packages globally by running ``gpip install``. You can change the name
.. of the function to anything you like, just keep in mind that you will have to
.. use that name when trying to install packages globally with pip.

変更を保存して :file:`~/.bashrc` ファイルを入手したら、``gpip install`` を実行してパッケージをグローバルにインストールできます。 関数の名前を好きなものに変更することができます.pipを使ってパッケージをグローバルにインストールしようとするときにその名前を使用する必要があることに留意してください。

.. Caching packages for future use
.. -------------------------------

将来の使用のためのパッケージのキャッシュ
----------------------------------------

.. Every developer has preferred libraries and when you are working on a lot of
.. different projects, you are bound to have some overlap between the libraries
.. that you use. For example, you may be using the ``requests`` library in a lot
.. of different projects.

すべての開発者は優先ライブラリを持っており、多くの異なるプロジェクトで作業しているときは、使用するライブラリ間で重複することになります。 たとえば、多くの異なるプロジェクトで ``requests`` ライブラリを使用しているかもしれません。

.. It is surely unnecessary to re-download the same packages/libraries each time
.. you start working on a new project (and in a new virtual environment as a result).
.. Fortunately, you can configure pip in such a way that it tries to reuse already
.. installed packages.

新しいプロジェクト（および結果として新しい仮想環境）での作業を開始するたびに、同じパッケージ/ライブラリを再ダウンロードする必要はありません。 幸いにも、既にインストールされているパッケージを再利用するようにpipを設定することができます。

.. On UNIX systems, you can add the following line to your :file:`.bashrc` or
.. :file:`.bash_profile` file.

UNIXシステムでは、次の行を :file:`.bashrc` または :file:`.bash_profile` ファイルに追加することができます。

.. code-block:: console

    export PIP_DOWNLOAD_CACHE=$HOME/.pip/cache

.. You can set the path to anywhere you like (as long as you have write
.. access). After adding this line, ``source`` your :file:`.bashrc`
.. (or :file:`.bash_profile`) file and you will be all set.

パスを好きな場所に設定することができます（書き込みアクセス権がある限り）。 この行を追加した後、 :file:`.bashrc` （または :file:`.bash_profile` ）ファイルを ``source`` して、あなたはすべて設定されます。

.. Another way of doing the same configuration is via the :file:`pip.conf` or
.. :file:`pip.ini` files, depending on your system. If you are on Windows, you can
.. add the following line to your :file:`pip.ini` file under ``[global]`` settings:

同じ設定を行う別の方法は、あなたのシステムに応じて :file:`pip.conf` または :file:`pip.ini` ファイルを使用することです。 Windowsの場合は、 ``[global]`` 設定の下で :file:`pip.ini` ファイルに以下の行を追加することができます:

.. code-block:: console

    download-cache = %HOME%\pip\cache

.. Similarly, on UNIX systems you should simply add the following line to your
.. :file:`pip.conf` file under ``[global]`` settings:

同様に、UNIXシステムでは、``[global]`` 設定の下で :file:`pip.conf` ファイルに以下の行を追加するだけです:

.. code-block:: console

    download-cache = $HOME/.pip/cache

.. Even though you can use any path you like to store your cache, it is recommended
.. that you create a new folder *in* the folder where your :file:`pip.conf` or
.. :file:`pip.ini` file lives. If you don't trust yourself with all of this path
.. voodoo, just use the values provided here and you will be fine.

キャッシュを保存するのに好きなパスを使用することはできますが、:file:`pip.conf` または :file:`pip.ini` ファイルが存在するフォルダに新しいフォルダ*を作成することをお勧めします。 あなたがこのパス・ブードゥーのすべてを信頼しない場合は、ここで提供されている値を使用すれば問題ありません。
