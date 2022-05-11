```uml
@startuml

state menu{
mypage:マイページへ
cyclring:マップへ
post:投稿一覧へ
}

state Login{
ログイン:メールアドレス
ログイン:パスワード
ログイン:アカウント作成

ログイン-left->新規アカウント

新規アカウント:ユーザー名
新規アカウント:メールアドレス
新規アカウント:パスワード
新規アカウント:再パスワード
新規アカウント:性別選択
}

Login-down->Mypage

state Mypage{
マイページ:ユーザー名
マイページ:ID
マイページ:アイコン
マイページ:走行距離
マイページ-down->お気に入り
マイページ-down->データ
マイページ-down->作成ルート
}

state Map{

}

state Post{

}

@enduml
```
