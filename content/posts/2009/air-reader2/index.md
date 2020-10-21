---
title: HTMLReaderつくりました
date: 2009-12-04T07:16:26+00:00
categories:
  - プログラミング
  - 自作
tags:
  - AIR
---
[<img loading="lazy" src="http://farm3.static.flickr.com/2624/4156815709_ba5b78bd2e.jpg" width="180" height="300" alt="htmlchecker" />][1]

前回RSSReaderを作った結果、出力されるRSSでは満足な結果が得られないことがわかったので、

今度はHTMLのDOMから必要な情報を取り出す方向でReaderを作ってみました。

&#160;

■ドキュメントの取得

HTMLの読み込みはHTMLLoaderとかいうのでやるらしい。

HTMLLoaderに読み込みたいURLをload。

HTMLLoaderがhtmlControlという変数にセットされているとしたら、

doc:Object = htmlControl.window.document;

これでドキュメントがとれます。

&#160;

■タイトルを取得してみる

var title:Object = doc.getElementsByTagName("title");  
&#160;&#160;&#160; titleValue:String = title[0].innerHTML;

上記のように書くと、title要素の中身がtitleValueにセットされます。

&#160;

■属性の中身を取得してみる

要素.getAttribute("bgcolor");

これで@bgcolorの中身がとれるはず。

&#160;

■指定したクラス名の要素を取得したいんですけど・・・

指定したタグ名の要素を取得する方法は、上述した通りですが、クラス名はどーなの、ということで調べてみたんですけどどうやらなさそう？

私の場合は、<a href="http://blog.livedoor.jp/nipotan/archives/15424695.html" target="_blank">にぽたん研究所</a>さんが作成されたメソッドを利用させていただきました。

&#160;

ごちゃごちゃしたプログラムになってしまいましたが、一応必要な機能はそろったアプリになったとは思います。

これにてSQRReader作成は終了。

 [1]: http://www.flickr.com/photos/41082249@N07/4156815709/ "htmlchecker by aki1984, on Flickr"
