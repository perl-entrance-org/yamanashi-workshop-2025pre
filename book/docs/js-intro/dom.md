# DOM入門

ここでちょっとブラウザの世界に戻ってきましょう。

ブラウザがHTMLを表示する際、ブラウザはHTMLを読み込んだあとにどのようにページとして表示しているのでしょうか。
ブラウザはHTMLを読み込むと、その要素をDOM(Document Object Model)と呼ばれるデータ構造に変換します。

例えば次のようなHTMLはDOMとして解釈されると図のような構造になります。

```html
<html>
    <head>
        <title>HTMLページの例</title>
        <script src="./script.js"></script>
    </head>
    <body>
        <h1>見出しだよ~~</h1>
        <div>
            <p>ここにこんな感じでテキストを書く</p>
        </div>
        <ul>
            <li>箇条書き1</li>
            <li>箇条書き2</li>
            <li>箇条書き3</li>
        </ul>
    </body>
</html>
```

<img src="./dom.png">

この構造は一番上が`<html>`タグで、そこから`<head>`と`<body>`に枝が別れています。
このようなある一点から開始し、枝分かれしていく構造のことを、木を逆さまにしたような構造に見えることから「木構造」と言います。

ブラウザは実際はHTMLの内容をそのまま表示しているのではなく、内部的に変換したDOMに基づいて表示を行っています。
DOM上では各タグのことを「Element(エレメント)」と呼び、各エレメントの中の文字などの要素を「Node」と呼びます。
上のHTMLでは各文章の内容などがNodeとして管理され、タグ自体はElementとして管理されます。

# JavaScriptとDOM

JavaScriptはブラウザで動くことからなんとなく想像できるかもしれませんが、DOMを操作することが可能です。
(ただし標準でDOMが操作できるのはあくまでもブラウザ上のJavaScriptで、Node.jsの場合はライブラリのインストールが必要)

```html
<html lang="ja">
    <head>
        <title>サンプルページです</title>
    </head>
    <body>
        <h1>みだしだよ〜〜</h1>
        <script>
            const hello = document.createElement('p');
            hello.textContent = 'JavaScriptで追加したよ〜〜';
            document.body.appendChild(hello);
        </script>
    </body>
</html>
```

上のhtmlを保存して表示すると、HTMLとしては書いていないはずの`<p`>タグと文章が管理者ツールから見ると表示されています。
これはJavaScript実行時にDOMを操作して、`<p>`タグのElementをBodyの末尾に挿入したということです。

# idを使った

<!DOCTYPE html>
<html lang="ja">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <ol>
        <li>mono</li>
        <li>ゆるキャン△</li>
    </ol>
</body>
</html>
