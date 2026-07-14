## 📘 REVISION-GO-NO-GO.md  

### 1. Principios  
- La revisión Go/No-Go es el **último filtro de calidad** antes de pasar a implementación.  
- Se asegura que el equipo **entienda completamente qué se va a construir**.  
- Se basa en tiempos definidos, roles claros y criterios objetivos.  

### 2. Flujo de reunión  
- **Tech Lead presenta la spec** (15 min).  
- **Equipo revisa** (10 min).  
- **Debate abierto** (15 min).  
- **Decisión final** (5 min).  

Duración total: **45 minutos**.  

### 3. Resultados posibles  
- **Go (verde)**:  
  - La spec pasa todos los checkpoints.  
  - El equipo confía en la implementación.  

- **Go condicional (amarillo)**:  
  - Faltan 1–2 checkpoints menores.  
  - Se crean ADRs para cubrir los gaps.  

- **No-Go (rojo)**:  
  - Fallan checkpoints críticos.  
  - La spec vuelve a revisión y no se implementa.  

### 4. Pregunta clave  
- “¿Realmente entendemos qué vamos a construir?”  
- La respuesta debe ser **sí** para avanzar.  

### 5. Checklist vinculado  
- IDs trazables (FR, NFR, REG).  
- Escenarios BDD completos.  
- Especificación de fallos por dependencia.  
- ADRs documentados.  
- SLA definidos y verificables.  
