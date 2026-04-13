
# Welcome to range42

**range42** is a modular cyber range platform based on Proxmox + Ansible for deploying reproducible offensive, defensive and hybrid training environments.
One operator workstation can manage multiple Proxmox infrastructures each running multiple lab scenarios. Everything is infrastructure-as-code.

---

## Get started

| If you want to... | Read |
|------|------|
| **Deploy your first scenario** (full hands-on walkthrough, every wizard step explained) | [GETTING_STARTED.md](https://github.com/range42/range42/blob/main/GETTING_STARTED.md) |
| **Operate your lab daily** (`range42-context`: switch contexts, deploy/undeploy, SSH into VMs, view credentials) | [GETTING_STARTED.md - Using range42-context](https://github.com/range42/range42/blob/main/GETTING_STARTED.md#using-range42-context) |
| **Get the project context** (mission, roadmap, host groups, stack) | [range42/README.md](https://github.com/range42/range42/blob/main/README.md) |
| **Understand the vocabulary** (codename, scenario, workspace, vault...) | [GLOSSARY.md](https://github.com/range42/range42/blob/main/GLOSSARY.md) |
| **Try a documented network lab** (2 subnets, 4 VMs, network diagram) | [blank_scenario_2_subnets](https://github.com/range42/range42-playbooks/blob/main/scenarios/blank_scenario_2_subnets/README.md) |

---

## What's in this org

| Repo | Purpose |
|------|---------|
| [range42](https://github.com/range42/range42) | Main repository including an installation wizard, `Start here`. |
| [range42-playbooks](https://github.com/range42/range42-playbooks) | Lab scenarios - `demo_lab` (full SIEM + CTF), `blank_scenario_2/4/6_subnets` (network labs). |
| [range42-catalog](https://github.com/range42/range42-catalog) | Reusable Ansible roles (firewalls, packages, dotfiles, wazuh, etc.) used by scenarios. |
| [range42-ansible_roles-proxmox_controller](https://github.com/range42/range42-ansible_roles-proxmox_controller) | Wraps the Proxmox API - create/clone/delete VMs, templates, networks. |
| [range42-ansible_roles-debug-devkit](https://github.com/range42/range42-ansible_roles-debug-devkit) | Helper scripts for snapshots, reverts, debugging individual VMs. |
| [range42-backend-api](https://github.com/range42/range42-backend-api) | Backend API for deployer-ui (work in progress). |
| [range42-deployer-ui](https://github.com/range42/range42-deployer-ui) | Frontend UI for deployer-ui (work in progress). |


---

## Contributing

This is a collaborative initiative for applied security training and community capability building.

**Want a specific product, CVE or misconfiguration added?** Open an issue on the [range42-catalog](https://github.com/range42/range42-catalog/issues) repo - we centralise catalog requests there.

**Found a bug or have a feature request for range42 itself?** Open an issue on the [range42](https://github.com/range42/range42/issues) repo (anything not related to the catalog goes here).

We will prioritise as fast as we can.

Community health files: [.github/community](https://github.com/range42/.github/community)

---

## Authors and contributors

| Name | Company / Affiliation | Website |
|------|----------------------|---------|
| Benjamin Collas | DIGISQUAD | [DIGISQUAD](https://www.digisquad.com) |
| Philippe Parage | NC3 | [NC3](https://nc3.lu/) |

