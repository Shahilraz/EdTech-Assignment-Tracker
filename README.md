# 📘 EdTech Assignment Tracker

A simplified assignment tracking system for an EdTech platform. This project includes a complete **system design** and a **functional frontend prototype** demonstrating core features like role-based access, assignment creation, and submission tracking.

---

## 🧩 1. Objective

To design and implement a minimal assignment tracking system where:

* **Teachers** can post assignments.
* **Students** can submit solutions.
* Role-based access control ensures secure operations.

---

## 🏗️ 2. System Design

### 2.1 Architecture Overview

* **Client (Frontend):**
  Responsive web interface using **HTML**, **Tailwind CSS**, and **JavaScript**. Handles user interaction and communicates via REST APIs.

* **Server (Backend):**
  RESTful API built with **Python** using frameworks like **Flask**, **FastAPI**, or **Django**. Manages authentication, authorization, and business logic.

* **Database:**
  Relational database (**PostgreSQL** for production or **SQLite** for development) for persistent data storage.

---

### 2.2 Core Entities and Relationships

| Entity         | Fields                                                                 | Description                             |
| -------------- | ---------------------------------------------------------------------- | --------------------------------------- |
| **User**       | `id`, `username`, `password_hash`, `role` (`'teacher'` or `'student'`) | Represents a platform user              |
| **Assignment** | `id`, `title`, `description`, `created_at`, `teacher_id`               | Created by teachers                     |
| **Submission** | `id`, `content`, `submitted_at`, `assignment_id`, `student_id`         | Submitted by students for an assignment |

#### Relationships:

* A **Teacher** can create many **Assignments**.
* An **Assignment** can have many **Submissions**.
* A **Student** can submit multiple **Submissions**.

---

### 2.3 API Endpoint Definitions

#### ✅ Teacher Creates an Assignment

* **Endpoint:** `POST /api/assignments`
* **Role:** Teacher
* **Request Body:**

```json
{
  "title": "Introduction to Python",
  "description": "Write a function that returns 'hello world'."
}
```

---

#### 📝 Student Submits an Assignment

* **Endpoint:** `POST /api/assignments/{assignment_id}/submissions`
* **Role:** Student
* **Request Body:**

```json
{
  "content": "def hello():\n  return 'hello world'"
}
```

---

#### 📂 Teacher Views Submissions

* **Endpoint:** `GET /api/assignments/{assignment_id}/submissions`
* **Role:** Teacher
* **Description:** Fetches all submissions for a specific assignment.

---

### 2.4 Authentication Strategy

* **Token-Based Authentication** using **JWT (JSON Web Tokens)**
* User's role is encoded in the token.
* Backend middleware authorizes access based on role.

---

## 💻 3. Prototype Implementation

A self-contained frontend prototype is provided in the `index.html` file.

### 3.1 Tech Stack

* **HTML5**
* **Tailwind CSS** (Styling)
* **JavaScript (ES6)** (UI logic and mock API simulation)

### 3.2 How to Run the Prototype

1. **Copy** the content of `index.html`.
2. **Create** a file using a code editor (e.g., VS Code).
3. **Paste** the code and save it as `index.html`.
4. **Open in Browser:**

   * Right-click → "Open with Live Server" *(if installed)*
   * Or open `index.html` directly in any browser.

