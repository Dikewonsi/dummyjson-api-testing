# DummyJSON API Testing Project

This project documents API testing work carried out on selected modules from the
[DummyJSON API](https://dummyjson.com/): Products, Carts, and Posts.

The goal was to practice a realistic API testing workflow using Postman and a
test case spreadsheet. The project covers positive tests, negative tests, edge
cases, and nested endpoints.

## Modules Tested

- Products
- Carts
- Posts

## Tools Used

- Postman
- DummyJSON REST API
- JSON
- Excel / CSV
- Git and GitHub

## Project Structure

```text
.
├── data/
│   ├── carts.js
│   ├── posts.js
│   └── products.js
├── excel/
│   ├── dummyjson-all-test-cases.csv
│   └── dummyjson-all-test-cases.xlsx
├── postman/
│   ├── dummyjson-carts.postman_collection.json
│   ├── dummyjson-posts.postman_collection.json
│   └── dummyjson-products.postman_collection.json
└── README.md
```

## What Was Tested

### Products

- `GET /products`
- `GET /products/:id`
- `GET /products/search?q=phone`
- `GET /products/category/smartphones`
- `POST /products/add`
- `PUT /products/:id`
- `PATCH /products/:id`
- `DELETE /products/:id`
- Negative and edge cases such as invalid product IDs, invalid POST body data,
  `limit=0`, `limit=1000`, `skip=-1`, and empty search query.

### Carts

- `GET /carts`
- `GET /carts/:id`
- `GET /carts/user/:userId`
- `POST /carts/add`
- `PUT /carts/:id`
- `PATCH /carts/:id`
- `DELETE /carts/:id`
- Negative and edge cases such as invalid cart IDs, invalid user IDs, empty POST
  body, invalid product data types, `limit=0`, `limit=1000`, and `skip=-1`.

### Posts

- `GET /posts`
- `GET /posts/:id`
- `GET /posts/search?q=love`
- `GET /posts/tags`
- `GET /posts/tag-list`
- `GET /posts/tag/:tag`
- `GET /posts/user/:userId`
- `GET /posts/:id/comments`
- `POST /posts/add`
- `PUT /posts/:id`
- `PATCH /posts/:id`
- `DELETE /posts/:id`
- Negative and edge cases such as invalid post IDs, invalid user IDs, invalid
  tags, empty POST body, invalid user ID data type, `limit=0`, `limit=1000`,
  `skip=-1`, and empty search query.

## Test Case Spreadsheet

The combined spreadsheet is available at:

```text
excel/dummyjson-all-test-cases.xlsx
```

It contains test cases for Products, Carts, and Posts with the following fields:

- Test Case ID
- Module
- Description
- Preconditions
- Steps
- Test Data
- Expected Result
- Actual Result
- Status

## Postman Collections

Each module has its own Postman collection:

```text
postman/dummyjson-products.postman_collection.json
postman/dummyjson-carts.postman_collection.json
postman/dummyjson-posts.postman_collection.json
```

Each collection includes folders for:

- GET endpoints
- POST endpoints
- PUT/PATCH endpoints
- DELETE endpoints
- Nested endpoints
- Negative tests
- Edge cases

## How To Run The Tests

1. Open Postman.
2. Click **Import**.
3. Import any collection from the `postman/` folder.
4. Run requests individually or use the Postman Collection Runner.
5. Compare Postman results with the expected and actual results documented in
   `excel/dummyjson-all-test-cases.xlsx`.

## Key Observations

- DummyJSON uses mock write operations, so POST, PUT, PATCH, and DELETE requests
  simulate changes but do not permanently modify the database.
- Some invalid category/tag requests return `200 OK` with an empty result set
  instead of returning `404 Not Found`.
- `limit=0` and very large limits return all available records for the tested
  modules.
- Negative `skip` values are accepted and echoed back by the API.
- Posts and Carts validate some invalid POST payloads more strictly than
  Products.

## Purpose

This project demonstrates practical API testing skills, including endpoint
coverage, test documentation, validation of actual API behavior, negative
testing, edge-case testing, and organizing test artifacts for portfolio review.
