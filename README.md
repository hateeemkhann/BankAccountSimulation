# Bank Account Simulation System

A comprehensive Java-based Banking Management System built with Swing GUI framework and SQL Server database integration. This project simulates real-world banking operations with features for both administrators and account holders.

## 🌟 Features Overview

### For Account Holders
- **Account Management**
  - Individual and Joint Account Opening
  - Account Type Selection (Savings or Current)
  - Account Balance Tracking and Display
  - Account Details Viewing

- **Financial Transactions**
  - Deposit Money into Account
  - Withdraw Money from Account
  - Transfer Funds to Other Accounts (within bank or external banks)
  - View Complete Transaction History
  - Bill Payment (SUI Gas, K-Electric, Water Bill, WAPDA, Mobile Top-up, etc.)
  - Cheque Book Issuance (with charges)

- **Card Management**
  - Issue Debit Cards
  - Issue Credit Cards
  - View Card Details (Card Number, CVV, Expiry Date)
  - Card Charges Management

- **Loan Management**
  - View Available Loan Packages (Silver, Gold, Platinum)
  - Apply for Loans
  - View Loan Status
  - Track Loan Requests

- **Account Customization**
  - Change Password
  - Add Beneficiaries for Quick Transfers
  - View Beneficiary List
  - Interest Calculation (Savings Accounts)

- **Feedback System**
  - Submit Feedback
  - Submit Queries
  - Submit Suggestions
  - View Response Status

### For Administrators
- **Account Administration**
  - Create Individual Accounts
  - Create Joint Accounts
  - View All Customers
  - View Customer Details and Statements
  - Remove/Delete Account Holders
  - Edit Customer Details
  - Deposit Money into Customer Accounts

- **Request Management**
  - View Account Creation Requests
  - Approve Account Requests
  - Reject Account Requests
  - View Loan Requests
  - Approve Loan Requests
  - Reject Loan Requests
  - View Customer Feedback, Queries, and Suggestions

- **Bank Management**
  - Add Banks
  - Remove Banks
  - View All Banks
  - Manage Bank Database

- **Admin Management**
  - Add New Admins
  - View All Admins (Super Admin Only)
  - Remove Admins
  - Admin Authentication and Access Control

- **Loan Options Management**
  - Configure Loan Packages
  - Set Loan Amounts and Interest Rates
  - Define Loan Duration and Minimum Balance Requirements

- **User Requests Management**
  - Process Account Opening Requests
  - Handle Loan Applications
  - View Customer Feedback and Suggestions

## 🏗️ System Architecture

### Technology Stack
- **Language**: Java 11+
- **GUI Framework**: Swing (JFrame, JPanel, JButton, etc.)
- **Database**: Microsoft SQL Server
- **JDBC Driver**: mssql-jdbc-13.2.1.jre11
- **IDE**: IntelliJ IDEA

### Database Schema
The system uses a relational database with the following main entities:

1. **Admins** - Administrator credentials and information
2. **Accounts** - Account information (Balance, Account Type, Credentials)
3. **Customers** - Customer personal information
4. **CustomerAccounts** - Junction table linking Customers to Accounts
5. **Transactions** - Transaction records with type, amount, date, time
6. **Beneficiaries** - Saved beneficiary accounts for transfers
7. **Cards** - Debit and Credit card information
8. **LoanRequests** - Loan application records
9. **LoanOptions** - Available loan packages (Silver, Gold, Platinum)
10. **AccountRequests** - Pending account creation requests
11. **Feedback** - Customer feedback, queries, and suggestions
12. **Banks** - Bank database for inter-bank transfers
13. **OtherBankAccountHolders** - External bank account records

### Core Classes

#### User Hierarchy
- **User (Abstract)** - Base class for all users with common attributes
  - **Admin** - Administrative user with management capabilities
  - **AccountHolder (Abstract)** - Base for account holders
    - **SavingsAccountHolder** - Savings account with interest calculation
    - **CurrentAccountHolder** - Current account for business

#### Business Logic
- **Transaction** - Handles all transaction operations
- **Requests** - Manages account and loan requests
- **Validations** - Input validation for all user data
- **LoanOptions** - Loan package management
- **Identifiable** - Interface for unique identification

#### Data Access Objects (DAO)
- **AccountHolderDAO** - Account holder operations
- **AdminDAO** - Admin operations
- **TransactionDAO** - Transaction database operations
- **ValidationDAO** - Database validation queries
- **LoanOptionsDAO** - Loan options database operations
- **LoanRequestDAO** - Loan request database operations

#### Database Connection
- **DBConnection** - Azure SQL Server connection management

## 📋 Key Functionalities

### Security Features
- Username and Password Authentication
- Role-based Access Control (Admin vs Account Holder)
- Password Encryption Support
- Unique CNIC Validation
- Email Verification
- Input Validation for All Fields

