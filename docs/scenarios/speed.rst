.. Speed
.. =====

速度
====

.. CPython, the most commonly used implementation of Python, is slow for CPU bound
.. tasks. `PyPy`_ is fast.

最も一般的に使用されるPythonの実装であるCPythonは、CPUバインドされたタスクの速度が遅いです。 `PyPy`_ は高速です。

.. Using a slightly modified version of `David Beazley's`_ CPU bound test code
.. (added loop for multiple tests), you can see the difference between CPython
.. and PyPy's processing.

`David Beazley's`_ CPUバウンドテストコード（複数のテストで追加されたループ）を若干修正したものを使用すると、CPythonとPyPyの処理の違いを見ることができます。

.. code-block:: console

   # PyPy
   $ ./pypy -V
   Python 2.7.1 (7773f8fc4223, Nov 18 2011, 18:47:10)
   [PyPy 1.7.0 with GCC 4.4.3]
   $ ./pypy measure2.py
   0.0683999061584
   0.0483210086823
   0.0388588905334
   0.0440690517426
   0.0695300102234

.. code-block:: console

   # CPython
   $ ./python -V
   Python 2.7.1
   $ ./python measure2.py
   1.06774401665
   1.45412397385
   1.51485204697
   1.54693889618
   1.60109114647

.. Context
.. :::::::

コンテキスト
::::::::::::


The GIL
-------

.. `The GIL`_ (Global Interpreter Lock) is how Python allows multiple threads to
.. operate at the same time. Python's memory management isn't entirely thread-safe,
.. so the GIL is required to prevent multiple threads from running the same
.. Python code at once.

`The GIL`_ (Global Interpreter Lock) は、Pythonが複数のスレッドを同時に動作させる方法です。 Pythonのメモリ管理は完全にスレッドセーフではないため、複数のスレッドが同じPythonコードを同時に実行するのを防ぐためにGILが必要です。

.. David Beazley has a great `guide`_ on how the GIL operates. He also covers the
.. `new GIL`_ in Python 3.2. His results show that maximizing performance in a
.. Python application requires a strong understanding of the GIL, how it affects
.. your specific application, how many cores you have, and where your application
.. bottlenecks are.

David Beazley氏は、GILがどのように機能しているかについて素晴らしい `ガイド` を持っています。 彼はまた、Python 3.2で `new GIL`_ をカバーしています。 彼の結果は、Pythonアプリケーションのパフォーマンスを最大限にするには、GILの強み、アプリケーション固有のアプリケーションへの影響、コアの数、アプリケーションのボトルネックがどこにあるかを理解する必要があります。

.. C Extensions
.. ------------

C拡張機能
---------


The GIL
-------

.. `Special care`_ must be taken when writing C extensions to make sure you
.. register your threads with the interpreter.

あなたのスレッドをインタープリタに登録するためにC拡張を書くときには `特別な注意` が必要です。

.. C Extensions
.. ::::::::::::

C拡張機能
:::::::::


Cython
------

.. `Cython <http://cython.org/>`_ implements a superset of the Python language
.. with which you are able to write C and C++ modules for Python. Cython also
.. allows you to call functions from compiled C libraries. Using Cython allows
.. you to take advantage of Python's strong typing of variables and operations.

`Cython <http://cython.org/>`_ は、Python用のCとC ++モジュールを書くことができるPython言語のスーパーセットを実装しています。 Cythonでは、コンパイルされたCライブラリから関数を呼び出すこともできます。 Cythonを使うと、Pythonの強力な変数や演算のタイプを利用できます。

.. Here's an example of strong typing with Cython:

Cythonでの厳密な型付けの例を次に示します:

.. code-block:: cython

    def primes(int kmax):
    """Calculation of prime numbers with additional
    Cython keywords"""

        cdef int n, k, i
        cdef int p[1000]
        result = []
        if kmax > 1000:
            kmax = 1000
        k = 0
        n = 2
        while k < kmax:
            i = 0
            while i < k and n % p[i] != 0:
                i = i + 1
            if i == k:
                p[k] = n
                k = k + 1
                result.append(n)
            n = n + 1
        return result


