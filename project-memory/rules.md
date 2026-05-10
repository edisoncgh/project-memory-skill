# Memory Management Rules

## File Size Limits
- Each `sessions/*.md` file: **≤ 150 lines**
- `knowledge.md`: **≤ 300 lines**
- `context.md`: **≤ 100 lines** (keep it a working snapshot, not a dump)
- `index.md`: no hard limit, but keep entries to one line each

## Pruning (when session count > 20)
1. Read the 5 oldest session files
2. Extract any lasting knowledge → append to `knowledge.md`
3. Delete those 5 session files
4. Remove their entries from `index.md`
5. Add a note in `index.md`: `<!-- Archived sessions before YYYY-MM-DD into knowledge.md -->`

## Merging
- If two sessions cover the same topic on the same day, merge into one file
- Keep the later timestamp as the filename

## What to Store vs. Skip

### STORE
- User requirements and constraints
- Files read or modified, and why
- Technical decisions with rationale
- Unresolved items and next steps
- User preferences discovered during conversation
- User's "try this" suggestions that worked
- Environment issues and fixes (OS quirks, dependency conflicts)
- Error patterns and their resolutions

### SKIP
- Verbatim code (just reference file paths)
- Trivial exchanges ("hello", "thanks")
- Intermediate tool output that is already reflected in the outcome
- Successful tool outputs already reflected in file changes
- Repetitive "looks good" exchanges
- Full file diffs (reference the commit or file path instead)

## Vibe Coding Specific Rules

### Context Refresh Cadence
- Update `context.md` every 3-5 turns during active development
- Always update `context.md` when switching to a different file or feature
- On user "break"/"pause"/"later": write a detailed context snapshot immediately

### Context.md Must Contain
- **Active files**: list of files currently being edited (with line ranges if focused)
- **Last working state**: key functions/classes/interfaces in flux (names + brief description, not full code)
- **Pending decisions**: open questions the user hasn't resolved yet
- **Next steps**: what was about to happen next
- **Blockers**: anything preventing progress (compilation errors, failing tests, missing info)

### Error Tracking During Vibe Coding
When errors occur during iterative development:
- Record: error message, file:line, what was attempted, what fixed it
- If fix was user-suggested, note that explicitly (builds preference profile)
- If fix involved a workaround, note the proper solution for future reference

## Boundary Conditions

### When NOT to Create a Session File
- Conversation is purely exploratory (no code changes, no decisions)
- User is just asking a question (unless it reveals a new preference)
- Only reading files with no action taken

### When to Update knowledge.md
- A new convention or pattern is established
- A significant architectural decision is made
- User expresses a preference not previously recorded
- A toolchain or dependency version changes
- A recurring workaround is adopted as standard practice

### When to Skip Memory Entirely
- Single-turn trivial tasks ("what does this function do?")
- Tasks fully captured by git history (no additional context needed)
- Conversations where user explicitly says "don't record this"

## Conflict Handling
- If `.memory/index.md` is missing but `sessions/` exists, rebuild the index by scanning session files
- If a session filename already exists (same second), append `-2` before `.md`
- If `context.md` and actual code state diverge, trust the code and update `context.md`
- If two sessions contradict each other, trust the later session and flag the conflict in `knowledge.md`

## Privacy
- Never store API keys, passwords, or secrets in memory files
- If user shares sensitive info, reference it as "credentials provided" without values
- Do not store full URLs that contain tokens or session IDs
