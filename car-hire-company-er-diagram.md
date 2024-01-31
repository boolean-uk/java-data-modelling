````mermaid
erDiagram
    Company {
        
    }
    Cars {
        
    }
    Car {
        
    }
    Customer {
        
    }
    Booking {
        
    }
    Company ||--|| Cars : "owns"
    Car }|--|| Booking : "in"
    Cars ||--o{ Car : "has"
    Customer ||--|| Booking : "makes"
````