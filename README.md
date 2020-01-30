# freemarket_sample_61b DB設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|nickname|string|null: false|
|passwaord|string|null: false|
|e-mail|string|null: false|
|family_name|string|null: false|
|first_name|string|null: false|
|name_kana|string|null: false|
|birthday|datetime|null: false|
|profile|string|null: true|
|gender|string|null: true|
### Association
- has_many :comments
- has_many :items
- has_many :payments

## addressテーブル
|Column|Type|Options|
|------|----|-------|
|postal_code|integer|null: false|
|prefecturess|string|null: false|
|municipality|string|null: false|
|house_number|string|null: false|
|building_name|string|null: true|
|TEL|integer|null: false|
### Association
- belongs_to :user

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
### Association
- has_many :comments
- belongs_to :user

## deliveryテーブル
|Column|Type|Options|
|------|----|-------|
|delivery_dmg|string|null: false|
|deliverr_method|string|null: false|
|delivery_area|string|null: false|
|delivery_day|date|null: false|
### Association
- belongs_to :user
- belongs_to :item

## cardsテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|card_nunber|integer|null: false, foreign_key: true|
### Association
- belongs_to : user

## sellersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|text|text|null: true|
### Association
- has_many :comments
- has_many :items
- has_many :payments

## buyersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|text|text|null: true|
### Association
- has_many :comments
- has_many :items
- has_many :payments

## sellers_buyersテーブル
|Column|Type|Options|
|------|----|-------|
|seller_id|integer|null: false, foreign_key: true|
|buyer_id|integer|null: false, foreign_key: true|
|text|text|null: true|
### Association
- has_many :comments
- has_many :items
- has_many :payments