# HomoSkill — Tech Stack & Architecture

## Stack Overview

| Layer | Technology | Purpose |
|---|---|---|
| Simulation | NVIDIA Isaac Sim | Skill training & testing |
| Robot SDK | Unitree SDK + ROS 2 | Hardware communication |
| Skill Platform | OpenMind OM1 | Cross-platform skills |
| AI/ML | PyTorch + Isaac Lab | Reinforcement learning |
| Backend | Python FastAPI | Sapien API server |
| Frontend | Next.js + Tailwind | Studio & Fleet dashboards |
| Database | PostgreSQL + TimescaleDB | Data + telemetry |
| Cloud | AWS or GCP | Hosting + simulation |
| Auth | Clerk or Auth.js | SaaS authentication |
| Payments | Stripe | Billing |

## Architecture

```
[Hotel Systems]          [Humanoid Robots]
  PMS / POS                Unitree G1
     │                     Figure 02
     │                     Any humanoid
     │                        │
     └────── Sapien API ──────┘
                │
        ┌───────┴───────┐
        │  Sapien Core  │
        │  Skill Engine │
        └───────┬───────┘
                │
     ┌──────────┼──────────┐
     │          │          │
  Sapien     Sapien     Sapien
  Studio     Fleet      Sense
```

## Key Technical Decisions

- Start with Unitree G1 (~$16K) — cheapest production humanoid
- Simulation-first development — train in Isaac Sim before real hardware
- Hardware-agnostic from day 1 — abstract robot communication layer
- Skill = containerized module that can be deployed to any supported robot
