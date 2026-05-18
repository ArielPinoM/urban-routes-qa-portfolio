# Payment Methods & Card Binding Functional Checklist (56 Verification Points)

> 📌 **Note for Reviewers:** This checklist validates the functional constraints, input masking, and error handling of the "Payment Method" workflows.
> * **Requirement Source:** [PRD - Section 7.2: "Add card" window](../../docs/requirements/car_sharing_service_requirements_english.md#72-add-card-window)
> * **Test Design Methodology:** [payment_methods_equivalence_classes_boundary_analysis.md](../../docs/test-design/payment_methods_equivalence_classes_boundary_analysis.md)
> * **Visual Blueprints:** Interactivity rules and UI flows are mapped against [visual_references.md > 3. Car Sharing Service Module (Payment Method)](../../docs/design/visual_references.md#payment-method).
> * **Traceability:** Any verification point marked as 🔴 **FAILED** is fully documented with its technical root cause in the Consolidated Bug Matrix.

---

## 1. "Add Card" Modal - Input Fields Validation (Points 01 - 30)

### Card Number Field (Items 01 - 12)
| Item ID | Verification Criteria / Input Condition | Expected System Behavior | Status | Linked Bug |
| :--- | :--- | :--- | :---: | :---: |
| CK-PM-01 | Numeric-only constraint | Blocks alphabetic characters and special symbols instantly. | **PASS** | N/A |
| CK-PM-02 | Input Masking spaces | Injects a space automatically after every 4 digits (`#### #### #### ####`). | **PASS** | N/A |
| CK-PM-03 | Maximum character length | Limits the field strictly to 16 digits; truncates further keystrokes. | **PASS** | N/A |
| CK-PM-04 | Luhn Algorithm (Mod 10) validation | Triggers "Invalid card number" error message if the check digit fails. | **FAIL** | [UR-REG-14](../../bug-reports/consolidated_bug_matrix.md#ur-reg-14) |

### Expiry Date Field (Items 13 - 22)
| Item ID | Verification Criteria / Input Condition | Expected System Behavior | Status | Linked Bug |
| :--- | :--- | :--- | :---: | :---: |
| CK-PM-13 | Expiry Date Format Masking | Automatically injects the forward slash after the month (`MM/YY`). | **PASS** | N/A |
| CK-PM-14 | Historical / Expired date entry | Triggers an immediate inline validation error: "The card has expired." | **FAIL** | [UR-REG-15](../../bug-reports/consolidated_bug_matrix.md#ur-reg-15) |

### CVV / CVC Field (Items 23 - 30)
| Item ID | Verification Criteria / Input Condition | Expected System Behavior | Status | Linked Bug |
| :--- | :--- | :--- | :---: | :---: |
| CK-PM-23 | Character Masking / Security | Obscures inputs into security dots (`•`) within 0.5 seconds of entry. | **PASS** | N/A |
| CK-PM-24 | Fixed length constraint | Limits input strictly to 3 numeric digits (4 for Amex if applicable). | **PASS** | N/A |

---

## 2. Form Submission, State Persistence & Main View Integration (Points 31 - 56)

### "Add" Button States & Focus Management (Items 31 - 45)
| Item ID | Verification Criteria / Input Condition | Expected System Behavior | Status | Linked Bug |
| :--- | :--- | :--- | :---: | :---: |
| CK-PM-31 | Disabled state on empty fields | The "Link" / "Add" button remains grayed out and unclickable. | **PASS** | N/A |
| CK-PM-32 | Dynamic button activation | Button switches to active state immediately when all 3 fields are valid. | **PASS** | N/A |
| CK-PM-45 | Loss of focus (Blur event) | Pressing `Tab` out of CVV triggers validation check on the field. | **PASS** | N/A |

### Main Payment Window Integration (Items 46 - 56)
| Item ID | Verification Criteria / Input Condition | Expected System Behavior | Status | Linked Bug |
| :--- | :--- | :--- | :---: | :---: |
| CK-PM-46 | Card persistence on main menu | Once linked, the card appears listed under "My Cards" with masked ID. | **PASS** | N/A |
| CK-PM-56 | Selection Radio Button behavior | Selecting the new card unchecks "Cash" or other previously active methods. | **PASS** | N/A |