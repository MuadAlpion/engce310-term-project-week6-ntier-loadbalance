# Multi-Tier Load-Balanced Task Management Application

A comprehensive three-tier web application demonstrating modern architectural patterns including load balancing, caching, and containerization.

## 🏗️ Architecture Overview

This application implements a **three-tier architecture** with the following components:

### 📊 Presentation Tier (Frontend)
- **Location**: `frontend/`
- **Technology**: Vanilla HTML, CSS, and JavaScript
- **Features**:
  - Clean, responsive user interface
  - Real-time task management
  - Interactive task operations (Create, Read, Update, Delete)
  - Task status management (Pending, In Progress, Completed)

### 🔧 Application Tier (Backend API)
- **Location**: `api/`
- **Technology**: Node.js with Express.js
- **Architecture**: Clean Architecture with Repository Pattern
- **Features**:
  - RESTful API endpoints
  - Redis caching for performance
  - PostgreSQL database integration
  - Comprehensive error handling
  - Modular service-layer architecture

### 🗄️ Data Tier
- **Database**: PostgreSQL with Redis caching
- **Features**:
  - Persistent task storage
  - Redis for caching frequently accessed data
  - Optimized queries with caching strategy

### ⚖️ Load Balancer
- **Technology**: Nginx
- **Features**:
  - Round-robin load balancing
  - Health checks for backend services
  - Static file serving
  - Reverse proxy configuration

## 🚀 Quick Start

### Prerequisites
- Docker and Docker Compose
- Git

### Installation & Setup

1. **Clone the repository**:
   ```bash
   git clone https://github.com/MuadAlpion/engce310-term-project-week6-ntier-loadbalance.git
   cd engce310-term-project-week6-ntier-loadbalance
   ```

2. **Start the application**:
   ```bash
   docker-compose up -d
   ```

3. **Access the application**:
   - Frontend: http://localhost:80
   - API: http://localhost:3000

4. **Stop the application**:
   ```bash
   docker-compose down
   ```

## 📁 Project Structure

```
engce310-term-project-week6-ntier-loadbalance/
├── api/                    # Backend API (Node.js/Express)
│   ├── src/
│   │   ├── config/         # Configuration files
│   │   │   ├── database.js # PostgreSQL connection
│   │   │   └── redis.js    # Redis connection
│   │   ├── controllers/    # HTTP request handlers
│   │   │   └── taskController.js
│   │   ├── middleware/     # Express middleware
│   │   │   └── errorHandler.js
│   │   ├── models/         # Data models
│   │   │   └── Task.js
│   │   ├── repositories/   # Database abstraction
│   │   │   └── taskRepository.js
│   │   ├── routes/         # API route definitions
│   │   │   └── taskRoutes.js
│   │   └── services/       # Business logic
│   │       └── taskService.js
│   ├── server.js          # Main application entry point
│   ├── package.json       # Dependencies and scripts
│   └── Dockerfile         # Container configuration
├── frontend/              # Frontend application
│   ├── index.html         # Main HTML page
│   ├── css/
│   │   └── style.css      # Styling
│   └── js/
│       └── app.js         # Client-side JavaScript
├── nginx/                 # Load balancer configuration
│   ├── nginx.conf         # Main Nginx configuration
│   └── conf.d/
│       └── default.conf   # Server block configuration
├── database/              # Database setup
│   └── init.sql           # Database schema
├── scripts/               # Utility scripts
├── docker-compose.yml     # Docker orchestration
└── README.md             # This file
```

## 🔧 Technology Stack

### Backend (API)
- **Runtime**: Node.js
- **Framework**: Express.js
- **Database**: PostgreSQL
- **Cache**: Redis
- **Architecture**: Clean Architecture with Repository Pattern
- **Container**: Docker

### Frontend
- **Markup**: HTML5
- **Styling**: CSS3
- **Scripting**: Vanilla JavaScript (ES6+)
- **API Communication**: Fetch API

