---
title: RSSReaderつくりました
date: 2009-11-15T17:14:06+00:00
categories:
  - プログラミング
  - 自作
tags:
  - AIR
---
[<img loading="lazy" src="http://farm3.static.flickr.com/2573/4107105753_9d7bd55b30.jpg" width="180" height="300" alt="rsschecker" />][1]

前回の日記の続きです。

AIRでRSSReaderつくりました。

じぶんのアホみたいなコードさらしてもしょうがないので、

つまったところをメモしておきます。

■XMLListCollectionをDataGridにむすびつける

サンプルをみると、DataGridコンポーネントにはArrayを使っているものがとても多かったので、

dataFieldにデータを表示させる方法がもう全然わからなかったのですが、

labelFunctionに指定した関数で、

item.descendants( column.dataField );　// itemはデータのXML

をするとうまく表示できました。

詳しい理解はまだしてません・・・。

■フィードに＆とかがあるとき

RSSのフィードが＆でオプションをつなげているような形のURLだったのですが、

サンプルとかを参考に作ると、「区切り文字が・・・」と文句を言われる。

＆が問題だったようなのですが・・・

結論から言うと、URLRequestを使ってURLを指定するとうまくいきました。

■選択した項目の詳細を表示

myItem:Object = view.itemList.selectedItem;　// itemListはDataGridのID

viewはアプリの画面のことです。

選択項目が取得できたら、下画面に表示させます。

この時は、myItem.descendants( qnTitle ).toString();

でLinkButtonとかに表示させています。

・・・と、まだまだ何も理解できていない状態ですが、とりあえずRSSReaderはできました。

でも、作ってる途中に気づいたのですが、MantisのRSSはステータス情報もってなくて全然使えない・・・。

これでは普通にブラウザで見た方が便利なので、今度はHTMLのDOMを操作してデータを取得・表示するアプリを作ってみたいと思います。

 [1]: http://www.flickr.com/photos/41082249@N07/4107105753/ "rsschecker by aki1984, on Flickr"
