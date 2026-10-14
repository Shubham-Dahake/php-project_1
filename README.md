# Signup Form Website through MariaDB on AWS

## 💡 Introduction

The **Signup Form Website** is a simple web application developed using HTML and PHP, with MariaDB as the database. It allows users to submit their personal information through a signup form.

The form collects the user's name, email address, website URL, comment, and gender in the `users` table. When the user clicks the Submit button, the information is sent to the PHP backend and stored in the MariaDB database.

### Objectives
- Create a user-friendly signup form.
- Collect user information through HTML input fields.
- Process form data using PHP.
- Store submitted information in a MariaDB database.
- Display a submission success or error message.

## 🏗️ Architectural Diagram

The following diagram illustrates how the website works:

<img width="1672" height="941" alt="PHP Signup Form AWS Architecture Diagram" src="https://github.com/user-attachments/assets/65ccdb92-6219-4fde-9523-d9390c53b92b" />

User/Browser → Nginx Web Server → PHP-FPM (`submit.php`) → MariaDB (`FCT` database, `users` table) → Success Page

### Architecture Components

- **Frontend – HTML:** Displays the signup form and collects user information.
- **Backend – PHP:** Receives the submitted data, connects to MariaDB, and executes the database query.
- **Database – MariaDB:** Stores the submitted information in the `users` table.
- **Communication – HTTP POST:** Transfers the form data from the browser to the PHP backend.

## 📥 Input

The user's data is stored in the `FCT` database in the `users` table:

<img width="600" height="227" alt="Screenshot 2026-10-13 100513" src="https://github.com/user-attachments/assets/41fb7045-014f-4867-9ba5-57a576452b0b" />

The signup form collects the following information from the user.

| Field | Description | Input Type |
|---|---|---|
| Name | User's full name | Text |
| Email | User's email address | Email |
| Website | User's website URL | URL |
| Comment | Additional information | Textarea |
| Gender | User's selected gender | Radio Button |

### Input Process

1. The user opens `signup.html` in a web browser.
2. The user enters their name and email address.
3. The user optionally enters a website URL and comment.
4. The user selects their gender.
5. The user clicks the **Submit** button.
6. The form sends the information to `submit.php` using the HTTP POST method.

### Input Validation

- Name and email are required fields.
- Gender selection is required.
- The email field checks for a valid email format in the browser.
- The website field checks for a valid URL format when a value is entered.

<img width="1917" height="1078" alt="Screenshot 2026-10-13 094339" src="https://github.com/user-attachments/assets/4a9f9aae-e1b2-4b10-a221-cff90ecc2384" />

**Note:** These validations are performed by the browser. Server-side validation should also be implemented in PHP for better security.

## 📤 Output

After the user submits the form, the PHP script processes the information and attempts to store it in the MariaDB database.

### Successful Output

If the database query succeeds, the website displays:

- A success message: **New record created successfully!**
- The submitted name.
- The submitted email address.
- The submitted website URL.
- The submitted comment.
- The selected gender.

<img width="1917" height="1078" alt="Screenshot 2026-10-13 094325" src="https://github.com/user-attachments/assets/63612664-e63f-43cf-abfe-d5624671dfc8" />

The same record is stored in the MariaDB `users` table.

### Error Output

If the database connection or insertion fails, the application displays an error message.

The submitted information is displayed on the result page using PHP's `htmlspecialchars()` function to help prevent HTML injection when rendering these values.

### Data Storage Verification

Verify that the submitted data has been successfully stored in the MariaDB `users` table.

<img width="1917" height="530" alt="Screenshot 2026-10-13 094502" src="https://github.com/user-attachments/assets/aeeaa7c7-302a-4945-aa18-e7c5fb6d6593" />

## Path to Verification

1. Open MariaDB.
2. Run `USE FCT;`.
3. Run `SELECT * FROM users;`.

## 🚀 Deployment Guide

### 1. Launch an EC2 instance on AWS

### 2. Push the code to GitHub

### 3. Install the required packages

```bash
sudo yum install nginx mariadb105-server php git -y
```

### 4. Start and enable the services

```bash
sudo systemctl start nginx mariadb
sudo systemctl enable nginx mariadb
```

### 5. Clone the repository from GitHub

```bash
sudo git clone <url>
```

### 6. Create the database and table

Log in to MariaDB:

```bash
sudo mariadb
```

Run the following SQL commands:

```sql
CREATE DATABASE FCT;
USE FCT;

CREATE TABLE users (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(50),
    email VARCHAR(100),
    website VARCHAR(200),
    comment VARCHAR(500),
    gender VARCHAR(50)
);
```

Then open `http://<EC2-PUBLIC-IP>/<repository-folder>/signup.html` in your browser.

## 🏁 Conclusion

The Signup Form Website demonstrates the basic working of a web application using HTML, PHP, and MariaDB. It shows how users can enter information through a frontend form, send the data to a backend script, save it in a database, and receive a result message.

This project provides practical experience with HTML forms, HTTP POST requests, PHP scripting, MariaDB database connectivity, and basic web application architecture.

### Technologies Used

- **Frontend:** HTML
- **Backend:** PHP
- **Database:** MariaDB
- **Communication:** HTTP POST
- **Web Server:** Nginx

## 👤 Author

Shubham Dahake
