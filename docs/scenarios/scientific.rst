.. =======================
.. Scientific Applications
.. =======================

======================
科学的アプリケーション
======================

.. Context
.. :::::::

コンテキスト
::::::::::::

.. Python is frequently used for high-performance scientific applications. It
.. is widely used in academia and scientific projects because it is easy to write
.. and performs well.

Pythonは、高性能な科学アプリケーションに頻繁に使用されています。それは書くことが容易で、うまくいくので、学問や科学プロジェクトで広く使われています。

.. Due to its high performance nature, scientific computing in Python often
.. utilizes external libraries, typically written in faster languages (like C, or
.. FORTRAN for matrix operations). The main libraries used are `NumPy`_, `SciPy`_
.. and `Matplotlib`_. Going into detail about these libraries is beyond the scope
.. of the Python guide. However, a comprehensive introduction to the scientific
.. Python ecosystem can be found in the `Python Scientific Lecture Notes
.. <http://scipy-lectures.github.com/>`_

その高性能な性質から、Pythonでの科学計算は、一般的に高速言語（CやFORTRANなど）で書かれた外部ライブラリを利用することがよくあります。使用される主なライブラリは、 `NumPy`_ 、`SciPy`_ 、 `Matplotlib`_ です。これらのライブラリについて詳しくは、Pythonのガイドの範囲を超えています。しかし、科学的なPythonエコシステムの包括的な紹介は、 `Python Scientific Lecture Notes <http://scipy-lectures.github.com/>`_


.. Tools
.. :::::

ツール
::::::

IPython
-------

.. `IPython <http://ipython.org/>`_ is an enhanced version of Python interpreter,
.. which provides features of great interest to scientists. The `inline mode`
.. allows graphics and plots to be displayed in the terminal (Qt based version).
.. Moreover, the `notebook` mode supports literate programming and reproducible
.. science generating a web-based Python notebook. This notebook allows you to
.. store chunks of Python code along side the results and additional comments
.. (HTML, LaTeX, Markdown). The notebook can then be shared and exported in various
.. file formats.

`IPython <http://ipython.org/>`_ は、科学者に大きな関心を寄せている機能を提供するPythonインタープリタの拡張バージョンです。 `インラインモード` は、グラフィックスとプロットを端末に表示することができます（Qtベースのバージョン）。さらに、 `ノートブック` モードは、ウェブベースのPythonノートブックを生成するリテラートプログラミングと再現可能な科学をサポートしています。このノートブックでは、結果と追加のコメント（HTML、LaTeX、Markdown）の横にPythonコードのチャンクを保存することができます。ノートブックは、さまざまなファイル形式で共有してエクスポートすることができます。


Libraries
:::::::::

NumPy
-----

.. `NumPy <http://numpy.scipy.org/>`_ is a low level library written in C (and
.. FORTRAN) for high level mathematical functions. NumPy cleverly overcomes the
.. problem of running slower algorithms on Python by using multidimensional arrays
.. and functions that operate on arrays. Any algorithm can then be expressed as a
.. function on arrays, allowing the algorithms to be run quickly.

`NumPy <http://numpy.scipy.org/>`_ は、高レベルの数学的関数のためにC（およびFORTRAN）で書かれた低レベルのライブラリです。 NumPyは、多次元配列や配列を操作する関数を使用して、Python上でより遅いアルゴリズムを実行する問題を巧みに克服します。 どのアルゴリズムも配列の関数として表現でき、アルゴリズムを素早く実行できます。

.. NumPy is part of the SciPy project, and is released as a separate library so
.. people who only need the basic requirements can use it without installing the
.. rest of SciPy.

NumPyはSciPyプロジェクトの一部であり、基本的な要件だけを必要とする人はSciPyの残りの部分をインストールせずに使用できるように、別のライブラリとしてリリースされています。

.. NumPy is compatible with Python versions 2.4 through to 2.7.2 and 3.1+.

NumPyは、Python 2.4から2.7.2および3.1以降のバージョンと互換性があります。

