# LINEbot用Docker環境
## 事前設定
* ゲストOSはhttps通信出来る環境
  * ローカルで遊ぶだけなら./local内のngrokを起動してローカルまでトンネル引っ張る
  * 起動コマンド
    * ```./local/ngrok http 8888```
    * ターミナルに表示されるhttpsアドレスをLINE Devveloperに設定
## 起動コマンド
  * ```./docker/docker-compose up -d```

## APPサーバ
* python 3.6
* http(8888) - Nginx(80) - uWSGI - flask
* 受け入れポートは8888
  * ホストOSから8888ポートにリクエストを飛ばす

## DBサーバ
* MySQL
  * 最新のMySQLはrootユーザの承認方法が変更されたのでdocker/mysql-conf/default_authorization.cnfで以前の承認方法に変更
* APPサーバコンテナからはmysqlで名前解決可能

## docker-composeの設定
* CHANNEL_ACCESS_TOKEN, CHANNEL_SECRET : LINE Developerで取得したもの
* MYSQL_ROOT_PASSWORD : MySQLのrootユーザのパスワード