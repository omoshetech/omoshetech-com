---
layout: post
title: "新しいラムダ式 - Ruby 技術者認定試験改訂対策 #4"
categories: Ruby
---
[Ruby 技術者認定試験制度]の改訂により Ruby のバージョンが 1.8 から 2.1 になったので、その変更点を試験対策の観点で [Ruby 技術者認定試験改訂のお知らせ]を参考にしつつまとめていきます。第4回は新しいラムダ式についてです。


概要
----

Ruby 1.9 に新しいラムダ式が追加されました。

{% highlight ruby %}
->(x) { puts x }
{% endhighlight %}

これは lambda を使用した下記の式と同じです。

{% highlight ruby %}
lambda {|x| puts x }
{% endhighlight %}

例
--

### 引数なし

{% highlight ruby %}
-> { puts 'hello' }
{% endhighlight %}

### 引数1つ

{% highlight ruby %}
->(x) { puts x }
-> x { puts x }
{% endhighlight %}

### 引数2つ

{% highlight ruby %}
->(x, y) { puts x, y }
-> x, y { puts x, y }
{% endhighlight %}

--------------------------------------------------------------------------------

Ruby 1.9 で追加された新しいラムダ式について説明しました。ラムダ式のリテラルを追加しただけの変更です。

次回は Enumerable#lazy について説明します。

参考文献
--------

* [Ruby 技術者認定試験制度]
* [Ruby 技術者認定試験改訂のお知らせ]
* [Rubyで使われる記号の意味（正規表現の複雑な記号は除く） - Ruby 2.1.0 リファレンスマニュアル]

関連記事
--------

* [キーワード引数 - Ruby 技術者認定試験改訂対策 #3]({{ site.baseurl }}{% post_url 2015-02-19-keyword-arguments-taking-steps-to-the-revised-certified-ruby-programmer-exam-3 %})
* [Ruby Association Certified Ruby Programmer Silver version 2.1]({{ site.baseurl }}{% post_url 2015-02-03-ruby-association-certified-ruby-programmer-silver-version-2-1 %})

[Ruby 技術者認定試験制度]: http://www.ruby.or.jp/ja/certification/examination/
{:target="_blank"}
[Ruby 技術者認定試験改訂のお知らせ]: http://www.ruby.or.jp/ja/certification/examination/index.data/rubycert.pdf
{:target="_blank"}
[Rubyで使われる記号の意味（正規表現の複雑な記号は除く） - Ruby 2.1.0 リファレンスマニュアル]: http://docs.ruby-lang.org/ja/2.1.0/doc/symref.html
{:target="_blank"}
