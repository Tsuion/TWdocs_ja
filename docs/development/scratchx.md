---
slug: /development/scratchx
hide_table_of_contents: true
---

# ScratchX & TurboWarp

TurboWarpは、[ScratchX](https://scratchx.org)拡張機能の使用とScratchXプロジェクト(.sbx)のロードをプリミティブにサポートするようになりました。

ScratchXは、Scratch Teamが作成したScratch 2の修正版で、非公式な拡張機能を使用することができました。ScratchX は Flash がすべての主要なブラウザから削除されたため機能しなくなりましたが、ウェブサイト scratchx.org はまだ存在しています。

ScratchX拡張機能をTurboWarpで使用するには、拡張機能のJavaScriptソースコードのURLを見つけて、他の[カスタム拡張機能](/development/custom-extensions)と同じように読み込みます。

拡張機能の URL は、拡張機能の Web サイトまたは scratchx.org の URL を見て見つけることができます。例えば、`http://scratchx.org/?url=http://khanning.github.io/scratch-weather-extension/weather_extension.js` を読み込むための URL は `http://khanning.github.io/scratch-weather-extension/weather_extension.js` です。

## 重要な制限事項 {#limitations}

 - ハードウェアに関連するものはすべて動作しません。つまり、scratchx.org の圧倒的多数の拡張機能が動作しないことになります。
 - ScratchX の拡張機能はまだ拡張サンドボックスで動作しています。つまり、scratchx.org の 3D 拡張などは動作しません。
 - パッケージャの ScratchX サポートは一般的に悪くなっています。
 - .sbx ファイルを読み込む際、最初に拡張機能を手動で読み込まないとエラーになります。
 - この機能は非常に実験的なものであり、変更される可能性があります。
