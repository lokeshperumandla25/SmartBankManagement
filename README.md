# Smart Bank Management System

A web-based banking management system built using **Java, Spring MVC, Spring Data JPA, Hibernate, MySQL, and JSP**. The application provides separate workflows for administrators and customers, including account management, fund transfers, loan processing, OTP-based authentication, and transaction statements.

## Features

### Admin

* Admin login
* Create customer accounts
* Automatic account number generation
* Generate temporary customer passwords
* View and manage customers
* Activate/deactivate customer accounts
* View pending loan applications
* Approve or reject loans
* Credit approved loan amounts

### Customer

* Login using account number and password
* First-login password reset
* Email OTP verification
* View account dashboard
* Transfer funds between accounts
* Balance validation
* Apply for loans
* View loan status
* View transaction statements
* Filter transactions by month and year
* Logout

## Tech Stack

| Technology            | Purpose                   |
| --------------------- | ------------------------- |
| Java                  | Backend development       |
| Spring MVC 6          | Web application framework |
| Spring Data JPA       | Data access               |
| Hibernate 6           | ORM                       |
| MySQL                 | Database                  |
| JSP                   | User interface            |
| JSTL                  | JSP templating            |
| Maven                 | Build management          |
| Jakarta Servlet       | Web layer                 |
| JavaMail / Angus Mail | OTP email delivery        |

## Architecture

The application follows a layered architecture:

```text
Browser
   ↓
JSP Views
   ↓
Spring MVC Controllers
   ↓
Service Layer
   ↓
Spring Data JPA Repositories
   ↓
Hibernate / JPA
   ↓
MySQL
```

### Project Structure

```text
src/main/java/com/bank/
│
├── config/
├── controller/
├── dao/
├── model/
├── service/
├── serviceImpl/
└── util/

src/main/webapp/
└── WEB-INF/
    └── views/
```

## Authentication

Customer authentication includes email OTP verification.

```text
Login
  ↓
Validate Credentials
  ↓
Generate OTP
  ↓
Send OTP via Email
  ↓
Verify OTP
  ↓
Customer Dashboard
```

OTP verification uses a **5-minute expiration period**.

## Fund Transfer

The application supports account-to-account fund transfers with:

* Sender and receiver validation
* Account status validation
* Balance validation
* Sender balance debit
* Receiver balance credit
* Transaction record creation

The transfer operation is handled using a database transaction.

## Loan Management

Customers can apply for loans, while administrators can approve or reject applications.

```text
Customer
   ↓
Apply for Loan
   ↓
Pending
   ↓
Admin Review
   ↓
Approve / Reject
   ↓
Credit Amount if Approved
```

### Loan Interest Rates

| Loan Type      | Interest Rate |
| -------------- | ------------: |
| Home Loan      |          8.5% |
| Education Loan |          6.5% |
| Other Loans    |           12% |

## Database Setup

Create the MySQL database:

```sql
CREATE DATABASE bank;
```

The application uses Hibernate to create/update database tables based on the entity mappings.

Main entities:

* `Customer`
* `Loan`
* `Otp`
* `Transcation`

## Configuration

Database configuration is located in:

```text
src/main/java/com/bank/config/RootConfig.java
```

Email configuration is located in:

```text
src/main/java/com/bank/config/MailConfig.java
```

For a public repository, **do not commit database passwords, email passwords, API keys, or other secrets**. Use environment variables or a secrets manager instead.

## Running the Project

### Prerequisites

* Java 17+
* Maven
* MySQL
* Apache Tomcat 10.1+

### 1. Clone the Repository

```bash
git clone https://github.com/lokeshperumandla25/SmartBankManagement.git
cd SmartBankManagement
```

### 2. Create the Database

```sql
CREATE DATABASE bank;
```

### 3. Configure Database and Email

Update the database and email configuration with your local credentials.

### 4. Build the Project

```bash
mvn clean package
```

The generated WAR file will be available in:

```text
target/
```

### 5. Deploy

Deploy the generated WAR file to **Tomcat 10.1+** and start the server.


## Author

**Lokesh Perumandla**

[GitHub](https://github.com/lokeshperumandla25)

## License

This project is intended for educational and portfolio purposes.
