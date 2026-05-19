> 📌 **Technical Reference:** This document contains the logical test design partitions used to derive the 56 verification points in the Payment Methods Checklist.
> * **Target Component:** "Payment Method" -> "Add Card" Form.
> * **Requirement Mapping:** [PRD - Section 7: "Payment method" field](../../docs/requirements/car_sharing_service_requirements_english.md#7-método-de-pago-field)

## 1. Equivalence Partitioning (EP) & Boundary Value Analysis (BVA)

### 1.1 Card Number Field (Strict 12-Digit Numeric Constraint)
* **Core Rule:** Must accept exactly 12 numeric characters (`nnnn nnnn nnnn`). Spaces are inserted automatically on blur. Maximum input length is capped at 12; any characters beyond this limit must be blocked by the system.

<table>
  <tr>
    <th>Test Group</th>
    <th>Class Name</th>
    <th>Boundaries</th>
    <th>Test Data Within the Class (Field Content)</th>
    <th>Boundary Test Data (Field Content)</th>
  </tr>
<!-- Test Group: Card Number -->
  <tr>
    <td rowspan="13"><b>Card Number</b></td>
  </tr>

  <tr>
    <td>The number length is 12 characters.</td>
    <td>12</td>
    <td>12 chars — "123443211408"</td>
    <td>12 — "123443211408</td>
  </tr>

  <tr>
    <td>The number length is 11 character or fewer.</td>
    <td>11</td>
    <td>5 chars — "12344"</td>
    <td>11 char — "12344321140"<br>10 — "1234432114"</td>
  </tr>

  <tr>
   <td>The number length is 13 characters or more.</td>
   <td>13</td>
   <td>15 chars — "123443211408123"</td>
   <td>13 — "1234432114088"<br>14 — "12344321140888"</td>
  </tr>

  <tr>
   <td>Group nnnn: 0000 - 9999</td>
   <td>0000, 9999</td>
   <td>4999</td>
   <td>0000<br>9999<br>0001<br>9998</td>
  </tr>

  <tr>
   <td>Group nnnn: 10000 and more.</td>
   <td>10000</td>
   <td>20000</td>
   <td>10000<br>10001</td>
  </tr>

  <tr>
    <td>Empty Field.</td>
    <td></td>
    <td>0 — Empty string</td>
    <td></td>
  </tr>

  <tr>
    <td>Number with numeric characters.</td>
    <td></td>
    <td>12 chars — "123443211408"</td>
    <td></td>
  </tr>

  <tr>
    <td>Number containing spaces.</td>
    <td></td>
    <td>12 chars — "123 432 1408"</td>
    <td></td>
  </tr>

  <tr>
    <td>Number containing hyphens.</td>
    <td></td>
    <td>12 chars — "123-432-1408"</td>
    <td></td>
  </tr>

  <tr>
    <td>Number containing letters.</td>
    <td></td>
    <td>12 chars — "a123b32c1408"</td>
    <td></td>
  </tr>

  <tr>
    <td>Special characters.</td>
    <td></td>
    <td>12 chars — "@123/32$1408"</td>
    <td></td>
  </tr>

  <tr>
    <td>Characters from other languages.</td>
    <td></td>
    <td>12 chars — "布123加32爾1408"</td>
    <td></td>
  </tr>
</table>

### 1.2 Security Code / CVV Field (Strict 2-Digit Numeric Constraint)
* **Core Rule:** Must accept exactly 2 numeric characters (`nn`) within the range of 01–99. Maximum input length is capped at 2.

<table>
  <tr>
    <th>Test Group</th>
    <th>Class Name</th>
    <th>Boundaries</th>
    <th>Test Data Within the Class (Field Content)</th>
    <th>Boundary Test Data (Field Content)</th>
  </tr>

  <tr>
    <td rowspan="13"><b>Security Code</b></td>
  </tr>

  <tr>
    <td>The number length is 2 characters.</td>
    <td>2</td>
    <td>2 chars — "12"</td>
    <td>2 — "12"</td>
  </tr>

  <tr>
    <td>The number length is 1 character or fewer.</td>
    <td>1</td>
    <td>1 char — "4"</td>
    <td>1 char — "1"</td>
  </tr>

  <tr>
   <td>The number length is 3 characters or more.</td>
   <td>3</td>
   <td>3 chars — "490"</td>
   <td>3 — "123"<br>4 — "1234"</td>
  </tr>

  <tr>
   <td>Group nn: 01 - 99</td>
   <td>01, 99</td>
   <td>49</td>
   <td>01<br>99<br>02<br>98</td>
  </tr>

  <tr>
   <td>Group nn: 99 and more.</td>
   <td>100</td>
   <td>200</td>
   <td>100<br>101</td>
  </tr>

  <tr>
    <td>Empty Field.</td>
    <td></td>
    <td>0 — Empty string</td>
    <td></td>
  </tr>

  <tr>
    <td>Number with numeric characters.</td>
    <td></td>
    <td>2 chars — "12"</td>
    <td></td>
  </tr>

  <tr>
    <td>Number containing spaces.</td>
    <td></td>
    <td>2 chars — "1 "</td>
    <td></td>
  </tr>

  <tr>
    <td>Number containing hyphens.</td>
    <td></td>
    <td>2 caracteres — "1-"</td>
    <td></td>
  </tr>

  <tr>
    <td>Number containing letters.</td>
    <td></td>
    <td>2 chars — "1a"</td>
    <td></td>
  </tr>

  <tr>
    <td>Special characters.</td>
    <td></td>
    <td>2 chars — "1$"</td>
    <td></td>
  </tr>

  <tr>
    <td>Characters from other languages.</td>
    <td></td>
    <td>2 chars — "1爾"</td>
    <td></td>
  </tr>
</table>