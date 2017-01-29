.. Testing Your Code
.. =================

コードのテスト
==============

.. Testing your code is very important.

コードをテストすることは非常に重要です。

.. Getting used to writing testing code and running this code in parallel is now 
.. considered a good habit. Used wisely, this method helps you define more
.. precisely your code's intent and have a more decoupled architecture.

テストコードを書くことに慣れ、このコードを並行して実行することは、現在、良い習慣と考えられています。この方法は賢明に使用され、コードの意図をより正確に定義し、より分離されたアーキテクチャを持つのに役立ちます。

.. Some general rules of testing:

いくつかの一般的なテストのルール:

.. - A testing unit should focus on one tiny bit of functionality and prove it
..   correct.

- テストユニットは1つの機能のほんの少しに集中し、それが正しいことを証明する必要があります。

.. - Each test unit must be fully independent. Each test must be able to run
..   alone, and also within the test suite, regardless of the order that they are
..   called. The implication of this rule is that each test must be loaded with
..   a fresh dataset and may have to do some cleanup afterwards. This is
..   usually handled by :meth:`setUp()` and :meth:`tearDown()` methods.

- 各試験ユニットは完全に独立していなければなりません。各テストは、呼び出される順番に関係なく、単独で実行できなければならず、テストスイート内でも実行できなければなりません。このルールの意味は、各テストに新しいデータセットがロードされていなければならず、後で何らかのクリーンアップを行わなければならない可能性があるということです。これは通常 :meth:`setUp()` と :meth:`tearDown()` メソッドで処理されます。

.. - Try hard to make tests that run fast. If one single test needs more than a
..   few milliseconds to run, development will be slowed down or the tests will
..   not be run as often as is desirable. In some cases, tests can't be fast
..   because they need a complex data structure to work on, and this data structure
..   must be loaded every time the test runs. Keep these heavier tests in a
..   separate test suite that is run by some scheduled task, and run all other
..   tests as often as needed.

- テストを高速化するのは難しいです。 1回のテストに数ミリ秒以上の時間がかかる場合は、開発が遅くなるか、またはテストが望ましいほど頻繁に実行されません。場合によっては、複雑なデータ構造が必要であり、テストが実行されるたびにこのデータ構造をロードする必要があるため、テストを高速化することはできません。これらのより重いテストは、スケジュールされたタスクによって実行される別のテストスイートに保管し、必要に応じて他のすべてのテストを頻繁に実行します。

.. - Learn your tools and learn how to run a single test or a test case. Then,
..   when developing a function inside a module, run this function's tests 
..   frequently, ideally automatically when you save the code.

- あなたのツールを学び、単一のテストまたはテストケースを実行する方法を学びます。 次に、モジュール内の関数を開発するときは、この関数のテストを頻繁に、理想的にはコードを保存すると自動的に実行します。

.. - Always run the full test suite before a coding session, and run it again
..   after. This will give you more confidence that you did not break anything
..   in the rest of the code.

- コーディングセッションの前に常に完全なテストスイートを実行してから、それをやり直してください。 これにより、残りのコードで何も壊れていないという確信が得られます。

.. - It is a good idea to implement a hook that runs all tests before pushing
..   code to a shared repository.

- コードを共有リポジトリにプッシュする前に、すべてのテストを実行するフックを実装することをお勧めします。

.. - If you are in the middle of a development session and have to interrupt
..   your work, it is a good idea to write a broken unit test about what you
..   want to develop next. When coming back to work, you will have a pointer
..   to where you were and get back on track faster.

- 開発セッションの途中で作業を中断しなければならない場合は、次に開発したいものについて壊れた単体テストを書くことをお勧めします。開発作業に戻ったときに、中断した続きへポインタを持っていくことができ、すぐに軌道に乗れるでしょう。

.. - The first step when you are debugging your code is to write a new test
..   pinpointing the bug. While it is not always possible to do, those bug
..   catching tests are among the most valuable pieces of code in your project.

- コードをデバッグする最初のステップは、バグを特定する新しいテストを書くことです。必ずしもそうであるとは限りませんが、これらのバグを捕まえるテストは、プロジェクトの中で最も価値のあるコードです。

.. - Use long and descriptive names for testing functions. The style guide here
..   is slightly different than that of running code, where short names are
..   often preferred. The reason is testing functions are never called explicitly.
..   ``square()`` or even ``sqr()`` is ok in running code, but in testing code you
..   would have names such as ``test_square_of_number_2()``,
..   ``test_square_negative_number()``. These function names are displayed when
..   a test fails, and should be as descriptive as possible.

- テスト関数には長い記述的な名前を使用します。ここのスタイルガイドは、短い名前がしばしば好まれる実行コードとは少し異なります。なぜなら、テスト関数は決して明示的に呼び出されないからです。実行中のコードで ``square()`` や ``sqr()`` でもOKですが、テストコードでは ``test_square_of_number_2()``, ``test_square_negative_number()`` などの名前を使用します。これらの関数名は、テストが失敗したときに表示され、可能な限り説明的でなければなりません。

