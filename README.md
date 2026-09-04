# E-commerce Order & Inventory AI Agent

An AI-powered e-commerce automation system built with n8n, Google Sheets, Gemini, and Gmail. It automates order processing, inventory updates, low-stock alerts, order logging, and weekly sales reporting.

## What It Solves

E-commerce businesses need to keep orders and inventory synchronized while responding quickly when products reach low-stock levels.

This project automates the operational workflow from order intake through inventory management and reporting.

## Tech Stack

- n8n
- Google Sheets
- Google Gemini 2.5 Flash
- Gmail
- JavaScript

## Workflow Architecture

### Order & Inventory Automation

```text
Order Trigger
      ↓
Order Simulator
      ↓
Inventory Lookup
      ↓
Calculate Order
      ↓
Update Inventory
      ↓
Low Stock Check
      ↓
Gmail Low-Stock Alert
      ↓
Log Order in Google Sheets
```

How It Works
1. Order Processing

A new order is received through the order trigger. For the portfolio demonstration, a Shopify-style order is simulated using n8n.

The order contains:

Order ID
Customer name
Customer email
Product ID
Quantity
2. Inventory Lookup

n8n searches the Google Sheets inventory using the Product ID and retrieves:

Product name
Price
Current stock
Low-stock threshold
3. Order Calculation

The workflow calculates:

New inventory level
Order total
Whether the product has reached the low-stock threshold
4. Inventory Update

The product's stock level is automatically updated in Google Sheets.

5. Low-Stock Detection

An IF condition checks whether the updated stock is at or below the configured threshold.

If the condition is true, Gmail sends an automated low-stock alert to the administrator.

6. Order Logging

The processed order is automatically recorded in the Google Sheets orders table, including:

Order ID
Order date
Customer
Product
Quantity
Unit price
Total
Status
Weekly Sales Reporting

A separate scheduled workflow runs every Monday at 9:00 AM IST.

It retrieves the order records and calculates:

Total orders
Total sales
Total units sold
Best-selling product
Low-stock orders

Google Gemini 2.5 Flash then converts these metrics into a concise weekly business summary.

The report includes:

Sales performance
Top product
Inventory alert
Practical recommendation

The completed report is delivered automatically through Gmail.

Demo Result

The portfolio demonstration uses the following test order:

Field	Value
Order ID	ORD-1001
Product	Wireless Headphones
Product ID	P001
Quantity	8
Unit Price	₹2,499
Order Total	₹19,992
Starting Stock	10
Resulting Stock	2
Low-Stock Threshold	3
Status	Low Stock Alert

The workflow successfully:

Looked up the product
Calculated the order
Updated inventory
Detected low stock
Sent the administrator alert
Logged the order in Google Sheets
Generated the weekly sales summary
Screenshots
Workflow Architecture

The complete n8n order and inventory automation workflow.

Inventory Output

The inventory is automatically updated after the order. The demo shows Wireless Headphones stock reduced to 2, reaching the configured low-stock threshold.

Order Log

The processed order is automatically recorded in Google Sheets with the order details, pricing, total, and low-stock status.

Key Outcome

This project demonstrates how AI and workflow automation can connect multiple e-commerce operations into a single system.

The automation reduces manual inventory updates, provides immediate low-stock visibility, maintains structured order records, and turns sales data into a recurring business report.

Repository Contents
README.md — project documentation
ecommerce-order-inventory-agent-sanitized.json — sanitized n8n workflow export
workflow-architecture.png — workflow architecture screenshot
inventory-output.png — inventory result screenshot
google-sheets-output.png — order log screenshot
Security

The workflow JSON included in this repository has been sanitized for portfolio sharing.

Credentials, private Google Sheets identifiers, personal email addresses, webhook identifiers, and instance metadata have been removed or replaced with placeholders.

Future Improvements

Possible production extensions include:

Connect directly to Shopify webhooks
Add WhatsApp customer notifications
Add real-time inventory synchronization
Support multiple products per order
Add sales dashboards
Add automated restock recommendations
