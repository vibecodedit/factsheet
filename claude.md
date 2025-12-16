## Working Style & Principles

### Communication
- Be direct and candid. If there's a better approach, say so with reasoning.  
- Think from first principles. Challenge assumptions including mine.  
- Goal: Find the objectively best solution, not the most agreeable one.  
- High-level explanations only unless I ask for details.  

### Code Philosophy  
- Simplicity above all else. Every change should impact minimal code.  
- No temporary fixes or workarounds. Find and fix root causes.  
- Avoid complexity. If a change feels large or invasive, break it down further.  
- Goal: Zero bugs introduced, maximum clarity.  

### UI/UX Protection
- Never remove, hide, or rename existing features or UI elements unless explicitly requested.  
- If functionality isn't ready, stub it with annotations rather than deleting it.  
- Keep the user-facing surface intact while working on internals.  

---
## Multi-Agent Coordination

### BEFORE starting any work:
1. Check `task-registry.md` in project root - read the Active Tasks section  
2. List all files you plan to modify  
3. If any of your files match files in Active Tasks: STOP and tell me there's a conflict  
4. If no conflict: Add yourself to Active Tasks using format: [Agent-MMDD-HHMM] Your task | Files: file1, file2 | Started: timestamp  

### DURING work:
- If you discover you need to modify additional files, check registry again and update your entry  

### AFTER completing work:
- Move your entry from Active Tasks to Completed Today  
- Tell me: "Task complete and registry updated. Ready to merge."  

### If I say "Planning mode: [feature]":
- Ask me clarifying questions about the feature  
- Analyze the codebase yourself  
- Break the feature into 3-7 small tasks (each = 30-60 min, touches 1-3 files)  
- Number the tasks and store them in your context  
- For each task tell me: description, files, and dependencies  
- Ask: "Which task number should I execute?"  

### If I say "Execute task [number]":
- Look up that task from the plan you created  
- Follow the coordination protocol above  
- Do the work  

### Conflict resolution:
- If conflict detected, tell me which files conflict and wait for my decision.  

---
## Standard Workflow

### Planning Phase
1. Read relevant codebase files  
2. Write plan to `task-registry.md` as checklist of todo items  
3. Present plan and wait for my approval before starting  

### Execution Phase
1. Work through todos, checking them off as completed  
2. Give brief high-level explanation after each step  
3. If you discover issues mid-task, stop and propose adjusted approach  

### Completion Phase
1. Add review section to `task-registry.md` summarizing:  
   - What changed  
   - Files modified  
   - Any gotchas or considerations for future work  
2. Mark task complete in registry  
---
