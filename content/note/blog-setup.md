---
title: "Blog Setup"
date: 2022-12-11T10:39:43+09:00
categories : [ "Docs", "hugo" ]
tags : [ "hugo", "setup", "note" ]
---

# blogの設定

hugoのブログの設定をいくつかやっていく。

## 記事のテンプレート設定(hugo)

デフォルトで、```hugo new 記事名```で記事を作成すると、
```
---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
draft: true
---
```
が記入されている。  
```archetypes/default.md```でこの辺を設定できる。  
今回は
```
---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
categories : [ "category" ]
tags : [ "tag1", "tag2" ]
draft: true
---
```
とした。

## ブログの見た目の設定

現在は```blowfish```というテーマを使用している。  
quick startのものをそのまま使っても十分使えるが、documentを読んで色々設定していく。

[参考(blowfish)のGetting Started](https://nunocoracao.github.io/blowfish/docs/getting-started/)

### menu(最上段)に追加

```config/_default/menues.ja.toml```を設定する。

例えばgithubへのリンクを追加するには 
```
[[main]]
  identifier = "github"
  pre = "github"     # name = "Github"でもよい
  url = "https://github.com/e205721HarukiO"
  waight = 40        # 並びに関係してくるので、前後の数字を見てから決める
```

preはblowfishで用意されているアイコンセットの設定。  
[このページ](https://nunocoracao.github.io/blowfish/samples/icons/)で確認できる。  
例えばtwitterなら```pre = "twitter"```とすればよい。

