# Dockerfile_template_for_rails5
参考文献
（https://zenn.dev/tmasuyama1114/articles/rails-docker-5x-how-to)

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
