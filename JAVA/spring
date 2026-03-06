# Advanced Java – 4-Week Intern Training Program

> **Prerequisites:** Core Java (OOP, Collections, Exception Handling, Multithreading)
> **Goal:** Build production-ready skills in Spring ecosystem, persistence, security, and microservices.

---

## Program Overview

| Week | Theme | Topics |
|------|-------|--------|
| Week 1 | Web Foundations | MVC Architecture, Servlets, Tomcat, Spring MVC |
| Week 2 | Data Persistence | JDBC, Hibernate, JPA |
| Week 3 | Spring Ecosystem | Spring Data JPA, Spring Boot, Spring Security |
| Week 4 | Microservices | REST Design, Spring Cloud, Service Communication |

---

## Week 1: Web Foundations — MVC, Servlets, Tomcat & Spring MVC

### Day 1–2: MVC Architecture & Servlets

#### Core Concepts
- What is MVC (Model-View-Controller) and why it matters
- The Servlet lifecycle: `init()`, `service()`, `destroy()`
- `HttpServletRequest` and `HttpServletResponse`
- `web.xml` configuration and servlet mapping
- JSP as the View layer
- Session management: `HttpSession`, Cookies

#### Architecture Deep Dive
```
Browser
  ↓ HTTP Request
Tomcat (Servlet Container)
  ↓ routes to
DispatcherServlet / Servlet
  ↓ calls
Controller (Business Logic)
  ↓ uses
Model (Data / Service Layer)
  ↓ returns to
View (JSP / Thymeleaf)
  ↓ HTTP Response
Browser
```

#### Exercises
1. Create a `LoginServlet` that accepts POST requests with username/password, validates credentials hardcoded in a Map, sets a session attribute on success, and redirects to a `DashboardServlet`.
2. Build a simple Student Registration form using HTML + JSP. On submit, the servlet stores student data in an in-memory `ArrayList` and displays the list in a JSP table.
3. Implement a `CounterServlet` that tracks how many times a page has been visited using `ServletContext` (application-scoped attribute) vs `HttpSession` (user-scoped). Compare and explain the difference.
4. Create a `FileUploadServlet` using Apache Commons FileUpload that accepts a profile picture, saves it to a local directory, and displays it back on the response page.

---

### Day 3–4: Tomcat & Deployment

#### Core Concepts
- What is a Servlet Container vs an Application Server
- Tomcat directory structure: `webapps`, `conf`, `lib`, `logs`
- WAR file packaging and manual deployment
- `context.xml` and `server.xml` configuration
- Connection pooling with DBCP/HikariCP
- Tomcat's `Connector`, thread pool, and request processing pipeline

#### Architecture Deep Dive
```
Tomcat
├── Catalina Engine
│     └── Host (localhost)
│           └── Context (/myapp)  ← your WAR
│                 └── Servlet Instances
├── Coyote Connector (port 8080) ← handles HTTP
└── Thread Pool ← manages concurrent requests
```

#### Exercises
1. Package a multi-servlet application as a WAR file manually using `jar` command (no IDE). Deploy it to a standalone Tomcat and access it from a browser.
2. Configure a JNDI DataSource in `context.xml` for connection pooling. Modify a servlet to look up the DataSource via `InitialContext` and execute a query.
3. Set up two Tomcat instances on different ports. Deploy the same app to both and explain how you would load balance between them (conceptual + configuration).
4. Enable access logging in `server.xml`. Generate 20+ requests and analyze the log file — identify response times, status codes, and request patterns.

---

### Day 5: Spring MVC — Deep Architecture

#### Core Concepts
- `DispatcherServlet` as the Front Controller
- `HandlerMapping` → finds the right controller
- `HandlerAdapter` → invokes the controller method
- `ViewResolver` → maps view names to actual views
- `@Controller`, `@RequestMapping`, `@RequestParam`, `@PathVariable`
- `@ModelAttribute` and model binding
- `@RestController` vs `@Controller`
- `HandlerInterceptor` for cross-cutting concerns

