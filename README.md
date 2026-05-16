# QA Testing: Web Application and Business Logic - Urban Routes

## 1. Project Description
Urban Routes is a transportation platform that integrates multiple services (taxi, car sharing, and scooters). The objective of this project was to validate route calculation logic (pricing/time estimation), vehicle booking functionality, and UI consistency across different browser environments.

**Business Problem:** Ensure that the pricing algorithm calculates accurate fares based on distance and departure time, and that the driver registration/license workflow is frictionless to prevent user conversion drop-offs.

## 2. Test Strategy & Coverage
A **Shift-Left Testing** approach was implemented, initiating QA involvement during the requirement analysis and test design phases prior to execution. This strategy ensured early defect detection in business logic and UI layout compliance before concluding development cycles.

### Test Types Applied
*   **Regression Testing:** Full execution of core functionalities to verify system stability after changes.
*   **Functional Testing:** Validation of business logic, formulas, and transaction criteria (Car sharing and booking loops).
*   **Black-Box Design Techniques:** Boundary Value Analysis (BVA) and Equivalence Partitioning (ECP) applied to text inputs and calculation parameters.
*   **UI/UX & Cross-Browser Testing:** Verification of visual layouts across different screen resolutions and rendering engines.

### Test Environments & Scope Matrix

The verification scope was distributed across specific configurations to optimize testing efficiency based on platform requirements:

| Module / Feature | Test Type | Environment / Configuration | Scope / Volume |
| :--- | :--- | :--- | :--- |
| **01 Core Regression** | Functional Regression | Google Chrome | 24 Test Cases executed |
| **02 Car Sharing Logic** | Business Logic Design | N/A (Static Logic Design) | 30 Test Cases designed (ECP/BVA) |
| **03 Form Layout UI** | Cross-Browser UI | Google Chrome (800x600) <br> Mozilla Firefox (1920x1080) | 93 Checklist items verified |
| **03 Payment Window** | Functional UI / Security | Google Chrome | 56 Checklist items verified |
| **03 Booking Buttons** | End-to-End Functional | Google Chrome | 14 Test Cases (10 executed, 4 skipped) |

---

### Metrics & Defect Management Summary

The total lifecycle volume encompassed **68 test cases**, **149 checklist elements**, and the identification and formal logging of **61 defects** in Jira:

```text
Urban Routes Portfolio Metrics:
│
├── [Phase 1] Core Regression ────> 24 Executed TCs      │ 7 Bugs Logged
├── [Phase 2] Car Sharing Logic ──> 30 Designed TCs      │ 0 Bugs (Design Only)
└── [Phase 3] Payment & Booking ──> 149 Checklist Items  │ 54 Bugs Logged (UI/Cross-Browser)
```

## 3. Test Design Methodology
To ensure comprehensive test coverage, the following techniques were used:

* **Requirements Analysis:** Breakdown of the "Car Sharing" feature.
* **Mind Maps:** Visualization of the "Add Driver License" workflow ([View map](./docs/design/driver_license_mind_map.png)).
* **Flowcharts:** Modeling of average speed logic based on departure time ([View flowchart](./docs/design/speed_logic_flowchart.png)).
* **Test Design Techniques:**
    * **Equivalence Partitioning (ECP):** Applied to the "First Name", "Last Name", distance between addresses, Departure Time (determines average transportation speed), "Card Number", and "Code" fields.
    * **Boundary Value Analysis (BVA):** Identification of critical boundary points for character length validation in the "First Name", "Last Name", "Card Number", and "Code" fields. Also applied to departure time limits.

## 4. Execution and Results
### Calculation Logic (Validation Example)
* **Formula:** $T = S / V$ | $Price = T \times Cost/min$
* **Scenario:** East 2nd St -> 1717 E 7th St (0.89 km) at 11:00 AM (30 km/h).
* **Expected Result:** 1.8 min / $0.18.
* **Observed Result:** [Insert whether the test passed or failed].

### Defect Summary
| Total Test Cases | Passed | Failed | Blocked |
| :--- | :--- | :--- | :--- |
| XX | XX | XX | XX |

## 5. Bug Reporting (Evidence)
Detected defects were documented in Jira following the standard format: Title, Steps to Reproduce, Expected vs. Actual Result, Severity, and Priority.
* [View Consolidated Bug Report](./bug-reports/BUGS_REPORT.md)
* [View Jira Screenshots](./evidence/jira-tickets/)

## 6. Tools Used
* **Management:** Jira
* **Design:** Figma
* **Documentation:** Google Sheets / Markdown