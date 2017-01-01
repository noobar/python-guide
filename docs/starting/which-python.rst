.. Picking an Interpreter
.. ======================

インタプリタの選択
==================

.. _which-python:

.. The State of Python (3 & 2)
.. ~~~~~~~~~~~~~~~~~~~~~~~~~~~

Pythonの状態（3＆2）
~~~~~~~~~~~~~~~~~~~

.. When choosing a Python interpreter, one looming question is always present:
.. "Should I choose Python 2 or Python 3"? The answer is a bit more subtle than
.. one might think.

Pythonインタプリタを選択するときには、"Python 2 または Python 3 のどちらを選択する必要がありますか？" という漠然とした質問があります。答えは、思っているよりも少し微妙です。


.. The basic gist of the state of things is as follows:

状態の基本的な要点は次のとおりです。

.. 1. Most production applications today use Python 2.7.
.. 2. Python 3 is ready for the production deployment of applications today.
.. 3. Python 2.7 will only receive necessary security updates until 2020 [#pep373_eol]_.
.. 4. The brand name "Python" encapsulates both Python 3 and Python 2.

1. 今日の実稼働アプリケーションの多くは、Python 2.7 を使用しています。
2. Python 3は、現時点でアプリケーションの実環境への展開の準備が整っています。
3. Python 2.7は、2020年まで必要なセキュリティアップデートのみを受け取ります [#pep373_eol]_。
4. "Python" というブランドは、Python 3 と Python 2 の両方をカプセル化します。

.. Recommendations
.. ~~~~~~~~~~~~~~~

推奨事項
~~~~~~~~

.. I'll be blunt:

率直に言うと:

.. - Use Python 3 for new Python applications.
.. - If you're learning Python for the first time, familiarizing yourself with Python 2.7 will be very
..   useful, but not more useful than learning Python 3.
.. - Learn both. They are both "Python".
.. - Software that is already built often depends on Python 2.7.
.. - If you are writing a new open source Python library, it's best to write it for both Python 2 and 3
..   simultaneously. Only supporting Python 3 for a new library you want to be widely adopted is a
..   political statment and will alienate many of your users. This is not a problem — slowly, over the next three years, this will become less the case.

- 新しい Python アプリケーションは Python 3 を使用します。
- Python を初めて学ぶなら、Python 2.7 を身近に感じることは非常に大切ですが、Python 3 を学ぶことよりも有用ではありません。
- 両方を学びます。 どちらも "Python" です。
- 既に構築されているソフトウェアは Python 2.7 に依存していることが多いです。
- 新しいオープンソースの Python ライブラリを作成している場合は、Python 2 と Python 3 の両方を同時に作成することをお勧めします。 新しいライブラリのために Python 3 を広くサポートしたいのは政治的なものであり、多くのユーザを疎外させます。 これは問題ではありません。ゆっくりと、今後3年間で、このケースは少なくなります。

.. So.... 3?
.. ~~~~~~~~~

そんなわけで.... 3？
~~~~~~~~~~~~~~~~~~~~

.. If you're choosing a Python interpreter to use, I
.. recommend you use the newest Python 3.x, since every version brings new and
.. improved standard library modules, security and bug fixes.

使用する Python インタプリタを選択している場合は、最新バージョンの Python 3.x を使用することをお勧めします。これは、すべてのバージョンで新しく改良された標準ライブラリモジュール、セキュリティ、バグ修正がもたらされるからです。

.. Given such, only use Python 2 if you have a strong reason to, such as a
.. pre-existing code-base, a Python 2 exclusive library, simplicity/familiarity,
.. or, of course, you absolutely love and are inspired by Python 2. No harm in that.

このように、既存のコードベース、Python 2 専用ライブラリ、シンプルさ/馴染みやすさなどの理由がある場合や、Python 2 を絶対に愛し、インスピレーションを得ている場合は、Python 2 を使用してください。 それは害ではありません。

.. Check out `Can I Use Python 3? <https://caniusepython3.com/>`_ to see if any
.. software you're depending on will block your adoption of Python 3.

`Python 3 を使うことはできますか？ <https://caniusepython3.com/>`_ を実行して、依存しているソフトウェアが Python 3 の採用を妨げるかどうかを確認します。

.. `Further Reading <http://wiki.python.org/moin/Python2orPython3>`_

`さらに読む <http://wiki.python.org/moin/Python2 orPython3>`_

.. It is possible to `write code that works on Python 2.6, 2.7, and Python 3
.. <https://docs.python.org/3/howto/pyporting.html>`_. This
.. ranges from trivial to hard depending upon the kind of software
.. you are writing; if you're a beginner there are far more important things to
.. worry about.

`Python 2.6, 2.7, Python 3 <https://docs.python.org/3/howto/pyporting.html>`_ 書くことは可能です。 これは、あなたが書いているソフトウェアの種類に応じて、些細なものから難しいものまでさまざまです。 あなたが初心者なら、もっと重要なことが心配されます。

.. Implementations
.. ~~~~~~~~~~~~~~~

実装
~~~~

.. When people speak of *Python* they often mean not just the language but also
.. the CPython implementation. *Python* is actually a specification for a language
.. that can be implemented in many different ways.

人々が *Python* について話すとき、言語だけ意味するのではなく、CPython の実装も意味することがよくあります。 *Python* は実際にはさまざまな方法で実装できる言語の仕様です。

CPython
-------

.. `CPython <http://www.python.org>`_ is the reference implementation of Python,
.. written in C. It compiles Python code to intermediate bytecode which is then
.. interpreted by a virtual machine. CPython provides the highest
.. level of compatibility with Python packages and C extension modules.

`CPython <http://www.python.org>`_ は、Cで書かれた Python のリファレンス実装です。Python コードを中間バイトコードにコンパイルし、それを仮想マシンで解釈します。 CPython は、Python パッケージとC拡張モジュールとの最高レベルの互換性を提供します。

.. If you are writing open-source Python code and want to reach the widest possible
.. audience, targeting CPython is best. To use packages which rely on C extensions
.. to function, CPython is your only implementation option.

オープンソースの Python コードを作成していて、できるだけ広い範囲のユーザーにアプローチしたい場合は、CPython をターゲットにするのが最適です。 Cエクステンションに依存するパッケージを使用するには、CPython が唯一の実装オプションです。

.. All versions of the Python language are implemented in C because CPython is the
.. reference implementation.

CPython はリファレンス実装であるため、Python 言語のすべてのバージョンはC言語で実装されています。

PyPy
----

.. `PyPy <http://pypy.org/>`_ is a Python interpreter implemented in a restricted
.. statically-typed subset of the Python language called RPython. The interpreter
.. features a just-in-time compiler and supports multiple back-ends (C, CLI, JVM).

`PyPy <http://pypy.org/>`_ は Python 言語の制限付き静的型サブセットで実装された Python インタプリタです。これは RPython と呼ばれます。 インタプリタにはジャストインタイムコンパイラがあり、複数のバックエンド（C、CLI、JVM）をサポートしています。

.. PyPy aims for maximum compatibility with the reference CPython implementation
.. while improving performance.

PyPyは、パフォーマンスを向上させながら、リファレンス CPython 実装との最大の互換性を目指しています。

.. If you are looking to increase performance of your Python code, it's
.. worth giving PyPy a try. On a suite of benchmarks, it's currently `over 5 times
.. faster than CPython <http://speed.pypy.org/>`_.

Python コードのパフォーマンスを向上させたい場合は、PyPy を試してみる価値があります。 一連のベンチマークでは、現在、`CPythonより5倍以上高速 <http://speed.pypy.org/>`_ です。

.. PyPy supports Python 2.7. PyPy3 [#pypy_ver]_, released in beta, targets Python 3.

PyPy は Python 2.7 をサポートします。 ベータ版でリリースされた PyPy3 [#pypy_ver]_ は、Python 3 をターゲットにしています。

Jython
------

.. `Jython <http://www.jython.org/>`_ is a Python implementation that compiles
.. Python code to Java bytecode which is then executed by the JVM (Java Virtual Machine).
.. Additionally, it is able to import and use any Java class like a Python
.. module.

`Jython <http://www.jython.org/>`_ は、Python コードを Java バイトコードにコンパイルし、JVM（Java仮想マシン）によって実行される Python の実装です。さらに、Python モジュールのような Java クラスをインポートして使用することができます。

.. If you need to interface with an existing Java codebase or have other reasons to
.. need to write Python code for the JVM, Jython is the best choice.

既存の Java コードベースとのインタフェースが必要な場合や、JVM 用の Python コードを書く必要があるなどの理由がある場合は、Jython が最適です。

.. Jython currently supports up to Python 2.7. [#jython_ver]_

Jython は現在 Python 2.7 をサポートしています。 [#jython_ver]_

IronPython
----------

.. `IronPython <http://ironpython.net/>`_  is an implementation of Python for the .NET
.. framework. It can use both Python and .NET framework libraries, and can also
.. expose Python code to other languages in the .NET framework.

`IronPython <http://ironpython.net/>`_ は、.NETフレームワーク用の Python の実装です。これは、Python と .NETフレームワークライブラリの両方を使用することができますし、Python コードを .NETフレームワークの他の言語にも公開することができます。

.. `Python Tools for Visual Studio <http://ironpython.net/tools/>`_ integrates
.. IronPython directly into the Visual Studio development environment, making it
.. an ideal choice for Windows developers.

`Python Tools for Visual Studio <http://ironpython.net/tools/>`_ はIronPythonをVisual Studio開発環境に直接統合し、Windows開発者にとって理想的な選択肢にします。

.. IronPython supports Python 2.7. [#iron_ver]_

IronPython は Python 2.7 をサポートしています。 [#iron_ver]_

PythonNet
---------

.. `Python for .NET <http://pythonnet.github.io/>`_ is a package which
.. provides near seamless integration of a natively installed Python
.. installation with the .NET Common Language Runtime (CLR).  This is the
.. inverse approach to that taken by IronPython (see above), to which it
.. is more complementary than competing with.

`Python for .NET <http://pythonnet.github.io/>`_ は、ネイティブにインストールされた Python インストールを .NET Common Language Runtime（CLR）にシームレスに統合するパッケージです。 これは IronPython（上記を参照）とは逆のアプローチであり、これは競合するよりも補完的です。

.. In conjunction with Mono, pythonnet enables native Python
.. installations on non-Windows operating systems, such as OS X and
.. Linux, to operate within the .NET framework.  It can be run in
.. addition to IronPython without conflict.

Pythonnet は、Mono と組み合わせて、OS X や Linux などの Windows 以外のオペレーティングシステム上のネイティブ Python インストールを .NETフレームワーク内で動作させることができます。IronPython に加えて競合することなく実行できます。

.. Pythonnet supports from Python 2.6 up to Python 3.5. [#pythonnet_ver1]_ [#pythonnet_ver2]_

Pythonnet は、Python 2.6 から Python 3.5 までをサポートします。 [#pythonnet_ver1]_ [#pythonnet_ver2]_

.. [#pypy_ver] http://pypy.org/compat.html

.. [#jython_ver] https://hg.python.org/jython/file/412a8f9445f7/NEWS

.. [#iron_ver] http://ironpython.codeplex.com/releases/view/81726

.. [#pythonnet_ver1] https://travis-ci.org/pythonnet/pythonnet

.. [#pythonnet_ver2] https://ci.appveyor.com/project/TonyRoberts/pythonnet-480xs

.. [#pep373_eol] https://www.python.org/dev/peps/pep-0373/#id2
