---
title: "USDアドカレ対策"
date: 2021-11-23T20:49:01+09:00
draft: false
categories: ["雑談"]
---

[Universal Scene Description Advenc Calendar 2021](https://qiita.com/advent-calendar/2021/usd) という狂気のアドカレをやると宣言してしまったのでここ最近準備をしているわけですが、
このヤバい取り組みをどうやって乗り越えるかの作戦と基本方針について書いておこうと思います。

埋めるのはヘルツさんと技師長師匠のお二人以外の20日分（＋Houdiniアドカレ１件）
書くネタはそこそこあるので、埋められるとは思うものの、どういったこと書くといいのかは
去年の年末ごろから実は考えていましたが、基本方針は以下のようにします。

## 基本方針

まず、多くの人はUSDをつかってどのように運用したりパイプラインを構築したらいいのか
知りたいという人もいるかと思いますが、そのあたりは基本書きません。

というのも、パイプライン構築は会社の規模や分野（ゲーム、映像等々）によっても
大きく異なるというのと
私自身のポリシーとして、仕事にかかわるもの・仕事で得た運用ノウハウなどは
一切書くつもりはないので　今回のアドカレでもそういう内容には触れません。

## 予定

HoudiniアドカレでのComponentBuilder、３日目に技師長師匠のネタにのって Houdini InlineUSDあたりをやる予定ですが
それ以外は基本USDの技術 Python or C++ の実装、基本知識の解説を予定しています。

というのを踏まえてやる内容は以下の通り。

* USDの基本説明
  * Attribute - Relation - Property
  * PopulationMask
  * AssetInfo
  * Schema（IsA/Conclete/API/Multi-Applyed)
* Python
  * コンポジションアーク
  * SceneTraverse
  * usdviewPlugin
  * Tools
    * usdview
    * usdresolve
    * usdzip
    * usdcat
    * usdrecord
    * usdchecker
* 
* C++
  * Pluginの作り方
  * AssetResolution
  * FileFormatPlugin
* Houdini
  * Inline USD
  * ComponentBuilder
* そのほか
  * USDを語る

以上。
順番は気分次第で変わります。

AssetResolverは、usdresolve usdzip を含めてかなり大きい内容なので
これだけで２～３記事消化予定。
基本部分やPythonは、[NoteBook](https://fereria.github.io/reincarnation_tech/60_JupyterNotebook/USD/APISchema/USDCollectoinSample/ )で書くだけかいたけど文章化してないものなんかを中心に書きます。

Toolsは、コマンドラインツールとしての使い方というよりはPythonでの実装回り。
特に resolve や zip は、AssetResolverと大きく絡むので、2.0に切り替わったタイミングもあるので
そちらの実装方法と合わせてまとめる予定。

一応、テストコードの実装と今まで調べきれてなかったあたりの事前リサーチはしているのですが
なかなか書き出してみるとやべー内容だなと思います。
あと、今回は解説記事としてかくというより自分の勉強としての比重が大きいので
特にC++が絡むものに関してはコード的にアレなところがあっても許してください。苦手なのです...

とりあえず完走できるようにがんばります。