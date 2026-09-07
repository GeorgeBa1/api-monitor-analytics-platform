# A.P.I. Sentinel — User Management
> **Current release: v3.0.0 — Enterprise A.P.I. Sentineling, Analytics & Observability Platform.

## Roles

- **ADMIN** — full platform administration, including user management.
- **OPERATOR** — can run/stop monitoring and use the operational dashboard.
- **USER** — standard dashboard access without administrative controls.

## Creating a user

An ADMIN opens **Users → Add User** and enters:

- username
- password (minimum 10 characters)
- email
- phone number
- role: Admin, Operator, or User

The platform generates the ID automatically and sequentially per role:

- `ADMIN-001`, `ADMIN-002`, ...
- `OPERATOR-001`, `OPERATOR-002`, ...
- `USER-001`, `USER-002`, ...

IDs are not reused when an account is deactivated.

## Security

Passwords are never stored in plaintext. The existing PBKDF2-HMAC-SHA256 password hashing flow remains in use. The user list stores only the password salt and derived hash.

Only ADMIN users can access the Users page or create/deactivate accounts.


## v3.0.0 Operational Notes

The current release uses the unified Premium UI across the Dashboard, APIs, Endpoints, Analytics, Alerts, Reports and Users areas. Monitoring controls are now operationally verified: Run checks worker startup, Stop clears stale worker state, and Reset removes monitoring history from the database and generated artifacts while preserving users and API definitions. Worker startup output is available in `monitoring.log`.
