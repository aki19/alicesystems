---
title: MacにEclipse導入（＋日本語化）
date: 2009-08-28T06:07:13+00:00
categories:
  - ソフトウェア
---
家でもjQueryやるためにEclipse導入することにしました。  
（たぶんJavaもやるので）

[Eclipse][1]の最新版をDLします。  
最新はGalileo。  
会社ではまだGanymedeなので一足お先に導入です。

DL完了したら次に日本語化します。  
私はホント英語だめなのでまっさきにやっちゃいます。

日本語化には[Pleiades][2]を使います。  
ただ、PleiadesのAll in OneはWinのみなので  
単純にAll in Oneパッケージからdropinsフォルダだけコピーして導入することに。  
（3.4からdoropinsフォルダとかいうのがでてきて本体のみからの導入はよくわからない）

最後にiniファイルを編集します。  
Macのiniファイル場所はアプリケーションのEclipseアイコン上で右クリックメニューを開き、  
「パッケージの内容を表示」からたどれます。

ファイルに以下を記述して保存。

```
-javaagent:../../../dropins/MergeDoc/eclipse/plugins/jp.sourceforge.mergedoc.pleiades/pleiades.jar
```

これで無事日本語化できました。

参考にさせていただいたサイト  
[うえちょこ＠ぼろぐ][3]  
[mizomemo][4](Subversiveのインストール)

 [1]: http://www.eclipse.org/
 [2]: http://mergedoc.sourceforge.jp/
 [3]: http://labs.uechoco.com/blog/2009/04/mac-eclipse-install-pleiades-japanese.html
 [4]: http://mizomemo.blogspot.com/2008/11/eclipse-ganymede-subversive-wo.html
