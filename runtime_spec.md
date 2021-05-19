# OCI runtime-spec
## The 5 principles of Standard Containers
### 1. Standard operations
Standard Containers は一連の Standard Operations を定義している．
コンテナを
* 作成，実行，停止するもの
* コピーしたりスナップショットをとったりするもの
* ダウンロードやアップロードをするもの

がある．

## 2. Content-agnostic
Standard Containers はコンテンツに依存しない．
コンテンツによらず standard operations は同じ動作をする．

## 3. Infrastructure-agnostic
Standard Containers はインフラに依存しない．
コンテナは OCI がサポートするすべてのインフラで動く．

## 4. Designed for automation
Standard Containers は自動化を意識してデザインされている．
2つめと3つめの principle から考えて，コンテナは自動化に適している．

## 5.Industrial-grade delivery
Standard Containers は産業レベルのデリバリを実現する．
上記の性質から，コンテナは様々な規模においてソフトウェアのデリバリを自動化できる．


## Filesystem Bundle
コンテナをエンコードするフォーマットとして filesystem bundle を定義している．
これは仕様に沿ったコンテナが standard operations を実行するために必要なデータやメタデータを含んだファイル群である．

Standard Container bundle はコンテナをロードして実行するために必要なすべての情報を含む．
1. `config.json`: 設定データ． bundle directory のルートに設置**しなければならない**． また名前は `config.json` **でなければならない**
2. コンテナのルートファイルシステム: `root.path` が `config.json` にセットされているならばそのディレクトリが必要である

これらはローカルのファイルシステムのひとつのディレクトリに存在**しなければならず**，そのディレクトリは bundle には含まれない．
つまり bundle の tar archive はこれらの artifacts を archive のルートにもつはずである．