.. This implementation of an algorithm to find prime numbers has some additional
.. keywords compared to the next one, which is implemented in pure Python:

素数を見つけるためのこのアルゴリズムの実装には、純粋なPythonで実装されている次のものと比較していくつかの追加のキーワードがあります。

.. code-block:: python

    def primes(kmax):
    """Calculation of prime numbers in standard Python syntax"""

        p = range(1000)
        result = []
        if kmax > 1000:
            kmax = 1000
        k = 0
        n = 2
        while k < kmax:
            i = 0
            while i < k and n % p[i] != 0:
                i = i + 1
            if i == k:
                p[k] = n
                k = k + 1
                result.append(n)
            n = n + 1
        return result

.. Notice that in the Cython version you declare integers and integer arrays
.. to be compiled into C types while also creating a Python list:

Cythonのバージョンでは、整数型と整数型の配列をC型にコンパイルしてPythonリストを作成することを宣言していることに注意してください。


.. code-block:: cython

    def primes(int kmax):
        """Calculation of prime numbers with additional
        Cython keywords"""

        cdef int n, k, i
        cdef int p[1000]
        result = []


.. code-block:: python

    def primes(kmax):
        """Calculation of prime numbers in standard Python syntax"""

        p = range(1000)
        result = []

.. What is the difference? In the upper Cython version you can see the
.. declaration of the variable types and the integer array in a similar way as
.. in standard C. For example `cdef int n,k,i` in line 3. This additional type
.. declaration (i.e. integer) allows the Cython compiler to generate more
.. efficient C code from the second version. While standard Python code is saved
.. in :file:`*.py` files, Cython code is saved in :file:`*.pyx` files.

違いはなんですか？ 上のCythonバージョンでは、標準Cと同様の方法で変数型と整数配列の宣言を見ることができます。たとえば、行3の `cdef int n、k、i` のようになります。この追加の型宣言（つまり整数） Cythonコンパイラは2番目のバージョンからより効率的なCコードを生成することができます。 標準のPythonコードは :file:`*.py` ファイルに保存されますが、Cythonコードは :file:`*.pyx` ファイルに保存されます。

.. What's the difference in speed? Let's try it!

スピードの違いは何ですか？ 試してみよう！

.. code-block:: python

	import time
	#activate pyx compiler
	import pyximport
	pyximport.install()
	#primes implemented with Cython
	import primesCy
	#primes implemented with Python
	import primes

	print "Cython:"
	t1= time.time()
	print primesCy.primes(500)
	t2= time.time()
	print "Cython time: %s" %(t2-t1)
	print ""
	print "Python"
	t1= time.time()
	print primes.primes(500)
	t2= time.time()
	print "Python time: %s" %(t2-t1)


.. These lines both need a remark:

これらの行はいずれも発言が必要です:

.. code-block:: python

    import pyximport
    pyximport.install()


.. The `pyximport` module allows you to import :file:`*.pyx` files (e.g.,
.. :file:`primesCy.pyx`) with the Cython-compiled version of the `primes`
.. function. The `pyximport.install()` command allows the Python interpreter to
.. start the Cython compiler directly to generate C-code, which is automatically
.. compiled to a :file:`*.so` C-library. Cython is then able to import this
.. library for you in your Python code, easily and efficiently. With the
.. `time.time()` function you are able to compare the time between these 2
.. different calls to find 500 prime numbers. On a standard notebook (dual core
.. AMD E-450 1.6 GHz), the measured values are:

`pyximport` モジュールは、 `primes` 関数のCythonでコンパイルされたバージョンで :file:`*.pyx` ファイル（例 :file:`primesCy.pyx`）をインポートすることを可能にします。 `pyximport.install()` コマンドはPythonインタプリタがCythonコンパイラを直接起動してCコードを生成できるようにします。これは自動的に :file:`*.so` Cライブラリにコンパイルされます。 Cythonでは、このライブラリをPythonコードで簡単に、効率的にインポートすることができます。 `time.time()` 関数を使うと、これら2つの異なる呼び出しの間の時間を比較して、500個の素数を見つけることができます。 標準のノートブック（デュアルコアAMD E-450 1.6 GHz）では、測定値は次のとおりです。

