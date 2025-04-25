# Architecture Portfolio Application

## Overview
This application is a full-stack solution for architects to showcase their work online through a professional portfolio website. The system consists of three main components:
- **Backend API** (Node.js)
- **Client Frontend** (React/Vite)
- **Admin Dashboard** (React/Vite)

The application allows architects to manage their portfolio projects, display multiple images per project, highlight professional awards, and showcase their experience through a clean, professional interface.

## System Architecture

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

## Backend (Node.js + MySQL)

### Technologies
- Node.js
- Express.js
- MySQL
- Sequelize ORM (optional)
- JWT for authentication
- Multer for image uploads

### Database Schema

#### Tables
1. **Users**
   - id (PK)
   - username
   - email
   - password (hashed)
   - role (admin/architect)
   - created_at
   - updated_at

2. **Projects**
   - id (PK)
   - title
   - description
   - location
   - year_completed
   - architect_id (FK to Users)
   - featured (boolean)
   - created_at
   - updated_at

3. **Project_Images**
   - id (PK)
   - project_id (FK to Projects)
   - image_url
   - caption
   - display_order
   - created_at
   - updated_at

4. **Awards**
   - id (PK)
   - title
   - description
   - year
   - institution
   - architect_id (FK to Users)
   - created_at
   - updated_at

5. **Experience**
   - id (PK)
   - title
   - description
   - start_date
   - end_date
   - company
   - architect_id (FK to Users)
   - created_at
   - updated_at

### API Endpoints

#### Authentication
- `POST /api/auth/register` - Register new user
- `POST /api/auth/login` - Login
- `GET /api/auth/verify` - Verify token

#### Projects
- `GET /api/projects` - Get all projects
- `GET /api/projects/:id` - Get project by ID
- `POST /api/projects` - Create new project (protected)
- `PUT /api/projects/:id` - Update project (protected)
- `DELETE /api/projects/:id` - Delete project (protected)

#### Project Images
- `GET /api/projects/:id/images` - Get images for a project
- `POST /api/projects/:id/images` - Upload images for a project (protected)
- `PUT /api/projects/images/:id` - Update image details (protected)
- `DELETE /api/projects/images/:id` - Delete an image (protected)

#### Awards
- `GET /api/awards` - Get all awards
- `GET /api/awards/:id` - Get award by ID
- `POST /api/awards` - Create new award (protected)
- `PUT /api/awards/:id` - Update award (protected)
- `DELETE /api/awards/:id` - Delete award (protected)

#### Experience
- `GET /api/experience` - Get all experience entries
- `GET /api/experience/:id` - Get experience by ID
- `POST /api/experience` - Create new experience (protected)
- `PUT /api/experience/:id` - Update experience (protected)
- `DELETE /api/experience/:id` - Delete experience (protected)

## Client Frontend (React/Vite)

### Technologies
- React
- Vite
- React Router
- Axios
- React Query (optional)
- Styled Components or Tailwind CSS

### Pages/Components
1. **Home Page**
   - Hero section with featured projects
   - About section
   - Featured awards
   - Contact information

2. **Projects Page**
   - Project grid/list
   - Filtering options
   - Pagination

3. **Project Detail Page**
   - Image gallery/carousel
   - Project details
   - Project description
   - Related projects

4. **Awards Page**
   - List of awards with details
   - Timeline view

5. **Contact Page**
   - Contact form
   - Contact information
   - Map (optional)

### Features
- Responsive design
- Image lazy loading
- Image gallery with lightbox
- Filtering and sorting projects
- Contact form

## Admin Dashboard (React/Vite)

### Technologies
- React
- Vite
- React Router
- Axios
- React Query (optional)
- Material UI or Ant Design

### Pages/Components
1. **Login Page**
   - Authentication form

2. **Dashboard Overview**
   - Statistics
   - Recent activity
   - Quick actions

3. **Projects Management**
   - Create/edit/delete projects
   - Manage project images
   - Set featured projects

4. **Awards Management**
   - Create/edit/delete awards

5. **Experience Management**
   - Create/edit/delete experience entries

6. **Profile Management**
   - Update personal information
   - Change password

### Features
- Protected routes
- Form validation
- Drag and drop image upload
- Image preview and cropping
- Drag and drop for reordering images
- Rich text editor for descriptions

## Deployment Architecture

### Option 1: Traditional Hosting
- Backend: Node.js application deployed on VPS or cloud provider (AWS, DigitalOcean, etc.)
- Frontend: Static assets served from CDN or web server
- Database: MySQL server
- File Storage: S3 or similar service for image storage

### Option 2: Containerized
- Docker containers for backend, client, and admin applications
- Docker Compose for local development
- Kubernetes for production deployment (optional)
- MySQL container or managed database service
- Object storage for images

## Security Considerations
- JWT token auth with refresh tokens
- Password hashing using bcrypt
- Input validation and sanitization
- CSRF protection
- Rate limiting
- Secure file uploads
- Environment variable management
- HTTPS enforcement

## Future Enhancements
1. **Multi-language Support**
   - Localization for international audiences

2. **Advanced Analytics**
   - Track project views and engagement

3. **Social Sharing**
   - Share projects on social media

4. **Client Collaboration**
   - Allow clients to comment on projects

5. **Advanced Search**
   - Search functionality for projects

## Development Workflow
1. Set up development environment
2. Implement backend API
3. Develop admin dashboard
4. Develop client frontend
5. Integration testing
6. Deployment

## Installation & Setup

### Prerequisites
- Node.js (v16+)
- MySQL
- Git

### Backend Setup
```bash
# Clone the repository
git clone https://github.com/yourusername/architect-portfolio.git
cd architect-portfolio/backend

# Install dependencies
npm install

# Set up environment variables
cp .env.example .env
# Edit .env with your database credentials

# Run migrations
npm run migrate

# Start development server
npm run dev
```

### Frontend Setup (Client & Admin)
```bash
# Client
cd ../client
npm install
cp .env.example .env
# Edit .env with API URL
npm run dev

# Admin
cd ../admin
npm install
cp .env.example .env
# Edit .env with API URL
npm run dev
```

## Contributing
Please read the CONTRIBUTING.md file for details on our code of conduct and the process for submitting pull requests.

## License
This project is licensed under the MIT License - see the LICENSE file for details.
