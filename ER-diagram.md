# Entity Relationship Diagrams

ER-diagrams using [Mermaid.js](https://mermaid.js.org/syntax/entityRelationshipDiagram.html).

## Core Exercise - Restaurant Booking System
```mermaid
---
    title: Dinner Booking
---
erDiagram
    CUSTOMER ||--o{ BOOKING : requests
    CUSTOMER {
        int customerId PK
        string name
        string email
    }
    BOOKING ||--|{ TABLE : contains
    BOOKING {
        int bookingID PK
        LocalDateTime dateTime
        int numOfPeople
        int tableId FK
        int CustomerId FK
    }
    TABLE {
        int tableId PK
        int numOfSeats
        boolean isAvailable
    }
```

## Extension Exercises

### 1. Local Candle Maker
#### User Stories
- As a customer, so I can order candles and artifacts, I want to place an order in the online shop.
- As the Candle Shop owner, so that I can manage my business effectively I want to be able to add and update products of a given product type.
- As the Candle Shop owner, so that I can re-stock products, I want to be able to see the number of items in stock.
- As the Candle Shop owner, so I can notify customers when items are back in stock, I want to be able to see the delivery status of the products.

```mermaid
---
    title: Candle & Artifacts Shopping
---
erDiagram
    CUSTOMER ||--o{ ORDER : places
    CUSTOMER {
        int customerId PK
        string name
        string email
    }
    ORDER ||--|{ ORDER_ITEM : contains
    ORDER {
        int orderID PK
        LocalDateTime dateTime
        int CustomerId FK
    }
    ORDER_ITEM {
        int orderId FK
        int productId FK
        int numOfProducts
    }
    ORDER_ITEM ||--|| PRODUCT : contains
    PRODUCT {
        int productId PK
        String productType
        String description
        double price
        String imageURL
    }
    STORAGE ||--o{ PRODUCT : contains
    STORAGE {
        int productId FK
        int numOfItemsInStock
        boolean orderIsPlaced
        LocalDateTime deliveryDate
    }
    
```