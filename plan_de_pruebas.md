# Plan de Pruebas - Prototipo Sistema de Gestión de Taxi

## 📝 Información General

* **Software en Desarrollo:** Prototipo de Sistema de Gestión de Taxi (`prueba.html`)
* **Versión del Prototipo:** 1.0
* **Fecha de Planificación:** 7 de junio de 2025
* **Alcance:** Este plan cubre las funcionalidades básicas del prototipo frontend, incluyendo el inicio de sesión por roles, la gestión de entidades (conductores, vehículos), y el registro y consulta de carreras. Dada la naturaleza del prototipo (sin backend ni persistencia de datos), algunas pruebas de integración y no funcionales son conceptuales o se enfocan en la interacción a nivel de UI/JS en memoria.

---

## 🎯 Objetivos de las Pruebas

* Verificar que el sistema de login funciona correctamente para ambos roles (Administrador y Operador).
* Asegurar que las funcionalidades asociadas a cada rol son accesibles/inaccesibles según lo especificado.
* Confirmar que las operaciones CRUD básicas (Crear, Leer) para Conductores, Vehículos y Carreras funcionan como se espera.
* Validar que la funcionalidad de consulta y filtrado de carreras opera correctamente.
* Identificar posibles errores o inconsistencias en la interfaz de usuario y la lógica frontend.

---

## 🔑 Roles de Usuario Considerados

Para las pruebas se utilizarán los siguientes roles y credenciales:

* **Administrador:**
    * Usuario: `admin1`
    * Contraseña: `adminpassword`
    * Acceso esperado: Completo.
* **Operador:**
    * Usuario: `operador1`
    * Contraseña: `password1`
    * Acceso esperado: Limitado a registrar, consultar carreras y ver reportes.

---

## 🧪 Casos de Prueba Detallados

A continuación se presentan los casos de prueba planificados, organizados por tipo y funcionalidad.

### 1. Pruebas Funcionales (Caja Negra / Aceptación)

#### **Caso de Prueba 1.1: Login de Administrador - Flujo Exitoso**

* **Tipo de Prueba:** Funcional, Caja Negra, Aceptación.
* **Objetivo:** Verificar que el usuario "admin1" con la contraseña "adminpassword" puede iniciar sesión exitosamente y acceder a todas las funcionalidades de administrador.
* **Precondiciones:** La página `prueba.html` está cargada en el navegador. No hay sesión iniciada previamente.
* **Pasos a Seguir:**
    1.  Abrir `prueba.html` en el navegador.
    2.  En el campo "Usuario", ingresar `admin1`.
    3.  En el campo "Contraseña", ingresar `adminpassword`.
    4.  Hacer clic en el botón "Iniciar Sesión".
* **Resultados Esperados:**
    * Se muestra un mensaje de bienvenida (ej. "¡Bienvenido, admin1! (administrador)").
    * La pantalla de login (`login-screen`) se oculta.
    * La pantalla del sistema (`system-screen`) se vuelve visible.
    * Todos los botones de navegación (`Gestionar Conductores`, `Gestionar Vehículos`, `Registrar Carrera`, `Consultar Carreras`, `Reportes`) son visibles y funcionales.
    * La sección por defecto mostrada es `Gestionar Conductores`.

#### **Caso de Prueba 1.2: Login de Operador - Flujo Exitoso**

* **Tipo de Prueba:** Funcional, Caja Negra, Aceptación.
* **Objetivo:** Verificar que el usuario "operador1" con la contraseña "password1" puede iniciar sesión exitosamente y acceder solo a las funcionalidades permitidas para un operador.
* **Precondiciones:** La página `prueba.html` está cargada en el navegador. No hay sesión iniciada previamente.
* **Pasos a Seguir:**
    1.  Abrir `prueba.html` en el navegador.
    2.  En el campo "Usuario", ingresar `operador1`.
    3.  En el campo "Contraseña", ingresar `password1`.
    4.  Hacer clic en el botón "Iniciar Sesión".
* **Resultados Esperados:**
    * Se muestra un mensaje de bienvenida (ej. "¡Bienvenido, operador1! (operador)").
    * La pantalla de login (`login-screen`) se oculta.
    * La pantalla del sistema (`system-screen`) se vuelve visible.
    * Los botones de navegación `Gestionar Conductores` y `Gestionar Vehículos` **no son visibles**.
    * Los botones `Registrar Carrera`, `Consultar Carreras` y `Reportes` son visibles y funcionales.
    * La sección por defecto mostrada es `Registrar Carrera`.

#### **Caso de Prueba 1.3: Login - Credenciales Incorrectas**

* **Tipo de Prueba:** Funcional, Caja Negra.
* **Objetivo:** Verificar que el sistema rechaza los intentos de inicio de sesión con credenciales incorrectas.
* **Precondiciones:** La página `prueba.html` está cargada en el navegador.
* **Pasos a Seguir:**
    1.  Abrir `prueba.html` en el navegador.
    2.  En el campo "Usuario", ingresar `usuario_invalido`.
    3.  En el campo "Contraseña", ingresar `contraseña_incorrecta`.
    4.  Hacer clic en el botón "Iniciar Sesión".
