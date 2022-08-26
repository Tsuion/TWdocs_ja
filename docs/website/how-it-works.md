---
slug: /how
hide_table_of_contents: true
---

# TurboWarpがScratchプロジェクトを高速に実行する方法

TurboWarpは*コンパイラ*を使用し、Scratchは*インタープリタ*を使用します。これにより、TurboWarpはプロジェクトによって10倍から200倍の速度で動作しますが、ライブスクリプト編集が[不可能になります](#live-script-editing)。

export const Test = ({name, id, scratch, tw}) => (
  <tr>
    <td><a href={`https://scratch.mit.edu/projects/${id}/`}>{name}</a></td>
    <td>{scratch}</td>
    <td>{tw}</td>
  </tr>
);

<table style={{textAlign: "center"}}>
  <thead>
    <tr>
      <th>Test</th>
      <th>Scratch</th>
      <th>TurboWarp</th>
    </tr>
  </thead>
  <tbody>
    <Test name="Quicksort 200000 items" id="310372816" scratch="10.746s" tw="0.0528s" />
    <Test name="Cycles Raytracer r=1 s=10 dof=.08" id="412737809" scratch="832s" tw="16s" />
  </tbody>
</table>

(Tested in Chromium 103 on Linux)

次のようなスクリプトを考えてみましょう。

![旗をクリックしたとき、ずっと変数歩動かす](./assets/forever-move-my-variable-steps.svg)

Scratchのインタプリタは、実行時に[抽象構文木](https://ja.wikipedia.org/wiki/抽象構文木)を歩きます。内部的には次のような感じです。

```json
{
  "va[U{Cbi_NZpSOSx_kVA": {
    "opcode": "event_whenflagclicked",
    "inputs": {},
    "fields": {},
    "next": "tzXnZ{8G!xK|t^WAWF{m",
    "topLevel": true
  },
  "tzXnZ{8G!xK|t^WAWF{m": {
    "opcode": "control_forever",
    "inputs": {
      "SUBSTACK": {
        "name": "SUBSTACK",
        "block": "$xf$bq|xl(}RhT-K,taS"
      }
    },
    "fields": {},
    "next": null,
    "topLevel": false
  },
  "$xf$bq|xl(}RhT-K,taS": {
    "opcode": "motion_movesteps",
    "inputs": {
      "STEPS": {
        "name": "STEPS",
        "block": "cw__.I:g}Y~`:5KmO00q"
      }
    },
    "fields": {},
    "next": null,
    "topLevel": false
  },
  "cw__.I:g}Y~`:5KmO00q": {
    "opcode": "data_variable",
    "inputs": {},
    "fields": {
      "VARIABLE": {
        "name": "VARIABLE",
        "id": "`jEk@4|i[#Fk?(8x)AV.-my variable"
      }
    },
    "next": null,
    "topLevel": false
  }
}
```

Scratchがブロックを実行するときはいつも、いろいろなことをしなければなりません。

 - ブロックの ID と、ブロックのオペコードがどの関数に対応するかを調べなければなりません。
 - ブロックに入力がある場合、それもブロックであり、他のブロックと同じステップを踏まなければならないし、より深い入力もそうでなければならない。
 - ブロック、ループ、条件、プロシージャなどのスタックを手動で管理する。
 - スクラッチスクリプトは降伏することができるので、これらすべてを一時停止して後で再開できる方法で行わなければならない。
 - スクラッチスクリプトは実行中に変更できるため、事前にすべてをキャッシュすることは困難である。
 - などなど。Scratchが1つのブロックを実行するたびに、たくさんのことが起こっているのです。

インタプリタのオーバーヘッドは、JavaScript自体のオーバーヘッドに加え、このコードは非常に動的でJITが最適化するのが難しいため、取るに足らないものではありません。

TurboWarpのコンパイラーは、スクリプトを直接JavaScriptの関数に変換することで、そのオーバーヘッドをすべて取り除きます。たとえば、上記のスクリプトは次のようになります。

```js
const myVariable = stage.variables["`jEk@4|i[#Fk?(8x)AV.-my variable"];
return function* () {
  while (true) {
    runtime.ext_scratch3_motion._moveSteps((+myVariable.value || 0), target);
    yield;
  }
};
```

注目すべき点

 - ブロックIDやオペコードを調べる必要はありません：すべてJavaScriptだけです。
 - 手動で入力を探す必要はありません: これらは単なるJavaScriptの引数です。
 - 手動で状態を維持する必要はありません: ブラウザがすべてやってくれます。
 - これは単一のJavaScript関数なので、[ライブスクリプト編集](#live-script-editing)を実装することはできません。
 - このJavaScriptは人間が書いた典型的なJavaScriptと比べると非常に奇妙に見え、エッジケースScratchの動作との互換性を維持するため、動作も遅くなります。
 - 私たちはこのJavaScriptを手作業で整形し、読みやすくするためにいくつかの変数名を変更しました。実際のコードでは `b0` のような変数名を使い、書式設定もありません。

もちろん、これはインタプリタのオーバーヘッドが無視できるような非常に単純なスクリプトである。これはほとんどのプロジェクトでそうです。インタープリタのオーバーヘッドが大きくなるのは、1フレームあたり何千ものブロックを実行し始めたときだけなのです。

ここでは、より複雑な例として、素朴なソートアルゴリズムを紹介します。

```js
const length = stage.variables["O;aH~(njYNn}Bl@}!%pS-length-"];
const list = stage.variables["O;aH~(njYNn}Bl@}!%pS-list-list"];
const newLength = stage.variables["O;aH~(njYNn}Bl@}!%pS-new-"];
const i = stage.variables["O;aH~(njYNn}Bl@}!%pS-i-"];
const temp = stage.variables["O;aH~(njYNn}Bl@}!%pS-tmp-"];
return function fun1_sort () {
  length.value = list.value.length;
  // repeat until length = 0
  while (!compareEqual(length.value, 0)) {
    newLength.value = 0;
    i.value = 1;
    // repeat length - 1 times
    for (var counter = ((+length.value || 0) - 1) || 0; counter >= 0.5; counter--) {
      // change i by 1
      i.value = ((+i.value || 0) + 1);
      // if item i - 1 of list is greater than item i of list
      if (
        compareGreaterThan(
          list.value[((((i.value || 0) - 1) || 0) | 0) - 1] ?? "",
          list.value[((i.value || 0) | 0) - 1] ?? ""
        )
      ) {
        // swap item i and i - 1 of list
        temp.value = listGet(list.value, i.value);
        listReplace(
          list,
          i.value,
          list.value[((((+i.value || 0) - 1) || 0) | 0) - 1] ?? ""
        );
        listReplace(
          list,
          (+i.value || 0) - 1,
          temp.value
        );
        newLength.value = i.value;
      }
    }
    length.value = newLength.value;
  }
};
```

### ライブスクリプト編集 {#live-script-editing}

コンパイラを使ってスクリプトを起動した場合、Scratchのようにブロックを移動、削除、追加して、その変更をリアルタイムに反映させることはできないです。スクリプトを再起動する必要があります。これを実現する方法はいくつかあると思いますが、パフォーマンスが落ちたり、かなり複雑になってしまいます。いずれは実現したいが、今はまだできません。
