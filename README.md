# PostgresSQLをDockerを使って勉強してみた

## 基本操作
<p>参考URL：https://book.st-hakky.com/docs/try-postgres-on-docker/</p>
<br>

## コマンド
<br>
<li>コンテナの中に入り、SQLを操作する場合</li>
<br>

```
docker compose exec db bash
```
<br>
<li>postgreSQLにrootユーザーとして接続</li>
<br>

```
psql -U root
```

## PostgreSQL にデータベースを作成する

```
root=# CREATE DATABASE test_db;
```

<br>
<li>確認</li>
<br>

```
root=# \l
                             List of databases
   Name    | Owner | Encoding |  Collate   |   Ctype    | Access privileges
-----------+-------+----------+------------+------------+-------------------
 postgres  | root  | UTF8     | ja_JP.utf8 | ja_JP.utf8 |
 root      | root  | UTF8     | ja_JP.utf8 | ja_JP.utf8 |
 template0 | root  | UTF8     | ja_JP.utf8 | ja_JP.utf8 | =c/root          +
           |       |          |            |            | root=CTc/root
 template1 | root  | UTF8     | ja_JP.utf8 | ja_JP.utf8 | =c/root          +
           |       |          |            |            | root=CTc/root
 test_db   | root  | UTF8     | ja_JP.utf8 | ja_JP.utf8 |
(5 rows)
```

## テーブルを作成する

<br>
<li>使用するデータベースを選択する</li>
<br>

```
root=# \c test_db;
You are now connected to database "test_db" as user "root".
```

<br>
<li>カラムを作成する</li>
<br>

```
test_db=# CREATE TABLE test_tbl (id integer, name varchar(10), company varchar(20));
```

<br>
<li>テーブルができているのかを確認</li>
<br>


```
test_db=# \dt
         List of relations
 Schema |   Name   | Type  | Owner
--------+----------+-------+-------
 public | test_tbl | table | root
(1 row)
```