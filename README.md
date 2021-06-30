@@@
title=Pythonでmdをqiitaに投稿する
private=true
tags=python,qiita,md
tweet=false
id=
@@@

# はじめに

rubyでorgファイルをqiitaに投稿するgemであるqiita_orgにアイデアをもらい，

pythonでmdファイルをqiitaに投稿するcliアプリケーションを作ってみました．

# mdのいいところ

私が考えるmdのメリットとして，
- 情報が豊富
  - googleの検索で
    - md 約 41,200,000 件 （0.39 秒） 
    - orgmode 約 462,000 件 （0.55 秒） 
  - と，約100倍の差があった．
- vscodeのシンタックスハイライトとコード補完が使いやすい

# 環境

```
MacBook Pro
Quad-Core Intel Core i5
macOS Catalina 10.15.7

❯❯❯ python -V
Python 3.9.0
```

# 使用技術

- fire
- aws s3

# プログラムの仕様

## post

@image:./pyqiita.png

mdファイルをqiitaに投稿します．

mdファイルには先頭にヘッダー情報を書き込みそれを元に投稿します．

```
@@@
title=タイトル
private=true
tags=tag1,tag2
tweet=false
id=
@@@
```

また，qiita_orgの課題であった，画像のアップロードをs3を使うことで，自動化しています．

その方法として，md中に,```@image:./image.png```のように，@image:というキーワードを用います．

そうすることで，imageのpathをparseして，s3にアップロードします．

また，テーブルや，コードブロックなど，mdの機能を用いてそのままqiitaにアップローダできます．

もちろん，記事の更新も可能です．

## template

ヘッダー情報を書き込んだ，mdファイルを作成します．

# インストール
