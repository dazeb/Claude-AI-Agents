# Project Initializer - File & Folder Structure Specification

> **Version**: 1.0
> **Last Updated**: January 2026
> **Purpose**: Reference document for validating Project Initializer agent outputs

---

## Overview

The **Project Initializer** agent is responsible for creating the foundational file and folder structure that enables long-running AI agents to work effectively across multiple context windows. This document specifies exactly what files and folders should be created.

---

## Required Core Files

### 1. tests.json
**Purpose**: Machine-readable feature roadmap with 50-200+ atomic units

**Location**: Project root (`/`)

**Format**: JSON

**Required Structure**:
```json
{
  "features": [
    {
      "id": 1,
      "category": "functional|performance|security|accessibility|UX|error-handling",
      "description": "Clear, testable description of the feature",
      "steps": [
        "Step 1 to verify",
        "Step 2 to verify",
        "Step 3 to verify"
      ],
      "passes": false,
      "priority": "high|medium|low"
    }
  ],
  "total": 150,
  "passing": 0,
  "failing": 0,
  "not_started": 150
}
```

**Requirements**:
- Minimum 50 features, recommended 80-200+
- Each feature must be atomic (completable in 1-2 hours)
- Categories must be specific (functional, performance, security, etc.)
- Steps must be clear verification instructions
- All features start with `"passes": false`
- Include summary counts: total, passing, failing, not_started

**Categories to Cover**:
- Functional (core features)
- Performance (load times, optimization)
- Security (auth, validation, sanitization)
- Accessibility (a11y, ARIA, keyboard nav)
- Error handling (edge cases, validation)
- UX (user experience, polish)

---

### 2. claude-progress.txt
**Purpose**: Freeform session memory for tracking decisions and rationale

**Location**: Project root (`/`)

**Format**: Plain text (Markdown-style formatting allowed)

**Initial Template**:
```text
=== Project Initialization - Session 1 ===
Date: [YYYY-MM-DD]
Agent: Project Initializer

## Initial Setup Completed:
- Project type: [e.g., Next.js 14 + TypeScript + Tailwind]
- Created feature list with [N] total features
- Set up [testing framework, e.g., Playwright]
- Configured [linting/formatting, e.g., ESLint + Prettier]
- Created init.sh script
- Made initial git commit

## Architecture Decisions:
- [Technology choice and why, e.g., "Using Prisma ORM for type-safe database access"]
- [State management approach, e.g., "React Context for auth, Zustand for cart"]
- [Testing strategy, e.g., "E2E tests with Playwright, unit tests with Vitest"]

## Project Structure:
- /src - Application source code
- /tests - Integration and E2E tests
- /docs - Documentation and guides
- [Other relevant folders]

## Next Steps:
- Start with [category] features (features #1-10)
- Focus on one feature at a time
- Run init.sh to start environment
- Use [test tool] for verification
- Update this file at the end of each session

## Technical Debt / Known Issues:
- None yet (initial setup)

## Important Notes:
- [Any gotchas, platform-specific quirks, or critical context]
```

**Requirements**:
- Must be created with initial session entry
- Should document ALL architectural decisions
- Must include "Next Steps" section
- Should list project structure
- Freeform format (allow future agents to add notes naturally)

---

### 3. init.sh (or init.bat for Windows)
**Purpose**: One-command environment setup script

**Location**: Project root (`/`)

**Format**: Bash script (executable)