.. code-block:: console

    Cython time: 0.0054 seconds

    Python time: 0.0566 seconds


.. And here the output of an embedded `ARM beaglebone <http://beagleboard.org/Products/BeagleBone>`_ machine:

そしてここに埋め込まれた `ARM beaglebone <http://beagleboard.org/Products/BeagleBone>`_ マシンの出力があります:

.. code-block:: console

    Cython time: 0.0196 seconds

    Python time: 0.3302 seconds


Pyrex
-----


Shedskin?
---------

.. Concurrency
.. :::::::::::

並行性
::::::


Concurrent.futures
------------------

.. The `concurrent.futures`_ module is a module in the standard library that
.. provides a "high-level interface for asynchronously executing callables". It
.. abstracts away a lot of the more complicated details about using multiple
.. threads or processes for concurrency, and allows the user to focus on 
.. accomplishing the task at hand.

`concurrent.futures`_ モジュールは標準ライブラリのモジュールであり、 "非同期的に呼び出し可能なコールを実行するための高水準インターフェース" を提供します。これは、複数のスレッドやプロセスを並行処理に使用することに関するより複雑な詳細を抽象化し、ユーザが手近な作業を達成することに集中することを可能にします。

.. The `concurrent.futures`_ module exposes two main classes, the
.. `ThreadPoolExecutor` and the `ProcessPoolExecutor`. The ThreadPoolExecutor
.. will create a pool of worker threads that a user can submit jobs to. These jobs
.. will then be executed in another thread when the next worker thread becomes
.. available.  

`concurrent.futures`_ モジュールは `ThreadPoolExecutor` と `ProcessPoolExecutor` の2つの主要なクラスを公開します。 ThreadPoolExecutorは、ユーザーがジョブを送信できるワーカースレッドのプールを作成します。これらのジョブは、次のワーカー・スレッドが使用可能になると、別のスレッドで実行されます。

.. The ProcessPoolExecutor works in the same way, except instead of using multiple
.. threads for its workers, it will use multiple processes. This makes it possible
.. to side-step the GIL, however because of the way things are passed to worker
.. processes, only picklable objects can be executed and returned.

ProcessPoolExecutorは同じ方法で動作しますが、ワーカーに複数のスレッドを使用するのではなく、複数のプロセスを使用します。 これによりGILのサイドステップが可能になりますが、ワーカープロセスに渡される方法のために、picklableオブジェクトのみが実行されて返されます。

.. Because of the way the GIL works, a good rule of thumb is to use a
.. ThreadPoolExecutor when the task being executed involves a lot of blocking
.. (i.e. making requests over the network) and to use a ProcessPoolExecutor
.. executor when the task is computationally expensive.

GILの仕組みのおかげで、実行中のタスクには多くのブロッキング（ネットワーク経由での要求）があり、タスクが計算上高価な場合にはProcessPoolExecutorエグゼキュータを使用するときにThreadPoolExecutorを使用するのが良い方法です。

.. There are two main ways of executing things in parallel using the two
.. Executors. One way is with the `map(func, iterables)` method. This works
.. almost exactly like the builtin `map()` function, except it will execute
.. everything in parallel. :

2つのエグゼキュータを使用して並列実行するには、主に2つの方法があります。 1つの方法は `map(func, iterables)` メソッドです。 これは、すべてが並行して実行されることを除けば、組み込みの `map()` 関数とほぼ同じように機能します。 :

.. code-block:: python

    from concurrent.futures import ThreadPoolExecutor
    import requests

    def get_webpage(url):
        page = requests.get(url)
        return page

    pool = ThreadPoolExecutor(max_workers=5)

    my_urls = ['http://google.com/']*10  # Create a list of urls

    for page in pool.map(get_webpage, my_urls):
        # Do something with the result
        print(page.text)

.. For even more control, the `submit(func, *args, **kwargs)` method will schedule 
.. a callable to be executed ( as `func(*args, **kwargs)`) and returns a `Future`_
.. object that represents the execution of the callable.

さらに、 `submit(func, *args, **kwargs)` メソッドは、実行可能な呼び出しをスケジュールし (`func(*args, **kwargs)`)、 `Future`_ オブジェクトを返します。 呼び出し可能オブジェクトの実行を表します。

