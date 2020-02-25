# RailsTurorial学習記録
2/14より、RailsTutorialでの学習をスタート。  
自分用に学習過程でつまづいたところなどを記していく。  
ケアレスミスなどによる細かいエラーなどを含めると、つまづくことがかなり多い。  
投げ出したて寝たくなることもあるが、頑張る。
## 第一章
### 1.3.2 rails server
AWSのcloud9でrails serverコマンドを実行するが、プレビューがうまく表示されず、You're on Rails!のページが表示されなかった。  
プレビュー画面のアドレスバー横のポップアウトボタンを押して、別ウィンドウで見たら表示された。  
なぜプレビュー画面やアドレス入力ではうまく表示されないのかは不明。

### 1.4.3 Bitbucket
RailsTutorialではBitbucketの使用を推奨していたが、既にGitHubのアカウントを所持していたため、GitHubによるホスティングに挑戦した。  
GitHubでの公開鍵の登録の仕方などは、ググればすぐに出てきたが、リポジトリ追加が調べた方法でやってもなぜかうまくいかず、試行錯誤することになった。

Bitbucketへのリポジトリ追加とリポジトリへのプッシュは以下の通り説明されている。
``` Ruby
$ git remote add origin git@bitbucket.org:KoheiB/rails_tutorial.git
$ git push -u origin --all
```

では、GitHubへのリポジトリ追加とリポジトリへのプッシュはどうすればよいか、Gitの新規レポジトリのQuick setupのコードを試したところ、成功した。
```Ruby
$ git remote add origin git@github.com:KoheiB/rails_tutorial.git
$ git push -u origin --all
```
### 1.5.2 Herokuにデプロイする (1)
Herokuにデプロイする際に、Commitのコマンドが漏れていたため、エラーが出た。  
Commitしてやり直したところ、解決した。


### 2.1 アプリケーションの計画
Herokuにデプロイするところで苦戦。  
昨日やったはずなのになぜかうまくいかず、デプロイが中断されてしまう。  
調べたところ、Herokuはアプリケーションがエラーで動かないとデプロイが中断されるとのこと。
自分で書いたプログラムを見直すと、半角スペース漏れがあったため、修正。再度デプロイ。  
今度はURLを開いてもMethod Not Allowedと表示されてしまう。
これで１時間以上悩んだが、git push heroku master後のターミナル上のURLに飛んでいたことが原因。
```
remote: Verifying deploy... done.
To https://git.heroku.com/shielded-plains-01139.git
   cd90529..c019b66  master -> master
```

heroku createの際に表示されていたURLからアクセスして、無事に表示されていることが確認できた。
```
ec2-user:~/environment/toy_app (master) $ heroku create
Creating app... done, ⬢ shielded-plains-01139
https://shielded-plains-01139.herokuapp.com/ | https://git.heroku.com/shielded-plains-01139.git
```

第２章の勉強に入る前の導入時点で、かなりの遠回りになってしまった。

参考URL：同じミスしてた人　https://teratail.com/questions/149443

第２章の内容は、Progateで勉強した内容の復習だったので、その後は比較的スムーズに進んだ。  
しかし、デプロイでやはりherokuがNomethodErrorになったため、herokuをインストールするコマンドを再入力したところ、直った。

### 3.2.2 静的なページの調整
Cloud9のプレビューで直接URLを指定して確認する際は、既存URLの末尾に(/static_pages/home)のようなURLを直接入力すること。

参考URL：https://teratail.com/questions/144600


※大事だと思ったこと。
テスト駆動開発では「red ・ green ・REFACTOR」サイクルを繰り返すこと。

### 3.4.4 ルーティングの設定
原因はわからないが、作業がほぼ終了した時点で、cloud9からエラーメッセージでこれらのファイルはno longer exist的なことを言われ、closeを選択したらデータが全部なかったことになった。
意味がわからなくてキレそうだったが、とりあえずgit上にFinish static_pagesまでのデータはあったので、復元を試みた。
```
git reset --hard ハッシュ
```
調べたら上記のコマンドがそんな感じだったのでとりあえずやってみたらその時点までは直っていた。  
でもデータが消えて混乱していたので上のコマンドで直ったのか、それともデータが飛んだ時点でその時点までは生きてたのかよくわからない。  
復元コマンドこれで合ってるか北岡先生は教えてください。なんか違う気もする。
