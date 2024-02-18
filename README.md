# hugo blog

URL: https://OshiroHaruki.github.io/hugo-blog/

## 記事を書く
ブログ作成は  
```hugo new blog/記事名.md```  
何らかのメモ(技術含む)は
```hugo new note/記事名.md```

編集は  
```content/blog/記事名.md```を編集する。

手元で確認するには  
```hugo server```   

サイト生成は  
```hugo```

## hugoの便利な書き方メモ

ページ内リンクは
```
[記事名]({{< ref "/note/hugo-setup.md" >}})  
```
のように書くことでできる。
