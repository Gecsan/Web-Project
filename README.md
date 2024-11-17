MoveMate-backend/
│
├── app/
│   ├── __init__.py             # Marks the app directory as a Python package.
│   ├── crud.py                 # Handles all Create, Read, Update, Delete (CRUD) operations.
│   ├── database.py             # Configures the database connection and ORM session.
│   ├── dependencies.py         # Provides shared utilities like authentication.
│   ├── main.py                 # Entry point of the FastAPI application.
│   ├── models.py               # Defines database models using SQLAlchemy.
│   ├── schemas.py              # Defines Pydantic schemas for validation and serialization.
│   ├── routers/                # Contains individual route modules.
│       ├── __init__.py         # Marks the routers directory as a Python package.
│       ├── favorites.py        # Routes for managing user favorites.
│       ├── login.py            # Routes for authentication and login.
│       ├── moves.py            # Routes for move-related operations.
│       ├── quotes.py           # Routes for managing quotes.
│       ├── reviews.py          # Routes for handling reviews.
│       ├── schedules.py        # Routes for schedules.
│       ├── services.py         # Routes for managing services.
│       ├── users.py            # Routes for user management.
│
├── requirements.txt            # Lists Python dependencies.
├── .gitignore                  # Files to ignore in version control.
└── README.md                   # Documentation (you can paste this content here).

---

## Components Overview

### 1. **Main Application (`main.py`)**
The entry point of the FastAPI application. It initializes the app, configures CORS middleware, and includes all the API routes from the `routers` directory.

Key Functions:
- Sets up CORS middleware for cross-origin requests.
- Includes all API routers with their respective prefixes (e.g., `/api` for most routes).

### 2. **Routers (`routers/*.py`)**
Each module in the `routers` directory corresponds to a feature of the application. These modules define the endpoints (routes) that clients can interact with.

Examples:
- **`users.py`**: Handles user management (create, read, update, delete users).
- **`favorites.py`**: Manages user favorites.
- **`login.py`**: Authenticates users and issues JWT tokens.
- **`moves.py`**: Manages move-related operations.
- **`quotes.py`**: Creates and retrieves quotes for moving services.
- **`reviews.py`**: Handles user reviews for services.
- **`schedules.py`**: Manages schedules for service providers.
- **`services.py`**: Manages services offered by MoveMate.

### 3. **CRUD (`crud.py`)**
Contains reusable functions for database operations using SQLAlchemy. This keeps database logic separate from the routers.

Example CRUD Functions:
- `create_user()`: Adds a new user to the database.
- `get_users()`: Retrieves a list of users.
- `create_quote()`: Adds a new quote.
- `delete_service()`: Deletes a service by ID.

### 4. **Database (`database.py`)**
Configures the database connection and ORM session. It uses SQLAlchemy to connect to a PostgreSQL database.

Key Components:
- **`engine`**: Establishes the connection to the database.
- **`Base`**: A declarative base for defining SQLAlchemy models.
- **`get_db()`**: Dependency function to provide a database session to API endpoints.

### 5. **Models (`models.py`)**
Defines the database structure using SQLAlchemy. Each class represents a table in the database.

Example Models:
- **`User`**: Represents a user, with fields for `id`, `full_name`, `email`, etc.
- **`Quote`**: Represents a quote, with fields for `origin`, `destination`, `move_date`, etc.

### 6. **Schemas (`schemas.py`)**
Defines the data validation and serialization schemas using Pydantic. These ensure the data sent to and from the API is valid.

Example Schemas:
- **`UserCreate`**: Validates data for creating a user.
- **`Quote`**: Defines the structure of a quote when returned to clients.

### 7. **Dependencies (`dependencies.py`)**
Includes shared dependencies like authentication and utility functions.

Key Features:
- **JWT Authentication**: Provides functions to create and decode JSON Web Tokens (JWT).
- **Password Hashing**: Ensures secure storage of user passwords using hashing.

### 8. **Requirements (`requirements.txt`)**
Lists all dependencies required to run the project. Install them using:
```bash
pip install -r requirements.txt
