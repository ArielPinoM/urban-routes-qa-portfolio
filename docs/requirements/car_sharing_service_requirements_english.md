# Requirements — "Car Sharing" Feature

> **Version history**
>
> | Version | Date | Author | Description |
> |---------|------|--------|-------------|
> | 1.0 | 2026-05-17 | Merge of Doc A (V6_Requisitos) + Doc B (Requisitos_Urban_Routes) | Consolidated document. Unresolved conflicts flagged with `[DECISION]`. |
> | 1.1 | 2026-05-18 | Review | Spanish UI strings restored to match app copy. All strings marked with `[UI]` must match the app exactly. |

> **Convention:** strings marked `[UI]` are Spanish app copy and must not be translated. All other text is English documentation.

---

## Table of contents

1. [Service overview](#1-service-overview)
2. [Service access flow](#2-service-access-flow)
3. [Booking a car](#3-booking-a-car)
4. [Booking form](#4-booking-form)
5. [Fare selection panel](#5-fare-selection-panel)
6. ["Agregar licencia de conducir" field](#6-agregar-licencia-de-conducir-field)
7. ["Método de pago" field](#7-método-de-pago-field)
8. ["Requisitos del pedido" panel](#8-requisitos-del-pedido-panel)
9. ["Reservar" button — states](#9-reservar-button--states)
10. [Booking confirmation and timer](#10-booking-confirmation-and-timer)
11. [System parameters — price calculation](#11-system-parameters--price-calculation)
12. [Pending business decisions](#12-pending-business-decisions)

---

## 1. Service overview

"Compartir un automóvil" `[UI]` is an internal service available to **Urban Routes** users. It allows users to book a shared car by selecting an origin, a destination, and a fare — without needing to own a vehicle.

The service follows an **internal B2C model**: the platform manages the available car fleet and assigns vehicles to users based on geographic proximity.

---

## 2. Service access flow

To use the service, the user must follow these steps:

1. Open the **Urban Routes** app.
2. Fill in the **`"Desde"` `[UI]`** and **`"Hasta"` `[UI]`** fields with valid addresses. The app will generate the route and display the available route modes (`"Óptimo"` `[UI]`, `"Flash"` `[UI]`, and `"Personal"` `[UI]`) below the address fields.
3. Choose a route mode:

| Mode `[UI]` | Behaviour | Can the user choose the transport type? |
|-------------|-----------|------------------------------------------|
| **`"Óptimo"`** | The system automatically assigns the transport type (private car, walking, taxi, scooter, bicycle, or shared car). | ❌ Icons are disabled. |
| **`"Flash"`** | Same as `"Óptimo"`. | ❌ Icons are disabled. |
| **`"Personal"`** | The user can freely change the transport type. | ✅ Icons are enabled. |

---

## 3. Booking a car

The user can book a shared car in two situations:

- The app offers `"Compartir un automóvil"` `[UI]` as the transport type in **`"Óptimo"`** or **`"Flash"`** mode.
- The user selects `"Compartir un automóvil"` `[UI]` as the transport type in **`"Personal"`** mode.

When either condition is met, the following are displayed below the mode names:
- The **estimated trip price**.
- The **estimated trip duration**.
- The **`"Reservar"` `[UI]`** button.

Pressing `"Reservar"` `[UI]` replaces the route mode view with the order form.

---

## 4. Booking form

### 4.1 General behaviour

The booking screen allows the user to **remove the entered addresses**, as they are not required to complete a shared car booking. The user can select the desired car directly on the map.

In the form, the user must:
1. Choose a fare (the **`"Casual"`** `[UI]` fare is selected by default).
2. Add their driver's license information.
3. Specify a payment method.
4. Optionally, specify order requirements.

The `"Reservar"` `[UI]` button is located below the `"Requisitos del pedido"` `[UI]` panel.

### 4.2 Field constraints

| Field `[UI]` | Type | Valid values | Required |
|--------------|------|--------------|:--------:|
| `"Elegir tarifa"` | Single selection | `"Casual"`, `"Camping"`, or `"De lujo"` | ✅ |
| `"Agregar licencia de conducir"` | Text / numbers | See [section 6](#6-agregar-licencia-de-conducir-field) | ✅ |
| `"Método de pago"` | Single selection | Bank card only. See [section 7](#7-método-de-pago-field) | ✅ |
| `"Requisitos del pedido"` | Dropdown menu | Panel with additional parameters. See [section 8](#8-requisitos-del-pedido-panel) | ❌ |

**Initial form state:** fare `"Casual"` `[UI]` pre-selected; `"Agregar licencia de conducir"` `[UI]` and `"Método de pago"` `[UI]` fields empty.

---

## 5. Fare selection panel

### 5.1 Panel structure

The panel contains three fares. Each panel item displays:
- The car icon for that fare.
- The fare name `[UI]`.
- The calculated trip price.

**A fare is always selected.** The default is `"Casual"` `[UI]`, but the user can change it.

The selected fare is highlighted in grey. When a fare is selected, the lower section of the panel shows details about the nearest available car.

### 5.2 Information displayed when a fare is selected

- Car make.
- Fare description (heading and subtitle).
- Estimated travel time from the car to the `"Desde"` `[UI]` point *(hidden if the user removed the `"Desde"` address)*.
- Free waiting time.
- Car image.
- Additional fare parameters.

> **Implementation note:** the subtitle text must describe the waiting time in the direction **"desde el automóvil hasta el punto 'Desde'"** `[UI]` (the vehicle's perspective moving towards the user). See [section 12 — Decision #1](#12-pending-business-decisions).

### 5.3 Map behaviour

- The system automatically selects the car nearest to the user. Its map icon enlarges and a black label showing the car make appears above the icon.
- All other available cars remain visible on the map as normal icons, showing vehicles across **all** fares.
- The user can select any car on the map by clicking its icon. Doing so enlarges the icon, displays the black make label, and updates the left panel with the selected car's information.
- If the user **has no bank card on file**, the word `"Agregar"` `[UI]` appears instead of the card indicator. Booking is not possible without a card.

### 5.4 Detailed fare descriptions

| Fare `[UI]` | Make | Heading `[UI]` | Subtitle `[UI]` | Features `[UI]` |
|-------------|------|----------------|-----------------|-----------------|
| **`"Casual"`** | BMW 750 | `"Solo negocios, nada más"` | `"n min · 15 minutos de tiempo de espera gratuito"` | `"Cámara frontal"` · `"Cargador de teléfono"` |
| **`"Camping"`** | Audi A3 Sedan | `"Para viajar"` | `"n min · 12 minutos de tiempo de espera gratuito"` | `"Puertas Bluetooth"` · `"Equipo de acampada"` |
| **`"De lujo"`** | Porsche 911 | `"Brillo, poder, esplendor"` | `"n min · 10 minutos de tiempo de espera gratuito"` | `"Música ligera"` · `"Bebidas para los pasajeros"` |

---

## 6. `"Agregar licencia de conducir"` field

### 6.1 General behaviour

- The field is **empty** by default.
- If the user does not add their driver's license, they **cannot book a car**.
- Clicking the field opens the `"Agregar licencia de conducir"` `[UI]` modal window.
- Text entered by the user is displayed in **black**.
- It is not possible to add **more than one** driver's license per account.

### 6.2 `"Agregar licencia de conducir"` window

The user must enter the following data:

| Field `[UI]` | Type | Valid values | Required |
|--------------|------|--------------|:--------:|
| `"Nombre"` | Text | Latin alphabet letters, spaces, and hyphens only. Length: min 2, max 14 characters. Error: `"Introduce un nombre correcto"` `[UI]`. | ✅ |
| `"Apellido"` | Text | Latin alphabet letters, spaces, and hyphens only. Length: min 2, max 14 characters. Error: `"Introduce un apellido correcto"` `[UI]`. | ✅ |
| `"Fecha de nacimiento"` | Numbers | Format `dd.mm.aaaa`. Numbers only. `dd`: 01–31. `mm`: 01–12. `aaaa`: 1880–2006. Dots are inserted automatically on blur. The system blocks out-of-range characters. | ✅ |
| `"Número"` | Numbers | Format `nn nn nnnnnn`. Numbers only. `nn`: 01–99. `nnnnnn`: 000001–999999. Spaces are inserted automatically on blur. The system blocks out-of-range characters. | ✅ |

> **[DECISION #1 — Pending]:** First name and last name validation differs between source documents. Doc A allows "one space and one hyphen" (maximum one of each); Doc B allows "spaces or hyphens" (multiples permitted). The table above provisionally adopts Doc B's definition (more permissive) until the product team confirms. See [section 12](#12-pending-business-decisions).

### 6.3 Flow after submitting data

1. Once all data has been entered, the following message appears:
   > `"¡Gracias! Los documentos se enviaron para su verificación. En breve, te informaremos sobre los resultados."` `[UI]`
2. An **`"Entendido"` `[UI]`** button appears below the message.
3. Clicking `"Entendido"` `[UI]` closes the window and a **30-second countdown timer** appears in the `"Agregar licencia de conducir"` `[UI]` field.
4. After 30 seconds, the system notifies the user of the verification result.

### 6.4 Field states after verification

| Result | Visual indicator | Behaviour on click |
|--------|-----------------|-------------------|
| **Approved** | Green outline + green checkmark on the right edge of the field. | Field becomes **locked** (not editable). |
| **Rejected** | Red outline + red cross on the right edge of the field. | The `"Agregar licencia de conducir"` `[UI]` form reappears with the message: `"Tus documentos no aprobaron la verificación. Inténtalo de nuevo."` `[UI]` |

---

## 7. `"Método de pago"` field

### 7.1 General behaviour

- The field is **empty** by default.
- The only available payment method is **bank card**.
- To book, the user must add at least one card.
- The user can add **any number of cards** without restriction.
- Once a card is added, the interface shows its **last 4 digits** for identification.

### 7.2 `"Agregar tarjeta"` window

| Field `[UI]` | Constraints |
|--------------|-------------|
| `"Número de tarjeta"` | Format `nnnn nnnn nnnn`. Numbers only. 12 characters. `nnnn`: 0000–9999. Spaces are inserted automatically on blur. Maximum 12 characters (the system blocks additional input). If fewer than 12 characters are entered, the `"Agregar tarjeta"` `[UI]` button remains **inactive**. The system blocks non-numeric characters. |
| `"Código"` | Format `nn`. Numbers only. 2 characters. Range: 01–99. If fewer than 2 characters are entered, the `"Agregar tarjeta"` `[UI]` button remains **inactive**. Maximum 2 characters (the system blocks additional input). The system blocks non-numeric characters. |

---

## 8. `"Requisitos del pedido"` panel

### 8.1 General behaviour

- **`"Casual"` fare (default):** the panel is **hidden / collapsed**.
- **`"Camping"` or `"De lujo"` fares:** the panel **expands automatically** when the fare is selected.
- If the user switches back to `"Casual"`, the panel collapses again.
- The panel is **scrollable**.
- Panel content **differs per fare**.

### 8.2 Panel content by fare

#### `"Casual"` fare

| Item `[UI]` | Control type | Action |
|-------------|-------------|--------|
| `"Cargador de teléfono"` | Checkbox | Selected / Not selected |
| `"Luz de discoteca"` *(`"Disponible en la tarifa 'De lujo'"` `[UI]`)* | Button / Hyperlink | Switches fare to `"De lujo"` |

#### `"Camping"` fare

| Item `[UI]` | Control type | Limits / Action |
|-------------|-------------|-----------------|
| `"Spray antimosquitos"` | Stepper | 0–2 sprays (inclusive) |
| `"Saco de dormir"` | Stepper | 0–5 bags (inclusive) |
| `"Luz de discoteca"` *(`"Disponible en la tarifa 'De lujo'"` `[UI]`)* | Button / Hyperlink | Switches fare to `"De lujo"` |

#### `"De lujo"` fare

| Item `[UI]` | Control type | Limits / Action |
|-------------|-------------|-----------------|
| `"Luz de discoteca"` | Checkbox | Selected / Not selected |
| `"Relajante"` — `"Bebidas para los pasajeros"` / `"Fruta para los pasajeros"` | Radio buttons | Only one option can be selected |
| `"Copas frías"` | Stepper | 0–3 (inclusive) |

---

## 9. `"Reservar"` button — states

The button is located in the **bottom-left corner** of the screen.

| Field state | Button text `[UI]` | Action on press |
|-------------|-------------------|-----------------|
| All required fields and addresses completed | **`"Reservar"`** · `"El recorrido será de … kilómetros y se hará en … minutos"` | `"Automóvil reservado"` window appears |
| All fields completed except **driver's license** | **`"Agregar licencia de conducir y reservar"`** · `"El recorrido será de … kilómetros y se hará en … minutos"` | `"Agregar licencia de conducir"` window appears |
| All fields completed except **payment method** | **`"Agregar método de pago y reservar"`** · `"El recorrido será de … kilómetros y se hará en … minutos"` | `"Tarjeta agregada"` window appears |
| All required fields completed but **addresses removed** | **`"Agregar direcciones y reservar"`** | Button is **not clickable** |
| No required fields completed and **addresses removed** | **`"Agregar licencia de conducir y reservar"`** | `"Agregar licencia de conducir"` window appears |

---

## 10. Booking confirmation and timer

### 10.1 `"Automóvil reservado"` window

If the user correctly completes all fields and presses `"Reservar"` `[UI]`, the **`"Automóvil reservado"` `[UI]`** window appears, containing:

- Car make.
- License plate number.
- Car icon.
- Current car location.
- Trip price:
  - If `"Desde"` `[UI]` and `"Hasta"` `[UI]` fields are filled → the **exact trip price** is shown.
  - If not → the **per-minute price** is shown.
- Free waiting time countdown timer.

### 10.2 Timer

- The timer starts counting from the moment the user presses `"Reservar"` `[UI]`.
- During the free waiting period, the user can **cancel the trip at no charge**.
- Once the free waiting period expires, the timer begins counting **shared vehicle usage time** (billable time).

---

## 11. System parameters — price calculation

### 11.1 Default price display

The app displays the **exact trip price** by default, calculated using the formula in section 11.3.

### 11.2 Fare coefficients

| Fare `[UI]` | Coefficient |
|-------------|:-----------:|
| `"Casual"` | 1.5 |
| `"Camping"` | 2.0 |
| `"De lujo"` | 3.0 |

### 11.3 Pricing formula

```
trip_price = fixed_rental_fee + (60 × per_minute_price × duration_h) × fare_coefficient
```

**Fixed system values:**

| Parameter | Value |
|-----------|-------|
| Fixed rental fee | $2.00 |
| Per-minute usage price | $0.10 |

**Trip duration in hours** = `distance_km / speed_km_h`

**Canonical example from source document** (duration 1.25 h, coefficient 1.5):

```
2 + (60 × 0.1 × 1.25) × 1.5 = $13.25
```

### 11.4 Average car speed

The usage cost is **$0.10 / min**, regardless of time of day. The time slot affects the **speed** and therefore the **calculated trip duration**.

| Time slot | Average speed |
|-----------|:------------:|
| 00:01 – 08:00 | 45 km/h |
| 08:01 – 12:00 | 30 km/h |
| 12:01 – 18:00 | 40 km/h |
| 18:01 – 22:00 | 25 km/h |
| 22:01 – 00:00 | 45 km/h |

> **Interval rule:** if a trip spans multiple time slots, the algorithm uses the speed of the slot in which the **trip begins**.

### 11.5 Distance matrix (km) — highway routes

| | East 2nd St, 601 | 1300 1st St | 4201 Whittier Blvd | 1717 E 7th St | 1917 Bay St | 1811 E 20th St | 615 S Broadway |
|-|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| **East 2nd St, 601** | 0 | 1.4 | 1.5 | 0.89 | 2.6 | 2.6 | 2.6 |
| **1300 1st St** | 1.4 | 0 | 2.9 | 2.3 | 2.3 | 2.3 | 2.3 |
| **4201 Whittier Blvd** | 1.4 | 1.5 | 0 | 1.9 | 3.8 | 3.0 | 3.3 |
| **1717 E 7th St** | 1.5 | 3.0 | 2.4 | 0 | 1.2 | 3.4 | 2.3 |
| **1917 Bay St** | 1.5 | 3.7 | 3.7 | 1.2 | 0 | 1.7 | 1.7 |
| **1811 E 20th St** | 3.2 | 3.9 | 4.7 | 2.7 | 1.7 | 0 | 2.2 |
| **615 S Broadway** | 1.4 | 2.4 | 3.5 | 2.3 | 1.4 | 1.3 | 0 |

---

## 12. Pending business decisions

The following decisions must be made **before implementation begins** on the affected modules. Until resolved, the document adopts the provisional value indicated.

### Decision #1 — First name / last name validation in driver's license

| | Doc A (V6_Requisitos) | Doc B (Requisitos_Urban_Routes) | Provisional value |
|-|-----------------------|--------------------------------|-------------------|
| **Allowed characters** | Latin letters, **one** space and **one** hyphen (maximum one of each) | Latin letters, **spaces** or **hyphens** (multiples allowed) | Doc B definition (more permissive) |
| **Impact** | Frontend validation regex | QA test cases | — |
| **Affected examples** | "Anne-Marie" ✅ Doc B / ❓ Doc A · "De La Cruz" ✅ Doc B / ❌ Doc A | — | — |

**Action required:** the Product Owner must confirm which definition applies before the frontend team implements field validation.

### Decision #2 — Waiting time subtitle wording

| | Doc A | Doc B |
|-|-------|-------|
| **Wording `[UI]`** | `"…desde el automóvil hasta el punto 'Desde'"` | `"…desde el punto 'Desde' hasta el automóvil"` |
| **Physical meaning** | Identical (time for the car to reach the user) | — |

**Action required:** choose the definitive UI string and update it in the internationalisation system.

---

*Document generated by merging V6_Requisitos_para_la_funcionalidad_Compartir_un_automóvil (Doc A) and Requisitos_para_compartir_un_automóvil_en_Urban_Routes (Doc B). Identified conflicts are flagged with the `[DECISION]` tag. Strings marked `[UI]` are Spanish app copy and must not be translated. For the full compatibility analysis history, see the attached merge report.*