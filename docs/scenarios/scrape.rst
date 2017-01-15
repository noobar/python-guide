.. HTML Scraping
.. =============

HTMLスクレイピング
=================

.. Web Scraping
.. ------------

Webスクレイピング
-----------------

.. Web sites are written using HTML, which means that each web page is a
.. structured document. Sometimes it would be great to obtain some data from
.. them and preserve the structure while we're at it. Web sites don't always
.. provide their data in comfortable formats such as ``csv`` or ``json``.

WebサイトはHTMLを使用して書かれています。つまり、各Webページは構造化文書です。時には、それらからいくつかのデータを取得し、私たちがその間に構造を保存することは素晴らしいことでしょう。 Webサイトは、 ``csv`` や ``json`` などの快適な形式でデータを提供するとは限りません。

.. This is where web scraping comes in. Web scraping is the practice of using a
.. computer program to sift through a web page and gather the data that you need
.. in a format most useful to you while at the same time preserving the structure
.. of the data.

Webスクレイピングは、コンピュータプログラムを使用してWebページを調べ、必要なデータを、同時にデータの構造を保持しながら、最も便利な形式で収集するプラクティスです。

.. lxml and Requests
.. -----------------

lxml と Requests
----------------

.. `lxml <http://lxml.de/>`_ is a pretty extensive library written for parsing
.. XML and HTML documents very quickly, even handling messed up tags in the
.. process. We will also be using the
.. `Requests <http://docs.python-requests.org/en/latest/>`_ module instead of the
.. already built-in urllib2 module due to improvements in speed and readability.
.. You can easily install both using ``pip install lxml`` and
.. ``pip install requests``.

`lxml <http://lxml.de/>`_ はXMLやHTML文書を非常に素早く解析するために書かれた非常に広範囲なライブラリです。 また、速度と可読性が向上したため、すでに組み込まれているurllib2モジュールの代わりに `Requests <http://docs.python-requests.org/ja/latest/>`_ モジュールも使用します。 ``pip install lxml`` と ``pip install requests`` の両方を使って簡単にインストールできます。

.. Let's start with the imports:

インポートから始めましょう:

.. code-block:: python

    from lxml import html
    import requests

.. Next we will use ``requests.get`` to retrieve the web page with our data,
.. parse it using the ``html`` module and save the results in ``tree``:

次に、 ``requests.get`` を使ってデータを含むウェブページを取得し、 ``html`` モジュールを使って解析し、結果を ``tree`` に保存します:

.. code-block:: python

    page = requests.get('http://econpy.pythonanywhere.com/ex/001.html')
    tree = html.fromstring(page.content)

.. (We need to use ``page.content`` rather than ``page.text`` because
.. ``html.fromstring`` implicitly expects ``bytes`` as input.)

（ ``page.text`` ではなく ``page.content`` を使用する必要があります。なぜなら、 ``html.fromstring`` は入力として ``bytes`` を暗黙的に期待しているからです。）

.. ``tree`` now contains the whole HTML file in a nice tree structure which
.. we can go over two different ways: XPath and CSSSelect. In this example, we
.. will focus on the former.

``tree`` にはHTMLファイル全体がツリー構造で表示され、XPathとCSSSelectの2通りの方法があります。この例では、前者に焦点を当てます。

.. XPath is a way of locating information in structured documents such as
.. HTML or XML documents. A good introduction to XPath is on
.. `W3Schools <http://www.w3schools.com/xsl/xpath_intro.asp>`_ .

XPathは、HTMLやXML文書などの構造化文書に情報を配置する方法です。 XPathの良い紹介は、 `W3Schools <http://www.w3schools.com/xsl/xpath_intro.asp>`_ です。

.. There are also various tools for obtaining the XPath of elements such as
.. FireBug for Firefox or the Chrome Inspector. If you're using Chrome, you
.. can right click an element, choose 'Inspect element', highlight the code,
.. right click again and choose 'Copy XPath'.

FireBug for FirefoxやChrome Inspectorなどの要素のXPathを取得するためのさまざまなツールもあります。 Chromeを使用している場合は、要素を右クリックして `要素を検査` を選択し、コードを強調表示してもう一度右クリックし、 `XPathのコピー` を選択します。

.. After a quick analysis, we see that in our page the data is contained in
.. two elements - one is a div with title 'buyer-name' and the other is a
.. span with class 'item-price':

簡単な分析の結果、このページのデータは2つの要素に分かれています.1つはdivというタイトルで、 `buyer-name` という名前のクラスと `item-price` というクラスのスパンです。

.. code-block:: html

    <div title="buyer-name">Carson Busses</div>
    <span class="item-price">$29.95</span>

.. Knowing this we can create the correct XPath query and use the lxml
.. ``xpath`` function like this:

これを知ることで、正しいXPathクエリを作成し、lxmlの ``xpath`` 関数を以下のように使用することができます:

.. code-block:: python

    #This will create a list of buyers:
    buyers = tree.xpath('//div[@title="buyer-name"]/text()')
    #This will create a list of prices
    prices = tree.xpath('//span[@class="item-price"]/text()')

.. Let's see what we got exactly:

私たちが正確に何を得たかを見てみましょう:

.. code-block:: python

    print 'Buyers: ', buyers
    print 'Prices: ', prices

::

    Buyers:  ['Carson Busses', 'Earl E. Byrd', 'Patty Cakes',
    'Derri Anne Connecticut', 'Moe Dess', 'Leda Doggslife', 'Dan Druff',
    'Al Fresco', 'Ido Hoe', 'Howie Kisses', 'Len Lease', 'Phil Meup',
    'Ira Pent', 'Ben D. Rules', 'Ave Sectomy', 'Gary Shattire',
    'Bobbi Soks', 'Sheila Takya', 'Rose Tattoo', 'Moe Tell']

    Prices:  ['$29.95', '$8.37', '$15.26', '$19.25', '$19.25',
    '$13.99', '$31.57', '$8.49', '$14.47', '$15.86', '$11.11',
    '$15.98', '$16.27', '$7.50', '$50.85', '$14.26', '$5.68',
    '$15.00', '$114.07', '$10.09']

.. Congratulations! We have successfully scraped all the data we wanted from
.. a web page using lxml and Requests. We have it stored in memory as two
.. lists. Now we can do all sorts of cool stuff with it: we can analyze it
.. using Python or we can save it to a file and share it with the world.

おめでとう！ lxmlとRequestsを使用して、Webページから必要なすべてのデータを正常に削除しました。 私たちはそれを2つのリストとしてメモリに格納しています。 今では、あらゆる種類のクールなことを行うことができます。Pythonを使用して解析するか、ファイルに保存して世界と共有できます。

.. Some more cool ideas to think about are modifying this script to iterate
.. through the rest of the pages of this example dataset, or rewriting this
.. application to use threads for improved speed.

このスクリプトを修正して、このサンプルデータセットの残りのページを繰り返したり、このアプリケーションを書き直してスレッドを使用して速度を向上させたりすることも考えられます。
