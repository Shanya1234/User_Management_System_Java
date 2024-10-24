# **User Management Web Application**

## **Overview**
The **User Management Web Application** is a simple Java-based web app that manages a collection of users with CRUD (Create, Read, Update, Delete) operations. The application also includes key features like login authentication and session management, ensuring that secured pages can only be accessed by authenticated users.

---

## **View** 
Link- https://youtu.be/HS9XGd8I7mI

## **Features**

### **1. User Management:**
- **Create a User**: Add new users to the application.
- **Update a User**: Edit details of existing users.
- **Delete a User**: Remove users from the system.
- **Retrieve a User**: View details of a specific user.
- **List of all Users**: Display a list of all users stored in the system.

### **2. Authentication & Session Management:**
- **Login Authentication**: Users must authenticate via a login page to access the application. The following pages are secured:
  - Login Page
  - List of Users (Home Page)
  - Add New User
  - Edit User
  - Delete User
- **Session Management**: Once a user logs in successfully, a session is created. This session persists until the user logs out or the session expires. All cookies are handled within the session and are cleared upon logout.

---

## **Key Functionalities**

### **1. Login Authentication:**
Before accessing the core functionalities, users must first authenticate themselves. If a non-authenticated user tries to access a secured page, they will be redirected to the login page. Upon successful authentication, users will gain access to the protected pages.

#### **Secured JSP Pages:**
- **Login Page**: Entry point for authentication.
- **Home Page (List of Users)**: Displays a list of all registered users.
- **Add New User Page**: Form to create a new user.
- **Edit User Page**: Form to edit the details of an existing user.

### **2. Session Management:**
- After the user successfully logs in, a session is initiated. This session will remain active until the user logs out or the session times out.
- Cookies store the session information and are automatically cleared once the session is terminated via logout.


## **Database Setup**

This application uses PostgreSQL for data persistence. The required schema is located in the `resources/db.sql` file.

### **Database Schema (PostgreSQL):**

```sql
CREATE TABLE users (
  id SERIAL PRIMARY KEY,
  username TEXT UNIQUE NOT NULL,
  password TEXT NOT NULL,
  role TEXT NOT NULL
);
```

---

## **Servlets Overview**

### **LoginServlet.java**
Handles user login and session creation. Verifies credentials from the `users` table and generates a session upon successful login.

### **Logout.java**
Terminates the user session and clears all associated cookies when the user logs out.

### **UserServlet.java**
Handles CRUD operations (Create, Read, Update, Delete) for user data. All actions are secured, requiring login before access.

---

## **JSP Pages Overview**

### **login_page.jsp**
- Presents a login form to the user.
- Users must provide their username and password to log in.

### **user-lidt.jsp**
- Displays the list of all registered users in the system.
- Available after successful authentication.

### **error.jsp**
- Handles errors if occured.


---

## **How to Run the Application**

### **Prerequisites:**
- Java Development Kit (JDK) 8 or higher.
- Apache Tomcat server (version 9.0 or above).
- PostgreSQL database (or modify the connection to suit your database system).

### **Steps to Run:**
1. Clone or download the project repository.
   
2. Set up the database:
   - Create a new PostgreSQL database.
   - Run the `db.sql` file located in the `resources/` folder to create the necessary `users` table.

3. Open the project in your IDE (IntelliJ IDEA, Eclipse, etc.).

4. Configure the database connection in the `Database.java` file:
   ```java
   private static final String URL = "jdbc:postgresql://localhost:5432/your_database";
   private static final String USERNAME = "your_username";
   private static final String PASSWORD = "your_password";
   ```

5. Package the project using Maven or build it manually in your IDE.

6. Deploy the project to your Apache Tomcat server.

7. Access the application at `http://localhost:8080/your-app-name`.

---

## **Usage**

1. **Login**: 
   - Navigate to the login page and enter your credentials to log in.
   - Default credentials can be inserted directly into the database for testing purposes.
   
2. **List Users**:
   - After successful login, you’ll be redirected to the list of users.

3. **Add User**:
   - Click the "Add User" button to create a new user.

4. **Edit User**:
   - Click the "Edit" button next to an existing user to modify their information.

5. **Delete User**:
   - Click the "Delete" button next to an existing user to remove them from the system.

6. **Logout**:
   - Click the "Logout" button to terminate the session.

---

## **Technologies Used**
- Java (JSP, Servlets)
- PostgreSQL (Database)
- Apache Tomcat (Server)
- HTML, CSS, JavaScript (Frontend)
- Maven (Build Automation)

---
