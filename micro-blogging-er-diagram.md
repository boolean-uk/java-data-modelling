````mermaid
erDiagram
    User{
        int uniqueID PK
        Text userName
        Text password
        Text eMail
        Text profileImageSource
        Text profileBannerSource
        Text profileBio
        Date userCreation
        Date birthday
        bool activated
        Date lastUpdated
    }
    Post{
        int uniqueID PK
        Text title
        Text content
        Date datePosted
        Date dateUpdated
    }
    Like{
        int uniqueID PK
        int userID FK
        int postID FK
        Date dateLiked
    }
    Comment{
        int uniqueID PK
        int userID FK
        int postID FK
        Text content
        Date dateCommented
        Date dateUpdated
    }
    Follow{
        int uniqueID PK
        int userID FK
        int followerUserID FK
        date dateFollowed
    }
    Block{
        int uniqueID PK
        int blockedUserID FK
        int blockedByUserID FK
        date dateBlocked
    }
    
    User ||--o{ Post : "posts"
    User ||--o{ Comment : "makes"
    Post ||--o{ Comment : "has"
    Post ||--o{ Like : "has"
    User ||--o{ Follow : "followed_by"
    User ||--o{ Block : "blocked_by"
    User ||--o{ Like : "does"


````