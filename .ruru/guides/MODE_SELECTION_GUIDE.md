# 🧭 Mode Selection Guide

This guide helps determine the most appropriate mode for initiating or handling specific tasks within the Ruru multi-mode system. It's based on the primary focus and core responsibilities defined in each mode's Knowledge Base.

## 📜 General Principles

*   **Primary Focus:** Choose the mode whose core responsibilities most closely align with the primary goal of the task.
*   **Specificity:** Prefer more specialized modes (e.g., `team-lead-backend` for API implementation) over more general ones (e.g., `code`) if the task falls clearly within their domain.
*   **Leadership Level:** For tasks involving strategy, cross-team coordination, or management, consider the appropriate leadership level (Team Lead vs. EM vs. HoD).
*   **Cross-Cutting Concerns:** For tasks involving multiple domains (e.g., a feature needing FE, BE, and QA), start with the mode responsible for initiating the work (often Product Owner or a Team Lead) or use an orchestrator mode if available. Use `switch_mode` judiciously if a task transitions significantly between domains.
*   **Consult KBs:** When unsure, consult the "Core Responsibilities" and "Collaboration & Interfaces" sections of potentially relevant mode KBs.

## 🎯 Mode Responsibilities & Task Alignment

*   **👑 `head-of-development`**:
    *   **Focus:** Overall engineering strategy, departmental leadership, managing EMs/Leads, cross-departmental coordination, budget/resource allocation.
    *   **Use When:** Defining engineering-wide strategy, setting departmental goals, managing engineering leadership, addressing high-level organizational impediments.

*   **👔 `engineering-manager-1`**:
    *   **Focus:** Managing Frontend, Backend, QA Leads; cross-functional delivery involving these teams; performance management and career growth for these leads.
    *   **Use When:** Coordinating feature delivery across FE/BE/QA, managing performance of these leads, addressing cross-team issues within this group.

*   **👔 `engineering-manager-2`**:
    *   **Focus:** Managing Platform, DevOps, UI/UX Leads; cross-functional delivery involving these teams; performance management and career growth for these leads.
    *   **Use When:** Coordinating platform/infra/ops/design initiatives, managing performance of these leads, addressing cross-team issues within this group.

*   **🏗️ `lead-architect`**:
    *   **Focus:** High-level system design, technical vision & strategy, defining NFRs, architectural governance, cross-team technical guidance, managing architectural risk.
    *   **Use When:** Designing new systems/major features, making significant technology choices, defining architectural standards, resolving cross-cutting technical challenges.

*   **👨‍💻 `team-lead-frontend`**:
    *   **Focus:** Leading FE team, overseeing FE implementation (UI components, state management), ensuring FE code quality/standards/performance/accessibility, facilitating design integration, mentoring FE devs.
    *   **Use When:** Implementing UI features, building/refactoring FE components, addressing FE technical debt, managing FE team tasks.

*   **⚙️ `team-lead-backend`**:
    *   **Focus:** Leading BE team, overseeing BE implementation (APIs, business logic, database interaction), ensuring BE code quality/standards/performance, defining API contracts, mentoring BE devs.
    *   **Use When:** Implementing API endpoints, designing database schemas, building business logic, addressing BE technical debt, managing BE team tasks.

*   **✅ `qa-lead`**:
    *   **Focus:** Leading QA team, defining QA strategy/plans, overseeing test execution (manual/automated), managing bug tracking/reporting, defining release criteria, driving test automation.
    *   **Use When:** Creating test plans, setting up automation frameworks, managing bug triage, defining quality metrics, making release readiness recommendations.

*   **☁️ `team-lead-platform`**:
    *   **Focus:** Leading Platform team, designing/building/maintaining the Internal Developer Platform (IDP), providing self-service tools/infra, ensuring platform reliability/scalability, improving Developer Experience (DevEx).
    *   **Use When:** Building shared infrastructure components, creating IaC modules, setting up Kubernetes clusters, developing CI/CD *foundations*, managing the developer portal.

*   **🚀 `devops-lead`**:
    *   **Focus:** Leading DevOps team, designing/managing application CI/CD *pipelines*, ensuring operational stability/reliability, implementing monitoring/alerting, managing application IaC/deployments (often using platform services).
    *   **Use When:** Setting up application deployment pipelines, configuring monitoring/alerting for services, managing production incidents, automating operational tasks.

*   **🎨 `ui-ux-lead`**:
    *   **Focus:** Leading UI/UX team, defining UX strategy, overseeing design process (research, IA, interaction, visual), managing the design system, ensuring usability/accessibility.
    *   **Use When:** Conducting user research, designing user flows/wireframes, creating prototypes, managing the design system components/guidelines.

*   **🔒 `security-lead`**:
    *   **Focus:** Defining security strategy, integrating security into SDLC (DevSecOps), conducting security assessments/audits, guiding secure coding, managing vulnerabilities, ensuring compliance.
    *   **Use When:** Performing threat modeling, setting up security scanning tools, responding to security incidents, defining security policies, conducting security code reviews.

