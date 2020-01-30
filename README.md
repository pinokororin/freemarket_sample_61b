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
|user_id|integer|null: false, foreign_key: true|
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
|seller_id|integer|null: false, foreign_key: true|
|buyer_id|integer|null: false, foreign_key: true|
|name|string|null: false|
|price|integer|null: false|
|text|text|null: false|
|category_id|integer|null: false, foreign_key: true|
### Association
- has_many :comments
- belongs_to :user

## categoryテーブル
|Column|Type|Options|
|------|----|-------|
|women|string|
|mens|string|
|baby_kids|string|
|interior_house_accessories|string|
|books_musics_games|string|
|toy_hoby_goods|string|
|cosmetics_perfumes＿beauty|string|
|home_appliances_smartphone_camera|string|
|sports_leisure|string|
|hand_made|string|
|ticket|string|
|car_motorcycle|string|
|other|string|
### Association
- belongs_to :item

## imagesテーブル
|Column|Type|Options|
|------|----|-------|
|item_id|integer|null: false, foreign_key: true|
|category_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :item
- belongs_to :category

## deliveryテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|item_id|integer|null: false, foreign_key: true|
|dmg|string|null: false|
|method|string|null: false|
|area|string|null: false|
|day|date|null: false|
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
- belongs_to : user
- has_many :comments
- has_many :items
- has_many :payments

## buyersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|text|text|null: true|
### Association
- belongs_to : user
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
- belongs_to :seller
- belongs_to :buyer
- has_many :comments
- has_many :items
- has_many :payments