#### Architecture Deep Dive — Spring MVC Request Lifecycle
```
HTTP Request
     ↓
DispatcherServlet  (configured in web.xml or auto in Spring Boot)
     ↓
HandlerMapping     → finds: "GET /users/{id} → UserController.getUser()"
     ↓
HandlerInterceptor.preHandle()   (auth, logging, etc.)
     ↓
HandlerAdapter     → invokes controller method, binds parameters
     ↓
@Controller method executes, returns ModelAndView or String
     ↓
HandlerInterceptor.postHandle()
     ↓
ViewResolver       → "users/detail" → /WEB-INF/views/users/detail.jsp
     ↓
View renders with Model data
     ↓
HandlerInterceptor.afterCompletion()
     ↓
HTTP Response
```

#### Exercises
1. Build a full Spring MVC app (without Spring Boot) configured via XML. Implement a `ProductController` with list, detail, create, and delete endpoints. Use Thymeleaf as the view layer.
2. Implement a custom `HandlerInterceptor` that logs every request's URL, HTTP method, execution time, and response status to a file.
3. Build a form with validation using `@Valid` and `BindingResult`. Validate: non-empty name, valid email, age between 18–60. Show inline errors on the JSP without page redirect.
4. Create a `GlobalExceptionHandler` using `@ControllerAdvice` that catches `ResourceNotFoundException` (custom), `MethodArgumentNotValidException`, and generic `Exception` — returning different views for each.

---

## Week 2: Data Persistence — JDBC, Hibernate & JPA

### Day 1–2: JDBC — Deep Dive

#### Core Concepts
- JDBC Architecture: DriverManager, Connection, Statement, ResultSet
- `PreparedStatement` vs `Statement` (SQL injection prevention)
- `CallableStatement` for stored procedures
- Transaction management: `setAutoCommit(false)`, `commit()`, `rollback()`
- Connection pooling: HikariCP configuration
- `ResultSetMetaData` and `DatabaseMetaData`
- Batch processing with `addBatch()` / `executeBatch()`

#### Exercises
1. Build a generic `JdbcTemplate`-like utility class with methods: `query(sql, params, rowMapper)`, `update(sql, params)`, `queryForObject(sql, params, type)`. Use it to implement a full CRUD for an `Employee` table.
2. Implement a Bank Transfer feature using JDBC transactions. Transfer money between two accounts — if the debit succeeds but credit fails (simulate with a forced exception), ensure a full rollback occurs.
3. Use `executeBatch()` to insert 10,000 records into a table. Measure and compare time taken with and without batching. Then add an index to a column and measure query performance difference.
4. Write a JDBC program that reads `DatabaseMetaData` to print all table names, column names, and their types for a given schema — like a mini schema inspector.

---

### Day 3–4: Hibernate — ORM & Internals

#### Core Concepts
- ORM concept and the impedance mismatch problem
- `SessionFactory` and `Session` lifecycle
- Entity states: Transient → Persistent → Detached → Removed
- Dirty checking and automatic flush
- Associations: `@OneToOne`, `@OneToMany`, `@ManyToMany` with `@JoinColumn` / `@JoinTable`
- Cascading: `CascadeType.ALL`, `PERSIST`, `MERGE`, `REMOVE`
- Fetch strategies: `LAZY` vs `EAGER` and the N+1 problem
- HQL and Criteria API
- 1st and 2nd level caching

#### Architecture Deep Dive — Hibernate Internals
```
session.save(entity)
      ↓
ActionQueue  → schedules INSERT
      ↓
SessionCache (1st level)  → stores snapshot
      ↓
At flush/commit:
      ↓
Dirty Check → compare current state vs snapshot
      ↓
SQL Generator → builds INSERT/UPDATE/DELETE
      ↓
JDBC Connection → executes SQL
      ↓
Database
```

#### Exercises
1. Model a University schema: `University` → `Department` (OneToMany) → `Course` (ManyToMany with `Student`). Implement full CRUD with proper cascade and fetch types. Demonstrate lazy loading triggering a proxy.
2. Reproduce the **N+1 problem**: load 10 Orders, then access `order.getItems()` in a loop. Count SQL queries fired. Fix it using `JOIN FETCH` in HQL. Document before/after query count.
3. Implement **Optimistic Locking** using `@Version`. Simulate two concurrent sessions updating the same record. Show that the second update throws `OptimisticLockException`.
4. Write a Criteria API query that searches employees by optional filters: name (LIKE), department, salary range, and join date range — building the criteria dynamically based on which filters are provided.

---

### Day 5: JPA — Specification & Advanced Mapping

