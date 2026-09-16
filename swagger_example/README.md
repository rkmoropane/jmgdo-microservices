# 🚀 Hands-on Lab: Creating Swagger Documentation for REST API using Python

> **Course:** IBM Full Stack JavaScript Developer Professional Certificate
> **Course 9:** Application Development using Microservices and Serverless
> **Module 2:** Web API Essentials: REST API and GraphQL
> **Lab:** Creating Swagger Documentation for REST API using Python
> **Estimated Time:** 45 minutes

---

## 🎯 Learning Objectives

After completing this lab, you should be able to:

* Use **Swagger Editor** to create Swagger documentation for REST APIs.
* Use **Swagger UI** to access and test REST API endpoints.
* Generate server code using Swagger documentation.
* Build and run a Python Flask REST API using Docker.
* Test REST API endpoints using `curl`.
* Modify an API controller and rebuild a Docker image.

---

## 📚 Prerequisites

Before starting the lab, you should have:

* Basic knowledge of **REST APIs**.
* Familiarity with **Docker** and Docker commands.
* Basic knowledge of **Python**.
* Familiarity with Git and GitHub is helpful.

---

# 📝 Task 1: Create Swagger Documentation for a REST API

## 1. Clone the Repository

Open a terminal:

"Terminal → New Terminal"

Clone the repository containing the REST API and Swagger configuration:

"git clone https://github.com/ibm-developer-skills-network/jmgdo-microservices.git"

---

## 2. Navigate to the Swagger Example

Move into the project directory:

"cd jmgdo-microservices/swagger_example"

---

## 3. Install Required Packages

Install `flask_cors`:

"python3 -m pip install flask_cors"

---

## 4. Start the REST API

Run the Flask application:

"python3 app.py"

The REST API runs on:

"Port 5000"

---

## 5. Open the Application

In Skills Network:

1. Open **Skills Network Toolbox**.
2. Select **Launch Application**.
3. Enter port:

"5000"

4. Select **Your Application**.
5. A browser window will open with the running application.
6. Copy the application URL.

---

## 6. Configure Swagger

Open:

"jmgdo-microservices/swagger_example/swagger_config.json"

Find:

"<Your application URL>"

Replace it with the application URL you copied.

### Important

When entering the URL:

* Do **not** include `https://`.
* Do **not** add `/` at the end.

For example:

"your-application-url.example.com"

Save the file.

---

## 7. Open Swagger Editor

Open the Swagger Editor:

"https://editor.swagger.io/"

In Swagger Editor:

1. Select **File**.
2. Select **Clear Editor**.
3. Copy the complete contents of `swagger_config.json`.
4. Paste the contents into the left-hand editor.
5. If asked:

"Would you like to convert your JSON into YAML?"

Select:

"Cancel"

Swagger UI will automatically appear on the right side.

---

# 🔍 Testing REST API Endpoints with Swagger UI

The application already contains four tasks.

## GET /tasks

Expand:

"GET /tasks"

Select:

"Try it out"

Then select:

"Execute"

This sends a **GET request** to the REST API.

The response is returned as:

"application/json"

You can scroll down to see the API response.

---

## 🧪 Practice the Other Endpoints

Use Swagger UI to practice the following operations:

### 1. Add a Task

Use the appropriate endpoint to create a new task.

### 2. Retrieve Tasks

Call:

"GET /tasks"

Verify that the new task appears in the task list.

### 3. Get Task Details

Use the endpoint for retrieving an individual task.

Verify that the correct task information is returned.

### 4. Delete a Task

Use the delete endpoint to remove a task.

Then call:

"GET /tasks"

Verify that the deleted task no longer appears.

---

## 🧹 Clear Swagger Editor

After completing the REST API testing:

"Edit → Clear Editor"

This prepares Swagger Editor for the next task.

---

# 🐳 Task 2: Build and Run Greetings API with Docker

In this task, you will run a Python Flask REST API inside a Docker container.

The API provides greetings in different languages.

---

## 1. Navigate to `/home/project`

Open a new terminal:

"cd /home/project"

---

## 2. Download the Generated Flask Server

Run:

