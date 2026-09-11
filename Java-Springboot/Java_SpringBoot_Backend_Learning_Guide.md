# Java + Spring Boot — Complete Beginner-to-Backend Developer Guide

A simple, practical guide to learning Java and Spring Boot by understanding concepts and building a real backend project.

> Goal: By the end of this guide, you should understand the core Java concepts, Spring Boot fundamentals, REST APIs, databases, JPA/Hibernate, validation, exception handling, and basic authentication well enough to build a small backend independently.

---

# PART 1 — JAVA FUNDAMENTALS

## 1. What is Java?

Java is a programming language widely used for backend applications, enterprise software, Android history, financial systems, APIs, and large-scale applications.

Java is popular because it is:

- Object-oriented
- Strongly typed
- Portable
- Mature
- Well supported
- Common in enterprise software
- Supported by a huge ecosystem

A simple Java program:

```java
public class Main {
    public static void main(String[] args) {
        System.out.println("Hello World");
    }
}
```

Output:

```text
Hello World
```

---

# 2. JDK, JRE, and JVM

These three terms confuse beginners.

## JVM

JVM means Java Virtual Machine.

It runs Java bytecode.

The idea is:

```text
Java code
   ↓
Compiler
   ↓
Bytecode
   ↓
JVM
   ↓
Operating System
```

This is one reason Java is considered portable.

## JRE

JRE means Java Runtime Environment.

It provides what is needed to run Java applications.

## JDK

JDK means Java Development Kit.

It includes tools needed to develop Java applications.

Simple way to remember:

```text
JDK = Develop Java
JRE = Run Java
JVM = Executes Java bytecode
```

For development, install the JDK.

---

# 3. Your First Java Project

A simple structure:

```text
my-java-project/
└── src/
    └── Main.java
```

Compile:

```bash
javac Main.java
```

Run:

```bash
java Main
```

In real projects, Maven or Gradle usually manages the build.

---

# 4. Variables

A variable stores data.

Example:

```java
String name = "Aditya";
int age = 22;
double salary = 350000;
boolean active = true;
```

Think of:

```java
int age = 22;
```

as:

```text
type     variable   value
 ↓          ↓         ↓
int        age       22
```

---

# 5. Java Data Types

## Primitive types

Common primitive types:

```text
byte
short
int
long
float
double
char
boolean
```

Examples:

```java
int age = 22;
long population = 1000000000L;
double price = 999.99;
char grade = 'A';
boolean available = true;
```

## String

String is not a primitive.

```java
String name = "Aditya";
```

---

# 6. int vs long

Use `int` for many normal integer values.

```java
int age = 25;
```

Use `long` when the number can be larger.

```java
long views = 5000000000L;
```

The `L` tells Java that the number is a long literal.

---

# 7. Operators

## Arithmetic

```java
int a = 10;
int b = 3;

System.out.println(a + b);
System.out.println(a - b);
System.out.println(a * b);
System.out.println(a / b);
System.out.println(a % b);
```

## Comparison

```java
a == b
a != b
a > b
a < b
a >= b
a <= b
```

## Logical

```java
&&   // AND
||   // OR
!    // NOT
```

Example:

```java
if (age >= 18 && active) {
    System.out.println("Allowed");
}
```

---

# 8. if / else

```java
int age = 20;

if (age >= 18) {
    System.out.println("Adult");
} else {
    System.out.println("Minor");
}
```

Multiple conditions:

```java
if (marks >= 90) {
    System.out.println("A");
} else if (marks >= 75) {
    System.out.println("B");
} else {
    System.out.println("C");
}
```

---

# 9. switch

Useful when comparing one value against several known cases.

```java
int day = 2;

switch (day) {
    case 1:
        System.out.println("Monday");
        break;

    case 2:
        System.out.println("Tuesday");
        break;

    default:
        System.out.println("Unknown");
}
```

Modern Java also supports enhanced switch syntax.

---

# 10. Loops

## for loop

```java
for (int i = 1; i <= 5; i++) {
    System.out.println(i);
}
```

Output:

```text
1
2
3
4
5
```

## while loop

```java
int i = 1;

while (i <= 5) {
    System.out.println(i);
    i++;
}
```

## for-each

```java
String[] names = {"A", "B", "C"};

for (String name : names) {
    System.out.println(name);
}
```

---

# 11. Methods

A method is a reusable block of code.

```java
public static int add(int a, int b) {
    return a + b;
}
```

Use it:

```java
int result = add(10, 20);
System.out.println(result);
```

Why methods?

Without methods:

```text
same code
same code
same code
same code
```

With methods:

```text
call add()
call add()
call add()
```

---

# 12. Parameters and Return Values

```java
public static String greet(String name) {
    return "Hello " + name;
}
```

Here:

- `String` before the method name = return type
- `name` = parameter
- `"Hello " + name` = returned value

A method returning nothing:

```java
public static void printName(String name) {
    System.out.println(name);
}
```

---

# 13. Arrays

An array stores multiple values of the same type.

```java
int[] numbers = {10, 20, 30, 40};
```

Access:

```java
System.out.println(numbers[0]);
```

Output:

```text
10
```

Indexes start at `0`.

---

# 14. String

Example:

```java
String name = "Aditya";

System.out.println(name.length());
System.out.println(name.toUpperCase());
System.out.println(name.toLowerCase());
```

