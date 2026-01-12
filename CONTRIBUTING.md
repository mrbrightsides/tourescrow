# 🤝 Contributing to TourEscrow

**Thank you for your interest in contributing to TourEscrow, part of the STC Ultimate smart tourism platform!**

We welcome contributions from the community — whether it's bug fixes, new features, documentation improvements, or feedback. This guide will help you get started.

---

## 📋 **Table of Contents**

1. [Code of Conduct](#code-of-conduct)
2. [How Can I Contribute?](#how-can-i-contribute)
3. [Development Workflow](#development-workflow)
4. [Coding Standards](#coding-standards)
5. [Commit Message Guidelines](#commit-message-guidelines)
6. [Pull Request Process](#pull-request-process)
7. [Issue Reporting](#issue-reporting)
8. [Community](#community)

---

## 📜 **Code of Conduct**

### Our Pledge

We are committed to providing a welcoming and inclusive environment for all contributors. By participating in this project, you agree to:

- ✅ Be respectful and considerate in all interactions
- ✅ Accept constructive criticism gracefully
- ✅ Focus on what's best for the community
- ✅ Show empathy towards other contributors

### Unacceptable Behavior

- ❌ Harassment, discrimination, or offensive comments
- ❌ Trolling, insulting, or personal attacks
- ❌ Publishing others' private information without consent
- ❌ Any conduct that could be considered inappropriate in a professional setting

**Violations**: If you witness or experience unacceptable behavior, please report it to [support@elpeef.com].

---

## 💡 **How Can I Contribute?**

### 1. **Report Bugs** 🐛

Found a bug? Help us improve by reporting it!

- Search [existing issues](https://github.com/mrbrightsides/tourescrow/issues) first to avoid duplicates
- If it's new, [open an issue](https://github.com/mrbrightsides/tourescrow/issues/new) with:
  - Clear description of the problem
  - Steps to reproduce
  - Expected vs actual behavior
  - Environment details (OS, browser, Node version)
  - Screenshots/console logs (if applicable)

### 2. **Suggest Features** 💡

Have an idea to improve TourEscrow?

- Check [existing feature requests](https://github.com/mrbrightsides/tourescrow/issues?q=is%3Aissue+is%3Aopen+label%3Aenhancement)
- Open a new issue with:
  - Use case description
  - Why it's valuable
  - Proposed implementation (optional)
  - Mockups/diagrams (optional)

### 3. **Improve Documentation** 📚

Documentation is just as important as code!

- Fix typos or unclear instructions
- Add examples or tutorials
- Translate documentation to other languages
- Update setup guides or API references

### 4. **Submit Code** 💻

Ready to contribute code? Great! See [Development Workflow](#development-workflow) below.

---

## 🛠️ **Development Workflow**

### Step 1: Fork & Clone

```bash
# Fork the repository on GitHub
# Then clone your fork
git clone https://github.com/mrbrightsides/tourescrow.git
cd stc-ultimate

# Add upstream remote
git remote add upstream https://github.com/ORIGINAL_OWNER/tourescrow.git
```

### Step 2: Create a Branch

```bash
# Create a feature branch from main
git checkout -b feature/your-feature-name

# Or for bug fixes:
git checkout -b fix/your-bug-fix-name
```

**Branch naming conventions:**
- `feature/` — New features (e.g., `feature/multi-currency-support`)
- `fix/` — Bug fixes (e.g., `fix/escrow-release-error`)
- `docs/` — Documentation updates (e.g., `docs/setup-guide`)
- `refactor/` — Code refactoring (e.g., `refactor/revenue-split-logic`)
- `test/` — Test additions/improvements (e.g., `test/escrow-manager`)

### Step 3: Set Up Development Environment

```bash
# Install dependencies
pnpm install

# Copy environment variables
cp .env.example .env.local

# Configure your .env.local (see SETUP.md)
```

### Step 4: Make Changes

- Write clean, readable code
- Follow [Coding Standards](#coding-standards)
- Add tests for new features
- Update documentation if needed

### Step 5: Test Locally

```bash
# Run development server
pnpm dev

# Type checking
pnpm type-check

# Linting
pnpm lint

# Build production version
pnpm build
```

**Manual Testing Checklist:**
- [ ] Feature works as expected
- [ ] No console errors or warnings
- [ ] Responsive on mobile/desktop
- [ ] Wallet connection still works
- [ ] Smart contract interactions succeed
- [ ] No broken links or missing assets

### Step 6: Commit Changes

```bash
# Stage your changes
git add .

# Commit with descriptive message (see guidelines below)
git commit -m "feat: add multi-currency swap support"
```

### Step 7: Push & Create Pull Request

```bash
# Push to your fork
git push origin feature/your-feature-name
```

Then:
1. Go to your fork on GitHub
2. Click "Compare & pull request"
3. Fill out the PR template (see below)
4. Submit!

---

## 🎨 **Coding Standards**

### TypeScript Guidelines

✅ **Do:**
- Use explicit types for all variables, parameters, and return values
- Define interfaces at the top of files
- Use `type` imports: `import type { Foo } from 'bar'`
- Handle errors with try/catch blocks
- Use functional components with TypeScript types

❌ **Don't:**
- Use `any` type (unless absolutely necessary with documentation)
- Use implicit types
- Access object properties without proper typing
- Skip error handling in async functions

**Example:**

```typescript
// ✅ Good
interface BookingParams {
  serviceName: string;
  amount: bigint;
  operatorAddress: Address;
}

export function createBooking(params: BookingParams): Promise<string> {
  // implementation
}

// ❌ Bad
export function createBooking(params: any) {
  // missing types
}
```

### React Best Practices

✅ **Do:**
- Use functional components with hooks
- Add `'use client'` directive for client components
- Use `useEffect` cleanup functions
- Memoize expensive calculations with `useMemo`
- Handle loading and error states

❌ **Don't:**
- Use class components
- Forget to cleanup subscriptions/timers
- Mutate state directly
- Create infinite render loops

**Example:**

```tsx
// ✅ Good
'use client';

import { useState, useEffect } from 'react';
import type { Address } from 'viem';

interface WalletBadgeProps {
  address: Address;
}

export function WalletBadge({ address }: WalletBadgeProps): JSX.Element {
  const [balance, setBalance] = useState<bigint | null>(null);

  useEffect(() => {
    let cancelled = false;

    async function fetchBalance() {
      const result = await getBalance(address);
      if (!cancelled) setBalance(result);
    }

    fetchBalance();

    return () => {
      cancelled = true;
    };
  }, [address]);

  return <div>{balance?.toString()}</div>;
}
```

### Styling Guidelines

- Use **Tailwind CSS** utility classes for styling
- Keep components responsive with Tailwind breakpoints: `sm:`, `md:`, `lg:`
- Use the neon-themed color palette for consistency:
  - Purple: `bg-purple-500`, `text-purple-400`
  - Pink: `bg-pink-500`, `text-pink-400`
  - Cyan: `bg-cyan-500`, `text-cyan-400`
- Add sufficient top padding on mobile: `pt-12 sm:pt-16`
- Ensure text contrast for accessibility (black text on white backgrounds by default)

### File Organization

```
src/
├── app/                    # Next.js app directory
│   ├── tour-escrow/       # TourEscrow module
│   │   ├── page.tsx       # Main entry point
│   │   └── about/         # About page
│   ├── api/               # API routes
│   └── config/            # Configuration files
├── components/            # Reusable components
│   ├── mnee/             # MNEE-specific components
│   └── ui/               # UI components (buttons, modals, etc.)
├── lib/                  # Utility functions
│   ├── wagmi.ts          # Wagmi configuration
│   └── mock-data-generator.ts
└── hooks/                # Custom React hooks
```

### Naming Conventions

- **Files**: `kebab-case.tsx` (e.g., `activity-timeline.tsx`)
- **Components**: `PascalCase` (e.g., `ActivityTimeline`)
- **Functions**: `camelCase` (e.g., `createBooking`)
- **Constants**: `UPPER_SNAKE_CASE` (e.g., `MAX_ESCROW_AMOUNT`)
- **Interfaces**: `PascalCase` (e.g., `BookingParams`)
- **Hooks**: `useCamelCase` (e.g., `useEscrowManager`)

---

## 📝 **Commit Message Guidelines**

We follow [Conventional Commits](https://www.conventionalcommits.org/) specification:

### Format

```
<type>(<scope>): <subject>

<body>

<footer>
```

### Types

- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting, no logic change)
- `refactor`: Code refactoring (no feature/bug changes)
- `test`: Adding or updating tests
- `chore`: Maintenance tasks (dependencies, config)
- `perf`: Performance improvements

### Examples

```bash
# Feature
feat(escrow): add multi-signature approval system

# Bug fix
fix(revenue-split): correct percentage calculation for 5-party split

# Documentation
docs(setup): add Infura API key configuration steps

# Refactor
refactor(coordination-hub): extract stakeholder panel into separate component

# Performance
perf(activity-timeline): optimize rendering with virtualization
```

### Rules

- ✅ Use imperative mood: "add" not "added" or "adds"
- ✅ Keep subject line under 72 characters
- ✅ Capitalize first letter of subject
- ✅ Don't end subject with a period
- ✅ Add body for complex changes (explain "why" not "what")
- ✅ Reference issues: `Closes #123` or `Fixes #456`

---

## 🔄 **Pull Request Process**

### Before Submitting

- [ ] Code follows [Coding Standards](#coding-standards)
- [ ] All tests pass locally
- [ ] TypeScript compiles without errors (`pnpm type-check`)
- [ ] Linting passes (`pnpm lint`)
- [ ] Production build succeeds (`pnpm build`)
- [ ] Documentation updated (if needed)
- [ ] Commit messages follow guidelines
- [ ] Branch is up-to-date with `main`

### PR Template

When creating a pull request, include:

```markdown
## Description
[Brief description of what this PR does]

## Type of Change
- [ ] Bug fix (non-breaking change)
- [ ] New feature (non-breaking change)
- [ ] Breaking change (fix or feature that changes existing functionality)
- [ ] Documentation update

## Related Issue
Closes #[issue number]

## How Has This Been Tested?
[Describe the tests you ran]

## Screenshots (if applicable)
[Add screenshots for UI changes]

## Checklist
- [ ] My code follows the project's coding standards
- [ ] I have performed a self-review of my code
- [ ] I have commented my code where necessary
- [ ] I have updated the documentation
- [ ] My changes generate no new warnings
- [ ] I have added tests that prove my fix/feature works
- [ ] New and existing tests pass locally
```

### Review Process

1. **Automated Checks**: CI/CD pipeline runs tests and linting
2. **Code Review**: Maintainers review your code
3. **Changes Requested**: Address feedback and push updates
4. **Approval**: Once approved, maintainers will merge

**Response Time**: We aim to review PRs within 48 hours.

### After Merge

- Your contribution is now part of the project! 🎉
- Update your local repository:
  ```bash
  git checkout main
  git pull upstream main
  ```
- Delete your feature branch:
  ```bash
  git branch -d feature/your-feature-name
  ```

---

## 🐛 **Issue Reporting**

### Bug Report Template

```markdown
## Bug Description
[Clear description of the bug]

## Steps to Reproduce
1. Go to '...'
2. Click on '...'
3. Scroll down to '...'
4. See error

## Expected Behavior
[What you expected to happen]

## Actual Behavior
[What actually happened]

## Environment
- OS: [e.g., macOS 14.0]
- Browser: [e.g., Chrome 120]
- Node.js: [e.g., 18.17.0]
- pnpm: [e.g., 8.10.0]

## Screenshots
[If applicable]

## Console Logs
[Paste relevant console output]

## Additional Context
[Any other information]
```

### Feature Request Template

```markdown
## Feature Description
[Clear description of the feature]

## Problem It Solves
[Explain the use case]

## Proposed Solution
[How you envision it working]

## Alternatives Considered
[Other approaches you thought about]

## Additional Context
[Mockups, diagrams, examples]
```

---

## 🌐 **Community**

### Communication Channels

- **GitHub Issues**: Bug reports and feature requests
- **GitHub Discussions**: General questions and ideas
- **Discord**: Real-time chat with maintainers and contributors

### Recognition

Contributors are recognized in:
- `CONTRIBUTORS.md` file
- Release notes
- Project README

Top contributors may be invited as project maintainers!

---

## 🏆 **Contributor Levels**

### First-Time Contributor
- Submitted 1 merged PR
- Badge: 🌱 "First Contribution"

### Regular Contributor
- Submitted 5+ merged PRs
- Badge: ⭐ "Regular Contributor"

### Core Contributor
- Submitted 20+ merged PRs or major features
- Badge: 💎 "Core Contributor"
- May be invited as maintainer

### Maintainer
- Invited by project owners
- Badge: 🛡️ "Maintainer"
- Full repository access
- Can approve/merge PRs

---

## 📚 **Additional Resources**

### Documentation
- [Setup Guide](./SETUP.md)
- [Main README](./README.md)

### Learning Resources
- [Next.js Documentation](https://nextjs.org/docs)
- [TypeScript Handbook](https://www.typescriptlang.org/docs/)
- [React Documentation](https://react.dev/)
- [Wagmi Documentation](https://wagmi.sh/)
- [OnchainKit Docs](https://onchainkit.xyz/)
- [Base Developer Docs](https://docs.base.org/)

### Tools
- [BaseScan Sepolia](https://sepolia.basescan.org/)
- [Base Sepolia Faucet](https://www.coinbase.com/faucets/base-ethereum-sepolia-faucet)
- [Conventional Commits](https://www.conventionalcommits.org/)

---

## ❓ **FAQ**

### Q: I'm new to Web3. Can I still contribute?

**A:** Absolutely! We welcome contributors of all experience levels. Start with documentation improvements or UI enhancements, then gradually learn Web3 concepts.

### Q: How long does it take for my PR to be reviewed?

**A:** We aim to review within 48 hours, but complex PRs may take longer. Be patient!

### Q: Can I work on an existing issue?

**A:** Yes! Comment on the issue saying you'd like to work on it. Wait for maintainer approval before starting (to avoid duplicate work).

### Q: What if my PR isn't accepted?

**A:** Don't be discouraged! We'll provide feedback on why and how to improve. Learning from rejection is part of the process.

### Q: Can I contribute if I don't code?

**A:** Yes! We need help with:
- Documentation
- Design/UX feedback
- Testing and bug reports
- Community support (answering questions)
- Translations

### Q: How do I become a maintainer?

**A:** Consistently contribute high-quality PRs, help review others' code, and demonstrate deep understanding of the project. Maintainers are invited by project owners.

---

## 🙏 **Thank You!**

Every contribution, no matter how small, makes TourEscrow better. Thank you for being part of our community!

**Happy coding! 🚀**

---

*Part of [STC Ultimate](https://stc-ultimate.elpeef.com/) — Smart Tourism Platform*
