.. Introduction
.. ============

導入
====

.. From the `official Python website <http://python.org/about/>`_:

`公式のPythonのウェブサイト <http://python.org/about/>`_：

.. Python is a general-purpose, high-level programming language similar
.. to Tcl, Perl, Ruby, Scheme, or Java. Some of its main key features
.. include:

PythonはTcl、Perl、Ruby、Scheme、Javaに似た汎用の高水準プログラミング言語です。主な機能の一部は次のとおりです。

.. * **very clear, readable syntax**

* **非常に明確で読みやすい構文**

  Pythonの哲学は、重要な空白で区切られたコードブロックから、分かりにくい句読点の代わりに直感的なキーワードに至るまでの読みやすさに焦点を当てています。

..   Python's philosophy focuses on readability, from code blocks
..   delineated with significant whitespace to intuitive keywords in
..   place of inscrutable punctuation.

.. * **extensive standard libraries and third party modules for virtually
..   any task**

* **事実上あらゆる作業のための広範な標準ライブラリと第三者モジュール**

  Pythonは、正規表現、ファイルIO、分数処理、オブジェクトのシリアライズなどのモジュールを含む豊富な標準ライブラリのために、「バッテリー同梱」という言葉で記述されることがあります。

  さらに、 `Python Package Index <http://pypi.python.org/pypi/>`_ は、ユーザがPerlの `CPAN <http://www.cpan.org>`_ と同様に、広く使われるようにパッケージを提出することができます。 `Django <http://www.djangoproject.com>`_ ウェブフレームワークや 数学のルーチンがセットされた `NumPy <http://numpy.scipy.org>`_ のような非常に強力なPythonフレームワークとツールのコミュニティが盛んです。

..   Python is sometimes described with the words "batteries included"
..   because of its extensive
..   `standard library <http://docs.python.org/library/>`_, which includes
..   modules for regular expressions, file IO, fraction handling,
..   object serialization, and much more.
.. 
..   Additionally, the
..   `Python Package Index <http://pypi.python.org/pypi/>`_ is available
..   for users to submit their packages for widespread use, similar to
..   Perl's `CPAN <http://www.cpan.org>`_. There is a thriving community
..   of very powerful Python frameworks and tools like
..   the `Django <http://www.djangoproject.com>`_ web framework and the
..   `NumPy <http://numpy.scipy.org>`_ set of math routines.

.. * **integration with other systems**

* **他のシステムとの統合**

  Pythonは `Java libraries <http://www.jython.org>`_ と統合することができ、企業のプログラマーが慣れ親しんだ豊富なJava環境で使用することができます。 また、スピードが本質である場合、 `CまたはC ++モジュールによって拡張 <http://docs.python.org/extending/>`_ されます。

..   Python can integrate with `Java libraries <http://www.jython.org>`_,
..   enabling it to be used with the rich Java environment that corporate
..   programmers are used to. It can also be
..   `extended by C or C++ modules <http://docs.python.org/extending/>`_
..   when speed is of the essence.

.. * **ubiquity on computers**

* **コンピュータの普及**

  PythonはWindows、\*nix、およびMacで利用できます。 Java仮想マシンが実行される場所であればどこでも実行できます。リファレンス実装のCPythonは、動作しているCコンパイラがあればどこにでもPythonをもたらすのに役立ちます。

..   Python is available on Windows, \*nix, and Mac. It runs wherever the
..   Java virtual machine runs, and the reference implementation CPython
..   can help bring Python to wherever there is a working C compiler.

.. * **friendly community**

* **フレンドリーコミュニティ**

  Pythonには、Wiki、会議、無数のリポジトリ、メーリングリスト、IRCチャンネルなどを管理する活気に満ちた大きな :ref:`コミュニティ <the-community>` があります。 Pythonコミュニティはこのガイドを書くのにも役立っています！

..   Python has a vibrant and large :ref:`community <the-community>`
..   which maintains wikis, conferences, countless repositories,
..   mailing lists, IRC channels, and so much more. Heck, the Python
..   community is even helping to write this guide!


.. _about-ref:

.. About This Guide
.. ----------------

このガイドについて
------------------

.. Purpose
.. ~~~~~~~

目的
~~~~

.. The Hitchhiker's Guide to Python exists to provide both novice and expert
.. Python developers a best practice handbook for the installation, configuration,
.. and usage of Python on a daily basis.

Pythonヒッチハイク・ガイド は、初心者でも熟練のPython開発者にも、Pythonのインストール、設定、および使用に関するベストプラクティスハンドブックを毎日提供するために存在します。


.. By the Community
.. ~~~~~~~~~~~~~~~~

コミュニティによる
~~~~~~~~~~~~~~~~~~

.. This guide is architected and maintained by `Kenneth Reitz
.. <https://github.com/kennethreitz>`_ in an open fashion. This is a
.. community-driven effort that serves one purpose: to serve the community.

このガイドは、 `Kenneth Reitz <https://github.com/kennethreitz>`_ によってオープンな方法で設計され維持されています。 これは、コミュニティに役立つという、1つの目的のために役立つコミュニティ主導型の取り組みです。

.. For the Community
.. ~~~~~~~~~~~~~~~~~

コミュニティのために
~~~~~~~~~~~~~~~~~~~~

.. All contributions to the Guide are welcome, from Pythonistas of all levels.
.. If you think there's a gap in what the Guide covers, fork the Guide on
.. GitHub and submit a pull request.

ガイドへの寄稿はすべてのレベルのPythonista達から歓迎されます。 ガイドに記載されているものにギャップがあると思われる場合は、ガイドをGitHubにフォークし、プルリクエストを提出してください。

.. Contributions are welcome from everyone, whether they're an old hand or a
.. first-time Pythonista, and the authors to the Guide will gladly help if you
.. have any questions about the appropriateness, completeness, or accuracy of
.. a contribution.

寄付の妥当性、完全性、正確性について疑問がある場合、寄稿者は誰でも歓迎されます。彼らが古くからPythonistaであっても、Guideの著者は喜んで助けてくれます。

.. To get started working on The Hitchhiker's Guide,
.. see the :doc:`/notes/contribute` page.

ヒッチハイク・ガイドの作業を開始するには、:doc:`/notes/contribute` ページを参照してください。
