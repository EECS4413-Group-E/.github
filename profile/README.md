# Project Setup

Use Node LTS 24.17.0 and Java 26.0.1.

- Microservices and gateway: Spring Boot 4.1.0  
- Frontend: React 19.2.6  
- Database: MySQL (not set up yet)

If you need to run a Spring Boot microservice without the DB set up and it throws datasource/database errors, replace the `@SpringBootApplication` annotation in the main class with:

```java
@SpringBootApplication(exclude = {
    DataSourceAutoConfiguration.class,
    HibernateJpaAutoConfiguration.class
})
```

## Repositories
- [fabrik-ui](https://github.com/EECS4413-Group-E/fabrik-ui) — Frontend React application (TypeScript/React) for the web ui.
- [gateway](https://github.com/EECS4413-Group-E/gateway) — API gateway (Java/Spring Boot) routing requests to the microservices.  

- [authservice](https://github.com/EECS4413-Group-E/authservice) — Authentication microservice (Java/Spring Boot)
- [userservice](https://github.com/EECS4413-Group-E/userservice) — User management microservice (Java/Spring Boot)
- [shippingservice](https://github.com/EECS4413-Group-E/shippingservice) — Shipping microservice (Java/Spring Boot)
- [paymentservice](https://github.com/EECS4413-Group-E/paymentservice) — Payment processing microservice (Java/Spring Boot)
- [orderservice](https://github.com/EECS4413-Group-E/orderservice) — Order management microservice (Java/Spring Boot)
- [chatbotservice](https://github.com/EECS4413-Group-E/chatbotservice) — Chatbot microservice (Java/Spring Boot)
- [catalogueservice](https://github.com/EECS4413-Group-E/catalogueservice) — Catalogue/product microservice (Java/Spring Boot)

## Notes
- MySQL will be used as the database
