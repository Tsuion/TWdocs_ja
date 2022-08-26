---
slug: /packager/special-cloud-behaviors
hide_table_of_contents: true
---

# クラウド変数の特殊な挙動

:::info
このページは[TurboWarp Packager](https://packager.turbowarp.org)についての記事です。
:::

デフォルトでは無効になっている"Special cloud behaviors"オプションは、特定の名前のクラウド変数の動作を変更し、プロジェクトの新しい互換性を解除します。これは、[HTMLifierの類似機能](https://github.com/SheepTester/htmlifier/wiki/Special-cloud-behaviours)をベースにしています。この機能は、"クラウド変数"セクションで有効にすることができます。

これを作るには、通常通りクラウド変数を作成するだけですが、以下にあるような具体的な名前をつけます。例えば、`☁ url`変数を使用するには、`url`という名前の変数を作成し、クラウド変数としてマークします。

特別なクラウド動作を有効にすると、これらの変数に対する他の設定が上書きされます。したがって、`☁ username`のような変数は、ローカルに保存されたり、他のユーザーと同期されたりすることは決してありません。

## ☁ url {#url}

`☁ url`の値には、そのページの現在のURLが設定されます。`☁ url`の値を変更しても何も起こりません。

## ☁ redirect {#redirect}

`☁ redirect`の値にURLを指定すると、現在のタブはそのURLへと移動する。

## ☁ open link {#open-link}

`☁ open link`の値にURLを指定すると、プロジェクトはそのURLが開かれた新しいタブを開こうとします。ほとんどのブラウザに組み込まれたポップアップブロッカーにより、これは必ずしも信頼できるものではないことに注意してください。

## ☁ username {#username}

`☁ username`の値を変更すると、センシングカテゴリの`username`ブロックの値も変更されます。

## ☁ pasted {#pasted}

ユーザーがctrl+vなどのショートカットでテキストをページに貼り付けると、そのテキストは`☁pasted`に格納される。

## ☁ set clipboard {#set-clipboard}

`☁ set clipboard`の値が変更されると、ページはユーザーのクリップボードにテキストを保存しようとします。これは常に動作するとは限りません。

## ☁ room id {#room-id}

これは実験的なものであり、変更される可能性があります。

部屋番号 `☁ room id` の値を変更すると、プロジェクトのIDが変更されます。例えば、プロジェクトの元のIDが1234で、`☁ room id`に`xyz`を設定した場合、新しいプロジェクトのIDは`1234-xyz`となります。プロジェクトIDを元のIDに戻すには、`☁ room id`の値を空白の文字列に設定します。

これは、他のユーザーと同期するように設定されているクラウド変数に影響します。これらのクラウド変数はすべて、元の部屋から切り離された完全に別の部屋に移動します。同じルームIDを持つ人だけが、その人たちの間で変数を同期させることができます。クラウド変数の更新には、クラウド変数サーバーへの再接続が必要なため、数秒かかることがあります。

これは、ローカルに保存されたクラウド変数には影響しません。

## ☁ eval {#eval}

:::warning
このオプションを使用するには、"Unsafe special cloud behaviors"が有効になっている必要があります。

Unsafeクラウド動作により、パッケージ化されたプロジェクトは、プロジェクトが通常実行されるサンドボックスの外で任意のコードを実行することができるようになります。パッケージングする環境によっては、プロジェクトがあなたのコンピュータを完全に制御できるようになり、ウイルスをインストールする能力も得られます。

パッケージングするプロジェクトを信頼していない場合、またはこの機能を利用しない場合は、このオプションをオフにしてください。
:::

`eval`の値が変更されると、その値がJavaScriptとして評価される。

JavaScriptが正常に評価された場合、その出力は`☁ eval output`に格納される。

JavaScriptの評価に失敗した場合、そのエラーは`☁ eval error`に格納される。

JavaScriptが[Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise) を返した場合、Promiseが解決されれば`☁ eval output`に、拒否されれば`☁ eval error`にそのエラーが格納されます。なお`☁ eval`の設定は常に瞬時に行われるため、出力変数はすぐに更新されないかもしれません。

## 詳細な情報と考察 {#further-information}

https://github.com/TurboWarp/packager/issues/48 をご確認ください。
