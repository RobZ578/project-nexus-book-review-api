# Project Nexus: Book Review API

## 🚀 Overview
This project, **Project Nexus**, is a secure and performant **RESTful API** built with **Django** and **Django REST Framework (DRF)**. It functions as a backend for a comprehensive book review and rating platform, allowing users to register, manage book data, and submit/edit reviews.

It is designed to demonstrate mastery of backend best practices, including secure authentication, optimized database design (3NF), conditional caching, and professional API documentation using the **OpenAPI Specification (Swagger)**.

---

## 💡 Key Features & Endpoints

| Feature | HTTP Method | Endpoint | Authentication | Description |
| :--- | :--- | :--- | :--- | :--- |
| **User Auth** | `POST` | `/api/token/` | None | Obtain JWT Access and Refresh Tokens |
| **User Auth** | `POST` | `/api/token/refresh/` | None | Refresh an expired Access Token |
| **Books** | `GET` | `/api/books/` | Optional | Retrieve a list of all books (supports caching) |
| **Reviews** | `POST` | `/api/reviews/` | Required | Create a new review for a book |
| **Reviews** | `GET, PATCH, DELETE` | `/api/reviews/{id}/` | Required (Owner) | Manage a specific review |

---

## 🛠 Tech Stack

* **Backend Framework:** Python 3.10+ / Django 4.2+
* **API Framework:** Django REST Framework (DRF)
* **Database:** PostgreSQL (for production/deployment) / SQLite (for local development)
* **Authentication:** JWT (JSON Web Tokens) using `djangorestframework-simplejwt`
* **Caching:** Redis (`django-redis`) for server-side caching
* **Documentation:** OpenAPI 3.0 via `drf-spectacular`

---

## ⚙️ Local Setup and Installation

### Prerequisites

1.  Python 3.10+
2.  `pip` (Python package installer)
3.  A running **Redis** instance (e.g., via Docker or local install)

### Steps

1.  **Clone the Repository:**
    ```bash
    git clone [https://github.com/your-username/project-nexus-book-review-api.git](https://github.com/your-username/project-nexus-book-review-api.git)
    cd project-nexus-book-review-api
    ```

2.  **Create and Activate Virtual Environment:**
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Linux/macOS
    # venv\Scripts\activate   # On Windows
    ```

3.  **Install Dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

    > **Note:** Create a `requirements.txt` file listing all dependencies (`django`, `djangorestframework`, `django-redis`, `djangorestframework-simplejwt`, etc.).

4.  **Configure Environment Variables:**
    Create a `.env` file in the project root based on a provided `.env.example`.
    *Ensure you set a strong `SECRET_KEY` and correct Redis connection strings.*

5.  **Run Migrations:**
    ```bash
    python manage.py makemigrations
    python manage.py migrate
    ```

6.  **Create Superuser (for Admin access):**
    ```bash
    python manage.py createsuperuser
    ```

7.  **Run the Server:**
    ```bash
    python manage.py runserver
    ```

The API will be live at `http://127.0.0.1:8000/`.

---

## ✨ Professional Best Practices Applied

### 1. Database Design (3NF)
* The data model separates **Author** from **Book** and uses a dedicated **Review** entity to link **User** and **Book**, ensuring **Third Normal Form (3NF)** is maintained.
* **`unique_together`** constraint is used on the `Review` model (`book`, `user`) to enforce that a user can only review a book once.

### 2. Security (JWT Authentication)
* Implements **stateless authentication** using **JWT Bearer Tokens**.
* Tokens have a short **15-minute expiration** (`ACCESS_TOKEN_LIFETIME`) and are secured using a longer-lived **Refresh Token** for renewal.
* **Bcrypt** (via Django) is used for secure password hashing.

### 3. Performance & Caching
* **Server-Side Caching (Redis):** The list endpoint for books (`/api/books/`) is cached using **Redis** for 5 minutes to reduce database load on frequently accessed public data.
* **Client-Side Caching (ETag):** The API is configured to support **Conditional GETs** using the `If-None-Match` header. If the resource hasn't changed, the server returns a lightweight `304 Not Modified` status, saving bandwidth.
* **ORM Optimization:** Queries use **`select_related()`** and **`prefetch_related()`** to minimize the number of database queries (N+1 query problem avoidance).

### 4. API Documentation
* Full API specification generated using **`drf-spectacular`** conforming to **OpenAPI 3.0**.
* **Interactive Swagger UI** available at `/api/schema/swagger/`.

---

## 🔗 Documentation & Deployment Links

| Resource | URL | Status |
| :--- | :--- | :--- |
| **Swagger UI (Interactive Docs)** | `http://127.0.0.1:8000/api/schema/swagger/` (Local) | Live |
| **Hosted API Base URL** | `[INSERT RENDER/RAILWAY DEPLOYMENT URL HERE]` | Required (Mandatory #4) |
| **ERD (Data Model)** | `[INSERT GOOGLE DOC LINK HERE]` | Required (Mandatory #1) |
| **Presentation Deck** | `[INSERT GOOGLE SLIDES LINK HERE]` | Required (Mandatory #2) |
| **Demo Video** | `[INSERT YOUTUBE/DRIVE LINK HERE]` | Required (Mandatory #3) |

---

## 🤝 Contribution

This project is the capstone for the ProDev Backend Program.

* **Author:** Robel Zeradawit
* **Version:** 1.0.0
