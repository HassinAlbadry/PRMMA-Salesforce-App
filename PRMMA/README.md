# 🏘️ Property Rental & Maintenance Management App (PRMMA)

A full-featured Salesforce application to manage rental properties, tenants, lease agreements, maintenance requests, and payments. Built from scratch using custom objects, Flows, reports, dashboards, and automation.

---

## 📌 Features

- 🔧 **Custom Objects** for Property, Tenant, Rental Agreement, Maintenance, and Payment
- 🔗 **Lookup Relationships** to connect records and maintain data integrity
- 🔄 **Flows** to automate:
  - Creating Payment records when a Rental Agreement is signed
  - Notifying users when Maintenance is resolved
- 📊 **Reports & Dashboards** to track rent collection, agreement trends, and maintenance status
- 📂 **Sample Data** provided in CSV format for testing and import practice
- 📸 Includes screenshots of Flows and Dashboards for demonstration

---

## 🧱 Data Model

### Objects Used:

- `Property__c`: Address, Type, Status, Owner, Rent
- `Tenant__c`: Name, Contact Info, Start Date
- `Rental_Agreement__c`: Links Property and Tenant, Rent amount, Deposit, Duration
- `Maintenance__c`: Issue, Status, Priority, Resolution
- `Payment__c`: Linked to Rental Agreement, Amount, Method, Status

Relationships:
- `Rental_Agreement__c` → Lookup to `Property__c` and `Tenant__c`
- `Payment__c` → Lookup to `Rental_Agreement__c`
- `Maintenance__c` → Lookup to `Property__c` and optional `Tenant__c`

---

## ⚙️ Automations

### 1. Auto-create Payment on Agreement Creation
- Flow: Record-triggered
- Trigger: Rental Agreement Status = Active
- Action: Create a related Payment record

### 2. Notify on Maintenance Closure
- Flow: Record-triggered
- Trigger: Maintenance Status changed to Closed
- Action: Send in-app notification/email

---

## 📊 Dashboard Overview

- **Monthly Rent Collected** (Bar Chart)
- **Upcoming Payments** (Table)
- **Maintenance by Status** (Pie Chart)
- **Occupancy Rate** (Gauge)
- **Active Rental Agreements** (Table)

---


## 🛠️ How to Use

1. Create a Salesforce Developer Org
2. Recreate the custom objects & fields listed in `objects-design.md`
3. Import sample data using Data Import Wizard or Data Loader
4. Build Flows as shown in screenshots
5. Use reports to create dashboards

---

## 👨‍💻 Author

**Hassin Albadry**  
Salesforce Developer  