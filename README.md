# User Management Application in NestJS

![NestJS](https://img.shields.io/badge/NestJS-7E22CE?style=for-the-badge&logo=nestjs&logoColor=white)
![Mongoose](https://img.shields.io/badge/Mongoose-880000?style=for-the-badge&logo=mongoose&logoColor=white)
![JWT](https://img.shields.io/badge/JWT-black?style=for-the-badge&logo=JSON%20web%20tokens)
![Passport](https://img.shields.io/badge/Passport.js-34E27A?style=for-the-badge)
![Google](https://img.shields.io/badge/Google-4285F4?style=for-the-badge&logo=google&logoColor=white)
![Facebook](https://img.shields.io/badge/Facebook-1877F2?style=for-the-badge&logo=facebook&logoColor=white)

This is a **NestJS**-based user management application that allows users to register, log in, and manage their accounts with JWT-based authentication. The application supports OAuth login through Google and Facebook, as well as features for password management and user administration.

## Features

- **User Registration**: Users can sign up with their email and receive a confirmation message.
- **User Login**: Secure login with **JWT** token authentication via email or third-party OAuth providers.
- **Login via OAuth**: Support for logging in using Google and Facebook accounts.
- **User List**: Fetch a paginated list of users with search functionality.
- **User Update**: Update user profile information.
- **Password Management**:
  - **Forgot Password**: Request a password reset link.
  - **Reset Password**: Change password using the reset link.
  - **Change Password**: Change the password while logged in.
- **User Search**: Search users by various criteria.

## Technologies Used

- **NestJS**: A framework for building scalable Node.js server-side applications.
- **Mongoose**: For MongoDB database management and modeling.
- **NodeMailer**: A module for sending emails (for password resets).
- **Passport.js**: Authentication middleware for Node.js.
- **Passport-Google-OAuth20**: Google OAuth 2.0 strategy for Passport.js.
- **Passport-Facebook**: Facebook OAuth 2.0 strategy for Passport.js.
- **JWT**: For JSON Web Token authentication.

## APIs

### 1. **User Registration**

- **Endpoint**: `/auth/register`
- **Method**: `POST`
- **Request Body**:
  ```json
  {
    "username": "John Doe",
    "email": "john@example.com",
    "password": "your_password"
  }
  ```
- **Description**: Registers a new user and returns a confirmation message.

### 2. **User Login**

- **Endpoint**: `/auth/login`
- **Method**: `POST`
- **Request Body**:
  ```json
  {
    "email": "john@example.com",
    "password": "your_password"
  }
  ```
- **Description**: Logs in an existing user and returns a JWT token.

### 3. **Login via Google**

- **Endpoint**: `/auth/google`
- **Method**: `GET`
- **Description**: Initiates Google OAuth flow for user authentication.

### 4. **Google Callback**

- **Endpoint**: `/auth/google/callback`
- **Method**: `GET`
- **Description**: Handles the callback after Google authentication and logs in the user.

### 5. **Login via Facebook**

- **Endpoint**: `/auth/facebook`
- **Method**: `GET`
- **Description**: Initiates Facebook OAuth flow for user authentication.

### 6. **Facebook Callback**

- **Endpoint**: `/auth/facebook/callback`
- **Method**: `GET`
- **Description**: Handles the callback after Facebook authentication and logs in the user.

### 7. **User List**

- **Endpoint**: `/user`
- **Method**: `GET`
- **Query Parameters**:
  - `page`: Page number for pagination.
  - `limit`: Number of users per page.
  - `search`: Optional search term.
- **Description**: Retrieves a paginated list of users.

### 8. **User Update**

- **Endpoint**: `/user/update`
- **Method**: `PATCH`
- **Headers**:
  ```json
  {
    "Authorization": "Bearer <access_token>"
  }
  ```
- **Request Body**:
  ```json
  {
    "username": "John Doe",
    "email": "john@example.com"
  }
  ```
- **Description**: Updates the profile information of the logged-in user.

### 9. **Forgot Password**

- **Endpoint**: `/auth/forgot-password`
- **Method**: `POST`
- **Request Body**:
  ```json
  {
    "email": "john@example.com"
  }
  ```
- **Description**: Sends a password reset link to the user's email.

### 10. **Reset Password**

- **Endpoint**: `/auth/reset-password`
- **Method**: `POST`
- **Request Body**:
  ```json
  {
    "token": "reset_token",
    "newPassword": "your_new_password"
  }
  ```
- **Description**: Resets the password using the provided token.

### 11. **Change Password**

- **Endpoint**: `/auth/change-password`
- **Method**: `PATCH`
- **Headers**:
  ```json
  {
    "Authorization": "Bearer <access_token>"
  }
  ```
- **Request Body**:
  ```json
  {
    "currentPassword": "your_current_password",
    "newPassword": "your_new_password"
  }
  ```
- **Description**: Changes the password while the user is logged in.

### 12. **Profile**

- **Endpoint**: `/user/profile`
- **Method**: `GET`
- **Headers**:
  ```json
  {
    "Authorization": "Bearer <access_token>"
  }
  ```
- **Description**: Retrieves the profile details of the logged-in user.

## Installation

1. Clone the repository:

   ```bash
   git clone <repository-url>
   cd user-management-app

   ```

2. Install the required dependencies:
   npm install

3. Set up environment variables by creating a .env file in the root directory with the following values:

GOOGLE_CLIENT_ID=<your_google_client_id>
GOOGLE_CLIENT_SECRET=<your_google_client_secret>
GOOGLE_CALLBACK_URL=http://localhost:3000/auth/google/callback

FACEBOOK_APP_ID=<your_facebook_app_id>
FACEBOOK_APP_SECRET=<your_facebook_app_secret>
FACEBOOK_CALLBACK_URL=http://localhost:3000/auth/facebook/callback

JWT_SECRET=<your_jwt_secret>
MONGODB_URI=<your_mongodb_connection_string>

4. Run the application:

npm run start

5. Open the app in your browser at http://localhost:3000.

## Project Structure

src/
|-- auth/ # Authentication logic with Passport.js and OAuth strategies
|-- user/ # User management including registration, update, and listing
|-- app.module.ts # Main application file
|-- main.ts # Entry point of the application
|-- tests/ # Unit and integration tests
