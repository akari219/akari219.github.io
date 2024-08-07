---
layout: page
title: "git memo"
permalink: /docs/git-memo
---

# ソフトウェア工学 2024
講義で学んだことをmarkdown形式でまとめる．
## markdown形式
markdown形式とは，githubやその他の場面でも多多使われる形式である． \
タイトルを複数の大きさでまとめ，その下に本文を書く．そのとき，項目などを設定することができる． \
改行は改行コードを指定することで実現できる． \
以下，できることをリスト化したものである．
- 項目による箇条書き表現
  - その下に一つ小さい項目を作ることもできる．
- タイトルの表現
- 数式の表現
  - このとき，特殊な記号を使うことでまとめかっこなども作ることができる．

$$
\begin{cases}
  \frac{a}{b}=c+d \\
  a^{\ast}=e^f
\end{cases}
$$

## GitHubについて
以下，githubの説明である．
### 構造
あるリポジトリの中には，通常のローカルフォルダのシステムと同じような形でフォルダとファイルが存在する．慣例では，リポジトリのホームにはREADME.mdファイルが存在し，そのリポジトリについての説明が書かれている．
### ブランチ管理
リポジトリの現在の状況として，メインブランチというものがある．メインブランチの最新の状況がリポジトリの状況である．メインブランチから分岐してブランチを作り，そこで開発を進めることで，メインを正しい状態にしたままエラーを取り込まないようにできる．エラーが発生した場合は，メインブランチにマージする前に分岐先のブランチで修正が可能である． \
修正がメインブランチでも同じ場所で行われていた時，コンフリクトが起こる．これは，手動で調整することができる．一般的にはあまりおこらないように，ブランチを操作するときは編集する範囲が異なるものごとでブランチを用意しておく．機能ごとにブランチを分けるなどである． \
変更を加えたブランチは，プルリクエストを出すことで，メインブランチにプルしてもよいか共同開発者に問うことができる．問題がなければメインブランチにマージすることで，ブランチは閉じ，メインブランチが更新される．

### ローカルリポジトリ
ネットワーク上のリポジトリは，ローカルリポジトリで編集したものをpushすることで更新できる．ローカルリポジトリの更新をpushする方法はさまざまであり，VSCodeであれば内部にコミットやプッシュをするボタンも用意されているが，ここではターミナルから操作する方法を紹介する．
- git commit -a \
これにより，コミットに名前を付けてローカルリポジトリの最新の状態をステージングすることができる．
- git push \
これにより，ステージングされた状態をネットワーク上のリポジトリに反映させることができる．これでようやく共同開発者が自分の開発進捗を見ることができるようになる．
- git diff \
これは，必ず使わなければならないものではないが，現在のワークツリーとステージングされたものの差分を表示することが可能である．これにより，意図しない変更を防ぎやすくなる．

### ブランチの操作
ブランチの作成から，その確認までの操作を以下に示す．
- git switch -c [branchname] \
ブランチを作ってそのブランチに分岐する操作である．これを行った後の自分の作業ブランチは，新しく作ったブランチである．
- git branch \
現在の自分の作業ブランチや開いているブランチを確認するコマンド．作業ブランチは色が変わって表示されたり，アスタリスクがついてわかりやすくなっている．
- git push --set-upstream origin [branchname] \
作業ブランチで変更をコミットした後にプッシュするとき，最初は今の変更の上流ブランチが定義されていないため，それを定義してそこにプッシュするためのものである．一度これを行った後は上流ブランチが定義されているため，特に変更を加えなければbranchnameブランチにプッシュするようになる．