---
layout: post
title: "新しい Mac を英語環境で設定する方法"
categories: メモ
---
新しい Mac を最小構成の英語環境で設定する方法について説明します。システムの言語は英語になりますが日本語の表示と日本語入力ができるように設定します。個人的な備忘録を兼ねているので個人的な好みの設定も含まれています。

OS X の最小構成インストール
---------------------------

購入直後の Mac には iPhoto・iMovie・GarageBand・Pages・Numbers・Keynote がインストールされています。OS X を再インストールすることでそれらがインストールされてない状態で開始できます。

キーボードの ⌘ + R を押しながら Mac を起動します。OS X Utilities が立ち上がります。

Disk Utility を選択して Continue をクリックします。Macintosh HD を選択して Erase タブに移動して Erase をクリックして OS X を削除します。Disk Utility を終了します。

Reinstall OS X を選択して Continue をクリックします。指示どおりに進めてインストールを完了させます。インターネット経由で OS X をダウンロードするので時間がかかります。

OS X の初期設定
---------------

OS X のインストールが完了すると再起動して Welcome 画面が表示されます。まずは Japan を選びましょう。次に Select Your Keyboard で US キーボードであれば U.S. を、JIS キーボードであれば Japanese を選択します。

これ以降は各自の好みで設定してください。Select Your Wi-Fi Network で Wi-Fi に接続します。Transfer Information to This Mac で Don't transfer any information now を選択します。Sign in with Your Apple ID で Apple ID を入力します。Allow iCloud to use the location of this Mac for Find My Mac? と聞かれるので Allow を選択します。Terms and Conditions で Agree を選択します。Create a Computer Account で Use my iCloud account to log in をチェックし、アイコンと Account name を入力し、Set time zone based on current location をチェックします。iCloud Keychain で Set up iCloud Keychain を選択し、Approve from another device を選択します。

これで初期設定は完了です。

Software Update
---------------

起動直後に位置情報を使っていいかなどの承認が求められますがそれを承認します。その後、App Store を起動して Updates タブから Software Update を確認します。Software Update があるようであれば UPDATE ALL をクリックしてください。

日本語環境
----------

日本語フォントで日本語が表示され、日本語入力ができるように環境を設定します。

System Preferences を起動します。

Language & Region をクリックし、左下の + ボタンをクリックして、日本語を追加します。Primary Language のダイアログが表示されるので Use English をクリックします。Input Source のダイアログが表示されるので Add Input Source をクリックします。

Keyboard をクリックし、Shortcuts タブを選択します。

Input Sources を選択し Select the previous input source をチェックします。日本語環境でデフォルトの ⌘ + Space を割り当てます。また、Spotlight が英語環境だと ⌘ + Space がデフォルトなので、日本語環境でデフォルトの ⌃ + Space に割り当て直します。

次に Input Sources タブを選択します。U.S. の選択し - ボタンをクリックして削除します。Japanese を選択し Input modes から Katakana のチェックを外します。これは各自の好みで設定してください。

--------------------------------------------------------------------------------

新しい Mac を最小構成の英語環境で設定する方法を説明しました。新しい Mac を英語環境でセットアップするのは年に1回くらいなので内容を忘れがちです。英語環境で日本語を使えるようにするための設定は多いので備忘録も兼ねて書きました。参考になれば幸いです。

関連記事
--------

* [新しい Mac の設定ログ]

[新しい Mac の設定ログ]: {{ site.baseurl }}{% post_url 2015-04-01-new-mac-setup-log %}
