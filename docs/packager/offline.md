---
slug: /packager/offline
hide_table_of_contents: true
sidebar_label: オフラインパッケージャー
---

# オフラインパッケージャー

[TurboWarp Packager](https://packager.turbowarp.org/)をオフラインで使用する方法があり、様々な状況（例えば、おそらくあなたの学校はturbowarp.orgをブロックしています）で役に立つことがあります。

オフラインパッケージャーは1ヶ月に1回程度更新する予定です。

Electron、NW.js、WKWebViewの実行ファイルのような大きな資産はオフラインパッケージャーに含まれませんので、必要に応じて別途ダウンロードする必要があります。オフラインパッケージャーはこれらのファイルを最初にダウンロードした後、オフラインでキャッシュしようとするので、ダウンロードは一度だけでよいはずです。通常、これらのダウンロードは、あなたの学校がturbowarp.orgをブロックしている場合でも、まだ動作します。

## Desktop App {#desktop}

[TurboWarp Desktop](https://desktop.turbowarp.org/)をダウンロードすると、オフライン版のパッケージャーを含むことができます。右上の「(?)」ボタンを押し、パッケージャーを選択することでアクセスできます。

内蔵のパッケージャーは、エディターで開いているプロジェクトを自動的に読み込みます。

## スタンドアロンHTML {#html}

デスクトップアプリをダウンロードできない、またはしたくない場合は、代わりにGitHubからスタンドアロンHTML版をダウンロードすることができます。https://github.com/TurboWarp/packager/releases にアクセスし、トップリリースの「Assets」の下にある「turbowarp-packager-standalone-x.x.html」をダウンロードします。HTMLファイルはブラウザで開くだけでOKです。

このHTMLファイルにはアップデートチェッカーは含まれていません。自分でアップデートのチェックと処理をする必要があります。

## Webアプリケーション {#pwa}

https://packager.turbowarp.org/ は、一度読み込むとオフラインで機能しようとするウェブアプリです。これはまだ実験的なものであり、これに頼ることはお勧めしません。
