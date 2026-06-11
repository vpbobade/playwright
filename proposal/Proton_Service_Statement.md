# Statement of Work: Proton Integration with Playwright Framework

---

**The Service shall consist of:** Altimetrik is engaged with the customer to deliver the end-to-end integration of the existing Playwright test automation framework with the **Proton test management platform**. The integration replaces the current Xray-based test management workflow, enabling automated pre-execution approval validation, test run creation, result submission, and PDF report upload via Proton's REST API. The delivery is planned as a single 13-week engagement. All production deployment activities are planned to complete by **20-Sep-2026**. Business validation, 4-week hypercare, handover, and Xray decommission activities will continue through the project closure timeline.

---

## The project is scoped as below:

| Area | Scope |
|------|-------|
| Pre-Execution Approval | Current Xray approval check is replaced by `validateProtonTestCase.groovy`, which queries the Proton API for test case approval status before pipeline execution begins. |
| Test Run Management | Playwright test runs are created and managed in Proton via REST API (JSON/HTTPS), replacing the existing Xray test run creation workflow. |
| Result Submission | Test execution results (pass/fail/skip) are mapped using Jira-aligned test case IDs (e.g., `DNIGMP-188`) and submitted to Proton via `protonIntegration.groovy`. |
| Report Upload | Existing PDF report and `results.json` are uploaded as attachments to the Proton test run. Report format and structure remain unchanged (~80% code reuse). |
| Pipeline Wiring | All three language runners (TypeScript, JavaScript, Python) and `Jenkinsfile` are updated to route through the Proton integration and approval validation steps. |
| Sandbox Validation | Full end-to-end integration is validated against a Proton sandbox/test project before production deployment to avoid polluting live data. |
| Infrastructure | 1-week setup for API access provisioning, sandbox environment configuration, and connectivity confirmation. |
| Discovery | API documentation review, concept mapping, connectivity confirmation, and design document sign-off (Weeks 1–3). |

---

## Key Dependencies

- Proton must expose a **REST API (JSON/HTTPS)** supporting test run creation, result submission, and file attachment upload programmatically. Without this, integration is not feasible and will require re-scoping.
- **Proton team** must provision API credentials, sandbox environment access, and confirm the Jira-to-Proton test case ID mapping before Week 3. Any delay will require re-scoping and follow the change management process.
- **Jenkins pipeline infrastructure**, including all three language runners (TypeScript/JavaScript/Python), must be operational and accessible before kick-off (**17-Jun-2026**). Any platform delay will cascade to all sprint timelines.
- The **existing Xray integration** must remain fully operational and stable through the parallel run window to enable accurate result reconciliation between the legacy Xray workflow and the new Proton integration.
- Any change in scope or estimation will follow the change request process.
- **Proton team** to confirm API access, sandbox provisioning, and environment connectivity before project kick-off.
- Approval status validation, parallel test run readiness, and pipeline retrofit activities are consolidated into Weeks 8–9. Pipeline wiring (all three runners and `Jenkinsfile`) and production deployment readiness must complete in line with the revised milestone plan, with production deployment completed by **20-Sep-2026**.
- **Source/test-suite change freeze windows** must be published by the customer at least two weeks in advance. Unplanned changes to the Playwright test suite during the production readiness window may impact reconciliation baselines and require re-estimation.
- Proton team, Data Owners, and Business SMEs must align to project timelines for API review, approval, and UAT sign-off. Any delays must follow the change management process. The customer's QA/Ops team must formally support the parallel run window before the applicable production deployment readiness window.

---

## Key Assumptions

- Infrastructure setup and Proton API access provisioning should be aligned with delivery dates and completed before kick-off.
- Architecture review and approval from the customer must be completed within the development timeline.
- Proton team alignment for the Jira-to-Proton test case ID mapping must be confirmed before Sprint 1.
- As-Is Playwright pipeline configurations (`Jenkinsfile`, DAG/runner scripts for TypeScript, JavaScript, and Python) will be made available for analysis and mapping prior to Sprint 1 (**17-Jun-2026**).
- Jenkins agent/serverless compute capability is enabled in all environments before the start of the project.
- All required sign-offs, approvals, and alignments should be completed within the delivery timeline.
- Test data should be available in DEV and QA environments.
- UAT sign-off should be aligned with the delivery timeline. Any delay will result in re-estimation and follow the change management process.
- Any custom utility built by the customer for Proton integration is expected to support all pipeline migration requirements. Any deviation will result in re-estimation and follow the change management process.
- Project scope covers the current in-scope integration inventory of **3 language runners** across **1 unified Jenkinsfile** within the Playwright framework.
- Any deviation in the number/complexity of integration components or delay in enabling the required infrastructure will need re-estimation and follow a change management process.
- A minimum contingency factor of **10%** is included for code retrofit and stabilisation changes identified during integration, validation, or production readiness. Any utilisation beyond the agreed scope or assumptions will follow the change management process.
- All environments are assumed to be ready before development kick-off with test data; any delay will have a cascading impact on timelines.
- **4 weeks of hypercare** post-production deployment are included, covering parallel run validation and handover to the OPS team.

---

## Out of Scope

- Modifications to the Proton platform itself
- Creation, management, or migration of Proton test cases
- Reverse engineering of source test systems or Xray historical data migration
- Integration between source applications and Proton beyond automated test result submission
- Platform setup, infrastructure provisioning, or CI/CD environment configuration
- Data anonymisation or masking of test data
- Identifying or implementing test automation use cases not in scope of this engagement
- End-user training on Proton
- Metadata migration from Xray/Jira to Proton or Unity Catalog to Collibra
- PQM Services or Change Co-ordinator services

---

## Team Structure

| Role | Count | Responsibilities |
|------|:-----:|-----------------|
| Senior Test Automation Engineer (Lead) | 1 | Lead test automation architecture, code reviews, and technical governance for the Playwright → Proton integration. Design `protonIntegration.groovy` and `validateProtonTestCase.groovy` structure, pipeline topology, and API connectivity model. Own technical design specification and integration handbook. Drive the full delivery: discovery, development, testing, UAT support, and production deployment. Lead knowledge transfer and Xray decommission handover to the OPS team. |

---

*This statement of work is valid for 30 days from the date of issue. All costs are in CHF and exclusive of applicable taxes unless otherwise stated. Any scope changes will follow the formal change management process.*
