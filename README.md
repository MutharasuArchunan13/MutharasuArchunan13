<div align="center">

# 👨‍💻 Mutharasu Archunan

### Senior Software Engineer · Backend Architect · System Designer

<br/>

<a href="https://linkedin.com/in/mutharasu-a-90638823b"><img src="https://img.shields.io/badge/-LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white"/></a>
<a href="https://github.com/MutharasuArchunan13"><img src="https://img.shields.io/badge/-GitHub-171515?style=flat-square&logo=github&logoColor=white"/></a>
<a href="https://github.com/typesense/typesense/issues/2638"><img src="https://img.shields.io/badge/OSS-Typesense_Contributor-E5534B?style=flat-square&logo=github"/></a>
<img src="https://komarev.com/ghpvc/?username=MutharasuArchunan13&color=2EA043&style=flat-square&label=Views"/>

<br/>
<br/>

<img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=600&size=20&duration=3000&pause=1000&color=2EA043&center=true&vCenter=true&repeat=true&width=650&height=45&lines=Building+Identity+Systems+securing+5+products+%F0%9F%94%90;ETL+Pipelines+processing+200K%2B+records+%F0%9F%93%8A;Debugging+Raft+Consensus+at+protocol+level+%E2%9A%99%EF%B8%8F;Architecting+Backend+Systems+from+Zero+to+Prod+%F0%9F%9A%80" />

</div>

<br/>

---

<br/>

## 🧑‍💻 About Me

```python
class Mutharasu:
    
    role       = "Senior Software Engineer"
    company    = "10xScale.ai"
    location   = "Coimbatore, India"
    
    languages  = ["Python", "Java", "JavaScript", "SQL"]
    
    architect_of = {
        "Identity Provider": "Centralized OAuth 2.0 + OIDC serving 5 products",
        "ETL Pipelines":     "Airflow + PySpark · 200K+ records · Idempotent",
        "Search Infra":      "Typesense + pgvector · Semantic search at scale",
        "Web Scrapers":      "Source-specific workers · Redis/Celery distribution"
    }
    
    open_source = "Diagnosed Raft consensus thread starvation in Typesense (#2638)"
    taught      = "Java to 100+ students"
    
    superpower  = "I don't just use tools — I build the platform others build on."
```

<br/>

---

<br/>

## 🏗️ What I've Built

<table>
<tr>
<td width="50%" valign="top">

**🔐 Centralized Identity Provider**

OAuth 2.0 + OIDC compliant IdP for **5 products**

- JWT with **EdDSA** signing · PKCE for public clients
- Refresh token families with cascade revocation
- Per-product token isolation & subscription-based auth
- **29 endpoints** · Auth, Session, OIDC, Audit routers
- FastAPI + Tortoise ORM + asyncpg + Redis + Taskiq

</td>
<td width="50%" valign="top">

**📊 ETL Pipeline Architecture**

End-to-end data processing from scratch

- **Airflow** orchestration + **PySpark** transforms
- **200K+ recruitment records** processed
- Idempotent design — safe re-execution guaranteed
- **PostgreSQL + pgvector** for semantic search
- Schema-inconsistency handling across sources

</td>
</tr>
<tr>
<td width="50%" valign="top">

**🕷️ Distributed Web Scraping**

High-throughput scraping infrastructure

- Source-specific worker pools (LinkedIn, Naukri)
- **Redis/Celery** task distribution
- Planned **Kubernetes** + KEDA autoscaling
- Rate limiting & anti-detection strategies

</td>
<td width="50%" valign="top">

