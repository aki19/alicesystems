---
title: Adobe AIRはじめました
date: 2009-11-12T02:03:09+00:00
categories:
  - プログラミング
tags:
  - AIR
---
ずいぶん昔にちょろっと触ったきり忘れていたのですが、  
会社のSQRシステムが変わって、RSSを吐き出すようになったので  
Readerでも作ってみるかーっとAIR再挑戦してみました。

全てを忘れていたので開発環境の構築から。

■開発環境の構築  
とりあえず無料でやります。  
まずはSDKをダウンロード。  
・[Flex SDK][1]  
・[AIR SDK][2]  
続いて開発環境。  
今回はEclipseプラグインのAIR GEARを使います。  
このプラグインは無料なのにコンポーネントをD&Dで配置できたりして便利。  
（実際開発してみるとソースいじるほうが圧倒的に多かったけど・・・）

■とりあえず動かす  
Eclipseに配置＆起動したら設定でSDKの場所を設定。  
新規にAIRプロジェクトを作ります。  
AIRはHTMLベースでもFlexベースでも出来ますが、今回は色々試したかったのでFlexにしました。  
プロジェクトの設定画面ではIDをユニークなものに変更するぐらいかな。  
あとは好みでIconを設定。プロジェクトにインポートしてくれます。  
（でもここで設定した内容は即反映されるわけではなくて設定ファイルでコメントアウトしてたりするから注意）  
プロジェクトができたら「application.xml」という名前の設定ファイルができます。  
これは、色々サンプルみてたら「（アプリケーション名）-app.xml」という名前が多かったので変更してもいいかも。  
変更した場合は、プロジェクトのプロパティーにあるAIRGEARの設定項目のところの名前も変更してください。  
最後に[実行-AIR Application]で実行するとAIRがたちあがります。

■よくでたエラー  

```
application descriptor not found
```

なんか設定ファイルが間違っているよ、と言っている模様。  

```
invocation forwarded to primary instance
```

adlの二重起動エラー。タスクマネージャーとかから終了しよう。  

```
Could not generate timestamp: timestamp.geotrust.com
```

AIRパッケージとして出力する時にでました。イントラネットからだとプロキシの問題でアクセスできないみたい。  
解決策がフォーラムで色々あったのですが自分は家でやることにしました。

長くなったのでRSSReaderについては次回！

 [1]: http://www.adobe.com/cfusion/entitlement/index.cfm?e=flex3sdk
 [2]: http://www.adobe.com/jp/products/air/tools/sdk/
