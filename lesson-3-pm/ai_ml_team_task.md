# Jira Issue: Containerize Image Classification Model for Staging/Production

## Background
We need to package our image classification inference pipeline into reliable Docker images (`fat` and `slim`) to support upcoming staging deployment and integration tests.

## Scope
- Create `Dockerfile.fat` based on standard `python:3.13`.
- Create `Dockerfile.slim` based on `python:3.13-slim` using a multi-stage build pattern.
- Implement a comprehensive `.dockerignore` file to minimize build context.
- Lock all runtime dependencies in `requirements.txt`.
- Ensure identical inference behavior between `fat` and `slim` images.
- Provide a clear `README.md` with build and run instructions.

## Out of Scope
- Model retraining or weight adjustments.
- Accuracy improvements or hyperparameter tuning.
- Production Kubernetes orchestration manifests (handled in later modules).
- Full observability/monitoring setup.

## Expected Deliverables
- `Dockerfile.fat`
- `Dockerfile.slim`
- `.dockerignore`
- `requirements.txt`
- `README.md`
- `report.md` (comparison metrics)

## Technical Constraints
- Base image for slim variant: `python:3.13-slim`.
- Python runtime compatibility: Python 3.13.
- Input/Output format: Standardized image tensor input returning top-3 predictions.

## Acceptance Criteria Summary
- Both images build successfully without errors.
- Inference results (top-3 prediction) match completely between `fat` and `slim`.
- Clear documentation provided for running local validations.