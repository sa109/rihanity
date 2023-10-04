# テーブル設計

## usersテーブル

| Column             | Type   | Options                  |
| ------------------ | ------ | ------------------------ |
| nickname           | string | null: false              |
| profile            | string |                          |
| encrypted_password | string | null: false              |
| email              | string | null: false,unique: true |

### Association
- has_many: articles
- has_many: comments
- has_many: likes

## articlesテーブル

| Column           | Type       | Options                        |
| ---------------- | ---------- | ------------------------------ |
| tittle           | string     | null: false                    |
| content          | text       | null: false                    |
| user             | references | null: false, foreign_key: true |

### Association
- belongs_to: user
- belongs_to: category
- has_many: comments
- has_many: likes

## commentsテーブル
| Column  | Type       | Options                        |
| ------- | ---------- | ------------------------------ |
| article | references | null: false, foreign_key: true |
| user    | references | null: false, foreign_key: true |

### Association
- belongs_to: user
- belongs_to: article

## likesテーブル

| Column       | Type       | Options                        |
| ------------ | ---------- | ------------------------------ |
| article      | references | null: false, foreign_key: true |
| user         | references | null: false, foreign_key: true |

### Association
- belongs_to: user
- belongs_to: article