<h1 align="center">NODEJS-HW-07</h1>

<p align="center">Empowering Secure Connections, Simplifying User Management with Comprehensive API Documentation</p>

<p align="center">
  <!-- Dynamic badges - You may need to customize these for your specific GitHub repository -->
  <img src="https://img.shields.io/github/last-commit/emrealtnts0/nodejs-hw-07?color=blue&label=last%20commit" alt="Last Commit">
  <img src="https://img.shields.io/github/languages/percentage/emrealtnts0/nodejs-hw-07/javascript?color=orange&label=javascript" alt="JavaScript Percentage">
  <img src="https://img.shields.io/github/languages/count/emrealtnts0/nodejs-hw-07?color=green&label=languages" alt="Languages Count">
</p>

<p align="center">Built with the tools and technologies:</p>

<p align="center">
  <img src="https://img.shields.io/badge/Express.js-000000?style=for-the-badge&logo=express&logoColor=white" alt="Express.js">
  <img src="https://img.shields.io/badge/JSON-000000?style=for-the-badge&logo=json&logoColor=white" alt="JSON">
  <img src="https://img.shields.io/badge/Markdown-000000?style=for-the-badge&logo=markdown&logoColor=white" alt="Markdown">
  <img src="https://img.shields.io/badge/npm-CB3837?style=for-the-badge&logo=npm&logoColor=white" alt="npm">
  <img src="https://img.shields.io/badge/MongoDB-47A248?style=for-the-badge&logo=mongodb&logoColor=white" alt="MongoDB">
  <img src="https://img.shields.io/badge/.env-ECD53F?style=for-the-badge&logo=dot-env&logoColor=black" alt=".env">
  <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black" alt="JavaScript">
  <img src="https://img.shields.io/badge/Nodemon-76D04B?style=for-the-badge&logo=nodemon&logoColor=white" alt="Nodemon">
  <img src="https://img.shields.io/badge/Cloudinary-3399FF?style=for-the-badge&logo=cloudinary&logoColor=white" alt="Cloudinary">
  <img src="https://img.shields.io/badge/ESLint-4B32C3?style=for-the-badge&logo=eslint&logoColor=white" alt="ESLint">
  <img src="https://img.shields.io/badge/YAML-CB171E?style=for-the-badge&logo=yaml&logoColor=white" alt="YAML">
</p>

# Contact Management API with Swagger Documentation

This project is a REST API that includes user authentication, password reset functionality, contact management features, and comprehensive API documentation using Swagger/OpenAPI. It integrates with Brevo email service and Cloudinary image upload service.

## 🚀 Features

- User authentication (register, login, logout)
- JWT-based session management
- Password reset via email
- Contact management (CRUD operations)
- Photo upload and management (Cloudinary integration)
- Email sending (Brevo SMTP integration)
- **Comprehensive API documentation with Swagger/OpenAPI**
- **Interactive API documentation with ReDoc and Swagger UI**

## 📋 Requirements

- Node.js (v18 or higher)
- MongoDB
- Brevo account (for email sending)
- Cloudinary account (for image upload)

## 🔧 Installation

1. Clone the project:
```bash
git clone <repository-url>
cd nodejs-hw-07
```

2. Install dependencies:
```bash
npm install
```

3. Create `.env` file:
```bash
cp .env.example .env
```

4. Edit `.env` file and set required variables:
```env
# Server
PORT=3000

# Database
MONGODB_URI=mongodb://localhost:27017/your-database-name

# JWT
JWT_SECRET=your-jwt-secret

# Email (Brevo)
SMTP_HOST=smtp-relay.brevo.com
SMTP_PORT=587
SMTP_USER=your-brevo-username
SMTP_PASSWORD=your-brevo-password
SMTP_FROM=your-verified-email@domain.com

# Frontend Domain
APP_DOMAIN=http://localhost:3000/auth

# Cloudinary
CLOUDINARY_CLOUD_NAME=your-cloud-name
CLOUDINARY_API_KEY=your-api-key
CLOUDINARY_API_SECRET=your-api-secret
```

5. Start the application:
```bash
npm start
```

## 📚 API Documentation

### Interactive Documentation

The API provides multiple ways to access documentation:

1. **Swagger UI**: Visit `/api-docs` for interactive API documentation
2. **ReDoc**: Run `npm run preview-docs` to view styled documentation
3. **OpenAPI Specification**: Available at `/docs/openapi.yaml`

### Documentation Setup

This project uses the following tools for API documentation:

- **@redocly/cli**: For generating and previewing documentation
- **swagger-ui-express**: For serving interactive Swagger UI
- **OpenAPI 3.1.0**: Specification format

#### Available Scripts

