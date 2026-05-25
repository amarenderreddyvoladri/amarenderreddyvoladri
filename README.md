<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:00ff88,50:00cfff,100:bf5fff&height=220&section=header&text=Amarender%20Reddy%20Voladri&fontSize=44&fontColor=ffffff&fontAlignY=38&desc=Java%20Full%20Stack%20Developer%20%7C%20Spring%20Boot%20%7C%20Spring%20Security%206%20%7C%20JWT%20%2B%20RBAC%20%7C%20Microservices&descAlignY=58&descSize=15&descColor=d0ffe8" />

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
        "Spring Boot REST APIs",        "Spring Security 6 + JWT + RBAC",
        "Angular + TypeScript",          "Microservices Architecture",
        "MySQL + Hibernate/JPA",         "Docker + Kafka + Redis"
    };

    String philosophy  = "Secure · Scalable · Maintainable enterprise software.";
}
```

- 🏢 Built a **real-time enterprise HRMS platform** — employee onboarding, access control, attendance & approval workflows
- 🔐 Implemented **Spring Security 6 + JWT + RBAC** for multi-role access (Admin / HR / Employee) — stateless & scalable
- 🧩 Hands-on with **Microservices** — API Gateway, Eureka Service Registry, Docker, Kafka
- 🖥️ Contributed end-to-end: **Spring Boot APIs → Angular frontend → MySQL → CI/CD**
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

## 🔐 Spring Security 6 + JWT — Deep Dive

> **This is my primary area of expertise.** Below is the exact implementation pattern I use in enterprise HRMS projects.

### 🔄 Complete JWT Authentication Flow

```
┌──────────────────────────────────────────────────────────────────────────────┐
│                        JWT AUTHENTICATION FLOW                               │
├──────────────────────────────────────────────────────────────────────────────┤
│                                                                              │
│  STEP 1 ── Client sends credentials                                          │
│            POST /api/auth/login                                              │
│            Body: { "username": "admin@hrms.com", "password": "Pass@123" }   │
│                                    │                                         │
│                                    ▼                                         │
│  STEP 2 ── AuthenticationManager validates                                   │
│            → Delegates to UserDetailsService                                 │
│            → Loads user from DB                                              │
│            → BCryptPasswordEncoder.matches(rawPwd, hashedPwd)                │
│                                    │                                         │
│                                    ▼                                         │
│  STEP 3 ── JwtService generates tokens                                       │
│            → Access Token  (expires: 15 minutes)                             │
│            → Refresh Token (expires: 7 days)                                 │
│            → Signed with HMAC-SHA512 secret key                              │
│            → Claims: { sub, roles[], iat, exp }                              │
│                                    │                                         │
│                                    ▼                                         │
│  STEP 4 ── Client stores token, sends on every request                       │
│            Header: Authorization: Bearer <token>                             │
│                                    │                                         │
│                                    ▼                                         │
│  STEP 5 ── JwtAuthFilter (OncePerRequestFilter) intercepts                   │
│            → Extracts token from Authorization header                        │
│            → Validates signature + expiry                                    │
│            → Loads UserDetails, sets SecurityContextHolder                   │
│            → Stateless — NO HttpSession created                              │
│                                    │                                         │
│                                    ▼                                         │
│  STEP 6 ── @PreAuthorize enforces RBAC                                       │
│            → Checks roles from JWT claims                                    │
│            → Blocks unauthorized access BEFORE method executes               │
│                                                                              │
└──────────────────────────────────────────────────────────────────────────────┘
```

### ⚙️ SecurityFilterChain Configuration

```java
@Configuration
@EnableWebSecurity
@EnableMethodSecurity   // enables @PreAuthorize at method level
@RequiredArgsConstructor
public class SecurityConfig {

    private final JwtAuthFilter jwtAuthFilter;
    private final UserDetailsService userDetailsService;