.. The Future object provides various methods that can be used to check on the
.. progress of the scheduled callable. These include:

Futureオブジェクトは、スケジュールされた呼び出し可能ファイルの進行状況をチェックするために使用できるさまざまなメソッドを提供します。 これらには、

.. cancel()
..     Attempt to cancel the call.
.. cancelled()
..     Return True if the call was successfully cancelled.
.. running()
..     Return True if the call is currently being executed and cannot be
..     cancelled.
.. done()
..     Return True if the call was successfully cancelled or finished running.
.. result()
..     Return the value returned by the call. Note that this call will block until
..     the scheduled callable returns by default.
.. exception()
..     Return the exception raised by the call. If no exception was raised then
..     this returns `None`. Note that this will block just like `result()`.
.. add_done_callback(fn)
..     Attach a callback function that will be executed (as `fn(future)`) when the
..     scheduled callable returns.

cancel()
    コールをキャンセルしようとしています。
cancelled()
    呼び出しが正常にキャンセルされた場合はTrueを返します。
running()
    呼び出しが現在実行中でキャンセルできない場合はTrueを返します。
done()
    呼び出しが正常に取り消されたか、実行が終了した場合はTrueを返します。
result()
    呼び出しによって返された値を返します。 このコールは、スケジュールされたコールバックがデフォルトで戻るまでブロックされます。
exception()
    呼び出しによって発生した例外を返します。 例外が発生しなかった場合、これは `None` を返します。 これは `result()` のようにブロックされることに注意してください。
add_done_callback(fn)
    スケジュールされたコールバックが返ってくるときに実行されるコールバック関数を ( `fn(future)` として)アタッチします。


.. code-block:: python

    from concurrent.futures import ProcessPoolExecutor, as_completed

    def is_prime(n):
        if n % 2 == 0:
            return n, False

        sqrt_n = int(n**0.5)
        for i in range(3, sqrt_n + 1, 2):
            if n % i == 0:
                return n, False
        return n, True

    PRIMES = [
        112272535095293,
        112582705942171,
        112272535095293,
        115280095190773,
        115797848077099,
        1099726899285419]

    futures = []
    with ProcessPoolExecutor(max_workers=4) as pool:
        # Schedule the ProcessPoolExecutor to check if a number is prime
        # and add the returned Future to our list of futures
        for p in PRIMES:
            fut = pool.submit(is_prime, p)
            futures.append(fut)

    # As the jobs are completed, print out the results
    for number, result in as_completed(futures):
        if result:
            print("{} is prime".format(number))
        else:
            print("{} is not prime".format(number))

.. The `concurrent.futures`_ module contains two helper functions for working with
.. Futures. The `as_completed(futures)` function returns an iterator over the list
.. of futures, yielding the futures as they complete.

`concurrent.futures`_ モジュールには、Futuresを扱うための2つのヘルパー関数が含まれています。 `as_completed(futures)` 関数は、先物リストのイテレーターを返し、完了したときの先物を返します。

.. The `wait(futures)` function will simply block until all futures in the list of
.. futures provided have completed.

提供された先物リストのすべての先物が完了するまで、 `wait(futures)` 機能は単にブロックされます。

.. For more information, on using the `concurrent.futures`_ module, consult the
.. official documentation.

`concurrent.futures`_ モジュールの使い方については、公式文書を参照してください。

.. Threading
.. ---------

スレッディング
--------------

.. The standard library comes with a `threading`_ module that allows a user to
.. work with multiple threads manually.

標準ライブラリには、ユーザが複数のスレッドを手動で扱うことを可能にする `threading`_ モジュールが付属しています。

.. Running a function in another thread is as simple as passing a callable and
.. it's arguments to `Thread`'s constructor and then calling `start()`:

別のスレッドで関数を実行するのは、呼び出し可能オブジェクトを `Thread` のコンストラクタに渡し、`start()` を呼び出すという単純な操作です。

.. code-block:: python

    from threading import Thread
    import requests

    def get_webpage(url):
        page = requests.get(url)
        return page

    some_thread = Thread(get_webpage, 'http://google.com/')
    some_thread.start()

.. To wait until the thread has terminated, call `join()`:

