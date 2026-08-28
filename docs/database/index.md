# Database

## ERD

The authoritative database relationship model is the [SecureReader ERD](https://docs.google.com/document/d/1bwScVpZCh8B_trL5izIKHlrFW-PT39U_f7wSsHbguFY/edit?tab=t.0#heading=h.6fxiynwr0aa5).

The ERD should be linked from the database page rather than redrawn manually, unless the diagram is deliberately maintained as part of the documentation site.

## Data dictionary

A complete column-level database dictionary is not present in the supplied Chrome extension source. Therefore the following are not invented here:

- table names;
- exact SQL types;
- nullability;
- indexes;
- foreign keys;
- constraints;
- migration names;
- seed data.

These details must come from the backend repository/ERD.

## Extension/database boundary

The extension does not directly query the database.

```
Chrome Extension
 ↓
Backend API
 ↓
Backend application/data layer
 ↓
Database
```

This boundary is important: database changes should normally be exposed through backend API contracts rather than implemented as direct browser database access.