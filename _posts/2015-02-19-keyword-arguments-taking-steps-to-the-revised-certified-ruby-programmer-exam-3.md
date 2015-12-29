---
layout: post
title: "キーワード引数 - Ruby 技術者認定試験改訂対策 #3"
categories: Ruby
---
[Ruby 技術者認定試験制度]の改訂により Ruby のバージョンが 1.8 から 2.1 になったので、その変更点を試験対策の観点で [Ruby 技術者認定試験改訂のお知らせ]を参考にしつつまとめていきます。第3回はキーワード引数についてです。

概要
----

Ruby 2.0 でキーワード引数の機能が追加されました。また、Ruby 2.1 でデフォルト値のないキーワード引数が利用できるようになりました。

自然な改善だと思うので混乱する部分は多くないと思います。しかし、キーワード引数と可変長引数やブロック引数を一緒に利用するとなるとその順番が問題になるので、それについては記事の後半で解説します。

キーワード引数
--------------

下記のようにメソッドを定義することでキーワード引数が利用できます。

{% highlight ruby %}
def f(x:, y:, z:)
  x * y * z
end
{% endhighlight %}

このメソッドは下記のように呼び出します。なお、キーワード引数の場合は引数の順番は関係ありません。不足しているキーワード引数がある場合は ArgumentError が発生します。

{% highlight ruby %}
f(x: 1, y: 2, z: 3) # => 6
{% endhighlight %}

デフォルト式付きキーワード引数
------------------------------

下記のようにキーワード引数にはデフォルト式を指定できます。

{% highlight ruby %}
def f(x:, y: 2, z:)
  x * y * z
end
{% endhighlight %}

このメソッドを下記のように呼び出すことができます。デフォルト式付きキーワード引数は省略することができます。

{% highlight ruby %}
f(x: 1, z: 3) # => 6
{% endhighlight %}

オプションハッシュ
------------------

メソッドの引数として定義されていないキーワード引数が渡されると ArgumentError が発生します。ArgumentError を発生させたくない場合は下記のように ** 付きの引数を定義することでハッシュとして受け取ることができます。** 付きの引数はキーワード引数の定義より後に定義する必要があります。

{% highlight ruby %}
def f(x:, y:, z:, **kwargs)
  kwargs
end
f(a: 0, x: 1, y: 2, z: 3) # => {:a=>0}
{% endhighlight %}

ArgumentError の発生を抑制する意図であれば下記のように無名変数として定義も可能です。

{% highlight ruby %}
def f(x:, y:, z:, **)
  x * y * z
end
{% endhighlight %}

その他の引数との混在
--------------------

通常の引数・デフォルト式付き引数・可変長引数・ブロック引数などを混在させる場合は定義できる順番が決まっています。その順番は下記の通りです。

1. 通常の引数
2. デフォルト式付き引数
3. 可変長引数
4. 通常の引数
5. キーワード引数＆デフォルト式付きキーワード引数
6. オプションハッシュ
7. ブロック引数

すべての種類の引数を使用してメソッドを定義すると下記のようになります。

{% highlight ruby %}
def method(a, b = 1, *c, d, e:, f: 5, **g, &h)
  return a, b, c, d, e, f, g, h
end
method(0, 1, 2, 3, e: 4, f: 5, g: 6) { 7 }
# => [0, 1, [2], 3, 4, 5, {:g=>6}, #<Proc:0x007fab1118ec28@(irb):7>]
{% endhighlight %}

--------------------------------------------------------------------------------

Ruby 2.0 と Ruby 2.1 で追加・変更があったキーワード引数について説明しました。抵抗なく自然に理解できる追加・変更だと思います。キーワード引数とその他の引数を混在させるときの順番にだけ注意してください。

次回は新しいラムダ式について説明します。

参考文献
--------

* [Ruby 技術者認定試験制度]
* [Ruby 技術者認定試験改訂のお知らせ]
* [Ruby 2.0.0 のキーワード引数 - Rubyist Magazine]

関連記事

* [リテラル - Ruby 技術者認定試験改訂対策 #2]
* [新しいラムダ式 - Ruby 技術者認定試験改訂対策 #4]
* [Ruby Association Certified Ruby Programmer Silver version 2.1]

[リテラル - Ruby 技術者認定試験改訂対策 #2]: {{ site.baseurl }}{% post_url 2015-02-10-literal-taking-steps-to-the-revised-certified-ruby-programmer-exam-2 %}
[新しいラムダ式 - Ruby 技術者認定試験改訂対策 #4]: {{ site.baseurl }}{% post_url 2015-03-19-new-lambda-syntax-taking-steps-to-the-revised-certified-ruby-programmer-exam-4 %}
[Ruby Association Certified Ruby Programmer Silver version 2.1]: {{ site.baseurl }}{% post_url 2015-02-03-ruby-association-certified-ruby-programmer-silver-version-2-1 %}

[Ruby 技術者認定試験制度]: http://www.ruby.or.jp/ja/certification/examination/
{:target="_blank"}
[Ruby 技術者認定試験改訂のお知らせ]: http://www.ruby.or.jp/ja/certification/examination/index.data/rubycert.pdf
{:target="_blank"}
[Ruby 2.0.0 のキーワード引数 - Rubyist Magazine]: http://magazine.rubyist.net/?0041-200Special-kwarg
{:target="_blank"}
