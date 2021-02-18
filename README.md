# README

# アプリケーション名
anichat

# アプリケーション概要
アニメ、声優について話し合えるアプリです

実装機能は以下の通りです

・新規登録機能
・ログイン機能
・チャットルーム作成機能
・画像アップロード機能
・メッセージ投稿機能
・チャットルーム作成機能
・チャットルーム削除機能
・アカウント編集機能

使用言語
・Ruby
・Ruby on rails
・HTML
・CSS
・JavaScript

# アプリケーションのURL


# 制作背景
好きなアニメ、声優を好きな人同士で語り合えるためです。
このアニメ、声優が好きで好きな人同士で意見を言い合って共感して欲しいと言った気持ちを解消してくれる目的で作成しました。
また、このアニメ、声優が気になる、知ろうとしてるなどの場合にも活用できます。そのチャットに入りわかる人に魅力など聞き出せるといったメリットがあります。またアニメのこのキャラクター、このシーンが好き、この声優さんのこの画像がとても可愛いと言ったことも共有できるように画像投稿機能を実装して視覚でも魅力を伝えることができるように実装していきました。

## users テーブル

| Column   | Type   | Options     |
| -------- | ------ | ----------- |
| name     | string | null: false |
| email    | string | null: false |
| password | string | null: false |

### Association

- has_many :room_users
- has_many :rooms, through: room_users
- has_many :messages

## rooms テーブル

| Column | Type   | Options     |
| ------ | ------ | ----------- |
| name   | string | null: false |

### Association

- has_many :room_users
- has_many :users, through: room_users
- has_many :messages

## room_users テーブル

| Column | Type       | Options                        |
| ------ | ---------- | ------------------------------ |
| user   | references | null: false, foreign_key: true |
| room   | references | null: false, foreign_key: true |

### Association

- belongs_to :room
- belongs_to :user

## messages テーブル

| Column  | Type       | Options                        |
| ------- | ---------- | ------------------------------ |
| content | string     |                                |
| user    | references | null: false, foreign_key: true |
| room    | references | null: false, foreign_key: true |

### Association

- belongs_to :room
- belongs_to :user