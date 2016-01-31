---
layout: post
title: "pyenv で Python 環境を管理する方法"
categories: [技術, メモ]
featured_image: shutterstock_130179881
---
Python の環境を管理する [pyenv][yyuu/pyenv - GitHub] というツールについて解説します。OS X には標準で Python が含まれていますが、標準の Python 環境に変更を加えるのは避けたいところです。なので、標準の Python 環境と切り離された Python 環境を pyenv で作成して管理してみましょう。

インストール
------------

Homebrew を使用して pyenv という Python 環境を管理するツールを下記のコマンドでインストールします。Homebrew がインストールされていない場合は [Homebrew で OS X のコマンドラインツールを管理する方法]を参考にしてください。

{% highlight bash %}
$ brew install pyenv
{% endhighlight %}

pyenv を使用できるようにするために下記のコマンドを実行してください。これでターミナルの起動時に pyenv が自動的に実行されます。

{% highlight bash %}
$ echo 'if which pyenv > /dev/null; then eval "$(pyenv init -)"; fi' >> ~/.bash_profile
{% endhighlight %}

実行後にターミナルを再起動するか、下記のコマンドを実行して ~/.bash_profile の設定を反映させます。

{% highlight bash %}
$ source ~/.bash_profile
{% endhighlight %}

これで pyenv のインストールは完了です。

Python 環境のインストール
-------------------------

pyenv を使用して Python 環境をインストールします。Python のバージョンを指定して Python 環境をインストールできます。pyenv でインストールできるバージョンを下記のコマンドで一覧してみましょう。

{% highlight bash %}
$ pyenv install --list
{% endhighlight %}

たくさんの Python のバージョンが表示されます。Python 2 系の最新版をインストールしましょう。（2015年2月6日現在のバージョン番号の最新は 2.7.9 です。）

ここでは Python 2.7.9 を下記のコマンドでインストールします。インストールには数分かかるので完了するまで待ちましょう。

{% highlight bash %}
$ pyenv install 2.7.9
{% endhighlight %}

Python 環境のインストールが完了したらシステムの Python 環境から新しい Python 環境に切り替えます。下記のコマンドを実行してください。（実際にインストールした Python のバージョンを指定してください。）

{% highlight bash %}
$ pyenv global 2.7.9
{% endhighlight %}

切り替えた状態で Python のバージョンを確認する下記のコマンドを実行してください。新しくインストールした Python のバージョンが表示されるはずです。

{% highlight bash %}
$ python --version
{% endhighlight %}

これで pyenv を使用して新しく Python 環境を作成することができました。

なお Python 環境をシステムのものに戻す場合は下記のコマンドを入力してください。何度でもシステムの Python 環境と新しくインストールした Python 環境を切り替えることができます。

{% highlight bash %}
$ pyenv global system
{% endhighlight %}

参考文献
--------

* [yyuu/pyenv - GitHub]

関連記事
--------

* [Homebrew で OS X のコマンドラインツールを管理する方法]

[Homebrew で OS X のコマンドラインツールを管理する方法]: {{ site.baseurl }}{% post_url 2015-01-30-how-to-manage-os-x-packages-by-the-homebrew %}

[yyuu/pyenv - GitHub]: http://github.com/yyuu/pyenv
{:target="_blank"}
