# GitHub Issue を TODO リストとして使いたい
## 理由
- TODO リストは見なくなるのが一番の問題．TODO リストのアプリよりは GitHub を見る頻度のほうが高い
- GitHub Actions の action 作ってみたい(衝動)

## 要件
### 締め切りの設定
issue 作成時に締め切りを書いたら label をつけてほしい．
issue 作成時に action を動かすには [issues event](https://docs.github.com/en/actions/learn-github-actions/events-that-trigger-workflows#issues) を使えばできる．
label の変更には [この API](https://docs.github.com/en/rest/reference/issues#add-labels-to-an-issue) が使える．
「次の〇曜日」，「1週間後」，「2週間後」，「3週間後」，「1ヶ月後」などの label を用意して，毎日日付が変わったときに貼り直す．

issue のそれぞれについて現在の日時に応じて適切な label を貼る action を作り，issue 作成時と決まった時間に起動する．
`edited` をトリガーにしてコマンドに反応できるとうれしい．

### 通知
日時を書くとその日時に通知(コメント)をしてほしい．
10分ごとくらいに定期実行して，それぞれの issue について設定した日時を過ぎていたらコメントする．
`edited` をトリガーにしてコマンドに反応できるとうれしい．

### 定期的な issue の作成
毎週ある課題などは自動的に作成したい．
`weekly` などの label のついた issue が close されたら同じ締め切り・通知日時で作り直す．
