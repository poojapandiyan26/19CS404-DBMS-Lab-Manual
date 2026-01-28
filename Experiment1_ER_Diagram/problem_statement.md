# Experiment 1 – ER Diagram

## Objective
To understand and apply ER modeling concepts by creating ER diagrams for real-world applications.

## Purpose
Gain hands-on experience in designing ER diagrams that represent database structure including entities, relationships, attributes, and constraints.

---

# Scenario A: City Fitness Club Management

**Business Context:**  
FlexiFit Gym wants a database to manage its members, trainers, and fitness programs.

**Requirements:**  
- Members register with name, membership type, and start date.  
- Each member can join multiple programs (Yoga, Zumba, Weight Training).  
- Trainers assigned to programs; a program may have multiple trainers.  
- Members may book personal training sessions with trainers.  
- Attendance recorded for each session.  
- Payments tracked for memberships and sessions.

### ER Diagram
<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/1613344d-eef7-49e1-874d-74a630069624" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
| Member | **Member_ID (PK)**, Name, Membership_Type, Start_Date, Phone | Each gym member |
| Trainer | **Trainer_ID (PK)**, Name, Specialization, Phone | Trainers available |
| Program | **Program_ID (PK)**, Program_Name, Fee | Yoga, Zumba, etc. |
| Session | **Session_ID (PK)**, Session_Date, Time, **Trainer_ID (FK)**, **Member_ID (FK)** | Personal training session |
| Payment | **Payment_ID (PK)**, Amount, Payment_Date, Payment_Type, **Member_ID (FK)** | Membership/session payments |
| Attendance | **Attendance_ID (PK)**, Status, **Session_ID (FK)** | Present/Absent |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
| Member–Program | M:N | Total | Members can join many programs |
| Program–Trainer | M:N | Partial | Program may have multiple trainers |
| Member–Session | 1:M | Total | Member can book many sessions |
| Trainer–Session | 1:M | Total | Trainer conducts many sessions |
| Member–Payment | 1:M | Total | Payments tracked per member |

### Assumptions
- Each member must enroll in at least one program  
- Trainers can handle multiple programs  
- Attendance is recorded only for personal sessions  

---

# Scenario B: City Library Event & Book Lending System

**Business Context:**  
The Central Library wants to manage book lending and cultural events.

**Requirements:**  
- Members borrow books, with loan and return dates tracked.  
- Each book has title, author, and category.  
- Library organizes events; members can register.  
- Each event has one or more speakers/authors.  
- Rooms are booked for events and study.  
- Overdue fines apply for late returns.

### ER Diagram
<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/fa9e56b1-b6cd-4464-b948-5f7fcab2abd8" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
| Member | **Member_ID (PK)**, Name, Address, Phone | Library members |
| Book | **Book_ID (PK)**, Title, Author, Category | Books in library |
| Loan | **Loan_ID (PK)**, Loan_Date, Return_Date, **Member_ID (FK)**, **Book_ID (FK)** | Book lending |
| Event | **Event_ID (PK)**, Event_Name, Event_Date | Cultural events |
| Speaker | **Speaker_ID (PK)**, Name, Expertise | Event speakers |
| Room | **Room_ID (PK)**, Room_Name, Capacity | Library rooms |
| Fine | **Fine_ID (PK)**, Amount, **Loan_ID (FK)** | Overdue fines |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
| Member–Book | M:N | Partial | Through Loan entity |
| Event–Speaker | M:N | Total | Events have speakers |
| Event–Room | 1:1 | Total | Each event in one room |
| Loan–Fine | 1:0..1 | Partial | Fine only if overdue |

### Assumptions
- A book can be loaned to only one member at a time  
- Fine is applicable only after due date  
- Members may attend multiple events  

---

# Scenario C: Restaurant Table Reservation & Ordering

**Business Context:**  
A popular restaurant wants to manage reservations, orders, and billing.

**Requirements:**  
- Customers can reserve tables or walk in.  
- Each reservation includes date, time, and number of guests.  
- Customers place food orders linked to reservations.  
- Each order contains multiple dishes; dishes belong to categories (starter, main, dessert).  
- Bills generated per reservation, including food and service charges.  
- Waiters assigned to serve reservations.

### ER Diagram
<img width="1536" height="1024" alt="image" src="https://github.com/user-attachments/assets/012678f3-6220-4bc7-8242-2765b66d138d" />


### Entities and Attributes

| Entity | Attributes (PK, FK) | Notes |
|--------|--------------------|-------|
| Customer | **Customer_ID (PK)**, Name, Phone | Walk-in or reserved |
| Reservation | **Reservation_ID (PK)**, Date, Time, Guests, **Customer_ID (FK)** | Table booking |
| Table | **Table_ID (PK)**, Capacity | Restaurant tables |
| Order | **Order_ID (PK)**, Order_Time, **Reservation_ID (FK)** | Food order |
| Dish | **Dish_ID (PK)**, Dish_Name, Price, Category | Menu items |
| Bill | **Bill_ID (PK)**, Total_Amount, Service_Charge, **Reservation_ID (FK)** | Final bill |
| Waiter | **Waiter_ID (PK)**, Name, Phone | Service staff |

### Relationships and Constraints

| Relationship | Cardinality | Participation | Notes |
|--------------|------------|---------------|-------|
| Customer–Reservation | 1:M | Partial | Customer may walk in |
| Reservation–Table | 1:1 | Total | One table per reservation |
| Reservation–Order | 1:M | Total | Multiple orders possible |
| Order–Dish | M:N | Total | Multiple dishes per order |
| Waiter–Reservation | 1:M | Partial | Waiter serves reservations |

### Assumptions
- Walk-in customers are recorded without reservation  
- One bill is generated per reservation  
- A waiter may serve multiple tables  

---

## Instructions for Submission
1. Complete all three scenarios (A, B, C).  
2. Insert your ER diagrams (`.png` images) in the same folder.  
3. Export or submit as a **single PDF** if required.  
4. Commit and push to GitHub.  
5. Copy the **repository link** to Moodle.

