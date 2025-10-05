# Travel Planner - Full-Stack Web Application

A comprehensive travel planning platform built with modern web technologies, allowing users to discover destinations, plan itineraries, manage bookings, and track expenses all in one place.

## 🌟 Features

### Core Features
- **User Authentication & Authorization** - Secure JWT-based authentication system
- **Destination Discovery** - Browse and search destinations with detailed information
- **Trip Planning** - Create detailed itineraries with activities, accommodations, and schedules
- **Booking Management** - Track flights, hotels, activities, and other reservations
- **Expense Tracking** - Monitor and categorize travel expenses
- **Profile Management** - Update user information and preferences
- **Admin Dashboard** - Administrative interface for managing the platform

### User Experience
- **Responsive Design** - Works seamlessly on desktop, tablet, and mobile devices
- **Modern UI/UX** - Clean, intuitive interface built with Tailwind CSS
- **Real-time Updates** - Dynamic content updates and notifications
- **Search & Filtering** - Advanced search capabilities for destinations and trips
- **Social Features** - Share trips and connect with other travelers

## 🛠️ Tech Stack

### Frontend
- **React.js** - Modern JavaScript library for building user interfaces
- **React Router** - Client-side routing for single-page application
- **Tailwind CSS** - Utility-first CSS framework for styling
- **React Icons** - Comprehensive icon library
- **React DatePicker** - Date selection components
- **Axios** - HTTP client for API requests
- **React Toastify** - Toast notifications

### Backend
- **Node.js** - JavaScript runtime environment
- **Express.js** - Web application framework
- **MongoDB** - NoSQL database for data storage
- **Mongoose** - MongoDB object modeling for Node.js
- **JWT** - JSON Web Tokens for authentication
- **Bcryptjs** - Password hashing
- **Multer** - File upload handling
- **Nodemailer** - Email sending functionality
- **Express Validator** - Input validation
- **Helmet** - Security middleware
- **CORS** - Cross-origin resource sharing

### Development Tools
- **Concurrently** - Run multiple commands simultaneously
- **Nodemon** - Development server with auto-restart
- **ESLint** - Code linting and formatting

## 📁 Project Structure

```
travelplanner/
├── client/                 # React frontend application
│   ├── public/            # Static files
│   ├── src/
│   │   ├── components/    # Reusable React components
│   │   │   ├── auth/      # Authentication components
│   │   │   ├── common/    # Common/shared components
│   │   │   └── layout/    # Layout components (Navbar, Footer)
│   │   ├── contexts/      # React Context providers
│   │   ├── pages/         # Page components
│   │   │   ├── admin/     # Admin dashboard pages
│   │   │   └── auth/      # Authentication pages
│   │   ├── App.js         # Main App component
│   │   └── index.js       # Application entry point
│   ├── package.json       # Frontend dependencies
│   └── tailwind.config.js # Tailwind CSS configuration
├── server/                # Node.js backend application
│   ├── models/           # Database models (Mongoose schemas)
│   ├── routes/           # API route handlers
│   ├── middleware/       # Custom middleware functions
│   ├── uploads/          # File upload storage
│   ├── index.js          # Server entry point
│   └── package.json      # Backend dependencies
├── package.json          # Root package.json for scripts
└── README.md            # Project documentation
```

## 🚀 Getting Started

