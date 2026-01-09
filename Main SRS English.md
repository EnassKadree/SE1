p# Software Requirements Specification (SRS)
## E-Commerce Management System

**Project Title:** Comprehensive E-Commerce Management System  
**Academic Year:** 2025-2026  
**Course:** Software Engineering I  
**Document Version:** 1.0  
**Date:** 10-1-2026
**Authors:** 
  - Enass Al-Kadree Al-Haijanee
  - Batoul Nassar Nassar
  - Joelle Butros
  - Rawan Zoa'iter
  - Manar Al-Jarkas

---

## Table of Contents

1. [Introduction](#1-introduction)
2. [Overall Description](#2-overall-description)
3. [Functional Requirements](#3-functional-requirements)
4. [Non-Functional Requirements](#4-non-functional-requirements)
5. [Future Enhancements (Out of Scope)](#5-future-enhancements-out-of-scope)
6. [Appendix A: Use Case Diagrams](#appendix-a-use-case-diagrams)
7. [Appendix B: Entity Relationship Diagrams](#appendix-b-entity-relationship-diagrams)



## 1. Introduction

### 1.1 Purpose
This document provides a comprehensive Software Requirements Specification (SRS) for a complete e-commerce management system designed to automate all business operations for a large retail store in the Syrian Arab Republic. The system aims to digitize the entire business workflow from product display to warehouse management, order fulfillment, and financial operations.

### 1.2 Scope
The system encompasses two main applications:
- **Customer Application (Mobile/Web)**: For end-users to browse, search, and purchase products
- **Admin Panel (Web Application)**: For system administrators and staff to manage all aspects of the business

### 1.3 Business Context
The system is designed for a large retail store with:
- Daily sales exceeding 1,000 transactions
- Diverse product categories (Electronics, Food, Household Items, Medical Products)
- Large warehouse inventory
- Multiple Syrian provinces for delivery
- Need for complete automation and reduced physical store visits

---

## 2. Overall Description

### 2.1 System Description
The e-commerce system is a comprehensive platform that automates:
- Product catalog management
- Customer authentication and authorization
- Shopping cart and order processing
- Inventory tracking and management
- Order fulfillment workflow
- Financial transaction processing
- Delivery and shipping management
- Employee and role management
- Reporting and analytics

### 2.2 Product Functions

This section provides a high-level summary of the major functions that the E-Commerce Management System must perform. Detailed specifications for each function are provided in Section 3 (Functional Requirements). The system consists of two main applications with distinct functional areas as described below.

#### 2.2.1 Customer Application Functions

**Product Discovery and Browsing**
- Display products by categories and brands with search, filtering, and sorting capabilities
- Customizable homepage with featured products, new arrivals, and promotions
- Product variations (size, color, etc.) with individual pricing and inventory

**Customer Authentication**
- Unified authentication via phone number and OTP
- Route existing users to home screen; new users to account setup
- Session management

**Shopping Cart and Order Management**
- Add products to cart, modify quantities, and remove items
- Place orders with OTP verification, delivery address selection, and province-based fee calculation
- View order history, track order status in real-time, and reorder previous orders
- Automatic province detection for delivery fee calculation

#### 2.2.2 Admin Panel Functions

**Content Management**
- Manage categories, brands, and products with hierarchical organization
- Customize homepage content and schedule promotions

**Customer and Order Management**
- Create and manage customer accounts with automatic password generation
- View, update, and search orders through defined workflow stages
- Automatic order completion upon payment registration

**Inventory Management**
- Real-time inventory tracking with automatic updates on order completion
- Low stock alerts and manual inventory adjustments
- Prevent overselling through availability checks

**Delivery and Reporting**
- Manage delivery provinces and configure fees per province
- Generate sales and operational reports with export capabilities (PDF, Excel/CSV)
- Role-based access control (RBAC) with custom roles and granular permissions

#### 2.2.3 Functional Relationships

The major functional groups are interrelated: Product Discovery feeds into Shopping Cart Management and Order Processing. Customer Authentication is required for cart and order operations. Order Processing triggers Inventory Management updates. Content Management affects Product Discovery. Reporting aggregates data from Order, Inventory, and Customer Management. RBAC controls access to all admin functions.

A top-level class diagram would illustrate these relationships, showing data flow from customer actions to admin processing and real-time updates back to customers.

### 2.3 System Architecture

#### 2.3.1 Architecture Overview
The system follows a three-tier architecture:
- **Presentation Layer**: Customer Application and Admin Panel
- **Business Logic Layer**: Application server with business rules
- **Data Layer**: Database for persistent storage

#### 2.3.2 Technology Stack (Recommended)
- **Frontend**: React/Vue.js or Flutter (for mobile)
- **Backend**: Node.js/Laravel
- **Database**: PostgreSQL/MySQL
- **Caching**: Redis
- **File Storage**: AWS S3 or local storage
- **SMS Gateway**: Integration with Syrian telecom providers (Syriatel, MTN)

#### 2.3.3 Integration Points
- SMS Gateway for OTP and notifications
- Payment Gateway (if applicable) like Syriatel-Cach, Sham-Cash, etc.. 
- GPS/Geolocation services
- Email service (for notifications)

### 2.4 Assumptions and Constraints

#### 2.4.1 Assumptions
- Customers have access to smartphones or computers
- Internet connectivity is available
- SMS services are reliable and available
- GPS/geolocation services are available
- Payment processing will be handled (Physical Payment/ Sham-Cash/ Syriatel-Cash)

#### 2.4.2 Constraints
- Must support Syrian provinces for delivery
- Must integrate with Syrian telecom providers (Syriatel, MTN)
- Must comply with local regulations
- Limited to available technology stack

---

## 3. Functional Requirements

### 3.1 Customer Application Requirements

#### 3.1.1 Product Management

**FR-CA-001: Product Display**
- **Description**: The system shall display products organized by categories and brands
- **Priority**: High
- **Details**:
  - Products must be organized in clear, hierarchical categories
  - Products must be associated with brands
  - Product listings must include: name, image, price, availability status, rating
  - Products must support multiple images per item
  - Stock quantity (available quantity) must be displayed in real-time and updated automatically as inventory changes

**FR-CA-002: Dynamic Homepage**
- **Description**: The system shall provide a customizable homepage managed from the admin panel
- **Priority**: High
- **Details**:
  - Homepage must display featured products
  - Homepage must display new arrivals
  - Homepage must display promotional offers
  - Homepage must display special/featured products
  - Content must be dynamically configurable by administrators

**FR-CA-003: Advanced Product Filtering**
- **Description**: The system shall provide advanced filtering capabilities for product search
- **Priority**: High
- **Details**:
  - Filter by price range (minimum and maximum)
  - Filter by category
  - Filter by brand
  - Filter by customer rating
  - Support multiple simultaneous filters
  - Provide sorting options (price, rating, date added, popularity)

**FR-CA-004: Product Variations**
- **Description**: The system shall support products with multiple variations (e.g., size, color)
- **Priority**: High
- **Details**:
  - Products may have multiple attributes (size, color, material, etc.)
  - Each variation must have its own SKU, price, and inventory
  - Variations must be selectable on product detail pages
  - Inventory must be tracked per variation

**FR-CA-005: Product Search**
- **Priority**: High
- **Description**: The system shall provide search functionality with autocomplete and suggestions

#### 3.1.2 Customer Authentication and Authorization

**FR-CA-005: User Authentication**
- **Priority**: Critical
- **Description**: All customers must be authenticated before using the application
- **Requirements**:
  - Secure login mechanism
  - Password encryption
  - Session management

**FR-CA-006: First-Time Password Activation**
- **Description**: Customers added by admin must activate their password on first login
- **Priority**: High
- **Details**:
  - If account created by admin, password sent via SMS
  - First login requires password change
  - Password change enforced before accessing other features
  - Password meets security requirements (minimum 8 characters, mix of letters and numbers)

**FR-CA-007: Order Verification (OTP)**
- **Description**: Each order must be verified via OTP before processing
- **Priority**: High
- **Details**:
  - OTP sent to registered phone number
  - OTP valid for limited time (e.g., 5 minutes)
  - Order not processed until OTP verified
  - Purpose: Verify phone number is still active and not reassigned by telecom provider

#### 3.1.3 Shopping Cart Management

**FR-CA-008**: Shopping Cart Functionality
  - **Description**: The system shall allow customers to add products to shopping cart with ability to modify quantities or remove items before purchase
  - **Priority**: High
  - **Details**:
    - Add products to cart
    - Update quantities
    - Remove items
    - Save cart for later
    - Cart persists across sessions

**FR-CA-009**: Cart Review Page
  - **Description**: The system shall provide a cart page displaying all added products with quantities, prices, and total sum
  - **Priority**: High
  - **Details**: 
    - Real-time price calculations
    - Clear display of all charges including delivery

#### 3.1.4 Order Management

**FR-CA-010: Order Placement**
- **Description**: Customers shall be able to place orders from shopping cart
- **Priority**: Critical
- **Details**:
  - Review order summary before confirmation
  - Confirm delivery address
  - Select delivery province (auto-detected from location)
  - Apply delivery fees based on province
  - Complete payment information
  - Verify order via OTP
  - Receive order confirmation

**FR-CA-014: Order History**
- **Description**: Customers shall be able to view order history
- **Priority**: High
- **Details**:
  - List all past orders
  - Display order details: products, quantities, prices, dates
  - Display current order status
  - Filter orders by status
  - Search orders by date range or order number

**FR-CA-015: Order Status Tracking**
- **Description**: Customers shall be able to track order status in real-time
- **Priority**: High
- **Details**:
  - Display current order status: Pending, Preparing, Out for Delivery, Delivered, Completed
  - Show status history with timestamps
  - Receive notifications on status changes

**FR-CA-016: Reorder Functionality**
- **Description**: Customers shall be able to reorder previous orders with one click
- **Priority**: Medium
- **Details**:
  - "Reorder" button on past orders
  - Copy all items from previous order to current cart
  - Allow modification before checkout
  - Check current availability before adding to cart

#### 3.1.5 Location and Delivery

**FR-CA-017: Automatic Location Detection**
- **Description**: The system shall automatically detect customer's province
- **Priority**: High
- **Details**:
  - Use device GPS
  - Auto-select province in delivery form
  - Allow manual override if needed
  - Calculate delivery fees based on province

---

### 3.2 Admin Panel Requirements

#### 3.2.1 Content Management

**FR-AD-001: Category Management**
- **Description**: Administrators shall be able to manage product categories
- **Priority**: High
- **Details**:
  - Create, edit, and delete categories
  - Organize categories hierarchically (parent/child)
  - Upload category images
  - Set category display order
  - Enable/disable categories

**FR-AD-002: Brand Management**
- **Description**: Administrators shall be able to manage product brands
- **Priority**: High
- **Details**:
  - Create, edit, and delete brands
  - Upload brand logos
  - Associate brands with categories
  - Set brand display order

**FR-AD-003: Homepage Content Management**
- **Description**: Administrators shall be able to customize homepage content
- **Priority**: High
- **Details**:
  - Select featured products
  - Auto-Select new arrival products
  - Create and manage promotional banners
  - Set display order of homepage sections
  - Schedule promotional content (start/end dates)

**FR-AD-004: Product Management**
- **Description**: Administrators shall be able to manage products
- **Priority**: High
- **Details**:
  - Create, edit, and delete products
  - Upload multiple product images
  - Set product attributes and variations
  - Set pricing (base price, sale price) for the product OR for each variant
  - Assign products to categories and brands
  - Set product availability and auto update it on stock changes
  - Manage product descriptions and specifications

**FR-AD-004A: Bulk Product Import**
- **Description**: Administrators shall be able to import products and variations in bulk from Excel sheet
- **Priority**: Critical
- **Details**:
  - Import products with all details (name, description, category, brand, price, images, etc.) from Excel sheet
  - Import product variations (size, color, material, etc.) with individual SKU, price, and inventory for each variation
  - Support mapping of Excel columns to product fields
  - Validate imported data (required fields, data types, format validation)
  - Handle duplicate products (update existing or skip)
  - Preview imported data before final import
  - Report import errors and success statistics
  - Support rollback of failed imports
  - System validates Excel data format and reports any import errors

#### 3.2.2 Customer Management

**FR-AD-005: Customer Account Creation**
- **Description**: Administrators shall be able to create customer accounts manually or import existing customers in bulk
- **Priority**: Critical
- **Details**:
  - **Manual Creation**:
    - Add customer information: name, phone number, email, address
    - Generate temporary password
    - Send password via SMS to customer
    - Set account status (active/inactive)
    - Add notes about customer
  - **Bulk Import (for existing store customers)**:
    - Import customer details from Excel sheet (name, phone number, email, address)
    - System automatically completes the account creation flow for each imported customer:
      - Adds customer information from Excel data
      - Generates temporary password for each customer
      - Sends password via SMS to each customer's phone number
    - All imported customer accounts are automatically set to **deactivated** status
    - Accounts remain deactivated until customer logs in and changes the temporary password (see FR-CA-006)
    - System validates Excel data format and reports any import errors

**FR-AD-006: Customer Account Management**
- **Description**: Administrators shall be able to manage existing customer accounts
- **Priority**: High
- **Details**:
  - View customer list with search and filters
  - View customer order history
  - Deactivate/reactivate accounts
  - Reset customer passwords

#### 3.2.3 Order Management

**FR-AD-007: Order Status Management**
- **Description**: Administrators shall be able to update order status
- **Priority**: High
- **Details**:
  - View all orders with filters (status, date, customer)
  - Update order status through workflow:
    1. **Pending**: Order received, awaiting processing
    2. **Preparing**: Order being prepared in warehouse
    3. **Out for Delivery**: Order dispatched to delivery
    4. **Delivered**: Order delivered to customer
    5. **Completed**: Order completed (automatic after payment)
  - Cannot change status of completed or cancelled orders

**FR-AD-008: Automatic Order Completion**
- **Description**: Order status shall automatically change to "Completed" after payment registration
- **Priority**: High
- **Details**:
  - When payment recorded with matching order number and amount
  - System automatically updates order status to "Completed"
  - No manual intervention required
  - Payment must match order exactly (amount and order number)

**FR-AD-009: Order Viewing and Search**
- **Description**: Administrators shall be able to view and search orders
- **Priority**: High
- **Details**:
  - View order details: customer, products, quantities, prices, dates
  - Filter by status, date range, customer, province
  - Search by order number
  - Export order data

#### 3.2.4 Inventory Management

**FR-AD-010: Inventory Tracking**
- **Description**: The system shall track inventory levels for all products
- **Priority**: High
- **Details**:
  - Real-time inventory tracking per product and variation
  - Display current stock levels
  - Track inventory movements (in/out)
  - Support multiple warehouses

**FR-AD-011: Automatic Inventory Updates**
- **Description**: Inventory shall automatically update when orders are placed and cancelled
- **Priority**: High
- **Details**:
  - When order is confirmed, system automatically decrements inventory
  - Update inventory for each product variation immediately upon order placement
  - If order is cancelled, system automatically restores inventory (increments stock back)
  - This prevents overselling by reserving stock at order placement
  - Check availability before order confirmation to prevent placing orders for out-of-stock items

**FR-AD-012: Low Stock Alerts**
- **Description**: The system shall alert administrators when inventory falls below threshold
- **Priority**: High
- **Details**:
  - Configurable threshold per product
  - Alert via dashboard notification
  - Alert via email/SMS (configurable)
  - List of low stock items in dashboard
  - Alert when product reaches zero stock

**FR-AD-013: Inventory Management Interface**
- **Description**: Administrators shall be able to manually adjust inventory
- **Priority**: Medium
- **Details**:
  - Manually add/remove stock
  - Record inventory adjustments with reason
  - View inventory history
  - Bulk inventory updates

#### 3.2.5 Reporting and Analytics

**FR-AD-014: Sales Reports**
- **Description**: The system shall generate sales reports when wanted
- **Priority**: High
- **Details**:
  - Daily sales reports
  - Weekly sales reports
  - Monthly sales reports
  - Custom date range reports
  - Reports include: total sales, number of orders, average order value, top products

**FR-AD-016: Report Export**
- **Description**: Reports shall be exportable in multiple formats
- **Priority**: Medium
- **Details**:
  - Export to PDF
  - Export to Excel/CSV
  - Print reports

#### 3.2.6 Delivery and Shipping Management

**FR-AD-017: Province Management**
- **Description**: Administrators shall be able to manage delivery provinces
- **Priority**: High
- **Details**:
  - Add, edit, and delete provinces
  - Set delivery fee per province
  - Enable/disable delivery to specific provinces
  - Set delivery time estimates per province

**FR-AD-018: Delivery Fee Configuration**
- **Description**: Administrators shall be able to configure delivery fees
- **Priority**: High
- **Details**:
  - Set base delivery fee per province
  - Set free delivery threshold (minimum order amount)
  - Set additional fees for remote areas
  - Apply discounts or promotions to delivery fees

#### 3.2.7 Employee and Permission Management (RBAC)

**FR-AD-019: Role Management**
- **Description**: Administrators shall be able to create and manage custom roles
- **Priority**: High
- **Details**:
  - Create custom roles (not fixed roles)
  - Assign descriptive names to roles
  - Enable/disable roles

**FR-AD-020: Permission Management**
- **Description**: Administrators shall be able to assign permissions to roles
- **Priority**: High
- **Details**:
  - System provides list of available permissions
  - Permissions organized by module (Products, Orders, Customers, etc.)
  - Assign multiple permissions to a role
  - Remove permissions from roles
  - View all permissions assigned to a role

**FR-AD-021: Employee Management**
- **Description**: Administrators shall be able to manage employee accounts
- **Priority**: High
- **Details**:
  - Create employee accounts
  - Assign roles to employees
  - Employees inherit permissions from assigned roles
  - Deactivate/reactivate employee accounts
  - View employee activity logs

**FR-AD-022: Permission Granularity**
- **Description**: Permissions shall be granular and specific
- **Priority**: High
- **Details**:
  - Example permissions: "View Products", "Edit Products", "Delete Products", "View Orders", "Update Order Status", "View Reports", etc.
  - Permissions should cover all major operations
  - Support for read-only vs. read-write permissions

---

## 4. Non-Functional Requirements

### 4.1 Performance Requirements

**NFR-001: Response Time**
- Page load time: < 2 seconds
- Search results: < 1 second
- Order processing: < 5 seconds
- Report generation: < 10 seconds for standard reports

**NFR-002: Scalability**
- Support minimum 1,000 daily transactions
- Support concurrent users: 500+ customers, 50+ admin users
- Database should handle 100,0000+ products
- System should scale horizontally

**NFR-003: Availability**
- System uptime: 99.5% (approximately 3.6 hours downtime per month)
- Scheduled maintenance windows

### 4.2 Security Requirements

**NFR-004: Data Security**
- All data transmitted over HTTPS
- Passwords stored using secure hashing 
- Sensitive data encrypted at rest
- SQL injection prevention


**NFR-005: Authentication Security**
- Strong password requirements
- Token-based authentication
- Session timeout after inactivity
- Protection against brute force attacks
- OTP expiration and single-use

**NFR-006: Authorization Security**
- Role-based access control enforced at API level
- Principle of least privilege
- Audit logs for sensitive operations

### 4.3 Usability Requirements

**NFR-007: User Interface**
- Intuitive and user-friendly interface
- Responsive design (mobile, tablet, desktop)
- Support for Arabic and English languages

**NFR-008: User Experience**
- Clear navigation and information architecture
- Helpful error messages
- Loading indicators for long operations
- Consistent design language

### 4.4 Reliability Requirements

**NFR-009: Data Integrity**
- Transaction consistency
- Data validation at all entry points
- Backup and recovery procedures
- Data redundancy

**NFR-010: Error Handling**
- Graceful error handling
- User-friendly error messages
- Error logging and monitoring
- Automatic retry for transient failures

### 4.5 Compatibility Requirements

**NFR-011: Browser Support**
- Modern browsers (Chrome, Firefox, Safari, Edge)
- Mobile browsers (iOS Safari, Chrome Mobile)

**NFR-012: Device Support**
- Desktop computers
- Tablets
- Mobile phones
- Responsive design for all screen sizes

### 4.6 Maintainability Requirements

**NFR-013: Code Quality**
- Well-documented code
- Following coding standards
- Modular architecture
- Unit and integration tests

**NFR-014: Documentation**
- Technical documentation
- User manuals
- API documentation
- Deployment guides

---

## 5. Future Enhancements (Out of Scope)

- Mobile native applications (iOS/Android)
- Customer reviews and ratings system
- Wishlist functionality
- Product recommendations
- Loyalty program
- Multi-language support expansion
- Advanced analytics and AI recommendations
- Integration with social media
- Live chat support

---

## Appendix A: Use Case Diagrams
<we-will-add-use-case-diagram-here>

## Appendix B: Entity Relationship Diagrams
<we-will-replace-this-with-class-diagram>

---
**End of Document**

