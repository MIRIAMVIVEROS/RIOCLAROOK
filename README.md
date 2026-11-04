# RIOCLAROOK
COMO SE HIZO EL PROYECTO DE RIO CLARO
# Manual de Despliegue: Aplicación Web en Azure (Costo Cero)

**Autora:** Miriam Viveros
**Proyecto:** Río Claro IA - Prototipo de Inteligencia Artificial
**Plataforma:** Microsoft Azure (App Service)

## 1. Objetivo del Proyecto
El presente documento detalla el procedimiento técnico paso a paso para desplegar una aplicación web interactiva (HTML, CSS, JavaScript) en la nube de Microsoft Azure, garantizando un costo de operación de **$0 (Cero pesos)**, utilizando la suscripción *Azure for Students* y el plan de hospedaje **F1 (Free)**.

## 2. Arquitectura de la Solución
*   **Frontend:** Interfaz de usuario construida con HTML5, CSS3 (Bootstrap 5) y JavaScript nativo.
*   **Backend / Alojamiento:** Azure App Service en sistema operativo Windows.
*   **Costo:** Plan de App Service F1 (Gratuito, con límites de CPU y ancho de banda diarios).
*   **Despliegue:** Transferencia de archivos mediante la consola Kudu y el Editor de App Service.

---

## 3. Procedimiento Paso a Paso

### Fase 1: Creación del Recurso en Azure
1.  Iniciar sesión en el [Portal de Azure](https://portal.azure.com).
2.  En la barra de búsqueda, escribir **"App Services"** y seleccionar **"+ Crear"** > **"Aplicación web"**.
3.  Completar la pestaña **"Datos básicos"**:
    *   **Suscripción:** Azure for Students.
    *   **Grupo de recursos:** Crear uno nuevo (ej. `rg-rio-claro-ia`).
    *   **Nombre:** Un nombre único a nivel global (ej. `rio-claro-ia-miriam`).
    *   **Publicar:** Código.
    *   **Pila en tiempo de ejecución:** .NET 8 (LTS) o cualquier opción (se sobrescribirá con el HTML).
    *   **Sistema operativo:** Windows.
    *   **Región:** Seleccionar una región permitida para cuentas educativas (ej. `West US 3`).
    *   **Plan de App Service:** Crear nuevo y seleccionar el **Plan de precios "Free F1"**.
4.  Hacer clic en **"Revisar y crear"**. Verificar que la SKU diga **"Gratis"** y el precio estimado sea **$0.00**. Hacer clic en **"Crear"**.

### Fase 2: Configuración de Seguridad y Costos
Una vez desplegado el recurso, es obligatorio blindar la configuración para evitar cobros automáticos por parte de Azure.

1.  Hacer clic en **"Ir al recurso"**.
2.  En el menú lateral izquierdo, ir a **Configuración** > **Configuración general**.
3.  Localizar la opción **"Siempre activado" (Always On)** y asegurarse de que esté **Desmarcada (Desactivada)**. 
    *   *Nota técnica: El plan F1 no soporta esta función; si se activa, Azure podría intentar cobrar por escalar el plan.*
4.  Hacer clic en **Guardar**.

### Fase 3: Carga de Archivos mediante Kudu
Azure Kudu es el motor de despliegue detrás de App Service. Se utilizará su consola para inyectar el código.

1.  En el menú lateral del App Service, ir a **Herramientas de desarrollo** > **Herramientas avanzadas** y hacer clic en **"Ir"**.
2.  En la nueva pestaña (Kudu), ir a la barra superior, hacer clic en **"Debug console"** y seleccionar **"CMD"**.
3.  En la consola negra, navegar a la carpeta pública con el comando:
    ```cmd
    cd site\wwwroot
