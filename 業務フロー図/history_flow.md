```
@startuml

ユーザー -> webサーバー : 履歴一覧の選択
webサーバー -> DBサーバー : 履歴一覧の要求
DBサーバー -> webサーバー

@enduml
```
