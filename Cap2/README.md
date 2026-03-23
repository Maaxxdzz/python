# 2. Uso del Intérprete de Python

Resumen técnico sobre la invocación, ejecución y configuración del intérprete de Python.

## 2.1. Invocar el Intérprete

### Comandos de Inicio
*   **Unix/Linux:** Generalmente `python3.14` (ruta típica: `/usr/local/bin/python3.14`).
*   **Windows:** 
    *   Instalación desde Microsoft Store: `python3.14`.
    *   Con launcher instalado: `py`.
*   **Salir del intérprete:**
    *   **Unix:** `Control-D` o comando `quit()`.
    *   **Windows:** `Control-Z` o comando `quit()`.

### Modos de Ejecución
1.  **Interactivo:** Lee y ejecuta comandos desde el terminal.
2.  **Script:** Lee y ejecuta un archivo pasado como argumento.
3.  **Comando directo:** `python -c comando [arg] ...` (ejecuta una sentencia específica).
4.  **Módulo:** `python -m módulo [arg] ...` (ejecuta el archivo fuente del módulo).
5.  **Script + Interactivo:** `python -i script.py` (ejecuta el script y mantiene la sesión interactiva al finalizar).

> **Nota:** Se recomienda citar el `comando` completamente al usar `-c` debido a espacios o caracteres especiales del shell.

## 2.1.1. Paso de Argumentos (`sys.argv`)

Los argumentos se almacenan en la lista `sys.argv` (módulo `sys`).
*   **`sys.argv[0]`** varía según el método de invocación:
    *   Script normal: Nombre del script.
    *   Sin script/args: Cadena vacía `''`.
    *   Entrada estándar (`-`): `'-'`.
    *   Opción `-c`: `'-c'`.
    *   Opción `-m`: Nombre completo del módulo.
*   Las opciones después de `-c` o `-m` no son consumidas por Python, pero se guardan en `sys.argv` para que las maneje el script/módulo.

## 2.1.2. Modo Interactivo

*   **Prompt Primario:** `>>>` (espera comando).
*   **Prompt Secundario:** `...` (continuación de líneas, ej. dentro de un `if`).
*   **Edición de línea:** Soporta edición, historial y autocompletado (verificar presionando `Flecha Izquierda` o `Control-b`).
*   **Mensaje de bienvenida:** Muestra versión, fecha y licencia antes del primer prompt.

## 2.2. El Intérprete y su Entorno

### 2.2.1. Codificación del Código Fuente

*   **Predeterminado:** **UTF-8**. Permite usar caracteres de casi cualquier idioma en identificadores, literales y comentarios.
*   **Cambiar Codificación:** Se debe declarar explícitamente en el archivo.
    *   **Sintaxis:** `# -*- coding: encoding -*-`
    *   **Ejemplo:** `# -*- coding: cp1252 -*-`

#### Regla de Posición del Declaración de Encoding
1.  **Caso normal:** Debe ser la **primera línea** del archivo.
2.  **Con Shebang:** Si el archivo comienza con `#!/usr/bin/env python3`, la declaración de encoding debe ser la **segunda línea**.

```python
#!/usr/bin/env python3
# -*- coding: cp1252 -*-
# El resto del código...