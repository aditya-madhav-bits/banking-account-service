# Account Service  

![Build](https://img.shields.io/badge/Build-Passing-brightgreen.svg) ![License](https://img.shields.io/github/license/aditya-madhav-bits/account-service)

The **Account Service** handles account-related operations such as creating, updating, retrieving, and closing accounts. It also provides endpoints for querying account balances and associated transactions.  

## Features ✨
- **Account Management**: Create, update, close, and retrieve account details.  
- **Transaction Integration**: Retrieve transactions linked to an account.  
- **Balance Inquiry**: Get the current balance of an account.  
- **User Account Query**: Fetch account details by user ID.  

## API Endpoints 📡

### Base URL: `/accounts`  

---

### 1. Create Account  
- **Endpoint**: `POST /accounts`  
- **Request Body**:  
  ```json
  {
    "accountHolderName": "John Doe",
    "accountType": "SAVINGS",
    "balance": 1000.0,
    "currency": "USD"
  }
  ```  
- **Response**:  
  ```json
  {
    "status": "SUCCESS",
    "message": "Account created successfully.",
    "data": {
      "accountNumber": "123456789",
      "accountHolderName": "John Doe",
      "balance": 1000.0
    }
  }
  ```  

---

### 2. Update Account Status  
- **Endpoint**: `PATCH /accounts`  
- **Request Parameters**:  
  - `accountNumber`: The account number to update.  
- **Request Body**:  
  ```json
  {
    "status": "INACTIVE"
  }
  ```  
- **Response**:  
  ```json
  {
    "status": "SUCCESS",
    "message": "Account status updated."
  }
  ```  

---

### 3. Retrieve Account by Account Number  
- **Endpoint**: `GET /accounts`  
- **Request Parameters**:  
  - `accountNumber`: The account number to fetch.  
- **Response**:  
  ```json
  {
    "accountNumber": "123456789",
    "accountHolderName": "John Doe",
    "balance": 1000.0,
    "accountType": "SAVINGS"
  }
  ```  

---

### 4. Update Account Details  
- **Endpoint**: `PUT /accounts`  
- **Request Parameters**:  
  - `accountNumber`: The account number to update.  
- **Request Body**:  
  ```json
  {
    "accountHolderName": "John Doe",
    "balance": 1200.0
  }
  ```  
- **Response**:  
  ```json
  {
    "status": "SUCCESS",
    "message": "Account updated successfully."
  }
  ```  

---

### 5. Retrieve Account Balance  
- **Endpoint**: `GET /accounts/balance`  
- **Request Parameters**:  
  - `accountNumber`: The account number to query.  
- **Response**:  
  ```json
  "1200.0"
  ```  

---

### 6. Fetch Transactions for an Account  
- **Endpoint**: `GET /accounts/{accountId}/transactions`  
- **Path Variable**:  
  - `{accountId}`: The account ID to fetch transactions for.  
- **Response**:  
  ```json
  [
    {
      "transactionId": "txn_001",
      "type": "DEBIT",
      "amount": 100.0,
      "timestamp": "2024-11-19T10:00:00Z"
    },
    {
      "transactionId": "txn_002",
      "type": "CREDIT",
      "amount": 200.0,
      "timestamp": "2024-11-19T15:00:00Z"
    }
  ]
  ```  

---

### 7. Close Account  
- **Endpoint**: `PUT /accounts/closure`  
- **Request Parameters**:  
  - `accountNumber`: The account number to close.  
- **Response**:  
  ```json
  {
    "status": "SUCCESS",
    "message": "Account closed successfully."
  }
  ```  

---

### 8. Retrieve Account by User ID  
- **Endpoint**: `GET /accounts/{userId}`  
- **Path Variable**:  
  - `{userId}`: The user ID to fetch the account for.  
- **Response**:  
  ```json
  {
    "accountNumber": "123456789",
    "accountHolderName": "John Doe",
    "balance": 1000.0,
    "accountType": "SAVINGS"
  }
  ```  

---

## Installation 🚀

1. Clone the repository:  
   ```bash
   git clone https://github.com/aditya-madhav-bits/account-service.git
   cd account-service
   ```  

2. Configure the application:  
   Update the `application.yml` file with necessary details like database credentials and server ports.  

3. Build and run the application:  
   ```bash
   mvn clean install
   mvn spring-boot:run
   ```  

4. Access the service at `http://localhost:8080/accounts`.  

---
