# Node.jsの環境構築

環境構築をやっていきます。わかっている方やこだわりがある方はよしなにやっていただいて大丈夫です。
~~たとえばNixを使って構築するとか~~

## Windows

Windowsの方はWSL2上に環境を構築していきます。
まずはWSL2のセットアップから始めましょう。

[マイクロソフト公式のドキュメント](https://learn.microsoft.com/ja-jp/windows/wsl/install)

インストールするLinuxはデフォルトであるUbuntuがオススメです。


### Node.jsとv8
![](https://nodejs.org/static/logos/nodejsDark.svg)

ローカルでJavaScriptを動作させるには、JavaScriptのサーバー用途の実行環境、あるいはWebブラウザが必要となります。
Webブラウザで試すこともできますが、本格的なプログラミングを行う場合はローカルにサーバー向けの実行環境を用意するのがやりやすいです。
JavaScriptのサーバー用途の実行環境にはNode.js, Deno, Bunなどがありますが、ここではデファクトスタンダードであるNode.jsを使います。

<img src="https://v8.dev/_img/v8.svg" alt="ロゴの説明" width="150" />

Node.jsはV8というGoogleが開発したJavaScriptエンジン(JavaScriptを実際に解釈するもの)を使ってJavaScriptを実行するための環境です。
V8はGoogle ChromeやChromiumなどのWebブラウザでも使われているJavaScriptエンジンで、非常に高速にJavaScriptを実行することができます。
Node.jsはサーバーサイドのJavaScriptを実行するための環境であり、Webアプリケーションの開発や、CLIツールの開発などに広く使われています。
そのためブラウザで動くJavaScriptと違い、 HTMLを操作するDOM APIなどのWeb APIがなく、代わりにファイルシステムを操作したり、 HTTPサーバーを立てたりするためのAPIが提供されています。

ちなみにV8はあのV8由来です。 ~~V8を讃えよ~~

Node.jsには様々なバージョンがありますが、大きく分けてLTS (Long-Term Support)版と最新版、それ以外のバージョンの3つです。
LTS版はリリース後2年間のメンテナンスとサポートをするバージョンです。
最新版は最新のNode.jsの機能を試せますが、次に新しいバージョンがリリースされるとメンテナンスされなくなります。
それ以外のバージョンは基本的にメンテナンスされていないので、可及的速やかに新しいバージョンにアップグレードする必要があります。

業務ではセキュリティ対策なども重要なので、理由がなければLTS版を利用しましょう。
個人の趣味の開発では、最新のNode.jsの動向を追うために、常に最新バージョンを利用する。という人もいます。

### mise
実際の開発ではNode.jsもプロジェクトによって使われているバージョンはバラバラです。
これらのプロジェクトを1つのマシンで開発するので、複数のNode.jsを切り替えて利用することが実際の現場では多いです。
またNode.jsはOSが使っていることは稀ですが、 PythonやPerlなどのスクリプト言語はOSの一部として動作している環境と開発で利用する環境を分けて利用したいというケースもあります。

このような複数のバージョンの処理系を管理し使うためのツールとしてNode.jsの場合[nvm](https://github.com/nvm-sh/nvm)や[nodenv](https://github.com/nodenv/nodenv)などのバージョン管理ツールが存在しますが、ここでは[mise](https://mise.jdx.dev/)というツールを使用します。

mise(ミーズ)とは開発に必要な様々なものを一元管理してくれるツールです。
言語のバージョン管理や、よく使われる周辺ツール、タスクの管理まですることが出来ます。
asdfというツールを参考にRustという言語で実装されており、非常に高速に動作することがウリです。


### コマンドの表記について

コマンドの表記は以下のようにします。

```bash
$ 実際に入力するコマンド
```

`$`は一般ユーザーのコマンドラインのプロンプト(今は入力できますよというマーク)を表しており、実際には入力しません。
したがって次のような表記があった場合、ターミナルには`ls`と入力してください。

```bash
$ ls
```

このハンズオンでは出てきませんが、`#`から始まった場合、rootユーザーのコマンドラインのプロンプトを表しています。

### macOS

```bash
$ brew install mise
```

### Ubuntu

```bash
$ curl https://mise.run | sh
```

## macOS/Windows共通編

ターミナルで次のコマンドを実行します。

```bash
$ echo $SHELL;
```

この結果がbashかzshかで次のステップが異なります。
(どれでもなかった人はサポーターを呼んでください)


### bashの場合

`.bashrc`に追加、もしくは編集してください。

```bash
if type mise &>/dev/null; then
  eval "$(mise activate bash)"
  eval "$(mise activate --shims)" 
fi
```

なおmiseを`brew`以外で入れた場合は以下の行を`if type mise`の前の行に加えてください

```bash
export PATH="$HOME/.local/bin:$PATH"
```

### zshの場合

```bash
if type mise &>/dev/null; then
  eval "$(mise activate zsh)"
  eval "$(mise activate --shims)" 
fi
```

なおmiseを`brew`以外で入れた場合は以下の行を`if type mise`の前の行に加えてください

```bash
export PATH="$HOME/.local/bin:$PATH"
```

## Node.jsのインストール

miseを使ってインストールします。

```bash
$ mise use -g node@22
```

`-g`はグローバルにインストールするオプションです。
`node@22`はNode.jsのバージョン22をインストールすることを意味します。

今回は利用しませんが、miseはディレクトリごとに利用する言語のバージョンを切り替えることもできます。
様々なプロジェクトを開発する場合は、プロジェクトごとにNode.jsのバージョンを切り替えることができるので便利です。
