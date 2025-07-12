# 関数入門

ここではJavaScriptの関数について学びます。関数は、コードを再利用可能なブロックに分割するための重要な要素です。

# 関数とは
関数は、特定のタスクを実行するためのコードの集まりです。
関数を定義することで、同じコードを何度も書く必要がなくなり、コードの可読性と保守性が向上します。
実はこれまで利用してきた`console.log`も`console`オブジェクトの`log`関数を呼び出していました。

保守性と可読性についてちょっと見てみましょう。

## コードの再利用

例えば、あるお買い物サイトを開発していると考えましょう。
そのサイトはデザイン上で商品の代金は常に税別で表示しています。

- 信玄餅: 300円
- 栗せんべい: 200円
- 紅梅: 100円

これらを購入する際はレシートとしてそれぞれの税込み金額を表示する必要があります。

<!-- js-console -->
```js
const shingenmochi = 300;
const senbei = 200;
const koubai = 100;

console.log(`信玄餅は ${shingenmochi * 1.08}`);
console.log(`栗せんべいは ${senbei * 1.08}`);
console.log(`紅梅は ${koubai * 1.08}`);
```

これくらいならまぁそれぞれで計算してもいいような気もしますが、以下のような問題があります。

- 毎回同じ計算をしており重複している
    - なにかの拍子に一箇所だけ1.5とかをかけてしまった場合、間違い探しが発生する
- 突然税率が代わったときに数値を全部変更しなくてはならず面倒
    - 例えば税率ではない意味で1.08をかけていたりすると最悪...

## 詳細な実装の隠蔽
例えば自動販売機で飲み物を買うことを考えてみます。

1. お金を入れる
1. ボタンを押す
1. ジュースが出てくる
1. おつりを受け取る

という一連の作業があります。

これを「ジュースを買う()」という一つの関数だと考えてみましょう。

1. あなた: 「コーラが飲みたいな。150円玉を入れよう。」
1. 関数（自販機）を呼び出す: `ジュースを買う(150円, "コーラ")`
1. 関数内の処理: 自販機が中でごにょごにょ動きます。
1. 結果: ガコン！とコーラが出てきます。これが結果です。

もしコーヒーが120円で売られている自動販売機だとしたら、なんとなく`ジュースを買う(120円, "コーヒー")`とするとコーヒーが買えそうな気もします。

このように、私たちは中の複雑な仕組みを知らなくても、「お金」と「欲しいものの名前」を渡すだけで、簡単に「ジュース」という結果を得られます。
また、同じ行為(飲み物を買う)場合でも、金額や対象が異なっても動作するように外から値(お金や飲み物の種類)を与えることができます。

関数を使うとこのように、コードの再利用性を高めたり、詳細な実装を考えずにロジックに集中することができます。


## 関数の定義
関数はJavaScriptでは`function`を利用することで定義できます。
`function`を使って関数を書くことを「関数定義」とか「関数宣言」のような言い方をします。

先程の自動販売機で言う「飲み物の種類」や「お金」のような「関数に渡したい値」を「引数(ひきすう)」と呼びます。
引数は複数指定することが可能で、`,`で区切って書きます。

```javascript
function 関数名(引数1, 引数2) {
    // 関数の処理
    return;
}


const 関数の結果 = 関数名();
```

JavaScriptでは関数は`function 関数名(引数)`と書くことで宣言できます。
実際にしたい処理は`{}`の中で書きます。

引数を必要としない場合は`()`の中身は省略できます。

```javascript
function 関数名(){
    ...
}
```

例えば先程の自動販売機だと次のようになります。

```js
function 購入する(商品名, 投入金額){
    なんやかんやして購入する処理;
}
```


## 関数の呼び出し
関数を呼び出すには次のように、関数名の後ろに`()`をつけて呼び出します。

```javascript
関数名();
```

<!-- js-console -->
```javascript
function say_hello() {
    console.log("Hello!!");
}

say_hello();
```

引数がある場合は次のようになります。

```javascript
関数名(引数1, 引数2);
```

<!-- js-console -->
```javascript
function show_price(kind, money) {
    console.log(`${kind}は税込み${ money * 1.1}円です`);
}

show_price('コーヒー', 120);
```


## 引数と返り値
関数は引数を受け取り、処理を行った結果を値として返すことができます。
この値のことを「返り値」あるいは「戻り値」と呼びます。
返り値は`return`の後に値を書きます。

引数は関数に渡すデータで、返り値は関数の処理結果です。