String comparison:

Use:

```java
name.equals("Aditya")
```

Do not normally compare strings using:

```java
name == "Aditya"
```

`==` compares references, while `.equals()` compares content.

---

# 15. Object-Oriented Programming

Java is heavily based on object-oriented programming.

The four commonly taught pillars are:

1. Encapsulation
2. Inheritance
3. Polymorphism
4. Abstraction

Before these, understand classes and objects.

---

# 16. Class

A class is like a blueprint.

Example:

```java
public class User {
    String name;
    int age;
}
```

It describes what a User has.

---

# 17. Object

An object is an actual instance of a class.

```java
User user = new User();

user.name = "Aditya";
user.age = 22;
```

Think:

```text
Class = blueprint
Object = actual thing created from blueprint
```

---

# 18. Constructor

A constructor runs when an object is created.

```java
public class User {

    String name;
    int age;

    public User(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
```

Create:

```java
User user = new User("Aditya", 22);
```

`this.name` refers to the object's field.

---

# 19. Encapsulation

Encapsulation means controlling access to an object's internal data.

Instead of:

```java
public String password;
```

prefer:

```java
private String password;
```

Then provide controlled methods.

```java
public String getPassword() {
    return password;
}

public void setPassword(String password) {
    this.password = password;
}
```

In real applications, you generally should not expose passwords through APIs at all.

---

# 20. Access Modifiers

Common access modifiers:

```text
public
private
protected
default
```

### public

Accessible broadly.

```java
public class User {}
```

### private

Accessible only inside the class.

```java
private String email;
```

### protected

Accessible in the class and related subclasses/packages according to Java's access rules.

---

# 21. Inheritance

Inheritance lets one class derive from another.

```java
class Animal {
    public void eat() {
        System.out.println("Eating");
    }
}

class Dog extends Animal {
    public void bark() {
        System.out.println("Barking");
    }
}
```

Now:

```java
Dog dog = new Dog();

dog.eat();
dog.bark();
```

---

# 22. Polymorphism

Polymorphism means one interface/type can represent different implementations.

Example:

```java
Animal animal = new Dog();
```

If `Dog` overrides a method:

```java
class Animal {
    public void sound() {
        System.out.println("Animal sound");
    }
}

class Dog extends Animal {
    @Override
    public void sound() {
        System.out.println("Bark");
    }
}
```

Then:

```java
Animal animal = new Dog();
animal.sound();
```

Output:

```text
Bark
```

---

# 23. Abstraction

Abstraction means exposing what something does while hiding unnecessary implementation details.

Example interface:

```java
interface PaymentService {
    void pay(double amount);
}
```

Implementation:

```java
class CardPayment implements PaymentService {

    @Override
    public void pay(double amount) {
        System.out.println("Paid using card");
    }
}
```

The caller only needs to know that `pay()` exists.

---

# 24. Interfaces

An interface defines a contract.

```java
public interface UserService {
    User findUser(Long id);
}
```

Implementation:

```java
public class UserServiceImpl implements UserService {

    @Override
    public User findUser(Long id) {
        // implementation
        return null;
    }
}
```

Spring uses interfaces frequently, especially when designing service layers.

---

# 25. Abstract Classes

Example:

```java
abstract class Animal {

    abstract void sound();

    void eat() {
        System.out.println("Eating");
    }
}
```

An abstract class can contain both abstract and implemented methods.

---

# 26. Collections

Collections are extremely important for backend development.

The most important ones:

```text
List
Set
Map
Queue
```

---

# 27. ArrayList

A `List` keeps elements in order and can contain duplicates.

```java
List<String> names = new ArrayList<>();

names.add("Aditya");
names.add("Rahul");
names.add("Amit");

System.out.println(names);
```

Access:

```java
names.get(0);
```

---

# 28. HashSet

A Set generally stores unique values.

```java
Set<String> emails = new HashSet<>();

emails.add("a@example.com");
emails.add("a@example.com");

System.out.println(emails.size());
```

The duplicate is not stored as another set element.

---

# 29. HashMap

A Map stores key-value pairs.

```java
Map<Long, String> users = new HashMap<>();

users.put(1L, "Aditya");
users.put(2L, "Rahul");
```

Get:

```java
String name = users.get(1L);
```

Think:

```text
ID     NAME
1      Aditya
2      Rahul
```

Maps are very common in backend code.

---

# 30. Generics

Generics make collections type-safe.

```java
List<String> names = new ArrayList<>();
```

This means the list should contain Strings.

Another example:

```java
List<User> users = new ArrayList<>();
```

---

# 31. Exceptions

An exception is a problem that occurs while a program runs.

Example:

```java
int result = 10 / 0;
```

This causes an exception.

Handle it:

```java
try {
    int result = 10 / 0;
} catch (ArithmeticException e) {
    System.out.println("Cannot divide by zero");
}
```

---

# 32. Checked and Unchecked Exceptions

Java has different exception categories.

Common unchecked exceptions:

```text
NullPointerException
IllegalArgumentException
IndexOutOfBoundsException
```

Checked exceptions must be handled or declared.

You should understand the distinction, but don't overuse exceptions for normal control flow.

---

# 33. Optional

`Optional` can represent a value that may or may not exist.

Example:

```java
Optional<User> user = userRepository.findById(id);
```

