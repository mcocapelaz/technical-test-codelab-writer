# Add a POST Endpoint to Create Products

## Introduction

Welcome to this hands-on codelab! In this tutorial, you'll learn how to add a POST endpoint to a Spring Boot REST API that allows users to create new products in a product catalog with proper validation and best practices.

### What you'll learn

- How to create a Data Transfer Object (DTO) with validation constraints
- How to implement service layer logic with proper data mapping
- How to create a POST endpoint in a Spring Boot REST Controller
- How to test your endpoint using curl or API testing tools
- Best practices for RESTful API design with proper HTTP status codes

### What you'll need

- Basic understanding of Java and Spring Boot
- The starter code with the existing GET endpoints
- A code editor (IntelliJ IDEA, VS Code, Eclipse, etc.)
- Java 17+ and Maven installed

### What you'll build

By the end of this codelab, you'll have a fully functional POST endpoint at `/products` that accepts validated JSON data and creates new products in your catalog.

---

## Step 1: Create the CreateProductRequest DTO

### Objective

Create a Data Transfer Object (DTO) with validation constraints to ensure data integrity.

### Instructions

Create a new file `src/main/java/com/example/codelab/dto/CreateProductRequest.java`:

```java
package com.example.codelab.dto;

import jakarta.validation.constraints.NotBlank;
import jakarta.validation.constraints.NotNull;
import jakarta.validation.constraints.Positive;
import jakarta.validation.constraints.PositiveOrZero;
import jakarta.validation.constraints.Size;
import lombok.AllArgsConstructor;
import lombok.Builder;
import lombok.Data;
import lombok.NoArgsConstructor;

/**
 * Data Transfer Object for creating a new product.
 * Contains validation constraints for input data.
 */
@Data
@Builder
@NoArgsConstructor
@AllArgsConstructor
public class CreateProductRequest {

    @NotBlank(message = "Product name is required")
    @Size(min = 1, max = 100, message = "Product name must be between 1 and 100 characters")
    private String name;

    @Size(max = 500, message = "Description cannot exceed 500 characters")
    private String description;

    @NotNull(message = "Price is required")
    @Positive(message = "Price must be a positive value")
    private Double price;

    @Size(max = 50, message = "Category cannot exceed 50 characters")
    private String category;

    @PositiveOrZero(message = "Stock cannot be negative")
    private Integer stock;
}
```

### Explanation

**Why use a DTO instead of the Product entity directly?**
- Separates API contracts from domain models
- Allows different validation rules for creation vs. entity itself
- Prevents exposing internal entity details (like generated IDs)

**Validation annotations:**
- `@NotBlank` - Ensures the field is not null, empty, or whitespace
- `@NotNull` - Ensures the field is not null
- `@Positive` - Ensures the number is greater than 0
- `@PositiveOrZero` - Allows 0 or positive values
- `@Size` - Limits string length

**Lombok annotations:**
- `@Data` - Generates getters, setters, toString, equals, and hashCode
- `@Builder` - Enables the builder pattern for object creation
- `@NoArgsConstructor` / `@AllArgsConstructor` - Generates constructors

### Expected outcome

You now have a validated request object that will automatically reject invalid data before it reaches your business logic.

---

## Step 2: Add the createProduct method to ProductService

### Objective

Implement the business logic to map the request DTO to a Product entity and save it.

### Instructions

Open `src/main/java/com/example/codelab/service/ProductService.java` and add the import and method:

**Add this import at the top:**

```java
import com.example.codelab.dto.CreateProductRequest;
```

**Add this method:**

```java
/**
 * Creates a new product from the request data.
 *
 * @param request the product creation request
 * @return the created product with generated ID
 */
public Product createProduct(CreateProductRequest request) {
    Product product = Product.builder()
        .name(request.getName())
        .description(request.getDescription())
        .price(request.getPrice())
        .category(request.getCategory())
        .stock(request.getStock() != null ? request.getStock() : 0)
        .build();
    
    return productRepository.save(product);
}
```

### Explanation

**The method flow:**
1. Receives a validated `CreateProductRequest`
2. Uses the Builder pattern to create a new `Product` entity
3. Maps each field from the request to the entity
4. Provides a default value of 0 for stock if not provided
5. Saves the product using the repository and returns it (with generated ID)

**Why separate mapping logic?**
- Keeps the controller thin and focused on HTTP concerns
- Makes the business logic testable independently
- Allows for future enhancements (e.g., additional validation, enrichment)

### Expected outcome

Your `ProductService` class should now have three methods:
- `getAllProducts()` - retrieves all products
- `getProductById(String id)` - retrieves a product by ID
- `createProduct(CreateProductRequest request)` - creates a new product ✅

---

## Step 3: Create the POST endpoint in ProductController

### Objective

Add a REST endpoint that handles HTTP POST requests with automatic validation.

### Instructions

