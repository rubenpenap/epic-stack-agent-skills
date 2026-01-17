# Epic Stack Agent Skills

A collection of skills for AI agents working with [Epic Stack](https://www.epicweb.dev/epic-stack). These skills provide packaged instructions and scripts that extend agent capabilities to work efficiently with all aspects of the stack.

The skills follow the [Agent Skills](https://github.com/vercel-labs/agent-skills) format but are 100% adapted for Epic Stack. Additional patterns and best practices from vercel-labs/agent-skills have been integrated and adapted for Epic Stack's React Router, Radix UI, and Tailwind CSS stack.

## Available Skills

### epic-routing

Guide on routing with React Router and react-router-auto-routes.

**Use when:**
- Create new routes or pages
- Implement nested layouts
- Configure resource routes
- Work with route parameters and search params

**Categories covered:**
- File-based routing conventions
- Route groups and layouts
- Loaders and Actions patterns
- Code co-location

### epic-forms

Guide on forms with Conform and validation with Zod.

**Use when:**
- Create new forms
- Implement form validation
- Handle file uploads
- Work with progressive enhancement

**Categories covered:**
- Conform patterns
- Zod validation
- Error handling
- Honeypot fields

### epic-auth

Guide on authentication, sessions, and user security.

**Use when:**
- Implement authentication
- Work with sessions
- Configure OAuth providers
- Implement 2FA or passkeys

**Categories covered:**
- Cookie-based sessions
- Email/password auth
- OAuth providers
- WebAuthn passkeys
- TOTP 2FA

### epic-permissions

Guide on RBAC system and permissions.

**Use when:**
- Implement access control
- Create new permissions or roles
- Validate permissions on server/client

**Categories covered:**
- RBAC patterns
- Permission model
- Role management
- Access control utilities

### epic-caching

Guide on caching with cachified.

**Use when:**
- Optimize expensive queries
- Implement cache for external APIs
- Configure TTL and stale-while-revalidate

**Categories covered:**
- SQLite cache (long-lived)
- LRU cache (short-lived)
- Cache invalidation
- Server timing integration

### epic-testing

Guide on testing with Vitest and Playwright.

**Use when:**
- Write unit tests
- Create E2E tests
- Test forms and routes
- Mock external services

**Categories covered:**
- Vitest patterns
- Playwright E2E tests
- Testing Library
- MSW mocking

### epic-security

Guide on security practices.

**Use when:**
- Implement CSP
- Configure CSRF protection
- Add rate limiting
- Manage secrets

**Categories covered:**
- Content Security Policy
- CSRF protection
- Rate limiting
- Session security
- Input validation

### epic-database

Guide on Prisma, SQLite, and LiteFS.

**Use when:**
- Design database schema
- Create migrations
- Optimize queries
- Work with LiteFS

**Categories covered:**
- Prisma patterns
- SQLite with LiteFS
- Migrations
- Query optimization

### epic-deployment

Guide on deployment with Fly.io.

**Use when:**
- Configure deployment
- Setup multi-region
- Configure CI/CD
- Manage secrets in production

**Categories covered:**
- Fly.io configuration
- LiteFS setup
- GitHub Actions CI/CD
- Preview deployments (inspired by Vercel deploy claimable)
- Environment detection
- Build artifact optimization
- Multi-region deployment
- Zero-downtime deploys
- Rollback strategies
- Secrets management

### epic-react-best-practices

Guide on React best practices for Epic Stack applications.

**Use when:**
- Write efficient React components
- Optimize performance and bundle size
- Follow React Router best practices
- Avoid common React anti-patterns

**Categories covered:**
- Data fetching with loaders (avoiding useEffect)
- Preventing data fetching waterfalls
- Code splitting and bundle optimization
- Optimizing re-renders and memoization
- SSR performance optimization
- TypeScript best practices
- React 18+ features (transitions, concurrent rendering)

### epic-ui-guidelines

Guide on UI/UX guidelines and accessibility for Epic Stack.

**Use when:**
- Create accessible UI components
- Follow Epic Stack design patterns
- Use Tailwind CSS effectively
- Ensure proper form accessibility

**Categories covered:**
- Semantic HTML and ARIA attributes
- Radix UI component usage
- Tailwind CSS utility-first styling
- Keyboard navigation patterns
- Screen reader best practices
- Focus management for React Router
- Color contrast and readability
- Responsive design principles
- Dark mode accessibility
- Touch target sizes
- Progressive enhancement

## Installation

Install Epic Stack skills using the `add-skill` CLI tool:

```bash
# Install all skills from the latest version
npx add-skill rubenpenap/epic-stack-agent-skills

# Install a specific version
npx add-skill rubenpenap/epic-stack-agent-skills@v1.0.0

# Install specific skills only
npx add-skill rubenpenap/epic-stack-agent-skills --skill epic-routing --skill epic-auth

# Install globally (available across all projects)
npx add-skill rubenpenap/epic-stack-agent-skills --global
```

## Usage

Skills are automatically activated when an AI agent detects relevant tasks related to Epic Stack. Once installed via `npx add-skill`, the agent will automatically use these skills when working on Epic Stack projects.

**Example prompts that will trigger skills:**

```
Create a new route to display users
```
→ Activates `epic-routing` skill

```
Implement authentication with GitHub OAuth
```
→ Activates `epic-auth` skill

```
Add caching to this expensive database query
```
→ Activates `epic-caching` skill

```
Write E2E tests for the login form
```
→ Activates `epic-testing` skill

```
Configure rate limiting for the API
```
→ Activates `epic-security` skill

### Skill Activation

Each skill is automatically detected by AI agents when:
- The task description matches the skill's purpose
- The codebase contains Epic Stack patterns (React Router, Prisma, etc.)
- You reference Epic Stack concepts in your prompts

### Manual Skill Reference

You can also explicitly reference a skill in your prompts:

```
Using the epic-forms skill, create a signup form with validation
```

```
Follow the epic-ui-guidelines skill to make this component accessible
```

## Skill Structure

Each skill contains:

* `SKILL.md` - Instructions for the agent (with YAML frontmatter metadata)
* Optional supporting files or references

**SKILL.md format:**

Each `SKILL.md` file includes:
- **YAML Frontmatter**: Metadata (name, description, categories)
- **When to use**: Clear guidance on when the skill should be activated
- **Patterns and conventions**: Detailed patterns specific to Epic Stack
- **Common examples**: Real-world code examples
- **Common mistakes**: What to avoid
- **References**: Links to relevant documentation

## Versioning

This repository uses semantic versioning with Git tags:

- `v1.0.0` - Initial release
- `v1.1.0` - Added new skills or enhancements
- `v1.0.1` - Bug fixes and improvements

When installing, you can specify a version:

```bash
npx add-skill rubenpenap/epic-stack-agent-skills@v1.0.0
```

## Contributing

Contributions are welcome! To add or improve skills:

1. Create or update the `SKILL.md` file in the appropriate `skills/epic-*/` directory
2. Ensure each `SKILL.md` includes YAML frontmatter:
   ```yaml
   ---
   name: epic-your-skill-name
   description: Brief description of the skill
   categories:
     - category1
     - category2
   ---
   ```
3. Follow the existing skill structure:
   - When to use this skill
   - Patterns and conventions
   - Common examples
   - Common mistakes
   - References
4. Test that `add-skill` can install your skill correctly
5. Submit a pull request

## Releasing a New Version

To create a new release:

1. Update version in `package.json` (if publishing to npm)
2. Create a Git tag:
   ```bash
   git tag v1.0.0
   git push origin v1.0.0
   ```
3. Users can then install the specific version:
   ```bash
   npx add-skill rubenpenap/epic-stack-agent-skills@v1.0.0
   ```

## License

MIT

## Features from Vercel Labs Agent Skills

This project integrates and adapts best practices from [vercel-labs/agent-skills](https://github.com/vercel-labs/agent-skills):

- **React Best Practices**: Performance optimization patterns, waterfall prevention, SSR optimization, and bundle size strategies
- **Web Design Guidelines**: Enhanced accessibility patterns, keyboard navigation, screen reader support, and responsive design
- **Deployment Automation**: Preview deployment workflows adapted for Fly.io, environment detection, and build optimization

All patterns have been adapted to work with Epic Stack's technology choices (React Router, Prisma, SQLite, LiteFS, Fly.io, Radix UI, Tailwind CSS).

## About

These skills are specifically designed to work with [Epic Stack](https://www.epicweb.dev/epic-stack), an opinionated web development stack based on the experience of [Kent C. Dodds](https://kentcdodds.com) and the community. The skills integrate best practices from vercel-labs/agent-skills adapted for Epic Stack's unique architecture and conventions.
