<!-- Rapider Official App SOW & Specification | App #106: Automated Software Testing (automated-software-testing) | Domain: DEV -->

# #106 Automated Software Testing (`automated-software-testing`) — Scope of Work (SOW)

- **App Number & Name:** `#106 Automated Software Testing`
- **Proposed App Key:** `automated-software-testing`
- **Domain / Suite & Model Prefix:** `DEV` (`Dev*`) — Category `11. Software Development & DevOps`
- **Representative Benchmark (`P1`):** `BrowserStack`
- **Combined Feature Catalog:** [../combined-features/106-automated-software-testing-features.md](../combined-features/106-automated-software-testing-features.md)

---

## 1. Executive Outcome & Target Audience

**Automated Software Testing (`automated-software-testing`)** unifies test case authoring, cross-browser/real-device execution matrices, CI/CD test report observability, Percy-style visual snapshot regression review, automated WCAG 2.2 AA accessibility auditing, and release quality gates inside the Rapider `DEV` suite. Instead of juggling disconnected spreadsheets, raw CI console logs, unreviewed screenshot folders, and flaky E2E specs that erode developer trust, QA and engineering teams govern software quality end-to-end from `ApmIssue` requirement to production sign-off.

- **SME & Startup Fast-Path:** A lean product team connects their Playwright, Cypress, or JUnit CI pipeline via a single reporter token (`ingestTestRunReport`), immediately gaining rich failure screenshots/videos/HAR logs, visual diff baselines across `390px`/`768px`/`1440px` (`light`/`dark`), automatic flaky-spec detection, and 1-click bug creation into `ApmIssue`.
- **Enterprise Progressive Disclosure:** Multi-squad organizations unlock hierarchical `DevTestSuite` release plans, requirements traceability matrices against `ApmEpic` / `ApmIssue`, multi-OS/browser `DevTestEnvironmentMatrix` sharding, `#105` feature-flag variant matrix runs, mandatory `DevQualityGate` pass-rate & WCAG gates with governed Home `WorkItem` waivers, and grounded AI test generation/locator self-healing proposals.
- **Measurable Business & Engineering Outcomes:**
  1. Cut escaped production UI, functional, and accessibility defects by **60%–80%** via automated cross-viewport visual baselines and WCAG 2.2 AA release gates.
  2. Reclaim **30%–50% of lost CI developer hours** by automatically detecting, scoring (`Decimal128` `flakinessRate`), and quarantining flaky E2E tests before they block unrelated pull requests.
  3. Compress failed-test triage from **45 minutes to under 5 minutes** by pairing video/HAR/DOM evidence directly with correlated `#104` backend stack traces (`traceId`).
- **Top 6 Global Benchmarks Synthesized (`P1`–`P6`):** `BrowserStack` (`P1` — Representative Product), `Sauce Labs` (`P2`), `Tricentis Tosca & qTest` (`P3`), `LambdaTest HyperExecute` (`P4`), `Microsoft Azure Test Plans & Playwright Testing` (`P5`), and `ServiceNow Automated Test Framework (ATF)` (`P6`).

---

## 2. In-Scope, Out-of-Scope & Suite Ownership Boundaries

### In-Scope
- Authoring, versioning, and organizing `DevTestCase` items (`FUNCTIONAL`, `E2E_UI`, `API`, `VISUAL`, `ACCESSIBILITY`, `SECURITY_ACL`) and `DevTestSuite` hierarchies linked to `ApmEpic`/`ApmIssue` (`AST-001`–`AST-004`).
- Managing `DevTestEnvironmentMatrix` configurations (browsers, real mobile devices, `390px`/`768px`/`1440px` viewports, `light`/`dark` themes), orchestrating/ingesting CI `DevTestRun` and `DevTestResult` executions, and storing video/HAR/trace artifacts in Platform Files (`AST-005`–`AST-009`, `AST-020`, `AST-021`).
- Percy-style `DevVisualSnapshot` baseline comparison, stabilization masking, side-by-side approval/rejection, and automated `DevAccessibilityFinding` WCAG 2.2 AA violation tracking (`AST-010`–`AST-012`).
- `Decimal128` flakiness scoring, smart `QUARANTINED` workflow, `#104`/`#105` cross-app test correlation, `DevQualityGate` enforcement with Home `WorkItem` waivers, exploratory charters, and grounded AI QA assistants (`AST-013`–`AST-019`, `AST-022`–`AST-028`).

