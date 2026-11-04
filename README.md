# RIOCLAROOK
COMO SE HIZO EL PROYECTO DE RIO CLARO
# Documentación Técnica y Manual de Despliegue: Río Claro IA

**Autora:** Miriam Viveros
**Proyecto:** Causas por la Transformación - Certificación AI-901 (Microsoft Azure AI Fundamentals)
**Plataforma de Despliegue:** Microsoft Azure App Service (Plan F1 - Gratuito)

---

## 1. Resumen Ejecutivo
El presente documento detalla la arquitectura, el desarrollo y el proceso de despliegue del prototipo **Río Claro IA**, una aplicación web interactiva diseñada para resolver la problemática de dispersión de datos en una empresa distribuidora ficticia. El proyecto se ha desarrollado bajo un estricto control presupuestario (Costo Cero), utilizando herramientas de vanguardia como Bootstrap 5 para el diseño y Microsoft Azure para el alojamiento en la nube.

## 2. Justificación y Planteamiento del Problema
La Distribuidora Río Claro, con 22 años de trayectoria, enfrenta un problema crítico: **la falta de una estructura de datos unificada**. La información vital (facturas, inventario, políticas) se encuentra dispersa en correos personales, hojas de cálculo aisladas y fotografías. Esto genera:
*   **Pérdidas financieras:** Pagos duplicados de facturas por falta de un registro centralizado.
*   **Ineficiencia operativa:** Más de 12 horas semanales dedicadas a la captura manual de datos.
*   **Mala experiencia del cliente:** Respuestas lentas o inexistentes a consultas de pedidos.

La solución **Río Claro IA** centraliza estas operaciones en un panel web accesible desde cualquier dispositivo, demostrando cómo la tecnología puede transformar datos dispersos en activos estratégicos.

## 3. Arquitectura de la Solución
El sistema se diseñó bajo una arquitectura moderna, priorizando el rendimiento y el costo cero:

*   **Frontend (Capa de Presentación):** Desarrollado con **HTML5**, **CSS3** y **JavaScript (Vanilla)**. Se utilizó el framework **Bootstrap 5** para garantizar un diseño *Responsive* (adaptable a móviles y computadoras).
*   **Interfaz de Usuario (UI):** Implementación de un tema oscuro (Dark Mode) con efectos *Glassmorphism* (cristal), acentos en cian neón y tipografía tecnológica (Orbitron), buscando una estética de "centro de operaciones futurista".
*   **Backend / Alojamiento:** **Microsoft Azure App Service**. Se seleccionó el plan **F1 (Free)** para el despliegue, garantizando un costo de operación de $0.00 MXN.
*   **Seguridad:** Implementación de un sistema de Login visual para restringir el acceso (Usuario: `admin`, Contraseña: `123`).

## 4. Módulos del Sistema
La aplicación se divide en cinco módulos accesibles a través de pestañas dinámicas:

1.  **Resumen (Dashboard):** Panel de control con indicadores clave (KPIs) como el número de sucursales activas, el ahorro semanal estimado y alertas de facturas en revisión.
2.  **Asistente IA:** Una interfaz de chat interactiva. (En su versión actual, funciona mediante reglas lógicas en JavaScript para simular la inteligencia).
3.  **Facturas:** Módulo transaccional que permite registrar proveedores y montos. Incluye un algoritmo de validación que detecta y bloquea folios duplicados, enviándolos a revisión humana.
4.  **Inventario:** Tabla consolidada que normaliza los nombres de los productos (ej. unificando "Cloro 1L" y "Blanqueador 1000ml") y permite filtrar existencias por sucursal.
5.  **IA Responsable:** Sección dedicada a documentar los principios éticos aplicados.

---

## 5. Principios de IA Responsable Aplicados
Un pilar fundamental de la certificación AI-901 es el desarrollo ético. El sistema implementa las siguientes directrices:

*   **Equidad:** Los algoritmos de consulta y visualización de inventario tratan por igual a todas las sucursales de la empresa (Guadalajara, Zapopan, León, etc.), sin favorecer ninguna región.
*   **Confiabilidad y Seguridad:** El asistente virtual está programado para admitir su ignorancia si no encuentra una respuesta en su base de datos (evitando "alucinaciones" o invención de datos). Además, el módulo de facturas bloquea transacciones dudosas.
*   **Privacidad y Protección de Datos:** El prototipo opera exclusivamente con **datos ficticios**. No contiene información de clientes reales, nóminas ni credenciales sensibles.
*   **Transparencia:** El sistema muestra advertencias claras indicando que se trata de un "Modo de Demostración" y explica al usuario de dónde proviene la información mostrada.
*   **Rendición de Cuentas (Human-in-the-loop):** La IA nunca toma decisiones financieras autónomas. Si una factura parece duplicada, el sistema notifica y *exige* la validación de un humano (Laura, cuentas por pagar) antes de proceder al pago.

---

## 6. Manual de Despliegue en Azure (Costo Cero)

A continuación, se detalla el procedimiento técnico para publicar esta aplicación en internet usando la suscripción educativa, sin generar cargos.

### Fase 1: Creación del Recurso en Azure
1.  Iniciar sesión en el [Portal de Azure](https://portal.azure.com).
2.  En la barra de búsqueda, escribir **"App Services"** y seleccionar **"+ Crear"** > **"Aplicación web"**.
3.  Completar la pestaña **"Datos básicos"**:
    *   **Suscripción:** Azure for Students.
    *   **Grupo de recursos:** Crear uno nuevo (ej. `rg-rio-claro-ia`).
    *   **Nombre:** Un nombre único (ej. `rio-claro-ia-miriam`).
    *   **Publicar:** Código.
    *   **Pila en tiempo de ejecución:** .NET 8 (LTS).
    *   **Sistema operativo:** Windows.
    *   **Región:** Seleccionar una región permitida (ej. `West US 3`).
    *   **Plan de App Service:** Crear nuevo y seleccionar el **Plan de precios "Free F1"**.
4.  Hacer clic en **"Revisar y crear"**. Verificar que la SKU diga **"Gratis"** y el precio estimado sea **$0.00**. Hacer clic en **"Crear"**.

### Fase 2: Configuración de Seguridad y Costos (Crítico)
Para evitar cobros automáticos por parte de Azure:
1.  Ir al recurso recién creado.
2.  En el menú lateral, ir a **Configuración** > **Configuración general**.
3.  Localizar **"Siempre activado" (Always On)** y asegurarse de que esté **Desmarcada**. *(El plan F1 no lo soporta y Azure podría cobrar por escalar el plan).*
4.  Hacer clic en **Guardar**.

### Fase 3: Carga de Archivos (Método Kudu)
1.  En el menú lateral del App Service, ir a **Herramientas de desarrollo** > **Herramientas avanzadas** y hacer clic en **"Ir"**.
2.  En la nueva pestaña (Kudu), ir a **Debug console** > **CMD**.
3.  En la consola negra, navegar a la carpeta pública:
    ```cmd
    cd site\wwwroot
