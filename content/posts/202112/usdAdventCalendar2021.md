---
title: "USDアドカレ対策"
date: 2021-11-23T20:49:01+09:00
draft: false
categories: ["雑談"]
slug: usdac21_talk
---

[Universal Scene Description Advenc Calendar 2021](https://qiita.com/advent-calendar/2021/usd) という狂気のアドカレをやると宣言してしまったのでここ最近準備をしているわけですが、
このヤバい取り組みをどうやって乗り越えるかの作戦と基本方針について書いておこうと思います。

埋めるのはヘルツさんと技師長師匠のお二人以外の 20 日分（＋ Houdini アドカレ１件）
書くネタはそこそこあるので、埋められるとは思うものの、どういったこと書くといいのかは
去年の年末ごろから実は考えていましたが、基本方針は以下のようにします。

## 基本方針

まず、多くの人は USD をつかってどのように運用したりパイプラインを構築したらいいのか
知りたいという人もいるかと思いますが、そのあたりは基本書きません。

というのも、パイプライン構築は会社の規模や分野（ゲーム、映像等々）によっても
大きく異なるというのと
私自身のポリシーとして、仕事にかかわるもの・仕事で得た運用ノウハウなどは
一切書くつもりはないので　今回のアドカレでもそういう内容には触れません。

## 投稿先

投稿先は、[Zenn](https://zenn.dev/remiria) or [Tech ページ](https://fereria.github.io/reincarnation_tech/11_Pipeline/)です（Tech ページのほうが多め）。

## 予定構成

Houdini アドカレでの ComponentBuilder、３日目に技師長師匠のネタにのって Houdini InlineUSD あたりをやる予定ですが
それ以外は基本 USD の技術 Python or C++ の実装、基本知識の解説を予定しています。
基本説明含めて、Python 比率多めです。

というのを踏まえてやる内容は以下の通り。

-   USD の基本説明
    -   Attribute - Relation - Property
    -   PopulationMask
    -   AssetInfo
    -   Schema（IsA/Conclete/API/Multi-Applyed)
-   Python
    -   コンポジションアーク
    -   SceneTraverse
    -   usdviewPlugin
    -   Tools
        -   usdview
        -   usdresolve
        -   usdzip
        -   usdcat
        -   usdrecord
        -   usdchecker
-   C++
    -   Plugin の作り方
    -   AssetResolution
    -   FileFormatPlugin
-   Houdini
    -   Inline USD
    -   ComponentBuilder
-   そのほか
    -   USD を語る

以上。
順番は気分次第で変わります。

AssetResolver は、usdresolve usdzip を含めてかなり大きい内容なので
これだけで２～３記事消化予定。
最近 Resolver 回りでずっと遊んでいたのですが、このあたりが個人的な USD の強いところだと思ってるので
今回のメインになるかなぁと思われます。
基本部分や Python は、[NoteBook](https://fereria.github.io/reincarnation_tech/60_JupyterNotebook/USD/APISchema/USDCollectoinSample/)で書くだけかいたけど文章化してないものなんかを中心に書きます。

Tools は、コマンドラインツールとしての使い方というよりは Python での実装回り。
特に resolve や zip は、AssetResolver と大きく絡むので、2.0 に切り替わったタイミングもあるので
そちらの実装方法と合わせてまとめる予定。

一応、テストコードの実装と今まで調べきれてなかったあたりの事前リサーチはしているのですが
なかなか書き出してみるとやべー内容だなと思います。
あと、今回は解説記事としてかくというより自分の勉強としての比重が大きいので
特に C++が絡むものに関してはコード的にアレなところがあっても許してください。苦手なのです...

とりあえず完走できるようにがんばります。
