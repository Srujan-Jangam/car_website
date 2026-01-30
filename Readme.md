# 🚗 Elite Motors – Luxury Car E-Commerce (Database)

This repository contains the **MySQL database schema and seed data** for **Elite Motors**, a luxury car e-commerce platform.  
The database supports car listings, customer inquiries, user authentication, and admin management.

---

## 📌 Features

- User authentication with roles (**admin / user**)
- Luxury car inventory management
- Customer inquiries linked to cars
- Customer reviews
- Admin-ready database structure
- Foreign key integrity using **InnoDB**

---

## 🛠️ Tech Stack

- **Database:** MySQL  
- **Tested On:** phpMyAdmin  
- **Storage Engine:** InnoDB  

---

## 🗂️ Database Tables

### 1️⃣ Users
Stores registered users and admin accounts.

**Fields**
- `id` (Primary Key)
- `username`
- `email` (Unique)
- `password` (Hashed)
- `role` (user / admin)
- `created_at`

---

### 2️⃣ Cars
Stores luxury car inventory.

**Fields**
- `id` (Primary Key)
- `make`
- `model`
- `price`
- `description`
- `image_url`
- `stock_status` (available / sold)

---

### 3️⃣ Inquiries
Stores customer inquiries related to cars.

**Fields**
- `id` (Primary Key)
- `car_id` (Foreign Key → cars.id)
- `customer_name`
- `customer_email`
- `customer_phone`
- `message`
- `created_at`

**Constraint**
- `ON DELETE CASCADE` to maintain referential integrity

---

### 4️⃣ Reviews
Stores customer reviews and ratings.

**Fields**
- `id` (Primary Key)
- `customer_name`
- `rating`
- `review_text`
- `created_at`

---

## 🔄 Data Reset Strategy

This project **does not use `TRUNCATE`** due to foreign key constraints.

Instead, it safely clears data using:

```sql
DELETE FROM inquiries;
DELETE FROM reviews;
DELETE FROM cars;
DELETE FROM users;
✔ Foreign-key safe
✔ Works reliably in phpMyAdmin
✔ Prevents #1701 errors
Auto-increment values are reset manually after deletion.
```

🔐 Admin Credentials (Demo Only)
Email: admin@elite.com
Password: admin123
Role: admin


⚠️ For testing/demo purposes only.
Change credentials before production use.

🚀 How to Run

Open phpMyAdmin

Create a database (or let the SQL script create it)

Import the provided SQL file

Verify tables and sample data

Connect the database to your backend application

📁 Recommended Repository Structure

```
elite-motors-db/
│
├── database.sql
├── README.md
└── screenshots/ (optional)
```

📎 Notes

Suitable for academic projects and prototypes

Easy to extend with payments, orders, or analytics

Designed to avoid common MySQL foreign key issues

👨‍💻 Author

Developed as part of a luxury e-commerce mini project for learning database design and full-stack development.