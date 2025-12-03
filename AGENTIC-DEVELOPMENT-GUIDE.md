# Agentic Development Guide
Complete reference for hands-free AI-powered coding with Warp

---

## Table of Contents
1. [Getting Started](#getting-started)
2. [Rules Overview](#rules-overview)
3. [Key Principles](#key-principles)
4. [WARP.md Template](#warpmd-template)
5. [Best Practices](#best-practices)
6. [Hands-Free Development](#hands-free-development)
7. [Real-World Examples](#real-world-examples)
8. [Living Documentation](#living-documentation)
9. [Quick Reference](#quick-reference)

---

## Getting Started

### Basic Usage
Just ask the AI agent naturally:
- "Fix the bug in my login function"
- "Add error handling to this API endpoint"
- "Refactor this code to be more efficient"
- "Write tests for the User class"

The agent can read code, understand context, make edits, run commands, and verify changes work correctly.

### Key Tips
1. **Be specific about what you want**
   - Instead of: "improve my code"
   - Try: "add input validation to the signup form"

2. **Handle complex tasks**
   - "Migrate this component from JavaScript to TypeScript"
   - "Set up a REST API with authentication"
   - "Debug why tests are failing and fix them"

3. **Context is maintained**
   - The agent remembers the conversation and sees file changes
   - Build on previous requests naturally

### The /init Command
When you run `/init` in a Git repository:
1. **Indexes your codebase** - Enables semantic search and context-aware responses
2. **Generates WARP.md** - Creates initial project rules based on codebase analysis
3. **Links existing rule files** - Integrates CLAUDE.md, .cursorrules, AGENT.md, etc.

---

## Rules Overview

### What Are Rules?
Rules are instructions that guide the AI agent's behavior. They eliminate the need to re-explain your project setup every time.

### Types of Rules

**Global Rules** (optional)
- Personal preferences that apply to all projects
- Accessed via: Warp Drive > Personal > Rules
- Example: "Always use functional components in React"

**Project Rules** (WARP.md)
- Live in your codebase root
- Apply automatically when working in that project
- Version controlled with your code

**Hierarchical Rules** (for monorepos)
```
project/
  WARP.md          # Project-wide rules
  api/
    WARP.md        # API-specific rules (takes precedence in api/)
  frontend/
    WARP.md        # Frontend-specific rules (takes precedence in frontend/)
```

**Rule Precedence**
- Nearest WARP.md > Root WARP.md > Global rules
- Subdirectory rules override parent directory rules

---

## Key Principles

### WARP.md is the Central Piece
It's your "instruction manual" for the AI:
- **Without WARP.md**: You explain everything each time
- **With WARP.md**: High-level requests to a developer who knows your codebase

### What Makes a Good WARP.md
1. **Specific to your project** (not generic advice)
2. **Command-focused** (exact commands to run)
3. **Prescriptive** (clear tooling choices)
4. **Clear about what NOT to do**
5. **References subdirectory rules when applicable**

### Living Document Philosophy
- Start minimal, grow organically
- Update after repeating instructions
- Document architectural decisions
- Add guardrails after mistakes
- Version control it with your code

---

## WARP.md Template

### Basic Structure
```markdown
# Project Overview
[Brief description of what your project does]

# Tech Stack
- Framework: [e.g., Next.js 14, Django 4.2]
- Language: [e.g., TypeScript, Python 3.11]
- Database: [e.g., PostgreSQL, MongoDB]
- Key dependencies: [list main libraries]

# Project Structure
```
/src
  /components  # React components
  /api        # API routes
  /utils      # Helper functions
```

# Development Guidelines

## Code Style
- Use functional components with hooks
- Prefer async/await over promises
- Follow ESLint configuration

## Testing
- Write tests for all new features
- Run `npm test` before committing
- Aim for 80% coverage

## Git Workflow
- Use conventional commits (feat:, fix:, docs:)
- Create feature branches from main
- Squash commits before merging

# Commands
- `npm run dev` - Start development server
- `npm run build` - Build for production
- `npm test` - Run test suite
- `npm run lint` - Check code style

# Environment Variables
Required variables (see .env.example):
- DATABASE_URL
- API_KEY
- JWT_SECRET

# Common Patterns

## API Error Handling
Always wrap API calls in try-catch blocks and return consistent error responses

## State Management
Use Zustand for global state, React Query for server state

# Verification Requirements
- Run tests after every code change
- Run linter and fix issues automatically
- Verify functionality works before marking complete
- Update documentation when adding features

# Never Assume
- Check existing code before making changes
- Search for similar patterns in codebase
- Ask before making architectural decisions

# Git Workflow
- NEVER commit unless explicitly asked
- Descriptive commit messages following conventional commits
- Create feature branches when requested
```

### What Goes Into WARP.md

**Project Knowledge**
- Tech stack and versions
- Architecture decisions
- File/folder structure conventions
- Dependencies and why they're used

**Behavioral Rules**
- Code style and patterns
- Testing requirements
- Error handling approaches
- Security practices
- Performance considerations

**Workflow Instructions**
- How to run/test/build
- Git conventions
- When to verify changes
- What needs approval vs. what to do automatically

**Context That Prevents Mistakes**
- Common pitfalls to avoid
- Known limitations
- Integration requirements
- Environment-specific quirks

---

## Best Practices

### Starting a New Project

**Option 1: Use Warp's Zero State**
1. Open a new tab in Warp
2. Click "Create a New Project"
3. Give a detailed prompt describing what you want to build

**Option 2: Manual Setup**
1. `mkdir my-project && cd my-project`
2. `git init`
3. Tell the agent: "Create a [type] project with [tech stack] that does [purpose]"
4. Agent scaffolds project, then run `/init`

### Keep WARP.md Concise
- Only include non-obvious information
- Focus on your specific conventions
- Optimize large files to conserve tokens
- Remove outdated information regularly

### Treat as Living Documentation
- Update it as your project evolves
- Document patterns as they emerge
- Add guardrails after discovering issues
- Review and refine periodically

### Use Hierarchical Rules for Monorepos
```
project/
  WARP.md              # Shared conventions
  packages/
    api/
      WARP.md          # API-specific rules
    design-system/
      WARP.md          # Design system rules
```

---

## Hands-Free Development

### Key Elements for Success

**1. Detailed Initial Prompt**
Be specific:
```
"Create a REST API for a task management system using:
- FastAPI with Python 3.11
- PostgreSQL database with SQLAlchemy
- JWT authentication
- Docker containerization
- pytest for testing
Include: user registration, task CRUD, task assignments, and due date notifications"
```

**2. Comprehensive WARP.md from the Start**
After project creation, refine WARP.md to include:
- Testing commands and expectations
- Deployment process
- Error handling patterns
- Security requirements
- Performance expectations
- Code organization rules

**3. Clear Testing Strategy**
Specify upfront:
- Test framework to use
- Coverage expectations
- How to run tests
- CI/CD requirements

**4. Structured Communication**
Be explicit in requests:
- ✅ "Add user authentication with email/password, including password reset flow, email verification, and rate limiting. Write tests and ensure all pass."
- ❌ "Add login"

### Recommended Workflow
```
1. Create project with detailed requirements
2. Review and refine generated WARP.md
3. Set up testing infrastructure first
4. Build features iteratively with verification
5. Always include "and test this" in requests
6. Let agent run linters, tests, and checks after changes
```

### Pro Tips for Feature Requests

**Use This Pattern:**
```
"Add [feature] to [location]. 
Include error handling, input validation, and tests.
Verify it works by [how to verify].
Fix any linting issues."
```

**Add to Your WARP.md:**
```markdown
# Verification Requirements
- Run tests after every code change
- Run linter and fix issues automatically
- Verify functionality works before marking complete
- Update documentation when adding features

# Never Assume
- Check existing code before making changes
- Search for similar patterns in codebase
- Ask before making architectural decisions

# Git Workflow
- NEVER commit unless explicitly asked
- Descriptive commit messages following conventional commits
- Create feature branches when requested
```

---

## Real-World Examples

### Production Example: Next.js Project

```markdown
# Core assistant rules
- No inline style attributes. Use CSS variables/tokens and Tailwind utilities only.
- Always import @ratigan/design-system/global.css in the app's global CSS
- Use these token-backed utilities: bg-background, bg-surface, text-fg, text-fg-muted, text-fg-inverse, border-[--color-border], bg-primary, bg-secondary, bg-success, bg-warning, bg-error
- Rule precedence: nearest WARP.md > root WARP.md > .warp/rules.md
- Editor/linting: VS Code should set css.lint.unknownAtRules to ignore (for Tailwind @theme). If using Stylelint, ignore the theme at-rule.

# Project/tooling rules I'll respect
- Monorepo with Bun workspaces
- Package manager: Bun (bun install; bun --cwd frontend dev|build|start)
- Lint: bun --cwd frontend run lint (ESLint 9 + eslint-config-next)
- Next.js 15 (App Router), React 19, Tailwind v4 (via @tailwindcss/postcss in postcss.config.mjs)
- TypeScript path alias: @/* -> ./src/*; frontend source under frontend/src
- Default branch: main
- Do not commit .env; use .env.example; root .gitignore is authoritative

# Design system-specific rules (packages/design-system/WARP.md)
- All tokens live in the design system; apps must consume via CSS variables (no hex in apps)

# Your personal workflow rules
- Commits should use git ship "Commit message"
- Always use Bun as the package manager
- Always use the latest versions of packages we install
```

### Common Pattern Examples

**Authentication Rules**
```markdown
# Authentication
- Always validate JWT tokens
- Use bcrypt for password hashing
- Session timeout: 30 minutes
- Password requirements: min 12 chars, 1 uppercase, 1 number, 1 special
```

**Database Conventions**
```markdown
# Database
- Use migrations for all schema changes
- Never query in loops (use batch operations)
- Always use parameterized queries (prevent SQL injection)
- Connection pooling via Prisma
- Run migrations: npm run db:migrate
```

**Error Handling**
```markdown
# Error Handling
- Log errors to Sentry
- Return user-friendly messages (never expose stack traces)
- Include correlation IDs in all errors
- Use ErrorBoundary for React components
```

**Deployment**
```markdown
# Deployment
- Staging deploys automatically on PR merge
- Production requires manual approval
- Run migrations before deployment
- Health check endpoint: /api/health
- Rollback command: ./scripts/rollback.sh
```

---

## Living Documentation

### Start Minimal, Grow Organically

**Day 1: Simple**
```markdown
# Initial WARP.md
- Framework: Next.js 14
- Package manager: npm
- Run: npm run dev
```

**Week 2: Patterns Emerging**
```markdown
# WARP.md
- Framework: Next.js 14
- Package manager: npm
- Run: npm run dev

# Patterns we've established
- API routes go in /app/api
- Use Server Actions for mutations
- Client components must have 'use client' directive
```

### Example Evolution

**Month 1: Simple**
```markdown
- React + TypeScript
- npm run dev to start
```

**Month 3: Patterns Emerging**
```markdown
- React + TypeScript
- npm run dev to start

# File Organization
- Components: /components (shared)
- Features: /features (feature-specific)
- Hooks: /hooks (reusable logic)

# State Management
- Use Zustand for global state
- React Query for server state
```

**Month 6: Mature**
```markdown
- React 18 + TypeScript 5.2
- npm run dev to start
- Test: npm test (Jest + RTL)

# Architecture
- Feature-based folder structure
- Each feature has: components/, hooks/, api/, types/

# State Management
- Zustand for global state
- React Query for server state
- Context only for theme/auth

# Testing
- Unit tests for hooks and utilities
- Integration tests for features
- E2E tests for critical paths
- Aim for 80% coverage

# Common Patterns
## Error Handling
Always use ErrorBoundary and toast for user feedback

## API Calls
All API calls go through /lib/api with automatic retry
```

### When to Update WARP.md

**1. After Repeating Instructions**
If you tell the agent the same thing twice, add it to WARP.md:
- "Remember, we use Zod for validation"
- "We decided to use React Query for data fetching"

**2. After Architectural Decisions**
Major changes warrant updates:
- "We're switching from REST to tRPC"
- "All new components should use Tailwind, not CSS modules"
- "We're deprecating the old auth system"

**3. When Patterns Emerge**
Document recurring patterns:
- Every new feature follows similar structure
- Tests always written in specific format
- Error handling has consistent pattern

**4. After Mistakes**
If the agent makes mistakes due to lack of knowledge:
- "Don't use the /legacy folder, it's deprecated"
- "Never modify files in /generated, they're auto-generated"

### Practical Workflow

**Version Control It**
```bash
git add WARP.md
git commit -m "docs: update WARP.md with new auth pattern"
```

Benefits:
- History of how your project evolved
- Ability to reference old approaches
- Team visibility into changes

**Use Comments for Temporal Context**
```markdown
# Database
- Using PostgreSQL 15
- Connection pooling: Prisma (migrating from TypeORM - complete by Q1 2025)
- Migration command: npm run db:migrate

# Deprecated (remove after v2.0)
- ~~Old REST endpoints in /api/v1~~ (use /api/v2)
```

**Incremental Updates During Development**
```
You: "Add user authentication"
Agent: [builds auth system]
You: "Update WARP.md to document the auth pattern we just established"
Agent: [updates WARP.md with auth conventions]
```

### Structure for Evolving Projects

```markdown
# Current Architecture
[What's true NOW]

# In Progress
- Migrating from REST to GraphQL (see /graphql branch)
- A/B testing new UI components

# Conventions
[Patterns we follow]

# Deprecated
- Old authentication (remove after all users migrate)
- Legacy API endpoints (shutdown date: 2025-03-01)

# Future Plans
- Consider moving to monorepo
- Evaluate Bun as npm replacement
```

### Periodic Reviews

**Weekly Scan**
- Any repeated instructions this week?
- Quick additions to WARP.md

**Sprint End**
- Review what changed
- Update WARP.md to reflect current state
- Remove outdated information

**Quarterly**
- Major cleanup
- Reorganize structure
- Remove deprecated sections
- Add emerging patterns

---

## Quick Reference

### Starting a Project
```bash
# Option 1: Warp UI
# Click "Create a New Project" in new tab

# Option 2: Manual
mkdir my-project && cd my-project
git init
# Tell agent: "Create a [type] project..."
# Then run: /init
```

### Essential WARP.md Sections
1. Project Overview
2. Tech Stack
3. Commands (dev, test, build, deploy)
4. Development Guidelines
5. Common Patterns
6. Testing Strategy
7. Deployment Process

### Maintenance Schedule
- **Daily**: Note repeated instructions
- **Weekly**: Quick WARP.md updates
- **Sprint end**: Comprehensive review
- **Quarterly**: Major cleanup and reorganization

### Feature Request Template
```
"Add [feature] to [location].
Include [requirements: error handling, validation, tests].
Verify it works by [verification method].
Fix any linting issues."
```

### What Makes WARP.md Effective
✅ Specific to your project (not generic)
✅ Exact commands to run
✅ Clear about what NOT to do
✅ Documents patterns that emerged
✅ Version controlled with code
✅ Updated regularly
✅ Concise (optimized for token usage)

❌ Generic best practices AI already knows
❌ Outdated information
❌ Verbose explanations
❌ Duplicate information
❌ Obvious conventions

---

## Next Steps

1. **Create your first WARP.md** using the template
2. **Start simple** with just tech stack and commands
3. **Document as you go** when patterns emerge
4. **Review regularly** and keep it current
5. **Iterate and improve** based on what works

Remember: The better your WARP.md, the more hands-free your coding becomes. Think of it as documentation that directly improves your AI coding partner.

---

*This guide will evolve. Treat it as a living document just like WARP.md itself.*
