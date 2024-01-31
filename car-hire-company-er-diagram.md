````mermaid
erDiagram
    Company {
        int uniqueID PK
        Text name
        Text address
        Text phoneNumber
        Text eMail
    }
    Cars {
        int uniqueID PK
        int carID FK
    }
    Car {
        int uniqueID PK
        Text make
        Text model
        Text color
        Text fuelType
        Text transmission
        int seatCount
        double cargoSpace
    }
    Customer {
        int uniqueID PK
        Text firstName
        Text lastName
        Text eMail
        Text phoneNumber
    }
    Booking {
        int uniqueID PK
        int customerID FK
        int locationID FK
        int carID FK
        Text date
    }
    Location{
        int uniqueID PK
        Text city
        Text address
    }
    LocationCar {
        int uniqueID PK
        int locationID FK
        int carID FK
    }
    Company ||--|| Cars : "owns"
    Car }|--|| Booking : "in"
    Cars ||--o{ Car : "has"
    Customer ||--|| Booking : "makes"
    Car }o--|| Location : "is_at"
````