# vite入門

今まではHTMLファイルに1つのJavaScriptファイルを読み込んでいましたが、実際の開発では複数のJavaScriptファイルを使うことが多いです。
このような場合、JavaScript内で他のJavaScriptファイルを読み込む必要があります。 
しかし、JavaScriptを複数読み込むにしてもブラウザからそれぞれのJavaScriptファイルを取得するには、HTTPリクエストを行う必要があります。
そのため、JavaScriptの読み込みが多くなると、HTTPリクエストの数が増えてしまい、ページの表示速度が遅くなってしまいます。

また、今まではJavaScriptのコードを書いて確認するために、都度ブラウザをリロードしていました。
これも開発の効率を下げてしまいます。

これらの問題を解決するために、**Vite**というツールを使います。
Viteは、JavaScriptの開発を効率化するためのツールで、以下のような機能を提供します。

- モジュールバンドリング: 複数のJavaScriptファイルを1つのファイルにまとめて、HTTPリクエストの数を減らすことができます。
- ビルド: 本番環境でスムーズに配信できるように、最適化されたJavaScriptファイルを生成することができます。
- ホットリロード: JavaScriptのコードを変更した際に、ブラウザをリロードせずに変更を反映することができます。
- 開発サーバー: ローカルで開発を行うためのサーバーを立ち上げることができます。

似たツールにWebpackなどがありますが、Viteは特に高速なのが特徴で、最近のWeb開発では非常に人気があります。

# npm

npmとはNode Package Managerの略で、2種類の意味があります

- 世界中の様々な人が開発した便利にプログラミングをすすめられる「パッケージ」を管理するシステム
- そのパッケージをダウンロードするコマンド

前者の方はJavaScriptの世界におけるGooglePlayStoreやAppleStoreのようなものだと思えば理解しやすいでしょうか。
jQueryやVite, Reactなどの今の開発には欠かせないツールや、Webサイトにコナミコマンドを構築するようなジョークに近いモジュールまで様々なものが存在します。

そのアプリストアからモジュールをダウンロードする際には`npm`という専用コマンドを利用します。
npmはNode.jsに付随する形でリリースされています。

似たツールに`yarn`, `pnpm`が存在します。
かつては`yarn`が高速などの理由で人気でしたが、現代においては`npm`も高速化していたり、yarnがバージョンごとで挙動が異なっていたりと、あまり`yarn`を選択する理由はありません。
筆者は`pnpm`が個人的に好きですが、ここではデファクトスタンダードの`npm`を利用します。


# viteでプロジェクトをつくろう

```bash
$ npm create vite@latest
```


```
> npx
> create-vite

│
◇  Project name:
│  js-vite
│
◆  Select a framework:
│  ● Vanilla
│  ○ Vue
│  ○ React
│  ○ Preact
│  ○ Lit
│  ○ Svelte
│  ○ Solid
│  ○ Qwik
│  ○ Angular
│  ○ Marko
│  ○ Others
└
```

次のような画面が現れたら、矢印キーの上下でVanillaに印を合わせてエンターを押しましょう。
Vanillaとはシンプルなバニラソフトクリームのように、他のライブラリを使わないシンプルな構成のことを言います。



srcディレクトリの下に`counter.js`があります。見てみましょう。

```javascript
export function setupCounter(element) {
  let counter = 0
  const setCounter = (count) => {
    counter = count
    element.innerHTML = `count is ${counter}`
  }
  element.addEventListener('click', () => setCounter(counter + 1))
  setCounter(0)
}
```

これは`element`を引数で取得し、その`element`に`addEventListener`しています。
`addEventListener`とは、そのelementに対するイベント(ユーザーがなんらかの操作をした際に発生するもの)と、イベント時に実行する関数を設定できるものです。

ここではクリック時に`setCounter`関数を`counter + 1`の結果を引数として渡しています。

## 練習問題

ここではボタンをクリックすると表示内容が変わるプログラムを作ってみます。

main.jsの中身を次のようにしましょう

```javascript
import './style.css'
import javascriptLogo from './javascript.svg'
import viteLogo from '/vite.svg'
import { setupCounter, setupMyTitle } from './counter.js'

document.querySelector('#app').innerHTML = `
  <div>
    <a href="https://vite.dev" target="_blank">
      <img src="${viteLogo}" class="logo" alt="Vite logo" />
    </a>
    <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript" target="_blank">
      <img src="${javascriptLogo}" class="logo vanilla" alt="JavaScript logo" />
    </a>
    <h1>Hello Vite!</h1>
    <div class="card">
      <button id="counter" type="button"></button>
    </div>
    <div class="card">
      <button id="mono" type="button">mono</button>
      <button id="yurucamp" type="button">ゆるキャン</button>
      <p id="title"></title>
    </div>
    <p class="read-the-docs">
      Click on the Vite logo to learn more
    </p>
  </div>
`

setupCounter(document.querySelector('#counter'))
setupMyTitle(document.querySelector('#mono'), document.querySelector('#yurucamp'), document.querySelector('#title'))
```

次にcounter.jsの中身を次のようにしましょう。

```js
export function setupCounter(element) {
  let counter = 0
  const setCounter = (count) => {
    counter = count
    element.innerHTML = `count is ${counter}`
  }
  element.addEventListener('click', () => setCounter(counter + 1))
  setCounter(0)
}

export function setupMyTitle(monoElement, yuruElement, htmlResultValue) {
  let counter = 0
  const setMono = () => {
    htmlResultValue.innerHTML = `mono`
  }

  const setYuru = () => {
    htmlResultValue.innerHTML = `ゆるキャン`
  }

  monoElement.addEventListener('click', () => setMono())
  yuruElement.addEventListener('click', () => setYuru())
  htmlResultValue.innerHTML = `未設定`
}
```

1. ボタンをクリックするとどのような表示になるか確認しましょう
1. 新しく「スーパーカブ」に変化するボタンを作ってみましょう
