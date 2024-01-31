````mermaid
erDiagram
    Shop {
        int uniqueID PK
        Text name
        Text address
        Text phoneNumber
    }
    Product {
        int uniqueID PK
        Text name
        Text type
        Text description
        double price
        int stock
    }
    Customer    {
        int uniqueID PK
        Text firstName
        Text lastName
        Text eMail
        Text username
        Text password
    }
    Order {
        int uniqueID PK
        int customerID FK
        Date createdAt
        Date updatedAt
    }
    OrderHistory  {
        int uniqueID PK
        int orderID FK
    }
    OrderProduct {
        int uniqueID PK
        int orderID FK
        int productID FK
    }
    

    OrderItem ||--o{ Product : ""
    OrderItem ||--|| Order : ""
    Shop ||--o{ Product : "sells"
    Shop ||--|| OrderHistory : "has"
    Product }o--|| Order : "in"
    Customer ||--|| Order : "places"
    OrderHistory ||--o{ Order : "tracks"
````