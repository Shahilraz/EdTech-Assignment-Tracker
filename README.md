# EdTech-Assignment-Tracker
This project is a solution to the EdTech Assignment Tracker problem. It includes a comprehensive system design and a functional frontend prototype that demonstrates the core features of the application.

1. Objective
To design and implement a simplified assignment tracking system for an EdTech platform that allows teachers to post assignments and students to submit them, with clear role-based access control.

2. System Design
2.1. System Architecture
The system is designed using a Client-Server Architecture.

Client (Frontend): A responsive web interface built with HTML, CSS (Tailwind CSS), and JavaScript. It handles user interaction and communicates with the backend via API calls.

Server (Backend): A RESTful API responsible for business logic, user authentication, and database operations. The proposed backend framework is Python (Flask, FastAPI, or Django).

Database: A relational database (like PostgreSQL for production or SQLite for development) to persist data.

2.2. Core Entities and Relationships
Entity

Fields

Description

User

id (PK)<br>username<br>password_hash<br>role ('teacher', 'student')

Represents a user of the platform.

Assignment

id (PK)<br>title<br>description<br>created_at<br>teacher_id (FK -> User.id)

Represents an assignment created by a teacher.

Submission

id (PK)<br>content<br>submitted_at<brassignment_id (FK -> Assignment.id)<br>student_id (FK -> User.id)

Represents a student's submission for an assignment.

Relationships:

A Teacher can create many Assignments. (One-to-Many)

An Assignment can have many Submissions. (One-to-Many)

A Student can make many Submissions. (One-to-Many)

2.3. API Endpoint Definitions
Teacher Creates an Assignment
Endpoint: POST /api/assignments

Role: Teacher

Description: Creates a new assignment.

Request Body:

{
  "title": "Introduction to Python",
  "description": "Write a function that returns 'hello world'."
}

Student Submits an Assignment
Endpoint: POST /api/assignments/{assignment_id}/submissions

Role: Student

Description: Submits a solution for a specific assignment.

Request Body:

{
  "content": "def hello():\n  return 'hello world'"
}

Teacher Views Submissions for an Assignment
Endpoint: GET /api/assignments/{assignment_id}/submissions

Role: Teacher

Description: Retrieves all submissions for a specific assignment.

2.4. Authentication Strategy
The system uses Token-Based Authentication with JSON Web Tokens (JWT). The user's role ('teacher' or 'student') is encoded into the JWT upon login, and this role is used by the backend middleware to authorize access to protected API endpoints.

3. Prototype Implementation
A fully functional, self-contained prototype is provided in the index.html file.

3.1. Technology Stack
HTML5

Tailwind CSS (for styling)

JavaScript (ES6) (for UI logic and API simulation)

3.2. How to Run the Prototype
Copy the Code: Copy the entire content of the index.html file.

Create a File: Open a code editor like VS Code and create a new file.

Paste and Save: Paste the code and save the file as index.html.

Open in Browser: Right-click the file and choose "Open with Live Server" (if you have the VS Code extension) or simply open the index.html file directly in your web browser (like Chrome or Firefox).

4. Future Scaling
The system can be scaled in the future through:

Database Optimization: Migrating to a production-grade database like PostgreSQL and using read replicas.

Microservices Architecture: Breaking down the application into smaller services (e.g., Auth Service, Assignment Service).

Asynchronous Processing: Using a message queue (e.g., RabbitMQ) for handling time-consuming tasks like file uploads for submissions.

Containerization: Using Docker and Kubernetes for automated deployment, scaling, and management.

Content Delivery Network (CDN): Caching static assets to reduce latency for users.
