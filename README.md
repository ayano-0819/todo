## アプリ名
to do

## 概要
本アプリは、Laravelを使用して作成したタスク管理用Webアプリケーションです。
データの登録・表示・更新・削除ができます。
Docker（nginx / PHP / MySQL）を用いた開発環境上で動作します。


## 使用技術
- PHP
- Laravel
- MySQL
- Nginx
- Docker

## Docker構成
- **nginx**：Webサーバー
- **php**：Laravel実行環境
- **mysql**：データベース
- **phpMyAdmin**：データベース管理ツール

## 環境構築手順（Docker）

### 1. リポジトリをクローン

```
git clone git@github.com:ayano-0819/todo.git
```

### 2. Dockerコンテナをビルド

```
docker compose up -d --build
```
### 3. Laravelのパッケージのインストール

```
docker compose exec php bash

composer install
```

### 4. .envファイル作成（PHPコンテナ内で入力）

```
cp .env.example .env
```

### 5. アプリケーションキーの生成（PHPコンテナ内で入力）

```
php artisan key:generate
```

### 6. .envファイル修正
4で作成された「.env 」を以下のように修正してください。

```
DB_CONNECTION=mysql
DB_HOST=mysql
DB_PORT=3306
DB_DATABASE=laravel_db
DB_USERNAME=laravel_user
DB_PASSWORD=laravel_pass
```
### 7. マイグレーション実行（PHPコンテナ内で入力）

```
php artisan migrate
```

### 8. シーディングの実行（PHPコンテナ内で入力）

```
php artisan db:seed
```

### 9. ブラウザでアクセス

```
http://localhost
```
## phpMyAdmin
以下のURLからphpMyAdminにアクセスできます。

```
http://localhost:8080
```