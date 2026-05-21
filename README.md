# E-commerce Product API (Django REST Framework)

Capstone project for the **ALX Back-End (BE)** programme.

This repository contains a Django REST Framework API for managing **products**, **categories**, **orders**, and **reviews**, with **JWT authentication**.

## Project structure

> The Django project lives inside the `Ecommerce_api/` directory.

- `README.md` (this file)
- `Ecommerce_api/`
  - `manage.py`
  - `Ecommerce_api/` (Django project settings/urls)
  - `product/` (main app: models, serializers, views, urls)
  - `db.sqlite3` (local dev database — you may want to remove this from Git)

## Features

- Products CRUD
- Categories CRUD (and list products by category)
- Orders CRUD (placing an order reduces product stock)
- Reviews CRUD
- Users CRUD
- JWT authentication (access + refresh tokens)

## Tech stack

- Python
- Django
- Django REST Framework
- `djangorestframework-simplejwt` (JWT auth)

## Setup (local)

### 1) Clone the repo

```bash
git clone https://github.com/medob6/E-commerce-Product-API.git
cd E-commerce-Product-API
```

### 2) Create & activate a virtual environment

```bash
python -m venv .venv
# Linux/Mac:
source .venv/bin/activate
# Windows (PowerShell):
# .venv\Scripts\Activate.ps1
```

### 3) Install dependencies

This project should have its dependencies listed in `Ecommerce_api/requirements.txt`.

```bash
pip install -r Ecommerce_api/requirements.txt
```

> Note: `Ecommerce_api/requirements.txt` is currently empty in the repository.
> You should add your dependencies there (at minimum: `Django`, `djangorestframework`, `djangorestframework-simplejwt`).

### 4) Run migrations

```bash
cd Ecommerce_api
python manage.py migrate
```

### 5) Start the development server

```bash
python manage.py runserver
```

The API will be available at:

- `http://127.0.0.1:8000/api/`

## Authentication (JWT)

JWT endpoints (from `product/urls.py`):

- `POST /api/token/` – obtain access + refresh tokens
- `POST /api/token/refresh/` – refresh an access token

Example:

```bash
curl -X POST http://127.0.0.1:8000/api/token/ \
  -H "Content-Type: application/json" \
  -d '{"username":"YOUR_USERNAME","password":"YOUR_PASSWORD"}'
```

Use the access token:

```http
Authorization: Bearer <access_token>
```

## API endpoints

All endpoints are under the `/api/` prefix (see `Ecommerce_api/Ecommerce_api/urls.py`).

The router registers these resources (see `Ecommerce_api/product/urls.py`):

- `/api/products/`
- `/api/users/`
- `/api/orders/`
- `/api/reviews/`
- `/api/categorys/` (typo in route name in code: `categorys`)

## Notes / improvements

- Consider renaming the `categorys` route to `categories` in `Ecommerce_api/product/urls.py`.
- Remove `Ecommerce_api/db.sqlite3` from the repository and add it to `.gitignore`.
- Fill `Ecommerce_api/requirements.txt` with the required packages.

## Contributing

Contributions are welcome — open an issue or submit a pull request.

## License

No license is currently specified. Add a `LICENSE` file if you want to open-source this project under a specific license.
