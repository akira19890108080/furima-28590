# テーブル設計

## users テーブル

| Column        | Type    | Options     |
| --------      | ------  | ----------- |
| nickname      | string  | null: false |
| email         | string  | null: false |
| password      | string  | null: false |
| name          | string  | null: false |
| name katakana | string  | null: false |
| birthday      | integer | null: false |

Association

- has_many :items
- has_one  :buys
- has_one  :Shipping address

## items テーブル

| Column             | Type       | Options                        |
| ---------          | ---------- | ------------------------------ |
| Product name       | string     | null: false                    |
| Explanation        | text       | null: false                    |
| Product Details    | text       | null: false                    |
| delivery           | text       | null: false                    |
| price              | integer    | null: false                    |
| user               | references | null: false, foreign_key: true |

Association

- belongs_to :user
- has_one  :buy
- has_one  :Shipping address

## buys テーブル

| Column    　　　| Type          | Options                        |
| ----------　　　| ----------    | ------------------------------ |
| card number    | integer       | null: false                    |
| Deadline       | integer       | null: false                    |
| security code  | integer       | null: false                    |
| user           | references    | null: false, foreign_key: true |
| item           | references    | null: false, foreign_key: true |


Association

- belongs_to :user
- belongs_to :item
- has_one  :Shipping address

## Shipping address テーブル

| Column            | Type          | Options                        |
| ----------        | ----------    | ------------------------------ |
| Postal code       | integer       | null: false                    |
| Prefectures       | string        | null: false                    |
| Municipality      | text          | null: false                    |
| address           | text          | null: false                    |
| Building name     | text          |                                |
| phone number      | integer       | null: false                    |
| user              | references    | null: false, foreign_key: true |
| prototype         | references    | null: false, foreign_key: true |


Association

- belongs_to :user
- belongs_to :item
- belongs_to :buy

