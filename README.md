# manual-qa-saucedemo
Testing for saucedemo.com website
# SauceDemo E-Commerce QA Testing & Technical Defect Analysis

##  Project Overview
Comprehensive manual testing and technical root-cause analysis performed on the **SauceDemo** web application (`problem_user` context). The primary objective was to execute end-to-end exploratory testing, design structured test cases, manage cross-ticket dependencies in Jira, and conduct DOM/DevTools state validation.

---

##  Tools & Technologies
* **Issue Tracking & Project Management:** Jira (Scrum / Kanban)
* **Test Case Management:** Standardized Test Suites (Excel)
* **Browser DevTools:** Chrome DevTools (Console inspection, DOM analysis, `localStorage` state injection)
* **Documentation:** Markdown, Visual Artifacts

---

## Key Achievements & Deep Technical Analyses

### 1. State Isolation via Local Storage Injection (`KAN-16`)
* **Issue:** "Remove" buttons on the inventory page failed to update UI state for added items.
* **Technical Troubleshooting:** Utilized DevTools `Application -> Local Storage` to manually inject missing product IDs (`1, 5, 3`) into the session cart array. Proved that core state management and removal logic were operational, isolating the bug strictly to frontend event handler bindings on specific product cards.

### 2. Off-by-One Array Index Routing Error (`KAN-17`)
* **Issue:** Clicking product cards redirected users to incorrect item details pages or 404 pages.
* **Technical Troubleshooting:** Identified a systematic pattern where item link parameters routed to `item_id = target_id + 1`. Formulated a hypothesis mapping a 0-based vs 1-based index mismatch across all 6 product cards, including the final item ($ID=5$) triggering an `ITEM NOT FOUND` ($ID=6$) page error.

---

##  Portfolio Artifacts
* **Test Cases Sheet:** `saucedemo_test_cases(1).xlsx`
* **Test Scenarios Sheet:** `Test Scenarios.xlsx`
* **Jira Board Project Key:** `KAN`

---

##  Selected Defect Reports Summary

| Ticket ID | Title | Priority | Severity | Technical Focus |
| :--- | :--- | :--- | :--- | :--- |
| **KAN-15** | Non-responsive "Add to cart" buttons | Medium | Medium | Dead event listeners / Silent console |
| **KAN-16** | Non-responsive "Remove" buttons | Medium | High | `localStorage` state isolation |
| **KAN-17** | Product card link redirection off-by-one error | Medium | Medium | Array index routing mismatch ($ID+1$) |
| **KAN-18** | Product sorting dropdown execution failure | Low | Low | Unhandled `<select>` change listener |
| **KAN-19** | Incorrect visual asset mapping across cards | Low | Low | Hardcoded fallback asset (`sl-404.jpg`) |

---

## Author
**Арсеній Волоско**  
Junior QA Engineer | Focus on Web Architecture, Manual Testing & Defect Isolation
