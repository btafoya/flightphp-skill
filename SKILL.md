---
name: flightphp
description: "Helps with FlightPHP questions, code examples, debugging, and migrating existing PHP projects to FlightPHP. Use when working with FlightPHP framework, routing, middleware, requests, responses, plugins, building PHP APIs, or converting from other PHP frameworks like CodeIgniter or custom MVC."
---

# FlightPHP Skill

This skill helps users work with FlightPHP - a fast, simple, and extensible PHP micro-framework.

## When to Use This Skill

Use this skill whenever the user:
- Asks about FlightPHP features or how to do something in Flight
- Needs code examples for routing, middleware, requests, responses, or plugins
- Is debugging a FlightPHP application
- Mentions Flight framework, PHP API development, or any FlightPHP-specific topics

## Context7 Integration

FlightPHP has excellent documentation available via Context7. Always use Context7 to fetch relevant, up-to-date information.

**Library ID:** `/websites/flightphp_en_v3`

### How to Query Context7

1. First, resolve the library to get the Context7-compatible ID:
   - Use `mcp__plugin_context7_context7__resolve-library-id` with `libraryName: "flightphp"`

2. Then query the documentation:
   - Use `mcp__plugin_context7_context7__query-docs` with the library ID and a specific query about the topic

**Example queries:**
- "How to set up routing in FlightPHP with route parameters"
- "FlightPHP middleware implementation example"
- "FlightPHP request and response handling"
- "FlightPHP configuration and dependency injection"
- "FlightPHP plugins - JWT, sessions, caching"

## How This Skill Works

### 1. Answering Questions

When the user asks a question about FlightPHP:

1. Use Context7 to fetch relevant documentation
2. Read the documentation to understand the topic
3. Provide a clear, accurate answer with code examples when appropriate
4. Reference the official docs for further reading

### 2. Generating Code Examples

When the user needs code:

1. Identify what they're trying to accomplish (routing, middleware, DB, etc.)
2. Use Context7 to get current best practices
3. Provide complete, working code snippets
4. Explain the code briefly

### 3. Debugging FlightPHP Issues

When helping debug:

1. Ask clarifying questions about the error/issue
2. Use Context7 to find relevant documentation
3. Provide diagnostic steps and solutions
4. Suggest common pitfalls to check

## Core Topics Covered by FlightPHP

- **Routing**: Basic routes, route parameters, groups, named routes
- **Requests**: Input data, headers, uploaded files
- **Responses**: JSON, HTML, redirects, cookies
- **Middleware**: Before/after request processing
- **Configuration**: Framework settings, environment config
- **Dependency Injection**: Container and service registration
- **Events**: Event system for extensibility
- **Database**: PDO helpers, Active Record, Easy Query plugin
- **Templates**: View rendering with template engines
- **Security**: CSRF protection, input filtering
- **Plugins**: JWT auth, sessions, caching, Tracy debugging

### 4. Migrating to FlightPHP

When helping migrate an existing PHP project to FlightPHP:

#### Step 1: Analyze Existing Structure (Code Review)

Before generating any FlightPHP code, you MUST understand the user's existing codebase:

1. **Explore the project structure**:
   - List files and directories to understand organization
   - Look for common patterns: controllers, models, views folders
   - Identify the entry point (index.php, public/index.php, etc.)

2. **Review key files**:
   - Read controller files to understand routing patterns
   - Read model files to understand database access patterns
   - Read base/parent classes if inheritance is used
   - Look at configuration files

3. **Ask the user clarifying questions**:
   - "Can you show me a typical controller file?"
   - "How do you handle database queries?"
   - "What does your routing look like?"
   - "How are views rendered?"

#### Step 2: Map Patterns to FlightPHP

Based on the code review, map existing patterns to FlightPHP:

| Original Pattern | FlightPHP Equivalent |
|-----------------|---------------------|
| Custom router | `Flight::route()` with parameters |
| BaseController class | Plain PHP class or Flight's controller pattern |
| Model base class | `SimplePdo`, `PdoWrapper`, or `EasyQuery` plugin |
| View files | `Flight::render()` or Latte plugin |
| Custom auth | JWT plugin or middleware |
| Session handling | Session plugin |
| Input filtering | Flight's filtering functions |

#### Step 3: Generate Migration Code

1. Create a **mapping document** showing:
   - Original file → FlightPHP equivalent
   - Key changes needed (syntax, structure)

2. Generate the FlightPHP version:
   - Use Context7 to find best practices
   - Convert routing patterns
   - Convert controllers to FlightPHP style
   - Set up database connection

3. Test the migration:
   - Ensure routes work correctly
   - Verify database queries function
   - Check middleware execution order

### Migration Code Generation Examples

**Custom Controller → FlightPHP:**
```php
// BEFORE (custom MVC)
class UserController extends BaseController {
    public function show($id) {
        $user = $this->model->find($id);
        $this->view('user/profile', ['user' => $user]);
    }
}

// AFTER (FlightPHP)
Flight::route('/user/@id', function(string $id) {
    $user = User::find($id);
    Flight::render('user/profile', ['user' => $user]);
});
```

**Custom Model → FlightPHP with EasyQuery:**
```php
// BEFORE (custom MVC)
class User extends Model {
    public function find($id) {
        return $this->db->query("SELECT * FROM users WHERE id = ?", [$id])->fetch();
    }
}

// AFTER (FlightPHP with EasyQuery)
use flight\awesome\Querying\Model;

class User extends Model {
    protected static string $table = 'users';
}

// Usage: User::find($id)
```

## Output Guidelines

- Always be helpful and concise
- Provide working code examples when possible
- Use modern PHP (PHP 8+) syntax
- Reference official FlightPHP documentation when available
- If unsure about something, say so and suggest checking the docs