# Project Setup

Use Node LTS 24.17.0 and Java 26.0.1.

- Microservices and gateway: Spring Boot 4.1.0  
- Frontend: React 19.2.6  
- Database: MySQL

## Repositories
- [fabrik-ui](https://github.com/EECS4413-Group-E/fabrik-ui) — Frontend React application (TypeScript/React) for the web ui.
- [gateway](https://github.com/EECS4413-Group-E/gateway) — API gateway (Java/Spring Boot) routing requests to the microservices.  

- [authservice](https://github.com/EECS4413-Group-E/authservice) — Authentication microservice (Java/Spring Boot)
- [catalogueservice](https://github.com/EECS4413-Group-E/catalogueservice) — Catalogue/product microservice (Java/Spring Boot)
- [chatbotservice](https://github.com/EECS4413-Group-E/chatbotservice) — Chatbot microservice (Java/Spring Boot)
- [orderservice](https://github.com/EECS4413-Group-E/orderservice) — Order management microservice (Java/Spring Boot)
- [paymentservice](https://github.com/EECS4413-Group-E/paymentservice) — Payment processing microservice (Java/Spring Boot)
- [shippingservice](https://github.com/EECS4413-Group-E/shippingservice) — Shipping microservice (Java/Spring Boot)
- [userservice](https://github.com/EECS4413-Group-E/userservice) — User management microservice (Java/Spring Boot)


## Local Setup Instructions
1. Install java 26.0.1 (if you haven't already). [Oracle jdk](https://www.oracle.com/ca-en/java/technologies/downloads/#jdk26-windows)
2. Install node 24.17.0, preferrably using nvm (node version manager). Gettin
   - [nvm Getting Started Guide](https://www.nvmnode.com/guide/introduction.html#getting-started)
   - ```nvm install 24.17.0```
   - ```nvm use 24.17.0```
3. Install [MySql 8 Community Edition](https://dev.mysql.com/downloads/)
4. Create the auth, user, product, and order db schemas in your local database:
   ```sql
    CREATE SCHEMA `auth` ;
    CREATE SCHEMA `catalogue`;
    CREATE SCHEMA `order`;
    CREATE SCHEMA `payment`;
    CREATE SCHEMA `shipping`;
    CREATE SCHEMA `user` ;
   ```
5. For each schema, create an admin user that will be used to access the database (by you and the microservices). Run the following script from your root mysql user and replace password with the schema you are making the user for and a custom password for you to use.
   ```sql
   CREATE USER 'auth_admin'@'localhost' IDENTIFIED BY 'REPLACE_WITH_NEW_PASSWORD';
   GRANT ALL PRIVILEGES ON `auth`.* TO 'auth_admin'@'localhost' WITH GRANT OPTION;
   
   CREATE USER 'catalogue_admin'@'localhost' IDENTIFIED BY 'REPLACE_WITH_NEW_PASSWORD';
   GRANT ALL PRIVILEGES ON `catalogue`.* TO 'catalogue_admin'@'localhost' WITH GRANT OPTION;

   CREATE USER 'order_admin'@'localhost' IDENTIFIED BY 'REPLACE_WITH_NEW_PASSWORD';
   GRANT ALL PRIVILEGES ON `order`.* TO 'order_admin'@'localhost' WITH GRANT OPTION;

   CREATE USER 'payment_admin'@'localhost' IDENTIFIED BY 'REPLACE_WITH_NEW_PASSWORD';
   GRANT ALL PRIVILEGES ON `product`.* TO 'product_admin'@'localhost' WITH GRANT OPTION;
   
   CREATE USER 'shipping_admin'@'localhost' IDENTIFIED BY 'REPLACE_WITH_NEW_PASSWORD';
   GRANT ALL PRIVILEGES ON `shipping`.* TO 'shipping_admin'@'localhost' WITH GRANT OPTION;

   CREATE USER 'user_admin'@'localhost' IDENTIFIED BY 'REPLACE_WITH_NEW_PASSWORD';
   GRANT ALL PRIVILEGES ON `user`.* TO 'user_admin'@'localhost' WITH GRANT OPTION;
   ```
6. When working on a microservice, make sure to create a run configuration that will launch the main springboot java file and configure environment variables for the `DB_URL` (localhost), `<schema>_DB_USERNAME`, and `<schema>_DB_PASSWORD` as you configured in the step above to match the variables in the application.properties file.
   - Example for the authservice in Intellij Idea:
     <img width="1418" height="1034" alt="image" src="https://github.com/user-attachments/assets/0fcfac30-9299-41ab-8f58-5b678de72a5d" />

7. For running the full system, including the gateway and auth service, you will need the private-key.pem and publick-key.pem files. For these files, you can generate them locally using the openssl utility or reach out to me personally for these files. Add the path to public-key.pem as JWT_PUBLIC_KEY_PATH in gateway service and the path to private-key.pem as JWT_PRIVATE_KEY_PATH in the auth service.


## Making and Commiting Changes
1. Make a new branch named corresponding to the change you are making. For ex: set-default-application-properties
2. Make user changes and commits on the branch you created
3. Create a pull request with a title and description explaining your changes
4. Have someone review the changes, make any adjustments, merge into main/master

Example pull request: https://github.com/EECS4413-Group-E/authservice/pull/1

<b>Note: Please do not commit straight to main/master without a pull request</b>