### Out-of-Scope
- Static source-code SAST, cyclomatic complexity, code smell analysis, and line-level unit-test Sonar coverage Duplication gates (owned by `#107 Code Quality & Static Analysis`).
- Production live-user runtime crash ingestion and source-map symbolication (owned by `#104 Application Error Tracking`).
- Agile sprint backlog prioritization, story-point estimation, and roadmap capacity planning (owned by `APM` / `planning` and `#108 Product Roadmap Management`).
- Infrastructure load/DDoS network packet simulation and cloud host telemetry (owned by `#083 Cloud Infrastructure Monitoring`).

### Cross-Suite Ownership & Integration Contract

| Domain / App | Owns (Canonical System of Record) | Integration Contract with `#106` (`automated-software-testing`) |
| :--- | :--- | :--- |
| **`#106` (`automated-software-testing`)** | `DevTestCase`, `DevTestSuite`, `DevTestEnvironmentMatrix`, `DevTestRun`, `DevTestResult`, `DevVisualSnapshot`, `DevAccessibilityFinding`, `DevQualityGate` | Publishes `dev.test.run_completed.v1` and `dev.test.quality_gate_evaluated.v1` events; serves requirement coverage & pass-rate metrics. |
| **`APM` (`planning` / `apm`)** | `ApmProject`, `ApmEpic`, `ApmSprint`, `ApmIssue` | `DevTestCase.requirementIssueIds` links user stories for coverage; failed `DevTestResult` or flaky quarantine creates/links bug `ApmIssue` records. |
| **`#104` (`application-error-tracking`)** | `DevErrorIssue`, `DevErrorEvent` | `DevTestResult` stores W3C `traceId` linking E2E `500` failures to `#104` stack traces; `#104` AI reproduction steps scaffold draft regression `DevTestCase` items. |
| **`#105` (`feature-flag-management`)** | `DevFeatureFlag`, `DevFlagEnvironment` | `DevTestRun` accepts `flagOverrides` (`#105` keys/variants) so both `on` and `off` code paths are verified prior to production rollout. |
| **`#107` (`code-quality-and-static-analysis`)** | `DevCodeAnalysisRun`, `DevCodeQualityGate` | `#106` handles dynamic runtime/UI/API/visual/WCAG execution gates while `#107` handles static AST/SAST/coverage gates on pull requests. |
| **Platform Core Services** | Identity/RBAC, Secret Manager, Files/Drive, Notebooks, Home `WorkItem`s, `projectChannelMessage` | Screenshots, `.webp` videos, Playwright traces, and HAR logs live in Platform Files; quality-gate waiver requests emit Home `WorkItem`s; AI & QA reviews use `projectChannelMessage`. |

---

## 3. Primary Web Pages & Sidebar Navigation Architecture (12 Pages)

Every visible sidebar section strictly enforces the **Minimum 3 Items Rule** (`Test Repository & Suites` = 3 items, `Execution & Visual QA` = 3 items, `Observability & Gates` = 3 items; detail and drawer routes set `displayOnMenu: false`).

