---
layout: post
title: "多言語化 - Ruby 技術者認定試験改訂対策 #1"
categories: [技術, Ruby]
featured_image: photo-1415302199888-384f752645d0
---
[Ruby 技術者認定試験制度]の改訂により Ruby のバージョンが 1.8 から 2.1 になったので、その変更点を試験対策の観点で [Ruby 技術者認定試験改訂のお知らせ]を参考にしつつまとめていきます。第1回は多言語化についてです。

概要
----

Ruby 1.9 になったときに Ruby は多言語化されました。その詳細は [Rubyist Magazine - Ruby M17N の設計と実装][Ruby M17N の設計と実装 - Rubyist Magazine]に書かれています。

試験に関係ありそうな多言語化による変更は Encoding・String に存在します。なお、Encoding は Ruby 1.9 になって新しく追加されたクラスです。また、多言語化に伴いスクリプトエンコーディングの概念が追加されたので、スクリプトエンコーディングについても理解しておく必要があります。

それぞれの変更点について解説していきます。Ruby 2.0 と Ruby 2.1 での変更点も一緒にまとめています。

スクリプトエンコーディング
--------------------------

まずは Ruby のスクリプトを書いて実行するときに考えなければならないスクリプトエンコーディングについてです。Ruby 1.9 で導入された概念です。後述するように Ruby 2.0 でも重要な変更が追加されています。

Ruby 1.9 からファイルの先頭にマジックコメントを追加することでスクリプトエンコーディングを指定できます。スクリプトエンコーディングはファイルごとに指定することができるようになっています。下記の指定では Ruby はファイルを UTF-8 でエンコーディングされたものとして解釈します。

{% highlight ruby %}
# coding: utf-8
{% endhighlight %}

Ruby 1.9 では、マジックコメントがない場合のデフォルトスクリプトエンコーディングは US-ASCII です。しかし、Ruby 2.0 で UTF-8 に変更されました。試験では Ruby 2.1 を対象としているので、デフォルトスクリプトエンコーディングは UTF-8 になります。

Encoding クラス
---------------

文字エンコーディングのクラスです。多言語化に伴い追加されました。

Encoding クラスのインスタンスを文字列から取得することができます。

{% highlight ruby %}
p 'あ'.encoding # => #<Encoding:UTF-8>
{% endhighlight %}

例えば、マジックコメントがない、文字エンコーディングが UTF-8 のファイルで、文字エンコーディングを表す文字列を取得すると下記のようになります。

{% highlight ruby %}
p 'あ'.encoding.name # => "UTF-8"
{% endhighlight %}

また、マジックコメントがあり、文字エンコーディングが Shift_JIS のファイルで、文字エンコーディングを表す文字列を取得すると下記のようになります。

{% highlight ruby %}
# coding: Shift_JIS
p 'あ'.encoding.name # => "Shift_JIS"
{% endhighlight %}

文字列リテラルはスクリプトエンコーディングによって文字エンコーディングが決まります。ただし、文字列ごとに文字エンコーディングを持つため、文字エンコーディングの違う文字列を混在させることもできます。

{% highlight ruby %}
# coding: Shift_JIS
a = 'あ'
b = 'あ'.encode('UTF-8')
p a.encoding.name # => "Shift_JIS"
p b.encoding.name # => "UTF-8"
{% endhighlight %}

時間があれば、[Ruby 2.1.0 リファレンスマニュアル の Encoding クラス]を眺めるとより完璧だと思います。

String クラス
-------------

文字列のクラスです。多元化に伴い大きな変更があったクラスです。

Ruby 1.8 では文字列はバイト単位で扱われるので String#[] の結果は下記のようになりました。

{% highlight ruby %}
'abc'[0]    # => 97
'abc'[0..1] # => "ab"
{% endhighlight %}

しかし、Ruby 1.9 では文字列は文字単位で扱われるので String#[] の結果は下記のようになります。

{% highlight ruby %}
'abc'[0]    # => "a"
'abc'[0..1] # => "ab"
{% endhighlight %}

また、Ruby 1.8 では文字リテラルの結果は数値になりました。

{% highlight ruby %}
?a # => 97
{% endhighlight %}

しかし、Ruby 1.9 では文字リテラルの結果は1文字の文字列になります。

{% highlight ruby %}
?a # => "a"
{% endhighlight %}

Ruby 2.1 に含まれる Ruby 1.9.1 以降の NEWS ファイルを参照すると下記メソッドの追加／変更がありました。完全を期すのであればひとつひとつのメソッドのマニュアルを参照することをおすすめします。

