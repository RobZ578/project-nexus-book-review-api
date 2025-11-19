# BookReviewHub

BookReviewHub is a web application backend built with Django and Django REST Framework that allows users to track books they've read and submit ratings and reviews. This project provides a fully-featured RESTful API for managing users, books, reviews, and personal reading lists.

## Features

- ✅ User Authentication with JWT (register, login, logout)  
- ✅ CRUD operations for Books  
- ✅ Users can submit Reviews and Ratings for books  
- ✅ Track books in personal Reading Lists (read, currently reading, want to read)  
- ✅ Optional: Search and filter books by genre, author, or rating  

## Tech Stack

- Python 3.x  
- Django 4.x  
- Django REST Framework  
- PostgreSQL (or SQLite for local development)  
- djangorestframework-simplejwt for JWT authentication  

## Project Structure

bookreviewhub/
├── bookreviewhub/ # Django project folder
├── users/ # User management app
├── books/ # Books app
├── reviews/ # Reviews app
├── readinglist/ # User reading list app
├── manage.py
└── requirements.txt


## Getting Started

### 1. Clone the repository
```bash
git clone https://github.com/<your-username>/bookreviewhub.git
cd bookreviewhub
2. Set up a virtual environment

python -m venv venv
source venv/bin/activate  # Linux/macOS
venv\Scripts\activate     # Windows
3. Install dependencies

pip install -r requirements.txt
4. Set up the database
Edit settings.py to configure PostgreSQL or use SQLite


python manage.py migrate
5. Run the server

python manage.py runserver
6. Access the API
By default: http://127.0.0.1:8000/

API Endpoints
/api/users/ – Register/Login/Logout

/api/books/ – List, Create, Update, Delete books

/api/reviews/ – Submit or view reviews for books

/api/readinglist/ – Manage your reading list

(Full documentation will be added once the project is completed.)

License
This project is licensed under the MIT License.
