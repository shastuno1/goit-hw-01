# Risk Register: MLOps Containerization & Delivery

| Risk Description | Probability | Impact | Mitigation Strategy | Owner |
| :--- | :--- | :--- | :--- | :--- |
| Image runs locally but fails or behaves differently in staging | Medium | High | Standardize base runtime environments and test container entrypoints thoroughly | DevOps / AI PM |
| Slim image produces different inference outputs due to missing system libraries | Low | High | Enforce automated regression testing comparing fat vs. slim outputs on identical inputs | AI/ML Engineer |
| Version incompatibility between Python 3.13, PyTorch, and torchvision | Medium | High | Pin exact package versions in `requirements.txt` and run pre-build compatibility checks | AI/ML Engineer |
| Unnecessary build context files bloated into the Docker daemon | High | Medium | Implement strict rules inside `.dockerignore` | DevOps |
| Missing or incomplete README build instructions | Medium | Low | Require README validation as a strict Definition of Done criterion | AI PM |
| Absence of comparative optimization metrics report (`report.md`) | Low | Medium | Block PR merge until metrics table is filled with real build numbers | AI PM |
| Production secrets accidentally committed into Docker Compose configuration | Low | High | Mandate use of `.env` files and `.gitignore` integration | DevOps |
| Local stack accidentally points to production database/queues | Low | High | Use isolated Docker bridge networks and local dummy connection strings | DevOps / AI PM |
| Unversioned model artifacts causing unpredictable inference behavior | Medium | High | Implement strict semantic versioning for `model.pt` files in storage | AI/ML Engineer |
| Docker image footprint too large, slowing down deployment pipelines | Medium | Medium | Enforce multi-stage builds and slim base images across all services | DevOps |