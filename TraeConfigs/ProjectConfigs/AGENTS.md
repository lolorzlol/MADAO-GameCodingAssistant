# AGENTS.md

## Development Workflow

### Operation Requirements

- Check both `message` and `success` from MCP call results to determine success. When `message` doesn't match expectations, treat the call as failed.
- When MCP calls fail, adjust parameters based on the returned `message` and retry.
- Follow `Test-Driven Development (TDD)` during development.
- Check the Unity Editor `Console` window regularly for errors during development.

- Load the `unity-mcp-helper` skill before using unityMCP to understand available editor operations.
- Use git for version control.

### Plan Mode Orchestration

- Non-trivial tasks (3+ steps or architecture decisions) must enter plan mode.
- If things go off track, stop and replan—don't push through.
- If bugs or frustration accumulate, stop and replan.
- Write detailed specs as input to reduce ambiguity.
- Use numbered steps.

### Task Management

1. Plan first: write plan to `tasks/todo.md` with checkboxes.
2. Validate plan: check before starting implementation.
3. Implement incrementally: check off each step as completed.
4. Explain changes: provide high-level summary for each step.
5. Document results: add review section in `tasks/todo.md`.
6. Record lessons: update `tasks/lessons.md` after corrections.

### Subagent Strategy

- Use subagents heavily to keep the main context window clean.
- Outsource research, exploration, and parallel analysis to subagents.
- Reduce cognitive load and separate concerns via subagents.
- One task per subagent, focused execution.

### Code Quality Principles

**Self-Improvement Loop:**

- After user correction: update `tasks/lessons.md` to record patterns.
- Write rules for yourself to prevent the same mistakes.
- Iterate improvements until error rate drops.
- Verify improvements each session, apply to relevant projects.

**Verification Defaults:**

- Never mark a task complete until you've proven it works.
- Compare main branch to your changes when relevant.
- Always be ready to push to production, verify.
- Ask yourself "Would a senior engineer approve this?"
- Do assertions, logs, test suite corrections.

**Elegant Code:**

- For non-trivial changes: pause and ask "Is there a more elegant way?"
- If a fix feels like a patch: "Now that I know everything, implement an elegant solution."
- Skip this step for simple obvious fixes, don't over-engineer.
- Challenge your own work before committing.

**Core Principles:**

- Simplicity first: each change should be as simple as possible, affecting minimal code.
- Don't be lazy: find root causes, no band-aid fixes, senior engineer standards.
- Minimal impact: changes should only involve what's necessary.

**Autonomous Bug Fixing:**

- When you find a bug: fix it directly, don't ask for help.
- Point out logs, errors, failing tests, then resolve.
- User doesn't need to switch context.
- Proactively fix failing CI tests, no need to tell how.

## Testing Instructions

### Test-Driven Development (TDD)

- Follow the *Red-Green-Refactor* cycle: write failing tests first, then implement code, and run the tests again to make them pass.
- Run tests through the Unity Editor TestRunner.
- After tests pass, refactor code through code-review.
- Use *unityMCP* to launch tests via TestRunner in the editor.

### In-Editor Game Testing

Basic workflow:

1. Enter Play mode to start the game.
2. Simulate input.
3. Screenshot the Game window.
4. Analyze the screenshot visually and fix any issues found.

## Skills Reference

Load the appropriate skill before starting each workflow:

| Workflow | Skill |
|----------|-------|
| Using unityMCP | `unity-mcp-helper` |
| Using unity-test-framework | `unity-test-framework` |
| Test-Driven Development | `test-driven-development` |

## Preferences

### Input System

- Use the legacy input system.

### Git

- Do not use `git worktree`.
- Commit changes promptly.

## Scene Setup

- Design the size and materials of different objects carefully.
- **Automated Configuration with Editor Scripts**: When needing to set up complex references, create editor scripts (in `Assets/Scripts/Editor/` folder) to automate the configuration process. This includes both:
  - **Scene object references**: Use `GameObject.Find()` to locate objects in the scene
  - **Prefab references**: Use `AssetDatabase.LoadAssetAtPath<T>()` to load prefabs and assets from disk
  - Then assign them directly to component fields programmatically. Add a menu item with `[MenuItem]` attribute to trigger the setup process.

## Troubleshooting

### Common Issues

- When using unit-test-framework, forgetting to call the `unity-test-framework` skill causes compilation errors.

### Debugging Steps

- First check the Console window for compilation errors.
- Check for any other issues as needed.