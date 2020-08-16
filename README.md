## groups_usersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|group_id|references|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user

## groupsテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false|

### Association
- has_many :messages
- belongs_to :user
- has_many :users,through::groups_users
- has_many :groups_users

## usersテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|Email|string|null: false,unique: true|
|password|string|null: false|

### Association
- has_many :messages
- belongs_to :user
- has_many :groups,through::groups_users
- has_many :groups_users

## messagesテーブル

|Column|Type|Options|
|------|----|-------|
|content|text||
|image|text||
|user_id|references|null: false, foreign_key: true|
|group_id|references|null: false, foreign_key: true|

### Association
- belongs_to :user
- belongs_to :group