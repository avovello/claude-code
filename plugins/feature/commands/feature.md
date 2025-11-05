# Feature Development Command

**Purpose**: Complete feature development lifecycle with planning, implementation, testing loops, review loops, and documentation

## Workflow

1. **Architecture Planning**: Plan architecture changes
2. **Implementation Planning**: Plan implementation steps
3. **Code Implementation**: Write production code
4. **Test Writing**: Write tests
5. **Testing Loop**: Test → (if fail) → Analyze → Fix → Re-test (max 3 iterations)
6. **Code Quality Review**: Review code quality
7. **Review Loop**: Review → (if changes requested) → Apply feedback → Re-review (max 2 iterations)
8. **Documentation**: Create/update documentation

## Specialized Agents (8)
- architecture-planner: Plans architecture changes
- implementation-planner: Plans implementation steps
- code-implementer: Writes code
- test-writer: Writes tests
- test-runner: Runs tests
- test-failure-analyzer: Analyzes test failures
- code-quality-reviewer: Reviews code
- implementation-documenter: Documents implementation

## Usage
```bash
/feature "Add user authentication with OAuth2"
```

## Processing Loops
- **Testing Loop**: Repeats until tests pass (max 3 times)
- **Review Loop**: Repeats until approved (max 2 times)

## Version
1.0.0
