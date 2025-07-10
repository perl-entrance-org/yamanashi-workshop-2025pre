# AltJS

2025年の現代でこそ生のJavaScriptの表現力はだいぶ向上しましたが、特に2008年あたりの時代ではJavaScriptの言語仕様の進化が停滞し、プログラマの期待に沿うような開発がやりずらい状態が発生しました。

そこでモダンな文法や書きやすい機能を実装した別の言語でプログラミングをし、それをJavaScriptのソースコードにコンパイルするという手法が台頭しました。このようにあるプログラミング言語のソースコードを別のプログラミング言語のソースコードにコンパイルすること一般的に「**トランスパイル**」と言い、特にJavaScriptの代替となるようなプログラミング言語のことをAlternative JavaScript、通称**AltJS**と呼ぶようになりました。

代表的なAltJSには次のようなものがあります。(いっぱいありますね)

- CoffeeScript
  - かつてRuby on Rails方面でよく使われた
- TypeScript
  - 今回のトピック
- Scala.js
  - Scalaというプログラミング言語をJavaScriptに変換する
- PureScript
- Elm
- Gleam
  - [関数型まつりでGleamについて話しました](https://zenn.dev/comamoca/articles/2025-06-17-i-was-talk-about-gleam-at-fpmatsuri)
  - [TypeScriptユーザーに贈るGleam入門](https://zenn.dev/comamoca/articles/gleam-tour-for-typescript-user)
- ClojureScript


JavaScript界隈は進化が激しい世界なので、2~3年前の情報ですらだいぶ古いという状態になります。
特にAltJSに関しては現在では開発が止まっているもの、現代のJavaScriptよりも表現力が落ちているものなどが存在するため、技術選択をする際は最近の動向をチェックするようにしましょう。

# jQuery

Webフロントエンドで昔からよく聞くライブラリにjQueryがあります。
jQueryは2006年にリリースされて以降現在でも広く使われています。

jQueryは当時のJavaScriptが抱えていた次のような課題に対して作られました。
- ブラウザごとの互換性が低い
- JavaScript自体の機能が弱い

jQueryはJavaScriptのAPIを抽象化し、ブラウザごとの差異を吸収することで、同じコードでどのブラウザでも動作するようにしました。
jQueryは非常に多くの機能を提供しており、特にDOM操作やイベント処理、Ajax通信などを簡単に行うことができるようになっています。
しかし、現在ではブラウザ間の差異がほとんどなくなったこと、 JavaScript自体の言語仕様が大きく改善されたことから、jQueryを使わずとも同じようなことができるようになりました。
そのため、現在ではjQueryを使うことは少なくなっています。
とはいえ便利なライブラリであることは変わりないので、比較的長く運用されているサイトや枯れた技術スタックを採用している場合はjQueryが使われていることもあります。

jQueryそのものはTypeScriptの型定義も提供されており、TypeScriptからも利用することができます。
いまからjQueryを使うぞ!!という場合もTypeScriptで書くのがおすすめです。
