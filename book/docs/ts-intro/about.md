# TypeScript入門

今まではJavaScriptの話をしてきましたが、TypeScriptについても触れていきます。

# TypeScriptとは
TypeScriptはJavaScriptのスーパーセットであり、JavaScriptに型システムを追加した言語です。TypeScriptはJavaScriptの上位互換であり、JavaScriptのコードはそのままTypeScriptとしても有効です。
TypeScriptはJavaScriptのコードに型注釈を追加することで、コードの可読性や保守性を向上させることができます。また、TypeScriptはコンパイル時に型チェックを行うため、実行時のエラーを減らすことができます。

TypeScriptはMicrosoftによって開発され、2012年に初めてリリースされました。現在では多くの企業やプロジェクトで採用されており、JavaScriptの代替として広く利用されています。

# TypeScriptの特徴
TypeScriptの主な特徴は以下の通りです。
- **型システム**: TypeScriptは静的型付け言語であり、変数や関数の引数、戻り値に型を指定できます。これにより、コードの意図を明確にし、エラーを早期に発見できます。
- **型推論**: TypeScriptは型推論を行い、明示的に型を指定しなくても多くのケースで型を自動的に推測します。これにより、コードが簡潔になります。
- **インターフェースとクラス**: TypeScriptはオブジェクト指向プログラミングの概念をサポートしており、インターフェースやクラスを使用してコードを構造化できます。
- **モジュールシステム**: TypeScriptはES6のモジュールシステムをサポートしており、コードをモジュール化して再利用性を高めることができます。
- **JavaScriptとの互換性**: TypeScriptはJavaScriptのスーパーセットであり、既存のJavaScriptコードをそのままTypeScriptとして使用できます。これにより、既存のプロジェクトにTypeScriptを導入しやすくなっています。
- **コンパイル時の型チェック**: TypeScriptはコンパイル時に型チェックを行い、型エラーを検出します。これにより、実行時のエラーを減らし、コードの信頼性を向上させます。

他のAltJSと比較して、TypeScriptは限りなくJavaScriptに近い言語であるため、 JavaScriptの知識がそのまま利用できるのが大きな特徴です。


# こういうときに便利

例えば次のようなJavaScriptのコードがあるとします。
これは2つの値を足す関数ですが、`2`が文字列であるため、JavaScriptでは文字列の連結が行われてしまいます。


<!-- js-console -->
```js
function add(left, right) {
    return left + right;
}

console.log(add(1, "2"));
```

TypeScriptでは、関数の引数に型を指定することができます。

```typescript
function 関数名(引数: 型): 返り値の型{
    ...
}
```

今回の例では`left`と`right`は数値型であることを指定し、返り値も数値型であることを明示します。

このコードをTypeScriptで書くと、次のように型を指定することができます。

```typescript
function add(left: number, right: number): number {
    return left + right;
}
console.log(add(1, "2")); // エラー: Argument of type 'string' is not assignable to parameter of type 'number'.
```

# 練習問題

https://www.typescriptlang.org/play/ で以下のコードを貼り付けてTypeScriptではどうなるかを確認してみましょう。

<!-- js-console -->
```js
function add(left, right) {
    return left + right;
}
console.log(add(1, 2, 3)); 
```

```typescript
function add(left: number, right: number): number {
    return left + right;
}
console.log(add(1, 2, 3)); 
```

## 配列の保護

TypeScriptでは、配列の型を指定することができます。

```typescript
const 配列名: それぞれの型[] = [...];
```

さらに`readonly`をつけることで、配列を変更できないようにすることもできます。

```typescript
const animations : readonly string[] = ['mono', 'ゆるキャン'];
animations.push('ラブライブサンシャイン'); // エラーになる
```
