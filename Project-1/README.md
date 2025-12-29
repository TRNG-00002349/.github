# Project 1: Java API
This first project will be in progress for the first three weeks of training. This will coincide with the training topics of Java, SQL, JDBC, and REST with Javalin. We will be building a server API with no front end UI, and simple authentication/authorization.

> ```This project is a REST API built with Java, Javalin, JDBC, and SQL that implements user authentication, content management, and social features. The application follows a 3-tier architecture (Presentation, Service, Data layers) and includes secure user registration/login, CRUD operations for a generic content entity, and the ability for users to follow each other. The project requires proper validation, password hashing, and query filtering while working with a relational database using JDBC. The domain and content type are intentionally left unspecified, allowing associates to theme their project around any topic of interest.```

We will follow a [Multitier Architecture](https://en.wikipedia.org/wiki/Multitier_architecture) with 3 layers:
 - Presentation Layer (Web Controllers)
 - Service Layer (Business Logic)
 - Data Layer (Database Access)

## Presentation Layer
This layer should include classes which handle web communication. These classes should really only be dealing with the requests and responses. All other work should be invoked in the service layer.

We will build controllers here to handle web requests using the Javalin API library.

## Service Layer
This layer handles most of the business logic, everything that doesn't belong in the presentation or data layers. The presentation layer above invokes business operations here in the service layer. This layer then breaks those operations into individual data operations and invokes them in the data layer below.

## Data Layer
The service layer invokes operations here in the data layer in order to persist or retrieve data from some data source. Often a business operation makes multiple calls down into this layer.

We will build DAOs here to access a SQL database using the built in Java JDBC library.

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
- Passwords must be hashed, no plain text
- Users cannot follow themselves
- Users cannot follow the same user more than once