    @Bean
    public SecurityFilterChain securityFilterChain(HttpSecurity http) throws Exception {
        http
            .csrf(csrf -> csrf.disable())                                      // stateless API — no CSRF
            .sessionManagement(session -> session
                .sessionCreationPolicy(SessionCreationPolicy.STATELESS))      // no sessions, JWT only
            .authorizeHttpRequests(auth -> auth
                .requestMatchers("/api/auth/**").permitAll()                   // login/register open
                .requestMatchers("/api/admin/**").hasRole("ADMIN")            // Admin only
                .requestMatchers("/api/hr/**").hasAnyRole("ADMIN", "HR")      // Admin + HR
                .requestMatchers("/api/employee/**").hasAnyRole("ADMIN", "HR", "EMPLOYEE")
                .anyRequest().authenticated()
            )
            .authenticationProvider(authenticationProvider())
            .addFilterBefore(jwtAuthFilter,
                UsernamePasswordAuthenticationFilter.class);                  // JWT filter before auth

        return http.build();
    }

    @Bean
    public AuthenticationProvider authenticationProvider() {
        DaoAuthenticationProvider provider = new DaoAuthenticationProvider();
        provider.setUserDetailsService(userDetailsService);
        provider.setPasswordEncoder(passwordEncoder());
        return provider;
    }

    @Bean
    public PasswordEncoder passwordEncoder() {
        return new BCryptPasswordEncoder(12);   // strength factor 12
    }

    @Bean
    public AuthenticationManager authenticationManager(AuthenticationConfiguration config)
            throws Exception {
        return config.getAuthenticationManager();
    }
}
```

### 🔑 JWT Token Structure & Generation

```
JWT = Base64(Header) . Base64(Payload) . HMAC-SHA512-Signature
       ─────────────   ───────────────   ────────────────────────
       eyJhbGciOi...   eyJzdWIiOiJhZ...  HMACSHA512(secret)

HEADER  → { "alg": "HS512", "typ": "JWT" }
PAYLOAD → { "sub": "admin@hrms.com",
             "roles": ["ROLE_ADMIN"],
             "iat": 1717600000,
             "exp": 1717600900  }   ← 15 min expiry
```

```java
@Service
public class JwtService {

    @Value("${jwt.secret}")
    private String secretKey;

    private static final long ACCESS_TOKEN_EXPIRY  = 1000 * 60 * 15;     // 15 min
    private static final long REFRESH_TOKEN_EXPIRY = 1000 * 60 * 60 * 24 * 7; // 7 days

    // Generate Access Token with roles claim
    public String generateAccessToken(UserDetails userDetails) {
        Map<String, Object> claims = new HashMap<>();
        claims.put("roles", userDetails.getAuthorities().stream()
                .map(GrantedAuthority::getAuthority)
                .collect(Collectors.toList()));

        return Jwts.builder()
                .setClaims(claims)
                .setSubject(userDetails.getUsername())
                .setIssuedAt(new Date())
                .setExpiration(new Date(System.currentTimeMillis() + ACCESS_TOKEN_EXPIRY))
                .signWith(getSigningKey(), SignatureAlgorithm.HS512)
                .compact();
    }

    // Validate token — checks signature + expiry
    public boolean isTokenValid(String token, UserDetails userDetails) {
        final String username = extractUsername(token);
        return username.equals(userDetails.getUsername()) && !isTokenExpired(token);
    }

    private Key getSigningKey() {
        return Keys.hmacShaKeyFor(Decoders.BASE64.decode(secretKey));
    }

    private boolean isTokenExpired(String token) {
        return extractExpiration(token).before(new Date());
    }

    public String extractUsername(String token) {
        return extractClaim(token, Claims::getSubject);
    }

    public <T> T extractClaim(String token, Function<Claims, T> claimsResolver) {
        final Claims claims = Jwts.parserBuilder()
                .setSigningKey(getSigningKey()).build()
                .parseClaimsJws(token).getBody();
        return claimsResolver.apply(claims);
    }
}
```

### 🚦 JwtAuthFilter — Intercepts Every Request

```java
@Component
@RequiredArgsConstructor
public class JwtAuthFilter extends OncePerRequestFilter {

    private final JwtService jwtService;
    private final UserDetailsService userDetailsService;

