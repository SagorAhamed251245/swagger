# TS4U Ecommerce API Documentation (JavaScript)

## API Version: 1.0.0  
**Base URL:** `https://staging-be-ecom.techserve4u.com/`

This documentation explains how to interact with the **TS4U Ecommerce API** using JavaScript, specifically through the `fetch` API. It includes examples for common endpoints such as user signup, signin, Google authentication, OTP verification, and user verification.

---

## Authentication

The API uses **Bearer Token** for authentication in some endpoints. Make sure to include the token in the **Authorization** header for relevant requests.

---

## Endpoints

### 1. **User Signup**
- **Endpoint:** `POST /api/user/signup`
- **Description:** Allows users to sign up with their details.

#### Request Body:
```json
{
  "email": "string",    // User's email address
  "name": "string",     // User's full name
  "password": "string"  // User's password
}
```

#### JavaScript Example:
```javascript
fetch('https://staging-be-ecom.techserve4u.com/api/user/signup', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({
    email: 'user@example.com',
    name: 'John Doe',
    password: 'password123'
  })
})
.then(response => response.json())
.then(data => console.log('User Signup Successful:', data))
.catch(error => console.error('Error:', error));
```

#### Possible Responses:
- **200 OK** - User signed up successfully.
- **400 Bad Request** - Invalid data provided.
- **404 Not Found** - Endpoint not found.

---

### 2. **User Signin**
- **Endpoint:** `POST /api/user/signin`
- **Description:** Allows users to sign in using their email and password.

#### Request Body:
```json
{
  "email": "string",    // User's email address
  "password": "string"  // User's password
}
```

#### JavaScript Example:
```javascript
fetch('https://staging-be-ecom.techserve4u.com/api/user/signin', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({
    email: 'user@example.com',
    password: 'password123'
  })
})
.then(response => response.json())
.then(data => console.log('User Signin Successful:', data))
.catch(error => console.error('Error:', error));
```

#### Possible Responses:
- **200 OK** - User signed in successfully.
- **400 Bad Request** - Invalid credentials or missing data.
- **404 Not Found** - Endpoint not found.

---

### 3. **Google Authentication**
- **Endpoint:** `POST /api/user/googleauth`
- **Description:** Allows users to authenticate using their Google token.

#### Request Body:
```json
{
  "tokenId": "string"  // The Google authentication token
}
```

#### JavaScript Example:
```javascript
fetch('https://staging-be-ecom.techserve4u.com/api/user/googleauth', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({
    tokenId: 'google_token_here'
  })
})
.then(response => response.json())
.then(data => console.log('Google Authentication Successful:', data))
.catch(error => console.error('Error:', error));
```

#### Possible Responses:
- **200 OK** - User authenticated successfully.
- **400 Bad Request** - Invalid token or missing data.

---

### 4. **Verify User**
- **Endpoint:** `POST /api/user/verify`
- **Description:** Verifies a user by using a bearer token in the authorization header.

#### Request Header:
```json
{
  "Authorization": "Bearer <your_token_here>"
}
```

#### JavaScript Example:
```javascript
const token = 'your_bearer_token_here';

fetch('https://staging-be-ecom.techserve4u.com/api/user/verify', {
  method: 'POST',
  headers: {
    'Authorization': `Bearer ${token}`,
  }
})
.then(response => response.json())
.then(data => console.log('User Verified:', data))
.catch(error => console.error('Error:', error));
```

#### Possible Responses:
- **200 OK** - User verified successfully.
- **400 Bad Request** - Invalid request format.
- **401 Unauthorized** - Missing or invalid authorization token.

---

### 5. **Verify OTP**
- **Endpoint:** `POST /api/user/verifyotp`
- **Description:** Verifies a user by using an OTP sent to their email.

#### Request Body:
```json
{
  "email": "string",  // User's email address
  "otp": "string"     // One-Time Password (OTP) received by the user
}
```

#### JavaScript Example:
```javascript
fetch('https://staging-be-ecom.techserve4u.com/api/user/verifyotp', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({
    email: 'user@example.com',
    otp: '123456'
  })
})
.then(response => response.json())
.then(data => console.log('OTP Verified:', data))
.catch(error => console.error('Error:', error));
```

#### Possible Responses:
- **200 OK** - OTP verified successfully.
- **400 Bad Request** - Invalid OTP or missing data.
- **401 Unauthorized** - Unauthorized request.

---

## Error Codes

- **200 OK:** The request was successful.
- **400 Bad Request:** The request was malformed or missing required parameters.
- **401 Unauthorized:** Authentication failed due to missing or invalid token.
- **404 Not Found:** The requested endpoint could not be found.

---

## Example Usage

Here are examples of how you can interact with the API using JavaScript.

### Example 1: User Signup
```javascript
fetch('https://staging-be-ecom.techserve4u.com/api/user/signup', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({
    email: 'user@example.com',
    name: 'John Doe',
    password: 'password123'
  })
})
.then(response => response.json())
.then(data => console.log('User Signup Successful:', data))
.catch(error => console.error('Error:', error));
```

### Example 2: User Signin
```javascript
fetch('https://staging-be-ecom.techserve4u.com/api/user/signin', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({
    email: 'user@example.com',
    password: 'password123'
  })
})
.then(response => response.json())
.then(data => console.log('User Signin Successful:', data))
.catch(error => console.error('Error:', error));
```

### Example 3: Google Authentication
```javascript
fetch('https://staging-be-ecom.techserve4u.com/api/user/googleauth', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({
    tokenId: 'google_token_here'
  })
})
.then(response => response.json())
.then(data => console.log('Google Authentication Successful:', data))
.catch(error => console.error('Error:', error));
```

### Example 4: Verify User
```javascript
const token = 'your_bearer_token_here';

fetch('https://staging-be-ecom.techserve4u.com/api/user/verify', {
  method: 'POST',
  headers: {
    'Authorization': `Bearer ${token}`,
  }
})
.then(response => response.json())
.then(data => console.log('User Verified:', data))
.catch(error => console.error('Error:', error));
```

### Example 5: Verify OTP
```javascript
fetch('https://staging-be-ecom.techserve4u.com/api/user/verifyotp', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({
    email: 'user@example.com',
    otp: '123456'
  })
})
.then(response => response.json())
.then(data => console.log('OTP Verified:', data))
.catch(error => console.error('Error:', error));
```

---

This documentation provides a quick guide for using the **TS4U Ecommerce API** in your JavaScript projects. For more details, refer to the official API documentation.