**Minimum Template**:
```bash
#!/bin/bash
# Project Initialization Script
# Run this at the start of each session to prepare the development environment

set -e  # Exit on error

echo "============================================"
echo "  Initializing Development Environment"
echo "============================================"
echo ""

# Check for dependencies
echo "📦 Checking dependencies..."

# Install dependencies if needed (Node.js example)
if [ ! -d "node_modules" ]; then
  echo "Installing npm dependencies..."
  npm install
fi

# Python example (uncomment if Python project)
# if [ ! -d "venv" ]; then
#   echo "Creating Python virtual environment..."
#   python3 -m venv venv
# fi
# source venv/bin/activate
# pip install -r requirements.txt

# Database setup (if applicable)
# echo "🗄️  Setting up database..."
# npm run db:migrate  # or equivalent command

# Start development servers
echo ""
echo "🚀 Starting development servers..."
echo ""

# Backend (if applicable)
# cd backend && npm run dev &

# Frontend
npm run dev &

# Wait a moment for servers to start
sleep 3

echo ""
echo "============================================"
echo "  Environment Ready!"
echo "============================================"
echo ""
echo "Frontend: http://localhost:5173"
echo "Backend:  http://localhost:3000"  # if applicable
echo ""
echo "Run tests: npm test"
echo "Run E2E tests: npm run test:e2e"
echo ""
```

**Requirements**:
- Must be executable (`chmod +x init.sh`)
- Must check for dependencies before installing
- Must start all necessary development servers
- Should include clear output messages
- Must handle both first-time setup and subsequent runs
- Should include comments for common variations
- Must print URLs where servers are running

**Platform Variations**:
- Create `init.bat` for Windows projects (PowerShell/CMD syntax)
- Document which script to use in README.md

---

### 4. README.md
**Purpose**: Project overview with setup instructions

**Location**: Project root (`/`)

**Format**: Markdown

**Minimum Sections**:
```markdown
# [Project Name]

> [One-line project description]

## Overview

[2-3 paragraph description of what this project does and its purpose]

## Tech Stack

- **Frontend**: [e.g., React 18 + TypeScript + Vite + Tailwind CSS]
- **Backend**: [e.g., Node.js + Express + Prisma + PostgreSQL]
- **Testing**: [e.g., Playwright (E2E) + Vitest (unit)]
- **Deployment**: [e.g., Vercel (frontend) + Railway (backend)]

## Getting Started

### Prerequisites

- Node.js 18+ and npm
- PostgreSQL 14+ (if applicable)
- [Other requirements]

### Installation

1. Clone the repository
2. Run the initialization script:
   ```bash
   ./init.sh
   ```
3. Open http://localhost:5173 in your browser

### Development

- **Start dev servers**: `./init.sh`
- **Run tests**: `npm test`
- **Run E2E tests**: `npm run test:e2e`
- **Build for production**: `npm run build`

## Project Structure

```
project-name/
├── src/               # Application source code
│   ├── components/    # React components
│   ├── pages/         # Page components
│   ├── lib/           # Utilities and helpers
│   └── styles/        # CSS/styling
├── tests/             # E2E and integration tests
├── docs/              # Documentation
├── tests.json         # Feature roadmap (50-200+ features)
├── init.sh            # Environment setup script
├── claude-progress.txt # Session memory and decisions
└── README.md          # This file
```

## Long-Running Agent Workflow

This project uses the **Long-Running Agents** methodology for incremental development:

1. **Orientation**: Agent reads `claude-progress.txt` and `tests.json`
2. **Setup**: Agent runs `./init.sh` to prepare environment
3. **Work**: Agent implements ONE feature from `tests.json`
4. **Verify**: Agent tests end-to-end and updates `passes: true`
5. **Commit**: Agent commits with clear message
6. **Document**: Agent updates `claude-progress.txt`

**Feature List**: See `tests.json` for the complete roadmap ([N] features total)

## License

[License type, e.g., MIT]
```

**Requirements**:
- Must include setup instructions referencing init.sh
- Must document project structure
- Must explain Long-Running Agents workflow
- Should include tech stack
- Should reference tests.json and claude-progress.txt

---

### 5. .gitignore
**Purpose**: Exclude generated files from version control

**Location**: Project root (`/`)

**Format**: Plain text

**Minimum Template** (Node.js/Python):
```gitignore
# Dependencies
node_modules/
venv/
__pycache__/
*.pyc

# Environment variables
.env
.env.local
.env.*.local

# Build outputs
dist/
build/
*.log

# IDE
.vscode/
.idea/
*.swp
*.swo

# OS
.DS_Store
Thumbs.db

# Testing
coverage/
.nyc_output/

# Temporary files
*.tmp
.cache/
```

