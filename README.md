# FlightPHP Skill

A Claude Code skill for working with [Flight](https://flightphp.com) - a fast, simple, and extensible PHP micro-framework.

## Features

- **Answers FlightPHP questions** - Get guidance on routing, middleware, requests, responses, plugins, and more
- **Generates code examples** - Working PHP code snippets for common FlightPHP patterns
- **Debugs FlightPHP issues** - Helps diagnose and fix common problems
- **Migrates to FlightPHP** - Convert existing PHP projects (custom MVC, CodeIgniter, etc.) to FlightPHP

## Installation

### Claude Code

```bash
# Copy skill to your plugins directory
cp -r flightphp-skill ~/.claude/plugins/skills/flightphp
```

### skills.sh

```bash
npx skills add btafoya/flightphp-skill
```

### ctx7 (Context7 CLI)

```bash
# Install for Claude Code
npx ctx7 skills install btafoya/flightphp-skill flightphp --claude

# Or install globally
npx ctx7 skills install btafoya/flightphp-skill flightphp --global
```

## Usage

### Questions

```
How do I set up route parameters in FlightPHP?
```

### Code Examples

```
Can you show me how to create middleware in FlightPHP for authentication?
```

### Debugging

```
I'm getting a 'Route not found' error in my FlightPHP app even though I defined the route.
```

### Migration

```
I have a custom PHP MVC with a UserController. How would I convert this to FlightPHP?
```

The skill will:
1. Analyze your existing codebase
2. Map patterns to FlightPHP equivalents
3. Generate migration code

## Integration

This skill uses [Context7](https://context7.com) to fetch up-to-date FlightPHP documentation, ensuring you get accurate guidance based on the official docs.

## Contributing

Contributions welcome! Please open an issue or PR on GitHub.

## License

MIT