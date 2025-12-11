# API-Documentation
Bookstore API Documentation
## Base URL
https://github.com/terrajrvs/API-Documentation/edit/main/README.md
## Authentication
This API uses API Key for authentication. The API key is included in the request header:
## Authorization
Account YOUR_API_KEY
## Introduction to the Document
This document provides information about the Bookstore API Documentation, allowing developers to integrate applications with the Bookstore system. The API gives access to book listings, customer orders, user accounts, reviews, Used Book Management, Publisher/Distributor Inegration, Event Management, and payment processing. This user guide highlights the available endpoints, authentication methods, request/response formats, and error handling.
## Intended Audience
+ **Software Developers:** Developers integrating the Bookstore API into their applications for tasks such as fetching book data, managing orders, and handling user accounts.
+ **Technical Writers:** Documentation writers maintaining and updating the API documentation.
+ **API Consumers:** External clients or teams that wish to leverage the Bookstore API for e-commerce or data-related purposes.
+ **Quality Assurance (QA) Engineers:** Professionals who verify and test the functionality of the API endpoints.
## Scope of the Document
# Table of Contents
1. [Books](#1-books)
2. [Endpoints](#endpoints) 
3. [Get All Books](#get-all-books)
4. [Get Single Book by ID](#get-single-book-by-id)
5. [Create a New Book](#create-a-new-book)
6. [Update a Book](#update-a-book)
7. [Delete a Book](#delete-a-book)
8. [Shopping Cart](#shopping-cart)
9. [Get Cart](#get-cart)
10. [Add Book to Cart](#add-a-book-to-cart)
11. [Delete Book from Cart](#delete-a-book-from-cart)
12. [Add Book to Cart](#add-a-book-to-cart)
13. [Checkout](#checkout)
14. [Error Response](#error-response)
16. [Rate Limiting](#rate-limiting)
# Endpoints
## Books
### Get All Books
- URL: /books
- Method: GET
- Description: Retrieve list of available books.
- Query Parameters:
  - page: (optional) Page number for pagination (default: 1)
  - limit: (optional) Number of books per page (default: 10)
  - genre: (optional) Filter by book genre (e.g., fiction, non-fiction, mystery)
  - author: (optional) Filter by author name
- **Response:**

    ```json
    {
    "page": 1,
    "limit": 10,
    "total_books": 100,
    "books": [
        {
        "id": 1,
        "title": "My Inventions: The Autobiography of Nikola Tesla",
        "author": "Nikola Tesla",
        "genre": "Non-Fiction",
        "price": 19.95,
        "stock": 37,
        "description": "My Inventions: The Autobiography of Nikola Tesla is a firsthand account of the inventor's life, written at age 63, detailing his early life, creative process, and major inventions like the AC electrical system, radio, and wireless power transmission.",
        "cover_image": "[https://www.penguinrandomhouse.com/books/308224/my-inventions-and-other-writings-by-nikola-tesla/#:~:text=Related%20Genres,Memoir%20Classic%20Nonfiction%20Science%20&%20Technology]"
        },
        {
        "id": 2,
        "title": "1919",
        "author": "Nikola Tesla",
        "genre": "Autobiography and Science & Technology Nonfiction.",
        "price": 19.95,
        "stock": 15,
        "description": "Autobiography and Science & Technology Nonfiction.",
        "cover_image": "[[https://example.com/images/1919.jpg](https://www.penguinrandomhouse.com/books/308224/my-inventions-and-other-writings-by-nikola-tesla/#:~:text=Related%20Genres,Memoir%20Classic%20Nonfiction%20Science%20&%20Technology](https://www.penguinrandomhouse.com/books/308224/my-inventions-and-other-writings-by-nikola-tesla/#:~:text=Related%20Genres,Memoir%20Classic%20Nonfiction%20Science%20&%20Technology))"
        }
    ]
    }
    ```


    | Sr No | Key                    | Value                                                      | Description                                                                                       |
    |-------|------------------------|------------------------------------------------------------|---------------------------------------------------------------------------------------------------|
    | 1     | page                   | 1                                                          | The current page number of the results. Must be a positive integer. Example: 1, 2, etc.           |
    | 2     | limit                  | 10                                                         | The limit on the number of items (books) per page. Positive integer, typically between 1 and 100. |
    | 3     | total_books            | 100                                                        | Total number of books available. Must be a positive integer (e.g., 100).                          |
    | 4     | books[0].id            | 1                                                          | Unique identifier for the book. Positive integer. E.g., 1, 2, etc. Must be ≤ total_books.         |
    | 5     | books[0].title         | "[My Inventions: The Autobiography of Nikola Tesla](https://www.penguinrandomhouse.com/books/308224/my-inventions-and-other-writings-by-nikola-tesla/#:~:text=Related%20Genres,Memoir%20Classic%20Nonfiction%20Science%20&%20Technology)"                                         | Title of the book. String with a max of 255 characters. Example: "My Inventions: The Autobiography of Nikola Tesla".              |
    | 6     | books[0].author        | "Nikola Tesla"                                      | Author of the book. String with a max of 150 characters. Example: "Nicola Tesla".          |
    | 7     | books[0].genre         | "Non-Fiction"                                                 | Genre of the book. String with a max of 50 characters. Example: "Non-Fiction".                        |
    | 8     | books[0].price         | 19.95                                                      | Price of the book. Decimal number with up to 2 decimal places. Must be positive. Example: 10.99.   |
    | 9     | books[0].stock         | 20                                                         | Number of copies in stock. Positive integer. Example: 20. Must be ≥ 0.                            |
    | 10    | books[0].description   | "The fascinating autobiography of the legendary inventor behind the radio, wireless energy, robotics, and much more.
" | Description of the book. String with a max of 500 characters. Example: "A novel set in the 1920s...". |
| 11    | books[0].cover_image   | "https://www.amazon.com/My-Inventions-Autobiography-Nikola-Tesla/dp/0910077002"         | URL of the book's cover image. Must be a valid URL. Example: "https://example.com/images/gatsby.jpg". |
    | 12    | books[1].id            | 2                                                          | Unique identifier for the second book. Positive integer. Example: 2. Must be ≤ total_books.       |
    | 13    | books[1].title         | "1919"                                                    | Title of the book. String with a max of 255 characters. Example: "1919".                          |
    | 14    | books[1].author        | "Nikola Tesla"                                            | Author of the book. String with a max of 150 characters. Example: "Nikola Tesla".                |
    | 15    | books[1].genre         | "Autobiography"                                               | Genre of the book. String with a max of 50 characters. Example: "Autobiography".                      |
    | 16    | books[1].price         | 19.95                                                      | Price of the book. Decimal number with up to 2 decimal places. Must be positive. Example: 19.95.  |
    | 17    | books[1].stock         | 25                                                         | Number of copies in stock. Positive integer. Example: 11. Must be ≥ 0.                            |
    | 18    | books[1].description   | "Tesla's autobiography, originally printed as a series of six magazine articles in The Electrical Experimenter magazine. Complete with all original plus 6 additional illustrations."            | Description of the book. String with a max of 500 characters. Example: "A dystopian novel...".     |
    | 19    | books[1].cover_image   | "[https://example.com/images/1984.jpg](https://www.amazon.com/My-Inventions-Autobiography-Nikola-Tesla/dp/0910077002)"     | URL of the book's cover image. Must be a valid URL. Example: "https://www.amazon.com/My-Inventions-Autobiography-Nikola-Tesla/dp/0910077002". |
    
**Notes:**

- **Title:** The title field has a maximum length of 255 characters to accommodate longer book titles.
- **Author:** The author field allows for up to 150 characters.
- **Genre:** The genre field has a max of 50 characters to account for standard genre names.
- **Description:** Both book descriptions have a max of 500 characters, allowing a brief yet detailed summary.
- **Price:** Prices should be expressed as a decimal number with up to 2 decimal places (e.g., 10.99).
- **Stock:** The stock field is a positive integer (≥ 0).
- **Cover Image URL:** URLs for images must be valid and properly formatted.

#### Get Single Book by ID

- **URL:** /books/{book_id}
  
- **Method:** GET
  
- **Description:** Retrieve details of a specific book.
  
- **URL Parameters:**

  - book_id: The ID of the book to retrieve.

- **Response:**

    ```json
    {
    "id": 1,
    "title": "My Inventions: The Autobiography of Nikola Tesla",
    "author": "Nikola Tesla",
    "genre": "Non-Fiction",
    "price": 19.95,
    "stock": 37,
    "description": "Nikola Tesla's own writings fall under Autobiography and Science & Technology Nonfiction.",
    "cover_image": "[https://www.penguinrandomhouse.com/books/308224/my-inventions-and-other-writings-by-nikola-tesla/#:~:text=Related%20Genres,Memoir%20Classic%20Nonfiction%20Science%20&%20Technology](https://www.penguinrandomhouse.com/books/308224/my-inventions-and-other-writings-by-nikola-tesla/#:~:text=Related%20Genres,Memoir%20Classic%20Nonfiction%20Science%20&%20Technology)",
    "reviews": [
        {
        "user": "john_doe",
        "rating": 5,
        "comment": "His core autobiographical work, detailing his early life, education, and breakthroughs in AC power, the Tesla coil, and wireless technology, revealing his visionary mindset."
        },
        {
        "user": "jane_doe",
        "rating": 4,
        "comment": "He explains complex concepts like alternating current (AC) systems, wireless energy transmission, and high-frequency currents, providing primary source material for science history."
        }
    ]
    }
    ```

    | Sr No | Key         | Value                                       | Description                                                                 |
    |-------|-------------|---------------------------------------------|-----------------------------------------------------------------------------|
    | 1     | id          | 1                                           | Unique identifier for the book. Must be a positive integer.                 |
    | 2     | title       | My Inventions: The Autobiography of Nikola Tesla | Title of the book. Max 255 characters.                                      |
    | 3     | author      | Nikola Tesla                    | Author’s name. Max 100 characters.                                          |
    | 4     | genre       | Non-Fiction                                     | Genre of the book. Should be a valid genre type.                            |
    | 5     | price       | 19.95                                       | Price of the book. Must be a positive decimal, max two decimal places.      |


#### Create a New Book
  
- **URL:** /books
  
- **Method:** POST

- **Description:** Add a new book to the store.

- **Request Body:**

    ```json
    {
    "title": "The Problem of Increasing Human Energy
Book by Nikola Tesla
",
    "author": "Nikola Tesl",
    "genre": "Non-Fiction",
    "price": 19.95,
    "stock": 10,
    "description": "A story about a young man’s journey of self-discovery.",
    "cover_image": "[https://example.com/images/catcher.jpg](https://www.amazon.com/Problem-Increasing-Human-Energy-Harnessing/dp/1605200956#:~:text=Part%20philosophical%20ponderings%20on%20humanity's,unsung%20hero%20of%20scientific%20philosophy.)"
    }
    ```

    | Sr No | Key         | Value                                       | Description                                                                 |
    |-------|-------------|---------------------------------------------|-----------------------------------------------------------------------------|
    | 1     | title       | The Problem of Increasing Human Energy Book by Nikola Tesla  | Title of the book. Max 255 characters.                                      |
    | 2     | author      | Nikola Tesla                               | Author’s name. Max 100 characters.                                          |
    | 3     | genre       | Fiction                                     | Genre of the book. Should be a valid genre type.                            |
    | 4     | price       | 8.99                                        | Price of the book. Positive decimal, max two decimal places.                |
    | 5     | stock       | 25                                          | Stock quantity. Must be a non-negative integer.                             |


- **Response:**

    ```json
    {
    "id": 3,
    "title": "The Problem of Increasing Human Energy Book by Nikola Tesla",
    "author": "Nikola Tesla",
    "genre": "Non-Fiction",
    "price": 19.95,
    "stock": 15,
    "description": "A major focus is on using the sun's power for industrial and societal needs, a concept ahead of its time.",
    "cover_image": "[https://example.com/images/catcher.jpg](https://www.amazon.com/Problem-Increasing-Human-Energy-Harnessing/dp/1605200956#:~:text=Part%20philosophical%20ponderings%20on%20humanity's,unsung%20hero%20of%20scientific%20philosophy.)"
    }
    ```

    | Sr No | Key         | Value                                       | Description                                                                 |
    |-------|-------------|---------------------------------------------|-----------------------------------------------------------------------------|
    | 1     | id          | 3                                           | Unique identifier for the book. Must be a positive integer.                 |
    | 2     | title       | The Problem of Increasing Human Energy Book by Nikola Tesla | Title of the book. Max 255 characters.                                      |
    | 3     | author      | Nikola Tesla                               | Author’s name. Max 100 characters.                                          |
    | 4     | genre       | Fiction                                     | Genre of the book. Should be a valid genre type.                            |
    | 5     | price       | 8.99                                        | Price of the book. Positive decimal, max two decimal places.                |


#### Update a Book

**URL:**/books/{book_id}

**Method:** PUT

**Description:** Update the details of an existing book.

**URL Parameters:**
  - book_id: The ID of the book to update.

- **Request Body:**
  
    ```json
    {
    "price": 9.99,
    "stock": 30,
    "description": "Updated description of the book."
    }
    ```

    | Sr No | Key         | Value                                       | Description                                                                 |
    |-------|-------------|---------------------------------------------|-----------------------------------------------------------------------------|
    | 1     | price       | 9.99                                        | Updated price of the book. Positive decimal, max two decimal places.        |
    | 2     | stock       | 30                                          | Updated stock quantity. Must be a non-negative integer.                     |
    | 3     | description | Updated description of the book.            | Updated description. Max 500 characters.                                    |


- **Response:**

    ```json
    {
    "id": 1,
    "title": "My Inventions: The Autobiography of Nikola Tesla",
    "author": "Nikola Tesla",
    "genre": "Non-Fiction",
    "price": 19.95,
    "stock": 37,
    "description": "He explains complex concepts like alternating current (AC) systems, wireless energy transmission, and high-frequency currents, providing primary source material for science history.",
    "cover_image": "[https://www.penguinrandomhouse.com/books/308224/my-inventions-and-other-writings-by-nikola-tesla/#:~:text=Related%20Genres,Memoir%20Classic%20Nonfiction%20Science%20&%20Technology"
    }
    ```

    | Sr No | Key         | Value                                       | Description                                                                 |
    |-------|-------------|---------------------------------------------|-----------------------------------------------------------------------------|
    | 1     | id          | 1                                           | Unique identifier for the book. Must be a positive integer.                 |
    | 2     | title       | My Inventions: The Autobiography of Nikola Tesla | Title of the book. Max 255 characters.                                      |
    | 3     | author      | Nikola Tesla                         | Author’s name. Max 100 characters.                                          |
    | 4     | genre       | Non-Fiction                                     | Genre of the book. Should be a valid genre type.                            |
    | 5     | price       | 99.95                                        | Updated price of the book. Positive decimal, max two decimal places.        |


#### Delete a Book

- **URL:** /books/{book_id}

- **Method:** DELETE

- **Description:** Remove a book from the store.

- **URL Parameters:**
  - book_id: The ID of the book to delete.

- **Response:**

    ```json
    {
    "message": "Book deleted successfully."
    }
    ```

    | Sr No | Key         | Value                                       | Description                                                                 |
    |-------|-------------|---------------------------------------------|-----------------------------------------------------------------------------|
    | 1     | message     | Book deleted successfully.                  | Confirmation message for book deletion.                                      |


### Shopping Cart

#### Get Cart

- **URL:** /cart

- **Method:** GET

- **Description:** Retrieve the current user's shopping cart.

- **Response:**

    ```json
    {
    "cart": [
        {
        "book_id": 1,
        "title": "My Inventions: The Autobiography of Nikola Tesla",
        "quantity": 1,
        "price": 19.95
        },
        {
        "book_id": 2,
        "title": "1919",
        "quantity": 2,
        "price": 39.90
        }
    ],
    "total": 39.90
    }
    ```

    | Sr No | Key         | Value                                       | Description                                                                 |
    |-------|-------------|---------------------------------------------|-----------------------------------------------------------------------------|
    | 1     | cart        | [{"book_id": 1, "title": "My Inventions: The Autobiography of Nikola Tesla", "quantity": 1, "price": 19.95}, {"book_id": 2, "title": "1919", "quantity": 2, "price": 39.90}] | List of books in the cart. Each entry contains book_id, title, quantity, and price.|
    | 2     | total       | 39.90                                       | Total amount for all items in the cart. Calculated based on quantity and price. Must be a positive decimal.      |


#### Add Book to Cart

- **URL:** /cart

- **Method:** POST
  
- **Description:** Add a book to the shopping cart.
  
- **Request Body:**

    ```json
    {
    "book_id": 3,
    "quantity": 1
    }
    ```

    | Sr No | Key         | Value                                       | Description                                                                 |
    |-------|-------------|---------------------------------------------|-----------------------------------------------------------------------------|
    | 1     | book_id     | 3                                           | Unique identifier for the book to add. Must be a positive integer.          |
    | 2     | quantity    | 1                                           | Quantity of the book to add. Must be a positive integer.                    |


- **Response:**

    ```json
    {
    "message": "Book added to cart successfully."
    }
    ```

    | Sr No | Key         | Value                                       | Description                                                                 |
    |-------|-------------|---------------------------------------------|-----------------------------------------------------------------------------|
    | 1     | message     | Book added to cart successfully.            | Confirmation message for adding a book to the cart.                         |


#### Update Cart

- **URL:** /cart/{book_id}
  
- **Method:** PUT

- **Description:** Update the quantity of a book in the shopping cart.

- **URL Parameters:**
  - book_id: The ID of the book to update.

- **Request Body:**

    ```json
    {
    "quantity": 3
    }
    ```

    | Sr No | Key         | Value                                       | Description                                                                 |
    |-------|-------------|---------------------------------------------|-----------------------------------------------------------------------------|
    | 1     | quantity    | 3                                           | Updated quantity for the book. Must be a positive integer.                  |


- **Response:**

    ```json
    {
    "message": "Cart updated successfully."
    }
    ```

    | Sr No | Key         | Value                                       | Description                                                                 |
    |-------|-------------|---------------------------------------------|-----------------------------------------------------------------------------|
    | 1     | message     | Cart updated successfully.                  | Confirmation message for successfully updating the cart.                    |


#### Delete Book from Cart

- **URL:** /cart/{book_id}
  
- **Method:** DELETE
  
- **Description:** Remove a book from the shopping cart.
  
- **URL Parameters:**
  - book_id: The ID of the book to remove.

- **Response:**

    ```json
    {
    "message": "Book removed from cart successfully."
    }
    ```

    | Sr No | Key         | Value                                       | Description                                                                 |
    |-------|-------------|---------------------------------------------|-----------------------------------------------------------------------------|
    | 1     | message     | Book removed from cart successfully.        | Confirmation message for successfully removing a book from the cart.        |


### Checkout

This is how the checkout call is made.

#### Checkout

- **URL:** /checkout

- **Method:** POST

- **Description:** Complete the purchase of items in the shopping cart.

- **Request Body:**

    ```json
    {
    "payment_method": "credit_card",
    "address": {
        "line1": "2222 First Ave.",
        "city": "New York",
        "state": "NY",
        "postal_code": "10013"
    }
    }
    ```
    | Sr No | Key         | Value                                       | Description                                                                 |
    |-------|-------------|---------------------------------------------|-----------------------------------------------------------------------------|
    | 1     | payment_method | credit_card                              | Payment method. Must be a valid payment method (e.g., credit_card, PayPal). |
    | 2     | address     | {"line1": "2222 First Ave.", "city": "New York", "state": "NY", "postal_code": "10013"} | Shipping address. Each field must follow respective formats (e.g., postal_code must be valid). |


- **Response:**

    ```json
    {
    "message": "Purchase completed successfully.",
    "order_id": 1010101,
    "total_amount": 39.90
    }
    ```

    | Sr No | Key         | Value                                       | Description                                                                 |
    |-------|-------------|---------------------------------------------|-----------------------------------------------------------------------------|
    | 1     | message     | Purchase completed successfully.            | Confirmation message for successful purchase.                               |
    | 2     | order_id    | 1010101                                       | Unique order identifier. Must be a positive integer.                        |
    | 3     | total_amount| 39.90                                       | Total amount for the order. Positive decimal, max two decimal places.       |


### Error Responses
All error responses have the following structure:

- **Example Error Response:**

    ```json
    {
    "error": {
        "code": 400,
        "message": "Invalid request. Please check the request body or parameters."
    }
    }
    ```

    | Sr No | Key         | Value                                       | Description                                                                 |
    |-------|-------------|---------------------------------------------|-----------------------------------------------------------------------------|
    | 1     | code        | 400                                         | HTTP status code for the error. Must be a valid code (e.g., 400 for Bad Request).|
    | 2     | message     | Invalid request. Please check the request body or parameters. | Error message explaining the issue with the request.                        |


- **Error Codes:**
  

    | **Sr. No.** | **HTTP Status Code** | **Error Type**           | **Description**                                                                 |
    |-------------|----------------------|--------------------------|---------------------------------------------------------------------------------|
    | **1**       | **400**              | Bad Request              | The server could not understand the request due to invalid syntax or parameters.|
    | **2**       | **401**              | Unauthorized             | Authentication failed, likely due to an invalid API key or missing credentials.  |
    | **3**       | **403**              | Forbidden                | The client is authenticated but does not have permission to access the resource.|
    | **4**       | **404**              | Not Found                | The requested resource could not be found on the server.                        |
    | **5**       | **405**              | Method Not Allowed       | The requested HTTP method is not allowed for the resource.                      |
    | **6**       | **408**              | Request Timeout          | The server timed out waiting for the request to be completed.                   |
    | **7**       | **429**              | Too Many Requests        | The user has sent too many requests in a given amount of time ("rate limiting").|
    | **8**       | **500**              | Internal Server Error    | The server encountered an unexpected condition that prevented it from fulfilling the request. |
    | **9**       | **502**              | Bad Gateway              | The server, while acting as a gateway, received an invalid response from the upstream server.|
    | **10**      | **503**              | Service Unavailable      | The server is temporarily unavailable, often due to being overloaded or maintenance.|
    | **11**      | **504**              | Gateway Timeout          | The server, while acting as a gateway, did not receive a timely response from the upstream server.|

### Rate Limiting:

  - Max Requests per Minute: 1000 requests.

  - Response on Rate Limit Exceeded:
  
    ```json
    {
    "error": {
        "code": 429,
        "message": "Too many requests. Please try again later."
    }
    }
    ```


    | Sr No | Key         | Value                                       | Description                                                                 |
    |-------|-------------|---------------------------------------------|-----------------------------------------------------------------------------|
    | 1     | code        | 429                                         | HTTP status code for rate limiting. 429 means Too Many Requests.            |
    | 2     | message     | Too many requests. Please try again later.  | Error message explaining rate limit exceeded.                               |
