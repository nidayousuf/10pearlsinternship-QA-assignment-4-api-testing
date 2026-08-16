# API Testing Project – JSONPlaceholder

## Project Overview

This project demonstrates **API functional testing using Postman** and **basic performance testing using Apache JMeter**.

The API used for this assignment is **JSONPlaceholder**, a free fake REST API designed for testing and learning API interactions.

The project covers:

* Testing REST API endpoints
* Validating HTTP status codes
* Validating response data and structure
* Writing automated Postman test scripts
* Organizing requests using a Postman Collection
* Performing basic load testing using Apache JMeter
* Analyzing response time, throughput, and error rate

---

## API Under Test

**Base URL:**

`https://jsonplaceholder.typicode.com`

JSONPlaceholder provides sample resources such as posts, comments, albums, users, and more.

---

## Project Structure

```text
API-Testing-Assignment/
│
├── Postman/
│   ├── JSONPlaceholder_API_Testing.postman_collection.json
│
├── JMeter/
│   ├── JSONPlaceholder_Performance_Test.jmx
│   ├── JMeter_Summary_Report.xlsx
│   ├── JMeter_Summary_Report.png
│   └── JMeter_View_Results.png
│
└── README.md
```

---

#  Postman API Testing

## 1. GET – Retrieve All Posts

**Method:** `GET`

**Endpoint:**

```text
https://jsonplaceholder.typicode.com/posts
```

### Validations

The response was validated for:

* HTTP status code `200`
* Response time
* JSON response structure
* Presence of required fields:

  * `id`
  * `title`
  * `body`
  * `userId`

---

## 2. GET – Retrieve a Single Post

**Method:** `GET`

**Endpoint:**

```text
https://jsonplaceholder.typicode.com/posts/1
```

### Expected Response

The response should contain:

```json
{
  "userId": 1,
  "id": 1,
  "title": "...",
  "body": "..."
}
```

The automated tests verify the response status, structure, and required field values.

---

# POST – Create a New Post

**Method:** `POST`

**Endpoint:**

```text
https://jsonplaceholder.typicode.com/posts
```

### Request Body

```json
{
  "title": "API Testing",
  "body": "Testing POST API using Postman",
  "userId": 1
}
```

### Validations

The following were validated:

* Status code `201`
* Response time
* Response JSON structure
* Presence of `id`
* `title` value
* `body` value
* `userId` value

> JSONPlaceholder simulates creation of a resource. The data is not permanently stored on the server.

---

# PUT – Update an Existing Post

**Method:** `PUT`

**Endpoint:**

```text
https://jsonplaceholder.typicode.com/posts/1
```

### Request Body

```json
{
  "id": 1,
  "title": "Updated API Testing Post",
  "body": "This post has been updated using PUT",
  "userId": 1
}
```

### Validations

* Status code `200`
* Response time
* Response structure
* Updated `id`
* Updated `title`
* Updated `body`
* `userId`

---

# DELETE – Delete a Post

**Method:** `DELETE`

**Endpoint:**

```text
https://jsonplaceholder.typicode.com/posts/1
```

### Validations

* Status code `200`
* Response time
* Successful deletion response

---

# Automated Postman Tests

Automated tests were added to the **Tests** section of the Postman requests.

The tests cover:

### Status Code Validation

Verifies that each endpoint returns the expected HTTP status code.

### Response Time Validation

Checks that the API responds within the defined acceptable response time.

### Response Structure Validation

Verifies that the response contains the expected JSON structure.

### Response Field Validation

Checks important fields such as:

```text
id
title
body
userId
```

These tests allow the API requests to be validated automatically instead of checking every response manually.

---

# JMeter Performance Testing

A basic load test was created using **Apache JMeter**.

## Test Configuration

| Setting         |     Value |
| --------------- | --------: |
| Threads / Users |        10 |
| Ramp-Up Period  | 5 seconds |
| Loop Count      |         5 |
| Total Requests  |        50 |

The test simulates multiple users sending requests to the API.

## JMeter Components

The test plan contains:

1. Thread Group
2. HTTP Request Sampler
3. View Results Tree
4. Summary Report

### HTTP Request

The configured API endpoint is:

```text
https://jsonplaceholder.typicode.com/posts/1
```

---

# Performance Metrics

The JMeter results were analyzed using the following metrics:

### Response Time

Measures how long the API takes to respond to a request.

### Throughput

Measures the number of requests processed over a period of time.

### Error Rate

Shows the percentage of requests that failed during the test.

### Results

The actual performance results and screenshots are included in the `Screenshots/` directory.

---

# How to Run the Project

## Postman

1. Install and open Postman.
2. Import the collection from the `Postman/` directory.
3. If an environment file is included, import it into Postman.
4. Select the imported environment.
5. Open the collection.
6. Run individual requests or use the **Collection Runner**.
7. Review the automated test results.

## JMeter

1. Install Apache JMeter.
2. Open the `.jmx` file from the `JMeter/` directory.
3. Review the Thread Group configuration.
4. Make sure the HTTP Request Sampler is configured correctly.
5. Start the test.
6. Review the **View Results Tree** and **Summary Report**.
7. Analyze response time, throughput, and error rate.

---

# Submission Contents

This repository contains:

* ✅ Postman Collection
* ✅ Postman Environment (if used)
* ✅ JMeter Test Plan (`.jmx`)
* ✅ JMeter result screenshots/reports
* ✅ README documentation

---

