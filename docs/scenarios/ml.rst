.. ================
.. Machine Learning
.. ================

========
機械学習
========

.. Python has a vast number of libraries for data analysis, statistics and Machine Learning itself, making it a language of choice for many data scientists. 

Pythonには、データ分析、統計、機械学習のための膨大な数のライブラリがあり、多くのデータ科学者にとって選択肢の多い言語になっています。

.. Some widely used packages for Machine Learning and other Data Science applications are enlisted below.

マシンラーニングやその他のデータサイエンスアプリケーションで広く使われているパッケージのいくつかを以下に挙げます。

Scipy Stack
-----------

.. The Scipy stack consists of a bunch of core helper packages used in data science, for statistical analysis and visualising data. Because of its huge number of functionalities and ease of use, the Stack is considered a must-have for most data science applications.

Scipyスタックは、統計解析とデータの可視化のために、データサイエンスで使用される一連のコアヘルパーパッケージで構成されています。膨大な数の機能と使い易さのために、このスタックは、ほとんどのデータサイエンスアプリケーションに欠かせないものと考えられています。

.. The Stack consists of the following packages (link to documentation given):

Stackは以下のパッケージで構成されています（ドキュメントへのリンク）:

1. `NumPy <http://www.numpy.org/>`_
2. `SciPy library <https://www.scipy.org/>`_
3. `Matplotlib <http://matplotlib.org/>`_
4. `IPython <https://ipython.org/>`_
5. `pandas <http://pandas.pydata.org/>`_
6. `Sympy <http://www.sympy.org/en/index.html>`_
7. `nose <http://nose.readthedocs.io/en/latest/>`_

.. The stack also comes with Python bundled in, but has been excluded from the above list.

このスタックにはPythonも付属していますが、上記のリストから除外されています。

.. Installation
.. ~~~~~~~~~~~~

インストール
~~~~~~~~~~~~

.. For installing the full stack, or individual packages, you can refer to the instructions given `here <https://www.scipy.org/install.html>`_.

完全なスタックまたは個々のパッケージをインストールするには、 `here <https://www.scipy.org/install.html>`_ の指示を参照することができます。

.. **NB:** `Anaconda <https://www.continuum.io/anaconda-overview>`_ is highly preferred and recommended for installing and maintaining data science packages seamlessly.

**NB:** `Anaconda <https://www.continuum.io/anaconda-overview>`_ は、データサイエンスパッケージをシームレスにインストールして維持するために非常に推奨され、推奨されています。

scikit-learn
------------

.. Scikit is a free and open-source machine learning library for Python. It offers off-the-shelf functions to implement many algorithms like linear regression, classifiers, SVMs, k-means, Neural Networks etc. It also has a few sample datasets which can be directly used for training and testing.

ScikitはPythonのためのフリーでオープンソースの機械学習ライブラリです。線形回帰、分類器、SVM、k-means、ニューラルネットワークなどの多くのアルゴリズムを実装するための既製の関数を提供します。トレーニングやテストに直接使用できるサンプルデータセットもいくつかあります。

.. Because of its speed, robustness and easiness to use, it's one of the most widely-used libraries for many Machine Learning applications.

そのスピード、堅牢性、使いやすさのため、多くの機械学習アプリケーションで最も広く使用されているライブラリの1つです。

.. Installation
.. ~~~~~~~~~~~~

インストール
~~~~~~~~~~~~

.. Through PyPI:

PyPIを通じて:

.. code-block:: python
	
	pip install -U scikit-learn

.. Through conda:

condaを通して:

.. code-block:: python

	conda install scikit-learn

.. scikit-learn also comes in shipped with Anaconda (mentioned above). For more installation instructions, refer to `this link <http://scikit-learn.org/stable/install.html>`_.

scikit-learnにはAnaconda（上記参照）が同梱されています。 詳しいインストール方法については、 `このリンク <http://scikit-learn.org/stable/install.html>`_ を参照してください。

.. Example
.. ~~~~~~~

例
~~

.. For this example, we train a simple classifier on the `Iris dataset <http://en.wikipedia.org/wiki/Iris_flower_data_set>`_, which comes bundled in with scikit-learn.

この例では、簡単な分類子を `Iris dataset <http://en.wikipedia.org/wiki/Iris_flower_data_set>`_ でトレーニングします。これはscikit-learnでバンドルされています。

.. The dataset takes four features of flowers: sepal length, sepal width, petal length and petal width, and classifies them into three flower species (labels): setosa, versicolor or virginica. The labels have been represented as numbers in the dataset: 0 (setosa), 1 (versicolor) and 2 (virginica). 

このデータセットは、葉の長さ、葉の幅、花弁の長さ、花弁の幅の4つの特徴を取り、それらを3つの花種（ラベル）：セソサ、バーシカラー、またはバージニアに分類します。 ラベルはデータセット内の数字として表されています：0（setosa）、1（versicolor）、2（virginica）。

.. We shuffle the Iris dataset, and divide it into separate training and testing sets: keeping the last 10 data points for testing and rest for training. We then train the classifier on the training set, and predict on the testing set.

アイリスデータセットをシャッフルし、別々のトレーニングとテストセットに分けます：テストのための最後の10データポイントを保持し、トレーニングのために休みます。 次に、トレーニングセットの分類子を訓練し、テストセットを予測します。

.. code-block:: python

	from sklearn.datasets import load_iris 
	from sklearn import tree
	from sklearn.metrics import accuracy_score
	import numpy as np

	#loading the iris dataset
	iris = load_iris() 

	x = iris.data #array of the data
	y = iris.target #array of labels (i.e answers) of each data entry

	#getting label names i.e the three flower species
	y_names = iris.target_names 

	#taking random indices to split the dataset into train and test
	test_ids = np.random.permutation(len(x)) 

	#splitting data and labels into train and test
	#keeping last 10 entries for testing, rest for training

	x_train = x[test_ids[:-10]]
	x_test = x[test_ids[-10:]]

	y_train = y[test_ids[:-10]]
	y_test = y[test_ids[-10:]]

	#classifying using decision tree
	clf = tree.DecisionTreeClassifier()

	#training (fitting) the classifier with the training set
	clf.fit(x_train, y_train)

	#predictions on the test dataset
	pred = clf.predict(x_test)

	print pred #predicted labels i.e flower species
	print y_test #actual labels
	print (accuracy_score(pred, y_test))*100 #prediction accuracy

.. Since we're splitting randomly and the classifier trains on every iteration, the accuracy may vary. Running the above code gives:

私たちはランダムに分割しているので、分類器は繰り返しごとに列車を辿るため、精度は異なる場合があります。 上記のコードを実行すると、次のようになります。

.. code-block:: python

	[0 1 1 1 0 2 0 2 2 2]
	[0 1 1 1 0 2 0 2 2 2]
	100.0

.. The first line contains the labels (i.e flower species) of the testing data as predicted by our classifier, and the second line contains the actual flower species as given in the dataset. We thus get an accuracy of 100% this time.

最初の行には、分類器によって予測されたテストデータのラベル（すなわち、花種）が含まれ、2行目には、データセットに示された実際の花種が含まれています。 このため、今回は100％の精度が得られます。

.. More on scikit-learn can be read in the `documentation <http://scikit-learn.org/stable/user_guide.html>`_.

scikit-learnの詳細は `documentation <http://scikit-learn.org/stable/user_guide.html>`_ をご覧ください。
