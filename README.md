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
| product_name          | string     | null: false                    |
| price                 | integer    | null: false                    |
| user                  | references | null: false, foreign_key: true |
| category_id           | integer    | null: false                    |
| product_condition_id  | integer    | null: false                    |
| shipping_charges_id   | integer    | null: false                    |
| prefecture_id         | integer    | null: false                    |
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
| postal_code       | string        | null: false                    |
| prefectures_id    | integer       | null: false                    |
| municipality      | string        | null: false                    |
| address           | string        | null: false                    |
| building_name     | string        |                                |
| phone_number      | string        | null: false                    |
| buy               | references    | null: false, foreign_key: true |

Association

- belongs_to :buy