Instead of blindly assuming a user exists:

```java
User user = userRepository.findById(id).get();
```

you can handle absence explicitly.

Example:

```java
return userRepository.findById(id)
        .orElseThrow(() -> new RuntimeException("User not found"));
```

---

# 34. Lambdas

Lambda expressions make Java code more concise.

Traditional:

```java
numbers.forEach(new Consumer<Integer>() {
    @Override
    public void accept(Integer number) {
        System.out.println(number);
    }
});
```

Lambda:

```java
numbers.forEach(number -> System.out.println(number));
```

---

# 35. Streams

Streams are useful for processing collections.

Example:

```java
List<Integer> numbers = List.of(1, 2, 3, 4, 5);

List<Integer> evenNumbers = numbers.stream()
        .filter(n -> n % 2 == 0)
        .toList();
```

Result:

```text
2, 4
```

Common operations:

```text
filter
map
sorted
distinct
limit
collect / toList
forEach
```

Example:

```java
List<String> names = List.of("Aditya", "Rahul", "Amit");

List<String> result = names.stream()
        .filter(name -> name.startsWith("A"))
        .toList();
```

---

# 36. Maven

Maven is a build and dependency management tool.

Spring Boot projects commonly use Maven.

The main file is:

```text
pom.xml
```

Dependencies are added there.

Example:

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>
```

Maven can:

- Download dependencies
- Compile code
- Run tests
- Package applications

Common commands:

```bash
mvn clean
mvn test
mvn package
```

With the Maven Wrapper:

```bash
./mvnw test
```

On Windows:

```bash
mvnw.cmd test
```

---

# PART 2 — SPRING AND SPRING BOOT

# 37. What is Spring?

Spring is a Java framework/ecosystem for building applications.

It provides tools for:

- Dependency Injection
- Web applications
- Database access
- Security
- Configuration
- Testing
- Transactions
- More

---

# 38. What is Spring Boot?

Spring Boot makes Spring applications easier to create and run.

Without Spring Boot, configuration can be more complicated.

Spring Boot provides:

- Auto-configuration
- Starter dependencies
- Embedded web server
- Production-oriented features
- Easy application setup

Typical backend:

```text
React
  |
  | HTTP
  v
Spring Boot
  |
  v
PostgreSQL
```

---

# 39. Creating a Spring Boot Project

A common way is Spring Initializr.

Select:

- Java
- Maven
- Spring Boot version
- Project name
- Packaging: Jar
- Java version

Common dependencies:

```text
Spring Web
Spring Data JPA
Validation
PostgreSQL Driver
Spring Security
```

You don't need all of them on day one.

Start with:

```text
Spring Web
```

Then add database dependencies when you're ready.

---

# 40. Spring Boot Project Structure

A common structure:

```text
src/
└── main/
    ├── java/
    │   └── com.example.shop/
    │       ├── ShopApplication.java
    │       ├── controller/
    │       ├── service/
    │       ├── repository/
    │       ├── entity/
    │       ├── dto/
    │       └── exception/
    │
    └── resources/
        └── application.properties
```

---

# 41. Main Application Class

Example:

```java
@SpringBootApplication
public class ShopApplication {

    public static void main(String[] args) {
        SpringApplication.run(ShopApplication.class, args);
    }
}
```

`@SpringBootApplication` is a key Spring Boot annotation.

It combines several important configuration behaviors, including component scanning and auto-configuration.

---

# 42. What is a Bean?

A Bean is an object managed by Spring.

Instead of manually doing:

```java
UserService service = new UserService();
```

Spring can create and manage it.

This enables dependency injection.

---

# 43. Dependency Injection

Suppose:

```text
Controller needs Service
Service needs Repository
Repository talks to Database
```

Spring can create and connect these objects.

Example:

```java
@Service
public class UserService {

}
```

Then:

```java
@RestController
public class UserController {

    private final UserService userService;

    public UserController(UserService userService) {
        this.userService = userService;
    }
}
```

Spring injects `UserService`.

This is called Dependency Injection.

---

# 44. Why Dependency Injection?

Without DI:

```java
UserService service = new UserService();
```

Your class creates its own dependencies.

With DI:

```java
public UserController(UserService service) {
    this.service = service;
}
```

Spring provides the dependency.

Benefits:

- Loose coupling
- Easier testing
- Better organization
- Easier replacement of implementations

Prefer constructor injection.

---

# 45. Common Spring Annotations

Important annotations:

```text
@SpringBootApplication
@RestController
@RequestMapping
@GetMapping
@PostMapping
@PutMapping
@PatchMapping
@DeleteMapping
@Service
@Repository
@Entity
@Id
@GeneratedValue
@Autowired
@Configuration
@Bean
```

You don't need to memorize them all immediately.

Understand what they do.

---

# 46. REST APIs

REST APIs allow applications to communicate over HTTP.

Example:

```text
React frontend
     |
     | GET /api/products
     v
Spring Boot
     |
     v
Database
```

---

# 47. HTTP Methods

Common methods:

```text
GET       Read
POST      Create
PUT       Replace/update
PATCH     Partial update
DELETE    Delete
```

Example:

```text
GET    /api/products
POST   /api/products
GET    /api/products/10
PATCH  /api/products/10
DELETE /api/products/10
```

---

# 48. Your First Controller

```java
@RestController
@RequestMapping("/api/hello")
public class HelloController {