* **Resultados Esperados:**
    * Se muestra el mensaje "Usuario o contraseña incorrectos." en el área de mensajes.
    * La pantalla de login (`login-screen`) permanece visible.
    * La pantalla del sistema (`system-screen`) permanece oculta.

#### **Caso de Prueba 1.4: Añadir Conductor - Flujo Exitoso**

* **Tipo de Prueba:** Funcional, Caja Negra, Integración (con la tabla de conductores).
* **Objetivo:** Verificar que se puede añadir un nuevo conductor y que aparece correctamente en la tabla de conductores.
* **Precondiciones:** Sesión iniciada como `admin1`. La sección `Gestionar Conductores` está visible.
* **Pasos a Seguir:**
    1.  Navegar a la sección `Gestionar Conductores`.
    2.  En el formulario "Añadir Nuevo Conductor":
        * Ingresar `Juan Pérez` en "Nombre".
        * Ingresar `L-12345` en "Licencia".
        * Ingresar `1234567890` en "Teléfono".
    3.  Hacer clic en el botón "Añadir Conductor".
* **Resultados Esperados:**
    * Se muestra un mensaje de éxito (ej. "Conductor añadido exitosamente.").
    * Los campos del formulario se borran.
    * La tabla de "Conductores Actuales" (`driverTableBody`) muestra una nueva fila con los datos `Juan Pérez`, `L-12345`, `1234567890`.

#### **Caso de Prueba 1.5: Registro de Carrera - Flujo Exitoso**

* **Tipo de Prueba:** Funcional, Caja Negra, Integración (con conductores y vehículos).
* **Objetivo:** Verificar que se puede registrar una nueva carrera seleccionando un conductor y un vehículo existentes, y que la carrera se guarda internamente.
* **Precondiciones:** Sesión iniciada (como `admin1` o `operador1`). Al menos un conductor y un vehículo han sido añadidos previamente. La sección `Registrar Carrera` está visible.
* **Pasos a Seguir:**
    1.  Añadir un conductor: `Driver Test`, `L-999`, `1111111111` (si no hay ninguno, como `admin1`).
    2.  Añadir un vehículo: `Toyota`, `Corolla`, `2020`, `ABC-123`, `Driver Test` (si no hay ninguno, como `admin1`).
    3.  Navegar a la sección `Registrar Carrera`.
    4.  En el formulario "Registrar Nueva Carrera":
        * Seleccionar `Driver Test` en "Conductor".
        * Seleccionar `Toyota Corolla (ABC-123)` en "Vehículo".
        * Ingresar `Calle A, Casa 1` en "Origen".
        * Ingresar `Calle B, Edificio X` en "Destino".
        * Ingresar `15.50` en "Costo".
        * Ingresar la fecha actual (ej. `2025-06-07`) en "Fecha".
    5.  Hacer clic en el botón "Registrar Carrera".
* **Resultados Esperados:**
    * Se muestra un mensaje de éxito (ej. "Carrera registrada exitosamente.").
    * Los campos del formulario se borran.
    * La carrera se añade al array `carreras` en JavaScript (verificable en la Prueba 1.6).

#### **Caso de Prueba 1.6: Consulta de Carreras - Filtrado por Conductor**

* **Tipo de Prueba:** Funcional, Caja Negra.
* **Objetivo:** Verificar que la consulta de carreras filtra correctamente por el conductor seleccionado.
* **Precondiciones:** Sesión iniciada. Varias carreras registradas, incluyendo al menos dos con el mismo conductor y una con un conductor diferente.
* **Pasos a Seguir:**
    1.  Registrar al menos 3 carreras:
        * Carrera 1: Conductor `Driver Test`, Origen `A`, Destino `B`
        * Carrera 2: Conductor `Driver Test`, Origen `C`, Destino `D`
        * Carrera 3: Conductor `Otro Driver`, Origen `E`, Destino `F`
    2.  Navegar a la sección `Consultar Carreras`.
    3.  En el formulario de consulta:
        * Seleccionar `Driver Test` en el campo "Conductor".
        * Dejar los otros campos de filtro vacíos.
    4.  Hacer clic en el botón "Consultar Carreras".
* **Resultados Esperados:**
    * La tabla de "Resultados de la Consulta" solo muestra las filas correspondientes a la `Carrera 1` y `Carrera 2`.
    * La `Carrera 3` no aparece en la tabla.

#### **Caso de Prueba 1.7: Validación de Formulario - Campos Obligatorios**

* **Tipo de Prueba:** Funcional, Caja Negra.
* **Objetivo:** Verificar que los formularios validan la presencia de campos obligatorios antes de procesar la entrada.
* **Precondiciones:** Sesión iniciada.
* **Pasos a Seguir (Ejemplo con "Añadir Conductor"):**
    1.  Navegar a la sección `Gestionar Conductores` (como `admin1`).
    2.  Dejar todos los campos del formulario "Añadir Nuevo Conductor" vacíos (o solo llenar algunos).
    3.  Hacer clic en el botón "Añadir Conductor".
