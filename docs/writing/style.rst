.. _code_style:

.. Code Style
.. ==========

コードスタイル
==============

.. If you ask Python programmers what they like most about Python, they will
.. often cite its high readability.  Indeed, a high level of readability
.. is at the heart of the design of the Python language, following the
.. recognized fact that code is read much more often than it is written.

PythonプログラマーにPythonについて最も好きなものを尋ねると、彼らはしばしば高い可読性を挙げるでしょう。 確かに、コードは書かれたよりもずっと頻繁に読み込まれるという認識された事実に従うことで、高いレベルの可読性がPython言語の設計の中心にあります。

.. One reason for the high readability of Python code is its relatively
.. complete set of Code Style guidelines and "Pythonic" idioms.

Pythonコードの可読性が高い理由の1つは、コードスタイルガイドラインとPythonのイディオムの比較的完全なセットです。

.. When a veteran Python developer (a Pythonista) calls portions of
.. code not "Pythonic", they usually mean that these lines
.. of code do not follow the common guidelines and fail to express its intent in
.. what is considered the best (hear: most readable) way.

ベテランのPython開発者（Pythonista）がPython以外のコード部分を呼び出すと、通常、これらのコード行は共通のガイドラインに従わず、最良のものとして意図されていることを表現することができません。 方法。

.. On some border cases, no best way has been agreed upon on how to express
.. an intent in Python code, but these cases are rare.

いくつかの国境のケースでは、Pythonコードで意図を表現するための最良の方法については合意されていませんが、これらのケースはまれです。

.. General concepts
.. ----------------

一般的な概念
------------

.. Explicit code
.. ~~~~~~~~~~~~~

明示的なコード
~~~~~~~~~~~~~~

.. While any kind of black magic is possible with Python, the
.. most explicit and straightforward manner is preferred.

Pythonではあらゆる種類の黒色の魔法が可能ですが、最も明快で簡単な方法が好まれます。

.. **Bad**

**悪い**

.. code-block:: python

    def make_complex(*args):
        x, y = args
        return dict(**locals())

.. **Good**

.. code-block:: python

    def make_complex(x, y):
        return {'x': x, 'y': y}

.. In the good code above, x and y are explicitly received from
.. the caller, and an explicit dictionary is returned. The developer
.. using this function knows exactly what to do by reading the
.. first and last lines, which is not the case with the bad example.

上記の良いコードでは、xとyは呼び出し元から明示的に受け取られ、明示的な辞書が返されます。 この関数を使用している開発者は、最初と最後の行を読むことによって何をすべきかを正確に知っていますが、悪い例ではそうではありません。

.. One statement per line
.. ~~~~~~~~~~~~~~~~~~~~~~

行ごとに1つのステートメント
~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. While some compound statements such as list comprehensions are
.. allowed and appreciated for their brevity and their expressiveness,
.. it is bad practice to have two disjointed statements on the same line of code.

リスト内包表記のようないくつかの複合文は、その簡潔さと表現力のために許可され、評価されますが、同じコード行に2つの分離した文を持つことは悪い習慣です。

.. **Bad**

**悪い**

.. code-block:: python

    print 'one'; print 'two'

    if x == 1: print 'one'

    if <complex comparison> and <other complex comparison>:
        # do something

.. **Good**

**良い**

.. code-block:: python

    print 'one'
    print 'two'

    if x == 1:
        print 'one'

    cond1 = <complex comparison>
    cond2 = <other complex comparison>
    if cond1 and cond2:
        # do something

.. Function arguments
.. ~~~~~~~~~~~~~~~~~~

関数の引数
~~~~~~~~~~

.. Arguments can be passed to functions in four different ways.

引数は4つの異なる方法で関数に渡すことができます。

.. 1. **Positional arguments** are mandatory and have no default values. They are
..    the simplest form of arguments and they can be used for the few function
..    arguments that are fully part of the function's meaning and their order is
..    natural. For instance, in ``send(message, recipient)`` or ``point(x, y)``
..    the user of the function has no difficulty remembering that those two
..    functions require two arguments, and in which order.

1. **位置引数** は必須であり、デフォルト値はありません。それらは引数の最も単純な形式であり、関数の意味の一部であり、順序は自然であるいくつかの関数引数に対して使用できます。例えば、 ``send(message, recipient)`` や ``point(x, y)`` では、関数のユーザは2つの引数を必要とし、

.. In those two cases, it is possible to use argument names when calling the
.. functions and, doing so, it is possible to switch the order of arguments,
.. calling for instance ``send(recipient='World', message='Hello')`` and
.. ``point(y=2, x=1)`` but this reduces readability and is unnecessarily verbose,
.. compared to the more straightforward calls to ``send('Hello', 'World')`` and
.. ``point(1, 2)``.

この2つのケースでは、関数を呼び出すときに引数名を使用することができます。そうすることで、引数の順序を切り替えることができます。例えば ``send(recipient='World', message='Hello')`` ``send('Hello', 'World')`` と ``point(y=2, x=1)`` へのより単純な呼び出しに比べて、``point(1, 2)``。