    @Override
    protected void doFilterInternal(HttpServletRequest request,
                                    HttpServletResponse response,
                                    FilterChain filterChain)
            throws ServletException, IOException {

        final String authHeader = request.getHeader("Authorization");

        // Skip if no Bearer token present
        if (authHeader == null || !authHeader.startsWith("Bearer ")) {
            filterChain.doFilter(request, response);
            return;
        }

        final String jwt = authHeader.substring(7);   // strip "Bearer "
        final String userEmail = jwtService.extractUsername(jwt);

        // Only authenticate if not already authenticated
        if (userEmail != null &&
            SecurityContextHolder.getContext().getAuthentication() == null) {

            UserDetails userDetails = userDetailsService.loadUserByUsername(userEmail);

            if (jwtService.isTokenValid(jwt, userDetails)) {
                // Build authentication token and set in SecurityContext
                UsernamePasswordAuthenticationToken authToken =
                    new UsernamePasswordAuthenticationToken(
                        userDetails, null, userDetails.getAuthorities());

                authToken.setDetails(
                    new WebAuthenticationDetailsSource().buildDetails(request));

                SecurityContextHolder.getContext().setAuthentication(authToken);
            }
        }
        filterChain.doFilter(request, response);
    }
}
```

---

## 🛡️ RBAC — Role-Based Access Control (Deep Dive)

### Role Hierarchy & Permissions Matrix

| Endpoint / Resource | `ROLE_ADMIN` | `ROLE_HR` | `ROLE_EMPLOYEE` |
|---|---|---|---|
| `POST /employees/onboard` | ✅ Full Access | ✅ Full Access | ❌ Denied |
| `GET /employees` (all) | ✅ Full Access | ✅ Full Access | ❌ Denied |
| `GET /employees/{id}` | ✅ Any Employee | ✅ Any Employee | ✅ Self Only |
| `PUT /employees/{id}` | ✅ Any Employee | ✅ Any Employee | ⚠️ Self Only |
| `DELETE /employees/{id}` | ✅ Full Access | ❌ Denied | ❌ Denied |
| `GET /attendance` (all) | ✅ Full Access | ✅ Full Access | ❌ Denied |
| `POST /attendance/mark` | ✅ Full Access | ✅ Full Access | ✅ Self Only |
| `GET /salary/{id}` | ✅ Any | ✅ Any | ✅ Self Only |
| `POST /salary/process` | ✅ Full Access | ⚠️ Limited | ❌ Denied |
| `GET /reports` | ✅ All Reports | ⚠️ HR Reports | ⚠️ Personal Only |
| `GET /system/config` | ✅ Full Access | ❌ Denied | ❌ Denied |

> ✅ Full Access &nbsp;|&nbsp; ⚠️ Limited/Conditional &nbsp;|&nbsp; ❌ Denied

### RBAC Implementation — Controller Level

```java
// ─── ADMIN ONLY ───────────────────────────────────────────────────────────────
@RestController
@RequestMapping("/api/admin")
@PreAuthorize("hasRole('ADMIN')")   // applies to all methods in this controller
public class AdminController {

    @GetMapping("/system/config")
    public ResponseEntity<SystemConfig> getSystemConfig() { ... }

    @DeleteMapping("/employees/{id}")
    public ResponseEntity<Void> deleteEmployee(@PathVariable Long id) { ... }
}

// ─── HR + ADMIN ───────────────────────────────────────────────────────────────
@RestController
@RequestMapping("/api/hr")
public class HRController {

    @PostMapping("/employees/onboard")
    @PreAuthorize("hasAnyRole('ADMIN', 'HR')")
    public ResponseEntity<EmployeeDTO> onboardEmployee(
            @RequestBody @Valid EmployeeRequest request) { ... }

    @GetMapping("/employees")
    @PreAuthorize("hasAnyRole('ADMIN', 'HR')")
    public ResponseEntity<List<EmployeeDTO>> getAllEmployees() { ... }

    @GetMapping("/reports/hr")
    @PreAuthorize("hasAnyRole('ADMIN', 'HR')")
    public ResponseEntity<HRReport> getHRReport() { ... }
}

// ─── EMPLOYEE — SELF-ACCESS PATTERN ──────────────────────────────────────────
@RestController
@RequestMapping("/api/employee")
public class EmployeeController {

