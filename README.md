# 🧺 Campus Laundry Connect

A web-based laundry management platform that connects **students** with **campus laundromats**, replacing walk-in queues, paper records and phone calls with a simple digital booking and tracking system.

## 📌 Overview

Campus Laundry Connect lets students find nearby laundromats, book laundry services online, pay, and track their orders in real time. Laundromat owners get a dashboard to manage services, machines, bookings and customers, while an administrator oversees the whole platform.

It eliminates:

* Physical queuing to drop off laundry
* Paper-based order books
* Manual tracking of customers and payments
* Repeated phone calls to ask "is my laundry ready?"

## 🎯 Problem Statement

The traditional campus laundry process involves:

* Students walking to a laundromat to check prices and availability
* Orders written down by hand
* No visibility of order progress
* Manual payment and record keeping
* Heavy administrative workload for owners

This leads to:

* Wasted time for students
* Lost or mixed-up orders
* Poor record management
* Missed revenue and weak customer communication

## 💡 Proposed Solution

A centralized digital platform with three user roles.

### 👨‍🎓 Students Can

* Register and log in securely (including Google login)
* Browse laundromats and view their services, prices and reviews
* Book laundry services online
* Pay for bookings and manage subscriptions
* Track order status from acceptance to completion
* Receive notifications and SMS updates
* Leave reviews and manage their profile

### 🧼 Laundromat Owners Can

* Manage their laundromat profile and logo
* Create and edit services and prices
* Manage machines and their availability
* Accept, reject and update orders (processing → ready → complete)
* View customers, bookings and payments
* View revenue and activity reports
* Manage their platform subscription

### 🛡️ Administrators Can

* Oversee students, laundromats, bookings and payments
* Manage platform settings
* Manage subscriptions
* View platform-wide reports and dashboards

## 🛠️ Technologies Used

### Backend

* **Flask (Python)** – REST API, routing and business logic
* **PostgreSQL** – Relational database (via `psycopg2`)
* **bcrypt** – Password hashing
* **Twilio** – SMS notifications
* **Google Auth** – Google sign-in
* **Gunicorn** – Production WSGI server

### Frontend

* **HTML** – Structure
* **CSS** – Styling
* **JavaScript** – Client-side logic and API calls

## 🗄️ Database Architecture

The system uses a PostgreSQL relational database.

Core tables include:

* `users` (authentication records and roles)
* `students`
* `laundromats`
* `services`
* `machines`
* `bookings`
* `payments`
* `subscriptions`
* `reviews`
* `notifications`
* `system_settings`

> ⚠️ The database connection is configured through the `DATABASE_URL` environment variable.

## 📂 Project Structure

```
Campus Laundry Connect/
├── backend/
│   ├── app.py                 # Flask app entry point
│   ├── database.py            # PostgreSQL helpers
│   ├── sms_service.py         # Twilio SMS integration
│   ├── requirements.txt
│   ├── routes/                # API blueprints
│   │   ├── login.py, register.py, auth.py
│   │   ├── students.py, laundromats.py
│   │   ├── services.py, machines.py
│   │   ├── bookings.py, orders.py
│   │   ├── payments.py, booking_payments.py, subscriptions.py
│   │   ├── reviews.py, notifications.py
│   │   └── admin.py, dashboard.py, settings.py
│   └── uploads/               # Laundromat logos & student photos
└── frontend/
    ├── index.html, login.html, register.html
    ├── student/               # Student pages
    ├── laundromat/            # Laundromat owner pages
    └── admin/                 # Administrator pages
```

## 🔐 Security & Authentication

* Passwords are hashed with **bcrypt**
* Role-based accounts: **Student / Laundromat / Admin**
* Google sign-in support
* CORS restricted to approved frontend origins
* Secrets (database URL, Twilio keys) stored in environment variables

> ⚠️ Never commit your `.env` file. Add it to `.gitignore` and rotate any credentials that were previously shared.

## 🚀 Key Features

* Online laundry booking
* Real-time order tracking
* Role-based dashboards (student, laundromat, admin)
* Service and machine management
* Payments and subscription management
* SMS and in-app notifications
* Reviews and ratings
* Reports and analytics
* Profile and image uploads

## 📊 System Benefits

### For Students

* No more queuing or guessing
* Transparent prices and order progress
* Convenient online booking and payment

### For Laundromat Owners

* Digital order and customer records
* Better machine and workload management
* Clear revenue reports
* Fewer phone calls and mistakes

### For Administrators

* Centralized platform oversight
* Easier monitoring of users and payments

## ⚙️ Running the Application

### 1. Clone the repository

```
git clone https://github.com/<your-username>/campus-laundry-connect.git
cd "campus-laundry-connect/backend"
```

### 2. Install dependencies

```
pip install -r requirements.txt
```

### 3. Configure environment variables

Create a `.env` file in the `backend/` folder:

```
DATABASE_URL=postgresql://user:password@localhost:5432/laundry_db
TWILIO_ACCOUNT_SID=your_sid
TWILIO_AUTH_TOKEN=your_token
TWILIO_PHONE_NUMBER=your_twilio_number
```

### 4. Run the Flask server

```
python app.py
```

The API runs at `http://127.0.0.1:5000`.

### 5. Run the frontend

Serve the `frontend/` folder with any static server, for example the VS Code **Live Server** extension (`http://127.0.0.1:5500`), then open `index.html` in your browser.

> The frontend is currently configured to call a hosted API URL. For local development, update the API base URLs in the frontend files to `http://127.0.0.1:5000`.

## 🌐 Deployment

The project is set up for deployment on **Render**:

* Backend: Flask + Gunicorn web service
* Database: Render PostgreSQL (`DATABASE_URL`)
* Frontend: Static site

## 🔮 Future Improvements

* JWT-based authentication for all protected endpoints
* Stronger role-based authorization on every route
* Online payment gateway integration
* Mobile app version
* Rate limiting and improved audit logging

## 👨‍💻 Authors

Developed as a collaborative academic project.
**Software Development Team**