| # | Route | Page Title | Sidebar Section | Menu Visible | Key Components & UX Standards |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | `dashboard` | Quality & Test Pulse | `Test Repository & Suites` | `true` (Order 1) | KPI cards (`countSWR`/`findSWR`) for 7d Pass Rate %, Active Suites, Unreviewed Visual Diffs, Open WCAG Criticals, and Quarantined Specs; recent `DevTestRun` timeline. |
| 2 | `test-cases` | Test Case Catalog | `Test Repository & Suites` | `true` (Order 2) | Dual Table + `<rapider-kanban>` Lifecycle Board (`DRAFT`, `READY`, `QUARANTINED`, `DEPRECATED`); `#activeFilterTagsBar` with `Clear all`; `ApmIssue` coverage badge; clickable case title/code (`test-case-drawer` edit / run history). |
| 3 | `test-suites` | Suites & Release Plans | `Test Repository & Suites` | `true` (Order 3) | Hierarchical `DevTestSuite` table with target pass-rate (`Decimal128`), linked `ApmEpic`, scheduled nightly trigger toggle, and **Trigger Suite Run** primary CTA. |
| 4 | `test-runs` | CI Runs & Device Matrix | `Execution & Visual QA` | `true` (Order 4) | Real-time & historical `DevTestRun` list showing Git branch/PR, `DevTestEnvironmentMatrix` badges, pass/fail/flaky bar, duration, and clickable run identifier (`test-run-detail`). |
| 5 | `visual-reviews` | Visual Regression & Baselines | `Execution & Visual QA` | `true` (Order 5) | `<rapider-kanban>` & Grid (`UNREVIEWED_DIFF`, `APPROVED_BASELINE`, `REJECTED_REGRESSION`) across `390px`/`768px`/`1440px` and `light`/`dark` themes; clicks through to `visual-snapshot-detail`. |
| 6 | `accessibility` | WCAG Accessibility Audits | `Execution & Visual QA` | `true` (Order 6) | `DevAccessibilityFinding` table grouped by WCAG 2.2 rule (`AA`/`AAA`), route, severity (`CRITICAL`, `SERIOUS`, `MODERATE`), DOM selector, and 1-click `ApmIssue` bug creation. |
| 7 | `flaky-quarantine` | Flaky Tests & Quarantine | `Observability & Gates` | `true` (Order 7) | Leaderboard of specs sorted by `Decimal128` `flakinessRate`, flip-flop commit evidence, **Quarantine Spec** / **Restore to Ready** guarded actions, and linked stabilization `ApmIssue`. |
| 8 | `quality-gates` | Release Gates & Matrices | `Observability & Gates` | `true` (Order 8) | Tabbed configuration for `DevQualityGate` rules (pass %, max WCAG criticals, visual sign-off) and reusable `DevTestEnvironmentMatrix` browser/device profiles + Home `WorkItem` waivers. |
| 9 | `analytics` | Coverage & Speed Analytics | `Observability & Gates` | `true` (Order 9) | `ApmEpic` requirement test coverage matrix, slowest p95 spec leaderboard, browser/OS failure heatmap, and Save-to-Notebook report export. |
| 10 | `test-run-detail` | Test Run Diagnostics & Logs | *(Hidden)* | `false` | Per-browser/viewport `DevTestResult` breakdown, embedded video/screenshot/HAR trace links (Platform Files), `#104` `traceId` jump link, **Create Bug (`ApmIssue`)**, and AI Failure RCA (`projectChannelMessage`). |
| 11 | `visual-snapshot-detail` | Visual Diff Inspector | *(Hidden)* | `false` | Side-by-side / slider / onion-skin baseline vs. candidate image comparator, `Decimal128` pixel-diff badge, dynamic mask region overlay, inline `projectChannelMessage` thread, and **Approve Baseline** / **Reject** buttons. |
| 12 | `test-case-drawer` | Create / Edit Test Case | *(Hidden)* | `false` | Sliding form drawer for `DevTestCase` steps, parameter datasets, `ApmIssue` requirement links, and spec path; enforces `try/catch/finally` button reset, SWR cache clear, broadcast, and auto-close. |

**Mandatory Rapider UI Compliance across all 12 Pages:**
- Initial data loads exclusively invoke `window.rapiderApi.findSWR` and `countSWR` with zero redundant `isDeleted` filter clauses; local in-memory arrays filter `item.isDeleted !== true` and perform optimistic updates on edit/quarantine/approve/delete.
- Tables never render a standalone "View" button in `Actions`; primary identifiers (`runNumber`, `caseCode`, `suiteName`, `snapshotName`) navigate to detail views; `Edit` uses icon + text and `Delete` uses icon-only with `aria-label="Delete"`.
- Primary and destructive confirmation buttons enforce `#ffffff !important` text contrast; native `alert`/`confirm`/`prompt` dialogs are strictly banned.

---

## 4. Canonical Data Models (`Dev*` — 8 Models)

All models omit `projectId`, use backend-generated UUIDs (`00000000-xxxx-xxxx-xxxx-xxxxxxxxxxxx` in deterministic fixtures), enforce optimistic `version` concurrency, and store precision ratios as `Decimal128`.

