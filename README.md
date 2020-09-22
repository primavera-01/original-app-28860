# アプリケーション名　original
<br>
<br>

# アプリケーション概要
- ゲーム専門の売買、チャットルームを備えたアプリケーションになります。
  コンセプトとしてはただゲームの売買を目的とするだけでなく、チャットルームなどを
  使い共通のジャンルに興味のある仲間を見つけることになります。
  機能につきましては今後、逐次導入していきます。
<br>
<br>

# herokuのURL

 []
<br>
<br>

# test用のアカウント

出品者アカウント名 test1
email              aaa@test.com
password           1qazxs

購入者アカウント test2
email              bbb@test.jp
password           1qazxs

# test用　クレジットカード

クレジット番号       4242424242424242
期限               3/23
セキュリティーコード  123

# テーブル設計

## users テーブル

| Column            | Type      | Options     |
| --------          | --------- | ----------- |
| nickname          | string    | null: false |
| email             | string    | null: false |
| password          | string    | null: false |
| first_name        | string    | null: false |
| family_name       | string    | null: false |
| first_name_kana   | string    | null: false |
| family_name_kana  | string    | null: false |
| birth_day         | date      | null: false |

### Association

- has_many :orders
- has_many :items

## orders テーブル

| Column            | Type      | Options                      |
| ------            | --------- | -----------                  |
| user              | references| null: false foreign_key: true|
| item              | references| null: false foreign_key: true|

### Association

- belongs_to :user
- has_one :destination
- belongs_to :item

## destination テーブル

| Column           | Type      | Options       |
| ------           | ---------- | ------------ |
| prefecture       | integer    | null:false   |
| post_code        | string     | null: false  |
| city             | string     | null: false  |
| house_number     | string     | null: false  |
| building_name    | string     |              |
| telephone_number | string     | unique: true |
| order            | references | null: false  |

### Association

- belongs_to :order

## items テーブル

| Column               | Type      | Options                      |
| ---------------------| ----------| ---------------------------  |
| name                 | string    | null:false                   |
| introduction         | text      | null: false                  |
| price                | integer   | null: false                  |
| condition_id         | integer   | null: false                  |
| shipping_date_id     | integer   | null: false                  |
| category_id          | integer   | null: false                  |
| prefecture_id        | integer   | null: false                  |
| shipping_location_id | integer   | null: false                  |
| user                 | references| null: false foreign_key: true|

### Association

- belongs_to :user
- has_one    :order

## chats テーブル

| Column               | Type      | Options                      |
| ---------------------| ----------| ---------------------------  |
| user                 | references| null: false foreign_key: true|
| message              | text      | null:false                   |

### Association

- has_one :user