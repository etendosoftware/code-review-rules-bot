# Etendo Code Review Rules

This repository contains the **JSON rules** used by the Etendo Code Review Bot to decide when a Pull Request should be **blocking** (request changes) or **non-blocking** (suggestions only).

> ⚠️ **Disclaimer:** Before adding a new rule, always check if a similar rule already exists in the JSON.  

---

## File Structure

Main sections:

- **`blocking_issues`** → Problems that must be fixed before merging (runtime errors, security issues, data integrity, framework-breaking changes).
- **`non_blocking_issues`** → Suggestions for style, best practices, refactoring, or documentation.
- **`never_comment_on`** → Exceptions where the bot must not add comments (e.g. unchanged code, framework patterns).

---

## How to Add a New Rule

1. Open the JSON file.
2. Find the correct section and language (`java`, `sql`, `xml`, `javascript`, `python`).
3. Use **snake_case keys** in English.
4. Add the rule with at least:
   - `"rule"` → short description
   - `"cases"` → optional list of scenarios
   - `"required"` / `"example_wrong"` / `"example_correct"` → optional but recommended

---

## Templates

### Blocking Issue
```json
"<rule_key>": {
  "rule": "Clear explanation of the blocking issue",
  "required": "How it should be fixed",
  "example_wrong": "bad example",
  "example_correct": "good example"
}
```

### Non-Blocking Issue
```json
"best_practices": [
  "Example suggestion 1",
  "Example suggestion 2"
]
```

### Never Comment
```json
"<rule_key>": {
  "rule": "What not to comment on",
  "reason": "Why it should be ignored",
  "languages": ["java", "xml"]
}
```

## Decision Criteria

- **Blocking if**: causes runtime failure, security vulnerability, data corruption, or breaks Etendo framework.
- **Non-blocking if**: style, best practice, refactor, docs, or listed under never_comment_on.

## PR Checklist
- Rule added to the correct section.
- Uses snake_case key.
- JSON is valid.
- Does not duplicate existing rules.
- Matches decision criteria.

🚀 Keep rules short, consistent, and framework-focused.