    @GetMapping
    public String hello() {
        return "Hello from Spring Boot";
    }
}
```

Run the application.

Visit:

```text
GET http://localhost:8080/api/hello
```

Response:

```text
Hello from Spring Boot
```

---

# 49. Path Variables

Example:

```java
@GetMapping("/users/{id}")
public String getUser(@PathVariable Long id) {
    return "User ID: " + id;
}
```

Request:

```text
GET /api/users/10
```

Response:

```text
User ID: 10
```

---

# 50. Query Parameters

Example:

```java
@GetMapping("/products")
public String search(@RequestParam String name) {
    return "Searching for " + name;
}
```

Request:

```text
GET /api/products?name=phone
```

---

# 51. Request Body

For POST requests, data is commonly sent as JSON.

Example JSON:

```json
{
  "name": "Keyboard",
  "price": 1499
}
```

Controller:

```java
@PostMapping("/products")
public Product createProduct(@RequestBody Product product) {
    return product;
}
```

---

# 52. HTTP Status Codes

Common status codes:

```text
200 OK
201 Created
204 No Content
400 Bad Request
401 Unauthorized
403 Forbidden
404 Not Found
409 Conflict
500 Internal Server Error
```

Example:

If a product doesn't exist:

```text
404 Not Found
```

Don't return `200 OK` for every situation.

---

# 53. ResponseEntity

`ResponseEntity` lets you control the response status and body.

Example:

```java
return ResponseEntity
        .status(HttpStatus.CREATED)
        .body(product);
```

Another:

```java
return ResponseEntity.notFound().build();
```

---

# PART 3 — DATABASES

# 54. What is SQL?

SQL is used to work with relational databases.

Examples:

```sql
SELECT * FROM products;

INSERT INTO products (name, price)
VALUES ('Keyboard', 1499);

UPDATE products
SET price = 1299
WHERE id = 1;

DELETE FROM products
WHERE id = 1;
```

---

# 55. PostgreSQL

PostgreSQL is a relational database.

A database might contain:

```text
users
products
categories
orders
order_items
```

Example product table:

```text
id | name      | price
---+-----------+------
1  | Keyboard  | 1499
2  | Mouse     | 799
```

---

# 56. Primary Key

A primary key uniquely identifies a row.

Example:

```text
id = 1
```

Two products should not have the same primary key.

---

# 57. Foreign Key

A foreign key connects tables.

Example:

```text
products
---------
id
name
category_id
```

`category_id` can reference:

```text
categories.id
```

---

# 58. Relationships

Common relationships:

```text
One-to-One
One-to-Many
Many-to-One
Many-to-Many
```

Example:

```text
Category
   |
   +---- Product
   +---- Product
   +---- Product
```

One category has many products.

---

# PART 4 — JPA AND HIBERNATE

# 59. What is JPA?

JPA is a Java standard for object-relational mapping.

It lets you work with database records through Java objects.

Instead of manually writing SQL for every operation, you can define entities and repositories.

---

# 60. What is Hibernate?

Hibernate is a popular implementation of JPA.

Simple distinction:

```text
JPA = specification
Hibernate = implementation
Spring Data JPA = Spring's convenient data-access layer built around JPA
```

---

# 61. Entity

An entity is a Java class mapped to a database table.

Example:

```java
@Entity
public class Product {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String name;

    private BigDecimal price;
}
```

This can represent a `products` table.

---

# 62. Why BigDecimal for Money?

For financial values, prefer `BigDecimal` instead of `double`.

Avoid:

```java
double price = 19.99;
```

Prefer:

```java
BigDecimal price = new BigDecimal("19.99");
```

This avoids many floating-point precision problems.

---

# 63. Repository

Spring Data JPA lets you create repositories.

Example:

```java
public interface ProductRepository
        extends JpaRepository<Product, Long> {

}
```

Now you get methods such as:

```java
findAll()
findById()
save()
deleteById()
existsById()
```

without writing their basic SQL yourself.

---

# 64. Service Layer

Business logic should generally live in a service.

Example:

```java
@Service
public class ProductService {

    private final ProductRepository repository;

    public ProductService(ProductRepository repository) {
        this.repository = repository;
    }

    public Product create(Product product) {
        return repository.save(product);
    }

    public List<Product> getAll() {
        return repository.findAll();
    }
}
```

---

# 65. Controller-Service-Repository Architecture

A common structure:

```text
Controller
    |
    v
Service
    |
    v
Repository
    |
    v
Database
```

Controller:
Handles HTTP requests.

Service:
Contains business logic.

Repository:
Handles data access.

Database:
Stores data.

This separation makes applications easier to maintain.

---

# 66. DTOs

DTO means Data Transfer Object.

Don't always expose your entity directly through the API.

Example request DTO:

```java
public class CreateProductRequest {

    private String name;
    private BigDecimal price;
}
```

Why use DTOs?

Because your database model and API model don't necessarily need to be identical.

DTOs help with:

- Validation
- Security
- API design
- Hiding internal fields
- Versioning

---

# 67. Validation

Spring supports validation using annotations.

Example:

```java
public class CreateProductRequest {

    @NotBlank
    private String name;

