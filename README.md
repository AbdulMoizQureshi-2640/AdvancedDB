```mermaid
erDiagram
    ApplicationUser {
        string Id PK
        string FirstName
        string LastName
        string Email
        int? EmployeeId FK
    }
    Employee {
        int EmployeeId PK
        string FirstName
        string LastName
        int DepartmentId FK
        int PositionId FK
    }
    Department {
        int DepartmentId PK
        string DepartmentName
    }
    Position {
        int PositionId PK
        string PositionTitle
        int DepartmentId FK
    }
    Order {
        int OrderId PK
        int CustomerId FK
        int EmployeeId FK
        int ShipperId FK
        DateTime OrderDate
        DateTime RequiredDate
        string ShipName
        string ShipAddress
        string ShipCity
        string ShipCountry
        string Status
        string Notes
    }
    OrderDetail {
        int OrderDetailId PK
        int OrderId FK
        int ProductId FK
        int Quantity
        decimal UnitPrice
        decimal Discount
    }
    Product {
        int ProductId PK
        string ProductName
        int SupplierId FK
        int CategoryId FK
        string QuantityPerUnit
        decimal UnitPrice
        int UnitsInStock
        int UnitsOnOrder
        int ReorderLevel
        bool Discontinued
    }
    Category {
        int CategoryId PK
        string CategoryName
        string Description
    }
    Supplier {
        int SupplierId PK
        string CompanyName
        string ContactName
        string ContactTitle
        string Email
        string Address
        string City
        string Region
        string PostalCode
        string Country
        string Phone
        string Fax
        string HomePage
    }
    Customer {
        int CustomerId PK
        string CompanyName
        string ContactName
        string ContactTitle
        string Email
        string Phone
        string Address
        string City
        string Country
    }
    Shipper {
        int ShipperId PK
        string CompanyName
        string PhoneNumber
        string Email
        string Address
        string City
        string State
        string PostalCode
        string Country
    }
    Invoice {
        int InvoiceId PK
        int OrderId FK
        string InvoiceNumber
        DateTime InvoiceDate
        decimal Subtotal
        decimal Tax
        decimal Total
        decimal AmountPaid
        decimal BalanceDue
        string Status
    }
    InvoicePayment {
        int PaymentId PK
        int InvoiceId FK
        DateTime PaymentDate
        decimal Amount
        string PaymentMethod
        string TransactionId
        string Status
    }

    ApplicationUser ||--o{ Employee : "has"
    Employee ||--o{ Order : "places"
    Department ||--o{ Employee : "belongs to"
    Position ||--o{ Employee : "holds"
    Order ||--o{ OrderDetail : "contains"
    OrderDetail ||--o{ Product : "references"
    Product ||--o{ Category : "belongs to"
    Product ||--o{ Supplier : "supplied by"
    Order ||--o{ Customer : "placed by"
    Order ||--o{ Shipper : "shipped by"
    Order ||--o{ Invoice : "generates"
    Invoice ||--o{ InvoicePayment : "receives"
```
