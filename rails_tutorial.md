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
