## 📘 SLA-Y-METRICAS-OPERATIVAS.md  

### 1. Principios  
- Los SLA garantizan niveles mínimos de servicio para usuarios y administradores.  
- Las métricas permiten validar cumplimiento y activar alertas en tiempo real.  
- Se definen umbrales claros para cada módulo crítico.  

### 2. SLA por módulo  

- **Search (búsqueda de hoteles)**  
  - Latencia: p95 < 500 ms  
  - Error rate: < 0.5 %  
  - Disponibilidad: 99.9 % mensual  

- **Reservation (reservas)**  
  - Latencia: p95 < 3 s  
  - Error rate: < 1 %  
  - Consistencia: transacciones serializables  

- **Payment (pagos)**  
  - Éxito: > 99.9 %  
  - Latencia: < 5 s  
  - Retry automático: hasta 3 intentos  

- **Email (notificaciones)**  
  - Entrega: > 99 % en ≤ 60 min  
  - Retry: cada 5 min durante 1 h  

- **Failover regional**  
  - Tiempo de recuperación: ≤ 15 min  
  - Disponibilidad global: 99.9 %  

### 3. Métricas de observabilidad  

- **RED metrics**:  
  - Rate: número de solicitudes por segundo.  
  - Errors: porcentaje de fallos por endpoint.  
  - Duration: latencia p95/p99.  

- **KPIs de negocio**:  
  - Tasa de ocupación hotelera.  
  - Ingresos por reservas confirmadas.  
  - Ratio de cancelaciones vs reservas.  

### 4. Alertas críticas  

- Error rate > 2 % → alerta P1.  
- Latencia p95 > 1 s en búsqueda → alerta P2.  
- Fallo de gateway de pago → alerta inmediata P1.  
- Failover no completado en 15 min → alerta P0.  