    // Employee can only view their OWN salary
    @GetMapping("/{id}/salary")
    @PreAuthorize("hasAnyRole('ADMIN','HR') or #id == authentication.principal.id")
    public ResponseEntity<SalaryDTO> getSalary(@PathVariable Long id) { ... }

    // Employee can only update their OWN profile
    @PutMapping("/{id}/profile")
    @PreAuthorize("hasAnyRole('ADMIN','HR') or #id == authentication.principal.id")
    public ResponseEntity<EmployeeDTO> updateProfile(
            @PathVariable Long id,
            @RequestBody ProfileUpdateRequest request) { ... }
}
```

### User Entity & Roles Setup

```java
@Entity
@Table(name = "users")
public class User implements UserDetails {

    @Id @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @Column(unique = true, nullable = false)
    private String email;

    @Column(nullable = false)
    private String password;   // BCrypt hashed

    @Enumerated(EnumType.STRING)
    private Role role;   // ADMIN | HR | EMPLOYEE

    @Override
    public Collection<? extends GrantedAuthority> getAuthorities() {
        return List.of(new SimpleGrantedAuthority("ROLE_" + role.name()));
    }

    @Override public boolean isAccountNonExpired()  { return true; }
    @Override public boolean isAccountNonLocked()   { return true; }
    @Override public boolean isCredentialsNonExpired(){ return true; }
    @Override public boolean isEnabled()             { return true; }
}

public enum Role { ADMIN, HR, EMPLOYEE }
```

---

## 🛠️ Tech Stack

### ☕ Backend
![Java](https://img.shields.io/badge/Java-ED8B00?style=flat-square&logo=openjdk&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=flat-square&logo=spring-boot&logoColor=white)
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
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white)
![Apache Kafka](https://img.shields.io/badge/Apache_Kafka-231F20?style=flat-square&logo=apache-kafka&logoColor=white)

### ⚙️ DevOps & Architecture
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Microservices](https://img.shields.io/badge/Microservices-00ff88?style=flat-square&logoColor=black)
![API Gateway](https://img.shields.io/badge/API_Gateway-FF9900?style=flat-square&logo=amazonaws&logoColor=white)
![Eureka](https://img.shields.io/badge/Eureka_Registry-6DB33F?style=flat-square&logo=spring&logoColor=white)
![CI/CD](https://img.shields.io/badge/CI%2FCD-2088FF?style=flat-square&logo=github-actions&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white)
![Postman](https://img.shields.io/badge/Postman-FF6C37?style=flat-square&logo=postman&logoColor=white)
![Swagger](https://img.shields.io/badge/Swagger_OpenAPI-85EA2D?style=flat-square&logo=swagger&logoColor=black)

---

## 🏗️ Microservices Architecture (HRMS)

```
┌─────────────────────────────────────────────────────────────────────────┐
│                         ANGULAR SPA (Frontend)                          │
│              Reactive Forms · HttpClient · Angular Material             │
└──────────────────────────────┬──────────────────────────────────────────┘
                               │  HTTPS
                               ▼
┌─────────────────────────────────────────────────────────────────────────┐
│                           API GATEWAY                                   │
│          Routing · JWT Validation · Rate Limiting · CORS                │
└──────┬──────────────┬──────────────┬───────────────┬────────────────────┘
       │              │              │               │
       ▼              ▼              ▼               ▼
┌────────────┐ ┌────────────┐ ┌───────────┐ ┌──────────────────┐
│   AUTH     │ │  EMPLOYEE  │ │ATTENDANCE │ │  NOTIFICATION    │
│  SERVICE   │ │  SERVICE   │ │  SERVICE  │ │    SERVICE       │
│            │ │            │ │           │ │                  │
│ JWT Issue  │ │ Onboarding │ │ Check-in  │ │ Kafka Consumer   │
│ BCrypt     │ │ Profiles   │ │ Leave Mgmt│ │ Email Alerts     │
│ RBAC       │ │ Role Assign│ │ Kafka Pub │ │ Async Events     │
└────────────┘ └────────────┘ └───────────┘ └──────────────────┘
       │              │              │               │
       └──────────────┴──────────────┴───────────────┘
                               │
       ┌───────────────────────┼───────────────────────┐
       ▼                       ▼                       ▼