### Validation Rules
- **Email**: Valid email format with no duplicates
- **Password**: 
  - Admin: 4+ characters with letters, digits, and special characters
  - Customer: 4+ digit numbers only
- **CNIC**: Exactly 13 digits, unique per user
- **Contact**: 11-digit phone numbers
- **Age**: Minimum 18 years
- **Name**: At least 2 words with only letters

### Transaction Types
- Deposit
- Withdrawal
- Transfer (Domestic and International)
- Bill Payment
- Card Issuance
- Cheque Book Charges
- Interest Deposit
- Loan Grants

### Account Types
- **Savings**: Earns 2% annual interest (calculated monthly)
- **Current**: For business transactions

## 🎨 User Interface

The application uses Swing components to provide:
- Clean and Intuitive Dashboard Interfaces
- Form-based Input Screens
- Table Views for Data Display
- Pop-up Confirmations and Alerts
- Login and Authentication Screens
- Full-screen Responsive Design

### Main UI Components
- **LoginForm** - Initial login page with role selection
- **MainDashboard** - Customer dashboard with all operations
- **AdminDashboard** - Admin dashboard with management options
- **Various Operation Dashboards** - Separate screens for each operation

## 🚀 Getting Started & Clone Instructions

### 📥 **CLONE THE PROJECT**

```bash
git clone https://github.com/your-username/BankAccountSimulation.git
cd BankAccountSimulation
```

**Or manually:**
- Download the ZIP file from the repository
- Extract to your desired location
- Open the project in IntelliJ IDEA

---

### ⚙️ Prerequisites
- ✅ Java 11 or higher
- ✅ Microsoft SQL Server (Azure SQL or Local)
- ✅ IntelliJ IDEA or any Java IDE
- ✅ Git (for cloning)

### 📋 Installation Steps

#### **Step 1: Clone/Download the Project**
   ```bash
   git clone https://github.com/your-username/BankAccountSimulation.git
   cd BankAccountSimulation
   ```

#### **Step 2: Database Configuration**
   - Open `DBConnection.java` in the `src/` folder
   - Update with your SQL Server credentials:
     ```java
     private static final String URL = "your-sql-server-url";
     private static final String USER = "your-username";
     private static final String PASSWORD = "your-password";
     ```
   - Execute the `DDL.sql` file to create database schema:
     ```sql
     sqlcmd -S your-server -U your-user -P your-password -i DDL.sql
     ```

#### **Step 3: Add JDBC Driver**
   - The project uses `mssql-jdbc-13.2.1.jre11`
   - In IntelliJ IDEA: `File → Project Structure → Libraries → Add JAR`
   - Select the JDBC driver JAR file

#### **Step 4: Run the Application**
   **Option A: From Terminal**
   ```bash
   javac src/*.java
   java -cp src LoginForm
   ```
   
   **Option B: From IDE**
   - Right-click on `LoginForm.java`
   - Select `Run 'LoginForm.main()'`

### 🔐 Sample Login Credentials

| Role | Username | Password |
|------|----------|----------|
| **Admin** | `hateem123` | `Admin@123` |
| **Customer** | `customer1` | `1234` |

> **Note:** Check `admins.txt` and `Account_Holders.txt` files in the `src/` folder for additional credentials

---

## 💻 **HOW TO USE - QUICK START GUIDE**

### 👥 **FOR CUSTOMERS**

#### **1️⃣ Create a New Account (First Time Users)**
   1. Launch the application → Click **"Request Account"**
   2. Fill in your personal details:
      - Full Name (at least 2 words)
      - Age (18+)
      - Gender
      - CNIC (13 digits)
      - Contact (11 digits)
      - Email
      - Address
      - Account Type (Savings/Current)
   3. Submit your request
   4. Wait for admin approval
   5. Once approved, you'll receive login credentials

#### **2️⃣ Login to Your Account**
   1. Launch application → Enter username and password
   2. Click **"Login as Customer"**
   3. Access your **Main Dashboard**

#### **3️⃣ Deposit Money**
   1. From Main Dashboard → Click **"Deposit Money"**
   2. Enter the amount to deposit
   3. Click **"Confirm"**
   4. Transaction complete! View receipt

#### **4️⃣ Withdraw Money**
   1. From Main Dashboard → Click **"Withdraw Money"**
   2. Enter the withdrawal amount
   3. Confirm the transaction
   4. Money withdrawn from your account

#### **5️⃣ Transfer Money**
   1. From Main Dashboard → Click **"Transfer Money"**
   2. Select transfer type:
      - **Within Bank**: Choose beneficiary or enter account number
      - **Other Banks**: Select bank and account number
   3. Enter transfer amount
   4. Review and confirm
   5. Transaction recorded with transaction ID

