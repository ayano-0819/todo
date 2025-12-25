## アプリ名
to do

## 概要
本アプリは、Laravelを使用して作成したタスク管理用Webアプリケーションです。
データの登録・表示・更新・削除ができます。
Docker（nginx / PHP / MySQL）を用いた開発環境上で動作します。


## 使用技術
- OS：Windows 11
- PHP 8.1
- Laravel 10
- MySQL 8.0
- Nginx 1.21
- Docker 28.4.0
- Docker Compose v2.39.2

## Docker構成
- **nginx**：Webサーバー
- **php**：Laravel実行環境
- **mysql**：データベース
- **phpMyAdmin**：データベース管理ツール

## 環境構築手順（Docker）

### 1. リポジトリをクローン

```
cd coachtech/laravel

git clone git@github.com:Estra-Coachtech/laravel-docker-template.git

mv laravel-docker-template todo

GitHubにて"to do"というリモートリポジトリをpublicで作成
⇒urlが作成される

cd to do

git remote set-url origin 作成したリポジトリのurl

git remote -v

git add .

git commit -m "リモートリポジトリの変更"

git push origin main

※エラーが発生した場合は下記コマンドを実行する

sudo chmod -R 777 *

```

### 2. Dockerコンテナをビルド

```
docker-compose up -d --build

code .
```
### 3. Laravelのパッケージのインストール

```
docker-compose exec php bash

composer install
```

### 4. .envファイル作成（PHPコンテナ内で入力）

```
cp .env.example .env

exit
```
### 5. .envファイル修正
4で作成された「.env 」を以下のように修正してください。

```
DB_CONNECTION=mysql
DB_HOST=mysql
DB_PORT=3306
DB_DATABASE=laravel_db
DB_USERNAME=laravel_user
DB_PASSWORD=laravel_pass
```
### 6. view ファイルの作成（コマンドラインに入力）

```
cd to do

mkdir src/resources/views/layouts

touch src/resources/views/layouts/app.blade.php

touch src/resources/views/index.blade.php

touch src/resources/views/category.blade.php

ディレクトリ構成
resources/views
├── index.blade.php
├── category.blade.php
└──  layouts
      └── app.blade.php
```

### 7. css ファイルの作成（コマンドラインに入力）

```
touch src/public/css/common.css

touch src/public/css/index.css

touch src/public/css/sanitize.css
```

### 8. マイグレーション実行

```
docker-compose exec php bash

php artisan migrate
```
### 8. ブラウザでアクセス

```
http://localhost
```
## phpMyAdmin
以下のURLからphpMyAdminにアクセスできます。

```
http://localhost:8080
```