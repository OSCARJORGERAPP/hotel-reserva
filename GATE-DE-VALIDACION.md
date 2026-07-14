## 📘 GATE-DE-VALIDACION.md  

### 1. Principios  
- El **gate de validación** es obligatorio antes de avanzar a implementación.  
- Se basa en un **checklist ejecutable** y en una reunión de revisión dura.  
- El resultado puede ser **Go, Go condicional o No-Go**.  

### 2. Checklist ejecutable  
Cada módulo debe cumplir:  
- IDs únicos y trazables (FR‑XXX, NFR‑XXX, REG‑XXX).  
- NFR cuantificados con método de verificación.  
- ≥ 2 escenarios BDD por FR (happy + error).  
- Máquinas de estado cubren todos los edge cases.  
- Dependencias con especificación de fallos (circuit breaker, fallback).  
- Documentación suficiente para que un ingeniero nuevo implemente sin preguntar.  

### 3. Revisión dura (decisión Go/No-Go)  
- **Formato de reunión**:  
  - Tech lead presenta spec (15 min).  
  - Equipo revisa (10 min).  
  - Debate (15 min).  
  - Decisión (5 min).  

- **Resultados posibles**:  
  - **Go (verde)**: spec pasa todos los checkpoints, equipo confía.  
  - **Go condicional (amarillo)**: faltan 1–2 checkpoints menores, se crean ADRs para cubrir gaps.  
  - **No-Go (rojo)**: fallan checkpoints críticos, la spec vuelve a revisión.  

- **Pregunta clave**:  
  - “¿Realmente entendemos qué vamos a construir?”  
  - La respuesta debe ser **sí** para avanzar.  

### 4. Automatización  
- El checklist se implementa como script (`SpecificationValidator`).  
- Si `result.canProceed = false` → el pipeline se detiene (`process.exit(1)`).  
- Reporte automático indica qué checkpoint falló y qué acción tomar.  