**Requirements**:
- Must exclude dependencies (node_modules, venv)
- Must exclude .env files
- Must exclude build outputs
- Should exclude IDE/OS-specific files
- Customize based on project stack

---

### 6. .env.example
**Purpose**: Template for environment variables

**Location**: Project root (`/`)

**Format**: Plain text (dotenv format)

**Template**:
```env
# Database
DATABASE_URL=postgresql://user:password@localhost:5432/dbname

# API Keys
API_KEY=your_api_key_here
SECRET_KEY=your_secret_key_here

# External Services
STRIPE_PUBLIC_KEY=pk_test_...
STRIPE_SECRET_KEY=sk_test_...

# URLs
FRONTEND_URL=http://localhost:5173
BACKEND_URL=http://localhost:3000

# Feature Flags
ENABLE_ANALYTICS=false
```

**Requirements**:
- Must include ALL required environment variables
- Should use placeholder values (not real secrets)
- Should include comments explaining each variable
- Must be committed to git (unlike .env)

---

## Required Project Structure

### Folder Organization

The Project Initializer must create a logical, organized folder structure. The exact structure varies by project type, but should follow these principles:

#### Web Application (React/Next.js Example)
```
project-name/
├── .git/                    # Git repository (initialized)
├── src/                     # Application source code
│   ├── components/          # Reusable UI components
│   ├── pages/               # Page components (or routes)
│   ├── lib/                 # Utilities, helpers, shared logic
│   ├── hooks/               # Custom React hooks
│   ├── context/             # React context providers
│   ├── styles/              # Global styles, CSS modules
│   ├── types/               # TypeScript type definitions
│   └── config/              # App configuration files
├── tests/                   # E2E and integration tests
│   ├── e2e/                 # End-to-end tests (Playwright/Cypress)
│   ├── integration/         # Integration tests
│   └── fixtures/            # Test data and fixtures
├── public/                  # Static assets
│   ├── images/
│   ├── fonts/
│   └── favicon.ico
├── docs/                    # Documentation
│   └── ARCHITECTURE.md      # (Optional) Architecture decisions
├── tests.json               # Feature roadmap
├── claude-progress.txt      # Session memory
├── init.sh                  # Environment setup script
├── .gitignore               # Git ignore file
├── .env.example             # Environment template
├── README.md                # Project documentation
├── package.json             # Dependencies and scripts
├── tsconfig.json            # TypeScript configuration
├── vite.config.ts           # Vite configuration (or webpack, etc.)
└── playwright.config.ts     # Testing framework config
```

#### Backend API (Python/FastAPI Example)
```
project-name/
├── .git/
├── app/                     # Application code
│   ├── api/                 # API endpoints
│   │   ├── routes/          # Route handlers
│   │   └── dependencies.py  # Shared dependencies
│   ├── models/              # Database models
│   ├── schemas/             # Pydantic schemas
│   ├── services/            # Business logic
│   ├── core/                # Core config, security
│   └── main.py              # Application entry point
├── tests/                   # Test suite
│   ├── api/                 # API tests
│   ├── services/            # Service tests
│   └── conftest.py          # Pytest fixtures
├── alembic/                 # Database migrations (if using Alembic)
├── docs/
├── tests.json
├── claude-progress.txt
├── init.sh
├── .gitignore
├── .env.example
├── README.md
├── requirements.txt         # Python dependencies
├── pyproject.toml           # Python project config
└── pytest.ini               # Pytest configuration
```

#### Full-Stack (Monorepo Example)
```
project-name/
├── .git/
├── frontend/                # Frontend app
│   ├── src/
│   ├── tests/
│   ├── package.json
│   └── vite.config.ts
├── backend/                 # Backend API
│   ├── app/
│   ├── tests/
│   ├── requirements.txt
│   └── main.py
├── shared/                  # Shared code (types, utils)
│   └── types/
├── docs/
├── tests.json               # Combined feature list
├── claude-progress.txt
├── init.sh                  # Starts both frontend and backend
├── .gitignore
├── .env.example
└── README.md
```

