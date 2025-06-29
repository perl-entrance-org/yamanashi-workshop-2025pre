# JavaScript入門

ここではまずTypeScriptの元になっている言語であるJavaScriptについて学んでいきましょう。

## 変数宣言

JavaScriptでは変数の宣言に`const`または`let`を使います。
(実はもう1つ`var`での宣言も可能なのですが、`var`は意図しない挙動を招きがちであるので現代では使用が非推奨となっています)

### `let`


### `const`

`const`を使用すると再代入不可な変数とその初期値を宣言できます。

`const`はあくまで変数の再代入を禁止する宣言であり、定数の宣言とは異なります。
したがってオブジェクトや配列を宣言した場合は破壊的に値を書き換えることが可能です。

```js
const people = ['satuki', 'ann'];
people.push('sakurako'); # 配列に破壊的に値を追加可能
console.log(people); # 'satuki', 'ann', 'sakurako'

const japan = { capital: 'Tokyo' };
japan.capital = 'Yamanashi' # フィールドには再代入が可能
console.log(japan) # { capital: 'Yamanashi' }
```

なおあくまでこれはJavaScriptの話であり、TypeScriptでは型を工夫することでこれらの破壊的な代入を防ぐことが可能です。