| Model Name | Key Fields & Types | Relationships & External Refs | Invariants & Lifecycle |
| :--- | :--- | :--- | :--- |
| **`DevTestCase`** | `id` (UUID), `caseCode` (String, e.g., `TC-1042`), `title` (String), `testType` (`FUNCTIONAL` \| `E2E_UI` \| `API` \| `VISUAL` \| `ACCESSIBILITY` \| `SECURITY_ACL`), `automationMode` (`AUTOMATED` \| `MANUAL` \| `HYBRID`), `framework` (`PLAYWRIGHT` \| `CYPRESS` \| `SELENIUM` \| `APPIUM` \| `JUNIT` \| `NONE`), `specFilePath` (String?), `steps` (JSON[]), `parameterDataset` (JSON[]?), `flakinessRate` (`Decimal128`), `status` (`DRAFT` \| `READY` \| `QUARANTINED` \| `DEPRECATED`), `priority` (`P0` \| `P1` \| `P2`), `version` (Integer) | Refs `requirementIssueIds` (`ApmIssue[]`), `stabilizationIssueId` (`ApmIssue`?), `ownerUserId` (Platform Identity) | `caseCode` unique per workspace; `flakinessRate` in `[0.0000, 100.0000]`; transitioning `status -> QUARANTINED` records mandatory reason and excludes failures from blocking standard PR gates while continuing execution monitoring. |
| **`DevTestSuite`** | `id` (UUID), `name` (String), `slug` (String), `suiteKind` (`STATIC` \| `TAG_QUERY`), `includedCaseIds` (UUID[]), `tagFilterQuery` (String?), `defaultMatrixId` (UUID), `qualityGateId` (UUID?), `cronSchedule` (String?), `targetPassRate` (`Decimal128`), `version` (Integer) | Refs `DevTestEnvironmentMatrix`, `DevQualityGate`, optional `linkedApmEpicId` (`ApmEpic`) | `slug` unique per workspace; `STATIC` suites require `>= 1` non-deprecated `DevTestCase` to trigger an automated run. |
| **`DevTestEnvironmentMatrix`** | `id` (UUID), `name` (String), `targets` (JSON[] — `{ browser, os, deviceModel?, viewportWidth, viewportHeight, theme: 'LIGHT'\|'DARK', locale }`), `parallelShards` (Integer), `maxRetries` (Integer), `tunnelProfileKey` (String?), `isDefault` (Boolean), `version` (Integer) | Referenced by `DevTestSuite` and `DevTestRun` | Requires `>= 1` target combination; `parallelShards >= 1` and `maxRetries` in `0..5`. |
| **`DevTestRun`** | `id` (UUID), `runNumber` (String, e.g., `RUN-8821`), `suiteId` (UUID?), `matrixId` (UUID), `triggerSource` (`CI_CD` \| `MANUAL` \| `SCHEDULED_CRON` \| `POST_DEPLOY`), `branchName` (String), `commitSha` (String), `pullRequestRef` (String?), `targetBaseUrl` (String), `flagOverrides` (JSON?), `status` (`QUEUED` \| `RUNNING` \| `PASSED` \| `FAILED` \| `FLAKY_PASSED` \| `CANCELLED`), `totalCount` (Integer), `passedCount` (Integer), `failedCount` (Integer), `quarantinedCount` (Integer), `passRatePercent` (`Decimal128`), `gateEvaluationStatus` (`PASSED` \| `BLOCKED` \| `WAIVED`), `durationMs` (Long), `startedAt` (DateTime), `completedAt` (DateTime?), `version` (Integer) | Belongs to `DevTestSuite` & `DevTestEnvironmentMatrix`; `flagOverrides` refs `#105` keys; `threadChannelId` (`projectChannelMessage`) | Terminal run counts & `passRatePercent` (`Decimal128`) are immutable once `completedAt` is sealed (except `gateEvaluationStatus` transitioning `BLOCKED -> WAIVED` via approved Home `WorkItem`). |
| **`DevTestResult`** | `id` (UUID), `runId` (UUID), `testCaseId` (UUID?), `targetDescriptor` (String, e.g., `Chromium 130 / macOS / 1440px / DARK`), `status` (`PASSED` \| `FAILED` \| `FLAKY_RETRY_PASSED` \| `SKIPPED` \| `QUARANTINED_FAILED`), `attemptCount` (Integer), `failureCategory` (`PRODUCT_BUG` \| `AUTOMATION_LOCATOR_DRIFT` \| `ENVIRONMENT_OUTAGE` \| `VISUAL_DIFF` \| `FLAKY`?), `errorMessage` (String?), `stackTrace` (String?), `artifactFileIds` (UUID[]), `backendTraceId` (String?), `durationMs` (Long), `version` (Integer) | Belongs to `DevTestRun` and `DevTestCase`; `artifactFileIds` ref Platform Files/Drive; `linkedBugIssueId` refs `ApmIssue`; `backendTraceId` correlates `#104` | **Append-only execution evidence** for status, timing, error stack, and artifact references; post-run triage mutates only `failureCategory` and `linkedBugIssueId`. |
| **`DevVisualSnapshot`** | `id` (UUID), `runId` (UUID), `snapshotKey` (String), `routeOrComponent` (String), `viewportWidth` (Integer), `theme` (`LIGHT` \| `DARK`), `baselineFileId` (UUID?), `candidateFileId` (UUID), `diffOverlayFileId` (UUID?), `diffPercentage` (`Decimal128`), `ignoredRegions` (JSON[]), `reviewStatus` (`MATCHED` \| `UNREVIEWED_DIFF` \| `APPROVED_BASELINE` \| `REJECTED_REGRESSION`), `reviewedByUserId` (UUID?), `reviewedAt` (DateTime?), `version` (Integer) | Belongs to `DevTestRun`; image `fileId`s ref Platform Files/Drive | `diffPercentage > toleranceThreshold` initializes `UNREVIEWED_DIFF`; approving promotes `candidateFileId` as the new branch baseline without overwriting historical `DevVisualSnapshot` audit rows. |
| **`DevAccessibilityFinding`** | `id` (UUID), `runId` (UUID), `routePath` (String), `theme` (`LIGHT` \| `DARK`), `wcagCriterion` (String, e.g., `1.4.3 Contrast (Minimum)`), `ruleId` (String), `severity` (`CRITICAL` \| `SERIOUS` \| `MODERATE` \| `MINOR`), `domSelector` (String), `htmlSnippet` (String), `remediationHint` (String), `status` (`OPEN` \| `LINKED_TO_BUG` \| `FALSE_POSITIVE_WAIVED` \| `RESOLVED`), `linkedBugIssueId` (UUID?), `version` (Integer) | Belongs to `DevTestRun`; `linkedBugIssueId` refs canonical `ApmIssue` | `htmlSnippet` sanitized on display via `escapeHtml()`; waiving `CRITICAL` findings requires QA Lead permission and audit reason. |
| **`DevQualityGate`** | `id` (UUID), `name` (String), `minPassRateThreshold` (`Decimal128`), `maxCriticalWcagCount` (Integer), `requireVisualBaselineApproval` (Boolean), `blockOnNewFlakyTests` (Boolean), `requireWaiverApproval` (Boolean), `isDefault` (Boolean), `version` (Integer) | Referenced by `DevTestSuite` and `DevTestRun`; waivers create Platform Home `WorkItem` | `minPassRateThreshold` stored as `Decimal128` (`0.0000`–`100.0000`); if `requireWaiverApproval = true`, only an approved Home `WorkItem` transitions a blocked run to `WAIVED`. |

