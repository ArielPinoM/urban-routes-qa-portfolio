# Equivalence Partitioning & Boundary Value Analysis
* **Distance between addresses**
* **Departure Time**

## Hacer Referencia a los requerimientos https://drive.google.com/drive/folders/1s9J7NQ6OsAG2XYfzz8Vr6hwmtBu_hFOk

---

## Equivalence Classes Partitioning (ECP) & Boundary Value Analysis (BVA)
<table>
  <tr>
    <th>Test Group</th>
    <th>Class Name</th>
    <th>Boundaries</th>
    <th>Test Data Within the Class</th>
    <th>Boundary Test Data</th>
  </tr>
<!-- Test Group: Distance Between Addresses -->
  <tr>
    <td rowspan="3"><b>Distance Between Addresses</b></td>
  </tr>

  <tr>
    <td>Distance > 0</td>
    <td></td>
    <td>From: 1300 1st St<br>To: 1811 E 20th St</td>
    <td></td>
  </tr>

  <tr>
    <td>Distance = 0</td>
    <td></td>
    <td>From: East 2nd Street, 601<br>To: East 2nd Street, 601</td>
    <td></td>
  </tr>
  
<!-- Test Group: Departure Time -->
  <tr>
    <td rowspan="6"><b>Departure Time</b></td>
  </tr>

  <tr>
    <td>The departure time is between 00:01 and 08:00</td>
    <td>00:01, 08:00</td>
    <td>04:00</td>
    <td>00:01<br>08:00<br>00:02<br>07:59</td>
  </tr>

  <tr>
    <td>The departure time is between 08:01 and 12:00</td>
    <td>08:01, 12:00</td>
    <td>10:00</td>
    <td>08:01<br>12:00<br>08:02<br>11:59</td>
  </tr>

  <tr>
    <td>The departure time is between 12:01 and 18:00</td>
    <td>12:01, 18:00</td>
    <td>15:00</td>
    <td>12:01<br>18:00<br>12:02<br>17:59</td>
  </tr>

  <tr>
    <td>The departure time is between 18:01 and 22:00</td>
    <td>18:01, 22:00</td>
    <td>20:00</td>
    <td>18:01<br>22:00<br>18:02<br>21:59</td>
  </tr>

  <tr>
    <td>The departure time is between 22:01 and 00:00</td>
    <td>22:01, 00:00</td>
    <td>23:00</td>
    <td>22:01<br>00:00<br>22:02<br>23:59</td>
  </tr>
</table>