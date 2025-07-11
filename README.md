**Salesforce CRM Project Documentation**

**Project Title**: *HandsMen Threads: Elevating the Art of Sophistication in Men's Fashion*

**Submitted by**: Indranil Ghosh
**Institution**: Academy of Technology
**Date**: 11/07/2025

---

### **Project Overview**

HandsMen Threads, a fashion-forward organization, aims to implement a Salesforce CRM solution to enhance their data management and customer engagement. The project builds a robust data model and automation framework that ensures streamlined operations across departments like sales, inventory, and marketing. It integrates intelligent features such as automatic order confirmations, loyalty status updates, and low-stock alerts to support dynamic business workflows.

---

### **Objectives**

* Streamline customer and order data management.
* Enable automated communication with customers and internal teams.
* Build a loyalty program based on customer purchase history.
* Maintain accurate inventory levels using automation.
* Ensure secure access and control using roles and permissions.

---

### **Phase 1: Requirement Analysis & Planning**

#### Understanding Business Requirements

* Capture and manage customer information.
* Record product catalog and track inventory.
* Enable order management and status updates.
* Execute targeted marketing campaigns.

#### Defining Project Scope and Objectives

* Design five custom objects: HandsMen Customer, HandsMen Order, HandsMen Product, Inventory, and Marketing Campaign.
* Create relationships: Lookup between Campaign → Customer and Product → Order.
* Automate workflows for stock alerts, loyalty updates, and order confirmations.
* Design batch jobs for weekly loyalty updates and daily inventory sync.

#### Design Data Model and Security Model

* Create required fields with validation rules.
* Set up roles: Inventory Manager, Sales, Marketing.
* Assign profiles and permission sets accordingly.

---

### **Phase 2: Salesforce Development – Backend & Configurations**

#### Setup Environment & DevOps Workflow

* Salesforce Developer Org created.
* Change Set deployment used for migration.

#### Custom Objects and Fields

* **HandsMen Customer**: Name, Email, Phone, Loyalty\_Status\_\_c, Total\_Purchases\_\_c
* **HandsMen Product**: Name, SKU, Price, Stock\_Quantity\_\_c
* **HandsMen Order**: Order\_Number, Status, Quantity\_\_c, Total\_Amount\_\_c
* **Inventory**: Auto Number, Warehouse, Stock\_Quantity\_\_c
* **Marketing Campaign**: Campaign\_Name, Start\_Date, End\_Date

#### Relationships

* Lookup: HandsMen Customer ↔ Marketing Campaign
* Lookup: HandsMen Product ↔ HandsMen Order

#### Validation Rules

* **Order**: Total\_Amount\_\_c must be greater than 0
* **Inventory**: Stock\_Quantity\_\_c must be numeric
* **Customer**: Valid Email format

#### Formula Fields

* **Inventory**: Stock\_Status\_\_c (e.g., IF(Stock\_Quantity\_\_c < 5, "Low", "In Stock"))
* **Customer**: Full\_Name\_\_c = FirstName + " " + LastName (if fields are separated)

#### Automation

* **Flows**:

  * Order Confirmation (Record-Triggered)
  * Stock Alert Flow (Record-Triggered)
  * Loyalty Status Flow (Scheduled)
* **Apex Triggers**:

  * `UpdateOrderTotalTrigger` on Order\_\_c
  * `StockDeductionTrigger` on Inventory\_\_c
  * `LoyaltyStatusUpdateTrigger` on Customer\_\_c

#### Apex Batch Jobs

* **Loyalty Points Calculation**: Weekly on Sunday 12 AM
* **Inventory Sync**: Daily at 2 AM

---

### **Phase 3: UI/UX Development & Customization**

* Lightning App: *HandsMen Threads CRM*
* Page Layouts: Customized for each object
* Dynamic Forms used in Customer and Order
* Reports: Top Customers, Low Stock Products
* Dashboards: Sales Overview, Inventory Levels

---

### **Phase 4: Data Migration, Testing & Security**

#### Data Loading

* Tool Used: Data Import Wizard

#### Security Configuration

* **Profiles**: Standard and Custom profiles created
* **Roles**: Inventory Manager, Sales, Marketing
* **Users**: Niklaus Mikaelson, Kol Mikaelson, plus 2 additional users
* **Permission Sets**:

  * Sales Manager: Full access to Customers & Orders
  * Inventory Manager: Read/Edit on Inventory & Products
  * Marketing Team: Read on Customers, Edit on Campaigns

#### Email Templates

* Order Confirmation Email
* Low Stock Alert Email
* Loyalty Program Email

#### Testing Approach

* Unit testing of triggers and flows
* Test Class coverage ensured for Apex triggers
* Test Cases with screenshots for:

  * Booking creation
  * Order status update
  * Stock Alert email
  * Loyalty tier upgrade

---

### **Phase 5: Deployment, Documentation & Maintenance**

#### Deployment Strategy

* Using Change Sets from Sandbox to Production

#### Maintenance Plan

* Weekly data checks and automation monitoring
* User feedback and issue logging

#### Troubleshooting Approach

* Use of Debug Logs and Flow Fault Paths
* Apex Exception handling with try-catch blocks

---

### **Conclusion**

The HandsMen Threads Salesforce CRM project successfully demonstrates how to integrate customer, order, and inventory management into a scalable and secure platform. The automation and scheduled jobs enhance operational efficiency, while dashboards and reports offer valuable business insights. The project was fully tested, documented, and is ready for future enhancements.

---

### **Future Enhancements**

* Integration with WhatsApp or SMS for order alerts.
* AI Recommendations for product suggestions.
* Chatbot to handle FAQs and guide customers through orders.

---

### **Appendix**

* Screenshots of object fields, flows, dashboards, and permission sets.
* ER Diagram and Object Model
* Sample test case results and screen captures.

