## 📘 ESPECIFICACION-DE-FALLOS-Y-RESILIENCIA.md  

### 1. Principios  
- Cada dependencia crítica debe tener **patrón de resiliencia asignado**.  
- Los fallos se documentan con: **qué ocurre, cuándo ocurre y quién lo corrige**.  
- Se definen **SLA y tiempos de recuperación** para cada escenario.  

### 2. Escenarios de fallos  

#### Base de datos (DB)  
- **Fallo**: caída del nodo primario.  
- **Resiliencia**: failover automático a réplica secundaria.  
- **Tiempo de recuperación**: ≤ 15 minutos.  
- **Patrón aplicado**: réplica + heartbeat monitoring.  

#### Gateway de pago  
- **Fallo**: gateway primario no responde en 10s.  
- **Resiliencia**: retry automático (3 intentos) → fallback a gateway secundario.  
- **Tiempo de recuperación**: inmediato (≤ 30s).  
- **Patrón aplicado**: circuit breaker + retry policy.  

#### Servicio de email  
- **Fallo**: caída del proveedor SMTP.  
- **Resiliencia**: reintento cada 5 minutos durante 1 hora.  
- **Tiempo de recuperación**: ≤ 60 minutos.  
- **Patrón aplicado**: retry con backoff exponencial.  

#### Race condition en reservas  
- **Fallo**: dos usuarios intentan reservar la misma habitación.  
- **Resiliencia**: transacciones serializables en DB.  
- **Tiempo de recuperación**: inmediato.  
- **Patrón aplicado**: lock optimista/pesimista según escenario.  

#### API externa de disponibilidad hotelera  
- **Fallo**: proveedor externo no responde.  
- **Resiliencia**: cache local válido por ≤ 10 minutos.  
- **Tiempo de recuperación**: ≤ 10 minutos.  
- **Patrón aplicado**: fallback cache + timeout controlado.  

### 3. SLA de resiliencia  
- **Search**: p95 < 500 ms, error < 0.5 %.  
- **Reservation**: p95 < 3 s, error < 1 %.  
- **Payment**: success > 99.9 %, tiempo < 5 s.  
- **Failover regional**: ≤ 15 minutos.  

