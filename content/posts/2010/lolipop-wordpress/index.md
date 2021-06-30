---
title: ロリポップ！のWordPress簡単インストールでやったこと全部
date: 2010-12-07T16:43:59+00:00
categories:
  - ブログ
tags:
  - Tips
---
当ブログは先日、WordPress.comからロリポにお引越ししたわけですが、  
その際にやったこと、設定内容、などを全てメモしておこうと思います。

1.ロリポ登録  
・プランはロリポプランを選択。一番安いコロリポプランだとDB使えないので。  
2.サイト情報設定  
・支払情報とかその程度  
3.簡単インストールでWordPress選択  
・サイト名とかアカウントを決めて実行  
4.WordPressにログインすると更新できる、と言われたので更新作業  
・DBのエクスポート（Drop tabel込みで）  
・更新実行  
5.旧サイトの情報をエクスポート  
6.新サイトにインポート  
・これで記事は全部移行完了  
7.サイトの一般設定とかは移行できないので新たに設定  
・テーマは前回同様monochromeも利用。  
8.好きなプラグインをどんどん入れる！  
・プラグインを入れたら忘れずに有効化する。  
・使用中プラグインは以下の通り。

  * Akismet（AkismetAPIキーの取得も。）
  * Contact Form7（表示したい部分にコードをコピー。私の場合ページを追加してペースト。）
  * Google Analytics for WordPress（Analyticsに登録してコードを設定。）
  * Google Analytics Dashboard
  * Quick Flickr Widget（RSSの設定などはウィジェット画面から。）
  * Social Bookmarking JP（全部表示させるとちょっとしつこかったので一部非表示に。）
  * Wickett Twitter Widget（ユーザーの設定などはウィジェット画面から。）
  * WordPress Importer（旧ブログからのインポート操作のみに利用。）
  * WordPress Media Flickr（認証）
  * WP-SpamFree
  * WP Evernote Site Memory（ボタンの場所とかデザインとか。）
  * WP Multibyte Patch
  * WPtouch
  * SyntaxHighlighter
  * Yet Another Related Posts Plugin（後述）

YARPPは対応するバージョンがベータ版で、自動更新できなかったので直接更新しました。

FTP情報はCyberduckの場合以下を参照。  
<a href="http://lolipop.jp/manual/hp/m-cyberduck/" target="_blank">http://lolipop.jp/manual/hp/m-cyberduck/</a>

フォルダの更新（wp-content/plugins以下）と、使っているテーマフォルダ（今回はwp-content/themes/monochrome）以下にテンプレートファイル（yarpp-template-example.php）を追加。

テンプレートは、設定から利用する、とした場合のみ使われます。

普通に設定するとmonochromeテーマの場合、メインの一覧画面に表示されないので、表示されるようにテンプレートをカスタマイズします。  
テーマ編集からindex.phpのpost_contentクラスをもつdiv内の最後に以下の文字列を追加します。

<pre class="brush:php">&lt;?php related_posts(); ?&gt;</pre>

9.更新をTwitterに流す設定。私の場合は別サービス（FeedTweet）利用。

完成！  
後はウィジェットとかダッシュボードを並び替えたり・・・。  
プラグインはもっと細かくカスタムしても良いかもしれません。

まだ追加したいプラグインもあるので、もうしばらく色々いじることになりそうです。

ロリポップ、安いし簡単だしおすすめです。  
ドメイン決めるのに一番時間かかりました・・・。選択肢がいっぱいですよー。

<a href="https://lolipop.jp/" target="_blank">★ロリポップ！★WordPressやMovableTypeの簡単インストール、cron、共有SSL対応！</a>