"wget -O python-flask-server-generated.zip "https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/me5rJsBIv8MNqFSyBk5g6Q/python-flask-server-generated.zip""

---

## 3. Verify the Download

Check that the ZIP file exists:

"ls python-flask-server-generated.zip"

---

## 4. Extract the Server

Extract the ZIP file into a directory:

"unzip python-flask-server-generated.zip -d python-flask-server-generated/"

---

## 5. Navigate to the Server Directory

Run:

"cd python-flask-server-generated/python-flask-server-generated/python-flask-server-generated"

---

# 🏗️ Build the Docker Image

Build the Docker image and give it the tag `mynewserver`:

"docker build . -t mynewserver"

If successful, Docker creates an image called:

"mynewserver"

> ⏳ The Docker build may take some time.

---

# ▶️ Run the Docker Container

Start the application:

"docker run -dp 8080:8080 mynewserver"

The API is configured to run on port `8080`.

---

# 🔌 Test the REST API

Use `curl` to call the greetings endpoint:

"curl localhost:8080/greetings"

At this point, the API initially returns:

"do some magic!"

This means that the endpoint exists, but the actual response still needs to be implemented.

---

# 🔎 Troubleshooting Docker

If the API does not work, first check the container status:

"docker ps -a"

Look at:

* **STATUS**
* **EXIT CODE**
* **PORTS**

A correctly running container should show a port mapping similar to:

"0.0.0.0:8080->8080/tcp"

This means:

"Host port 8080 → Container port 8080"

---

## Start the Container with Port Mapping

If the container was not started correctly, run:

"docker run --rm -p 8080:8080 mynewserver"

Then test:

"curl localhost:8080/greetings"

---

# 🛑 Stop the Docker Container

Find the running container:

"docker ps | grep mynewserver"

Copy the **container ID**.

Then stop the container:

"docker kill <container_id>"

---

# 👨‍💻 Implement the Greetings Response

Navigate to:

"python-flask-server-generated/python-flask-server/swagger_server/controllers/hello_in_different_languages_controller.py"

Find:

"return 'do some magic!'"

Replace it with a dictionary containing greetings in different languages:

"hellos = {
"English": "hello",
"Hindi": "namastey",
"Spanish": "hola",
"French": "bonjour",
"German": "guten tag",
"Italian": "salve",
"Chinese": "nǐn hǎo",
"Portuguese": "olá",
"Arabic": "asalaam alaikum",
"Japanese": "konnichiwa",
"Korean": "anyoung haseyo",
"Russian": "Zdravstvuyte"
}

return hellos"

### Complete Function

The controller should look similar to:

"import connexion
import six

from swagger_server import util

def greetings_get():  # noqa: E501
"""Returns a list of greetings in different languages.

```
:rtype: dict
"""
hellos = {
    "English": "hello",
    "Hindi": "namastey",
    "Spanish": "hola",
    "French": "bonjour",
    "German": "guten tag",
    "Italian": "salve",
    "Chinese": "nǐn hǎo",
    "Portuguese": "olá",
    "Arabic": "asalaam alaikum",
    "Japanese": "konnichiwa",
    "Korean": "anyoung haseyo",
    "Russian": "Zdravstvuyte"
}

