## usersテーブル
|Column|Type|Options|
|------|----|-------|
|nickname|string|null: false|
|e-mail|string|null: false|
|passwaord|string|null: false|
|name|string|null: false|
|name-kana|string|null: false|
|birthday|datetime|null: false|
|TEL|integer|null: false|
|address|string|null: false|
### Association
- has_many :comments
- has_many :items
- has_many :many payments

## commentsテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|item_id|integer|null: false, foreign_key: true|
|text|text|null: false|
### Association
- belongs_to :user
- belongs_to :item

## itemsテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|name|string|null: false|
|price|integer|null: false|
|text|text|null: false|
|image|string|null: false|
|categoyr_id|integer|null: false, foreign_key: true|
|delivery_dmg|string|null: false|
|deliverr_method|string|null: false|
|delivery_area|string|null: false|
delivery_day|date|null: false|
### Association
- has_many :comments
- belongs_to :user

## cardsテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|card_nunber|integer|null: false, foreign_key: true|
### Association
- belongs_to :

## sellerテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|text|text|null: true|
### Association
- has_many :comments
- has_many :items
- has_many :many payments

## buyerテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|text|text|null: true|
### Association
- has_many :comments
- has_many :items
- has_many :many payments

## seller_buyerテーブル
|Column|Type|Options|
|------|----|-------|
|seller_id|integer|null: false, foreign_key: true|
|buyer_id|integer|null: false, foreign_key: true|
|text|text|null: true|
### Association
- has_many :comments
- has_many :items
- has_many :many payments