Multi-Vendor E-Commerce Backend

A Node.js and Express REST API powering a multi-vendor e-commerce marketplace, built for three types of users — buyers, sellers, and admins — with real-time chat, order management, and Stripe payments.

Features
Authentication & Authorization — separate JWT-based auth flows for buyers, sellers, and admins, including email verification, Google OAuth login, and password reset
Seller Onboarding — seller registration with admin approval/rejection workflow
Product Management — create, update, delete, and search products, with image uploads via Cloudinary, category and pagination support, and short-form video "reels"
Cart & Wishlist — add, remove, and update cart items; manage wishlists
Orders & Payments — order placement, Stripe checkout sessions and payment confirmation, and order status tracking for buyers, sellers, and admins
Reviews & Ratings — buyers can review products; admins can moderate reviews
Real-Time Chat — Socket.IO-powered messaging between sellers and buyers
Support & Disputes — buyers and sellers can raise disputes; admins can manage and resolve them
Admin Dashboard Insights — aggregated platform statistics for admins
Security — Helmet, CORS, cookie-based auth, and response compression
Tech Stack
Layer	Technology
Runtime	Node.js (ES Modules)
Framework	Express.js
Database	MongoDB with Mongoose
Real-time	Socket.IO
Auth	JSON Web Tokens, Google Auth Library
Payments	Stripe
Media Storage	Cloudinary
Validation	Joi
Email	Nodemailer
Security	Helmet, bcryptjs, CORS
Project Structure
├── chat/               # Real-time seller–buyer chat (routes, controllers, sockets, models)
├── config/             # Cloudinary configuration
├── controllers/        # Route handlers / business logic
├── db/                 # MongoDB connection setup
├── middlwares/         # Auth guards, validation, file uploads, error handling
├── models/             # Mongoose schemas
├── public/             # Static assets
├── routes/             # API route definitions
└── index.js            # Application entry point
Getting Started
Prerequisites
Node.js (v18+ recommended)
A MongoDB database (local or Atlas)
Cloudinary account (for image/video uploads)
Stripe account (for payments)
Gmail SMTP credentials (for transactional emails)
Installation
bash
git clone https://github.com/ZaryabAli-09/multi-vendor-ecommerce-backend.git
cd multi-vendor-ecommerce-backend
npm install
Environment Variables

Create a .env file in the project root with the following variables:

env
PORT=5000
NODE_ENV=development
MONGO_URI=your_mongodb_connection_string

# Frontend URLs
FRONTEND_DOMAIN_URL=
SELLER_FRONTEND_DOMAIN_URL=
SELLER_FRONTEND_LOGIN_DOMAIN_URL=

# JWT Secrets
ACCESS_TOKEN_SECRET_KEY=
REFRESH_TOKEN_SECRET_KEY=
SELLER_ACCESS_TOKEN_SECRET_KEY=
SELLER_REFRESH_TOKEN_SECRET_KEY=
ADMIN_ACCESS_TOKEN_SECRET_KEY=
RESET_PASSWORD_TOKEN_SECRET_KEY=
SELLER_RESET_PASSWORD_TOKEN_SECRET_KEY=
VERIFICATION_TOKEN_SECRET_KEY=

# Google OAuth
GOOGLEAUTH_CLIENTID=

# Cloudinary
CLOUDINARY_API_NAME=
CLOUDINARY_API_KEY=
CLOUDINARY_API_SECRET=

# Stripe
STRIPE_SECRET_KEY=

# Email (SMTP)
SMTP_GMAIL_USER=
SMTP_GMAIL_APP_PASSWORD=
SMTP_FROM_EMAIL=

# Misc
PLATFORM_NAME=
SUPPORT_NUMBER=
Run the Server
bash
npm start

The API will be available at http://localhost:5000.

API Overview

All routes are prefixed with /api.

Base Route	Description
/api/buyer/auth	Buyer registration, login, verification, password reset
/api/seller/auth	Seller registration, login, approval workflow
/api/admin	Admin login and dashboard insights
/api/buyer	Buyer profile, browsing history, cart, wishlist
/api/seller	Seller profiles and management
/api/product	Products, categories, reviews, and reels
/api/order	Order creation, payments, and status updates
/api/support&disputes	Support tickets and dispute resolution
/api/chat	Seller–buyer chat
