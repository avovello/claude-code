# Feature Plugin

Systematic feature development with a 7-phase workflow inspired by Anthropic's feature-dev approach: discovery, codebase exploration, clarifying questions, architecture design, implementation, QA-DEV-REVIEW loops, and summary.

## Installation

```bash
/plugin install feature
```

## Commands

### `/feature-dev` (Recommended)

The new 7-phase guided workflow:

```bash
/feature-dev "Add real-time notifications with WebSockets"

# With E2E browser testing (for UI features)
/feature-dev "Add shopping cart UI" --e2e
```

### `/feature` (Legacy)

The original workflow for backward compatibility:

```bash
/feature "Add OAuth2 authentication"
```

## The 7-Phase Workflow

```
Phase 1: Discovery
    │   Clarify requirements, understand the problem
    ▼
Phase 2: Codebase Exploration
    │   Launch parallel code-explorer agents
    │   Map architecture, find patterns, trace flows
    ▼
Phase 3: Clarifying Questions  ◄── CRITICAL
    │   Present ALL ambiguities
    │   PAUSE until questions answered
    ▼
Phase 4: Architecture Design
    │   code-architect provides decisive blueprint
    │   PAUSE for user approval
    ▼
Phase 5: Implementation
    │   Build following approved architecture
    │   Follow codebase conventions
    ▼
Phase 6: Quality Review (QA-DEV-REVIEW Loop)
    │   ┌─────────────────────────────┐
    │   │ Testing Loop (max 3 iter)   │
    │   │ Test → Analyze → Fix → Loop │
    │   └─────────────────────────────┘
    │   ┌─────────────────────────────┐
    │   │ Review Loop (max 2 iter)    │
    │   │ Review → Fix → Loop         │
    │   └─────────────────────────────┘
    │   (Optional: E2E testing via QA plugin)
    ▼
Phase 7: Summary
        Document accomplishments, decisions, next steps
```

## Specialized Agents (3)

| Agent | Purpose | Key Features |
|-------|---------|--------------|
| **code-explorer** | Deep codebase analysis | Traces execution paths, maps architecture, documents patterns |
| **code-architect** | Architecture design | Generates decisive blueprints with rationale |
| **code-reviewer** | Precision code review | Confidence-based filtering (80+), actionable fixes |

## Skills

| Skill | Purpose |
|-------|---------|
| **testing-loop** | Automated test-fix-retest (max 3 iterations) |
| **review-loop** | Automated review-fix-rereview (max 2 iterations) |
| **clarifying-questions** | Structured ambiguity identification |

## Key Principles

1. **Understand Before Building**: Deep codebase exploration before design
2. **Ask Questions Early**: Resolve ALL ambiguities before implementation
3. **Parallel Exploration**: Launch multiple code-explorer agents for efficiency
4. **Decisive Architecture**: One recommended approach with clear rationale
5. **Confidence Filtering**: Only report issues with 80+ confidence score
6. **Automated Loops**: Test and review until quality gates pass

## QA-DEV-REVIEW Loop

The plugin preserves the testing and review loops:

### Testing Loop
```
Run Tests → Parse Results → Failures?
    │                          │
    │                    ┌─────┴─────┐
    │                   Yes          No
    │                    │            │
    │              Analyze Root     Done ✅
    │              Cause & Fix
    │                    │
    └────────────────────┘
         (max 3 iterations)
```

### Review Loop
```
Run Quality Checks → Launch Reviewers → Issues?
    │                                     │
    │                              ┌──────┴──────┐
    │                             Yes            No
    │                              │              │
    │                         Apply Fixes      Done ✅
    │                              │
    └──────────────────────────────┘
         (max 2 iterations)
```

## E2E Browser Testing

For UI-heavy features, use the `--e2e` flag to include browser testing via the **QA plugin**:

| QA Plugin Command | Purpose |
|-------------------|---------|
| `/e2e` | Run Playwright browser tests |
| `/write-tests --e2e` | Generate E2E test code |
| `browser-tester` agent | Interactive testing via Playwright MCP |

## Legacy Agents (Backward Compatibility)

The original 8 agents are preserved for the legacy `/feature` command:

1. **architecture-planner**: Architecture planning
2. **implementation-planner**: Implementation planning
3. **code-implementer**: Code writing
4. **test-writer**: Test creation
5. **test-runner**: Test execution
6. **test-failure-analyzer**: Failure analysis
7. **code-quality-reviewer**: Code review
8. **implementation-documenter**: Documentation

## Related Plugins

- **QA Plugin**: Standalone testing workflows (`/qa`, `/e2e`, `/unit`, `/integration`, `/write-tests`)

## Version

1.0.0

## Changelog

### v1.0.0
- Added `/feature-dev` command with 7-phase Anthropic-style workflow
- Added 3 new agents: code-explorer, code-architect, code-reviewer
- Added skills directory with testing-loop, review-loop, clarifying-questions
- Preserved QA-DEV-REVIEW loop for quality assurance
- Preserved E2E testing integration with QA plugin
- Legacy `/feature` command maintained for backward compatibility
