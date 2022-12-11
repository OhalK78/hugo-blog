---
title: "Hugo Setup"
date: 2022-12-10T22:01:42+09:00
categories : [ "Docs", "hugo" ]
tags : [ "hugo", "setup", "note" ]
---

# hugoをつかおう

hugoでブログサイトを作ってみる。半年前とかにもやってたけど、メモが残ってない＆三日坊主で投げ出してたので、ほぼ覚えてない。

今回はちゃんと記録に残しておこうと思ったので書きます。

手順としては
* hugoを入れる
* hugoでサイトを作る
* themeを入れる
* 設定する
* なんか書く
* 確認する
* (サイト生成

## hugoを入れる

homebrewでいいはず。```brew update```して、```brew install hugo```。  
既に入ってるなら```brew upgrade hugo```とかする。

```hugo --version```して大丈夫そうならおk。


## hugoでサイトを作る。

```hugo new site 作りたいフォルダ名```を実行すると、```作りたいフォルダ名```フォルダが生成される。

```cd 作りたいフォルダ名```でフォルダに移動。

で、たぶんtheme入れる時に必要になるので、```git init```しておこう。

## themeを入れる。

```hugo theme```とかでggると、[hugoのthemeサイト](https://themes.gohugo.io)があるので、そこで使いたいものを探す。~~テーマありすぎで沼です~~

個人的に、検索機能がついてるとうれしくね？派閥の人間なのでついてそうなものを探した。

今回は[blow fish](https://themes.gohugo.io/themes/blowfish/)というthemeが目に入ったので、こちらを導入。カタカナでブルーフグって書いてあって、日本人の方？って思って選んだけどよくよく読んでたらどうやらスペイン？(確認したけどうろおぼえ)の方だった。まあdocumentは英語なので、問題なし。

選んだら、その配布元で入れ方とか書いてある(Getting StartedとかQuick Startとか)ので、とりあえずそれ通りにやればよい。

hugo modで導入もできるみたいだけど、今回はgit submoduleで導入。特に理由はない。

## 設定を書く

正直テーマ配布元にある設定をそのままやっておけばよい。  
最低限、```./config.toml```に```themes="テーマ名"```があれば動くはず。テーマ名とは、```themes/```以下のテーマのフォルダ名。

これ自体もほぼパクリで、画像とかちょこちょこ文を変えたり、あとは言語の設定を日本語にできる(ってdocumentに書いてあった)ので、```languages="ja"```にしたり、フォルダ名の一部を```*_en_*```から```*_ja_*```にするなどした。

## なんか書く

hugoのブログは
```
hugo new siteでつくったフォルダ
|- config/
    |- _default/
        |- config.toml # 複数configファイルがある時は、このようにconfig/_default以下に置く。複数ないならべた置きでおk。
        |- *.toml
|- content/
    |- _index.md  # トップページ
    |- hoge.md
    |- posts/
        |- _index.md  # posts/のトップページ
        |- hoge.md
|- *
```
のようなフォルダ構成になる。

記事の作成ではコマンドを使う。  
``` hugo new 作りたい記事名.md```をすると、```content/作りたい記事名.md```のように記事が生成される。  
``` hugo new hoge/huga.md```とすると、```content/hoge/huga.md```と記事が生成される。このときhogeフォルダがなくても、hugoが勝手に作ってくれる。

記事を生成したら書き込む。  
```---```で囲まれているのは記事の設定的なやつ。titleとかはいじってもいいしいじらなくても。```Draft```は下書き設定で、```true```だと表示されないので、```false```にするか```Draft```ごと消す。  
```categories : [ "カテゴリ名" ]```や```tags : [ "タグ名", "タグ名" ]```のようにカテゴリやタグも設定できる。  
この辺は設定でデフォルトをいじれる。```archetypes/default.md```をいじる。  
今はやらないが、Draft消してcategories, tagsを書くようにするかも。

今回は動作確認ように、トップページとpostsページになんか書こう。

```hugo new _index.md```して、```vim content/_index.md```でなんか書く。  
```hugo new posts/_index.md```, ```hugo new posts/my-first-post.md```してなんか書く。どれも```draft```を消すのを忘れないように。

拡張子でわかる通り、hugoでは記事はmarkdownで書く。楽だね。

## 確認する

```hugo server```を実行すると、```localhost:1313```で確認できるよって言われる(と思う)ので、ブラウザで確認。確認できたらできてるはず。

```hugo server -D```とすると、terminalを占有しないのでよいかも。個人的には停止し忘れそうなのでオプションはあんまつけない。

## サイトを生成

```hugo```と実行すれば```public```フォルダが生成され、それ以下に色々生成される。公開する時はpublicフォルダの中身を突っ込めば良い。実際にはgithubなどのCI/CLでよしなにする方が楽らしい。

