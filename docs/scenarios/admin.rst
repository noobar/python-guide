.. Systems Administration
.. ======================

システム管理
============

Fabric
------

.. `Fabric <http://docs.fabfile.org>`_ is a library for simplifying system
.. administration tasks. While Chef and Puppet tend to focus on managing servers
.. and system libraries, Fabric is more focused on application level tasks such
.. as deployment.

`Fabric <http://docs.fabfile.org>`_ は、システム管理作業を簡素化するためのライブラリです。 ChefとPuppetはサーバやシステムライブラリの管理に専念する傾向がありますが、Fabricはデプロイメントなどのアプリケーションレベルのタスクにもっと重点を置いています。

Install Fabric:

.. code-block:: console

    $ pip install fabric

.. The following code will create two tasks that we can use: ``memory_usage`` and
.. ``deploy``. The former will output the memory usage on each machine. The
.. latter will ssh into each server, cd to our project directory, activate the
.. virtual environment, pull the newest codebase, and restart the application
.. server.

次のコードは、 ``memory_usage`` と ``deploy`` の2つのタスクを作成します。 前者は各マシンでメモリ使用量を出力します。 後者は各サーバにsshし、プロジェクトディレクトリにcdし、仮想環境を有効にし、最新のコードベースを取得して、アプリケーションサーバを再起動します。

.. code-block:: python

    from fabric.api import cd, env, prefix, run, task

    env.hosts = ['my_server1', 'my_server2']

    @task
    def memory_usage():
        run('free -m')

    @task
    def deploy():
        with cd('/var/www/project-env/project'):
            with prefix('. ../bin/activate'):
                run('git pull')
                run('touch app.wsgi')

.. With the previous code saved in a file named :file:`fabfile.py`, we can check
.. memory usage with:

以前のコードを :file:`fabfile.py` という名前のファイルに保存すると、次のようにメモリ使用量を確認できます。

.. code-block:: console

    $ fab memory_usage
    [my_server1] Executing task 'memory'
    [my_server1] run: free -m
    [my_server1] out:              total     used     free   shared  buffers   cached
    [my_server1] out: Mem:          6964     1897     5067        0      166      222
    [my_server1] out: -/+ buffers/cache:     1509     5455
    [my_server1] out: Swap:            0        0        0

    [my_server2] Executing task 'memory'
    [my_server2] run: free -m
    [my_server2] out:              total     used     free   shared  buffers   cached
    [my_server2] out: Mem:          1666      902      764        0      180      572
    [my_server2] out: -/+ buffers/cache:      148     1517
    [my_server2] out: Swap:          895        1      894

.. and we can deploy with:

我々は次のものと共に展開できます:

.. code-block:: console

    $ fab deploy

.. Additional features include parallel execution, interaction with remote
.. programs, and host grouping.

追加機能には、パラレル実行、リモートプログラムとの対話、およびホストグルーピングが含まれます。

    `Fabric Documentation <http://docs.fabfile.org>`_

Salt
----

.. `Salt <http://saltstack.org/>`_ is an open source infrastructure management
.. tool.  It supports remote command execution from a central point (master host)
.. to multiple hosts (minions). It also supports system states which can be used
.. to configure multiple servers using simple template files.

`Salt <http://saltstack.org/>`_ はオープンソースのインフラ管理ツールです。これは、中心点（マスターホスト）から複数のホスト（下位）へのリモートコマンド実行をサポートします。また、シンプルなテンプレートファイルを使用して複数のサーバーを構成するために使用できるシステム状態もサポートしています。

.. Salt supports Python versions 2.6 and 2.7 and can be installed via pip:

SaltはPythonバージョン2.6と2.7をサポートしており、pip経由でインストールできます:

.. code-block:: console

    $ pip install salt

.. After configuring a master server and any number of minion hosts, we can run
.. arbitrary shell commands or use pre-built modules of complex commands on our
.. minions.

マスターサーバーと任意の数のminionホストを設定したら、任意のシェルコマンドを実行するか、複雑なコマンドの既成モジュールをminionで使用できます。

.. The following command lists all available minion hosts, using the ping module.

次のコマンドは、pingモジュールを使用して利用可能なすべてのminionホストを一覧表示します。

.. code-block:: console

    $ salt '*' test.ping