**🔍 Open Source — Typesense [#2638](https://github.com/typesense/typesense/issues/2638)**

Diagnosed critical issue in **25K+ ⭐ project**

- **Raft consensus** thread starvation during 228K bulk inserts
- Write queue blocking `/health` & `/search` APIs
- Proposed decoupled health endpoints + backpressure
- Systems-level debugging at consensus layer

</td>
</tr>
</table>

<br/>

---

<br/>

## 🔐 Architecture — Identity Provider

```
┌──────────────────────────────────────────────────────────────────┐
│                   CENTRALIZED IDENTITY PROVIDER                   │
├──────────────────────────────────────────────────────────────────┤
│                                                                   │
│  ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────┐ ┌─────────┐  │
│  │Product 1│ │Product 2│ │Product 3│ │Product 4│ │Product 5│  │
│  └────┬────┘ └────┬────┘ └────┬────┘ └────┬────┘ └────┬────┘  │
│       └───────────┴─────┬─────┴───────────┴───────────┘        │
│                         │                                        │
│                  ┌──────▼──────┐                                 │
│                  │ API Gateway │                                 │
│                  └──────┬──────┘                                 │
│       ┌─────────────────┼─────────────────┐                     │
│ ┌─────▼─────┐   ┌──────▼──────┐  ┌───────▼──────┐             │
│ │Auth Router│   │OIDC Router  │  │Audit Router  │              │
│ │Login, Reg │   │Authorize,   │  │Logs, Events  │              │
│ │PKCE       │   │Token, JWKS  │  │Sessions      │              │
│ └─────┬─────┘   └──────┬──────┘  └───────┬──────┘             │
│       └─────────────────┼─────────────────┘                     │
│                         │                                        │
│            ┌────────────▼────────────┐                          │
│            │   FastAPI + Async Core  │                          │
│            └────────────┬────────────┘                          │
│     ┌───────────┐ ┌────▼────┐ ┌──────────┐                    │
│     │PostgreSQL │ │  Redis  │ │  Taskiq  │                     │
│     │26 Tables  │ │Sessions │ │Async Jobs│                     │
│     │Snowflake  │ │Cache    │ │Email,    │                     │
│     │IDs+Aerich │ │Rate Lim │ │Webhooks  │                     │
│     └───────────┘ └─────────┘ └──────────┘                     │
│                                                                   │
│ Security: EdDSA JWT · PKCE · HttpOnly+SameSite · No Enumeration │
│ Per-App: Token Isolation · Unique Audience · Refresh Families    │
└──────────────────────────────────────────────────────────────────┘
```

<br/>

---

<br/>

## 🛠️ Tech Stack

**Languages**

![Python](https://img.shields.io/badge/Python-3776AB?style=flat-square&logo=python&logoColor=white)
![Java](https://img.shields.io/badge/Java-ED8B00?style=flat-square&logo=openjdk&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![SQL](https://img.shields.io/badge/SQL-4479A1?style=flat-square&logo=postgresql&logoColor=white)
![Bash](https://img.shields.io/badge/Bash-4EAA25?style=flat-square&logo=gnubash&logoColor=white)

**Backend & Frameworks**

![FastAPI](https://img.shields.io/badge/FastAPI-005571?style=flat-square&logo=fastapi&logoColor=white)
![Spring Boot](https://img.shields.io/badge/Spring_Boot-6DB33F?style=flat-square&logo=springboot&logoColor=white)
![Django](https://img.shields.io/badge/Django-092E20?style=flat-square&logo=django&logoColor=white)
![Celery](https://img.shields.io/badge/Celery-37814A?style=flat-square&logo=celery&logoColor=white)
![Pydantic](https://img.shields.io/badge/Pydantic-E92063?style=flat-square&logo=pydantic&logoColor=white)

**Auth & Security**

![OAuth 2.0](https://img.shields.io/badge/OAuth_2.0-3C3C3D?style=flat-square&logo=auth0&logoColor=white)
![OIDC](https://img.shields.io/badge/OpenID_Connect-F78C40?style=flat-square&logo=openid&logoColor=white)
![JWT](https://img.shields.io/badge/JWT_(EdDSA)-000000?style=flat-square&logo=jsonwebtokens&logoColor=white)
![PKCE](https://img.shields.io/badge/PKCE-2EA043?style=flat-square)

**Frontend**

![React](https://img.shields.io/badge/React_19-61DAFB?style=flat-square&logo=react&logoColor=black)
![Redux](https://img.shields.io/badge/Redux-764ABC?style=flat-square&logo=redux&logoColor=white)
![Vite](https://img.shields.io/badge/Vite-646CFF?style=flat-square&logo=vite&logoColor=white)
![Radix UI](https://img.shields.io/badge/Radix_UI-161618?style=flat-square&logo=radixui&logoColor=white)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white)

**Databases & Search**

![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=flat-square&logo=postgresql&logoColor=white)
![pgvector](https://img.shields.io/badge/pgvector-316192?style=flat-square&logo=postgresql&logoColor=white)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat-square&logo=redis&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-005C84?style=flat-square&logo=mysql&logoColor=white)
![Typesense](https://img.shields.io/badge/Typesense-D21F3C?style=flat-square)

**Data & ETL**

![Airflow](https://img.shields.io/badge/Airflow-017CEE?style=flat-square&logo=apacheairflow&logoColor=white)
![PySpark](https://img.shields.io/badge/PySpark-E25A1C?style=flat-square&logo=apachespark&logoColor=white)
![Superset](https://img.shields.io/badge/Superset-1FA2E3?style=flat-square&logo=apache&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat-square&logo=pandas&logoColor=white)

**Cloud & DevOps**

![GCP](https://img.shields.io/badge/GCP-4285F4?style=flat-square&logo=googlecloud&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Kubernetes](https://img.shields.io/badge/Kubernetes-326CE5?style=flat-square&logo=kubernetes&logoColor=white)
![Terraform](https://img.shields.io/badge/Terraform-7B42BC?style=flat-square&logo=terraform&logoColor=white)
![Nginx](https://img.shields.io/badge/Nginx-009639?style=flat-square&logo=nginx&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/Actions-2088FF?style=flat-square&logo=githubactions&logoColor=white)

**ORM & Async Tools**

![Tortoise ORM](https://img.shields.io/badge/Tortoise_ORM-2EA043?style=flat-square)
![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy-D71F00?style=flat-square)
![asyncpg](https://img.shields.io/badge/asyncpg-316192?style=flat-square)
![Aerich](https://img.shields.io/badge/Aerich-017CEE?style=flat-square)
![Taskiq](https://img.shields.io/badge/Taskiq-E92063?style=flat-square)

<br/>

---

<br/>

## 👨‍🏫 Teaching & Mentoring

| 🎓 100+ Students Taught | 🎥 Content Creator | 📊 Data Engineering |
|:---:|:---:|:---:|
| Core Java, OOP, Backend fundamentals | Transitioning live → recorded tutorials | Building intermediate DE tutorial series |

<br/>

---

<br/>

## 📈 GitHub Stats

<div align="center">

<img src="https://github-readme-streak-stats-eight.vercel.app/?user=MutharasuArchunan13&theme=github-dark-blue&hide_border=true&ring=2EA043&fire=2EA043&currStreakLabel=2EA043&sideNums=F0F6FC&sideLabels=8B949E&dates=6E7681&stroke=21262D&background=0D1117" width="55%"/>

</div>

<br/>

---

<br/>

## 💎 Open Source

<a href="https://github.com/typesense/typesense/issues/2638">
<img src="https://github-readme-stats-ten-olive-80.vercel.app/api/pin/?username=typesense&repo=typesense&theme=github_dark&hide_border=true&bg_color=0D1117&title_color=2EA043&icon_color=2EA043" />
</a>

> **Issue #2638** — Diagnosed Raft consensus thread starvation during 228K document bulk inserts. Proposed decoupled health endpoints and configurable write backpressure.

<br/>

---

<div align="center">
<br/>

*"I don't just write code — I architect systems, debug at the protocol level, and teach others to do the same."*

<br/>
</div>
