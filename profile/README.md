
# Welcome to range42

**range42** is a modular cyber range platform built on Proxmox + Ansible for deploying reproducible offensive, defensive, and hybrid cybersecurity training environments.
One operator workstation can manage multiple Proxmox clusters, each running independent lab scenarios. Everything is infrastructure-as-code.

---

## Get started

| If you want to… | Read |
|------|------|
| **Deploy your first scenario** (full hands-on walkthrough, every wizard step explained) | [GETTING_STARTED.md](https://github.com/range42/range42/blob/main/GETTING_STARTED.md) |
| **Operate your lab daily** (`range42-context`: switch contexts, deploy/undeploy, SSH into VMs, view credentials) | [GETTING_STARTED.md — Using range42-context](https://github.com/range42/range42/blob/main/GETTING_STARTED.md#using-range42-context) |
| **Get the project context** (mission, host groups, stack, long-term goals) | [range42/README.md](https://github.com/range42/range42/blob/main/README.md) |
| **Understand the vocabulary** (codename, scenario, workspace, vault…) | [GLOSSARY.md](https://github.com/range42/range42/blob/main/GLOSSARY.md) |
| **Try a documented network lab** (2 subnets, 4 VMs, network diagram) | [blank_scenario_2_subnets](https://github.com/range42/range42-playbooks/blob/main/scenarios/blank_scenario_2_subnets/README.md) |

---

## Architecture

```
Operator browser
    │
    ▼
range42-deployer-ui          Visual topology canvas — design, configure, deploy
    │
    │  REST + WebSocket
    ▼
range42-api-gw               Kong gateway — authentication, ACLs, rate-limiting
    │
    ▼
range42-backend-api          FastAPI — orchestrates Ansible via ansible-runner
    │                        80 REST endpoints (CR42 API v0.1) + /ws/status stream
    ├── range42-playbooks    Ansible playbooks: bundles (Linux, Proxmox) + scenarios
    └── range42-catalog      Ansible roles, Docker stacks, CTF/gamification content
                                 │
                                 ▼
                            Proxmox VE cluster — VMs, LXC containers, networks
```

---

## What's in this org

### Core platform

| Repo | Purpose |
|------|---------|
| [range42](https://github.com/range42/range42) | Main entry point — setup wizard, `range42-context` CLI, Ansible inventories and configs. Start here. |
| [range42-deployer-ui](https://github.com/range42/range42-deployer-ui) | Vue 3 + VueFlow topology canvas — drag-and-drop infra design, Proxmox import, one-click deployment. |
| [range42-backend-api](https://github.com/range42/range42-backend-api) | FastAPI orchestration backend — runs Ansible playbooks, streams live job status via WebSocket, manages Ansible Vault. |
| [range42-emp-mockup](https://github.com/range42/range42-emp-mockup) | Vue 3 + TypeScript mockup for the Exercise Management Platform (EMP). |
| [range42-api-gw](https://github.com/range42/range42-api-gw) | Kong API gateway configuration — authentication, ACLs, and access control in front of the backend. |
| [range42-api-definitions](https://github.com/range42/range42-api-definitions) | OpenAPI spec for the CR42 API (v0.1, 80 endpoints) — source of truth for the HTTP contract. |

### Automation

| Repo | Purpose |
|------|---------|
| [range42-playbooks](https://github.com/range42/range42-playbooks) | Centralized Ansible playbooks — `blank_scenario_2/4_subnets`, reusable bundles for Linux and Proxmox. |
| [range42-catalog](https://github.com/range42/range42-catalog) | Reusable Ansible roles (packages, dotfiles, Wazuh, firewalls, Docker), CTF scenarios (CVE, malware, misconfiguration), and gamification challenges. |
| [range42-ansible_roles-proxmox_controller](https://github.com/range42/range42-ansible_roles-proxmox_controller) | Ansible role wrapping the Proxmox API — create, clone, start, stop, snapshot, and delete VMs, templates, and networks. |
| [range42-ansible_roles-debug-devkit](https://github.com/range42/range42-ansible_roles-debug-devkit) | Developer toolkit role — VM snapshots, reverts, debugging helpers, and callback plugins. |
| [range42-deployment](https://github.com/range42/range42-deployment) | Deployment automation scripts and playbooks for standing up the platform itself. |

---

## Contributing

This is a collaborative initiative for applied security training and community capability building.

**Want a product, CVE, or misconfiguration added to the catalog?** Open an issue on [range42-catalog](https://github.com/range42/range42-catalog/issues) — catalog requests are centralised there.

**Found a bug or have a feature request for the platform?** Open an issue on [range42](https://github.com/range42/range42/issues) for anything not catalog-related, or on the relevant repo directly.

See [CONTRIBUTING.md](https://github.com/range42/.github/blob/main/CONTRIBUTING.md), [GITWORKFLOW.md](https://github.com/range42/.github/blob/main/GITWORKFLOW.md), and [SECURITY.md](https://github.com/range42/.github/blob/main/SECURITY.md) for process details.

---

## Authors and contributors

| Name | Company / Affiliation | Website |
|------|----------------------|---------|
| Benjamin Collas | DIGISQUAD | [DIGISQUAD](https://www.digisquad.com) |
| Philippe Parage | NC3 | [NC3](https://nc3.lu/) |
| Steve Clement | NC3 | [NC3](https://nc3.lu/) |
| [t0kubetsu (Alexis D.)](https://github.com/t0kubetsu) | NC3 | [NC3](https://nc3.lu/) |

