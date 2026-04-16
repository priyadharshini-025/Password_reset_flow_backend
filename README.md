# 📘 Backend README (Password Reset Flow)

A Node.js backend API that provides secure authentication and password reset functionality using token-based verification.


## Features

- User Registration & Login
- JWT Authentication
- Forgot Password (Email-based)
- Secure token generation
- Password reset with token validation
- Password hashing using bcrypt


## Tech Stack

- Node.js
- Express.js
- MongoDB (Mongoose)
- JWT
- bcrypt
- Nodemailer

## Password Reset Flow (Backend)
User requests password reset
Backend generates secure token
Token stored in database with expiry
Email sent with reset link
User clicks link
Backend verifies token
If valid → allows password update
Password is hashed and saved

## API Endpoints
POST api/auth/register	           -> Register user
POST api/auth/login	               -> Login user
POST api/auth/forgot-password	   -> Send reset email
GET	api/auth/reset-password/:token -> Verify token
POST api/auth/reset-password/:token -> Reset password

## Eg:
# 1) POST https://password-reset-flow-backend-cjmv.onrender.com/api/auth/register
POST JSON
{
    "email": "learningcpriya@gmail.com",
    "password": "learning@123"
}

Response
{
    "message": "User registered successfully"
}


# 2) POST https://password-reset-flow-backend-cjmv.onrender.com/api/auth/login
POST JSON
{
    "email": "learningcpriya@gmail.com"
}

Response
{
    "message": "Login successful",
    "email": "learningcpriya@gmail.com"
}

# 3) POST https://password-reset-flow-backend-cjmv.onrender.com/api/auth/forget-password
POST JSON 1
{
    "email": "learningcpriya@gmail.com"
}

Response
{
    "message": "Password reset email sent, check your email",
    "resetToken": "15a25f5841ee951214d4a9b8e4966275c8699b8246af4e503eeace9f8f614a42"
}

POST JSON 2
{
    "email" : "priyadharshinic04@gmail.com"
}

Response
{
    "error": "User not found"
}

# 4) GET https://password-reset-flow-backend-cjmv.onrender.com/api/auth/reset-password/15a25f5841ee951214d4a9b8e4966275c8699b8246af4e503eeace9f8f614a42
Request Data
{
    "email": "learningcpriya@gmail.com"
}

Response
{
    "message": "Token is valid"
}

# 5) POST https://password-reset-flow-backend-cjmv.onrender.com/api/auth/reset-password/15a25f5841ee951214d4a9b8e4966275c8699b8246af4e503eeace9f8f614a42
POST JSON
{
    "password": "priya@123"
}

Response
{
    "message": "Password reset successfully"
}

## Security Features
Password hashing (bcrypt)
Token expiration handling
Secure email-based reset
Input validation
