# Sistema de Gestión de Taxi - Prototipo Frontend

![GitHub repo size](https://img.shields.io/github/repo-size/TU_USUARIO_GITHUB/NOMBRE_DEL_REPOSITORIO?style=flat-square)
![GitHub last commit](https://img.shields.io/github/last-commit/TU_USUARIO_GITHUB/NOMBRE_DEL_REPOSITORIO?style=flat-square)
![GitHub top language](https://img.shields.io/github/languages/top/TU_USUARIO_GITHUB/NOMBRE_DEL_REPOSITORIO?style=flat-square)

---

## 📝 Descripción del Proyecto

Este repositorio contiene un prototipo de un **Sistema de Gestión de Taxi**, desarrollado enteramente en el lado del cliente (frontend) utilizando **HTML, CSS (Tailwind CSS) y JavaScript**. El objetivo principal de este prototipo es simular las operaciones básicas de una oficina de taxis, incluyendo la gestión de conductores, vehículos, el registro y consulta de carreras, y la generación de reportes (con funcionalidades de reporte como *placeholders*).

El sistema ha sido diseñado para demostrar la implementación de roles de usuario (`Administrador` y `Operador`) y cómo se diferencia el acceso a las funcionalidades según el rol del usuario logueado.

**Nota Importante:** Este es un **prototipo educativo**. Los datos se almacenan en memoria del navegador y no persisten al recargar la página. No incluye un backend real ni integración con bases de datos.

---

## 🛠️ Tecnologías Utilizadas

* **HTML5:** Estructura de la página web.
* **CSS3:** Estilos personalizados.
* **Tailwind CSS:** Framework CSS de utilidad para un diseño rápido y responsivo.
* **JavaScript (Vainilla JS):** Lógica del lado del cliente para la interactividad, gestión de datos en memoria y control de flujo de la aplicación.
* **Google Fonts:** Para la fuente 'Roboto'.

---

## ✨ Funcionalidades Principales

El prototipo ofrece las siguientes secciones y operaciones:

1.  **Login de Usuarios:**
    * Autenticación de usuarios por roles.
    * Mensajes de éxito/error en el inicio de sesión.
2.  **Gestión de Conductores:**
    * Añadir nuevos conductores (Nombre, **Licencia**, Teléfono).
    * Visualizar la lista de conductores actuales en una tabla.
3.  **Gestión de Vehículos:**
    * Añadir nuevos vehículos (Marca, Modelo, Año, **Placa**, Conductor Asignado).
    * Visualizar la lista de vehículos actuales en una tabla.
4.  **Registro de Carreras:**
    * Registrar nuevas carreras con detalles como Conductor, Vehículo, Origen, Destino, Costo y Fecha.
    * Selección de conductor y vehículo de listas existentes.
5.  **Consulta de Carreras:**
    * Filtrar carreras por Conductor, Vehículo o Fecha.
    * Visualizar los resultados de la consulta en una tabla.
6.  **Reportes:**
    * Sección dedicada a la generación de reportes (funcionalidad base implementada, pero la lógica de generación de reportes avanzados como PDF o impresión es un *placeholder*).

---

## 🔑 Roles de Usuario

El sistema incorpora dos roles principales con diferentes niveles de acceso:

### **1. Administrador**
* **Usuario:** `admin1`
* **Contraseña:** `adminpassword`
* **Acceso:** Completo a todas las funcionalidades del sistema: Gestión de Conductores, Gestión de Vehículos, Registro de Carreras, Consulta de Carreras, y Reportes.

### **2. Operador**
* **Usuario:** `operador1`
* **Contraseña:** `password1`
* **Acceso:** Limitado a las operaciones diarias: Registro de Carreras, Consulta de Carreras, y Reportes. Las secciones de Gestión de Conductores y Gestión de Vehículos están ocultas para este rol.

---

## 🚀 Cómo Ejecutar el Prototipo

1.  **Clonar el Repositorio:**
    ```bash
    git clone [https://github.com/TU_USUARIO_GITHUB/gestion-serviciostaxi-pruebas.git](https://github.com/TU_USUARIO_GITHUB/NOMBRE_DEL_REPOSITORIO.git)
    ```
2.  **Navegar al Directorio del Proyecto:**
    ```bash
    cd NOMBRE_DEL_REPOSITORIO
    ```
3.  **Abrir el Archivo:**
    Simplemente abre el archivo `prueba.html` en tu navegador web preferido (Google Chrome, Firefox, Edge, etc.). No se requiere un servidor web para este prototipo.

---

## 📊 Planificación de Pruebas

Como parte del desarrollo de este prototipo, se ha elaborado un plan de pruebas para verificar su funcionalidad, integración y usabilidad. Este plan se basa en las técnicas de pruebas de software aprendidas, incluyendo pruebas unitarias (conceptuales), de integración, funcionales (caja negra y blanca), de aceptación y de regresión.

**Puedes encontrar el detalle del plan de pruebas en el archivo `PLAN_DE_PRUEBAS.md` incluido en este repositorio.**

---

## 📹 Video de Demostración

Se ha creado un video de demostración para ilustrar el funcionamiento del prototipo y la ejecución de algunas de las pruebas planificadas, destacando la diferenciación de roles.

**[https://youtu.be/g_sdnV5mHtM]**
*(Reemplaza este texto con el enlace real a tu video una vez lo hayas subido a YouTube, Google Drive u otra plataforma.)*

---

## 🤝 Contribuciones

Este es un proyecto de prototipo para fines educativos. Las contribuciones no están activamente solicitadas, pero si tienes sugerencias o mejoras, no dudes en abrir un *issue* o *pull request*.

---

## 📄 Licencia

Este proyecto se distribuye bajo la licencia [MIT License](https://opensource.org/licenses/MIT) (o la que prefieras).

---

**Autor:** [LENNY GARCIA]
**Universidad:** [UPT]
**Asignatura:** [ING.DEL SOFTWARE]
