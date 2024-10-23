# Stocks API in C#

I started this project to get into ASP.NET Core. This is a simple RESTful API built with C#, using ASP.NET Core, Entity Framework Core, and MSSQL Server for managing stock information. It supports CRUD operations for users, portfolios, comments, and stocks. The API is secured using JWT-based authentication. Future plans are to create a User Interface for the application.

## Table of Contents

-   [Features](#features)
-   [Technologies](#technologies)
-   [Getting Started](#getting-started)
-   [API Endpoints](#api-endpoints)
-   [Database Setup](#database-setup)
-   [Running the Application](#running-the-application)
-   [Authentication](#authentication)
-   [Contributing](#contributing)
-   [License](#license)

## Features

-   User registration and authentication (JWT).
-   CRUD operations for:
    -   Stocks
    -   Comments
    -   Portfolios
-   MSSQL Server integration with Entity Framework Core.
-   RESTful principles with JSON responses.

## Technologies

-   **Backend Framework**: ASP.NET Core
-   **Database**: MSSQL Server
-   **ORM**: Entity Framework Core
-   **Authentication**: JWT (JSON Web Token)
-   **Language**: C#

## Getting Started

### Prerequisites

Ensure you have the following installed on your machine:

-   [.NET 8 SDK](https://dotnet.microsoft.com/download/dotnet/8.0)
-   [SQL Server](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)
-   [Postman](https://www.postman.com/downloads/) or any API testing tool

### Clone the Repository

```bash
git clone https://github.com/yourusername/stocks-api.git
cd stocks-api
```

### Setting Up the Database

Update the connection string in the `appsettings.json` file to match your MSSQL Server setup:

```json
"ConnectionStrings": {
  "DefaultConnection": "Server=YOUR_SERVER;Database=StocksDb;User Id=YOUR_USER;Password=YOUR_PASSWORD;"
}
```

### Database Migrations

Run the following commands to apply migrations and create the database:

```bash
dotnet ef migrations add InitialCreate
dotnet ef database update
```

This will set up the required tables in your MSSQL database.

### API Endpoints

Run the following commands to apply migrations and create the database:

```bash
dotnet ef migrations add InitialCreate
dotnet ef database update
```

This will set up the required tables in your MSSQL database.

### API Endpoints

#### Authentication

-   **POST** `/api/account/login`:  
    Authenticate a user and return a JWT token.

-   **POST** `/api/account/register`:  
    Register a new user.

#### Stocks

-   **GET** `/api/stock`:  
    Retrieve a list of all stocks with optional filters.

-   **GET** `/api/stock/{id}`:  
    Retrieve details of a specific stock by its ID.

-   **POST** `/api/stock`:  
    Create a new stock entry.

-   **PUT** `/api/stock/{id}`:  
    Update an existing stock's information.

-   **DELETE** `/api/stock/{id}`:  
    Delete a stock by its ID.

#### Portfolios

-   **GET** `/api/portfolio`:  
    Retrieve portfolio information.

-   **POST** `/api/portfolio`:  
    Add a new stock to the portfolio.

-   **DELETE** `/api/portfolio`:  
    Remove a stock from the portfolio.

#### Comments

-   **GET** `/api/comment`:  
    Retrieve all comments.

-   **POST** `/api/comment/{stockId}`:  
    Add a comment to a stock.

### Database Setup

#### Entity Models

-   **Stock**: Represents stock data (symbol, company name, industry, etc.).
-   **Portfolio**: Represents a user's collection of stocks.
-   **Comment**: User comments on stocks.

Entity relationships are set up through navigation properties in the models, and Entity Framework handles the ORM tasks.

### Running the Application

Build the project:

```bash
dotnet build
dotnet run
```

### Authentication

The API uses JWT for secure authentication. Once a user registers or logs in, a JWT token is returned. Include this token in the Authorization header of requests to protected endpoints:

```http
Authorization: Bearer <token>
```

### Contributing

Shoutout to the amazing series by [@teddysmithdev](https://twitter.com/teddysmithdev) on ASP.NET made this project possible.Feel free to submit a pull request or open an issue if you find any bugs or want to add new features.

### License

This project is licensed under the MIT License.
