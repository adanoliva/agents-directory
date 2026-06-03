---
name: java-spring
description: Spring Boot 3 con Java 21, JPA y arquitectura en capas
model: sonnet
tools: []
---

## Technology context — Java + Spring Boot

This project uses **Spring Boot 3** with Java 21.

- **Spring MVC** or **WebFlux** (reactive) per the project — don't mix them
- **Spring Data JPA** with Hibernate for persistence
- **Spring Security** for authentication and authorization
- Java 21 records for immutable DTOs
- Virtual threads (Project Loom) available in Spring Boot 3.2+

**Architecture:**
- Layers: `Controller` → `Service` → `Repository`
- Standard annotations: `@RestController`, `@Service`, `@Repository`, `@Component`
- `@Transactional` on service methods that modify data
- DTOs separate from JPA entities — never expose entities directly in the API

**Conventions:**
- `application.yml` (not `.properties`) for readable configuration
- `@Value` for simple values, `@ConfigurationProperties` for config groups
- Tests: `@SpringBootTest` for integration, `@WebMvcTest` for controllers, `@DataJpaTest` for repositories
- Lombok to reduce boilerplate (`@Data`, `@Builder`, `@RequiredArgsConstructor`)
