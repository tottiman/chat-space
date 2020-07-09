# DB設計

## usersテーブル

|Column|Type|Options|
|------|----|-------|
|name|stirng|null: false|
|email|string|null: false|
|password|string|null: false|

### Association
- has_many :comments
- has_many :groups, through: :groups_users

## groupsテーブル

|Column|Type|Options|
|------|----|-------|
|group_name|stirng|null: false|
|user_id|integer|null: false, foreign_key: true|

### Association
- has_many :users, through: :groups_users
- has_many :comments

## groups_usersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user

## commentsテーブル

|Column|Type|Options|
|------|----|-------|
|comment|string|null: false|
|user_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :user
- belongs_to :group
