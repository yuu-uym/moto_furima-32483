# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...
README.md
# テーブル設計

## users テーブル
| Column             | Type   | Options     |
| ------------------ | ------ | ----------- |
| nickname           | string | null: false |
| email              | string | null: false |
| encrypted_password | string | null: false |
| first_name         | string | null: false |
| last_name          | string | null: false |
| kana_first         | string | null: false |
| kana_family        | string | null: false |
| birth              | date   | null: false |

### Association

- has_many :items
- has_many :orders

## items テーブル
| Column               | Type       | Options                        |
| -------------------- | ---------- | -----------                    |
| name                 | string     | null: false                    |
| description          | text       | null: false                    |
| category_id          | integer    | null: false                    |
| condition_id         | integer    | null: false                    |
| delivery_fee_id      | integer    | null: false                    |
| prefectures_id       | integer    | null: false                    |
| day_to_delivery_id   | integer    | null: false                    |
| value                | integer    | null: false                    |
| user                 | references | null: false,foreign_key: true  | 

### Association

- belongs_to :user
- has_one :order
- belongs_to_active_hash :category
- belongs_to_active_hash :condition
- belongs_to_active_hash :delivery_fee
- belongs_to_active_hash :prefectures
- belongs_to_active_hash :day_to_delivery

## orders テーブル

| Column           | Type       | Options                        |
| -------------    | ---------- | ------------------------------ |
| postal_code      | string     | null: false                    |
| prefectures_id   | integer    | null: false                    |
| city             | string     | null: false                    |
| address          | string     | null: false                    |
| building_name    | string     |                                |
| phone_number     | string     | null: false                    |
| item_id          | integer    | null: false, foreign_key: true |

### Association

- belongs_to :item
- belongs_to :user
- has_one_active_hash :prefectures

