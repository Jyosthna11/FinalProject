# ecomm-backend

# Project Setup Instructions

## Prerequisites

Before you begin, ensure you have met the following requirements:

- You have installed [Git](https://git-scm.com/).
- You have installed [Java JDK](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html) (version 17 or later).
- You have installed [Maven](https://maven.apache.org/install.html).
- You have installed [MySQL](https://dev.mysql.com/downloads/installer/).

## Setting Up the Project Locally

### 1. Clone the Repository
Start by cloning the project repository from GitHub:

```bash
git clone https://github.com/immoien/ecomm-backend.git
```

Navigate to the project directory:

```bash
cd ecomm-backend
```

### 2. Setup MySQL Database

Ensure that MySQL is installed and running on your local machine. Then, follow these steps:

Open your MySQL client (like MySQL Workbench or command line).

Create a new database named `ecommerce`:

```bash
CREATE DATABASE ecommerce;
```

### 3. Update Database Configuration

In the project directory, locate the application.properties or application.yml file (usually inside the src/main/resources directory).

Update the database configuration properties with your MySQL credentials:

The project uses dynamic placeholders for database configuration:
```properties
    # Database Configuration
    spring.datasource.url=jdbc:mysql://${DB_HOST:localhost}:${DB_PORT:3306}/${DB_NAME:ecommerce}
    spring.datasource.username=your_mysql_username
    spring.datasource.password=your_mysql_password
    spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver

    # JPA and Hibernate Configuration
    spring.jpa.hibernate.ddl-auto=update
    spring.jpa.show-sql=true
```

Replace your_mysql_username and your_mysql_password with your actual MySQL login credentials.

### 4. Build and Run the Project

You can now build and run the project using Maven:

```bash
mvn clean install
mvn spring-boot:run
```

This command will start the application on the default port (e.g., http://localhost:5454 if configured in the application properties).

### Additional Notes

- Make sure that the ecommerce database is empty when starting for the first time;
- The application will automatically create the necessary tables.
- If you encounter any errors related to dependencies or configurations, run:

```bash
mvn clean install
```

This ensures that all required dependencies are downloaded and configured properly.
