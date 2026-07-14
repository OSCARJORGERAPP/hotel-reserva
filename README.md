
## 📘 README.md — Índice Maestro de la Especificación *HotelReserva*  

### 1. Documentos principales  
- **RESUMEN-EJECUTIVO-Y-ALCANCE.md**  
- **REQUERIMIENTOS-FUNCIONALES.md**  
- **REQUERIMIENTOS-NO-FUNCIONALES.md**  
- **CRITERIOS-DE-ACEPTACION.md** *(incluye FR‑001 a FR‑010)*  
- **CONTRATOS-FORMALES.md**  
- **ESPECIFICACION-DE-FALLOS-Y-RESILIENCIA.md**  
- **SLA-Y-METRICAS-OPERATIVAS.md**  
- **GATE-DE-VALIDACION.md**  
- **ADRs.md**  
- **SPEC-OPERATIVA-Y-DESPLIEGUE.md**  
- **REVISION-GO-NO-GO.md**  
- **ARTEFACTOS-FINALES.md**  

### 2. Organización  
- Cada documento está separado para mantener **prolijidad y extensión razonable**.  
- Los IDs (FR‑XXX, NFR‑XXX, ADR‑XXX) aseguran **trazabilidad** entre requisitos, escenarios y validaciones.  
- El paquete completo constituye la **spec final de HotelReserva**, lista para auditoría, implementación y operación.  

### 3. Uso recomendado  
1. **Inicio** → leer *Resumen Ejecutivo y Alcance*.  
2. **Definición** → revisar FR y NFR.  
3. **Validación** → criterios BDD (FR‑001 a FR‑010) + contratos formales.  
4. **Resiliencia y métricas** → fallos, SLA, operativa.  
5. **Decisiones** → ADRs + Gate de validación.  
6. **Cierre** → revisión Go/No-Go + artefactos finales.  

### 4. Mermaid
flowchart TD
    A[Resumen Ejecutivo y Alcance] --> B[Requisitos Funcionales (FR)]
    A --> C[Requisitos No Funcionales (NFR)]
    B --> D[Criterios de Aceptación (BDD)]
    C --> D
    D --> E[Contratos Formales (TypeScript)]
    D --> F[Espec. Fallos y Resiliencia]
    E --> G[SLA y Métricas Operativas]
    F --> H[ADRs (Decisiones Arquitectónicas)]
    G --> I[Gate de Validación]
    H --> J[Revisión Go / No-Go]
    I --> K[Artefactos Finales]
    J --> K

Nota:

La flecha J --> K significa que una vez completada la Revisión Go/No-Go (J), el proceso continúa hacia la consolidación de los Artefactos Finales (K).

Es el último paso del flujo, donde todo lo validado se integra en el entregable final.

### 5. Roadmap temporal de entregables (Mermaid Gantt)
gantt
    title Roadmap de Entregables - HotelReserva
    dateFormat  YYYY-MM-DD
    section Definición
    Resumen Ejecutivo y Alcance     :done,    des1, 2026-08-01, 3d
    Requerimientos Funcionales (FR) :active,  des2, 2026-08-04, 5d
    Requerimientos No Funcionales   :         des3, 2026-08-09, 5d
    section Validación
    Criterios de Aceptación (BDD)   :         val1, 2026-08-14, 7d
    Contratos Formales (TS)         :         val2, 2026-08-21, 5d
    Espec. Fallos y Resiliencia     :         val3, 2026-08-26, 4d
    section Operativa
    SLA y Métricas Operativas       :         op1, 2026-08-30, 4d
    ADRs                            :         op2, 2026-09-03, 3d
    Spec Operativa y Despliegue     :         op3, 2026-09-06, 5d
    section Cierre
    Gate de Validación              :         cer1, 2026-09-11, 2d
    Revisión Go/No-Go               :         cer2, 2026-09-13, 2d
    Artefactos Finales              :         cer3, 2026-09-15, 3d

### 6. Checklist extendido de Entregables — HotelReserva
# Checklist extendido de Entregables - HotelReserva

