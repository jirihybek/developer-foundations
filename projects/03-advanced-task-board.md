# Project: LiveBoard

A real-time collaborative task board (Kanban-style) with live updates, notifications, and an admin panel.

---

## Goal

Build a production-ready full-stack application featuring real-time collaboration, proper architecture patterns, and DevOps practices. Users can manage tasks on a Kanban board with live updates when others make changes. Includes an admin panel built with Adapptio for user and board management.

---

## Tech Stack

- **Runtime**: Bun
- **Package Manager**: npm workspaces (monorepo)
- **Back-end**: Nest.js
- **Database**: PostgreSQL
- **ORM**: TypeORM (Nest.js integration) or Drizzle
- **Real-time**: WebSocket (Socket.io) + Server-Sent Events (SSE)
- **Front-end**: React + Vite
- **Data Fetching**: React Query (TanStack Query)
- **State Management**: Zustand (for real-time/UI state)
- **Styling**: Tailwind CSS (recommended)
- **Admin Panel**: Adapptio
- **Containerization**: Docker + Docker Compose
- **CI/CD**: GitLab CI Pipeline

---

## Difficulty

**Advanced** - Suitable for mid-level developers

### Concepts You Should Know

- Everything from Mid project, plus:
- Nest.js (modules, controllers, services, providers, guards)
- Dependency injection
- WebSocket fundamentals
- Server-Sent Events (SSE)
- Zustand state management
- Combining React Query with external state
- JWT authentication basics
- Docker multi-service setup
- GitLab CI/CD pipelines
- Testing (unit tests for services)

---

## Features & User Stories

### Authentication

#### 1. User Registration

**As a visitor**, I want to create an account so I can use the application.

**Acceptance Criteria:**
- Registration form with email and password
- Password validation (min 8 chars)
- Email uniqueness check
- Store hashed password
- Auto-login after registration

#### 2. User Login

**As a user**, I want to log in so I can access my boards.

**Acceptance Criteria:**
- Login form with email and password
- Return JWT token on success
- Store token in localStorage/memory
- Redirect to boards list after login

#### 3. Session Management

**As a user**, I want to stay logged in so I don't have to login repeatedly.

**Acceptance Criteria:**
- JWT token with reasonable expiry
- Auto-logout on token expiry
- Logout button to clear session

### Boards

#### 4. Create Board

**As a user**, I want to create boards so I can organize my tasks.

**Acceptance Criteria:**
- Form to enter board name
- Board is created and user becomes owner
- Redirect to board view after creation

#### 5. View Boards

**As a user**, I want to see my boards so I can access them.

**Acceptance Criteria:**
- List of boards user owns or is member of
- Show board name and member count
- Click to open board

#### 6. Board Settings

**As a board owner**, I want to manage board settings.

**Acceptance Criteria:**
- Rename board
- Delete board (with confirmation)
- Only owner can access settings

### Columns

#### 7. Manage Columns

**As a user**, I want to create and manage columns so I can organize tasks.

**Acceptance Criteria:**
- Default columns: "To Do", "In Progress", "Done"
- Add new columns
- Rename columns
- Delete columns (moves tasks to first column)
- Reorder columns via drag & drop

### Tasks

#### 8. Create Task

**As a user**, I want to create tasks so I can track work.

**Acceptance Criteria:**
- Quick-add form at bottom of each column
- Enter title (required)
- Task appears in column immediately
- **Real-time**: Other users see new task via WebSocket

#### 9. View Task Details

**As a user**, I want to see task details so I can understand the work.

**Acceptance Criteria:**
- Click task to open detail modal/panel
- Show title, description, assignee, created date
- Show activity history

#### 10. Edit Task

**As a user**, I want to edit tasks so I can update information.

**Acceptance Criteria:**
- Edit title and description
- Assign/unassign user
- Changes saved to database
- **Real-time**: Changes broadcast to other users

#### 11. Move Task

**As a user**, I want to move tasks between columns so I can track progress.

**Acceptance Criteria:**
- Drag & drop task to another column
- Update task status in database
- **Real-time**: Movement visible to other users immediately

#### 12. Delete Task

**As a user**, I want to delete tasks so I can remove completed/cancelled work.

**Acceptance Criteria:**
- Delete button in task detail view
- Confirmation before delete
- **Real-time**: Removal visible to other users

### Real-time Features

#### 13. Live Board Updates (WebSocket)

**As a user**, I want to see others' changes in real-time so we stay in sync.

