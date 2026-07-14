## 📘 REQUERIMIENTOS-FUNCIONALES.md  

### 1. Identificación y trazabilidad  
Cada requisito funcional se etiqueta con un ID único (FR‑XXX) para asegurar trazabilidad en casos de uso, criterios de aceptación y validaciones.  

### 2. Lista de Requerimientos Funcionales  

- **FR‑001: Búsqueda de hoteles**  
  - El sistema debe permitir buscar hoteles por ciudad, fechas y número de huéspedes.  
  - Debe mostrar resultados ordenados por relevancia y disponibilidad.  

- **FR‑002: Visualización de disponibilidad**  
  - El sistema debe mostrar disponibilidad en tiempo real.  
  - En caso de fallo de DB, debe ofrecer datos en caché hasta 10 minutos.  

- **FR‑003: Reserva de habitaciones**  
  - El sistema debe permitir reservar habitaciones seleccionadas.  
  - Validación de disponibilidad concurrente (transacciones serializables).  

- **FR‑004: Cancelación de reservas**  
  - El sistema debe permitir cancelar reservas según política de anticipación.  
  - Debe calcular penalización automática si corresponde.  

- **FR‑005: Modificación de reservas**  
  - El sistema debe permitir modificar fechas y huéspedes de una reserva existente.  
  - Debe recalcular disponibilidad y precio.  

- **FR‑006: Procesamiento de pagos**  
  - El sistema debe integrar pasarela de pago primaria y secundaria.  
  - En caso de fallo, debe reintentar hasta 3 veces y marcar orden como `PENDING_PAYMENT`.  

- **FR‑007: Notificaciones y confirmaciones**  
  - El sistema debe enviar email de confirmación al usuario.  
  - En caso de fallo del servicio de email, debe reintentar cada 5 minutos durante 1 hora.  

- **FR‑008: Gestión de usuarios**  
  - El sistema debe permitir registro, login y autenticación segura (JWT).  
  - Debe ofrecer recuperación de contraseña vía email.  

- **FR‑009: Panel de administración**  
  - El sistema debe permitir a administradores visualizar reservas, disponibilidad y métricas.  
  - Debe incluir alertas cuando el error rate supere el 2 %.  

- **FR‑010: Reportes de negocio**  
  - El sistema debe generar reportes de ocupación, ingresos y cancelaciones.  
  - Exportables en formatos estándar (CSV, PDF).  
