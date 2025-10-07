# PHP REST API
A simple REST API built in PHP that provides CRUD (Create, Read, Update, Delete) operatings for managing your databases.

## Overview
This REST API demonstrates a basic backend architecture using PHP.
It handles **Create**, **Read**, **Update**, **Delete** operations and returns responses in JSON format.

Example use case:
`Managing users, products or tasks in a lightweight PHP environment without external frameworks.`

## Requirements
- PHP 8.1 or higher
- MySQL (or any database alike)
- Apache/Nginx with `mod_rewrite` enabled
- Composer

## Installation
**1.** Clone the repository
```bash
git clone https://github.com/crowware/RestAPI.git
cd RestAPI
```

**2.** Configure your web server to point the document root to **/**

**3.** Set up your database (e.g.)
```sql
CREATE DATABASE product_db;
USE product_db;

CREATE TABLE product (
 id INT NOT NULL AUTO_INCREMENT,
 name VARCHAR(128) NOT NULL,
 size INT NOT NULL DEFAULT 0,
 is_available BOOLEAN NOT NULL DEFAULT FALSE,
 PRIMARY KEY (id)
);
```

**4.** Configure your environment file:
Rename the `.env.example` to `.env` in the project root. Then modify the variables to match your database credentials

**5.** Start your PHP built-in server:
```bash
php -S localhost:8000
```

**6.** API is now available at:
http://localhost:8000

## API Endpoints
| Method        | Endpoint      | Description   |
| ------------- | ------------- | ------------- |
| GET           | /products     | Get all products |
| GET           | /products/{id}     | Get a product |
| POST          | /products     | Create a new product |
| DEL           | /products/{id}     | Delete a product |
| PATCH         | /products     | Update a  products|


## Example Requests

**GET all products**
```bash
curl http://localhost:8000/products
```

**GET a product**
```bash
curl http://localhost:8000/products/1
```

**POST a product**
```bash
curl -X POST http://localhost:8000/products \
-H "Content-Type: application/json" \
-d '{"name": "Product Name", "size": 5, "is_available": false}'
```

**DEL a product**
```bash
curl -X DELETE http://localhost:8000/products/1
```

**GET all products**
```bash
curl -X PATCH http://localhost:8000/products/1
-H "Content-Type: application/json" \
-d '{
    "name": "product updated"
}'
```

## Example Response

**Success**
```json
[
  {
    "id": 1,
    "name": "Product One",
    "size": 543,
    "is_available": false
  },
  {
    "id": 2,
    "name": "Product Two",
    "size": 30,
    "is_available": true
  }
]
```

**Error**
```json
{
  "message": "Product not found"
}
```

## License
MIT License - free to use and modify.

## Author
[Julian Radix](https://github.com/JulianRadix)
*Crowware Co-Owner & General Manager*