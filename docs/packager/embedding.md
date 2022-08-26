---
slug: /packager/embedding
hide_table_of_contents: true
sidebar_label: 埋め込み
---

# パッケージャーを組み込む

:::info
このページは[TurboWarp Packager](https://packager.turbowarp.org)についてのページです。もし、Scratchプロジェクトを簡単にWebサイトに埋め込みたいだけなら、[その他の埋め込みページ](/embedding)をご覧ください。
:::

TurboWarp Packagerの出力を他のWebサイトに埋め込むことができます。

```html
<iframe src="path_to_project.html" width="480" height="360" allowtransparency="true" frameborder="0" scrolling="no" allowfullscreen></iframe>
```

使用した環境、プロジェクトの保存場所、プロジェクトの名前によって、 `src` 属性は異なります。

 - "Plain HTML"の場合は、HTMLファイルへのパスです。
 - "Zip"の場合は、解凍されたZipに含まれるファイル `index.html` へのパスが指定されます。

コントロールを有効にしている場合は、ステージが縮小されないように `height` の値に 48 を追加してください。
