# ここのせつめい
Ruby on Rails開発環境の構築手順を解説します。  
Macでの開発を前提としています。
ここを参考にしてください。  
[Homebrew + rbenv + ruby-buildでruby 2.0.0-p0をインストール](http://qiita.com/s-yamaz@github/items/b38b330b44f517f3c77c)

## 全体的な手順
1. XCode Command Line Toolsをインストール
2. Homebrewをインストール
3. rbenvをインストール
4. ruby2.0.0-p247（最新版）をインストール
5. Rails4.0（最新版）をインストール


## 1. Xcode Command Line Toolsのインストール
Xcodeから入れる方法と単体で入れる方法があります。

### Xcodeから
Xcodeの「Preferences」→「Downloads」→「Command Line Tools」の「install」  
（Xcode立ち上げたら「コマンド+,」でPreferencesが立ち上がります。）

### 単体で
[Apple Developer Center](https://developer.apple.com/downloads/index.action) から  
「Command Line Tools (OS X Mountain Lion) for Xcode - April 2013」  
or  
「Command Line Tools (OS X Lion) for Xcode - April 2013」  
をダウンロードしてインストール。


## 2. Homebrewのインストール
以下のコマンドを打てば完了    

	$ ruby -e "$(curl -fsSL https://raw.github.com/mxcl/homebrew/go)"

rubyはMacに標準で入ってますが、バージョン古いので使いません。

## 3. rbenvのインストール
ruby本体のバージョン管理システム。  
常に最新のバージョンを追いかけ、作ったシステムを長い間メンテナンスするためにバージョン管理ソフトを導入して作業をしやすいようにする。  
oepnsslとreadlineというパッケージを入れなおさないと不具合が起こる可能性があるので一緒に導入します。  
Homebrewにて導入  

	$ brew install openssl  
	$ brew install readline  
	$ brew install rbenv  


## 4. ruby2.0.0-p247のインストール
### ruby-buidldのインストール
rbenvは単なるバージョン管理システムなので、rubyのインストール機能はありません。  
まずはruby-buildというものを使ってrbenvにインストール機能をつけます。  
インストールした後は.bashrcなどに ```eval "$(rbenv init -)"```というを追記します。  

	$ brew install --HEAD ruby-build
	$ echo 'eval "$(rbenv init -)"' >> ~/.bashrc
	$ source ~/.bashrc

### インストールできるか確認
つぎに、```2.0.0-p247```がインストールできるかどうか見ます。  
以下のコマンドを実行して```2.0.0-p247```が表示されていればOK。

	$ rbenv install -l

表示されない場合は以下を実行します。

	$ brew upgrade ruby-build

### 実際にインストール

	$ rbenv install 2.0.0-p247

標準で使うバージョンを```2.0.0-p247```に設定する。  

	$ rbenv global 2.0.0-p247

## 3. Rails4.0のインストール
最新版 rails 4.0.0 をインストールします。  
まずは4.0.0がインストールできるか確認する。最後に```$```を入れてください。

	$ gem list -r rails$

	*** REMOTE GEMS ***

	rails (4.0.0)

実際に入れます。
	
	$ gem install rails

rbenvのrehashというコマンドを使って有効化

	$ rbenv rehash

インストールできたか確認

	$ which rails
