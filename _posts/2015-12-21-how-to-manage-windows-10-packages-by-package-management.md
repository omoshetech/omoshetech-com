---
layout: post
title: "PackageManagement で Windows 10 のアプリケーションを管理する方法"
categories: メモ
---
Windows 10 から標準搭載されている PowerShell 5.0 の PackageManagement モジュールというパッケージマネージャーについて解説します。このパッケージマネージャーに [Chocolatey] をパッケージプロバイダーとして追加してアプリケーションをインストールします。

初期設定
--------

Windows 10 で PowerShell を管理者権限で起動します。スタートメニューの「すべてのアプリ」の Windows PowerShell を右クリックして「その他」の「管理者として実行」をクリックしてください。スタートメニューの「Cortana に何か聞いてみてください。」に powershell と入力して Windows PowerShell が選択されたら Ctrl + Shift + Enter で起動してください。

Windows PowerShell が管理者権限で起動します。最初に下記のコマンドでパッケージプロバイダーを一覧してみます。NuGet がインストールされていないというメッセージが出るので Enter を入力してインストールしておきます。

{% highlight powershell %}
> Find-PackageProvider
{% endhighlight %}

下記のコマンドで Chocolatey をパッケージプロバイダーとして追加します。

{% highlight powershell %}
> Get-PackageProvider chocolatey
{% endhighlight %}

基本的な使い方
--------------

この手順だけ知っていれば PackageManagement モジュールを使い始められます。

### パッケージの検索

下記のコマンドで Google Chrome ブラウザを検索してみます。

{% highlight powershell %}
> Find-Package chrome
{% endhighlight %}

いくつかパッケージが表示されます。Name の列にあるパッケージ名を使用してパッケージをインストールすることができます。今回は GoogleChrome というパッケージをインストールします。

### パッケージのインストール

現在の PackageManagement モジュールで Chocolatey のパッケージをインストールする場合は実行ポリシー (Execution Policy) の変更が必要です。パッケージをインストールするコマンドを実行する前に実行ポリシーを一時的に変更します。下記のコマンドを実行してください。

{% highlight powershell %}
> Set-ExecutionPolicy RemoteSigned Process
{% endhighlight %}

実行ポリシーを変更したのち、下記のコマンドで Google Chrome ブラウザをインストールします。

{% highlight powershell %}
> Install-Package GoogleChrome
{% endhighlight %}

--------------------------------------------------------------------------------

Windows 10 から標準搭載されているパッケージマネージャーについて解説しました。アプリケーションを PowerShell から管理できるのは便利なのでぜひ利用してみてください。

参考文献
--------

* [Chocolatey]
* [about_Execution_Policies - TechNet]
* [about_PackageManagement - TechNet]

[Chocolatey]: https://chocolatey.org
[about_Execution_Policies - TechNet]: https://technet.microsoft.com/en-us/library/hh847748.aspx
[about_PackageManagement - TechNet]: https://technet.microsoft.com/en-us/library/dn927162.aspx
