# Non-Functional Requirements (NFR) Checklist: {System/Feature Name}

*   **Date:** {YYYY-MM-DD}
*   **Version:** {Version Number}
*   **Author(s):** {Author Names}

## Overview

{Brief description of the system or feature these NFRs apply to.}

## NFR Categories

*(Fill in specific, measurable requirements under each relevant category. Add/remove categories as needed.)*

### 1. Performance
*   [ ] **Response Time:** {e.g., Average API response time < 200ms under X concurrent users}
*   [ ] **Throughput:** {e.g., System must process Y transactions per second}
*   [ ] **Load Capacity:** {e.g., System must support Z concurrent users without degradation}
*   [ ] **Resource Utilization:** {e.g., CPU/Memory usage below N% under peak load}

### 2. Scalability
*   [ ] **Horizontal Scalability:** {e.g., Ability to add more instances to handle increased load}
*   [ ] **Vertical Scalability:** {e.g., Ability to increase resources (CPU/RAM) of existing instances}
*   [ ] **Data Scalability:** {e.g., Ability to handle growth in data volume to X TB}

### 3. Availability & Reliability
*   [ ] **Uptime Requirement:** {e.g., 99.9% uptime during business hours}
*   [ ] **Mean Time Between Failures (MTBF):** {Target MTBF}
*   [ ] **Mean Time To Recovery (MTTR):** {Target MTTR < N minutes}
*   [ ] **Fault Tolerance:** {e.g., System remains operational if one node fails}
*   [ ] **Disaster Recovery (DR):** {e.g., RPO < 1 hour, RTO < 4 hours}

### 4. Security
*   [ ] **Authentication:** {e.g., MFA required for admin access}
*   [ ] **Authorization:** {e.g., Role-based access control implemented}
*   [ ] **Data Encryption:** {e.g., Data encrypted at rest (AES-256) and in transit (TLS 1.2+)}
*   [ ] **Vulnerability Management:** {e.g., No critical/high vulnerabilities allowed in production}
*   [ ] **Compliance:** {e.g., Adherence to GDPR, HIPAA, PCI DSS}
*   [ ] **Audit Logging:** {e.g., Security-relevant events logged}

### 5. Maintainability
*   [ ] **Code Quality:** {e.g., Adherence to defined coding standards, cyclomatic complexity limits}
*   [ ] **Modularity:** {Degree of coupling between components}
*   [ ] **Testability:** {e.g., Unit test coverage > N%}
*   [ ] **Deployability:** {e.g., Automated deployment process exists}
*   [ ] **Documentation:** {e.g., Key architectural decisions documented}

### 6. Usability
*   [ ] **Learnability:** {e.g., New user can complete core task X within N minutes}
*   [ ] **Efficiency:** {e.g., Experienced user can complete core task Y in < N steps/seconds}
*   [ ] **Accessibility:** {e.g., Compliance with WCAG 2.1 AA}

### 7. Other (Add as needed)
*   [ ] **Interoperability:** {Requirements for interacting with other systems}
*   [ ] **Portability:** {Requirements for running on different environments}
*   [ ] **Data Integrity:** {Requirements for data accuracy and consistency}
*   [ ] **Supportability:** {Requirements for monitoring, logging, diagnostics}

## Approval

*   **Approved By:** {Name/Role}
*   **Date:** {YYYY-MM-DD}