.. The host filtering is accomplished by matching the minion id,
.. or using the grains system. The
.. `grains <http://docs.saltstack.org/en/latest/topics/targeting/grains.html>`_
.. system uses static host information like the operating system version or the
.. CPU architecture to provide a host taxonomy for the Salt modules.

ホストフィルタリングは、minion idを一致させるか、またはgrainシステムを使用して行います。 `grains <http://docs.saltstack.org/ja/latest/topics/targeting/grains.html>`_ システムは、オペレーティングシステムのバージョンまたはCPUアーキテクチャのような静的ホスト情報を使用して、Saltモジュールのホスト分類を提供します。

.. The following command lists all available minions running CentOS using the
.. grains system:

次のコマンドは、grainsシステムを使用してCentOSを実行している利用可能なすべてのminionを一覧表示します。

.. code-block:: console

    $ salt -G 'os:CentOS' test.ping

.. Salt also provides a state system. States can be used to configure the minion
.. hosts.

Saltはまた、状態システムを提供する。 状態を使用してminionホストを構成することができます。

.. For example, when a minion host is ordered to read the following state file,
.. it will install and start the Apache server:

たとえば、minionホストが次の状態ファイルを読み込むように指示されると、Apacheサーバーがインストールされ、起動されます。

.. code-block:: yaml

    apache:
      pkg:
        - installed
      service:
        - running
        - enable: True
        - require:
          - pkg: apache

.. State files can be written using YAML, the Jinja2 template system or pure Python.

状態ファイルは、YAML、Jinja2テンプレートシステムまたは純粋なPythonを使用して記述することができます。

    `Salt Documentation <http://docs.saltstack.com>`_


Psutil
------

.. `Psutil <https://github.com/giampaolo/psutil/>`_ is an interface to different
.. system information (e.g. CPU, memory, disks, network, users and processes).

`Psutil <https://github.com/giampaolo/psutil/>`_ は、異なるシステム情報（例えば、CPU、メモリ、ディスク、ネットワーク、ユーザ、プロセス）へのインタフェースです。

.. Here is an example to be aware of some server overload. If any of the
.. tests (net, CPU) fail, it will send an email.

ここでは、サーバーの過負荷を認識するための例を示します。 いずれかのテスト（ネット、CPU）が失敗すると、電子メールが送信されます。

.. code-block:: python

    # Functions to get system values:
    from psutil import cpu_percent, net_io_counters
    # Functions to take a break:
    from time import sleep
    # Package for email services:
    import smtplib
    import string
    MAX_NET_USAGE = 400000
    MAX_ATTACKS = 4
    attack = 0
    counter = 0
    while attack <= MAX_ATTACKS:
        sleep(4)
        counter = counter + 1
        # Check the cpu usage
        if cpu_percent(interval = 1) > 70:
            attack = attack + 1
        # Check the net usage
        neti1 = net_io_counters()[1]
        neto1 = net_io_counters()[0]
        sleep(1)
        neti2 = net_io_counters()[1]
        neto2 = net_io_counters()[0]
        # Calculate the bytes per second
        net = ((neti2+neto2) - (neti1+neto1))/2
        if net > MAX_NET_USAGE:
            attack = attack + 1
        if counter > 25:
            attack = 0
            counter = 0
    # Write a very important email if attack is higher than 4
    TO = "you@your_email.com"
    FROM = "webmaster@your_domain.com"
    SUBJECT = "Your domain is out of system resources!"
    text = "Go and fix your server!"
    BODY = string.join(("From: %s" %FROM,"To: %s" %TO,"Subject: %s" %SUBJECT, "",text), "\r\n")
    server = smtplib.SMTP('127.0.0.1')
    server.sendmail(FROM, [TO], BODY)
    server.quit()


.. A full terminal application like a widely extended top which is based on
.. psutil and with the ability of a client-server monitoring is
.. `glance <https://github.com/nicolargo/glances/>`_.

psutilとクライアント/サーバ監視の能力をベースにした、広く拡張されたtopのようなフル端末アプリケーションは `glance <https://github.com/nicolargo/glances/>`_ です。

Ansible
-------

.. `Ansible <http://ansible.com/>`_  is an open source system automation tool.
.. The biggest advantage over Puppet or Chef is it does not require an agent on
.. the client machine. Playbooks are Ansible’s configuration, deployment, and
.. orchestration language and are written in YAML with Jinja2 for templating.

