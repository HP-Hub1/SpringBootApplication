SpringBoot News Application with PostgreSQL and Liquibase

This is a Spring Boot web application that manages news and their associated categories.  
The application uses PostgreSQL as a database, Liquibase for database migrations, and Spring Data JPA for ORM and repository support.

Features

- REST API for managing news and categories
- PostgreSQL database integration
- Database version control with Liquibase (SQL-based migrations)
- Entity relationships mapped via JPA annotations
- Clean layered architecture: Controller → Service → Repository → Entity

Technologies Used

- Java 17+
- Spring Boot
- Spring Data JPA
- PostgreSQL
- Liquibase
- Maven
- Docker (for PostgreSQL container)
- Lombok

Entities

Category
- id (Long): Unique identifier
- title (String): Name of the category

News
- id (Long): Unique identifier
- title (String): News title
- text (String): News content
- date (LocalDateTime): Publication date
- category (Category): News category (ManyToOne relation)

API Endpoints

Categories

GET /api/categories  
Returns a list of all categories.

GET /api/categories/{id}  
Returns a category by its ID.  
If not found, returns HTTP 404.

POST /api/categories  
Creates a new category.  
Request body example:
{
  "title": "AI & Machine Learning"
}

PUT /api/categories  
Updates an existing category.  
Request body example:
{
  "id": 3,
  "title": "Updated Title"
}

DELETE /api/categories/{id}  
Deletes a category by ID.

News

GET /api/news  
Returns a list of all news items, including category name.

GET /api/news/{id}  
Returns a single news item by ID, including its category.

GET /api/news/category/{id}  
Returns all news belonging to a given category ID.

POST /api/news  
Creates a new news item.  
Request body example:
{
  "title": "New AI Release",
  "text": "Details about the release...",
  "category": "AI & Machine Learning"
}

PUT /api/news  
Updates an existing news item.  
Request body example:
{
  "id": 2,
  "title": "Updated Title",
  "text": "Updated text...",
  "category": "AI & Machine Learning"
}

Database Migrations

The database schema is managed with Liquibase.
Migration scripts are written in SQL and located in src/main/resources/db/changelog.
Tables created include:
- category
- news (with foreign key category_id)

