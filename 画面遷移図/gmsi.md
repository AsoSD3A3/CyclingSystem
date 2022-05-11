```uml
@startuml
[*]-down->マイページ
マイページ:ユーザー名
マイページ:ID
マイページ:アイコン
マイページ:走行距離
マイページ-->Myfavorite
マイページ-->Mydata
マイページ-->createroute

state menu{
カレンダー:do/カレンダーを表示
設定:do/
ログアウト:do/
}
state 掲示板{

}

state 設定{

}

@enduml
```