#### **6️⃣ Issue a Card**
   1. From Main Dashboard → Click **"Issue Card"**
   2. Select card type:
      - **Debit Card** (charged PKR 2,230)
      - **Credit Card** (charged PKR 2,230)
   3. Confirm issuance
   4. Card generated with:
      - 16-digit card number
      - CVV (3 digits)
      - Expiry date
      - Deducted from your balance

#### **7️⃣ Request Cheque Book**
   1. From Main Dashboard → Click **"Issue Cheque Book"**
   2. Confirm the request
   3. Cheque book charges: PKR 500 (deducted from balance)
   4. Cheque book issued

#### **8️⃣ Pay Bills**
   1. From Main Dashboard → Click **"Bill Payment"**
   2. Select bill type:
      - SUI Gas
      - K-Electric
      - Water Bill
      - WAPDA
      - Mobile Top-up
      - Challan Payment
   3. Enter bill amount
   4. Confirm payment
   5. Balance updated

#### **9️⃣ Apply for Loan**
   1. From Main Dashboard → Click **"View Loan Packages"**
   2. Browse loan options:
      - **Silver**: Entry-level loan
      - **Gold**: Mid-tier loan
      - **Platinum**: Premium loan
   3. Click **"Apply"**
   4. Enter loan amount
   5. Submit application
   6. Admin reviews and approves/rejects
   7. If approved, amount deposited to your account

#### **🔟 View Transaction History**
   1. From Main Dashboard → Click **"View Transactions"**
   2. See all transactions with:
      - Transaction ID
      - Description
      - Amount
      - Date & Time
      - Type

#### **1️⃣1️⃣ Add Beneficiary**
   1. From Main Dashboard → Menu → **"Add Beneficiary"**
   2. Enter beneficiary details:
      - Account number
      - Beneficiary name
      - Bank name
   3. Save beneficiary
   4. Use for quick transfers

#### **1️⃣2️⃣ Change Password**
   1. From Main Dashboard → Menu → **"Change Password"**
   2. Enter old password
   3. Enter new password (4+ digits)
   4. Confirm new password
   5. Password updated

#### **1️⃣3️⃣ Submit Feedback**
   1. From Main Dashboard → Click **"Feedback/Queries"**
   2. Select category:
      - Feedback
      - Query
      - Suggestion
   3. Write your message
   4. Submit
   5. Admin will review

---

### 🛡️ **FOR ADMINISTRATORS**

#### **1️⃣ Login to Admin Panel**
   1. Launch application → Click **"Login as Admin"**
   2. Enter admin credentials
   3. Access **Admin Dashboard**

#### **2️⃣ Create Customer Account**
   1. From Admin Dashboard → Click **"Open Account"**
   2. Select account type:
      - Individual Account
      - Joint Account
   3. Fill customer details
   4. Account created with auto-generated credentials

#### **3️⃣ View All Customers**
   1. From Admin Dashboard → Click **"View Customers"**
   2. See all registered customers
   3. View customer details and statements

#### **4️⃣ Approve Account Requests**
   1. From Admin Dashboard → Click **"Account Requests"**
   2. View pending requests
   3. Review customer information
   4. Click **"Approve"** or **"Reject"**
   5. Approved customers receive login credentials

#### **5️⃣ Approve Loan Requests**
   1. From Admin Dashboard → Click **"View Loan Requests"**
   2. Review pending loan applications
   3. Check:
      - Loan amount requested
      - Customer balance
      - Loan eligibility
   4. Click **"Approve"** (deposits amount) or **"Reject"**

#### **6️⃣ Deposit Money into Customer Account**
   1. From Admin Dashboard → Click **"Deposit into Account"**
   2. Enter customer account number
   3. Enter deposit amount
   4. Confirm deposit
   5. Amount added to customer's account

#### **7️⃣ Remove Customer Account**
   1. From Admin Dashboard → Click **"Remove Account"**
   2. Enter customer account number
   3. Confirm deletion
   4. Account removed from system

#### **8️⃣ Manage Banks**
   1. From Admin Dashboard → Click **"View Banks"**
   2. View all registered banks
   3. Option to **"Add Bank"** or **"Remove Bank"**
   4. Updated for transfer operations

#### **9️⃣ Add New Admin**
   1. From Admin Dashboard → Click **"Add Admin"**
   2. Fill admin details:
      - Name
      - CNIC
      - Contact
      - Age
      - Gender
      - Email
      - Password (must have letters, digits, special chars)
   3. Admin account created

#### **🔟 View Feedback & Queries**
   1. From Admin Dashboard → Click **"View Feedback"**
   2. See customer:
      - Feedback
      - Queries
      - Suggestions
   3. Review and take necessary action

