---
sidebar_position: 6
---

# Other Matters

This page discusses other matters related to Flower that are not discussed in the previous sections.

## Development Conventions

### Code Style

For coding style, we can use [Prettier](https://prettier.io/) and [ESLint](https://eslint.org/), along with the recommended configurations by Prettier and ESLint. This would keep the configuration fairly simple, while enforcing reasonable coding standards.

### Commit Messages

Commit messages should be written in the imperative mood, with a maximum of 50 characters per line. For example:

```text
fix a bug in the code
```

or

```text
add a new feature to the code
```

or

```text
update the documentation for the code
```

The commit message should also include a brief description of the changes made.

### Branch Naming Conventions

Branch names should be prefixed with the type of change being made, followed by a forward slash, and then a descriptive summary of the changes. For example:

```text
feat/new-feature
```

or

```text
fix/bug-fix
```

or

```text
docs/documentation-update
```

### Pull Request Naming Conventions

The title of the pull request should contain the type of change being made in square brackets, followed by a space, and then a descriptive summary of the changes. For example:

```text
[feat] add new feature to the code
```

or

```text
[fix] fix a bug in the code
```

or

```text
[docs] update the documentation for the code
```

## Other Potential Enhancements

We could introduce **organisations** as an entity. Users could create organisations, or be assigned to them with different roles. Organisations could also manage multiple projects and the tasks under them.

We could also introduce **workflows** as an entity. The transition between workflow steps could be managed by a state machine. This would allow project/organisation admins to create custom workflows specific how they manage their tasks. Workflows could be used to automate parts of the todo lifecycle.