### Folder Structure Requirements

**Must Have**:
- Source code directory (`src/`, `app/`, etc.)
- Tests directory (`tests/`, `__tests__/`)
- Documentation directory (`docs/`)
- Git repository (`.git/`)

**Should Have**:
- Logical separation of concerns (components, routes, services)
- Clear naming conventions
- Nested structure for organization (not flat)

**Should NOT**:
- Mix source code and tests in the same folder
- Use unclear abbreviations
- Create deeply nested structures (>4 levels)

---

## Required Configuration Files

### Package Management

**Node.js Projects**: Must create `package.json`
```json
{
  "name": "project-name",
  "version": "0.1.0",
  "private": true,
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "test": "vitest",
    "test:e2e": "playwright test",
    "lint": "eslint src/",
    "format": "prettier --write src/"
  },
  "dependencies": {
    "react": "^18.2.0",
    "react-dom": "^18.2.0"
  },
  "devDependencies": {
    "@playwright/test": "^1.40.0",
    "@types/react": "^18.2.0",
    "@vitejs/plugin-react": "^4.2.0",
    "eslint": "^8.55.0",
    "prettier": "^3.1.0",
    "typescript": "^5.3.0",
    "vite": "^5.0.0",
    "vitest": "^1.0.0"
  }
}
```

**Python Projects**: Must create `requirements.txt` or `pyproject.toml`
```txt
fastapi==0.108.0
uvicorn==0.25.0
sqlalchemy==2.0.23
pydantic==2.5.0
pytest==7.4.3
pytest-asyncio==0.21.1
httpx==0.25.2
```

### Testing Framework Configuration

**Must include** testing framework configuration:
- `playwright.config.ts` (for Playwright)
- `cypress.config.js` (for Cypress)
- `pytest.ini` (for Pytest)
- `vitest.config.ts` (for Vitest)
- `jest.config.js` (for Jest)

**Example Playwright Config**:
```typescript
import { defineConfig, devices } from '@playwright/test';

export default defineConfig({
  testDir: './tests/e2e',
  fullyParallel: true,
  forbidOnly: !!process.env.CI,
  retries: process.env.CI ? 2 : 0,
  workers: process.env.CI ? 1 : undefined,
  reporter: 'html',
  use: {
    baseURL: 'http://localhost:5173',
    trace: 'on-first-retry',
  },
  projects: [
    {
      name: 'chromium',
      use: { ...devices['Desktop Chrome'] },
    },
  ],
  webServer: {
    command: 'npm run dev',
    url: 'http://localhost:5173',
    reuseExistingServer: !process.env.CI,
  },
});
```

### Code Quality Configuration

**Should include** (not required but recommended):
- ESLint configuration (`.eslintrc.json`)
- Prettier configuration (`.prettierrc`)
- TypeScript configuration (`tsconfig.json`)
- Pre-commit hooks (`.husky/` or `.git/hooks/`)

---

## Git Repository Setup

### Required Git Operations

The Project Initializer must:

1. **Initialize repository**: `git init`
2. **Create .gitignore**: Before first commit
3. **Stage initial files**: `git add .`
4. **Make initial commit**: `git commit -m "Initial project setup with feature list and scaffolding"`

### Initial Commit Requirements

**Commit Message Format**:
```
Initial project setup with feature list and scaffolding

- Created [N] feature roadmap in tests.json
- Set up [framework] with [testing tool]
- Configured ESLint and Prettier
- Created init.sh for environment setup
- Generated claude-progress.txt for session tracking
```

**What Must Be Committed**:
- All core files (tests.json, claude-progress.txt, init.sh, README.md)
- All configuration files
- Project scaffolding (src/, tests/ directories)
- .env.example (but NOT .env)
- .gitignore

**What Must NOT Be Committed**:
- node_modules/, venv/
- .env files with secrets
- Build outputs (dist/, build/)
- IDE-specific files (.vscode/, .idea/)

---

## Basic Integration Test

### Purpose
Verify that the project setup works before completing initialization.

