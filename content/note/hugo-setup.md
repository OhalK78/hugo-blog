---
title: "Hugo Setup"
date: 2022-12-10T22:01:42+09:00
categories : [ "Docs", "hugo" ]
tags : [ "hugo", "setup", "note" ]
---

# hugoでサイト生成

hugoでブログサイトを作ってみる。  
以下自分用のメモ。

手順としては
* hugoを入れる
* hugoでサイトを作る
* themeを入れる
* 設定する
* 何か書く
* 確認する
* サイト生成

## hugoを入れる

homebrewで入れる。  
```brew update```して、```brew install hugo```。  
アップデートは```brew upgrade hugo```。

```hugo --version```して大丈夫そうならおk。


## hugoでサイトを作る。

```hugo new site name```を実行すると、```name```フォルダが生成される。

```cd name```でフォルダに移動。

このタイミングで```git init```しておく。

## themeを入れる。

```hugo theme```とかでggると、[hugoのthemeサイト](https://themes.gohugo.io)があるので、そこで使いたいものを探す。

個人的に、検索機能が手軽に使えるととうれしいので、検索機能が手軽に使えそうなテーマを探した。

今回は[blow fish](https://themes.gohugo.io/themes/blowfish/)というthemeが目に入ったので、こちらを導入。coolなテーマだと思います。

テーマを選んだら、その配布元で入れ方とか書いてある(Getting StartedやQuick Startとか)ので、それ通りにやればよい。

hugo modで導入もできるようだが、今回はgit submoduleがrecommendedだったのでgit submoduleで導入。

## 設定を書く

テーマ配布元にある設定をそのままやっておけばよい。  
最低限、```./config.toml```に```themes="テーマ名"```があれば動くはず。テーマ名とは、```themes/```以下のテーマのフォルダ名。

このサイト自体もほとんど配布下の設定を流用している。画像や説明文を変えたり、言語の設定を日本語にできる(とdocumentに書いてあった)ので```languages="ja"```にしたり、フォルダ名の一部を```*_en_*```から```*_ja_*```にしたりするなどした。

## なんか書く

hugoでは
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
|- その他
```
のようなフォルダ構成になる。

記事の作成にはコマンドを使う。  
``` hugo new 作りたい記事名.md```をすると、```content/作りたい記事名.md```ファイルが生成される。  
また、``` hugo new hoge/huga.md```とすると、```content/hoge/huga.md```ファイルが生成される。このときhogeフォルダがなくても、フォルダを作ってくれる。

記事を生成したら書き込む。  
冒頭の```---```で囲まれている部分は記事の設定となる。```Draft```は下書き設定で、```true```だとサイト生成時に表示されないので、```false```にするか```Draft```ごと消す。  
```categories : [ "カテゴリ名" ]```や```tags : [ "タグ名", "タグ名" ]```のようにカテゴリやタグも設定できる。  
この辺は設定でデフォルトをいじれる。```archetypes/default.md```がテンプレートになっている。  

動作確認用に、トップページとpostsページに何か書いてみる。

```hugo new _index.md```して、```vim content/_index.md```でなんか書く。  
```hugo new posts/_index.md```, ```hugo new posts/my-first-post.md```して開き、何かしらを書く。```draft```を消すかfalseにするのを忘れないように。

## 確認する

```hugo server```を実行し、```localhost:1313```をブラウザで確認。

```hugo server -D```とすると、draft状態の記事も確認可能。

## サイトを生成

```hugo```と実行すれば```public```フォルダが生成され、それ以下に公開用のhtmlファイルなどが生成される。公開する時はpublicフォルダの中身をサーバーに配置するなどする。

