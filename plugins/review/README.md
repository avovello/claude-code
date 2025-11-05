# Review Plugin 👁️

Multi-perspective code review with 19 specialized reviewers covering architecture, security, performance, backend, frontend, and DevOps.

## Overview

The Review plugin provides comprehensive code review through 19 specialized reviewers that examine code from different perspectives. Each reviewer has precise, non-overlapping responsibilities.

## Installation

```bash
/plugin install review
```

## Usage

```bash
# Review current changes
/review

# Review specific files
/review src/auth/*.php

# Review PR
/review --pr=123
```

## Specialized Reviewers (19)

### Architecture (1)
- **architect-reviewer**: System architecture, service boundaries, Clean Architecture

### Security (3)
- **security-authentication-reviewer**: Auth, OAuth, JWT, session management
- **security-input-reviewer**: SQL injection, XSS, command injection, input validation
- **security-crypto-reviewer**: Encryption, hashing, secrets management

### Performance (3)
- **performance-algorithm-reviewer**: Algorithm complexity, loops, recursion
- **performance-database-reviewer**: N+1 queries, indexes, query optimization
- **performance-resource-reviewer**: Memory leaks, connection pooling, resource cleanup

### Backend (5)
- **backend-php-reviewer**: PHP, PSR, Laravel, SOLID/KISS/DRY
- **backend-python-reviewer**: Python, PEP, Django, SOLID/KISS/DRY
- **backend-nodejs-reviewer**: Node.js, async/await, TypeScript, SOLID/KISS/DRY
- **backend-go-reviewer**: Go idioms, error handling, SOLID/KISS/DRY
- **backend-bash-reviewer**: Shellcheck, POSIX, quoting, SOLID/KISS/DRY

### Frontend (4)
- **frontend-react-reviewer**: React hooks, components, SOLID/KISS/DRY
- **frontend-vue-reviewer**: Vue Composition API, reactivity, SOLID/KISS/DRY
- **frontend-html-reviewer**: Semantic HTML, accessibility, ARIA
- **frontend-css-reviewer**: BEM, specificity, responsive design

### DevOps (3)
- **devops-docker-reviewer**: Dockerfile, multi-stage builds, security
- **devops-kubernetes-reviewer**: K8s manifests, Helm, resources
- **devops-cicd-reviewer**: GitHub Actions, GitLab CI, pipelines

## Workflow

1. **Analyze Files**: Determine which reviewers are needed
2. **Launch Reviewers**: Run 2-19 reviewers in parallel (based on file types)
3. **Consolidate**: Merge results, remove duplicates
4. **Quality Gates**: Check critical (0), high (≤2), medium (≤10)
5. **Fix Loop**: Up to 2 iterations to address issues
6. **Report**: Generate comprehensive review report

## Quality Gates

- **Critical issues**: 0 allowed → BLOCKED
- **High issues**: ≤ 2 allowed → NEEDS WORK
- **Medium issues**: ≤ 10 allowed → APPROVED

## Output

```
review-reports/review-[timestamp].md
```

Contains:
- Summary statistics
- Issues by severity
- Review by category
- Recommendations
- Approval status

## Responsibility Separation

### Architect Reviewer
- ✅ System architecture, service boundaries, dependency flow
- ❌ NOT code-level SOLID (that's language reviewers)

### Security Reviewers
- ✅ Vulnerabilities in their domain (auth, input, crypto)
- ❌ NOT overlapping (each has specific focus)

### Language Reviewers
- ✅ SOLID/KISS/DRY at implementation level
- ❌ NOT system architecture (that's architect)
- ❌ NOT security (that's security reviewers)

## Examples

### Example 1: PHP Backend Change

**Files changed**: `src/UserController.php`, `src/UserService.php`

**Reviewers launched**:
- architect-reviewer (always)
- security-input-reviewer (handles user input)
- backend-php-reviewer (PHP files)

### Example 2: React Frontend Change

**Files changed**: `src/components/UserProfile.jsx`

**Reviewers launched**:
- architect-reviewer (always)
- security-input-reviewer (renders user data)
- frontend-react-reviewer (React files)

### Example 3: Full Stack Change

**Files changed**: PHP backend, React frontend, Dockerfile

**Reviewers launched**: (9 reviewers)
- architect-reviewer
- security-input-reviewer
- backend-php-reviewer
- frontend-react-reviewer
- devops-docker-reviewer
- performance-algorithm-reviewer
- performance-database-reviewer
- frontend-html-reviewer
- frontend-css-reviewer

## Version

1.0.0

## Notes

- Minimum 2 reviewers always run (architect + security-input)
- Maximum 19 reviewers if all file types present
- Average 5-8 reviewers for typical changes
- All reviewers run in parallel
- Review takes 2-5 minutes
