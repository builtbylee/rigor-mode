# Project Context Template

Copy this file to your project root as `.agent/context.md` and fill in the details.

---

# Project: [Name]

## Overview
[1-2 sentence description of what this project does]

## Stack
- **Language**: [TypeScript/Python/Go/etc.]
- **Framework**: [Next.js/Django/etc.]
- **Database**: [PostgreSQL/MongoDB/etc.]
- **Deployment**: [Vercel/AWS/etc.]

## Key Directories
| Path | Purpose |
|------|---------|
| `src/` | [Main source code] |
| `src/api/` | [API routes] |
| `src/components/` | [UI components] |
| `tests/` | [Test files] |

## Commands
| Command | Purpose |
|---------|---------|
| `npm run dev` | Start dev server |
| `npm run build` | Production build |
| `npm test` | Run tests |
| `npm run lint` | Run linter |

## Conventions

### Naming
- Files: [kebab-case / PascalCase / etc.]
- Components: [PascalCase]
- Functions: [camelCase]
- Constants: [SCREAMING_SNAKE_CASE]

### Code Style
- [Indentation: 2 spaces / tabs]
- [Quotes: single / double]
- [Semicolons: yes / no]

### Patterns
- [State management approach]
- [Error handling approach]
- [API response format]

## Critical Paths
Areas requiring extra care:
- **Auth**: `[path]` - [notes]
- **Payments**: `[path]` - [notes]
- **Data**: `[path]` - [notes]

## Environment Variables
| Variable | Purpose | Required |
|----------|---------|----------|
| `DATABASE_URL` | Database connection | Yes |
| `API_KEY` | External API | Yes |

## Known Issues / Tech Debt
- [ ] [Issue 1]
- [ ] [Issue 2]

## Recent Architectural Decisions
| Decision | Date | Rationale |
|----------|------|-----------|
| [Decision] | [Date] | [Why] |

## Team Conventions
- [PR review requirements]
- [Branch naming]
- [Commit message format]

## External Dependencies
| Service | Purpose | Docs |
|---------|---------|------|
| [Service] | [What it does] | [Link] |

## Notes for AI Agents
- [Any specific instructions]
- [Things to avoid]
- [Preferred approaches]
