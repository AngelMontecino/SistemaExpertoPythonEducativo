# Sistema Experto para Diagnóstico de Errores en Python

Este proyecto es un **sistema experto** basado en reglas, desarrollado en Python, capaz de analizar fragmentos de código y diagnosticar errores comunes de sintaxis, ejecución y estilo. [cite_start]Utiliza una base de conocimiento en formato JSON para definir las reglas de diagnóstico, lo que lo hace fácilmente extensible[cite: 13, 1].

##  Características

* [cite_start]**Detección de Errores de Sintaxis**: Identifica problemas como `SyntaxError` e `IndentationError` antes de la ejecución[cite: 6, 20, 21, 22, 37, 38].
* [cite_start]**Diagnóstico de Errores en Tiempo de Ejecución**: Detecta errores comunes que ocurren durante la ejecución, como `NameError`, `TypeError`, `IndexError`, `KeyError`, `AttributeError` y `ZeroDivisionError`[cite: 23, 24, 25, 26, 27, 28, 29, 30, 31, 39, 40, 41, 42, 43, 44].
* [cite_start]**Análisis de Buenas Prácticas**: Advierte sobre el uso de prácticas no recomendadas, como el uso de la función `eval()` o de argumentos mutables por defecto en funciones[cite: 32, 33, 34, 35, 45, 46].
* [cite_start]**Motor de Inferencia Separado**: La lógica para evaluar el código (`motor_inferencia.py`) está desacoplada de la base de conocimiento (`base_conocimiento.json`)[cite: 1, 13].
* [cite_start]**Interfaz Interactiva de Consola**: Permite al usuario introducir código multilínea y recibir un análisis detallado[cite: 2, 3, 4].
* [cite_start]**Explicaciones Claras**: Proporciona mensajes y explicaciones sencillas para cada error detectado, ayudando a los programadores principiantes a entender el problema[cite: 11, 12].

##  Tecnologías Utilizadas

* **Python 3.13**: Lenguaje principal de desarrollo.
* [cite_start]**Módulo `ast`**: Para el análisis estático del árbol de sintaxis abstracta del código[cite: 13, 21, 32].
* [cite_start]**Módulo `json`**: Para cargar y gestionar la base de conocimiento[cite: 13, 14].
* [cite_start]**Módulo `io` y `contextlib`**: Para suprimir la salida estándar durante la verificación de errores de ejecución[cite: 13, 23, 24, 25, 26, 27, 28, 29, 30, 31].



##  Manual de Instalación

Para poner en marcha el sistema experto, solo necesitas tener **Python 3** instalado en tu sistema. Sigue estos pasos:

1.  **Descarga los archivos del proyecto**: Asegúrate de tener los tres archivos en la misma carpeta o directorio:
    * `main.py` (Archivo principal de la aplicación)
    * `motor_inferencia.py` (El motor de inferencia)
    * `base_conocimiento.json` (La base de conocimiento con las reglas)

2.  **Abre una terminal o consola**:
    * En **Windows**: Busca "cmd" o "PowerShell".
    * En **macOS** o **Linux**: Abre la aplicación "Terminal".

3.  **Navega a la carpeta del proyecto**: Usa el comando `cd` para moverte al directorio donde guardaste los archivos. Por ejemplo:
    ```sh
    cd ruta/a/tu/proyecto
    ```

4.  **Ejecuta el programa**: Inicia la aplicación con el siguiente comando:
    ```sh
    python main.py
    ```
¡Y listo! El sistema experto estará en ejecución y listo para recibir tu código.

---

##  Manual de Usuario

El programa funciona de manera interactiva. [cite_start]Una vez iniciado, te encontrarás en un modo de entrada donde puedes escribir tu código y comandos[cite: 2].

### Comandos Disponibles

* **Escribir código**: Simplemente escribe tu código Python línea por línea. [cite_start]El programa las irá almacenando[cite: 3].
* `analizar`: Cuando hayas terminado de escribir tu código, escribe la palabra `analizar` en una nueva línea y presiona Enter. [cite_start]El sistema evaluará todo el código que introdujiste[cite: 2, 4].
* [cite_start]`salir`: Para cerrar el programa, escribe `salir` en una nueva línea y presiona Enter[cite: 2, 4].

### ¿Cómo funciona el ciclo?

1.  **Entrada de código**: El programa te pedirá que introduzcas líneas de código con el prompt `> `. [cite_start]Puedes escribir cuantas líneas necesites[cite: 3].
2.  [cite_start]**Análisis**: Cuando escribes `analizar`, el motor de inferencia procesa el código[cite: 6].
    * [cite_start]Primero, busca errores críticos como `SyntaxError` o `IndentationError`[cite: 7].
    * [cite_start]Si no hay errores críticos, intenta ejecutar el código para detectar problemas de runtime[cite: 8, 9, 10].
3.  **Reporte de Diagnóstico**: El sistema te mostrará un informe detallado con los problemas encontrados, incluyendo un nombre, un mensaje y una explicación para cada uno. [cite_start]Si no encuentra errores, ¡te felicitará![cite: 11, 12].
4.  [cite_start]**Nuevo ciclo**: Después del análisis, el programa se reiniciará para que puedas introducir un nuevo fragmento de código[cite: 2].