return hellos"
```

> ⚠️ Python uses indentation to define code blocks. Make sure the indentation is correct.

---

# 🔄 Rebuild the Docker Image

Because the Python code has changed, rebuild the Docker image:

"docker build . -t mynewserver"

The new Docker image now contains the updated application code.

---

# ▶️ Run the Updated Container

Run the container without detached mode:

"docker run -p 8080:8080 mynewserver"

### Why use `-p` instead of `-dp`?

`-p` exposes the port while keeping the application attached to the terminal.

This allows you to see errors and application output directly.

---

# 🌐 Test the Greetings API

Open:

"Skills Network Toolbox → Launch Application"

Enter:

"8080"

Select:

"Your Application"

Then append:

"/greetings"

to the application URL.

The endpoint should return greetings similar to:

"{
"English": "hello",
"Hindi": "namastey",
"Spanish": "hola",
"French": "bonjour",
"German": "guten tag",
"Italian": "salve",
"Chinese": "nǐn hǎo",
"Portuguese": "olá",
"Arabic": "asalaam alaikum",
"Japanese": "konnichiwa",
"Korean": "anyoung haseyo",
"Russian": "Zdravstvuyte"
}"

---

# 🧠 Key Concepts Learned

## REST API

A **REST API** allows applications to communicate over HTTP using standard HTTP methods such as:

* `GET` — retrieve data.
* `POST` — create data.
* `PUT` — update data.
* `DELETE` — remove data.

---

## Swagger

**Swagger** is a collection of tools used to describe, document, test, and work with REST APIs.

In this lab, Swagger was used to:

* Describe REST API endpoints.
* Display API documentation.
* Test API requests.
* View API responses.
* Generate API server code.

---

## Swagger Editor

**Swagger Editor** allows you to create and edit API specifications.

It provides a visual interface where:

"API specification → Swagger UI documentation"

---

## Swagger UI

Swagger UI provides an interactive web interface for REST APIs.

It allows developers to:

1. View available endpoints.
2. View request parameters.
3. Click **Try it out**.
4. Execute API requests.
5. View API responses.

---

## Docker

Docker packages an application and its dependencies into a container.

Important commands from this lab:

"docker build . -t mynewserver"

"docker run -dp 8080:8080 mynewserver"

"docker ps -a"

"docker kill <container_id>"

---

## Docker Port Mapping

The syntax:

"-p 8080:8080"

means:

"Host Port : Container Port"

Therefore:

"8080 → 8080"

allows requests sent to port `8080` on the host to reach port `8080` inside the container.

---

## curl

`curl` can be used to test HTTP endpoints from the terminal.

Example:

"curl localhost:8080/greetings"

---

# 📌 Important Commands Cheat Sheet

| Purpose                | Command                                                                             |
| ---------------------- | ----------------------------------------------------------------------------------- |
| Clone repository       | "git clone https://github.com/ibm-developer-skills-network/jmgdo-microservices.git" |
| Enter project          | "cd jmgdo-microservices/swagger_example"                                            |
| Install Flask CORS     | "python3 -m pip install flask_cors"                                                 |
| Start Flask app        | "python3 app.py"                                                                    |
| Download server        | "wget -O python-flask-server-generated.zip ..."                                     |
| Extract ZIP            | "unzip python-flask-server-generated.zip -d python-flask-server-generated/"         |
| Build Docker image     | "docker build . -t mynewserver"                                                     |
| Run detached container | "docker run -dp 8080:8080 mynewserver"                                              |
| Run attached container | "docker run -p 8080:8080 mynewserver"                                               |
| List containers        | "docker ps -a"                                                                      |
| Find server container  | "docker ps | grep mynewserver"                                                      |
| Stop container         | "docker kill <container_id>"                                                        |
| Test API               | "curl localhost:8080/greetings"                                                     |

---

# ✅ Lab Completion Checklist

* [ ] Cloned the `jmgdo-microservices` repository.
* [ ] Started the Flask REST API.
* [ ] Configured `swagger_config.json`.
* [ ] Opened Swagger Editor.
* [ ] Loaded the Swagger specification.
* [ ] Tested `GET /tasks`.
* [ ] Added a task.
* [ ] Retrieved the task list.
* [ ] Retrieved individual task details.
* [ ] Deleted a task.
* [ ] Downloaded the generated Flask server.
* [ ] Built the Docker image.
* [ ] Started the Docker container.
* [ ] Tested `/greetings` using `curl`.
* [ ] Checked Docker container status.
* [ ] Updated `hello_in_different_languages_controller.py`.
* [ ] Rebuilt the Docker image.
* [ ] Ran the updated container.
* [ ] Tested `/greetings` through the browser.
* [ ] Confirmed that greetings are returned in multiple languages.

---

# 💡 Final Takeaway

This lab demonstrates a complete workflow for working with a REST API:

"REST API → Swagger Documentation → Swagger UI → API Testing → Generated Flask Server → Docker Image → Docker Container → REST API"

The key idea is that **Swagger makes REST APIs easier to document, understand, test, and generate code for**, while **Docker makes it easier to package and run the application consistently**.