* **Resultados Esperados:**
    * El navegador muestra un mensaje de error o una indicación visual (ej. borde rojo) señalando los campos obligatorios vacíos (comportamiento por defecto del atributo `required` en HTML5).
    * No se muestra un mensaje de éxito.
    * El conductor no se añade a la tabla.

### 2. Pruebas Unitarias (Conceptuales / Caja Blanca)

#### **Caso de Prueba 2.1: Filtrado de Carreras (Función `filtrarCarreras`)**

* **Tipo de Prueba:** Unitaria, Caja Blanca.
* **Objetivo:** Verificar el correcto funcionamiento de la función `filtrarCarreras()` de forma aislada, asegurando que devuelve el subconjunto de carreras correcto para diferentes criterios de filtro.
* **Precondiciones:** Acceso al código fuente de `prueba.html`. Entorno de desarrollo con posibilidad de ejecutar JavaScript directamente (ej. consola del navegador).
* **Pasos a Seguir (Conceptual):**
    1.  Simular un array `carreras` con datos de prueba variados (ej. con diferentes conductores, vehículos, fechas).
    2.  Llamar a `filtrarCarreras()` con diferentes combinaciones de parámetros de filtro (solo conductor, solo vehículo, solo fecha, combinaciones, todos vacíos).
    3.  Inspeccionar el valor de retorno de la función.
* **Resultados Esperados:**
    * Cuando se filtra por un conductor específico, el array retornado solo contiene carreras de ese conductor.
    * Cuando se filtra por múltiples criterios, el array retornado solo contiene carreras que cumplen todos los criterios.
    * Si los filtros están vacíos, la función retorna todas las carreras.

### 3. Pruebas de Integración

#### **Caso de Prueba 3.1: Interacción Formulario -> Lógica -> Visualización**

* **Tipo de Prueba:** Integración.
* **Objetivo:** Verificar la interacción completa desde la entrada de datos en un formulario, el procesamiento por la lógica JavaScript interna, y la correcta visualización de esos datos en otra sección de la UI.
* **Precondiciones:** Sesión iniciada como `admin1`.
* **Pasos a Seguir:**
    1.  Navegar a la sección `Registrar Carrera`.
    2.  Registrar una nueva carrera con datos únicos (ej. Conductor: `INTEGRACION_DRV`, Vehículo: `INT-VEH-1`, Origen: `X`, Destino: `Y`, Costo: `50.00`, Fecha: `2025-06-07`).
    3.  Navegar a la sección `Consultar Carreras`.
    4.  En el formulario de consulta, filtrar por el conductor `INTEGRACION_DRV`.
    5.  Hacer clic en "Consultar Carreras".
* **Resultados Esperados:**
    * La carrera registrada en el paso 2 aparece en la tabla de resultados de la consulta. Esto confirma que la cadena de interacción (entrada -> procesamiento -> visualización) funciona correctamente.

### 4. Pruebas de Regresión

#### **Caso de Prueba 4.1: Regresión de Login y Visibilidad de Roles**

* **Tipo de Prueba:** Regresión.
* **Objetivo:** Después de cualquier modificación o mejora en el código (ej. adición de nuevas funcionalidades, refactorización), verificar que las funcionalidades de login y la diferenciación de visibilidad por roles no se han roto.
* **Precondiciones:** Se ha realizado algún cambio en el código fuente de `prueba.html`.
* **Pasos a Seguir:**
    1.  Ejecutar el `Caso de Prueba 1.1: Login de Administrador - Flujo Exitoso`.
    2.  Ejecutar el `Caso de Prueba 1.2: Login de Operador - Flujo Exitoso`.
    3.  Ejecutar el `Caso de Prueba 1.3: Login - Credenciales Incorrectas`.
* **Resultados Esperados:**
    * Todos los resultados esperados de los casos de prueba 1.1, 1.2 y 1.3 se cumplen.
    * La implementación de los roles y la lógica de ocultamiento/mostrado de secciones funciona correctamente para ambos tipos de usuario.

---

## 📈 Consideraciones para Futuras Pruebas (No Funcionales)

Dada la naturaleza del prototipo frontend en memoria, las pruebas no funcionales como las de rendimiento, seguridad de datos o escalabilidad requerirían un backend y/o una base de datos real. Sin embargo, conceptualmente, se podría considerar:

* **Pruebas de Rendimiento (Básicas):** Medir el tiempo de carga de la página o el tiempo que tarda en renderizar tablas con un gran número de elementos (simulados).
* **Pruebas de Seguridad (Básicas):** Intentos de inyección XSS en campos de texto (aunque el prototipo no envía datos a un servidor). Verificar la solidez de las credenciales de prueba.
* **Pruebas de Usabilidad:** Evaluar la facilidad de uso de la interfaz, la claridad de los mensajes y la intuición del flujo de trabajo.

---
