```uml
@startuml

state ﾊﾝﾊﾞｰｶﾞｰﾒﾆｭｰ{
カレンダー:do/カレンダーを表示
設定:do/
ログアウト:do/
}

state menu{
mypage:do/Mypageへ遷移
cyclring:do/mapへ遷移
post:do/
}

mypage-left->マイページ
cyclring-down->map
post-right->投稿一覧

[*]-down->ログイン
ログイン:enter/ユーザー名
ログイン:enter/パスワード
ログイン:do/アカウント作成
ログイン-down->新規アカウント
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
Myfavorite-down->投稿詳細
投稿詳細:do/お気に入り機能
投稿詳細:do/Go
投稿詳細:do/back
Mydata-down->ルート詳細
ルート詳細:do/共有
ルート詳細-right->共有ルート :共有クリック
createroute-down->開始
開始:do/Yes
開始:do/No
開始-right->cyclring開始
cyclring開始:do/中断
cyclring開始-right->中断
中断:do/Yes
中断:do/No


@enduml
```