---

## 5. Core End-to-End User Journeys

1. **SME CI Pipeline Ingestion -> Failure Inspection -> 1-Click `ApmIssue` Bug:**
   - Developer pushes PR `#412`; Playwright CI finishes and posts results to `ingestTestRunReport`.
   - QA opens `#/test-runs`, sees `RUN-8821` (`FAILED`, `96.50%` pass rate), clicks `RUN-8821` to open `#/test-run-detail?id=...`, inspects the failed `Checkout Dark Mode` step video, console error, and correlated `#104` `backendTraceId`, and clicks **Create APM Bug**—creating a pre-populated `ApmIssue` linked to the run.
2. **Percy-Style Multi-Theme Visual Diff Review & Baseline Promotion:**
   - Design system update modifies primary card padding, flagging 4 `UNREVIEWED_DIFF` items on `#/visual-reviews` across `390px` and `1440px` (`LIGHT` and `DARK`).
   - Frontend Lead clicks a snapshot card into `#/visual-snapshot-detail`, toggles the side-by-side diff overlay (`diffPercentage = 2.1400%`), verifies intentional styling on `LIGHT`, approves the baseline (`reviewVisualSnapshot`), and rejects `DARK` where a subtle text-contrast overlap appeared—blocking merge until fixed.
3. **Flaky Spec Detection & Smart Quarantine:**
   - `TC-1099` fails on attempt 1 and passes on retry across 4 consecutive commits (`flakinessRate = 28.5000%`).
   - On `#/flaky-quarantine`, QA Lead clicks **Quarantine Spec**, entering reason `"Third-party map tile timeout"`, transitioning `TC-1099` to `QUARANTINED` and creating stabilization `ApmIssue` `APM-510` so PR pipelines stay green while reliability is fixed.
4. **Release Quality Gate Breach & Governed Home `WorkItem` Waiver:**
   - Hotfix `v2.4.1` passes `100%` of functional E2E tests on `RUN-8840`, but `DevQualityGate` blocks promotion due to 1 `MODERATE`/`SERIOUS` legacy WCAG violation in an untouched footer component.
   - Engineering Lead requests an emergency hotfix waiver; `requestQualityGateWaiver` emits a shared Rapider Home `WorkItem` to the QA Director with run metrics and risk justification. Approval transitions `gateEvaluationStatus -> WAIVED` with an immutable audit entry.
