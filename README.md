<div align="center">

<img src="hero.svg" width="100%" alt="Yash Agarwal — AWS Cloud Engineer / Platform · DevOps. A pixel terminal, a Grafana monitor breaching its SLO line, a blinking server rack, and a green snake crawling along the bottom." />

</div>

**AWS Cloud Engineer** — I provision the infrastructure, ship the services onto it, and keep both observable.

I write the platform in **Terraform** (ECS, ALB, Route 53, ACM, EC2, IAM), release to it from **GitHub Actions**
on self-hosted runners, run multi-service workloads on **Kubernetes**, and wire up the
**Grafana / Prometheus / Loki / OpenTelemetry** stack so that when something breaks at 3am,
the dashboard says _where_ before anyone has to guess. I still write the backend — **Python** (FastAPI, Django)
and **TypeScript** — which is why my infra fits the code it runs.

Open to **Cloud / DevOps / Platform / SRE** roles. AWS Certified, based in India, comfortable remote.

<img src="divider.svg" width="100%" alt="" />

## ▸ How my code reaches prod

<img src="pipeline.svg" width="100%" alt="Animated pipeline: write, test and build, containerise, deploy, observe — with alerts and runbooks feeding back into the code." />

Every stage above is something I've built for real, not aspirationally:

| Stage            | What that means in my repos                                                                                                                                                                                                                                                                                                                                                                                                                               |
| ---------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Write**        | Infra as **Terraform** modules — VPC, ECS services, ALB listeners, Route 53 records, ACM certs, least-privilege IAM — reviewed and planned in CI like any other code. Application side: FastAPI + Django services, async pipelines on Celery/Redis, a Fastify server in TypeScript. Domain logic kept pure and unit-tested — [Focus-Den's core/](https://github.com/yashukun/Focus-Den) takes an explicit `now` so it never touches the clock or storage. |
| **Test + Build** | GitHub Actions running typecheck, tests, build and `terraform plan` on every push. Deploys only roll forward to the newest **CI-green commit** — a broken build physically can't ship.                                                                                                                                                                                                                                                                    |
| **Containerise** | Dockerfiles with pinned Git-SHA build metadata, multi-service Compose stacks ([FixED](https://github.com/yashukun/FixED) runs 8 services with isolated networking), restart policies, volume-backed state.                                                                                                                                                                                                                                                |
| **Deploy**       | **ECS behind an ALB** with Route 53 + ACM TLS, provisioned end-to-end by Terraform and released to by **self-hosted GitHub Actions runners**. On Kubernetes: Deployments, Ingress, ConfigMaps/Secrets, StorageClass-backed volumes, HPA. Smaller boxes get one **idempotent script** — the same command sets up a fresh host or updates a running one. Day-2 ops written down, not memorised.                                                             |
| **Observe**      | Prometheus alerts on user-visible symptoms (plus **custom exporters** for the metrics nobody ships), Loki logs correlated to traces by ID, OpenTelemetry + Jaeger across services, Grafana dashboards split by audience. Incidents end as runbooks.                                                                                                                                                                                                       |

<img src="divider.svg" width="100%" alt="" />

## ▸ Proof of work

|                                                                | What it is                                                                                                                                             | What it proves                                                                                                                                                         |
| -------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **[Focus-Den](https://github.com/yashukun/Focus-Den)**         | A shift tracker with a cozy pixel room — clock in, focus, earn points, grow your den. Tauri (Rust) shell around a React/TS/Vite app, fully local data. | I can **build and release** the whole thing solo: CI gates → GitHub Actions release pipeline → signed macOS + Windows installers → auto-updater. Documented day-2 ops. |
| **[FixED](https://github.com/yashukun/FixED)**                 | RAG microservices platform: hybrid vector + lexical retrieval over textbooks, async ingestion, exam generation, SSE streaming.                         | Multi-service architecture under one Compose file — FastAPI, Qdrant, Celery, Redis, MinIO — with **token/cost observability** built in.                                |
| **[Django-Docker](https://github.com/yashukun/Django-Docker)** | Django, containerised the boring-good way.                                                                                                             | The fundamentals: a clean, reproducible path from `manage.py` to a running container.                                                                                  |

<img src="divider.svg" width="100%" alt="" />

## ▸ Stack

```yaml
cloud: [aws-ecs, alb, route53, acm, ec2, iam, s3, cloudwatch]
iac: [terraform, docker, docker-compose]
platform: [kubernetes, github-actions, self-hosted-runners, nginx/caddy, linux]
observability:
  [
    grafana,
    prometheus,
    custom-exporters,
    loki,
    opentelemetry,
    jaeger,
    promql,
    slis/slos,
  ]
languages: [python, typescript, bash, hcl, sql]
backend: [fastapi, django, node/fastify, celery, redis, rest, sse/websockets]
data: [postgresql, elasticsearch, qdrant, minio, sqlite]
certified: aws-cloud-practitioner # 2025 → 2028, verify below
```

[![AWS Certified Cloud Practitioner](https://img.shields.io/badge/AWS%20Certified-Cloud%20Practitioner-FF9900?style=flat-square&logo=amazonwebservices&logoColor=white)](https://www.credly.com/badges/2c765ea7-224a-43df-ae7d-c51bcda7f821/public_url)

<img src="divider.svg" width="100%" alt="" />

## ▸ The snake also eats my commits

<div align="center">

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/yashukun/yashukun/output/snake-dark.svg" />
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/yashukun/yashukun/output/snake.svg" />
  <img src="https://raw.githubusercontent.com/yashukun/yashukun/output/snake.svg" alt="a snake eating my contribution graph" width="100%" />
</picture>

<img height="165" src="https://github-readme-stats.vercel.app/api?username=yashukun&show_icons=true&cache_seconds=86400&hide_border=true&bg_color=0D1117&title_color=39D353&icon_color=39D353&text_color=C9D1D9" alt="github stats" />
<img height="165" src="https://github-readme-stats.vercel.app/api/top-langs/?username=yashukun&layout=compact&cache_seconds=86400&hide_border=true&bg_color=0D1117&title_color=39D353&text_color=C9D1D9" alt="top languages" />

</div>

<img src="divider.svg" width="100%" alt="" />

<div align="center">

**▸ PING ME**

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/yashukun/)
[![Email](https://img.shields.io/badge/Email-EA4335?style=flat-square&logo=gmail&logoColor=white)](mailto:yashagarwal.cs@gmail.com)
[![Upwork](https://img.shields.io/badge/Upwork-Freelance-6FDA44?style=flat-square&logo=upwork&logoColor=white)](https://www.upwork.com/freelancers/~01c362d0288b459345)
![Discord](https://img.shields.io/badge/Discord-yashu31-5865F2?style=flat-square&logo=discord&logoColor=white)

```
░░░░░░░░░░░░░░░  P R E S S   S T A R T  ░░░░░░░░░░░░░░░
```

</div>
