.. Continuous Integration
.. ======================

継続的な統合
============


.. Why?
.. ----

どうして？
----------

.. Martin Fowler, who first wrote about `Continuous Integration <http://martinfowler.com/articles/continuousIntegration.html>`_
.. (short: CI) together with Kent Beck, describes the CI as follows:

Kent Beckと一緒に `Continuous Integration <http://martinfowler.com/articles/continuousIntegration.html>`_ （ショート：CI）」を初めて書いたMartin Fowlerは、CIについて次のように説明しています。

    継続的統合とは、チームのメンバーが頻繁に作業を統合するソフトウェア開発のことで、通常は1日に少なくとも1人は統合し、1日に複数の統合につながります。 各統合は、自動化ビルド（テストを含む）によって検証され、統合エラーを可能な限り迅速に検出します。 多くのチームでは、このアプローチにより統合の問題が大幅に軽減され、チームが一貫性のあるソフトウェアをより迅速に開発できるようになりました。

..     Continuous Integration is a software development practice where members of
..     a team integrate their work frequently, usually each person integrates at
..     least daily - leading to multiple integrations per day. Each integration is
..     verified by an automated build (including test) to detect integration errors
..     as quickly as possible. Many teams find that this approach leads to
..     significantly reduced integration problems and allows a team to develop
..     cohesive software more rapidly.


Jenkins
-------

.. `Jenkins CI <http://jenkins-ci.org>`_ is an extensible continuous integration
.. engine. Use it.

`Jenkins CI <http://jenkins-ci.org>`_ は、拡張可能な継続的統合エンジンです。 これを使って。



Buildbot
--------

.. `Buildbot <http://docs.buildbot.net/current/>`_ is a Python system to
.. automate the compile/test cycle to validate code changes.

`Buildbot <http://docs.buildbot.net/current/>`_ はコードの変更を検証するためのコンパイル/テストサイクルを自動化するPythonシステムです。



Tox
---

.. `tox <https://tox.readthedocs.io/en/latest/>`_ is an automation tool providing
.. packaging, testing and deployment of Python software right from the console or
.. CI server. It is a generic virtualenv management and test command line tool
.. which provides the following features:

`tox <https://tox.readthedocs.io/en/latest/>`_ は、コンソールやCIサーバからPythonソフトウェアをパッケージ化、テスト、デプロイするオートメーションツールです。これは、以下の機能を提供する汎用の仮想管理およびテストコマンドラインツールです。

.. * Checking that packages install correctly with different Python versions and
..   interpreters
.. * Running tests in each of the environments, configuring your test tool of
..   choice
.. * Acting as a front-end to Continuous Integration servers, reducing boilerplate
..   and merging CI and shell-based testing.

* 異なるPythonのバージョンとインタプリタでパッケージが正しくインストールされていることを確認する
* 各環境でのテストの実行、テストツールの選択
* Continuous Integrationサーバーのフロントエンドとして機能し、定型文を削減し、CIおよびシェルベースのテストをマージします。


Travis-CI
---------

.. `Travis-CI <https://travis-ci.org/>`_ is a distributed CI server which builds
.. tests for open source projects for free. It provides multiple workers to run
.. Python tests on and seamlessly integrates with GitHub. You can even have it
.. comment on your Pull Requests whether this particular changeset breaks the
.. build or not. So if you are hosting your code on GitHub, travis-ci is a great
.. and easy way to get started with Continuous Integration.

`Travis-CI <https://travis-ci.org/>`_ はオープンソースプロジェクトのテストを無料でビルドする分散型CIサーバです。 Pythonテストを実行する複数のワーカーを提供し、GitHubとシームレスに統合します。 この特定のチェンジセットがビルドを破るかどうかは、Pull Requestにコメントすることさえできます。 したがって、GitHubでコードをホストしている場合、travis-ciはContinuous Integrationを使い始めることができます。

.. In order to get started, add a :file:`.travis.yml` file to your repository with
.. this example content::

開始するには、この例のコンテンツで、 :file:`.travis.yml` ファイルをリポジトリに追加してください::

    language: python
    python:
      - "2.6"
      - "2.7"
      - "3.2"
      - "3.3"
    # command to install dependencies
    script: python tests/test_all_of_the_units.py
    branches:
      only:
        - master


.. This will get your project tested on all the listed Python versions by
.. running the given script, and will only build the master branch. There are a
.. lot more options you can enable, like notifications, before and after steps
.. and much more. The `travis-ci docs <http://about.travis-ci.org/docs/>`_
.. explain all of these options, and are very thorough.

これにより、指定されたスクリプトを実行することによってリストされたすべてのPythonバージョンでプロジェクトがテストされ、マスターブランチのみがビルドされます。 通知や前後の手順など、さらに多くのオプションを有効にすることができます。 `travis-ci docs <http://about.travis-ci.org/docs/>`_ はこれらすべてのオプションを説明しており、非常に徹底的です。

.. In order to activate testing for your project, go to `the travis-ci site <https://travis-ci.org/>`_
.. and login with your GitHub account. Then activate your project in your
.. profile settings and you're ready to go. From now on, your project's tests
.. will be run on every push to GitHub.

プロジェクトのテストを有効にするには、 `travis-ci site <https://travis-ci.org/>`_ に行き、あなたのGitHubアカウントでログインしてください。次に、あなたのプロファイル設定でプロジェクトをアクティブにし、あなたが移動する準備が整いました。 これから、あなたのプロジェクトのテストはすべてのGitHubへのプッシュで実行されます。
