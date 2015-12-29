---
layout: post
title: "新しい Mac の設定ログ"
categories: メモ
---
[新しい Mac を英語環境で設定する方法]の続きになる記事です。個人的な設定ログなのでご参考までにどうぞ。

System Preferences
------------------

System Preferences を起動して設定を進めます。

### Spotlight

Spotlight をクリックし、Finder search window keyboard shortcut のチェックを外します。Spotlight search keyboard shortcut のキーを ⌥ + ⌘ + Space に変更します。日本語環境のデフォルトは ⌃ + Space ですが、開発環境のショートカットキーと被りやすいので別のショートカットキーにしています。

### Energy Saver

Energy Saver をクリックし、Power Adapter タブを選択し、Computer sleep を Never に設定します。さらに Prevent computer from sleeping automatically when the display is off をチェックします。

### Trackpad

Trackpad をクリックし、More Gestures タブを選択し、App Exposé をチェックします。

### Sharing

Sharing をクリックし、Computer Name を変更します。

### Users and Groups

Users and Groups をクリックし、ユーザーアカウントの写真を変更します。また Guest User を選択し Allow guests to log in to this computer のチェックを外します。

iTunes
------

iTunes のライブラリを移動します。古い Mac の iTunes Media ディレクトリを新しい Mac の iTunes ディレクトリ内に上書き保存します。iTunes を起動し、Scan Media をクリックします。

Terminal
--------

Preferences で Profiles タブを選択します。Pro を選択し Default をクリックします。Font を Osaka-Mono 14 pt. に変更します。

Adobe Creative Suite 6
----------------------

Adobe Creative Suite 6 をインストールします。先に古い Mac のライセンス認証を解除します。その後、インストールメディアから普通にインストールします。

英語環境の OS X で Adobe Illustrator を正常に起動するためには Terminal で下記のコマンドを実行する必要があります。

{% highlight bash %}
$ defaults write com.adobe.illustrator AppleLanguages "(ja)"
{% endhighlight %}

Adobe Illustrator を起動すると Java SE 6 が必要というダイアログが表示されます。More Info をクリックして表示されるダウンロードページからダウンロードしてインストールする必要があります。

Adobe 製品を起動後、Adobe 製品をアップデートするようにします。

Homebrew & Cask
---------------

Homebrew をパッケージマネージャーとしてインストールします。Terminal を起動しコマンドを入力します。

{% highlight bash %}
$ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
{% endhighlight %}

Command Line Tools が必要だと表示されるのでインストールします。その後、Homebrew のインストール作業が進みます。完了後にコマンドを入力して正常にインストールされたことを確認します。

{% highlight bash %}
$ brew doctor
{% endhighlight %}

Homebrew Cask を GUI アプリケーションのパッケージマネージャーとしてインストールします。

{% highlight bash %}
$ brew install caskroom/cask/brew-cask
{% endhighlight %}

Dropbox
-------

Dropbox をインストールします。

{% highlight bash %}
$ brew cask install dropbox
{% endhighlight %}

Google Chrome
-------------

Google Chrome をインストールします。

{% highlight bash %}
$ brew cask install google-chrome
{% endhighlight %}

Google Drive
------------

Google Drive をインストールします。

{% highlight bash %}
$ brew cask install google-drive
{% endhighlight %}

Dock
----

Dock に表示されているアプリケーションを使用するものだけにします。

* Finder
* Mail
* Chrome
* Calendar
* iTunes
* Terminal

--------------------------------------------------------------------------------

個人的な設定ログを記事にまとめました。OS X をデフォルト状態で使用することが多いのでほとんどの設定は変更していません。新しい Mac を購入しても設定が楽なのでおすすめです。

関連記事
--------

* [新しい Mac を英語環境で設定する方法]
* [Homebrew で OS X のコマンドラインツールを管理する方法]

[新しい Mac を英語環境で設定する方法]: {{ site.baseurl }}{% post_url 2015-03-21-setup-new-mac-as-english-environment %}
[Homebrew で OS X のコマンドラインツールを管理する方法]: {{ site.baseurl }}{% post_url 2015-01-30-how-to-manage-os-x-packages-by-the-homebrew %}