### Infrastructure
- **Load Balancer**: Nginx
- **Container Orchestration**: Docker Compose
- **Database**: PostgreSQL with Redis

## 📋 API Endpoints

The backend API provides the following endpoints:

### Task Management
- `GET /api/tasks` - Get all tasks
- `GET /api/tasks/:id` - Get a specific task
- `POST /api/tasks` - Create a new task
- `PUT /api/tasks/:id` - Update a task
- `DELETE /api/tasks/:id` - Delete a task

### Health Monitoring
- `GET /health` - Health check endpoint

## 🎯 Key Features

### ✨ Frontend Features
- **Responsive Design**: Works on desktop and mobile devices
- **Real-time Updates**: Instant feedback for all operations
- **User-friendly Interface**: Clean and intuitive task management
- **Form Validation**: Client-side validation for better UX

### 🔧 Backend Features
- **Caching Strategy**: Redis caching for improved performance
- **Error Handling**: Comprehensive error handling with proper HTTP status codes
- **Modular Architecture**: Clean separation of concerns
- **Database Abstraction**: Repository pattern for database operations
- **Health Monitoring**: Built-in health check endpoints

### ⚡ Performance Features
- **Load Balancing**: Nginx distributes traffic across multiple API instances
- **Caching**: Redis caches frequently accessed data
- **Connection Pooling**: Efficient database connection management
- **Static File Serving**: Nginx serves frontend files directly

## 🐳 Docker Configuration

The application uses Docker Compose to orchestrate multiple containers:

### Services
- **frontend**: Serves static files (port 80)
- **api**: Node.js application server (port 3000)
- **postgres**: PostgreSQL database (port 5432)
- **redis**: Redis cache (port 6379)
- **nginx**: Load balancer and reverse proxy

### Environment Variables
- `DB_HOST`: PostgreSQL host
- `DB_PORT`: PostgreSQL port
- `DB_USER`: Database username
- `DB_PASSWORD`: Database password
- `DB_NAME`: Database name
- `REDIS_HOST`: Redis host
- `REDIS_PORT`: Redis port

## 🔍 Code Architecture

### Backend Architecture
The backend follows Clean Architecture principles:

1. **Controllers**: Handle HTTP requests and responses
2. **Services**: Contain business logic
3. **Repositories**: Handle data access
4. **Models**: Define data structures

### Frontend Architecture
The frontend uses a simple but effective structure:
- **HTML**: Semantic markup with proper accessibility
- **CSS**: Modern CSS with flexbox layout
- **JavaScript**: Modular ES6+ code with async/await

## 🧪 Development

### Running Locally
1. Install dependencies:
   ```bash
   cd api && npm install
   ```

2. Set up environment variables (create `.env` file)

3. Start services:
   ```bash
   docker-compose up -d postgres redis
   npm start
   ```

### Adding New Features
1. Follow the existing architectural patterns
2. Add new endpoints to `api/src/routes/`
3. Implement business logic in `api/src/services/`
4. Update frontend JavaScript as needed

## 📊 Monitoring & Health Checks

The application includes health monitoring:
- **API Health**: `/health` endpoint
- **Nginx Health Checks**: Automatic backend health monitoring
- **Container Health**: Docker health checks for all services

## 🔒 Security Considerations

- **Input Validation**: Client and server-side validation
- **Error Handling**: No sensitive information in error responses
- **Container Security**: Non-root user execution in containers
- **Network Isolation**: Internal network for service communication

## 🚀 Deployment

### Production Deployment
1. Ensure all environment variables are set
2. Build and deploy containers:
   ```bash
   docker-compose -f docker-compose.yml up -d
   ```

3. Monitor application health through logs:
   ```bash
   docker-compose logs -f
   ```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes following the existing code style
4. Test thoroughly
5. Submit a pull request

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🆘 Support

For support, email [your-email@example.com](mailto:your-email@example.com) or create an issue in the repository.

---

**Built with ❤️ using modern web technologies**