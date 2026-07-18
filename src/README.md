# MreddyVeera Blog

A full-stack blog application built with the MERN stack (MongoDB, Express, React, Node.js). This project allows users to create, edit, and manage blog posts with features like categorization, comments, likes, and user authentication.

**Live Demo:** [https://mreddyveera-blog.vercel.app](https://mreddyveera-blog.vercel.app)

---

## 📋 Table of Contents

- [Features](#features)
- [Tech Stack](#tech-stack)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Configuration](#configuration)
- [Running the Application](#running-the-application)
- [API Endpoints](#api-endpoints)
- [Components & Pages](#components--pages)
- [Key Features](#key-features)
- [Contributing](#contributing)

---

## ✨ Features

### User Authentication & Management
- User signup and signin with JWT authentication
- Password encryption using bcryptjs
- User profile management
- Admin privileges for content management

### Blog Management
- Create, read, update, and delete (CRUD) blog posts
- Rich text editor (CKEditor 5) for blog content
- Blog categorization system
- Search functionality across blog posts
- Filter blogs by category

### Engagement Features
- Comment system on blog posts
- Like/Unlike blog posts
- Real-time notifications using react-toastify
- User interaction tracking

### Content Management
- Category creation and management
- Image upload support (Cloudinary integration)
- Rich text editing capabilities
- Admin panel for content moderation

---

## 🛠 Tech Stack

### Frontend (Client)
- **React 19.2** - UI library
- **Vite 7.2** - Build tool and dev server
- **Redux Toolkit & Redux Persist** - State management
- **React Router v7** - Client-side routing
- **Tailwind CSS** - Styling framework
- **CKEditor 5** - Rich text editor
- **Radix UI** - Accessible UI components
- **Axios** - HTTP client
- **React Hook Form** - Form management with Zod validation
- **Firebase** - Backend services (v12.6)
- **React Toastify** - Toast notifications

### Backend (API)
- **Node.js + Express 5.2** - Server framework
- **MongoDB + Mongoose 9.0** - Database
- **JWT** - Authentication token
- **bcryptjs** - Password hashing
- **Cloudinary** - Image hosting and management
- **Multer 2.0** - File upload middleware
- **Cookie Parser** - Cookie handling
- **CORS** - Cross-origin resource sharing
- **Dotenv** - Environment variable management

---

## 📁 Project Structure

```
mreddyveera-blog/
├── client/                      # React frontend application
│   ├── src/
│   │   ├── pages/              # Page components (Index, SignIn, SignUp, Profile, etc.)
│   │   ├── components/         # Reusable components
│   │   ├── Layout/             # Layout wrapper
│   │   ├── helpers/            # Helper functions and route names
│   │   ├── App.jsx             # Main app component
│   │   └── main.jsx            # Entry point
│   ├── package.json
│   └── vite.config.js
│
└── api/                        # Express backend application
    ├── index.js               # Server entry point
    ├── routes/
    │   ├── Auth.route.js      # Authentication routes
    │   ├── User.route.js      # User management routes
    │   ├── Category.route.js  # Category routes
    │   ├── Blog.route.js      # Blog routes
    │   ├── Comment.route.js   # Comment routes
    │   └── Bloglike.route.js  # Like routes
    ├── models/
    │   └── category.model.js  # MongoDB category schema
    ├── package.json
    └── .env                   # Environment variables
```

---

## 📦 Prerequisites

Before you begin, ensure you have the following installed:
- **Node.js** (v14 or higher)
- **npm** or **yarn** package manager
- **MongoDB** (local or MongoDB Atlas cloud)
- **Cloudinary Account** (for image uploads)
- **Firebase Account** (optional, for backend services)

---

## 🚀 Installation

### 1. Clone the Repository

```bash
git clone https://github.com/mreddyveera/mreddyveera-blog.git
cd mreddyveera-blog
```

### 2. Install Backend Dependencies

```bash
cd api
npm install
```

### 3. Install Frontend Dependencies

```bash
cd ../client
npm install
```

---

## ⚙️ Configuration

### Backend Configuration

Create a `.env` file in the `api/` directory:

```env
PORT=5000
MONGODB_CONNECTION=mongodb://username:password@cluster.mongodb.net/
FRONTEND_URL=http://localhost:5173
JWT_SECRET=your_jwt_secret_key
CLOUDINARY_CLOUD_NAME=your_cloudinary_cloud_name
CLOUDINARY_API_KEY=your_cloudinary_api_key
CLOUDINARY_API_SECRET=your_cloudinary_api_secret
```

### Frontend Configuration

The frontend is configured through the `vite.config.js` and uses environment variables if needed. Update the API base URL in your axios configuration to match your backend server.

---

## 🎯 Running the Application

### Start the Backend Server

```bash
cd api
npm run dev
```

The backend API will start on `http://localhost:5000`

### Start the Frontend Development Server

In a new terminal:

```bash
cd client
npm run dev
```

The frontend will start on `http://localhost:5173`

### Build for Production

**Frontend Build:**
```bash
cd client
npm run build
```

**Backend Start (Production):**
```bash
cd api
npm start
```

---

## 🔌 API Endpoints

### Authentication Routes (`/api/auth`)
- `POST /signup` - Register a new user
- `POST /signin` - Login user
- `POST /logout` - Logout user

### User Routes (`/api/user`)
- `GET /:id` - Get user profile
- `PUT /:id` - Update user profile
- `DELETE /:id` - Delete user account

### Category Routes (`/api/category`)
- `GET /` - Get all categories
- `POST /` - Create new category (admin only)
- `GET /:id` - Get category details
- `PUT /:id` - Update category
- `DELETE /:id` - Delete category

### Blog Routes (`/api/blog`)
- `GET /` - Get all blogs with pagination
- `POST /` - Create new blog post
- `GET /:id` - Get blog details
- `PUT /:id` - Update blog post
- `DELETE /:id` - Delete blog post
- `GET /search/:query` - Search blogs

### Comment Routes (`/api/comment`)
- `GET /blog/:blogId` - Get comments for a blog
- `POST /` - Create comment
- `DELETE /:id` - Delete comment

### Blog Like Routes (`/api/bloglike`)
- `POST /` - Like a blog post
- `DELETE /:id` - Unlike a blog post

---

## 🎨 Components & Pages

### Main Pages
- **Index** - Homepage displaying all blogs
- **SignIn/SignUp** - User authentication pages
- **Profile** - User profile management
- **BlogDetails** - Blog management dashboard
- **SingleBlogDetails** - Individual blog post view
- **AddBlog/EditBlog** - Blog creation and editing
- **CategoryDetails** - Category management
- **SearchResult** - Search results page
- **Comments** - Comments management
- **Users** - User management (admin only)

### Key Components
- **AuthRouteProtection** - Protects authenticated routes
- **OnlyAdminAllowed** - Admin-only route protection
- **Layout** - Main application layout wrapper

---

## 🎯 Key Features Explained

### Authentication System
- JWT-based authentication with secure token storage
- Password encryption with bcryptjs
- Protected routes for authenticated users
- Admin role management

### Rich Text Editor
- CKEditor 5 integration for blog content creation
- HTML content support with entity handling
- Image upload capabilities

### State Management
- Redux Toolkit for global state
- Redux Persist for state persistence
- Organized action creators and reducers

### Form Handling
- React Hook Form for efficient form management
- Zod validation schema integration
- Real-time error feedback

### Styling
- Tailwind CSS for utility-first styling
- Radix UI for accessible components
- Custom animations and transitions

---

## 📝 Environment Variables

### Backend (.env)
| Variable | Description |
|----------|-------------|
| PORT | Express server port |
| MONGODB_CONNECTION | MongoDB connection string |
| FRONTEND_URL | Frontend application URL |
| JWT_SECRET | Secret key for JWT signing |
| CLOUDINARY_CLOUD_NAME | Cloudinary cloud name |
| CLOUDINARY_API_KEY | Cloudinary API key |
| CLOUDINARY_API_SECRET | Cloudinary API secret |

---

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a new branch (`git checkout -b feature/AmazingFeature`)
3. Make your changes
4. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
5. Push to the branch (`git push origin feature/AmazingFeature`)
6. Open a Pull Request

---

## 📄 License

This project is licensed under the ISC License - see the package.json file for details.

---

## 👨‍💻 Author

**MreddyVeera** - [GitHub Profile](https://github.com/mreddyveera)

---

## 📞 Support

For support, issues, or questions, please open an issue on the [GitHub Issues](https://github.com/mreddyveera/mreddyveera-blog/issues) page.

---

**Happy Blogging! 🚀**
