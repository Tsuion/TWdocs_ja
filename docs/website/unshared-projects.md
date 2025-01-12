---
slug: /unshared-projects
sidebar_label: 非共有プロジェクト
---

# 非共有プロジェクトは、いずれ実際に非公開になる

<!-- 
  I won't link these in the public website because there will be way too much spam if we do that, but here are relevant links:
  https://github.com/LLK/scratch-gui/pull/8269
  https://github.com/LLK/scratch-www/pull/6773
-->

**2022年6月1日更新** - TurboWarp、forkphorus、パッケージャー、その他のサードパーティーサイトでの非共有プロジェクトの読み込みは、Scratch APIへの今後の変更により、非共有プロジェクトが実際に非公開になるため、**将来のある時点で**できなくなる予定です。

私たちはこれを[良いこと](#good-thing)だと考えていますが、あなたのワークフローによっては[回避策](#workarounds)を見つけなければならないかもしれません。

##6月1日更新 {#june-1}

<!-- https://scratch.mit.edu/discuss/topic/602417/?page=55#post-6356705 -->
Scratch Teamのフォーラムへの投稿で、私たちが以前から推測していたことが確認されました：この変更により、非共有プロジェクトは最初からそうであったように、実際に非公開となります。このページの残りの部分は、これを反映するために更新されました。

この変更がいつ行われるかは、まだ不明です。私たちは「将来のある時点で」以上の時間の予測を提供することはありません。盲目的な推測は役に立ちません。また、意見の相違をフォーラムで怒り狂って発散しても、何の解決にもなりません。

この変更がなされるには[正当な理由](#good-thing)があるのです。

混乱を減らすために、言い換えだけでなくこのページに誘導することを検討してください。

## 実際に起きていること {#whats-happening}

Scratchでは、プロジェクトのロード方法を変更し、"プロジェクトトークン "を使用するようになりました。非共有プロジェクトの場合、このトークンはプロジェクトの所有者のみがアクセスすることができます。

このトークンへのアクセスはプロジェクトをダウンロードする際に必要となり、プロジェクトIDを知るだけではTurboWarp、forkphorus、scratch-gui、その他のサードパーティサイトで非共有プロジェクトをロードすることは不可能になります。この変更は、同じブラウザでScratchにサインインしている場合でも、自分の非共有プロジェクトに影響を及ぼします。

## これは良いことです {#good-thing}

非共有プロジェクトの保護は、10年遅れています。

Scratchのウェブサイトには「自分だけが見ることができる」と書かれているのに、非共有プロジェクトが実は非公開であることを知らなかったために、誰も自分のプロジェクトを盗まれたことがない、というふりはしないでください。多くの非共有プロジェクトには、非共有プロジェクトが実際には非公開であるという前提で、子供やその友人、家族などの写真やビデオ、その他の個人情報が含まれています。

他のほとんどの大規模なウェブサイトでは、「非共有」または「非公開」のものが実際には事実上公開されていることは、重大なセキュリティバグとみなされ、通常は非常に大きなバグバウンティの対象となります。([例](https://bugs.xdavidhu.me/google/2021/01/11/stealing-your-private-videos-one-frame-at-a-time/))

私たちは、非共有プロジェクトを実際に非公開にしたいのであれば、Scratch Teamに相談すべきだというスタンスを常にとっており、おそらくScratch Teamが耳を傾けるほど多くの人がそうしてくれたのでしょう。

## 回避策 {#workarounds}

私たちの最優先事項は、共有プロジェクトが最小限の中断で作業を継続できるようにすることです。非共有プロジェクトに関連するその他のことは、起こるとすれば、後で起こることです。

非共有プロジェクトの閲覧に依存する既存のリンク（埋め込みを含む）は、今後、変更なしに機能しなくなると考えてください。

以下は、現在提案されている回避策のリストです。

1. プロジェクトを他の人と共有する最良の方法は、Scratchのウェブサイトで共有することです。Scratchのコミュニティは本当に素敵です。これはScratchが推奨していることです。
1. プロジェクトを共有せずにサードパーティのサイトでテストしたいだけなら、プロジェクトをコンピュータにダウンロードし(ファイル > コンピューターに保存)、ダウンロードしたファイルをロードすることができます。ほとんどのツールはこれをサポートしています。
1. Scratch上でプロジェクトを共有せずに他のサイトに埋め込むには、 [TurboWarp Packager](https://packager.turbowarp.org/), [forkphorus packager](https://forkphorus.github.io/packager/), または [HTMLifier](https://sheeptester.github.io/htmlifier/) ([埋め込みの詳細](/packager/embedding)) を使ってください。これらは、生成されたファイルをアップロードする場所を見つければ、Scratchでプロジェクトを共有することの代替になるかもしれません。

共同作業のようなものに対するより多くの回避策は、検討されているかもしれませんし、されていないかもしれませんが、約束はできません。何も起きないと思ってください。Scratchは15年前、TurboWarpは2年前です。TurboWarpのない13年間、コラボレーションはうまくいっていましたし、これからもうまくいくでしょう。

:::caution
このような提案をする人を何人か見かけましたので、はっきりさせておきたいと思います。**scratch.mit.edu 以外のサイトで、Scratchのパスワードを要求してくるものは詐欺です。Scratchのパスワードを尋ねるサイト（scratch.mit.edu以外）は詐欺です。正規のサイトが Scratchのパスワードを尋ねることは決してありません。<span style={{textDecoration: 'underline'}}>例外はありません。</span>.**
:::

## オリジナルページ {#original}

:::info
このセクションは、変更が実施されるまでは正確なままです。
:::

TurboWarpやforkphorusなどは共有されていないプロジェクトを読み込むことができるので、その点を気にされている方も多いのではないでしょうか？

<!-- "9年 "のリファレンスは https://github.com/scratchblocks/scratchblocks/issues/1 -->。
<h3>これは9年前から存在するScratch APIの問題です。TurboWarpのバグではありません。</h3>。

Scratch Teamによって管理されている公式のScratch開発ビルドでさえ、共有されていないプロジェクトを表示できます (例: https://llk.github.io/scratch-gui/develop/#1)。これは、Scratch Teamがこの問題を深刻なものとは考えていないことを示唆しています。TurboWarpはscratch-guiと同じ方法でプロジェクトを読み込むので、共有されていないプロジェクトも読み込むことができます。この問題は、Scratch Teamによってのみ適切に解決されます。

### TurboWarpが非共有プロジェクトの読み込みを拒否しないのはなぜですか？ {#why-not-fix}

TurboWarpが非共有プロジェクトの読み込みを拒否したとしても、根本的な原因はScratchのAPIにあります。非共有プロジェクトは、Scratchの公式開発ビルドや他の多くのツールを使って簡単に見ることができます。TurboWarpは完全にオープンソースなので、プロジェクトが非共有であるかどうかをチェックするコードを持たない独自のバージョンを誰かが簡単に作ることができます。非共有プロジェクトは、何ら安全ではないでしょう。

これは、Scratch Teamが、api.scratch.mit.edu（プロジェクトのタイトルと説明を読み込む場所）に対してすでに行ったように、projects.scratch.mit.edu（プロジェクトのデータをダウンロードする場所）に対してもアクセスコントロールを行うことでのみ解決できる問題です。もしこれが重要だと思うのであれば、Scratch Team に知らせてください。

### 非共有プロジェクトを保護する方法 {#prevention}

プロジェクトID（あなたのプロジェクトのURLに含まれる数字）を他人と共有しないでください。これには、あなたのプロジェクトへのリンクや、ブラウザのURLバーを含むスクリーンショット・動画も含まれます。

プロジェクトIDがすでに流出していて、そのプロジェクトを他の人に見られたくない場合、マイスタッフからプロジェクトを削除しないでください。その代わり、次のことを行ってください。

1. ファイル > コピーとして保存]メニューからプロジェクトのコピーを保存する。
2. コピーの保存が完了するのを待ちます。コピーしたプロジェクトを更新して、正しく保存されたことを確認する。
3. 元のプロジェクトに戻り、元のプロジェクトからすべてを手動で削除します。スプライト、サウンド、コスチューム、スクリプトなど、他の人に見られたくないものをすべて手動で削除してから、再度プロジェクトを保存して上書きしてください。マイスタッフページからプロジェクトを削除しても、ゴミ箱を空にしても、Scratchは実際にはプロジェクトデータを削除しないので、十分ではありません。
4. 今後の作業はすべて、手順1で作成したコピーで行ってください。

もし、この作業をする前に誰かがすでに自分のコンピュータにプロジェクトをダウンロードしていた場合、あなたが直接できることはあまりありません。もし誰かがあなたの非共有プロジェクトを盗み、あたかも自分が作ったかのように公開した場合は、Scratch Teamに連絡してください。

プロジェクトを安全に保つもう一つの方法は、[Scratch Desktop](https://scratch.mit.edu/download)や[TurboWarp Desktop](https://desktop.turbowarp.org/)などのオフラインエディタを使用することでしょう。

また、この機会にプロジェクトのバックアップをコンピュータの安全な場所に保存しておくと、バックアップの重要性を[苦労して](https://ocular.jeffalo.net/search?q=project%20disappeared&sort=relevance)学ぶ必要がありません。

### プロジェクトID1とは何ですか？{#what-is-1}

好奇心旺盛な人は、https://turbowarp.org/1 や https://llk.github.io/scratch-gui/develop/#1 を訪れて、奇妙なプロジェクトを発見したことがあるでしょう。これはまさに、Scratch APIがID 1のプロジェクトを問い合わせたときに返すものです。
