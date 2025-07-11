# JavaScritpのオブジェクトとは

JavaScriptではプリミティブな型以外のデータはオブジェクトでした。
ここではオブジェクトがどんなものか見ていきます。

JavaScriptのオブジェクトとは**プロパティの集まり**のことであり、プロパティは**名前(key)と値(value)の組**の概念です。
これは他の言語で言うところの連想配列、ハッシュ、辞書などと呼ばれるものと近いです。(連想配列として使うとちょっと微妙なので、あくまで近いもの、として理解しましょう)

## オブジェクトを作成する

オブジェクトを作成するにはオブジェクトリテラル(`{}`)を使います。

```js
const obj = {};
```

オブジェクトリテラルでは、初期値を設定できます。
プロパティは`:`でキーと値を区切って記述します。

<!-- js-console -->
```js
const obj = {
    "key": "value", // キー : 値
};
console.log(obj);
```

プロパティ名は`'`や`"`などのクォートを省略することができます。

<!-- js-console -->
```js
const obj = {
    key: "value", // キー : 値
};
console.log(obj);
```

valueを省略するとエラーになります。

<!-- js-console -->
```js
const obj = {
    key: 
};
console.log(obj);
```

また、複数のプロパティを持つオブジェクトも作成できます。
複数作る場合はプロパティの宣言の最後に`,`をいれて区切ります。

<!-- js-console -->
```js
const obj = {
    yamanashi: '甲府',
    nagano: '松本',
    okinawa: '那覇',
};
console.log(obj);
```

オブジェクトを`conosle.log`すると中身がすべて表示されてしまいます。
あるkeyに対応するvalueのみにアクセスしたい場合は`オブジェクト.キー`のように書きます。

<!-- js-console -->
```js
const obj = {
    yamanashi: '甲府',
    nagano: '松本',
    okinawa: '那覇',
};
console.log(obj.yamanashi);
```

式なので`console.log`以外にも変数代入時の右辺としても使えます。

<!-- js-console -->
```js
const obj = {
    yamanashi: '甲府',
    nagano: '松本',
    okinawa: '那覇',
};

const koko = obj.yamanashi;
console.log(koko);
```

value に変数を設定することもできます。

<!-- js-console -->
```js
const food = 'とりもつ';

const obj = {
    yamanashi: food,
};

console.log(obj);
```

また、キーの名前と変数名が一致している場合は`:`を省略できます。

<!-- js-console -->
```js
const yamanashi = 'とりもつ';

const obj = {
    yamanashi,
};

console.log(obj);
```



### 練習問題


- `object_practice`というディレクトリを作りましょう
- 次のソースコードをコピペし、それぞれ保存してください、

`example.html`

```html
<!DOCTYPE html>
<html lang="ja">
    <head>
        <title>オブジェクトのテスト</title>
        <script src="./script.js"></script>
    </head>
    <body>
        コンソールをひらいてね!
    </body>
</html>
```

`script.js`
```javascript
// ここになんかかく
```

- 以下の値の組を持つオブジェクト`haruno`を作りましょう
    - key: `car`, value: `pao`
    - key: `pet`, value: `cat`
- まずは`haruno`の中身をすべて`console.log`で表示してみましょう
- 次に`haruno`オブジェクトの`pet`valueだけ`console.log`で表示してみましょう


## constとオブジェクト

`const`はあくまで変数の再代入を禁止する宣言であり、定数の宣言とは異なります。
したがってオブジェクトを破壊的に値を書き換えることが可能です。


オブジェクトの場合はフィールドに対しての再代入が可能です。

<!-- js-console -->
```js
const japan = { capital: '東京' };
japan.capital = '山梨';  // フィールドには再代入が可能
console.log(`日本の首都は${japan.capital}`);
```

なおあくまでこれはJavaScriptの話であり、TypeScriptでは型を工夫することでこれらの破壊的な代入を防ぐことが可能です。

