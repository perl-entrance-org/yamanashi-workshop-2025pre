# 配列

JavaScriptに限らずプログラミング言語では、複数の値をまとめて扱うためのデータ構造として「配列」があります。

### 配列の宣言と初期化
配列は`[]`を使って宣言します。

<!-- js-console -->
```js
const fruits = ['apple', 'banana', 'orange'];
console.log(fruits); // ['apple', 'banana', 'orange']
```
### 配列の要素へのアクセス
配列の要素には、インデックスを使ってアクセスします。
おおよそのプログラミング言語と同じくインデックスは0から始まります。


<!-- js-console -->
```js
const fruits = ['apple', 'banana', 'orange'];
console.log(fruits[0]); // 'apple'
console.log(fruits[1]); // 'banana'
```

存在しないインデックスにアクセスすると`undefined`が返されます。

<!-- js-console -->
```js
const fruits = ['apple', 'banana', 'orange'];
console.log(fruits[3]); // undefined
```


### 配列の要素の追加と削除
配列に要素を追加するには、`push`メソッドを使います。

<!-- js-console -->
```js
const fruits = ['apple', 'banana'];
fruits.push('orange'); // 'orange'を追加
console.log(fruits); // ['apple', 'banana', 'orange']
```

配列の要素を削除するには、`pop`メソッドを使います。

<!-- js-console -->
```js
const fruits = ['apple', 'banana', 'orange'];
fruits.pop(); // 最後の要素を削除
console.log(fruits); // ['apple', 'banana']
```

逆に、先頭に要素を追加するには`unshift`メソッドを使い、先頭の要素を削除するには`shift`メソッドを使います。

<!-- js-console -->
```js
const fruits = ['banana', 'orange'];
fruits.unshift('apple'); // 'apple'を先頭に追加
console.log(fruits); // ['apple', 'banana', 'orange']
fruits.shift(); // 先頭の要素を削除
console.log(fruits); // ['banana', 'orange']
```

### 配列の長さ
配列の長さは、`length`プロパティを使って取得できます。
<!-- js-console -->
```js
const fruits = ['apple', 'banana', 'orange'];
console.log(fruits.length); // 3
```


## constとオブジェクト

`const`はあくまで変数の再代入を禁止する宣言であり、定数の宣言とは異なります。
したがってオブジェクトや配列を宣言した場合は破壊的に値を書き換えることが可能です。

<!-- js-console -->
```js
const cinephoto = ['satuki', 'ann'];
cinephoto.push('sakurako'); // 配列に破壊的に値を追加可能
console.log(cinephoto); // 'satuki', 'ann', 'sakurako'
```


### 配列のループ処理
配列の要素を順番に処理するには、繰り返し処理(ループ)構文を使うと便利です。
特に配列の中身を表示させる場合は、`for-of`ループが便利です。

`for-of`ループは次のように書きます。

```js
for (const ループごとの要素 of 配列名) {
    // elementに配列の要素が順番に代入される
}
```

習うより慣れろということで、実際に配列の要素を表示してみましょう。

<!-- js-console -->
```js
const fruits = ['apple', 'banana', 'orange'];
for (const fruit of fruits) {
    console.log(fruit);
}
```


## 練習問題

配列を使って、次のようなデータを作成してみましょう。

- 山梨県の市町村名を3つ以上含む配列
- 山梨県の有名な観光地を3つ以上含む配列

作成した配列の要素をループ文で表示してみましょう。

<!-- js-console -->
```js
const ...
```