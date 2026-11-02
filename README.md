Swag Labs (SauceDemo) – Manual Testing Project

Manual testing of the demo e-commerce site [Swag Labs](https://www.saucedemo.com), done as Project 1 of my self-study path in software testing, based on the ISTQB CTFL v4.0.1 syllabus.

**Author:** Phạm Thanh Vy · **Period:** Oct – Nov 2026 · **Role:** Tester (also test management)

---

## Deliverables

| Deliverable | Link |
|---|---|
| Test plan (scope, approach, risks, entry/exit criteria) | [Saucedemo – Test Plan](https://docs.google.com/document/d/1qDFjcmVy5oGG22HZnLXAYfEStl3pQzyDXRRV5QkfQC8/edit?usp=sharing) |
| Requirements, test cases, RTM, bug reports, exploratory notes | [Saucedemo – Test cases (Google Sheet)](https://docs.google.com/spreadsheets/d/1RohdAC92pyPIa1F65Ztnpomn5BitYWi59uj_60wFYho/edit?usp=sharing) |
| Scrum board, bugs and saved JQL filters | Jira Cloud (private workspace, see screenshots below) |

## Scope

- **In scope:** 6 requirements: login, product list, sorting, cart, checkout, logout.
- **Out of scope:** in-depth performance and security testing, mobile app. Only basic observations were recorded.
- **Test basis:** the site has no specification, so the 6 requirements were written as assumptions. Expected results without a clear basis are marked "to be confirmed with BA".
- **Environment:** Brave 1.98.60, Windows 11. Accounts: `standard_user`, `problem_user`, `locked_out_user`, `performance_glitch_user`.

## Test design

75 test cases (74 in scope, 1 out of scope). Each test case records the technique used to derive it.

| Technique | Test cases | Used for |
|---|---|---|
| Equivalence partitioning | 16 | Account types (standard vs problem user), sort options, invalid usernames |
| Boundary value analysis | 4 | Cart badge at 0, 1 and 6 items |
| Decision table | 8 | Login rules, checkout information fields |
| State transition | 13 | Purchase flow, logout, direct URL access without login |
| Business flows (main, alternative, exception) | 9 | Checkout |
| Error guessing | 11 | Spaces in username, sort order after reload, cart after logout |
| Checklist-based | 14 | Product page content, price format, password masking |

White-box techniques (statement and branch coverage) were not applicable because the source code is not available.

I also ran two time-boxed exploratory sessions with a charter, and practised EP, BVA, decision tables and state transition diagrams on separate exercises (see the Sheet).

## Results

All 74 in-scope test cases were executed.

| Requirement | Test cases | Pass | Fail | Bugs |
|---|---|---|---|---|
| REQ_LOGIN | 12 | 11 | 1 | – (awaiting BA) |
| REQ_PRODUCT | 12 | 9 | 3 | BUG_002, BUG_003, BUG_007 |
| REQ_SORT | 10 | 8 | 2 | – (awaiting BA) |
| REQ_CART | 16 | 10 | 6 | BUG_004, BUG_005, BUG_008, BUG_009 |
| REQ_CHECKOUT | 17 | 14 | 3 | BUG_001, BUG_006 |
| REQ_LOGOUT | 7 | 7 | 0 | – |
| **Total** | **74** | **59** | **15** | **9 bugs** |

Of the 15 failed test cases, 11 are linked to bug reports and 4 are waiting for clarification of the expected behaviour (see Open questions).

## Bugs found

10 bug reports (1 Critical, 7 Major, 2 Minor): 9 on Swag Labs and 1 on [The Internet (herokuapp)](https://the-internet.herokuapp.com) from an exploratory session. Each report has environment, preconditions, numbered steps, expected and actual results, frequency (3/3), severity, priority, related test case and screenshots.

| ID | Jira | Title | Severity | Priority |
|---|---|---|---|---|
| BUG_001 | SD-8 | [Checkout] Order can be completed with an empty cart | Major | Medium |
| BUG_002 | SD-9 | [Product] problem_user: detail page shows wrong product | Major | Medium |
| BUG_003 | SD-10 | [Product] problem_user: all products show the same image | Minor | Medium |
| BUG_004 | SD-11 | [Cart] problem_user: Remove on Products page has no effect | Major | Medium |
| BUG_005 | SD-12 | [Cart] problem_user: 3 products cannot be added from list | Major | High |
| BUG_006 | SD-13 | [Checkout] problem_user: Last Name input goes to First Name | Critical | High |
| BUG_007 | SD-14 | [Product] problem_user: Remove on detail page has no effect | Major | Medium |
| BUG_008 | SD-15 | [Cart] problem_user: badge count is 1 higher than cart | Major | Medium |
| BUG_009 | SD-16 | [Product] problem_user: detail Add to cart has no effect | Major | Medium |
| BUG_010 | SD-17 | [Broken Images] 2 of 3 images fail to load | Minor | Medium |

**Finding I am most proud of (BUG_008):** the cart badge was always 1 higher than the real number of items. Instead of reporting only the symptom, I traced it to a hidden item in the cart: a product page showing "ITEM NOT FOUND" with price "$√-1" (`inventory-item.html?id=6`), which cannot be removed.

## Jira (Scrum)

- **Structure:** 1 Epic (Swag Labs testing), 6 Stories with acceptance criteria (one per requirement), 10 Bugs linked to the affected story with "relates to".
- **Sprint 1:** started with a sprint goal; stories moved across To Do, In Progress and Done.
- **Severity** is stored as a label (`severity-major`…) because Jira Free has no severity field. **Priority** uses the Jira Priority field.

Saved JQL filters:

| Filter | JQL | Purpose |
|---|---|---|
| SD – Open bugs | `project = SD AND issuetype = Bug AND statusCategory != Done` | All bugs not yet done |
| SD – High priority bugs | `project = SD AND issuetype = Bug AND priority in (Highest, High)` | Bugs to fix first |
| SD – Current sprint | `project = SD AND sprint in openSprints()` | Everything in the open sprint |

**Sprint board**

<img width="713" height="446" alt="Screenshot 2026-11-02 231306" src="https://github.com/user-attachments/assets/d63eca28-ec96-489b-a89f-23fd6125c809" />


**Open bugs**

<img width="959" height="485" alt="Screenshot 2026-11-02 233202" src="https://github.com/user-attachments/assets/02f1d3f4-94ac-4b1e-9651-088467f88262" />


## Traceability

Requirement → Test case → Bug report (Sheet) → Jira bug → Jira story.

- The RTM tab counts test cases, executed, passed and failed per requirement with formulas, so it updates when a status changes.
- Each bug report lists the test case that found it and its Jira key. Each Jira bug repeats the Sheet ID and related test case in its description, because Jira Free has no built-in test case management.

## Open questions for BA

Expected results that were assumptions and failed during execution. No bug report was filed until they are confirmed:

1. Should leading and trailing spaces in the username be trimmed? (TC_LOGIN_008)
2. Should the sort order be kept after opening a product detail page or reloading? (TC_SORT_007, TC_SORT_008)
3. Should direct access to the checkout overview page be blocked when the cart is empty? (TC_CHK_016)

## What I learned

- Writing expected results that are specific and checkable, and marking assumptions instead of guessing.
- Choosing a test technique from the nature of the feature: input fields → EP/BVA, combined rules → decision table, flows and states → state transition, display-only pages → checklist.
- Re-checking a failure before reporting it: one "failed" test turned out to be a wrong test step, and one login failure could not be reproduced.
- Avoiding duplicate bug reports and resolving contradictions between reports before sending them.
- Using an RTM to find coverage gaps, and keeping traceability across Google Sheets and Jira.
