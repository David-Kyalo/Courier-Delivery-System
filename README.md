# Courier-Delivery-System

# Express Courier - Delivery Management System

A full-stack delivery and courier management system built with Node.js, Express, PostgreSQL, Prisma, and React.

## 🚀 Features

### Admin Panel
- **Dashboard** - Overview with statistics and recent orders
- **User Management** - Create and manage customers and couriers
- **Order Management** - View all orders, assign couriers (manual or auto)
- **Reports** - Revenue and delivery statistics

### Customer Portal
- **Create Orders** - Submit delivery requests with package details
- **Track Orders** - Real-time order tracking with status timeline
- **Order History** - View and manage past orders

### Courier Dashboard
- **Assignment Requests** - Accept or reject new delivery assignments
- **Active Deliveries** - View and manage current deliveries
- **Status Updates** - Update delivery progress and location

## 🛠️ Tech Stack

**Backend:**
- Node.js + Express
- PostgreSQL + Prisma ORM
- JWT Authentication
- Role-based Access Control (RBAC)

**Frontend:**
- React 18
- React Router v6
- Axios for API calls
- Custom CSS with modern design

## 📦 Installation

### Prerequisites
- Node.js 18+
- PostgreSQL database
- npm or yarn

### Backend Setup

```bash
cd backend

# Install dependencies
npm install

# Configure environment variables
cp .env.example .env
# Edit .env with your database connection string

# Generate Prisma client
npx prisma generate

# Run database migrations
npx prisma migrate dev

# Seed the database with sample data
npm run seed

# Start the development server
npm run dev
```

### Frontend Setup

```bash
cd frontend

# Install dependencies
npm install

# Start the development server
npm start
```

## 🔧 Environment Variables

Create a `.env` file in the backend directory:

```env
# Database
DATABASE_URL="postgresql://user:password@localhost:5432/delivery_db"

# JWT
JWT_SECRET="your-secret-key"
JWT_EXPIRES_IN="7d"

# Server
PORT=5000
NODE_ENV=development
FRONTEND_URL=http://localhost:3000
```

## 👥 Demo Accounts

After running the seed script:

| Role     | Email                | Password    |
|----------|---------------------|-------------|
| Admin    | admin@delivery.com  | password123 |
| Customer | john@customer.com   | password123 |
| Courier  | mike@courier.com    | password123 |

## 📁 Project Structure

```
Delivery/
├── backend/
│   ├── prisma/
│   │   ├── schema.prisma    # Database schema
│   │   └── seed.js          # Sample data
│   ├── src/
│   │   ├── middleware/      # Auth, error handling
│   │   ├── routes/          # API endpoints
│   │   ├── services/        # Business logic
│   │   ├── utils/           # Helpers, validators
│   │   └── index.js         # Server entry
│   └── package.json
├── frontend/
│   ├── public/
│   ├── src/
│   │   ├── components/      # Navbar, Sidebar
│   │   ├── contexts/        # AuthContext
│   │   ├── pages/
│   │   │   ├── admin/       # Admin pages
│   │   │   ├── customer/    # Customer pages
│   │   │   └── courier/     # Courier pages
│   │   ├── services/        # API client
│   │   └── App.js
│   └── package.json
└── README.md
```

## 🔌 API Endpoints

### Authentication
- `POST /api/auth/register` - Register new customer
- `POST /api/auth/login` - Login user
- `GET /api/auth/me` - Get current user profile

### Orders
- `GET /api/orders` - List orders
- `POST /api/orders` - Create new order
- `GET /api/orders/:id` - Get order details
- `PUT /api/orders/:id/status` - Update order status
- `DELETE /api/orders/:id` - Cancel order
- `GET /api/orders/track/:trackingNumber` - Public tracking

### Users (Admin only)
- `GET /api/users` - List all users
- `POST /api/users` - Create user
- `PUT /api/users/:id` - Update user
- `GET /api/users/couriers` - List available couriers

### Assignments
- `POST /api/assignments` - Assign courier to order
- `POST /api/assignments/auto` - Auto-assign courier
- `GET /api/assignments/my` - Get courier's assignments
- `PUT /api/assignments/:id/respond` - Accept/reject assignment

### Tracking
- `POST /api/tracking/location` - Update courier location
- `GET /api/tracking/:orderId` - Get tracking info

### Payments
- `GET /api/payments` - List payments
- `PUT /api/payments/:id/status` - Update payment status

## 🔒 Security Features

- JWT-based authentication
- Password hashing with bcrypt
- Role-based access control
- Input validation with express-validator
- Security headers with Helmet
- CORS configuration

## 📝 License

MIT License
