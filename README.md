# MERN Backend Production

A robust, enterprise-grade backend application built with **Express.js** and **TypeScript**, designed for production deployment with Kubernetes and ArgoCD. This backend provides comprehensive APIs for a SaaS platform with advanced features including AI integration, email services, and cloud storage.

## 📋 Table of Contents

- [Overview](#overview)
- [Tech Stack](#tech-stack)
- [Features](#features)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Environment Setup](#environment-setup)
- [Development](#development)
- [Build & Deployment](#build--deployment)
- [Docker](#docker)
- [Kubernetes & ArgoCD](#kubernetes--argocd)
- [API Documentation](#api-documentation)
- [Dependencies](#dependencies)
- [CI/CD Pipeline](#cicd-pipeline)
- [Contributing](#contributing)
- [License](#license)

---

## Overview

This project is a production-ready Node.js backend for a MERN (MongoDB, Express, React, Node.js) stack application. It features enterprise-level security, scalability, and monitoring capabilities with full Kubernetes deployment support.

**Key Characteristics:**
- ✅ TypeScript for type safety
- ✅ Express.js REST API framework
- ✅ MongoDB with Mongoose ODM
- ✅ JWT authentication & authorization
- ✅ Docker containerization
- ✅ Kubernetes ready with Helm charts
- ✅ ArgoCD GitOps deployment
- ✅ CI/CD with Jenkins

---

## Tech Stack

| Layer | Technology | Version |
|-------|-----------|---------|
| **Runtime** | Node.js | Latest LTS |
| **Language** | TypeScript | ^6.0.3 |
| **Framework** | Express.js | ^5.2.1 |
| **Database** | MongoDB | ^7.0.0 |
| **ODM** | Mongoose | ^9.0.2 |
| **Authentication** | JWT (jsonwebtoken) | ^9.0.3 |
| **Security** | bcrypt | ^6.0.0 |
| **Container** | Docker | - |
| **Orchestration** | Kubernetes | - |
| **GitOps** | ArgoCD | - |
| **CI/CD** | Jenkins | - |

---

## Features

### Core Features
- 🔐 **Authentication & Authorization**
  - JWT-based authentication
  - Bcrypt password hashing
  - Role-based access control (RBAC)

- 🗄️ **Database**
  - MongoDB with Mongoose schema validation
  - Type-safe database models with TypeScript

- 📧 **Email Services**
  - SendGrid integration for transactional emails
  - Nodemailer support for SMTP-based emails

- ☁️ **Cloud Storage**
  - Cloudinary integration for image/media management
  - Optimized media delivery

- 🤖 **AI Integration**
  - OpenAI GPT integration
  - Google Generative AI (Gemini)
  - Hugging Face Inference API
  - Voyage AI embeddings

- 📊 **Monitoring & Logging**
  - Morgan HTTP request logger
  - Prometheus metrics (prom-client)
  - Production-ready error handling

- 🔗 **External Integrations**
  - HTTP client (Axios)
  - Web scraping (Puppeteer)
  - File uploads (Multer)
  - Cookie management

### Advanced Features
- CORS support for cross-origin requests
- Environment-based configuration
- Structured logging and monitoring
- Scalable container deployment
- GitOps-based application management

---

## Project Structure

```
MERN-BE-Production/
├── src/                          # TypeScript source code
│   ├── index.ts                 # Application entry point
│   ├── controllers/             # Request handlers
│   ├── models/                  # Mongoose schemas
│   ├── routes/                  # API endpoints
│   ├── middleware/              # Express middleware
│   ├── services/                # Business logic
│   ├── utils/                   # Helper functions
│   └── config/                  # Configuration files
├── express-chart/               # Helm chart for Kubernetes deployment
│   ├── Chart.yaml              # Chart metadata
│   ├── values.yaml             # Default values
│   └── templates/              # K8s resource templates
├── dist/                        # Compiled JavaScript (generated)
├── Jenkinsfile                  # CI/CD pipeline definition
├── argocd-application.yaml      # ArgoCD application manifest
├── Dockerfile                   # Container image definition
├── package.json                 # Node.js dependencies
├── tsconfig.json               # TypeScript configuration
└── README.md                    # This file
```

---

## Prerequisites

- **Node.js** (v18 or higher) and npm/yarn
- **MongoDB** (v6 or higher) - local or Atlas
- **Docker** & **Docker Compose** (for containerization)
- **Kubernetes** cluster (for deployment)
- **ArgoCD** installed on K8s cluster
- **Jenkins** (for CI/CD pipeline)

### Optional
- **Cloudinary** account (for media management)
- **SendGrid** API key (for email)
- **OpenAI** API key (for GPT)
- **Google Cloud** credentials (for Gemini)
- **Hugging Face** API token (for inference)
- **Voyage AI** API key (for embeddings)

---

## Installation

### 1. Clone the Repository
```bash
git clone https://github.com/namal1230/MERN-BE-Production.git
cd MERN-BE-Production
```

### 2. Install Dependencies
```bash
npm ci
```

### 3. Setup Environment Variables
```bash
cp .env.example .env
```

Edit `.env` with your configuration (see [Environment Setup](#environment-setup) section).

### 4. Build TypeScript
```bash
npm run build
```

### 5. Start Development Server
```bash
npm start
```

The server will start on `http://localhost:5000` (or configured PORT).

---

## Environment Setup

Create a `.env` file in the root directory with the following variables:

```env
# Server Configuration
NODE_ENV=development
PORT=5000
HOST=0.0.0.0

# Database
MONGODB_URI=process.env.MONGODB_URI
MONGODB_DB_NAME=your_database_name

# Authentication
JWT_SECRET=process.env.JWT_SECRET
JWT_EXPIRE=7d

# SendGrid (Email Service)
SENDGRID_API_KEY=process.env.SENDGRID_API_KEY

# Cloudinary (Media Storage)
CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=process.env.CLOUDINARY_API_KEY
CLOUDINARY_API_SECRET=process.env.CLOUDINARY_API_SECRET

# OpenAI
OPENAI_API_KEY=process.env.OPENAI_API_KEY
OPENAI_MODEL=gpt-4

# Google Generative AI
GOOGLE_API_KEY=process.env.GOOGLE_API_KEY

# Hugging Face
HUGGING_FACE_API_KEY=process.env.HUGGING_FACE_API_KEY

# Voyage AI
VOYAGE_API_KEY=process.env.VOYAGE_API_KEY

# Logging
LOG_LEVEL=info

# CORS
CORS_ORIGIN=http://localhost:3000
```

**⚠️ Security Note:** Never commit `.env` files with real secrets. Use environment variables in production.

---

## Development

### Available Scripts

```bash
# Install dependencies
npm ci

# Build TypeScript to JavaScript
npm run build

# Start production server
npm start

# Run tests (if configured)
npm test
```

### Development Workflow

1. Write TypeScript code in `src/`
2. Use IDE with TypeScript support (VS Code recommended)
3. Build to generate `dist/` folder
4. Run the application
5. Test using API client (Postman, cURL, Insomnia)

### TypeScript Configuration
- Configured in `tsconfig.json`
- Strict mode enabled for type safety
- Compiled to `dist/` directory

---

## Build & Deployment

### Local Build

```bash
# Install dependencies
npm ci

# Compile TypeScript
npm run build

# Start the server
npm start
```

### Production Build

```bash
npm ci --omit=dev
npm run build
```

---

## Docker

### Build Docker Image

```bash
docker build -t namaldil/saas-backend:latest .
```

### Run Docker Container

```bash
docker run -p 5000:5000 \
  -e MONGODB_URI=your_mongodb_uri \
  -e JWT_SECRET=your_jwt_secret \
  namaldil/saas-backend:latest
```

### Docker Compose

For local development with MongoDB:

```bash
docker-compose up -d
```

### Push to Docker Hub

```bash
docker login
docker push namaldil/saas-backend:latest
```

---

## Kubernetes & ArgoCD

### Helm Chart

The `express-chart/` directory contains Kubernetes manifests as a Helm chart.

**Chart Details:**
- Release Name: `express-chart`
- Namespace: `saas-app-backend`
- Docker Image: `namaldil/saas-backend:latest`

### Deploy with Helm

```bash
cd express-chart
helm install express-chart . \
  --namespace saas-app-backend \
  --create-namespace
```

### ArgoCD Deployment

The `argocd-application.yaml` defines automated GitOps deployment:

```bash
kubectl apply -f argocd-application.yaml
```

**Key Features:**
- ✅ Automated sync on Git changes
- ✅ Auto-prune of unused resources
- ✅ Self-healing capabilities
- ✅ Automatic namespace creation

### Access ArgoCD Dashboard

```bash
kubectl port-forward -n argocd svc/argocd-server 8080:443
# Visit: https://localhost:8080
```

### Monitor Deployment

```bash
# Check deployment status
kubectl get deployment -n saas-app-backend

# View pod logs
kubectl logs -n saas-app-backend -l app=express-chart

# Port forward to access API
kubectl port-forward -n saas-app-backend svc/express-chart 5000:5000
```

---

## CI/CD Pipeline

### Jenkins Pipeline

The `Jenkinsfile` defines automated CI/CD workflow:

**Pipeline Stages:**

1. **SCM Checkout** - Clone from GitHub
2. **Build** - Install npm dependencies
3. **Build Docker Image** - Create containerized image
4. **Push to Docker Registry** - Push to Docker Hub

**Configuration:**
- Source: `https://github.com/namal1230/MERN-BE`
- Docker Registry: Docker Hub
- Credentials: `docker-hub-creds` (Jenkins secret)

### Trigger Pipeline

Push to `main` branch to automatically trigger the Jenkins pipeline:

```bash
git push origin main
```

### Jenkins Credentials Setup

1. Go to Jenkins Dashboard → Manage Jenkins → Credentials
2. Add Docker Hub credentials with ID: `docker-hub-creds`
3. Configure repository webhook (Settings → Webhooks)

---

## API Documentation

### Base URL
```
http://localhost:5000
```

### Common Response Format

**Success (2xx):**
```json
{
  "success": true,
  "data": {},
  "message": "Operation successful"
}
```

**Error (4xx/5xx):**
```json
{
  "success": false,
  "error": "Error message",
  "statusCode": 400
}
```

### Authentication

Include JWT token in request headers:
```
Authorization: Bearer <your_jwt_token>
```

### Example Endpoints

Refer to route files in `src/routes/` for complete API documentation.

---

## Dependencies

### Production Dependencies

| Package | Version | Purpose |
|---------|---------|---------|
| `express` | ^5.2.1 | Web framework |
| `mongoose` | ^9.0.2 | MongoDB ODM |
| `jsonwebtoken` | ^9.0.3 | JWT authentication |
| `bcrypt` | ^6.0.0 | Password hashing |
| `cors` | ^2.8.5 | CORS middleware |
| `dotenv` | ^17.2.3 | Environment variables |
| `cloudinary` | ^2.8.0 | Cloud storage |
| `nodemailer` | ^9.0.3 | Email service |
| `@sendgrid/mail` | ^8.1.6 | SendGrid integration |
| `openai` | ^6.15.0 | OpenAI GPT API |
| `@google/genai` | ^1.34.0 | Google Generative AI |
| `axios` | ^1.13.2 | HTTP client |
| `puppeteer` | ^24.34.0 | Web scraping |
| `multer` | ^2.0.2 | File uploads |
| `prom-client` | ^15.1.3 | Prometheus metrics |
| `morgan` | ^1.10.1 | HTTP logging |

### Development Dependencies

| Package | Version | Purpose |
|---------|---------|---------|
| `typescript` | ^6.0.3 | Type safety |
| `@types/node` | ^25.9.3 | Node.js types |
| `@types/express` | ^5.0.6 | Express types |

---

## Monitoring & Observability

### Prometheus Metrics

Access metrics endpoint:
```
GET http://localhost:5000/metrics
```

### Logging

- **Morgan Logger** - HTTP request logging
- **Console Logs** - Application events
- **Kubernetes Logs** - Pod output via `kubectl logs`

### Health Check

Implement a health endpoint:
```
GET http://localhost:5000/health
```

---

## Security Best Practices

✅ **Implemented:**
- JWT-based authentication
- Bcrypt password hashing
- CORS configuration
- Environment variable management
- Docker security practices
- Kubernetes network policies (can be added)
- Input validation via Mongoose schemas

⚠️ **Recommended Additions:**
- Rate limiting middleware
- Request validation (joi/yup)
- API key rotation
- Security headers (helmet)
- SQL/NoSQL injection prevention
- HTTPS/TLS enforcement

---

## Troubleshooting

### Common Issues

**MongoDB Connection Error**
```bash
# Check MONGODB_URI in .env
# Ensure MongoDB is running and accessible
# Verify network connectivity to MongoDB Atlas
```

**Docker Build Fails**
```bash
# Clear Docker cache
docker system prune -a

# Rebuild with no cache
docker build --no-cache -t namaldil/saas-backend:latest .
```

**Kubernetes Deployment Issues**
```bash
# Check pod events
kubectl describe pod <pod-name> -n saas-app-backend

# View logs
kubectl logs <pod-name> -n saas-app-backend

# Check resource availability
kubectl top nodes
```

**JWT Token Expired**
```bash
# Re-authenticate to get new token
POST /api/auth/login
```

---

## Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature`
3. Commit changes: `git commit -m 'Add feature'`
4. Push to branch: `git push origin feature/your-feature`
5. Submit a Pull Request

### Code Standards
- Use TypeScript for type safety
- Follow Express.js best practices
- Add JSDoc comments for functions
- Write meaningful commit messages

---

## License

ISC License - See `package.json` for details.

---

## Support & Contact

For issues, questions, or contributions:

- **GitHub Issues:** [Report an issue](https://github.com/namal1230/MERN-BE-Production/issues)
- **Repository:** https://github.com/namal1230/MERN-BE-Production
- **Author:** namal1230

---

## Deployment Checklist

- [ ] Environment variables configured
- [ ] MongoDB connection tested
- [ ] Docker image built successfully
- [ ] Docker image pushed to registry
- [ ] Kubernetes cluster ready
- [ ] ArgoCD configured
- [ ] Helm chart values updated
- [ ] Jenkins credentials set up
- [ ] CI/CD pipeline tested
- [ ] Health checks passing
- [ ] Monitoring/logging verified
- [ ] Security scan completed

---

**Last Updated:** 2026-08-07  
**Version:** 1.0.0