Open `src/main/java/com/example/codelab/controller/ProductController.java` and add the necessary imports and method.

**Add these imports at the top:**

```java
import com.example.codelab.dto.CreateProductRequest;
import jakarta.validation.Valid;
import org.springframework.http.HttpStatus;
import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.RequestBody;
```

**Add this method below the existing GET endpoints:**

```java
/**
 * Creates a new product.
 *
 * @param request the product creation request
 * @return the created product with HTTP 201 status
 */
@PostMapping
@Operation(summary = "Create a new product", description = "Creates a new product in the catalog")
@ApiResponses(value = {
    @ApiResponse(responseCode = "201", description = "Product created successfully"),
    @ApiResponse(responseCode = "400", description = "Invalid request data")
})
public ResponseEntity<Product> createProduct(
    @Parameter(description = "Product creation data") 
    @Valid @RequestBody CreateProductRequest request) {
    
    Product createdProduct = productService.createProduct(request);
    return ResponseEntity.status(HttpStatus.CREATED).body(createdProduct);
}
```

### Explanation

**Key annotations:**
- `@PostMapping` - Maps HTTP POST requests to `/products`
- `@Valid` - Triggers validation of the `CreateProductRequest` based on its annotations
- `@RequestBody` - Converts the JSON request body into the DTO object
- `@Parameter` - Swagger annotation for API documentation

**HTTP status codes:**
- `HttpStatus.CREATED` (201) - Standard REST response for successful resource creation
- 400 (Bad Request) - Automatically returned by Spring if validation fails

**Validation flow:**
1. Spring receives the JSON request
2. Converts it to `CreateProductRequest`
3. `@Valid` triggers validation based on DTO annotations
4. If validation fails → returns 400 with error details
5. If validation passes → calls service layer

### Expected outcome

Your `ProductController` should now have three endpoints:
- `GET /products` - list all products
- `GET /products/{id}` - get a product by ID
- `POST /products` - create a new product ✅

---

## Step 4: Test the endpoint

### Objective

Verify that your POST endpoint works correctly and validates input properly.

### Instructions

#### Option 1: Using curl (Command Line)

**Test with valid data:**

```bash
curl -X POST http://localhost:8080/products \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Wireless Mouse",
    "description": "Ergonomic wireless mouse with USB receiver",
    "price": 29.99,
    "category": "Electronics",
    "stock": 50
  }'
```

**Test validation with invalid data (negative price):**

```bash
curl -X POST http://localhost:8080/products \
  -H "Content-Type: application/json" \
  -d '{
    "name": "Invalid Product",
    "price": -10.00,
    "category": "Test"
  }'
```

#### Option 2: Using Postman

1. Set method to **POST**
2. URL: `http://localhost:8080/products`
3. Headers tab:
   - Key: `Content-Type`
   - Value: `application/json`
4. Body tab → **raw** → paste:

```json
{
  "name": "Wireless Mouse",
  "description": "Ergonomic wireless mouse with USB receiver",
  "price": 29.99,
  "category": "Electronics",
  "stock": 50
}
```

5. Click **Send**

#### Option 3: Using Swagger UI

1. Start your application
2. Navigate to `http://localhost:8080/swagger-ui.html`
3. Find the POST `/products` endpoint
4. Click **Try it out**
5. Enter the product data and click **Execute**

### Expected outcomes

**Valid request response (201 Created):**

```json
{
  "id": "generated-uuid",
  "name": "Wireless Mouse",
  "description": "Ergonomic wireless mouse with USB receiver",
  "price": 29.99,
  "category": "Electronics",
  "stock": 50
}
```

**Invalid request response (400 Bad Request):**

```json
{
  "timestamp": "2026-02-10T12:00:00",
  "status": 400,
  "error": "Bad Request",
  "message": "Price must be a positive value"
}
```

### Verify the product was created

```bash
curl http://localhost:8080/products
```

You should see your new product in the list! 🎉

---

## Congratulations! 🎊

You've successfully implemented a production-ready POST endpoint with validation!

### What you learned

✅ How to create a DTO with Bean Validation annotations  
✅ How to implement proper data mapping in the service layer  
✅ How to use `@Valid` for automatic request validation  
✅ How to return proper HTTP status codes (201 Created, 400 Bad Request)  
✅ How to test your API using different tools  

### Key takeaways

**Separation of concerns:**
- Controller handles HTTP concerns
- Service handles business logic
- DTO handles data validation and API contracts

**Validation best practices:**
- Validate at the API boundary
- Provide clear error messages
- Use appropriate constraints for each field

### Next steps

To improve your endpoint further, consider:
- Adding custom exception handling with `@ControllerAdvice`
- Implementing unique constraint validation (e.g., duplicate product names)
- Adding pagination for the GET endpoints
- Writing unit and integration tests with JUnit and MockMvc
- Adding authentication and authorization with Spring Security



***

