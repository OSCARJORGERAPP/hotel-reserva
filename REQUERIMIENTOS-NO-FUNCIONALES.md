## 📘 REQUERIMIENTOS-NO-FUNCIONALES.md  

### 1. Identificación y trazabilidad  
Cada requisito no funcional se etiqueta con un ID único (NFR‑XXX) para asegurar trazabilidad en métricas, validaciones y SLA.  

### 2. Lista de Requerimientos No Funcionales  

- **NFR‑001: Rendimiento**  
  - El sistema debe responder a búsquedas en < 500 ms (p95).  
  - Reservas deben completarse en < 3 s (p95).  
  - Error rate global < 0.5 %.  

- **NFR‑002: Disponibilidad**  
  - El sistema debe garantizar 99.9 % de uptime mensual.  
  - Failover automático a región secundaria en < 15 min.  

- **NFR‑003: Escalabilidad**  
  - El sistema debe soportar hasta 10 000 reservas concurrentes.  
  - Debe escalar horizontalmente mediante balanceadores y réplicas de DB.  

- **NFR‑004: Seguridad**  
  - Todo tráfico debe estar cifrado con TLS 1.3.  
  - Autenticación mediante JWT con expiración configurable.  
  - Cumplimiento con GDPR y PCI DSS.  

- **NFR‑005: Observabilidad**  
  - Monitoreo RED (Rate, Errors, Duration) + KPIs de negocio.  
  - Alertas críticas: error rate > 2 % → P1.  
  - Logs centralizados con trazabilidad de transacciones.  

- **NFR‑006: Mantenibilidad**  
  - Código documentado con estándares de estilo.  
  - Tests unitarios con cobertura mínima del 80 %.  
  - ADRs para decisiones arquitectónicas mayores.  

- **NFR‑007: Usabilidad**  
  - Interfaz clara y accesible (WCAG 2.1 AA).  
  - Flujo de reserva en ≤ 3 pasos.  
  - Mensajes de error comprensibles y con opción de reintento.  

- **NFR‑008: Portabilidad**  
  - Frontend compatible con navegadores modernos (Chrome, Edge, Firefox, Safari).  
  - App móvil disponible en iOS y Android.  
