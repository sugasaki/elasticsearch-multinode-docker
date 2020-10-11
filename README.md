# elasticsearch-multinode-docker

- Docker で構築
- Elasticsearch: 3 ノードで起動
- Logstash: Twitter データ取得
- Kibana: Twitter データ可視化

# elasticsearch 起動

## 1. build

```
$ docker-compose build
```

## 2. up

```
$ docker-compose up
```

## 3. kibana

以下にアクセスする

http://localhost:5601/

[ダッシュボード](<http://localhost:5601/app/dashboards#/list?_g=(filters:!(),refreshInterval:(pause:!t,value:0),time:(from:now-1h,to:now))>)で確認します。

# キーワードの変更

./logstash/pipeline/twitter.conf

keywords に取得したいキーワードを設定する

```
keywords => ["","",""]
```

index 名も適宜変更する。

```
output {
  elasticsearch {
    hosts => ["http://es01:9200/"]
    index => "twitter_covid"
  }
}
```

# 後片付け

## Elasticsearch 終了

停止とコンテナの削除

```
docker-compose down
```

## 停止とコンテナの削除、及び、ボリュームも消す

ボリュームも消す時は以下

```
docker-compose down --volumes
```

## 全て消す

全て消す時は以下（コンテナ、イメージ、ボリュームそしてネットワーク、全て）

```
docker-compose down --rmi all --volumes
```

# ボリューム

## ボリュームの一覧

```
docker volume ls
```

## ボリュームの削除

```
docker volume prune
```