Numba
-----

.. `Numba <http://numba.pydata.org>`_ is a NumPy aware Python compiler
.. (just-in-time (JIT) specializing compiler) which compiles annotated Python (and
.. NumPy) code to LLVM (Low Level Virtual Machine) through special decorators.
.. Briefly, Numba uses a system that compiles Python code with LLVM to code which
.. can be natively executed at runtime.

`Numba <http://numba.pydata.org>`_ はNumPy対応Pythonコンパイラ（Just-In-Time（JIT）専門コンパイラ）で、注釈付きPython（およびNumPy）コードをLLVM（Low Level Virtual Machine） 特別なデコレータを通して。 簡潔に言えば、Numbaは、実行時にネイティブに実行できるコードにLLVMを使用してPythonコードをコンパイルするシステムを使用します。

SciPy
-----

.. `SciPy <http://scipy.org/>`_ is a library that uses NumPy for more mathematical
.. functions. SciPy uses NumPy arrays as the basic data structure, and comes
.. with modules for various commonly used tasks in scientific programming,
.. including linear algebra, integration (calculus), ordinary differential equation
.. solving and signal processing.

`SciPy <http://scipy.org/>`_ はNumPyをより多くの数学的関数に使用するライブラリです。 SciPyはNumPy配列を基本的なデータ構造として使用し、線形代数、積分（微積分）、常微分方程式の解法、信号処理など、科学プログラミングのさまざまな一般的なタスクのモジュールを備えています。

Matplotlib
----------

.. `Matplotlib <http://matplotlib.sourceforge.net/>`_ is a flexible plotting
.. library for creating interactive 2D and 3D plots that can also be saved as
.. manuscript-quality figures. The API in many ways reflects that of `MATLAB
.. <http://www.mathworks.com/products/matlab/>`_, easing transition of MATLAB
.. users to Python. Many examples, along with the source code to re-create them,
.. are available in the `matplotlib gallery
.. <http://matplotlib.sourceforge.net/gallery.html>`_.

`Matplotlib <http://matplotlib.sourceforge.net/>`_ は、インタラクティブな2Dと3Dプロットを作成するための柔軟なプロットライブラリであり、原稿の質の高い数字として保存することもできます。 APIは多くの点で、 `MATLAB <http://www.mathworks.com/products/matlab/>`_ を反映しており、MATLABユーザーのPythonへの移行を容易にしています。多くの例とそれらを再作成するソースコードは、 `matplotlib gallery <http://matplotlib.sourceforge.net/gallery.html>`_ で利用できます。

Pandas
------

.. `Pandas <http://pandas.pydata.org/>`_ is data manipulation library
.. based on Numpy which provides many useful functions for accessing,
.. indexing, merging and grouping data easily. The main data structure (DataFrame)
.. is close to what could be found in the R statistical package; that is,
.. heterogeneous data tables with name indexing, time series operations and
.. auto-alignment of data.

`Pandas <http://pandas.pydata.org/>`_ は、Numpyをベースにしたデータ操作ライブラリであり、データのアクセス、索引付け、マージ、およびグループ化を容易にするための多くの便利な機能を提供します。 主なデータ構造（DataFrame）は、R統計パッケージにあるものに近いです。 つまり、名前の索引付け、時系列操作、およびデータの自動整列を使用する異種データ表です。

Rpy2
----

.. `Rpy2 <http://rpy2.bitbucket.org>`_ is a Python binding for the R
.. statistical package allowing the execution of R functions from Python and
.. passing data back and forth between the two environments. Rpy2 is the object
.. oriented implementation of the `Rpy <http://rpy.sourceforge.net/rpy.html>`_
.. bindings.

`Rpy2 <http://rpy2.bitbucket.org>`_ はPythonからのR関数の実行と2つの環境間でのデータの受け渡しを可能にするR統計パッケージのPythonバインディングです。 Rpy2はオブジェクト指向の実装で、 `Rpy <http://rpy.sourceforge.net/rpy.html>`_ バインディング。

