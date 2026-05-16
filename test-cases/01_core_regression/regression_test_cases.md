# Casos de Prueba de Regresión - Urban Routes

Este documento contiene la matriz de ejecución de los 24 casos de prueba provistos por el equipo de QA para la verificación de la interfaz y la lógica de negocio básica.

## Matriz de Ejecución

| ID | Título | Condición previa | Pasos a seguir | Resultado esperado | Estado | ID Bug Relacionado |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| TC-01 | Interfaz - Direcciones | Validar campo "Desde" con dirección válida | **PASS** | No | N/A |
| TC-02 | Interfaz - Direcciones | Validar campo "Hasta" con dirección válida | **PASS** | No | N/A |
| TC-03 | Módulo Óptimo | Verificar cálculo de tarifa en coche del usuario | **FAIL** | No | [BUG-01](../../bug-reports/BUGS_REPORT.md#bug-01) |
| TC-04 | Módulo Flash | Verificar selección de tarifa Flash | **PASS** | No | N/A |
| ... | ... | ... (Completa con tus 24 casos) | ... | ... | ... |

*Nota: Para ver el detalle del flujo de reproducción de los casos fallidos, diríjase al reporte de errores.*