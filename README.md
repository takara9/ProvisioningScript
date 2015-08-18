ProvisioningScript
==================

Provisioning Script は、SoftLayer の仮想サーバーや物理サーバーを
起動する際に、初回起動時の一回だけ実行されるスクリプトです。

SoftLayerカスタマーポータルへの登録方法など詳しい使い方は、以下の
URLにあります。

1.2.2 設定スクリプトの自動実行
http://www.gg-web.jp/document/ConfigGuide/01002_2/index.html


##centos_basic_config##

CentOS 5,6,7 用のプロビジョニング・スクリプトで、下記の自動実行をおこないます。
* パスワードでのログイン禁止、SSH鍵が必須になります。
* 日本語サポートのインストール
* 日本語化
* タイムゾーンをJST (Japan Standard Time)に変更
* iptables の設定 インターネット側からのアクセス禁止
* ツールのインストール


##ubuntu_basic_config##

Ubunte 13.04,14.04 用のプロビジョニング・スクリプトです。自動設定内容は上記と同じです。


