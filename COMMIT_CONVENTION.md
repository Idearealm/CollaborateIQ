# Commit Message Convention

This document defines the commit message convention for the CollaborateIQ project. Following these guidelines helps maintain clear communication and automated tooling for releases and changelogs.

## 📝 Commit Message Format

Each commit message consists of:
```
<type>(<scope>): <subject>

[optional body]

[optional footer]
```

### Types

- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting, missing semicolons, etc)
- `refactor`: Code refactoring
- `perf`: Performance improvements
- `test`: Adding or updating tests
- `chore`: Maintenance tasks, dependencies, build changes
- `ci`: CI/CD changes
- `revert`: Reverting changes

### Scopes

- `auth`: Authentication related changes
- `problem`: Problem feature related changes
- `solution`: Solution feature related changes
- `ui`: UI component changes
- `api`: API related changes
- `db`: Database related changes
- `test`: Testing framework changes
- `deps`: Dependency updates
- `config`: Configuration changes

## 📋 Examples

### Feature Addition
```
feat(problem): add problem categorization system

- Implemented automatic tagging system
- Added category selection in problem creation form
- Created API endpoints for category management

Closes #123
```

### Bug Fix
```
fix(auth): resolve login persistence issue

Fixed issue where user session wasn't properly maintained after
browser refresh.

Fixes #456
```

### Documentation Update
```
docs(readme): update installation steps

- Added prerequisites section
- Updated development setup instructions
- Added troubleshooting guide
```

### Breaking Change
```
feat(api)!: change problem submission endpoint response

BREAKING CHANGE: Problem submission endpoint now returns the full
problem object instead of just the ID.

Migration guide:
1. Update client-side handling
2. Adjust response parsing
```

## 🎯 Best Practices

1. **Subject Line**
   - Use imperative mood ("add" not "added" or "adds")
   - Max 50 characters
   - Don't end with a period
   - Capitalize first letter

2. **Body**
   - Wrap at 72 characters
   - Use to explain what and why, not how
   - Separate from subject with blank line

3. **Footer**
   - Reference issues and PRs
   - Mention breaking changes
   - List contributors

## 🤖 Commit Tools

### Git Template Setup

1. Create commit template:
```bash
git config --global commit.template ~/.gitmessage
```

2. Add this template to `~/.gitmessage`:
```
<type>(<scope>): <subject>

# Why is this change needed?
# →

# How does it address the issue?
# →

# What side effects does this change have?
# →

# Include a link to the ticket, if any.
# Fixes #
```

### Commitizen Setup

1. Install Commitizen:
```bash
npm install -g commitizen
npm install --save-dev @commitlint/config-conventional
```

2. Initialize in project:
```bash
commitizen init cz-conventional-changelog
```

3. Use by running:
```bash
git cz
```

## 🔍 Commit Verification

We use commitlint to enforce these conventions:

```bash
npm install --save-dev @commitlint/cli @commitlint/config-conventional
```

Add to `package.json`:
```json
{
  "scripts": {
    "commitmsg": "commitlint -E HUSKY_GIT_PARAMS"
  }
}
```

## 📦 Automatic Changelog Generation

Using conventional commits enables automatic changelog generation:

```bash
npm install --save-dev standard-version
```

Add to `package.json`:
```json
{
  "scripts": {
    "release": "standard-version"
  }
}
```

## ⚠️ Common Mistakes to Avoid

1. ❌ Mixing multiple changes in one commit
2. ❌ Writing vague commit messages
3. ❌ Forgetting to reference related issues
4. ❌ Not indicating breaking changes
5. ❌ Using past tense in subject line

## ✅ Quick Reference

```
feat: ✨ New feature
fix: 🐛 Bug fix
docs: 📚 Documentation
style: 💎 Code style
refactor: ♻️ Code refactoring
perf: ⚡️ Performance
test: ✅ Testing
chore: 🔧 Maintenance
ci: 👷 CI/CD
revert: ⏪️ Revert changes
```

---

Remember: Good commit messages serve three important purposes:
- Speed up the reviewing process
- Help write good release notes
- Help future maintainers understand why changes were made

