テーマは特に決めていない。
やわらかい雰囲気よりは、slackのようにシンプル・洗練

## 用意する画面

### 認証(users)

- 新規登録画面（名前・メアド・パスワード・パスワード確認）
- ログイン画面（メアド・パスワード）

### グループ(groups)

- グループ作成画面（名前）
- グループ詳細画面（名前を表示、招待ボタン・削除ボタン。3点にまとめてでもいいかも）

### タスク(tasks)

- タスク作成画面（タイトル・説明）
- タスク詳細画面（タイトル・説明を表示、ステータスの切り替えボタン？）

タスク一覧画面は不要かな？
グループ詳細画面でタスク全件取得→表示でいいかな、と思う

## コメント(comments)

画面は不要。フォームだけ必要。
slackのチャット送信みたいにする or 普通にtaskの下に出すか。

## テーブル案

### users

| カラム | 型 | 備考 |
| --- | --- | --- |
| email | string | NOT NULL / unique |
| encrypted_password | string | Devise標準 |
| name | string | NOT NULL |

### groups

| カラム | 型 | 備考 |
| --- | --- | --- |
| owner_id | integer (FK) | users.id / 管理者 |
| name | string | NOT NULL |
| invite_code | string | NOT NULL / unique |
| is_personal | boolean | default: false / ユーザー専用の個人グループかどうか |

### group_members

| カラム | 型 | 備考 |
| --- | --- | --- |
| user_id | integer (FK) | users.id |
| group_id | integer (FK) | groups.id |

### tasks

| カラム | 型 | 備考 |
| --- | --- | --- |
| group_id | integer (FK) | groups.id |
| user_id | integer (FK) | users.id / 担当者（1人固定） |
| title | string | NOT NULL |
| description | text | 任意 |
| status | integer (enum) | todo / in_progress / done を想定 |

### comments

| カラム | 型 | 備考 |
| --- | --- | --- |
| task_id | integer (FK) | tasks.id |
| user_id | integer (FK) | users.id |
| content | text | NOT NULL / 日報本文 |
