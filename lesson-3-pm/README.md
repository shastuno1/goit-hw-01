# Lesson 3 PM Artifacts: MLOps Containerization Package

## Objective
This repository contains the governance, task definitions, review checklists, and validation reports prepared by the AI Project Manager for the image classification model containerization milestone.

## Context
Transitioning a machine learning model from experimental scripts to a robust staging environment requires strict delivery standards, reproducible builds, and clear separation of concerns between raw implementation and operational readiness.

## PM Artifacts Index
1. `project_brief.md` — Business and technical context.
2. `ai_ml_team_task.md` — Structured engineering task description.
3. `acceptance_criteria.md` — Clear, testable acceptance rules and DoD.
4. `docker_image_review.md` — Technical checklist for Dockerfiles and dependencies.
5. `optimization_report_review.md` — Comparative performance & size matrix (`fat` vs `slim`).
6. `compose_readiness_checklist.md` — Local multi-service integration checklist.
7. `risk_register.md` — Comprehensive delivery risk assessment matrix.
8. `stakeholder_summary.md` — Non-technical executive summary.
9. `README.md` — Navigational overview (this file).

---

## Questions to AI/ML Team
- What is the exact version and storage path of the final model artifact (`model.pt`)?
- What precise input image dimensions and normalization ranges are expected by `app/inference.py`?
- Has full compatibility between `python:3.13`, `torch`, and `torchvision` been verified?
- Is `.dockerignore` properly filtering out local virtual environments and caches?
- Do the inference results for `ml-infer-fat:1.0` and `ml-infer-slim:1.0` match down to the top-3 confidence scores?
- Does `report.md` include verified image sizes and build times?
- Are build and run commands fully documented in the team's working documentation?
- Does the local Docker Compose stack spin up successfully with a single command (`docker compose up --build`)?
- Are all environment variables externalized without exposing sensitive credentials?

## Quick Validation Commands
```bash
# Build fat image
docker build -t ml-infer-fat:1.0 -f Dockerfile.fat .

# Build slim image
docker build -t ml-infer-slim:1.0 -f Dockerfile.slim .

# Check image sizes
docker images | grep ml-infer

# Run local inference test
docker run --rm -v $(pwd)/test_images:/app/input ml-infer-slim:1.0 python app/inference.py --input /app/input/sample.jpg