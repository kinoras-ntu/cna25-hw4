# CNA25-HW4: Docker + CI/CD

A minimal FastAPI backend service, containerized with Docker.  
This project uses GitHub Actions to automate building and pushing images to Docker Hub.

## Build & Run Locally

```bash
# Build Docker image
docker build -t kinoras/2025cloud .

# Run the container
docker run -p 8000:8000 kinoras/2025cloud
```

Once running, test with:

```bash
curl http://localhost:8000/
# Expected: {"message":"Hello from 2025cloud backend"}
```

## Image Generation & Tag Logic

### Image Builds

Docker images are built automatically via GitHub Actions:

- **On `main` push** → Build & push image to Docker Hub

- **On pull request** → Only build (no push)

### Tag Rules

`latest` → always the newest main build

`<short-sha>` → 7-character Git commit hash (e.g. 3f2a9d1) for traceability

This ensures a clean, traceable, and safe image release process.
