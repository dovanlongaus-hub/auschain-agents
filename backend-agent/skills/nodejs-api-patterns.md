# Skill: Node.js API Patterns (2025/2026)
**Version:** 1.0 | **Date:** 2026-03-13 | **Agent:** Axel ⚙️

## Khi nào dùng skill này
Khi build REST API với Node.js — Express hoặc Hono framework.

## Chuẩn mực

### Route structure
```javascript
// routes/users.js
router.get('/', authenticate, async (req, res) => {
  try {
    const users = await UserService.list(req.query);
    res.json({ data: users, meta: { count: users.length } });
  } catch (err) {
    next(err); // always pass to error handler
  }
});
```

### Error handling middleware
```javascript
// middleware/errorHandler.js
export function errorHandler(err, req, res, next) {
  const status = err.status || 500;
  const message = status < 500 ? err.message : 'Internal server error';
  console.error({ err, path: req.path, method: req.method }); // log full err
  res.status(status).json({ error: message, code: err.code });
}
```

### Input validation (Zod)
```javascript
import { z } from 'zod';
const CreateUserSchema = z.object({
  email: z.string().email(),
  name: z.string().min(1).max(100),
});
// In route:
const data = CreateUserSchema.parse(req.body); // throws on invalid
```

### Rate limiting
```javascript
import rateLimit from 'express-rate-limit';
export const apiLimiter = rateLimit({
  windowMs: 15 * 60 * 1000, // 15 min
  max: 100,
  message: { error: 'Too many requests' }
});
```

## Common mistakes to avoid
- ❌ `catch (err) {}` — bỏ qua lỗi hoàn toàn
- ❌ Return stack traces to client in production
- ❌ Blocking operations in async route (use await)
- ❌ Không validate input trước khi dùng

## Security updates 2026 (Node.js production)

### Environment variable validation (new standard)
```javascript
// Validate all env vars at startup — fail fast
import { z } from 'zod';
const EnvSchema = z.object({
  DATABASE_URL: z.string().url(),
  JWT_SECRET: z.string().min(32),
  NODE_ENV: z.enum(['development', 'staging', 'production']),
});
export const env = EnvSchema.parse(process.env); // crashes if missing
```

### API versioning pattern (2026 standard)
```javascript
// Always version APIs from day 1
app.use('/api/v1', v1Router);
app.use('/api/v2', v2Router); // backward compat
// Headers: Accept-Version or URL prefix both acceptable
```

### Testing setup (Vitest + Supertest)
```javascript
// Vitest preferred over Jest in 2026 for Node.js (faster, ESM-native)
import { describe, it, expect } from 'vitest';
import request from 'supertest';
import app from '../app.js';

it('POST /api/v1/cases returns 201', async () => {
  const res = await request(app).post('/api/v1/cases').send({ visaType: '482' });
  expect(res.status).toBe(201);
});
```

### Key security reference (use with security-agent/owasp-web-2025.md)
- Use `helmet()` for security headers
- Validate CORS origins explicitly
- Rate limit all public endpoints
- TypeScript (not plain JS) for production — avoid dynamic typing bugs

## Changelog
- v1.0: Initial bootstrap
- v1.1 (2026-03-13): Env validation, API versioning, Vitest testing, cross-ref to OWASP skill
