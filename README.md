# README

## usersテーブル

|Column|Type|Options|
|------|----|-------|
|user_name|text|index: true, null: false, unique: true|
|email|text|null: false|
|password|text|null: false|

### Association
- has_many : messages
- has_many : groups, through: :messages
- has_many : group_members
- has_many : groups, through: :group_members


## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|group_name|text|null: false, unique: true|

### Association
- has_many : messages
- has_many : users, through: :group_members
- has_many : group_members
- has_many : users, through: :group_members

## group_membersテーブル
|Column|Type|Options|
|------|----|-------|
|group_id|integer|foreign_key: true|
|user_id|integer|foreign_key: true|

### Association
- belongs_to :groups
- belongs_to :users


## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|body|text||
|image|string||
|time_stamp|||
|group_id|integer|foreign_key: true|
|user_id|integer|foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user