#### Core Concepts
- JPA vs Hibernate: spec vs implementation
- `EntityManagerFactory` and `EntityManager`
- `persistence.xml` configuration
- JPQL vs HQL vs Native Query
- `@NamedQuery` and `@NamedNativeQuery`
- Inheritance mapping strategies: `SINGLE_TABLE`, `TABLE_PER_CLASS`, `JOINED`
- `@Embeddable` and `@Embedded`
- `EntityTransaction` lifecycle

#### Exercises
1. Implement all three JPA inheritance strategies (`SINGLE_TABLE`, `JOINED`, `TABLE_PER_CLASS`) for a `Vehicle → Car, Truck, Motorcycle` hierarchy. Compare the generated SQL and table structures. Write a pros/cons analysis.
2. Use `@Embeddable` to model an `Address` (street, city, state, zip) embedded inside both `Employee` and `Customer` entities. Query employees by city using JPQL.
3. Write `@NamedQuery` definitions on an entity for: findAll, findByStatus, findByDateRange. Call them from a service class using `EntityManager`.
4. Build a `GenericRepository<T, ID>` using `EntityManager` with methods: `save`, `findById`, `findAll`, `delete`, `findByCriteria`. Make it reusable for any entity type.

---

## Week 3: Spring Ecosystem — Spring Data JPA, Spring Boot & Security

### Day 1–2: Spring Data JPA & Spring Boot Architecture

#### Core Concepts — Spring Data JPA
- `JpaRepository` hierarchy: `Repository → CrudRepository → PagingAndSortingRepository → JpaRepository`
- Query derivation from method names
- `@Query` with JPQL and native SQL
- Pagination and sorting: `Pageable`, `Page<T>`, `Sort`
- Projections: interface-based and class-based (DTO)
- `@Transactional` at service level
- Auditing: `@CreatedDate`, `@LastModifiedDate`, `@EnableJpaAuditing`

#### Core Concepts — Spring Boot Architecture
- Auto-configuration mechanism (`@EnableAutoConfiguration`, `spring.factories`)
- `@SpringBootApplication` = `@Configuration` + `@ComponentScan` + `@EnableAutoConfiguration`
- `ApplicationContext` and Bean lifecycle
- `@ConfigurationProperties` and externalized config
- Spring Boot starters and dependency management
- Embedded Tomcat vs external deployment
- Actuator endpoints for monitoring

#### Architecture Deep Dive — Spring Boot Auto-Config
```
@SpringBootApplication
        ↓
@EnableAutoConfiguration
        ↓
Reads: META-INF/spring/org.springframework.boot.autoconfigure.AutoConfiguration.imports
        ↓
Conditions evaluated: @ConditionalOnClass, @ConditionalOnMissingBean, etc.
        ↓
Auto-configures: DataSource, EntityManagerFactory,
                 TransactionManager, JpaRepositories
        ↓
Your Beans + Auto-configured Beans → ApplicationContext
```

#### Exercises
1. Build a **Blog API** with `Post`, `Tag` (ManyToMany), and `Comment` (OneToMany). Implement: paginated post listing, search by tag, full-text search using `@Query`, and a DTO projection that returns only `title`, `author`, `commentCount`.
2. Create a custom Spring Boot **Auto-Configuration** for a simple rate-limiter. Package it as a separate JAR with `spring.factories`. Import it into another project and verify it activates based on a property.
3. Implement JPA **Auditing** on all entities: track `createdBy`, `createdAt`, `lastModifiedBy`, `lastModifiedAt`. Populate `createdBy` from Spring Security context. Write a test verifying audit fields are populated on save and update.
4. Use `@ConfigurationProperties` to bind a custom `app.mail.*` configuration group. Validate with `@Validated` (`@NotNull`, `@Email`, `@Min`). Show that the app fails to start with invalid config.

---

### Day 3–4: Spring Security — Architecture Deep Dive

#### Core Concepts
- Security Filter Chain and `DelegatingFilterProxy`
- `SecurityContext` and `SecurityContextHolder`
- `Authentication` object: Principal, Credentials, Authorities
- `AuthenticationManager` → `AuthenticationProvider` → `UserDetailsService`
- Password encoding: `BCryptPasswordEncoder`
- Authorization: `@PreAuthorize`, `@Secured`, `hasRole()`, `hasAuthority()`
- CSRF protection and when to disable it
- JWT-based stateless authentication flow
- OAuth2 and OpenID Connect basics
- Method-level security with `@EnableMethodSecurity`

