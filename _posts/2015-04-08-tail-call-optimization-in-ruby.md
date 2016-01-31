---
layout: post
title: "Ruby で末尾呼び出し最適化する方法"
categories: [技術, Ruby]
featured_image: shutterstock_248969473
---
Ruby で RubyVM のオプション設定を変更して評価することで末尾呼び出し最適化する方法を説明します。本記事は処理系依存のため YARV が搭載された Ruby 処理系のみに対応しています。

Ruby で末尾呼び出し最適化することについて知りたい人に、末尾呼び出し最適化について説明する必要はないと思いますので、末尾再帰になっている階乗のコードを最初から例示します。

{% highlight ruby %}
def factorial(n, acc = 1)
  if n == 0
    acc
  else
    factorial(n - 1, acc * n)
  end
end
{% endhighlight %}

標準の状態では末尾呼び出し最適化されないので n = 10000 で実行すると SystemStackError: stack level too deep で停止します。

末尾呼び出し最適化するためには、まず RubyVM のオプション設定を変更する必要が有ります。

{% highlight ruby %}
RubyVM::InstructionSequence.compile_option = {
  tailcall_optimization: true,
  trace_instruction: false
}
{% endhighlight %}

次にオプション設定を変更した RubyVM でコンパイルして評価することで末尾呼び出し最適化されたメソッドとして実行できます。

{% highlight ruby %}
RubyVM::InstructionSequence.compile(<<EOS).eval

def factorial(n, acc = 1)
  if n == 0
    acc
  else
    factorial(n - 1, acc * n)
  end
end

EOS
{% endhighlight %}

この状態では末尾呼び出し最適化されているので n = 10000 で実行しても SystemStackError が発生しません。

--------------------------------------------------------------------------------

今回は Ruby で末尾呼び出し最適化する方法について説明しました。関数プログラミングを Ruby で試してみる場合などで役に立つと思います。

参考文献
--------

* [Tail Call Optimization in Ruby - Nithin Bekal]

[Tail Call Optimization in Ruby - Nithin Bekal]: http://nithinbekal.com/posts/ruby-tco/
{:target="_blank"}
