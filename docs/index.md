<!-- BADGES:START -->
[![CI](https://github.com/POps-Rox/backstage-bootstrap/actions/workflows/ci.yml/badge.svg)](https://github.com/POps-Rox/backstage-bootstrap/actions/workflows/ci.yml)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/POps-Rox/backstage-bootstrap/pulls)
[![Maintained](https://img.shields.io/badge/Maintained%3F-yes-green.svg)](https://github.com/POps-Rox/backstage-bootstrap/graphs/commit-activity)
[![Backstage](https://img.shields.io/badge/Backstage-enabled-36BAA2.svg?logo=backstage)](https://backstage.io)
[![Terraform](https://img.shields.io/badge/Terraform-%3E%3D1.5-623CE4.svg?logo=terraform)](https://www.terraform.io)
<!-- BADGES:END -->

# 🚀 Backstage Bootstrap

> Infrastructure as Code and setup scripts to deploy a [Backstage](https://backstage.io) instance for your Platform Ops team.

Part of the [POps-Rox](https://github.com/POps-Rox) Platform Ops organization.

## 📖 Overview

This repository provides everything you need to deploy and configure a Backstage instance on Azure:

```mermaid
graph TB
    subgraph "Bootstrap Process"
        A[📦 Clone This Repo] --> B[⚙️ Configure Variables]
        B --> C[🏗️ Terraform Apply]
        C --> D[🎭 Deploy Backstage]
    end

    subgraph "Azure Infrastructure"
        C --> E[🌐 App Service]
        C --> F[🗄️ PostgreSQL]
        C --> G[🔐 Key Vault]
        C --> H[📊 Log Analytics]
    end

    D --> E
    E --> F
    E --> G
```

## 🏗️ Architecture

```mermaid
graph LR
    subgraph "Users"
        DEV[👩‍💻 Developers]
        OPS[👨‍🔧 Platform Team]
    end

    subgraph "Backstage"
        PORTAL[🎭 Backstage Portal]
        CATALOG[📚 Software Catalog]
        TEMPLATES[📋 Templates]
        TECHDOCS[📖 TechDocs]
    end

    subgraph "Azure"
        APP[🌐 App Service]
        DB[🗄️ PostgreSQL]
        KV[🔐 Key Vault]
    end

    DEV --> PORTAL
    OPS --> PORTAL
    PORTAL --> CATALOG
    PORTAL --> TEMPLATES
    PORTAL --> TECHDOCS
    PORTAL --> APP
    APP --> DB
    APP --> KV
```

## 📂 Structure

```
backstage-bootstrap/
├── terraform/          # Azure infrastructure (App Service, PostgreSQL, Key Vault)
├── scripts/            # Setup and deployment scripts
├── docs/               # Deployment guides and runbooks
└── README.md
```

## 🚀 Quick Start

```bash
# 1. Clone
git clone https://github.com/POps-Rox/backstage-bootstrap.git
cd backstage-bootstrap

# 2. Configure
cp terraform/terraform.tfvars.example terraform/terraform.tfvars
# Edit terraform.tfvars with your values

# 3. Deploy infrastructure
cd terraform
terraform init
terraform plan
terraform apply

# 4. Deploy Backstage
./scripts/deploy.sh
```

## 🤝 Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## 📄 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.
