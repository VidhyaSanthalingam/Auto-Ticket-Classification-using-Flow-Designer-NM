# Auto Ticket Classification using Flow Designer

Automated ticket classification and routing to improve service management efficiency and reduce manual effort.


## 📑 Table of Contents

1. Overview
2. Objectives
3. Scope and Prerequisites
4. Flow Designer Overview
5. Flow Implementation
6. Ticket Classification
7. Testing and Validation
8. Best Practices
9. Expected Benefits
10. Conclusion

---

## 1. Overview

The **Auto Ticket Classification using Flow Designer** project automates
the classification of incident tickets in ServiceNow.

The system analyzes the information provided in an incident and automatically
classifies the ticket based on predefined conditions. This reduces manual
classification and improves ticket handling efficiency.

---

## 2. Objectives

- Automate incident ticket classification.
- Reduce manual work for Service Desk agents.
- Improve ticket routing and assignment.
- Ensure consistent ticket categorization.
- Improve response and resolution time.
- Maintain better data quality in incident records.

---

## 3. Scope and Prerequisites

### Scope

This project focuses on automatically classifying Incident records using
ServiceNow Flow Designer.

The flow can classify tickets based on:

- Short Description
- Description
- Category
- Subcategory
- Priority
- Impact
- Urgency

### Prerequisites

- ServiceNow instance
- Basic knowledge of ServiceNow
- Access to Flow Designer
- Incident table [incident]
- Required roles and permissions

---

## 4. Flow Designer Overview

ServiceNow **Flow Designer** is used to automate business processes
without writing complex code.

The flow consists of:

**Trigger → Conditions → Classification → Assignment → Update Record**

### Flow Components

- Trigger: Incident is created or updated.
- Conditions: Check incident details.
- Classification: Identify the ticket type.
- Assignment: Route the ticket to the appropriate group.
- Update Record: Update category and other required fields.

---

## 5. Flow Implementation

### Step 1: Create a New Flow

Navigate to:

**All → Flow Designer → New → Flow**

Enter the flow name:

**Auto Ticket Classification**

---

### Step 2: Configure Trigger

Select:

**Trigger: Record Created or Updated**

Table:

**Incident [incident]**

Configure the required conditions for the flow.

---

### Step 3: Add Classification Conditions

Use conditional logic to identify the type of ticket.

Example:

```text
IF Short Description contains "password"
    → Category = Software
    → Subcategory = Password Reset

IF Short Description contains "network"
    → Category = Network
    → Subcategory = Connectivity

IF Short Description contains "laptop"
    → Category = Hardware
    → Subcategory = Laptop

IF Short Description contains "email"
    → Category = Software
    → Subcategory = Email