*   **🗄️ `data-engineering-lead`**:
    *   **Focus:** Leading Data Engineering team, designing/managing data architecture (warehouses, lakes), overseeing data pipelines (ETL/ELT), ensuring data quality/governance.
    *   **Use When:** Building data pipelines, designing data models/schemas, setting up data quality checks, managing data infrastructure.

*   **✍️ `technical-writing-lead`**:
    *   **Focus:** Leading Tech Writing team, defining documentation strategy/standards/style guides, overseeing content lifecycle (creation, review, publishing), managing documentation tools/processes.
    *   **Use When:** Creating documentation plans, establishing style guides, reviewing documentation quality, managing documentation tools.

*   **📦 `product-owner`**:
    *   **Focus:** Defining product vision/goal, managing/prioritizing the Product Backlog, representing stakeholder/customer needs, defining requirements (user stories), accepting completed work.
    *   **Use When:** Creating/prioritizing user stories, defining product features, gathering customer requirements, making decisions about product direction.

*   **🔄 `scrum-master`**:
    *   **Focus:** Facilitating Scrum events, coaching team on Agile/Scrum, removing impediments, supporting the PO, shielding the team, promoting continuous improvement.
    *   **Use When:** Running Scrum ceremonies, addressing team blockers, coaching on Agile practices, improving team dynamics/processes.

*   **📊 `business-analyst`**:
    *   **Focus:** Eliciting/analyzing/documenting requirements, modeling business processes, facilitating communication between business and tech, ensuring solution alignment.
    *   **Use When:** Gathering detailed requirements from stakeholders, creating process diagrams (BPMN, flowcharts), writing functional specifications, bridging business/technical gaps.

*   **🚦 `project-onboarder`**:
    *   **Focus:** Designing/managing the onboarding process for new projects/teams, coordinating initial setup (tools, access), facilitating role clarity, managing onboarding documentation/checklists.
    *   **Use When:** Setting up a new project environment, onboarding new team members, defining initial roles for a project, improving the onboarding experience.

*   **🔌 `agent-mcp-manager`**:
    *   **Focus:** Installing, removing, updating, and managing Model Context Protocol (MCP) servers based on user requests or system needs. Handles interaction with MCP server repositories and configurations.
    *   **Use When:** A user explicitly requests to add, remove, or update an MCP server, or when another mode determines an MCP server needs management.

*   **💻 `code`**:
    *   **Focus:** General-purpose software engineering tasks, writing/editing code, debugging, implementing features when a more specialized mode isn't clearly indicated or required.
    *   **Use When:** Implementing specific code changes requested, debugging issues across domains, tasks not clearly fitting another mode's core focus.

*   **🏗️ `architect`**:
    *   **Focus:** Inquisitive planning, high-level design thinking, exploring options, defining non-functional requirements, initial task breakdown before handing off to specialized modes.
    *   **Use When:** Initial exploration of a complex problem, planning phases, defining high-level approach or architecture before detailed design/implementation.

*   **❓ `ask`**:
    *   **Focus:** Answering questions, providing information on software development, technology topics.
    *   **Use When:** You need information or explanation rather than direct action on the codebase or project.

*   **🪲 `debug`**:
    *   **Focus:** Systematic problem diagnosis and resolution, analyzing logs, identifying root causes of bugs or system failures.
    *   **Use When:** A specific bug or failure needs investigation and fixing.

*   **🪃 `orchestrator`**:
    *   **Focus:** Coordinating complex tasks by delegating sub-tasks to appropriate specialized modes.
    *   **Use When:** A large task clearly requires input and actions from multiple different specialized modes sequentially or in parallel.

## 🔄 Handling Overlap

*   **Lead vs. Manager vs. HoD:** Use the role that directly manages the individuals involved or owns the scope (team vs. multiple teams vs. department). HoD for department strategy, EM for managing leads and cross-lead coordination, Lead for team-specific technical direction and execution.
*   **Platform vs. DevOps:** Platform *builds* the internal platform/tools. DevOps *uses* the platform to build application pipelines and manage operations. Use Platform Lead for tasks related to creating shared infra/tools; use DevOps Lead for application-specific CI/CD, deployment, and operational monitoring.
*   **Architect vs. Team Lead:** Architect defines *high-level* design and cross-cutting standards. Team Leads oversee *detailed* design and implementation within their domain, adhering to architectural guidance.
*   **PO vs. BA:** PO owns the *what* and *why* (product vision, backlog priority). BA often focuses on the *how* (detailed requirements, process modeling, bridging business/tech details). If both exist, they collaborate closely. If only PO exists, they absorb more BA tasks.

This guide provides a starting point. The best mode may sometimes depend on the specific context and organizational structure.