<!-- js-console -->
```javascript
function add(left, right) {
    return left  + right; 
}
const result = add(5, 3); // resultは8になる
console.log(result); // 8 と表示される
```

この例は返り値を使わずにこのように関数内で`console.log`すればいいのではないか。と思われるかもしれません。

<!-- js-console -->
```javascript
function add(left, right) {
    console.log(left  + right); 
}
const result = add(5, 3); 
console.log(result); 
```

たしかにコンソールをに結果を表示する、ということはできているのですが、計算結果を関数を呼び出した側で再利用することができません。
また、`add`という名前からすると純粋に足し算だけやりそうな関数ですが、実際はコンソールに結果を表示しており、ややびっくりする挙動になっています。

このように関数が画面に出力したり、別の値を変更したりすることを、期待した動作以外の動作ということで「副作用」と呼びます。
基本的に副作用が起きるようなプログラミングは避けたほうがよいとされています。


また、`return`すると以降の処理が打ち切られます。

<!-- js-console -->
```javascript
function add(left, right) {
    return left  + right; 
    console.log("returnしているから実行されないよ");
}

const result = add(5, 3); // resultは8になる
console.log(result); // 8 と表示される
```


# 関数のスコープ
関数内で定義された変数は、その関数の外からは参照できません。
これはスコープといい、変数の有効範囲が決められいるためです。
関数のスコープは`{}`の中が該当します。


<!-- js-console -->
```javascript
function example() {
    const localVar = "I am local"; // この変数はexample関数内でのみ有効
    console.log(localVar);
}
example(); // "I am local" と表示される
console.log(localVar); 
```

同じ名前の変数を宣言していた場合、スコープによって値が保存されます。

<!-- js-console -->
```javascript
const x = "outer";

function example() {
    const x = "in function";
    console.log(x);
}
example(); 
console.log(x); 
```


# 関数の引数のデフォルト値
関数の引数にはデフォルト値を設定することができます。これにより、引数が渡されなかった場合でも、予期しないエラーを防ぐことができます。

<!-- js-console -->
```javascript
function greet(name = "Guest") {
    console.log(`Hello, ${name}!`);
}
greet(); // "Hello, Guest!" と表示される
greet("Bob"); // "Hello, Bob!" と表示される
```

# 関数式

JavaScriptでは、関数を変数に代入することもできます。これを関数式と呼びます。
この定義を見ると右側の`function`の部分が関数名を持たないことに気づくかもしれません。
関数名を持たない関数は「無名関数」と呼ばれ、変数に代入したり、他の関数の引数として渡すことができます。


```js
const 変数名 = function() {
    // 関数の処理...
    return 返り値;
};
```

<!-- js-console -->
```js
const add = function(a, b) {
    return a + b; // 関数の処理
};
const result = add(5, 3); // resultは8になる
console.log(result);

const double = function(x) {
    return x * 2; // 引数を2倍にする関数
};

console.log(double(add(5,3)));
```


# アロー関数式
アロー関数は、JavaScriptの関数をより簡潔に書くための導入された構文です。
`function`での関数定義より後に作られたため、(今回は説明しませんでしたが)`function`特有の罠をいくつか回避した実装になっています。

アロー関数は、アロー(矢印)の名前の通り`=>`を使った定義になります。


<!-- js-console -->
```javascript
const add = (a, b) => a + b; // アロー関数の定義
const result = add(5, 3); // resultは8になる
console.log(result); // 8 と表示される
```

また、引数が1つだけの場合は、括弧を省略することもできます。

<!-- js-console -->
```javascript
const square = x =>  { return x * x; } // 引数が1つのアロー関数
let squared = square(4); // squaredは16になる
console.log(squared); // 16 と表示される
```

さらに複数行の処理を行わない場合は、波括弧を省略することもできます。

<!-- js-console -->
```javascript
const greet = name => `Hello, ${name}!`; // 波括弧を省略したアロー関数
console.log(greet("Sakurako"));
```

# functionとアロー関数の使い分け
アロー関数の方が後発かつ`function｀と書かなくてよいので、アロー関数を好んで使う人もいます。

ただしアロー関数の場合、functionと違い定義より前に呼び出すことができません。

<!-- js-console -->
```javascript 
console.log(add(5, 3)); // エラーにならない
function add(a, b) {
    return a + b; // 関数の処理
}
```

<!-- js-console -->
```javascript 
console.log(add(5, 3)); // エラーになる
const add = (a, b) => a + b; // アロー関数の定義
```


<!-- js-console -->
```javascript 
const add = (a, b) => a + b; // アロー関数の定義
console.log(add(5, 3)); // エラーになる
```