    @NotNull
    @Positive
    private BigDecimal price;
}
```

Controller:

```java
@PostMapping
public Product create(
        @Valid @RequestBody CreateProductRequest request) {
    ...
}
```

Common validation annotations:

```text
@NotNull
@NotBlank
@NotEmpty
@Size
@Min
@Max
@Positive
@Email
@Pattern
```

---

# 68. Exception Handling

Don't return ugly stack traces to API users.

You can create a custom exception:

```java
public class ProductNotFoundException
        extends RuntimeException {

    public ProductNotFoundException(Long id) {
        super("Product not found: " + id);
    }
}
```

Then handle it globally.

Example:

```java
@RestControllerAdvice
public class GlobalExceptionHandler {

    @ExceptionHandler(ProductNotFoundException.class)
    public ResponseEntity<String> handle(
            ProductNotFoundException ex) {

        return ResponseEntity
                .status(HttpStatus.NOT_FOUND)
                .body(ex.getMessage());
    }
}
```

---

# 69. Transactions

A transaction groups database operations into one logical unit.

Example:

An order creation might do:

```text
Create order
    +
Create order items
    +
Reduce inventory
```

If inventory update fails, you may want the entire operation rolled back.

Spring provides:

```java
@Transactional
```

Example:

```java
@Transactional
public void placeOrder(...) {
    // database operations
}
```

---

# 70. Pagination

Suppose your store has 100,000 products.

Don't return all of them at once.

Instead:

```text
GET /api/products?page=0&size=20
```

Return 20 products.

Pagination improves:

- Performance
- Network usage
- Response size
- User experience

Spring Data provides pagination support using `Pageable` and `Page`.

---

# 71. Sorting

Example:

```text
GET /api/products?sort=price,asc
```

or:

```text
GET /api/products?sort=name,desc
```

Your API can support sorting through Spring Data.

---

# PART 5 — SPRING SECURITY

# 72. Authentication vs Authorization

Authentication:

> Who are you?

Authorization:

> What are you allowed to do?

Example:

```text
Login
 ↓
Authentication

Admin-only delete product
 ↓
Authorization
```

---

# 73. Password Hashing

Never store passwords like:

```text
password123
```

Use password hashing.

Spring Security commonly works with password encoders such as BCrypt.

Concept:

```text
User password
    ↓
Hashing
    ↓
Stored hash
```

During login, the entered password is checked against the stored hash.

---

# 74. JWT

JWT means JSON Web Token.

A common flow:

```text
User
 |
 | username + password
 v
POST /auth/login
 |
 v
Spring Security
 |
 | valid
 v
JWT token
 |
 v
Client stores/handles token
 |
 | Authorization: Bearer TOKEN
 v
Protected API
```

Example header:

```text
Authorization: Bearer eyJ...
```

The exact token handling strategy should follow your application's security requirements.

---

# 75. Roles

Example roles:

```text
USER
ADMIN
```

A normal user might:

```text
GET products
POST orders
GET own orders
```

An admin might:

```text
POST products
PATCH products
DELETE products
GET all orders
```

Authorization should be enforced by the backend, not just hidden in the React UI.

---

# PART 6 — TESTING

# 76. Why Testing?

Testing helps make sure your code works.

Types:

```text
Unit tests
Integration tests
Controller/API tests
End-to-end tests
```

---

# 77. JUnit

JUnit is commonly used for Java testing.

Example:

```java
@Test
void addShouldReturnCorrectValue() {
    int result = calculator.add(2, 3);

    assertEquals(5, result);
}
```

---

# 78. Mockito

Mockito helps create mock dependencies.

Example concept:

```text
ProductService
     |
     v
ProductRepository
```

For a unit test, you can mock the repository instead of using a real database.

---

# PART 7 — DEVELOPMENT TOOLS

# 79. Postman

Postman can test APIs.

Example:

```text
POST http://localhost:8080/api/products
```

Body:

```json
{
  "name": "Keyboard",
  "price": 1499
}
```

You can inspect the response without building the React frontend first.

---

# 80. Swagger / OpenAPI

Swagger/OpenAPI can document APIs.

A backend might expose documentation showing:

```text
GET /api/products
POST /api/products
GET /api/products/{id}
PATCH /api/products/{id}
DELETE /api/products/{id}
```

It is very useful for frontend-backend integration.

---

# 81. application.properties

Spring Boot configuration commonly lives in:

```text
src/main/resources/application.properties
```

Example:

```properties
spring.application.name=shop-api

server.port=8080

spring.datasource.url=jdbc:postgresql://localhost:5432/shop
spring.datasource.username=postgres
spring.datasource.password=your_password
```

Do not commit real production passwords.

For serious applications, use environment variables and secure secret management.

---

# 82. Environment Variables

Instead of:

```properties
spring.datasource.password=myPassword
```

use an environment variable.

Conceptually:

```properties
spring.datasource.password=${DB_PASSWORD}
```

Then set:

```text
DB_PASSWORD=your-secret
```

This keeps secrets out of source control.

---

# 83. Profiles

Spring profiles let you use different configuration for different environments.

Example:

```text
application.properties
application-dev.properties
application-test.properties
application-prod.properties
```

Typical environments:

```text
development
testing
production
```

---

# PART 8 — DOCKER

# 84. What is Docker?

Docker packages an application and its environment into containers.

Without Docker:

```text
"Works on my computer."
```

With Docker:

```text
Application
+
Dependencies
+
Configuration
=
Container
```

---

# 85. Docker Compose

For local development, you might run:

```text
Spring Boot
    |
    +---- PostgreSQL
    |
    +---- Redis
