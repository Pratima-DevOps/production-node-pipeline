# Enterprise Automated CI/CD Pipeline (Node.js + Docker + AWS)

![CI/CD Pipeline](https://github.com/Pratima-DevOps/production-node-pipeline/actions/workflows/deploy.yml/badge.svg)
![Docker](https://img.shields.io/badge/Container-Docker-blue?logo=docker)
![AWS ECR](https://img.shields.io/badge/Registry-Amazon_ECR-orange?logo=amazon-aws)

## 📌 Architectural Overview
This repository implements an automated, production-grade CI/CD pipeline delivering a microservice application using containerization and security-first deployment principles.
```
[ Git Push ] ──► [ GitHub Actions ] ──► [ Unit Tests ] ──► [ Docker Build ] ──► [ ECR / EC2 Deploy ]
```
## 🛠️ Key Pipeline Features
* **Automated Testing:** Triggered on every commit/PR to validate code integrity.
* **Multi-Stage Containerization:** Dockerfile optimizes overall footprint using a multi-stage Alpine Linux base.
* **Dual Orchestration Engine:** Includes native **GitHub Actions** workflow alongside an enterprise **Jenkinsfile**.