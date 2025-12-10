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
