# Docker環境構築
参考文献
（https://zenn.dev/tmasuyama1114/articles/rails-docker-5x-how-to)

# 作成ファイル
環境構築したいディレクトリーにDockerfile,docker-compose.yml,Gemfile,Gemfile.lock作成

# railsプロジェクトの作成 (rails new)

```docker-compose run web rails new . --force --no-deps --database=mysql```

--force: 既存の file (ここでは Gemfile, Gemfile.lock) は上書きする形<br>
--database=mysql: ただし rails のデータベースには MySQL を使用<br>
--no-deps mysqlを起動せずにrailsアプリケーションを作成する<br>

# buildの実行

```docker-compose build```

Gemfile に追記された gem のインストール

# データベースの作成

```docker-compose run web bundle exec rails db:create```

# コンテナの起動

```docker-compose up -d```
-dでバックグランド起動

# コンテナ一覧確認方法
```docker ps -a ```

# 不要なイメージやコンテナを削除する方法

コンテナを消す場合は、docker ps -aからコンテナを確認<br>
``` dockr rm コンテナID```
で削除

イメージを消す場合は、<br>
```docker images``` 
からイメージ一覧を確認し、不要なイメージIDを
``` docker rm images ```
で削除

```docker system prune -f ```<br>
停止中のコンテナや未使用ボリュームやイメージやネットワークを全部削除する（未使用オブジェクトを全て削除するため注意）
