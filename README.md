# freemarket_sample_61b DB設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|nickname|string|null: false|
|passwaord|string|null: false|
|name|string|null: false|
|name-kana|string|null: false|
|birthday|datetime|null: false|
### Association
- has_many :comments
- has_many :items
- has_many :payments

## addressテーブル
|Column|Type|Options|
|------|----|-------|
|e-mail|string|null: false|
|TEL|integer|null: false|
### Association
- has_many :items

## commentsテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|item_id|integer|null: false, foreign_key: true|
|text|text|null: false|
### Association
- belongs_to :user
- belongs_to :items

## deliveryテーブル
|Column|Type|Options|
|------|----|-------|
|delivery_dmg|string|null: false|
|deliverr_method|string|null: false|
|delivery_area|string|null: false|
|delivery_day|date|null: false|
### Association
- belongs_to :user
- belongs_to :items

## cardsテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|card_nunber|integer|null: false, foreign_key: true|
### Association
- belongs_to : user

## seller_itemsテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|name|string|null: false|
|price|integer|null: false|
|text|text|null: false|
|image|string|null: false|
|categoyr_id|integer|null: false, foreign_key: true|
### Association
- has_many :comments
- has_many :items
- has_many :payments

## buyer_itemsテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|name|string|null: false|
|price|integer|null: false|
|text|text|null: false|
|image|string|null: false|
|categoyr_id|integer|null: false, foreign_key: true|
### Association
- has_many :comments
- has_many :items
- has_many :payments

## seller_buyer_itemsテーブル
|Column|Type|Options|
|------|----|-------|
|seller_id|integer|null: false, foreign_key: true|
|buyer_id|integer|null: false, foreign_key: true|
|name|string|null: false|
|price|integer|null: false|
|text|text|null: false|
|image|string|null: false|
|categoyr_id|integer|null: false, foreign_key: true|
### Association
- has_many :comments
- has_many :items
- has_many :payments