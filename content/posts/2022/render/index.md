---
title: "Herokuからrenderに移行（PHP Lumenを動かす）"
date: 2022-12-05T14:46:19+09:00
categories:
  - プログラミング
---

Herokuの無料プランが終了したので、移行先を検討しました。  
Herokuを使っていたプロジェクトはいくつかあったのですが、最終的に移行が必要なプロジェクトはひとつ。  
以下の構成でした。

言語：PHP 7.3  
フレームワーク：Lumen 7.2.1  
※外部サービスのAPIを呼んでいるので鍵が外で管理できること

ただの趣味プロジェクトなので、とにかく無料で運用したくて・・・  
結果、<a target="_blank" href="https://render.com/">render</a>に移行することに決めました。

renderはDockerが使えるので、これの上でPHPを動かします。  
移行のために修正した箇所はほとんどこのDocker対応だけでした。

Lumenを動かす手順としては公式に用意してある<a target="_blank" href="https://render.com/docs/deploy-php-laravel-docker">Laravelのガイド</a>でほぼ足ります。

自分のLumen用に？少しだけ修正したのでのせておきます。

①利用するコンテナの変更  
自分のバージョンの場合、「richarvey/nginx-php-fpm:1.6.0」を利用

②起動スクリプト（00-laravel-deploy.sh）の修正  
config:cache,route:cacheのコメントアウト  
migrateのコメントアウト（DBを使わないので）  
以下を追記（必要かどうかは不明）

```
composer dump-autoload -o --working-dir=/var/www/html
```

③render側の設定  
Web Serviceで作成  
APP_KEYやそのほか鍵情報をEnvironment Variablesで設定

以上で動きました。

ただ、他の方も指摘していたのですが502になることが多くて・・・  
本当に自分が使うだけのプロジェクトとかでないと利用は厳しいかもです。
