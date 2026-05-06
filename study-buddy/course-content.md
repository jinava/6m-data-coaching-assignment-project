# SQL Database Module — Course Content Reference
**Programme:** Data Science Bootcamp (6-Month)
**Module:** Unit 1 — SQL & Databases
**Compiled:** 2026-04-23

---

## Table of Contents

- [Lesson 1.2 — Intro to Databases](#lesson-12--intro-to-databases)
  - [Overview](#12-overview)
  - [Pre-Class Reading](#12-pre-class-reading)
  - [Lesson Plan](#12-lesson-plan)
  - [Assignment](#12-assignment)
  - [Reference](#12-reference)
- [Lesson 1.3 — SQL Basic: DDL](#lesson-13--sql-basic-ddl)
  - [Overview](#13-overview)
  - [Pre-Class Reading](#13-pre-class-reading)
  - [Lesson Plan](#13-lesson-plan)
  - [Assignment](#13-assignment)
  - [Reference](#13-reference)
  - [Data Files](#13-data-files)
  - [Scripts](#13-scripts)
- [Lesson 1.4 — SQL Basic: DML](#lesson-14--sql-basic-dml)
  - [Overview](#14-overview)
  - [Pre-Class Reading](#14-pre-class-reading)
  - [Lesson Plan](#14-lesson-plan)
  - [Assignment](#14-assignment)
  - [Reference](#14-reference)
  - [Scripts](#14-scripts)
- [Lesson 1.5 — SQL Advanced](#lesson-15--sql-advanced)
  - [Overview](#15-overview)
  - [Pre-Class Reading](#15-pre-class-reading)
  - [Lesson Plan](#15-lesson-plan)
  - [Assignment](#15-assignment)
  - [Reference](#15-reference)
  - [Scripts](#15-scripts)

---

# Lesson 1.2 — Intro to Databases

**Theme:** Designing the Blueprint — how data is stored, related, and organised

---

## 1.2 Overview

| Section | Duration | Topic / Activity |
|---------|----------|-----------------|
| **Part 1: The Data Landscape** | 55 min | Relational vs. NoSQL vs. Vector Databases; SQL Data Types |
| **Part 2: Building the Blueprint** | 55 min | Primary & Foreign Keys; Entity-Relationship Diagrams (ERD) |
| **Part 3: Organising Data** | 55 min | Database Normalisation — 1NF, 2NF, and 3NF |

### Learning Outcomes

By the end of this lesson, you will be able to:

1. **Analyse** the differences between Relational, NoSQL, and Vector databases and select the right type for a given use case.
2. **Apply** Primary Keys and Foreign Keys to design Entity-Relationship Diagrams (ERD) using DBML.
3. **Evaluate** an unnormalised dataset and decompose it into 3rd Normal Form (3NF).
4. **Create** a complete database schema for a real-world business scenario.

### Course Materials

| Material | Description | Est. Time |
|----------|-------------|-----------|
| Pre-Class | Database types, keys, and normalisation fundamentals | 30–45 min |
| Lesson Plan | Instructor guide for the 3-hour flipped classroom session | 3 hours |
| Assignment | FoodFast Database Design Challenge | 45–60 min |
| Reference | DBML syntax, ERD notation, and normalisation cheat sheet | As needed |

### Tools & Setup

- **[dbdiagram.io](https://dbdiagram.io):** Free browser-based ERD tool — create a free account before class.
- **DBML syntax:** Used for describing schemas; introduced in the pre-class material.
- **No installation required** for this lesson.

---

## 1.2 Pre-Class Reading

**Estimated Time:** 30–45 minutes
**Prerequisites:** Lesson 1.1 — The Data Landscape

> In Lesson 1.1 you learned what Data Analytics, Data Science, and AI are. This lesson goes one level deeper: before data can be analysed, it needs to be *stored* somewhere. This pre-class reading introduces how databases are structured and why the design decisions matter.

Complete the steps below **before your class session**. The in-class activities (building schemas for a Car Insurance company and an E-Commerce platform) build directly on these concepts.

---

### Step 1 — Watch the Video (10 min)

▶️ [A Brief History of Databases and Their Applications](https://www.youtube.com/watch?v=WDTbDiQqPdA)

A concise overview of why databases were invented, how they evolved from flat files to relational systems, and where modern databases (NoSQL, Vector) fit in. Watching this first will give you the historical context for everything in Steps 2 and 3.

---

### Step 2 — Read the Core Concepts (15 min)

#### The Database Landscape

Not all data is stored the same way. There are three main categories:

- **Relational (SQL):** Think of a **Bank Vault** — strict, organised, and safe. Used for financial records, user accounts, and inventory. (Examples: PostgreSQL, MySQL)
- **NoSQL:** Think of a **Messy Desk** — flexible and fast. You can store documents (JSON) without worrying about rigid structure. Used for social media feeds or sensor data. (Examples: MongoDB)
- **Vector:** Think of a **Brain** — stores data by *meaning* rather than keywords. Used for AI and similarity searches (e.g., "Find me a song that sounds sad"). (Examples: Pinecone, Weaviate)

#### The Anatomy of a Table

In this lesson, we focus on **Relational (SQL)** databases. Tables are linked together using special IDs called **Keys**:

- **Primary Key (PK):** The unique ID of a row. Think of it like your **Passport Number** — every person in the system has one, and no two are the same. It distinguishes "John Smith (ID: 1)" from "John Smith (ID: 2)".
- **Foreign Key (FK):** A reference to someone else's Primary Key. Think of it like your **Passport Number written on a Flight Manifest** — the manifest doesn't copy your whole passport, it just holds a reference that points back to you.

#### Normalization — The Art of Tidying Up

Normalization means organising data to avoid redundancy. Imagine a spreadsheet where you write a customer's home address on every order row. If they move house, you'd have to update hundreds of rows.

- **Un-normalized:** Storing the address 500 times across 500 order rows.
- **Normalized:** Storing the address *once* in a `Customers` table, and referring to a `customer_id` in the `Orders` table.

> **See it in action:** The [Database Normalization Interactive Visualization](https://su-ntu-ctp.github.io/6m-data-1.2-intro-database/) walks you through this step-by-step in your browser. Highly recommended.

---

### Step 3 — Tool Setup (5 min)

We will use a browser-based tool to draw database diagrams in class. Set it up now so you're not doing it during the session.

1. Go to [**dbdiagram.io**](https://dbdiagram.io/)
2. Click **"Go to App"** — the free version is all you need
3. Try typing `Table users { id int }` on the left panel and watch the diagram appear on the right. That's DBML — the language you'll use in class.

---

### Step 4 — Think About This

Before the session, consider: **Why do we need a database at all? Why not just use a giant Excel spreadsheet?**

Write down your thoughts, then check the suggested answer below.

<details>
<summary>Suggested answer</summary>

Excel works well for small, human-curated datasets — but it breaks down quickly at scale and in multi-user environments. A few specific problems:

- **Concurrency:** If two people edit the same Excel file at the same time, one person's changes get overwritten. Databases handle thousands of simultaneous writes safely.
- **Scale:** Excel starts to struggle past ~1 million rows. Databases are designed to handle billions.
- **Integrity:** Excel lets you type anything into any cell — no validation. Databases enforce rules: a `customer_id` column can only contain integers, an `email` column must be unique, etc.
- **Relationships:** In Excel, linking two sheets together is manual and fragile. Databases have Foreign Keys that enforce relationships automatically.
- **Querying:** Finding all customers who spent more than $500 last month in Excel requires complex formulas. In a database, it's one SQL line.

</details>

---

### Pre-Class Activity

*Complete this short thought experiment before the session. It's the conceptual foundation for the E-Commerce Deconstruction activity in class.*

**The Receipt Challenge**

Find a physical receipt (grocery store, café, or online order) or imagine one. Look at the data on it and decide: does each piece of data belong to the **Transaction** (happened once, specific to this purchase) or the **Master Record** (stays the same regardless of how many times someone buys)?

| Data Item | Transaction or Master Record? |
|---|---|
| Date & Time | |
| Store Address | |
| Item Name (e.g., "Milk") | |
| Item Price | *(Tricky — what happens if the price of milk changes next week?)* |

<details>
<summary>Answer Key — The Receipt Challenge</summary>

| Data Item | Category | Reasoning |
|---|---|---|
| Date & Time | **Transaction** | The date is specific to this purchase. Every order has a different date. |
| Store Address | **Master Record** | The store's address doesn't change from transaction to transaction. It belongs in a `Stores` table, referenced by the order. |
| Item Name ("Milk") | **Master Record** | "Milk" is a product that exists independently of any single purchase. It belongs in a `Products` table. |
| Item Price | **Both — depending on context** | The *current* price of milk belongs in the `Products` table. But the *price you actually paid* on this specific date must be snapshotted into the Transaction row — because if the price changes next week, your old receipt should still show what you paid, not the new price. This is exactly the "History Problem" you'll solve in the in-class assignment. |

**The key insight:** Some data lives on the receipt *because it was true at that moment*, even if the master record changes later. This is why transaction tables often store a `price_at_purchase` column alongside a `product_id`.

</details>

---

## 1.2 Lesson Plan

## Before This Lesson

Make sure you have:
- Completed **Lesson 1.1** (Introduction to Data Science)
- A free account on [dbdiagram.io](https://dbdiagram.io/d)
- A basic grasp of Python variables

### Session Overview

| | |
|---|---|
| **Duration** | 3 hours |
| **Format** | Flipped Classroom + Code-Along |
| **Tools** | [dbdiagram.io](https://dbdiagram.io/d) |

### Agenda

| Time | Part | Topic |
|------|------|-------|
| 0:00 – 0:50 | Part 1 | The Data Landscape — Relational vs. NoSQL vs. Vector |
| 0:50 – 1:00 | Break | — |
| 1:00 – 1:50 | Part 2 | Blueprinting — ERD & Keys (PK/FK) |
| 1:50 – 2:00 | Break | — |
| 2:00 – 2:50 | Part 3 | Normalization — 1NF, 2NF, 3NF |
| 2:50 – 3:00 | Wrap-Up | Q&A, Next Steps |

---

### Part 1: The Data Landscape (50 min)

#### Learning Objectives
Analyse the differences between Relational, NoSQL, and Vector databases to select the correct tool for a business problem.

#### Concept Overview

Since you know Python, you know how to store data in variables. But what happens when you turn the computer off? The data is gone.

To persist data, we need a Database. But not all data is created equal — you wouldn't use a spreadsheet to store a 4K movie, and you wouldn't use a video player to calculate your taxes.

**The Three Pillars:**

| Type | The "Vibe" | Best For... | Tech Examples |
|------|-----------|-----------|---------------|
| **Relational (SQL)** | **Structured & Rigid.** Think of it like a bank vault — highly organized, strict rules. | Financials, Inventories, User Accounts | PostgreSQL, MySQL, Snowflake |
| **NoSQL** | **Flexible & Fast.** Think of it like a messy desk — throw documents anywhere, find them fast. | Social Media feeds, Chat logs, IoT sensor data | MongoDB, Cassandra |
| **Vector** | **Semantic & AI.** Think of it like a brain association game — "King" is close to "Queen". | Image search, LLM Memory, Recommendation engines | Pinecone, Weaviate |

#### Activity 1: The Sorting Game (10 min)

"I am the CEO of a new Startup. I have 4 features I need to build. Tell me which database type I should use and WHY."

1. **User Profile Pictures:**
   <details>
   <summary>Answer</summary>
   NoSQL/Object Store for the image binary, or SQL for the file path.
   </details>

2. **Payment Processing:**
   <details>
   <summary>Answer</summary>
   SQL. We need ACID (Atomicity, Consistency, Isolation, and Durability) compliance/Transactions.
   </details>

3. **"Find me songs that sound like Jazz":**
   <details>
   <summary>Answer</summary>
   Vector Database
   </details>

4. **A live chat for a video game:**
   <details>
   <summary>Answer</summary>
   NoSQL. High volume, simple structure.
   </details>

---

### Part 2: Building the Blueprint — ERD (50 min)

#### Learning Objectives
Apply the concepts of Primary Keys and Foreign Keys to create a logical Entity-Relationship Diagram (ERD) using DBML.

#### Concept Overview

Before we write SQL queries, we need a map. An Architect draws a blueprint before the construction crew lays bricks. An **ERD (Entity Relationship Diagram)** is our blueprint.

**The Keys:**

1. **Primary Key (PK):** The unique NRIC number of a row.
   - *Rule:* It creates identity. If two rows have the same PK, the database throws an error.

2. **Foreign Key (FK):** The reference pointing to someone else's PK.
   - *Rule:* It creates relationships — "I belong to that person over there."

> **SQL Data Types Reference** — used when declaring columns in DBML:
>
> | Data Type | Description |
> |-----------|-------------|
> | `INT` | Whole number (e.g., age, quantity) |
> | `VARCHAR` | Short text with variable length (e.g., name, email) |
> | `TEXT` | Long text (e.g., description, notes) |
> | `DATE` | Calendar date (e.g., 2026-01-01) |
> | `DATETIME` | Date + time (e.g., 2026-01-01 09:30:00) |
> | `BOOLEAN` | True or false |

#### Activity 2.1: Code-Along — Car Insurance Schema (15 min)

Open [dbdiagram.io](https://dbdiagram.io/d) and paste the following code:

```dbml
// --- 1. Define the Customer ---
Table customers {
  id int [pk, increment] // PRIMARY KEY: The unique ID for every customer
  name varchar
  address varchar
  phone varchar
  email varchar
}

// --- 2. Define the Car ---
Table cars {
  id int [pk, increment]
  make varchar
  model varchar
  year int
  car_plate varchar
  customer_id int
}

// --- 3. Define the Link (Relationship) ---
// The '>' symbol translates to "One-to-Many".
// Read as: "One Customer can have Many Cars"
Ref: cars.customer_id > customers.id


// --- CHALLENGE ---
// Task: Add an 'accidents' table below.
// Requirements:
// 1. Accidents have a date, location, and description.
// 2. An accident happens to a specific CAR.
// 3. Link the accident to the car.
```

<details>
<summary>Solution</summary>

```dbml
Table accidents {
  id int [pk, increment]
  date datetime
  location varchar
  description text

  car_id int // FK pointing to the car
}
Ref: accidents.car_id > cars.id
```

</details>

#### Activity 2.2: School System Workshop (15 min)

Construct an ERD for a school system whose classes have students and teachers. Each student belongs to a single class. Each teacher may teach more than one class, and each class may have more than one teacher.

Attributes:
> - Student: id, name, address, phone, email, class_id
> - Teacher: id, name, address, phone, email
> - Class: id, name, teacher_id

Write the DBML to create the ERD. Submit in the Discord Peer-Review Channel.

<details>
<summary>Sample Solution</summary>

```dbml
Table students {
  id int [pk, increment]
  name varchar
  address varchar
  phone varchar
  email varchar
  class_id int  // FK → classes
}

Table teachers {
  id int [pk, increment]
  name varchar
  address varchar
  phone varchar
  email varchar
}

Table classes {
  id int [pk, increment]
  name varchar
}

// Junction table: a class can have many teachers, a teacher can teach many classes
Table class_teachers {
  class_id int    // FK → classes
  teacher_id int  // FK → teachers
}

Ref: students.class_id > classes.id
Ref: class_teachers.class_id > classes.id
Ref: class_teachers.teacher_id > teachers.id
```

**Key design decisions:**
- `students.class_id` is a FK to `classes` because each student belongs to exactly one class (one-to-many).
- The `class_teachers` junction table resolves the many-to-many relationship between classes and teachers.

</details>

---

### Part 3: Organizing Your Data — Normalization (50 min)

#### Learning Objectives
Evaluate a raw, un-normalized dataset and decompose it into a 3rd Normal Form (3NF) schema to reduce data redundancy.

#### Concept Overview

> **Start Here: Interactive Visualization**
> Open the [Normalization Interactive Visualization](https://su-ntu-ctp.github.io/6m-data-1.2-intro-database/) in your browser before reading the explanations below. It's an 8-step guided tour that animates exactly what happens when you normalize a table.

**"Every fact should be about the key, the whole key, and nothing but the key."**

---

#### Rule 1 (1NF): One Item Per Space — "No Grocery Bags in Cells"

**Before 1NF:**

| Person | Favorite Fruits |
|--------|-----------------|
| Sarah | Apple, Banana, Orange |
| Mike | Grape, Mango |

**After 1NF:**

| Person | Favorite Fruit |
|--------|----------------|
| Sarah | Apple |
| Sarah | Banana |
| Sarah | Orange |
| Mike | Grape |
| Mike | Mango |

---

#### Rule 2 (2NF): Everything Relates to the Complete ID — "The Address Book Rule"

**Before 2NF:**

| BorrowID | StudentID | StudentName | BookID | BookTitle | BorrowDate |
|----------|-----------|-------------|--------|-----------|------------|
| 1 | S01 | Alice | B10 | Dune | 2026-01-05 |
| 2 | S01 | Alice | B20 | 1984 | 2026-01-12 |
| 3 | S02 | Bob | B10 | Dune | 2026-01-08 |

**After 2NF — split into three tables:**

| StudentID | StudentName |
|-----------|-------------|
| S01 | Alice |
| S02 | Bob |

| BookID | BookTitle |
|--------|-----------|
| B10 | Dune |
| B20 | 1984 |

| BorrowID | StudentID | BookID | BorrowDate |
|----------|-----------|--------|------------|
| 1 | S01 | B10 | 2026-01-05 |
| 2 | S01 | B20 | 2026-01-12 |
| 3 | S02 | B10 | 2026-01-08 |

---

#### Rule 3 (3NF): No Chain Dependencies — "The Phone Directory Principle"

**The Problem:**

| Employee ID | Employee Name | Department Code | Department Name | Department Manager |
|-----------|-------------|-----------------|-----------------|-------------------|
| E001 | Alice | D10 | Sales | John Smith |
| E002 | Bob | D10 | Sales | John Smith |
| E003 | Carol | D20 | Marketing | Jane Doe |

There is a transitive dependency:
```
Employee ID → Department Code → Department Name
Employee ID → Department Code → Department Manager
```

**The Solution:** Split into Employees and Departments tables. When the Sales manager changes, you update ONE cell.

---

#### Activity 3: The E-Commerce Deconstruction (Group Breakout — 20 min)

**Starting Point — The Messy Spreadsheet:**

| OrderID | ItemID | ItemName | ItemPrice | CustomerID | CustomerName | OrderDate |
|---------|--------|----------|-----------|-----------|-------------|-----------|
| 100 | 10 | iPhone | 1000 | 1 | John | 2021-01-01 |
| 100 | 20 | iPad | 500 | 1 | John | 2021-01-01 |
| 200 | 30 | Macbook | 2000 | 1 | John | 2021-01-02 |
| 300 | 10 | iPhone | 1000 | 2 | Mary | 2021-01-03 |
| 300 | 30 | Macbook | 2000 | 2 | Mary | 2021-01-03 |

**Step 1 — Apply 1NF:** Add a LineNumber to create a unique two-part identifier (OrderID + LineNumber) for each row.

**Step 2 — Apply 2NF:** Customer info (CustomerID, CustomerName, OrderDate) depends only on OrderID. Split into an **Orders Table** and an **Order Line Items Table**.

**Step 3 — Apply 3NF:** ItemName and ItemPrice depend on ItemID, not on the specific order. Create a separate **Products Table**.

**Final Result — 4 clean tables:** Customers, Products, Orders, Order Line Items.

<details>
<summary>Final DBML for all 4 tables</summary>

```dbml
Table customers {
  id int [pk, increment]
  name varchar
}

Table products {
  id int [pk, increment]
  name varchar
  price decimal
}

Table orders {
  id int [pk, increment]
  customer_id int          // FK → customers
  order_date date
}

Table order_line_items {
  order_id int             // FK → orders
  line_number int
  product_id int           // FK → products
}

Ref: orders.customer_id > customers.id
Ref: order_line_items.order_id > orders.id
Ref: order_line_items.product_id > products.id
```

</details>

#### Activity 3.2: Your Turn to Practice (15 min)

**Scenario:** You run a Movie Rental Service.

**Current Messy Data:**

| RentalID | CustomerName | CustomerPhone | MovieTitle | MovieGenre | RentalDate | ReturnDate |
|----------|-------------|-------------|-----------|-----------|-----------|-----------|
| R1 | Alice | 555-1234 | Inception | Sci-Fi | 2026-01-01 | 2026-01-03 |
| R1 | Alice | 555-1234 | Interstellar | Sci-Fi | 2026-01-01 | 2026-01-03 |
| R2 | Bob | 555-5678 | Inception | Sci-Fi | 2026-01-02 | 2026-01-04 |

**Task:** Normalize this to 3NF. Create the necessary tables and identify PKs and FKs. Write in DBML and share on Discord.

<details>
<summary>Sample Solution</summary>

```dbml
Table customers {
  id int [pk, increment]
  name varchar
  phone varchar
}

Table movies {
  id int [pk, increment]
  title varchar
  genre varchar
}

Table rentals {
  id int [pk, increment]
  customer_id int          // FK → customers
  rental_date date
  return_date date
}

Table rental_line_items {
  rental_id int    // FK → rentals
  line_number int
  movie_id int     // FK → movies
}

Ref: rentals.customer_id > customers.id
Ref: rental_line_items.rental_id > rentals.id
Ref: rental_line_items.movie_id > movies.id
```

**Result:** 4 tables — Customers, Movies, Rentals, Rental Line Items. Every fact lives exactly once.

</details>

#### Reflection

- When might a team *intentionally* denormalize (break normalization rules) for performance reasons? What are the trade-offs?

<details>
<summary>Suggested answer</summary>

Denormalization is common in read-heavy systems like analytics dashboards or data warehouses. Joining 10 tables to answer every query is slow, so teams sometimes store pre-joined or duplicated data to speed things up. The trade-off is that **writes become risky** — you can update a price in one place and forget another, leading to inconsistencies.

</details>

- How does normalization protect against "Update Anomalies"?

<details>
<summary>Suggested answer</summary>

An **Update Anomaly** happens when you change one fact and have to hunt down multiple rows to update it everywhere it appears. Normalization prevents this by ensuring each fact lives in exactly one place.

</details>

---

### Wrap-Up

**Key Takeaways:**
1. Choose your database type (SQL, NoSQL, Vector) based on the nature of your data and your query patterns.
2. ERDs are blueprints — design the structure before writing SQL.
3. Normalization ensures each fact lives in exactly one place, preventing duplicates and update errors.

**Next Steps:**
- Complete the Assignment.
- Next lesson: Lesson 1.3 introduces SQL DDL — how to physically build the tables you designed today.

---

## 1.2 Assignment

# Advanced Challenge: Architecting "FoodFast"

**Topic:** Complex Relationships & Data Integrity
**Estimated Time:** 45–60 Minutes

### What You'll Practice

- Designing a multi-table schema from plain-English requirements
- Resolving a many-to-many relationship using a junction table
- Handling historical data integrity (a real-world engineering problem)
- Reading auto-generated SQL and asking informed questions about it

### The Scenario

You have been hired as the Lead Backend Engineer for "FoodFast," a new competitor to UberEats/DoorDash.

**The Requirements:**

1. **Users:** Customers with a Name, Email, and *multiple* saved delivery addresses (Home, Work, etc.).
2. **Restaurants:** Establishments with a Name, Cuisine Type, and Rating.
3. **The Menu:** Each restaurant has many Menu Items (e.g., "Burger", "Fries"). Items have a Name and a Price.
4. **Couriers:** Drivers with a Name and Vehicle Type (Bike, Car).
5. **Orders:**
   - An order belongs to **one** Customer.
   - An order is picked up by **one** Courier.
   - An order comes from **one** Restaurant.
   - **CRITICAL:** An order can contain **many** Menu Items.

### Challenge 1: The "Many-to-Many" Problem

You cannot simply put `item_id` in the Orders table (because you might buy 5 items). You cannot put `order_id` in the Items table (because the item is sold to thousands of people).

**Solution Required:** Create a Junction Table (often called `order_items` or `order_details`) to sit between Orders and Menu Items.

### Challenge 2: The "History" Problem (Normalization Trap)

1. On Monday, John buys a "Big Mac" for **$5.00**.
2. On Tuesday, the Restaurant raises the price to **$6.00**.
3. On Wednesday, John looks at his receipt from Monday.

**The Question:** If your schema just links to `menu_items` for the price, John's receipt will now show $6.00 on Monday. This is illegal (fraud).

**Task:** Modify your schema to ensure that even if the Restaurant updates the Menu Item price, the historic Order Record remains accurate.

<details>
<summary>Hint</summary>

When John places an order, his `order_items` row is created at that exact moment. What if you added an extra column to `order_items` that captured the price *right then*, independent of the `menu_items` table?

</details>

### Challenge 3: Looking Ahead to SQL (DDL)

1. Build your diagram in dbdiagram.io.
2. Use the **"Export"** function to export to PostgreSQL or MySQL.
3. Paste the generated code for your Users table. Read it, then answer:
   - What does `NOT NULL` mean?
   - What does `DEFAULT` mean?
   - Note down 2 questions about anything else in the SQL syntax that puzzles you — you'll get answers in Lesson 1.3.

<details>
<summary>Solution Key (Don't peek until you try!)</summary>

```dbml
Table users {
  id int [pk, increment]
  name varchar
  email varchar
}

Table addresses {
  id int [pk]
  user_id int
  street varchar
  city varchar
  type varchar // 'Home', 'Work'
}

Table restaurants {
  id int [pk]
  name varchar
  cuisine varchar
  rating decimal
}

Table menu_items {
  id int [pk]
  restaurant_id int
  name varchar
  current_price decimal // This is the price TODAY
}

Table couriers {
  id int [pk]
  name varchar
  vehicle varchar
}

Table orders {
  id int [pk]
  user_id int
  courier_id int
  restaurant_id int
  order_time datetime
  total_price decimal
}

// THE JUNCTION TABLE (Many-to-Many Resolver)
Table order_items {
  id int [pk]
  order_id int
  menu_item_id int
  quantity int
  price_at_purchase decimal  // THE FIX FOR CHALLENGE 2
}

Ref: addresses.user_id > users.id
Ref: menu_items.restaurant_id > restaurants.id
Ref: orders.user_id > users.id
Ref: orders.courier_id > couriers.id
Ref: orders.restaurant_id > restaurants.id
Ref: order_items.order_id > orders.id
Ref: order_items.menu_item_id > menu_items.id
```

</details>

---

### Post-Class Reading: Normalisation Trade-offs

**Scenario 1 – Historical Accuracy:** Imagine the iPhone's price increases to $1,200 next year. If your `order_line_items` table only stores a FK to `menu_items` (not the actual price paid), what happens when you try to calculate last year's revenue?

**Scenario 2 – Query Complexity:** Assuming you *did* store historical prices in `order_line_items`, how many table joins would you need to answer "Total revenue by product last year"? What might that mean for a database with millions of rows?

<details>
<summary>Scenario 1 answer</summary>

Your query joins `orders → order_line_items → menu_items` to get the price. But `menu_items.current_price` is now $1,200. The join returns $1,200 for every iPhone sold last year — even though customers actually paid $1,000. **Your revenue report is now wrong, and historic receipts are inaccurate.** This is why we added `price_at_purchase` to `order_items` in Challenge 2.

</details>

<details>
<summary>Scenario 2 answer</summary>

To answer "total revenue by product last year" you'd need: `orders → order_line_items → menu_items` — that's 3 tables joined. As your database grows to millions of rows, every join multiplies the work the database has to do. This is why analytics systems like data warehouses often **deliberately denormalise** — they store `product_name` and `price_at_purchase` directly in the transaction row, sacrificing some storage efficiency to make reporting queries fast and simple.

</details>

<details>
<summary>The underlying principle</summary>

Fully normalised tables guarantee **structural correctness**: no duplicate customers, consistent foreign key references, each fact in one place. But real systems often accept controlled denormalisation for two reasons:

- **Historical accuracy:** Storing `sold_price` directly in the transaction row preserves what actually happened, regardless of future price changes.
- **Query efficiency:** Fewer joins means faster analytics, especially at scale.

</details>

**Key Takeaways:**
1. Normalisation ensures structural correctness.
2. Controlled denormalisation preserves history and improves performance.
3. Good data design balances integrity with practical business needs.

---

## 1.2 Reference

### Foundation

- [Tech Terms and Definitions](https://hackr.io/blog/programming-terms-definitions-for-beginners)

### Relational Database Management Systems

- [Codecademy — What is RDBMS](https://www.codecademy.com/article/what-is-rdbms-sql)
- [W3School — RDBMS](https://www.w3schools.com/mysql/mysql_rdbms.asp)
- SQL Data Types: https://www.w3schools.com/sql/sql_datatypes.asp | https://www.digitalocean.com/community/tutorials/sql-data-types
- DBML Reference: https://dbml.dbdiagram.io/docs/
- [Codd's 12 rules](https://en.wikipedia.org/wiki/Codd%27s_12_rules)
- [Normalization](https://en.wikipedia.org/wiki/Database_normalization)

### Other Resources

- [Video] "Database Design Course — Learn how to design and plan a database" (FreeCodeCamp on YouTube): https://www.youtube.com/watch?v=ztHopE5Wnpc
- [Read] "What is a Relational Database?" (AWS): https://aws.amazon.com/rds/what-is-a-relational-database/

---

---

# Lesson 1.3 — SQL Basic: DDL

**Theme:** Building the Structure — creating and managing database objects with SQL

---

## 1.3 Overview

| Section | Duration | Topic / Activity |
|---------|----------|-----------------|
| **Part 1: The Foundation** | 55 min | Database hierarchy; CREATE TABLE; Data types; INSERT & ALTER |
| **Part 2: The Blueprint** | 55 min | Constraints (PK, FK, NOT NULL, CHECK); Referential integrity |
| **Part 3: The Pipeline** | 55 min | COPY for bulk import; Indexes; Views; Export to CSV/JSON |

### Learning Outcomes

By the end of this lesson, you will be able to:

1. **Identify** the database hierarchy (Database → Schema → Table → Column → Row) and explain its purpose.
2. **Apply** `CREATE TABLE` statements with appropriate data types and constraints to enforce data integrity.
3. **Execute** `COPY` commands to import CSV data into structured tables in bulk.
4. **Create** Views and Indexes to simplify analyst workflows and improve query performance.

### Course Materials

| Material | Description | Est. Time |
|----------|-------------|-----------|
| Pre-Class | DDL concepts, DuckDB intro, DbGate setup | 30–45 min |
| Lesson Plan | Instructor guide for the 3-hour hands-on session | 3 hours |
| Assignment | The Tiny Library & The Marketing Dump — schema design challenges | 45–60 min |
| Reference | SQL DDL cheat sheet, DuckDB data types reference | As needed |

### Tools & Setup

- **[DuckDB](https://duckdb.org):** Lightweight, in-process analytical database (no server needed).
- **[DbGate](https://dbgate.org):** Free, cross-platform database manager — download before class.
- **Database file:** `db/unit-1-3.db`

---

## 1.3 Pre-Class Reading

**Estimated Time:** 30–40 minutes
**Prerequisites:** Lesson 1.2 — Data Modeling & Schema Design

> In Lesson 1.2 you designed database schemas using DBML and dbdiagram.io. This lesson is where you *build* those schemas for real — writing the actual SQL commands that create tables, define columns, and enforce constraints in a live database.

---

### Step 1 — Watch the Video (10 min)

🎬 [SQL DDL — The Blueprint for Data](https://youtu.be/adACCuMFjac)

---

### Step 2 — Read the Core Concepts (15 min)

#### What is a Database — and How is it Structured?

Think of a database as a highly organised digital filing cabinet:

- **Database** — the cabinet itself (e.g., `School_System`)
- **Schema** — a drawer inside the cabinet, used to group related tables (e.g., `Enrollment_Data`)
- **Table** — a specific spreadsheet inside the drawer (e.g., `Students`)
- **Columns (Fields)** — the categories of data (e.g., Name, Age, Email)
- **Rows (Records)** — individual entries (e.g., "John Doe, 25, john@example.com")

#### What is DDL?

**Data Definition Language (DDL)** is the subset of SQL used to **build and modify the structure** of a database — not the data itself. Think of it as the architect's work: you design and build the rooms before moving furniture in.

| DDL Command | What it does |
|---|---|
| `CREATE SCHEMA` | Creates a new folder/namespace in the database |
| `CREATE TABLE` | Defines a new table and its columns |
| `ALTER TABLE` | Adds or changes columns in an existing table |
| `DROP TABLE` | Deletes a table entirely ⚠️ **cannot be undone** |

**Data Types:**

| Type | Use for |
|---|---|
| `INTEGER` | Whole numbers (e.g., age, quantity) |
| `VARCHAR(n)` | Short text up to n characters (e.g., name, email) |
| `TEXT` | Long free-form text |
| `DATE` | Calendar date (e.g., 2026-01-01) |
| `BOOLEAN` | True or false |

---

### Step 3 — Tool Setup (10 min)

#### DuckDB
[DuckDB](https://duckdb.org/) is the database engine — it runs entirely on your laptop with no server required.

<details>
<summary>Why DuckDB?</summary>

Most databases need a separate server running in the background. DuckDB is **in-process** — it runs inside your Python script or DbGate session directly. This means:
- No installation of a server, no configuration
- The entire database lives in a single `.db` file you can copy or share
- Optimised for the kind of analytical queries (aggregations, joins across millions of rows) that data scientists run most often

</details>

#### DbGate — Community Edition (free)
[Download DbGate](https://www.dbgate.io/download-community/) — a visual database manager.

**Setup steps:**
1. Download and install DbGate (Community edition, free)
2. Download the `unit-1-3.db` file from the [course repository](https://github.com/su-ntu-ctp/6m-data-1.3-sql-basic-ddl/blob/main/db/)
3. Open DbGate → New Connection → DuckDB → point to your `.db` file

---

### Step 4 — Check Your Understanding

Try to answer these before class. Write your answers down, then check below.

1. If I want to add a "Phone Number" column to an existing table, which DDL command do I use?
2. What is the difference between a Schema and a Table?
3. Why might a Data Scientist prefer DuckDB over a traditional database server like PostgreSQL?

<details>
<summary>Suggested answers</summary>

**Q1:** `ALTER TABLE` — it modifies the structure of an existing table without destroying it or its data.

**Q2:** A Schema is a namespace or folder that groups related tables together. A Table is the actual data structure within that schema — rows and columns. One Schema can contain many Tables.

**Q3:** DuckDB requires no server setup or administration — it runs as a single file on your laptop. For a data scientist doing local analysis, this means less overhead, easier reproducibility (just share the `.db` file), and better performance on the analytical queries common in data science work.

</details>

---

## 1.3 Lesson Plan

**In data science, data is the new oil. DDL is how we build the refinery.**

### Session Overview

| | |
|---|---|
| **Duration** | 3 hours |
| **Format** | Flipped Classroom + Code-Along ("I do, We do, You do") |
| **Tools** | [DbGate](https://www.dbgate.io/download-community/), [DuckDB](https://duckdb.org/) |
| **Database file** | `db/unit-1-3.db` |

### Agenda

| Time | Part | Topic |
|------|------|-------|
| 0:00 – 0:55 | Part 1 | The Foundation — CREATE TABLE, data types, INSERT, ALTER |
| 0:55 – 1:05 | Break | — |
| 1:05 – 2:00 | Part 2 | The Blueprint — Constraints (PK, FK, NOT NULL, CHECK) |
| 2:00 – 2:10 | Break | — |
| 2:10 – 3:00 | Part 3 | The Pipeline — COPY, Indexes, Views, Export |

---

### Part 1: The Foundation (55 min)

#### Concept Overview

**In Python, you create variables like `my_data = []`. But when you turn off the computer, that data vanishes. To make data specific and permanent, we need a Database.**

Think of it like a physical File Cabinet:
- **The Database:** The Cabinet itself.
- **The Schema:** A specific drawer (labeled 'HR' or 'Sales').
- **The Table:** A folder inside that drawer.
- **The Column:** The specific form fields in that folder (Name, Date, ID).

**Types Matter:**
- **INTEGER:** Math-able numbers (e.g., Age, Count).
- **VARCHAR:** Text (e.g., Name, Email).
- **DATE:** Chronological points. *(Don't store dates as text!)*

#### Activity 1: The "Profile" Table (Code-Along — 20 min)

**1. Connecting to the Database:**

Open **DbGate** and create a new connection to the DuckDB file: `db/unit-1-3.db`

**2. Creating a Schema:**

```sql
CREATE SCHEMA IF NOT EXISTS lesson;
```

**3. Creating your first Table:**

```sql
CREATE TABLE lesson.users (
  id INTEGER,
  name VARCHAR,
  email VARCHAR
);
```

**4. Basic Data Entry:**

```sql
INSERT INTO lesson.users (id, name, email)
VALUES (1, 'John Doe', 'john.doe@gmail.com');
```

Insert multiple rows at once:

```sql
INSERT INTO lesson.users (id, name, email)
VALUES (2, 'Jane Doe', 'jane.doe@gmail.com'),
       (3, 'John Smith', 'john.smith@gmail.com');
```

**5. Alter Tables:**

Add a column:

```sql
ALTER TABLE lesson.users ADD COLUMN start_date DATE;
```

Rename a column:

```sql
ALTER TABLE lesson.users RENAME id TO uid;
```

Drop a column:

```sql
ALTER TABLE lesson.users DROP COLUMN email;
```

**6. TRUNCATE vs. DROP:**

```sql
TRUNCATE TABLE lesson.users;  -- removes all rows, keeps table structure
```

```sql
DROP TABLE lesson.users;      -- removes the table entirely
```

> **Tip:** "Always run a SELECT before a DROP. Double-check your table name. It's better to be slow and correct than fast and sorry."

#### Reflection

- Why is organizing data into schemas important in a production environment?
- What happens if you try to insert a second row with the same `id`?

---

### Part 2: The Blueprint — Constraints (55 min)

#### Concept Overview

"In Excel, you can type 'Banana' into a column meant for Prices. Excel doesn't care. Databases *do* care. **Constraints** are the 'Bouncers' at the door."

**The Keys:**
- **Primary Key (PK):** The Fingerprint. Unique and Not Null.
- **Foreign Key (FK):** The Link. It points to a PK in another table.

<details>
<summary>Constraints Reference — PK, FK, NOT NULL, CHECK, DEFAULT</summary>

- `primary key` or `unique` define a column, or set of columns, that are a unique identifier for a row.
- `primary key` constraints also enforce that keys cannot be NULL.
- `foreign key` defines a column that refers to a primary key in another table — enforcing that the referenced record exists.
- `not null` specifies that the column cannot contain any NULL values.
- `default` specifies a default value for the column when no value is specified.
- `check` allows you to specify an arbitrary boolean expression that all rows must satisfy.

</details>

#### Activity 2: The "Missing Link" Challenge (25 min)

**Part A: Code-Along — Creating Tables with Constraints:**

```sql
CREATE TABLE lesson.teachers (
  id INTEGER PRIMARY KEY,
  name VARCHAR NOT NULL,
  age INTEGER CHECK(age > 18 AND age < 70),
  address VARCHAR,
  phone VARCHAR,
  email VARCHAR CHECK(CONTAINS(email, '@'))
);

CREATE TABLE lesson.classes (
  id INTEGER PRIMARY KEY,
  name VARCHAR NOT NULL,
  teacher_id INTEGER REFERENCES lesson.teachers(id)  -- foreign key
);
```

**Part B: Your Challenge**

Complete the `CREATE TABLE` statement for the `students` table:

```dbml
Table students {
  id int [pk]
  name varchar
  address varchar
  phone varchar
  email varchar
  class_id int
}
```

<details>
<summary>Solution</summary>

```sql
CREATE TABLE lesson.students (
    id INTEGER PRIMARY KEY,
    name VARCHAR,
    email VARCHAR,
    class_id INTEGER REFERENCES lesson.classes(id)
);
```

</details>

#### Reflection

- What happens if you try to `INSERT` a student with a `class_id` that doesn't exist?
- How do constraints prevent "bad data" from entering your analysis pipeline?

---

### Part 3: The Pipeline (50 min)

#### Concept Overview

"We have empty tables. Typing `INSERT INTO...` one row at a time is fine for 10 rows. It is impossible for 1 million rows. The **COPY** command is the industrial vacuum cleaner of SQL — it inhales an entire CSV file in seconds."

<details>
<summary>What are Indexes?</summary>

Indexes are used to improve the performance of queries. Think of a book's index — instead of reading every page (full table scan), the database jumps directly to the relevant rows. Users cannot see the indexes; they are just used to speed up searches/queries.

</details>

<details>
<summary>Tables vs. Views</summary>

A **table** is a physical copy of the data (materialized), while a **view** is a virtual copy — a query that is run on the fly when you access the view. Views are perfect for giving analysts a simplified, pre-filtered view of complex tables without storing duplicate data.

</details>

#### Activity 3: The CSV Dump (Code-Along)

**1. Importing Data:**

```sql
COPY lesson.teachers FROM '<full directory path>' (AUTO_DETECT TRUE);
```

> **Note:** Use the full directory path to the CSV files, e.g. `/Users/yourname/Dev/6m-data-1.3-sql-basic-ddl/data/teachers.csv`

**2. Exercise:** Import data for the `classes` and `students` tables.

**3. Updating Data:**

```sql
UPDATE lesson.students
SET email = 'linda.g@example.com'
WHERE id = 4;
```

**4. Exporting Data:**

Export with a `|` delimiter:

```sql
COPY (SELECT * FROM lesson.students) TO '<full directory path>' WITH (HEADER 1, DELIMITER '|');
```

Export as JSON:

```sql
COPY (SELECT * FROM lesson.students) TO '<full directory path>';
```

**5. Challenge:** Repeat the export steps for the `teachers` and `classes` tables.

#### Activity 4: Index, Table & View (Code-Along)

**Creating Indexes:**

```sql
-- Create a unique index on the name column of teachers
CREATE UNIQUE INDEX teachers_name_idx ON lesson.teachers(name);

-- Create a non-unique index on the name column of students
CREATE INDEX students_name_idx ON lesson.students(name);

-- View indexes for a specific table
SELECT index_name, sql
FROM duckdb_indexes
WHERE table_name = 'students';
```

**Creating a View:**

```sql
CREATE VIEW lesson.students_view AS
SELECT id, name, email
FROM lesson.students;
```

**Challenge:** Create a `teachers_view` with the same columns but for the `teachers` table.

#### Reflection

- When should you *not* use an index?
- How does using a View simplify the work for a Data Analyst who only needs specific columns?

---

### Wrap-Up

**Key Takeaways:**
1. DDL (`CREATE`, `ALTER`, `DROP`) defines the skeleton of your database — the structure that everything else depends on.
2. Constraints prevent bad data from entering — always cheaper to reject invalid data at entry than to clean it up later.
3. `COPY`, Indexes, and Views are production tools — bulk loading, performance, and access control separate a prototype from a real database.

**Next Steps:**
- Complete the Assignment.
- Next lesson: Lesson 1.4 builds on today's structure by teaching you to *query* data with DML — SELECT, WHERE, GROUP BY, and more.

---

## 1.3 Assignment

**Estimated Time:** 45-60 Minutes
**Submission:** Post in **#peer-reviews** on Discord. Questions → **#questions**.

### Case Study 1: The "Tiny Library" (Schema Design)

**Scenario:** A local community library needs a database to track Books, Members, and Loans.

**Requirements:**

1. **Books Table:** Needs a title, author, and a unique ISBN (13 characters).
2. **Members Table:** Needs a name, email, and join date. Email must be unique.
3. **Loans Table:** Tracks which member borrowed which book and when.
   - Constraint: You cannot loan a book that doesn't exist.
   - Constraint: You cannot loan to a member who doesn't exist.
   - Constraint: The `return_date` can be null (meaning they haven't returned it yet), but the `loan_date` is required.

**Task:** Write the SQL DDL statements to create these three tables in a new schema called `library`.

### Case Study 2: The "Marketing Dump" (Data Ingestion)

The marketing team has sent you a raw CSV file named `leads_raw.csv` containing potential customer data.

**Data Preview (`leads_raw.csv`):**

```
id,full_name,contact_info,signup_date
101,"Alice Smith","alice@gmail.com",2023-01-01
102,"Bob Jones","555-0199",2023-01-02
103,"Charlie Brown","charlie@yahoo.com",2023-01-03
```

**Task:**

1. **Create a Staging Table:** Create a table called `marketing_leads` in the `public` schema. Use `VARCHAR` for almost everything to prevent import errors.
2. **Import Data:** Write the COPY command to load the CSV data into your table.
3. **Create a View:** Create a view called `valid_leads` that filters out rows where the `contact_info` does NOT contain an `@` symbol.

---

### Advanced Parts for learners with Python knowledge (Optional)

**Local Environment Setup:**

1. Create a new conda environment from `environment.yml`:
   ```
   conda env create -f environment.yml
   ```
2. Activate the conda environment:
   ```
   conda activate ddb
   ```
3. Run `create_duckdb.py` to create the database file:
   ```
   python db/create_duckdb.py
   ```

---

### Solutions

<details>
<summary>Solution 1: The Tiny Library</summary>

```sql
CREATE SCHEMA IF NOT EXISTS library;

-- 1. Books (The Inventory)
CREATE TABLE library.books (
    isbn VARCHAR(13) PRIMARY KEY,
    title VARCHAR NOT NULL,
    author VARCHAR NOT NULL,
    published_year INTEGER
);

-- 2. Members (The Users)
CREATE TABLE library.members (
    member_id INTEGER PRIMARY KEY,
    full_name VARCHAR NOT NULL,
    email VARCHAR UNIQUE,
    join_date DATE
);

-- 3. Loans (The Transaction/Link Table)
CREATE TABLE library.loans (
    loan_id INTEGER PRIMARY KEY,
    loan_date DATE NOT NULL,
    return_date DATE,  -- Can be NULL (currently borrowed)
    book_isbn VARCHAR(13) REFERENCES library.books(isbn),
    member_id INTEGER REFERENCES library.members(member_id)
);
```

</details>

<details>
<summary>Solution 2: The Marketing Dump</summary>

**Step 1 & 2: Create Table & Import**

```sql
-- Create a "loose" table to accept messy input
CREATE TABLE marketing_leads (
    id INTEGER,
    full_name VARCHAR,
    contact_info VARCHAR,
    signup_date DATE
);

-- Import the data
COPY marketing_leads 
FROM 'leads_raw.csv' 
(AUTO_DETECT TRUE);
```

**Step 3: The Cleaning View**

```sql
CREATE VIEW valid_leads AS
SELECT
    id,
    full_name,
    contact_info AS email,
    signup_date
FROM marketing_leads
WHERE contains(contact_info, '@');
-- OR for standard SQL: WHERE contact_info LIKE '%@%';
```

</details>

---

## 1.3 Reference

- SQL Introduction: https://duckdb.org/docs/sql/introduction
- SQL Cheatsheet: https://www.sqltutorial.org/sql-cheat-sheet/
- Popular RDBMS: https://www.codecademy.com/article/what-is-rdbms-sql | https://db-engines.com/en/ranking
- Why DuckDB?: https://hightouch.com/blog/duckdb | https://duckdb.org/why_duckdb

---

## 1.3 Data Files

### `data/teachers.csv`

```
id,name,age,address,phone,email
1,John Doe,30,123 Main St,555-1234,john.doe@example.com
2,Jane Smith,25,456 Oak Ave,555-5678,jane.smith@example.com
```

### `data/classes.csv`

```
id,name,teacher_id
101,Science01,1
102,Science02,1
103,Maths01,2
```

### `data/students.csv`

```
id,name,address,phone,email,class_id
1,Michael Brown,654 Birch Blvd,555-8765,michael.brown@example.com,102
2,Susan Lee,987 Maple Dr,555-2468,susan.lee@example.com,101
3,David Wang,753 Cedar Ave,555-1357,david.wang@example.com,103
4,Linda Garcia,159 Cherry Ln,555-5793,linda.garcia@example.com,102
```

### `data/leads_raw.csv`

```
id,full_name,contact_info,signup_date
101,"Alice Smith","alice@gmail.com",2023-01-01
102,"Bob Jones","555-0199",2023-01-02
103,"Charlie Brown","charlie@yahoo.com",2023-01-03
104,"David TextOnly","just-visited-website",2023-01-04
```

---

## 1.3 Scripts

### `data/import.sql`

```sql
COPY lesson.teachers FROM '/Users/zanelim/SkillsUnion/5m-data-1.3-sql-basic-ddl/data/teachers.csv' (HEADER TRUE);
COPY lesson.classes FROM '/Users/zanelim/SkillsUnion/5m-data-1.3-sql-basic-ddl/data/classes.csv' (HEADER TRUE);
COPY lesson.students FROM '/Users/zanelim/SkillsUnion/5m-data-1.3-sql-basic-ddl/data/students.csv' (HEADER TRUE);
```

### `db/create_duckdb.py`

```python
import duckdb

con = duckdb.connect("db/unit-1-3.db")
```

---

---

# Lesson 1.4 — SQL Basic: DML

**Theme:** Having a Conversation with Data — query, filter, aggregate, and transform

---

## 1.4 Overview

| Section | Duration | Topic / Activity |
|---------|----------|-----------------|
| **Part 1: Selection, Filtering & Sorting** | 55 min | SELECT, WHERE, ORDER BY; mathematical operators; narrowing results |
| **Part 2: Aggregates & Grouping** | 55 min | COUNT, SUM, AVG, MIN, MAX; GROUP BY; WHERE vs. HAVING |
| **Part 3: Advanced Logic & Data Cleaning** | 55 min | CASE statements; CAST for type conversion; date extraction |

### Learning Outcomes

By the end of this lesson, you will be able to:

1. **Retrieve** specific columns and rows from a database using `SELECT`, `WHERE`, and `ORDER BY`.
2. **Summarise** datasets using aggregate functions (`COUNT`, `SUM`, `AVG`, `MIN`, `MAX`) with `GROUP BY`.
3. **Filter** grouped results using `HAVING` and explain when to use `WHERE` vs. `HAVING`.
4. **Transform** data using `CASE` statements for categorisation and `CAST` for type conversion.

### Course Materials

| Material | Description | Est. Time |
|----------|-------------|-----------|
| Pre-Class | DML concepts, SELECT/WHERE/GROUP BY, DbGate setup | 30–45 min |
| Lesson Plan | Instructor guide for the 3-hour hands-on session | 3 hours |
| Assignment | The Property Analyst — HDB resale data SQL challenges | 45–60 min |
| Reference | SQL DML cheat sheet, common functions reference | As needed |

### Tools & Setup

- **[DuckDB](https://duckdb.org):** In-process analytical database engine.
- **[DbGate](https://dbgate.org):** Free, cross-platform database manager.
- **Dataset:** `unit-1-4.db` — Singapore HDB resale flat prices (2017).

---

## 1.4 Pre-Class Reading

**Estimated Time:** 30 minutes
**Prerequisites:** Lesson 1.3 — SQL DDL

> In Lesson 1.3 you built the structure of a database — creating tables, defining columns, and setting constraints. This lesson is about working with the *contents* of those tables: querying, filtering, summarising, and transforming data using DML.

---

### Step 1 — Watch the Video (8 min)

🎬 [Intro to SQL DML](https://youtu.be/baODMatLuqE)

---

### Step 2 — Read the Core Concepts (15 min)

#### DDL vs DML — What's the Difference?

| DDL (Lesson 1.3) | DML (This Lesson) |
|---|---|
| `CREATE TABLE` | `SELECT` — retrieve data |
| `ALTER TABLE` | `WHERE` — filter rows |
| `DROP TABLE` | `GROUP BY` — summarise groups |

#### The Key DML Commands

**Retrieve data:**
```sql
SELECT column1, column2 FROM table_name;
```

**Filter results:**
```sql
SELECT * FROM table_name WHERE condition;
-- Example: WHERE resale_price > 450000
```

**Summarise with aggregates:**
```sql
SELECT town, AVG(resale_price) AS avg_price
FROM resale_flat_prices_2017
GROUP BY town;
```

Common aggregate functions: `COUNT()`, `SUM()`, `AVG()`, `MIN()`, `MAX()`

**Transform data on the fly:**
```sql
-- CASE: conditional logic (like IF/ELSE)
SELECT
    CASE
        WHEN resale_price < 400000 THEN 'Budget'
        WHEN resale_price <= 700000 THEN 'Mid-Range'
        ELSE 'Premium'
    END AS price_category
FROM resale_flat_prices_2017;

-- CAST: convert data type
SELECT CAST(floor_area_sqm AS INTEGER) FROM resale_flat_prices_2017;
```

#### The Dataset: Singapore HDB Resale Prices 2017

In class we'll work with real Singapore public housing resale transaction data. Each row represents one flat sold, with columns including `town`, `flat_type`, `floor_area_sqm`, `resale_price`, and `month`.

---

### Step 3 — Tool Setup (5 min)

1. Ensure **DbGate** is installed (from Lesson 1.3)
2. Download `unit-1-4.db` from the course repository
3. Open DbGate → New DuckDB connection → point to `unit-1-4.db`
4. Verify your setup by running:

```sql
SELECT * FROM resale_flat_prices_2017 LIMIT 5;
```

---

### Step 4 — Check Your Understanding

Try to answer these before class, then check below.

1. What is the difference between `WHERE` and `HAVING`?
2. If you want to count how many flats were sold in each town, what SQL structure would you use?
3. What does `SELECT *` return, and why is it sometimes avoided?

<details>
<summary>Suggested answers</summary>

**Q1:** `WHERE` filters *individual rows* before any grouping happens. `HAVING` filters *groups* after a `GROUP BY` — you use it to filter on aggregated values (e.g., `HAVING AVG(resale_price) > 450000`). You can't use `WHERE` to filter on the result of an aggregate function.

**Q2:** `SELECT town, COUNT(*) FROM resale_flat_prices_2017 GROUP BY town;`

**Q3:** `SELECT *` returns every column in the table. It's convenient for exploration, but avoided in production queries because it retrieves more data than needed (slower), and if someone adds or removes columns from the table, your query results change unexpectedly.

</details>

---

## 1.4 Lesson Plan

### Session Overview

| | |
|---|---|
| **Duration** | 3 hours |
| **Format** | Flipped Classroom + Hands-On SQL in DbGate |
| **Tools** | DuckDB + DbGate |
| **Database** | `db/unit-1-4.db` — table: `resale_flat_prices_2017` |
| **Dataset** | Singapore HDB Resale Flat Prices 2017 |

### Agenda

| Time | Part | Topic |
|------|------|-------|
| 0:00 – 0:55 | Part 1 | Selection, Filtering & Sorting — SELECT, WHERE, ORDER BY |
| 0:55 – 1:00 | Break | — |
| 1:00 – 1:55 | Part 2 | Aggregates & Grouping — COUNT, SUM, AVG; GROUP BY; HAVING |
| 1:55 – 2:00 | Break | — |
| 2:00 – 2:55 | Part 3 | Advanced Logic & Data Cleaning — CASE, CAST, date extraction |

---

### Part 1: The Art of Asking — Selection, Filtering & Sorting (55 min)

#### Learning Objectives
Retrieve specific columns, apply mathematical operators, filter datasets, and organize results using sorting.

#### Concept Overview

**Analogy:** Querying a database is like having a conversation with your data:
- `SELECT` says: *"Give me these columns."*
- `FROM` says: *"...from this table."*
- `WHERE` says: *"...but only rows matching this condition."*
- `ORDER BY` says: *"...sorted this way."*

#### Data Dictionary: `main.resale_flat_prices_2017`

| Column Name | Data Type | Description |
|-------------|-----------|-------------|
| month | Datetime (Month) "YYYY-MM" | Transaction month |
| town | Text | Town name |
| flat_type | Text | Type of flat |
| block | Text | Block number |
| street_name | Text | Street name |
| storey_range | Text | Storey range |
| floor_area_sqm | Numeric | Floor area in sqm |
| flat_model | Text | Flat model |
| lease_commence_date | Datetime (Year) | Year lease commenced |
| remaining_lease | Text | Remaining lease |
| resale_price | Numeric ($) | Resale transaction price |

#### Workshop — Task 1: Basic Retrieval & Sorting

See all columns:

```sql
SELECT * FROM resale_flat_prices_2017;
```

Select specific columns and sort by price (ascending is default):

```sql
SELECT town, flat_type, resale_price
FROM resale_flat_prices_2017
ORDER BY resale_price;
```

Sort by price from highest to lowest:

```sql
SELECT *
FROM resale_flat_prices_2017
ORDER BY resale_price DESC;
```

Sort by town alphabetically, then by price (highest first):

```sql
SELECT town, street_name, resale_price
FROM resale_flat_prices_2017
ORDER BY town ASC, resale_price DESC;
```

**Exercise:**
- Select any 3 columns from the table.
- Select flats from highest to lowest resale price in Punggol.

---

#### Workshop — Task 2: Transformations & Filtering

**Operators:**

| Operator | Description |
|----------|-------------|
| `+` | Addition |
| `-` | Subtraction |
| `*` | Multiplication |
| `/` | Division |
| `%` | Modulo |

Example — calculate price in thousands:

```sql
SELECT
  street_name,
  resale_price / 1000 AS price_k
FROM resale_flat_prices_2017
WHERE town = 'PUNGGOL'
  AND resale_price > 500000
ORDER BY resale_price DESC;
```

**Comparison and Logical Operators:**

| Operator | Description |
|----------|-------------|
| `=` | Equal |
| `<>` | Not equal |
| `>` | Greater |
| `>=` | Greater or equal |
| `<` | Less |
| `<=` | Less or equal |
| `AND` | Logical AND |
| `OR` | Logical OR |
| `NOT` | Logical NOT |

**Advanced Filters:**

```sql
-- IN – one of several values
SELECT * FROM resale_flat_prices_2017
WHERE town IN ('BUKIT MERAH', 'BUKIT TIMAH');

-- BETWEEN – numbers in a range
SELECT * FROM resale_flat_prices_2017
WHERE resale_price BETWEEN 400000 AND 500000;

-- LIKE – pattern matching
SELECT * FROM resale_flat_prices_2017
WHERE town LIKE 'B%';

-- DISTINCT – remove duplicates
SELECT DISTINCT town FROM resale_flat_prices_2017;
```

**Functions:**

| Function | Description |
|----------|-------------|
| `ABS()` | Absolute value of a number |
| `ROUND()` | Round to a number of decimal places |
| `LOWER()` | String in lowercase |
| `UPPER()` | String in uppercase |
| `LENGTH()` | Length of a string |
| `TRIM()` | Remove leading and trailing spaces |
| `CONCAT()` | Concatenate strings |

Example:

```sql
SELECT
  LOWER(town) AS town_lower,
  CONCAT(block, ' ', street_name) AS address
FROM resale_flat_prices_2017;
```

#### Reflection

- Do SQL keywords need to be capitalized? Why do we use uppercase for them anyway?
- How would a real estate app like PropertyGuru use these filters when a user moves a slider on their screen?

---

### Part 2: Finding the Big Picture — Aggregates & Grouping (55 min)

#### Learning Objectives
Summarise datasets using aggregate functions and use the `HAVING` clause to filter those summaries.

#### Aggregate Functions

| Function | Description |
|----------|-------------|
| `COUNT()` | Number of rows |
| `SUM()` | Sum of values |
| `AVG()` | Average value |
| `MIN()` | Minimum value |
| `MAX()` | Maximum value |
| `FIRST()` | First value in a column |
| `LAST()` | Last value in a column |

#### Workshop — Task 3: Basic Aggregates

How many transactions happened?

```sql
SELECT COUNT(*) FROM resale_flat_prices_2017;
```

What is the most expensive flat ever sold?

```sql
SELECT MAX(resale_price) FROM resale_flat_prices_2017;
```

Average resale price overall:

```sql
SELECT AVG(resale_price) AS avg_price_overall FROM resale_flat_prices_2017;
```

Average price per town:

```sql
SELECT town, AVG(resale_price) AS avg_price
FROM resale_flat_prices_2017
GROUP BY town;
```

---

#### Workshop — Task 4: GROUP BY & HAVING

> **SQL execution order:**
> 1. FROM / JOIN
> 2. WHERE
> 3. GROUP BY
> 4. AGGREGATE (SUM/AVG/COUNT/MIN/MAX)
> 5. HAVING
> 6. SELECT
> 7. ORDER BY
> 8. LIMIT

**WHERE vs. HAVING side-by-side:**

```sql
-- Filter on individual rows BEFORE grouping
SELECT town, AVG(resale_price) AS avg_price
FROM resale_flat_prices_2017
WHERE resale_price > 600000
GROUP BY town;
```

```sql
-- Filter on the aggregated result AFTER grouping
SELECT town, AVG(resale_price) AS avg_price
FROM resale_flat_prices_2017
GROUP BY town
HAVING AVG(resale_price) > 600000;
```

Filter to show only towns with high average prices:

```sql
SELECT town, AVG(resale_price) AS avg_price
FROM resale_flat_prices_2017
GROUP BY town
HAVING avg_price > 600000
ORDER BY avg_price DESC;
```

> 💡 HAVING accepts aliases defined earlier in the SELECT statement.

Group by multiple columns:

```sql
SELECT town, lease_commence_date, AVG(resale_price) AS avg_price
FROM resale_flat_prices_2017
GROUP BY town, lease_commence_date;
```

#### Reflection

- What happens if you forget the `GROUP BY` but use an `AVG()`?
- If you are a government planner, how does `GROUP BY town` help you decide where to build the next MRT station or school?

---

### Part 3: Advanced Logic & Data Cleaning (55 min)

#### Learning Objectives
Transform data using `CASE` statements for conditional categorisation and `CAST` for type conversion including date extraction.

#### Workshop — Task 5: Categorizing with CASE

**Price Categories:**

```sql
SELECT
  town,
  resale_price,
  CASE
    WHEN resale_price > 1000000 THEN 'Million Dollar Club'
    WHEN resale_price > 500000 THEN 'Mid-Range'
    ELSE 'Entry-Level'
  END AS price_category
FROM resale_flat_prices_2017;
```

Categorize flat sizes:

```sql
SELECT
  town,
  flat_type,
  CASE
    WHEN flat_type IN ('1 ROOM', '2 ROOM', '3 ROOM') THEN 'Small'
    WHEN flat_type = '4 ROOM' THEN 'Medium'
    ELSE 'Large'
  END AS flat_size
FROM resale_flat_prices_2017;
```

---

#### Workshop — Task 6: Dates and Casting

**Casting Numbers:**

```sql
SELECT town, resale_price, CAST(resale_price AS INTEGER) AS resale_price_int
FROM resale_flat_prices_2017;
```

Or using shorthand:

```sql
SELECT town, resale_price, resale_price::INTEGER AS resale_price_int
FROM resale_flat_prices_2017;
```

**Convert text to a real date and extract the year:**

```sql
-- ANSI SQL style
SELECT
    month,
    CAST(month || '-01' AS DATE) AS transaction_date,
    EXTRACT(YEAR FROM CAST(month || '-01' AS DATE)) AS sale_year
FROM resale_flat_prices_2017;
```

```sql
-- DuckDB/PostgreSQL style
SELECT
    month,
    (month || '-01')::DATE AS transaction_date,
    date_part('year', (month || '-01')::DATE) AS sale_year
FROM resale_flat_prices_2017;
```

**Optional — Changing the Table Schema:**

```sql
ALTER TABLE resale_flat_prices_2017
ADD COLUMN transaction_date DATE;

UPDATE resale_flat_prices_2017
SET transaction_date = CONCAT(month, '-01')::DATE;
```

Extract the transaction year:

```sql
SELECT *, date_part('year', transaction_date) AS transaction_year
FROM resale_flat_prices_2017;
```

#### Reflection

- What does the `::` mean in DuckDB/PostgreSQL? How does it relate to `CAST()`?
- Why is it important to standardize date formats when merging data from two different countries?

---

### Wrap-Up

**Key Takeaways:**
1. **SELECT → FROM → WHERE → AGGREGATE → GROUP BY → HAVING → ORDER BY → LIMIT** — this is the logical execution order. Understanding it prevents most beginner SQL errors.
2. Aggregate functions collapse rows — always pair them with `GROUP BY` for meaningful results.
3. `CASE` and `CAST` are your cleaning tools — categorise messy text and convert mistyped columns directly in your query.

**Next Steps:**
- Complete the Assignment.
- Next lesson: Lesson 1.5 goes advanced — JOINs, window functions, and CTEs for complex multi-table analytics.

---

## 1.4 Assignment

**Goal:** Identify the most "undervalued" town.

1. Find the average `resale_price` per town.
2. Filter for towns where the average price is less than $450,000.
3. Within those towns, find the top 5 largest flats (by `floor_area_sqm`) currently available.
4. **Level Up:** Create a new column called `price_per_sqm` and find which town has the lowest average price per square meter.

---

Write the SQL DML statements for the following questions.

**Submission:** Post in **#peer-reviews** on Discord. Questions → **#questions**.

### Question 1

Select the minimum and maximum price per sqm of all the flats.

```sql
-- Your answer here
```

### Question 2

Select the average price per sqm for flats in each town.

```sql
-- Your answer here
```

### Question 3

Categorize flats into price ranges and count how many flats fall into each category:
- Under $400,000: 'Budget'
- $400,000 to $700,000: 'Mid-Range'
- Above $700,000: 'Premium'

Show the counts in descending order.

```sql
-- Your answer here
```

### Question 4

Count the number of flats sold in each town during the first quarter of 2017 (January to March).

```sql
-- Your answer here
```

---

### Solutions

<details>
<summary>Project: The Property Analyst</summary>

```sql
-- The Solution Query
SELECT 
    town, 
    block, 
    street_name, 
    floor_area_sqm, 
    resale_price
FROM resale_flat_prices_2017
WHERE town IN (
    SELECT town
    FROM resale_flat_prices_2017
    GROUP BY town
    HAVING AVG(resale_price) < 450000
)
ORDER BY floor_area_sqm DESC
LIMIT 5;
```

</details>

<details>
<summary>Level Up Solution</summary>

```sql
SELECT 
    town, 
    AVG(resale_price / floor_area_sqm) AS avg_price_per_sqm
FROM resale_flat_prices_2017
GROUP BY town
ORDER BY avg_price_per_sqm ASC
LIMIT 1;
```

</details>

<details>
<summary>Questions 1–4 Solutions</summary>

### Question 1

```sql
SELECT 
    MIN(resale_price / floor_area_sqm) AS min_price_per_sqm, 
    MAX(resale_price / floor_area_sqm) AS max_price_per_sqm
FROM resale_flat_prices_2017;
```

### Question 2

```sql
SELECT 
    town, 
    AVG(resale_price / floor_area_sqm) AS avg_price_per_sqm
FROM resale_flat_prices_2017
GROUP BY town
ORDER BY avg_price_per_sqm DESC;
```

### Question 3

```sql
SELECT 
    CASE 
        WHEN resale_price < 400000 THEN 'Budget'
        WHEN resale_price <= 700000 THEN 'Mid-Range'
        ELSE 'Premium' 
    END AS price_category,
    COUNT(*) AS number_of_flats
FROM resale_flat_prices_2017
GROUP BY price_category
ORDER BY number_of_flats DESC;
```

### Question 4

```sql
SELECT 
    town, 
    COUNT(*) AS flats_sold
FROM resale_flat_prices_2017
WHERE month IN ('2017-01', '2017-02', '2017-03')
GROUP BY town
ORDER BY flats_sold DESC;
```

</details>

**Post-class reading:**
- [DuckDB Documentation on Aggregate Functions](https://duckdb.org/docs/sql/aggregates)

---

## 1.4 Reference

- SQL Cheatsheet: https://www.sqltutorial.org/sql-cheat-sheet/ | https://www.datacamp.com/cheat-sheet/sql-basics-cheat-sheet
- DuckDB Reference: https://duckdb.org/docs/sql/functions/overview
- SQL query order of execution: https://www.sisense.com/blog/sql-query-order-of-operations/
- Introduction to SQL with DuckDB: https://duckdb.org/docs/sql/introduction

---

## 1.4 Scripts

### `db/create_duckdb.py`

```python
import duckdb

con = duckdb.connect("db/unit-1-4.db")

# Download csv file with the name "Resale flat prices based on registration date from Jan-2017 onwards"
# from the data.gov.sg website:
# https://beta.data.gov.sg/datasets/189/resources/d_8b84c4ee58e3cfc0ece0d773c8ca6abc/view
# then store the file (ResaleflatpricesbasedonregistrationdatefromJan2017onwards.csv) in this folder

con.sql(
    "CREATE TABLE resale_flat_prices_2017 AS SELECT * FROM read_csv_auto('db/ResaleflatpricesbasedonregistrationdatefromJan2017onwards.csv', HEADER=TRUE);"
)
```

---

---

# Lesson 1.5 — SQL Advanced

**Theme:** From Tables to Intelligence — joining, ranking, and structuring complex queries

---

## 1.5 Overview

| Section | Duration | Topic / Activity |
|---------|----------|-----------------|
| **Part 1: Joins & Unions** | 55 min | INNER, LEFT, RIGHT, FULL JOIN; UNION; multi-table reporting |
| **Part 2: Window Functions** | 55 min | Running totals; RANK(); QUALIFY; row-level analytics |
| **Part 3: Subqueries & CTEs** | 55 min | Nested queries; IN/EXISTS; Derived tables; Common Table Expressions |

### Learning Outcomes

By the end of this lesson, you will be able to:

1. **Execute** INNER, LEFT, RIGHT, and FULL OUTER JOINs to combine data across multiple tables.
2. **Apply** Window Functions (`SUM OVER`, `RANK OVER`) to compute running totals and rankings without losing row-level detail.
3. **Write** Subqueries using `IN`, `EXISTS`, and derived tables to filter results based on aggregated logic.
4. **Structure** complex analytical queries using Common Table Expressions (CTEs) for readability and reuse.

### Course Materials

| Material | Description | Est. Time |
|----------|-------------|-----------|
| Pre-Class | Metadata queries, JOIN types, DbGate setup | 30–45 min |
| Lesson Plan | Instructor guide for the 3-hour hands-on session | 3 hours |
| Assignment | Insurance Auditor — multi-table analysis challenge | 45–60 min |
| Reference | Advanced SQL cheat sheet — JOINs, window functions, CTEs | As needed |

### Tools & Setup

- **[DuckDB](https://duckdb.org):** In-process analytical database engine.
- **[DbGate](https://dbgate.org):** Free, cross-platform database manager.
- **Dataset:** `unit-1-5.db` — SafeDrive Insurance (clients, cars, claims, addresses).

---

## 1.5 Pre-Class Reading

**Estimated Time:** 30 minutes
**Prerequisites:** Lesson 1.4 — SQL DML

> In Lesson 1.4 you queried, filtered, and aggregated data with `SELECT`, `WHERE`, and `GROUP BY`. This lesson introduces the techniques that unlock *analytical* questions — the kind that can't be answered with a single simple query.

---

### Step 1 — Watch the Video (8 min)

🎬 [Advanced SQL Detective Kit](https://youtu.be/mJGjUi_XvXc)

---

### Step 2 — Read the Core Concepts (15 min)

#### What Makes SQL "Advanced"?

Basic SQL answers simple questions: *"Show me all claims."*
Advanced SQL answers analytical questions: *"For each client, show me their total claims compared to the average for their car type, ranked within their state."*

Three techniques make this possible:

#### A. JOINs — Linking Tables Together

Data in real databases is spread across multiple tables. A JOIN combines rows from two tables based on a shared key.

| Join Type | What it returns |
|---|---|
| `INNER JOIN` | Only rows that match in **both** tables |
| `LEFT JOIN` | All rows from the left table + matching rows from the right (unmatched = NULL) |

```sql
-- Example: Combine claim data with car details
SELECT cl.id, cl.claim_amt, c.car_type
FROM claim cl
INNER JOIN car c ON cl.car_id = c.id;
```

#### B. Window Functions — Row-Level Analytics Without Collapsing

Unlike `GROUP BY` (which collapses rows into groups), window functions add a calculated column *to each row* while keeping all rows visible.

```sql
-- Running total of travel_time per car
SELECT id, car_id, travel_time,
    SUM(travel_time) OVER (PARTITION BY car_id ORDER BY id) AS running_total
FROM claim;
```

- `PARTITION BY` = "do this calculation separately for each group"
- `ORDER BY` inside `OVER()` = "in what order to accumulate"

Also useful: `RANK()`, `ROW_NUMBER()`, `AVG() OVER()`

#### C. CTEs — Breaking Complex Queries into Steps

A **Common Table Expression (CTE)** is a named, temporary result set you define at the top of a query and reference like a table.

```sql
WITH avg_resale AS (
    SELECT car_use, AVG(resale_value) AS avg_val
    FROM car
    GROUP BY car_use
)
SELECT c.id, c.resale_value, c.car_use
FROM car c
JOIN avg_resale a ON c.car_use = a.car_use
WHERE c.resale_value < a.avg_val;
```

---

### Step 3 — Tool Setup (5 min)

1. Ensure **DbGate** is installed (from Lesson 1.3)
2. Download `unit-1-5.db` from the course repository
3. Open DbGate → New DuckDB connection → point to `unit-1-5.db`
4. Verify your setup:

```sql
SELECT * FROM client LIMIT 5;
```

---

### Step 4 — Check Your Understanding

1. You have a `Customers` table and an `Orders` table. Some customers have never placed an order. Which join type keeps *all* customers in the result?
2. What is the key difference between `GROUP BY` and a window function with `PARTITION BY`?
3. In a CTE, once you define `WITH my_cte AS (...)`, how do you use it?

<details>
<summary>Suggested answers</summary>

**Q1:** `LEFT JOIN` (with `Customers` as the left table). An `INNER JOIN` would drop customers with no orders because there's no matching row in `Orders`.

**Q2:** `GROUP BY` collapses all rows in a group into one summary row — you lose the individual row detail. A window function with `PARTITION BY` adds a calculated value to every row while keeping all rows intact.

**Q3:** You reference it by name exactly like a regular table: `SELECT * FROM my_cte` or `JOIN my_cte ON ...`. The CTE only exists for the duration of that single query.

</details>

---

## 1.5 Lesson Plan

### Session Overview

| | |
|---|---|
| **Duration** | 3 hours |
| **Format** | Flipped Classroom + Hands-On SQL in DbGate |
| **Tools** | DuckDB + DbGate |
| **Database** | `db/unit-1-5.db` |

### Agenda

| Time | Part | Topic |
|------|------|-------|
| 0:00 – 0:55 | Part 1 | The Map and the Bridge — Meta Queries, Joins & Unions |
| 0:55 – 1:00 | Break | — |
| 1:00 – 1:55 | Part 2 | The Moving Window — Window Functions |
| 1:55 – 2:00 | Break | — |
| 2:00 – 2:55 | Part 3 | Nested Logic — Subqueries & CTEs |

---

### Part 1: The Map and the Bridge (55 min)

#### Concept Overview

**The Analogy:** Imagine you are at a party. You have a list of names (client) and a list of who brought which gift (claim).

- **Inner Join:** Only people at the party who brought a gift.
- **Left Join:** Everyone at the party; if they didn't bring a gift, the "gift" column is just an empty box (NULL).
- **Union:** Putting two lists of names (e.g., Employees and Contractors) into one long "Staff" list.

#### Workshop

Open DbGate and connect to `db/unit-1-5.db`.

**List and Describe Tables:**

```sql
SHOW TABLES;
```

You should see 4 tables: `address`, `car`, `claim`, `client`.

```sql
SHOW ALL TABLES;
```

```sql
DESCRIBE address;
```

> **Exercise 1:** Describe the other 3 tables. Study their column names and data types.

**Summarize Tables:**

```sql
SUMMARIZE address;
```

> **Exercise 2:** Summarize the other 3 tables. Study their min, max, approx_unique, avg and std.

#### Database ERD

```dbml
Table claim {
  id int [pk]
  claim_date varchar
  travel_time int
  claim_amt int
  motor_vehicle_record int
  car_id int
  client_id int
}

Table car {
  id int [pk]
  resale_value int
  car_type varchar
  car_use varchar
  car_manufacture_year int
}

Table client {
  id int [pk]
  first_name varchar
  last_name varchar
  email varchar
  phone varchar
  birth_year int
  education varchar
  gender varchar
  home_value int
  home_kids int
  income int
  kids_drive int
  marriage_status varchar
  occupation varchar
  address_id int
}

Table address {
  id int [pk]
  country varchar
  state varchar
  city varchar
}

Ref: claim.car_id > car.id
Ref: claim.client_id > client.id
Ref: client.address_id > address.id
```

#### Joins

##### Inner Join

Returns only the rows that match in both tables.

```sql
SELECT *
FROM claim
INNER JOIN car ON claim.car_id = car.id;
```

> Inner join claim and client.
> Inner join client and address.

##### Left Join

Returns all rows from the left table, and the matching rows from the right table.

```sql
SELECT *
FROM claim
LEFT JOIN car ON claim.car_id = car.id;
```

##### Right Join

Returns all rows from the right table, and the matching rows from the left table.

```sql
SELECT *
FROM claim
RIGHT JOIN car ON claim.car_id = car.id;
```

##### Full (Outer) Join

Returns all rows from both tables.

```sql
SELECT *
FROM claim
FULL JOIN car ON claim.car_id = car.id;
```

> Return a joined table containing `id, claim_date, travel_time, claim_amt` from claim, `car_type, car_use` from car, `first_name, last_name` from client and `state, city` from address.

#### Union

A union combines the results of two or more queries into a single result set. The queries must have the same number of columns and compatible data types.

`UNION` removes duplicate rows. Use `UNION ALL` to keep duplicates.

```sql
-- Example syntax (not for this database)
SELECT * FROM employees
UNION
SELECT * FROM contractors;
```

#### Exercise 3: Master Claims Report

Create a master report of every claim. Include the client's name, their car type, and the city they live in.

> Hint: You will need to join 4 tables.

<details>
<summary>Solution for Exercise 3</summary>

```sql
SELECT
  cl.id, cl.claim_date, cl.claim_amt,
  c.car_type,
  cli.first_name, cli.last_name,
  a.city, a.state
FROM claim cl
INNER JOIN car c ON cl.car_id = c.id
INNER JOIN client cli ON cl.client_id = cli.id
INNER JOIN address a ON cli.address_id = a.id;
```

</details>

#### Reflection

- When joining tables, which table should you choose as the "Left" table? What is a useful rule of thumb?
- How would a "Full Outer Join" help us find cars that have never been claimed AND claims that (erroneously) don't have a car attached?

---

### Part 2: The Moving Window (55 min)

#### Concept Overview

**The Analogy:**

A standard `GROUP BY` is like asking "What is the average height of this class?" — you only get one summary line. You no longer see any individual students.

A **window function** keeps every student in the list, but adds calculated columns beside each one — while all the original rows stay visible.

#### Running Total

A running total is a cumulative sum: each row shows the sum of all rows from the start up to that row.

| row | claim_amt | running_total |
|-----|-----------|---------------|
| 1 | 100 | 100 |
| 2 | 50 | 150 |
| 3 | 200 | 350 |
| 4 | 25 | 375 |

```sql
SELECT
  id, claim_amt,
  SUM(claim_amt) OVER (ORDER BY id) AS running_total
FROM claim;
```

With `PARTITION BY` to compute the running total per `car_id`:

```sql
SELECT
  id, car_id, claim_amt,
  SUM(claim_amt) OVER (PARTITION BY car_id ORDER BY id) AS running_total
FROM claim;
```

**Exercise 4:** Calculate a running total of insurance payouts over time (ordered by claim_date).

<details>
<summary>Solution for Exercise 4</summary>

```sql
SELECT
  claim_date, claim_amt,
  SUM(claim_amt) OVER (ORDER BY claim_date) AS running_total
FROM claim;
```

</details>

#### Rank

`RANK()` gives each row a position (1st, 2nd, 3rd, …) within a group, allowing ties to share the same rank and leaving gaps after ties.

```sql
SELECT
  id, car_id, claim_amt,
  RANK() OVER (PARTITION BY car_id ORDER BY claim_amt DESC) AS rank
FROM claim;
```

Result example:

| claim_id | car_id | claim_amt | rank |
| ----: | ----: | ----: | ----: |
| 1 | A | 1000 | 1 |
| 2 | A | 800 | 2 |
| 3 | A | 800 | 2 |
| 4 | A | 500 | 4 |

#### Qualify

The `QUALIFY` clause filters rows based on window function results. To find the highest claim per car type:

```sql
SELECT
  cl.id,
  c.car_type,
  cl.claim_amt,
  RANK() OVER (
    PARTITION BY car_type
    ORDER BY claim_amt DESC
  ) AS rank
FROM claim cl
  JOIN car c ON cl.car_id = c.id
QUALIFY rank = 1
ORDER BY cl.claim_amt DESC;
```

#### Reflection

- What is the key difference between `GROUP BY` and window functions?
- When would you use `RANK()` vs. `ROW_NUMBER()`?

---

### Part 3: Nested Logic — Subqueries & CTEs (55 min)

#### Concept Overview

**A Subquery** is a query nested inside another query — a "thought within a thought."

**A CTE (Common Table Expression)** is like writing down a recipe step before you start cooking — it makes the code readable for humans, not just machines.

#### Subqueries

A subquery is a query nested inside another query.

To find the cars that have been involved in a claim:

```sql
SELECT id, resale_value, car_type
FROM car
WHERE id IN (
  SELECT DISTINCT car_id
  FROM claim
);
```

**Correlated Subquery** — the inner query references the outer query:

```sql
SELECT id, resale_value, car_type
FROM car c
WHERE id IN (
  SELECT DISTINCT car_id
  FROM claim
  WHERE claim_amt > 0.1 * c.resale_value
);
```

**EXISTS operator:**

```sql
SELECT id, resale_value, car_type
FROM car c1
WHERE EXISTS (
  SELECT DISTINCT car_id
  FROM claim c2
  WHERE c2.car_id = c1.id
);
```

**Subquery in FROM (derived table):**

```sql
SELECT car_id, avg_claim_amt
FROM (
  SELECT car_id, AVG(claim_amt) AS avg_claim_amt
  FROM claim
  GROUP BY car_id
) AS avg_claims
WHERE avg_claim_amt > (
  SELECT AVG(claim_amt)
  FROM claim
);
```

#### Common Table Expressions (CTEs)

A CTE is a temporary named result set created within a query. Use CTEs when you need to reference the same query multiple times, or to improve readability.

```sql
WITH avg_claims AS (
  SELECT car_id, AVG(claim_amt) AS avg_claim_amt
  FROM claim
  GROUP BY car_id
)
SELECT car_id, avg_claim_amt
FROM avg_claims
WHERE avg_claim_amt > (
  SELECT AVG(claim_amt)
  FROM claim
);
```

Multiple CTEs in one query:

```sql
WITH avg_claims AS (
  SELECT car_id, AVG(claim_amt) AS avg_claim_amt
  FROM claim
  GROUP BY car_id
),
overall_avg AS (
  SELECT AVG(claim_amt) AS overall_avg
  FROM claim
)
SELECT car_id, avg_claim_amt
FROM avg_claims
WHERE avg_claim_amt > (SELECT overall_avg FROM overall_avg);
```

**Exercise 5:** Create a CTE that finds the total claim amount for each car. Then use this CTE to find the cars with a total claim amount greater than the average.

<details>
<summary>Solution for Exercise 5</summary>

```sql
WITH total_claims AS (
  SELECT car_id, SUM(claim_amt) AS total_claim_amt
  FROM claim
  GROUP BY car_id
)
SELECT car_id, total_claim_amt
FROM total_claims
WHERE total_claim_amt > (SELECT AVG(total_claim_amt) FROM total_claims)
ORDER BY total_claim_amt DESC;
```

</details>

**Exercise 6:** Create a report showing each claim, the client's name, the car type, and the city. Include a column showing the rank of each claim by amount for each car type. Filter to show only the top 3 claims for each car type.

<details>
<summary>Solution for Exercise 6</summary>

```sql
WITH ranked_claims AS (
  SELECT
    cl.id,
    cli.first_name,
    cli.last_name,
    c.car_type,
    a.city,
    cl.claim_amt,
    RANK() OVER (PARTITION BY c.car_type ORDER BY cl.claim_amt DESC) AS rank
  FROM claim cl
  INNER JOIN car c ON cl.car_id = c.id
  INNER JOIN client cli ON cl.client_id = cli.id
  INNER JOIN address a ON cli.address_id = a.id
)
SELECT *
FROM ranked_claims
WHERE rank <= 3
ORDER BY car_type, rank;
```

</details>

#### Reflection

- When would you use a CTE instead of a subquery?
- How would a CTE help you identify "problem clients" (those with multiple high-value claims in a short time period)?

---

### Wrap-Up

**Key Takeaways:**
1. Joins let you combine data from multiple tables — always identify which table is your primary subject.
2. Window functions add calculated columns (running totals, ranks) without collapsing row detail — unlike `GROUP BY`.
3. CTEs make complex queries readable by breaking them into named, reusable steps.

**Optional Topics for Self Study:**
- Window Functions: `LEAD()`, `LAG()`, `FIRST_VALUE()`, `LAST_VALUE()`
- Advanced CTEs: Recursive CTEs for hierarchical data
- Performance Optimization: Indexing and query optimization techniques

**Next Steps:**
- Complete the Assignment.
- Next lesson: Lesson 1.6 introduces NumPy — the numerical foundation of the Python data science stack.

---

## 1.5 Assignment

**Submission:** Post in **#peer-reviews** on Discord. Questions → **#questions**.

### Question 1

Using the `claim` and `car` tables, write a SQL query to return a table containing `id, claim_date, travel_time, claim_amt` from `claim`, and `car_type, car_use` from `car`. Use an appropriate join based on the `car_id`.

```sql
-- Your answer here
```

### Question 2

Write a SQL query to compute the running total of the `travel_time` column for each `car_id` in the `claim` table. The resulting table should contain `id, car_id, travel_time, running_total`.

```sql
-- Your answer here
```

### Question 3

Using a Common Table Expression (CTE), write a SQL query to return a table containing `id, resale_value, car_use` from `car`, where the car resale value is less than the average resale value for the car use.

```sql
-- Your answer here
```

---

### Level Up: The Insurance Auditor Project

**Scenario:** You are the Lead Data Analyst for "SafeDrive Insurance". The CEO suspects that certain car types in specific cities are disproportionately expensive.

**Your Task** — create a comprehensive SQL report using CTEs that answers the following in a single script:

1. **Market Comparison:** For every claim, show the `claim_amt` alongside the **average claim amount for that specific `car_type`**.
2. **Risk Ranking:** Within each state, rank the clients by their total claim amounts.
3. **Efficiency:** Only show the **top 2** highest-claiming clients per state.
4. **Final Output:** The table should include: Client Name, State, Car Type, Total Claimed, State Rank.

**Submission:** Save your work as a `.sql` file with comments explaining your logic. Share in **#peer-reviews** on Discord.

---

### Solutions

<details>
<summary>Questions 1–3 Solutions</summary>

### Question 1

```sql
SELECT 
    cl.id, 
    cl.claim_date, 
    cl.travel_time, 
    cl.claim_amt,
    c.car_type, 
    c.car_use 
FROM claim cl
INNER JOIN car c ON cl.car_id = c.id;
```

### Question 2

```sql
SELECT 
    id,
    car_id,
    travel_time,
    SUM(travel_time) OVER (PARTITION BY car_id ORDER BY id) AS running_total
FROM claim;
```

### Question 3

```sql
WITH AvgResale AS (
    SELECT 
        car_use,
        AVG(resale_value) AS avg_resale_value
    FROM car
    GROUP BY car_use
)
SELECT 
    c.id,
    c.resale_value,
    c.car_use
FROM car c
JOIN AvgResale a ON c.car_use = a.car_use
WHERE c.resale_value < a.avg_resale_value;
```

</details>

<details>
<summary>Level Up: Insurance Auditor Project Solution</summary>

```sql
-- =============================================================================
-- SafeDrive Insurance: Comprehensive Claims Analysis Report
-- Purpose: Identify high-risk clients by car type and state
-- =============================================================================

-- REQUIREMENT 1: Market Comparison
WITH market_comparison AS (
    SELECT 
        cl.id AS claim_id,
        cl.claim_amt,
        cl.car_id,
        cl.client_id,
        ca.car_type,
        AVG(cl.claim_amt) OVER (PARTITION BY ca.car_type) AS avg_claim_by_car_type
    FROM claim cl
    INNER JOIN car ca ON cl.car_id = ca.id
),

-- REQUIREMENT 2: Aggregate total claims per client
client_claim_totals AS (
    SELECT 
        mc.client_id,
        mc.car_type,
        SUM(mc.claim_amt) AS total_claimed
    FROM market_comparison mc
    GROUP BY mc.client_id, mc.car_type
),

-- Join client information to get name and state details
client_with_details AS (
    SELECT 
        c.id AS client_id,
        c.first_name || ' ' || c.last_name AS client_name,
        a.state,
        cct.car_type,
        cct.total_claimed
    FROM client_claim_totals cct
    INNER JOIN client c ON cct.client_id = c.id
    INNER JOIN address a ON c.address_id = a.id
),

-- REQUIREMENT 2: Risk Ranking
ranked_clients AS (
    SELECT 
        client_name,
        state,
        car_type,
        total_claimed,
        RANK() OVER (PARTITION BY state ORDER BY total_claimed DESC) AS state_rank
    FROM client_with_details
)

-- REQUIREMENT 3 & 4: Efficiency Filter + Final Output
SELECT 
    client_name AS "Client Name",
    state AS "State",
    car_type AS "Car Type",
    ROUND(total_claimed, 2) AS "Total Claimed",
    state_rank AS "State Rank"
FROM ranked_clients
WHERE state_rank <= 2
ORDER BY state, state_rank;
```

</details>

---

## 1.5 Reference

- SQL Cheatsheet: https://www.sqltutorial.org/sql-cheat-sheet/
- DuckDB Guides:
  - https://duckdb.org/docs/sql/query_syntax/from
  - https://duckdb.org/docs/sql/window_functions
  - https://duckdb.org/docs/sql/expressions/subqueries
- SQL Joins Cheatsheet: https://www.datacamp.com/cheat-sheet/sql-joins-cheat-sheet
- SQL Window Functions Cheatsheet: https://www.datacamp.com/cheat-sheet/sql-window-functions-cheat-sheet

---

## 1.5 Scripts

### `db/create_duckdb.py`

```python
import duckdb

con = duckdb.connect("db/unit-1-5.db")

con.sql(
    """
    CREATE TABLE address AS SELECT * FROM read_csv_auto('db/address.csv', HEADER=TRUE);
    CREATE TABLE car AS SELECT * FROM read_csv_auto('db/car.csv', HEADER=TRUE);
    CREATE TABLE claim AS SELECT * FROM read_csv_auto('db/claim.csv', HEADER=TRUE);
    CREATE TABLE client AS SELECT * FROM read_csv_auto('db/client.csv', HEADER=TRUE);
    """
)
```

---

*End of SQL Database Module — Unit 1 Course Content*