`Ansible <http://ansible.com/>`_ はオープンソースのシステム自動化ツールです。 Puppet や Chef に比べて最大の利点は、クライアントマシンにエージェントを必要としないことです。 PlayBook は Ansible の設定、デプロイメント、オーケストレーション言語であり、YAMLでJinja2でテンプレート化されています。

.. Ansible supports Python versions 2.6 and 2.7 and can be installed via pip:

AnsibleはPythonバージョン2.6と2.7をサポートしており、pip経由でインストールできます:

.. code-block:: console

    $ pip install ansible

.. Ansible requires an inventory file that describes the hosts to which it has
.. access. Below is an example of a host and playbook that will ping all the
.. hosts in the inventory file.

Ansibleには、アクセス権のあるホストを記述するインベントリファイルが必要です。 以下は、インベントリファイル内のすべてのホストに対してpingを実行するホストとプレイブックの例です。

.. Here is an example inventory file:

次に、インベントリファイルの例を示します:
:file:`hosts.yml`

.. code-block:: yaml

    [server_name]
    127.0.0.1

.. Here is an example playbook:

ここでは、プレイブックの例です:
:file:`ping.yml`

.. code-block:: yaml

    ---
    - hosts: all

      tasks:
        - name: ping
          action: ping

.. To run the playbook:

プレイブックを実行するには:

.. code-block:: console

    $ ansible-playbook ping.yml -i hosts.yml --ask-pass

.. The Ansible playbook will ping all of the servers in the :file:`hosts.yml` file.
.. You can also select groups of servers using Ansible. For more information
.. about Ansible, read the `Ansible Docs <http://docs.ansible.com/>`_.

Ansibleのplaybookは :file:`hosts.yml` ファイル内のすべてのサーバにpingを実行します。また、Ansibleを使用してサーバーのグループを選択することもできます。 Ansibleの詳細については、 `Ansible Docs <http://docs.ansible.com/>`_ を参照してください。

.. `An Ansible tutorial <https://serversforhackers.com/an-ansible-tutorial/>`_ is also a 
.. great and detailed introduction to getting started with Ansible.

`An Ansible tutorial <https://serversforhackers.com/an-ansible-tutorial/>`_ も、Ansibleを使い始める上で非常に詳細な紹介です。


Chef
----
.. `Chef <https://www.chef.io/chef/>`_  is a systems and cloud infrastructure automation 
.. framework that makes it easy to deploy servers and applications to any physical, 
.. virtual, or cloud location. In case this is your choice for configuration management, 
.. you will primarily use Ruby to write your infrastructure code. 

`Chef <https://www.chef.io/chef/>`_ は、サーバーやアプリケーションを物理的、仮想的、またはクラウドの場所に簡単に展開できるシステムとクラウドインフラストラクチャの自動化フレームワークです。 これが設定管理のための選択である場合、主にRubyを使用してインフラストラクチャコードを記述します。

.. Chef clients run on every server that is part of your infrastructure and these regularly 
.. check with your Chef server to ensure your system is always aligned and represents the 
.. desired state. Since each individual server has its own distinct Chef client, each server 
.. configures itself and this distributed approach makes Chef a scalable automation platform.

Chefのクライアントは、インフラストラクチャの一部であるすべてのサーバー上で実行され、Chefサーバーと定期的にチェックして、システムが常に整列し、望ましい状態を表していることを確認します。 個々のサーバーにはそれぞれ独自のChefクライアントがあるため、各サーバーが構成され、この分散型アプローチによりシェフはスケーラブルな自動化プラットフォームになります。

.. Chef works by using custom recipes (configuration elements), implemented in cookbooks. Cookbooks, which are basically 
.. packages for infrastructure choices, are usually stored in your Chef server. 
.. Read the `Digital Ocean tutorial series 
.. <https://www.digitalocean.com/community/tutorials/how-to-install-a-chef-server-workstation-and-client-on-ubuntu-vps-instances>`_ 
.. on chef to learn how to create a simple Chef Server.

Chefは、クックブックで実装されたカスタムレシピ（構成要素）を使用して動作します。基本的にインフラストラクチャーの選択肢のパッケージであるクックブックは、通常Chefサーバーに保存されます。
`Digital Oceanチュートリアルシリーズ <https://www.digitalocean.com/community/tutorials/how-to-install-a-chef-server-workstation-and-client-on-ubuntu-vps-instances>`_ Chefの簡単なChefサーバーの作成方法を学びましょう。

