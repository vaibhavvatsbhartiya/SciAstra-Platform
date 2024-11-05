# SciAstra Platform

## Overview
The **SciAstra Platform** is a dynamic blog and course platform designed to allow users to browse and purchase courses and view blog content. The platform includes features for blog management, course display with discounted prices, and a two-step payment verification system.

## Folder Structure
The project is organized into frontend and backend folders, with an SQL database for data management.

```
SciAstra-Platform/
├── frontend/
│   ├── public/
│   │   ├── index.html               # Main HTML file
│   │   ├── styles.css               # Global CSS file
│   │   ├── favicon.ico              # Site favicon
│   └── src/
│       ├── assets/                  # Images, icons, and other static assets
│       ├── components/              # Reusable frontend components
│       │   ├── Header.js
│       │   ├── Footer.js
│       │   ├── CourseCard.js        # Component to display course info
│       │   └── BlogPost.js          # Component to display a single blog post
│       ├── pages/                   # Page-specific files
│       │   ├── HomePage.js
│       │   ├── BlogPage.js
│       │   ├── CoursePage.js
│       │   └── PaymentPage.js
│       ├── utils/
│       │   └── api.js               # File for API calls to the backend
│       ├── App.js                   # Main App component
│       └── index.js                 # Main entry point for the frontend
├── backend/
│   ├── config/
│   │   └── db.js                    # Database connection setup (MySQL)
│   ├── controllers/                 # Business logic for routes
│   │   ├── blogController.js        # Logic for blog CRUD operations
│   │   ├── courseController.js      # Logic for course management
│   │   └── paymentController.js     # Dummy payment processing logic
│   ├── models/                      # Database models
│   │   ├── Blog.js                  # Blog schema
│   │   ├── Course.js                # Course schema
│   │   ├── Transaction.js           # Transaction schema
│   │   └── User.js                  # User schema (optional)
│   ├── routes/                      # Express routes for API endpoints
│   │   ├── blogRoutes.js            # Routes for blog management
│   │   ├── courseRoutes.js          # Routes for course browsing and purchase
│   │   └── paymentRoutes.js         # Routes for handling payments
│   ├── middlewares/
│   │   └── authMiddleware.js        # Middleware for user authentication and 2-step verification
│   ├── utils/
│   │   ├── sendOTP.js               # Utility to send OTP for two-step verification
│   │   └── paymentMock.js           # Utility to simulate payment processing
│   ├── app.js                       # Main Express app setup
│   └── server.js                    # Server entry point
├── database/                        # SQL scripts or migration files
│   └── schema.sql                   # MySQL schema for tables
├── .env                             # Environment variables (e.g., database credentials)
├── .gitignore                       # Ignore node_modules, .env, etc.
├── README.md                        # Project documentation
└── package.json                     # Project dependencies and scripts
```

### Folder and File Descriptions

#### Frontend
- **public/**: Contains the main HTML file (`index.html`), global CSS (`styles.css`), and favicon.
- **src/**:
  - **assets/**: Stores images, icons, and other static assets.
  - **components/**: Contains reusable UI components like `Header`, `Footer`, `CourseCard`, and `BlogPost`.
  - **pages/**: Holds page-specific files, such as `HomePage`, `BlogPage`, `CoursePage`, and `PaymentPage`.
  - **utils/**: Contains helper files, such as `api.js` for making API requests to the backend.
  - **App.js**: Main component that renders the pages and components.
  - **index.js**: Main entry point to initialize the app.

#### Backend
- **config/**: Contains database configuration (`db.js`), which connects to a MySQL database.
- **controllers/**: Holds logic for various backend operations.
  - **blogController.js**: Manages CRUD operations for blog posts.
  - **courseController.js**: Handles course display and management.
  - **paymentController.js**: Processes dummy payment transactions.
- **models/**: Defines database schemas for `Blog`, `Course`, `Transaction`, and optionally, `User`.
- **routes/**: Sets up API endpoints for `blogRoutes`, `courseRoutes`, and `paymentRoutes`.
- **middlewares/**: Contains middleware like `authMiddleware` for user authentication and two-step verification.
- **utils/**: Stores backend utilities such as `sendOTP.js` for two-step verification and `paymentMock.js` to simulate payment processing.
- **app.js**: Sets up the Express app.
- **server.js**: Entry point for the backend server.

#### Database
- **database/schema.sql**: SQL file defining the database schema for the application.

## Setup Instructions

### Prerequisites
- **Node.js** and **npm** installed.
- **MySQL** for database management.

### Installation

1. **Clone the Repository**
   ```bash
   git clone https://github.com/vaibhavvatsbhartiya/SciAstra-Platform.git
   cd SciAstra-Platform
   ```

2. **Install Backend Dependencies**
   ```bash
   cd backend
   npm install
   ```

3. **Install Frontend Dependencies**
   ```bash
   cd ../frontend
   npm install
   ```

4. **Set Up the Database**
   - Create a MySQL database (e.g., `sciastra_db`).
   - Import the schema from `database/schema.sql` into your MySQL database.
   - Configure your database credentials in `.env` file.

5. **Configure Environment Variables**
   - Create a `.env` file in the root directory of `backend` and add your database credentials:
     ```
     DB_HOST=your_db_host
     DB_USER=your_db_user
     DB_PASSWORD=your_db_password
     DB_NAME=your_db_name
     ```

6. **Run the Backend Server**
   ```bash
   cd ../backend
   node server.js
   ```

7. **Run the Frontend Server**
   ```bash
   cd ../frontend
   npm start
   ```

### Usage
- **Homepage**: Displays dynamic course information with real-time discounted prices.
- **Blog Management**: Admin can add, edit, and schedule blog posts.
- **Course Purchase Flow**: Users can browse courses, select them, and proceed to a dummy payment page.
- **Two-Step Verification**: During payment, users are required to go through a two-step verification for enhanced security.

### API Endpoints
- **Blog Endpoints**:
  - `GET /api/blogs`: Fetch all blog posts.
  - `POST /api/blogs`: Create a new blog post (Admin only).
  - `PUT /api/blogs/:id`: Update a blog post (Admin only).
  - `DELETE /api/blogs/:id`: Delete a blog post (Admin only).
- **Course Endpoints**:
  - `GET /api/courses`: Fetch all available courses.
  - `POST /api/courses`: Add a new course (Admin only).
- **Payment Endpoint**:
  - `POST /api/payment`: Process a payment transaction with two-step verification.
