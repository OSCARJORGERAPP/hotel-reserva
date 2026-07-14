## 📘 ADRs.md  

### 1. Principios  
- Cada ADR registra una decisión arquitectónica relevante.  
- Incluye contexto, decisión, consecuencias y alternativas descartadas.  
- Se numeran y vinculan con FR/NFR para trazabilidad.  

### 2. ADRs principales  

#### ADR‑001: Stack tecnológico  
- **Contexto**: Se requiere un stack moderno, escalable y con soporte comunitario.  
- **Decisión**: Backend en **Node.js + TypeScript**, frontend en **React**, DB en **PostgreSQL**.  
- **Consecuencias**: Ecosistema sólido, tipado fuerte, soporte multiplataforma.  
- **Alternativas descartadas**: Java/Spring (mayor complejidad), MongoDB (menos consistencia).  

#### ADR‑002: Base de datos y transacciones  
- **Contexto**: Se necesita consistencia fuerte en reservas.  
- **Decisión**: PostgreSQL con transacciones serializables.  
- **Consecuencias**: Prevención de race conditions, integridad garantizada.  
- **Alternativas descartadas**: Isolation read committed (riesgo de inconsistencias).  

#### ADR‑003: Resiliencia en pagos  
- **Contexto**: Gateway de pago puede fallar.  
- **Decisión**: Circuit breaker + retry policy + fallback a gateway secundario.  
- **Consecuencias**: Alta confiabilidad en transacciones financieras.  
- **Alternativas descartadas**: Retry ilimitado (riesgo de saturación).  

#### ADR‑004: Despliegue y operaciones  
- **Contexto**: Se requiere despliegue seguro y monitoreo continuo.  
- **Decisión**: Canary deploy progresivo (5 % → 25 % → 100 %), monitoreo RED + KPIs de negocio.  
- **Consecuencias**: Reducción de riesgo en releases, visibilidad operativa.  
- **Alternativas descartadas**: Deploy directo (alto riesgo).  

#### ADR‑005: Failover regional  
- **Contexto**: Alta disponibilidad global.  
- **Decisión**: Failover automático a región secundaria en ≤ 15 min.  
- **Consecuencias**: SLA 99.9 % garantizado.  
- **Alternativas descartadas**: Failover manual (tiempo excesivo).  
