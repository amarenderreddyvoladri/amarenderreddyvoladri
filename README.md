<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8"/>
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;700&family=Space+Grotesk:wght@300;400;500;600;700&display=swap" rel="stylesheet"/>
<style>
*{margin:0;padding:0;box-sizing:border-box}
:root{
  --neon-green:#00ff88;--neon-blue:#00cfff;--neon-purple:#bf5fff;--neon-orange:#ff8c00;--neon-pink:#ff4da6;
  --dark:#060b14;--dark2:#0d1526;--dark3:#111c30;--card:#0a1628;--border:rgba(0,255,136,0.15);
  --text:#e2eaf7;--muted:#6b82a8;--font:'Space Grotesk',sans-serif;--mono:'JetBrains Mono',monospace;
}
html{scroll-behavior:smooth}
body{background:var(--dark);color:var(--text);font-family:var(--font);overflow-x:hidden;min-height:100vh}

/* Animated BG */
.bg-canvas{position:fixed;top:0;left:0;width:100%;height:100%;z-index:0;pointer-events:none}
.particle{position:absolute;width:2px;height:2px;border-radius:50%;animation:float linear infinite}
@keyframes float{0%{opacity:0;transform:translateY(100vh) translateX(0)}10%{opacity:1}90%{opacity:0.3}100%{opacity:0;transform:translateY(-10vh) translateX(var(--dx))}}

.container{position:relative;z-index:1;max-width:900px;margin:0 auto;padding:20px}

/* HERO */
.hero{text-align:center;padding:60px 20px 40px;position:relative}
.hero-badge{display:inline-flex;align-items:center;gap:8px;background:rgba(0,255,136,0.08);border:1px solid rgba(0,255,136,0.3);border-radius:999px;padding:6px 16px;font-size:12px;color:var(--neon-green);letter-spacing:1px;text-transform:uppercase;margin-bottom:24px;animation:fadeInDown 0.8s ease both}
.pulse-dot{width:8px;height:8px;border-radius:50%;background:var(--neon-green);animation:pulse 2s ease infinite}
@keyframes pulse{0%,100%{box-shadow:0 0 0 0 rgba(0,255,136,0.5)}50%{box-shadow:0 0 0 6px rgba(0,255,136,0)}}

.hero h1{font-size:clamp(28px,5vw,52px);font-weight:700;line-height:1.1;margin-bottom:16px;animation:fadeInDown 0.9s ease 0.1s both}
.hero h1 span{background:linear-gradient(135deg,var(--neon-green),var(--neon-blue));-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text}
.hero-sub{font-size:clamp(13px,2vw,17px);color:var(--muted);margin-bottom:32px;animation:fadeInDown 1s ease 0.2s both;line-height:1.6}
.hero-sub strong{color:var(--neon-blue)}

.badge-row{display:flex;flex-wrap:wrap;justify-content:center;gap:8px;margin-bottom:32px;animation:fadeInUp 1s ease 0.3s both}
.badge{display:inline-flex;align-items:center;gap:6px;padding:6px 14px;border-radius:8px;font-size:12px;font-weight:500;border:1px solid;cursor:default;transition:transform 0.2s,box-shadow 0.2s}
.badge:hover{transform:translateY(-2px)}
.b-green{background:rgba(0,255,136,0.08);border-color:rgba(0,255,136,0.3);color:var(--neon-green)}
.b-blue{background:rgba(0,207,255,0.08);border-color:rgba(0,207,255,0.3);color:var(--neon-blue)}
.b-purple{background:rgba(191,95,255,0.08);border-color:rgba(191,95,255,0.3);color:var(--neon-purple)}
.b-orange{background:rgba(255,140,0,0.08);border-color:rgba(255,140,0,0.3);color:var(--neon-orange)}
.b-pink{background:rgba(255,77,166,0.08);border-color:rgba(255,77,166,0.3);color:var(--neon-pink)}

