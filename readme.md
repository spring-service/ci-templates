1️⃣ Central CI/CD repo (ONLY ONE)

Repo name: spring-service/ci-templates

ci-templates/
└── .github/
    └── workflows/
        └── docker-k8s-deploy.yml   ✅ REAL CI/CD LOGIC
		
-----		
2️⃣ Application repo (example: app1)

Repo name: spring-service/app1

app1/
├── Dockerfile
├── k8s/
│   ├── deployment.yaml
│   └── service.yaml
└── .github/
    └── workflows/
        └── ci.yml                 ✅ SMALL TRIGGER FILE
