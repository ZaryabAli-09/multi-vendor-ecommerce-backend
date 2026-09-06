# Multi-Vendor E-Commerce Backend

A Node.js + Express REST API that powers a multi-vendor e-commerce marketplace. The backend supports three user roles — **buyers**, **sellers**, and **admins** — and includes features such as real-time chat, order management, Stripe payments, and an admin dashboard.

---

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [Environment Variables](#environment-variables)
  - [Run the Server](#run-the-server)
- [API Overview](#api-overview)
- [Related Repositories](#related-repositories)
- [Contributing](#contributing)
- [License](#license)

---

## Overview

This repository contains the backend for a multi-vendor e-commerce application. It exposes a RESTful API (prefixed with `/api`) that handles authentication, product management, orders & payments, real-time chat via Socket.IO, and admin operations.

## Features

- Authentication & Authorization
  - JWT-based flows for buyers, sellers, and admins
  - Email verification, Google OAuth, and password reset
- Seller onboarding
  - Seller registration with admin approval/rejection workflow
- Product management
  - CRUD operations, search, categories, pagination
  - Image and short-video uploads (Cloudinary) and "reels"
- Cart & Wishlist
  - Add/remove/update items and manage wishlists
- Orders & Payments
  - Order creation, Stripe checkout, payment confirmation, and status tracking
- Reviews & Ratings
  - Buyers can leave reviews; admins can moderate or remove them
- Real-time chat
  - Socket.IO-powered messaging between buyers and sellers
- Support & Disputes
  - Raise and manage disputes; admin resolution tools
- Admin dashboard
  - Aggregated platform metrics and insights
- Security & Performance
  - Helmet, CORS, cookie-based auth, bcryptjs, and response compression

## Tech Stack

- Runtime: Node.js (ES Modules)
- Framework: Express.js
- Database: MongoDB (Mongoose)
- Real-time: Socket.IO
- Auth: JSON Web Tokens, Google OAuth
- Payments: Stripe
- Media storage: Cloudinary
- Validation: Joi
- Email: Nodemailer
- Security: Helmet, bcryptjs, CORS

## Project Structure

```
├── chat/               # Real-time seller–buyer chat (routes, controllers, sockets, models)
├── config/             # Cloudinary and other configuration
├── controllers/        # Route handlers and business logic
├── db/                 # MongoDB connection setup
├── middlwares/         # Auth guards, validation, file uploads, error handling
├── models/             # Mongoose schemas
├── public/             # Static assets
├── routes/             # API route definitions
└── index.js            # Application entry point
```

## Getting Started

### Prerequisites

- Node.js v18+ (recommended)
- A MongoDB database (local or Atlas)
- Cloudinary account (for image/video uploads)
- Stripe account (for payments)
- Gmail SMTP credentials (for transactional emails)

### Installation

```bash
git clone https://github.com/ZaryabAli-09/multi-vendor-ecommerce-backend.git
cd multi-vendor-ecommerce-backend
npm install
```

### Environment Variables

Create a `.env` file in the project root and set the values below (example values shown):

```
PORT=5000
NODE_ENV=development
MONGO_URI=your_mongodb_connection_string

# Frontend URLs
FRONTEND_DOMAIN_URL=https://your-frontend.example.com
SELLER_FRONTEND_DOMAIN_URL=https://seller-frontend.example.com
SELLER_FRONTEND_LOGIN_DOMAIN_URL=https://seller-frontend.example.com/login

# JWT Secrets
ACCESS_TOKEN_SECRET_KEY=your_access_token_secret
REFRESH_TOKEN_SECRET_KEY=your_refresh_token_secret
SELLER_ACCESS_TOKEN_SECRET_KEY=your_seller_access_token_secret
SELLER_REFRESH_TOKEN_SECRET_KEY=your_seller_refresh_token_secret
ADMIN_ACCESS_TOKEN_SECRET_KEY=your_admin_access_token_secret
RESET_PASSWORD_TOKEN_SECRET_KEY=your_reset_password_secret
SELLER_RESET_PASSWORD_TOKEN_SECRET_KEY=your_seller_reset_password_secret
VERIFICATION_TOKEN_SECRET_KEY=your_verification_token_secret

# Google OAuth
GOOGLEAUTH_CLIENTID=your_google_client_id

# Cloudinary
CLOUDINARY_API_NAME=your_cloudinary_cloud_name
CLOUDINARY_API_KEY=your_cloudinary_api_key
CLOUDINARY_API_SECRET=your_cloudinary_api_secret

# Stripe
STRIPE_SECRET_KEY=your_stripe_secret_key

# Email (SMTP)
SMTP_GMAIL_USER=your_gmail_address
SMTP_GMAIL_APP_PASSWORD=your_gmail_app_password
SMTP_FROM_EMAIL=your_from_email@example.com

# Misc
PLATFORM_NAME=YourPlatformName
SUPPORT_NUMBER=+1-555-555-5555
```

Security tip: keep secrets out of version control and use environment secret managers in production.

### Run the Server

```bash
npm start
```

The API will be available at http://localhost:5000 (or the port you configured).

## API Overview

All routes are prefixed with `/api`.

| Base Route | Description |
|---|---|
| `/api/buyer/auth` | Buyer registration, login, verification, password reset |
| `/api/seller/auth` | Seller registration, login, approval workflow |
| `/api/admin` | Admin login and dashboard insights |
| `/api/buyer` | Buyer profile, browsing history, cart, wishlist |
| `/api/seller` | Seller profiles and management |
| `/api/product` | Products, categories, reviews, and reels |
| `/api/order` | Order creation, payments, and status updates |
| `/api/support&disputes` | Support tickets and dispute resolution |
| `/api/chat` | Seller–buyer chat |

## Related Repositories

This backend is designed to be used with separate frontend applications (buyer, seller, admin). See my GitHub for the frontend repositories.

## Contributing

Contributions are welcome — open issues or pull requests with a clear description and tests where applicable.

## License

This project is licensed under the ISC License.
