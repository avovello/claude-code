# Bugfix Plugin 🐛

Systematic bug fixing with reproduction, root cause analysis, and comprehensive regression testing.

## Installation
```bash
/plugin install bugfix
```

## Usage
```bash
/bugfix "Users can't upload files larger than 5MB"
```

## Specialized Agents (7)
1. **bug-reproducer**: Reproduces bugs, creates failing tests
2. **root-cause-analyst**: Identifies root causes
3. **impact-assessor**: Assesses severity and impact
4. **fix-planner**: Plans fix approach
5. **fix-implementer**: Implements fixes
6. **fix-tester**: Tests fixes
7. **regression-tester**: Runs regression tests

## Processing Loop
Fix → Test → (if fail) → Re-analyze → Re-fix → Re-test (max 3 iterations)

## Workflow
Reproduce → Analyze → Plan → Fix Loop → Regression Test

## Version
1.0.0
