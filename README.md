# First REST API – Spring Boot (Exercise 16, Task 2)

A REST API (backend only) for managing products, built with Spring Boot.
Exercise 16 – *First two Spring Framework apps*, Akademia Finansów i Biznesu Vistula.

## Technologies

- Java 21
- Spring Boot 4 (Spring Web, Spring Data JPA, Spring Boot DevTools)
- H2 in-memory database + H2 console
- Swagger UI / OpenAPI (springdoc-openapi 3.2.0)
- Maven

## How to run

1. Open the project in IntelliJ IDEA.
2. Wait for Maven to download the dependencies.
3. Run `FirstRestApiSpringApplication`.
4. The application starts on `http://localhost:8080`.

## Endpoints

| Method | URL | Description | Status |
| --- | --- | --- | --- |
| POST | `/api/v1/products` | Create a product | 201 Created |
| GET | `/api/v1/products/{id}` | Find a product by id | 200 OK / 404 Not Found |
| GET | `/api/v1/products` | Find all products | 200 OK |
| PUT | `/api/v1/products/{id}` | Update a product | 200 OK / 404 Not Found |
| DELETE | `/api/v1/products/{id}` | Delete a product | 204 No Content / 404 Not Found |

Example request body (POST / PUT):

```json
{
  "name": "Laptop"
}
```

Example error response (404):

```json
{
  "message": "Product with 99 not found"
}
```

## Useful links (while the app is running)

- Swagger UI: http://localhost:8080/swagger-ui/index.html
- OpenAPI docs (JSON): http://localhost:8080/v3/api-docs
- H2 console: http://localhost:8080/console
  - JDBC URL: `jdbc:h2:mem:testdb`
  - User: `sa`, password: empty

## Project structure

```
product
├── api            – ProductController (HTTP requests and responses)
│   ├── request    – ProductRequest, UpdateProductRequest
│   └── response   – ProductResponse
├── domain         – Product (JPA entity, table "products")
├── repository     – ProductRepository (extends JpaRepository)
├── service        – ProductService (business logic)
└── support        – ProductMapper, ProductExceptionSupplier, ProductExceptionAdvisor
    └── exception  – ProductNotFoundException
shared.api.response – ErrorMessageResponse
```

## Question from the exercise

**Why can `ProductService` use `save`, `findById`, `findAll` and `deleteById` when `ProductRepository` is empty?**
