```uml
@startuml

skinparam class {
    '図の背景
    BackgroundColor Snow
    '図の枠
    BorderColor Black
    'リレーションの色
    ArrowColor Black
}

!define MASTER_MARK_COLOR Orange 
!define TRANSACTION_MARK_COLOR DeepSkyBlue

package "AnyPort" as target_system {
    /'
      マスターテーブルを M、トランザクションを T などで表記
      １文字なら "主" とか "従" まど日本語でも記載可能
     '/
    
    
    entity "ユーザーマスタ" as users  <m_users> <<M,MASTER_MARK_COLOR>> {
        + user_id[PK]
        --
        user_name
        user_image
        user_mail
        user_pass
        age
        sex_Flag
        reg_date
        upd_date
        del_date
    }
    
    entity "プレユーザーマスタ" as pre_users  <m_pre_users> <<M,MASTER_MARK_COLOR>> {
        + pre_user_id[PK]
        --
        pre_user_mail
        pre_user_token
        reg_date
        upd_date
        del_date
    }
    
    entity "コースマスタ" as course <m_course> <<M,MASTER_MARK_COLOR>> {
        + course_id [PK]
        --
        course_name
        user_id
        checkpoint_num
        reg_date
        upd_date
        del_date
    }
    
    entity "コースカテゴリマスタ" as courseCategory <m_courseCategory> <<M,MASTER_MARK_COLOR>> {
        + course_id [PK][FK]
        + courseCategory_id [PK][FK]
        --
        reg_date
        upd_date
        del_date
    }
    
    
    entity "コースカテゴリIDマスタ" as m_courseCategoryID <m_courseCategoryID> <<M,MASTER_MARK_COLOR>> {
        + courseCategory_id [PK]
        --
        course_name
        reg_date
        upd_date
        del_date
    }
    
     entity "チェックポイントマスタ" as checkpoint <m_checkpoint> <<M,MASTER_MARK_COLOR>> {
        + checkpoint_id [PK]
        --
        checkpoint_name
        checkpoint_latitude
        checkpoint_longitude
        shop_explanation
        reg_date
        upd_date
        del_date
    }
    
     entity "チェックポイントカテゴリマスタ" as checkpointCategory <m_checkpointCategory> <<M,MASTER_MARK_COLOR>> {
        + checkpoint_id [PK][FK]
        + checkpointCategory_id [PK][FK]
        --
        reg_date
        upd_date
        del_date
    }
    
     entity "チェックポイントIDマスタ" as checkpointCategoryID <m_checkpointCategoryID> <<M,MASTER_MARK_COLOR>> {
        + checkpointCategory_id [PK]
        --
        checkpoint_name
        reg_date
        upd_date
        del_date
    }
    
     entity "コースチェックポイントマスタ" as m_course_checkpoint <m_course_checkpoint> <<M,MASTER_MARK_COLOR>> {
        + course_id [PK][FK]
        + checkpoint_id [PK][FK]
        --
        user_id
        checkpoint_num
        reg_date
        upd_date
        del_date
    }
    
     entity "コースヒストリテーブル" as CourseHistory <t_CourseHistory> <<T,TRANSACTION_MARK_COLOR>> {
        + courseHistory_id [PK]
        + user_id [PK][FK]
        --
        course_id
        start_time
        end_time
        distance
        end_Flag
        reg_date
        del_date
    }
    
    entity "コースチェックポイントテーブル" as t_course_checkpoint_History <t_course_checkpoint_History> <<T,TRANSACTION_MARK_COLOR>> {
        + checkpointHistory_id [PK]
        + user_id [PK][FK]
        --
        checkpoint_id
        start_time
        end_time
        distance
        end_Flag
        reg_date
        del_date
    }
    
    entity "マイコーステーブル" as myCourse <t_myCourse> <<T,TRANSACTION_MARK_COLOR>> {
        + mycourse_id [PK]
        + user_id [PK][FK]
        --
        course_id
        reg_date
        upd_date
        del_date
    }
    
        
    entity "検索履歴テーブル" as searchHistory <t_searchHistory> <<T,TRANSACTION_MARK_COLOR>> {
        + user_id [PK][FK]
        + searchHistory_id [PK]
        --
        searchWord
        reg_date
        upd_date
        del_date
    }
    
    
    
    
    
    
    
    
    entity "お気に入りテーブル" as favorite <t_favorite> <<T,TRANSACTION_MARK_COLOR>> {
        + user_id [PK][FK]
        + favorite_id [PK]
        --
        shop_id [FK]
        item_id [FK]
        reg_date
        upd_date
        del_date
    }
    
    entity "カートテーブル" as cart <t_cart> <<T,TRANSACTION_MARK_COLOR>> {
        + user_id [PK][FK]
        + cart_id [PK]
        --
        # shop_id [FK]
        # item_id [FK]
        item_count
        reg_date
        upd_date
        del_date
    }
    
    entity "購入履歴テーブル" as purchaseHistory <t_purchaseHistory> <<T,TRANSACTION_MARK_COLOR>> {
        + user_id [PK][FK]
        + purchaseHistory_id [PK]
        --
        purchase_num
        # shop_id [FK]
        # item_id [FK]
        item_count
        reg_date
        upd_date
        del_date
    }
    
    entity "お知らせテーブル" as information <t_information> <<T,TRANSACTION_MARK_COLOR>> {
        + intformation_id [PK]
        --
        title
        text
        reg_date
        upd_date
        del_date
    }

  }

shopItems             }o-le-o|   shop
shopItems             }o-ri-o|   iCategoryId
shopItems             }o-do-o|   purchaseHistory
shopItems             }o-do-o|   cart
shopItems             }o-do-o|   favorite
searchHistory         }o-le-o|   users
users                 |o-up-o|   purchaseHistory
users                 |o-up-o|   cart
users                 |o-up-o|   favorite
pre_users             }o-ri-o|   users
       

@enduml
```

