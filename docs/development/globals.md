---
slug: /development/globals
hide_table_of_contents: true
---

# グローバル

開発者コンソールを使ってアクセスできる、便利なグローバル変数です。

これらはカスタム拡張機能からは使用できません。

## `vm`

[scratch-vm](https://github.com/TurboWarp/scratch-vm)のインスタンスを指します。

## `ScratchBlocks`

*実物の*[scratch-blocks](https://github.com/TurboWarp/scratch-blocks) を参照します (`Blockly` にはほとんど何も載っていません)。エディタを開いた後でのみ利用可能です。

## `paper`

[paper.js](https://github.com/LLK/paper.js)のインスタンスを参照しています。コスチュームエディタを開いた後でのみ利用可能です。

## `ReduxStore`

scratch-gui が使用する内部 redux ストアを指します。

`ReduxStore.getState()` で状態を取得し、 `ReduxStore.dispatch({ type: "..." })` でイベントをディスパッチします。
