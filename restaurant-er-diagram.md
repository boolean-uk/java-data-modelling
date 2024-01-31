````mermaid
erDiagram
    Restaurant {
        int uniqueID PK
        Text name
        Text address
        Text phoneNumber
    }
    DiningRoom  {
        int uniqueID PK
        int restaurantID FK
    }
    Booking{
        int uniqueID PK
        int tableNumber FK
        int customerID FK
        Text time
        Text date
    }
    Table{
        int number PK
        int diningRoomID FK
        int chairs
        bool available
    }
    Customer{
        int uniqueID PK
        Text firstName
        Text lastName
        Text phoneNumber
    }
    
    Restaurant ||--|{ DiningRoom : ""
    DiningRoom ||--o{ Table : ""
    Table ||--o{ Booking : ""
    Customer ||--o{ Booking : ""
````