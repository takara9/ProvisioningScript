Provisioning Script
==================

Provisioning Script / Post Install Script は、SoftLayer の仮想サーバーや
物理サーバーを起動する際に、初回起動時の一回だけ実行されるスクリプトです。

SoftLayerカスタマーポータルへの登録方法など詳しい使い方は、以下の
URLにあります。

1.2.2 設定スクリプトの自動実行
https://www.change-makers.jp/post/10294


##centos_basic_config##

CentOS 5,6,7 用のプロビジョニング・スクリプトで、下記の自動実行をおこないます。
* パスワードでのログイン禁止、SSH鍵が必須になります。
* 日本語サポートのインストール
* 日本語化
* タイムゾーンをJST (Japan Standard Time)に変更
* iptables の設定 インターネット側からのアクセス禁止
* ツール類のパッケージインストール
* SoftLayerのDNSサーバーを追加 (ローカル参照)

##ubuntu_basic_config##

Ubunte 13.04,14.04 用のプロビジョニング・スクリプトです。自動設定内容は上記と同じです。



##ubuntu_chef_config

プロビジョニング時にCHEFを利用してWordpressをインストールするスクリプトです。対象となるOSは、Ubuntu-14.04 です。

* パスワードでのログイン禁止、SSH鍵が必須になります。
* 日本語サポートのインストール
* 日本語化
* タイムゾーンをJST (Japan Standard Time)に変更
* ufwの設定 インターネット側からのアクセス禁止
* ツール類のパッケージインストール
* SoftLayerのDNSサーバーを追加 (ローカル参照)
* CHEF ver 12.5 のインストール
* クックブックをダウンロード https://github.com/takara9/wordpress01
* Nginx, FastCGI(fpm)のインストールと設定
* MySQLサーバーの設定
* Wordpressのインストール

サーバーが起動した後、ログインした後でも、本スクリプトが実行中の場合があります。
このため、ps コマンドなどで、スクリプトの終了を確認するなどして、Wordpressの設定を開始します。

CHEFのクックブックは、https://github.com/takara9/wordpress01 にありますので、そちらも参照すると、設定内容を知る事ができます。


#### Wordpressの設定

インターネットVPNを確立してしておき、以下のアドレスをアクセスします。

    http://プライベートIPアドレス/wordpress/
    または
    http://プライベートIPアドレス/wordpress/wp-admin/install.php

ブラウザ画面のガイドに従って、項目をインプットすることで、利用を開始できます。


#### インターネットへの公開

このスクリプトは、最初、インターネットからのアクセスを禁止しています。
インターネットに公開するには、以下のコマンドで HTTPプロトコルの接続を許可することで可能になります。

HTTPプロトコルの許可

```
# ufw allow http
Rule added
Rule added (v6)
```
ファイアウォールの状態確認

```
# ufw status
Status: active

To                         Action      From
--                         ------      ----
Anywhere                   ALLOW       10.0.0.0/8
80                         ALLOW       Anywhere
80 (v6)                    ALLOW       Anywhere (v6)
```

参考資料
- https://wpdocs.osdn.jp/Nginx
