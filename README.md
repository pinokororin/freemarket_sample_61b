# freemarket_sample_61b DB設計

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|nickname|string|null: false|
|password|string|null: false|
|e-mail|string|null: false|
|family_name|string|null: false|
|first_name|string|null: false|
|family_name_kana|string|null: false|
|first_name_kana|string|null: false|
|birthday|integer|null: false|
|phone_number|string|null: false| 
|profile|text|null: true|
|icon|text|       |

### Association 
- has_many :items
- has_many :comments
- has_many :cards 
- has_many :addresses 

## addressテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreing_key:true|
|name|string|null: false| 
|name_kana|string|null: false| 
|postal_code|integer|null: false|
|prefectures|string|null: false|
|municipalities|string|null: false|
|house_number|string|null: false|
|building_name|string|null: true|
|phone_number|integer|null: false| 

### Association 
- has_many :transactions 
- belong_to :user

## cardsテーブル ^^
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|card_number|integer|null: false, foreign_key: true|
|expiration_date|integer|null: false| 
|securitycord|integer|null: false| 

### Association
- belongs_to : user


## commentsテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|item_id|integer|null: false, foreign_key: true|
|text|text|null: false|
### Association
- belongs_to :user
- belongs_to :items

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
- belongs_to :items


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