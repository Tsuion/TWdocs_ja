---
slug: /translate
hide_table_of_contents: true
---

# TurboWarpの翻訳をお手伝いします

TurboWarpの英語以外の言語への翻訳を手伝ってくれる人を募集しています。興味のある方は、ぜひお読みください。

このガイドに沿って質問がある場合は、新しいディスカッションを作成してください： https://github.com/TurboWarp/scratch-gui/discussions

## 翻訳チームへの参加 {#joining-the-translation-team}

### 必要条件 {#requirements}

 - この文書全体を読むことが期待されています。
 - 英語と他の言語の両方に堪能であることが必要です。
 - 私たちは、機械ではなく、人間によって書かれた翻訳を望んでいます。つまり、**Google翻訳**やその他の機械翻訳は使わないでください。
 - Scratchがまだサポートしていない新しい言語を翻訳するリクエストは却下されます。
 - 新しい言語の最初の翻訳にはしばらく時間がかかるかもしれませんが、今後のアップデートは非常に迅速に行われます。新しく追加された文字列を翻訳するために、時々チェックしてください。
 - これは大きな時間的負担にはならないでしょう。このことで眠れなくなることはありません。私たちは皆ボランティアです。

### 参加申し込み {#request-to-join}
 
 - [Transifexのページ](https://www.transifex.com/turbowarp/turbowarp/)にアクセスし、紫の"JOIN THIS PROJECT"ボタンをクリックします。
 - おそらくTransifexのアカウントを作成しなければならないでしょう。あなたのEメールと新しいパスワードを入力し、サインアップしてください。
 - 名前を聞かれたら、本名ではなく、ユーザー名を名字で入力します。部署と職種は、"localization"と"individual contributor"を選択します。
 - 次のステップでは、"既存のプロジェクトに参加する"を選択します。
 - 翻訳したい言語を選択します。

依頼は数日以内に受理されます。

リクエストが却下された場合は、Scratch（ひいてはTurboWarpも）がその言語をサポートしていない可能性が高いです。

## 翻訳を書く {#writing-translations}

https://www.transifex.com/turbowarp/turbowarp/dashboard/ で自分の言語を探し、"翻訳"ボタンをクリックします。

Transifex翻訳機の使い方は、https://docs.transifex.com/translation/translating-with-the-web-editor をお読みください。

翻訳は定期的にTransifexから引き出されます。

私たちの翻訳は、各サブプロジェクトごとに異なるリソースに分割されています。

 - `gui.json`は[ウェブサイトとエディタ](https://turbowarp.org)のためのものです。これは翻訳する上で最も重要なファイルです。
 - `desktop.json` は [デスクトップアプリ](https://desktop.turbowarp.org/) 用のファイルです。
 - `desktop-web.json` は、[デスクトップアプリのウェブサイト](https://desktop.turbowarp.org/) 用のファイルです。
 - `addons.json` は、[アドオン設定ページ](https://turbowarp.org/addons) 用です (アドオンそのものではありません)。
 - アドオン自体の翻訳は、外部で管理されています。Scratch のブラウザ拡張機能に関するポリシーのため、このページにはリンクしていません。
 - `packager.json` は [the packager] (https://packager.turbowarp.org/) 用です。
 - `store-listings.yaml` は、[Microsoft Store](https://apps.microsoft.com/store/detail/9P4DPZGV5ZKL) のような場所でのデスクトップアプリのリストアップのためのものです。
