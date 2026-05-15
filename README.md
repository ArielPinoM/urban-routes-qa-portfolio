# QA Testing: Aplicación Web y Lógica de Negocio - Urban Routes

## 1. Descripción del Proyecto
Urban Routes es una plataforma de transporte que integra múltiples servicios (taxi, automóvil compartido, scooters). El objetivo de este proyecto fue validar la lógica de cálculo de rutas (precio/tiempo), la funcionalidad de reserva de vehículos y la consistencia de la interfaz en diferentes entornos de navegación.

**Problema de Negocio:** Asegurar que el algoritmo de precios sea exacto según la distancia y hora de salida, y que el flujo de registro de conductores/licencias no presente fricciones que impidan la conversión de usuarios.

## 2. Estrategia de Pruebas
Se implementó un enfoque de **Shift-Left Testing**, iniciando con el análisis de requerimientos y diseño de pruebas antes de la ejecución.

* **Tipos de pruebas:** Regresión, Funcionales, UI/UX (Cross-browser), y Pruebas de Caja Negra (Partición de Clases de Equivalencia y Análisis de Valores Límite).
* **Entornos:**
    * Google Chrome (Resolución 800x600).
    * Mozilla Firefox (Resolución 1920x1080).

## 3. Metodología de Diseño de Pruebas
Para garantizar una cobertura exhaustiva, se utilizaron las siguientes técnicas:

* **Análisis de Requisitos:** Descomposición de la función "Compartir automóvil".
* **Mapas Mentales:** Visualización del flujo de "Agregar licencia de conducir" ([Ver mapa](./docs/design/UrbanRoutes_AgregarLicenciaConducir_QA_MindMap.png)).
* **Diagramas de Flujo:** Modelado de la lógica de velocidad promedio según la hora ([Ver diagrama](./docs/design/UrbanRoutes_SeleccionVelocidadAutomovilCompartido_QA__FlowChart.png)).
* **Técnicas de Diseño:**
    * **Clases de Equivalencia (ECP):** Aplicadas a los campos "Nombre", "Apellido", distancia entre las direcciones, Hora de salida (determina la velocidad promedio del transporte), campos "Número de tarjeta" y "Código".
    * **Valores Límite (BVA):** Identificación de puntos críticos para la longitud de caracteres en los campos "Nombre", "Apellido", "Número de tarjeta" y "Código". Tambien, para los límites en las horas de salida.

## 4. Ejecución y Resultados
### Lógica de Cálculo (Ejemplo de Validación)
* **Fórmula:** $T = S / V$ | $Precio = T \times Costo/min$
* **Escenario:** East 2nd St -> 1717 E 7th St (0.89 km) a las 11:00 (30 km/h).
* **Resultado Esperado:** 1.8 min / $0.18.
* **Resultado Observado:** [Insertar si hubo éxito o error].

### Resumen de Hallazgos
| Total de Casos | Pasados | Fallidos | Bloqueados |
| :--- | :--- | :--- | :--- |
| XX | XX | XX | XX |

## 5. Reporte de Errores (Evidencia)
Los errores detectados fueron documentados en Jira, siguiendo el estándar: Título, Pasos de reproducción, Resultado esperado vs. observado, Severidad y Prioridad.
* [Ver Reporte de Errores Consolidado](./bug-reports/BUGS_REPORT.md)
* [Ver Capturas de Jira](./evidence/jira-tickets/)

## 6. Herramientas Utilizadas
* **Gestión:** Jira
* **Diseño:** Figma
* **Documentación:** Google Sheets / Markdown