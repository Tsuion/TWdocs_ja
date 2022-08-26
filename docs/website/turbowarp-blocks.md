---
slug: /blocks
hide_table_of_contents: true
---

# TurboWarpブロック

TurboWarpにはブロックのセクションがあり、これまでScratchプロジェクトではアクセスできなかった特定の機能を使用することができます。

## is compiled? と is TurboWarp? {#is-compiled}

![is compiled?](./assets/is-compiled.svg)

https://scratch.mit.edu/projects/414716080/ をご覧ください。

これらのブロックはScratchと"互換"であり、実際には引数レポーターを変更しただけのものだからです。

:::warning
この警告を超えたブロックは、Scratchと**互換性がありません**。これらを使用したプロジェクトは、Scratchのウェブサイトにアップロードすることはできません。TurboWarp専用のブロックを使用しないのであれば、TurboWarpでプロジェクトを作成し、Scratchにアップロードしても問題はないはずです。

**これらのブロックの使用はお勧めしません。当面の間、新しいブロックは追加されません**。
:::

## さいごに押したキー {#last-key-pressed}

![last key pressed](./assets/last-key-pressed.svg)

最後に押されたキーが分かります。このような使い方を想定しています。

![when any key pressed, do something with last key pressed](./assets/how-to-use-last-key-pressed.svg)

## マウスボタンを押したまま？ {#mouse-button-down}

![primary mouse button down?](./assets/mouse-button-down.svg)

これは"マウスが押された"のようなものですが、個々のボタンをチェックすることができます。Scratchがマウスの入力をどのように解釈するかによって、"is primary mouse button down?"のようなブロックがtrueを報告し、標準の"マウスが押された"がfalseを報告することがあることを覚えておいてください。

 * (0)プライマリは通常左です。
 * (1) middleは通常スクロールホイール
 * (2) secondaryは通常右 (このブロックを一度実行すると、ステージ上で右クリックができなくなります)
