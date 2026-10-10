# Prisma Schema Design 

A database schema design project built using **Prisma ORM, PostgreSQL, Node.js, and Supabase**. The project demonstrates how to design relational databases, define data models, establish relationships, apply constraints, and manage database migrations using Prisma.

## Project Overview

This assignment focuses on designing three real-world database systems within a single Prisma schema file:

1. **Blog Platform** – Manages users, posts, comments, and tags.
2. **E-Commerce Platform** – Manages products, categories, customers, orders, and order items.
3. **School Management System** – Manages departments, teachers, courses, students, and enrolments.

The project also includes an optional bonus challenge implementing an enum for order status management.

## Project Objectives

By completing this project, I aim to demonstrate my understanding of:

- Designing relational database schemas using Prisma ORM.
- Defining models, fields, primary keys, and foreign keys.
- Implementing one-to-many and many-to-many relationships.
- Applying database constraints such as `@id`, `@unique`, and `@default`.
- Using optional fields, timestamps, and appropriate data types.
- Creating junction tables for complex relationships.
- Performing database migrations with Prisma CLI.
- Connecting Prisma ORM to a PostgreSQL database hosted on Supabase.
- Managing database structures using Prisma Studio.

## Technologies Used

| Technology | Purpose |
|------------|---------|
| Node.js | JavaScript runtime environment |
| Prisma ORM | Database modelling and schema management |
| PostgreSQL | Relational database |
| Supabase | PostgreSQL database hosting |
| Prisma CLI | Schema validation and migrations |
| Prisma Studio | Database visualisation |
| VS Code | Development environment |
| Git & GitHub | Version control and project hosting |

## Live Pages
[Live] (https://dominic-kores.github.io/prisma-schema-design/)

## Project Structure

```text
week-6-day-2-assignment/
│
├── prisma/
│   ├── schema.prisma
│   └── migrations/
│
├── screenshots/
│   ├── blog-schema.png
│   ├── ecommerce-schema.png
│   ├── school-schema.png
│   
│
├── .env
├── .gitignore
├── package.json
├── package-lock.json
└── README.md
```

## Task 1: Blog Platform Schema

Designed a relational database for a blogging platform using four models.

| Model | Description |
|-------|-------------|
| User | Stores registered users and author details |
| Post | Stores blog articles published by users |
| Comment | Stores user comments on blog posts |
| Tag | Stores unique tags used to categorise posts |

### Relationships

- One User can create many Posts.
- One User can write many Comments.
- One Post can have many Comments.
- One Post can have many Tags.
- One Tag can belong to many Posts.

**Key Concepts:** One-to-many relationships, many-to-many relationships, unique constraints, optional fields, timestamps, and foreign keys.

### Migration Command

```bash
npx prisma migrate dev --name blog-schema
```


## Task 2: E-Commerce Platform Schema

Extended the existing Prisma schema by adding four models to represent an e-commerce system.

| Model | Description |
|-------|-------------|
| Category | Organises products into categories |
| Product | Stores product information, pricing, and inventory |
| Order | Stores customer orders and payment totals |
| OrderItem | Connects products to orders and stores quantities and purchase prices |

### Relationships

- One Category has many Products.
- One Product belongs to one Category.
- One User can place many Orders.
- One Order contains many OrderItems.
- One Product can appear in many OrderItems.

**Key Concepts:** Decimal data types for prices, foreign keys, order management, reusable relationships, and junction tables.

The existing `User` model was extended to include the `orders` relationship.

### Migration Command

```bash
npx prisma migrate dev --name ecommerce-schema
```

## Task 3: School Management Schema

Designed a database for managing academic departments, teaching staff, students, courses, and enrolments.

| Model | Description |
|-------|-------------|
| Department | Stores academic departments |
| Teacher | Stores teaching staff information |
| Course | Stores available academic courses |
| Student | Stores student details |
| Enrollment | Connects students to courses and stores grades |

### Relationships

- One Department has many Teachers.
- One Department offers many Courses.
- One Teacher teaches many Courses.
- One Student can enrol in many Courses.
- One Course can have many Students.

The `Enrollment` model acts as a junction table between students and courses.

### Unique Constraint

```prisma
@@unique([studentId, courseId])
```

This ensures that a student cannot be enrolled in the same course more than once.

**Key Concepts:** Composite unique constraints, junction tables, academic records, and many-to-many relationships.

### Migration Command

```bash
npx prisma migrate dev --name school-schema
```

##  Prisma Enums

Implemented an `OrderStatus` enum to restrict order statuses to predefined values.

```prisma
enum OrderStatus {
  PENDING
  PROCESSING
  SHIPPED
  DELIVERED
  CANCELLED
}
```

Updated the `Order` model to use:

```prisma
status OrderStatus @default(PENDING)
```

### Bonus Migration

```bash
npx prisma migrate dev --name order-status-enum
```

**Benefit:** Enums improve consistency and type safety by preventing unsupported order status values.


## Learning Outcomes

Through this assignment, I gained practical experience in designing relational database schemas using Prisma ORM.

I developed a stronger understanding of how models relate to one another, how foreign keys maintain data relationships, and how junction tables support many-to-many relationships.

I also practised applying field constraints, working with PostgreSQL data types, managing schema changes using Prisma migrations, and inspecting database structures through Prisma Studio.

These skills provide a foundation for developing database-driven applications using Node.js, Express, and React.




## Author

**Dominic Kisioya**

Full-Stack Software & AI Engineer


