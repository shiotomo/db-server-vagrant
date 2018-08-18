# db-server-vagrant

## データベース用vagrantリポジトリ
- 仕様
  - 5432,3306番ポートをあけてある
  - ホスト名をcamryにしてある
  - PostgreSQL、MySQL用
  - 共有フォルダの作成はしない(wsl用)

## 注意点
- vm内にPythonをインストールしないとAnsibleを利用できないので`vagrant ssh`後にpythonをインストールする
```
sudo apt-get install python-minimal -y
```
