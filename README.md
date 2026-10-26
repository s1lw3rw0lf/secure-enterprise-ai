# Secure Enterprise AI

A hands-on engineering project exploring how to build secure, automated, and enterprise-ready solutions using Microsoft Azure, Bicep, Microsoft Entra ID, and eventually Microsoft Foundry.

This repository accompanies technical tutorials and demonstrations from **Niklas Tageby – Technical Training**.

## Project Goals

- Build infrastructure using Infrastructure as Code (IaC).
- Apply security-focused configuration from the beginning.
- Automate validation through GitHub Actions.
- Explore identity, access control, and secure application architecture.
- Extend the foundation toward enterprise AI agents and Microsoft Foundry.

## Current Implementation

The first version contains an Azure Storage Account defined in Bicep.

The template includes the following security settings:

| Setting | Configuration |
|---|---|
| Storage type | StorageV2 |
| Replication | Standard_LRS |
| HTTPS traffic | Required |
| Minimum TLS version | TLS 1.2 |
| Anonymous blob access | Disabled |
| Shared Key authorization | Disabled |
| Public network access | Disabled |

> **Important:** This is an infrastructure template and validation example, not a complete production deployment. Private connectivity, identity permissions, monitoring, and other operational controls must be designed before deployment.

## Repository Structure

```text
secure-enterprise-ai/
├── .github/
│   └── workflows/
│       └── validate-bicep.yml
├── infra/
│   └── main.bicep
├── .gitignore
└── README.md
```

## Validate the Bicep Template

### Prerequisites

- Azure CLI
- Bicep CLI (available through Azure CLI)
- Git

### Build

```powershell
az bicep build --file infra/main.bicep
```

### Lint

```powershell
az bicep lint --file infra/main.bicep
```

Both commands can run locally without deploying Azure resources.

## Continuous Integration

GitHub Actions automatically validates the Bicep template on pushes and pull requests targeting `main`.

The workflow performs:

1. Repository checkout.
2. Bicep installation.
3. Template build.
4. Bicep linting.

A successful pipeline confirms that these validation steps completed. It does **not** guarantee that deployment will succeed or that the resulting infrastructure is fully secure.

## Roadmap

- [x] Initial security-focused Azure Storage template
- [x] Automated Bicep build validation
- [x] Automated Bicep linting
- [ ] Architecture documentation
- [ ] Managed identities and role-based access control (RBAC)
- [ ] Private networking and secure connectivity
- [ ] Deployment validation and testing
- [ ] Microsoft Foundry integration
- [ ] Secure AI agent examples

## YouTube

This repository supports hands-on tutorials published on the **Niklas Tageby** YouTube channel.

[Visit the YouTube channel](https://www.youtube.com/@NiklasTageby)

## Disclaimer

This repository is an independent educational project and is not an official Microsoft product. Examples should be reviewed and adapted before use in production environments.