### Requirements

**Web Applications**: Must create a basic E2E test
```typescript
// tests/e2e/basic.spec.ts
import { test, expect } from '@playwright/test';

test('application loads successfully', async ({ page }) => {
  await page.goto('/');

  // Verify page loads without errors
  await expect(page).toHaveTitle(/Project Name/);

  // Verify basic navigation works
  await page.click('text=Home');
  await expect(page).toHaveURL('/');
});
```

**API Projects**: Must create a basic API test
```python
# tests/api/test_basic.py
import pytest
from httpx import AsyncClient
from app.main import app

@pytest.mark.asyncio
async def test_health_check():
    async with AsyncClient(app=app, base_url="http://test") as client:
        response = await client.get("/health")
        assert response.status_code == 200
        assert response.json() == {"status": "ok"}
```

### Test Execution

Before completing initialization, the agent must:
1. Run the basic integration test
2. Verify it passes
3. Document test execution in claude-progress.txt
4. Only proceed if test is successful

---

## Technology-Specific Scaffolding

### Frontend Frameworks

**React + Vite**:
```bash
npm create vite@latest project-name -- --template react-ts
```

**Next.js**:
```bash
npx create-next-app@latest project-name --typescript --tailwind --app --src-dir
```

**Vue**:
```bash
npm create vue@latest project-name
```

### Backend Frameworks

**FastAPI (Python)**:
```bash
mkdir project-name && cd project-name
python -m venv venv
source venv/bin/activate
pip install fastapi uvicorn sqlalchemy pydantic
```

**Express (Node.js)**:
```bash
mkdir project-name && cd project-name
npm init -y
npm install express typescript @types/express @types/node
npx tsc --init
```

**NestJS**:
```bash
npm i -g @nestjs/cli
nest new project-name
```

### Testing Frameworks

**Playwright**:
```bash
npm init playwright@latest
```

**Cypress**:
```bash
npm install cypress --save-dev
npx cypress open
```

**Pytest**:
```bash
pip install pytest pytest-asyncio httpx
```

---

## Validation Checklist

Use this checklist to verify the Project Initializer completed its job correctly:

### Core Files
- [ ] `tests.json` exists with 50-200+ features
- [ ] `claude-progress.txt` exists with initial session entry
- [ ] `init.sh` (or `init.bat`) exists and is executable
- [ ] `README.md` exists with setup instructions
- [ ] `.gitignore` exists with sensible defaults
- [ ] `.env.example` exists with all required variables

### Project Structure
- [ ] Source code directory created (`src/`, `app/`)
- [ ] Tests directory created (`tests/`, `__tests__/`)
- [ ] Docs directory created (`docs/`)
- [ ] Public/static directory created (if web project)
- [ ] Logical folder organization (components, routes, etc.)

### Configuration
- [ ] Package file exists (`package.json`, `requirements.txt`)
- [ ] Testing framework configured
- [ ] TypeScript configured (if TypeScript project)
- [ ] Linting configured (ESLint, Ruff, etc.)
- [ ] Build tool configured (Vite, Webpack, etc.)

### Git Repository
- [ ] Git repository initialized (`.git/` exists)
- [ ] Initial commit made with descriptive message
- [ ] `.gitignore` prevents committing sensitive files
- [ ] No sensitive data in version control

### Testing
- [ ] Testing framework installed and configured
- [ ] Basic integration test created
- [ ] Basic integration test passes
- [ ] Test execution documented in claude-progress.txt

### Environment
- [ ] `init.sh` runs without errors
- [ ] Development server starts successfully
- [ ] All dependencies installed correctly
- [ ] Application accessible at documented URL

### Documentation
- [ ] README explains setup process
- [ ] README references Long-Running Agents workflow
- [ ] claude-progress.txt documents architecture decisions
- [ ] claude-progress.txt includes "Next Steps"

### Feature List Quality
- [ ] Features are atomic (1-2 hours each)
- [ ] Features have clear verification steps
- [ ] Features categorized correctly
- [ ] Features prioritized (high/medium/low)
- [ ] All features start with `passes: false`
- [ ] Summary counts match feature array length

