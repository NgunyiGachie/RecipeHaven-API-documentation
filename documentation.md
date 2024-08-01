# API Documentation

## **Authentication Endpoints**

### **Login**

**Endpoint**: `POST /api/auth/login`

**Request Body**:
```json
{
  "email": "user@example.com",
  "password": "password123"
}
```

**Response**:
- **Success** (200 OK):
```json
{
  "token": "JWT token here",
  "user": {
    "id": 1,
    "username": "exampleuser",
    "email": "user@example.com"
  }
}
```

- **Error** (401 Unauthorized):
```json
{
  "error": "Invalid credentials"
}
```

### **Signup**

**Endpoint**: `POST /api/auth/signup`

**Request Body**:
```json
{
  "username": "exampleuser",
  "email": "user@example.com",
  "password": "password123"
}
```

**Response**:
- **Success** (201 Created):
```json
{
  "message": "User registered successfully",
  "user": {
    "id": 1,
    "username": "exampleuser",
    "email": "user@example.com"
  }
}
```

- **Error** (400 Bad Request):
```json
{
  "error": "Signup failed"
}
```

### **Reset Password**

**Endpoint**: `POST /api/auth/reset_password`

**Request Body**:
```json
{
  "email": "user@example.com"
}
```

**Response**:
- **Success** (200 OK):
```json
{
  "message": "Password reset email sent"
}
```

- **Error** (404 Not Found):
```json
{
  "error": "Email not found"
}
```

### **Activate Account**

**Endpoint**: `POST /api/auth/activate_account`

**Request Body**:
```json
{
  "activation_token": "token_here"
}
```

**Response**:
- **Success** (200 OK):
```json
{
  "message": "Account activated successfully"
}
```

- **Error** (400 Bad Request):
```json
{
  "error": "Invalid or expired token"
}
```

## **Recipe Endpoints**

### **Fetch All Recipes**

**Endpoint**: `GET /api/recipes`

**Response**:
- **Success** (200 OK):
```json
{
  "recipes": [
    {
      "id": 1,
      "title": "Recipe Title",
      "description": "Recipe description",
      "ingredients": "List of ingredients",
      "instructions": "Step-by-step instructions",
      "created_at": "2024-07-31",
      "user": {
        "id": 1,
        "username": "exampleuser"
      }
    }
  ]
}
```

### **Fetch a Single Recipe**

**Endpoint**: `GET /api/recipes/:recipe`

**Response**:
- **Success** (200 OK):
```json
{
  "recipe": {
    "id": 1,
    "title": "Recipe Title",
    "description": "Recipe description",
    "ingredients": "List of ingredients",
    "instructions": "Step-by-step instructions",
    "created_at": "2024-07-31",
    "user": {
      "id": 1,
      "username": "exampleuser"
    }
  }
}
```

- **Error** (404 Not Found):
```json
{
  "error": "Recipe not found"
}
```

### **Create a Recipe**

**Endpoint**: `POST /api/recipes`

**Request Body**:
```json
{
  "title": "New Recipe Title",
  "description": "Description of the recipe",
  "ingredients": "List of ingredients",
  "instructions": "Step-by-step instructions"
}
```

**Response**:
- **Success** (201 Created):
```json
{
  "message": "Recipe created successfully",
  "recipe": {
    "id": 2,
    "title": "New Recipe Title",
    "description": "Description of the recipe",
    "ingredients": "List of ingredients",
    "instructions": "Step-by-step instructions",
    "created_at": "2024-07-31",
    "user": {
      "id": 1,
      "username": "exampleuser"
    }
  }
}
```

- **Error** (400 Bad Request):
```json
{
  "error": "Invalid recipe data"
}
```

### **Update a Recipe**

**Endpoint**: `PUT /api/recipes/:recipe`

**Request Body**:
```json
{
  "title": "Updated Recipe Title",
  "description": "Updated description",
  "ingredients": "Updated list of ingredients",
  "instructions": "Updated instructions"
}
```

