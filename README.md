# SauceDemo | Manual Testing Portfolio

![Status](https://img.shields.io/badge/Test%20Execution-74%2F74-2563eb)
![Pass Rate](https://img.shields.io/badge/Pass%20Rate-78.38%25-f59e0b)
![Release](https://img.shields.io/badge/Release-NOT%20READY-dc2626)

> A manual testing portfolio for the [Swag Labs (SauceDemo)](https://www.saucedemo.com/) sample e-commerce application, aligned with the **ISTQB Certified Tester Foundation Level (CTFL) v4.0.1** syllabus.
>
> **Author:** Phạm Thanh Vy · **Project period:** October–November 2026 · **Latest test summary:** November 7, 2026

## Project overview

This project demonstrates a complete manual testing workflow: planning, requirement analysis, test design, execution, defect reporting, requirement traceability, and test completion reporting. It also includes a small Scrum/Jira workflow for managing stories and reported defects. The system under test (SUT) is a public demonstration website; it is not a production release controlled by this project.

## Scope

**In scope:** Six functional requirements — **Login, Product listing, Sorting, Cart, Checkout, and Logout**. The test environment was **Brave 1.98.60 on Windows 11**, with the four SauceDemo test accounts `standard_user`, `problem_user`, `locked_out_user`, and `performance_glitch_user`.

**Out of scope:** In-depth performance and security testing, cross-browser certification, and mobile application testing. Basic observations about these areas are not comprehensive coverage. Because there is no formal product specification available for this demo site, some expected results are documented as assumptions pending clarification with a business analyst (BA).

## Test approach and techniques

The test approach combined **requirements-based functional testing**, **risk-based prioritization**, **black-box test design**, and **time-boxed exploratory testing**. Test cases were linked to requirements using a requirements traceability matrix (RTM). Failures were rechecked before filing defects, with open questions retained where expected behavior was unclear.

| Test design technique | Cases | Application |
| :-- | --: | :-- |
| Equivalence Partitioning (EP) | 16 | Valid/invalid accounts and sorting options |
| Boundary Value Analysis (BVA) | 4 | Cart badge boundaries (0, 1, and 6 items) |
| Decision Tables | 8 | Login rules and checkout information validation |
| State Transition Testing | 13 | Purchase workflow, logout, and direct URL access |
| Business Flows | 9 | Main, alternative, and exception checkout paths |
| Error Guessing | 11 | Whitespace, navigation, reloading, and session-related cases |
| Checklist-Based Testing | 14 | Product content, price presentation, and password masking |
| **Total** | **75** | **74 in scope; 1 N/A/out of scope** |

Source-code-dependent statement and branch coverage could not be measured because the application's source code was not available to the tester.

## Tools

| Tool | Purpose |
| :-- | :-- |
| **Brave browser** | Executing test cases and observing application behavior |
| **Google Sheets / Microsoft Excel** | Test cases, execution status, RTM, bug reports, and exploratory notes |
| **Google Docs / PDF** | Test plan and test summary report |
| **Jira Cloud (Scrum)** | One Epic, six Stories, defect tracking, and a Sprint board |
| **Git / GitHub** | Version control, packaging, and portfolio presentation |

## Results

**Baseline:** Updated RTM and Test Summary Report v1.0, **November 7, 2026**. Results below replace the earlier, outdated 59-pass/15-fail summary.

| Requirement | Test cases | Executed | Pass | Fail | Blocked | Pass rate |
| :-- | --: | --: | --: | --: | --: | --: |
| REQ_LOGIN | 12 | 12 | 11 | 1 | 0 | 91.67% |
| REQ_PRODUCT | 12 | 12 | 9 | 3 | 0 | 75.00% |
| REQ_SORT | 10 | 10 | 7 | 3 | 0 | 70.00% |
| REQ_CART | 16 | 16 | 10 | 6 | 0 | 62.50% |
| REQ_CHECKOUT | 17 | 17 | 14 | 3 | 0 | 82.35% |
| REQ_LOGOUT | 7 | 7 | 7 | 0 | 0 | 100.00% |
| **TOTAL** | **74** | **74** | **58** | **16** | **0** | **78.38%** |

- **Test suite:** 75 cases designed, of which 1 case was out of scope (`N/A`); all **74 in-scope** cases were executed.
- **Problem-user rerun (November 7):** 12 high-priority cases executed — **7 passed and 5 failed**.
- **High-priority coverage:** All 25 of 25 high-priority cases in TestCases were executed.
- **Defects:** 10 SauceDemo bugs recorded in the updated BugReports sheet (**1 Critical, 8 Major, 1 Minor**). One additional exploratory bug involving a different website is **excluded** from SauceDemo totals.
- **Release recommendation: NOT READY FOR RELEASE.** At the November 7 reporting baseline, `BUG_006` was still marked **Critical / New**, so the “no open Critical defect” exit criterion was not satisfied. Current live Jira status was not reverified for this portfolio snapshot.
- Four test failures involve expected behavior that still requires BA clarification, rather than a confirmed product defect.

## Sample bugs and evidence

Screenshots below are **original evidence extracted from the existing test-case workbook**, not simulated UI images. The Jira project is private; references to issue IDs are for traceability.

| Bug ID / Jira | Severity | Issue | Evidence |
| :-- | :-- | :-- | :-- |
| **BUG_001 / SD-8** | Major | Checkout can be completed with an empty cart. | [Empty-cart checkout](screenshots/BUG_001_empty_cart_checkout.png) · [Order confirmation](screenshots/BUG_001_order_confirmation.png) |
| **BUG_003 / SD-10** | Minor | `problem_user`: all product cards show the same incorrect dog image. | [Incorrect product images](screenshots/BUG_003_incorrect_product_images.png) |
| **BUG_006 / SD-13** | Critical | `problem_user`: typing in the Last Name field affects First Name, blocking normal checkout. | [Checkout input evidence](screenshots/BUG_006_checkout_name_input.png) |

**Jira board screenshot:** Not included in the verified source files. Add your actual Jira Scrum-board image at `screenshots/jira-sprint-board.png` before final submission; see [screenshots instructions](screenshots/README.md). Do not substitute a fabricated screenshot.

## Deliverables

```text
manual-testing-saucedemo/
├── README.md
├── test-plan/
│   └── Test_Plan.pdf
├── test-cases/
│   └── Saucedemo_TestCases.xlsx
├── reports/
│   └── Test_Summary_Report.pdf
└── screenshots/
    ├── README.md
    ├── BUG_001_empty_cart_checkout.png
    ├── BUG_001_order_confirmation.png
    ├── BUG_003_incorrect_product_images.png
    ├── BUG_006_checkout_name_input.png
    └── jira-sprint-board.png  # add the authentic Jira screenshot
```

The last line is a **required follow-up asset** and is intentionally absent from the package until an authentic image is provided. The `test-cases` workbook contains the detailed RTM, BugReports, and execution history.

Original working documents: [Test Plan (Google Docs)](https://docs.google.com/document/d/1qDFjcmVy5oGG22HZnLXAYfEStl3pQzyDXRRV5QkfQC8/edit) · [Test Cases / RTM (Google Sheets)](https://docs.google.com/spreadsheets/d/1RohdAC92pyPIa1F65Ztnpomn5BitYWi59uj_60wFYho/edit).

## Lessons learned

1. **Check expected results before raising defects.** Unclear business rules should become BA questions, not automatic bug reports.
2. **Choose techniques that suit the problem.** EP/BVA fit input classes and boundaries; decision tables fit rule combinations; state transitions fit user journeys.
3. **Retest apparent failures.** A misleading test step or a non-reproducible outcome should not become a confirmed defect.
4. **Preserve traceability.** Linking requirement → test case → defect → Jira story made coverage and priorities easier to review.
5. **Treat the release decision as evidence-based.** A high execution rate or good pass rate does not override an unmet Critical-defect exit criterion.
6. **Maintain one source of truth.** The RTM and completion report must be synchronized; earlier README totals should be replaced when the rerun changes results.

## ISTQB references and next study focus

- [ISTQB CTFL v4.0.1 syllabus](https://istqb.org/wp-content/uploads/2024/11/ISTQB_CTFL_Syllabus_v4.0.1.pdf), **Section 2.1** — Testing in the context of an SDLC: lifecycle impact, early testing, test-first approaches, DevOps, shift-left, and retrospectives.
- **Section 5.5** — Defect Management: recording, classifying, tracking, and resolving anomalies; writing actionable defect reports with reproduction steps and expected vs. actual results.

---

*Educational portfolio project. SauceDemo/Swag Labs is a third-party demonstration application; this repository is not affiliated with its operator.*
