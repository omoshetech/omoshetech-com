---
layout: post
title: "リテラル - Ruby 技術者認定試験改訂対策 #2"
categories: Ruby
---
[Ruby 技術者認定試験制度]の改訂により Ruby のバージョンが 1.8 から 2.1 になったので、その変更点を試験対策の観点で [Ruby 技術者認定試験改訂のお知らせ]を参考にしつつまとめていきます。第2回はリテラルについてです。

概要
----

Ruby 1.9 でハッシュリテラルに変更がありました。また、Ruby 2.1 で有理数リテラルと複素数リテラルが追加になりました。

混乱するようなリテラルの変更ではないので自然に覚えられると思います。

ハッシュ
--------

Ruby 1.9 で下記のような新しい表記のハッシュリテラルが追加されました。この表現は普段から目にすることも多いので知っている人がほとんどだと思います。

{% highlight ruby %}
{ a: 1, b: 2, c: 3 } # => {:a=>1, :b=>2, :c=>3}
{% endhighlight %}

シンボルをキーとするハッシュが簡単に書けるようになりました。

逆に下記のような書き方はできなくなりました。

{% highlight ruby %}
{ :a, 1, :b, 2, :c, 3 } # => SyntaxError
{% endhighlight %}

有理数
------

Ruby 2.1 で下記のような有理数リテラルが追加されました。Rational クラスのインスタンスが生成されます。

{% highlight ruby %}
1r # => (1/1)
1 / 2r # => (1/2)
1r.class # => Rational
{% endhighlight %}

接尾辞として r を付与した数値が有理数リテラルになります。

複素数
------

Ruby 2.1 で下記のような複素数リテラルが追加されました。Complex クラスのインスタンスが生成されます。

{% highlight ruby %}
1i # => (0+1i)
1 + 2i # => (1+2i)
1i.class # => Complex
{% endhighlight %}

接尾辞として i を付与した数値が複素数リテラルになります。

虚数部が有理数の複素数
----------------------

Ruby 2.1 で虚数部が有理数の複素数を表現するためのリテラルも追加されました。Complex クラスのインスタンスが生成されます。

{% highlight ruby %}
1ri # => (0+(2/1)*i)
1ri.class # => Complex
{% endhighlight %}

接尾辞として ri を付与した数値が虚数部が有理数の複素数を表現するためのリテラルになります。r と i の順番が逆だと SyntaxError になるので注意してください。

--------------------------------------------------------------------------------

Ruby 1.9 と Ruby 2.1 で追加・変更があったリテラルについて説明しました。抵抗なく自然に理解できる追加・変更だと思います。

次回はキーワード引数について説明します。

参考文献
--------

* [Ruby 技術者認定試験制度]
* [Ruby 技術者認定試験改訂のお知らせ]
* [リテラル - Ruby 2.1.0 リファレンスマニュアル]
* [NEWS for Ruby 2.1.0 - Documentation for Ruby 2.1.0]
* [NEWS for Ruby 1.9.1 - Documentation for Ruby 2.1.0]

関連記事
--------

* [多言語化 - Ruby 技術者認定試験改訂対策 #1]
* [キーワード引数 - Ruby 技術者認定試験改訂対策 #3]
* [Ruby Association Certified Ruby Programmer Silver version 2.1]

[多言語化 - Ruby 技術者認定試験改訂対策 #1]: {{ site.baseurl }}{% post_url 2015-02-07-m17n-taking-steps-to-the-revised-certified-ruby-programmer-exam-1 %}
[キーワード引数 - Ruby 技術者認定試験改訂対策 #3]: {{ site.baseurl }}{% post_url 2015-02-19-keyword-arguments-taking-steps-to-the-revised-certified-ruby-programmer-exam-3 %}
[Ruby Association Certified Ruby Programmer Silver version 2.1]: {{ site.baseurl }}{% post_url 2015-02-03-ruby-association-certified-ruby-programmer-silver-version-2-1 %}

[Ruby 技術者認定試験制度]: http://www.ruby.or.jp/ja/certification/examination/
{:target="_blank"}
[Ruby 技術者認定試験改訂のお知らせ]: http://www.ruby.or.jp/ja/certification/examination/index.data/rubycert.pdf
{:target="_blank"}
[リテラル - Ruby 2.1.0 リファレンスマニュアル]: http://docs.ruby-lang.org/ja/2.1.0/doc/spec=2fliteral.html
{:target="_blank"}
[NEWS for Ruby 2.1.0 - Documentation for Ruby 2.1.0]: http://docs.ruby-lang.org/en/2.1.0/NEWS.html
{:target="_blank"}
[NEWS for Ruby 1.9.1 - Documentation for Ruby 2.1.0]: http://docs.ruby-lang.org/en/2.1.0/NEWS-1_9_1.html
{:target="_blank"}
