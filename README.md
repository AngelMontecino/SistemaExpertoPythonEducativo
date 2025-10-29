# Trabajo Práctico 3: Sistema Experto para Detección de Errores en Python
**Asignatura:** Inteligencia Artificial
**Docente:** Dra. Carola Figueroa-Flores
**Estudiantes:**
* Javier Baeza Toro
* Angel Montecino Flores
* Lucas Varas Navarrete

---

## Descripción del Proyecto

Este repositorio contiene el prototipo funcional de un **Sistema Experto Basado en Reglas**, desarrollado como parte del Trabajo Práctico 3. El objetivo del sistema es diagnosticar errores comunes en código Python, orientado a estudiantes de nivel introductorio.

El proyecto aplica la metodología **CommonKADS** para la adquisición, modelado y representación del conocimiento experto (en este caso, el de un tutor de programación). El sistema es capaz de identificar errores de sintaxis, errores de *runtime* y advertencias de malas prácticas, proveyendo una explicación pedagógica para cada diagnóstico, en lugar de un *traceback* técnico estándar.

## Arquitectura del Sistema

El sistema se ha diseñado bajo una arquitectura modular de tres componentes principales para asegurar la mantenibilidad y la separación del conocimiento y la lógica (Nivel de Artefacto - CommonKADS):

1.  **`main.py` (Interfaz de Usuario)**
    * Es el punto de entrada de la aplicación y gestiona la interfaz de consola (CLI).
    * Es responsable de recolectar el código multilínea del usuario y gestionar los comandos (`analizar`, `salir`).
    * Orquesta la ejecución: invoca al motor de inferencia, decide si el código se puede ejecutar de forma segura y presenta los resultados al usuario.

2.  **`motor_inferencia.py` (Motor de Inferencia)**
    * Contiene la clase `MotorDeInferencia`, que actúa como el núcleo lógico del sistema experto.
    * Carga la Base de Conocimiento desde el archivo JSON al iniciarse.
    * Su método `diagnosticar()` aplica las reglas iterando sobre las condiciones.
    * Implementa las funciones de chequeo (ej. `check_syntax`, `check_name_error`) usando la biblioteca `ast` para análisis estático y `exec` (en un entorno silenciado) para análisis de *runtime*.

3.  **`base_conocimiento.json` (Base de Conocimiento)**
    * Archivo en formato JSON que almacena el conocimiento experto de forma declarativa.
    * Cada regla define un `error_id`, `nombre`, `mensaje` de error, `explicacion` pedagógica y la `condicion` (el nombre del método en el motor que debe invocarse).
    * Esta separación permite que la base de conocimiento sea modificada o expandida por un experto de dominio sin necesidad de alterar el código fuente del motor.
  
    ---

    # Manual de Instalación y Usuario

## Instalación

El prototipo utiliza únicamente bibliotecas estándar de Python 3 (`json`, `ast`, `io`, `contextlib`). Por lo tanto, no requiere la instalación de dependencias externas.

1.  Clone este repositorio en su máquina local utilizando Git:
    ```bash
    git clone [URL_DE_SU_REPOSITORIO]
    ```
2.  Navegue al directorio raíz del proyecto:
    ```bash
    cd [NOMBRE_DEL_DIRECTORIO_DEL_PROYECTO]
    ```

## Instrucciones de Uso

1.  Para iniciar el sistema experto, ejecute el archivo `main.py` desde su terminal:
    ```bash
    python main.py
    ```
2.  El sistema mostrará un mensaje de bienvenida y entrará en modo de entrada de código (indicado por el prompt `>`).
3.  Escriba su código Python línea por línea, presionando Enter después de cada una.
    ```
    > x = 10
    > print(x)
    ```
4.  Cuando haya terminado de ingresar su código, escriba el comando `analizar` en una nueva línea y presione Enter.
    ```
    > analizar
    ```
5.  El sistema procesará el código y presentará dos secciones:
    * **Resultado de la Ejecución:** Si el código no presenta errores de sintaxis, se ejecutará y mostrará su salida (ej. el resultado de un `print`).
    * **Reporte de Diagnóstico:** Mostrará la lista de errores o advertencias encontradas, o un mensaje de felicitaciones si el código está limpio.

6.  Para finalizar el programa en cualquier momento, escriba el comando `salir`.

---

## Ejemplos de Prueba

A continuación, se muestran dos ejemplos de uso para verificar la correcta operación del sistema.

### Ejemplo 1: Código con Error (NameError)

**Entrada de Usuario:**
x = 10 print(variable_indefinida) 
analizar


**Salida Esperada del Sistema:**

--- Analizando tu código... ---

--- Resultado de la Ejecución --- Error durante la ejecución: NameError: name 'variable_indefinida' is not defined --- Fin de la Ejecución ---

Se encontraron los siguientes problemas:

--- Problema #1: Variable no definida (NameError) (ID: E003) --- Mensaje: Parece que estás usando una variable que no existe. Explicación: Un 'NameError' aparece cuando intentas usar una variable...


### Ejemplo 2: Código Correcto (Positivo)

**Entrada de Usuario:**

mi_lista = [10, 20, 30] mi_lista.append(40) print(mi_lista) 
analizar

**Salida Esperada del Sistema:**

--- Analizando tu código... ---

--- Resultado de la Ejecución --- 
[10, 20, 30, 40] 
--- Fin de la Ejecución ---

¡Felicitaciones! No se encontraron errores comunes en tu código.