#### Architecture Deep Dive — Spring Security Filter Chain
```
HTTP Request
     ↓
DelegatingFilterProxy
     ↓
FilterChainProxy
     ↓ runs filters in order:
SecurityContextPersistenceFilter  → loads SecurityContext from session
UsernamePasswordAuthenticationFilter → processes login form
BasicAuthenticationFilter          → processes Basic Auth header
BearerTokenAuthenticationFilter    → processes JWT token
ExceptionTranslationFilter         → handles 401/403
FilterSecurityInterceptor          → checks authorization rules
     ↓
DispatcherServlet → Controller
```

#### JWT Authentication Flow
```
Client POST /login {username, password}
     ↓
AuthenticationManager.authenticate()
     ↓
UserDetailsService.loadUserByUsername()
     ↓ success
JwtUtil.generateToken(userDetails)
     ↓
Response: { "token": "eyJ..." }

--- subsequent requests ---

Client GET /api/data
  Header: Authorization: Bearer eyJ...
     ↓
JwtAuthFilter extracts + validates token
     ↓
Sets Authentication in SecurityContextHolder
     ↓
FilterSecurityInterceptor checks authorities
     ↓
Controller executes
```

#### Exercises
1. Implement **JWT Authentication** from scratch: login endpoint returns a token, a custom `OncePerRequestFilter` validates it on every request, and endpoints are secured by role (`ROLE_ADMIN`, `ROLE_USER`). Implement token expiry and refresh token endpoint.
2. Build a **Role-Based Access Control** system: Admin can CRUD all resources, Manager can read and update, User can only read their own data. Use `@PreAuthorize("@resourceGuard.canAccess(#id, authentication)")` with a custom bean for fine-grained access.
3. Implement **OAuth2 Login** with Google. After successful login, persist the user to the database via `OAuth2UserService`. Map Google profile fields to your `AppUser` entity. Restrict access to a `/dashboard` endpoint to authenticated OAuth users only.
4. Configure **CORS** globally for a frontend on `http://localhost:3000`. Add **rate limiting** per IP using a custom filter that stores request counts in a `ConcurrentHashMap`. Return `429 Too Many Requests` after 100 requests/minute.

---

### Day 5: Spring Boot — Production Patterns

#### Core Concepts
- Profiles: `@Profile`, `application-{profile}.yml`
- Actuator: health, metrics, info, custom endpoints
- Exception handling: `@RestControllerAdvice`, `ProblemDetail`
- Validation: `@Valid`, custom `ConstraintValidator`
- Async processing: `@Async`, `@EnableAsync`, `CompletableFuture`
- Scheduling: `@Scheduled`, `@EnableScheduling`
- Events: `ApplicationEvent`, `@EventListener`

#### Exercises
1. Build a global exception handling system using `@RestControllerAdvice` that returns RFC 7807 `ProblemDetail` responses. Handle: validation errors (with field-level details), not found, conflict, and unexpected errors — each with distinct HTTP status and error codes.
2. Write a custom `ConstraintValidator` for `@ValidPhoneNumber` that validates Indian mobile numbers. Apply it to a DTO and test with both valid and invalid inputs.
3. Implement an `@Async` email notification service. When a user registers, publish an `UserRegisteredEvent`. An `@EventListener` picks it up and sends a welcome email asynchronously. Use `@Retryable` (Spring Retry) to retry on failure.
4. Create a custom Actuator endpoint `/actuator/app-stats` that returns: total registered users, active sessions, last DB query time, and application uptime. Secure it to only be accessible with `ROLE_ADMIN`.

---

## Week 4: Microservices — Design, Communication & Resilience

### Day 1–2: Microservices Architecture & REST Design

#### Core Concepts
- Monolith vs Microservices: trade-offs
- Domain-Driven Design: Bounded Contexts, Aggregates
- RESTful API design: HATEOAS, versioning, status codes
- API Gateway pattern
- Service Registry: Eureka
- Config Server: Spring Cloud Config
- Inter-service communication: synchronous (REST/Feign) vs asynchronous (Kafka/RabbitMQ)
- CAP theorem and eventual consistency

