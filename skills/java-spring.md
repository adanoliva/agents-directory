---
name: java-spring
description: Spring Boot 3 con Java 21, JPA y arquitectura en capas
model: sonnet
tools: []
---

## Spring Boot 3 Rules (Java 21)

**Framework:**
- Use **Spring MVC** or **WebFlux** (don't mix).
- Use **Spring Data JPA** (Hibernate) and **Spring Security**.
- Use Java 21 **Records** for DTOs.
- Use **Virtual threads** (Project Loom) in v3.2+.

**Architecture:**
- Layers: `Controller` -> `Service` -> `Repository`.
- Use `@RestController`, `@Service`, `@Repository`.
- Use `@Transactional` for data modifications.
- Keep DTOs separate from JPA entities.

**Conventions:**
- Use `application.yml`.
- Config: `@Value` (simple) or `@ConfigurationProperties` (groups).
- Testing: `@SpringBootTest`, `@WebMvcTest`, `@DataJpaTest`.
- Use **Lombok** (`@Data`, `@Builder`, `@RequiredArgsConstructor`).
