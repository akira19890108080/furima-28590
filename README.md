# テーブル設計

## users テーブル

| Column              | Type    | Options     |
| --------            | ------  | ----------- |
| nickname            | string  | null: false |
| email               | string  | unique: true |
| encrypted_password  | string  | null: false |
| first_name          | string  | null: false |
| last_name           | string  | null: false |
| first_name_katakana | string  | null: false |
| last_name_katakana  | string  | null: false |
| birthday            | date    | null: false |

Association

- has_many :items
- has_many :buys


## items テーブル

| Column                | Type       | Options                        |
| ---------             | ---------- | ------------------------------ |
| Product name          | string     | null: false                    |
| Explanation           | text       | null: false                    |
| Product Details       | text       | null: false                    |
| delivery              | text       | null: false                    |
| price                 | integer    | null: false                    |
| user                  | references | null: false, foreign_key: true |
| category_id           | integer    | null: false                    |
| product_condition_id  | integer    | null: false                    |
| shipping_charges_id   | integer    | null: false                    |
| shipping_area_id      | integer    | null: false                    |
| days_to_ship_id       | integer    | null: false                    |

Association

- belongs_to :user
- has_one  :buy

## buys テーブル

| Column         | Type          | Options                        |
| ----------     | ----------    | ------------------------------ |
| user           | references    | null: false, foreign_key: true |
| item           | references    | null: false, foreign_key: true |


Association

- belongs_to :user
- belongs_to :item
- has_one  :Shipping address

## Shipping address テーブル

| Column            | Type          | Options                        |
| ----------        | ----------    | ------------------------------ |
| Postal_code       | string        | null: false                    |
| Prefectures_id    | integer       | null: false                    |
| Municipality      | string        | null: false                    |
| address           | string        | null: false                    |
| Building_name     | string        |                                |
| phone_number      | string        | null: false                    |
| buy               | references    | null: false, foreign_key: true |

Association

- belongs_to :buy