```

Docker Compose can start these services together.

Example conceptual `docker-compose.yml`:

```yaml
services:

  postgres:
    image: postgres
    environment:
      POSTGRES_DB: shop
      POSTGRES_USER: postgres
      POSTGRES_PASSWORD: password
    ports:
      - "5432:5432"
```

For real projects, don't use weak/default passwords in production.

---

# PART 9 — BACKEND ARCHITECTURE

# 86. A Typical Spring Boot Backend

A clean beginner-friendly architecture:

```text
src/main/java/com/example/shop

├── controller
│   ├── ProductController
│   └── AuthController
│
├── service
│   ├── ProductService
│   └── AuthService
│
├── repository
│   ├── ProductRepository
│   └── UserRepository
│
├── entity
│   ├── Product
│   └── User
│
├── dto
│   ├── CreateProductRequest
│   └── LoginRequest
│
├── exception
│   └── GlobalExceptionHandler
│
└── config
    └── SecurityConfig
```

---

# 87. Request Flow

Suppose React sends:

```text
POST /api/products
```

with:

```json
{
  "name": "Keyboard",
  "price": 1499
}
```

Flow:

```text
React
  |
  v
ProductController
  |
  v
ProductService
  |
  v
ProductRepository
  |
  v
PostgreSQL
```

Response travels back:

```text
PostgreSQL
   ↓
Repository
   ↓
Service
   ↓
Controller
   ↓
React
```

---

# 88. Why Not Put Everything in Controller?

Bad:

```java
@PostMapping
public Product create(Product product) {

    // validation

    // business logic

    // calculations

    // database code

    // email

    // everything
}
```

This becomes difficult to maintain.

Better:

```text
Controller
    ↓
Service
    ↓
Repository
```

Each layer has a responsibility.

---

# PART 10 — BUILDING A SMALL PROJECT

# 89. Practice Project: Task Manager API

We will build a small backend called:

**Task Manager API**

The application allows users to create and manage tasks.

This project is intentionally smaller than a full e-commerce system so you can finish it.

---

# 90. Project Requirements

Technologies:

```text
Java
Spring Boot
Maven
Spring Web
Spring Data JPA
PostgreSQL
Validation
JUnit
Postman
```

Optional later:

```text
Spring Security
JWT
Docker
Swagger
```

---

# 91. Features

The API should support:

```text
Create task
Get all tasks
Get task by ID
Update task
Delete task
Mark task completed
Search tasks
Filter tasks
Pagination
Validation
Proper error responses
```

---

# 92. Task Model

Each task contains:

```text
id
title
description
completed
priority
createdAt
updatedAt
```

Example:

```json
{
  "id": 1,
  "title": "Learn Spring Boot",
  "description": "Build my first REST API",
  "completed": false,
  "priority": "HIGH"
}
```

---

# 93. Task Entity

Create:

```text
entity/Task.java
```

Example:

```java
@Entity
public class Task {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    private String title;

    private String description;

    private boolean completed;

    @Enumerated(EnumType.STRING)
    private Priority priority;

    // getters and setters
}
```

Enum:

```java
public enum Priority {
    LOW,
    MEDIUM,
    HIGH
}
```

---

# 94. Repository

Create:

```text
repository/TaskRepository.java
```

Example:

```java
public interface TaskRepository
        extends JpaRepository<Task, Long> {

}
```

---

# 95. DTO

Create:

```text
dto/CreateTaskRequest.java
```

Example:

```java
public class CreateTaskRequest {

    @NotBlank
    private String title;

    private String description;

    @NotNull
    private Priority priority;
}
```

---

# 96. Service

Create:

```text
service/TaskService.java
```

Example:

```java
@Service
public class TaskService {

    private final TaskRepository repository;

    public TaskService(TaskRepository repository) {
        this.repository = repository;
    }

    public Task create(Task task) {
        return repository.save(task);
    }

    public List<Task> getAll() {
        return repository.findAll();
    }

    public Task getById(Long id) {
        return repository.findById(id)
                .orElseThrow(() ->
                    new RuntimeException("Task not found"));
    }

    public void delete(Long id) {
        repository.deleteById(id);
    }
}
```

This is a starting point. Improve it as you learn.

---

# 97. Controller

Create:

```text
controller/TaskController.java
```

Example:

```java
@RestController
@RequestMapping("/api/tasks")
public class TaskController {

    private final TaskService service;

    public TaskController(TaskService service) {
        this.service = service;
    }

    @GetMapping
    public List<Task> getAll() {
        return service.getAll();
    }

    @GetMapping("/{id}")
    public Task getById(@PathVariable Long id) {
        return service.getById(id);
    }

    @PostMapping
    public Task create(@RequestBody Task task) {
        return service.create(task);
    }

