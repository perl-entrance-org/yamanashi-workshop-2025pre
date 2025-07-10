# エディタ入門

___
## エディタ
コードを書く時に最も使う道具、それがエディタです。

プログラミングに特化した様々なエディタが開発されていますが、Perl入学式ではその中でもVisual Studio Codeを紹介します。

特にこだわりのない方は、今回紹介するVisual Studio Codeを試してみましょう。

もちろん、EmacsやVim、サクラエディタなど、既に使い慣れているエディタがある方はそちらをお使いください。

___
## Visual Studio Code

<a href="https://code.visualstudio.com/" target="_blank">Visual Studio Code - Code Editing. Redefined</a>へアクセスし、「Download」をクリックします。

___
## Visual Studio Code

### Windows
ダウンロードした`VSCodeUserSetup-**.exe`をダブルクリックすると、インストールが開始されます。

`**` としたところにはバージョン番号が入ります。

インストール後は、スタートメニューから「Visual Studio Code」をダブルクリックすればVisual Studio Codeが起動します。

インストール直後は自動的に起動します。

___
## Visual Studio Code

### macOS
ダウンロードした`VSCode-darwin-stable.zip`をダブルクリックすると、`Visual Studio Code.app`が生成されます。

これをダブルクリックすればVisual Studio Codeが起動します。

「"Visual Studio Code.app"はインターネットからダウンロードされたアプリケーションです」という警告が出た場合、「開く」をクリックします。

___
## Visual Studio Code

### 日本語化
メニューが英語でとっつきにくい場合には、日本語化することが可能です。

1. ウィンドウ左上の View -> Command Palette から `Configure Display Language`と入力して候補を選択する。

1. Install Addicional Languages を選択する。

1. 左側のメニューから「日本語」を選択し、緑色の「Install」ボタンを押す。

1. 一度Visual Studio Codeを閉じて、再度起動する。

1. 英語表記に戻す場合には、1. から en を選択することで英語メニューになります。

### WSL2の設定

WindowsでWSL2を使っている場合、Visual Studio CodeをWSL2の環境で使うことができます。
1. Visual Studio Codeを起動し、左側のメニューから拡張機能(Extensions)を選択します。
1. 検索バーに「Remote - WSL」と入力し、拡張機能をインストールします。
1. インストール後、左下の緑色のアイコンをクリックし、「Remote-WSL: New Window」を選択します。
1. これでWSL2の環境でVisual Studio Codeが起動します。

___
## Visual Studio Code

### ファイルを開く
- 左上メニューの ファイル -> (Windows版)ファイルを開く(macOS)開く

### ファイルを保存する
- 左上メニューの ファイル -> 保存

___
## 練習問題
1. `yamanashi-programming`ディレクトリ内に`profile.txt`という空のファイルを用意して、Visual Studio Codeで編集します。

  ファイルの中には、「使用したコマンド1つとその説明」、「今使用しているOS」、「使用しているエディタ」を書いて保存します。

1. ターミナルを使って、`profile.txt`を`profile2.txt`という名前でコピーしましょう。

1. コピー元の`profile.txt`をターミナルから削除しましょう。

1. コピーした`profile2.txt`をターミナルから`profile.txt`という名前に変更しましょう。

次のページに練習問題のヒントを載せます。

___
## 練習問題のヒント
「エディタで保存したファイルがターミナルから見つからない!」という場合、`pwd`コマンドで現在いるディレクトリを確認してみましょう。

大抵の場合、エディタがファイルを保存した保存先とは違うディレクトリにいます。`cd`コマンドで移動しましょう。

