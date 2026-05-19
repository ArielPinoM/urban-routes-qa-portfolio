# QA Testing: Web Application and Business Logic - Urban Routes

## 1. Project Description
Urban Routes is a transportation platform that integrates multiple services (taxi, car sharing, and scooters). The objective of this project was to validate route calculation logic (pricing/time estimation), vehicle booking functionality, and UI consistency across different browser environments.

**Business Problem:** Ensure that the pricing algorithm calculates accurate fares based on distance and departure time, and that the driver registration/license workflow is frictionless to prevent user conversion drop-offs.

> 📌 For visual details and interface mockups, see [Visual References](./docs/design/visual_references.md).

---

## 2. Test Strategy & Coverage
A **Specification-Based Testing** approach was implemented. Prior to test execution, a thorough static analysis of the requirements was conducted to design rigorous test suites using black-box techniques. This process ensured that execution was driven by established business logic and formal criteria rather than ad-hoc exploration.

### Test Environments & Scope Matrix
The verification scope was distributed across specific configurations to optimize testing efficiency based on platform requirements:

| Module / Feature | Test Type | Environment / Configuration | Scope / Volume | Deliverables & Traceability Links |
| :--- | :--- | :--- | :--- | :--- |
| **01 Core Requirements** | Specifications Unification | N/A (Single Source of Truth) | 2 Unified PRD Docs | [English PRD](./docs/requirements/car_sharing_service_requirements_english.md) / [Spanish PRD](./docs/requirements/car_sharing_service_requirements_spanish.md) |
| **02 Core Regression** | Functional Regression | Google Chrome | 24 Test Cases executed | [Regression Test Cases](./test-cases/01_core_regression/regression_test_cases.md) |
| **03 Car Sharing Logic** | Business Logic Design | N/A (Static Logic Design) | 30 Test Cases designed | [Logic Test Cases](./test-cases/02_car_sharing/logic_test_cases_design.md) |
| **04 Form Layout UI** | Cross-Browser UI Layout | Google Chrome / Firefox | 93 Checklist items | [Reservation Form Checklist](./test-cases/03_payment_and_reservation/checklist_reservation_form_design.md) |
| **05 Payment Window** | Functional UI / Security | Google Chrome | 56 Checklist items | [Payment Checklist](./test-cases/03_payment_and_reservation/checklist_payment_methods.md) |
| **06 Booking Lifecycle** | End-to-End Functional | Google Chrome | 4 Lifecycle Test Cases | [Car Booking TCs](./test-cases/03_payment_and_reservation/test_cases_car_booking.md) / [Reservation Button TCs](./test-cases/03_payment_and_reservation/test_cases_reservation_button.md) |

---

## 3. Test Design Methodology
To ensure comprehensive test coverage, the following techniques and strategic files were used:

* **Requirements Analysis:** Breakdown and consolidation of the "Car Sharing" feature into a single Product Requirements Document ([View Unified PRD](./docs/requirements/car_sharing_service_requirements_english.md)).
* **Test Design Specifications (EP & BVA Matrices):**
    * **Route & Time Analysis:** [Distance & Departure Time Test Design](./docs/test-design/distance_between_addresses_departure_time_equivalence_classes_boundary_analysis.md)
    * **Identity Validation:** [Driver's License Test Design](./docs/test-design/driver_license_equivalence_classes_boundary_analysis.md)
    * **Payment Gateways:** [Payment Methods Test Design](./docs/test-design/payment_methods_equivalence_classes_boundary_analysis.md)

### Test Artifact Nomenclature (ID Mapping)
To maintain strict traceability across requirements, design specs, and execution matrices, the following systematic ID convention was enforced:

* **`TC-XX`**: Test Case - Regression (Phase 1). Direct functional verification of baseline features.
* **`TC-CS-XX`**: Test Case - Car Sharing (Phase 2). Input conditions and logic test design parameters.
* **`CK-PM-XX`**: ChecK - Payment Methods (Phase 3). Validation items for the card binding modal.
* **`CK-UI-XX`**: ChecK - User Interface (Phase 3). Layout and element checks for the booking form.
* **`TC-CSR-XX`**: Test Case - Car Sharing Reservation (Phase 3). End-to-end car booking lifecycles.
* **`TC-BB-XX`**: Test Case - Book Button (Phase 3). Conditional text states and actions for the primary CTA.
* **`UR-BR-XX`**: Defect unique identifiers mapped directly to Jira tickets within the Consolidated Bug Matrix.

---

## 4. Execution and Results

### Calculation Logic (Validation Example)
* **Formula:** `trip_price = fixed_rental_fee + (60 × per_minute_price × duration_h) × fare_coefficient`
* **Scenario:** East 2nd St -> 1717 E 7th St (0.89 km) at 11:00 AM (Speed slot: 30 km/h).
    * *Duration Calculation:* $0.89 \text{ km} / 30 \text{ km/h} = 0.0296 \text{ h}$
* **Expected Result:** $2.00 + (60 \times 0.10 \times 0.0296) \times 1.5 = \$2.26$
* **Observed Result:** Verification details and logic edge-cases are mapped in the execution matrices.

### Defect Summary
| Total Test Cases / Items | Passed | Failed | Skipped |
| :--- | :--- | :--- | :--- |
| 58 TCs / 149 Checklist Items | 146 | 61 | 17 |

---

## 5. Bug Reporting (Evidence)
Detected defects were documented in Jira following the standard format: Title, Steps to Reproduce, Expected vs. Actual Result, Severity, and Priority. All entries are mapped in the central matrix:
* [View Consolidated Bug Report Matrix](./bug-reports/consolidated_bug_matrix.md)
* [View Evidence Folder](./bug-reports/evidence/)

---

## 6. Tools Used
* **Management & Tracking:** Jira
* **Design & Vector Maps:** Figma
* **Documentation & Specifications:** Markdown / Git / VS Code