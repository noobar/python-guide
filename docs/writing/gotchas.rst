.. Common Gotchas
.. ==============

共通の落とし穴
==============

.. For the most part, Python aims to be a clean and consistent language that
.. avoids surprises. However, there are a few cases that can be confusing to
.. newcomers.

ほとんどの場合、Pythonは驚きを避けるきれいで一貫した言語を目指しています。 しかし、新入社員を混乱させる可能性のあるケースがいくつかあります。

.. Some of these cases are intentional but can be potentially surprising. Some
.. could arguably be considered language warts. In general, what follows
.. is a collection of potentially tricky behavior that might seem strange at first
.. glance, but is generally sensible once you're aware of the underlying cause for
.. the surprise.

これらのケースのいくつかは意図的ですが、潜在的に驚くことでしょう。 間違いなく、言語の欠点と見なすこともできます。 一般的には、一見すると奇妙に見える可能性のあるトリッキーな動作の集合ですが、驚きの根底にある原因を認識すると一般的には賢明です。

.. _default_args:

.. Mutable Default Arguments
.. -------------------------

変更可能なデフォルト引数
------------------------

.. Seemingly the *most* common surprise new Python programmers encounter is
.. Python's treatment of mutable default arguments in function definitions.

おそらく新しいPythonプログラマが遭遇する最も驚くべき点は、関数定義におけるデフォルトの引数を変更できるPythonの扱いです。

.. What You Wrote
.. ~~~~~~~~~~~~~~

あなたが書いたもの
~~~~~~~~~~~~~~~~~~

.. code-block:: python

    def append_to(element, to=[]):
        to.append(element)
        return to

.. What You Might Have Expected to Happen
.. ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

起こることが予想されること
~~~~~~~~~~~~~~~~~~~~~~~~~~

.. code-block:: python

    my_list = append_to(12)
    print my_list

    my_other_list = append_to(42)
    print my_other_list

.. A new list is created each time the function is called if a second argument
.. isn't provided, so that the output is::

2番目の引数が指定されていない場合、関数が呼び出されるたびに新しいリストが作成され、出力は次のようになります。

    [12]
    [42]

.. What Does Happen
.. ~~~~~~~~~~~~~~~~

何が起こるか
~~~~~~~~~~~~

.. testoutput::

    [12]
    [12, 42]

.. A new list is created *once* when the function is defined, and the same list is
.. used in each successive call.

関数が定義されているときに新しいリストが作成され、各リスト内で連続して同じリストが使用されます。

.. Python's default arguments are evaluated *once* when the function is defined,
.. not each time the function is called (like it is in say, Ruby). This means that
.. if you use a mutable default argument and mutate it, you *will* and have
.. mutated that object for all future calls to the function as well.

Pythonのデフォルト引数は、関数が定義されているときに評価されます。関数が呼び出されるたびに（例えば、Rubyのように）評価されるのではありません。 つまり、変更可能なデフォルトの引数を使用してそれを変更すると、その関数への今後のすべての呼び出しのためにそのオブジェクトを変更してしまいます。

.. What You Should Do Instead
.. ~~~~~~~~~~~~~~~~~~~~~~~~~~

代わりに何をすべきか
~~~~~~~~~~~~~~~~~~~~

.. Create a new object each time the function is called, by using a default arg to
.. signal that no argument was provided (:py:data:`None` is often a good choice).

関数が呼び出されるたびに、デフォルトの引数を使用して引数が指定されていないことを伝える (:py:data:`None` はしばしば良い選択です) 新しいオブジェクトを作成します。

.. code-block:: python

    def append_to(element, to=None):
        if to is None:
            to = []
        to.append(element)
        return to


.. When the Gotcha Isn't a Gotcha
.. ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

落とし穴が落とし穴でないとき
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. Sometimes you can specifically "exploit" (read: use as intended) this behavior
.. to maintain state between calls of a function. This is often done when writing
.. a caching function.

場合によっては、関数の呼び出し間で状態を維持するために、この動作を具体的に「悪用する」（読み込み：意図したとおりに使用する）ことができます。 これは、キャッシング機能を記述するときによく行われます。


.. Late Binding Closures
.. ---------------------

遅延バインディングクロージャ
----------------------------

.. Another common source of confusion is the way Python binds its variables in
.. closures (or in the surrounding global scope).

混乱のもう一つの一般的な原因は、Pythonがクロージャー（またはその周囲のグローバルスコープ）で変数をバインドする方法です。

.. What You Wrote
.. ~~~~~~~~~~~~~~

あなたが書いたもの
~~~~~~~~~~~~~~~~~~

.. testcode::

    def create_multipliers():
        return [lambda x : i * x for i in range(5)]

.. What You Might Have Expected to Happen
.. ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

起こることが予想されること
~~~~~~~~~~~~~~~~~~~~~~~~~~

.. testcode::

    for multiplier in create_multipliers():
        print multiplier(2)

.. A list containing five functions that each have their own closed-over ``i``
.. variable that multiplies their argument, producing::

引数を掛け合わせる独自のクローズドオーバー ``i`` 変数を持つ5つの関数を含むリストです::

    0
    2
    4
    6
    8

.. What Does Happen
.. ~~~~~~~~~~~~~~~~

何が起こるか
~~~~~~~~~~

.. testoutput::

    8
    8
    8
    8
    8

.. Five functions are created; instead all of them just multiply ``x`` by 4.

5つの関数が作成されます。 代わりにそれらのすべてが ``x`` を4倍します。

