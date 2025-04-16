# 🚀 Deployment Notes – PRMMA (Property Rental & Maintenance Management App)

These instructions explain how to recreate the PRMMA Salesforce application in a fresh Salesforce Developer Org using the provided project files.

---

## ✅ 1. Environment Setup

1. Sign up for a free Salesforce Developer Org:  
   https://developer.salesforce.com/signup

2. Log in and switch to the **App Launcher** to access objects and setup tools.

---

## 🧱 2. Create Custom Objects

Create the following custom objects with these Record Name types:

| Object Name         | Record Name           | Data Type   |
|----------------------|------------------------|-------------|
| Property             | Property Name          | Text        |
| Tenant               | Tenant Name            | Text        |
| Rental Agreement     | Agreement ID           | Auto Number (RA-{0001}) |
| Maintenance          | Request ID             | Auto Number (MR-{0001}) |
| Payment              | Payment ID             | Auto Number (PAY-{0001}) |

Make sure to enable:  
✅ Allow Reports  
✅ Track Field History (optional)  
✅ Allow Activities

---

## 🔗 3. Add Lookup Relationships

| From Object         | To Object     | Field Type      |
|---------------------|---------------|------------------|
| Rental Agreement     | Property      | Lookup           |
| Rental Agreement     | Tenant        | Lookup           |
| Maintenance          | Property      | Lookup           |
| Maintenance          | Tenant        | Lookup (optional)|
| Payment              | Rental Agreement | Lookup         |

---

## 🔣 4. Create Fields

Create all custom fields as listed in `objects-design.md` for each object.

---

## 🧩 5. Create Tabs for All Objects

Go to **Setup → Tabs** and create custom tabs for:

- Property
- Tenant
- Rental Agreement
- Maintenance
- Payment

Add them to a new App (optional):  
🧭 *Property Rental Manager*

---

## 📥 6. Import Sample Data

Use **Data Import Wizard** or **Data Loader** to import the sample data provided in the `/data-sample/` folder.

⚠️ Import Order (due to relationships):

1. Property.csv  
2. Tenant.csv  
3. RentalAgreement.csv  
4. Maintenance.csv  
5. Payment.csv

Make sure to map lookup fields using Salesforce Record IDs.

---

## 🔄 7. Build Automation Flows

Recreate these Flows (screenshots provided in `/flow-screenshots/`):

### Flow 1: Auto-Create Payment
- Trigger: When Rental_Agreement__c is created and Status = Active
- Action: Create a Payment__c record

### Flow 2: Notify on Maintenance Closed
- Trigger: When Maintenance__c is updated and Status changes to Closed
- Action: Send email or in-app notification

---

## 📊 8. Create Reports

Create custom report types for:

- Rental Agreements with Tenant and Property
- Maintenance by Property
- Payments with Agreements

Then build reports like:
- Agreements by Status
- Rent by Property
- Maintenance Requests by Priority
- Monthly Rent Collected
- Upcoming Payments

---

## 📈 9. Build Dashboard

Create a Dashboard named:
> `Rental Management Overview`

Use the reports to add:
- Bar Chart: Rent Collected Per Month
- Table: Upcoming Payments
- Pie Chart: Maintenance by Status
- Table: Active Agreements
- Gauge: Occupancy Rate (manual)

---

## 📸 10. Optional – Upload Screenshots

You can upload dashboard screenshots or flow designs using the **Files tab** in Salesforce or attach them here in your GitHub repo under `/flow-screenshots/`.

---

## ✅ Done!

Your Property Rental & Maintenance App is ready to demo!

This project demonstrates your ability to:
- Architect relational data models
- Build process automation with Flows
- Create reports and dashboards for business operations
- Handle data import/export for real-world testing
