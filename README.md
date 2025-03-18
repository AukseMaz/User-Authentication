# 🚀 User Authentication API

This project is a simple user authentication system built with Express.js, PostgreSQL, bcryptjs for password hashing, and JWT for authentication.

## ✨ Features
- ✅ User registration with hashed passwords
- ✅ User login with JWT authentication
- ✅ Update user profile (email and title) with authentication
- ✅ Secure API endpoints with JWT-based authentication

## 🛠 Technologies Used
- 🟢 **Node.js** with **Express.js** for server-side logic
- 🟠 **PostgreSQL** as the database
- 🔐 **bcryptjs** for password hashing
- 🔑 **jsonwebtoken (JWT)** for authentication
- 🌍 **dotenv** for managing environment variables
- 📦 **body-parser** for parsing JSON requests

## 📥 Installation

1. Clone the repository:
   ```sh
   git clone https://github.com/your-repo/user-authentication.git
   cd user-authentication
   ```

2. Install dependencies:
   ```sh
   npm install
   ```

3. Set up environment variables:
   Create a `.env` file in the project root with the following content:
   ```env
   PORT=3000
   DB_USER=your_db_user
   DB_HOST=your_db_host
   DB_NAME=your_db_name
   DB_PASSWORD=your_db_password
   DB_PORT=your_db_port
   JWT_SECRET=your_jwt_secret
   ```

4. Start the server:
   ```sh
   node app.js
   ```
   Or start in development mode:
   ```sh
   npm run dev
   ```

## 📡 API Endpoints

### 🔧 Variables Used
- `{{base_url}}` → The base URL of your API (e.g., `http://localhost:3000`)
- `{{token}}` → The JWT token required for authentication
- `{{user_ID}}` → The ID of the registered user, needed for updating user details
- `{{$randomEmail}}`, `{{$randomUserName}}`, `{{$randomPassword}}` → Randomly generated values in Postman for testing

### 📝 Register a User
**Endpoint:** `POST {{base_url}}/register`

**Request Body:**
```json
{
    "username": "{{username_positive}}",
    "email": "{{email_positive}}",
    "title": "Mrs.",
    "password": "{{password_positive}}"
}
```

**Response:**
```json
{
    "message": "User registered successfully",
    "user": {
        "id": 1,
        "username": "{{username_positive}}",
        "email": "{{email_positive}}",
        "title": "Mrs.",
        "created_at": "2024-03-18T12:00:00.000Z"
    }
}
```

### 🔑 Login a User
**Endpoint:** `POST {{base_url}}/login`

**Request Body:**
```json
{
    "username": "{{username_positive}}",
    "password": "{{password_positive}}"
}
```

**Response:**
```json
{
    "message": "Login successful",
    "token": "your_jwt_token"
}
```

### ✏️ Update User Profile
**Endpoint:** `PUT {{base_url}}/user/{{user_ID}}`

**Headers:**
```
Authorization: Bearer {{token}}
```

**Request Body:**
```json
{
    "email": "{{$randomEmail}}",
    "title": "Mrs."
}
```

**Response:**
```json
{
    "message": "User updated successfully",
    "user": {
        "id": 1,
        "username": "{{username_positive}}",
        "email": "{{$randomEmail}}",
        "title": "Mrs.",
        "updated_at": "2024-03-18T12:30:00.000Z"
    }
}
```

## 🧪 Test Cases

### ✅ Registration Test Cases
- Register a new user with all parameters
- Register a new user with only mandatory parameters
- Attempt to register without a username
- Attempt to register with an empty username
- Attempt to register with a duplicate username
- Attempt to register with a username exceeding 50 characters
- Attempt to register without an email
- Attempt to register with an empty email
- Attempt to register with a duplicate email
- Attempt to register without a password
- Attempt to register with empty data

### ✅ Login Test Cases
- Login with valid credentials
- Attempt to login without providing a username
- Attempt to login with an empty username
- Attempt to login with an invalid username
- Attempt to login without providing a password
- Attempt to login with an empty password
- Attempt to login with an incorrect password

### ✅ Update User Test Cases
- Update user profile with a valid ID and details
- Attempt to update with a non-existing user ID
- Attempt to update without providing a user ID
- Attempt to update with an empty title
- Attempt to update with an empty email
- Attempt to update without mandatory parameters

## 📜 License
This project is licensed under the ISC License.



