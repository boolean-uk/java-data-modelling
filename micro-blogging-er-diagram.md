````mermaid
erDiagram
    User{
        
    }
    Post{
        
    }
    Like{
        
    }
    Comment{
        
    }
    Follow{
        
    }
    Block{
        
    }
    
    User ||--o{ Post : "posts"
    User ||--o{ Comment : "makes"
    Post ||--o{ Comment : "has"
    User ||--o{ Follow : "followed_by"
    User ||--o{ Block : "blocked_by"
    User ||--o{ Like : "does"
    Post ||--o{ Like : "has"

````