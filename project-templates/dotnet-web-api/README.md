# .NET Minimal API with GitHub Copilot

This project template demonstrates building a REST API using .NET minimal APIs and C# with GitHub Copilot assistance.

## 🎯 Learning Objectives

- Master minimal API development patterns with Copilot
- Implement authentication and authorization with JWT
- Design data models and Entity Framework Core relationships
- Create comprehensive error handling with Problem Details
- Write API tests with xUnit and documentation with OpenAPI
- Deploy and monitor APIs with health checks

## 🚀 Features

- **Minimal API Design**: CRUD operations with typed route handlers
- **C# & .NET 10**: Latest language features and framework capabilities
- **Authentication**: JWT-based auth with role management
- **Database**: SQLite/PostgreSQL with Entity Framework Core
- **Validation**: Request validation with FluentValidation
- **Testing**: Unit and integration tests with xUnit
- **Documentation**: Auto-generated OpenAPI docs via built-in support
- **Monitoring**: Health checks and structured logging with Serilog

## 📋 Prerequisites

- .NET 10 SDK
- GitHub Copilot extension
- Basic knowledge of REST APIs and C#

## 🛠️ Setup Instructions

### 1. Verify SDK

```bash
dotnet --version
```

### 2. Restore Dependencies

```bash
dotnet restore
```

### 3. Run the Application

```bash
dotnet run
```

The API will be available at `http://localhost:5152`. Open `/openapi/v1.json` for the API spec.

### 4. Test with the .http File

Use `dotnet-web-api.http` in VS Code with the REST Client extension, or use the built-in HTTP file support.

## 📚 Copilot Practice Exercises

### Exercise 1: Todo API

Create a todo management API with CRUD operations.

**Copilot Prompts to Try:**
- "Create a Todo record with Id, Title, IsCompleted, and CreatedAt"
- "Add a MapGroup for /api/todos with GET, POST, PUT, and DELETE endpoints"
- "Implement in-memory storage using a ConcurrentDictionary for todos"

### Exercise 2: Entity Framework Core Integration

Replace in-memory storage with a real database.

**Copilot Prompts to Try:**
- "Create an AppDbContext with a DbSet for Todo entities"
- "Configure SQLite as the database provider in Program.cs"
- "Add EF Core migrations for the Todo model"

### Exercise 3: Request Validation

Add input validation to your endpoints.

**Copilot Prompts to Try:**
- "Create a CreateTodoRequest record with required Title and optional DueDate"
- "Add a validation filter that returns ProblemDetails for invalid requests"
- "Implement FluentValidation rules for CreateTodoRequest"

### Exercise 4: Authentication & Authorization

Secure your API with JWT tokens.

**Copilot Prompts to Try:**
- "Add JWT bearer authentication to the service collection"
- "Create a /api/auth/login endpoint that returns a JWT token"
- "Add .RequireAuthorization() to the todo endpoints"

### Exercise 5: Testing

Create thorough tests for your API.

**Copilot Prompts to Try:**
- "Create an xUnit test project with WebApplicationFactory for integration tests"
- "Write tests for the todo CRUD endpoints using HttpClient"
- "Add FluentAssertions to verify response bodies and status codes"

## 🏗️ Project Structure

```
dotnet-web-api/
├── Program.cs                  # Application entry point and endpoint registration
├── dotnet-web-api.csproj       # Project file with dependencies
├── dotnet-web-api.http         # HTTP request file for testing
├── appsettings.json            # Application configuration
├── appsettings.Development.json
└── Properties/
    └── launchSettings.json     # Development server configuration
```

**Recommended structure after exercises:**

```
dotnet-web-api/
├── Program.cs
├── Models/                     # Data models and entities
│   └── Todo.cs
├── DTOs/
│   ├── Requests/               # Request DTOs
│   │   └── CreateTodoRequest.cs
│   └── Responses/              # Response DTOs
│       └── TodoResponse.cs
├── Data/
│   └── AppDbContext.cs         # EF Core database context
├── Endpoints/                  # Endpoint route groups
│   ├── TodoEndpoints.cs
│   └── AuthEndpoints.cs
├── Validators/                 # FluentValidation validators
│   └── CreateTodoValidator.cs
└── Tests/
    └── dotnet-web-api.Tests/   # xUnit test project
        ├── TodoEndpointTests.cs
        └── Helpers/
            └── TestWebApplicationFactory.cs
```

## 🔧 Available Commands

```bash
dotnet restore          # Restore NuGet packages
dotnet build            # Build the project
dotnet run              # Run the application
dotnet test             # Run tests (after creating test project)
dotnet watch            # Run with hot reload
dotnet ef migrations add <Name>   # Add EF Core migration
dotnet ef database update         # Apply migrations
```

## 📖 API Endpoints

### Default (scaffolded)

- `GET /weatherforecast` — Sample weather data (replace during exercises)

### After Exercise 1 (Todo API)

- `GET /api/todos` — List all todos
- `GET /api/todos/{id}` — Get a specific todo
- `POST /api/todos` — Create a new todo
- `PUT /api/todos/{id}` — Update a todo
- `DELETE /api/todos/{id}` — Delete a todo

### After Exercise 4 (Auth)

- `POST /api/auth/login` — Authenticate and receive JWT token
- `POST /api/auth/register` — Register a new user

## 🧪 Testing Strategy

### Unit Tests

- Validation logic
- Service layer methods
- Mapping functions

### Integration Tests

- API endpoint testing with `WebApplicationFactory`
- Database operations with in-memory provider
- Authentication flows

### Example Test with Copilot

```csharp
// Prompt: "Create integration tests for the todo CRUD endpoints"
public class TodoEndpointTests : IClassFixture<WebApplicationFactory<Program>>
{
    // Copilot will generate the complete test class
}
```

## 🎓 Key .NET Minimal API Patterns

### 1. Typed Route Handlers

```csharp
// Create a typed handler for the GET /api/todos endpoint
// that returns a list of TodoResponse records
app.MapGet("/api/todos", (AppDbContext db) =>
{
    // Let Copilot implement the handler
});
```

### 2. Route Groups

```csharp
// Create a route group for /api/todos with OpenAPI tags
var todos = app.MapGroup("/api/todos")
    .WithTags("Todos");

// Let Copilot add endpoints to the group
```

### 3. Result Types

```csharp
// Return typed results with proper status codes
app.MapGet("/api/todos/{id}", Results<Ok<TodoResponse>, NotFound> (int id) =>
{
    // Let Copilot implement with TypedResults
});
```

### 4. Endpoint Filters

```csharp
// Create a validation filter for request DTOs
// that returns ProblemDetails on validation failure
public class ValidationFilter<T> : IEndpointFilter
{
    // Let Copilot implement the filter
}
```

## 🔗 Learning Resources

- [Minimal APIs Overview](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/minimal-apis/overview)
- [Entity Framework Core](https://learn.microsoft.com/en-us/ef/core/)
- [ASP.NET Core Authentication](https://learn.microsoft.com/en-us/aspnet/core/security/authentication/)
- [xUnit Documentation](https://xunit.net/docs/getting-started/netcore/cmdline)

## 🎯 Certification Tips

1. **Use descriptive comments** — Guide Copilot with clear intent before each code block
2. **Leverage records** — Use C# records for DTOs to get clean Copilot suggestions
3. **Start with signatures** — Write method signatures and let Copilot fill in the body
4. **Use extension methods** — Organize endpoint registrations in static extension methods
5. **Follow conventions** — Consistent patterns help Copilot produce better suggestions

## 📝 License

This project template is provided for educational purposes as part of GitHub Copilot certification preparation.