    @DeleteMapping("/{id}")
    public ResponseEntity<Void> delete(
            @PathVariable Long id) {

        service.delete(id);

        return ResponseEntity.noContent().build();
    }
}
```

---

# 98. API Endpoints

Your first version should have:

```text
GET    /api/tasks
GET    /api/tasks/{id}
POST   /api/tasks
PUT    /api/tasks/{id}
DELETE /api/tasks/{id}
PATCH  /api/tasks/{id}/complete
```

---

# 99. Test the API

Create task:

```text
POST /api/tasks
```

JSON:

```json
{
  "title": "Learn Java",
  "description": "Study OOP and collections",
  "priority": "HIGH"
}
```

Get all:

```text
GET /api/tasks
```

Get one:

```text
GET /api/tasks/1
```

Delete:

```text
DELETE /api/tasks/1
```

---

# 100. Add Validation

Improve the request:

```java
public class CreateTaskRequest {

    @NotBlank(message = "Title is required")
    @Size(max = 100)
    private String title;

    @Size(max = 500)
    private String description;

    @NotNull
    private Priority priority;
}
```

Controller:

```java
@PostMapping
public Task create(
        @Valid @RequestBody CreateTaskRequest request) {

    return service.create(request);
}
```

---

# 101. Add Not-Found Handling

Create:

```text
exception/TaskNotFoundException.java
```

```java
public class TaskNotFoundException
        extends RuntimeException {

    public TaskNotFoundException(Long id) {
        super("Task with id " + id + " not found");
    }
}
```

Then:

```java
@RestControllerAdvice
public class GlobalExceptionHandler {

    @ExceptionHandler(TaskNotFoundException.class)
    public ResponseEntity<?> handle(
            TaskNotFoundException ex) {

        return ResponseEntity
                .status(HttpStatus.NOT_FOUND)
                .body(Map.of(
                    "error", ex.getMessage()
                ));
    }
}
```

---

# 102. Add Search

Add an endpoint:

```text
GET /api/tasks/search?title=java
```

Repository:

```java
List<Task> findByTitleContainingIgnoreCase(String title);
```

Service:

```java
public List<Task> search(String title) {
    return repository.findByTitleContainingIgnoreCase(title);
}
```

Controller:

```java
@GetMapping("/search")
public List<Task> search(
        @RequestParam String title) {

    return service.search(title);
}
```

---

# 103. Add Filtering

Example:

```text
GET /api/tasks?priority=HIGH
```

You can create a repository method such as:

```java
List<Task> findByPriority(Priority priority);
```

Later, you can combine filters using Specifications or other query techniques.

---

# 104. Add Pagination

Example:

```text
GET /api/tasks?page=0&size=10
```

Service:

```java
public Page<Task> getTasks(Pageable pageable) {
    return repository.findAll(pageable);
}
```

Controller:

```java
@GetMapping
public Page<Task> getTasks(Pageable pageable) {
    return service.getTasks(pageable);
}
```

---

# 105. Add Authentication — Advanced Step

After the CRUD version works, add:

```text
User registration
User login
Password hashing
JWT
Authentication
Roles
```

Then tasks can belong to users:

```text
User
 |
 +---- Task
 +---- Task
 +---- Task
```

A user should only be able to access their own tasks.

This teaches an important real-world backend concept: authorization at the data level.

---

# 106. Add Docker

Once the application works locally, containerize:

```text
Spring Boot API
PostgreSQL
```

Use Docker Compose for local development.

Later you can add:

```text
Redis
```

---

# 107. Add Testing

Write tests for:

```text
Create task
Get task
Task not found
Update task
Delete task
Validation
Search
Authorization
```

Aim to test business behavior, not just lines of code.

---

# 108. Suggested Final Project Structure

```text
task-manager-api/
│
├── src/
│   ├── main/
│   │   ├── java/
│   │   │   └── com.example.taskmanager/
│   │   │       │
│   │   │       ├── TaskManagerApplication.java
│   │   │       │
│   │   │       ├── controller/
│   │   │       │   ├── TaskController.java
│   │   │       │   └── AuthController.java
│   │   │       │
│   │   │       ├── service/
│   │   │       │   ├── TaskService.java
│   │   │       │   └── AuthService.java
│   │   │       │
│   │   │       ├── repository/
│   │   │       │   ├── TaskRepository.java
│   │   │       │   └── UserRepository.java
│   │   │       │
│   │   │       ├── entity/
│   │   │       │   ├── Task.java
│   │   │       │   └── User.java
│   │   │       │
│   │   │       ├── dto/
│   │   │       │   ├── CreateTaskRequest.java
│   │   │       │   └── LoginRequest.java
│   │   │       │
│   │   │       ├── exception/
│   │   │       │   └── GlobalExceptionHandler.java
│   │   │       │
│   │   │       └── config/
│   │   │           └── SecurityConfig.java
│   │   │
│   │   └── resources/
│   │       └── application.properties
│   │
├── pom.xml
├── README.md
├── .gitignore
└── docker-compose.yml
```

---

# 109. Backend Skills You Should Eventually Know

After this project, continue with:

```text
Java
 ├── OOP
 ├── Collections
 ├── Generics
 ├── Streams
 ├── Exceptions
 ├── Multithreading
 └── JVM basics

Spring Boot
 ├── REST
 ├── Dependency Injection
 ├── Configuration
 ├── Validation
 ├── Exception Handling
 ├── Transactions
 ├── Spring Data JPA
 └── Spring Security

Database
 ├── SQL
 ├── PostgreSQL
 ├── Joins
 ├── Indexes
 ├── Transactions
 └── Query optimization