/* Code block */
.code-hero{background:var(--card);border:1px solid var(--border);border-radius:16px;padding:24px;text-align:left;font-family:var(--mono);font-size:13px;line-height:1.8;animation:fadeInUp 1s ease 0.4s both;position:relative;overflow:hidden}
.code-hero::before{content:'';position:absolute;top:0;left:0;right:0;height:3px;background:linear-gradient(90deg,var(--neon-green),var(--neon-blue),var(--neon-purple))}
.code-bar{display:flex;align-items:center;gap:6px;margin-bottom:16px;padding-bottom:12px;border-bottom:1px solid rgba(255,255,255,0.06)}
.dot{width:12px;height:12px;border-radius:50%}
.d-red{background:#ff5f56}.d-yellow{background:#ffbd2e}.d-green{background:#27c93f}
.code-bar span{margin-left:8px;font-size:11px;color:var(--muted)}
.kw{color:#bf5fff}.cls{color:#00cfff}.str{color:#00ff88}.cmt{color:#4a6285}.prop{color:#ff8c00}.val{color:#ff4da6}

/* SECTION */
.section{margin:48px 0}
.section-title{display:flex;align-items:center;gap:12px;margin-bottom:24px;font-size:20px;font-weight:700}
.section-title::after{content:'';flex:1;height:1px;background:linear-gradient(90deg,rgba(0,255,136,0.3),transparent)}
.section-icon{width:36px;height:36px;border-radius:10px;display:flex;align-items:center;justify-content:center;font-size:18px;flex-shrink:0}
.si-green{background:rgba(0,255,136,0.12);border:1px solid rgba(0,255,136,0.25)}
.si-blue{background:rgba(0,207,255,0.12);border:1px solid rgba(0,207,255,0.25)}
.si-purple{background:rgba(191,95,255,0.12);border:1px solid rgba(191,95,255,0.25)}
.si-orange{background:rgba(255,140,0,0.12);border:1px solid rgba(255,140,0,0.25)}

/* CARDS */
.card{background:var(--card);border:1px solid rgba(255,255,255,0.06);border-radius:16px;padding:24px;transition:transform 0.25s,border-color 0.25s,box-shadow 0.25s}
.card:hover{transform:translateY(-3px);border-color:rgba(0,255,136,0.2);box-shadow:0 8px 32px rgba(0,255,136,0.06)}
.card-grid{display:grid;gap:16px}
.card-grid-2{grid-template-columns:repeat(auto-fit,minmax(280px,1fr))}
.card-grid-3{grid-template-columns:repeat(auto-fit,minmax(200px,1fr))}

/* PROJECT CARD */
.proj-card{background:var(--card);border-radius:16px;overflow:hidden;transition:transform 0.25s,box-shadow 0.25s;position:relative}
.proj-card:hover{transform:translateY(-4px);box-shadow:0 16px 48px rgba(0,0,0,0.4)}
.proj-header{padding:20px 24px 16px;border-bottom:1px solid rgba(255,255,255,0.05);position:relative}
.proj-glow{position:absolute;top:0;left:0;right:0;height:3px}
.proj-name{font-size:16px;font-weight:700;margin-bottom:6px}
.proj-desc{font-size:13px;color:var(--muted);line-height:1.5}
.proj-body{padding:20px 24px}
.proj-features{list-style:none;display:flex;flex-direction:column;gap:8px}
.proj-features li{display:flex;align-items:flex-start;gap:10px;font-size:13px;color:#c5d1e8}
.feat-icon{width:20px;height:20px;border-radius:6px;display:flex;align-items:center;justify-content:center;font-size:11px;flex-shrink:0;margin-top:1px}
.proj-tags{display:flex;flex-wrap:wrap;gap:6px;padding:0 24px 20px}
.tag{font-size:11px;padding:3px 10px;border-radius:6px;font-family:var(--mono);border:1px solid}

/* TECH GRID */
.tech-item{display:flex;flex-direction:column;align-items:center;gap:10px;padding:20px 12px;background:var(--card);border:1px solid rgba(255,255,255,0.06);border-radius:14px;transition:all 0.25s;cursor:default}
.tech-item:hover{border-color:var(--accent-color,rgba(0,255,136,0.3));box-shadow:0 4px 20px rgba(0,255,136,0.06);transform:translateY(-2px)}
.tech-icon{width:44px;height:44px;border-radius:12px;display:flex;align-items:center;justify-content:center;font-size:22px}
.tech-name{font-size:12px;font-weight:600;text-align:center;color:var(--text)}
.tech-level{width:100%;height:3px;background:rgba(255,255,255,0.06);border-radius:999px;overflow:hidden}
.tech-bar{height:100%;border-radius:999px;animation:barIn 1.5s ease both}
@keyframes barIn{from{width:0}to{width:var(--w)}}

/* JWT/RBAC DEEP DIVE */
.flow-container{background:var(--card);border:1px solid rgba(0,207,255,0.15);border-radius:16px;padding:24px;overflow:hidden}
.flow-title{font-size:14px;font-weight:600;color:var(--neon-blue);margin-bottom:20px;display:flex;align-items:center;gap:8px}
.flow-steps{display:flex;flex-direction:column;gap:0}
.flow-step{display:flex;gap:16px;position:relative}
.flow-step:not(:last-child)::after{content:'';position:absolute;left:18px;top:36px;width:1px;height:calc(100% - 12px);background:linear-gradient(to bottom,rgba(0,207,255,0.3),transparent)}
.step-num{width:36px;height:36px;border-radius:10px;display:flex;align-items:center;justify-content:center;font-size:12px;font-weight:700;flex-shrink:0;font-family:var(--mono)}
.step-content{flex:1;padding-bottom:20px}
.step-title{font-size:14px;font-weight:600;margin-bottom:4px}
.step-desc{font-size:12px;color:var(--muted);line-height:1.5}
.step-code{background:rgba(0,0,0,0.4);border-radius:8px;padding:10px 14px;font-family:var(--mono);font-size:11px;color:#a8c8f8;margin-top:8px;border-left:2px solid rgba(0,207,255,0.4);line-height:1.7}

/* RBAC TABLE */
.rbac-table{width:100%;border-collapse:collapse;font-size:13px}
.rbac-table th{padding:10px 14px;text-align:left;font-weight:600;font-size:12px;text-transform:uppercase;letter-spacing:0.5px;color:var(--muted);border-bottom:1px solid rgba(255,255,255,0.06)}
.rbac-table td{padding:12px 14px;border-bottom:1px solid rgba(255,255,255,0.04);vertical-align:top}
.rbac-table tr:last-child td{border-bottom:none}
.role-badge{display:inline-flex;align-items:center;gap:5px;padding:3px 10px;border-radius:6px;font-size:11px;font-weight:600;font-family:var(--mono)}
.perm-cell{display:flex;flex-wrap:wrap;gap:4px}
.perm{display:inline-block;padding:2px 8px;border-radius:4px;font-size:10px;font-family:var(--mono)}
.p-yes{background:rgba(0,255,136,0.1);color:var(--neon-green);border:1px solid rgba(0,255,136,0.2)}
.p-no{background:rgba(255,77,166,0.08);color:#ff4da6;border:1px solid rgba(255,77,166,0.15)}
.p-partial{background:rgba(255,140,0,0.1);color:var(--neon-orange);border:1px solid rgba(255,140,0,0.2)}

/* SKILL BARS */
.skill-row{display:flex;align-items:center;gap:12px;margin-bottom:12px}
.skill-label{min-width:130px;font-size:13px;color:var(--text)}
.skill-track{flex:1;height:6px;background:rgba(255,255,255,0.06);border-radius:999px;overflow:hidden}
.skill-fill{height:100%;border-radius:999px;animation:barIn 1.8s ease both}
.skill-pct{min-width:34px;font-size:12px;color:var(--muted);font-family:var(--mono);text-align:right}

/* STATS */
.stat-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(140px,1fr));gap:12px}
.stat-card{background:var(--card);border:1px solid rgba(255,255,255,0.06);border-radius:12px;padding:18px 16px;text-align:center;transition:all 0.25s}
.stat-card:hover{border-color:var(--sc,rgba(0,255,136,0.3));transform:translateY(-2px)}
.stat-num{font-size:28px;font-weight:700;font-family:var(--mono);background:linear-gradient(135deg,var(--ca),var(--cb));-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text}
.stat-label{font-size:11px;color:var(--muted);margin-top:4px;text-transform:uppercase;letter-spacing:0.5px}

/* TIMELINE */
.timeline{position:relative;padding-left:24px}
.timeline::before{content:'';position:absolute;left:6px;top:0;bottom:0;width:1px;background:linear-gradient(to bottom,var(--neon-green),transparent)}
.tl-item{position:relative;margin-bottom:24px}
.tl-dot{position:absolute;left:-24px;top:4px;width:14px;height:14px;border-radius:50%;border:2px solid var(--neon-green);background:var(--dark);z-index:1}
.tl-dot::after{content:'';position:absolute;inset:2px;border-radius:50%;background:var(--neon-green)}
.tl-title{font-size:15px;font-weight:700;margin-bottom:4px}
.tl-subtitle{font-size:12px;color:var(--neon-green);margin-bottom:8px;font-family:var(--mono)}
.tl-list{list-style:none;display:flex;flex-direction:column;gap:5px}
.tl-list li{font-size:13px;color:#c5d1e8;padding-left:16px;position:relative;line-height:1.5}
.tl-list li::before{content:'▸';position:absolute;left:0;color:var(--neon-green);font-size:10px;top:2px}

/* ANIMATIONS */
@keyframes fadeInDown{from{opacity:0;transform:translateY(-20px)}to{opacity:1;transform:translateY(0)}}
@keyframes fadeInUp{from{opacity:0;transform:translateY(20px)}to{opacity:1;transform:translateY(0)}}
@keyframes shimmer{0%{background-position:-200% center}100%{background-position:200% center}}
@keyframes borderGlow{0%,100%{border-color:rgba(0,255,136,0.1)}50%{border-color:rgba(0,255,136,0.4)}}
@keyframes typing{from{width:0}to{width:100%}}
@keyframes blink{0%,100%{opacity:1}50%{opacity:0}}
.cursor::after{content:'|';animation:blink 1s step-end infinite;color:var(--neon-green)}

/* GITHUB CONTRIB MAP */
.contrib-grid{display:grid;grid-template-columns:repeat(52,1fr);gap:2px}
.c-cell{width:100%;aspect-ratio:1;border-radius:2px;background:rgba(255,255,255,0.04)}
.c-l1{background:rgba(0,255,136,0.15)}
.c-l2{background:rgba(0,255,136,0.35)}
.c-l3{background:rgba(0,255,136,0.6)}
.c-l4{background:rgba(0,255,136,0.9)}

/* CONNECT */
.connect-grid{display:grid;grid-template-columns:repeat(auto-fit,minmax(180px,1fr));gap:12px}
.connect-card{display:flex;align-items:center;gap:14px;padding:16px 20px;background:var(--card);border:1px solid rgba(255,255,255,0.06);border-radius:14px;transition:all 0.25s;text-decoration:none;color:var(--text)}
.connect-card:hover{transform:translateY(-2px);border-color:rgba(0,207,255,0.3);box-shadow:0 8px 24px rgba(0,207,255,0.06)}
.connect-icon{width:40px;height:40px;border-radius:12px;display:flex;align-items:center;justify-content:center;font-size:20px;flex-shrink:0}
.connect-label{font-size:11px;color:var(--muted);text-transform:uppercase;letter-spacing:0.5px}
.connect-val{font-size:13px;font-weight:600}

/* SECURITY ARCH */
.arch-row{display:flex;align-items:stretch;gap:8px;margin-bottom:8px;flex-wrap:wrap}
.arch-box{flex:1;min-width:120px;background:rgba(0,0,0,0.3);border-radius:10px;padding:12px 14px;border:1px solid rgba(255,255,255,0.06);position:relative;transition:all 0.25s}
.arch-box:hover{border-color:rgba(0,255,136,0.3)}
.arch-box-title{font-size:11px;font-weight:700;text-transform:uppercase;letter-spacing:0.5px;margin-bottom:4px}
.arch-box-desc{font-size:11px;color:var(--muted);line-height:1.4}
.arch-arrow{display:flex;align-items:center;justify-content:center;color:var(--muted);font-size:18px;flex-shrink:0;align-self:center}

/* Scrollbar */
::-webkit-scrollbar{width:6px}
::-webkit-scrollbar-track{background:var(--dark)}
::-webkit-scrollbar-thumb{background:rgba(0,255,136,0.2);border-radius:3px}
</style>

<div class="bg-canvas" id="bgCanvas"></div>

<div class="container">

<!-- HERO -->
<div class="hero">
  <div class="hero-badge"><span class="pulse-dot"></span> Available for Opportunities</div>
  <h1>Amarender <span>Reddy</span> Voladri</h1>
  <p class="hero-sub">
    <strong>Java Full Stack Developer</strong> · Spring Boot · Angular · Microservices<br/>
    Building secure, scalable enterprise systems with precision
  </p>

  <div class="badge-row">
    <span class="badge b-green">☕ Spring Boot</span>
    <span class="badge b-blue">🔐 JWT + RBAC</span>
    <span class="badge b-purple">🅰 Angular</span>
    <span class="badge b-orange">🐳 Docker</span>
    <span class="badge b-pink">⚡ Kafka</span>
    <span class="badge b-green">🗄 MySQL</span>
    <span class="badge b-blue">🛡 Spring Security 6</span>
    <span class="badge b-orange">☁ Microservices</span>
  </div>

  <div class="code-hero">
    <div class="code-bar">
      <div class="dot d-red"></div><div class="dot d-yellow"></div><div class="dot d-green"></div>
      <span>AmarenderReddyVoladri.java</span>
    </div>
    <div>
      <span class="kw">public class</span> <span class="cls">AmarenderReddyVoladri</span> {<br/>
      &nbsp;&nbsp;<span class="kw">private final</span> <span class="cls">String</span> <span class="prop">role</span> = <span class="str">"Software Engineer Associate | Java Full Stack Developer"</span>;<br/>
      &nbsp;&nbsp;<span class="kw">private final</span> <span class="cls">String</span> <span class="prop">edu</span>&nbsp;&nbsp; = <span class="str">"MCA — Master of Computer Applications (2024)"</span>;<br/>
      &nbsp;&nbsp;<span class="kw">private final</span> <span class="cls">String</span> <span class="prop">exp</span>&nbsp;&nbsp; = <span class="str">"1+ Year · Enterprise HRMS · Microservices"</span>;<br/>
      &nbsp;&nbsp;<span class="kw">private final</span> <span class="cls">String</span> <span class="prop">loc</span>&nbsp;&nbsp; = <span class="str">"Hyderabad, India 🇮🇳"</span>;<br/><br/>
      &nbsp;&nbsp;<span class="cmt">// Core Expertise</span><br/>
      &nbsp;&nbsp;<span class="kw">private final</span> <span class="cls">String[]</span> <span class="prop">stack</span> = {<br/>
      &nbsp;&nbsp;&nbsp;&nbsp;<span class="str">"Spring Boot + Spring Security 6"</span>, <span class="str">"JWT + RBAC"</span>,<br/>
      &nbsp;&nbsp;&nbsp;&nbsp;<span class="str">"Angular + TypeScript"</span>, <span class="str">"Microservices Architecture"</span>,<br/>
      &nbsp;&nbsp;&nbsp;&nbsp;<span class="str">"MySQL + Hibernate/JPA"</span>, <span class="str">"Docker + Kafka + Redis"</span><br/>
      &nbsp;&nbsp;};<br/><br/>
      &nbsp;&nbsp;<span class="cmt">// Philosophy</span><br/>
      &nbsp;&nbsp;<span class="kw">public</span> <span class="cls">String</span> <span class="prop">goal</span>() {<br/>
      &nbsp;&nbsp;&nbsp;&nbsp;<span class="kw">return</span> <span class="str">"Secure · Scalable · Maintainable enterprise software"</span>;<br/>
      &nbsp;&nbsp;}<br/>
      }
    </div>
  </div>
</div>

<!-- STATS -->
<div class="section">
  <div class="stat-grid">
    <div class="stat-card" style="--sc:rgba(0,255,136,0.3);--ca:#00ff88;--cb:#00cfff">
      <div class="stat-num">1+</div><div class="stat-label">Years Experience</div>
    </div>
    <div class="stat-card" style="--sc:rgba(0,207,255,0.3);--ca:#00cfff;--cb:#bf5fff">
      <div class="stat-num">15+</div><div class="stat-label">Technologies</div>
    </div>
    <div class="stat-card" style="--sc:rgba(191,95,255,0.3);--ca:#bf5fff;--cb:#ff4da6">
      <div class="stat-num">4+</div><div class="stat-label">Projects Built</div>
    </div>
    <div class="stat-card" style="--sc:rgba(255,140,0,0.3);--ca:#ff8c00;--cb:#ff4da6">
      <div class="stat-num">100%</div><div class="stat-label">Open to Work</div>
    </div>
  </div>
</div>

<!-- DEEP DIVE: JWT AUTH FLOW -->
<div class="section">
  <div class="section-title"><div class="section-icon si-blue">🔐</div> JWT Authentication — Deep Dive</div>

  <div class="card-grid card-grid-2" style="margin-bottom:16px">
    <div class="flow-container">
      <div class="flow-title">🔑 Authentication Flow (Step-by-Step)</div>
      <div class="flow-steps">
        <div class="flow-step">
          <div class="step-num" style="background:rgba(0,255,136,0.1);border:1px solid rgba(0,255,136,0.3);color:var(--neon-green)">01</div>
          <div class="step-content">
            <div class="step-title" style="color:#e2eaf7">Client Sends Credentials</div>
            <div class="step-desc">POST /auth/login with username + password in request body (HTTPS only)</div>
            <div class="step-code">POST /api/auth/login<br/>{"username": "admin@hrms.com",<br/> "password": "securePass@123"}</div>
          </div>
        </div>
        <div class="flow-step">
          <div class="step-num" style="background:rgba(0,207,255,0.1);border:1px solid rgba(0,207,255,0.3);color:var(--neon-blue)">02</div>
          <div class="step-content">
            <div class="step-title" style="color:#e2eaf7">AuthenticationManager Validates</div>
            <div class="step-desc">Spring Security's AuthManager delegates to UserDetailsService — loads user, verifies BCrypt hash</div>
            <div class="step-code">authManager.authenticate(<br/>  new UsernamePasswordAuthToken(<br/>    username, password))</div>
          </div>
        </div>
        <div class="flow-step">
          <div class="step-num" style="background:rgba(191,95,255,0.1);border:1px solid rgba(191,95,255,0.3);color:var(--neon-purple)">03</div>
          <div class="step-content">
            <div class="step-title" style="color:#e2eaf7">JWT Token Generated</div>
            <div class="step-desc">Access token (15min) + Refresh token (7d) signed with RS256 / HS512 secret</div>
            <div class="step-code">Header.Payload.Signature<br/>Claims: sub, roles, iat, exp<br/>Signed: HMACSHA512(secret)</div>
          </div>
        </div>
        <div class="flow-step">
          <div class="step-num" style="background:rgba(255,140,0,0.1);border:1px solid rgba(255,140,0,0.3);color:var(--neon-orange)">04</div>
          <div class="step-content">
            <div class="step-title" style="color:#e2eaf7">JwtAuthFilter Intercepts Every Request</div>
            <div class="step-desc">OncePerRequestFilter validates token, sets SecurityContext — stateless, no session</div>
            <div class="step-code">Authorization: Bearer {token}<br/>→ JwtAuthFilter.doFilter()<br/>→ SecurityContextHolder.set()</div>
          </div>
        </div>
        <div class="flow-step">
          <div class="step-num" style="background:rgba(0,255,136,0.1);border:1px solid rgba(0,255,136,0.3);color:var(--neon-green)">05</div>
          <div class="step-content">
            <div class="step-title" style="color:#e2eaf7">RBAC Enforces Authorization</div>
            <div class="step-desc">@PreAuthorize checks role from JWT claims — blocks unauthorized access before method execution</div>
            <div class="step-code">@PreAuthorize("hasRole('ADMIN')")<br/>@GetMapping("/users")<br/>public List&lt;User&gt; getAll() {...}</div>
          </div>
        </div>
      </div>
    </div>

    <div style="display:flex;flex-direction:column;gap:16px">
      <!-- JWT Structure -->
      <div class="flow-container" style="border-color:rgba(0,255,136,0.15)">
        <div class="flow-title" style="color:var(--neon-green)">📦 JWT Token Anatomy</div>
        <div style="font-family:var(--mono);font-size:11px;line-height:1.7;background:rgba(0,0,0,0.4);border-radius:10px;padding:14px">
          <span style="color:#e05c5c">eyJhbGciOiJIUzUxMiJ9</span><span style="color:var(--muted)">.</span><br/>
          <span style="color:#60c0ff">eyJzdWIiOiJhZG1pbiIsInJvbGVzIjpbIlJPTEVfQURNSU4iXX0</span><span style="color:var(--muted)">.</span><br/>
          <span style="color:var(--neon-green)">HMACSHA512_SIGNATURE</span>
        </div>
        <div style="margin-top:12px;display:flex;flex-direction:column;gap:6px">
          <div style="display:flex;align-items:center;gap:8px;font-size:12px">
            <span style="width:12px;height:12px;border-radius:3px;background:#e05c5c;flex-shrink:0"></span>
            <span style="color:var(--muted)">Header:</span>&nbsp;<span style="font-family:var(--mono);color:#e2eaf7">alg: HS512, typ: JWT</span>
          </div>
          <div style="display:flex;align-items:center;gap:8px;font-size:12px">
            <span style="width:12px;height:12px;border-radius:3px;background:#60c0ff;flex-shrink:0"></span>
            <span style="color:var(--muted)">Payload:</span>&nbsp;<span style="font-family:var(--mono);color:#e2eaf7">sub, roles[], iat, exp</span>
          </div>
          <div style="display:flex;align-items:center;gap:8px;font-size:12px">
            <span style="width:12px;height:12px;border-radius:3px;background:var(--neon-green);flex-shrink:0"></span>
            <span style="color:var(--muted)">Signature:</span>&nbsp;<span style="font-family:var(--mono);color:#e2eaf7">HMAC-SHA512(base64(H)+"."+base64(P), secret)</span>
          </div>
        </div>
      </div>

      <!-- Security Config snippet -->
      <div class="flow-container" style="border-color:rgba(191,95,255,0.15)">
        <div class="flow-title" style="color:var(--neon-purple)">⚙️ SecurityFilterChain Config</div>
        <div class="step-code" style="font-size:11px;line-height:1.8;border-left-color:rgba(191,95,255,0.4)">
          <span class="kw">@Bean</span><br/>
          <span class="kw">public</span> SecurityFilterChain <span class="prop">securityChain</span>(HttpSecurity http) {<br/>
          &nbsp;&nbsp;http<br/>
          &nbsp;&nbsp;&nbsp;&nbsp;.csrf(csrf → csrf.<span class="prop">disable</span>())<br/>
          &nbsp;&nbsp;&nbsp;&nbsp;.sessionManagement(s → s.<span class="prop">sessionCreationPolicy</span>(<br/>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;SessionCreationPolicy.<span class="cls">STATELESS</span>))<br/>
          &nbsp;&nbsp;&nbsp;&nbsp;.authorizeHttpRequests(auth → auth<br/>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;.<span class="prop">requestMatchers</span>(<span class="str">"/auth/**"</span>).<span class="prop">permitAll</span>()<br/>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;.<span class="prop">anyRequest</span>().<span class="prop">authenticated</span>())<br/>
          &nbsp;&nbsp;&nbsp;&nbsp;.addFilterBefore(<span class="prop">jwtFilter</span>,<br/>
          &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;UsernamePasswordAuthFilter.<span class="kw">class</span>);<br/>
          &nbsp;&nbsp;<span class="kw">return</span> http.build();<br/>
          }
        </div>
      </div>
    </div>
  </div>

  <!-- RBAC Deep Dive -->
  <div class="card" style="border-color:rgba(255,77,166,0.15);margin-top:16px">
    <div style="font-size:15px;font-weight:700;margin-bottom:16px;color:var(--neon-pink)">🛡️ RBAC — Role-Based Access Control Matrix</div>
    <div style="overflow-x:auto">
      <table class="rbac-table">
        <thead>
          <tr>
            <th>Role</th>
            <th>User Management</th>
            <th>Attendance</th>
            <th>Salary/Payroll</th>
            <th>Reports</th>
            <th>System Config</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td><span class="role-badge" style="background:rgba(255,77,166,0.1);color:#ff4da6;border:1px solid rgba(255,77,166,0.25)">👑 ADMIN</span></td>
            <td><div class="perm-cell"><span class="perm p-yes">CREATE</span><span class="perm p-yes">READ</span><span class="perm p-yes">UPDATE</span><span class="perm p-yes">DELETE</span></div></td>
            <td><div class="perm-cell"><span class="perm p-yes">FULL</span></div></td>
            <td><div class="perm-cell"><span class="perm p-yes">FULL</span></div></td>
            <td><div class="perm-cell"><span class="perm p-yes">ALL</span></div></td>
            <td><div class="perm-cell"><span class="perm p-yes">FULL</span></div></td>
          </tr>
          <tr>
            <td><span class="role-badge" style="background:rgba(0,207,255,0.1);color:var(--neon-blue);border:1px solid rgba(0,207,255,0.25)">🧑‍💼 HR</span></td>
            <td><div class="perm-cell"><span class="perm p-yes">CREATE</span><span class="perm p-yes">READ</span><span class="perm p-yes">UPDATE</span><span class="perm p-no">DELETE</span></div></td>
            <td><div class="perm-cell"><span class="perm p-yes">MANAGE</span></div></td>
            <td><div class="perm-cell"><span class="perm p-yes">READ</span><span class="perm p-partial">PROCESS</span></div></td>
            <td><div class="perm-cell"><span class="perm p-partial">HR ONLY</span></div></td>
            <td><div class="perm-cell"><span class="perm p-no">DENIED</span></div></td>
          </tr>
          <tr>
            <td><span class="role-badge" style="background:rgba(0,255,136,0.1);color:var(--neon-green);border:1px solid rgba(0,255,136,0.25)">👤 EMPLOYEE</span></td>
            <td><div class="perm-cell"><span class="perm p-no">NO</span><span class="perm p-partial">SELF ONLY</span></div></td>
            <td><div class="perm-cell"><span class="perm p-yes">VIEW OWN</span><span class="perm p-partial">MARK</span></div></td>
            <td><div class="perm-cell"><span class="perm p-partial">VIEW OWN</span></div></td>
            <td><div class="perm-cell"><span class="perm p-partial">SELF</span></div></td>
            <td><div class="perm-cell"><span class="perm p-no">DENIED</span></div></td>
          </tr>
        </tbody>
      </table>
    </div>
    <div style="margin-top:16px;padding:12px 16px;background:rgba(0,0,0,0.3);border-radius:10px;font-family:var(--mono);font-size:11px;color:#a8c8f8;line-height:1.8;border-left:2px solid rgba(255,77,166,0.4)">
      <span class="kw">@PreAuthorize</span>(<span class="str">"hasAnyRole('ADMIN','HR')"</span>) <span class="cmt">// HR Manager endpoint</span><br/>
      <span class="kw">@PostMapping</span>(<span class="str">"/employees/onboard"</span>)<br/>
      <span class="kw">public</span> ResponseEntity&lt;EmployeeDTO&gt; <span class="prop">onboardEmployee</span>(@RequestBody EmployeeRequest req) { ... }<br/><br/>
      <span class="kw">@PreAuthorize</span>(<span class="str">"hasRole('EMPLOYEE') and #id == authentication.principal.id"</span>) <span class="cmt">// Self-access only</span><br/>
      <span class="kw">@GetMapping</span>(<span class="str">"/employees/{id}/salary"</span>)<br/>
      <span class="kw">public</span> ResponseEntity&lt;SalaryDTO&gt; <span class="prop">getMySalary</span>(@PathVariable Long id) { ... }
    </div>
  </div>
</div>

<!-- FEATURED PROJECTS -->
<div class="section">
  <div class="section-title"><div class="section-icon si-green">🚀</div> Featured Projects</div>
  <div class="card-grid card-grid-2">

    <!-- Project 1 -->
    <div class="proj-card" style="border:1px solid rgba(0,255,136,0.12)">
      <div class="proj-header">
        <div class="proj-glow" style="background:linear-gradient(90deg,var(--neon-green),var(--neon-blue))"></div>
        <div style="display:flex;align-items:center;gap:10px;margin-bottom:8px">
          <div style="width:36px;height:36px;border-radius:10px;background:rgba(0,255,136,0.12);border:1px solid rgba(0,255,136,0.25);display:flex;align-items:center;justify-content:center;font-size:18px">🔐</div>
          <div>
            <div class="proj-name" style="color:var(--neon-green)">Enterprise Spring Security Template</div>
            <div style="font-size:11px;color:var(--muted)">Production-Ready Auth Microservice</div>
          </div>
        </div>
        <div class="proj-desc">Enterprise-grade JWT + RBAC security template replicating real-world HRMS, fintech & SaaS security patterns. Plug-and-play architecture with clean layer separation.</div>
      </div>
      <div class="proj-body">
        <ul class="proj-features">
          <li><div class="feat-icon" style="background:rgba(0,255,136,0.12);color:var(--neon-green)">✓</div>JWT + BCrypt + Refresh Token rotation</li>
          <li><div class="feat-icon" style="background:rgba(0,207,255,0.12);color:var(--neon-blue)">✓</div>RBAC with endpoint-level @PreAuthorize guards</li>
          <li><div class="feat-icon" style="background:rgba(191,95,255,0.12);color:var(--neon-purple)">✓</div>Global Exception Handler + Custom Error DTOs</li>
          <li><div class="feat-icon" style="background:rgba(255,140,0,0.12);color:var(--neon-orange)">✓</div>Swagger/OpenAPI auto-docs + Docker compose</li>
          <li><div class="feat-icon" style="background:rgba(255,77,166,0.12);color:var(--neon-pink)">✓</div>Redis session caching + Kafka event hooks</li>
        </ul>
      </div>
      <div class="proj-tags">
        <span class="tag" style="background:rgba(0,255,136,0.06);color:var(--neon-green);border-color:rgba(0,255,136,0.2)">Spring Boot</span>
        <span class="tag" style="background:rgba(0,207,255,0.06);color:var(--neon-blue);border-color:rgba(0,207,255,0.2)">Spring Security 6</span>
        <span class="tag" style="background:rgba(191,95,255,0.06);color:var(--neon-purple);border-color:rgba(191,95,255,0.2)">JWT</span>
        <span class="tag" style="background:rgba(255,140,0,0.06);color:var(--neon-orange);border-color:rgba(255,140,0,0.2)">Docker</span>
        <span class="tag" style="background:rgba(255,77,166,0.06);color:var(--neon-pink);border-color:rgba(255,77,166,0.2)">Redis</span>
        <span class="tag" style="background:rgba(0,255,136,0.06);color:var(--neon-green);border-color:rgba(0,255,136,0.2)">Kafka</span>
      </div>
    </div>

    <!-- Project 2 -->
    <div class="proj-card" style="border:1px solid rgba(0,207,255,0.12)">
      <div class="proj-header">
        <div class="proj-glow" style="background:linear-gradient(90deg,var(--neon-blue),var(--neon-purple))"></div>
        <div style="display:flex;align-items:center;gap:10px;margin-bottom:8px">
          <div style="width:36px;height:36px;border-radius:10px;background:rgba(0,207,255,0.12);border:1px solid rgba(0,207,255,0.25);display:flex;align-items:center;justify-content:center;font-size:18px">🏢</div>
          <div>
            <div class="proj-name" style="color:var(--neon-blue)">Enterprise HRMS Platform</div>
            <div style="font-size:11px;color:var(--muted)">Employee Lifecycle & Workforce Ops</div>
          </div>
        </div>
        <div class="proj-desc">Real-time HRMS handling end-to-end employee lifecycle — onboarding, attendance, access control, approval workflows, and real-time status dashboards.</div>
      </div>
      <div class="proj-body">
        <ul class="proj-features">
          <li><div class="feat-icon" style="background:rgba(0,207,255,0.12);color:var(--neon-blue)">✓</div>REST APIs: onboarding, profiles, role assignment</li>
          <li><div class="feat-icon" style="background:rgba(0,255,136,0.12);color:var(--neon-green)">✓</div>Spring Security 6 + JWT + 3-tier RBAC</li>
          <li><div class="feat-icon" style="background:rgba(191,95,255,0.12);color:var(--neon-purple)">✓</div>Angular + Reactive Forms + Material UI</li>
          <li><div class="feat-icon" style="background:rgba(255,140,0,0.12);color:var(--neon-orange)">✓</div>Microservices: API Gateway + Eureka Registry</li>
          <li><div class="feat-icon" style="background:rgba(255,77,166,0.12);color:var(--neon-pink)">✓</div>Agile Scrum · CI/CD · Postman testing</li>
        </ul>
      </div>
      <div class="proj-tags">
        <span class="tag" style="background:rgba(0,207,255,0.06);color:var(--neon-blue);border-color:rgba(0,207,255,0.2)">Angular</span>
        <span class="tag" style="background:rgba(0,255,136,0.06);color:var(--neon-green);border-color:rgba(0,255,136,0.2)">Hibernate/JPA</span>
        <span class="tag" style="background:rgba(191,95,255,0.06);color:var(--neon-purple);border-color:rgba(191,95,255,0.2)">Microservices</span>
        <span class="tag" style="background:rgba(255,140,0,0.06);color:var(--neon-orange);border-color:rgba(255,140,0,0.2)">API Gateway</span>
        <span class="tag" style="background:rgba(255,77,166,0.06);color:var(--neon-pink);border-color:rgba(255,77,166,0.2)">MySQL</span>
      </div>
    </div>

    <!-- Project 3 -->
    <div class="proj-card" style="border:1px solid rgba(191,95,255,0.12)">
      <div class="proj-header">
        <div class="proj-glow" style="background:linear-gradient(90deg,var(--neon-purple),var(--neon-pink))"></div>
        <div style="display:flex;align-items:center;gap:10px;margin-bottom:8px">
          <div style="width:36px;height:36px;border-radius:10px;background:rgba(191,95,255,0.12);border:1px solid rgba(191,95,255,0.25);display:flex;align-items:center;justify-content:center;font-size:18px">🏫</div>
          <div>
            <div class="proj-name" style="color:var(--neon-purple)">SchoolAdmin Portal</div>
            <div style="font-size:11px;color:var(--muted)">Full-Stack School Management System</div>
          </div>
        </div>
        <div class="proj-desc">Comprehensive digital school administration — student management, attendance tracking, and fee management with multi-role access control (Admin, Staff, Students).</div>
      </div>
      <div class="proj-body">
        <ul class="proj-features">
          <li><div class="feat-icon" style="background:rgba(191,95,255,0.12);color:var(--neon-purple)">✓</div>Student, attendance & fee modules end-to-end</li>
          <li><div class="feat-icon" style="background:rgba(0,255,136,0.12);color:var(--neon-green)">✓</div>Spring Boot REST + Angular reactive data flow</li>
          <li><div class="feat-icon" style="background:rgba(0,207,255,0.12);color:var(--neon-blue)">✓</div>RBAC with granular per-role access levels</li>
          <li><div class="feat-icon" style="background:rgba(255,140,0,0.12);color:var(--neon-orange)">✓</div>Optimized SQL queries — bottleneck resolved</li>
        </ul>
      </div>
      <div class="proj-tags">
        <span class="tag" style="background:rgba(191,95,255,0.06);color:var(--neon-purple);border-color:rgba(191,95,255,0.2)">Spring Boot</span>
        <span class="tag" style="background:rgba(0,207,255,0.06);color:var(--neon-blue);border-color:rgba(0,207,255,0.2)">Angular</span>
        <span class="tag" style="background:rgba(0,255,136,0.06);color:var(--neon-green);border-color:rgba(0,255,136,0.2)">MySQL</span>
        <span class="tag" style="background:rgba(255,140,0,0.06);color:var(--neon-orange);border-color:rgba(255,140,0,0.2)">RBAC</span>
      </div>
    </div>

    <!-- Project 4 -->
    <div class="proj-card" style="border:1px solid rgba(255,140,0,0.12)">
      <div class="proj-header">
        <div class="proj-glow" style="background:linear-gradient(90deg,var(--neon-orange),var(--neon-green))"></div>
        <div style="display:flex;align-items:center;gap:10px;margin-bottom:8px">
          <div style="width:36px;height:36px;border-radius:10px;background:rgba(255,140,0,0.12);border:1px solid rgba(255,140,0,0.25);display:flex;align-items:center;justify-content:center;font-size:18px">📰</div>
          <div>
            <div class="proj-name" style="color:var(--neon-orange)">EveryDay News Portal</div>
            <div style="font-size:11px;color:var(--muted)">Full-Stack News Aggregation Platform</div>
          </div>
        </div>
        <div class="proj-desc">Real-time news platform with category filtering, live feed integration, and responsive TypeScript frontend. Clean REST API architecture with React components.</div>
      </div>
      <div class="proj-body">
        <ul class="proj-features">
          <li><div class="feat-icon" style="background:rgba(255,140,0,0.12);color:var(--neon-orange)">✓</div>Live news feed with category filters</li>
          <li><div class="feat-icon" style="background:rgba(0,207,255,0.12);color:var(--neon-blue)">✓</div>TypeScript + React.js responsive frontend</li>
          <li><div class="feat-icon" style="background:rgba(0,255,136,0.12);color:var(--neon-green)">✓</div>Clean RESTful API integration layer</li>
        </ul>
      </div>
      <div class="proj-tags">
        <span class="tag" style="background:rgba(255,140,0,0.06);color:var(--neon-orange);border-color:rgba(255,140,0,0.2)">TypeScript</span>
        <span class="tag" style="background:rgba(0,207,255,0.06);color:var(--neon-blue);border-color:rgba(0,207,255,0.2)">React.js</span>
        <span class="tag" style="background:rgba(0,255,136,0.06);color:var(--neon-green);border-color:rgba(0,255,136,0.2)">REST API</span>
      </div>
    </div>
  </div>
</div>

<!-- MICROSERVICES ARCHITECTURE -->
<div class="section">
  <div class="section-title"><div class="section-icon si-orange">☁</div> Microservices Architecture</div>
  <div class="card" style="border-color:rgba(255,140,0,0.15)">
    <div style="font-size:13px;color:var(--muted);margin-bottom:16px">HRMS Platform — Service Topology</div>
    <div style="display:flex;flex-direction:column;gap:8px">
      <div class="arch-row">
        <div class="arch-box" style="border-color:rgba(255,77,166,0.3);text-align:center;background:rgba(255,77,166,0.06)">
          <div class="arch-box-title" style="color:var(--neon-pink)">Angular Client</div>
          <div class="arch-box-desc">SPA · Reactive Forms · HTTP Client</div>
        </div>
      </div>
      <div style="text-align:center;color:var(--muted);font-size:18px">↓</div>
      <div class="arch-row">
        <div class="arch-box" style="border-color:rgba(255,140,0,0.3);text-align:center;background:rgba(255,140,0,0.06)">
          <div class="arch-box-title" style="color:var(--neon-orange)">API Gateway</div>
          <div class="arch-box-desc">Routing · JWT Validation · Rate Limiting · CORS</div>
        </div>
      </div>
      <div style="text-align:center;color:var(--muted);font-size:18px">↓</div>
      <div class="arch-row">
        <div class="arch-box" style="border-color:rgba(0,255,136,0.25)">
          <div class="arch-box-title" style="color:var(--neon-green)">Auth Service</div>
          <div class="arch-box-desc">Spring Security 6 · JWT Issue/Validate · BCrypt · RBAC</div>
        </div>
        <div class="arch-box" style="border-color:rgba(0,207,255,0.25)">
          <div class="arch-box-title" style="color:var(--neon-blue)">Employee Service</div>
          <div class="arch-box-desc">Profiles · Onboarding · Role Assignment · Hibernate/JPA</div>
        </div>
        <div class="arch-box" style="border-color:rgba(191,95,255,0.25)">
          <div class="arch-box-title" style="color:var(--neon-purple)">Attendance Service</div>
          <div class="arch-box-desc">Check-in/out · Leave · Real-time Status · Kafka Events</div>
        </div>
        <div class="arch-box" style="border-color:rgba(255,77,166,0.25)">
          <div class="arch-box-title" style="color:var(--neon-pink)">Notification Service</div>
          <div class="arch-box-desc">Email Alerts · Kafka Consumer · Async Processing</div>
        </div>
      </div>
      <div style="display:flex;gap:8px">
        <div class="arch-box" style="border-color:rgba(255,140,0,0.25);text-align:center">
          <div class="arch-box-title" style="color:var(--neon-orange)">Eureka Registry</div>
          <div class="arch-box-desc">Service Discovery · Health Checks · Load Balancing</div>
        </div>
        <div class="arch-box" style="border-color:rgba(0,255,136,0.25);text-align:center">
          <div class="arch-box-title" style="color:var(--neon-green)">MySQL DB</div>
          <div class="arch-box-desc">Persistent Store · JPA · Optimized Queries</div>
        </div>
        <div class="arch-box" style="border-color:rgba(0,207,255,0.25);text-align:center">
          <div class="arch-box-title" style="color:var(--neon-blue)">Redis Cache</div>
          <div class="arch-box-desc">Token Store · Session Cache · Fast Lookup</div>
        </div>
        <div class="arch-box" style="border-color:rgba(191,95,255,0.25);text-align:center">
          <div class="arch-box-title" style="color:var(--neon-purple)">Kafka Broker</div>
          <div class="arch-box-desc">Event Streaming · Async Comms · Decoupled Pub/Sub</div>
        </div>
      </div>
    </div>
  </div>
</div>

<!-- TECH STACK -->
<div class="section">
  <div class="section-title"><div class="section-icon si-purple">🛠</div> Tech Stack & Proficiency</div>
  <div style="margin-bottom:16px">
    <div style="font-size:13px;font-weight:600;color:var(--muted);text-transform:uppercase;letter-spacing:0.5px;margin-bottom:12px">☕ Backend Core</div>
    <div class="card-grid card-grid-3">
      <div class="tech-item" style="--accent-color:rgba(0,255,136,0.3)">
        <div class="tech-icon" style="background:rgba(0,255,136,0.1)">☕</div>
        <div class="tech-name">Java</div>
        <div class="tech-level"><div class="tech-bar" style="--w:90%;background:linear-gradient(90deg,var(--neon-green),var(--neon-blue))"></div></div>
      </div>
      <div class="tech-item" style="--accent-color:rgba(0,207,255,0.3)">
        <div class="tech-icon" style="background:rgba(0,207,255,0.1)">🌱</div>
        <div class="tech-name">Spring Boot</div>
        <div class="tech-level"><div class="tech-bar" style="--w:88%;background:linear-gradient(90deg,var(--neon-blue),var(--neon-purple))"></div></div>
      </div>
      <div class="tech-item" style="--accent-color:rgba(255,77,166,0.3)">
        <div class="tech-icon" style="background:rgba(255,77,166,0.1)">🛡</div>
        <div class="tech-name">Spring Security</div>
        <div class="tech-level"><div class="tech-bar" style="--w:85%;background:linear-gradient(90deg,var(--neon-pink),var(--neon-purple))"></div></div>
      </div>
      <div class="tech-item" style="--accent-color:rgba(255,140,0,0.3)">
        <div class="tech-icon" style="background:rgba(255,140,0,0.1)">🔑</div>
        <div class="tech-name">JWT / RBAC</div>
        <div class="tech-level"><div class="tech-bar" style="--w:87%;background:linear-gradient(90deg,var(--neon-orange),var(--neon-pink))"></div></div>
      </div>
      <div class="tech-item" style="--accent-color:rgba(191,95,255,0.3)">
        <div class="tech-icon" style="background:rgba(191,95,255,0.1)">🗃</div>
        <div class="tech-name">Hibernate/JPA</div>
        <div class="tech-level"><div class="tech-bar" style="--w:82%;background:linear-gradient(90deg,var(--neon-purple),var(--neon-blue))"></div></div>
      </div>
      <div class="tech-item" style="--accent-color:rgba(0,255,136,0.3)">
        <div class="tech-icon" style="background:rgba(0,255,136,0.1)">📮</div>
        <div class="tech-name">REST APIs</div>
        <div class="tech-level"><div class="tech-bar" style="--w:91%;background:linear-gradient(90deg,var(--neon-green),var(--neon-blue))"></div></div>
      </div>
    </div>
  </div>
  <div style="margin-bottom:16px">
    <div style="font-size:13px;font-weight:600;color:var(--muted);text-transform:uppercase;letter-spacing:0.5px;margin-bottom:12px">🌐 Frontend & DevOps</div>
    <div class="card-grid card-grid-3">
      <div class="tech-item" style="--accent-color:rgba(255,77,166,0.3)">
        <div class="tech-icon" style="background:rgba(255,77,166,0.1)">🅰</div>
        <div class="tech-name">Angular</div>
        <div class="tech-level"><div class="tech-bar" style="--w:80%;background:linear-gradient(90deg,var(--neon-pink),var(--neon-purple))"></div></div>
      </div>
      <div class="tech-item" style="--accent-color:rgba(0,207,255,0.3)">
        <div class="tech-icon" style="background:rgba(0,207,255,0.1)">TS</div>
        <div class="tech-name">TypeScript</div>
        <div class="tech-level"><div class="tech-bar" style="--w:78%;background:linear-gradient(90deg,var(--neon-blue),var(--neon-green))"></div></div>
      </div>
      <div class="tech-item" style="--accent-color:rgba(0,207,255,0.3)">
        <div class="tech-icon" style="background:rgba(0,207,255,0.1)">🐳</div>
        <div class="tech-name">Docker</div>
        <div class="tech-level"><div class="tech-bar" style="--w:72%;background:linear-gradient(90deg,var(--neon-blue),var(--neon-purple))"></div></div>
      </div>
      <div class="tech-item" style="--accent-color:rgba(255,140,0,0.3)">
        <div class="tech-icon" style="background:rgba(255,140,0,0.1)">⚡</div>
        <div class="tech-name">Apache Kafka</div>
        <div class="tech-level"><div class="tech-bar" style="--w:68%;background:linear-gradient(90deg,var(--neon-orange),var(--neon-pink))"></div></div>
      </div>
      <div class="tech-item" style="--accent-color:rgba(255,77,166,0.3)">
        <div class="tech-icon" style="background:rgba(255,77,166,0.1)">💾</div>
        <div class="tech-name">Redis</div>
        <div class="tech-level"><div class="tech-bar" style="--w:70%;background:linear-gradient(90deg,var(--neon-pink),var(--neon-orange))"></div></div>
      </div>
      <div class="tech-item" style="--accent-color:rgba(0,255,136,0.3)">
        <div class="tech-icon" style="background:rgba(0,255,136,0.1)">🗄</div>
        <div class="tech-name">MySQL</div>
        <div class="tech-level"><div class="tech-bar" style="--w:84%;background:linear-gradient(90deg,var(--neon-green),var(--neon-blue))"></div></div>
      </div>
    </div>
  </div>
</div>

<!-- EXPERIENCE TIMELINE -->
<div class="section">
  <div class="section-title"><div class="section-icon si-green">💼</div> Experience</div>
  <div class="card">
    <div class="timeline">
      <div class="tl-item">
        <div class="tl-dot"></div>
        <div class="tl-title">Software Engineer Associate — Enterprise HRMS Platform</div>
        <div class="tl-subtitle">Real-time enterprise application · Employee Lifecycle & Workforce Operations</div>
        <ul class="tl-list">
          <li>Developed RESTful APIs using Java & Spring Boot for onboarding, profile management, role assignment, and real-time status tracking</li>
          <li>Implemented Spring Security 6 + JWT + RBAC — stateless, scalable, multi-role access control (Admin/HR/Employee)</li>
          <li>Built Angular frontend with Reactive Forms, TypeScript, and Angular Material — dynamic forms, dashboards, validations</li>
          <li>Used Hibernate/JPA + MySQL for CRUD operations, entity mapping, and optimized data handling queries</li>
          <li>Worked with Microservices: API Gateway + Eureka Service Registry for centralized routing and service discovery</li>
          <li>Gained hands-on Docker, Redis caching, Kafka event messaging, Git versioning, and CI/CD workflows</li>
          <li>Collaborated in Agile Scrum — daily standups, sprint planning, code reviews, and release cycles</li>
        </ul>
      </div>
    </div>
  </div>
</div>

<!-- CURRENTLY EXPLORING -->
<div class="section">
  <div class="section-title"><div class="section-icon si-blue">🌱</div> Currently Leveling Up</div>
  <div class="card-grid card-grid-2">
    <div class="card" style="border-color:rgba(255,140,0,0.2);display:flex;gap:14px;align-items:flex-start">
      <div style="font-size:28px;flex-shrink:0">☁</div>
      <div><div style="font-size:14px;font-weight:700;color:var(--neon-orange);margin-bottom:4px">AWS Cloud</div><div style="font-size:13px;color:var(--muted);line-height:1.5">EC2, S3, RDS — deploying Spring Boot microservices to cloud infrastructure with auto-scaling and load balancers</div></div>
    </div>
    <div class="card" style="border-color:rgba(0,207,255,0.2);display:flex;gap:14px;align-items:flex-start">
      <div style="font-size:28px;flex-shrink:0">🏗</div>
      <div><div style="font-size:14px;font-weight:700;color:var(--neon-blue);margin-bottom:4px">System Design</div><div style="font-size:13px;color:var(--muted);line-height:1.5">Scalability patterns, distributed architecture, CAP theorem, high availability, database sharding</div></div>
    </div>
    <div class="card" style="border-color:rgba(191,95,255,0.2);display:flex;gap:14px;align-items:flex-start">
      <div style="font-size:28px;flex-shrink:0">📨</div>
      <div><div style="font-size:14px;font-weight:700;color:var(--neon-purple);margin-bottom:4px">Kafka at Scale</div><div style="font-size:13px;color:var(--muted);line-height:1.5">Event-driven microservices, consumer groups, partitioning strategies, real-time stream processing</div></div>
    </div>
    <div class="card" style="border-color:rgba(0,255,136,0.2);display:flex;gap:14px;align-items:flex-start">
      <div style="font-size:28px;flex-shrink:0">🔒</div>
      <div><div style="font-size:14px;font-weight:700;color:var(--neon-green);margin-bottom:4px">Secure Coding</div><div style="font-size:13px;color:var(--muted);line-height:1.5">OWASP Top 10, API hardening, OAuth 2.0, vulnerability scanning, pen-testing fundamentals</div></div>
    </div>
  </div>
</div>

<!-- CONNECT -->
<div class="section">
  <div class="section-title"><div class="section-icon si-green">📬</div> Let's Connect</div>
  <div class="connect-grid">
    <a href="https://amarenderreddyvoladri-portfolio.netlify.app/" class="connect-card">
      <div class="connect-icon" style="background:rgba(0,255,136,0.12);border:1px solid rgba(0,255,136,0.25)">🌐</div>
      <div><div class="connect-label">Portfolio</div><div class="connect-val" style="color:var(--neon-green)">Visit Now →</div></div>
    </a>
    <a href="https://www.linkedin.com/in/amarender-reddy-voladri/" class="connect-card">
      <div class="connect-icon" style="background:rgba(0,207,255,0.12);border:1px solid rgba(0,207,255,0.25)">💼</div>
      <div><div class="connect-label">LinkedIn</div><div class="connect-val" style="color:var(--neon-blue)">Connect →</div></div>
    </a>
    <a href="https://github.com/amarenderreddyvoladri" class="connect-card">
      <div class="connect-icon" style="background:rgba(191,95,255,0.12);border:1px solid rgba(191,95,255,0.25)">🐙</div>
      <div><div class="connect-label">GitHub</div><div class="connect-val" style="color:var(--neon-purple)">Follow →</div></div>
    </a>
    <div class="connect-card">
      <div class="connect-icon" style="background:rgba(255,140,0,0.12);border:1px solid rgba(255,140,0,0.25)">📍</div>
      <div><div class="connect-label">Location</div><div class="connect-val" style="color:var(--neon-orange)">Hyderabad, India</div></div>
    </div>
  </div>
  <div style="text-align:center;margin-top:40px;padding:32px;background:var(--card);border-radius:16px;border:1px solid rgba(0,255,136,0.1)">
    <div style="font-size:13px;color:var(--muted);margin-bottom:8px;text-transform:uppercase;letter-spacing:1px">Engineering Philosophy</div>
    <div style="font-size:20px;font-weight:700;font-style:italic;background:linear-gradient(135deg,var(--neon-green),var(--neon-blue));-webkit-background-clip:text;-webkit-text-fill-color:transparent;background-clip:text">"First, solve the problem. Then, write the code."</div>
    <div style="font-size:13px;color:var(--muted);margin-top:8px">— John Johnson</div>
  </div>
</div>

</div>

<script>
const canvas = document.getElementById('bgCanvas');
const colors = ['#00ff88','#00cfff','#bf5fff','#ff8c00','#ff4da6'];
for(let i=0;i<60;i++){
  const el = document.createElement('div');
  el.className = 'particle';
  const left = Math.random()*100;
  const dur = 8 + Math.random()*16;
  const delay = Math.random()*20;
  const dx = (Math.random()-0.5)*200;
  el.style.cssText = `left:${left}%;bottom:-10px;background:${colors[i%5]};opacity:${0.3+Math.random()*0.4};--dx:${dx}px;animation-duration:${dur}s;animation-delay:-${delay}s`;
  canvas.appendChild(el);
}

// Animate skill bars on scroll
const observer = new IntersectionObserver((entries)=>{
  entries.forEach(e=>{
    if(e.isIntersecting){
      e.target.style.animationPlayState='running';
    }
  });
},{threshold:0.1});
document.querySelectorAll('.tech-bar,.skill-fill').forEach(el=>{
  el.style.animationPlayState='paused';
  observer.observe(el);
});

// Card hover glow
document.querySelectorAll('.proj-card').forEach(card=>{
  card.addEventListener('mouseenter',()=>card.style.boxShadow='0 16px 48px rgba(0,0,0,0.5)');
  card.addEventListener('mouseleave',()=>card.style.boxShadow='');
});
</script>
