
  # Global Preferences

  ## Git
  - `git clone` prefer git URLs over https URLs

  ## Others 
  - In web search tasks, when built in web_search falied, try web_fetch, websearch mcp, and playwright mcp，until it success.
  - Prefer UTF-8 encoding
  
  # Workflow Orchestration

  ## Plan Mode Orchestration
  - Non-trivial tasks (3+ steps or architecture decisions) must enter plan mode
  - If things go off track, stop and replan—don't push through
  - If bugs or frustration accumulate, stop and replan
  - Write detailed specs as input to reduce ambiguity
  - Use numbered steps

  ## Convert List to Subagents
  - Use subagents heavily to keep the main context window clean
  - Outsource research, exploration, and parallel analysis to subagents
  - Reduce cognitive load and separate concerns via subagents
  - One task per subagent, focused execution

  ## Self-Improvement Loop
  - After user correction: update `tasks/lessons.md` to record patterns
  - Write rules for yourself to prevent the same mistakes
  - Iterate improvements until error rate drops
  - Verify improvements each session, apply to relevant projects

  ## Verification Defaults On
  - Never mark a task complete until you've proven it works
  - Compare main branch to your changes when relevant
  - Always be ready to push to production, verify
  - Ask yourself "Would a senior engineer approve this?"
  - Do assertions, logs, test suite corrections

  ## Elegant Elegance - Balanced
  - For non-trivial changes: pause and ask "Is there a more elegant way?"
  - If a fix feels like a patch: "Now that I know everything, implement an elegant solution"
  - Skip this step for simple obvious fixes, don't over-engineer
  - Challenge your own work before committing

  ## Autonomous Bug Fixing
  - When you find a bug: fix it directly, don't ask for help
  - Point out logs, errors, failing tests, then resolve
  - User doesn't need to switch context
  - Proactively fix failing CI tests, no need to tell how

  ## Task Management
  1. Plan first: write plan to `tasks/todo.md` with checkboxes
  2. Validate plan: check before starting implementation
  3. Implement incrementally: check off each step as completed
  4. Explain changes: provide high-level summary for each step
  5. Document results: add review section in `tasks/todo.md`
  6. Record lessons: update `tasks/lessons.md` after corrections

  ## Core Principles
  - Simplicity first: each change should be as simple as possible, affecting minimal code
  - Don't be lazy: find root causes, no band-aid fixes, senior engineer standards
  - Minimal impact: changes should only involve what's necessary