5. **List Search, Filter Chips, Click-Through & Back Restoration:**
   - On `#/test-cases`, user searches `"checkout"` and selects `Type: E2E_UI` + `Status: READY`. `#activeFilterTagsBar` displays `Search: "checkout" ✕`, `Type: "E2E_UI" ✕`, `Status: "READY" ✕`, and `Clear all`.
   - User navigates from `#/test-runs` into `#/test-run-detail?id=...` and clicks `#btnGoBack`, returning to `#/test-runs` with active filter tags and scroll position intact.

---

## 6. Consolidated Feature Priorities & Work Packages

### `P0` Foundation (MVP Release-Ready Core)
- **WP-P0-1: Test Case Catalog, Suites & `ApmIssue` Traceability (`AST-001`–`AST-003`, `AST-016`):** `DevTestCase` & `DevTestSuite` CRUD, `<rapider-kanban>` lifecycle board, `ApmEpic`/`ApmIssue` coverage links, `#activeFilterTagsBar`, `#/test-cases`, `test-case-drawer`, `#/test-suites`.
- **WP-P0-2: Environment Matrices, CI Report Ingestion & Evidence Viewer (`AST-005`–`AST-007`):** `DevTestEnvironmentMatrix`, `DevTestRun`, `DevTestResult` schemas, Playwright/Cypress/JUnit report ingestion command, Platform Files screenshot/video/HAR attachments, `#/dashboard`, `#/test-runs`, `#/test-run-detail`.
- **WP-P0-3: Visual Baselines & WCAG 2.2 AA Auditing (`AST-010`, `AST-011`):** `DevVisualSnapshot` baseline/candidate comparison (`#/visual-reviews`, `#/visual-snapshot-detail`) and `DevAccessibilityFinding` WCAG scanner ingestion (`#/accessibility`).
- **WP-P0-4: Flakiness Quarantine, Defect Escalation & Quality Gates (`AST-013`–`AST-015`):** `Decimal128` flakiness engine (`#/flaky-quarantine`), `#104`/`ApmIssue` defect escalation, and `DevQualityGate` evaluation + Home `WorkItem` waivers (`#/quality-gates`).

### `P1` Enterprise Scale & Continuous Quality
- **WP-P1-1: Parameterized Datasets, Parallel Sharding & Staging Tunnels (`AST-004`, `AST-008`, `AST-009`):** Data-driven parameter sets, shard/retry policies, and Secret-Manager-backed private staging runner profiles.
- **WP-P1-2: Role/ACL Boundary Tests, Crash-to-Test & Flag Matrix Runs (`AST-012`, `AST-018`–`AST-021`):** Multi-role impersonation security specs, `#104` crash reproduction import, `#105` flag variant matrix runs, API smoke assertions, and cron nightly runs.
- **WP-P1-3: Coverage & Speed Analytics (`AST-017`):** `#/analytics` requirement coverage matrix, p95 duration bottleneck charts, and Notebook export.

### `P2` Adjacent Capabilities & Grounded AI Agents
- **WP-P2-1: Exploratory Charters & Synthetic Data Teardown (`AST-022`, `AST-023`):** Exploratory charter sessions and automated test-fixture cleanup verification.
- **WP-P2-2: Grounded AI Quality Agents (`AST-024`–`AST-028`):** `ApmIssue`-to-`DevTestCase` generator, DOM self-healing locator diff proposals, cascading CI failure root-cause clustering, visual diff noise filter, WCAG HTML fix snippets, and suite deduplication advisor on `projectChannelMessage`.

---

## 7. Roles, Permissions & Field-Level Governance

| Role | Permitted Actions | Restricted / Field-Level Boundaries |
| :--- | :--- | :--- |
| **QA Engineer / SDET** | Create/edit `DevTestCase` & `DevTestSuite`; trigger `DevTestRun`; classify `DevTestResult` failures; review `DevVisualSnapshot` non-prod diffs; link `ApmIssue` bugs; invoke AI QA agents on `projectChannelMessage`. | Cannot waive blocked production `DevQualityGate` runs without Lead approval; cannot view plaintext staging tunnel secrets. |
| **Developer** | View all test cases, CI runs, artifacts, visual diffs, and WCAG findings; trigger branch/PR `DevTestRun`s; submit `DevQualityGate` waiver requests; apply AI locator/WCAG fix snippets in PRs. | Cannot unilaterally quarantine `P0` release-gate test cases or lower `DevQualityGate` `minPassRateThreshold` settings. |
| **QA Lead / Release Manager** | All QA Engineer actions + configure `DevQualityGate` thresholds, quarantine/restore `DevTestCase` specs, approve `main`/`prod` `DevVisualSnapshot` baselines, and approve/reject Home `WorkItem` gate waivers. | Cannot mutate historical sealed `DevTestRun` or `DevTestResult` execution counts/evidence; self-approval of own waiver request prohibited when 4-eyes policy enabled. |
| **Workspace Security Admin** | Manage private staging tunnel credentials in Platform Secret Manager, configure HAR/screenshot PII scrubbing policies, and set artifact retention TTLs. | Audited on all policy and retention mutations. |
| **CI Runner Identity** | Scoped `ingestTestRunReport`, `uploadTestArtifact`, and `evaluateQualityGate` for authorized suites/branches. | Zero interactive administrative or waiver-approval privileges. |

