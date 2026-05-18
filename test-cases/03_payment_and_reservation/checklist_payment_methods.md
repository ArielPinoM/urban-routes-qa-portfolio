# Payment Methods & Card Binding Functional Checklist (56 Verification Points)

> 📌 **Note for Reviewers:** This checklist validates the functional constraints, input masking, and error handling of the "Payment Method" workflows.
> * **Requirement Source:** [PRD - Section 7.2: "Add card" window](../../docs/requirements/car_sharing_service_requirements_english.md#72-add-card-window)
> * **Test Design Methodology:** [payment_methods_equivalence_classes_boundary_analysis.md](../../docs/test-design/payment_methods_equivalence_classes_boundary_analysis.md)
> * **Visual Blueprints:** Interactivity rules and UI flows are mapped against [visual_references.md > 3. Car Sharing Service Module (Payment Method)](../../docs/design/visual_references.md#payment-method).
> * **Traceability:** Any verification point marked as 🔴 **FAILED** is fully documented with its technical root cause in the Consolidated Bug Matrix.

---

## 1. "Payment Method" Field & Modal Window - (Points 01 - 30)

### "Payment Method Field" (Items 01 - 02)

| Item ID | Monitoring Description | Test Status for Google Chrome 800x600 | Bug Report Link |
| :--- | :--- | :--- | :---: |
| CK-PM-01 | Clicking the "Payment Method" field opens the "Payment Method" modal. | 🟢 PASSED |  |
| CK-PM-02 | Any number of cards can be added without restrictions. | 🟢 PASSED |  |

---

### "Payment Method Modal Window" (Items 03 - 04)

| Item ID | Monitoring Description | Test Status for Google Chrome 800x600 | Bug Report Link |
| :--- | :--- | :--- | :---: |
| CK-PM-03 | In the "Payment Method" modal, the added card name matches "Tarjeta ● xxxx", where "xxxx" represents the last 4 digits of the card number. | 🔴 FAILED | [UR-BR-25](../../bug-reports/consolidated_bug_matrix.md#ur-br-25) |
| CK-PM-04 | Clicking the "Agregar tarjeta" button opens the "Add Card" modal. | 🟢 PASSED |  |

---

## 2. "Card Number", CVV Fields & Form Submission (Points 05 - 56)

### "Card Number" field (Items 05 - 27)
| Item ID | Monitoring Description | Test Status for Google Chrome 800x600 | Bug Report Link |
| :--- | :--- | :--- | :---: |
| CK-PM-05 | Verify that the "Card Number" field accepts a 12-character card number. | 🟢 PASSED |  |
| CK-PM-06 | Verify that entering a 5-character card number is invalid. | 🔴 FAILED |  |
| CK-PM-07 | Verify that entering an 11-character card number is invalid. | 🔴 FAILED |  |
| CK-PM-08 | Verify that entering a 10-character card number is invalid. | 🔴 FAILED |  |
| CK-PM-09 | Verify that entering a 15-character card number is invalid. | 🔴 FAILED |  |
| CK-PM-10 | Verify that entering a 13-character card number is invalid. | 🔴 FAILED |  |
| CK-PM-11 | Verify that entering a 14-character card number is invalid. | 🔴 FAILED |  |
| CK-PM-12 | Verify that the field accepts a card number containing a "0000" group. | 🟢 PASSED |  |
| CK-PM-13 | Entering a card number containing a "0001" group is valid. | 🟢 PASSED |  |
| CK-PM-14 | Entering a card number containing a "9999" group is valid. | 🟢 PASSED |  |
| CK-PM-15 | Entering a card number containing a "9998" group is valid. | 🟢 PASSED |  |
| CK-PM-16 | Verify that leaving the "Card Number" field empty is invalid. | 🔴 FAILED |  |
| CK-PM-17 | The "Card Number" field displays the format restriction "nnnn nnnn nnnn". | 🟢 PASSED |  |
| CK-PM-18 | The "Card Number" field only allows numeric input. | 🔴 FAILED |  |
| CK-PM-19 | The "Card Number" field only allows 12 characters. | 🔴 FAILED |  |
| CK-PM-20 | Spaces are automatically added when the user enters the number and removes focus from the "Card Number" field. | 🔴 FAILED |  |
| CK-PM-21 | The "Add" button remains disabled if fewer than 12 characters are entered in the "Card Number" field. | 🔴 FAILED |  |
| CK-PM-22 | It is not possible to enter more than 12 characters in the "Card Number" field. | 🔴 FAILED |  |
| CK-PM-23 | It is not possible to enter spaces in the "Card Number" field. | 🔴 FAILED |  |
| CK-PM-24 | It is not possible to enter hyphens in the "Card Number" field. | 🔴 FAILED |  |
| CK-PM-25 | It is not possible to enter letters in the "Card Number" field. | 🔴 FAILED |  |
| CK-PM-26 | It is not possible to enter special characters in the "Card Number" field. | 🔴 FAILED |  |
| CK-PM-27 | It is not possible to enter characters from other languages in the "Card Number" field. | 🔴 FAILED |  |

---

### CVV Field (Items 28 - 47)
| Item ID | Monitoring Description | Test Status for Google Chrome 800x600 | Bug Report Link |
| :--- | :--- | :--- | :---: |
| CK-PM-28 | Verify the validity of a 2-character code. | 🟢 PASSED |  |
| CK-PM-29 | Verify that entering a 1-character code is invalid. | 🔴 FAILED |  |
| CK-PM-30 | Verify that entering a 3-character code is invalid. | 🔴 FAILED |  |
| CK-PM-31 | Verify that entering a 4-character code is invalid. | 🔴 FAILED |  |
| CK-PM-32 | Entering the code "01" is valid. | 🟢 PASSED |  |
| CK-PM-33 | Entering the code "02" is valid. | 🟢 PASSED |  |
| CK-PM-34 | Entering the code "98" is valid. | 🟢 PASSED |  |
| CK-PM-35 | Entering the code "99" is valid. | 🟢 PASSED |  |
| CK-PM-36 | Entering the code "00" is invalid. | 🟢 PASSED |  |
| CK-PM-37 | Verify that leaving the "Code" field empty is invalid. | 🔴 FAILED |  |
| CK-PM-38 | The "Code" field displays the format restriction "nn". | 🟢 PASSED |  |
| CK-PM-39 | The "Code" field only allows numeric input. | 🔴 FAILED |  |
| CK-PM-40 | The "Code" field only allows 2 characters. | 🔴 FAILED |  |
| CK-PM-41 | The "Add Card" button remains disabled if fewer than 2 characters are entered in the "Code" field. | 🔴 FAILED |  |
| CK-PM-42 | It is not possible to enter more than 2 characters in the "Code" field. | 🔴 FAILED |  |
| CK-PM-43 | It is not possible to enter spaces in the "Code" field. | 🔴 FAILED |  |
| CK-PM-44 | It is not possible to enter hyphens in the "Code" field. | 🔴 FAILED |  |
| CK-PM-45 | It is not possible to enter letters in the "Code" field. | 🔴 FAILED |  |
| CK-PM-46 | It is not possible to enter special characters in the "Code" field. | 🔴 FAILED |  |
| CK-PM-47 | It is not possible to enter characters from other languages in the "Code" field. | 🔴 FAILED |  |

---

### Form Submission (Items 48 - 56)

| Item ID | Monitoring Description | Test Status for Google Chrome 800x600 | Bug Report Link |
| :--- | :--- | :--- | :---: |
| CK-PM-48 | The card is added when a valid card number and valid code are entered. | 🟢 PASSED |  |
| CK-PM-49 | The card is not added when a valid card number and invalid code are entered. | 🔴 FAILED |  |
| CK-PM-50 | The card is not added when a valid card number and empty code are entered. | 🟢 PASSED |  |
| CK-PM-51 | The card is not added when an invalid card number and invalid code are entered. | 🔴 FAILED |  |
| CK-PM-52 | The card is not added when an invalid card number and empty code are entered. | 🟢 PASSED |  |
| CK-PM-53 | The card is not added when an invalid card number and valid code are entered. | 🔴 FAILED |  |
| CK-PM-54 | The card is not added when an empty card number and empty code are entered. | 🟢 PASSED |  |
| CK-PM-55 | The card is not added when an empty card number and valid code are entered. | 🟢 PASSED |  |
| CK-PM-56 | The card is not added when an empty card number and invalid code are entered. | 🟢 PASSED |  |
