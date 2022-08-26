---
slug: /embedding
hide_table_of_contents: true
---

# 埋め込み

TTurboWarpは、標準的なiframeで埋め込むことができます。

```html
<iframe src="https://turbowarp.org/414716080/embed" width="499" height="416" allowtransparency="true" frameborder="0" scrolling="no" allowfullscreen></iframe>
```

`414716080`をプロジェクトのIDに置き換えてください。iframeの幅と高さを変更すると、プレーヤーはそれに合わせて自動的にリサイズされます（499x416の場合、ステージは歪みのない480x360でレンダリングされます）。

TurboWarpのembedは、iframeの透過が許可されている場合、背景が透明になります。TurboWarpの埋め込みは、iframeがフルスクリーンになることを許可されている場合、フルスクリーンボタンを持つようになります。上のコード例では、この2つの機能を有効にしています。

## 非共有プロジェクトに注意 {#unshared-projects}

あなたは、[Scratch APIへの今後の変更により、エンベッドが共有されていないScratchプロジェクトにアクセスできなくなる](/unshared-projects)ことに注意する必要があります。この変更はエンベッディングに影響します。これを回避するには、エンベッディングするプロジェクトが共有されていることを確認するか、代わりに [TurboWarp Packager](https://packager.turbowarp.org/) を使用することができます。

## URLパラメーター {#url-parameters}

[標準のURLパラメータ](url-parameters.md)はすべてそのまま利用可能です。これらを使って、ユーザー名などを制御することができます。

また、embedでのみ利用可能な特殊なパラメータもあります。以下の通りです。

### 自動実行 {#autoplay}

Embedは`autoplay`パラメータをサポートしており、プロジェクトがロードされると自動的にグリーンフラッグがヒットします。例: https://turbowarp.org/15832807/embed?autoplay

サウンドブロックは、ユーザーがプロジェクトとインタラクトする（例えば、クリックする）までは動作しない場合があることに注意してください。これはブラウザが課す制限です。TurboWarpはこれを回避することはできません。

### 設定ボタン {#settings-button}

オプションで、ウェブサイトやエディタにある"Advanced settings"メニューと同様のメニューを開く`settings-button`パラメータを持つembedの設定ボタンを有効にすることができます。例: https://turbowarp.org/15832807/embed?autoplay&settings-button

### フルスクリーンの背景色 {#fullscreen-background}

フルスクリーンモード以外では、埋め込みは透明なので、背景色を変更したい場合は、親要素にスタイルを設定することができます。

フルスクリーンモードでは、ユーザーのコンピュータがダークモードに設定されているかどうかによって、埋め込みは白かほぼ黒のどちらかの色を使用することになります。

この動作をオーバーライドするには、 `fullscreen-background` パラメータに `black` や `rgb(50,90,100)` といったCSSカラーを設定してください。例: https://turbowarp.org/15832807/embed?fullscreen-background=yellow

パーセントエンコーディングで `#` をエスケープすれば、16進数の色も使用できます。`23abc123` のようになります。

### アドオン {#addons}

デフォルトでは、embedはアドオンを有効にしていません。これは`addons`パラメータで上書きすることができ、有効にするアドオンIDをカンマ区切りで列挙します。例: https://turbowarp.org/15832807/embed?addons=pause,gamepad,mute-project

便利なアドオンとそのID。

 - "一時停止ボタン"は`pause`です。
 - "ミュートプロジェクトプレイヤーモード"は`mute-project`です。
 - "ステージの曲面ボーダーを削除"は`remove-curved-stage-border`です。
 - "ファイルのドラッグ＆ドロップ"は`drag-drop` です。
 - "ゲームパッドのサポート"は`gamepad`です。
 - "プロジェクトコントロールの逆順序"は`editor-buttons-reverse-order`です。

他のアドオンは埋め込みに影響を与えません。

## セキュリティへの配慮 {#security}

ユーザーが提供する情報を使って埋め込みリンクを生成する場合、ユーザーが任意のURLパラメータを提供できないように、すべての引数をサニタイズする必要があります。

## もっとコントロールしたい？ {#packager}

[TurboWarp Packager](https://packager.turbowarp.org/)を使用すると、ローディング画面、アクセントカラー、コントロールなどをより自由にコントロールすることができます。また、[Packagerの出力を埋め込む](/packager/embedding)ことも非常に簡単にできます。

## 寄付金について {#donations}

商用サイトでTurboWarpの埋め込みを使用する場合、埋め込みがスムーズに機能し続けるように、[私たちと私たちが依存しているプロジェクトに寄付する](/donate)ことが最善の利益となります。❤️

## ライセンス {#license}

TurboWarpは[GPLv3.0](https://github.com/TurboWarp/scratch-gui/blob/develop/LICENSE)のもとでライセンスされています。私たちは、GPLv3.0作品の`<iframe>`はGPLv3.0に基づく派生作品を作成せず、むしろ派生作品と同じ要件に従わない「集合的作品」を作成すると考えています。しかし、わたしたちは弁護士ではありませんし、これは法的なアドバイスではありません。もしこれがあなたにとって重要なことであれば、弁護士に相談してください。
