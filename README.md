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

#　Chat-space DB設計
## groups_usersテーブル
|Column|Type|Option|
|------|----|------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to: group
- belomgs_to: user

## usersテーブル
|Column|Type|Option|
|------|----|------|
|email|string|null: false|
|password|string|null: false|
|nickname|string|null: false|
### Association
- has_many: groups_users
- has_many: groups, through: :groups_users
- has_many: messages


## messageテーブル
|Column|Type|Options|
|------|----|-------|
|body|text|null: false|
|image|string||
|group|references|null: false, foreign_key: true|
|user|reference|null: false, foreign_key: true|
## Associatisn
- belongs_to: user
- belongs_to: group

## groupテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
### Association
- has_many: groups_users
- has_many: users, through: :groups_users
- has_many: messages