---
title: "Hugoで生成したサイトをGithub Pagesで公開する"
date: 2022-12-17T14:24:38+09:00
categories : [ "Docs", "hugo" ]
tags : [ "hugo", "note" ]
---

Hugoで作成したサイトをGithubで公開する。  
Github Pages機能で手軽に公開可能。無料で利用可能だが、制限などがあるので確認しておく→[Github Docs](https://docs.github.com/en/pages/getting-started-with-github-pages/about-github-pages)。

```
Hugoでコンテンツ作成
 → Github Actionsを設定
 → Github Pagesで公開
```
といった流れで公開する。

[Host on GitHub (Hugo website)](https://gohugo.io/hosting-and-deployment/hosting-on-github/)通りにやれば良い。

以下個人的なメモ.

## Hugoでコンテンツ作成

[hugoでのブログ作成]({{< ref "/note/hugo-setup.md" >}})

```config.toml```で以下の設定を記述
```
baseURL = "https://e205721harukio.github.io/<Githubのリポジトリ名>/"
canonifyurls = true
```

上記設定をしておかないと、テーマの見た目が崩れるなどする。

## Github Actionsを設定

[これ](https://github.com/marketplace/actions/hugo-setup)を参考にして記述する。

```.github/workflows/gh-pages.yml```を作成し、上記サイトからコピペする。

## Github pagesで公開する

上記までの設定でGithubへpushすると、Github Actionsが動作する。

```gh-pages```ブランチができるため、これをGithub Pagesに設定する。

