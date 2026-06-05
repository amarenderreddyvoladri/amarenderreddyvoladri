<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:00ff88,50:00cfff,100:bf5fff&height=240&section=header&text=Amarender%20Reddy%20Voladri&fontSize=46&fontColor=ffffff&fontAlignY=36&desc=Java%20Full%20Stack%20Developer%20%7C%20Spring%20Boot%20%7C%20Spring%20Security%206%20%7C%20JWT%20%2B%20RBAC%20%7C%20Microservices&descAlignY=58&descSize=15&descColor=d0ffe8" />

</div>

<div align="center">

[![Portfolio](https://img.shields.io/badge/🌐_Portfolio-Visit_Now-00ff88?style=for-the-badge&logoColor=white)](https://amarenderreddyvoladri-portfolio.netlify.app/)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/amarender-reddy-voladri/)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/amarenderreddyvoladri)
[![Open to Work](https://img.shields.io/badge/🟢_Open_To_Work-Available_Now-2ea44f?style=for-the-badge)](https://www.linkedin.com/in/amarender-reddy-voladri/)

</div>

---

## 👨‍💻 About Me

```java
public class AmarenderReddyVoladri {

    String role        = "Software Engineer Associate | Java Full Stack Developer";
    String education   = "MCA — Master of Computer Applications (2024)";
    String experience  = "1+ Year · Enterprise HRMS · Microservices · Full Stack";
    String location    = "Hyderabad, India 🇮🇳";

    String[] expertise = {
        "Spring Boot 3 REST APIs",       "Spring Security 6 + JWT + RBAC",
        "Angular + TypeScript",           "Microservices Architecture",
        "MySQL + Hibernate/JPA",          "Docker + Redis + Kafka",
        "Eureka + Spring Cloud",          "CI/CD Pipelines + DevOps"
    };

    String philosophy  = "Secure · Scalable · Maintainable enterprise software.";
}
```

- 🏢 Built a **real-time enterprise HRMS platform** — employee onboarding, access control, attendance & approval workflows
- 🔐 Implemented **production-grade Spring Security 6 + JWT + RBAC** with userId-based immutable tokens, DB-backed session control, OTP flows, brute-force protection, and forced password change enforcement
- 🧩 Hands-on with **Microservices** — Spring Cloud Config Server, Eureka Service Registry, Docker Compose, Kafka
- 🗂️ Engineered **comprehensive audit logging**, token lifecycle management, Redis-backed OTP flows, and scheduled token cleanup
- 🌐 **Portfolio:** [amarenderreddyvoladri-portfolio.netlify.app](https://amarenderreddyvoladri-portfolio.netlify.app/)

---

## 📊 GitHub Stats

<div align="center">

<img src="https://github-readme-stats.vercel.app/api?username=amarenderreddyvoladri&show_icons=true&theme=github_dark&hide_border=true&count_private=true&bg_color=0d1117&title_color=00ff88&icon_color=00cfff&text_color=c9d1d9" height="170"/>
&nbsp;&nbsp;
<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=amarenderreddyvoladri&layout=compact&theme=github_dark&hide_border=true&bg_color=0d1117&title_color=00ff88&text_color=c9d1d9" height="170"/>

</div>

<div align="center">

<img src="https://github-readme-streak-stats.herokuapp.com/?user=amarenderreddyvoladri&theme=github-dark-blue&hide_border=true&background=0d1117&ring=00ff88&fire=00cfff&currStreakLabel=00ff88&sideLabels=c9d1d9&dates=6b82a8" />

</div>

---

## 🔐 Featured Project — Enterprise Spring Security Template

> **Production-Ready Authentication, Authorization & Identity Management Microservice**
> A reusable enterprise-grade security foundation simulating real-world systems used in HRMS, fintech, and SaaS platforms.

### 🏗️ Complete System Architecture

```
╔══════════════════════════════════════════════════════════════════════════════════╗
║             ENTERPRISE SPRING SECURITY TEMPLATE — PRODUCTION ARCHITECTURE       ║
╠══════════════════════════════════════════════════════════════════════════════════╣
║                                                                                  ║
║   CLIENT (Angular SPA / Postman / Mobile App)                                    ║
║   ┌────────────────────────────────────────────────────────────────────────┐     ║
║   │  POST /api/v1/auth/login    │  Authorization: Bearer <access_token>   │     ║
║   │  POST /api/v1/users/register│  POST /api/v1/auth/refresh-token         │     ║
║   └──────────────────┬─────────────────────────────────┬──────────────────┘     ║
║                      │ HTTPS                           │ HTTPS                  ║
║                      ▼                                 ▼                        ║
║   ╔════════════════════════════════════════════════════════════════════════╗     ║
║   ║              SPRING SECURITY FILTER CHAIN (OncePerRequestFilter)      ║     ║
║   ║  ┌────────────────────────────────────────────────────────────────┐   ║     ║
║   ║  │  JwtFilter (8-Layer Validation Pipeline)                        │   ║     ║
║   ║  │  ① No Bearer token? → pass to public endpoints               │   ║     ║
║   ║  │  ② Cryptographic JWT signature + expiry check                 │   ║     ║
║   ║  │  ③ tokenType guard → ONLY "ACCESS" tokens pass                │   ║     ║
║   ║  │  ④ DB session check → revoked / expired flags in user_tokens  │   ║     ║
║   ║  │  ⑤ DB expiry sync → detects clock/timing mismatch             │   ║     ║
║   ║  │  ⑥ Extract userId (immutable PK) + role + permissions         │   ║     ║
║   ║  │  ⑦ forcePasswordChange guard → blocks all endpoints but /auth │   ║     ║
║   ║  │  ⑧ Build GrantedAuthority list → set SecurityContextHolder    │   ║     ║
║   ║  └────────────────────────────────────────────────────────────────┘   ║     ║
║   ╚════════════════════════════════════════════════════════════════════════╝     ║
║                      │                                                           ║
║          ┌───────────┼───────────┬─────────────┐                               ║
║          ▼           ▼           ▼             ▼                               ║
║   ┌─────────────┐ ┌──────────┐ ┌──────────┐ ┌──────────────┐                 ║
║   │    AUTH     │ │  ADMIN   │ │   USER   │ │    AUDIT     │                 ║
║   │  CONTROLLER │ │CONTROLLER│ │CONTROLLER│ │  CONTROLLER  │                 ║
║   │             │ │          │ │          │ │              │                 ║
║   │ POST /login │ │GET /users│ │GET /me   │ │GET /logs     │                 ║
║   │ POST /logout│ │ lock/    │ │ register │ │ (ADMIN only) │                 ║
║   │ POST /refresh│ │ unlock/  │ │ otp-flow │ │              │                 ║
║   │ GET /sessions│ │ enable/  │ │ password │ │              │                 ║
║   │ DELETE /     │ │ disable  │ │ reset    │ │              │                 ║
║   │  sessions/id │ │ force-   │ │ change   │ │              │                 ║
║   │ POST /logout-│ │ logout   │ │ username │ │              │                 ║
║   │  all         │ │ revoke   │ │ change   │ │              │                 ║
║   └──────┬──────┘ └────┬─────┘ └────┬─────┘ └──────┬───────┘                 ║
║          │             │            │              │                           ║
║          └─────────────┴────────────┴──────────────┘                          ║
║                                    │                                           ║
║               ┌────────────────────┼────────────────────┐                     ║
║               ▼                    ▼                    ▼                     ║
║   ┌───────────────────┐ ┌─────────────────────┐ ┌─────────────────────┐       ║
║   │   SERVICE LAYER   │ │   SECURITY SERVICES │ │  SCHEDULED SERVICES │       ║
║   │                   │ │                     │ │                     │       ║
║   │  AuthServiceImpl  │ │ LoginAttemptService │ │ TokenCleanupScheduler│       ║
║   │  AdminServiceImpl │ │ RedisLoginAttempt   │ │ (every 5 minutes)   │       ║
║   │  UserServiceImpl  │ │   Service           │ │ → marks expired     │       ║
║   │  AuditService     │ │ RedisOtpService     │ │   tokens in DB      │       ║
║   │  EmailService     │ │ RoleInitialization  │ │                     │       ║
║   │  AuditQueryService│ │   Service           │ │                     │       ║
║   └────────┬──────────┘ └──────────┬──────────┘ └─────────────────────┘       ║
║            │                       │                                           ║
║            └───────────┬───────────┘                                           ║
║                        ▼                                                       ║
║   ┌────────────────────────────────────────────────────────────────────────┐   ║
║   │                      INFRASTRUCTURE LAYER                              │   ║
║   │                                                                        │   ║
║   │  ┌─────────────────────┐  ┌─────────────────────┐  ┌────────────────┐ │   ║
║   │  │   MYSQL 8.4         │  │   REDIS 7 (Alpine)  │  │  SENDGRID API  │ │   ║
║   │  │   (Docker Volume)   │  │   (Docker Volume)   │  │  (Email/OTP)   │ │   ║
║   │  │                     │  │                     │  │                │ │   ║
║   │  │  users              │  │  otp:<purpose>:     │  │ Registration   │ │   ║
║   │  │  roles              │  │    <email>  TTL:5m  │  │ OTP emails     │ │   ║
║   │  │  permissions        │  │                     │  │ Password reset │ │   ║
║   │  │  role_permissions   │  │  login_attempt:     │  │ Notifications  │ │   ║
║   │  │  user_tokens        │  │    <username>       │  │                │ │   ║
║   │  │  audit_logs         │  │    TTL: configurable│  │                │ │   ║
║   │  │  otp_tokens         │  │                     │  │                │ │   ║
║   │  │  password_reset_    │  │  permission cache   │  │                │ │   ║
║   │  │    tokens           │  │                     │  │                │ │   ║
║   │  └─────────────────────┘  └─────────────────────┘  └────────────────┘ │   ║
║   └────────────────────────────────────────────────────────────────────────┘   ║
║                                                                                  ║
║   ┌────────────────────────────────────────────────────────────────────────┐   ║
║   │                  SPRING CLOUD MICROSERVICES LAYER                      │   ║
║   │                                                                        │   ║
║   │  ┌───────────────────────┐        ┌────────────────────────────┐       │   ║
║   │  │   CONFIG SERVER       │        │   EUREKA SERVICE REGISTRY  │       │   ║
║   │  │   (Spring Cloud)      │        │   (Port 8761)              │       │   ║
║   │  │   Dockerfile + Docker │        │   Dockerfile + Docker      │       │   ║
║   │  │   Compose ready       │        │   Compose ready            │       │   ║
║   │  │   ApplicationInfo     │        │   DiscoveryServer          │       │   ║
║   │  │   Contributor         │        │   HealthIndicator          │       │   ║
║   │  │   StartupLogger       │        │   StartupLogger            │       │   ║
║   │  └───────────────────────┘        └────────────────────────────┘       │   ║
║   └────────────────────────────────────────────────────────────────────────┘   ║
║                                                                                  ║
╚══════════════════════════════════════════════════════════════════════════════════╝
```

---

### 🔄 JWT Authentication & Token Lifecycle Flow

```
┌──────────────────────────────────────────────────────────────────────────────────┐
│                      COMPLETE JWT TOKEN LIFECYCLE (PRODUCTION)                   │
├──────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  REGISTRATION FLOW ──────────────────────────────────────────────────────────── │
│                                                                                  │
│  Client → POST /users/send-registration-otp                                      │
│             └──► RedisOtpService.saveOtp()                                       │
│                  Key: "otp:REGISTRATION:<email>"  TTL: 5 minutes                 │
│             └──► EmailService (SendGrid) → OTP email delivered                   │
│                                                                                  │
│  Client → POST /users/register  { email, otp, password }                        │
│             └──► RedisOtpService.getOtp() → verifies OTP                        │
│             └──► BCrypt.encode(password, strength=configurable)                  │
│             └──► User saved with status=PENDING_APPROVAL                         │
│             └──► Admin approves → role assigned → ACTIVE                         │
│                                                                                  │
│  LOGIN FLOW ─────────────────────────────────────────────────────────────────── │
│                                                                                  │
│  Client → POST /api/v1/auth/login { username, password }                        │
│    │                                                                             │
│    ▼                                                                             │
│  AuthenticationManager.authenticate()                                            │
│    └──► DaoAuthenticationProvider                                                │
│           └──► UserDetailsService.loadUserByUsername()                           │
│           └──► BCryptPasswordEncoder.matches(raw, hashed)                        │
│                  │                                                               │
│                  ▼                                                               │
│  LoginAttemptService ──────────────────────────────────────────────             │
│    FAILED? → RedisLoginAttemptService.increment(username)                        │
│              attempts >= max? → accountLocked=true, lockTime=now                 │
│              AuditService.log(ACCOUNT_LOCKED, BLOCKED)                           │
│                                                                                  │
│    SUCCESS? → RedisLoginAttemptService.reset(username)                           │
│               User.lastLoginAt=now, lastLoginIp, lastLoginDevice                 │
│                  │                                                               │
│                  ▼                                                               │
│  JwtUtility.generateAccessToken(userId, role, permissions)                       │
│    subject = userId (Long)  ← IMMUTABLE — username-change-safe                  │
│    claims  = { role, permissions[], tokenType="ACCESS" }                         │
│    signed  = HMAC-SHA256(secret)                                                 │
│    expiry  = configurable (default 15 min)                                       │
│                                                                                  │
│  JwtUtility.generateRefreshToken(userId)                                         │
│    claims  = { tokenType="REFRESH" }                                             │
│    expiry  = configurable (default 7 days)                                       │
│                                                                                  │
│  UserToken saved to DB ──────────────────────────────────────────────────────   │
│    tokenId (UUID jti), accessToken, refreshToken                                 │
│    accessExpiry, refreshExpiry, deviceInfo, ipAddress                            │
│    revoked=false, expired=false, refreshUsed=false                               │
│                                                                                  │
│  TOKEN REFRESH FLOW ─────────────────────────────────────────────────────────── │
│                                                                                  │
│  Client → POST /api/v1/auth/refresh-token { refreshToken }                      │
│    └──► isTokenValid() + tokenType="REFRESH" check                               │
│    └──► DB token: revoked=false, refreshUsed=false                               │
│    └──► refreshUsed=true (prevents refresh token reuse)                          │
│    └──► New access + refresh tokens issued                                       │
│    └──► Old token record updated                                                 │
│                                                                                  │
│  LOGOUT / SESSION MANAGEMENT ────────────────────────────────────────────────── │
│                                                                                  │
│  POST /logout          → current token: revoked=true, expired=true               │
│  POST /logout-all      → ALL user tokens: revoked=true                           │
│  DELETE /sessions/{id} → specific session revoked                                │
│  Admin force-logout    → admin can revoke any user's tokens                      │
│                                                                                  │
│  SCHEDULED CLEANUP ──────────────────────────────────────────────────────────── │
│                                                                                  │
│  TokenCleanupScheduler runs every 5 minutes                                      │
│    → fetches all tokens where expired=false                                      │
│    → if accessExpiry AND refreshExpiry both passed → marks expired=true          │
│    → batch saveAll() to DB                                                       │
│                                                                                  │
└──────────────────────────────────────────────────────────────────────────────────┘
```

---

### 🛡️ RBAC — Role, Permission & Authorization Model

```
┌──────────────────────────────────────────────────────────────────────────────────┐
│                      ROLE-BASED ACCESS CONTROL (RBAC) MODEL                      │
├──────────────────────────────────────────────────────────────────────────────────┤
│                                                                                  │
│  DATABASE SCHEMA ────────────────────────────────────────────────────────────── │
│                                                                                  │
│  ┌──────────┐    ┌───────────────────┐    ┌──────────────────┐                  │
│  │  users   │    │  role_permissions │    │   permissions    │                  │
│  ├──────────┤    ├───────────────────┤    ├──────────────────┤                  │
│  │ id (PK)  │    │ role_id (FK)      │    │ id (PK)          │                  │
│  │ username │    │ permission_id(FK) │    │ name (UNIQUE)    │                  │
│  │ password │    └───────────────────┘    │ description      │                  │
│  │ role_id  │                             └──────────────────┘                  │
│  │ status   │    ┌──────────────────┐                                            │
│  │ enabled  │    │      roles       │                                            │
│  │ accountLocked│ ├──────────────────┤                                           │
│  │ failedLogin  │ │ id (PK)          │                                           │
│  │ Attempts     │ │ name (UNIQUE)    │                                           │
│  │ lockTime     │ │ description      │                                           │
│  │ forcePassword│ └──────────────────┘                                           │
│  │ Change       │                                                                 │
│  │ lastLoginAt  │                                                                 │
│  │ lastLoginIp  │                                                                 │
│  │ lastLoginDevice│                                                               │
│  └──────────┘                                                                    │
│                                                                                  │
│  JWT CLAIMS STRUCTURE ────────────────────────────────────────────────────────  │
│                                                                                  │
│  {                                                                               │
│    "sub":         "42",                   ← userId (immutable PK, not email)    │
│    "role":        "ADMIN",                ← role name                            │
│    "permissions": ["READ_USER",           ← granular permission strings          │
│                    "DELETE_USER",                                                │
│                    "FORCE_LOGOUT",                                               │
│                    "ACCOUNT_LOCK",                                               │
│                    "SYSTEM_ADMIN"],                                              │
│    "tokenType":   "ACCESS",               ← guards against refresh token abuse  │
│    "iat":         1717600000,                                                    │
│    "exp":         1717600900                                                     │
│  }                                                                               │
│                                                                                  │
│  AUTHORIZATION LAYERS ────────────────────────────────────────────────────────  │
│                                                                                  │
│  Layer 1 — Route-level (SecurityFilterChain)                                     │
│    /api/v1/auth/login              → permitAll()                                 │
│    /api/v1/users/register          → permitAll()                                 │
│    /api/v1/users/forgot-password   → permitAll()                                 │
│    OPTIONS /**                     → permitAll() (CORS preflight)                │
│    /swagger-ui/**                  → permitAll()                                 │
│    everything else                 → authenticated()                             │
│                                                                                  │
│  Layer 2 — Controller-level (@PreAuthorize)                                      │
│    @PreAuthorize("hasRole('ADMIN')")           ← all methods in AdminController  │
│    @PreAuthorize("hasAuthority('READ_USER')")  ← granular permission check       │
│    @PreAuthorize("hasAuthority('FORCE_LOGOUT')")                                 │
│    @PreAuthorize("hasAuthority('ACCOUNT_LOCK')")                                 │
│    @PreAuthorize("hasAuthority('SYSTEM_ADMIN')")                                 │
│    @PreAuthorize("isAuthenticated()")          ← user-level self-service         │
│                                                                                  │
│  Layer 3 — Permission Matrix                                                     │
│                                                                                  │
│  Permission          │ ADMIN │ MANAGER │ EMPLOYEE │ Description                  │
│  ────────────────────┼───────┼─────────┼──────────┼───────────────────────────  │
│  READ_USER           │  ✅   │   ✅    │    ❌    │ View user list               │
│  VIEW_USERS          │  ✅   │   ✅    │    ❌    │ Access user endpoints        │
│  DELETE_USER         │  ✅   │   ❌    │    ❌    │ Permanent delete             │
│  FORCE_LOGOUT        │  ✅   │   ❌    │    ❌    │ Terminate any session        │
│  REVOKE_TOKEN        │  ✅   │   ❌    │    ❌    │ Revoke user tokens           │
│  SESSION_REVOKE      │  ✅   │   ❌    │    ❌    │ Invalidate sessions          │
│  ACCOUNT_LOCK        │  ✅   │   ❌    │    ❌    │ Lock user account            │
│  ACCOUNT_UNLOCK      │  ✅   │   ❌    │    ❌    │ Unlock user account          │
│  TOGGLE_USER_ACCESS  │  ✅   │   ❌    │    ❌    │ Enable / disable user        │
│  SYSTEM_ADMIN        │  ✅   │   ❌    │    ❌    │ Maintenance, cache ops       │
│  VIEW_SYSTEM_STATS   │  ✅   │   ❌    │    ❌    │ System analytics             │
│  VIEW_SECURITY_STATS │  ✅   │   ❌    │    ❌    │ Security analytics           │
│  ASSIGN_EMPLOYEE     │  ✅   │   ✅    │    ❌    │ Approve registration         │
│  ASSIGN_MANAGER      │  ✅   │   ❌    │    ❌    │ Promote to manager           │
│  UPDATE_USER_STATUS  │  ✅   │   ✅    │    ❌    │ Reject registration          │
│                                                                                  │
└──────────────────────────────────────────────────────────────────────────────────┘
```

---

### 🔒 Production Security Features Matrix

| Security Feature | Implementation | Location |
|---|---|---|
| **Immutable JWT Subject** | `sub` = `userId` (Long PK), never username — username-change-safe | `JwtUtility.java` |
| **Token Type Guard** | REFRESH tokens blocked from API access via `tokenType` claim check | `JwtFilter.java` |
| **DB-Backed Session Control** | Every token stored in `user_tokens` table; revoked/expired flags checked on every request | `JwtFilter.java`, `UserToken.java` |
| **DB Expiry Sync** | `accessExpiry` compared against `Instant.now()` to catch clock mismatch | `JwtFilter.java` |
| **Force Password Change** | `forcePasswordChange` flag blocks all endpoints except `/change-password` + `/logout` | `JwtFilter.java`, `User.java` |
| **Brute-Force Protection** | Redis-backed login attempt counter; auto-lock after configurable max attempts | `LoginAttemptService`, `RedisLoginAttemptService` |
| **OTP Registration** | Redis-stored OTP (`TTL: 5 min`) for registration; verified before account creation | `RedisOtpService` |
| **OTP Password Reset** | Redis-stored OTP for forgot-password flow; OTP verified before new password accepted | `RedisOtpService`, `UserController` |
| **Refresh Token Reuse Detection** | `refreshUsed` flag set on first use; reuse attempt is rejected | `UserToken.java` |
| **Multi-Device Session Management** | Active sessions viewable and individually revocable; logout-all supported | `AuthController.java` |
| **Device + IP Tracking** | `deviceInfo`, `ipAddress` captured on login and token issuance | `User.java`, `UserToken.java` |
| **Production Audit Logging** | Every action logged in `audit_logs` with userId, role, action, status, endpoint, IP, device, timestamp | `AuditService.java`, `AuditLog.java` |
| **Audit Transaction Isolation** | `@Transactional(propagation = REQUIRES_NEW)` — audit never fails business operations | `AuditService.java` |
| **Scheduled Token Cleanup** | `@Scheduled(fixedRate = 300000)` — expired tokens auto-marked every 5 minutes | `TokenCleanupScheduler.java` |
| **Security Headers** | `X-Content-Type-Options: nosniff`, `X-Frame-Options: DENY`, `Referrer-Policy: no-referrer` | `SecurityConfig.java` |
| **Centralised CORS** | Environment-based allowed origins; no `*` wildcard with credentials | `SecurityConfig.java` |
| **Lazy Auth Circular Dep Fix** | `@Lazy` on `IAuthService` in `SecurityConfig` constructor resolves Spring circular dependency | `SecurityConfig.java` |
| **JPA Auditing** | `createdBy`, `updatedBy`, `createdDate`, `lastModifiedDate` auto-populated via `AuditorAwareImpl` | `Auditable.java`, `AuditConfig.java` |
| **DB Indexes** | Indexes on `username`, `status` in `users`; `user_id`, `action`, `status`, `created_at` in `audit_logs` | `User.java`, `AuditLog.java` |
| **Bean Validation** | `@Email`, `@NotBlank`, `@Size` + `@Valid` on all request bodies | Entity + Request classes |
| **Global Exception Handler** | Catches `ExpiredJwtException`, `MalformedJwtException`, `LockedException`, `AccessDeniedException`, etc. | `GlobalExceptionHandler.java` |
| **Multi-Stage Docker Build** | Build stage: `maven:3.9.9-eclipse-temurin-21`; Runtime: `eclipse-temurin:21-jre` — minimal image | `Dockerfile` |
| **Docker Compose Healthchecks** | MySQL and Redis health checks before app container starts (`depends_on` with `service_healthy`) | `docker-compose.yml` |
| **Env-Based Config** | `.env` driven secrets (JWT secret, DB credentials, SendGrid keys) — no hardcoded values | `docker-compose.yml`, `.env` |

---

### 📁 Project Structure

```
production-prototype-security-template/
│
├── 📦 springboot-security-jwt-rbac-app4/         ← Main Security Service
│   ├── 📄 Dockerfile                              ← Multi-stage build (Maven → JRE)
│   ├── 📄 docker-compose.yml                      ← MySQL 8.4 + Redis 7 + App
│   └── src/main/java/com/harinitech/
│       └── springboot_security_jwt_rbac_app1/
│           ├── config/
│           │   ├── SecurityConfig.java            ← Filter chain, CORS, headers, @Lazy fix
│           │   ├── RedisConfig.java               ← Jackson serializer, JavaTimeModule
│           │   ├── SwaggerConfig.java             ← OpenAPI / Swagger UI
│           │   ├── AuditConfig.java               ← @EnableJpaAuditing
│           │   ├── AuditorAwareImpl.java          ← userId-based JPA auditor
│           │   ├── PaginationConfig.java          ← Default page size config
│           │   └── TimeZoneConfig.java            ← Timezone standardisation
│           │
│           ├── filter/
│           │   └── JwtFilter.java                 ← 8-layer validation pipeline
│           │
│           ├── utility/
│           │   ├── JwtUtility.java                ← userId-based token gen/validation
│           │   ├── TokenCleanupScheduler.java     ← @Scheduled every 5 min cleanup
│           │   └── RequestInfoUtil.java           ← Client IP + device extraction
│           │
│           ├── entity/
│           │   ├── User.java                      ← Full account security model
│           │   ├── Role.java                      ← @ManyToMany permissions
│           │   ├── Permission.java                ← Granular authority strings
│           │   ├── UserToken.java                 ← Full token lifecycle (jti, expiry, device)
│           │   ├── AuditLog.java                  ← Indexed audit trail
│           │   ├── Auditable.java                 ← @CreatedDate, @LastModifiedDate base
│           │   └── OtpToken.java                  ← DB-backed OTP entity
│           │
│           ├── controller/
│           │   ├── AuthController.java            ← login, refresh, logout, sessions
│           │   ├── AdminController.java           ← @PreAuthorize("hasRole('ADMIN')")
│           │   ├── UserController.java            ← register, OTP, password, profile
│           │   └── AuditController.java           ← audit log queries (admin only)
│           │
│           ├── service/
│           │   ├── AuthServiceImpl.java           ← Full auth flow
│           │   ├── AdminServiceImpl.java          ← Admin operations
│           │   ├── UserServiceImpl.java           ← User management
│           │   ├── AuditService.java              ← REQUIRES_NEW transaction
│           │   ├── AuditQueryService.java         ← Audit log querying
│           │   ├── LoginAttemptService.java       ← Brute-force + auto-lock
│           │   ├── RedisLoginAttemptService.java  ← Redis attempt counter
│           │   ├── RedisOtpService.java           ← TTL-based OTP store
│           │   ├── EmailService.java              ← SendGrid integration
│           │   └── TokenCleanupService.java       ← Token lifecycle management
│           │
│           ├── passwordreset/
│           │   ├── PasswordResetToken.java        ← Reset token entity
│           │   ├── PasswordResetTokenRepository.java
│           │   ├── ForgotPasswordRequest.java
│           │   └── ResetPasswordRequest.java
│           │
│           ├── security/
│           │   ├── RoleInitializationService.java ← Seeds roles/permissions on startup
│           │   └── UserDataInitializer.java       ← Seeds default admin user
│           │
│           ├── exceptions/
│           │   └── GlobalExceptionHandler.java   ← JWT, Security, Validation errors
│           │
│           └── model/                             ← DTOs, Request/Response models
│               ├── ApiResponse.java              ← Unified response wrapper
│               ├── JwtRequest/Response           ← Login models
│               ├── RegisterRequest.java          ← OTP + credentials
│               ├── UserResponseDto.java          ← Safe user projection
│               └── AuditAction/Status enums
│
├── ⚙️ eureka-server/                              ← Service Discovery
│   ├── Dockerfile
│   ├── docker-compose.yml
│   └── DiscoveryServerHealthIndicator.java
│
└── ⚙️ config-server/                              ← Centralised Config
    ├── Dockerfile
    ├── docker-compose.yml
    └── ApplicationInfoContributor.java
```

---

### ⚙️ Tech Stack Deep-Dive

| Layer | Technology | Version | Purpose |
|---|---|---|---|
| **Runtime** | Java | 21 (LTS) | Modern records, sealed classes, virtual threads ready |
| **Framework** | Spring Boot | 3.x | Auto-configuration, production-ready starters |
| **Security** | Spring Security | 6.x | SecurityFilterChain, @EnableMethodSecurity |
| **Auth** | JJWT (jjwt-api/impl/jackson) | Latest | HMAC-SHA256 signed tokens |
| **ORM** | Spring Data JPA + Hibernate | 6.x | Entities, repositories, lazy/eager loading |
| **Database** | MySQL | 8.4 | Production-grade RDBMS, Docker healthcheck |
| **Cache / Session** | Redis | 7 (Alpine) | OTP TTL store, login attempt counters |
| **Redis Client** | Spring Data Redis + commons-pool2 | Latest | Connection pooling, Jackson serialization |
| **Email** | SendGrid + Spring Mail | Latest | OTP delivery, password reset emails |
| **Service Discovery** | Spring Cloud Netflix Eureka | Latest | Service registry, health monitoring |
| **Config Management** | Spring Cloud Config Server | Latest | Centralised configuration |
| **API Docs** | SpringDoc OpenAPI (Swagger UI) | Latest | Auto-generated API documentation |
| **Build** | Maven | 3.9.9 | Dependency management, lifecycle |
| **Containerisation** | Docker + Docker Compose | Latest | Multi-stage build, health checks |
| **Validation** | Spring Validation (Hibernate Validator) | Latest | Bean validation on all requests |
| **Utilities** | Lombok | Latest | Boilerplate reduction |
| **Scheduler** | Spring @Scheduled | Built-in | Token cleanup every 5 min |

---

## 🏢 Work Experience

### Software Engineer Associate — Enterprise HRMS Platform
> *Real-time enterprise application · Employee Lifecycle & Workforce Operations*

- 🔧 Developed and maintained **RESTful APIs** using Java & Spring Boot for onboarding workflows, employee profile management, role assignment, approval processes, and real-time status tracking
- 🔐 Implemented **Spring Security 6 + JWT + RBAC** for Admin, HR, and Employee module access control — stateless, secure, and scalable with refresh token rotation and multi-device session management
- 🖥️ Built **Angular frontend** with Reactive Forms, TypeScript, and Angular Material — dynamic forms, validations, dashboards, and user interaction workflows
- 🗄️ Used **Hibernate/JPA + MySQL** for CRUD operations, entity mapping, lazy/eager loading, and optimized queries with database indexing
- 🧩 Worked with **Microservices architecture** — Spring Cloud Config Server and Eureka Service Registry for centralised configuration and service discovery
- 🐳 Implemented **Docker containerisation** with multi-stage builds, Redis caching for OTP and session management, Kafka event communication, Git version control, and CI/CD deployment workflows
- 🔄 Collaborated in **Agile Scrum** — daily stand-ups, sprint planning, code reviews, bug fixes, and release cycles
- 🐛 Debugged production issues, performed **Postman API testing**, wrote Swagger/OpenAPI docs, and supported stable deployment activities

`Java` `Spring Boot 3` `Spring Security 6` `JWT` `RBAC` `Angular` `TypeScript` `Reactive Forms` `Hibernate` `JPA` `MySQL` `Microservices` `Spring Cloud` `Eureka` `Config Server` `Docker` `Redis` `Kafka` `CI/CD` `Swagger`

---

## 🚀 Projects

### 🔐 Enterprise Spring Security Template
> **Production-Ready Authentication, Authorization & Identity Management Microservice**
> [→ View on GitHub](https://github.com/amarenderreddyvoladri/production-prototype-security-template)

A reusable enterprise-grade Spring Security template with production-quality security architecture covering the complete identity management lifecycle.

| Feature Area | What's Built |
|---|---|
| 🔑 **Authentication** | OTP-verified registration, login with JWT access (15 min) + refresh tokens (7 days), BCrypt password hashing |
| 🛡️ **Authorization** | RBAC with `@PreAuthorize` — dual-layer role + granular permission checks per endpoint |
| 🔄 **Token Lifecycle** | DB-backed session store, refresh token rotation with reuse detection, token type guards, scheduled cleanup |
| 🔒 **Brute-Force Protection** | Redis-backed attempt counter with configurable threshold, auto account lock + audit log |
| 📱 **Session Management** | Multi-device session view, individual session revoke, logout-all, admin force-logout |
| 🔑 **OTP Flows** | Redis TTL-based OTP for registration + password reset via SendGrid email |
| 🧾 **Audit Trail** | Every security event logged with userId, role, endpoint, IP, device, timestamp — isolated transactions |
| ⚙️ **Infrastructure** | Multi-stage Docker build, Docker Compose with MySQL 8.4 + Redis 7, healthcheck dependencies |
| ☁️ **Spring Cloud** | Eureka Service Registry + Spring Cloud Config Server, both Dockerised |
| 📄 **API Docs** | Swagger / OpenAPI UI with complete endpoint documentation |

`Java 21` `Spring Boot 3` `Spring Security 6` `JWT` `RBAC` `MySQL 8.4` `Redis 7` `Docker` `Spring Cloud` `Eureka` `Config Server` `SendGrid` `Swagger` `Lombok` `JPA`

---

### 🏫 SchoolAdmin Portal
> **Comprehensive Digital School Management System**

Full-featured school administration platform with role-based access for Admin, Staff, and Students.

- 📋 Built **student management, attendance tracking, and fee management** modules end-to-end
- 🔗 Integrated **Spring Boot REST APIs with Angular frontend** for real-time reactive data flow
- 🔐 Implemented **RBAC** with granular access levels per role (Admin / Staff / Student)
- ⚡ Wrote **optimized SQL queries** and resolved performance bottlenecks in data fetching

`Java` `Spring Boot` `Angular` `MySQL` `RBAC` `REST APIs`

---

### 📰 EveryDay News Portal
> **Full-Stack News Aggregation Platform** · [View on GitHub](https://github.com/amarenderreddyvoladri/EveryDay-News-Portal-Project)

Real-time news platform with category filtering, live feed integration, and responsive TypeScript frontend.

`TypeScript` `React.js` `REST API`

---

### 🧠 Quiz Portal
> **Interactive Quiz Application with Java Backend** · [View on GitHub](https://github.com/amarenderreddyvoladri/Quiz_Portal)

Dynamic question management, scoring engine, and session tracking with clean RESTful API architecture.

`Java` `Spring Boot` `MySQL`

---

## 🛠️ Tech Stack

### ☕ Backend
![Java](https://img.shields.io/badge/Java_21-ED8B00?style=flat-square&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot_3-6DB33F?style=flat-square&logo=spring-boot&logoColor=white)
![Spring Security](https://img.shields.io/badge/Spring_Security_6-6DB33F?style=flat-square&logo=springsecurity&logoColor=white)
![JWT](https://img.shields.io/badge/JWT-000000?style=flat-square&logo=jsonwebtokens&logoColor=white)
![REST APIs](https://img.shields.io/badge/REST_APIs-FF6C37?style=flat-square&logo=postman&logoColor=white)
![Hibernate](https://img.shields.io/badge/Hibernate_JPA-59666C?style=flat-square&logo=hibernate&logoColor=white)
![Maven](https://img.shields.io/badge/Maven-C71A36?style=flat-square&logo=apache-maven&logoColor=white)

### 🌐 Frontend
![Angular](https://img.shields.io/badge/Angular-DD0031?style=flat-square&logo=angular&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=flat-square&logo=typescript&logoColor=white)
![Angular Material](https://img.shields.io/badge/Angular_Material-009688?style=flat-square&logo=angular&logoColor=white)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white)

### 🗄️ Database & Messaging
![MySQL](https://img.shields.io/badge/MySQL_8.4-4479A1?style=flat-square&logo=mysql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis_7-DC382D?style=flat-square&logo=redis&logoColor=white)
![Apache Kafka](https://img.shields.io/badge/Apache_Kafka-231F20?style=flat-square&logo=apache-kafka&logoColor=white)

### ⚙️ DevOps & Architecture
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Spring Cloud](https://img.shields.io/badge/Spring_Cloud-6DB33F?style=flat-square&logo=spring&logoColor=white)
![Eureka](https://img.shields.io/badge/Eureka_Registry-6DB33F?style=flat-square&logo=spring&logoColor=white)
![Microservices](https://img.shields.io/badge/Microservices-00ff88?style=flat-square&logoColor=black)
![CI/CD](https://img.shields.io/badge/CI%2FCD-2088FF?style=flat-square&logo=github-actions&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white)
![Postman](https://img.shields.io/badge/Postman-FF6C37?style=flat-square&logo=postman&logoColor=white)
![Swagger](https://img.shields.io/badge/Swagger_OpenAPI-85EA2D?style=flat-square&logo=swagger&logoColor=black)

---

## 🌱 Currently Exploring

| Area | What I'm Learning |
|---|---|
| ☁️ AWS Cloud | EC2, S3, RDS — deploying Spring Boot microservices to production cloud |
| 🏗️ System Design | Scalability patterns, CAP theorem, distributed architecture, high availability |
| 📨 Kafka at Scale | Consumer groups, partitioning strategies, real-time stream processing |
| 🔒 Secure Coding | OWASP Top 10, OAuth 2.0, API hardening, vulnerability scanning |
| 🚀 Kubernetes | Container orchestration, Helm charts, auto-scaling |

---

## 📫 Let's Connect

<div align="center">

| | |
|---|---|
| 🌐 **Portfolio** | [amarenderreddyvoladri-portfolio.netlify.app](https://amarenderreddyvoladri-portfolio.netlify.app/) |
| 💼 **LinkedIn** | [linkedin.com/in/amarender-reddy-voladri](https://www.linkedin.com/in/amarender-reddy-voladri/) |
| 🐙 **GitHub** | [github.com/amarenderreddyvoladri](https://github.com/amarenderreddyvoladri) |
| 📍 **Location** | Hyderabad, India |

</div>

---

<div align="center">

*"First, solve the problem. Then, write the code."* — John Johnson

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:bf5fff,50:00cfff,100:00ff88&height=120&section=footer" />

</div>
