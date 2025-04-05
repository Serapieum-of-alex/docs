# Git Branch Naming Convention (Based on Conventional Commits)

This document describes the branch naming convention used in this project, inspired by the
[Conventional Commits](https://www.conventionalcommits.org/) specification.
Following a consistent naming pattern improves clarity and makes collaboration smoother.

---

## Branch Naming Structure

### Recommended Pattern

Use the following structure for naming branches:

```
<type>/<short-description>
```

Or, if linking to an issue or ticket:

```
<type>/<issue-id>-<short-description>
```


---

### Examples

- `feat/user-login`
- `fix/typo-in-readme`
- `chore/update-dependencies`
- `docs/api-endpoint-docs`
- `refactor/auth-handler`
- `test/login-component`
- `feat/123-add-export-button`

---

### Allowed `<type>` Values

| Type       | Description                          |
|------------|--------------------------------------|
| `feat`     | A new feature                        |
| `fix`      | A bug fix                            |
| `docs`     | Documentation-only changes           |
| `style`    | Code style changes (no logic impact) |
| `refactor` | Code refactoring (no behavior change)|
| `perf`     | Performance improvement              |
| `test`     | Adding or updating tests             |
| `chore`    | Maintenance tasks (build, deps, etc) |

---

### Tips

- Use **kebab-case**: `my-new-feature`, not `my_new_feature` or `MyNewFeature`.
- Keep it short but descriptive.
- Include the issue or ticket number when possible for traceability.
- Avoid long or overly detailed branch names.

---

## Pull Request Naming Convention

Pull requests should follow the following naming convention.

```
<type>: <short, imperative summary>
```
This mimics a conventional commit, which makes changelogs, automation, and code reviews more consistent.

### Examples

- `feat: add user login functionality`
- `fix: correct typo in README`
- `docs: add API usage examples`
- `refactor: clean up auth handler logic`
- `test: add unit tests for login form`
- `chore: update project dependencies`

If your PR is linked to an issue or ticket, you can prefix or suffix with the ID:
- `feat: add export button (closes #123)`
- `fix: handle null values in parser [JIRA-456]`

### Tips
- Use an imperative voice, just like in commit messages: “add” instead of “added”.
- Keep it concise and focused on the goal of the PR.
- Use the same <type> keywords as in Conventional Commits.
- Link the PR to the related issue/ticket either in the title or body (or both!).


## Reference

- [Conventional Commits](https://www.conventionalcommits.org/)

---

By following this convention, we ensure that our Git history is more readable and maintainable. Happy branching! 🌱
