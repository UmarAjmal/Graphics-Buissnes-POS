# 🖨️ Graphics & Panaflex Business POS ERP System

[![Laravel](https://img.shields.io/badge/Laravel-11.x-FF2D20?style=for-the-badge&logo=laravel&logoColor=white)](https://laravel.com)
[![Vue.js](https://img.shields.io/badge/Vue.js-3.x-4FC08D?style=for-the-badge&logo=vuedotjs&logoColor=white)](https://vuejs.org/)
[![Inertia.js](https://img.shields.io/badge/Inertia.js-2.x-9553E9?style=for-the-badge&logo=inertia&logoColor=white)](https://inertiajs.com/)
[![Tailwind CSS](https://img.shields.io/badge/Tailwind_CSS-3.x-38B2AC?style=for-the-badge&logo=tailwind-css&logoColor=white)](https://tailwindcss.com/)
[![PHP](https://img.shields.io/badge/PHP-8.2+-777BB4?style=for-the-badge&logo=php&logoColor=white)](https://php.net)
[![License](https://img.shields.io/badge/License-MIT-green.svg?style=for-the-badge)](LICENSE)

An enterprise-grade **Point of Sale (POS) and Enterprise Resource Planning (ERP)** software suite engineered specifically for **Graphics Design Houses, Panaflex & Flex Printing, Vinyl & Banner Production, Signage Manufacturers**, as well as general retail POS businesses.

The application features **dynamic area-based pricing engine** ($Length \times Width \times Quantity = Total Sq. Ft.$) supporting real-time unit conversions (feet, inches, millimeters, centimeters, meters), coupled with inventory batch tracking, customer credit ledgers, cash register sessions, automated financial analytics, and granular role-based permissions.

---

## 📋 Table of Contents

- [🌟 Key Highlights](#-key-highlights)
- [🧩 Core Modules & Detailed Features](#-core-modules--detailed-features)
  - [1. Point of Sale (POS) Terminal](#1-point-of-sale-pos-terminal)
  - [2. Products & Inventory Management](#2-products--inventory-management)
  - [3. Customer Ledger & Credit Control](#3-customer-ledger--credit-control)
  - [4. Purchases & Supplier Management](#4-purchases--supplier-management)
  - [5. Expense Management & Overhead Tracking](#5-expense-management--overhead-tracking)
  - [6. Cash Register & Session Control](#6-cash-register--session-control)
  - [7. Financial Reports & Business Intelligence](#7-financial-reports--business-intelligence)
  - [8. User Management & Role-Based Access Control (RBAC)](#8-user-management--role-based-access-control-rbac)
  - [9. System Administration & Backup Tools](#9-system-administration--backup-tools)
- [🛠️ Technology Stack](#️-technology-stack)
- [🚀 Quick Start & Installation Guide](#-quick-start--installation-guide)
- [🔑 Default User Accounts](#-default-user-accounts)
- [📁 Project Directory Architecture](#-project-directory-architecture)
- [🛡️ Production Deployment & Hosting](#️-production-deployment--hosting)
- [📄 License & Credits](#-license--credits)

---

## 🌟 Key Highlights

- **📐 Dynamic Area & Custom Size Calculation**: Automatic calculation of total square footage based on length and width inputs in any unit (`ft`, `in`, `mm`, `cm`, `m`).
- **📦 Dual Product Architecture**: Full support for both square-foot-based media rolls (`panaflex_roll`) and standard count-based inventory items (`simple`).
- **📊 Real-time Financial Ledger**: Integrated customer receivables, supplier payables, advance deposits, and credit accounts.
- **🏷️ Multi-Format Thermal & Standard Printing**: Instant generation and printing of 80mm thermal receipts and A4 detailed invoices.
- **💼 Cash Register Session Management**: Register opening drawer balances, mid-shift cash operations, and shift-end reconciliation.
- **📈 Advanced Export & Analytics**: Instant export of reports to PDF, Excel, and CSV formats.
- **🔒 Granular RBAC Security**: Strict permission control tailored for Administrators, Sales Staff, and Accountants.
- **⚡ Single-Port Production Ready**: Built for easy zero-config deployment on local XAMPP Apache servers or cloud hosts.

---

## 🧩 Core Modules & Detailed Features

### 1. Point of Sale (POS) Terminal
- **Dynamic Panaflex Calculator**: Enter Length and Width with real-time conversion between units (`ft`, `in`, `mm`, `cm`, `m`). Automatically calculates total square feet ($Sq. Ft. = \frac{Length}{Unit} \times \frac{Width}{Unit} \times Quantity$).
- **Dual Product Processing**: Seamlessly mix Panaflex roll media sales and fixed-unit items (e.g. eyelets, display stands, ink cartridges) within a single invoice.
- **Live Cart Operations**: Instant unit rate application, item-level discounts, line tax calculations, and dynamic bill totals.
- **Flexible Customer Billing**: Support for Walk-in Customers and registered Account Customers with real-time credit limit alerts.
- **Multi-Payment Gateways**: Accept Cash, Bank Transfers, Credit Cards, Customer Account Ledger / Credit, or Split Payments across methods.
- **Invoice Printing**: Instant 80mm POS Thermal Receipt and A4 PDF Invoice preview and print functionality.

### 2. Products & Inventory Management
- **Product Classification**:
  - `Panaflex Roll`: Roll width (inches), roll length (meters), total roll area, sq.ft rate, and roll valuation calculations.
  - `Simple Item`: Fixed-unit inventory items with cost price, retail price, stock alerts, and barcode support.
- **Categories & Units**: Full CRUD control over product categories and custom units of measurement (`pcs`, `sqft`, `roll`, `meter`, `kg`, `box`).
- **Batch Stock Tracking (`StockBatch`, `StockMove`)**: FIFO/LIFO tracking of incoming stock batches with cost rate tracing.
- **Stock Adjustments**: Log inventory adjustments due to printing wastage, damaged materials, expired goods, or manual stock corrections.
- **Low Stock Alerts**: Automated reorder point indicators for raw materials and supplies.
- **Barcode Generator**: Built-in barcode generation for quick item lookup (`picqer/php-barcode-generator`).

### 3. Customer Ledger & Credit Control
- **Customer Profiles**: Store complete contact records, business details, tax numbers, and credit limits.
- **Account Ledger**: Complete transaction ledger tracking past sales, payments, pending balances, and total receivables.
- **Customer Advance Deposits (`CustomerAdvance`)**: Record advance payments from clients before project execution.
- **Credit Collection (`CustomerCreditPayment`)**: Collect pending dues against specific invoices or customer credit balances.
- **Import / Export**: Import customer lists from CSV/Excel and export formatted customer reports.

### 4. Purchases & Supplier Management
- **Supplier Directory**: Manage vendor details, company names, contact numbers, and opening balances.
- **Purchase Orders & Goods Receiving**: Create purchase orders for raw materials (media rolls, flex, solvent ink, display stands). Receiving stock automatically creates new stock batches (`StockBatch`).
- **Supplier Payables**: Track unpaid purchases, record vendor prepayments, and manage supplier account ledgers.
- **Status Workflows**: Track status transitions (`Pending`, `Received`, `Cancelled`).

### 5. Expense Management & Overhead Tracking
- **Expense Categorization**: Define custom expense categories (e.g., Electricity, Premises Rent, Machine Maintenance, Staff Wages, Office Supplies).
- **Expense Logging**: Log operational expenses with date, amount, category, payment method, and note/receipt attachments.
- **Impact on P&L**: Automatically factors daily operational expenses into real-time net profit calculations.

### 6. Cash Register & Session Control
- **Register Opening**: Start shift by specifying initial drawer cash balance.
- **Mid-Shift Drawer Operations**: Record Cash In (additional cash float) and Cash Out (petty cash expenses paid directly from drawer).
- **Register Closure & Reconciliation**: Enter physical cash count at shift end. The system calculates expected drawer balance vs actual count and highlights cash overage/shortage.
- **Register Audit Reports**: View historical register session summaries per user.

### 7. Financial Reports & Business Intelligence
- **Sales Analytics**: View daily, weekly, monthly, or custom date-range sales with product and customer breakdowns.
- **Profit & Loss Statement**: Gross profit calculation ($Sales - Stock Cost$) and Net Profit calculation ($Gross Profit - Operational Expenses$).
- **Purchase & Inventory Valuation Reports**: Analyze total stock value, cost of goods purchased, and supplier commitments.
- **Expense Breakdown**: Visual charts and tables mapping spending across expense categories (`Chart.js`).
- **Receivables & Dues Report**: Detailed list of outstanding customer balances for active credit control.
- **All-Parties Ledger**: Combined financial ledger audit for customers and suppliers.
- **Multi-Format Exporting**: Export any analytical report to PDF (`dompdf`), Excel (`maatwebsite/excel`), or CSV.

### 8. User Management & Role-Based Access Control (RBAC)
- **Role Management**: Create custom roles with tailored permission sets.
- **Pre-Configured System Roles**:
  - 👑 **Administrator**: Unrestricted administrative access across all modules, company settings, database management, and user roles.
  - 💼 **Sales Staff**: Access restricted to POS terminal, customer management, and their own sales history.
  - 📊 **Accountant**: Access focused on financial reports, customer/supplier ledgers, payment approvals, and expense records.
- **User Account Management**: Create user accounts, assign roles, toggle active status, and reset security credentials.

### 9. System Administration & Backup Tools
- **Company Configuration**: Set shop name, logo, address, NTN number, phone contact, and custom terms on printed invoices.
- **Tax Settings**: Define default sales tax rates and tax inclusion options.
- **Database Backup & Restore (`BackupController`)**: One-click database backup generation, backup downloads, and system restoration.
- **Database Sanitation (`DatabaseCleanupController`)**: Selective data clearing tools for resetting sales, customers, suppliers, or products during deployment.
- **System Information Dashboard**: Monitor PHP environment, database engine stats, memory allocation, and system uptime.

---

## 🛠️ Technology Stack

| Layer | Technology / Package | Description |
| :--- | :--- | :--- |
| **Backend Framework** | [Laravel 11.x](https://laravel.com) | PHP Web Application Framework |
| **Runtime Language** | PHP 8.2+ | Server-side execution engine |
| **Frontend Architecture** | [Vue.js 3.x](https://vuejs.org/) + [Inertia.js 2.x](https://inertiajs.com/) | Reactive Single Page Application framework |
| **Styling & UI** | [Tailwind CSS 3.x](https://tailwindcss.com/) | Modern utility-first CSS framework |
| **Icon System** | [Lucide Vue Next](https://lucide.dev/) + Heroicons | Clean modern UI icon library |
| **Database Engine** | SQLite / MySQL 8.0+ | Relational data persistence with Eloquent ORM |
| **Document Generation** | [DomPDF 3.x](https://github.com/dompdf/dompdf) | Server-side PDF invoice and report rendering |
| **Spreadsheet Handling** | [Maatwebsite Excel 3.1](https://laravel-excel.com/) | Excel / CSV data export and import engine |
| **Barcode Processing** | [Picqer Barcode Generator](https://github.com/picqer/php-barcode-generator) | 1D barcode generation engine |
| **Charting & Visuals** | [Chart.js 4.x](https://www.chartjs.org/) | Interactive data charts and financial analytics |

---

## 🚀 Quick Start & Installation Guide

### Prerequisites
- **PHP**: `^8.2` or higher (with `pdo`, `sqlite`, `gd`, `mbstring`, `zip` extensions)
- **Composer**: `^2.x`
- **Node.js**: `^18.x` or `^20.x` & `npm`
- **XAMPP / WampServer** (Optional for local Apache hosting)

### 1. Clone the Repository
```bash
git clone https://github.com/UmarAjmal/Graphics-Buissnes-POS.git
cd Graphics-Buissnes-POS
```

### 2. Install PHP & Node Dependencies
```bash
composer install
npm install
```

### 3. Environment Configuration
Copy the environment file template:
```bash
cp .env.example .env
```
Ensure the database settings in `.env` match your environment (SQLite by default):
```ini
DB_CONNECTION=sqlite
# Or for MySQL:
# DB_CONNECTION=mysql
# DB_HOST=127.0.0.1
# DB_PORT=3306
# DB_DATABASE=graphics_pos
# DB_USERNAME=root
# DB_PASSWORD=
```

### 4. Generate Application Key & Database Setup
```bash
php artisan key:generate
php artisan migrate --seed
```

### 5. Compile Frontend Assets & Start Server

**For Local Development:**
```bash
# Option A: Run Artisan Server
php artisan serve --host=0.0.0.0 --port=8000

# Option B: Run Vite Dev Server (In separate terminal)
npm run dev
```
Visit **http://localhost:8000** in your browser.

**For Production Build:**
```bash
npm run build
php artisan config:cache
php artisan route:cache
php artisan view:cache
```

---

## 🔑 Default User Accounts

When the system is seeded (`php artisan db:seed`), the following pre-configured user accounts are generated:

| Role | Email | Password | Access Scope |
| :--- | :--- | :--- | :--- |
| 👑 **Administrator** | `admin@pos.com` | `admin123` | Full unrestricted access to all modules, settings & DB tools |
| 💼 **Sales Staff** | `sales@pos.com` | `sales123` | POS Terminal, Customer Management & personal sales history |
| 📊 **Accountant** | `accountant@pos.com` | `account123` | Financial Analytics, Reports, Dues, Ledgers & Expenses |

> ⚠️ **Security Notice**: Please change default passwords immediately after initial server installation!

---

## 📁 Project Directory Architecture

```
AL-Raza_Graphcs_panaflex_pos_web/
├── app/
│   ├── Http/Controllers/     # RESTful Controllers (POS, Sales, Products, Reports, etc.)
│   ├── Models/               # Eloquent Data Models (PanaflexSpec, Product, Sale, Customer, etc.)
│   ├── Services/             # Area calculation & business logic services
│   └── Providers/            # Application service providers
├── config/                   # Laravel configuration files
├── database/
│   ├── migrations/           # Database schema migrations
│   └── seeders/              # Initial database seed data & roles
├── resources/
│   ├── js/
│   │   ├── Components/       # Reusable Vue components (UI elements, modals, tables)
│   │   ├── Layouts/          # Authenticated App Layout & Navigation Sidebar
│   │   └── Pages/            # Inertia Vue pages (Pos, Sales, Products, Reports, etc.)
│   └── views/                # Blade views & print layout templates (A4 / 80mm thermal)
├── routes/
│   ├── web.php               # Main web application route declarations
│   └── auth.php              # Authentication route mappings
├── public/                   # Web root containing compiled assets
├── storage/                  # Application logs, backups, and media uploads
├── composer.json             # PHP dependencies
├── package.json              # JavaScript dependencies & scripts
├── START_HERE.md             # Quick start operational guide
└── README.md                 # System documentation
```

---

## 🛡️ Production Deployment & Hosting

### Single-Port Operation
The application is configured to run on a single port without requiring a separate Vite server in production. 
1. Build frontend assets: `npm run build`.
2. Point your web server (Nginx / Apache / XAMPP) document root to the `public/` directory.
3. Ensure directory permissions:
   ```bash
   chmod -R 755 storage bootstrap/cache
   chmod -R 777 storage/logs storage/framework/views
   ```

---

## 📄 License & Credits

Developed for **Graphics & Panaflex POS ERP Solutions**.

Maintained by **[Muhammad Umar Ajmal](https://github.com/UmarAjmal)**.  
Repository: [https://github.com/UmarAjmal/Graphics-Buissnes-POS.git](https://github.com/UmarAjmal/Graphics-Buissnes-POS.git)

Distributed under the **MIT License**.