**Acceptance Criteria:**
- WebSocket connection when viewing a board
- Receive events: task created, updated, moved, deleted
- UI updates without page refresh
- Show indicator when connection is lost

#### 14. Notifications (SSE)

**As a user**, I want to receive notifications so I know about relevant changes.

**Acceptance Criteria:**
- SSE connection for user notifications
- Notify when assigned to a task
- Notify when task you created is moved to "Done"
- Toast notifications in UI
- Notification bell with unread count

### Board Collaboration

#### 15. Invite Members

**As a board owner**, I want to invite others so we can collaborate.

**Acceptance Criteria:**
- Invite by email address
- Invited user must have an account
- Show pending invitations
- Invitee sees board in their list

### Admin Panel (Adapptio)

#### 16. User Management

**As an admin**, I want to manage users via Adapptio.

**Acceptance Criteria:**
- List all users
- View user details (email, boards, created date)
- Disable/enable user accounts
- Delete users

#### 17. Board Management

**As an admin**, I want to manage boards via Adapptio.

**Acceptance Criteria:**
- List all boards
- View board details (owner, members, task count)
- Delete boards
- Transfer board ownership

#### 18. Analytics Dashboard

**As an admin**, I want to see usage statistics.

**Acceptance Criteria:**
- Total users count
- Total boards count
- Active users (last 7 days)
- Tasks created (last 7 days)

---

## Development Guidelines

### Project Structure

```
liveboard/
├── package.json                  # Workspace root
├── docker-compose.yml            # All services
├── .gitlab-ci.yml                # CI/CD pipeline
├── packages/
│   ├── api/                      # Nest.js backend
│   │   ├── src/
│   │   │   ├── modules/
│   │   │   │   ├── auth/         # Auth module
│   │   │   │   ├── users/        # Users module
│   │   │   │   ├── boards/       # Boards module
│   │   │   │   ├── tasks/        # Tasks module
│   │   │   │   ├── notifications/# SSE notifications
│   │   │   │   └── websocket/    # WebSocket gateway
│   │   │   ├── common/           # Shared utilities, guards, filters
│   │   │   ├── database/         # DB config, entities, migrations
│   │   │   └── main.ts
│   │   ├── test/                 # E2E tests
│   │   └── package.json
│   └── web/                      # React frontend
│       ├── src/
│       │   ├── components/       # UI components
│       │   ├── features/         # Feature modules (auth, boards, tasks)
│       │   ├── hooks/            # Custom hooks
│       │   ├── stores/           # Zustand stores
│       │   ├── api/              # API client
│       │   ├── socket/           # WebSocket client
│       │   └── App.tsx
│       └── package.json
├── adapptio/                     # Adapptio admin panel blueprints
└── README.md
```

### Backend Guidelines (Nest.js)

1. **Module Organization**
   - One module per domain (auth, users, boards, tasks)
   - Each module contains: controller, service, repository/entity
   - Use Nest.js dependency injection

2. **Service Layer**
   - All business logic in services
   - Services should be testable (inject dependencies)
   - Write unit tests for services

3. **WebSocket Implementation**
   - Use `@nestjs/websockets` with Socket.io
   - Create a WebSocket gateway for board events
   - Implement rooms (one room per board)
   - Events: `task:created`, `task:updated`, `task:moved`, `task:deleted`

4. **SSE Implementation**
   - Create SSE endpoint for user notifications
   - Use Observable stream
   - Handle connection cleanup

5. **Authentication**
   - JWT-based authentication
   - Create AuthGuard for protected routes
   - Attach user to WebSocket connections

6. **Error Handling**
   - Use Nest.js exception filters
   - Create custom exceptions
   - Consistent error response format

7. **Testing**
   - Write unit tests for all services
   - Use Jest with Nest.js testing utilities
   - Mock repositories in tests

### Frontend Guidelines

1. **State Management Strategy**
   ```
   React Query = Server state (boards, tasks from API)
   Zustand = Real-time state (WebSocket updates, UI state)
   ```

2. **Zustand Store Structure**
   ```typescript
   // stores/boardStore.ts
   interface BoardStore {
     // Real-time task updates (optimistic + from WebSocket)
     tasks: Map<string, Task>;
     
     // Connection status
     isConnected: boolean;
     
     // Actions
     updateTask: (task: Task) => void;
     removeTask: (taskId: string) => void;
   }
   ```