### Prerequisites
- Node.js (v16 or higher)
- MongoDB (local installation or MongoDB Atlas)
- npm or yarn package manager

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/travelplanner.git
   cd travelplanner
   ```

2. **Install dependencies**
   ```bash
   npm run install-all
   ```

3. **Environment Setup**
   ```bash
   # Copy environment example file
   cp server/env.example server/.env
   
   # Edit the .env file with your configuration
   nano server/.env
   ```

4. **Configure Environment Variables**
   ```env
   # Server Configuration
   PORT=5000
   NODE_ENV=development
   
   # Database
   MONGODB_URI=mongodb://localhost:27017/travelplanner
   
   # JWT Secret
   JWT_SECRET=your_super_secret_jwt_key_here
   
   # Email Configuration (for password reset)
   EMAIL_HOST=smtp.gmail.com
   EMAIL_PORT=587
   EMAIL_USER=your_email@gmail.com
   EMAIL_PASS=your_app_password
   ```

5. **Start the application**
   ```bash
   # Development mode (runs both frontend and backend)
   npm run dev
   
   # Or start individually
   npm run server  # Backend only
   npm run client  # Frontend only
   ```

6. **Access the application**
   - Frontend: http://localhost:3000
   - Backend API: http://localhost:5000
   - API Health Check: http://localhost:5000/api/health

## 📚 API Documentation

### Authentication Endpoints
- `POST /api/auth/register` - User registration
- `POST /api/auth/login` - User login
- `POST /api/auth/logout` - User logout
- `GET /api/auth/me` - Get current user profile
- `POST /api/auth/forgot-password` - Request password reset
- `POST /api/auth/reset-password` - Reset password

### User Endpoints
- `GET /api/users` - Get all users (Admin only)
- `GET /api/users/:id` - Get user by ID
- `PUT /api/users/:id` - Update user profile
- `POST /api/users/:id/upload-avatar` - Upload profile picture
- `PUT /api/users/:id/change-password` - Change password

### Destination Endpoints
- `GET /api/destinations` - Get all destinations
- `GET /api/destinations/featured` - Get featured destinations
- `GET /api/destinations/search` - Search destinations
- `GET /api/destinations/:id` - Get destination by ID
- `POST /api/destinations` - Create destination (Admin only)
- `PUT /api/destinations/:id` - Update destination (Admin only)
- `DELETE /api/destinations/:id` - Delete destination (Admin only)

### Trip Endpoints
- `GET /api/trips` - Get user's trips
- `GET /api/trips/public` - Get public trips
- `GET /api/trips/:id` - Get trip by ID
- `POST /api/trips` - Create new trip
- `PUT /api/trips/:id` - Update trip
- `DELETE /api/trips/:id` - Delete trip
- `POST /api/trips/:id/activities` - Add activity to trip

### Booking Endpoints
- `GET /api/bookings` - Get user's bookings
- `GET /api/bookings/upcoming` - Get upcoming bookings
- `GET /api/bookings/:id` - Get booking by ID
- `POST /api/bookings` - Create new booking
- `PUT /api/bookings/:id` - Update booking
- `PUT /api/bookings/:id/cancel` - Cancel booking

### Contact Endpoints
- `POST /api/contact` - Submit contact form
- `GET /api/contact` - Get contact messages (Admin only)
- `GET /api/contact/:id` - Get contact message by ID (Admin only)

## 🗄️ Database Schema

### User Model
```javascript
{
  firstName: String,
  lastName: String,
  email: String (unique),
  password: String (hashed),
  phone: String,
  dateOfBirth: Date,
  profilePicture: String,
  isEmailVerified: Boolean,
  role: String (user/admin),
  preferences: {
    currency: String,
    language: String,
    notifications: Object
  }
}
```

### Destination Model
```javascript
{
  name: String,
  description: String,
  country: String,
  city: String,
  coordinates: { latitude: Number, longitude: Number },
  images: Array,
  categories: Array,
  averageCost: Object,
  attractions: Array,
  rating: { average: Number, count: Number }
}
```

### Trip Model
```javascript
{
  title: String,
  description: String,
  destination: ObjectId (ref: Destination),
  user: ObjectId (ref: User),
  startDate: Date,
  endDate: Date,
  duration: Number,
  travelers: Array,
  budget: Object,
  itinerary: { days: Array },
  status: String,
  packingList: Array,
  reminders: Array
}
```

### Booking Model
```javascript
{
  user: ObjectId (ref: User),
  trip: ObjectId (ref: Trip),
  type: String,
  provider: Object,
  bookingDetails: Object,
  cost: Object,
  status: String,
  documents: Array,
  reminders: Array
}
```

## 🔐 Security Features

- **JWT Authentication** - Secure token-based authentication
- **Password Hashing** - Bcrypt for secure password storage
- **Input Validation** - Express Validator for request validation
- **CORS Protection** - Configured cross-origin resource sharing
- **Helmet Security** - Security headers and protection
- **Rate Limiting** - API rate limiting to prevent abuse
- **Email Verification** - Optional email verification system

## 🎨 UI/UX Features

- **Responsive Design** - Mobile-first responsive layout
- **Dark/Light Theme** - Theme switching capability
- **Loading States** - Skeleton loaders and spinners
- **Error Handling** - User-friendly error messages
- **Toast Notifications** - Real-time feedback for user actions
- **Form Validation** - Client-side and server-side validation
- **Accessibility** - WCAG compliance and keyboard navigation

## 🧪 Testing

```bash
# Run backend tests
cd server
npm test

# Run frontend tests
cd client
npm test

# Run all tests
npm run test:all
```

## 📦 Deployment

### Frontend Deployment (Vercel/Netlify)
```bash
cd client
npm run build
# Deploy the build folder
```

### Backend Deployment (Heroku/DigitalOcean)
```bash
cd server
# Set environment variables in deployment platform
# Deploy the server folder
```

### Docker Deployment
```bash
# Build and run with Docker Compose
docker-compose up --build
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **Unsplash** - For providing beautiful travel images
- **React Community** - For excellent documentation and support
- **Tailwind CSS** - For the amazing utility-first CSS framework
- **MongoDB** - For the flexible NoSQL database
- **Express.js** - For the robust web framework

## 📞 Support

For support, email support@travelplanner.com or join our Discord community.

## 🗺️ Roadmap

- [ ] **Mobile App** - React Native mobile application
- [ ] **Real-time Chat** - User-to-user messaging system
- [ ] **Social Features** - User profiles, following, and social feeds
- [ ] **AI Recommendations** - Machine learning-based destination recommendations
- [ ] **Offline Support** - Progressive Web App capabilities
- [ ] **Multi-language Support** - Internationalization (i18n)
- [ ] **Advanced Analytics** - Trip analytics and insights
- [ ] **Integration APIs** - Third-party travel service integrations

---

**Happy Traveling! 🌍✈️**
