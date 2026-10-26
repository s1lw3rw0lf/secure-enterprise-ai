
# Secure Enterprise AI – Architecture

## Current Architecture

This diagram illustrates the current Infrastructure as Code (IaC) development and validation workflow.

```mermaid
flowchart TD
    A["Developer<br/>VS Code + Bicep"]
    B["GitHub Repository<br/>secure-enterprise-ai"]
    C["GitHub Actions"]
    D["Bicep Build"]
    E["Bicep Lint"]
    F["Validation Complete"]
    G["Azure Storage Account<br/>Planned Deployment"]

    A -->|Git Push| B
    B -->|Push / Pull Request| C
    C --> D
    C --> E
    D --> F
    E --> F
    F -.->|Future Step| G

    style A fill:#172554,color:#ffffff,stroke:#60a5fa
    style B fill:#1e293b,color:#ffffff,stroke:#94a3b8
    style C fill:#1e40af,color:#ffffff,stroke:#93c5fd
    style D fill:#065f46,color:#ffffff,stroke:#6ee7b7
    style E fill:#065f46,color:#ffffff,stroke:#6ee7b7
    style F fill:#166534,color:#ffffff,stroke:#86efac
    style G fill:#374151,color:#ffffff,stroke:#9ca3af,stroke-dasharray:5 5
```

## Security Configuration

The current Bicep template defines an Azure Storage Account with:

- HTTPS-only traffic
- Minimum TLS version 1.2
- Anonymous blob access disabled
- Shared Key authorization disabled
- Public network access disabled

These settings provide a security-focused starting point, but additional controls are required before production deployment.

## Current Status

**Implemented:**
- Azure Storage Account Bicep template
- GitHub Actions build validation
- GitHub Actions lint validation

**Planned:**
- Azure deployment
- Private networking
- Managed identities and RBAC
- Monitoring and diagnostics
- Microsoft Foundry and AI agent integration

> A successful Bicep build and lint run does not guarantee successful Azure deployment or production security.