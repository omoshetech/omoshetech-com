---
layout: post
title: "Gist を Google Sites に埋め込む方法"
categories: [技術, メモ]
featured_image: shutterstock_83090794
---
Gist を Google Sites に Google Gadgets を使って埋め込む方法を説明します。

1. Google Sites のページの編集で Insert > More gadgets... をクリックする。
2. Add gadget by URL をクリックする。
3. URL に https://gist.githubusercontent.com/omoshetech-t/10683373/raw/ を入力し Add をクリックする。
4. 埋め込みたい Gist の ID を入力し OK をクリックする。

次の設定で Gist を埋め込むと下記のように表示されます。

* Gist ID: 10683373
* Font size (px): 12
* Line height (px): 16
* Width: 100 percent
* Height: 520 pixels
* Include a scrollbar on gadget when necessary: Yes
* Include a border around gadget: No
* Display title on gadget: No

{% gist omoshetech-t/10683373 %}

[gist-gadget.xml] をカスタマイズしたい場合は Gist でフォークして編集することをおすすめします。

[gist-gadget.xml]: https://gist.github.com/omoshetech-t/10683373
{:target="_blank"}
