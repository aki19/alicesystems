---
title: Toodledo APIを使う方法
date: 2010-02-26T01:22:00+00:00
categories:
  - WEBサービス
  - プログラミング
tags:
  - AIR
---
TODOサービスに[Toodledo][1]を使っているのですが、  
勉強用にAPIを使ったAIRのクライアントソフトを作ってみようと思います。  
開発環境はフリーの[AIR GEAR][2]を使います。

ToodledoAPIを利用するためには、まずkeyを取得する必要があります。  
今回はkeyを取得するまでの流れをメモしておこうと思います。

keyを取得するために、まずは自分のuseridを確認します。  
useridは、メイン画面左メニューのTools & Servicesページの一番下にあるDevelopers APIの詳細画面で確認できます。  
Your unique useridと書かれたところにある文字の羅列がuseridになります。  
これはAPIで取得することもできます。

次にこれを使ってtokenを得ます。  
ActionScriptだと以下のようなコードで得ることができます。

[sourcecode language=&#8221;actionscript3&#8243;]  
private function loadXML():void {  
// tokenを得るAPIをたたく  
var getTokenRequest:URLRequest = new URLRequest("http://api.toodledo.com/api.php?method=getToken;userid=" + UniqueUserId + ";");  
var getTokenLoader:URLLoader = new URLLoader();  
getTokenLoader.load(getTokenRequest);  
getTokenLoader.addEventListener(Event.COMPLETE, onCompleteGetToken);  
}

/**  
* 取得できたXMLからTokenを得る  
*/  
private function onCompleteGetToken(event:Event):void {  
ReadyToken = true;  
// tokenの抽出  
var loader:URLLoader = URLLoader(event.target);  
var tokenXML:XML = XML(loader.data);  
trace(tokenXML);  
Token = tokenXML.toString();  
}  
[/sourcecode]

tokenを得たら先ほど確認したuseridとパスワードを組み合わせてkeyを得ます。  
が、この時パスワードと連結した全体の文字列をMD5ハッシュする必要があります。  
ActionScriptの場合、以下のライブラリを使ってMD5ハッシュできるようになります。  
[as3corelib][3]  
※私の場合このライブラリを使いました。他にもあるかもしれません。

DLしたswcファイルをプロジェクトの外部ライブラリとして指定します。  
ファイルのimport文は以下の通り。

[sourcecode language=&#8221;actionscript3&#8243;]  
import com.adobe.crypto.*;  
[/sourcecode]

これを使って以下のようにMD5ハッシュし、keyを生成します。

[sourcecode language=&#8221;actionscript3&#8243;]  
/**  
* keyを得る（ハッシュしたパス＋Token＋UserId）  
*/  
private function getKey():void {  
Key = MD5.hash(MD5.hash(PassWord) + Token + UserId);  
}  
[/sourcecode]

これでkeyを使ったAPIが使えます。

 [1]: http://www.toodledo.com/
 [2]: http://amateras.sourceforge.jp/cgi-bin/fswiki/wiki.cgi?page=AmaterasAIR
 [3]: http://code.google.com/p/as3corelib/
