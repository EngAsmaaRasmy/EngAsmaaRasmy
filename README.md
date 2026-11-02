<h1 align="center">Asmaa Rasmy</h1>
<p align="center"><b>Lead Full Stack Engineer</b> · Laravel · React · AI Agents · Multi-tenant SaaS</p>
<p align="center">
  <a href="https://linkedin.com/in/asmaarasmy"><img src="https://img.shields.io/badge/LinkedIn-asmaarasmy-0A66C2?style=flat-square" alt="LinkedIn" /></a>
  <a href="mailto:asmaarasmy98@gmail.com"><img src="https://img.shields.io/badge/Email-asmaarasmy98%40gmail.com-555?style=flat-square" alt="Email" /></a>
</p>

---

I design and lead the delivery of multi-tenant SaaS platforms, from architecture and data modelling to code review and production releases. I currently lead a 7-person engineering team, and my focus is on system design: tenant isolation, authorization and workflow engines, reliable async processing, and AI agents that run safely in production.

> Most of my work lives in private employer and client repositories. The notes below describe the systems and the design decisions behind them, without any proprietary code.

## Featured Systems

### 1. AI-native commerce platform
An AI agent that works as a first-class user: it can create, find and update anything a merchant can, in Arabic or English, live for every merchant.

**Key decisions:** one action layer shared by the UI and the agent, so both pass the same permission checks; human confirmation before destructive actions; a full audit trail of agent activity; queue-based pipelines for AI image, video and product data generation.

```mermaid
flowchart LR
    UI["Merchant UI"] --> AL["Action Layer"]
    AG["AI Agent"] --> AL
    AL --> P{"Permission check"}
    P -->|"destructive"| C["User confirmation"]
    P -->|"safe"| M["Domain modules"]
    C --> M
    M --> A[("Audit log")]
```

### 2. Central authorization & approvals platform
A single source of truth for permissions and approvals across ERP, HR and finance systems.

**Key decisions:** a policy engine with attribute-based record scopes, field-level rights and deny-overrides; client-side caching with push-based invalidation; fail-closed behavior when the service is unreachable; HMAC-signed callbacks and outbox/inbox delivery for reliable approvals; versioned policies with a simulator for safe changes.

```mermaid
flowchart LR
    APPS["ERP · HR · Finance apps"] -->|"context API"| CORE["Authorization Platform"]
    CORE -->|"push cache invalidation"| APPS
    CORE --> PE["Policy engine"]
    CORE --> WF["Approval workflow engine"]
    WF -->|"outbox/inbox · HMAC callbacks"| APPS
```

### 3. Two-level multi-tenant donation platform
A white-label platform serving charities across multiple countries.

**Key decisions:** branded domains sharing one central database with per-domain data scoping, each hosting charities on isolated tenant databases; per-charity ledgers for fees, withdrawals and refunds; versioned donor consent and sanctions enforcement; per-tenant payment and SMS providers with automatic failover.

```mermaid
flowchart TB
    D1["Domain A"] --> C[("Central DB · per-domain scoping")]
    D2["Domain B"] --> C
    C --> T1[("Charity DB")]
    C --> T2[("Charity DB")]
    C --> T3[("Charity DB")]
```

## Tech Stack

![Laravel](https://img.shields.io/badge/Laravel-FF2D20?style=flat-square&logo=laravel&logoColor=white)
![PHP](https://img.shields.io/badge/PHP-777BB4?style=flat-square&logo=php&logoColor=white)
![Node.js](https://img.shields.io/badge/Node.js-339933?style=flat-square&logo=nodedotjs&logoColor=white)
![React](https://img.shields.io/badge/React-20232A?style=flat-square&logo=react&logoColor=61DAFB)
![Next.js](https://img.shields.io/badge/Next.js-000000?style=flat-square&logo=nextdotjs&logoColor=white)
![Angular](https://img.shields.io/badge/Angular-DD0031?style=flat-square&logo=angular&logoColor=white)
![TypeScript](https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-4479A1?style=flat-square&logo=mysql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-232F3E?style=flat-square)
![OpenAI](https://img.shields.io/badge/OpenAI-412991?style=flat-square)
![Gemini](https://img.shields.io/badge/Gemini-1A73E8?style=flat-square)

**System design:** multi-tenancy · authorization policy engines · approval workflows · event-driven & queues · outbox/inbox · idempotency · ledgers & payment orchestration

---

<p align="center"><i>Open to Senior and Lead full-time remote roles · Cairo, Egypt (UTC+2/+3)</i></p>
