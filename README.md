# cursor_standards

Reusable Cursor rules for Python backend architecture, error handling, integrations, and clean class design.

## What this repo contains

This repository provides rule files under `.cursor/rules/` that guide AI-generated code toward consistent patterns:

- `exception-handling.mdc` - domain exception design with centralized error codes
- `http-error-mapping.mdc` - maps domain error codes to HTTP responses
- `third-party-integration.mdc` - structure for external API/SDK integrations
- `pydantic-usage.mdc` - when and how to use Pydantic models/settings
- `dependency-and-extension.mdc` - SOLID dependency inversion and extension patterns
- `class-design.mdc` - behavior-rich class structure and encapsulation rules
- `null-handling.mdc` - Null Object pattern for domain entities

## Intended usage

Use these rules in Cursor projects to enforce consistent architecture and code quality for:

- Domain-driven service layers
- Exception strategy and API-safe error responses
- Third-party integration boundaries
- DTO/schema validation conventions
- Maintainable, extensible class design

## Rule location

```text
.cursor/
  rules/
    *.mdc
```

## How to use in a project

1. Copy selected `.mdc` files into your target project's `.cursor/rules/` folder.
2. Keep rule names descriptive and domain-focused.
3. Apply only rules relevant to the project stack (mostly Python/FastAPI-oriented).
4. Iterate on rule text as team conventions evolve.

## Design principles enforced

- Domain exceptions must be HTTP-agnostic.
- Pydantic for boundary/data models, regular classes for domain behavior.
- Depend on protocols/abstractions, not concrete infrastructure classes.
- Prefer Null Object in domain layer over pervasive `None` checks.
- Keep extension points open without over-engineering.

## Best practices for maintaining this repo

- Keep each rule focused on one concern.
- Include clear "DO / DON'T" examples.
- Add migration notes when changing established patterns.
- Version major rule changes with changelog entries.

## Source repository

GitHub: [akashsingla19/cursor_standards](https://github.com/akashsingla19/cursor_standards)