# 🧱 Object Design – PRMMA (Property Rental & Maintenance Management App)

This document outlines the custom objects, fields, and relationships used in the PRMMA Salesforce application.

---

## 🔹 1. Property__c

**Purpose**: Represents a physical rental unit such as a house, apartment, or office.

| Field Name            | Data Type     | Description                          |
|----------------------|---------------|--------------------------------------|
| Property Name         | Text          | Name or identifier of the property   |
| Address__c            | Text Area     | Full street address                  |
| Type__c               | Picklist      | Apartment, House, Office, Condo      |
| Status__c             | Picklist      | Available, Occupied, Maintenance     |
| Owner_Name__c         | Text          | Property owner's name                |
| Monthly_Rent__c       | Currency      | Rent amount per month                |
| Description__c        | Long Text     | Additional notes                     |
| Number_of_Rooms__c    | Number        | Number of rooms in the unit          |

---

## 🔹 2. Tenant__c

**Purpose**: Represents a renter who signs a rental agreement.

| Field Name       | Data Type     | Description                          |
|------------------|---------------|--------------------------------------|
| Tenant Name       | Text          | Full name of the tenant              |
| Phone__c          | Phone         | Contact number                       |
| Email__c          | Email         | Email address                        |
| Address__c        | Text Area     | Tenant's current address             |
| Start_Date__c     | Date          | Date when tenant moved in            |

> **Note**: Files related list used to upload ID proof documents.

---

## 🔹 3. Rental_Agreement__c

**Purpose**: Represents a lease agreement between a tenant and a property.

| Field Name              | Data Type     | Description                          |
|-------------------------|---------------|--------------------------------------|
| Agreement ID (Name)     | Auto Number   | Format: RA-{0001}                    |
| Start_Date__c           | Date          | Lease start date                     |
| End_Date__c             | Date          | Lease end date                       |
| Rent_Amount__c          | Currency      | Monthly rent as per contract         |
| Deposit__c              | Currency      | Security deposit amount              |
| Payment_Frequency__c    | Picklist      | Monthly, Quarterly, Annually         |
| Status__c               | Picklist      | Active, Ended, Canceled              |
| Property__c             | Lookup        | Linked to Property__c                |
| Tenant__c               | Lookup        | Linked to Tenant__c                  |

---

## 🔹 4. Maintenance__c

**Purpose**: Represents maintenance requests for a specific property.

| Field Name            | Data Type     | Description                          |
|-----------------------|---------------|--------------------------------------|
| Request ID (Name)     | Auto Number   | Format: MR-{0001}                    |
| Issue_Type__c         | Picklist      | Plumbing, Electrical, HVAC, etc.     |
| Description__c        | Long Text     | Issue details                        |
| Date_Reported__c      | Date          | When the issue was reported          |
| Status__c             | Picklist      | Open, In Progress, Closed            |
| Priority__c           | Picklist      | Low, Medium, High                    |
| Resolution__c         | Long Text     | Resolution notes                     |
| Property__c           | Lookup        | Linked to Property__c                |
| Tenant__c (optional)  | Lookup        | Linked to Tenant__c                  |

---

## 🔹 5. Payment__c

**Purpose**: Tracks rent and deposit payments for a rental agreement.

| Field Name            | Data Type     | Description                          |
|------------------------|---------------|--------------------------------------|
| Payment ID (Name)      | Auto Number   | Format: PAY-{0001}                   |
| Amount__c              | Currency      | Amount paid                          |
| Payment_Date__c        | Date          | Payment date                         |
| Method__c              | Picklist      | Cash, Credit, Bank Transfer, Check   |
| Status__c              | Picklist      | Paid, Pending, Failed                |
| Notes__c               | Long Text     | Notes on transaction                 |
| Rental_Agreement__c    | Lookup        | Linked to Rental_Agreement__c        |

---

## 🔗 Object Relationships Summary

| Child Object          | Parent Object(s)              | Field(s)                      |
|------------------------|-------------------------------|-------------------------------|
| Rental_Agreement__c    | Property__c, Tenant__c        | Property__c, Tenant__c        |
| Maintenance__c         | Property__c, Tenant__c        | Property__c, Tenant__c        |
| Payment__c             | Rental_Agreement__c           | Rental_Agreement__c           |

---

## 📌 Notes

- Lookup relationships used to maintain flexibility
- Reports leverage related fields like `Tenant__r.Name` and `Property__r.Name`
- Automations trigger on Rental Agreement and Maintenance objects