---

## 8. Technical APIs, Guarded Commands, Events & `requiredWorkflows`

### Guarded Domain Commands
All state transitions enforce `idempotencyKey`, `correlationId`, RBAC, and `expectedVersion`:
- `triggerTestSuiteRun(suiteId, matrixId?, branchName, commitSha, targetBaseUrl, flagOverrides?, idempotencyKey)` -> Initializes `DevTestRun` (`QUEUED`) and dispatches runner shards.
- `ingestTestRunReport(runId, framework, resultsPayload, visualSnapshots[], wcagFindings[], idempotencyKey)` -> Idempotently persists `DevTestResult`, `DevVisualSnapshot`, and `DevAccessibilityFinding`, computes `Decimal128` `passRatePercent` & `flakinessRate`, and evaluates `DevQualityGate`.
- `reviewVisualSnapshot(snapshotId, decision, comment?, ignoredRegions?, expectedVersion, idempotencyKey)` -> Transitions `UNREVIEWED_DIFF -> APPROVED_BASELINE | REJECTED_REGRESSION` and re-evaluates run quality gate.
- `quarantineTestCase(testCaseId, reason, createApmBug, expectedVersion, idempotencyKey)` -> Transitions `DevTestCase` to `QUARANTINED` and optionally creates linked `ApmIssue`.
- `requestQualityGateWaiver(runId, justification, expectedVersion, idempotencyKey)` / `decideQualityGateWaiver(runId, decision, comment, expectedVersion, idempotencyKey)` -> Routes and resolves governed Rapider Home `WorkItem`.

### Kafka Domain Events (Published & Consumed)
- **Published:** `dev.test.run_started.v1`, `dev.test.run_completed.v1`, `dev.test.quality_gate_blocked.v1`, `dev.test.quality_gate_passed.v1`, `dev.test.case_quarantined.v1`, `dev.test.visual_regression_detected.v1`.
- **Consumed:** `dev.deployment.preview_ready.v1` (auto-triggers post-deploy smoke `DevTestSuite`), `apm.issue.updated.v1` (flags linked `DevTestCase` items when requirement acceptance criteria change), `dev.error.regression_handoff.v1` (from `#104` to scaffold regression tests).

### `requiredWorkflows` in `app.manifest.json`
1. `dev-test-orchestration-and-ingest-wf` (Coordinates matrix shard execution, ingests JUnit/Playwright/WCAG reports, and computes `Decimal128` pass/flakiness metrics).
2. `dev-test-visual-diff-engine-wf` (Computes pixel/layout diffs between `baselineFileId` and `candidateFileId` in Platform Files while masking configured dynamic regions).
3. `dev-test-quality-gate-and-waiver-wf` (Evaluates `DevQualityGate` rules on completed runs and manages shared Home `WorkItem` waiver lifecycles).
4. `dev-test-ai-qa-agents-wf` (Grounded AI generator for test cases, failure clustering, locator drift diffs, and WCAG fixes on `projectChannelMessage`—human review mandatory before promoting cases or committing locator changes).

---

## 9. Security, Privacy, Compliance & Non-Functional Requirements

- **Test Credential Isolation & HAR Sanitization (SOC2 / GDPR):** Test runner credentials and private staging tunnel keys are never hardcoded in `DevTestCase` steps or `parameterDataset` JSON (validated server-side; must reference Platform Secret Manager placeholders). Ingested HAR network archives and console logs automatically strip `Authorization`, `Cookie`, and `Set-Cookie` headers before writing to Platform Files, ensuring \$0 exposure of session tokens.
- **XSS-Safe HTML Snippet & Error Rendering:** All `DevAccessibilityFinding.htmlSnippet`, DOM selectors, and `DevTestResult.errorMessage` payloads are rendered strictly as escaped text (`escapeHtml()`) so malicious or broken test payloads cannot execute scripts inside the QA UI.
- **Artifact Retention & Storage Hygiene:** Passing run videos/HARs follow configurable short TTLs (e.g., 14 days) while failed run evidence and approved `DevVisualSnapshot` baselines are retained per compliance policy (e.g., 180–365 days).
- **Accessibility & Responsive Parity:** Full WCAG 2.2 AA compliance across `390px`, `768px`, and `1440px` in both `light` and `dark` themes; keyboard-operable visual diff slider and table filters; `findSWR` cached views render `< 150ms` p95.

