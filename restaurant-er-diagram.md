````mermaid
erDiagram
    Restaurant {
        int uniqueID PK
        Text name
        Text address
        Text phoneNumber
        Date createdAt
        Date updatedAt
    }
    DiningRoom  {
        int uniqueID PK
        int restaurantID FK
        Date createdAt
        Date updatedAt
    }
    Booking{
        int uniqueID PK
        int tableNumber FK
        int customerID FK
        Text time
        Text date
        Date createdAt
        Date updatedAt
    }
    Table{
        int number PK
        int diningRoomID FK
        int chairs
        bool available
        Date createdAt
        Date updatedAt
    }
    Customer{
        int uniqueID PK
        Text firstName
        Text lastName
        Text phoneNumber
        Date createdAt
        Date updatedAt
    }
    
    Restaurant ||--|{ DiningRoom : ""
    DiningRoom ||--o{ Table : ""
    Table ||--o{ Booking : ""
    Customer ||--o{ Booking : ""
````