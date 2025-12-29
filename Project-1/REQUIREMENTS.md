# User Entity Requirements

## API Requirements

### User Entity

- [ ] Register a new user account with username and password
- [ ] Authenticate a user with username and password
- [ ] Retrieve user information by ID
- [ ] Retrieve all users with optional filtering
- [ ] Update user account information
- [ ] Delete a user account

### Content Entity

- [ ] Create new content
- [ ] Retrieve content by ID
- [ ] Retrieve all content with optional filtering
- [ ] Update existing content
- [ ] Delete content

### Social Features

- [ ] Follow another user
- [ ] Unfollow a user
- [ ] Retrieve all users that a specific user follows

## API Endpoints

### Registration & Authentication
- `POST /users/register` - Register new user
- `POST /users/login` - Authenticate user

### User Operations
- `GET /users/{id}` - Get user by ID
- `GET /users` - Get all users with optional filters
  - `firstName` - Filter by first name
  - `lastName` - Filter by last name
  - `username` - Filter by username
  - `email` - Filter by email
- `PUT /users/{id}` - Update user
- `DELETE /users/{id}` - Delete user

### Content Operations
- `POST /content` - Create new content
- `GET /content/{id}` - Get content by ID
- `GET /content` - Get all content with optional filters
  - `userId` - Filter by content owner
  - `date` - Filter by date
- `PUT /content/{id}` - Update content
- `DELETE /content/{id}` - Delete content

### Social Operations
- `POST /users/{id}/follows/{followId}` - Follow a user
- `DELETE /users/{id}/follows/{followId}` - Unfollow a user
- `GET /users/{id}/follows` - Get all users that a user follows

## Validation Rules
- Username is required and must be unique
- Email is required, must be unique, and must be properly formatted
- Password is required and must contain:
  - Minimum 8 characters
  - At least one uppercase letter
  - At least one lowercase letter
  - At least one number
- Users cannot follow themselves
- Users cannot follow the same user more than once