---

## 📁 Project Structure

```
BankAccountSimulation/
├── src/
│   ├── Core Classes/
│   │   ├── Main.java
│   │   ├── LoginForm.java
│   │   ├── User.java
│   │   ├── Transaction.java
│   │   ├── Requests.java
│   │   └── Validations.java
│   ├── DAO Classes/
│   │   ├── AccountHolderDAO.java
│   │   ├── AdminDAO.java
│   │   ├── TransactionDAO.java
│   │   ├── ValidationDAO.java
│   │   ├── LoanOptionsDAO.java
│   │   └── LoanRequestDAO.java
│   ├── Admin Screens/
│   │   ├── AdminDashboard.java
│   │   ├── AddAdminDashboard.java
│   │   ├── RequestsDashboard.java
│   │   ├── ViewCustomers.java
│   │   └── ... (other admin screens)
│   ├── Customer Screens/
│   │   ├── MainDashboard.java
│   │   ├── TransferDashboard.java
│   │   ├── DepositDashboard.java
│   │   ├── WithdrawDashboard.java
│   │   └── ... (other customer screens)
│   ├── Utility Classes/
│   │   ├── DBConnection.java
│   │   ├── Identifiable.java
│   │   └── LoanOptions.java
│   ├── Form Files (.form) - IntelliJ GUI Designer files
│   ├── Data Files/
│   │   ├── Account_Holders.txt
│   │   ├── Transactions.txt
│   │   ├── admins.txt
│   │   ├── Banks.txt
│   │   ├── Beneficiaries.txt
│   │   ├── Cards.txt
│   │   ├── Requests.txt
│   │   └── ... (other data files)
│   └── Images/
│       └── SBL (1).png (Bank Logo)
├── DDL.sql - Database schema creation script
├── BankAccountSimulation.iml - IntelliJ project configuration
└── README.md - This file
```

## 🔒 Security Considerations

- Passwords are stored in encrypted format
- Admin credentials are restricted to super admins
- Each user has role-based access control
- Transaction audit trail maintained
- Input validation prevents SQL injection
- Unique identifiers prevent account duplication

## 🐛 Known Limitations

1. Local file storage used alongside database (mixed approach)
2. No multi-currency support
3. Limited concurrent user handling
4. No mobile application support
5. Interest calculation is simplified
6. No audit logging system

## 🔄 Future Enhancements

- [ ] Mobile Application (Android/iOS)
- [ ] Web-based Portal
- [ ] Advanced Reporting Dashboard
- [ ] Multi-currency Support
- [ ] Real-time Notifications
- [ ] Advanced Analytics
- [ ] Integration with Payment Gateways
- [ ] API Development
- [ ] Comprehensive Audit Logging
- [ ] Machine Learning for Fraud Detection

## 📊 Database Schema Overview

The system uses a normalized relational database design with:
- Parent-child relationships maintained through Foreign Keys
- Composite primary keys for junction tables
- Proper indexing on frequently queried columns
- Cascading relationships for data integrity

### Entity Relationships
```
Admins (Parent)
├── Admin Management

Accounts (Parent)
├── Transactions (Child)
├── Beneficiaries (Child)
├── Cards (Child)
├── LoanRequests (Child)
├── Feedback (Child)
└── CustomerAccounts (Junction)
    └── Customers (Parent)

Banks (Parent)
├── Used for Transfer Operations

LoanOptions (Parent)
├── Independent Configuration

AccountRequests (Parent)
├── Independent Requests
```

## 🤝 Contributing

This is an educational project. Feel free to:
- Fork and modify for learning purposes
- Submit improvements and bug fixes
- Enhance documentation
- Optimize performance

## 📝 License

This project is created for educational purposes. Usage is subject to institutional guidelines.

## 📧 Contact & Support

For issues, questions, or suggestions:
- Document issues clearly with steps to reproduce
- Provide screenshots when applicable
- Include system configuration details
- Reference the relevant code sections

## 🎓 Educational Value

This project demonstrates:
- Object-Oriented Programming Principles (Abstraction, Inheritance, Polymorphism)
- GUI Development with Swing
- Database Design and SQL
- JDBC for Database Connectivity
- Data Validation and Security
- File I/O Operations
- Design Patterns (DAO Pattern, etc.)
- Software Architecture and Organization

## 📚 Additional Resources

- Java Documentation: https://docs.oracle.com/javase/11/docs/
- Swing Tutorial: https://docs.oracle.com/javase/tutorial/uiswing/
- Microsoft SQL Server Documentation: https://learn.microsoft.com/en-us/sql/
- JDBC Guide: https://docs.oracle.com/javase/tutorial/jdbc/

---

**Last Updated**: April 2026  
**Version**: 1.0  
**Status**: Educational/Development