```bash
# Build documentation
npm run build-docs

# Preview documentation locally
npm run preview-docs

# Start the server
npm start
```

### Documentation Structure

```
docs/
├── openapi.yaml          # Main OpenAPI specification
├── swagger.json          # Generated JSON specification
└── index.html            # ReDoc HTML template

swagger/
├── components/           # Reusable components (schemas, responses)
└── paths/               # API endpoint definitions
    ├── contacts/
    │   ├── get.yaml     # GET /contacts
    │   ├── post.yaml    # POST /contacts
    │   └── {id}/
    │       ├── get.yaml # GET /contacts/:id
    │       ├── patch.yaml # PATCH /contacts/:id
    │       └── delete.yaml # DELETE /contacts/:id
    └── auth/
        ├── register.yaml # POST /auth/register
        ├── login.yaml    # POST /auth/login
        └── logout.yaml   # POST /auth/logout
```

## 🔐 Authentication Endpoints

### User Registration
```http
POST /api/auth/register
Content-Type: application/json

{
    "email": "user@example.com",
    "password": "password123",
    "name": "John Doe"
}
```

### User Login
```http
POST /api/auth/login
Content-Type: application/json

{
    "email": "user@example.com",
    "password": "password123"
}
```

### Send Password Reset Email
```http
POST /api/auth/send-reset-email
Content-Type: application/json

{
    "email": "user@example.com"
}
```

### Reset Password
```http
POST /api/auth/reset-pwd
Content-Type: application/json

{
    "token": "jwt-token-from-email",
    "password": "new-password123"
}
```

### Logout
```http
POST /api/auth/logout
Authorization: Bearer <access-token>
```

## 📞 Contact Management Endpoints

### Get All Contacts
```http
GET /api/contacts
Authorization: Bearer <access-token>
```

**Query Parameters:**
- `page` (optional): Page number for pagination
- `limit` (optional): Number of contacts per page
- `favorite` (optional): Filter by favorite status (true/false)

### Get Contact by ID
```http
GET /api/contacts/:contactId
Authorization: Bearer <access-token>
```

### Create Contact (with Photo)
```http
POST /api/contacts
Authorization: Bearer <access-token>
Content-Type: multipart/form-data

{
    "name": "Contact Name",
    "email": "contact@example.com",
    "phone": "1234567890",
    "photo": <file>
}
```

### Update Contact (with Photo)
```http
PATCH /api/contacts/:contactId
Authorization: Bearer <access-token>
Content-Type: multipart/form-data

{
    "name": "Updated Name",
    "email": "updated@example.com",
    "phone": "0987654321",
    "photo": <file>
}
```

### Delete Contact
```http
DELETE /api/contacts/:contactId
Authorization: Bearer <access-token>
```

## 🔐 Security

- All sensitive data is stored in `.env` file
- JWT tokens are valid for 15 minutes
- Password reset tokens are valid for 5 minutes
- Passwords are hashed before storage
- All API endpoints (except registration and login) require authentication
- Bearer token authentication for protected routes

## 📧 Email Template

The password reset email includes:
- User's name
- Password reset link
- Token expiration information
- Security warnings

## 🖼️ Image Upload

- Image upload using Cloudinary service
- Supported formats: JPG, PNG, GIF
- Maximum file size: 5MB
- Automatic image optimization

## ⚠️ Error Codes

- 400: Bad Request (validation error)
- 401: Unauthorized (token error)
- 404: Not Found
- 409: Conflict (e.g., email already in use)
- 500: Server Error

## 🧪 Testing

```bash
# Run all tests
npm test

# Run specific test file
npm test -- <test-file-name>
```

## 📖 Documentation Development

### Adding New Endpoints

1. Create a new YAML file in `swagger/paths/` following the naming convention
2. Define the endpoint with proper OpenAPI 3.1.0 specification
3. Include tags, summary, operationId, description, security, parameters, and responses
4. Reference the new path in `docs/openapi.yaml`

### Example Endpoint Definition

```yaml
tags:
  - Contacts
summary: Get contact by ID
operationId: getContactById
description: Retrieve a specific contact by its unique identifier
security:
  - bearerAuth: []
parameters:
  - name: contactId
    in: path
    required: true
    schema:
      type: string
    description: Contact unique identifier
responses:
  '200':
    description: Contact found successfully
    content:
      application/json:
        schema:
          $ref: '../components/schemas/Contact'
  '404':
    description: Contact not found
    content:
      application/json:
        schema:
          $ref: '../components/schemas/Error'
```

## 🚀 Deployment

The application is configured for deployment on Render.com with the following settings:

- **Branch**: `hw7-swagger`
- **Build Command**: `npm install`
- **Start Command**: `npm start`
- **Environment**: Node.js

## 📝 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
