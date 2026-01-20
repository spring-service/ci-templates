## 📦 CI/CD Repository & Application Structure

This setup uses **one central CI/CD repository** and **multiple application repositories** that reuse the same pipeline logic.

---

### 1️⃣ Central CI/CD Repository (ONLY ONE)

**Repo name:** `spring-service/ci-templates`

This repository contains the **actual reusable CI/CD workflow**.

ci-templates/
└── .github/
└── workflows/
└── docker-k8s-deploy.yml ✅ REAL CI/CD LOGIC

yaml
Copy code

---

### 2️⃣ Application Repository (Example: app1)

**Repo name:** `spring-service/app1`

This repository contains application-specific code and a **small trigger workflow** that calls the central CI/CD pipeline.

app1/
├── Dockerfile
├── k8s/
│ ├── deployment.yaml
│ └── service.yaml
└── .github/
└── workflows/
└── ci.yml ✅ SMALL TRIGGER FILE

yaml
Copy code

---

### 🔁 How It Works

1. Developer pushes code to the **application repository**
2. `ci.yml` is triggered in the app repo
3. The workflow **calls the reusable pipeline** from `ci-templates`
4. Docker image is built and pushed
5. Kubernetes manifests are applied
6. Application is deployed to the cluster

---

### 🎯 Benefits

- Single source of truth for CI/CD
- No duplication of pipeline logic
- Easy maintenance and scalability
- Enterprise-grade CI/CD pattern
