---
layout: post
title: "ショートカットメニューに「ターミナルで開く」を追加する方法"
categories: メモ
---
Finder で選択したフォルダのショートカットメニューに Automator と AppleScript を用いて「ターミナルで開く」という項目を追加する方法を説明します。

Automator を起動します。Automator の書類の種類としてサービスを選択してください。

[![Automator の書類の種類でサービスを選択]({{ site.baseurl }}/assets/mavericks-automator-service.png){:width="380" height="256"}]({{ site.baseurl }}/assets/mavericks-automator-service.png)

受け取る選択項目をフォルダに、検索対象を Finder にしてください。

[![サービスの設定]({{ site.baseurl }}/assets/mavericks-automator-service-setting.png){:width="380" height="256"}]({{ site.baseurl }}/assets/mavericks-automator-service-setting.png)

左側のライブラリの Run AppleScript アクションを右側のワークフロー領域にドラッグしてください。「AppleScript を実行」というアクションが追加されます。

[![Run AppleScript アクションの追加]({{ site.baseurl }}/assets/mavericks-automator-service-run-applescript-action.png){:width="380" height="256"}]({{ site.baseurl }}/assets/mavericks-automator-service-run-applescript-action.png)

下記の AppleScript を「AppleScript を実行」というアクションのテキストエリアに入力してください。入力したあとにコンパイルボタン（ハンマーのアイコンのボタン）をクリックすると AppleScript の構文が検証されたのちに綺麗に整形されます。

{% gist omoshetech-t/c06c2772c17e27b33c7f %}

[![AppleScript の入力]({{ site.baseurl }}/assets/mavericks-automator-applescript.png){:width="380" height="256"}]({{ site.baseurl }}/assets/mavericks-automator-applescript.png)

AppleScript の動作について説明します。まず input にはフォルダへのパスが入っています。最初に command に cd とフォルダへのパスを連結したコマンドを設定します。input に入っているパスはコロン区切りなので cd で受け付けることのできるスラッシュ区切りに POSIX path で変換しています。つぎに、ターミナル (Terminal) に命令し、ターミナルが起動していたら、新しいウィンドウが立ち上がって Finder で選択したフォルダに移動します。ターミナルが起動していなかったら、ターミナルが起動し、新しいウィンドウが立ち上がって Finder で選択したフォルダに移動します。後者の場合、ターミナルの起動時に立ち上がるウィンドウ window 1 でコマンドを実行するように指定することでウィンドウが2つ立ち上がってしまうことを防いでいます。

このサービスを「ターミナルで開く」という名前で保存します。

[![サービスを「ターミナルで開く」として保存]({{ site.baseurl }}/assets/mavericks-automator-service-saving.png){:width="380" height="256"}]({{ site.baseurl }}/assets/mavericks-automator-service-saving.png)

Finder で選択したフォルダのショートカットメニューに「ターミナルで開く」が追加されます。

[![「デスクトップ」フォルダのショートカットメニュー]({{ site.baseurl }}/assets/mavericks-finder-contextual-menu-open-with-terminal.png){:width="264" height="447"}]({{ site.baseurl }}/assets/mavericks-finder-contextual-menu-open-with-terminal.png)

実際に「デスクトップ」フォルダを「ターミナルで開く」と下記のようなターミナルが起動します。

[![「デスクトップ」フォルダを「ターミナルで開く」すると起動するターミナル]({{ site.baseurl }}/assets/mavericks-terminal-open-with-terminal.png){:width="380" height="253"}]({{ site.baseurl }}/assets/mavericks-terminal-open-with-terminal.png)

ショートカットメニューに「ターミナルで開く」を追加する方法について説明しました。同様の方法でショートカットメニューに色々なサービスを追加することができます。別のサービスの追加にも挑戦してみてください。
