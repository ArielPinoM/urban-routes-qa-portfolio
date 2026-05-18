# Requisitos — Funcionalidad "Compartir un automóvil"
**Urban Routes · Documento unificado**

> **Historial de versiones**
>
> | Versión | Fecha | Autor | Descripción |
> |---------|-------|-------|-------------|
> | 1.0 | 2026-05-17 | Fusión Doc A (V6_Requisitos) + Doc B (Requisitos_Urban_Routes) | Documento consolidado. Conflictos resueltos marcados con `[DECISIÓN]`. |

---

## Índice

1. [Descripción general del servicio](#1-descripción-general-del-servicio)
2. [Flujo de acceso al servicio](#2-flujo-de-acceso-al-servicio)
3. [Reservar un automóvil](#3-reservar-un-automóvil)
4. [Formulario de reserva](#4-formulario-de-reserva)
5. [Panel de selección de tarifas](#5-panel-de-selección-de-tarifas)
6. [Campo "Agregar licencia de conducir"](#6-campo-agregar-licencia-de-conducir)
7. [Campo "Método de pago"](#7-campo-método-de-pago)
8. [Panel "Requisitos del pedido"](#8-panel-requisitos-del-pedido)
9. [Botón "Reservar" — estados](#9-botón-reservar--estados)
10. [Confirmación de reserva y temporizador](#10-confirmación-de-reserva-y-temporizador)
11. [Parámetros del sistema — cálculo de precio](#11-parámetros-del-sistema--cálculo-de-precio)
12. [Decisiones de negocio pendientes](#12-decisiones-de-negocio-pendientes)

---

## 1. Descripción general del servicio

"Compartir un automóvil" es un servicio interno disponible para los usuarios de **Urban Routes**. Permite reservar un automóvil compartido seleccionando origen, destino y tarifa, sin necesidad de que el usuario sea propietario del vehículo.

El servicio es de tipo **B2C interno**: la plataforma gestiona la flota de automóviles disponibles y los asigna al usuario según proximidad geográfica.

---

## 2. Flujo de acceso al servicio

Para utilizar el servicio, el usuario debe seguir estos pasos:

1. Abrir la aplicación **Urban Routes**.
2. Completar los campos **"Desde"** y **"Hasta"** con direcciones válidas. La aplicación generará la ruta y mostrará los modos disponibles ("Óptimo", "Flash" y "Personal") debajo de los campos de dirección.
3. Elegir el modo de ruta:

| Modo | Comportamiento | ¿El usuario elige el tipo de transporte? |
|------|---------------|------------------------------------------|
| **Óptimo** | El sistema asigna automáticamente el tipo de transporte (automóvil particular, a pie, taxi, scooter, bicicleta o automóvil compartido). | ❌ Los íconos están desactivados. |
| **Flash** | Igual que Óptimo. | ❌ Los íconos están desactivados. |
| **Personal** | El usuario puede cambiar libremente el tipo de transporte. | ✅ Los íconos están activos. |

---

## 3. Reservar un automóvil

El usuario puede reservar un automóvil compartido en dos situaciones:

- La aplicación ofrece "Compartir un automóvil" como tipo de transporte en los modos **Óptimo** o **Flash**.
- El usuario elige "Compartir un automóvil" como tipo de transporte en el modo **Personal**.

Cuando se cumple alguna de estas condiciones, se muestra debajo de los nombres de los modos:
- El **precio estimado** del viaje.
- La **duración estimada** del viaje.
- El botón **"Reservar"**.

Al pulsar "Reservar", el formulario del pedido reemplaza la vista de los modos de ruta.

---

## 4. Formulario de reserva

### 4.1 Comportamiento general

La pantalla de reserva permite **eliminar las direcciones** ingresadas, ya que no son obligatorias para completar la reserva de un automóvil compartido. El usuario puede elegir el automóvil de su interés directamente en el mapa.

En el formulario, el usuario debe:
1. Elegir la tarifa (la tarifa **"Casual"** queda seleccionada por defecto).
2. Añadir información sobre su licencia de conducir.
3. Indicar el método de pago.
4. Opcionalmente, especificar requisitos del pedido.

El botón "Reservar" se ubica debajo del panel "Requisitos del pedido".

### 4.2 Restricciones de los campos

| Campo | Tipo | Valores válidos | Obligatorio |
|-------|------|-----------------|:-----------:|
| Elegir tarifa | Selección única | "Casual", "Camping" o "De lujo" | ✅ |
| Licencia de conducir | Texto / números | Ver [sección 6](#6-campo-agregar-licencia-de-conducir) | ✅ |
| Método de pago | Selección única | Tarjeta bancaria únicamente. Ver [sección 7](#7-campo-método-de-pago) | ✅ |
| Requisitos del pedido | Menú desplegable | Panel con parámetros adicionales. Ver [sección 8](#8-panel-requisitos-del-pedido) | ❌ |

**Estado inicial del formulario:** tarifa "Casual" preseleccionada; campos "Agregar licencia de conducir" y "Método de pago" vacíos.

---

## 5. Panel de selección de tarifas

### 5.1 Estructura del panel

El panel contiene tres tarifas. Cada elemento del panel muestra:
- Ícono del automóvil correspondiente.
- Nombre de la tarifa.
- Precio calculado del viaje.

**Siempre hay una tarifa seleccionada.** Por defecto es "Casual", pero el usuario puede cambiarla.

La tarifa seleccionada se resalta en gris. Al seleccionar una tarifa, la sección inferior del panel muestra los detalles del automóvil más cercano disponible.

### 5.2 Información mostrada al seleccionar una tarifa

- Marca del automóvil.
- Descripción de la tarifa (encabezado y subtítulo).
- Duración estimada del viaje desde el automóvil hasta el punto "Desde" *(no se mostrará si el usuario eliminó la dirección en el campo "Desde")*.
- Tiempo de espera gratuito.
- Imagen del automóvil.
- Parámetros adicionales de la tarifa.

> **Nota de implementación:** el texto del subtítulo debe describir el tiempo de espera en dirección **"desde el automóvil hasta el punto 'Desde'"** (perspectiva del vehículo desplazándose hacia el usuario). Ver [sección 12 — Decisión #1](#12-decisiones-de-negocio-pendientes).

### 5.3 Comportamiento del mapa

- El sistema selecciona automáticamente el automóvil más cercano al usuario. Su ícono en el mapa se amplía y aparece un recuadro negro con la marca del vehículo sobre el ícono.
- Los demás automóviles disponibles se visualizan como íconos normales en el mapa, mostrando vehículos de **todas** las tarifas.
- El usuario puede seleccionar cualquier automóvil en el mapa haciendo clic sobre su ícono. Al hacerlo, el ícono se amplía, aparece el recuadro negro con la marca, y el panel izquierdo actualiza la información del vehículo seleccionado.
- Si el usuario **no tiene tarjeta bancaria añadida**, aparece la palabra "Agregar" en lugar del indicador de tarjeta. No es posible completar la reserva sin tarjeta.

### 5.4 Descripción detallada de las tarifas

| Tarifa | Marca | Encabezado | Subtítulo | Características |
|--------|-------|------------|-----------|-----------------|
| **Casual** | BMW 750 | Solo negocios, nada más | n min · 15 min de espera gratuita | Cámara frontal · Cargador de teléfono |
| **Camping** | Audi A3 Sedan | Para viajar | n min · 12 min de espera gratuita | Puertas Bluetooth · Equipo de acampada |
| **De lujo** | Porsche 911 | Brillo, poder, esplendor | n min · 10 min de espera gratuita | Música ligera · Bebidas para los pasajeros |

---

## 6. Campo "Agregar licencia de conducir"

### 6.1 Comportamiento general

- Por defecto, el campo está **vacío**.
- Si el usuario no añade su licencia de conducir, **no podrá reservar un automóvil**.
- Al hacer clic en el campo, aparece la ventana modal "Agregar licencia de conducir".
- El texto introducido por el usuario se muestra en **color negro**.
- No es posible añadir **más de una** licencia de conducir por cuenta.

### 6.2 Ventana "Agregar licencia de conducir"

El usuario debe ingresar los siguientes datos:

| Campo | Tipo | Valores válidos | Obligatorio |
|-------|------|-----------------|:-----------:|
| Nombre | Texto | Solo letras del alfabeto latino, espacios y guiones. Longitud: mínimo 2, máximo 14 caracteres. Error: *"Introduce un nombre correcto"*. | ✅ |
| Apellido | Texto | Solo letras del alfabeto latino, espacios y guiones. Longitud: mínimo 2, máximo 14 caracteres. Error: *"Introduce un apellido correcto"*. | ✅ |
| Fecha de nacimiento | Números | Formato `dd.mm.aaaa`. Solo números. `dd`: 01–31. `mm`: 01–12. `aaaa`: 1880–2006. Los puntos se insertan automáticamente al quitar el foco. El sistema bloquea caracteres fuera del rango. | ✅ |
| Número de licencia | Números | Formato `nn nn nnnnnn`. Solo números. `nn`: 01–99. `nnnnnn`: 000001–999999. Los espacios se insertan automáticamente al quitar el foco. El sistema bloquea caracteres fuera del rango. | ✅ |

> **[DECISIÓN #1 — Pendiente]:** La validación de Nombre y Apellido difiere entre documentos fuente. Doc A permite "un espacio y un guión" (máximo uno de cada uno); Doc B permite "espacios o guiones" (múltiples). La tabla anterior adopta la definición de Doc B (más permisiva) como valor provisional hasta que el equipo de producto confirme. Ver [sección 12](#12-decisiones-de-negocio-pendientes).

### 6.3 Flujo tras completar los datos

1. Al introducir todos los datos, aparece el mensaje:
   > *"¡Gracias! Los documentos se enviaron para su verificación. En breve, te informaremos sobre los resultados."*
2. Debajo del mensaje aparece el botón **"Entendido"**.
3. Al hacer clic en "Entendido", la ventana se cierra y en el campo "Agregar licencia de conducir" aparece un **temporizador de 30 segundos**.
4. Transcurridos los 30 segundos, el sistema informa al usuario del resultado de la verificación.

### 6.4 Estados del campo tras la verificación

| Resultado | Indicador visual | Comportamiento al hacer clic |
|-----------|-----------------|------------------------------|
| **Aprobado** | Contorno verde + marca de verificación verde en el borde derecho del campo. | El campo queda **bloqueado** (no editable). |
| **Rechazado** | Contorno rojo + cruz roja en el borde derecho del campo. | Reaparece el formulario "Agregar licencia de conducir" con el texto: *"Tus documentos no aprobaron la verificación. Inténtalo de nuevo."* |

---

## 7. Campo "Método de pago"

### 7.1 Comportamiento general

- Por defecto, el campo está **vacío**.
- El único método de pago disponible es **tarjeta bancaria**.
- Para reservar, el usuario debe añadir al menos una tarjeta.
- El usuario puede añadir **cualquier número de tarjetas** sin restricción.
- Cuando se añade una tarjeta, la interfaz muestra los **últimos 4 dígitos** del número para facilitar la identificación.

### 7.2 Ventana "Agregar tarjeta"

| Campo | Restricciones |
|-------|---------------|
| **Número de tarjeta** | Formato `nnnn nnnn nnnn`. Solo números. 12 caracteres. `nnnn`: 0000–9999. Los espacios se insertan automáticamente al quitar el foco. Máximo 12 caracteres (el sistema bloquea caracteres adicionales). Si se ingresan menos de 12 caracteres, el botón "Agregar tarjeta" permanece **inactivo**. El sistema bloquea caracteres no numéricos. |
| **Código** | Formato `nn`. Solo números. 2 caracteres. Rango: 01–99. Si se ingresan menos de 2 caracteres, el botón "Agregar tarjeta" permanece **inactivo**. Máximo 2 caracteres (el sistema bloquea caracteres adicionales). El sistema bloquea caracteres no numéricos. |

---

## 8. Panel "Requisitos del pedido"

### 8.1 Comportamiento general

- **Tarifa "Casual" (por defecto):** el panel se muestra **oculto/colapsado**.
- **Tarifas "Camping" o "De lujo":** el panel se **despliega automáticamente** al seleccionar la tarifa.
- Si el usuario regresa a la tarifa "Casual", el panel vuelve a ocultarse.
- Es posible **desplazarse** dentro del panel.
- El contenido del panel es **diferente para cada tarifa**.

### 8.2 Contenido del panel por tarifa

#### Tarifa "Casual"

| Ítem | Tipo de control | Acción |
|------|----------------|--------|
| Cargador de teléfono | Casilla de verificación | Seleccionado / No seleccionado |
| Luz de discoteca *(Disponible en la tarifa "De lujo")* | Botón / Hipervínculo | Cambia la tarifa a "De lujo" |

#### Tarifa "Camping"

| Ítem | Tipo de control | Límites / Acción |
|------|----------------|------------------|
| Spray antimosquitos | Taxímetro | 0–2 sprays (incluidos) |
| Saco de dormir | Taxímetro | 0–5 sacos (incluidos) |
| Luz de discoteca *(Disponible en la tarifa "De lujo")* | Botón / Hipervínculo | Cambia la tarifa a "De lujo" |

#### Tarifa "De lujo"

| Ítem | Tipo de control | Límites / Acción |
|------|----------------|------------------|
| Luz de discoteca | Casilla de verificación | Seleccionado / No seleccionado |
| Relajante — Bebidas para los pasajeros / Fruta para los pasajeros | Botones de radio | Solo se puede elegir una opción |
| Copas frías | Taxímetro | 0–3 (incluidos) |

---

## 9. Botón "Reservar" — estados

El botón está situado en la **esquina inferior izquierda** de la pantalla.

| Estado de los campos | Texto del botón | Acción al pulsar |
|----------------------|----------------|-----------------|
| Todos los campos y direcciones requeridos completados | **"Reservar"** · *El recorrido será de … km y se hará en … min* | Aparece la ventana "Automóvil reservado" |
| Todos los campos completados, excepto la **licencia de conducir** | **"Agregar licencia de conducir y reservar"** · *El recorrido será de … km y se hará en … min* | Aparece la ventana "Agregar licencia de conducir" |
| Todos los campos completados, excepto el **método de pago** | **"Agregar método de pago y reservar"** · *El recorrido será de … km y se hará en … min* | Aparece la ventana "Tarjeta agregada" |
| Todos los campos obligatorios completados, pero **sin direcciones** | **"Agregar direcciones y reservar"** | El botón **no es pulsable** |
| Ningún campo completado y **sin direcciones** | **"Agregar licencia de conducir y reservar"** | Aparece la ventana "Agregar licencia de conducir" |

---

## 10. Confirmación de reserva y temporizador

### 10.1 Ventana "Automóvil reservado"

Si el usuario completó todos los campos correctamente y pulsó "Reservar", aparece la ventana con el encabezado **"Automóvil reservado"**, que contiene:

- Marca del vehículo.
- Número de placa.
- Ícono del automóvil.
- Dirección actual del automóvil.
- Precio del viaje:
  - Si los campos "Desde" y "Hasta" están completados → se muestra el **precio exacto del trayecto**.
  - Si no → se muestra el **precio por minuto**.
- Temporizador de tiempo de espera gratuito.

### 10.2 Temporizador

- El temporizador comienza a contar desde el momento en que el usuario pulsa "Reservar".
- Durante el tiempo de espera gratuito, el usuario puede **cancelar el viaje de forma gratuita**.
- Una vez agotado el tiempo de espera gratuito, el temporizador comienza a contar el **tiempo de uso compartido del vehículo** (tiempo facturable).

---

## 11. Parámetros del sistema — cálculo de precio

### 11.1 Precio por defecto

La aplicación muestra por defecto el **precio exacto** del viaje, calculado mediante la fórmula de la sección 11.3.

### 11.2 Coeficientes por tarifa

| Tarifa | Coeficiente |
|--------|:-----------:|
| Casual | 1.5 |
| Camping | 2.0 |
| De lujo | 3.0 |

### 11.3 Fórmula de cálculo

```
precio_viaje = precio_fijo_alquiler + (60 × precio_por_minuto × duración_h) × coeficiente_tarifa
```

**Valores fijos del sistema:**

| Parámetro | Valor |
|-----------|-------|
| Precio fijo de alquiler | $2.00 |
| Precio por minuto de uso | $0.10 |

**Duración del viaje en horas** = `distancia_km / velocidad_km_h`

**Ejemplo con tarifa "Casual"** (distancia 1.4 km, velocidad 30 km/h → duración ≈ 0.0467 h):

> No incluido para evitar confusión con datos de prueba específicos. Ver matriz de distancias y tabla de velocidades para construir casos de prueba reales.

**Ejemplo canónico del documento fuente** (duración 1.25 h, coeficiente 1.5):

```
2 + (60 × 0.1 × 1.25) × 1.5 = $13.25
```

### 11.4 Velocidad media del automóvil compartido

El costo por uso es **$0.10 / min**, independientemente de la franja horaria. La franja horaria afecta la **velocidad** y por tanto la **duración calculada** del viaje.

| Franja horaria | Velocidad media |
|---------------|:--------------:|
| 00:01 – 08:00 | 45 km/h |
| 08:01 – 12:00 | 30 km/h |
| 12:01 – 18:00 | 40 km/h |
| 18:01 – 22:00 | 25 km/h |
| 22:01 – 00:00 | 45 km/h |

> **Regla de intervalos:** si el viaje abarca varias franjas horarias, el algoritmo utiliza la velocidad correspondiente a la franja en la que **comienza el viaje**.

### 11.5 Matriz de distancias (km) — rutas con autopistas

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

## 12. Decisiones de negocio pendientes

Las siguientes decisiones deben tomarse **antes de comenzar la implementación** de los módulos afectados. Hasta que se resuelvan, el documento adopta el valor provisional indicado.

### Decisión #1 — Validación de Nombre y Apellido en licencia de conducir

| | Doc A (V6_Requisitos) | Doc B (Requisitos_Urban_Routes) | Valor provisional |
|-|-----------------------|--------------------------------|-------------------|
| **Caracteres permitidos** | Solo letras latinas, **un** espacio y **un** guión (máximo uno de cada uno) | Solo letras latinas, **espacios** o **guiones** (múltiples permitidos) | Definición de Doc B (más permisiva) |
| **Impacto** | Regex de validación frontend | Casos de prueba QA | — |
| **Ejemplos afectados** | "Anne-Marie" ✅ Doc B / ❓ Doc A · "De La Cruz" ✅ Doc B / ❌ Doc A | — | — |

**Acción requerida:** el Product Owner debe confirmar cuál de las dos definiciones aplica antes de que el equipo de frontend implemente la validación del campo.

### Decisión #2 — Redacción del subtítulo de tiempo de espera

| | Doc A | Doc B |
|-|-------|-------|
| **Redacción** | "…desde el **automóvil** hasta el punto 'Desde'" | "…desde el punto **'Desde'** hasta el automóvil" |
| **Sentido físico** | Idéntico (tiempo que tarda el auto en llegar al usuario) | — |

**Acción requerida:** elegir la redacción UI definitiva y actualizar las cadenas de texto en el sistema de internacionalización.

---

*Documento generado mediante fusión de V6_Requisitos_para_la_funcionalidad_Compartir_un_automóvil (Doc A) y Requisitos_para_compartir_un_automóvil_en_Urban_Routes (Doc B). Conflictos identificados marcados con etiqueta `[DECISIÓN]`. Para historial de análisis de compatibilidad, ver informe de fusión adjunto.*