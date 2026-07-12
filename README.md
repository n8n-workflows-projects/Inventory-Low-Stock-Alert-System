# 📦 Inventory Low Stock Alert System

A beginner-friendly inventory management workflow built using **n8n**. This workflow automatically monitors product inventory, identifies low-stock and out-of-stock products, organizes inventory by category, generates inventory reports, and sends email notifications.

The goal of this project was to practice workflow automation using Google Sheets and learn how to manage multiple branches within a single n8n workflow.

---

# 📌 Project Overview

This workflow reads inventory data from Google Sheets and performs multiple inventory management tasks automatically.

It helps keep inventory organized by:

- Monitoring stock levels
- Detecting low-stock products
- Detecting out-of-stock products
- Organizing products into separate category sheets
- Creating inventory summaries
- Finding the top 5 most expensive products
- Sending automated email notifications

---

# 🚀 Workflow

```text
Schedule Trigger
        │
        ▼
Update Google Sheet
        │
        ▼
Read Inventory
        │
        ▼
Switch (Stock Status)
 ┌─────────┬──────────┐
 │         │          │
 ▼         ▼          ▼
Out      Low      Available
Stock    Stock      Stock
 │         │           │
 │         │           ▼
 │         │     Available Sheet
 │         ▼
 │   Sort by Stock
 │         │
 │         ▼
 │   Low Stock Sheet
 │         │
 │         ▼
 │    Inventory Summary
 │
 ▼
Out of Stock Email

Inventory
        │
        ▼
Category Switch
        │
        ├── Electronics
        ├── Furniture
        ├── Home Appliances
        ├── Accessories
        ├── Networking
        ├── Sports
        └── Fitness

Each category is stored in a separate Google Sheet.

Inventory
        │
        ▼
Sort by Price
        │
        ▼
Limit (Top 5)
        │
        ▼
Top 5 Products Sheet
```

---

# 🛠 Nodes Used

| Node | Purpose |
|------|---------|
| Schedule Trigger | Runs the workflow automatically |
| Google Sheets | Read, update, and append inventory data |
| Switch | Separate products based on stock and category |
| Sort | Sort low-stock products and expensive products |
| Summarize | Generate inventory statistics |
| Limit | Select the top 5 expensive products |
| Gmail | Send inventory email reports |
| No Operation | End workflow branches |

---

# 📊 Business Logic

## Stock Status

### Out of Stock

```
Stock = 0
```

- Send email notification
- Save separately

---

### Low Stock

```
Stock < 10
```

- Save to Low Stock Sheet
- Sort products by stock
- Generate inventory report

---

### Available Stock

```
Stock ≥ 10
```

- Save to Available Stock Sheet

---

# 📂 Category Management

Products are automatically separated into different Google Sheets based on their category.

Categories include:

- Electronics
- Furniture
- Home Appliances
- Accessories
- Networking
- Sports
- Fitness

This makes inventory easier to organize and manage.

---

# 📊 Inventory Summary

The workflow calculates:

- Total Products
- Low Stock Products
- Average Stock
- Lowest Stock

These values are saved into a Daily Inventory Report sheet.

---

# 💰 Top 5 Expensive Products

The workflow also:

- Sorts all products by price
- Selects the top 5 most expensive products
- Saves the result into a separate Google Sheet

---

# 📧 Email Notifications

### Out of Stock Alert

Whenever a product has zero stock, the workflow sends an alert email.

Example:

```
Subject:
🚨 Out of Stock Alert

Hello Warehouse Manager,

The following product is currently out of stock.

Product:
Drone

Category:
Electronics

Please arrange for restocking as soon as possible.

Thank you.
```

---

### Daily Inventory Report

The warehouse manager also receives an inventory summary containing:

- Total Products
- Low Stock Products
- Average Stock
- Lowest Stock

---

# 📚 Techniques Used

While building this project, I practiced the following n8n concepts:

- Workflow Automation
- Conditional Routing using Switch
- Multi-Branch Workflow Design
- Google Sheets Integration
- Data Sorting
- Data Limiting
- Inventory Classification
- Category-Based Data Processing
- Inventory Reporting
- Automated Email Notifications
- Scheduled Workflows
- Inventory Monitoring

---

# 🎯 What I Learned

This project helped me understand how to:

- Build workflows with multiple branches
- Organize data into different categories
- Generate inventory reports automatically
- Send email notifications
- Work with large datasets
- Use Sort and Limit nodes effectively
- Design a real-world inventory management workflow

---

# 💻 Technologies Used

- n8n
- Google Sheets
- Gmail

---

# 📂 Project Structure

```
inventory-low-stock-alert-system/
│
├── README.md
├── workflow.json
├── images/
│   ├── workflow.png
│   └── output.png
└── sample-data/
    └── inventory-data.csv
```

---

# 🚀 Future Improvements

Some features I plan to add in the future:

- Slack notifications
- PDF inventory reports
- Warehouse dashboard
- AI-powered inventory insights
- Automatic purchase order generation
- Weekly inventory reports
- Duplicate product detection
- Inventory value calculation

---

# 📸 Workflow Preview


## workflow Design
![image alt](https://github.com/n8n-workflows-projects/Inventory-Low-Stock-Alert-System/blob/d81cf676db701bdabb5291a51a89a80aea03481d/Screenshot%202026-07-12%20123230.png)

## workflow sources
![image alt](https://github.com/n8n-workflows-projects/Inventory-Low-Stock-Alert-System/blob/d81cf676db701bdabb5291a51a89a80aea03481d/Screenshot%202026-07-12%20123341.png)

## workflow output
![image alt](https://github.com/n8n-workflows-projects/Inventory-Low-Stock-Alert-System/blob/d81cf676db701bdabb5291a51a89a80aea03481d/Screenshot%202026-07-12%20122905.png)
![image alt](https://github.com/n8n-workflows-projects/Inventory-Low-Stock-Alert-System/blob/d81cf676db701bdabb5291a51a89a80aea03481d/Screenshot%202026-07-12%20123410.png)
![image alt](https://github.com/n8n-workflows-projects/Inventory-Low-Stock-Alert-System/blob/eebccb2f4acf2159e2f6dd6ef04cbbd938f0e2ad/Screenshot%202026-07-12%20125340.png)






---

# 🙌 About This Project

I built this project while learning n8n to practice inventory automation using Google Sheets. It helped me understand how to create workflows with multiple branches, organize products into categories, generate reports, and automate warehouse notifications.