---

## Common Mistakes to Avoid

### ❌ Anti-Patterns

1. **Too Few Features (<50)**
   - Results in missing edge cases
   - Future agents miss critical functionality

2. **Vague Feature Descriptions**
   - "Implement authentication" is too broad
   - Should be: "Create signup endpoint with email validation"

3. **Unstructured Feature Format**
   - Using Markdown lists instead of JSON
   - Makes it hard for agents to update programmatically

4. **Missing init.sh Script**
   - Future agents waste time figuring out setup
   - Breaks session continuity

5. **No Initial Git Commit**
   - Loses baseline reference
   - Can't track changes effectively

6. **Not Running Basic Test**
   - May deliver broken environment
   - Future agents start with failing state

7. **Over-Engineering Initial Setup**
   - Adding unnecessary complexity
   - Should be minimal but complete

8. **Skipping Environment Configuration**
   - No .env.example
   - Future agents don't know required variables

9. **Poor Folder Organization**
   - Flat structure with no separation
   - Mixing concerns in same directory

10. **Incomplete Documentation**
    - README missing setup instructions
    - claude-progress.txt lacks architectural decisions

---

## Success Criteria

A successful Project Initializer output should:

1. **Enable Quick Orientation**: Future agent can understand project in <2 minutes
2. **One-Command Setup**: `./init.sh` works every time
3. **Clear Roadmap**: `tests.json` captures all requirements
4. **Test-Ready**: Testing framework configured and working
5. **Well-Documented**: README and claude-progress.txt provide context
6. **Version Controlled**: Git repo with clean initial commit
7. **Validated**: Basic integration test passes
8. **Production-Ready Structure**: Follows best practices for the stack

---

## Examples by Project Type

### Example 1: E-commerce Web App (Next.js)

**Files Created**:
- tests.json (120 features: auth, products, cart, checkout, admin)
- claude-progress.txt (architecture: Next.js 14, Prisma, PostgreSQL, Stripe)
- init.sh (npm install, db migrate, dev server)
- README.md
- .gitignore
- .env.example

**Structure**:
```
ecommerce-app/
├── src/
│   ├── app/              # Next.js app directory
│   ├── components/
│   ├── lib/
│   └── types/
├── tests/e2e/
├── prisma/
│   └── schema.prisma
├── tests.json
├── claude-progress.txt
├── init.sh
└── README.md
```

### Example 2: REST API (FastAPI)

**Files Created**:
- tests.json (60 features: endpoints, auth, validation, error handling)
- claude-progress.txt (architecture: FastAPI, PostgreSQL, JWT, Redis)
- init.sh (venv setup, pip install, db migrate, uvicorn)
- README.md
- .gitignore
- .env.example
- requirements.txt

**Structure**:
```
api-service/
├── app/
│   ├── api/
│   ├── models/
│   ├── schemas/
│   └── main.py
├── tests/
├── alembic/
├── tests.json
├── claude-progress.txt
├── init.sh
└── README.md
```

### Example 3: Mobile App (React Native)

**Files Created**:
- tests.json (80 features: onboarding, features, offline, notifications)
- claude-progress.txt (architecture: Expo, React Navigation, AsyncStorage)
- init.sh (npm install, expo start)
- README.md
- .gitignore
- .env.example

**Structure**:
```
mobile-app/
├── src/
│   ├── screens/
│   ├── components/
│   ├── navigation/
│   └── services/
├── tests/
├── tests.json
├── claude-progress.txt
├── init.sh
└── README.md
```

---

## Version History

- **v1.0** (January 2026): Initial specification based on Long-Running Agents methodology

---

## References

- [Project Initializer Agent Definition](.claude/agents/engineering/project-initializer.md)
- [Long-Running Agents Best Practices](LONG_RUNNING_AGENTS.md)
- [Anthropic: Effective Harnesses for Long-Running Agents](https://www.anthropic.com/engineering/effective-harnesses-for-long-running-agents)
