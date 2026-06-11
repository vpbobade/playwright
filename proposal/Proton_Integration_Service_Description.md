# Service Description: Proton Integration with Playwright Framework

---

## The Service

Altimetrik is engaged to deliver the end-to-end integration of the existing Playwright test automation framework with the **Proton test management platform**. The integration replaces the current Xray-based test management workflow with Proton, enabling automated test execution, approval validation, result submission, and PDF report upload via Proton's REST API. The delivery is planned as a single 13-week engagement, with all production deployment activities completed by **20-Sep-2026**. Business validation, hypercare, handover, and decommission of the Xray integration will continue through project closure.

---

## Project Scope

| Area | Scope |
|------|-------|
| Pre-Execution Approval | Current Xray approval check replaced by `validateProtonTestCase.groovy` — queries Proton API for test case approval status before pipeline execution. |
| Test Run Management | Playwright test runs created and managed in Proton via REST API (JSON/HTTPS), replacing Xray test run creation. |
| Result Submission | Test execution results (pass/fail/skip) mapped and submitted to Proton using Jira-aligned test case IDs (e.g., `DNIGMP-188`). |
| Report Upload | Existing PDF report and `results.json` uploaded as attachments to the Proton test run — format unchanged (~80% code reuse). |
| Pipeline Wiring | All three language runners (TypeScript, JavaScript, Python) and `Jenkinsfile` updated to route through the Proton integration. |
| Sandbox Validation | Full end-to-end integration validated against a Proton sandbox/test project before production deployment. |
| UAT & Hypercare | 4-week hypercare post-production deployment, including handover to the operations team and Xray integration decommission. |
| Xray Decommission | Out of scope for active development; decommission timeline aligned with Proton go-live. |

---

## Key Dependencies

- Proton must expose a **REST API (JSON/HTTPS)** supporting test run creation, result submission, and file attachment upload programmatically. Without this, integration is not feasible and will require re-scoping.
- **EDM / Proton team** must provision API credentials, sandbox environment access, and confirm the Jira-to-Proton test case ID mapping by **Week 3 (04-Jul-2026)**. Any delay will cascade to all sprint timelines.
- **Proton sandbox/test project** must be available and stable from **Week 4 (07-Jul-2026)** through **Week 12** to prevent pollution of live data during development and testing.
- The **Proton API must expose a test case approval status endpoint** to enable pre-execution pipeline gating — same pattern as the current Xray check. Any deviation will require re-design and follow the change management process.
- **Source change freeze windows** for the Playwright test suite must be published at least two weeks in advance. Unplanned changes during the production readiness window may impact reconciliation baselines and require re-estimation.
- **Proton team availability** of approximately **3 days** spread across the 13-week engagement is required for API onboarding, test data support, and UAT sign-off. Any unavailability must follow the change management process.
- All **pipeline infrastructure** (Jenkins, existing CI/CD runners for TypeScript/JavaScript/Python) must remain operational and accessible throughout the engagement.
- Any change in scope or estimation will follow the change request process.

---

## Key Assumptions

- Infrastructure setup and Proton API access provisioning will be completed before project kick-off (**17-Jun-2026**).
- Proton test cases use the same IDs as Jira (e.g., `DNIGMP-188`), or a clear, queryable mapping exists between the two systems — confirmed by Week 3.
- The existing **PDF report format** and `results.json` structure are accepted by Proton stakeholders without modification; approximately 80% of the existing Xray integration code is reused as-is.
- As-Is Playwright pipeline configurations (`Jenkinsfile`, runner scripts for TypeScript/JavaScript/Python) will be made available for analysis and mapping prior to Sprint 1 (**17-Jun-2026**).
- All required sign-offs, approvals, and architectural alignments will be completed within the delivery timeline. Any delay will result in re-estimation and follow the change management process.
- UAT sign-off will be aligned with the delivery timeline. Any delay will result in re-estimation and follow the change management process.
- Project scope covers the current in-scope inventory of **3 language runners** and **1 unified Jenkinsfile** across the Playwright framework.
- A minimum contingency factor of **10%** is included within the rework allocation (10 person days) for enhancement retrofit and stabilization changes identified during migration or UAT. Any utilisation beyond the agreed scope will follow the change management process.
- All environments are assumed to be ready before development kick-off; any delay will have a cascading impact on timelines.
- **4 weeks of hypercare** post-production deployment are included, covering parallel run validation and handover to the operations team.
- Serverless/agent compute capability for Jenkins pipelines is enabled in all environments before the start of the project.
- Any deviation in the number or complexity of integration components, or delays in enabling the required infrastructure, will require re-estimation and follow a change management process.

---

## Out of Scope

- Modifications to the Proton platform itself
- Creation, management, or migration of Proton test cases
- Reverse engineering of source test systems or Xray historical data migration
- Changes to existing Playwright test scripts beyond integration wiring
- Platform setup, infrastructure provisioning, or CI/CD environment configuration
- Data anonymisation or masking of test data
- End-user training on Proton
- Metadata migration from Xray/Jira to Proton
- Integration between source applications and Proton beyond test result submission
- PQM services or Change Co-ordinator services
- Identifying or implementing test automation use cases not in scope of this engagement

---

## Team Structure

| Role | Count | Responsibilities |
|------|:-----:|-----------------|
| Senior Test Automation Engineer (Lead) | 1 | Lead end-to-end delivery of the Proton integration. Design `protonIntegration.groovy` and `validateProtonTestCase.groovy` architecture. Own technical design specification, API connectivity, pipeline wiring across all three language runners (TypeScript/JavaScript/Python), and `Jenkinsfile` updates. Drive testing, UAT support, and production deployment. Lead knowledge transfer and Xray decommission handover to the operations team. |

---

## Effort Estimate

| Activity | Effort (Person Days) |
|----------|---------------------:|
| Discovery, Design & Development | 40 |
| Testing and Validation | 20 |
| Rework as per UAT Feedback | 10 |
| **Total Person Days** | **70** |
| **Total Person Months** | **3** |

---

## Project Timeline

| Weeks | Phase | Deliverables |
|-------|-------|-------------|
| 1–3 | Discovery | API docs reviewed, connectivity confirmed, concept map produced, design document signed off |
| 4–7 | Core Integration | `protonIntegration.groovy` — Standalone + Regression execution + error handling |
| 8–9 | Approval Validation | `validateProtonTestCase.groovy` wired into pipeline pre-execution checks |
| 9 | Pipeline Wiring | All 3 runners (TypeScript/JavaScript/Python) + `Jenkinsfile` updated |
| 10–12 | Testing & Validation | E2E tests across all language runners; failure scenarios covered |
| 12–13 | UAT & Rework | Rework based on UAT feedback; production deployment; handover |

**All production deployments to be completed by 20-Sep-2026.**

---

## Commercials

| Parameter | Value |
|-----------|-------|
| Engagement Model | Fixed Price |
| Average Day Rate (ADR) | CHF 181 |
| Working Days per Month | 21 |
| Monthly Cost | CHF 3,801 |
| Project Duration | 3 Months |
| **Total Project Cost** | **CHF 11,403** |

### Payment Milestones

| Milestone | Payment (%) | Amount (CHF) |
|-----------|:-----------:|-------------:|
| Project Kickoff | 30% | 3,421 |
| Development Complete (Week 9) | 40% | 4,561 |
| UAT Sign-Off & Go-Live (Week 13) | 30% | 3,421 |
| **Total** | **100%** | **11,403** |

---

*This service description is valid for 30 days from the date of issue. All costs are in CHF and exclusive of applicable taxes unless otherwise stated. Any scope changes will follow the formal change management process.*
