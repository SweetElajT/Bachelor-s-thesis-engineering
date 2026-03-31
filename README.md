# E-commerce Platform Design and Implementation

Engineering thesis: **Design and implementation of an e-commerce platform in a decoupled architecture using the Django framework and the React library**.

Author: **Artur Kupś**  
Field of study: **Computer Science**  
Year: **2026**

## About the Project

This project presents the implementation of a modern e-commerce platform based on a **decoupled/headless** architecture:
- frontend as a separate SPA application (React + TypeScript),
- backend as an independent API (Django REST Framework),
- communication between layers via HTTP and JSON.

Core idea: separate the presentation layer from business logic to simplify development, testing, and scaling.

## Functional Scope

- product catalog and categories,
- shopping cart (with client-side state persistence),
- user registration and login (JWT),
- order creation,
- Stripe payment integration (Payment Intent),
- user profile,
- Django admin panel.

## Technology Stack

### Backend
- Python 3.10+
- Django 6.0
- Django REST Framework
- djangorestframework-simplejwt
- django-cors-headers
- Stripe SDK
- SQLite

### Frontend
- React 18
- TypeScript
- Vite
- Tailwind CSS
- React Router
- React Context API

### DevOps
- Docker
- Docker Compose

## Architecture

The system follows a client-server model:

1. Frontend (React) sends HTTP requests to the API.
2. Backend (DRF) validates data, executes business logic, and performs database operations.
3. API returns JSON responses.
4. Frontend renders data and updates the interface.

Access to protected resources is handled with JWT tokens (`access` and `refresh`).

## Project Structure

```text
.
├── backend/                  # API Django + DRF
│   ├── api/
│   ├── core/
│   ├── manage.py
│   └── requirements.txt
├── frontend/                 # SPA React + TypeScript + Vite
│   ├── src/
│   └── package.json
└── docker-compose.yml
```

## Running the Project

### Option 1: Docker (recommended)

From the root directory:

```bash
docker-compose up --build
```

The application should be available at:
- Frontend: `http://localhost:5173`
- Backend API: `http://localhost:8000`

### Option 2: Local setup (without Docker)

#### Backend

```bash
cd backend
python -m venv venv
# Windows:
venv\Scripts\activate
# Linux/macOS:
# source venv/bin/activate
pip install -r requirements.txt
python manage.py migrate
python manage.py runserver
```

#### Frontend

```bash
cd frontend
npm install
npm run dev
```

## Example API Endpoints

- `GET /api/products/` - list products
- `GET /api/products/{id}/` - product details
- `POST /api/orders/` - create an order
- `POST /api/register/` - user registration
- `POST /api/token/` - login (JWT)
- `POST /api/token/refresh/` - refresh token
- `POST /api/create-payment-intent/` - initialize Stripe payment
- `GET /api/user/me/` - currently authenticated user data

## Testing

Run backend tests:

```bash
cd backend
python manage.py test
```

The thesis includes:
- unit tests,
- integration tests for the purchase flow,
- quality audit (Google Lighthouse).


## Further Development

Development directions:
- migration to PostgreSQL/MySQL,
- caching layer (Redis),
- extended logistics and payment integrations,
- PWA/SSR,
- CI/CD and monitoring.


## License

Educational project created for an engineering thesis.  