---

## 10. Deterministic Acceptance Criteria

1. **Zero `projectId` & Platform UUIDs:** All 8 `Dev*` schemas contain zero `projectId` fields, generate backend UUIDs on creation, and use `00000000-xxxx-xxxx-xxxx-xxxxxxxxxxxx` in seed fixtures.
2. **Idempotent CI Report Ingestion & `Decimal128` Metrics:** Replaying `ingestTestRunReport` with an identical `idempotencyKey` creates zero duplicate `DevTestResult` rows and computes exact `Decimal128` `passRatePercent` (`e.g., 98.7500%`) and `flakinessRate`.
3. **Secret Rejection & HAR Header Scrubbing:** Attempting to save a `DevTestCase` step containing a raw `Bearer eyJ...` token or `postgres://user:pass@...` URI fails validation; ingested HAR files strip `Authorization` and `Cookie` headers prior to storage.
4. **Visual Baseline Lifecycle:** Uploading a candidate screenshot with `diffPercentage > tolerance` sets `reviewStatus = UNREVIEWED_DIFF` and blocks a `DevQualityGate` with `requireVisualBaselineApproval = true` until `reviewVisualSnapshot` (`APPROVED_BASELINE`) completes.
5. **Smart Flaky Quarantine:** Quarantining `TC-1099` moves its `<rapider-kanban>` card to `QUARANTINED`, prevents its failures from failing standard PR gates, and creates/links a stabilization `ApmIssue`.
6. **Quality Gate Waiver via Home `WorkItem`:** Requesting a waiver on a `BLOCKED` `DevTestRun` emits a Rapider Home `WorkItem`; self-approval is rejected under 4-eyes policy, and authorized QA Lead approval transitions `gateEvaluationStatus -> WAIVED` with audit attribution.
7. **Sidebar Minimum 3 Items Rule:** All 3 visible sidebar sections (`Test Repository & Suites`, `Execution & Visual QA`, `Observability & Gates`) each contain exactly 3 visible items (`displayOnMenu: true`), while `test-run-detail`, `visual-snapshot-detail`, and `test-case-drawer` set `displayOnMenu: false`.
8. **SWR Clean Query & Optimistic Updates:** Every page uses `findSWR`/`countSWR` with zero `isDeleted` filter clauses; editing a test case, approving a visual baseline, or deleting a draft suite updates local state and `<rapider-kanban>` optimistically, clears SWR cache, and rolls back on simulated failure.
9. **Table Actions, Contrast & Dialog Ban:** Zero tables render a "View" button in `Actions`; primary identifiers (`runNumber`, `caseCode`, `suiteName`, `snapshotKey`) navigate to detail views; `Edit` is icon + text; `Delete` is icon-only with `aria-label="Delete"`; primary/danger buttons enforce `#ffffff` text; zero `alert`/`confirm`/`prompt` calls exist.
10. **Active Filter Tags & Clear All:** Searching or filtering `#/test-cases` or `#/test-runs` displays `#activeFilterTagsBar` with HTML-escaped dismissible chips and `Clear all`, synchronously updating list and `<rapider-kanban>` views.
11. **Drawer Auto-Close & `finally` Reset:** Saving or cancelling `test-case-drawer` closes the drawer, broadcasts `RECORD_CREATED`/`RECORD_UPDATED`, and restores the Save button state inside a `finally` block.
12. **Click-Through Navigation & Back State Restoration:** Clicking `RUN-8821` on `#/test-runs` transitions to `#/test-run-detail?id=...` without `<base href>` 404 diversion, renders test results, and `#btnGoBack` restores `#/test-runs` with active filters intact.
13. **Grounded AI Safety:** AI-generated test cases and self-healing locator diffs post as `DRAFT` proposals on `projectChannelMessage` citing `ApmIssue` / DOM evidence and never overwrite active `READY` specs without human confirmation.
14. **Theme & Responsive Validation:** Automated light/dark `validate_theme` checks and `390px`/`768px`/`1440px` layout validations pass with zero contrast violations or clipped controls.
