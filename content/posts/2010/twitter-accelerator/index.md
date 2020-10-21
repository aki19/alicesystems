---
title: Twitter投稿アクセラレータつくりました
date: 2010-02-03T06:46:13+00:00
categories:
  - 自作
  - 配布
tags:
  - アドオン
---
思っていたよりもずっと簡単だったので、暇つぶしに作ってみました。

Twitter投稿系はすでに数え切れないぐらい公開されているとは思いますが・・・

一応作り方とかもちょこっとメモしておきます。

・まずアクセラレータってなに？

[<img src="http://static.flickr.com/4025/4326570373_0109d95447_m.jpg" border="0" alt="アクセラレータ" />][1]

IE８の新機能です。

文字を選択すると青いアイコンが出てくると思うのですが、

それをクリックするとサブメニューみたいなのがでてきて

選択した文字を元に、いろんなサービスと連携して色々してくれる機能。

例えば選択文字を翻訳してその場で表示したり・・・

文字を選択しなくても有効なアクセラレータもあります。

・Twitter投稿アクセラレータって？

表示中のページのタイトルとURLを引用してTwitterの投稿画面を表示する機能をもっています。

実行＝投稿、も可能だったのですが何か一言書けたほうがいいかなと思い、投稿画面まで飛ぶようにしました。

例えばこのページを表示中に実行すると、下図の状態で投稿画面が開きます。

[<img src="http://static.flickr.com/4068/4327317698_be6a45ea17.jpg" border="0" alt="投稿画面" />][2]

たぶんこういう機能をもったブックマークレット、わんさかあると思います（汗）

・どうやって作ったの？

XMLファイルひとつ作ればできます。

例えば今回作ったアクセラレータだとコードは以下のようになります。

[sourcecode language=&#8221;xml&#8221;]  
<?xml version="1.0" encoding="UTF-8"?>  
<os:openServiceDescription  
xmlns:os="http://www.microsoft.com/schemas/openservicedescription/1.0">  
<os:homepageUrl>http://twitter.com/</os:homepageUrl>  
<os:display>  
<os:name>Post to Twitter</os:name>  
<os:icon>https://www.example.com/sample.ico</os:icon>  
<os:description>The title and URL on the page are contributed to the Twitter.</os:description>  
</os:display>  
<os:activity category="ブログ">  
<os:activityAction context="document">  
<os:execute action="http://twitter.com/home">  
<os:parameter name="status" value="Check! →「{documentTitle}」{documentUrl}" type="text" />  
</os:execute>  
</os:activityAction>  
</os:activity>  
</os:openServiceDescription>  
[/sourcecode]

os:homepageUrlには利用するサービスのメインURLを記述します。  
os:executeで記述するURLと同じドメインでなければだめです。  
os:display要素は右クリックメニューに表示される（アクセラレータの管理画面でも表示される）  
内容です。  
機能はos:activityに記述します。  
category属性にはアクセラレータのグループ名を適当に。  
os:activityActionにサービスへの命令を記述します。  
context属性は今回documentにしているので、常に実行可能であることを示します。  
他、selectionは選択テキストがある場合、linkはハイパーリンク上、などが指定できます。  
os:executeは実行されるアクション。  
サービスに対して、パラメータを渡しています。  
value属性内の{}で囲まれた部分は変数です。  
ドキュメントのドメインとかいつかの変数が使えます。  
・・・こんな感じで作成したXMLファイルを用意して、インストールできるようにします。  
コードは以下の通り。

[sourcecode]  
<button onclick="window.external.addService(&#8216;https://www.example.com/sample.xml&#8217;)" type="submit">アクセラレータのインストール</button>  
[/sourcecode]

・使ってみる

ありがとうございます。

IE８で[リンク先][3]のボタンをクリックしてインストールしてください。

すみませんが、勉強用に作ったものなので自己責任でお願いします。

何か問題あればコメントなどで教えてください。

・参考にしたサイト  
[OpenService アクセラレータ開発者向けガイド][4]  
[IE8の新機能「アクセラレータ」の作り方][5]

※IE８をそもそもまったく使っていないので、この機能今日知りました（笑）

 [1]: http://www.flickr.com/photos/41082249@N07/4326570373/ "アクセラレータ"
 [2]: http://www.flickr.com/photos/41082249@N07/4327317698/ "投稿画面"
 [3]: http://www.asahi-net.or.jp/~vx7a-oogk/develop/TwitterQuickPost.htm
 [4]: http://msdn.microsoft.com/ja-jp/library/cc287851(VS.85).aspx
 [5]: http://www.okoshi.org/tadashi/optimism/2009/03/21/ie8_10.html