.. 2. **Keyword arguments** are not mandatory and have default values. They are
..    often used for optional parameters sent to the function. When a function has
..    more than two or three positional parameters, its signature is more difficult
..    to remember and using keyword arguments with default values is helpful. For
..    instance, a more complete ``send`` function could be defined as
..    ``send(message, to, cc=None, bcc=None)``. Here ``cc`` and ``bcc`` are
..    optional, and evaluate to ``None`` when they are not passed another value.

2. **キーワード引数** は必須ではなく、デフォルト値を持ちます。これらは、関数に送信されるオプションのパラメータによく使用されます。関数に2つまたは3つ以上の位置パラメータがある場合、そのシグネチャは覚えにくく、キーワード引数をデフォルト値で使用すると便利です。例えば、より完全な ``send`` 関数は ``send(message, to, cc=None, bcc=None)`` として定義できます。ここで、 ``cc`` と ``bcc`` はオプションで、別の値が渡されないときは ``None`` と評価されます。

.. Calling a function with keyword arguments can be done in multiple ways in
.. Python, for example it is possible to follow the order of arguments in the
.. definition without explicitly naming the arguments, like in
.. ``send('Hello', 'World', 'Cthulhu', 'God')``, sending a blind carbon copy to
.. God. It would also be possible to name arguments in another order, like in
.. ``send('Hello again', 'World', bcc='God', cc='Cthulhu')``. Those two
.. possibilities are better avoided without any strong reason to not follow the
.. syntax that is the closest to the function definition:
.. ``send('Hello', 'World', cc='Cthulhu', bcc='God')``.

キーワード引数を持つ関数をPythonで複数の方法で呼び出すことができます。たとえば、 ``send('Hello', 'World', 'Cthulhu', 'God')`` のように、引数に明示的に名前を付けずにカーボンコピーを送る。 ``send('Hello again', 'World', bcc='God', cc='Cthulhu')`` のように、別の順序で引数を指定することもできます。 ``send('Hello', 'World', cc='Cthulhu', bcc='God')`` 関数の定義に最も近い構文に従わないという強い理由がなくても、 。

.. As a side note, following `YAGNI <http://en.wikipedia.org/wiki/You_ain't_gonna_need_it>`_
.. principle, it is often harder to remove an optional argument (and its logic
.. inside the function) that was added "just in case" and is seemingly never used,
.. than to add a new optional argument and its logic when needed.

副作用として、 `YAGNI <http://en.wikipedia.org/wiki/You_ain't_gonna_need_it>`_ 原則の後で、オプションの引数（およびその関数内のロジック）を削除することは難しい場合があります。必要に応じて新しいオプションの引数とそのロジックを追加するよりも、まるで使用されていて一見無意味です。

.. 3. The **arbitrary argument list** is the third way to pass arguments to a
..    function. If the function intention is better expressed by a signature with
..    an extensible number of positional arguments, it can be defined with the
..    ``*args`` constructs. In the function body, ``args`` will be a tuple of all
..    the remaining positional arguments. For example, ``send(message, *args)``
..    can be called with each recipient as an argument:``send('Hello', 'God',
..    'Mom', 'Cthulhu')``, and in the function body ``args`` will be equal to
..    ``('God', 'Mom', 'Cthulhu')``.

3. **任意の引数リスト** は、引数を関数に渡す3番目の方法です。関数の意図が、拡張可能な数の位置引数を持つシグネチャによってうまく表現されている場合は、 ``* args`` 構造体で定義できます。関数本体では、 ``args`` は残りのすべての位置引数のタプルになります。たとえば、 ``send('Hello', 'God', 'Mom', 'Cthulhu')`` と ``send(message, *args)`` のように、関数本体 ``args`` は ``('God', 'Mom', 'Cthulhu')`` に等しくなります。

.. However, this construct has some drawbacks and should be used with caution. If a
.. function receives a list of arguments of the same nature, it is often more
.. clear to define it as a function of one argument, that argument being a list or
.. any sequence. Here, if ``send`` has multiple recipients, it is better to define
.. it explicitly: ``send(message, recipients)`` and call it with ``send('Hello',
.. ['God', 'Mom', 'Cthulhu'])``. This way, the user of the function can manipulate
.. the recipient list as a list beforehand, and it opens the possibility to pass
.. any sequence, including iterators, that cannot be unpacked as other sequences.

