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
POST /auth/register	            -> Register user
POST /auth/login	            -> Login user
POST /auth/forgot-password	    -> Send reset email
GET	/auth/reset-password/:token -> Verify token
POST /auth/reset-password/:token -> Reset password

## Security Features
Password hashing (bcrypt)
Token expiration handling
Secure email-based reset
Input validation
