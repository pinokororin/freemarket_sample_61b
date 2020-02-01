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

## cardsテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|card_number|integer|null: false, foreign_key: true|
|expiration_date|integer|null: false| 
|securitycord|integer|null: false| 

### Association
- belongs_to : user

## itemsテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|name|string|null: false|
|price|integer|null: false|
|item_explanation|text|null: false|
|category|integer|null: false| 
|product_situation(商品の状態)|string|| 
|shipping_charges(配送料の負担)|integer|null: false| 
|shipping_method(発送方法)|string|null: false|
|shipping_origin(発送元)|integer|null: false| 
|arrival_days(到着日数)|integer|| 

### Association
- has_many :comments
- has_many :images
- has_many :nices(いいね)
- belongs_to :user

## imagesテーブル
|Column|Type|Options| 
|------|----|-------| 
|item_id|integer| null: false, foreign_key: true| 
|image|string|null: false| 

### Association
- belong_to :item

## commentsテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|item_id|integer|null: false, foreign_key: true|
|text|text|null: false|

### Association
- belongs_to :user
- belongs_to :items

## nice(いいね)テーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false,foreign_key: true|
|item_id|integer|null: false,foreign_key: true|
|number|integer|null: false|

### Association
- belong_to :user
- belong_to :item


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