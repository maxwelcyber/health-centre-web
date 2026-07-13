text
```
┌─────────────────────────────────────────────────────────────────┐
│  1. YOU (Developer)                                            │
│  ┌────────────────────────────────────────────────────────┐    │
│  │  • Write app code                                      │    │
│  │  • Build container image (docker build)               │    │
│  │  • Push image to ACR                                  │    │
│  │  • Update YAML in GitHub repo (change image tag)     │    │
│  └────────────────────────────────────────────────────────┘    │
│                          │                        │             │
│                          ▼                        ▼             │
│  ┌──────────────────────────────────┐  ┌─────────────────────┐ │
│  │  ACR (Warehouse)                │  │  GitHub (Private)   │ │
│  │  • Stores bulky container images│  │  • Stores YAML files│ │
│  │  • Immutable, versioned        │  │  • Audit trail      │ │
│  └──────────────────────────────────┘  └─────────────────────┘ │
│                          │                        │             │
│                          │                        ▼             │
│                          │          ┌─────────────────────────┐ │
│                          │          │  ArgoCD (In AKS)       │ │
│                          │          │  • Pulls YAML from Git │ │
│                          │          │  • Auto-syncs to AKS   │ │
│                          │          └─────────────────────────┘ │
│                          ▼                        │             │
│  ┌──────────────────────────────────────────────────┐          │
│  │  AKS Cluster (Runs your app)                    │          │
│  │  • Pulls image from ACR                         │◄─────────┘
│  │  • Runs containers based on YAML instructions  │
│  └──────────────────────────────────────────────────┘          │
└─────────────────────────────────────────────────────────────────┘
```
