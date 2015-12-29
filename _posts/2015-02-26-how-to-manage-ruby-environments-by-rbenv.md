---
layout: post
title: "rbenv で Ruby 環境を管理する方法"
categories: Ruby
---
Ruby の環境を管理する [rbenv][sstephenson/rbenv - GitHub] というツールについて解説します。OS X には標準で Ruby が含まれていますが、標準の Ruby 環境に変更を加えるのは避けたいところです。なので、標準の Ruby 環境と切り離された Ruby 環境を rbenv で作成して管理してみましょう。

インストール
------------

rbenv をインストールする前に readline を Homebrew を使用してインストールします。これは irb できちんと日本語を扱えるようにするためです。Homebrew がインストールされていない場合は [Homebrew で OS X のコマンドラインツールを管理する方法]を参考にしてください。

{% highlight bash %}
$ brew install readline
{% endhighlight %}

readline がインストールできたら Homebrew を使用して rbenv という Ruby 環境を管理するツールを下記のコマンドでインストールします。Ruby インタプリタなどの Ruby 環境を rbenv を使用して切り替えることができるようになります。

{% highlight bash %}
$ brew install rbenv
{% endhighlight %}

さらに Homebrew を使用して rbenv 用のプラグインである ruby-build をインストールします。ruby-build を使用することで Ruby 環境をインストールできるようになります。

{% highlight bash %}
$ brew install ruby-build
{% endhighlight %}

rbenv を使用できるようにするために下記のコマンドを実行してください。これでターミナルの起動時に rbenv が自動的に実行されます。

{% highlight bash %}
$ echo 'if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi' >> ~/.bash_profile
{% endhighlight %}

実行後にターミナルを再起動するか、下記のコマンドを実行して ~/.bash_profile の設定を反映させます。

{% highlight bash %}
$ source ~/.bash_profile
{% endhighlight %}

これで rbenv のインストールは完了です。

Ruby 環境のインストール
-----------------------

rbenv を使用して Ruby 環境をインストールします。Ruby のバージョンを指定して Ruby 環境をインストールできます。rbenv でインストールできるバージョンを下記のコマンドで一覧してみましょう。

{% highlight bash %}
$ rbenv install --list
{% endhighlight %}

たくさんの Ruby のバージョンが表示されます。Ruby 2.1 系の最新版をインストールしましょう。（2015年2月26日現在のバージョン番号の最新は 2.1.5 です。）

ここでは Ruby 2.1.5 を下記のコマンドでインストールします。インストールには数分かかるので完了するまで待ちましょう。その際、RUBY_CONFIGURE_OPTIONS で readline ライブラリのディレクトリを指定します。

{% highlight bash %}
$ RUBY_CONFIGURE_OPTS=--with-readline-dir=`brew --prefix readline` rbenv install 2.1.5
{% endhighlight %}

Ruby 環境のインストールが完了したらシステムの Ruby 環境から新しい Ruby 環境に切り替えます。下記のコマンドを実行してください。（実際にインストールした Ruby のバージョンを指定してください。）

{% highlight bash %}
$ rbenv global 2.1.5
{% endhighlight %}

切り替えた状態で Ruby のバージョンを確認する下記のコマンドを実行してください。新しくインストールした Ruby のバージョンが表示されるはずです。

{% highlight bash %}
$ ruby -v
{% endhighlight %}

これで rbenv を使用して新しく Ruby 環境を作成することができました。

なお Ruby 環境をシステムのものに戻す場合は下記のコマンドを入力してください。何度でもシステムの Ruby 環境と新しくインストールした Ruby 環境を切り替えることができます。

{% highlight bash %}
$ rbenv global system
{% endhighlight %}

参考文献
--------

* [sstephenson/rbenv - GitHub]

関連記事
--------

* [Homebrew で OS X のコマンドラインツールを管理する方法]

[Homebrew で OS X のコマンドラインツールを管理する方法]: {{ site.baseurl }}{% post_url 2015-01-30-how-to-manage-os-x-packages-by-the-homebrew %}

[sstephenson/rbenv - GitHub]: http://github.com/sstephenson/rbenv
{:target="_blank"}
