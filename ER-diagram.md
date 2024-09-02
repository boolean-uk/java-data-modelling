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

### 2. Car Hire Company
#### User Stories
- As a customer, so I can go for a trip with my family, I want to hire a car in my hometown.
- As a customer, so I don't need to bring my own car to my vacation, I want to know if there is a car available nearby my hotel.
- As the Car Company owner, so that I can manage my business effectively I want to be able to manage the hourly price for renting a specific car model.

```mermaid
---
    title: Rent A Car Service
---
erDiagram
    CUSTOMER ||--o{ BOOKING : places
    CUSTOMER {
        int customerId PK
        string name
        string email
    }
    BOOKING ||--|| CAR : contains
    BOOKING {
        int bookingID PK
        LocalDateTime bookingCreatedDate
        LocalDateTime startDateTime
        localDateTime endDateTime
        int carId FK
        int customerId FK
    }
    CAR {
        int carId PK
        String model
        int year
        boolean isAvailable
        int locationId FK
    }
    LOCATION ||--|| CAR : associated
    LOCATION {
        int locationId PK
        String adress
    }
    CAR }|--|| PRICE_TABLE : associated
    PRICE_TABLE {
        String model FK
        int year FK
        double hourlyPrice
    }
```
### 3. University Library
#### User Stories
- As a user, so I borrow books, I want to see available books.
- As the Library administrator, so that I can manage the loans effectively, I want to be able to update the max number of books users can borrow.

```mermaid
---
    title: Library books and loans
---
erDiagram
    USER ||--o{ LOAN : requests
    USER {
        int userId PK
        string name
        string email
        int currentNumOfLoans "Max number 6"
    }
    LOAN ||--|{ BOOK : contains
    LOAN {
        int loanID PK
        int bookId FK
        int userId FK
    }
    BOOK {
        int bookId PK
        String title
        int numOfPages
        boolean isAvailable
    }
```

### 4. Social Media Site
#### User Stories
- As a user, so I can see what my friends are doing, I want to see my personal feed.
- As the Site owner, so that I can manage the business effectively, I want to be able to decide what a user will see in the personal feed.

```mermaid
---
    title: Micro-blogging
---
erDiagram
    USER ||--|| PERSONAL_FEED : shows
    USER {
        int userId PK
        string name
        string email
        LocalDateTime memberSince
    }
    PERSONAL_FEED ||--|{ BLOG_POST : contains
    BLOG_POST {
        int blogId PK
        LocalDateTime dateTimeCreated
        String text "Max number of characters are 150"
        int userId FK
    }
    BLOG_POST ||--|{ FRIEND : where
    FRIEND {
        int userID FK
        int friendId FK
    }
```

### 5. Online Learning
#### User Stories
- As a student, so I can get access to the course material, I want to see when I'm enrolled in a course.
- As a head teacher, so that I can manage the school effectively, I want to see the teacher responsible for different courses.
- As a teacher, so that I can give feedback to students, I want to be able to grade students en every course I'm responsible for.

```mermaid
---
    title: Micro-blogging
---
erDiagram
    STUDENT ||--|| ENROLLED : is
    STUDENT {
        int studentId PK
        string name
        string email
    }
    ENROLLED {
        int studentId FK
        int courseId FK
        boolean isEnrolled
    }
    ENROLLED ||--|{ COURSE : contains
    COURSE {
        int courseId PK
        String title
        String subject
    }
    TEACHER }|--o{ COURSE_RESPONSIBILITIES : associatedTo
    COURSE_RESPONSIBILITIES ||--|{ COURSE : contains
    COURSE_RESPONSIBILITIES {
        int teacherID FK
        int courseId FK
    }
    TEACHER {
        int teacherID FK
        String name
        String email
    }
```