しかしながら、この構築物にはいくつかの欠点があり、慎重に使用すべきである。ある関数が同じ性質の引数のリストを受け取った場合、それを1つの引数の関数として定義することがより明確であり、その引数はリストまたは任意のシーケンスです。ここで ``send`` に複数の受信者がある場合、``send('Hello', ['God', 'Mom', 'Cthulhu'])`` で明示的に ``send(message, recipients')``。この方法では、関数のユーザーは受信者リストをあらかじめリストとして操作し、イテレーターを含む他のシーケンスとして解凍できないシーケンスを渡す可能性を開きます。

.. 4. The **arbitrary keyword argument dictionary** is the last way to pass
..    arguments to functions. If the function requires an undetermined series of
..    named arguments, it is possible to use the ``**kwargs`` construct. In the
..    function body, ``kwargs`` will be a dictionary of all the passed named
..    arguments that have not been caught by other keyword arguments in the
..    function signature.

4. **任意のキーワード引数辞書** は、関数に引数を渡す最後の方法です。 関数が未定義の一連の名前付き引数を必要とする場合は、 ``** kwargs`` 構造体を使用することができます。 関数本体では、 ``kwargs`` は、関数シグネチャ内の他のキーワード引数によってキャッチされていない、渡されたすべての名前付き引数の辞書になります。

.. The same caution as in the case of *arbitrary argument list* is necessary, for
.. similar reasons: these powerful techniques are to be used when there is a
.. proven necessity to use them, and they should not be used if the simpler and
.. clearer construct is sufficient to express the function's intention.

同様の理由から、*任意の引数リスト* の場合と同じ注意が必要です。これらの強力な手法は、実証された必要性がある場合に使用されるものであり、よりシンプルで明確な構成が関数の意図を表現するのに十分である。

.. It is up to the programmer writing the function to determine which arguments
.. are positional arguments and which are optional keyword arguments, and to
.. decide whether to use the advanced techniques of arbitrary argument passing. If
.. the advice above is followed wisely, it is possible and enjoyable to write
.. Python functions that are:

どの引数が定位置引数であり、かつオプションのキーワード引数であるかを決定し、任意の引数渡しの高度な技術を使用するかどうかを決定するのは、関数を記述するプログラマの責任です。上記のアドバイスが賢明に守られれば、Pythonの関数を書くことが可能で楽しいです:

.. * easy to read (the name and arguments need no explanations)

* 読みやすい（名前と引数は説明が不要）

.. * easy to change (adding a new keyword argument does not break other parts of
..   the code)

* 簡単に変更することができます（新しいキーワード引数を追加することでコードの他の部分が破られることはありません）

.. Avoid the magical wand
.. ~~~~~~~~~~~~~~~~~~~~~~

魔法の杖を避ける
~~~~~~~~~~~~~~~~

.. A powerful tool for hackers, Python comes with a very rich set of hooks and
.. tools allowing you to do almost any kind of tricky tricks. For instance, it is
.. possible to do each of the following:

ハッカー向けの強力なツールであるPythonには、非常に豊富なフックやツールが付属しており、あらゆる種類のトリッキーなトリックを行うことができます。 たとえば、以下のそれぞれを行うことができます。

.. * change how objects are created and instantiated

* オブジェクトの作成およびインスタンス化の方法を変更する

.. * change how the Python interpreter imports modules

* Pythonインタープリタがどのようにモジュールをインポートするかを変更する

.. * it is even possible (and recommended if needed) to embed C routines in Python.

* CのルーチンをPythonに埋め込むことも可能です（必要に応じてお勧めします）。

.. However, all these options have many drawbacks and it is always better to use
.. the most straightforward way to achieve your goal. The main drawback is that
.. readability suffers greatly when using these constructs. Many code analysis
.. tools, such as pylint or pyflakes, will be unable to parse this "magic" code.

しかし、これらのオプションには多くの欠点があります。目標を達成するためには、最も簡単な方法を使用する方が常に優れています。 主な欠点は、これらのコンストラクトを使用すると可読性が大幅に低下することです。 pylintやpyflakesなどの多くのコード解析ツールは、この「魔法の」コードを解析できません。

.. We consider that a Python developer should know about these nearly infinite
.. possibilities, because it instills confidence that no impassable problem will
.. be on the way. However, knowing how and particularly when **not** to use
.. them is very important.

私たちは、Pythonの開発者は、これらの無限の可能性について知っておくべきだと考えています。なぜなら、途方もなく問題が起こらないという自信があるからです。 しかし、どのように、特に使用 **しない** かを知ることは非常に重要です。

.. Like a kung fu master, a Pythonista knows how to kill with a single finger, and
.. never to actually do it.

カンフーのマスターのように、Pythonistaは単一の指で殺す方法を知っています。
実際にそれをすることは決してありません。

.. We are all responsible users
.. ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

私たちはすべて責任あるユーザーです
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. As seen above, Python allows many tricks, and some of them are potentially
.. dangerous. A good example is that any client code can override an object's
.. properties and methods: there is no "private" keyword in Python. This
.. philosophy, very different from highly defensive languages like Java, which
.. give a lot of mechanisms to prevent any misuse, is expressed by the saying: "We
.. are all responsible users".

上で見たように、Pythonは多くのトリックを許し、そのうちのいくつかは潜在的に危険です。良い例は、どんなクライアントコードでも、オブジェクトのプロパティとメソッドをオーバーライドすることができるということです。Pythonでは "private"キーワードはありません。このような哲学は、誤用を防ぐための多くの仕組みを提供するJavaのような高度に防御的な言語とは異なり、「私たちはすべての責任あるユーザーです」と表現されています。

.. This doesn't mean that, for example, no properties are considered private, and
.. that no proper encapsulation is possible in Python. Rather, instead of relying
.. on concrete walls erected by the developers between their code and other's, the
.. Python community prefers to rely on a set of conventions indicating that these
.. elements should not be accessed directly.

これは、例えばプロパティがプライベートであるとはみなされず、Pythonでは適切なカプセル化ができないことを意味しません。 Pythonコミュニティは、開発者がコードと他のコードの間に構築したコンクリートの壁に頼るのではなく、これらの要素に直接アクセスすべきではないことを示す一連の規則に頼っています。

.. The main convention for private properties and implementation details is to
.. prefix all "internals" with an underscore. If the client code breaks this rule
.. and accesses these marked elements, any misbehavior or problems encountered if
.. the code is modified is the responsibility of the client code.

プライベートプロパティと実装の詳細の主な慣例は、すべての "内部"にアンダースコアを付けることです。 クライアントコードがこのルールを破ってこれらのマークされた要素にアクセスする場合、コードが変更された場合に遭遇する不正行為や問題は、クライアントコードの責任です。

.. Using this convention generously is encouraged: any method or property that is
.. not intended to be used by client code should be prefixed with an underscore.
.. This will guarantee a better separation of duties and easier modification of
.. existing code; it will always be possible to publicize a private property,
.. but making a public property private might be a much harder operation.

このコンベンションを惜しみなく使用することをお勧めします。クライアントコードで使用されないメソッドやプロパティには、アンダースコアを前に付ける必要があります。 これにより、任務の分離と既存のコードの変更が容易になります。 プライベートプロパティを公開することは常に可能ですが、パブリックプロパティをプライベートにすることは、はるかに難しい操作になる可能性があります。

.. Returning values
.. ~~~~~~~~~~~~~~~~

戻り値
~~~~~~

.. When a function grows in complexity it is not uncommon to use multiple return
.. statements inside the function's body. However, in order to keep a clear intent
.. and a sustainable readability level, it is preferable to avoid returning
.. meaningful values from many output points in the body.

関数が複雑になると、関数本体に複数のreturn文を使用することは珍しくありません。しかし、明確な意図と持続可能な可読性レベルを維持するためには、身体の多くの出力点から意味のある値を返すことを避けることが望ましいです。

.. There are two main cases for returning values in a function: the result of the
.. function return when it has been processed normally, and the error cases that
.. indicate a wrong input parameter or any other reason for the function to not be
.. able to complete its computation or task.

関数内で値を返す主なケースが2つあります。関数の結果が正常に処理されたときの結果と、誤った入力パラメータを示すエラーケース、または関数が計算を完了できないその他の理由またはタスク。

.. If you do not wish to raise exceptions for the second case, then returning a
.. value, such as None or False, indicating that the function could not perform
.. correctly might be needed. In this case, it is better to return as early as the
.. incorrect context has been detected. It will help to flatten the structure of
.. the function: all the code after the return-because-of-error statement can
.. assume the condition is met to further compute the function's main result.
.. Having multiple such return statements is often necessary.

2番目のケースの例外を発生させたくない場合は、関数が正しく実行できなかったことを示すNoneやFalseなどの値を返す必要があります。 この場合、間違ったコンテキストが検出されたときに早く戻ってください。 関数の構造をフラット化するのに役立ちます。return-of-errorステートメントの後のすべてのコードは、関数の主な結果をさらに計算するために条件が満たされたとみなすことができます。 多くの場合、そのようなreturn文が必要です。

.. However, when a function has multiple main exit points for its normal course,
.. it becomes difficult to debug the returned result, so it may be preferable to
.. keep a single exit point. This will also help factoring out some code paths,
.. and the multiple exit points are a probable indication that such a refactoring
.. is needed.

しかし、ある関数が通常のコースに対して複数のメイン出口点を持つ場合、返された結果をデバッグするのが難しくなるため、単一の出口点を保つことが望ましい場合があります。 これはまた、いくつかのコードパスを抽出するのにも役立ちます。また、複数の出口ポイントがそのようなリファクタリングが必要であることを示す可能性があります。

.. code-block:: python

   def complex_function(a, b, c):
       if not a:
           return None  # Raising an exception might be better
       if not b:
           return None  # Raising an exception might be better
       # Some complex code trying to compute x from a, b and c
       # Resist temptation to return x if succeeded
       if not x:
           # Some Plan-B computation of x
       return x  # One single exit point for the returned value x will help
                 # when maintaining the code.

.. Idioms
.. ------

慣用句
------

.. A programming idiom, put simply, is a *way* to write code. The notion of
.. programming idioms is discussed amply at `c2 <http://c2.com/cgi/wiki?ProgrammingIdiom>`_
.. and at `Stack Overflow <http://stackoverflow.com/questions/302459/what-is-a-programming-idiom>`_.

簡単に言えば、プログラミングのイディオムは、コードを書く *方法* です。プログラミングイディオムの概念については、 `c2 <http://c2.com/cgi/wiki?ProgrammingIdiom>`_ と `Stack Overflow <http://stackoverflow.com/questions/302459/what-is-a-programming-idiom>`_ です。

.. Idiomatic Python code is often referred to as being *Pythonic*.

慣用的なPythonコードは *Pythonic* と呼ばれることが多い。

.. Although there usually is one --- and preferably only one --- obvious way to do
.. it; *the* way to write idiomatic Python code can be non-obvious to Python
.. beginners. So, good idioms must be consciously acquired.

通常は、それを実行するための1つの方法、好ましくは1つの方法しかありません。 *慣用のPythonコードを書く* 方法は、Pythonの初心者には明らかではありません。 ですから、良い熟語を意識的に獲得しなければなりません。

.. Some common Python idioms follow:

いくつかの一般的なPythonのイディオムが続きます:

.. _unpacking-ref:

.. Unpacking
.. ~~~~~~~~~

開梱
~~~~

.. If you know the length of a list or tuple, you can assign names to its
.. elements with unpacking. For example, since ``enumerate()`` will provide
.. a tuple of two elements for each item in list:

リストやタプルの長さを知っている場合、その要素に名前をつけることができます。 たとえば、 ``enumerate()`` はlistの各項目に対して2つの要素のタプルを提供します:

.. code-block:: python

    for index, item in enumerate(some_list):
        # do something with index and item

.. You can use this to swap variables as well:

変数をスワップするときにもこれを使うことができます:

.. code-block:: python

    a, b = b, a

.. Nested unpacking works too:

ネストされたアンパックも機能します:

.. code-block:: python

   a, (b, c) = 1, (2, 3)

.. In Python 3, a new method of extended unpacking was introduced by
.. :pep:`3132`:

Python 3では、拡張アンパックの新しいメソッドが次のように導入されました :pep:`3132`:

.. code-block:: python

   a, *rest = [1, 2, 3]
   # a = 1, rest = [2, 3]
   a, *middle, c = [1, 2, 3, 4]
   # a = 1, middle = [2, 3], c = 4

.. Create an ignored variable
.. ~~~~~~~~~~~~~~~~~~~~~~~~~~

無視された変数を作成する
~~~~~~~~~~~~~~~~~~~~~~~~

.. If you need to assign something (for instance, in :ref:`unpacking-ref`) but
.. will not need that variable, use ``__``:

何かを割り当てる必要がある場合（例えば、:ref:`unpacking-ref`）、その変数は必要ないでしょう。``__`` を使ってください:

.. code-block:: python

    filename = 'foobar.txt'
    basename, __, ext = filename.rpartition('.')

.. .. note::
.. 
..    Many Python style guides recommend the use of a single underscore "``_``"
..    for throwaway variables rather than the double underscore "``__``"
..    recommended here. The issue is that "``_``" is commonly used as an alias
..    for the :func:`~gettext.gettext` function, and is also used at the
..    interactive prompt to hold the value of the last operation. Using a
..    double underscore instead is just as clear and almost as convenient,
..    and eliminates the risk of accidentally interfering with either of
..    these other use cases.

.. note::

   多くのPythonスタイルガイドでは、ここで推奨される二重アンダースコア "``__``" ではなく、使い捨て変数に単一のアンダースコア "``_``"を使用することを推奨しています。 問題は、 "``_``" は :func:`~gettext.gettext` 関数のエイリアスとしてよく使われ、最後の操作の値を保持するために対話型プロンプトでも使われます。 代わりに二重のアンダースコアを使用することは、明らかであり、ほぼ同じくらい便利で、これらの他のユースケースのいずれかを誤って妨害するリスクを排除します。

.. Create a length-N list of the same thing
.. ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

同じものの長さNのリストを作成する
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. Use the Python list ``*`` operator:

Pythonのリスト ``*`` 演算子を使う:

.. code-block:: python

    four_nones = [None] * 4

.. Create a length-N list of lists
.. ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

リストの長さNのリストを作成する
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. Because lists are mutable, the ``*`` operator (as above) will create a list
.. of N references to the `same` list, which is not likely what you want.
.. Instead, use a list comprehension:

リストは変更可能であるため、 ``*`` 演算子（上記のように）は `same` リストに対するN個の参照のリストを作成します。 代わりに、リストの理解を使用します。

.. code-block:: python

    four_lists = [[] for __ in xrange(4)]

.. Note: Use range() instead of xrange() in Python 3

Note: Python 3では xrange() の代わりに range() を使用してください

.. Create a string from a list
.. ~~~~~~~~~~~~~~~~~~~~~~~~~~~

リストから文字列を作成する
~~~~~~~~~~~~~~~~~~~~~~~~~~

.. A common idiom for creating strings is to use :py:meth:`str.join` on an empty
.. string.

文字列を作成する一般的な方法は、空の文字列に :py:meth:`str.join` を使用することです。

.. code-block:: python

    letters = ['s', 'p', 'a', 'm']
    word = ''.join(letters)

.. This will set the value of the variable *word* to 'spam'. This idiom can be
.. applied to lists and tuples.

変数 *word* の値を 'spam' に設定します。 このイディオムは、リストやタプルに適用できます。

.. Searching for an item in a collection
.. ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

コレクション内のアイテムを検索する
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. Sometimes we need to search through a collection of things. Let's look at two
.. options: lists and sets.

時々、私たちは物事のコレクションを検索する必要があります。リストとセットの2つのオプションを見てみましょう。

.. Take the following code for example:

たとえば、次のコードを実行します:

.. code-block:: python

    s = set(['s', 'p', 'a', 'm'])
    l = ['s', 'p', 'a', 'm']

    def lookup_set(s):
        return 's' in s

    def lookup_list(l):
        return 's' in l

.. Even though both functions look identical, because *lookup_set* is utilizing
.. the fact that sets in Python are hashtables, the lookup performance
.. between the two is very different. To determine whether an item is in a list,
.. Python will have to go through each item until it finds a matching item.
.. This is time consuming, especially for long lists. In a set, on the other
.. hand, the hash of the item will tell Python where in the set to look for
.. a matching item. As a result, the search can be done quickly, even if the
.. set is large. Searching in dictionaries works the same way. For
.. more information see this
.. `StackOverflow <http://stackoverflow.com/questions/513882/python-list-vs-dict-for-look-up-table>`_
.. page. For detailed information on the amount of time various common operations
.. take on each of these data structures, see
.. `this page <https://wiki.python.org/moin/TimeComplexity?>`_.

* *lookup_set* はPythonのセットがハッシュテーブルであるという事実を利用しているので、両方の関数が同じに見えますが、2つのルックアップのパフォーマンスは大きく異なります。項目がリストにあるかどうかを判断するには、Pythonは一致する項目が見つかるまで各項目を調べなければなりません。これは時間がかかります。特に長いリストの場合は特にそうです。一方、あるセットでは、アイテムのハッシュは、セット内のどこで一致するアイテムを探すかをPythonに指示します。その結果、セットが大きい場合であっても、迅速に検索を行うことができます。辞書での検索も同じように機能します。詳細は、この `StackOverflow <http://stackoverflow.com/questions/513882/python-list-vs-dict-for-look-up-table>`_ ページを参照してください。これらのデータ構造のそれぞれに共通するさまざまな操作の詳細については、 `このページ <https://wiki.python.org/moin/TimeComplexity？>`_ を参照してください。これらのパフォーマンスの違いのため、リストの代わりにセットまたは辞書を使用することは、しばしば良い考えです：

.. Because of these differences in performance, it is often a good idea to use
.. sets or dictionaries instead of lists in cases where:

これらのパフォーマンスの違いにより、リストの代わりにセットまたは辞書を使用することがよくあります。

.. * The collection will contain a large number of items

* コレクションには多数のアイテムが含まれます

.. * You will be repeatedly searching for items in the collection

* コレクション内のアイテムを繰り返し検索します

.. * You do not have duplicate items.

* 重複アイテムはありません。

.. For small collections, or collections which you will not frequently be
.. searching through, the additional time and memory required to set up the
.. hashtable will often be greater than the time saved by the improved search
.. speed.

小さなコレクション、または頻繁に検索しないコレクションの場合、ハッシュテーブルを設定するために必要な時間とメモリが、検索速度が向上した時間よりも長くなることがよくあります。


.. Zen of Python
.. -------------

Pythonの禅
----------

.. Also known as :pep:`20`, the guiding principles for Python's design.

:pep:`20` とも呼ばれ、Pythonの設計の基本原則です。

.. code-block:: pycon

    >>> import this
    The Zen of Python, by Tim Peters

    Beautiful is better than ugly.
    Explicit is better than implicit.
    Simple is better than complex.
    Complex is better than complicated.
    Flat is better than nested.
    Sparse is better than dense.
    Readability counts.
    Special cases aren't special enough to break the rules.
    Although practicality beats purity.
    Errors should never pass silently.
    Unless explicitly silenced.
    In the face of ambiguity, refuse the temptation to guess.
    There should be one-- and preferably only one --obvious way to do it.
    Although that way may not be obvious at first unless you're Dutch.
    Now is better than never.
    Although never is often better than *right* now.
    If the implementation is hard to explain, it's a bad idea.
    If the implementation is easy to explain, it may be a good idea.
    Namespaces are one honking great idea -- let's do more of those!

.. For some examples of good Python style, see `these slides from a Python user
.. group <http://artifex.org/~hblanks/talks/2011/pep20_by_example.pdf>`_.

よいPythonスタイルのいくつかの例については、 `Pythonユーザグループのこれらのスライド <http://artifex.org/~hblanks/talks/2011/pep20_by_example.pdf>`_ を参照してください。

PEP 8
-----

.. :pep:`8` is the de-facto code style guide for Python. A high quality,
.. easy-to-read version of PEP 8 is also available at `pep8.org <http://pep8.org/>`_.

:pep:`8` はPythonの事実上のコードスタイルガイドです。 `pep8.org <http://pep8.org/>`_ には、高品質で読みやすいPEP 8のバージョンもあります。

.. This is highly recommended reading. The entire Python community does their
.. best to adhere to the guidelines laid out within this document. Some project
.. may sway from it from time to time, while others may
.. `amend its recommendations <http://docs.python-requests.org/en/master/dev/contributing/#kenneth-reitz-s-code-style>`_.

これは強くお勧めします。 Pythonコミュニティ全体は、このドキュメント内に記載されているガイドラインを守るために最善を尽くしています。 プロジェクトの中には時々動揺するものもあれば、 `その勧告を修正するものもあります <http://docs.python-requests.org/en/master/dev/contributing/#kenneth-reitz-s-code-style>`_ 。

.. That being said, conforming your Python code to PEP 8 is generally a good
.. idea and helps make code more consistent when working on projects with other
.. developers. There is a command-line program, `pep8 <https://github.com/jcrocholl/pep8>`_,
.. that can check your code for conformance. Install it by running the following
.. command in your terminal:

つまり、PythonコードをPEP 8に準拠させることは、一般的には良いアイデアであり、他の開発者と一緒にプロジェクトを作業する場合にコードをより一貫性のあるものにするのに役立ちます。 あなたのコードの適合性をチェックできるコマンドラインプログラム `pep8 <https://github.com/jcrocholl/pep8>`_ があります。 ターミナルで次のコマンドを実行してインストールします。


.. code-block:: console

    $ pip install pep8


.. Then run it on a file or series of files to get a report of any violations.

次に、ファイルまたは一連のファイルに対して実行して、違反の報告を取得します。

.. code-block:: console

    $ pep8 optparse.py
    optparse.py:69:11: E401 multiple imports on one line
    optparse.py:77:1: E302 expected 2 blank lines, found 1
    optparse.py:88:5: E301 expected 1 blank line, found 0
    optparse.py:222:34: W602 deprecated form of raising exception
    optparse.py:347:31: E211 whitespace before '('
    optparse.py:357:17: E201 whitespace after '{'
    optparse.py:472:29: E221 multiple spaces before operator
    optparse.py:544:21: W601 .has_key() is deprecated, use 'in'

.. The program `autopep8 <https://pypi.python.org/pypi/autopep8/>`_ can be used to
.. automatically reformat code in the PEP 8 style. Install the program with:

`autopep8 <https://pypi.python.org/pypi/autopep8/>`_ プログラムを使って、PEP 8形式のコードを自動的に再フォーマットすることができます。 次のようにプログラムをインストールします。

.. code-block:: console

    $ pip install autopep8

.. Use it to format a file in-place with:

これを使用して、次のようにファイルをインプレースでフォーマットします。

.. code-block:: console

    $ autopep8 --in-place optparse.py

.. Excluding the ``--in-place`` flag will cause the program to output the modified
.. code directly to the console for review. The ``--aggressive`` flag will perform
.. more substantial changes and can be applied multiple times for greater effect.

``--in-place`` フラグを除外すると、プログラムは変更されたコードをレビューのためにコンソールに直接出力します。 ``--aggressive`` フラグはより実質的な変更を行い、効果を高めるために複数回適用することができます。

.. Conventions
.. ----------------

コンベンション
--------------

.. Here are some conventions you should follow to make your code easier to read.

あなたのコードを読みやすくするために従わなければならない規則がいくつかあります。

.. Check if variable equals a constant
.. ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

変数が定数に等しいかどうかをチェックする
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. You don't need to explicitly compare a value to True, or None, or 0 - you can
.. just add it to the if statement. See `Truth Value Testing
.. <http://docs.python.org/library/stdtypes.html#truth-value-testing>`_ for a
.. list of what is considered false.

明示的に値をTrue、None、または0と明示的に比較する必要はありません。if文に値を追加するだけです。 誤っていると思われるもののリストについては、 `真理値テスト <http://docs.python.org/library/stdtypes.html#truth-value-testing>`_ を参照してください。

.. **Bad**:

**悪い**:

.. code-block:: python

    if attr == True:
        print 'True!'

    if attr == None:
        print 'attr is None!'

.. **Good**:

**良い**:

.. code-block:: python

    # Just check the value
    if attr:
        print 'attr is truthy!'

    # or check for the opposite
    if not attr:
        print 'attr is falsey!'

    # or, since None is considered false, explicitly check for it
    if attr is None:
        print 'attr is None!'

.. Access a Dictionary Element
.. ~~~~~~~~~~~~~~~~~~~~~~~~~~~

辞書要素へのアクセス
~~~~~~~~~~~~~~~~~~~~

.. Don't use the :py:meth:`dict.has_key` method. Instead, use ``x in d`` syntax,
.. or pass a default argument to :py:meth:`dict.get`.

:py:meth:`dict.has_key` メソッドを使わないでください。 その代わりに、 ``x in d`` 構文を使うか、デフォルト引数を :py:meth:`dict.get` に渡します。

.. **Bad**:

**悪い**:

.. code-block:: python

    d = {'hello': 'world'}
    if d.has_key('hello'):
        print d['hello']    # prints 'world'
    else:
        print 'default_value'

.. **Good**:

**良い**:

.. code-block:: python

    d = {'hello': 'world'}

    print d.get('hello', 'default_value') # prints 'world'
    print d.get('thingy', 'default_value') # prints 'default_value'

    # Or:
    if 'hello' in d:
        print d['hello']

.. Short Ways to Manipulate Lists
.. ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

リストを操作するための短い方法
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. `List comprehensions
.. <http://docs.python.org/tutorial/datastructures.html#list-comprehensions>`_
.. provide a powerful, concise way to work with lists. Also, the :py:func:`map` and
.. :py:func:`filter` functions can perform operations on lists using a different,
.. more concise syntax.

`List comprehensions <http://docs.python.org/tutorial/datastructures.html#list-comprehensions>`_ は、リストを扱うための強力かつ簡潔な方法を提供します。 また、:py:func:`map` と :py:func:`filter` 関数は、より簡潔で異なった構文を使ってリストに対して操作を実行できます。

.. **Bad**:

**悪い**:

.. code-block:: python

    # Filter elements greater than 4
    a = [3, 4, 5]
    b = []
    for i in a:
        if i > 4:
            b.append(i)

.. **Good**:

**良い**:

.. code-block:: python

    a = [3, 4, 5]
    b = [i for i in a if i > 4]
    # Or:
    b = filter(lambda x: x > 4, a)

.. **Bad**:

**悪い**：

.. code-block:: python

    # Add three to all list members.
    a = [3, 4, 5]
    for i in range(len(a)):
        a[i] += 3

.. **Good**:

**良い**：

.. code-block:: python

    a = [3, 4, 5]
    a = [i + 3 for i in a]
    # Or:
    a = map(lambda i: i + 3, a)

.. Use :py:func:`enumerate` keep a count of your place in the list.

使用 :py:func:`enumerate` リスト内のあなたの場所の数を保持します。

.. code-block:: python

    a = [3, 4, 5]
    for i, item in enumerate(a):
        print i, item
    # prints
    # 0 3
    # 1 4
    # 2 5

.. The :py:func:`enumerate` function has better readability than handling a
.. counter manually. Moreover, it is better optimized for iterators.

:py:func:`enumerate` 関数はカウンタを手動で扱うよりも読み易いです。 さらに、イテレータの方が最適化されています。

.. Read From a File
.. ~~~~~~~~~~~~~~~~

ファイルからの読み取り
~~~~~~~~~~~~~~~~~~~~~~

.. Use the ``with open`` syntax to read from files. This will automatically close
.. files for you.

ファイルから読み込むには ``with open`` 構文を使用します。 これにより、自動的にファイルが閉じられます。

.. **Bad**:

**悪い**:

.. code-block:: python

    f = open('file.txt')
    a = f.read()
    print a
    f.close()

.. **Good**:

**良い**:

.. code-block:: python

    with open('file.txt') as f:
        for line in f:
            print line

.. The ``with`` statement is better because it will ensure you always close the
.. file, even if an exception is raised inside the ``with`` block.

``with`` ステートメントは、 ``with`` ブロック内で例外が発生したとしても、ファイルを常に確実に閉じることができるので、より優れています。

.. Line Continuations
.. ~~~~~~~~~~~~~~~~~~

行の継続
~~~~~~~~

.. When a logical line of code is longer than the accepted limit, you need to
.. split it over multiple physical lines. The Python interpreter will join
.. consecutive lines if the last character of the line is a backslash. This is
.. helpful in some cases, but should usually be avoided because of its fragility:
.. a white space added to the end of the line, after the backslash, will break the
.. code and may have unexpected results.

論理行のコードが許容限度より長い場合は、複数の物理行に分割する必要があります。 行の最後の文字がバックスラッシュの場合、Pythonインタプリタは連続する行を結合します。 これはいくつかの場合に役立ちますが、通常、その脆弱性のために回避する必要があります。バックスラッシュの後ろに行末に空白を追加すると、コードが壊れて予期しない結果になることがあります。

.. A better solution is to use parentheses around your elements. Left with an
.. unclosed parenthesis on an end-of-line the Python interpreter will join the
.. next line until the parentheses are closed. The same behavior holds for curly
.. and square braces.

より良い解決策は、要素の周りにかっこを使用することです。 行末に閉じられていないカッコが残っていると、Pythonインタプリタはカッコが閉じられるまで次の行に結合します。 中括弧と中括弧も同じ動作をします。

.. **Bad**:

**悪い**:

.. code-block:: python

    my_very_big_string = """For a long time I used to go to bed early. Sometimes, \
        when I had put out my candle, my eyes would close so quickly that I had not even \
        time to say “I’m going to sleep.”"""

    from some.deep.module.inside.a.module import a_nice_function, another_nice_function, \
        yet_another_nice_function

.. **Good**:

**良い**:

.. code-block:: python

    my_very_big_string = (
        "For a long time I used to go to bed early. Sometimes, "
        "when I had put out my candle, my eyes would close so quickly "
        "that I had not even time to say “I’m going to sleep.”"
    )

    from some.deep.module.inside.a.module import (
        a_nice_function, another_nice_function, yet_another_nice_function)

.. However, more often than not, having to split a long logical line is a sign that
.. you are trying to do too many things at the same time, which may hinder
.. readability.

しかし、しばしば長い論理行を分割しなければならないことは、同時に多くのことをしようとしている兆候であり、読みやすさの妨げになりかねません。
