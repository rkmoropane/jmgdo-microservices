# 🛠️ Hands-on Lab — CRUD Operations Using Python

## 📌 Overview

This hands-on lab focuses on implementing **CRUD operations** using **Python, Flask, REST APIs, cURL, and Postman**.

You will create a Flask server that manages a list of products. The REST API will allow clients to:

* ➕ Add a product
* 📋 Retrieve all products
* 🔍 Retrieve a specific product by ID
* ✏️ Update a specific product by ID
* 🗑️ Delete a product by ID

The lab uses **transient data**, meaning the products are stored temporarily while the Flask application is running rather than being persisted in a database.

---

## ⏱️ Estimated Time

**45 minutes**

---

# 🎯 Objectives

After completing this lab, you should be able to:

* Create API endpoints for **Create, Retrieve, Update, and Delete** operations.
* Work with transient product data using a Flask server.
* Create REST API endpoints using Python and Flask.
* Test REST APIs using **cURL**.
* Test REST APIs using **Postman**.
* Understand how HTTP methods map to CRUD operations.

---

# 🧠 Concepts Covered

This lab combines several concepts covered in the module:

* REST APIs
* Flask
* Python
* HTTP methods
* CRUD operations
* JSON
* REST API endpoints
* cURL
* Postman
* Transient data
* HTTP request/response cycle

---

# 🔄 CRUD Operations

CRUD represents the four fundamental operations performed on data:

| CRUD Operation | HTTP Method | Purpose                    |
| -------------- | ----------- | -------------------------- |
| **Create**     | `POST`      | Add a new product          |
| **Read**       | `GET`       | Retrieve products          |
| **Update**     | `PUT`       | Modify an existing product |
| **Delete**     | `DELETE`    | Remove a product           |

### 🧠 Memory Trick

"POST → Create"

"GET → Read"

"PUT → Update"

"DELETE → Delete"

---

# 🏗️ Application Architecture

The basic architecture for the lab is:

"Client
|
| HTTP Request
v
Flask REST API
|
v
Product List
|
| HTTP Response
v
Client"

The client can be:

* cURL
* Postman
* Another application
* A web application

---

# 🚀 Project Setup

## 1. Open a Terminal

In the development environment, open:

"Terminal → New Terminal"

---

## 2. Navigate to the Project Directory

Change to the project directory:

"cd /home/project"

---

## 3. Clone the Starter Repository

Clone the repository containing the starter code if it does not already exist:

"[ ! -d 'jmgdo-microservices' ] && git clone https://github.com/ibm-developer-skills-network/jmgdo-microservices.git"

### Repository

The starter repository contains the code required for the lab.

The relevant lab directory is:

"jmgdo-microservices/CRUD"

---

## 4. Navigate to the CRUD Directory

"cd jmgdo-microservices/CRUD"

This is the directory where you will work on the CRUD application.

---

## 5. Inspect the Directory

List the contents of the directory:

"ls"

Review the available files and starter code before beginning the implementation.

---

# 📦 Install Dependencies

Install Flask and Flask-CORS using pip:

"python3 -m pip install flask flask_cors"

### Packages

| Package        | Purpose                                        |
| -------------- | ---------------------------------------------- |
| **Flask**      | Used to create and host the REST API           |
| **Flask-CORS** | Provides Cross-Origin Resource Sharing support |

---

# 🛍️ Product API

The application manages a list of products.

Each product contains information such as:

* `id`
* `name`
* `price`

Example product:

"{
"id": 146,
"name": "Laptop Bag",
"price": 45.00
}"

---

# 🌐 REST API Operations

The Flask application should provide endpoints that support the following operations.

## 📋 1. Retrieve All Products

### HTTP Method

"GET"

### Purpose

Retrieve the complete list of products.

---

## 🔍 2. Retrieve a Specific Product

### HTTP Method

"GET"

### Purpose

Retrieve a specific product using its ID.

### Example

"GET /products/146"

This should return the product whose ID is `146`.

---

## ➕ 3. Add a Product

### HTTP Method

"POST"

### Purpose

Add a new product to the product list.

### Example JSON Body

"{
"id": 146,
"name": "Laptop Bag",
"price": 45.00
}"

---

## ✏️ 4. Update a Product

### HTTP Method

"PUT"

### Purpose

Update information belonging to an existing product.

The product ID is included in the URL.

### Example

"PUT /products/146"

Example request body:

"{
"price": 42.00
}"

This changes the price of product `146` to `42.00`.

---

## 🗑️ 5. Delete a Product

### HTTP Method

"DELETE"

### Purpose

Remove a specific product from the product list.

### Example

"DELETE /products/142"

This deletes the product with ID `142`.

---

# 📮 Testing with Postman

The lab uses **Postman** to test REST API endpoints.

While `GET` requests are relatively easy to test using cURL, requests such as:

* `POST`
* `PUT`
* `DELETE`

can be more convenient to test using Postman.

---

# 🌐 Postman Setup

Postman is an external application/service, so it needs access to the running Flask server.

### Steps