スレッドが終了するまで待つには `join()` を呼び出します:

.. code-block:: python

    some_thread.join()

.. After calling `join()`, it is always a good idea to check whether the thread is
.. still alive (because the join call timed out):

`join()` を呼び出した後は、スレッドがまだ生存しているかどうかを確認することをお勧めします（結合呼び出しがタイムアウトしたため）:

.. code-block:: python

    if some_thread.is_alive():
        print("join() must have timed out.")
    else:
        print("Our thread has terminated.")

.. Because multiple threads have access to the same section of memory, sometimes
.. there might be situations where two or more threads are trying to write to the
.. same resource at the same time or where the output is dependent on the sequence
.. or timing of certain events. This is called a `data race`_ or race condition. 
.. When this happens, the output will be garbled or you may encounter problems
.. which are difficult to debug. A good example is this `stackoverflow post`_.  

複数のスレッドが同じメモリセクションにアクセスできるため、同時に複数のスレッドが同じリソースに書き込もうとする状況や、出力が特定のイベントのシーケンスやタイミングに依存する状況が発生することがあります。 これは、 `data race`_ または競合状態と呼ばれます。 これが発生すると、出力が文字化けしたり、デバッグが困難な問題が発生することがあります。 良い例がこの `stackoverflow post`_ です。

.. The way this can be avoided is by using a `Lock`_ that each thread needs to
.. acquire before writing to a shared resource. Locks can be acquired and released
.. through either the contextmanager protocol (`with` statement), or by using
.. `acquire()` and `release()` directly. Here is a (rather contrived) example:

これを避ける方法は、各スレッドが共有リソースに書き込む前に取得する必要がある `Lock`_ を使用することです。 ロックは、コンテキストマネージャプロトコル (`with` 文)、または `acquire()` と `release()` を直接使用して取得して解放することができます。 ここに（やや工夫した）例があります:


.. code-block:: python

    from threading import Lock, Thread

    file_lock = Lock()

    def log(msg):
        with file_lock:
            open('website_changes.log', 'w') as f:
                f.write(changes)

    def monitor_website(some_website):
        """
        Monitor a website and then if there are any changes, 
        log them to disk.
        """
        while True:
            changes = check_for_changes(some_website)
            if changes:
                log(changes)

    websites = ['http://google.com/', ... ]
    for website in websites:
        t = Thread(monitor_website, website)
        t.start()

.. Here, we have a bunch of threads checking for changes on a list of sites and
.. whenever there are any changes, they attempt to write those changes to a file
.. by calling `log(changes)`. When `log()` is called, it will wait to acquire
.. the lock with `with file_lock:`. This ensures that at any one time, only one
.. thread is writing to the file. 

ここでは、サイトリストの変更を確認するためのスレッドがたくさんあります。変更があった場合は、 `log(changes)` を呼び出すことによってその変更をファイルに書き込もうとします。 `log()` が呼び出されると、 `with file_lock:` でロックを取得するのを待ちます。 これにより、一度に1つのスレッドのみがファイルに書き込まれます。

.. Spawning Processes
.. ------------------

産卵プロセス
------------


.. Multiprocessing
.. ---------------

マルチプロセッシング
--------------------


.. _`PyPy`: http://pypy.org
.. _`The GIL`: http://wiki.python.org/moin/GlobalInterpreterLock
.. _`guide`: http://www.dabeaz.com/python/UnderstandingGIL.pdf
.. _`New GIL`: http://www.dabeaz.com/python/NewGIL.pdf
.. _`Special care`: http://docs.python.org/c-api/init.html#threads
.. _`David Beazley's`: http://www.dabeaz.com/GIL/gilvis/measure2.py
.. _`concurrent.futures`: https://docs.python.org/3/library/concurrent.futures.html
.. _`Future`: https://docs.python.org/3/library/concurrent.futures.html#concurrent.futures.Future
.. _`threading`: https://docs.python.org/3/library/threading.html
.. _`stackoverflow post`: http://stackoverflow.com/questions/26688424/python-threads-are-printing-at-the-same-time-messing-up-the-text-output
.. _`data race`: https://en.wikipedia.org/wiki/Race_condition
