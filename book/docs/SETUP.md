# Node.jsの環境構築

環境構築をやっていきます。わかっている方やこだわりがある方はよしなにやっていただいて大丈夫です。
~~たとえばNixを使って構築するとか~~

## Windows

- WSL2をubuntuする
- nvm-windowsでもいいんじゃないか感はある

## macOS/Windows共通編

### Node.jsとv8
![](https://nodejs.org/static/logos/nodejsDark.svg)

ローカルでJavaScriptを動作させるには、JavaScriptのサーバー用途の実行環境、あるいはWebブラウザが必要となります。
Webブラウザで試すこともできますが、本格的なプログラミングを行う場合はローカルにサーバー向けの実行環境を用意するのがやりやすいです。
JavaScriptのサーバー用途の実行環境にはNodejs, Deno, Bunなどがありますが、ここではデファクトスタンダードであるNode.jsを使います。

<img src="https://v8.dev/_img/v8.svg" alt="ロゴの説明" width="150" />

Node.jsはV8というGoogleが開発したJavaScriptエンジンを使ってJavaScriptを実行するための環境です。
V8はGoogle ChromeやChromiumなどのWebブラウザでも使われているJavaScriptエンジンで、非常に高速にJavaScriptを実行することができます。
Node.jsはサーバーサイドのJavaScriptを実行するための環境であり、Webアプリケーションの開発や、CLIツールの開発などに広く使われています。
そのためブラウザで動くJavaScriptと違い、 HTMLを操作するDOM APIなどのWeb APIがなく、代わりにファイルシステムを操作したり、 HTTPサーバーを立てたりするためのAPIが提供されています。

ちなみにV8はあのV8由来です。 ~~V8を讃えよ~~

### mise
実際の開発ではNode.jsもプロジェクトによって様々なバージョンを利用することが多いです。
すなわち複数のNode.jsを切り替えて利用することが実際の現場では多いです。
またNode.jsはOSが使っていることは稀ですが、 PythonやPerlなどのスクリプト言語はOSの一部として動作している環境と開発で利用する環境を分けて利用したいというケースが多いです。

このような複数のバージョンの処理系を管理し使うためのツールとしてNode.jsの場合[nvm](https://github.com/nvm-sh/nvm)や[nodenv](https://github.com/nodenv/nodenv)などのバージョン管理ツールが存在しますが、ここでは[mise](https://mise.jdx.dev/)というツールを使用します。

mise(ミーズ)とは開発に必要な様々なものを一元管理してくれるツールです。
言語のバージョン管理や、よく使われる周辺ツール、タスクの管理まですることが出来ます。
asdfというツールを参考にRustという言語で実装されており、非常に高速に動作することがウリです。

### macOS

```bash
$ brew install mise
```

### Ubuntu

```bash
$ curl https://mise.run | sh
```


```bash
$ mise use -g node@22
```