**Response**:
- **Success** (200 OK):
```json
{
  "message": "Recipe updated successfully",
  "recipe": {
    "id": 1,
    "title": "Updated Recipe Title",
    "description": "Updated description",
    "ingredients": "Updated list of ingredients",
    "instructions": "Updated instructions",
    "updated_at": "2024-07-31T12:00:00Z",
    "user": {
      "id": 1,
      "username": "exampleuser"
    }
  }
}
```

- **Error** (400 Bad Request):
```json
{
  "error": "Invalid recipe data"
}
```

### **Delete a Recipe**

**Endpoint**: `DELETE /api/recipes/:recipe`

**Response**:
- **Success** (200 OK):
```json
{
  "message": "Recipe deleted successfully"
}
```

- **Error** (404 Not Found):
```json
{
  "error": "Recipe not found"
}
```

## **Cooking Tips Endpoints**

### **Fetch All Cooking Tips**

**Endpoint**: `GET /api/cooking_tips`

**Response**:
- **Success** (200 OK):
```json
{
  "cooking_tips": [
    {
      "id": 1,
      "title": "Tip Title",
      "content": "Tip content",
      "created_at": "2024-07-31",
      "updated_at": "2024-07-31",
      "user": {
        "id": 1,
        "username": "exampleuser"
      }
    }
  ]
}
```

### **Fetch a Single Cooking Tip**

**Endpoint**: `GET /api/cooking_tips/:cooking_tip`

**Response**:
- **Success** (200 OK):
```json
{
  "cooking_tip": {
    "id": 1,
    "title": "Tip Title",
    "content": "Tip content",
    "created_at": "2024-07-31",
    "updated_at": "2024-07-31",
    "user": {
      "id": 1,
      "username": "exampleuser"
    }
  }
}
```

- **Error** (404 Not Found):
```json
{
  "error": "Cooking tip not found"
}
```

### **Create a Cooking Tip**

**Endpoint**: `POST /api/cooking_tips`

**Request Body**:
```json
{
  "title": "New Tip Title",
  "content": "Content of the cooking tip"
}
```

**Response**:
- **Success** (201 Created):
```json
{
  "message": "Cooking tip created successfully",
  "cooking_tip": {
    "id": 2,
    "title": "New Tip Title",
    "content": "Content of the cooking tip",
    "created_at": "2024-07-31T12:00:00Z",
    "user": {
      "id": 1,
      "username": "exampleuser"
    }
  }
}
```

- **Error** (400 Bad Request):
```json
{
  "error": "Invalid cooking tip data"
}
```

### **Update a Cooking Tip**

**Endpoint**: `PUT /api/cooking_tips/:cooking_tip`

**Request Body**:
```json
{
  "title": "Updated Tip Title",
  "content": "Updated content"
}
```

**Response**:
- **Success** (200 OK):
```json
{
  "message": "Cooking tip updated successfully",
  "cooking_tip": {
    "id": 1,
    "title": "Updated Tip Title",
    "content": "Updated content",
    "updated_at": "2024-07-31T12:00:00Z",
    "user": {
      "id": 1,
      "username": "exampleuser"
    }
  }
}
```

- **Error** (400 Bad Request):
```json
{
  "error": "Invalid cooking tip data"
}
```

### **Delete a Cooking Tip**

**Endpoint**: `DELETE /api/cooking_tips/:cooking_tip`

**Response**:
- **Success** (200 OK):
```json
{
  "message": "Cooking tip deleted successfully"
}
```

- **Error** (404 Not Found):
```json
{
  "error": "Cooking tip not found"
}
```

## **Comments Endpoints**

### **Fetch Reviews**

**Endpoint**: `GET /api/recipes/:recipe/reviews`

**Response**:
- **Success** (200 OK):
```json
{
  "reviews": [
    {
      "id": 1,
      "review": "I love this beef recipe",
      "user": {
        "id": 1,
        "username": "exampleuser"
      },
      "created_at": "2024-07-31T12:00:00Z"
    }
  ]
}
```
