# Docker Compose Readiness Checklist (Local Integration Stack)

## Stack Components
- `model-api` (Inference service running `ml-infer-slim:1.0`)
- `Redis` (Task queue / caching layer)
- `PostgreSQL` (Metadata / request logging DB)
- `Monitoring` (Prometheus/Grafana lightweight metrics collector)

## Checklist Items
- [ ] `compose.yaml` is present in the root directory.
- [ ] `model-api` service correctly references the built inference image.
- [ ] All dependent backing services (Redis, Postgres) are declared with healthchecks.
- [ ] Services spin up automatically without manual intervention steps.
- [ ] Port mappings are correctly exposed (e.g., `8000:8000`) with no port conflicts.
- [ ] `/health` and `/predict` endpoints are available and functional.
- [ ] Configuration variables are externalized into a `.env.example` file.
- [ ] No production secrets or sensitive keys are hardcoded in `compose.yaml`.
- [ ] Local stack is completely isolated and does not connect to production databases or message queues.
- [ ] Quick-start instructions (`docker compose up --build`) are documented in the README.

## Final Verdict
> The local stack is approved for integration testing as all components spin up via a single command and execute test predictions smoothly.