.. To create a simple cookbook the `knife <https://docs.chef.io/knife.html>`_ command is used:

シンプルなクックブックを作成するには、 `knife <https://docs.chef.io/knife.html>`_ コマンドを使用します:

.. code-block:: console 

    knife cookbook create cookbook_name

.. `Getting started with Chef <http://gettingstartedwithchef.com/first-steps-with-chef.html>`_ 
.. is a good starting point for Chef Beginners and many community maintained cookbooks that can 
.. serve as a good reference or tweaked to serve your infrastructure configuration needs can be 
.. found on the `Chef Supermarket <https://supermarket.chef.io/cookbooks>`_.

`Getting started with Chef <http://gettingstartedwithchef.com/first-steps-with-chef.html>`_ は、Chefの初心者のための良い出発点であり、あなたのインフラストラクチャ構成のニーズを満たすために調整された良いリファレンスとして役立つことができる多くのコミュニティ管理された料理ブックは、`Chef Supermarket <https://supermarket.chef.io/cookbooks>`_ で見つけることができます。

- `Chef Documentation <https://docs.chef.io/>`_

Puppet
------

.. `Puppet <http://puppetlabs.com>`_ is IT Automation and configuration management
.. software from Puppet Labs that allows System Administrators to define the state
.. of their IT Infrastructure, thereby providing an elegant way to manage their
.. fleet of physical and virtual machines.

`Puppet <http://puppetlabs.com>`_ は、システム管理者がITインフラストラクチャの状態を定義できるようにする、PuppetラボのIT自動化および構成管理ソフトウェアであり、物理マシンと仮想マシンを管理するエレガントな方法を提供します。

.. Puppet is available both as an Open Source and an Enterprise variant. Modules
.. are small, shareable units of code written to automate or define the state of a
.. system.  `Puppet Forge <https://forge.puppetlabs.com/>`_ is a repository for
.. modules written by the community for Open Source and Enterprise Puppet.

Puppetはオープンソースとエンタープライズの両方で利用可能です。 モジュールは、システムの状態を自動化または定義するために書かれた、小さな、共有可能なコード単位です。 `Puppet Forge <https://forge.puppetlabs.com/>`_ は、オープンソースとエンタープライズPuppetのためにコミュニティによって書かれたモジュールのリポジトリです。

.. Puppet Agents are installed on nodes whose state needs to be monitored or
.. changed.  A designated server known as the Puppet Master is responsible for
.. orchestrating the agent nodes.

Puppetエージェントは、状態を監視または変更する必要があるノードにインストールされます。 Puppetマスターと呼ばれる指定されたサーバーは、エージェントノードの編成を担当します。

.. Agent nodes send basic facts about the system such as to the operating system,
.. kernel, architecture, ip address, hostname etc. to the Puppet Master.
.. The Puppet Master then compiles a catalog with information provided by the
.. agents on how each node should be configured and sends it to the agent. The
.. agent enforces the change as prescribed in the catalog and sends a report back
.. to the Puppet Master.

エージェントノードは、オペレーティングシステム、カーネル、アーキテクチャ、IPアドレス、ホスト名などの基本的な事実をPuppet Masterに送信します。 Puppet Masterは、エージェントが提供する情報でカタログをコンパイルし、各ノードをどのように設定してエージェントに送信するかを決定します。 エージェントは、カタログに記載されている変更を適用し、レポートをPuppet Masterに送り返します。

.. Facter is an interesting tool that ships with Puppet that pulls basic facts
.. about the system. These facts can be referenced as a variable while writing
.. your Puppet modules.

Facterは、Puppetに同梱されている、システムに関する基本的な事実を引き出す興味深いツールです。 これらのファクトは、Puppetモジュールを記述する際に変数として参照できます。

.. code-block:: console

    $ facter kernel
    Linux
.. code-block:: console

    $ facter operatingsystem
    Ubuntu  

.. Writing Modules in Puppet is pretty straight forward. Puppet Manifests together
.. form Puppet Modules. Puppet manifest end with an extension of ``.pp``.
.. Here is an example of 'Hello World' in Puppet.

