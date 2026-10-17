# Protocolo obligatorio de verificación antes de publicar

Este archivo es para asistentes de programación (incluidos agentes IA) que modifican este repositorio. Objetivo: **no utilizar GitHub Actions ni los correos de fallos como entorno de prueba**.

## Orden obligatorio de trabajo

1. Leer README, estructura, instrucciones propias, workflows y estado actual. Limitar cambios al pedido y preservar material existente.
2. Determinar los comandos de comprobación que aplican realmente a los archivos cambiados. Ejecutarlos **antes de cualquier commit/push** en un entorno local o aislado; verificar la salida y el código de retorno. Nunca declarar una prueba aprobada sin ejecutarla.
3. Ejecutar siempre `git diff --check`, comprobar los cambios con `git diff` y revisar `git status --short`. Comprobar que no entren credenciales, tokens, datos privados ni archivos generados innecesarios.
4. Si hay Python, JavaScript, TypeScript, cuadernos, SQL o HTML modificados: validar sintaxis y estructura con las herramientas de ese lenguaje, y ejecutar las pruebas del proyecto relevantes. Si existen workflows, ejecutar previamente sus pasos de validación equivalentes que no dependan de servicios externos. Para notebooks, comprobar JSON y ejecutar celdas cuando sea viable, distinguiendo pruebas simuladas de integraciones reales.
5. Para interfaces, validar navegación, consola, enlaces y una pantalla móvil además de escritorio. Para acciones externas o despliegues, usar modo seguro/dry-run si existe; nunca realizar efectos reales solo para “probar”.
6. **Si falla una comprobación, detener la publicación, corregir y repetir la validación local.** No hacer secuencias de pushes de prueba. Si el entorno impide una validación esencial, explicarlo sin inventar resultados y no presentar el trabajo como verificado.
7. Solo después de pasar las validaciones, publicar un cambio cohesivo. Preferir rama y pull request para cambios de riesgo; no convertir `main` en banco de pruebas. Después del push, verificar los checks activados y el sitio/servicio cuando aplique; GitHub Actions es una segunda barrera, no la primera.
8. Si el check remoto falla, leer primero el log exacto, reproducir y corregir localmente ANTES de un nuevo push. No desactivar, suprimir ni maquillar tests para obtener verde.

## Comunicación

Reportar: archivos modificados, pruebas y comandos ejecutados, resultados reales, puntos no verificados y URL del commit/PR. No afirmar “listo” mientras haya fallos relevantes. Minimizar commits y notificaciones, **sin ocultar errores ni eliminar alertas de seguridad**.

Las reglas específicas del repositorio y las instrucciones directas del usuario prevalecen si son más estrictas.