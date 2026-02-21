# Car-Hire - Premium Car Rental Platform 🚗

[![React](https://img.shields.io/badge/React-18.3-blue.svg)](https://reactjs.org/)
[![Node.js](https://img.shields.io/badge/Node.js-20.x-green.svg)](https://nodejs.org/)
[![MongoDB](https://img.shields.io/badge/MongoDB-7.x-brightgreen.svg)](https://www.mongodb.com/)
[![TailwindCSS](https://img.shields.io/badge/TailwindCSS-4.x-38B2AC.svg)](https://tailwindcss.com/)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## 📋 Table of Contents
- [Overview](#-overview)
- [Key Features](#-key-features)
- [Tech Stack](#-tech-stack)
- [Architecture](#-architecture)
- [Installation & Setup](#-installation--setup)
- [API Documentation](#-api-documentation)
- [Screenshots](#-screenshots)
- [Performance Optimizations](#-performance-optimizations)
- [Security Features](#-security-features)
 

## 🎯 Overview

**Car-Hire** is a full-stack, production-ready car rental platform that connects car owners with travelers. Built with modern web technologies, it offers a seamless experience for both car owners and renters. The platform features real-time availability checking, secure authentication, and an intuitive dashboard for managing listings and bookings.

### 🌟 Why This Project Stands Out

- **Real-world Business Logic**: Complete rental system with owner/tourist role separation
- **Production-Ready**: Scalable architecture with best practices
- **Smooth UI/UX**: Framer Motion animations, responsive design
- **Complete Payment Flow**: SSLCommerz integration with transaction handling
- **Type-Safe**: Full TypeScript support for better maintainability

## 🚀 Key Features

### 👤 User Features
- **🔐 Secure Authentication**: JWT-based login/register with role management
- **🚗 Car Search**: Advanced filtering by location, dates, category, and more
- **📅 Real-time Availability**: Instant availability checking with date validation
- **💳 Payment Integration**: SSLCommerz gateway for secure transactions
- **📱 Responsive Design**: Mobile-first approach with smooth animations

### 👑 Owner Dashboard
- **📊 Analytics Dashboard**: Real-time stats, revenue tracking, booking overview
- **🚙 Car Management**: Add, edit, delete listings with image upload
- **📅 Booking Management**: Accept/reject bookings, update status
- **💰 Revenue Reports**: Track earnings and payment history
- **🖼️ Profile Management**: Customizable profile with image upload

### 🛡️ Admin Panel
- **👥 User Management**: View all users, manage roles
- **📋 Listing Moderation**: Approve/reject car listings
- **📊 Platform Analytics**: Track platform performance
- **🔍 Search & Filters**: Advanced search by name, email, role

## 🛠️ Tech Stack

### Frontend
```javascript
{
  "core": ["React 18", "React Router 6"],
  "styling": ["TailwindCSS 4", "Framer Motion"],
  "state": ["Context API"],
  "http": ["Axios"],
  "forms": ["FormData API"],
  "notifications": ["React Hot Toast"]
}
```

### Backend
```javascript
{
  "runtime": ["Node.js", "Express"],
  "database": ["MongoDB", "Mongoose"],
  "auth": ["JWT", "Bcrypt"],
  "fileUpload": ["Multer", "ImageKit"],
  "payment": ["SSLCommerz"],
  "security": ["CORS", "Helmet"]
}
```

### DevOps & Tools
```javascript
{
  "versionControl": ["Git", "GitHub"],
  "packageManager": ["npm/yarn"],
  "development": ["Nodemon"],
  "environment": ["dotenv"]
}
```

## 🏗️ Architecture

```
car-hire/
├── client/                      # React Frontend
│   ├── src/
│   │   ├── components/          # Reusable UI components
│   │   │   ├── owner/           # Owner-specific components
│   │   │   ├── CarCard.jsx      # Car listing card
│   │   │   ├── Navbar.jsx       # Navigation
│   │   │   └── ...
│   │   ├── pages/               # Page components
│   │   │   ├── owner/           # Owner dashboard pages
│   │   │   ├── Home.jsx
│   │   │   ├── Cars.jsx
│   │   │   └── ...
│   │   ├── context/             # Global state management
│   │   ├── assets/              # Images, icons
│   │   └── App.jsx              # Main app component
│   └── index.css                 # Global styles
│
└── server/                       # Node.js Backend
    ├── controllers/              # Business logic
    ├── models/                   # MongoDB models
    ├── routes/                   # API routes
    ├── middleware/               # Auth, upload middleware
    ├── configs/                   # DB, ImageKit config
    └── server.js                  # Entry point
```

## 📦 Installation & Setup

### Prerequisites
- Node.js (v18+)
- MongoDB (v7+)
- npm/yarn
- ImageKit account
- SSLCommerz sandbox account (for testing)

### Step-by-Step Setup

#### 1️⃣ Clone the Repository
```bash
git clone https://github.com/yourusername/car-hire.git
cd car-hire
```

#### 2️⃣ Backend Setup
```bash
cd server
npm install

# Create .env file
cp .env.example .env
```

**.env Configuration:**
```env
# Server Configuration
PORT=5000
NODE_ENV=development

# Database
MONGODB_URI=mongodb://localhost:27017/car-rental

# JWT
JWT_SECRET=your-super-secret-jwt-key-min-32-chars-long

# ImageKit
IMAGEKIT_PUBLIC_KEY=your_public_key
IMAGEKIT_PRIVATE_KEY=your_private_key
IMAGEKIT_URL_ENDPOINT=https://ik.imagekit.io/yourid

# SSLCommerz (Sandbox)
SSL_STORE_ID=your_store_id
SSL_STORE_PASSWORD=your_store_password
SSL_SANDBOX=true
SSL_SUCCESS_URL=http://localhost:3000/payment/success
SSL_FAIL_URL=http://localhost:3000/payment/fail
SSL_CANCEL_URL=http://localhost:3000/payment/cancel
SSL_IPN_URL=http://localhost:5000/api/payment/ipn

# Frontend URL
FRONTEND_URL=http://localhost:3000
```

#### 3️⃣ Frontend Setup
```bash
cd ../client
npm install

# Create .env file
cp .env.example .env
```

**.env Configuration:**
```env
VITE_BASE_URL=http://localhost:5000
VITE_CURRENCY=৳
```

#### 4️⃣ Start Development Servers

**Backend:**
```bash
cd server
npm run dev
# Server running on http://localhost:5000
```

**Frontend:**
```bash
cd client
npm run dev
# Frontend running on http://localhost:3000
```

## 📚 API Documentation

### Authentication Endpoints

| Method | Endpoint | Description | Auth |
|--------|----------|-------------|------|
| POST | `/api/user/register` | Register new user | Public |
| POST | `/api/user/login` | Login user | Public |
| GET | `/api/user/data` | Get user data | Required |

### Car Endpoints

| Method | Endpoint | Description | Auth |
|--------|----------|-------------|------|
| GET | `/api/user/cars` | Get all available cars | Public |
| POST | `/api/owner/add-car` | Add new car listing | Owner |
| GET | `/api/owner/cars` | Get owner's cars | Owner |
| POST | `/api/owner/toggle-car` | Toggle availability | Owner |
| POST | `/api/owner/delete-car` | Delete car listing | Owner |

### Booking Endpoints

| Method | Endpoint | Description | Auth |
|--------|----------|-------------|------|
| POST | `/api/bookings/check-availability` | Check car availability | Public |
| POST | `/api/bookings/create` | Create booking | Required |
| GET | `/api/bookings/user` | Get user bookings | Required |
| GET | `/api/bookings/owner` | Get owner bookings | Owner |
| POST | `/api/bookings/change-status` | Update booking status | Owner |

### Payment Endpoints

| Method | Endpoint | Description | Auth |
|--------|----------|-------------|------|
| POST | `/api/payment/init` | Initialize payment | Required |
| POST | `/api/payment/ipn` | Payment webhook | Public |
| GET | `/api/payment/success` | Payment success callback | Public |
| GET | `/api/payment/fail` | Payment fail callback | Public |
| GET | `/api/payment/cancel` | Payment cancel callback | Public |
| GET | `/api/payment/verify/:bookingId` | Verify payment | Required |
| GET | `/api/payment/history` | Get payment history | Required |

## 📸 Screenshots

### Home Page
*Hero section with search functionality, featured vehicles, and promotional banner*

### Car Details
*Complete car information with booking form and availability calendar*

### Owner Dashboard
*Analytics dashboard with recent bookings and revenue tracking*

### My Bookings
*User booking history with status tracking*

## ⚡ Performance Optimizations

### Frontend
- ✅ **Lazy Loading**: Images with `loading="lazy"`
- ✅ **Code Splitting**: Route-based code splitting
- ✅ **Image Optimization**: ImageKit transformations (WebP format, auto-compression)
- ✅ **Memoization**: React.memo for expensive components
- ✅ **Debounced Search**: 300ms delay for search inputs
- ✅ **Virtual Scrolling**: For large lists (planned)

### Backend
- ✅ **Database Indexing**: Optimized MongoDB queries
- ✅ **Response Caching**: NodeCache for frequent queries
- ✅ **Connection Pooling**: MongoDB connection reuse
- ✅ **Pagination**: Limit/skip for large datasets
- ✅ **Aggregation Pipeline**: Optimized MongoDB aggregations

## 🔒 Security Features

### Authentication & Authorization
- ✅ **JWT Tokens**: Secure, stateless authentication
- ✅ **Password Hashing**: bcrypt with 10 salt rounds
- ✅ **Role-Based Access**: Owner/user separation
- ✅ **Protected Routes**: Middleware for authorization

### Data Security
- ✅ **Input Validation**: Server-side validation
- ✅ **Sanitization**: Prevent XSS attacks
- ✅ **CORS**: Configured for frontend only
- ✅ **Environment Variables**: Secure credential storage
- ✅ **HTTPS**: Enforced in production

### Payment Security
- ✅ **SSLCommerz PCI-DSS**: Level-1 certified
- ✅ **Transaction Validation**: IPN verification
- ✅ **Secure Callbacks**: Signed URLs
- ✅ **Fraud Prevention**: Availability checks
 **
