---
title: "Release Notes Guide"
description: "How to set up and maintain release notes for your project"
---

# Release Notes Guide

This guide explains how engineers should structure and maintain release notes for their projects.

## Requirements

### Folder Structure

Every project that requires release notes must have a `release_notes` folder in the root directory:

```
your-project/
├── src/
├── release_notes/
│   ├── v1.0.0.md
│   ├── v1.1.0.md
│   └── TEMPLATE.md
├── README.md
└── ...
```

### File Naming

Release note files should follow semantic versioning:
- `v1.0.0.md` - Major release
- `v1.1.0.md` - Minor release
- `v1.1.1.md` - Patch release

## Template

Use this template for all release notes. Copy `TEMPLATE.md` and rename it to your version number.

```markdown
# Release X.Y.Z - Title

**Branch:** branch-name
**Date:** YYYY-MM-DD
**Author:** Your Name

---

## Summary

Brief description of what this release contains.

---

## Changes

### Bug Fixes

1. **Fix Name** - `file:line`
   - Description

### New Features

1. **Feature Name** - `file:line`
   - Description

### Improvements

1. **Improvement Name** - `file:line`
   - Description

### UI Changes

1. **UI Change** - `file:line`
   - Description

---

## How to Test

1. Step one
2. Step two

---

## Files Changed

- `path/to/file` - Description

---

## Breaking Changes

None / List any breaking changes

---

## Migration Notes

Any steps needed to migrate from previous version.
```

## Required Fields

| Field | Required | Description |
|-------|----------|-------------|
| Title | Yes | Version number and brief title |
| Branch | Yes | Git branch name |
| Date | Yes | Release date (YYYY-MM-DD) |
| Author | Yes | Who prepared the release |
| Summary | Yes | Brief description |
| Changes | Yes | At least one section with changes |
| How to Test | Recommended | Testing steps |
| Breaking Changes | If applicable | List any breaking changes |
| Migration Notes | If applicable | Migration steps |

## Internal Projects

For internal tools and applications, you should display release notes directly in the application:

### Implementation

1. **Add a Release Notes page** to your application
2. **Read the markdown files** from the `release_notes` folder
3. **Display version numbers** as tabs or dropdown at the top of the page
4. **Render the markdown** content for the selected version

### Example UI

```
┌─────────────────────────────────────────────────────┐
│  Release Notes                                       │
├─────────────────────────────────────────────────────┤
│  [v2.0.0] [v1.9.1] [v1.9.0] [v1.8.0] ◄── Version tabs│
├─────────────────────────────────────────────────────┤
│                                                      │
│  # Release v2.0.0 - Major Update                    │
│                                                      │
│  **Date:** 2026-01-29                               │
│  **Author:** Development Team                        │
│                                                      │
│  ## Summary                                          │
│  This release includes...                           │
│                                                      │
└─────────────────────────────────────────────────────┘
```

### Code Example (React)

```tsx
// Example: Loading and displaying release notes
const ReleaseNotes = () => {
  const [versions, setVersions] = useState<string[]>([]);
  const [selectedVersion, setSelectedVersion] = useState<string>('');
  const [content, setContent] = useState<string>('');

  // Fetch available versions from your API
  // Display version selector
  // Render markdown content
};
```

## Publishing to Documentation Portal

Release notes from registered projects are automatically pulled into this documentation portal. To register your project:

1. Ensure your `release_notes` folder follows the structure above
2. Contact the documentation team to add your project
3. Release notes will sync automatically on each push

### Currently Registered Projects

| Project | Source Path |
|---------|-------------|
| Engineering | `D:\repos\engineering\release_notes` |
| AI Chat | `D:\repos\ai-chat\release-notes` |
| Platform Config | `D:\repos\platform_config\release_notes` |

## Best Practices

1. **Write release notes as you develop** - Don't wait until release day
2. **Be specific** - Include file paths and line numbers where helpful
3. **Think about the reader** - What do they need to know?
4. **Include testing steps** - Help QA and other developers
5. **Document breaking changes prominently** - Don't surprise users
6. **Use consistent formatting** - Follow the template exactly
