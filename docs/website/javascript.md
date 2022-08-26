---
slug: /javascript
hide_table_of_contents: true
---

# JavaScriptのダウンロード方法

## 短い答え {#short}

 * プロジェクトをパッケージ化・HTML化したい場合は、https://packager.turbowarp.org/ を使用してください。
 * Scratchプロジェクトを読みやすく、編集可能な JavaScript に変換したい場合は、https://leopardjs.com/ を使用してください。

## 長い答え {#long}

TurboWarpが生成するコードは、人間が読んだり編集したりできるように設計されていません。互換性やパフォーマンスを向上させるために多くの変わったことが行われているため、そうしようとすると、学習にとって積極的に有害となります。

例えば、通常のJavaScriptでは、リストアイテムへのアクセスは`myList[myIndex]`のように単純ですが、TurboWarpでは`(b1.value[(b0.value | 0) - 1] ?? "")`または `listGet(b0, b1.value)`といった具合に、どのような仮定ができるかによります。`b0`と`b1`はTurboWarpが使用する実際の変数名で`listGet`はTurboWarpのランタイムの一部である魔法の関数です。また、このコードには書式設定が一切ありません。他のコードサンプルは[別のページ](how)にあります。

Scratchプロジェクトを読みやすく、編集可能なJavaScriptに変換したい場合は、https://leopardjs.com/ を使用してください。

<details>
<summary>本当にわかっているのなら...</summary>

プロジェクトを開始する前に、JavaScriptコンソールでこれを実行します。

```js
vm.enableDebug();
```

そして、JavaScriptがコンパイルされると、コンソールにログが記録されます。

もしあなたが"JavaScriptコンソール"が何なのか、どうやってアクセスするのか知らないのであれば、とにかく生成されたJavaScriptを見ないのが得策でしょう。
</details>
