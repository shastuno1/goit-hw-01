# AI PM Review Checklist: Docker Solution

## 4.1 Dockerfile Structure
- [ ] Separate `Dockerfile.fat` and `Dockerfile.slim` files exist.
- [ ] Appropriate base images selected (`python:3.13` vs `python:3.13-slim`).
- [ ] Multi-stage build properly separates compiler tools from the final runtime image in `Dockerfile.slim`.
- [ ] `COPY` instructions ordered logically to maximize Docker layer caching (dependencies copied before application code).
- [ ] `.dockerignore` is present and excludes `.git`, caches, virtual environments, and local test outputs.

## 4.2 Dependencies & Libraries
- [ ] `requirements.txt` is present and pinned to explicit package versions.
- [ ] All packages (`torch`, `torchvision`, `Pillow`, etc.) are fully compatible with Python 3.13.
- [ ] No extraneous development-only packages (e.g., pytest, black, flake8) leak into the runtime container.

## 4.3 Inference Execution
- [ ] Both images build successfully.
- [ ] Containers accept mounting or passing test images/inputs correctly.
- [ ] Inference execution outputs valid top-3 predictions.
- [ ] Step-by-step execution instructions are documented in the README.

## 4.4 Reproducibility
- [ ] Identical model artifact (`model/model.pt`) used across both variants.
- [ ] Preprocessing steps and normalization parameters are identical.
- [ ] Source origin or model version tag is clearly noted.