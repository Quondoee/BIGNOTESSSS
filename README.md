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