.. - When something goes wrong or has to be changed, and if your code has a
..   good set of tests, you or other maintainers will rely largely on the
..   testing suite to fix the problem or modify a given behavior. Therefore
..   the testing code will be read as much as or even more than the running
..   code. A unit test whose purpose is unclear is not very helpful in this
..   case.

- 何かがうまくいかなかったり、変更が必要な場合、コードに適切なテストセットがある場合、あなたや他のメンテナはテストスイートに大きく依存して、問題を修正したり、特定の動作を修正します。 したがって、テストコードは、実行中のコードと同じくらい、あるいはそれ以上に読み込まれます。 その目的がはっきりしない単体テストは、この場合はあまり役に立ちません。

.. - Another use of the testing code is as an introduction to new developers. When
..   someone will have to work on the code base, running and reading the related
..   testing code is often the best thing that they can do to start. They will 
..   or should discover the hot spots, where most difficulties arise, and the 
..   corner cases. If they have to add some functionality, the first step should 
..   be to add a test to ensure that the new functionality is not already a 
..   working path that has not been plugged into the interface.

- テストコードのもう1つの使用方法は、新しい開発者を紹介することです。誰かがコードベースで作業しなければならない場合、関連するテストコードを実行して読むことが、しばしば彼らが始めるためにできる最善のことです。彼らは、最も困難が発生するホットスポット、およびコーナーケースを発見するでしょう。いくつかの機能を追加する必要がある場合は、最初にテストを追加して、新しい機能がインターフェイスにプラグインされていない現用パスでないことを確認します。

.. The Basics
.. ::::::::::

基本
::::


.. Unittest
.. --------

ユニットテスト
--------------

.. :mod:`unittest` is the batteries-included test module in the Python standard
.. library. Its API will be familiar to anyone who has used any of the
.. JUnit/nUnit/CppUnit series of tools.

:mod:`unittest` は、Pythonの標準ライブラリに含まれるバッテリー同梱のテストモジュールです。 そのAPIは、JUnit/nUnit/CppUnitシリーズのいずれかを使用している人にとっては馴染み深いものです。

.. Creating test cases is accomplished by subclassing :class:`unittest.TestCase`.

テストケースを作成するには、:class:`unittest.TestCase` をサブクラス化します。

.. code-block:: python

    import unittest

    def fun(x):
        return x + 1

    class MyTest(unittest.TestCase):
        def test(self):
            self.assertEqual(fun(3), 4)

.. As of Python 2.7 unittest also includes its own test discovery mechanisms.

Python 2.7の時点で、unittestには独自のテスト検出メカニズムも含まれています。

..     `unittest in the standard library documentation <http://docs.python.org/library/unittest.html>`_

    `標準ライブラリのドキュメントのunittest <http://docs.python.org/library/unittest.html>`_


Doctest
-------

.. The :mod:`doctest` module searches for pieces of text that look like interactive
.. Python sessions in docstrings, and then executes those sessions to verify that
.. they work exactly as shown.

:mod:`doctest` モジュールは、ドキュメンテーション文字列中のインタラクティブなPythonセッションのように見えるテキストを検索し、それらのセッションを実行して、表示されているとおりに動作することを確認します。

.. Doctests have a different use case than proper unit tests: they are usually
.. less detailed and don't catch special cases or obscure regression bugs. They
.. are useful as an expressive documentation of the main use cases of a module and
.. its components. However, doctests should run automatically each time the full
.. test suite runs.

Doctestは、適切な単体テストとは異なるユースケースを持っています。通常、それは詳細は少なく、特殊なケースやあいまいな回帰バグは検出されません。 これらは、モジュールとそのコンポーネントの主な使用例を表現した文書として役立ちます。 ただし、doctestは、完全なテストスイートが実行されるたびに自動的に実行されます。

.. A simple doctest in a function:

関数内の簡単なdoctest:

.. code-block:: python

    def square(x):
        """Return the square of x.

        >>> square(2)
        4
        >>> square(-2)
        4
        """

        return x * x

    if __name__ == '__main__':
        import doctest
        doctest.testmod()

.. When running this module from the command line as in ``python module.py``, the
.. doctests will run and complain if anything is not behaving as described in the
.. docstrings.

``python module.py`` のようにコマンドラインからこのモジュールを実行すると、doctestは実行され、docstringに記述されているように動作していないものがあれば文句を言います。

.. Tools
.. :::::

ツール
::::::


py.test
-------

.. py.test is a no-boilerplate alternative to Python's standard unittest module.

py.testは、Pythonの標準的なunittestモジュールに代わるものではありません。

.. code-block:: console

    $ pip install pytest

.. Despite being a fully-featured and extensible test tool, it boasts a simple
.. syntax. Creating a test suite is as easy as writing a module with a couple of
.. functions:

完全に機能し、拡張可能なテストツールであるにもかかわらず、簡単な構文です。 テストスイートを作成するのは、以下の2つの機能を持つモジュールを作成するのと同じくらい簡単です。

.. code-block:: python

    # content of test_sample.py
    def func(x):
        return x + 1

    def test_answer():
        assert func(3) == 5

.. and then running the `py.test` command

`py.test` コマンドを実行します