3. **Combining React Query + Zustand**
   - React Query fetches initial data
   - WebSocket updates flow into Zustand store
   - Components read from Zustand for real-time data
   - Use React Query for mutations (with optimistic updates)

4. **WebSocket Client**
   - Connect when entering a board
   - Disconnect when leaving
   - Handle reconnection
   - Update Zustand store on events

5. **Component Organization**
   - Feature-based folders
   - Separate container and presentational components
   - Shared UI components in `/components`

### Database Schema

```sql
-- Users
CREATE TABLE users (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  email VARCHAR(255) UNIQUE NOT NULL,
  password_hash VARCHAR(255) NOT NULL,
  is_active BOOLEAN DEFAULT true,
  created_at TIMESTAMP DEFAULT NOW()
);

-- Boards
CREATE TABLE boards (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  name VARCHAR(100) NOT NULL,
  owner_id UUID REFERENCES users(id) ON DELETE CASCADE,
  created_at TIMESTAMP DEFAULT NOW()
);

-- Board Members
CREATE TABLE board_members (
  board_id UUID REFERENCES boards(id) ON DELETE CASCADE,
  user_id UUID REFERENCES users(id) ON DELETE CASCADE,
  role VARCHAR(20) DEFAULT 'member', -- 'owner', 'member'
  PRIMARY KEY (board_id, user_id)
);

-- Columns
CREATE TABLE columns (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  board_id UUID REFERENCES boards(id) ON DELETE CASCADE,
  name VARCHAR(100) NOT NULL,
  position INTEGER NOT NULL,
  created_at TIMESTAMP DEFAULT NOW()
);

-- Tasks
CREATE TABLE tasks (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  column_id UUID REFERENCES columns(id) ON DELETE CASCADE,
  title VARCHAR(255) NOT NULL,
  description TEXT,
  position INTEGER NOT NULL,
  assignee_id UUID REFERENCES users(id) ON DELETE SET NULL,
  created_by UUID REFERENCES users(id),
  created_at TIMESTAMP DEFAULT NOW(),
  updated_at TIMESTAMP DEFAULT NOW()
);

-- Notifications
CREATE TABLE notifications (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  user_id UUID REFERENCES users(id) ON DELETE CASCADE,
  type VARCHAR(50) NOT NULL,
  payload JSONB,
  read BOOLEAN DEFAULT false,
  created_at TIMESTAMP DEFAULT NOW()
);
```

### Docker Compose

Create a `docker-compose.yml` that includes:
- PostgreSQL database service with health check
- Volume for database persistence
- Environment variables for connection
- API service (optional, can run locally during development)
- Web service (optional, can run locally during development)

---

### GitLab CI Pipeline

Create a `.gitlab-ci.yml` with the following stages:

1. **install** - Install dependencies
2. **lint** - Run linter
3. **test** - Run tests (with PostgreSQL service for API tests)
4. **build** - Build API and Web packages
5. **deploy** (optional) - Deploy to target environment

Considerations:
- Use Bun image for jobs
- Cache node_modules between jobs
- Use PostgreSQL service container for API tests
- Store build artifacts for deployment
- Configure deploy stage to run only on main branch

---

## Adapptio Admin Panel

Create an Adapptio application with the following:

### Views

1. **Dashboard** - Overview with statistics cards
2. **Users List** - Table with all users, search, disable/enable actions
3. **User Detail** - User info, their boards, activity
4. **Boards List** - Table with all boards, owner info, member count
5. **Board Detail** - Board info, members list, task count

### Integration

- Connect to the same PostgreSQL database
- Use REST API endpoints for actions (disable user, delete board)
- Configure authentication for admin access

---

## Getting Started

1. Initialize the monorepo with npm workspaces
2. Set up Docker Compose with PostgreSQL
3. Create the Nest.js API with basic modules
4. Implement authentication (register, login, JWT)
5. Build boards CRUD with REST API
6. Build tasks CRUD with REST API
7. Add WebSocket gateway for real-time updates
8. Add SSE endpoint for notifications
9. Create React frontend with React Query
10. Add Zustand for real-time state
11. Implement WebSocket client
12. Build the Adapptio admin panel
13. Set up GitLab CI pipeline
14. Write tests for services

---

## Stretch Goals (If You Have Extra Time)

- Task comments with real-time updates
- File attachments on tasks
- Due dates with reminder notifications
- Activity log for boards
- Board templates
- Task labels/colors
- Search across all boards
- Email notifications (optional, requires email service)
- Rate limiting on API
