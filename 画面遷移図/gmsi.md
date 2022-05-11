```uml
@startuml

state menu{
カレンダー:do/カレンダーを表示
設定:do/
ログアウト:do/
}

[*]-down->ログイン
ログイン:enter/ユーザー名
ログイン:enter/パスワード
ログイン:do/アカウント作成
ログイン-left->新規アカウント
新規アカウント:enter/ユーザー名
新規アカウント:enter/メールアドレス
新規アカウント:enter/パスワード
新規アカウント:enter/再パスワード
新規アカウント:do/性別
新規アカウント-down->マイページ :sign inクリック
ログイン-down->マイページ : Loginクリック
マイページ:ユーザー名
マイページ:ID
マイページ:アイコン
マイページ:走行距離
マイページ-->Myfavorite :favoクリック
マイページ-->Mydata :datクリック
マイページ-->createroute :creクリック
Myfavorite:do/お気に入り一覧表示
Mydata:do/data表示
Mydata:do/過去ルート表示
createroute:do/作成ロート一覧表示

@enduml
```