Puppetにモジュールを書くことはかなり簡単です。 Puppetマニフェストが一緒にPuppetモジュールを形成します。 Puppetは ``.pp`` の拡張子を持つマニフェストを明示します。 Puppetの 'Hello World' の例を次に示します。

.. code-block:: puppet

    notify { 'This message is getting logged into the agent node':

        #As nothing is specified in the body the resource title
        #the notification message by default.
    }

.. Here is another example with system based logic. Note how the operating system
.. fact is being used as a variable prepended with the ``$`` sign. Similarly, this
.. holds true for other facts such as hostname which can be referenced by
.. ``$hostname``

システムベースのロジックを使用した別の例を次に示します。 オペレーティングシステムのファクトが、 ``$`` が付いた変数としてどのように使われているかに注意してください。 同様に、 ``$hostname`` で参照可能なホスト名のような他の事実にも当てはまります

.. code-block:: puppet

    notify{ 'Mac Warning':
        message => $operatingsystem ? {
            'Darwin' => 'This seems to be a Mac.',
            default  => 'I am a PC.',
        },
    }

.. There are several resource types for Puppet but the package-file-service
.. paradigm is all you need for undertaking majority of the configuration
.. management. The following Puppet code makes sure that the OpenSSH-Server
.. package is installed in a system and the sshd service is notified to restart
.. everytime the sshd configuration file is changed.

Puppetにはいくつかのリソースタイプがありますが、パッケージファイルサービスのパラダイムは、構成管理の大部分を行うために必要なものです。 次のPuppetコードは、OpenSSH-Serverパッケージがシステムにインストールされていることを確認し、sshd設定ファイルが変更されるたびにsshdサービスが再起動するように通知します。

.. code-block:: puppet

    package { 'openssh-server':
        ensure => installed,
    }

    file { '/etc/ssh/sshd_config':
        source   => 'puppet:///modules/sshd/sshd_config',
        owner    => 'root',
        group    => 'root',
        mode     => '640',
        notify   =>  Service['sshd'], # sshd will restart
                                      # whenever you edit this
                                      # file
        require  => Package['openssh-server'],

    }

    service { 'sshd':
        ensure    => running,
        enable    => true,
        hasstatus => true,
        hasrestart=> true,
    }

.. For more information, refer to the `Puppet Labs Documentation <http://docs.puppetlabs.com>`_

詳細については、 `Puppet Labsのドキュメント <http://docs.puppetlabs.com>`_

Blueprint
---------

.. .. todo:: Write about Blueprint

.. todo:: 青写真について書く

Buildout
--------

.. `Buildout <http://www.buildout.org>`_ is an open source software build tool.
.. Buildout is created using the Python programming language. It implements a 
.. principle of separation of configuration from the scripts that do the setting up.
.. Buildout is primarily used to download and set up dependencies in Python eggs
.. format of the software being developed or deployed. Recipes for build tasks in any
.. environment can be created, and many are already available.

`Buildout <http://www.buildout.org>`_ はオープンソースのソフトウェアビルドツールです。 Buildoutは、Pythonプログラミング言語を使用して作成されます。 設定を行うスクリプトと設定の分離の原則を実装しています。 Buildoutは主に、開発またはデプロイされるソフトウェアの Python eggs 形式で依存関係をダウンロードして設定するために使用されます。 どのような環境でもビルドタスクのためのレシピを作成することができ、すでに多数のレシピが利用可能です。

Shinken
-------

.. `Shinken <http://www.shinken-monitoring.org/>`_ is a modern, Nagios compatible
.. monitoring framework written in Python. Its main goal is to give users a flexible
.. architecture for their monitoring system that is designed to scale to large
.. environments.

`Shinken <http://www.shinken-monitoring.org/>`_ は、Pythonで書かれたモダンなNagios互換モニタリングフレームワークです。 その主な目的は、大規模な環境に合わせて設計された監視システムの柔軟なアーキテクチャをユーザに提供することです。

.. Shinken is backwards-compatible with the Nagios configuration standard, and
.. plugins.It works on any operating system, and architecture that supports Python
.. which includes Windows, GNU/Linux, and FreeBSD.

Shinkenは、Nagiosの設定標準とプラグインとの下位互換性があります。これは、Windows、GNU / Linux、FreeBSDを含むPythonをサポートする任意のオペレーティングシステムとアーキテクチャで動作します。
