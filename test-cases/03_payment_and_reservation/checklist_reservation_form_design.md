# Reservation Form Design Checklist (93 Verification Points)

> 📌 **Note for Reviewers:** This checklist comprehensively validates the design layout, visual constraints, and interactive elements of the primary booking and reservation form.
> * **Execution Environments:** Google Chrome (Viewport: 800x600) & Mozilla Firefox (Viewport: 1920x1080).
> * **Visual Blueprints:** The interface layouts, maps, and component mockups validated in this checklist can be fully reviewed in [visual_references.md > 3. Car Sharing Service Module](../../docs/design/visual_references.md#3-car-sharing-service-module).
> * **Traceability:** 🔴 FAILED verification points are linked directly to their respective reports in the Bug Matrix.

---

## 1. Core Interface & Tariff Selection (Points 01 - 33)

### Tariff Selector (Items 01 - 12)

| Item ID | Monitoring Description | Test Status for Google Chrome 800x600 | Test Status for Firefox 1920x1080 | Bug Report Link |
| :--- | :--- | :--- | :--- | :---: |
| CK-UI-01 | The single fare selector is located at the top of the booking panel. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-02 | Three available fare options are displayed: "Casual", "Camping", and "De lujo". | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-03 | The "Casual" fare is selected by default. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-04 | The selected fare is highlighted in gray. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-05 | The "fare" component includes a car icon. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-06 | The car icon is located at the top of the component. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-07 | The "fare" component includes the fare name. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-08 | The fare name is located below the car icon. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-09 | The "fare" component includes the fare price. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-10 | The fare price is located below the fare name. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-11 | The car icon for the "Casual" fare matches the design. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-12 | The "Casual" fare name matches the text "Casual". | 🟢 PASSED | 🟢 PASSED |  |

### Tariff Descriptions & Details (Items 13 - 33)

| Item ID | Monitoring Description | Test Status for Google Chrome 800x600 | Test Status for Firefox 1920x1080 | Bug Report Link |
| :--- | :--- | :--- | :--- | :---: |
| CK-UI-13 | There is a section with the selected fare details below the fare list. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-14 | The "Fare Details" component includes a badge. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-15 | The badge is located at the top of the component. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-16 | The badge text is bold. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-17 | The "Fare Details" component includes a header (fare description). | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-18 | The header is located below the badge. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-19 | The header text is bold. | 🟢 PASSED | 🔴 FAILED | [UR-BR-08](../../bug-reports/consolidated_bug_matrix.md#ur-br-08) |
| CK-UI-20 | The "Fare Details" component includes a subtitle (trip duration and free waiting time). | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-21 | The subtitle is located below the header. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-22 | The subtitle text is bold. | 🟢 PASSED | 🔴 FAILED | [UR-BR-09](../../bug-reports/consolidated_bug_matrix.md#ur-br-09) |
| CK-UI-23 | The subtitle includes an icon on the left side. | 🔴 FAILED | 🔴 FAILED | [UR-BR-10](../../bug-reports/consolidated_bug_matrix.md#ur-br-10) |
| CK-UI-24 | The icon matches the design. | 🟡 SKIPPED | 🟡 SKIPPED |  |
| CK-UI-25 | The "Fare Details" component includes a car image. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-26 | The "Fare Details" component includes features (additional parameters). | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-27 | The feature text is bold. | 🟢 PASSED | 🔴 FAILED | [UR-BR-11](../../bug-reports/consolidated_bug_matrix.md#ur-br-11) |
| CK-UI-28 | The badge for the "Casual" fare details matches the text "BMW 750". | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-29 | The header for the "Casual" fare details matches the text "Solo negocios, nada más". | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-30 | The subtitle for the "Casual" fare details matches the text "n minutos ● 15 minutos de tiempo de espera gratuito". | 🔴 FAILED | 🔴 FAILED | [UR-BR-12](../../bug-reports/consolidated_bug_matrix.md#ur-br-12) |
| CK-UI-31 | The trip duration is not displayed in the subtitle if the user clears the address from the "From" field. | 🟡 SKIPPED | 🟡 SKIPPED |  |
| CK-UI-32 | The car image in the fare details matches the design. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-33 | The features for the "Casual" fare match the text "cámara frontal ● cargador de teléfono". | 🟢 PASSED | 🟢 PASSED |  |

---

## 2. Map Elements (Points 34 - 36)

### Car Icon Rendering on Map (Items 34 - 36)

| Item ID | Monitoring Description | Test Status for Google Chrome 800x600 | Test Status for Firefox 1920x1080 | Bug Report Link |
| :--- | :--- | :--- | :--- | :---: |
| CK-UI-34 | The icon of the car closest to the user is displayed on the map. | 🔴 FAILED | 🔴 FAILED | [UR-BR-13](../../bug-reports/consolidated_bug_matrix.md#ur-br-13) |
| CK-UI-35 | The icon of the closest car is larger than the others. | 🟡 SKIPPED | 🟡 SKIPPED |  |
| CK-UI-36 | A black label with the brand name is displayed above the car icon. | 🟡 SKIPPED | 🟡 SKIPPED |  |

---

## 3. Form Requirements (Points 37 - 63)

### "Add Driver's License" Field (Items 37 - 42)

| Item ID | Monitoring Description | Test Status for Google Chrome 800x600 | Test Status for Firefox 1920x1080 | Bug Report Link |
| :--- | :--- | :--- | :--- | :---: |
| CK-UI-37 | There is an "Add driver's license" field. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-38 | The "Add driver's license" field is located below the "Fare Details" component. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-39 | The initial state of the "Add driver's license" field is empty. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-40 | The text of the "Add driver's license" field matches the text "Agregar licencia de conducir". | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-41 | The text of the "Add driver's license" field is bold. | 🟢 PASSED | 🔴 FAILED | [UR-BR-14](../../bug-reports/consolidated_bug_matrix.md#ur-br-14) |
| CK-UI-42 | There is a ">" icon inside the "Add driver's license" field next to the right border. | 🔴 FAILED | 🔴 FAILED | [UR-BR-15](../../bug-reports/consolidated_bug_matrix.md#ur-br-15) |

---

### "Payment Method" Field (Items 43 - 55)

| Item ID | Monitoring Description | Test Status for Google Chrome 800x600 | Test Status for Firefox 1920x1080 | Bug Report Link |
| :--- | :--- | :--- | :--- | :---: |
| CK-UI-43 | There is a "Payment Method" field. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-44 | The "Payment Method" field is located below the "Add driver's license" field. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-45 | The initial state of the "Payment Method" field is empty. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-46 | The text in the "Payment Method" field is gray. | 🔴 FAILED | 🔴 FAILED | [UR-BR-16](../../bug-reports/consolidated_bug_matrix.md#ur-br-16) |
| CK-UI-47 | The text in the "Payment Method" field is bold. | 🟢 PASSED | 🔴 FAILED | [UR-BR-17](../../bug-reports/consolidated_bug_matrix.md#ur-br-17) |
| CK-UI-48 | The text in the "Payment Method" field matches the text "Método de pago". | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-49 | An "Agregar" text is displayed inside the "Payment Method" field when it is empty. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-50 | The "Agregar" text inside the "Payment Method" field is aligned to the right side. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-51 | There is a credit card icon inside the "Payment Method" field. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-52 | The credit card icon inside the "Payment Method" field is located to the right of the "Agregar" text. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-53 | The credit card icon inside the "Payment Method" field matches the design. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-54 | There is a ">" icon inside the "Payment Method" field. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-55 | The ">" icon inside the "Payment Method" field is located to the right of the credit card icon. | 🟢 PASSED | 🟢 PASSED |  |

---

### "Order Requirements" Dropdown Menu (Items 56 - 63)

| Item ID | Monitoring Description | Test Status for Google Chrome 800x600 | Test Status for Firefox 1920x1080 | Bug Report Link |
| :--- | :--- | :--- | :--- | :---: |
| CK-UI-56 | There is an "Order Requirements" dropdown menu. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-57 | The "Order Requirements" dropdown menu is collapsed by default. | 🔴 FAILED | 🔴 FAILED | [UR-BR-18](../../bug-reports/consolidated_bug_matrix.md#ur-br-18) |
| CK-UI-58 | The "Order Requirements" dropdown menu expands when another fare is selected. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-59 | The "Order Requirements" dropdown menu is disabled when the user switches back to the "Casual" fare. | 🔴 FAILED | 🔴 FAILED | [UR-BR-19](../../bug-reports/consolidated_bug_matrix.md#ur-br-19) |
| CK-UI-60 | The "Order Requirements" dropdown menu for the "Casual" fare contains a status bar with the text "Cargador de teléfono". | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-61 | The "Cargador de teléfono" status bar includes a checkbox. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-62 | The "Order Requirements" dropdown menu for the "Casual" fare contains a status bar with the text:<br>'Luz de discoteca<br>Disponible en la tarifa "De lujo"'. | 🔴 FAILED | 🔴 FAILED | [UR-BR-20](../../bug-reports/consolidated_bug_matrix.md#ur-br-20) |
| CK-UI-63 | The status bar<br>'Luz de discoteca<br>Disponible en la tarifa "De lujo"'<br>includes a button/hyperlink. | 🟢 PASSED | 🟢 PASSED |  |

---

## 4. Booking Lifecycle & Modal Windows (Points 64 - 93)

### Booking & Reservation Button (Items 64 - 72)

| Item ID | Monitoring Description | Test Status for Google Chrome 800x600 | Test Status for Firefox 1920x1080 | Bug Report Link |
| :--- | :--- | :--- | :--- | :---: |
| CK-UI-64 | There is a booking button. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-65 | The booking button is located in the bottom-left corner of the screen. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-66 | The booking button text is readable. | 🔴 FAILED | 🟢 PASSED | [UR-BR-21](../../bug-reports/consolidated_bug_matrix.md#ur-br-21) |
| CK-UI-67 | The booking button is blue. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-68 | Verify that the booking button text matches<br>"Reservar<br>El recorrido será de .. kilómetros y se hará en .. minutos"<br>when all required fields and addresses have been completed. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-69 | Verify that the booking button text matches<br>"Agregar licencia de conducir y reservar<br>El recorrido será de .. kilómetros y se hará en .. minutos"<br>when all required fields and addresses have been completed except for the driver's license field. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-70 | Verify that the booking button text matches<br>"Agregar método de pago y reservar<br>El recorrido será de .. kilómetros y se hará en .. minutos"<br>when all required fields and addresses have been completed except for the payment method field. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-71 | Verify that the booking button text matches "Agregar direcciones y reservar" when all required fields have been completed and the addresses have been cleared. | 🟡 SKIPPED | 🟡 SKIPPED |  |
| CK-UI-72 | Verify that the booking button text matches "Agregar licencia de conducir y reservar" when none of the required fields have been completed and the addresses have been cleared. | 🟡 SKIPPED | 🟡 SKIPPED |  |

---

### "Car Reserved" Window Overlay (Items 73 - 85)

| Item ID | Monitoring Description | Test Status for Google Chrome 800x600 | Test Status for Firefox 1920x1080 | Bug Report Link |
| :--- | :--- | :--- | :--- | :---: |
| CK-UI-73 | The "Car Reserved" window is displayed without overlapping elements. | 🔴 FAILED | 🔴 FAILED | [UR-BR-22](../../bug-reports/consolidated_bug_matrix.md#ur-br-22) |
| CK-UI-74 | The "Car Reserved" window includes the header "Automóvil reservado". | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-75 | The "Car Reserved" window includes the text "Tiempo de espera gratuito". | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-76 | The "Car Reserved" window includes a timer displaying the free waiting time. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-77 | The "Car Reserved" window includes the brand name. | 🔴 FAILED | 🔴 FAILED | [UR-BR-23](../../bug-reports/consolidated_bug_matrix.md#ur-br-23) |
| CK-UI-78 | The "Car Reserved" window includes the vehicle license plate number. | 🔴 FAILED | 🔴 FAILED | [UR-BR-24](../../bug-reports/consolidated_bug_matrix.md#ur-br-24) |
| CK-UI-79 | The "Car Reserved" window includes the car icon. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-80 | The "Car Reserved" window includes the "X" cancel button. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-81 | The cancel button includes an "X" icon. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-82 | The cancel button includes the text "Cancelar". | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-83 | The "Cancelar" text in the cancel button is located below. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-84 | The "Car Reserved" window includes the car address. | 🟢 PASSED | 🟢 PASSED |  |
| CK-UI-85 | The "Car Reserved" window includes the trip price. | 🟢 PASSED | 🟢 PASSED |  |

---

### "Are you sure you want to cancel the ride?" Confirmation Modal (Items 86-90)

| Item ID | Monitoring Description | Test Status for Google Chrome 800x600 | Test Status for Firefox 1920x1080 | Bug Report Link |
| :--- | :--- | :--- | :--- | :---: |
| CK-UI-86 | The "Are you sure you want to cancel the trip?" window includes the text "¿Seguro que quieres cancelar el viaje?". | 🟡 SKIPPED | 🟡 SKIPPED |  |
| CK-UI-87 | The "Are you sure you want to cancel the trip?" window includes the "No" button. | 🟡 SKIPPED | 🟡 SKIPPED |  |
| CK-UI-88 | The "No" button is gray. | 🟡 SKIPPED | 🟡 SKIPPED |  |
| CK-UI-89 | The "Are you sure you want to cancel the trip?" window includes the "Sí" button. | 🟡 SKIPPED | 🟡 SKIPPED |  |
| CK-UI-90 | The "Sí" button is blue. | 🟡 SKIPPED | 🟡 SKIPPED |  |

---

### "Ride Cancelled" Status Window (Items 91 - 93)

| Item ID | Monitoring Description | Test Status for Google Chrome 800x600 | Test Status for Firefox 1920x1080 | Bug Report Link |
| :--- | :--- | :--- | :--- | :---: |
| CK-UI-91 | The "Ride Canceled" window includes the text "Viaje cancelado". | 🟡 SKIPPED | 🟡 SKIPPED |  |
| CK-UI-92 | The "Ride Canceled" window includes the "Entendido" button. | 🟡 SKIPPED | 🟡 SKIPPED |  |
| CK-UI-93 | The "Entendido" button is blue. | 🟡 SKIPPED | 🟡 SKIPPED |  |