1. Launch the application/server.
2. Obtain the URL provided by the development environment.
3. Copy the URL.
4. Open Postman.
5. Sign up or log in if required.
6. Create a new HTTP request.

---

# 🆕 Creating a Postman Request

In Postman:

1. Select **Create New**.
2. Choose **HTTP Request**.
3. Paste the server URL into the request address bar.
4. Select the appropriate HTTP method.
5. Configure the request body when required.
6. Click **Send**.
7. Inspect the response.

---

# ➕ Testing POST

Use `POST` to add a new product.

### Request Method

"POST"

### Request Body

Set the body to:

"Body → raw → JSON"

Use the following JSON:

"{
"id": 146,
"name": "Laptop Bag",
"price": 45.00
}"

Click **Send**.

### Verify

After sending the request, perform a `GET` request to retrieve the products and verify that the new product has been added.

---

# 📋 Verifying the Product List

Change the request method to:

"GET"

Remove the JSON request body if one is present.

Click **Send**.

Inspect the response and verify that the newly added product appears in the product list.

---

# ✏️ Testing PUT

The lab requires updating the product with ID `146`.

### Objective

Change the price from:

"45.00"

to:

"42.00"

### Request Method

"PUT"

### Endpoint

"PUT /products/146"

### Request Body

"{
"price": 42.00
}"

Click **Send**.

---

# 🔍 Verify the PUT Operation

After updating the product:

1. Change the request method to `GET`.
2. Request the product with ID `146`.
3. Inspect the response.
4. Verify that the price has changed to `42.00`.

---

# 🧪 Practice Tasks

After completing the guided exercises, complete the following tasks independently.

## 📝 Task 1 — Update Product

Update the product with ID `144`.

### Requirement

Change its price to:

"2.50"

### HTTP Method

"PUT"

### Endpoint

"PUT /products/144"

---

## 📝 Task 2 — Add Product

Add the following product using the **POST** method:

"{
"id": 142,
"name": "Eraser",
"price": 1.50
}"

### HTTP Method

"POST"

### Requirement

The new product should have:

| Field     | Value    |
| --------- | -------- |
| **ID**    | `142`    |
| **Name**  | `Eraser` |
| **Price** | `1.50`   |

---

## 📝 Task 3 — Delete Product

Delete the product with ID `142`.

### HTTP Method

"DELETE"

### Endpoint

"DELETE /products/142"

---

# 🧪 Testing Checklist

Use this checklist when completing the lab:

* [ ] Clone the starter repository.
* [ ] Navigate to the `CRUD` directory.
* [ ] Install Flask and Flask-CORS.
* [ ] Review the starter code.
* [ ] Start the Flask server.
* [ ] Verify the API is accessible.
* [ ] Test `GET` for all products.
* [ ] Test `GET` for a specific product.
* [ ] Test `POST` to add a product.
* [ ] Verify the new product using `GET`.
* [ ] Test `PUT` to update a product.
* [ ] Verify the updated product using `GET`.
* [ ] Test `DELETE` to remove a product.
* [ ] Verify the product was deleted.
* [ ] Complete all three practice tasks.
* [ ] Test the endpoints using Postman.

---

# 📊 CRUD Endpoint Reference

| Operation | HTTP Method | Example Endpoint | Purpose               |
| --------- | ----------- | ---------------- | --------------------- |
| Create    | `POST`      | `/products`      | Add a product         |
| Read All  | `GET`       | `/products`      | Retrieve all products |
| Read One  | `GET`       | `/products/146`  | Retrieve product 146  |
| Update    | `PUT`       | `/products/146`  | Update product 146    |
| Delete    | `DELETE`    | `/products/142`  | Delete product 142    |

---

# 🧠 Important Concepts to Remember

### REST API

A REST API allows clients to interact with resources using HTTP methods.

### Flask

Flask is the Python micro web framework used to host the REST API.

### Endpoint

An endpoint is a specific URL through which an API provides functionality.

### JSON

JSON is used to represent product data in API requests and responses.

### Transient Data

The product data is stored temporarily rather than in a database.

Therefore:

"Application starts
↓
Products loaded into memory
↓
CRUD operations performed
↓
Application stops
↓
Data is lost"

---

# 🎯 Lab Outcome

By the end of this lab, you should have a Flask REST API capable of performing:

"CREATE → POST"

"READ → GET"

"UPDATE → PUT"

"DELETE → DELETE"

You should also be comfortable testing these endpoints using **Postman** and **cURL**.

---

# 🏆 Key Takeaway

> **This lab demonstrates how to build and test a basic CRUD REST API using Python and Flask. The API exposes endpoints that allow clients to create, retrieve, update, and delete product data. Postman and cURL can then be used to send HTTP requests and verify that each endpoint works correctly.**

### 🔑 Remember

"POST → Create"

"GET → Read"

"PUT → Update"

"DELETE → Delete"

"Flask → Python REST API"

"Postman → API Testing"

"cURL → Command-line API Requests"

"Transient Data → Data is not persisted after the application stops"
