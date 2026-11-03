# Acceptance Criteria: Dockerization & Inference Pipeline

## Functional Criteria
1. **Base Images**: 
   - `Dockerfile.fat` explicitly uses `python:3.13`.
   - `Dockerfile.slim` explicitly uses `python:3.13-slim`.
2. **Build Optimization**: 
   - `Dockerfile.slim` implements a multi-stage build to separate build dependencies from runtime assets.
   - A `.dockerignore` file is present in the repository root.
3. **Build & Execution**:
   - Both `ml-infer-fat:1.0` and `ml-infer-slim:1.0` build successfully without errors.
   - Both containers launch successfully using standard `docker run` commands.
4. **Inference Consistency**:
   - Both containers accept the exact same test input image.
   - Both containers successfully return top-3 class predictions.
   - Prediction outputs between `fat` and `slim` match precisely.
5. **Documentation & Reporting**:
   - `README.md` contains clear, copy-pasteable build and run commands.
   - `report.md` includes a comparative analysis of the `fat` and `slim` builds.

## Definition of Done (DoD)
> The task is considered complete when any team member can clone the repository, execute the commands specified in the `README.md`, build both fat and slim images, run inference on a shared test input, and verify identical top-3 predictions with zero manual code interventions.