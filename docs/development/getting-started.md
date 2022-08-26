---
slug: /development/getting-started
sidebar_position: 2
hide_table_of_contents: true
---

# はじめに

TurboWarpの開発環境のセットアップや、ご自身のコンピュータでカスタムビルドを行うための手順です。

TurboWarpを使用したいだけであれば、https://turbowarp.org/ をご利用ください。これらの指示に従う必要はありません。

### 依存関係 {#dependencies}

これらがインストールされていることを確認してください。

 - [Git](https://git-scm.com)
 - [Node.js](https://nodejs.org/en/)

完全にインストールされるには、端末やコンピューターを再起動する必要があるかもしれません。コマンドラインにある程度慣れていることを前提としています。TurboWarpは大規模なアプリであり、ビルドに多くのリソースを必要とする可能性があることに注意してください。

### Scratchの構成についてのメモ {#organization}

Scratch 3は、たくさんの異なるリポジトリに整理されています。それぞれがアプリの一部を実装しています。ここでは、TurboWarpがフォークするほど気になるものを紹介します。

 - scratch-vm はプロジェクトを実行し、コンパイラが存在する場所です。
 - scratch-render はスプライトをレンダリングし、「触れる」ブロックを実装するもので、高品質のペンが存在する場所です。
 - scratch-blocks はスクリプトエディタです。
 - scratch-gui は外部インターフェイスを実装し、すべてをつなぎ、アドオンが存在する場所です。
 - scratch-paint はコスチュームエディタです。
 - scratch-parser は sb2 と sb3 ファイルを抽出します。
 - scratch-svg-render は SVG ファイルをレンダリングします。
 - scratch-storage はファイルのダウンロードとアップロードを行います。
 - scratch-l10n は翻訳を含みます。

### GUIの構築 {#gui}

GUIはTurboWarpを構築するための最小限のものです。

```bash
git clone https://github.com/TurboWarp/scratch-gui
cd scratch-gui
npm ci
npm start
```

リポジトリにpackage-lock.jsonがある場合は、`npm install`の代わりに`npm ci`を使用することをお勧めします。

http://localhost:8601/

GUIを作るだけなら、ここでやめてもよいです。

### Buildビルド {#build}

`npm start` は開発には便利ですが、ある時点で HTML や JS などを取り出す必要があります。これを行うには、scratch-guiフォルダでこれを実行します。

```
npm run build
```

出力は `build` フォルダに入ります。

TurboWarpをWebサイトにデプロイする場合、プロダクションモードを有効にする必要があります。これにより、実行速度が向上し、ファイルサイズが大幅に縮小されます。

```bash
# mac, linux
NODE_ENV=production npm run build

# windows command prompt (untested)
set NODE_ENV=production
npm run build

# windows powershell
$env:NODE_ENV="production"
npm run build
```

デフォルトでは、TurboWarpはhttps://turbowarp.org/editor.html#123 のようなリンクを生成します。しかし、`ROOT=/`と`ROUTING_STYLE=wildcard`（`NODE_ENV=production`と同じように）を設定すると、代わりに https://turbowarp.org/123/editor のようなルートを取得することができます。このためには、適切なエイリアスを設定するサーバーが必要なことに注意してください。scratch-gui の webpack 開発用サーバーはこのためにセットアップされています。本番環境では、https://github.com/TurboWarp/turbowarp.org のようなものが必要でしょう。

### 他のパッケージとの連携 {#linking}

TurboWarpのGUI以外の部分を変更することに興味がある場合、余分な手順を踏まなければなりません。scratch-guiにしか興味がないのであれば、このようなことをする必要はありません。

例で説明するのが一番わかりやすいと思いますので、ここではローカルのscratch-vmとscratch-renderのインスタンスをローカルのscratch-guiにリンクさせる方法を説明します。

```bash
git clone https://github.com/TurboWarp/scratch-vm
git clone https://github.com/TurboWarp/scratch-render

cd scratch-vm
npm ci
npm link
cd ..

cd scratch-render
npm ci
npm link
cd ..

cd scratch-gui
npm link scratch-vm scratch-render
```
