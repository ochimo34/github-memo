# Githubの主な使い方

#### ・ なぜGitHubを使うのか？
#### ・ 開発の流れ
#### ・ 解説

## なぜGithubを使うのか？

Git = バージョン管理ツール
したがってGitを使っていれば編集した時期の確認,  
あるいは数日前にコードに戻ることができる.  
(20201111_sample.pyで管理しているイメージ)

Githubは オープンでコードを管理しているので, チーム開発の際に威力を発揮する.


## 開発の流れ

① リポジトリを作成する  
② 自分のパソコンにファイルを引っ張ってくる(clone)  
③ 編集用のbranchに移動する or 新しく作る  
④ ファイルを更新する(更新対象に入れて(add), 実際に更新する(commit))  
⑤ mainブランチを更新する(push)


## 解説①：リポジトリを作成する


## 解説②：clone

コードを編集するためには自分のパソコンにリポジトリ(**リモートリポ**)を取り込む必要がある.  
これを**cloneする**という.  
この取り込んだリポジトリを**ローカルリポ**という.

実際に次のように行う.  
```
$ cd ~/Desktop(ローカルリポを作成したい場所のpath)
$ git clone https://github.com/ochimo34/github-memo.git(リモートリポのURL)
```

これで指定したディレクトリにローカルリポが作成されている.


## 解説③：branch

リポジトリには木のような構造で中心branch(**main**)があり,  
それに対して様々なbranch(**feature branch**)を付け足すことでmain branchを更新していく.  
したがって, ローカルでの更新はbranchで行う.  
(mainは公開中なので, 直接変更してしまうと使用中のユーザーが混乱してしまう)

それではbranchに移動してみる.
```
$ cd ~/Desktop/github-memo(ローカルリポの場所のpath)
$ git checkout -b update-readme
```
-bを指定すると新しいbranchを作成することができる.  
また
```
$ git branch
```
で現在のbranchを確認することができる.

ここでコードを編集する.


## 解説④：add, commit

コードの変更はまとめて行うことができるので一旦変更対象にする(**add**).
このとき変更対象のことを**staging**と呼ぶ.
```
$ git add README.md(更新ファイル)
```

そしてstagingに上げた変更をrepoに反映する(**commit**).
```
$ git commit -m 'update readme'(変更内容)
```


## 解説⑤：push

これまでは編集用のbranchを更新してきたが, mainの更新はローカルで勝手に行うのではなくリモートリポで更新する.  
**その前にリポが更新されていないのかを確認する.**
```
$ git pull origin main
```
そしてpushする.
```
git push origin update-readme
```
そうするとgithubのリポジトリ上に更新通知(pull request)が行くので,  
認証するとリポが更新される.