┌────────────┐         ┌──────────────┐       ┌──────────────┐
│   MySQL    │         │    REDIS     │       │    KAFKA     │
│  Database  │         │    Cache     │       │    Broker    │
│            │         │              │       │              │
│ Persistent │         │ Token Store  │       │ Event Stream │
│ Hibernate  │         │ Session Cache│       │ Pub / Sub    │
└────────────┘         └──────────────┘       └──────────────┘
                               │
                    ┌──────────┘
                    ▼
           ┌─────────────────┐
           │ EUREKA REGISTRY │
           │ Service Discover│
           │ Health Checks   │
           └─────────────────┘
```

---

## 💼 Work Experience

### 🏢 Software Engineer Associate — Enterprise HRMS Platform
> *Real-time enterprise application · Employee Lifecycle & Workforce Operations*

**Key Contributions:**

- 🔧 Developed and maintained **RESTful APIs** using Java & Spring Boot for onboarding workflows, employee profile management, role assignment, approval processes, and real-time status tracking

- 🔐 Implemented **Spring Security 6 + JWT + RBAC** for Admin, HR, and Employee module access control — stateless, secure, and scalable with refresh token rotation

- 🖥️ Built **Angular frontend** with Reactive Forms, TypeScript, and Angular Material — dynamic forms, validations, dashboards, and user interaction workflows

- 🗄️ Used **Hibernate/JPA + MySQL** for CRUD operations, entity mapping, lazy/eager loading, and optimized queries to improve data handling efficiency

- 🧩 Worked with **Microservices architecture** — API Gateway and Eureka Service Registry for service communication and centralized routing

- 🐳 Gained hands-on exposure to **Docker containerization, Redis caching, Kafka event communication**, Git, and CI/CD deployment workflows

- 🔄 Collaborated in **Agile Scrum** — daily stand-ups, sprint planning, code reviews, bug fixes, and release cycles

- 🐛 Debugged production issues, performed **Postman API testing**, wrote Swagger/OpenAPI docs, and supported stable deployment activities

`Java` `Spring Boot` `Spring Security 6` `JWT` `RBAC` `Angular` `TypeScript` `Reactive Forms` `Hibernate` `JPA` `MySQL` `Microservices` `API Gateway` `Eureka` `Docker` `Redis` `Kafka` `CI/CD` `Swagger`

---

## 🚀 Featured Projects

### 🔐 Enterprise Spring Security Template
> **Production-Ready Authentication & Authorization Microservice**

A reusable enterprise-grade Spring Security template simulating real-world security systems used in HRMS, fintech, and SaaS applications.

| Feature | Implementation |
|---|---|
| 🔑 Authentication | JWT Access Token (15min) + Refresh Token (7d) + BCrypt password hashing |
| 🛡️ Authorization | RBAC + `@PreAuthorize` endpoint-level protection + stateless session management |
| 🔄 Token Rotation | Refresh token endpoint + token blacklisting via Redis |
| 🏗️ Clean Architecture | Controller → Service → Repository → DTO → Global Exception Handler |
| 📄 API Docs | Swagger / OpenAPI — auto-generated developer documentation |
| 🐳 Containerization | Docker Compose + environment-based dev/prod configuration profiles |
| ⚡ Scalability | Redis caching + Kafka-based event communication patterns |

`Java` `Spring Boot 3` `Spring Security 6` `JWT` `RBAC` `MySQL` `Hibernate` `Docker` `Redis` `Kafka` `Swagger` `CI/CD`

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

## 🌱 Currently Exploring

| Area | What I'm Learning |
|---|---|
| ☁️ AWS Cloud | EC2, S3, RDS — deploying Spring Boot microservices to production cloud |
| 🏗️ System Design | Scalability patterns, CAP theorem, distributed architecture, high availability |
| 📨 Kafka at Scale | Consumer groups, partitioning strategies, real-time stream processing |
| 🔒 Secure Coding | OWASP Top 10, OAuth 2.0, API hardening, vulnerability scanning |

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