## Definición
- [x] Resumen Ejecutivo y Alcance
  - [x] Objetivos claros
  - [x] Alcance delimitado
  - [x] Stakeholders identificados
- [x] Requerimientos Funcionales (FR)
  - [x] IDs trazables (FR-XXX)
  - [x] ≥2 escenarios BDD por FR
  - [x] Edge cases documentados
- [x] Requerimientos No Funcionales (NFR)
  - [x] Cuantificación de métricas (latencia, disponibilidad)
  - [x] Método de verificación definido
  - [x] SLA vinculado

## Validación
- [x] Criterios de Aceptación (BDD)
  - [x] Escenarios happy path
  - [x] Escenarios de error
  - [x] Escenarios de resiliencia
- [x] Contratos Formales (TypeScript)
  - [x] Interfaces con precondiciones
  - [x] Postcondiciones definidas
  - [x] Invariantes documentados
- [x] Especificación de Fallos y Resiliencia
  - [x] DB failover
  - [x] Gateway de pago con circuit breaker
  - [x] Email con retry/backoff
  - [x] Race condition en reservas

## Operativa
- [x] SLA y Métricas Operativas
  - [x] RED metrics (Rate, Errors, Duration)
  - [x] KPIs de negocio
  - [x] Alertas críticas definidas
- [x] ADRs (Decisiones Arquitectónicas)
  - [x] Stack tecnológico
  - [x] DB y transacciones
  - [x] Resiliencia en pagos
  - [x] Despliegue y monitoreo
  - [x] Failover regional
- [x] Spec Operativa y Despliegue
  - [x] Canary deploy progresivo
  - [x] Rollback automático
  - [x] Monitoreo RED + KPIs
  - [x] Runbooks y postmortems

## Cierre
- [x] Gate de Validación
  - [x] Checklist ejecutable
  - [x] Script SpecificationValidator
  - [x] Pipeline CI/CD integrado
- [x] Revisión Go/No-Go
  - [x] Reunión de 45 min
  - [x] Pregunta clave: “¿Entendemos qué vamos a construir?”
  - [x] Decisión Go / Go condicional / No-Go
- [x] Artefactos Finales
  - [x] Documentos separados
  - [x] IDs trazables
  - [x] Paquete completo listo para auditoría

# Checklist en Tabla - HotelReserva

| Documento                         | Subtareas principales                                                                 | Estado |
|-----------------------------------|---------------------------------------------------------------------------------------|--------|
| Resumen Ejecutivo y Alcance       | Objetivos claros, Alcance delimitado, Stakeholders identificados                       | ✅     |
| Requerimientos Funcionales (FR)   | IDs trazables, ≥2 escenarios BDD por FR, Edge cases documentados                       | ✅     |
| Requerimientos No Funcionales     | Métricas cuantificadas, Método de verificación, SLA vinculado                          | ✅     |
| Criterios de Aceptación (BDD)     | Escenarios happy path, Escenarios de error, Escenarios de resiliencia                  | ✅     |
| Contratos Formales (TypeScript)   | Interfaces con precondiciones, Postcondiciones definidas, Invariantes documentados     | ✅     |
| Espec. Fallos y Resiliencia       | DB failover, Circuit breaker en pagos, Retry/backoff en email, Race condition reservas | ✅     |
| SLA y Métricas Operativas         | RED metrics, KPIs de negocio, Alertas críticas definidas                               | ✅     |
| ADRs                              | Stack tecnológico, DB y transacciones, Resiliencia en pagos, Despliegue, Failover      | ✅     |
| Spec Operativa y Despliegue       | Canary deploy, Rollback automático, Monitoreo RED+KPIs, Runbooks y postmortems         | ✅     |
| Gate de Validación                | Checklist ejecutable, Script SpecificationValidator, Pipeline CI/CD integrado          | ✅     |
| Revisión Go/No-Go                 | Reunión 45 min, Pregunta clave, Decisión Go/Condicional/No-Go                          | ✅     |
| Artefactos Finales                | Documentos separados, IDs trazables, Paquete completo listo para auditoría             | ✅     |


