#  chat-space DB設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false, index: true|
|email|string|null: false|
|password|string|null: false|
### Association
- has_many :messages
- has_many :users_groups
- has_many :groups, through: :users_groups

## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|image|text||
|text|text||
|user|references|null: false, foreign_key: true|
|group|references|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group

## groupテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
### Association
- has_many :users, through: :users_groups
- has_many :users_groups
- has_many :messages

## users_groupテーブル
|Column|Type|Options|
|------|----|-------|
|user|references|null: false, foreign_key: true|
|group|references|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group
