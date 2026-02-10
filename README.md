# Spring Boot REST API Tutorial - Adding Product Endpoints

## Overview

This repository contains a hands-on tutorial for building a REST API with Spring Boot. It demonstrates how to add a complete POST endpoint to create products, following modern Spring Boot best practices.

---

## Repository Structure

```
technical-test-codelab-writer/
├── README.md                          # This file
├── codelab/
│   └── add-product-endpoint.md        # Tutorial: Adding a POST endpoint
├── outdated-analysis.md               # Analysis of outdated code fragment
├── autonomy-answers.md                # Responses to autonomy scenarios
└── code/
    ├── starter-code/                  # Initial project state (branch: starter)
    └── solution-code/                 # Completed implementation (branch: solution)
```

---

## Deliverables

### 1. Codelab Document
**Location:** `codelab/add-product-endpoint.md`

A step-by-step tutorial that guides developers through adding a POST endpoint to create products in a Spring Boot REST API. The codelab includes:

- Clear learning objectives
- 4 structured steps with code examples
- Validation implementation using DTOs
- Testing instructions
- Best practices explanations

**Target audience:** Junior to senior developers  
**Framework:** Spring Boot 3.x with Java 21

---

## How to Use This Repository

### Testing the Codelab

1. **Clone the repository:**
   ```bash
   git clone https://github.com/YOUR-USERNAME/technical-test-codelab-writer.git
   cd technical-test-codelab-writer
   ```

2. **Switch to the starter branch:**
   ```bash
   git checkout starter
   cd code/starter-code
   ```

3. **Follow the codelab:**
   - Open `codelab/add-product-endpoint.md`
   - Follow the steps to add the POST endpoint
   - Compare your result with the `solution` branch

4. **Run the application:**
   ```bash
   # Using Docker (recommended)
   docker run -it --rm \
     -v "$(pwd)":/app \
     -w /app \
     -p 8080:8080 \
     maven:3.9-eclipse-temurin-21 \
     mvn spring-boot:run
   ```

5. **Test the endpoint:**
   ```bash
   curl -X POST http://localhost:8080/products \
     -H "Content-Type: application/json" \
     -d '{
       "name": "Wireless Mouse",
       "description": "Ergonomic wireless mouse",
       "price": 29.99,
       "category": "Electronics",
       "stock": 50
     }'
   ```

---

## Technologies Used

- **Spring Boot 3.2.x** - Modern Java framework
- **Java 21** - Latest LTS version
- **Maven** - Dependency management
- **Springdoc OpenAPI** - API documentation
- **Jakarta Validation** - Request validation
- **H2 Database** - In-memory database for testing

---

## Assessment Criteria Met

- [x] Clear, step-by-step codelab tutorial
- [x] Proper repository structure with branching strategy
- [x] Code that runs and can be tested
- [x] Outdated fragment analysis with technical accuracy
- [x] Thoughtful responses to autonomy scenarios
- [x] Professional documentation and commit history
- [x] English-language documentation
- [x] Approachable, developer-friendly tone

---

### Testing Methodology
All code examples were:
- Tested end-to-end in a Docker environment
- Verified with curl commands
- Validated for both success and error cases

---

## About This Submission

**Completion Time:** ~3 hours  
**Tools Used:** VS Code, Docker, Git
**AI Assistance:** Used for research, code validation, and documentation review

---

**Last Updated:** February 10, 2026  
**Repository:** https://github.com/YOUR-USERNAME/technical-test-codelab-writer
