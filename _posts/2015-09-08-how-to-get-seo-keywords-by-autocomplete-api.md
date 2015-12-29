---
layout: post
title: "Autocomplete API で SEO キーワードを取得する方法"
categories: メモ
---
Google 検索が提供している Autocomplete の機能を利用できる非公式 API を利用して SEO キーワードの一覧を取得する方法について説明します。

注意事項
--------

Autocomplete API はアクセス制限することがすでに案内されていますのでご注意ください。

[Update on the Autocomplete API - Official Google Webmaster Central Blog]

仕様
----

Autocomplete API を利用して SEO キーワードの一覧を取得する方法は単純です。指定したキーワードに1文字を追加して Autocomplete API にリクエストすることで SEO キーワードの一覧を取得します。1文字はアルファベットの「a」から「z」までとカタカナの「ァ」から「ヶ」までを利用します。例えば、キーワードが「ruby」の場合は「ruby a」「ruby b」…「ruby ァ」「ruby ア」「ruby ィ」「ruby イ」…「ruby ン」「ruby ヴ」「ruby ヵ」「ruby ヶ」をリクエストします。

Autocomplete API
----------------

Autocomplete API のホストは suggestqueries.google.com です。下記の API を提供しています。

### GET /complete/search

|パラメーター|必須|説明                                                                                 |
|------------|----|-------------------------------------------------------------------------------------|
|q           |◯  |キーワード文字列を指定します。                                                       |
|client      |◯  |レスポンスのフォーマット (firefox: JSON, toolbar: XML, youtube: JSONP) を指定します。|
|jsonp       |-   |JSONP のコールバック関数を指定します。デフォルト値は window.google.ac.h です。       |
|hl          |-   |言語を ISO 639-1 コードで指定します。デフォルト値は en です。                        |

SEO キーワード取得スクリプト
----------------------------

SEO キーワード取得スクリプトを Ruby で実装しました。

{% gist omoshetech-t/e6d8a25e4667e46af251 %}

下記のようにターミナルから実行してください。

{% highlight bash %}
$ ruby seo_keywords.rb ruby on rails
{% endhighlight %}

この例は「ruby on rails」のキーワードについて SEO キーワードの一覧を取得して表示します。

--------------------------------------------------------------------------------

今回は Autocomplete API で SEO キーワードを取得する方法について説明しました。僕も Google 検索でオートコンプリートの候補を選ぶことがよくあるので SEO キーワードの一覧としてこの方法は有用なのではないかと思います。

参考文献
--------

* [Content SEO - Yoast]
* [Google Autocomplete "API" - Shreyas Chand]

[Update on the Autocomplete API - Official Google Webmaster Central Blog]: http://googlewebmastercentral.blogspot.jp/2015/07/update-on-autocomplete-api.html
{:target="_blank"}
[Content SEO - Yoast]: https://yoast.com/ebooks/content-seo/
{:target="_blank"}
[Google Autocomplete "API" - Shreyas Chand]: http://shreyaschand.com/blog/2013/01/03/google-autocomplete-api/
{:target="_blank"}