PsychoPy
--------

.. `PsychoPy <http://www.psychopy.org/>`_ is a library for cognitive scientists
.. allowing the creation of cognitive psychology and neuroscience experiments.
.. The library handles presentation of stimuli, scripting of experimental design
.. and data collection.

`Rpy2 <http://rpy2.bitbucket.org>`_ はPythonからのR関数の実行と2つの環境間でのデータの受け渡しを可能にするR統計パッケージのPythonバインディングです。 Rpy2は `Rpy <http://rpy.sourceforge.net/rpy.html>`_ バインディングのオブジェクト指向の実装です。


.. Resources
.. :::::::::

リソース
::::::::

.. Installation of scientific Python packages can be troublesome, as many of
.. these packages are implemented as Python C extensions which need to be compiled.
.. This section lists various so-called scientific Python distributions which
.. provide precompiled and easy-to-install collections of scientific Python
.. packages.

科学的なPythonパッケージのインストールは、これらのパッケージの多くがコンパイルする必要があるPython C拡張として実装されるので、面倒なことがあります。この節では、サイエンスPythonパッケージのプリコンパイル済みでインストールが簡単なコレクションを提供する、さまざまないわゆる科学Pythonディストリビューションを紹介します。

.. Unofficial Windows Binaries for Python Extension Packages
.. ---------------------------------------------------------

Python拡張パッケージ用の非公式Windowsバイナリ
---------------------------------------------

.. Many people who do scientific computing are on Windows, yet many of the
.. scientific computing packages are notoriously difficult to build and install on
.. this platform. `Christoph Gohlke <http://www.lfd.uci.edu/~gohlke/pythonlibs/>`_
.. however, has compiled a list of Windows binaries for many useful Python
.. packages.  The list of packages has grown from a mainly scientific Python
.. resource to a more general list. If you're on Windows, you may want to check it
.. out.

科学的コンピューティングを行う多くの人々がWindows上にありますが、科学的コンピューティングパッケージの多くは、このプラットフォームで構築してインストールすることは難しいことで有名です。 `Christoph Gohlke <http://www.lfd.uci.edu/~gohlke/pythonlibs/>`_ しかし、多くの便利なPythonパッケージのWindowsバイナリのリストをコンパイルしました。パッケージのリストは、主に科学的なPythonリソースからより一般的なリストに成長しました。 Windowsの場合は、チェックアウトすることができます。

Anaconda
--------

.. `Continuum Analytics <http://continuum.io/>`_ offers the `Anaconda
.. Python Distribution <https://store.continuum.io/cshop/anaconda>`_ which
.. includes all the common scientific Python packages as well as many packages
.. related to data analytics and big data. Anaconda itself is free, and
.. Continuum sells a number of proprietary add-ons. Free licenses for the
.. add-ons are available for academics and researchers.

`Continuum Analytics <http://continuum.io/>`_ は `Anaconda Python Distribution <https://store.continuum.io/cshop/anaconda>`_ を提供しています。これには一般的な科学Pythonパッケージと多くの パッケージは、データ分析と大きなデータに関連しています。 Anaconda自体は無料で、Continuumは独自のアドオンを多数販売しています。 アドオンの無料ライセンスは、学者や研究者が利用できます。

Canopy
------

.. `Canopy <https://www.enthought.com/products/canopy/>`_ is another scientific
.. Python distribution, produced by `Enthought <https://www.enthought.com/>`_.
.. A limited 'Canopy Express' variant is available for free, but Enthought
.. charges for the full distribution. Free licenses are available for academics.

`Canopy <https://www.enthought.com/products/canopy/>`_ は、 `Enthought <https://www.enthought.com/>`_ によって作成されたもう一つの科学的なPythonディストリビューションです。 限定された `Canopy Express` の亜種は無料で入手できますが、完全配布の場合はEnthoughtが請求します。 学者は無料ライセンスを利用できます。