* String#clear
* String#ord
* String#getbyte, String#setbyte
* String#chars, String#each_char
* String#codepoints, String#each_codepoint
* String#unpack
* String#hash
* String.try_convert
* String#encoding
* String#force_encoding, String#encode, String#encode!
* String#ascii_only?
* String#valid_encoding?
* String#match
* String#prepend
* String#byteslice
* String#b
* String#lines
* String#chars
* String#codepoints
* String#bytes
* String#scrub, String#scrub!

--------------------------------------------------------------------------------

Ruby 1.9 で導入された多言語化による変更点を駆け足で説明しました。多言語化自体は深いトピックですが試験対策という意味では深く追求する必要はないと思います。本記事で説明した「スクリプトエンコーディング」「Encoding クラス」「文字列がバイト単位ではなく文字単位」の3点を抑えて、irb でメソッドを試してみれば試験対策としては十分ではないでしょうか。

次回はリテラルについて説明します。

参考文献
--------

* [Ruby 技術者認定試験制度]
* [Ruby 技術者認定試験改訂のお知らせ]
* [Ruby M17N の設計と実装 - Rubyist Magazine]
* [Ruby 2.0.0 の注意点やその他の新機能 - Rubyist Magazine]
* [多言語化 - Ruby 2.1.0 リファレンスマニュアル]
* [ライブラリ一覧 > 組み込みライブラリ > Encoding クラス - Ruby 2.1.0 リファレンスマニュアル]
* [ライブラリ一覧 > 組み込みライブラリ > String クラス - Ruby 2.1.0 リファレンスマニュアル]
* [NEWS for Ruby 2.1.0 - Documentation for Ruby 2.1.0]
* [NEWS for Ruby 2.0.0 - Documentation for Ruby 2.1.0]
* [NEWS for Ruby 1.9.3 - Documentation for Ruby 2.1.0]
* [NEWS for Ruby 1.9.2 - Documentation for Ruby 2.1.0]
* [NEWS for Ruby 1.9.1 - Documentation for Ruby 2.1.0]

関連記事
--------

* [リテラル - Ruby 技術者認定試験改訂対策 #2]
* [Ruby Association Certified Ruby Programmer Silver version 2.1]

[リテラル - Ruby 技術者認定試験改訂対策 #2]: {{ site.baseurl }}{% post_url 2015-02-10-literal-taking-steps-to-the-revised-certified-ruby-programmer-exam-2 %}
[Ruby Association Certified Ruby Programmer Silver version 2.1]: {{ site.baseurl }}{% post_url 2015-02-03-ruby-association-certified-ruby-programmer-silver-version-2-1 %}

[Ruby 技術者認定試験制度]: http://www.ruby.or.jp/ja/certification/examination/
{:target="_blank"}
[Ruby 技術者認定試験改訂のお知らせ]: http://www.ruby.or.jp/ja/certification/examination/index.data/rubycert.pdf
{:target="_blank"}
[Ruby M17N の設計と実装 - Rubyist Magazine]: http://magazine.rubyist.net/?0025-Ruby19_m17n
{:target="_blank"}
[Ruby 2.0.0 の注意点やその他の新機能 - Rubyist Magazine]: http://magazine.rubyist.net/?0041-200Special-note
{:target="_blank"}
[多言語化 - Ruby 2.1.0 リファレンスマニュアル]: http://docs.ruby-lang.org/ja/2.1.0/doc/spec=2fm17n.html
{:target="_blank"}
[ライブラリ一覧 > 組み込みライブラリ > Encoding クラス - Ruby 2.1.0 リファレンスマニュアル]: http://docs.ruby-lang.org/ja/2.1.0/class/Encoding.html
{:target="_blank"}
[ライブラリ一覧 > 組み込みライブラリ > String クラス - Ruby 2.1.0 リファレンスマニュアル]: http://docs.ruby-lang.org/ja/2.1.0/class/String.html
{:target="_blank"}
[NEWS for Ruby 2.1.0 - Documentation for Ruby 2.1.0]: http://docs.ruby-lang.org/en/2.1.0/NEWS.html
{:target="_blank"}
[NEWS for Ruby 2.0.0 - Documentation for Ruby 2.1.0]: http://docs.ruby-lang.org/en/2.1.0/NEWS-2_0_0.html
{:target="_blank"}
[NEWS for Ruby 1.9.3 - Documentation for Ruby 2.1.0]: http://docs.ruby-lang.org/en/2.1.0/NEWS-1_9_3.html
{:target="_blank"}
[NEWS for Ruby 1.9.2 - Documentation for Ruby 2.1.0]: http://docs.ruby-lang.org/en/2.1.0/NEWS-1_9_2.html
{:target="_blank"}
[NEWS for Ruby 1.9.1 - Documentation for Ruby 2.1.0]: http://docs.ruby-lang.org/en/2.1.0/NEWS-1_9_1.html
{:target="_blank"}
