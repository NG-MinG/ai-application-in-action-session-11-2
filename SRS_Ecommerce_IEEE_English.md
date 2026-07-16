# Software Requirements Specification (SRS) - E-commerce System

*According to IEEE 830-1998 Standard*

## 1. Introduction

### 1.1 Purpose
This document provides the Software Requirements Specification (SRS) for the E-commerce system. The purpose of this document is to clearly define the functional and non-functional requirements of the system, serving as a foundation for the development team, QA/testers, and project managers throughout the product development lifecycle.

### 1.2 Document Conventions
- The document uses standard fonts, and headings are numbered in a hierarchical structure.
- The priority levels of the requirements are marked as: High, Medium, Low.
- The keyword "Must" indicates a mandatory requirement, and "Should" indicates a highly recommended requirement.

### 1.3 Intended Audience and Reading Suggestions
- **Developers:** To understand the technical and functional requirements to be implemented.
- **Testers/QA:** To design test cases and test scenarios based on specific requirements.
- **Project Managers:** To track progress and evaluate the product's completeness against the requirements.
- **Customers/Product Owners:** To understand what the system will do and approve the requirements.

### 1.4 Product Scope
The E-commerce system is an online shopping platform that allows users to search, view details, add to cart, and purchase products. The system consists of 2 main components:
- **Customer Application (Storefront):** Web/Mobile interface for customers to shop.
- **Admin Dashboard:** Web interface for administrators and sellers to manage products, orders, customers, and revenue reports.

### 1.5 References
- IEEE 830-1998 Standard for Software Requirements Specifications.

---

## 2. Overall Description

### 2.1 Product Perspective
The E-commerce system is an independent web application that integrates with third-party systems such as: Payment Gateways (Stripe, PayPal, VNPay), Shipping/Delivery Services, and Automated Email/SMS Systems.

### 2.2 Product Functions
The main functions include:
- User Management (Registration, login, role-based access control).
- Category and Product Management.
- Product Search and Filtering.
- Cart Management and Checkout Process.
- Order Management and Shipping Status Tracking.
- Product Ratings and Reviews.
- Statistical Reports (Admin).

### 2.3 User Classes and Characteristics
- **Guest:** Can view and search for products but cannot make a purchase without creating an account.
- **Customer:** A registered user who can manage their shopping cart, proceed to checkout, view order history, and rate products.
- **Admin:** Has the highest privileges; manages the entire system (users, products, orders, UI configurations, and reports).

### 2.4 Operating Environment
- **Server:** Linux/Ubuntu OS, Cloud services (AWS/Google Cloud/Azure).
- **Database:** PostgreSQL / MySQL.
- **Client (Browser):** Supports all modern web browsers (Chrome, Safari, Firefox, Edge) on Desktop, Tablet, and Mobile devices.

### 2.5 Design and Implementation Constraints
- The system must be designed using either a Microservices or Monolithic architecture depending on the scale, utilizing popular frameworks (e.g., ReactJS/VueJS for Frontend, Node.js/Java/Python for Backend).
- Password data must be securely hashed (e.g., using Bcrypt) before storage.
- All APIs must comply with RESTful or GraphQL standards.

### 2.6 Assumptions and Dependencies
- The system relies on the stability and availability of third-party services (Payment Gateways, Shipping Providers).
- It is assumed that the customer has a stable Internet connection.

---

## 3. Specific Requirements

### 3.1 Functional Requirements

#### 3.1.1 User Management
- **REQ-01:** The system must allow users to register an account using an Email address or Phone number.
- **REQ-02:** The system should support Social Login (Google, Facebook, Apple).
- **REQ-03:** The system must provide a "Forgot Password" feature and recovery via OTP/Email link.
- **REQ-04:** Administrators must be able to lock/unlock customer accounts.

#### 3.1.2 Product Management
- **REQ-05:** Admins must be able to Add, Edit, and Delete product information (Name, price, description, images, stock quantity).
- **REQ-06:** Customers must be able to search for products by keywords.
- **REQ-07:** The system must allow users to filter products by price range, category, brand, and rating.

#### 3.1.3 Cart & Checkout
- **REQ-08:** Users must be able to add, remove, and update the quantity of products in their shopping cart.
- **REQ-09:** The system must accurately calculate the total amount, including taxes (if applicable) and shipping fees.
- **REQ-10:** Customers must be able to select a payment method (Cash on Delivery, Credit Card, E-Wallet).
- **REQ-11:** The system must send an order confirmation email immediately after a successful purchase.

#### 3.1.4 Order Management
- **REQ-12:** Customers must be able to view their purchase history and current order statuses.
- **REQ-13:** Admins must be able to update order statuses (Pending -> Confirmed -> Shipping -> Completed / Canceled).

### 3.2 External Interface Requirements

#### 3.2.1 User Interfaces
- The user interface must be user-friendly, intuitive, and fully responsive (Responsive Design) for both mobile devices and desktops.
- Must ensure consistency in colors, typography, and layout according to the brand identity guidelines.

#### 3.2.2 Software Interfaces
- **Payment Gateway:** Communicate via HTTPS APIs, utilizing secure encryption.
- **Shipping Service:** Fetch shipping rates and update tracking codes in real-time via REST APIs.

### 3.3 Non-Functional Requirements

#### 3.3.1 Performance
- The page load time must not exceed 3 seconds under a standard network connection.
- The system must support a minimum of 10,000 concurrent users during high-traffic events (e.g., Flash Sales).

#### 3.3.2 Security
- The system must enforce SSL certificates (HTTPS) across the entire application.
- Must prevent common web vulnerabilities such as SQL Injection, XSS, and CSRF.
- The system must not store customers' raw credit card information directly (Must utilize Payment Gateway Tokenization).

#### 3.3.3 Availability
- The system's Uptime must be at least 99.9%.
- The system must have an automated daily data backup mechanism.

#### 3.3.4 Scalability
- The system must be capable of Auto-scaling resources on the Cloud environment when traffic spikes unexpectedly.

---

## 4. Appendices
- **Glossary:**
  - **COD (Cash on Delivery):** Payment made directly to the courier upon delivery of the goods.
  - **OTP (One-Time Password):** A dynamically generated password valid for only one login session or transaction.
  - **API (Application Programming Interface):** A set of protocols for building and integrating application software, allowing different systems to communicate.
