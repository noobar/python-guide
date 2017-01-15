.. Interfacing with C/C++ Libraries
.. ================================

C/C ++ライブラリとのインタフェース
==================================

.. C Foreign Function Interface
.. ----------------------------

C外部関数インタフェース
-----------------------

.. `CFFI <https://cffi.readthedocs.io/en/latest/>`_ provides a simple to use
.. mechanism for interfacing with C from both CPython and PyPy. It supports two
.. modes: an inline ABI compatibility mode (example provided below), which allows
.. you to dynamically load and run functions from executable modules (essentially
.. exposing the same functionality as LoadLibrary or dlopen), and an API mode,
.. which allows you to build C extension modules.

`CFFI <https://cffi.readthedocs.io/en/latest/>`_ は、CPythonとPyPyの両方からCとインタフェースするための使いやすいメカニズムを提供します。実行可能モジュール（LoadLibraryまたはdlopenと同じ機能を本質的に公開します）から関数を動的にロードおよび実行できるインラインABI互換モード（下記の例）とAPIモードをサポートしています。 C拡張モジュール。

.. ABI Interaction
.. ~~~~~~~~~~~~~~~

ABIインタラクション
~~~~~~~~~~~~~~~~~~~

.. code-block:: python
    :linenos:

    from cffi import FFI
    ffi = FFI()
    ffi.cdef("size_t strlen(const char*);")
    clib = ffi.dlopen(None)
    length = clib.strlen("String to be evaluated.")
    # prints: 23
    print("{}".format(length))

ctypes
------

.. `ctypes <https://docs.python.org/3/library/ctypes.html>`_ is the de facto
.. library for interfacing with C/C++ from CPython, and it provides not only
.. full access to the native C interface of most major operating systems (e.g.,
.. kernel32 on Windows, or libc on \*nix), but also provides support for loading
.. and interfacing with dynamic libraries, such as DLLs or shared objects at
.. runtime. It does bring along with it a whole host of types for interacting
.. with system APIs, and allows you to rather easily define your own complex
.. types, such as structs and unions, and allows you to modify things such as
.. padding and alignment, if needed. It can be a bit crufty to use, but in
.. conjunction with the `struct <https://docs.python.org/3.5/library/struct.html>`_
.. module, you are essentially provided full control over how your data types get
.. translated into something usable by a pure C(++) method.

`ctypes <https://docs.python.org/3/library/ctypes.html>`_ はCPythonのC / C ++とのインタフェースのための事実上のライブラリであり、CのネイティブCインタフェースへのフルアクセスだけでなく、 （例えば、Windowsの場合はkernel32、\*nixの場合はlibc）、実行時にDLLや共有オブジェクトなどの動的ライブラリを読み込み、インタフェースするためのサポートも提供します。 システムAPIとやりとりするためのさまざまな型の型を持ち合わせており、構造体や共用体などの複雑な型を簡単に定義でき、必要に応じてパディングやアラインメントなどの変更が可能です。 使用するのはちょっと難しいかもしれませんが、 `struct <https://docs.python.org/3.5/library/struct.html>`_ モジュールと関連して、基本的にあなたのデータ型 純粋なC（++）メソッドで使用可能なものに変換されます。

.. Struct Equivalents
.. ~~~~~~~~~~~~~~~~~~

構造体の構造
~~~~~~~~~~~~

:file:`MyStruct.h`

.. code-block:: c
    :linenos:

    struct my_struct {
        int a;
        int b;
    };

:file:`MyStruct.py`

.. code-block:: python
    :linenos:

    import ctypes
    class my_struct(ctypes.Structure):
        _fields_ = [("a", c_int),
                    ("b", c_int)]

SWIG
----

.. `SWIG <http://www.swig.org>`_, though not strictly Python focused (it supports a
.. large number of scripting languages), is a tool for generating bindings for
.. interpreted languages from C/C++ header files. It is extremely simple to use:
.. the consumer simply needs to define an interface file (detailed in the
.. tutorial and documentations), include the requisite C/C++ headers, and run
.. the build tool against them. While it does have some limits, (it currently
.. seems to have issues with a small subset of newer C++ features, and getting
.. template-heavy code to work can be a bit verbose), it provides a great deal
.. of power and exposes lots of features to Python with little effort.
.. Additionally, you can easily extend the bindings SWIG creates (in the
.. interface file) to overload operators and built-in methods, effectively re-
.. cast C++ exceptions to be catchable by Python, etc.

`SWIG <http://www.swig.org>`_ は、厳密にはPythonに焦点を当てていませんが（スクリプト言語の数が多い）、C/C++ ヘッダーファイルから解釈言語用のバインディングを生成するためのツールです。 消費者はインターフェイスファイル（チュートリアルとドキュメントで詳述）を定義し、必要なC / C ++ヘッダーを組み込み、それらに対してビルドツールを実行するだけで簡単に使用できます。 それにはいくつかの制限がありますが（現在、新しいC ++機能の小さなサブセットに問題があるようで、テンプレートの重いコードを少し冗長にすると少し冗長になります）、多くの機能を提供し、多くの機能を公開します 少しの努力でPythonに さらに、SWIGが（インターフェイスファイル内で）作成したバインディングを演算子や組み込みメソッドのオーバーロードに容易に拡張でき、効果的にC ++例外を再キャストしてPythonなどがキャッチ可能にすることができます。

.. Example: Overloading __repr__
.. ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

例: __repr__ のオーバーロード
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:file:`MyClass.h`

.. code-block:: c++
    :linenos:

    #include <string>
    class MyClass {
    private:
        std::string name;
    public:
        std::string getName();
    };

:file:`myclass.i`

.. code-block:: c++
    :linenos:

    %include "string.i"

    %module myclass
    %{
    #include <string>
    #include "MyClass.h"
    %}

    %extend MyClass {
        std::string __repr__()
        {
            return $self->getName();
        }
    }

    %include "MyClass.h"


Boost.Python
------------

.. `Boost.Python <http://www.boost.org/doc/libs/1_59_0/libs/python/doc/>`_
.. requires a bit more manual work to expose C++ object functionality, but
.. it is capable of providing all the same features SWIG does and then some,
.. to include providing wrappers to access PyObjects in C++, extracting SWIG-
.. wrapper objects, and even embedding bits of Python into your C++ code.

`Boost.Python <http://www.boost.org/doc/libs/1_59_0/libs/python/doc/>`_ では、C++オブジェクトの機能を公開するために少し手作業が必要ですが、すべての 同じ機能をSWIGが実行し、C++でPyObjectにアクセスするためのラッパーを提供したり、SWIGラッパーオブジェクトを抽出したり、PythonのビットをC++コードに埋め込んだりすることもできます。
