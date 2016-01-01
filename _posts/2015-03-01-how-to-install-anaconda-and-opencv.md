---
layout: post
title: "Anaconda と OpenCV をインストールする方法"
categories: [技術, メモ]
featured_image: d5e1ad1d
---
Python と科学計算パッケージのディストリビューションの [Anaconda] とコンピュータービジョンライブラリの [OpenCV] をインストールする方法を説明します。

Anaconda のインストール
-----------------------

Anaconda を pyenv を使用してインストールします。pyenv がインストールされていない場合は [pyenv で Python 環境を管理する方法]を参考にしてください。

pyenv をインストールしたら、pyenv で Anaconda をインストールします。

{% highlight bash %}
$ pyenv install anaconda-2.1.0
{% endhighlight %}

インストールが完了したら Python 環境を Anaconda に切り替えます。

{% highlight bash %}
$ pyenv global anaconda-2.1.0
{% endhighlight %}

OpenCV のインストール
---------------------

OpenCV を Anaconda 環境のパッケージ管理ツールの conda を使用してインストールします。

{% highlight bash %}
$ conda install -c https://conda.binstar.org/menpo opencv
{% endhighlight %}

OpenCV がインストールできたことを確認するために Python の REPL を起動します。

{% highlight bash %}
$ python
{% endhighlight %}

REPL で OpenCV ライブラリをインポートして OpenCV のバージョン番号を表示します。

{% highlight python %}
>>> import cv2
>>> cv2.__version__
'2.4.9.1'
>>> exit()
{% endhighlight %}

これでインストールは完了です。

関連記事
--------

* [pyenv で Python 環境を管理する方法]

[pyenv で Python 環境を管理する方法]: {{ site.baseurl }}{% post_url 2015-02-06-how-to-manage-python-environments-by-pyenv %}

[Anaconda]: http://store.continuum.io/cshop/anaconda/
{:target="_blank"}
[OpenCV]: http://opencv.org/
{:target="_blank"}
