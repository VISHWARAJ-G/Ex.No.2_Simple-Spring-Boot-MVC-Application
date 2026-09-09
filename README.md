# Exp 02 - Simple Spring Boot MVC Application

# Name: Vishwaraj G
# Register Number: 212223220125

## AIM

To develop a simple Spring Boot MVC (Model-View-Controller) application that uses a **Controller** to handle HTTP requests, a **Model** to pass data, and a **View (Thymeleaf)** to render dynamic HTML pages.

---

## ALGORITHM

### Step 1: Create a New Spring Boot Project

Use **Spring Initializr** to create a new Spring Boot project.

Add the following dependencies:

* Spring Web
* Thymeleaf

### Step 2: Set Up the Project Structure

Create the main application class and annotate it with `@SpringBootApplication`.

Create a Controller class using the `@Controller` annotation.

Create HTML templates inside:

```text
src/main/resources/templates
```

### Step 3: Create the Controller

Create a Controller class and define a method to handle HTTP GET requests using `@GetMapping`.

The controller method should:

1. Receive the HTTP request.
2. Add data to the `Model` object.
3. Return the name of the view.

### Step 4: Pass Data Using Model

Use the `Model` object to pass data from the Controller to the View.

For example:

```java
model.addAttribute("message", "Welcome to Spring Boot MVC!");
```

The attribute can then be accessed in the Thymeleaf HTML page.

### Step 5: Create the View

Create an HTML file inside:

```text
src/main/resources/templates
```

Use **Thymeleaf** syntax to display dynamic content.

For example:

```html
<h1 th:text="${message}">Default Message</h1>
```

### Step 6: Run the Application

Run the Spring Boot application from the IDE or using the command line.

```bash
mvn spring-boot:run
```

### Step 7: Access the Application

Open a web browser and navigate to:

```text
http://localhost:8081/
```

The dynamic message should be displayed on the webpage.

---

## PROGRAM

### Project Structure

```text
spring-mvc-demo/
│
├── src/
│   └── main/
│       ├── java/
│       │   └── com/
│       │       └── example/
│       │           └── mvc/
│       │               ├── MvcApplication.java
│       │               └── HomeController.java
│       │
│       └── resources/
│           ├── templates/
│           │   └── index.html
│           │
│           └── application.properties
│
└── pom.xml
```

---

### 1. pom.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
                             https://maven.apache.org/xsd/maven-4.0.0.xsd">

    <modelVersion>4.0.0</modelVersion>

    <parent>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-parent</artifactId>
        <version>3.1.2</version>
        <relativePath/>
    </parent>

    <groupId>com.example</groupId>
    <artifactId>spring-mvc-demo</artifactId>
    <version>0.0.1-SNAPSHOT</version>

    <name>Spring MVC Demo</name>

    <dependencies>

        <!-- Spring Web -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-web</artifactId>
        </dependency>

        <!-- Thymeleaf for View Rendering -->
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-starter-thymeleaf</artifactId>
        </dependency>

    </dependencies>

    <build>
        <plugins>

            <!-- Spring Boot Maven Plugin -->
            <plugin>
                <groupId>org.springframework.boot</groupId>
                <artifactId>spring-boot-maven-plugin</artifactId>
            </plugin>

        </plugins>
    </build>

</project>
```

---

### 2. MvcApplication.java

**Main Application Class**

```java
package com.example.mvc;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class MvcApplication {

    public static void main(String[] args) {
        SpringApplication.run(MvcApplication.class, args);
    }
}
```

---

### 3. HomeController.java

**Controller**

```java
package com.example.mvc;

import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.GetMapping;

@Controller
public class HomeController {

    @GetMapping("/")
    public String homePage(Model model) {

        model.addAttribute(
            "message",
            "Welcome to Spring Boot MVC!"
        );

        return "index";
    }
}
```

> `return "index";` refers to the `index.html` file inside the `templates` folder.

---

### 4. index.html

**View – `src/main/resources/templates/index.html`**

```html
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">

<head>
    <title>Spring MVC</title>
</head>

<body>

    <h1 th:text="${message}">Default Message</h1>

</body>

</html>
```

---

### 5. application.properties

```properties
server.port=8081
```

---

## MVC FLOW

The application follows the Spring Boot MVC architecture:

```text
User / Browser
      │
      │ GET /
      ▼
HomeController
      │
      │ Adds "message" to Model
      ▼
Model
      │
      │ Passes data
      ▼
Thymeleaf View
(index.html)
      │
      │ Renders HTML
      ▼
User / Browser
```

### Explanation

1. The user accesses `http://localhost:8081/`.
2. The request is handled by `HomeController`.
3. The Controller adds the `message` attribute to the `Model`.
4. The Controller returns the view name `index`.
5. Thymeleaf locates `index.html` inside the `templates` folder.
6. Thymeleaf replaces `${message}` with the value provided by the Controller.
7. The generated HTML page is returned to the browser.

---

## OUTPUT

### URL

```text
http://localhost:8081/
```

### Expected Output

```text
Welcome to Spring Boot MVC!
```

### Browser Output

![Spring Boot MVC Output](https://github.com/user-attachments/assets/5c2946d9-55a0-4b05-80ea-bb244ff431ad)

---

## RESULT

Thus, a **Simple Spring Boot MVC Application** was successfully created using **Spring Web, Thymeleaf, Controller, Model, and View** to render dynamic HTML content.
