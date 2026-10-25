---
name: clean-architecture-dotnet
description: >-
  Architect and implement clean .NET 10 solutions using Service-Layer, Repository & Unit of Work patterns,
  Result Pattern, FluentValidation, and EF Core 10 conventions. Use for backend architecture tasks.
---

# Clean Architecture .NET 10 & Service-Layer Pattern

This skill guides the implementation of clean, maintainable, and high-performance .NET 10 backend solutions adhering strictly to Code Academy's Clean Architecture guidelines (Service Pattern without CQRS/MediatR complexity).

## 1. Solution Architecture & Layer Responsibilities
- **`KurSivLms.Domain`**: Core entities, value objects, domain enums, base entity (`BaseAuditableEntity`), interfaces for domain repositories. Zero external dependencies.
- **`KurSivLms.Application`**: Service interfaces (`ICourseService`, `IAuthService`, etc.), service implementations, strongly-typed DTOs, FluentValidation validators, mapping extensions, custom exceptions, Result pattern.
- **`KurSivLms.Infrastructure`**: External integrations (MailKit Gmail SMTP, QuestPDF generator, Gemini AI client, MediaPipe helpers, Token service).
- **`KurSivLms.Persistence`**: `ApplicationDbContext`, EF Core 10 Fluent API configurations, migrations, repository implementations, Unit of Work, database seeders.
- **`KurSivLms.WebAPI`**: ASP.NET Core REST API controllers, Scalar/Swagger OpenAPI specs, middlewares, SignalR hubs, JWT authentication.
- **`KurSivLms.AdminMVC`**: ASP.NET Core MVC controllers and Razor Views for back-office administration, course moderation, and reviewer queues.

## 2. Modern C# 14 & .NET 10 Standards
- **Primary Constructors**: Use primary constructors for dependency injection across services and controllers:
  ```csharp
  public class CourseService(ICourseRepository courseRepo, IUnitOfWork uow, ILogger<CourseService> logger) : ICourseService
  ```
- **Pattern Matching & Switch Expressions**: Clean type checking and state evaluation.
- **File-scoped Namespaces**: Single declaration at top of file without indentation.
- **Collection Expressions**: Use `[.. items]` instead of `new List<T>()`.
- **Global Exception Handling Middleware**: Intercept exceptions globally and return RFC 7807 `ProblemDetails`.

## 3. Result Pattern
Avoid throwing exceptions for anticipated business logic outcomes:
```csharp
public class Result<T>
{
    public bool IsSuccess { get; init; }
    public T? Value { get; init; }
    public string? ErrorMessage { get; init; }
    public static Result<T> Success(T value) => new() { IsSuccess = true, Value = value };
    public static Result<T> Failure(string error) => new() { IsSuccess = false, ErrorMessage = error };
}
```
