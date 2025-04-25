# Architecture Portfolio Application

![Architecture Portfolio Banner](https://via.placeholder.com/800x200?text=Architecture+Portfolio+App)

[![Issues](https://img.shields.io/github/issues/yourusername/architect-portfolio)](https://github.com/yourusername/architect-portfolio/issues)
[![Pull Requests](https://img.shields.io/github/issues-pr/yourusername/architect-portfolio)](https://github.com/yourusername/architect-portfolio/pulls)
[![License](https://img.shields.io/github/license/yourusername/architect-portfolio)](https://github.com/yourusername/architect-portfolio/blob/main/LICENSE)

## 📑 Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [System Architecture](#system-architecture)
- [Repository Structure](#repository-structure)
- [Installation & Setup](#installation--setup)
- [API Documentation](#api-documentation)
- [Database Schema](#database-schema)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## 🏛️ Overview
A full-stack architecture portfolio application designed for architects to showcase their professional work, achievements, and experience. The platform enables architects to manage multiple projects with image galleries, highlight awards, and present their professional journey through an elegant, user-friendly interface.

**Live Demo:** [Architecture Portfolio Demo](https://your-demo-url.com)

## ✨ Features
- **Project Showcase** - Display architectural projects through multiple images per project
- **Awards Section** - Highlight professional achievements and recognition
- **Experience Timeline** - Document career milestones and professional history
- **Admin Dashboard** - Easy-to-use interface for content management
- **Responsive Design** - Optimized for all devices from mobile to desktop
- **Image Gallery** - Professional presentation of project visuals with lightbox functionality

## 🛠️ Tech Stack
### Backend
- Node.js
- Express.js
- MySQL
- JWT Authentication
- Multer (Image Upload)

### Frontend (Client & Admin)
- React
- Vite
- React Router
- Axios
- Modern CSS (Styled Components/Tailwind)

## 🏗️ System Architecture
The application follows a three-tier architecture:

```
                                    +----------------+
                                    |                |
                                    |   MySQL DB     |
                                    |                |
                                    +-------+--------+
                                            |
                                            |
                                    +-------v--------+
                                    |                |
                                    |  Node.js API   |
                                    |                |
                                    +----------------+
                                           /\
                                          /  \
                                         /    \
                                        /      \
                        +---------------+      +---------------+
                        |               |      |               |
                        | Client Portal |      | Admin Portal  |
                        |  (React/Vite) |      |  (React/Vite) |
                        |               |      |               |
                        +---------------+      +---------------+
```

## 📁 Repository Structure
```
architecture-portfolio/
├── README.md
├── LICENSE
├── .github/
│   ├── ISSUE_TEMPLATE/
│   │   ├── bug_report.md
│   │   └── feature_request.md
│   └── PULL_REQUEST_TEMPLATE.md
├── backend/
│   ├── src/
│   │   ├── controllers/
│   │   ├── middleware/
│   │   ├── models/
│   │   ├── routes/
│   │   ├── utils/
│   │   └── app.js
│   ├── package.json
│   └── .env.example
├── client/
│   ├── src/
│   │   ├── assets/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── hooks/
│   │   ├── services/
│   │   └── App.jsx
│   ├── package.json
│   └── .env.example
└── admin/
    ├── src/
    │   ├── assets/
    │   ├── components/
    │   ├── pages/
    │   ├── hooks/
    │   ├── services/
    │   └── App.jsx
    ├── package.json
    └── .env.example
```

## 🚀 Installation & Setup

### Prerequisites
- Node.js (v16+)
- MySQL (v8+)
- Git

### Quick Start

1. **Clone the repository**
```bash
git clone https://github.com/yourusername/architect-portfolio.git
cd architect-portfolio
```

2. **Backend Setup**
```bash
cd backend
npm install
cp .env.example .env
# Edit .env with your database credentials
npm run migrate
npm run dev
```

3. **Client Frontend Setup**
```bash
cd ../client
npm install
cp .env.example .env
# Edit .env with API URL
npm run dev
```

4. **Admin Dashboard Setup**
```bash
cd ../admin
npm install
cp .env.example .env
# Edit .env with API URL
npm run dev
```

### Environment Variables

#### Backend (.env)
```
NODE_ENV=development
PORT=3000
DB_HOST=localhost
DB_USER=root
DB_PASS=password
DB_NAME=architect_portfolio
JWT_SECRET=your_jwt_secret
JWT_EXPIRY=24h
```

#### Frontend (.env)
```
VITE_API_URL=http://localhost:3000/api
```

## 📚 API Documentation

### Authentication
| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|--------------|
| POST | /api/auth/register | Register new user | No |
| POST | /api/auth/login | Login | No |
| GET | /api/auth/verify | Verify token | Yes |

### Projects
| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|--------------|
| GET | /api/projects | Get all projects | No |
| GET | /api/projects/:id | Get project by ID | No |
| POST | /api/projects | Create new project | Yes |
| PUT | /api/projects/:id | Update project | Yes |
| DELETE | /api/projects/:id | Delete project | Yes |

### Project Images
| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|--------------|
| GET | /api/projects/:id/images | Get images for a project | No |
| POST | /api/projects/:id/images | Upload images for a project | Yes |
| PUT | /api/projects/images/:id | Update image details | Yes |
| DELETE | /api/projects/images/:id | Delete an image | Yes |

### Awards
| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|--------------|
| GET | /api/awards | Get all awards | No |
| GET | /api/awards/:id | Get award by ID | No |
| POST | /api/awards | Create new award | Yes |
| PUT | /api/awards/:id | Update award | Yes |
| DELETE | /api/awards/:id | Delete award | Yes |

### Experience
| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|--------------|
| GET | /api/experience | Get all experience entries | No |
| GET | /api/experience/:id | Get experience by ID | No |
| POST | /api/experience | Create new experience | Yes |
| PUT | /api/experience/:id | Update experience | Yes |
| DELETE | /api/experience/:id | Delete experience | Yes |

## 💾 Database Schema

### Users
| Column | Type | Description |
|--------|------|-------------|
| id | INT | Primary Key |
| username | VARCHAR(255) | Unique username |
| email | VARCHAR(255) | Unique email |
| password | VARCHAR(255) | Hashed password |
| role | ENUM | 'admin' or 'architect' |
| created_at | DATETIME | Creation timestamp |
| updated_at | DATETIME | Update timestamp |

### Projects
| Column | Type | Description |
|--------|------|-------------|
| id | INT | Primary Key |
| title | VARCHAR(255) | Project title |
| description | TEXT | Project description |
| location | VARCHAR(255) | Project location |
| year_completed | INT | Year project was completed |
| architect_id | INT | Foreign Key to Users |
| featured | BOOLEAN | Is project featured |
| created_at | DATETIME | Creation timestamp |
| updated_at | DATETIME | Update timestamp |

### Project_Images
| Column | Type | Description |
|--------|------|-------------|
| id | INT | Primary Key |
| project_id | INT | Foreign Key to Projects |
| image_url | VARCHAR(255) | Image URL/path |
| caption | VARCHAR(255) | Image caption |
| display_order | INT | Order in gallery |
| created_at | DATETIME | Creation timestamp |
| updated_at | DATETIME | Update timestamp |

### Awards
| Column | Type | Description |
|--------|------|-------------|
| id | INT | Primary Key |
| title | VARCHAR(255) | Award title |
| description | TEXT | Award description |
| year | INT | Year received |
| institution | VARCHAR(255) | Awarding institution |
| architect_id | INT | Foreign Key to Users |
| created_at | DATETIME | Creation timestamp |
| updated_at | DATETIME | Update timestamp |

### Experience
| Column | Type | Description |
|--------|------|-------------|
| id | INT | Primary Key |
| title | VARCHAR(255) | Position title |
| description | TEXT | Experience description |
| start_date | DATE | Start date |
| end_date | DATE | End date or NULL for current |
| company | VARCHAR(255) | Company name |
| architect_id | INT | Foreign Key to Users |
| created_at | DATETIME | Creation timestamp |
| updated_at | DATETIME | Update timestamp |

## 👥 Contributing
We welcome contributions from the community! Please read our [Contributing Guidelines](CONTRIBUTING.md) before submitting a pull request.

### Branch Organization
- `main` - Production-ready code
- `develop` - Development branch for feature integration
- `feature/*` - Feature branches
- `bugfix/*` - Bug fix branches
- `release/*` - Release preparation branches

### Issues
When creating an issue, please use the provided templates:
- **Bug Report**: For reporting bugs
- **Feature Request**: For suggesting new features

### Pull Requests
1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request using the PR template

## 📄 License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 📞 Contact
Project Maintainer - [Your Name](mailto:your.email@example.com)

GitHub: [@yourusername](https://github.com/yourusername)  
LinkedIn: [Your LinkedIn](https://linkedin.com/in/yourprofile)

---

⭐ **Star this repo if you find it useful!** ⭐# architecture