.. code-block:: console

    $ py.test
    =========================== test session starts ============================
    platform darwin -- Python 2.7.1 -- pytest-2.2.1
    collecting ... collected 1 items

    test_sample.py F

    ================================= FAILURES =================================
    _______________________________ test_answer ________________________________

        def test_answer():
    >       assert func(3) == 5
    E       assert 4 == 5
    E        +  where 4 = func(3)

    test_sample.py:5: AssertionError
    ========================= 1 failed in 0.02 seconds =========================

.. is far less work than would be required for the equivalent functionality with
.. the unittest module!

unittestモジュールと同等の機能に必要な作業よりはるかに少ない作業です！

    `py.test <http://pytest.org/latest/>`_


Nose
----

.. nose extends unittest to make testing easier.

noseはunittestを拡張してテストを容易にします。


.. code-block:: console

    $ pip install nose

.. nose provides automatic test discovery to save you the hassle of manually
.. creating test suites. It also provides numerous plugins for features such as
.. xUnit-compatible test output, coverage reporting, and test selection.

noseは、テストスイートを手動で作成する手間を省くための自動テスト検出機能を提供します。 また、xUnitと互換性のあるテスト出力、カバレッジレポート、テストの選択など、多数のプラグインを提供します。

    `nose <https://nose.readthedocs.io/en/latest/>`_


tox
---

.. tox is a tool for automating test environment management and testing against
.. multiple interpreter configurations

toxは、テスト環境の管理を自動化し、複数のインタープリタ構成に対してテストするためのツールです

.. code-block:: console

    $ pip install tox

.. tox allows you to configure complicated multi-parameter test matrices via a
.. simple ini-style configuration file.

toxを使用すると、単純なini形式の構成ファイルを使用して、複雑な複数パラメータのテスト行列を構成できます。

    `tox <https://tox.readthedocs.io/en/latest/>`_


Unittest2
---------

.. unittest2 is a backport of Python 2.7's unittest module which has an improved
.. API and better assertions over the one available in previous versions of Python.

unittest2は、Python 2.7のunittestモジュールのバックポートであり、改良されたAPIと以前のバージョンのPythonよりも優れたアサーションを備えています。

.. If you're using Python 2.6 or below, you can install it with pip

Python 2.6以降を使用している場合は、pipでインストールできます

.. code-block:: console

    $ pip install unittest2

.. You may want to import the module under the name unittest to make porting code
.. to newer versions of the module easier in the future

将来的にモジュールの新しいバージョンへの移植コードをより簡単にするために、unittestという名前でモジュールをインポートすることができます

.. code-block:: python

    import unittest2 as unittest

    class MyTest(unittest.TestCase):
        ...

.. This way if you ever switch to a newer Python version and no longer need the
.. unittest2 module, you can simply change the import in your test module without
.. the need to change any other code.

こうすることで、新しいPythonバージョンに切り替えてunittest2モジュールが不要になった場合でも、他のコードを変更することなくテストモジュールのインポートを変更することができます。

    `unittest2 <http://pypi.python.org/pypi/unittest2>`_


mock
----

.. :mod:`unittest.mock` is a library for testing in Python. As of Python 3.3, it is
.. available in the
.. `standard library <https://docs.python.org/dev/library/unittest.mock>`_.

:mod:`unittest.mock` はPythonでテストするためのライブラリです。 Python 3.3以降、これは `標準ライブラリ <https://docs.python.org/dev/library/unittest.mock>`_ で利用可能です。

.. For older versions of Python:

古いバージョンのPythonの場合:

.. code-block:: console

    $ pip install mock

.. It allows you to replace parts of your system under test with mock objects and
.. make assertions about how they have been used.

テスト中のシステムの一部をモックオブジェクトに置き換え、それらがどのように使用されたかをアサーションすることができます。

For example, you can monkey-patch a method:

.. code-block:: python

    from mock import MagicMock
    thing = ProductionClass()
    thing.method = MagicMock(return_value=3)
    thing.method(3, 4, 5, key='value')

    thing.method.assert_called_with(3, 4, 5, key='value')

.. To mock classes or objects in a module under test, use the ``patch`` decorator.
.. In the example below, an external search system is replaced with a mock that
.. always returns the same result (but only for the duration of the test).

テスト中のモジュールのクラスやオブジェクトをモックするには、 ``patch`` デコレータを使います。 以下の例では、外部検索システムが、常に同じ結果を返すモック（ただし、テストの期間のみ）に置き換えられています。

.. code-block:: python

    def mock_search(self):
        class MockSearchQuerySet(SearchQuerySet):
            def __iter__(self):
                return iter(["foo", "bar", "baz"])
        return MockSearchQuerySet()

    # SearchForm here refers to the imported class reference in myapp,
    # not where the SearchForm class itself is imported from
    @mock.patch('myapp.SearchForm.search', mock_search)
    def test_new_watchlist_activities(self):
        # get_search_results runs a search and iterates over the result
        self.assertEqual(len(myapp.get_search_results(q="fish")), 3)

.. Mock has many other ways you can configure it and control its behavior.

Mockには他の多くの方法があります。

    `mock <http://www.voidspace.org.uk/python/mock/>`_

