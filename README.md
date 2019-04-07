# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...


# DBの設計

## messagesテーブル

|Column|Type|Options|
|------|----|-------|
|body|text|null: false|
|image|string|null: false|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user
- belongs_to :users_groups

## usersテーブル

|Column|Type|Options|
|------|----|-------|
|e-mail|integer|null: false, foreign_key: true|
|password|integer|null: false, foreign_key: true|
|name|integer|null: false, foreign_key: true|


### Association
- has_many :messages
- has_many :users_groups
- has_many :groups, through: :users_groups

## groupsテーブル

|Column|Type|Options|
|------|----|-------|
|group_name|integer|null: false|
|chat_member|integer|null: false|

### Association
- has_many :messages
- has_many :users_groups
- has_many :users, through: :users_groups


## users_groupsテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|

### Association
- has_many   :messages
- belongs_to :user
- belongs_to :group


