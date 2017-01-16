.. Cryptography
.. ============

暗号
====

.. Cryptography
.. ------------

暗号
----

.. `Cryptography <https://cryptography.io/en/latest/>`_ is an actively developed
.. library that provides cryptographic recipes and primitives. It supports 
.. Python 2.6-2.7, Python 3.3+ and PyPy.

`Cryptography <https://cryptography.io/en/latest/>`_ は、暗号レシピとプリミティブを提供する、積極的に開発されたライブラリです。 Python 2.6-2.7、Python 3.3+、PyPyをサポートしています。


.. Cryptography is divided into two layers of recipes and hazardous materials
.. (hazmat).  The recipes layer provides simple API for proper symmetric
.. encryption and the hazmat layer provides low-level cryptographic primitives.

暗号は、レシピと危険物（ハザード）の2つの層に分かれています。 レシピ層は適切な共通鍵暗号化のための簡単なAPIを提供し、ハザード層は低レベルの暗号プリミティブを提供します。



.. Installation
.. ~~~~~~~~~~~~

インストール
~~~~~~~~~~~~

.. code-block:: console

    $ pip install cryptography

.. Example
.. ~~~~~~~

例
~~

.. Example code using high level symmetric encryption recipe:

高レベルの共通鍵暗号レシピを使用したコード例:

.. code-block:: python

	from cryptography.fernet import Fernet
	key = Fernet.generate_key()
	cipher_suite = Fernet(key)
	cipher_text = cipher_suite.encrypt(b"A really secret message. Not for prying eyes.")
	plain_text = cipher_suite.decrypt(cipher_text)




PyCrypto
--------

.. `PyCrypto <https://www.dlitz.net/software/pycrypto/>`_ is another library,
.. which provides secure hash functions and various encryption algorithms. It
.. supports Python version 2.1 through 3.3.

`PyCrypto <https://www.dlitz.net/software/pycrypto/>`_ は安全なハッシュ関数とさまざまな暗号化アルゴリズムを提供する別のライブラリです。 Python 2.1から3.3までのバージョンをサポートしています。

.. Installation
.. ~~~~~~~~~~~~

インストール
~~~~~~~~~~~~

.. code-block:: console

    $ pip install pycrypto

.. Example
.. ~~~~~~~

例
~~

.. code-block:: python

	from Crypto.Cipher import AES
	# Encryption
	encryption_suite = AES.new('This is a key123', AES.MODE_CBC, 'This is an IV456')
	cipher_text = encryption_suite.encrypt("A really secret message. Not for prying eyes.")

	# Decryption
	decryption_suite = AES.new('This is a key123', AES.MODE_CBC, 'This is an IV456')
	plain_text = decryption_suite.decrypt(cipher_text)
