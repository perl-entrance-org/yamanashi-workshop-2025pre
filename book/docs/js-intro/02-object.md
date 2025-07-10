# JavaScritpのオブジェクトとは

JavaScriptではプリミティブ型でないものはすべてオブジェクトでした。
ではオブジェクトとは一体どのようなものでしょうか。

JavaScriptのオブジェクトとは**プロパティの集まり**のことであり、プロパティは**名前(key)と値(value)の組**の概念です。
これは他の言語で言うところの連想配列、ハッシュ、辞書などと呼ばれるものと近いです。

## constふたたび

`const`はあくまで変数の再代入を禁止する宣言であり、定数の宣言とは異なります。
したがってオブジェクトや配列を宣言した場合は破壊的に値を書き換えることが可能です。

<!-- js-console -->
```js
const cinephoto = ['satuki', 'ann'];
cinephoto.push('sakurako'); // 配列に破壊的に値を追加可能
console.log(cinephoto); // 'satuki', 'ann', 'sakurako'
```

オブジェクトの場合はフィールドに対しての再代入が可能です。

<!-- js-console -->
```js
const japan = { capital: '東京' };
japan.capital = '山梨';  // フィールドには再代入が可能
console.log(`日本の首都は${japan.capital}`);
```

なおあくまでこれはJavaScriptの話であり、TypeScriptでは型を工夫することでこれらの破壊的な代入を防ぐことが可能です。

