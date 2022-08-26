---
slug: /url-parameters
hide_table_of_contents: true
---

# URLパラメーター


:::note
##"隠し "URLパラメータのみここに記載{#only-hidden-url-parameters-are-listed-here}。
TurboWarpは、ターボモード、60FPS、高品質ペンなどの設定を自動的にURLに格納しますが、一部の高度なオプションはまだ手動で適用する必要があります。このページでは、これらの高度なオプションについてのみ説明します。
:::


## Username {#username}

`username`オプションは、ユーザー名ブロックの値を制御します。

https://turbowarp.org/443603478?username=ExampleUsername

## クラウドホスト {#cloud_host}

`cloud_host`オプションは、TurboWarpが接続するクラウド変数サーバーなどを変更することができます。

https://turbowarp.org/12785898?cloud_host=wss://clouddata.turbowarp.org

`ws://`または`wss://`を含めることは任意ですが、推奨されます。`wss://clouddata.turbowarp.org`はTurboWarpが使用するデフォルトのクラウドデータサーバーなので、この例では実際には何も変更されません。TurboWarpはHTTPSを使用するため、安全でない`ws://`サーバーは動作しない可能性があります。

Scratchのクラウド変数サーバーへの接続には、TurboWarpがサポートできないアカウント認証が必要なため、これを使用することはできません。

## カスタム拡張機能 {#extension}

`extension` オプションは、URLからカスタム拡張機能をロードします。[カスタム拡張機能](/development/custom-extensions)を参照してください。

<!-- Commented due to possible removal -->
<!--
## `scale` {#scale}

フルスクリーンモード時のプレーヤーの最大相対スケールを制御します。

https://turbowarp.org/fullscreen?scale=2
-->

## コンパイラを無効にする {#nocompile}

`nocompile` オプションはコンパイラをオフにします。おそらく、これを有効にするべきではありません。

https://turbowarp.org/?nocompile

## プロジェクトURL {#project_url}

`project_url`オプションは、TurboWarpに任意のURLからプロジェクトデータをダウンロードするように指示します。通常のプロジェクトIDと一緒に使用しないでください。

https://turbowarp.org/?project_url=projects.scratch.mit.edu/10128407

これは、projects.scratch.mit.eduに限らず、CORSをサポートしているURLであれば動作します。 https:// はオプションですが、簡潔にするために付けないことを推奨します。 http:// URLは一般的にセキュリティ上の理由から動作しません。URL は直接ダウンロードする必要があり、CORS (`Access-Control-Allow-Origin: *`) をサポートしていなければならないことに注意してください。[GitHub Pages](https://pages.github.com/) は自動的にこれを行い、うまく機能することが知られています。

## プロジェクトトークン {#token}

`token`オプションは、TurboWarpがScratchからプロジェクトを取得する際にプロジェクト・トークンとして使用するものを指定します。これは、[unshared project changes](/unshared-projects) に関連する実験的な機能で、プロジェクトの作成者が自分の非共有プロジェクトを共有できるようになる可能性があります。

プロジェクト・トークンの入手方法については、ここでは割愛します。

なお、Scratchから返されるトークンには300秒先のタイムスタンプが含まれているため、トークンは5分後に失効するように設計されているようで、この機能を使ったリンクは非常に早く機能しなくなることが予想されます。

プロジェクト トークンは TurboWarp のサーバーに送信されるため、URL に入れることに抵抗がある方もいらっしゃるかもしれません。 **URLパラメータで指定されたプロジェクト・トークンは、一切記録されません。** この約束では不十分な場合は、URLのフラグメントまたはハッシュ部分にトークンを入れて、サーバーに送信されないようにすることもできます。例えば、`https://turbowarp.org/1#?token=1234567_abcdef...`このトークンがScratchから直接プロジェクトをダウンロードするためにのみ使用されることを確認するために、ウェブサイトが行うリクエストを調べることができます。
