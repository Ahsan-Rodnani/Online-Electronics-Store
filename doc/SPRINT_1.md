# Sprint 1: System Architecture & Scope Definition

## Project Title

Online Electronics Store

## Technology Platform

WordPress + WooCommerce + MySQL

# 1. Target Audience & Market Focus

## 1.1 Primary Persona

The primary users of the Online Electronics Store are retail consumers, university students, professionals, and general customers who want to purchase electronic products conveniently through an online platform.

The platform is designed for customers who want to browse different electronic products, compare prices, check product availability, add products to their shopping cart, and place orders online.

An administrator will also use the platform to manage products, categories, inventory, and customer orders.

### Target Users

University students

IT professionals

General retail consumers

Customers looking for computer accessories

Customers looking for mobile and electronic devices

Store administrators

## 1.2 Core Pain Point

Customers may face difficulties when searching for electronic products, checking their availability, comparing prices, and purchasing products through traditional physical stores.

The proposed Online Electronics Store provides a centralized online platform where customers can browse electronic products, search by category, manage their shopping cart, and place orders conveniently.

The system also helps administrators manage product information and inventory through an online management interface.

## 1.3 Domain Scope

The project focuses on the Consumer Electronics E-Commerce domain.

The store will primarily offer products such as:

Mobile Phones

Laptops

Headphones

Keyboards

Computer Accessories

Mice

Chargers

USB Devices

Speakers

Other Consumer Electronics

The initial project scope will focus on product browsing, product searching, shopping-cart management, checkout/order processing, user accounts, and basic inventory management.

# 2. Minimum Viable Product (MVP) Feature Scope

The Minimum Viable Product will contain the core workflows required for customers and administrators to use the Online Electronics Store.

The scope is intentionally limited to features that are practical to implement within the academic semester.

## 2.1 MVP Feature Scope Matrix

The selected features correspond to the core workflows identified in the Sprint 1 specification, including authentication, catalog/search, cart management, checkout/order processing, and administrative inventory control.

## 2.2 MVP User Workflows

### Workflow 1: User Registration and Login

Customer opens the website.

Customer creates an account.

Customer provides required account information.

WordPress authenticates the user.

Customer logs into the system.

Customer can access shopping and order functionality.

### Workflow 2: Browse and Search Products

Customer opens the product catalog.

Customer selects a product category.

The system displays available products.

Customer searches for a specific product.

Customer opens the product details page.

Customer views product information and price.

### Workflow 3: Shopping Cart Management

Customer selects a product.

Customer adds the product to the shopping cart.

Customer views the cart.

Customer changes product quantity if required.

Customer can remove products.

The cart displays the selected products and total amount.

### Workflow 4: Checkout and Order Processing

Customer proceeds to checkout.

Customer provides required billing/shipping information.

Customer reviews the order.

Customer selects the available payment method.

The order is created.

Customer receives an order confirmation.

### Workflow 5: Product and Inventory Management

Administrator logs into the WordPress administration panel.

Administrator accesses WooCommerce product management.

Administrator adds new products.

Administrator updates product information.

Administrator updates stock quantity.

Administrator can remove products when necessary.

# 3. Tech Stack Selection & Justification

## 3.1 Technology Stack Overview

## 3.2 Frontend

### Selected Technology: WordPress Theme + HTML, CSS and JavaScript

The frontend will use a WordPress theme together with HTML, CSS, and JavaScript to provide the customer-facing interface.

WordPress themes provide reusable layouts and components, while HTML and CSS are used for page structure and styling. JavaScript can be used for interactive functionality.

### Justification

WordPress was selected because it provides a practical content-management environment and reduces the amount of frontend infrastructure that must be developed from scratch. Compared with developing the entire interface from the beginning using a framework such as React or Vue, WordPress allows the team to focus more quickly on the e-commerce workflows required for the semester project.

# 3.3 E-Commerce Platform

### Selected Technology: WooCommerce

WooCommerce will provide the core e-commerce functionality of the Online Electronics Store.

It will be used for:

Product management

Product categories

Shopping cart

Checkout

Orders

Inventory management

Payment integration

### Justification

WooCommerce is selected because it is designed specifically for e-commerce functionality within WordPress. It provides the core shopping and order workflows required by the MVP, reducing unnecessary implementation complexity while allowing the project to remain focused on the required academic scope.

# 3.4 Backend Infrastructure

### Selected Technology: WordPress / PHP

The backend infrastructure will be based on WordPress and PHP, with WooCommerce providing e-commerce functionality.

The backend will manage application operations such as:

User accounts

Product information

Cart operations

Orders

Inventory

Database communication

### Justification

