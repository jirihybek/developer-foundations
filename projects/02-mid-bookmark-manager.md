# Project: Bookmark Vault

A full-stack bookmark manager where users can save, organize, and search their favorite links.

---

## Goal

Build a full-stack application with a REST API backend and React frontend. Users can save bookmarks, organize them into collections, add tags, and search through their saved links. The project introduces backend development, database design, and proper API consumption patterns.

---

## Tech Stack

- **Runtime**: Bun
- **Package Manager**: npm workspaces (monorepo)
- **Back-end**: Express.js
- **Database**: PostgreSQL
- **ORM**: Drizzle ORM (or TypeORM)
- **Front-end**: React + Vite
- **Data Fetching**: React Query (TanStack Query)
- **Styling**: Tailwind CSS (recommended)
- **Containerization**: Docker + Docker Compose

---

## Difficulty

**Intermediate** - Suitable for junior developers ready to learn full-stack

### Concepts You Should Know

- Everything from Basic project, plus:
- REST API principles (resources, HTTP methods, status codes)
- Express.js basics (routes, middleware, error handling)
- SQL basics (CRUD operations, JOINs)
- Database design (tables, relationships, constraints)
- React Query for server state management
- Environment variables
- Docker basics (images, containers, compose)
- Request validation

---

## Features & User Stories

### 1. Add Bookmark

**As a user**, I want to save a URL so I can access it later.

**Acceptance Criteria:**
- Form to enter URL and optional title
- Automatically fetch page title if not provided (bonus)
- URL validation (must be valid URL format)
- Save bookmark to database
- Show success/error feedback

### 2. View Bookmarks

**As a user**, I want to see all my bookmarks so I can find what I saved.

**Acceptance Criteria:**
- Display bookmarks as a list or grid
- Show title, URL, collection, tags, and created date
- Paginate results (10-20 per page)
- Sort by date added (newest first by default)

### 3. Edit Bookmark

**As a user**, I want to edit a bookmark so I can fix mistakes or update information.

**Acceptance Criteria:**
- Edit title, URL, collection, and tags
- Save changes to database
- Show success feedback
- Cancel returns to previous state

### 4. Delete Bookmark

**As a user**, I want to delete a bookmark so I can remove links I no longer need.

**Acceptance Criteria:**
- Delete button on each bookmark
- Confirmation dialog before deleting
- Remove from database
- Update UI immediately (optimistic update)

### 5. Collections

**As a user**, I want to organize bookmarks into collections so I can group related links.

**Acceptance Criteria:**
- Create, edit, and delete collections
- Assign a bookmark to one collection
- Filter bookmarks by collection
- "Uncategorized" for bookmarks without collection

### 6. Tags

**As a user**, I want to add tags to bookmarks so I can categorize them flexibly.

**Acceptance Criteria:**
- Add multiple tags to a bookmark
- Create tags on-the-fly when adding/editing
- Filter bookmarks by tag
- Display tags as clickable chips

### 7. Search

**As a user**, I want to search my bookmarks so I can quickly find what I need.

**Acceptance Criteria:**
- Search by title and URL
- Real-time search (debounced)
- Clear search button
- Show "no results" message when empty

### 8. Error Handling

**As a user**, I want to see helpful error messages so I know what went wrong.

**Acceptance Criteria:**
- Show user-friendly error messages
- Handle network errors gracefully
- Loading states for all async operations
- Retry option for failed requests

---

## Development Guidelines

### Project Structure

```
bookmark-vault/
├── package.json              # Workspace root
├── docker-compose.yml        # PostgreSQL + app services
├── packages/
│   ├── api/                  # Express backend
│   │   ├── src/
│   │   │   ├── routes/       # Route handlers
│   │   │   ├── services/     # Business logic
│   │   │   ├── repositories/ # Database queries
│   │   │   ├── db/           # Database connection, schema, migrations
│   │   │   ├── middleware/   # Error handling, validation
│   │   │   ├── utils/        # Helper functions
│   │   │   └── index.ts      # App entry point
│   │   └── package.json
│   └── web/                  # React frontend
│       ├── src/
│       │   ├── components/   # Reusable UI components
│       │   ├── pages/        # Page components
│       │   ├── hooks/        # Custom hooks
│       │   ├── api/          # API client functions
│       │   └── App.jsx
│       └── package.json
└── README.md
```

