# Instrucciones para agentes de IA

## Contexto y Stack Tecnológico
- Proyecto de **Ingeniería Web (UCA 2026/2027)**: plataforma de gestión del Concurso Oficial de Agrupaciones Carnavalescas (COAC) y archivo histórico del Carnaval de Cádiz.
- Stack obligatorio: **Java 21**, **Spring Boot 4** (Jakarta EE 11), **Vaadin 25** (Flow con tema Aura) y **Apache Maven** (construcción y pruebas mediante `./mvnw`).
- Base de datos: **H2** en desarrollo inicial y **MySQL 8.4** con migraciones **Flyway** para despliegue.

## Convenciones de Código y Arquitectura
- **Idioma:** Todo el código de dominio, mensajes al usuario, comentarios y documentación en `docs/` deben redactarse en **español**.
- **Paquetes:** Organización modular por funcionalidad bajo el paquete raíz del proyecto (`common/`, `edicion/`, `agrupacion/`, `concurso/`, `jurado/`, `archivo/`, `usuario/`), nunca por capas horizontales.
- **Java 21 Moderno:** Usar `jakarta.*` (nunca `javax.*`), `record` para DTOs y objetos valor inmutables, `Optional` solo como tipo de retorno, y programación funcional con *Streams* cuando mejore la legibilidad. No usar características *preview* ni de Java 22–25.
- **Spring Boot:** Inyección de dependencias **siempre por constructor** con atributos `private final` (prohibido `@Autowired` en atributos). Inyectar `Clock` para obtener la fecha y hora actual. Servicios anotados con `@Transactional(readOnly = true)` a nivel de clase y `@Transactional` en métodos de escritura.
- **Spring Data JPA:** Claves primarias `UUID` con `@UuidGenerator(style = UuidGenerator.Style.VERSION_7)`, enumerados con `@Enumerated(EnumType.STRING)` y asociaciones `@ManyToOne(fetch = FetchType.LAZY)`.
- **Vaadin 25:** Usar `@StyleSheet(Aura.STYLESHEET)` en el `AppShellConfigurator` (prohibido `@Theme`, variables `--lumo-*` o `VaadinWebSecurity`). Vistas con `@Route` y formularios enlazados con `Binder` / `BeanValidationBinder`. Capturar `BusinessException` para mostrar mensajes comprensibles mediante `Notification`.

## Guardarraíles y Flujo de Trabajo
- **Seguridad:** Nunca leer, generar ni incluir contraseñas, tokens o credenciales en el repositorio; usar siempre variables de entorno.
- **Bases de datos:** No ejecutar comandos destructivos ni consultas contra bases de datos compartidas o de producción.
- **Control de versiones:** No ejecutar `git commit` ni `git push` de forma autónoma; todo cambio propuesto debe ser revisado por un miembro del equipo humano e integrado vía Pull Request.
- **Documentación:** Mantener actualizada la documentación en formato Markdown dentro de `docs/` junto con cada cambio funcional.