Engineering
 ├── Git
 ├── Testing
 ├── Docker
 ├── Logging
 ├── API documentation
 └── CI/CD

Advanced
 ├── Redis
 ├── Kafka
 ├── Microservices
 ├── AWS
 └── System Design
```

---

# 110. What You Should NOT Do

Don't try to learn all of this simultaneously.

Bad approach:

```text
Java
Spring
Spring Boot
AWS
Kafka
Docker
Redis
Microservices
Kubernetes
all at once
```

Better:

```text
Core Java
   ↓
Spring Boot
   ↓
REST API
   ↓
PostgreSQL
   ↓
JPA
   ↓
Validation + Exceptions
   ↓
Security
   ↓
Testing
   ↓
Docker
   ↓
Redis / Kafka
   ↓
AWS
   ↓
System Design
```

---

# 111. Recommended Learning Method

For every concept:

## Step 1 — Understand

Ask:

> What problem does this solve?

## Step 2 — Write a tiny example

Don't copy a 500-line project.

Write 10–30 lines.

## Step 3 — Break it

Change something intentionally.

See what happens.

## Step 4 — Use it in the project

For example:

Learn:

```text
Dependency Injection
```

Then use it in:

```text
TaskController
TaskService
TaskRepository
```

This makes the concept stick.

---

# 112. Your First Milestone

Don't move to advanced topics until you can build this without blindly copying:

```text
POST /api/tasks
GET /api/tasks
GET /api/tasks/{id}
PUT /api/tasks/{id}
DELETE /api/tasks/{id}
```

with:

```text
Java
Spring Boot
PostgreSQL
JPA
DTOs
Validation
Exception handling
```

Once you can do that, you have the foundation for real backend development.

---

# 113. Final Challenge

After completing the basic Task Manager API, add these features yourself:

### Level 1

- Create task
- Update task
- Delete task
- Get task
- Get all tasks

### Level 2

- Search
- Filtering
- Sorting
- Pagination
- Validation
- Global exception handling

### Level 3

- User registration
- Login
- BCrypt password hashing
- JWT authentication
- User roles
- User-owned tasks

### Level 4

- Unit tests
- Integration tests
- Swagger/OpenAPI
- Docker
- PostgreSQL Docker container
- CI pipeline

### Level 5

Add:

```text
Redis caching
Kafka events
AWS deployment
Logging/monitoring
```

---

# 114. The Big Picture

Eventually your backend should look like:

```text
                    React
                      |
                      | HTTP/JSON
                      v
             Spring Boot API
                      |
          +-----------+-----------+
          |           |           |
          v           v           v
      Security     Services    Validation
                      |
                      v
                 Repositories
                      |
             +--------+--------+
             |                 |
             v                 v
        PostgreSQL           Redis
             |
             v
          Database

Additional infrastructure:

Docker
   |
CI/CD
   |
AWS

Async communication:

Spring Boot
    |
    v
  Kafka
```

You don't need to build this entire architecture on day one.

Start with:

```text
Java
  ↓
Spring Boot
  ↓
REST
  ↓
PostgreSQL
  ↓
JPA
  ↓
Task Manager
```

Then add complexity only when you understand why it is needed.

---

# 115. Final Checklist

Before calling yourself comfortable with beginner Spring Boot backend development, you should be able to explain:

- [ ] What Java is
- [ ] JDK vs JRE vs JVM
- [ ] Variables and data types
- [ ] Conditions and loops
- [ ] Methods
- [ ] Classes and objects
- [ ] Constructors
- [ ] Encapsulation
- [ ] Inheritance
- [ ] Polymorphism
- [ ] Abstraction
- [ ] Interfaces
- [ ] Collections
- [ ] Exceptions
- [ ] Generics
- [ ] Lambdas
- [ ] Streams
- [ ] Maven
- [ ] What Spring is
- [ ] What Spring Boot is
- [ ] Dependency Injection
- [ ] Beans
- [ ] Controllers
- [ ] Services
- [ ] Repositories
- [ ] REST APIs
- [ ] HTTP methods
- [ ] HTTP status codes
- [ ] Request bodies
- [ ] Path variables
- [ ] Query parameters
- [ ] DTOs
- [ ] Validation
- [ ] Exception handling
- [ ] PostgreSQL
- [ ] SQL
- [ ] JPA
- [ ] Hibernate
- [ ] Entities
- [ ] Relationships
- [ ] Transactions
- [ ] Pagination
- [ ] Authentication
- [ ] Authorization
- [ ] JWT
- [ ] Password hashing
- [ ] Testing
- [ ] Git
- [ ] Docker

---

# 116. Start Here

Your practical order should be:

```text
WEEK 1
Core Java
OOP
Collections
Exceptions
Streams

WEEK 2
Maven
Spring Boot basics
Dependency Injection
Controllers
REST APIs

WEEK 3
PostgreSQL
SQL
JPA
Hibernate
Repositories
Relationships

WEEK 4
DTOs
Validation
Exception handling
Pagination
Testing

WEEK 5+
Spring Security
JWT
Docker
Advanced project features
```

The most important rule:

> Don't just read this guide. Build the Task Manager API while learning it.

Every time you learn a concept, put it into the project.

That is how you move from "I know Spring Boot" to "I can actually build a backend."
