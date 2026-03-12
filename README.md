# Cookbook API
A RESTful API built with Express.js for managing recipes and user accounts.
## Description
The Cookbook API provides endpoints for creating, reading, updating, and deleting recipes, as well as a user password reset flow secured with security questions and bcrypt password hashing. Data is managed via an in-memory `Collection` class that mimics MongoDB-style CRUD operations.
## Prerequisites
- Node.js v22.21.0+
- npm v10.9.4+
## Installation
```bash
npm install
```
## Usage
**Start (production)**
```bash
npm start
```
**Start (development with auto-reload)**
```bash
npm run dev
```
The server runs on `http://localhost:3000` by default.
## API Endpoints
### Landing Page
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/` | Returns an HTML landing page |
### Recipes
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/api/recipes` | Retrieve all recipes |
| GET | `/api/recipes/:id` | Retrieve a recipe by ID |
| POST | `/api/recipes` | Create a new recipe |
| PUT | `/api/recipes/:id` | Update an existing recipe |
| DELETE | `/api/recipes/:id` | Delete a recipe |
**Recipe object shape:**
```json
{
  "id": 1,
  "name": "Classic Beef Tacos",
  "ingredients": ["ground beef", "taco shells", "lettuce", "cheese"]
}
```
### Users
| Method | Endpoint | Description |
|--------|----------|-------------|
| POST | `/api/users/:email/reset-password` | Reset a user's password |
**Reset password request body:**
```json
{
  "newPassword": "newSecurePassword",
  "securityQuestions": [
    { "answer": "answer1" },
    { "answer": "answer2" },
    { "answer": "answer3" }
  ]
}
```
## Testing
```bash
npm test
```
Tests are written with [Jest](https://jestjs.io/) and [Supertest](https://github.com/ladjs/supertest).
## Dependencies
- [express](https://expressjs.com/) - Web framework
- [bcryptjs](https://github.com/dcodeIO/bcrypt.js) - Password hashing
- [ajv](https://ajv.js.org/) - JSON schema validation
- [http-errors](https://github.com/jshttp/http-errors) - HTTP error creation
## License
MIT
