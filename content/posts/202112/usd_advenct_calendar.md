---
title: "Advent Calendarハジマルヨー"
date: 2021-12-01T00:00:47+09:00
draft: false
categories: ["雑談"]
---


さて、狂気のAdvent Calendar [Universal Scene Description](https://qiita.com/advent-calendar/2021/usd) 1日目。
最初は、テクニカルな記事というより、
これまでのUSDについての概要（過去主要記事まとめ）や以降の記事の方針、
個人的なUSDへの考え方についてを書いていこうと思います。

## まずはじめに

USDがどんなものかは、以前書いた [USDとは](https://fereria.github.io/reincarnation_tech/11_Pipeline/01_USD/02_whats_USD/)に書いてありますので詳細は省きますが、
ざっくりと書くとPixarが公開しているシーングラフを扱うオープンソースのライブラリです。
この記事を書いている段階で version 21.11 が、[GithubのUSDリポジトリ](https://github.com/PixarAnimationStudios/USD/)で公開されています。
現在もライブラリ本体も常に進化を続け、さらに対応するツールもここ数年で大幅に増えてきており、
世界的に見てもシーングラフを扱うライブラリとしては標準的なフォーマットになりつつあるのではないかと思います。

### 勉強を始めた理由

そんな中、私が勉強を開始したのが2019年の夏頃です。

自分自身が勉強を始めた理由はいろいろとありますが、
2019年のSIGGRAPHに参加して、各種パイプラインのセッションで当たり前のように導入が語られていたことです。
これだけ語られるということは、
近い将来どのソフトウェアにも導入され当たり前に扱われる未来が来るはずです。
それならば早いうちに勉強を開始するに越したことはないと思い、
本腰をいれて勉強を開始しました。

パイプラインまわりは、どこも手探りなところが多く問題を解決する手段を探している事が多いと思います。
そんな中で、海外のすごいエンジニアやアーティストが、議論を重ね、実践を重ね、そして洗練してきたものであれば
問題を解決するための答えが得られるのではないか？と、考えました。

実際、USDは
大規模なシーングラフを扱うことのできる強固なフォーマットであり、
さらには[コンポジションアーク](https://fereria.github.io/reincarnation_tech/11_Pipeline/01_USD/05_comp_arc/)を代表する多数のファイルをオーサリングのための機能や、
[ファイルフォーマットプラグイン](https://zenn.dev/remiria/articles/c6470aea5f6f59)のような、既存のデータを組み込んだり動的にシーングラフを構築する機能、
[カスタムスキーマ](https://fereria.github.io/reincarnation_tech/11_Pipeline/10_USDTips/00_create_custom_schema/)のような、カスタマイズを可能にする各種API等々。
さらに、USDを使う上で便利なプレビューツールであるusdview含めた実用的な各種ツールセット。

それらの多くが、パイプラインを作る上で非常に強力な機能を持っています。

### パイプラインツールとしてのUSD

最初に書いた通り、2021年現在DCCツールの対応がだいぶ進み、
主要なツールでは USDのImport・Exportが可能になり
HoudiniのSOLARISやBlenderUSDHydraAddon、Katana等を使用すればライティングやレンダリングが可能になりました。
また、OmniverseのようなUSDをベースにした強力な共同開発環境も登場しています。

それらのツールは非常に便利で、誰でもUSDを扱える環境ができつつあります。
ですが、それと同時に（それ以上に）個人的USDはパイプラインを構築するためのツールだと思うので、
そのUSDの仕組みや、その構造、ライブラリの機能を利用してどのようにパイプラインを構築できるのか？
といったことが、とても大切なのではないかと思います。

## アドカレ記事について

というわけで、今回のアドカレを始めるにあたり
自分の担当分をどういった内容をメインにするか考えていましたが、
[https://fereria.github.io/blog/posts/usdadventcalendar2021/](https://fereria.github.io/blog/posts/usdadventcalendar2021/)
事前の雑談Blogにも書きましたが、学習理由にもあるとおり以下のような方針でいきます。

1. USDの機能や実装方法についてを書く（具体的な事例等は書かない）
2. 過去記事・JupyterNotebookにだけ書いたような内容の記事化
3. DCCツールの使い方は書かない（Python C++ の実装側メイン）
4. 自分の学習結果を書く

Houdiniに関しては、
[https://qiita.com/advent-calendar/2021/happrentice](https://qiita.com/advent-calendar/2021/happrentice)
Houdini Apprentice ２日目に InlineUSDについて。
[https://qiita.com/advent-calendar/2021/houdini](https://qiita.com/advent-calendar/2021/houdini)
Houdini １２日目に、コンポーネントビルダーについてを投稿予定です。

ある程度事前に調査・テスト実装などはしていますが、
特にC++絡みは自分も勉強しながらなのでミスやら勘違いはお許しください（突っ込まれたら直します）

これから１か月、どこまでいけるかわかりませんが最後までどうぞお付き合いください。
よろしくお願いします。

次は、HoudiniApprentice２日目で InlineUSDについて書きます。

## いつも参考にしているリンクなど

最後に、日ごろUSDを調べる＋今回のアドカレ記事を書くにあたり、
参考にしているサイトや各種リンクをご紹介します。


公式

- [https://github.com/PixarAnimationStudios/USD](https://github.com/PixarAnimationStudios/USD)
- [https://graphics.pixar.com/usd/release/index.html](https://graphics.pixar.com/usd/release/index.html)
- [https://graphics.pixar.com/usd/release/api/index.html](https://graphics.pixar.com/usd/release/api/index.html)

実装参考

- [https://github.com/ColinKennedy/USD-Cookbook](https://github.com/ColinKennedy/USD-Cookbook)

USD関係スライド、記事

- [https://www.slideshare.net/takahitotejima/usd-79288174](https://www.slideshare.net/takahitotejima/usd-79288174)
- [https://indyzone.co.jp/archives/1715](https://indyzone.co.jp/archives/1715)

様々な対応ツール

- [https://www.sidefx.com/ja/products/houdini/solaris/](https://www.sidefx.com/ja/products/houdini/solaris/)
- [https://github.com/Autodesk/maya-usd](https://github.com/Autodesk/maya-usd)
- [https://github.com/GPUOpen-LibrariesAndSDKs/BlenderUSDHydraAddon](https://github.com/GPUOpen-LibrariesAndSDKs/BlenderUSDHydraAddon)
- [https://docs.blender.org/manual/en/latest/files/import_export/usd.html](https://docs.blender.org/manual/en/latest/files/import_export/usd.html)
- [https://learn.foundry.com/nuke/content/comp_environment/3d_compositing/usd.html](https://learn.foundry.com/nuke/content/comp_environment/3d_compositing/usd.html)
ほかにもいろいろ。
- [https://www.nvidia.com/ja-jp/omniverse/](https://www.nvidia.com/ja-jp/omniverse/)

過去に自分で書いた記事やサンプルコード

- [https://fereria.github.io/reincarnation_tech/11_Pipeline/](https://fereria.github.io/reincarnation_tech/11_Pipeline/)
- [https://fereria.github.io/reincarnation_tech/60_JupyterNotebook/USD/APISchema/USDCollectoinSample/](https://fereria.github.io/reincarnation_tech/60_JupyterNotebook/USD/APISchema/USDCollectoinSample/)

