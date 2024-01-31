````mermaid
erDiagram
    Book{
        int uniqueID PK
        int author FK
        Text title
        int pageCount
        Text language
        Date published
    }
    
    Author{
        int uniqueID PK
        Text firstName
        Text lastName
    }
    Library{
        int uniqueID PK
        Text phoneNumber
        Text eMail
        Text address
    }
    Reservation{
        int uniqueID PK
        int studentID FK
        Date dueDate
    }
    Student{
        int uniqueID PK
        Text firstName
        Text lastName
        Text loancardNum
    }
    BookReservation{
        int uniqueID PK
        int bookID FK
        int reservarionID FK
    }

    Student ||--o{ Reservation : "makes"
    Book }o--|| Reservation : "in"
    Book }o--|| Library : "in"
    Author }|--o{ Book : "writes"
    Book ||--|| BookReservation : ""
    Reservation ||--|| BookReservation : ""
````