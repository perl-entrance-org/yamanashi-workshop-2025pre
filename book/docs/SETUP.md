# Node.jsの環境構築

## Windows

- WSL2をubuntuする
- nvm-windowsでもいいんじゃないか感はある

## macOS/Windows共通編

### Node.js
ローカルでJavaScriptを動作させるには、JavaScriptのサーバー用途の実行環境、あるいはWebブラウザが必要となります。
Webブラウザで試すこともできますが、本格的なプログラミングを行う場合はローカルにサーバー向けの実行環境を用意するのがやりやすいです。
JavaScriptのサーバー用途の実行環境にはNodejs, Deno, Bunなどがありますが、ここではデファクトスタンダードであるNode.jsを使います。

Node.jsはV8というGoogleが開発したJavaScriptエンジンを使ってJavaScriptを実行するための環境です。
V8はGoogle ChromeやChromiumなどのWebブラウザでも使われているJavaScriptエンジンで、非常に高速にJavaScriptを実行することができます。
Node.jsはサーバーサイドのJavaScriptを実行するための環境であり、Webアプリケーションの開発や、CLIツールの開発などに広く使われています。

### mise
実際の開発ではNode.jsもプロジェクトによって様々なバージョンを利用することが多いです。
すなわち複数のNode.jsを切り替えて利用することが実際の現場では多いです。
またNode.jsはOSが使っていることは稀ですが、 PythonやPerlなどのスクリプト言語はOSの一部として動作している環境と開発で利用する環境を分けて利用したいというケースが多いです。

このような複数のバージョンの処理系を管理し使うためのツールとしてNode.jsの場合[nvm](https://github.com/nvm-sh/nvm)や[nodenv](https://github.com/nodenv/nodenv)などのバージョン管理ツールが存在しますが、ここでは[mise](https://mise.jdx.dev/)というツールを使用します。

```bash
$ mise use -g node@lts
```