### Backend Guidelines

1. **3-Layer Architecture**
   - **Routes**: Handle HTTP requests, parse params, call services
   - **Services**: Business logic, validation, orchestration
   - **Repositories**: Database queries only, no business logic

2. **API Design**
   - Follow REST conventions
   - Use proper HTTP methods (GET, POST, PUT, DELETE)
   - Return appropriate status codes (200, 201, 400, 404, 500)
   - Consistent response format: `{ data: ... }` or `{ error: ... }`

3. **Error Handling**
   - Create custom error classes (NotFoundError, ValidationError)
   - Global error handling middleware
   - Never expose internal errors to client

4. **Validation**
   - Validate all incoming data
   - Use a validation library (zod, joi, or class-validator)
   - Return clear validation error messages

5. **Database**
   - Use migrations for schema changes
   - Use parameterized queries (ORM handles this)
   - Add appropriate indexes

### Frontend Guidelines

1. **React Query Usage**
   - Use queries for GET requests
   - Use mutations for POST/PUT/DELETE
   - Implement optimistic updates for better UX
   - Set up proper cache invalidation

2. **Component Organization**
   - Separate presentational and container components
   - Keep components small and focused
   - Create a shared UI component library (Button, Input, Card, etc.)

3. **API Layer**
   - Create an API client module
   - Centralize API base URL configuration
   - Handle errors consistently

4. **State Management**
   - Use React Query for server state
   - Use React state (useState/useContext) for UI state only
   - Don't duplicate server state in local state

### Database Schema

```sql
-- Collections
CREATE TABLE collections (
  id SERIAL PRIMARY KEY,
  name VARCHAR(100) NOT NULL,
  created_at TIMESTAMP DEFAULT NOW()
);

-- Bookmarks
CREATE TABLE bookmarks (
  id SERIAL PRIMARY KEY,
  url TEXT NOT NULL,
  title VARCHAR(255),
  collection_id INTEGER REFERENCES collections(id) ON DELETE SET NULL,
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);

-- Tags
CREATE TABLE tags (
  id SERIAL PRIMARY KEY,
  name VARCHAR(50) UNIQUE NOT NULL
);

-- Bookmark-Tag junction table
CREATE TABLE bookmark_tags (
  bookmark_id INTEGER REFERENCES bookmarks(id) ON DELETE CASCADE,
  tag_id INTEGER REFERENCES tags(id) ON DELETE CASCADE,
  PRIMARY KEY (bookmark_id, tag_id)
);
```

### Docker Compose

Create a `docker-compose.yml` that includes:
- PostgreSQL database service
- Volume for database persistence
- Environment variables for connection

```yaml
version: '3.8'
services:
  db:
    image: postgres:16-alpine
    environment:
      POSTGRES_USER: bookmark
      POSTGRES_PASSWORD: bookmark
      POSTGRES_DB: bookmark_vault
    ports:
      - "5432:5432"
    volumes:
      - postgres_data:/var/lib/postgresql/data

volumes:
  postgres_data:
```

---

## API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | /api/bookmarks | List bookmarks (with pagination, filters) |
| POST | /api/bookmarks | Create bookmark |
| GET | /api/bookmarks/:id | Get single bookmark |
| PUT | /api/bookmarks/:id | Update bookmark |
| DELETE | /api/bookmarks/:id | Delete bookmark |
| GET | /api/collections | List collections |
| POST | /api/collections | Create collection |
| PUT | /api/collections/:id | Update collection |
| DELETE | /api/collections/:id | Delete collection |
| GET | /api/tags | List tags |

---

## Getting Started

1. Initialize the monorepo with npm workspaces
2. Set up Docker Compose with PostgreSQL
3. Create the Express API with basic routes
4. Set up database schema with migrations
5. Implement the 3-layer architecture
6. Create the React app with Vite
7. Set up React Query
8. Build features incrementally (CRUD for bookmarks first)
9. Add collections, then tags, then search

---

## Stretch Goals (If You Have Extra Time)

- Import/export bookmarks (JSON or HTML)
- Favicon fetching for bookmarks
- Bookmark preview (screenshot or metadata)
- Keyboard shortcuts
- Dark mode
- Browser extension to save bookmarks