.. Python's closures are *late binding*.
.. This means that the values of variables used in closures are looked
.. up at the time the inner function is called.

Pythonのクロージャは *late binding* です。 これは、内部関数が呼び出された時点でクロージャーで使用される変数の値が参照されることを意味します。

.. Here, whenever *any* of the returned functions are called, the value of ``i``
.. is looked up in the surrounding scope at call time. By then, the loop has
.. completed and ``i`` is left with its final value of 4.

ここで、返される関数の *any* が呼び出されるたびに、呼び出し時に ``i`` の値が周囲のスコープで参照されます。 それまでにループが完了し、最終値が4のままの ``i`` が残されます。

.. What's particularly nasty about this gotcha is the seemingly prevalent
.. misinformation that this has something to do with :ref:`lambdas <python:lambda>`
.. in Python. Functions created with a ``lambda`` expression are in no way special,
.. and in fact the same exact behavior is exhibited by just using an ordinary
.. ``def``:

この問題について特に厄介なのは、これが何かと関係していると思われる誤った情報です :ref:`lambdas <python:lambda>` ``lambda`` 式で作成された関数は決して特別なものではなく、実際には普通の ``def`` を使うだけで同じ正確な振る舞いが現れます:

.. code-block:: python

    def create_multipliers():
        multipliers = []

        for i in range(5):
            def multiplier(x):
                return i * x
            multipliers.append(multiplier)

        return multipliers

.. What You Should Do Instead
.. ~~~~~~~~~~~~~~~~~~~~~~~~~~

代わりに何をすべきか
~~~~~~~~~~~~~~~~~~~~

.. The most general solution is arguably a bit of a hack. Due to Python's
.. aforementioned behavior concerning evaluating default arguments to functions
.. (see :ref:`default_args`), you can create a closure that binds immediately to
.. its arguments by using a default arg like so:

最も一般的な解決策は間違いなくハックのビットです。 関数へのデフォルト引数の評価に関するPythonの前述の動作 (:ref:`default_args` を参照) のために、デフォルト引数を使用してその引数にすぐにバインドするクロージャを作成することができます:

.. code-block:: python

    def create_multipliers():
        return [lambda x, i=i : i * x for i in range(5)]

.. Alternatively, you can use the functools.partial function:

代わりに、functools.partial関数を使用することもできます:

.. code-block:: python

    from functools import partial
    from operator import mul

    def create_multipliers():
        return [partial(mul, i) for i in range(5)]

.. When the Gotcha Isn't a Gotcha
.. ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

落とし穴が落とし穴でないとき
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. Sometimes you want your closures to behave this way. Late binding is good in
.. lots of situations. Looping to create unique functions is unfortunately a case
.. where they can cause hiccups.

場合によっては、クロージャーがこのように動作することを望みます。 最近のバインディングは、多くの状況で良好です。 ユニークな機能を作り出すためのループは、残念ながら、しゃっくりを引き起こす可能性があります。



.. Bytecode (.pyc) Files Everywhere!
.. ---------------------------------

どこでもバイトコード (.pyc) ファイル！
--------------------------------------

.. By default, when executing Python code from files, the Python interpreter
.. will automatically write a bytecode version of that file to disk, e.g.
.. ``module.pyc``.

デフォルトでは、ファイルからPythonコードを実行すると、Pythonインタプリタは自動的にそのファイルのバイトコードバージョンをディスクに書き込みます。 ``module.pyc``。

.. These ``.pyc`` files should not be checked into your source code repositories.

これらの ``.pyc`` ファイルはあなたのソースコードリポジトリにチェックインされるべきではありません。

.. Theoretically, this behavior is on by default, for performance reasons.
.. Without these bytecode files present, Python would re-generate the bytecode
.. every time the file is loaded.

理論的には、パフォーマンス上の理由から、この動作は既定でオンになっています。 これらのバイトコードファイルがなければ、Pythonはファイルが読み込まれるたびにバイトコードを再生成します。


.. Disabling Bytecode (.pyc) Files
.. ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

バイトコード (.pyc) ファイルの無効化
 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. Luckily, the process of generating the bytecode is extremely fast, and isn't
.. something you need to worry about while developing your code.

幸いにも、バイトコードを生成するプロセスは非常に高速であり、コードを開発する際に心配する必要はありません。

.. Those files are annoying, so let's get rid of them!

それらのファイルは迷惑なので、取り除いてみましょう！

::

    $ export PYTHONDONTWRITEBYTECODE=1

.. With the ``$PYTHONDONTWRITEBYTECODE`` environment variable set, Python will
.. no longer write these files to disk, and your development environment will
.. remain nice and clean.

``$PYTHONDONTWRITEBYTECODE`` 環境変数を設定すると、Pythonはこれらのファイルをディスクに書き込まなくなり、開発環境はきれいになります。

.. I recommend setting this environment variable in your ``~/.profile``.

あなたの ``~/.profile`` にこの環境変数を設定することをお勧めします。

.. Removing Bytecode (.pyc) Files
.. ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

バイトコード (.pyc) ファイルの削除
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. Here's nice trick for removing all of these files, if they already exist::

すでに存在する場合、これらのファイルをすべて削除するための素晴らしいトリックです:

    $ find . -type f -name "*.py[co]" -delete -or -type d -name "__pycache__" -delete

.. Run that from the root directory of your project, and all ``.pyc`` files
.. will suddenly vanish. Much better.

プロジェクトのルートディレクトリから実行すると、すべての ``.pyc`` ファイルが突然消えます。 はるかに良い。











