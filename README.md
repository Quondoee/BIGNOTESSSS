## 1. Spring IOC (Inversion of Control)


- **Inversion of Control (IOC)** is a design principle in which the control of object creation and lifecycle is transferred from the application code to the Spring container.
- Spring IOC is implemented using the **Spring Container** and **Beans**.
- The Spring container is responsible for instantiating, configuring, and managing the lifecycle of beans (objects).
  
**Types of Spring Containers:**
- **BeanFactory**: Basic container that provides the fundamental functionality of IOC.
- **ApplicationContext**: A more advanced container that adds additional features like event propagation, declarative mechanisms, etc.

**Common Annotations:**
- `@Component`: Marks a class as a Spring bean.
- `@Autowired`: Automatically injects dependencies into the class.
- `@Configuration` & `@Bean`: Used for configuration classes and bean definition in Java-based Spring configuration.

---

## 2. Dependency Injection (DI)


- **Dependency Injection** is a design pattern that allows for decoupling of objects by injecting dependencies at runtime rather than creating them directly within the class.
- DI can be achieved in Spring via:
  - **Constructor Injection**
  - **Setter Injection**
  - **Field Injection**

**Advantages:**
- **Loose Coupling**: Classes are independent and easier to test.
- **Flexibility**: Dependencies can be changed without modifying the class.
- **Ease of Testing**: Mock dependencies in unit tests.

---

## 3. Dispatcher Servlet


- The **DispatcherServlet** is the central component of Spring MVC, handling HTTP requests and routing them to appropriate controllers for processing.
- It serves as a **front controller** and manages the entire request-response lifecycle.
- It works by delegating the request to appropriate handler mappings, invoking the handler methods, and rendering the view.

**Components Involved:**
- **HandlerMapping**: Determines which controller to invoke based on the request.
- **HandlerAdapter**: Invokes the controller method.
- **ViewResolver**: Resolves the view (such as JSP, Thymeleaf) after the controller processes the request.

---

## 4. RESTful API Development


- **REST** (Representational State Transfer) is an architectural style for building web services that communicate over HTTP.
- REST APIs use standard HTTP methods such as GET, POST, PUT, DELETE to perform operations on resources.

**Best Practices:**
- **Stateless**: Each API call should contain all information to process it, with no server-side session.
- **Use proper HTTP status codes**: E.g., 200 for success, 404 for resource not found, 500 for server error.
- **Resource Naming**: Resources should be named using nouns, e.g., `/users`, `/orders`.
  
**Spring Annotations for REST:**
- `@RestController`: Marks a class as a REST controller.
- `@RequestMapping`, `@GetMapping`, `@PostMapping`, `@PutMapping`, `@DeleteMapping`: Mappings for different HTTP methods.

---

## 5. CRUD Operations


- **CRUD** stands for Create, Read, Update, and Delete, the four basic operations for persistent storage management.
- These operations can be mapped directly to HTTP methods:
  - **Create**: POST
  - **Read**: GET
  - **Update**: PUT/PATCH
  - **Delete**: DELETE
  
**CRUD in Spring Data JPA:**
- The **JpaRepository** interface provides built-in methods for these operations:
  - `save()`, `findById()`, `findAll()`, `deleteById()`, etc.

---

## 6. JPA (Java Persistence API) Mappings


- **JPA** is a specification for managing relational data in Java applications.
- JPA annotations are used to map Java objects to database tables and vice versa.

**Common Annotations:**
- `@Entity`: Marks a class as an entity to be persisted in the database.
- `@Table`: Specifies the table name.
- `@Id`: Marks the primary key of the entity.
- `@GeneratedValue`: Specifies how the primary key is generated (e.g., auto-increment).
- `@OneToMany`, `@ManyToOne`, `@ManyToMany`, `@OneToOne`: Define relationships between entities.
  
---

## 7. Query Methods in Spring Data JPA


- Spring Data JPA allows defining custom queries using method names or the `@Query` annotation.

**Method Query Naming Conventions:**
- Spring Data JPA uses method names to automatically generate queries:
  - `findByName(String name)` -> `SELECT * FROM entity WHERE name = ?`
  - `findByAgeGreaterThanEqual(int age)` -> `SELECT * FROM entity WHERE age >= ?`
  
**Custom Queries with `@Query`:**
- You can define more complex queries using the `@Query` annotation:
  ```java
  @Query("SELECT u FROM User u WHERE u.name LIKE %?1%")
  List<User> findByNameContaining(String name);

  
8. Lambdas
Lambdas are anonymous functions that allow you to treat functionality as a method argument or create a function to be executed later.

Syntax:
java
Copy code
(parameters) -> expression
Examples:
No parameters:

java
Copy code
() -> System.out.println("Hello, world!");
With parameters:

java
Copy code
(a, b) -> a + b;
Single line expression:

java
Copy code
(a, b) -> a * b;
Multiple lines:

java
Copy code
(a, b) -> {
    int sum = a + b;
    return sum;
}
Use case:
Lambdas are used primarily with functional interfaces. For example, using Comparator to sort a list of strings:

java
Copy code
List<String> list = Arrays.asList("banana", "apple", "cherry");
list.sort((a, b) -> a.compareTo(b));


9. Method References
Method references provide a shorthand way to call a method. They enhance readability and simplify the code by referring to methods by their names instead of using lambdas.

Types of Method References:
Static method reference:

java
Copy code
ClassName::staticMethodName
Example:

java
Copy code
Math::max
Instance method reference (for a specific object):

java
Copy code
instance::instanceMethodName
Example:

java
Copy code
String str = "hello";
str::toUpperCase
Instance method reference (for an object of a particular type):

java
Copy code
ClassName::instanceMethodName
Example:

java
Copy code
String::toUpperCase
Constructor reference:

java
Copy code
ClassName::new
Example:

java
Copy code
ArrayList::new
Use case:
Instead of a lambda expression:

java
Copy code
list.forEach(s -> System.out.println(s));
You can use:

java
Copy code
list.forEach(System.out::println);
10. Map
Map is a method of the Stream interface that transforms each element in the stream using a given function. It takes a function as an argument and applies it to each element, returning a new stream.

Syntax:
java
Copy code
Stream<T> map(Function<? super T, ? extends R> mapper);
Example:
java
Copy code
List<String> names = Arrays.asList("John", "Paul", "George", "Ringo");
List<String> upperNames = names.stream()
                               .map(String::toUpperCase)
                               .collect(Collectors.toList());
Use case:
Transforming a list of integers to their squares:

java
Copy code
List<Integer> numbers = Arrays.asList(1, 2, 3, 4);
List<Integer> squares = numbers.stream()
                               .map(n -> n * n)
                               .collect(Collectors.toList());
11. Filter
Filter is a method of the Stream interface used to exclude elements from a stream that don't match a given condition. It returns a new stream consisting of elements that satisfy the provided predicate.

Syntax:
java
Copy code
Stream<T> filter(Predicate<? super T> predicate);
Example:
java
Copy code
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6);
List<Integer> evenNumbers = numbers.stream()
                                   .filter(n -> n % 2 == 0)
                                   .collect(Collectors.toList());
Use case:
Filtering a list to retain only elements greater than 5:

java
Copy code
List<Integer> numbers = Arrays.asList(1, 5, 10, 20);
List<Integer> filtered = numbers.stream()
                                .filter(n -> n > 5)
                                .collect(Collectors.toList());
Conclusion
Lambdas, Method References, Map, and Filter are key elements in functional programming in Java. They enable more declarative and concise code, reducing boilerplate and enhancing readability. By embracing functional techniques, you can write cleaner and more efficient program
