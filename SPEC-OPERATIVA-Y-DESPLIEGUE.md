## 📘 SPEC-OPERATIVA-Y-DESPLIEGUE.md  

### 1. Principios  
- La operación del sistema debe ser **segura, observable y resiliente**.  
- Todo despliegue se realiza con **canary release** y monitoreo continuo.  
- Se definen protocolos claros de **alerta y recuperación**.  

### 2. Flujo de despliegue  
- **Canary deploy progresivo**:  
  - 5 % de usuarios → validación inicial.  
  - 25 % de usuarios → monitoreo extendido.  
  - 100 % de usuarios → despliegue completo.  
- **Rollback automático** si error rate > 2 % o latencia p95 > 1 s.  
- **Pipeline CI/CD** con validación de spec (`SpecificationValidator`) antes de merge.  

### 3. Monitoreo y observabilidad  
- **RED metrics**: Rate, Errors, Duration por endpoint.  
- **KPIs de negocio**: ocupación hotelera, ingresos, ratio de cancelaciones.  
- **Logs centralizados** con trazabilidad de transacciones.  
- **Dashboards** en Grafana/Prometheus para métricas técnicas y de negocio.  

### 4. Alertas y protocolos  
- **P0**: Failover no completado en 15 min → intervención inmediata.  
- **P1**: Gateway de pago caído → alerta crítica.  
- **P2**: Latencia p95 > 1 s en búsqueda → alerta moderada.  
- **P3**: Error rate > 0.5 % en reservas → alerta preventiva.  

### 5. Failover y resiliencia  
- Failover automático a región secundaria en ≤ 15 min.  
- Replicación activa-activa de DB.  
- Circuit breaker en integraciones externas.  
- Retry con backoff exponencial en servicios críticos (email, pagos).  

### 6. Operación continua  
- **On-call rotation** para soporte 24/7.  
- **Runbooks** documentados para incidentes recurrentes.  
- **Postmortems** obligatorios tras incidentes P0/P1.  