WordPress/PHP is suitable for this project because WordPress provides an established server-side architecture and a large ecosystem of plugins and extensions. Compared with developing a complete backend from scratch using Node.js/Express or another framework, WordPress reduces development overhead and allows the team to concentrate on the defined e-commerce features.

# 3.5 Database Management System

### Selected Technology: MySQL

MySQL will be used as the relational database management system for the project.

The database will store structured information related to:

Users

Products

Categories

Orders

Order items

Shopping carts

Cart items

### Justification

MySQL is suitable because the e-commerce domain contains strongly related data structures. Relationships between users, orders, products, categories, and order items can be represented using primary and foreign keys. A relational database is therefore appropriate for maintaining data integrity and structured relationships.

The Sprint 1 specification specifically requires analysis of data integrity, schema requirements, and relational versus non-relational database choices.

# 3.6 Authentication

### Selected Technology: WordPress Authentication

WordPress’s built-in authentication functionality will be used for customer and administrator accounts.

The system will support:

User registration

User login

User accounts

Administrator accounts

Password protection

User passwords will be handled through WordPress’s built-in password management mechanisms.

# 3.7 Version Control

### Selected Technology: Git + GitHub

Git will be used for version control and GitHub will be used as the central project repository.

The repository will contain project documentation, source/configuration files, and Sprint deliverables.

This also allows team members and instructors to track project changes and review submitted work.

# 4. Entity-Relationship Diagram (ERD)

## 4.1 Database Entities

The proposed relational data model contains the following entities:

Users

Products

Categories

Orders

Order_Items

Cart

Cart_Items

These entities cover the database requirements specified for Sprint 1.

## 4.2 Entity Attributes

### USERS

### CATEGORIES

### PRODUCTS

### ORDERS

### ORDER_ITEMS

### CART

### CART_ITEMS

# 4.3 Relationships and Cardinality

### Users → Orders

One-to-Many (1:N)

One user can place multiple orders, while each order belongs to one user.

USERS 1 ───────── N ORDERS

### Categories → Products

One-to-Many (1:N)

One category can contain multiple products, while each product belongs to a category.

CATEGORIES 1 ───────── N PRODUCTS

### Orders → Order_Items

One-to-Many (1:N)

One order can contain multiple order items.

ORDERS 1 ───────── N ORDER_ITEMS

### Products → Order_Items

One-to-Many (1:N)

One product can appear in multiple order items.

PRODUCTS 1 ───────── N ORDER_ITEMS

### Users → Cart

One-to-One (1:1)

A customer account has one active shopping cart in the proposed MVP model.

USERS 1 ───────── 1 CART

### Cart → Cart_Items

One-to-Many (1:N)

One cart can contain multiple cart items.

CART 1 ───────── N CART_ITEMS

### Products → Cart_Items

One-to-Many (1:N)

A product can appear in multiple users’ cart items.

PRODUCTS 1 ───────── N CART_ITEMS

# 4.4 Mermaid ERD

