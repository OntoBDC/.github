# 🚀 OntoBDC (Ontology-Based Dataset & Containers)

[![License](https://img.shields.io/badge/license-Apache%202.0-blue.svg)](https://github.com/OntoBDC/ontobdc-core/blob/main/LICENSE) [![Python](https://img.shields.io/badge/python-3.10%2B-blue)](https://www.python.org/) [![RO-Crate](https://img.shields.io/badge/RO--Crate-1.1-green)](https://www.researchobject.org/ro-crate/) [![Status](https://img.shields.io/badge/status-active-success)](https://github.com/OntoBDC)

**OntoBDC** (Ontology-Based Dataset & Containers) is a domain-driven data architecture and capability runtime for executing ontology-aware data operations on portable datasets. It bridges the gap between static data storage and dynamic semantic execution.

When data is described by **RO-Crate**, it becomes self-describing. OntoBDC leverages this metadata to automatically discover and execute available operations relevant to the data context.

Use OntoBDC to manage the lifecycle of your engineering data projects. The runtime orchestrates **L1 Queries** (Discovery), **L2 Actions** (Transformation), and **L3 Use Cases** (State Transitions) to provide reproducible and auditable workflows.

---

## 📺 The End of Engineering Data "Hostage"
Watch the video below to understand the concept of the "Digital Briefcase" and how OntoBDC solves the Vendor Lock-in problem:

[![OntoBDC Video](https://img.youtube.com/vi/98zhTFi2I14/maxresdefault.jpg)](https://youtu.be/98zhTFi2I14?si=Yc4M2J3uS8GL6ve4)

---

**Table of contents**

- [📖 About the Project](#-about-the-project)
- [⚠️ The Problem (Single Point of Failure)](#-the-problem-single-point-of-failure)
- [⚙️ Architecture and Workflow](#️-architecture-and-workflow)
- [🚀 Main Advantages](#-main-advantages)
- [Capabilities](#capabilities)
- [Getting Started](#getting-started)
- [Entity Framework](#entity-framework)
- [Useful Links](#useful-links)

---

## 📖 About the Project
**OntoBDC** is a new, free, and *open-source* standard created to ensure true ownership of engineering data. It solves the vendor lock-in problem by replacing isolated files that require expensive licenses with **Open Semantic Containers ("Digital Briefcases")**.

With OntoBDC, the file is no longer a passive object. It becomes a unified container that carries its own raw data and the instructions to process it, allowing it to be opened and understood by any computer, anywhere.

It is commonly used to:
- **Standardize** data exchange between diverse engineering disciplines (BIM, GIS, Documents).
- **Execute** context-aware operations and automated checks without hardcoded pipelines.
- **Validate** engineering data against defined capabilities and rules ensuring reproducibility.

## ⚠️ The Problem (Single Point of Failure)
Legacy engineering projects risk becoming inaccessible if the original proprietary software is discontinued or if subscriptions expire. This dependency creates a single point of failure (SPOF), holding data "hostage" and demanding financial tolls just to access your own intellectual property.

## ⚙️ Architecture and Workflow
The transition from static governance to dynamic execution is based on the following pillars:

* **The "Digital Briefcase" (Portable):** OntoBDC packages original documents, metadata, and processing logic into an autonomous structure. The entire runtime and data package are independent and can run on a laptop, server, or container.
* **Semantic Model (Context Layer):** Uses [RO-Crate](https://www.researchobject.org/ro-crate/) for semantic metadata and relationships. The container orchestrates project rules, acting as the Single Source of Truth (SSOT).
* **Capabilities (Modular):** Embedded scripts (isolated plugins) that function as the project's "DNA". They teach the computer how to organize raw data into clean grids, eliminating the need for proprietary macros.

## 🚀 Main Advantages

* **Sovereignty and End of Vendor Lock-in:** The standard returns total data ownership to the organization. The entire team can work with the same information without being forced to acquire the same proprietary software.
* **Offline and Field Execution:** "Self-taught" containers do not depend on the cloud or online validation. Engineers can process massive volumes of data locally (on their laptops) in the middle of a construction site.
* **Future-Proof:** Packaging data and rules together ensures that an engineering project can be reproduced identically 30 years from now, immunizing the information against technological obsolescence.
* **AI-Ready:** The *capabilities*-based architecture allows Large Language Models (LLMs) to natively interact with project rules, promoting semantic automations.

## Capabilities

Capabilities are the core units of execution in OntoBDC. They are categorized into three levels of power and responsibility, ensuring safety and clarity for autonomous agents:

| Level | Name | Scope & Power | Side Effects? | Example |
| :--- | :--- | :--- | :--- | :--- |
| **L1** | **Query** | **Read-Only / Discovery.** Pure interface to query the environment. | **NO.** Must be idempotent and safe to retry infinite times. | `list_documents`, `get_file_content`, `check_syntax`. |
| **L2** | **Action** | **Transformation / Creation.** Takes input data and produces new data/files without changing business state logic. | **Local Only.** Can create/write files but does not advance workflow state. | `unzip_file`, `convert_pdf_to_png`, `generate_ro_crate_json`. |
| **L3** | **Use Case** | **State Transition.** Orchestrates L1 and L2 to move the business process forward. | **YES.** Changes the "truth" of the system. | `process_chat_folder` (Raw -> Processed), `publish_dataset`. |

This structure allows granular control over what an agent can do, separating "sensing" (L1) from "doing" (L2) and "deciding" (L3).

## Getting Started

OntoBDC requires Python 3.11+ and pip. Install it to start using the CLI:

```bash
pip install ontobdc
```

After installation, you can initialize a project context:

```bash
ontobdc init
```

This creates the local configuration (`.__ontobdc__` directory) automatically detecting the environment (e.g., `venv` or `Google Colab`).

To execute capabilities interactively:

```bash
ontobdc run
```

To validate engineering data against defined rules:

```bash
ontobdc check --repair
```

## Entity Framework

The Entity Framework is a local structure that helps you manage **Entities** (ELOFs) and their ontology façade files under `.__ontobdc__/ontology/entity/`, indexed by `.__ontobdc__/entity.rdf`.

Enable it (also prepares `.__ontobdc__/payload/*` and downloads ISO 21597 container ontologies when needed):

```bash
ontobdc entity --enable true
```

Create and list entities:

```bash
ontobdc entity --create org.example.my_entity
ontobdc entity --list
```

Disable and purge all local Entity Framework state:

```bash
ontobdc entity --enable false
ontobdc entity --purge
```

## Useful Links

| Resource | Link |
|----------|------|
| 📘 Documentation | <a href="https://docs.ontobdc.org" target="_blank">docs.ontobdc.org</a> |
| 🐙 GitHub | <a href="https://github.com/OntoBDC" target="_blank">github.com/OntoBDC</a> |
| 📦 PyPI | <a href="https://pypi.org/project/ontobdc" target="_blank">pypi.org/project/ontobdc</a> |

## Open Source & Contributing

OntoBDC is a free and open-source initiative, licensed under the **Apache License 2.0**.
We believe in the power of community-driven development to solve complex data interoperability challenges. We are always on the lookout for contributors to help us fix bugs, create new features, or improve project documentation. If you are interested, feel free to open a PR or issue on GitHub.

### Who uses OntoBDC?
OntoBDC is the core engine behind **InfoBIM**, powering semantic data interoperability for complex engineering projects.

---
<p align="center">Proudly developed in Brazil 🇧🇷</p>
