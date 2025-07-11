# データ型

これまで文字列や数値などのデータを扱ってきました。
これらのデータの種類のことを「データ型」と言います。

JavaScriptは動的型付け言語であるので、一度別のデータ型を代入した変数に再度別のデータ型の変数を代入する、みたいなことができます。
```js
let foo = 42; // foo は数値型になった
foo = "bar"; // foo は文字列型になった
foo = true; // foo は論理型になった
```

また、型が違う変数同士で計算をした場合、処理系がいい感じに型を変換してしまう性質があります。
これを弱い型付け、などと言ったりすることもあります。
反対に強い型付けの言語では、いい感じに変換はしてくれず、エラーになります。

<!-- js-console -->
```js
const foo = 42; // 数値
const result = foo + "1"; // 数値 + 文字列
console.log(result);
```


JavaScriptが持つデータの型は全部で7種類の基本となる型(プリミティブ型)とオブジェクトから成り立っています。


## 数値型 (Number)

数値型はこれまでやってきた数値を表す型のことです。負の数や小数点も表せます。

<!-- js-console -->
```js
console.log(10);
console.log(0);
console.log(0.5);
console.log(-1000);
```

## 文字列

`'`や`"`, `\``で囲われた文字列のことです

<!-- js-console -->
```js
"ABC";
```


## BigInt
コンピュータ特有の問題でNumberで表現できない大きな数値を扱う型のことです。
たまにでかい数値を使うときに思い出すくらいで良いです。


## null

`null`とは値が存在していないことを示す値のことです。
意図的に「この変数にはデータが含まれてませんよ」ということを示すために使います。

<!-- js-console -->
```js
const data = null;
console.log(data);
```


## undefined

値が設定されていないことを示すデータ型です。
意図的に「この変数はまだ値を設定していませんよ」ということを示すために使います。

また、`let`で変数を宣言した際に初期値を設定していないと`undefined`になります。

<!-- js-console -->
```js
let bar;
console.log(bar);

const undef = undefined;
console.log(undef);
```

概念としてはこんな感じです。
<img src="https://qph.cf2.quoracdn.net/main-qimg-65c92e6ab76ce796d2f7343a2b324185" >

## 真偽値 (Boolean)

真か偽か、trueかfalseか、onかoffかを示す型です。

<!-- js-console -->
```js
console.log(true);

console.log(false);
```

## シンボル

基本的に我々がつかうことはない....


# nullとundefined

nullとundefinedは共に「値がない」を示すデータ型です。使い分けがよくわかんないですよね。
一般的には次のように言われています。

> undefinedは「値が代入されていないため、値がない」、nullは「代入すべき値が存在しないため、値がない」

とはいえ現実問題としてこの通りになっているかというとそうではなく、わりと入り乱れて利用されています。
実際プログラミングする上では**ほぼほぼ`undefined`を使っていれば間違いない**です。


{% hint style='info' %}
実際はJavaScriptの仕様を制定している団体の兼ね合いでECMAScriptではundefinedが使われがちであったり、 Web API関連ではnullが使われがちであったりします。
https://susisu.hatenablog.com/entry/2024/09/07/213747
{% endhint %}