#### Architecture Deep Dive — Microservices Topology
```
Client
  ↓
API Gateway (Spring Cloud Gateway)
  ├── routes /users/** → User Service
  ├── routes /orders/** → Order Service
  ├── routes /products/** → Product Service
  └── applies: Auth filter, Rate limiting, Logging

User Service ──────────────────→ User DB
Order Service → (Feign Client) → User Service
             → (Feign Client) → Product Service
             ──────────────────→ Order DB
             → (Kafka Producer) → Notification Service

All services register with Eureka (Service Registry)
All services pull config from Config Server
```

#### Exercises
1. Build a 3-service system: `UserService`, `ProductService`, `OrderService`. Each has its own H2 database. `OrderService` calls `UserService` and `ProductService` via **Feign clients**. Register all with **Eureka**. Add an **API Gateway** that routes traffic.
2. Implement **Circuit Breaker** using Resilience4j on `OrderService`'s Feign calls. Configure: failure threshold 50%, wait duration 10s, fallback response. Simulate failures by stopping `UserService` and observe the circuit opening.
3. Set up **Spring Cloud Config Server** with a Git backend. Externalize DB credentials, JWT secret, and feature flags for all three services. Implement `/actuator/refresh` so services pick up config changes without restart.
4. Design and document a REST API for an e-commerce platform following REST best practices: proper resource naming, HTTP verbs, status codes, pagination headers, versioning strategy, and error response format. Implement it with OpenAPI/Swagger documentation.

---

### Day 3–4: Asynchronous Communication & Distributed Patterns

#### Core Concepts
- Message-driven architecture with Kafka / RabbitMQ
- Spring Kafka: `@KafkaListener`, `KafkaTemplate`
- Saga pattern for distributed transactions
- Outbox pattern for reliable messaging
- Distributed tracing: Spring Cloud Sleuth + Zipkin
- Centralized logging: structured logs with correlation IDs
- Idempotency in microservices

#### Exercises
1. Implement an **Order Processing Saga** (choreography-based): `OrderService` publishes `OrderPlaced` event → `InventoryService` reserves stock, publishes `StockReserved` → `PaymentService` charges card, publishes `PaymentProcessed` → `OrderService` marks order `CONFIRMED`. If any step fails, publish compensating events to rollback.
2. Implement the **Outbox Pattern**: instead of publishing Kafka events directly, write events to an `outbox` table in the same DB transaction as the business entity. A separate scheduled poller reads the outbox and publishes to Kafka, marking records as `PUBLISHED`.
3. Add **distributed tracing** using Micrometer Tracing + Zipkin across all services. Make a request that spans 3 services and visualize the full trace in Zipkin UI. Add custom spans for DB queries and external calls.
4. Build a **notification service** that consumes events from multiple topics (`user.registered`, `order.shipped`, `payment.failed`). For each event type, send a different formatted email/SMS. Implement dead-letter queue handling for failed messages.

---

### Day 5: Capstone Project

#### Project: E-Commerce Platform

Build a mini e-commerce backend with the full stack learned over 4 weeks:

**Services:**
- `user-service` — Registration, Login (JWT), Profile management
- `product-service` — Product catalog with search and pagination
- `order-service` — Cart, checkout, order history
- `api-gateway` — Routing, auth filter, rate limiting

**Requirements:**
- Each service has its own database (no shared DB)
- Services communicate via Feign (sync) and Kafka (async)
- Spring Security with JWT across all services
- Spring Data JPA with auditing on all entities
- Global exception handling with ProblemDetail
- Eureka for service discovery
- Config Server for centralized config
- At least one Resilience4j circuit breaker
- Swagger/OpenAPI docs on each service
- At least 3 integration tests per service

---

## Assessment Rubric

| Criteria | Weight |
|---|---|
| Code correctness & functionality | 30% |
| Architecture understanding (can explain decisions) | 25% |
| Code quality (clean code, SOLID principles) | 20% |
| Error handling & edge cases | 15% |
| Documentation & tests | 10% |

---

## Recommended Resources

- **Books:** Spring in Action (Craig Walls), Java Persistence with Hibernate (Bauer & King)
- **Docs:** docs.spring.io, hibernate.org/orm/documentation
- **Practice:** Build each exercise before looking up solutions
- **Tools:** IntelliJ IDEA, Postman, Docker (for Kafka/Zipkin), DBeaver

---

*Training Plan prepared for Advanced Java Intern Cohort | 4 Weeks | 20 Days*
