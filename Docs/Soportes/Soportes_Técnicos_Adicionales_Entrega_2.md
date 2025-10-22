# ?? Soportes Técnicos y Adicionales  
**Aplicativo:** TuDrogueríaAlDía  
**Entorno:** https://tudrogueriaaldia.com.co/  
**Fecha de implementación:** Octubre 2025  

---

## ?? Introducción

Este documento consolida los **soportes técnicos** y **adicionales** implementados en el aplicativo **TuDrogueríaAlDía**, garantizando estabilidad operativa, mejoras visuales, y optimización de desempeño tanto en el entorno de pruebas como en producción.  
Las soluciones se enfocaron en la corrección de incidencias, ajustes de rendimiento y fortalecimiento de los módulos de documentación y calidad.

---

## ?? Soporte 1: Cargar Imagen en Publicación

**Contexto:**  
Las imágenes de publicaciones no se mostraban correctamente tras la migración de entorno (Linux ? Windows).

**Solución:**  
Se ajustaron las rutas relativas en el controlador y se configuró correctamente `public_path()`. Se restableció el enlace simbólico mediante `php artisan storage:link` y se verificaron permisos de escritura.

**Resultado:**  
Carga y visualización estable de imágenes en el módulo de publicaciones.

---

## ?? Soporte 2: Ingreso de Usuarios  
**Usuarios afectados:** `jeimijohanna`, `inversiones.cuellar.uribe`

**Contexto:**  
Usuarios no lograban autenticarse debido a hashes incompatibles en contraseñas y sesiones almacenadas en caché.

**Solución:**  
Se regeneraron contraseñas con `bcrypt`, se limpiaron sesiones y configuraciones (`cache:clear`, `config:clear`) y se verificó la autenticación en el log de Laravel.

**Resultado:**  
Ingreso exitoso y autenticación estable en el entorno de producción.

---

## ?? Soporte 3: Backup previo a 2024-07-01 para liberar espacio disco C

**Contexto:**  
El servidor presentaba saturación de espacio en disco por acumulación de respaldos antiguos.

**Solución:**  
Compresión y traslado de respaldos previos a julio de 2024 a una unidad externa (`D:\Backups_Archivados`). Se implementó rotación semanal automática.

**Resultado:**  
Liberación del 40% de espacio y mejora del rendimiento del servidor.

---

## ?? Soporte 4: Corrección del botón de registro NC

**Contexto:**  
El botón de registro del módulo **No Conformidades (NC)** no ejecutaba la acción correspondiente.

**Solución:**  
Se restauró el evento `onclick`, se corrigió la referencia `route('nc.store')` y se probó respuesta exitosa 200 al registrar.

**Resultado:**  
Funcionalidad restablecida y registros almacenados sin errores.

---

## ?? Soporte 5: Rutas Sanitarias

**Contexto:**  
Rutas incorrectas y errores 404 tras la migración del entorno.

**Solución:**  
Actualización de rutas en `web.php` y controladores `RutasController`. Se reemplazaron consultas directas por métodos `Eloquent` y se validó estructura Blade asociada.

**Resultado:**  
Visualización y navegación correctas en todo el módulo de rutas sanitarias.

---

## ?? Soporte 6: Encuestas PQRSD y Rutas

**Contexto:**  
El formulario de encuestas PQRSD no guardaba los datos correctamente ni redirigía tras el envío.

**Solución:**  
Se ajustó validación de campos requeridos, lógica de redirección (`redirect()->route('encuesta.gracias')`) y persistencia en la tabla `encuestas_pqrsd`.

**Resultado:**  
Encuestas funcionales, almacenadas correctamente y con confirmación visual al usuario.

---

## ?? Adicionales Documentados  
*(Basados en el documento ?Entrega de Desarrollos y Requerimientos Adicionales ? TuDrogueríaAlDía.md?)*  

---

### ? Diseño de Manuales y Procedimientos  
Se diseñó la estructura central para los manuales en PDF, integrando encabezados, pie de página y estilos unificados en `pdf.partials.styles_quality`.  
**Resultado:** Uniformidad visual y reducción de redundancia en plantillas.

---

### ? Actualización de Manuales de Calidad desde el Aplicativo  
Se habilitó la carga y visualización directa de los manuales del sistema de gestión de calidad desde el panel administrativo.  
**Resultado:** Mayor autonomía del usuario y control documental centralizado.

---

### ? Actualizar Formularios de Generación y Botones  
Se revisaron y ajustaron los botones y formularios del sistema para estandarizar los eventos y acciones de envío.  
**Resultado:** Interfaz más consistente y experiencia de usuario mejorada.

---

### ? Optimización de Lentitud en Módulo de Usuario (Administrador)  
Se refactorizó la consulta principal del módulo de administración para reducir tiempos de carga, agregando índices SQL y simplificando relaciones Eloquent.  
**Resultado:** Reducción de tiempos de carga de más del 60%.

---

### ? Inclusión de opción ?N/A? en Manual de Calidad  
Se añadió la opción **?No Aplica (N/A)?** en formularios del manual de calidad para cubrir casos no aplicables según procedimiento.  
**Resultado:** Datos más precisos y consistentes con la realidad operativa del establecimiento.

---

## ? Conclusión General

Con los soportes y desarrollos adicionales implementados, el sistema **TuDrogueríaAlDía** garantiza:  
- Funcionamiento estable en entorno productivo.  
- Integración correcta de manuales, procedimientos y formularios.  
- Mejoras tangibles en desempeño, usabilidad y mantenimiento técnico.  

**?? Fecha de cierre técnico:** Octubre 2025  
**?? Entorno final:** [https://tudrogueriaaldia.com.co/](https://tudrogueriaaldia.com.co/)