erDiagram

    USERS ||--o{ ORDERS : places
    USERS ||--|| CART : owns

    CATEGORIES ||--o{ PRODUCTS : contains

    ORDERS ||--|{ ORDER_ITEMS : contains
    PRODUCTS ||--o{ ORDER_ITEMS : included_in

    CART ||--o{ CART_ITEMS : contains
    PRODUCTS ||--o{ CART_ITEMS : added_to

    USERS {
        INTEGER user_id PK
        VARCHAR name
        VARCHAR email
        VARCHAR password_hash
        VARCHAR role
        TIMESTAMP created_at
    }

    CATEGORIES {
        INTEGER category_id PK
        VARCHAR category_name
        VARCHAR description
    }

    PRODUCTS {
        INTEGER product_id PK
        INTEGER category_id FK
        VARCHAR product_name
        VARCHAR description
        DECIMAL price
        INTEGER stock_quantity
        TIMESTAMP created_at
    }

    ORDERS {
        INTEGER order_id PK
        INTEGER user_id FK
        DECIMAL total_amount
        VARCHAR status
        TIMESTAMP order_date
    }

    ORDER_ITEMS {
        INTEGER order_item_id PK
        INTEGER order_id FK
        INTEGER product_id FK
        INTEGER quantity
        DECIMAL unit_price
    }

    CART {
        INTEGER cart_id PK
        INTEGER user_id FK
        TIMESTAMP created_at
    }

    CART_ITEMS {
        INTEGER cart_item_id PK
        INTEGER cart_id FK
        INTEGER product_id FK
        INTEGER quantity
    }

The ERD explicitly identifies primary keys, foreign keys, relationships, cardinality, and SQL-compatible attribute data types as required by the Sprint 1 specification.

# 5. System Architecture Overview

The proposed system will follow a layered e-commerce architecture.

CUSTOMER
                       |
                       v
              +----------------+
              |   WordPress    |
              |   Frontend     |
              +----------------+
                       |
                       v
              +----------------+
              |  WooCommerce   |
              | E-Commerce     |
              | Functionality  |
              +----------------+
                       |
                       v
              +----------------+
              | WordPress/PHP  |
              |    Backend     |
              +----------------+
                       |
                       v
              +----------------+
              |     MySQL      |
              |    Database    |
              +----------------+

The administrator accesses the WordPress administration interface to manage products, inventory, orders, and other system information.

# 6. Scope Boundaries

The MVP will focus on the essential functionality required for an academic e-commerce platform.

## Included in MVP

Customer registration and login

Product browsing

Product searching

Product categories

Product details

Shopping cart

Checkout

Order creation

Basic inventory management

Administrator product management

## Outside Initial MVP Scope

The following features are outside the initial MVP scope:

Artificial intelligence product recommendations

Advanced customer analytics

Multi-vendor marketplace

Real-time delivery tracking

Advanced loyalty/reward system

Complex recommendation algorithms

Mobile application

International multi-currency infrastructure

These features can be considered future enhancements if sufficient development time remains.

# 7. Sprint 1 Conclusion

Sprint 1 establishes the architectural foundation for the Online Electronics Store.

The project will use WordPress and WooCommerce as the primary platform, with PHP/WordPress providing the backend infrastructure and MySQL providing relational data storage.

The MVP is limited to the essential workflows of authentication, product browsing, cart management, checkout/order processing, and administrative inventory management.

The proposed ERD defines the core relationships between users, products, categories, orders, order items, carts, and cart items. This architecture provides a clear foundation for the implementation phase of the e-commerce project.



| Category | Feature Name | Description | Priority |

| --- | --- | --- | --- |

| Authentication | User Registration & Login | Customers can create accounts, log in, and manage their accounts using WordPress authentication. | High (MVP) |

| Catalog | Product List & Search | Customers can browse electronic products and search/filter products by category. | High (MVP) |

| Product | Product Details | Customers can view product name, description, price, image, category, and availability. | High (MVP) |

| Cart | Cart Management | Customers can add products to the cart, modify quantities, and remove products. | High (MVP) |

| Checkout | Order Processing | Customers can provide checkout information and place an order through WooCommerce checkout. | High (MVP) |

| Admin | Inventory & Product Management | Administrators can add, update, delete, and manage product inventory. | Medium (MVP) |



| System Component | Selected Technology |

| --- | --- |

| CMS / Website Platform | WordPress |

| E-Commerce Platform | WooCommerce |

| Frontend | WordPress Theme, HTML, CSS, JavaScript |

| Backend Infrastructure | WordPress / PHP |

| Database Management System | MySQL |

| Authentication | WordPress Authentication |

| Payment Processing | WooCommerce Payment Gateway / Mock Payment |

| Version Control | Git and GitHub |



| Attribute | Data Type | Key |

| --- | --- | --- |

| user_id | INTEGER | PK |

| name | VARCHAR(100) |  |

| email | VARCHAR(150) | UNIQUE |

| password_hash | VARCHAR(255) |  |

| role | VARCHAR(30) |  |

| created_at | TIMESTAMP |  |



| Attribute | Data Type | Key |

| --- | --- | --- |

| category_id | INTEGER | PK |

| category_name | VARCHAR(100) |  |

| description | VARCHAR(255) |  |



| Attribute | Data Type | Key |

| --- | --- | --- |

| product_id | INTEGER | PK |

| category_id | INTEGER | FK |

| product_name | VARCHAR(150) |  |

| description | VARCHAR(500) |  |

| price | DECIMAL(10,2) |  |

| stock_quantity | INTEGER |  |

| created_at | TIMESTAMP |  |



| Attribute | Data Type | Key |

| --- | --- | --- |

| order_id | INTEGER | PK |

| user_id | INTEGER | FK |

| total_amount | DECIMAL(10,2) |  |

| status | VARCHAR(50) |  |

| order_date | TIMESTAMP |  |



| Attribute | Data Type | Key |

| --- | --- | --- |

| order_item_id | INTEGER | PK |

| order_id | INTEGER | FK |

| product_id | INTEGER | FK |

| quantity | INTEGER |  |

| unit_price | DECIMAL(10,2) |  |



| Attribute | Data Type | Key |

| --- | --- | --- |

| cart_id | INTEGER | PK |

| user_id | INTEGER | FK |

| created_at | TIMESTAMP |  |



| Attribute | Data Type | Key |

| --- | --- | --- |

| cart_item_id | INTEGER | PK |

| cart_id | INTEGER | FK |

| product_id | INTEGER | FK |

| quantity | INTEGER |  |
