# UserManagementAPI v3 — dengan Middleware (TechHive Solutions)

API Manajemen Pengguna (ASP.NET Core 8) dengan middleware logging, error handling, dan autentikasi token.
Dokumentasi: `docs/LAPORAN_MIDDLEWARE.md` (utama), `docs/LAPORAN_DEBUGGING.md` (aktivitas sebelumnya).

## Menjalankan
```bash
cd UserManagementAPI
dotnet run --launch-profile http     # Swagger: http://localhost:5080/swagger (klik Authorize, isi dev-token-techhive-2026)
```
Semua endpoint `/api/*` wajib header `Authorization: Bearer <token>`. Token Development: `dev-token-techhive-2026`.

## Test
```bash
cd UserManagementAPI.Tests
dotnet test
```

## Pipeline
`ErrorHandling → TokenAuthentication → RequestLogging → Controllers`

## Endpoint
| Method | URL | Respons |
|---|---|---|
| GET | /api/users?page&pageSize&department&search | 200 / 400 / 401 |
| GET | /api/users/{id} | 200 / 400 / 401 / 404 |
| POST | /api/users | 201 / 400 / 401 / 409 |
| PUT | /api/users/{id} | 200 / 400 / 401 / 404 / 409 |
| DELETE | /api/users/{id} | 204 / 400 / 401 / 404 |

Semua error: `{ "error": "pesan", "traceId": "...", "errors": { ... } (khusus validasi) }`.
