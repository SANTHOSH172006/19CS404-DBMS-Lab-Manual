# ER Diagram Workshop – Submission Template

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Restaurant Table Reservation & Ordering

**Business Context:**  
A popular restaurant wants to manage reservations, orders, and billing.

**Requirements:**  
- Customers can reserve tables or walk in.  
- Each reservation includes date, time, and number of guests.  
- Customers place food orders linked to reservations.  
- Each order contains multiple dishes; dishes belong to categories (starter, main, dessert).  
- Bills generated per reservation, including food and service charges.  
- Waiters assigned to serve reservations.

### ER Diagram:

<img width="4002" height="1581" alt="erdplus (2)" src="https://github.com/user-attachments/assets/b6c73a8f-8ce2-4e87-81c8-fe4530a5f598" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|---------------------|-------|
| Customer | CustomerID (PK), Name, PhoneNumber, TableNumber | Stores customer details |
| Waiter | WaiterID (PK), Name, ContactDetails, Experience | Stores waiter details |
| Chef | ChefID (PK), Name, ContactDetails, Speciality | Stores chef details |
| Table | TableID (PK), Location, Status, SeatingCapacity | Stores table information |
| FoodItem | FoodItemID (PK), Name, Price, Category, Availability | Stores menu information |
| Order | OrderID (PK), OrderDate, TotalAmount, Status, WaiterID (FK), TableID (FK) | Stores order details |
| OrderItem | OrderItemID (PK), OrderID (FK), FoodItemID (FK), Quantity, ItemStatus | Stores ordered items |
| Bill | BillID (PK), OrderID (FK), Amount, PaymentStatus, PaymentDate | Stores billing details |
| Supervisor | SupervisorID (PK), Name, ContactNumber, Department | Stores supervisor details |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|-------------|---------------|-------|
| Customer - Table (Assigned To) | Many-to-One | Customer: Total; Table: Partial | Customers are assigned to tables |
| Waiter - Table (Serves) | One-to-Many | Waiter: Partial; Table: Total | A waiter serves multiple tables |
| Waiter - Order (Creates) | One-to-Many | Waiter: Partial; Order: Total | A waiter creates multiple orders |
| Order - Table (Belongs To) | Many-to-One | Order: Total; Table: Partial | Each order belongs to one table |
| Order - OrderItem (Contains) | One-to-Many | Both: Total | An order contains multiple items |
| OrderItem - FoodItem (Selects) | Many-to-One | OrderItem: Total; FoodItem: Partial | Each order item refers to one food item |
| Order - Bill (Generates) | One-to-One | Order: Partial; Bill: Total | A bill is generated for an order |
| Chef - OrderItem (Prepares) | One-to-Many | Chef: Partial; OrderItem: Total | A chef prepares multiple items |
| Supervisor - Order (Monitors) | One-to-Many | Supervisor: Partial; Order: Partial | A supervisor monitors order issues |

### Assumptions

- Each entity has a unique primary key.
- Foreign keys connect related entities.
- Each customer is assigned to a table.
- A waiter can serve multiple tables and create multiple orders.
- Each order belongs to one table.
- An order contains one or more order items.
- Each order item refers to one food item.
- Food items have prices, categories, and availability.
- Each order can generate one bill.
- Each order item is prepared by one chef.
- Supervisors monitor order-related issues.
- Table status indicates whether a table is occupied or available.
- Payment status indicates whether the bill is paid or unpaid.

---
