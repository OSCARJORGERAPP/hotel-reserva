## 📘 CRITERIOS-DE-ACEPTACION.md  

### 1. Identificación  
Cada criterio se vincula con un FR específico y se redacta en formato **BDD/Gherkin** para asegurar trazabilidad y validación automatizada.  

### 2. Escenarios principales  

#### FR‑001: Búsqueda de hoteles  
```gherkin
Scenario: Búsqueda exitosa de hoteles
  Given el usuario ingresa ciudad "Buenos Aires" y fechas válidas
  When solicita búsqueda
  Then el sistema muestra lista de hoteles disponibles en <500ms

Scenario: Búsqueda con base de datos caída
  Given el usuario ingresa ciudad "Buenos Aires" y fechas válidas
  When la base de datos no responde en 2s
  Then el sistema devuelve resultados en caché (≤10 min)
  And muestra mensaje "Estamos verificando disponibilidad"
```

#### FR‑002: Visualización de disponibilidad  
```gherkin
Scenario: Disponibilidad mostrada correctamente
  Given el usuario selecciona fechas válidas
  When el sistema consulta la base de datos
  Then se muestra disponibilidad en tiempo real

Scenario: Base de datos caída
  Given el usuario selecciona fechas válidas
  When la base de datos no responde en 2s
  Then el sistema muestra datos en caché (≤10 min)
  And muestra mensaje "Estamos verificando disponibilidad"
```


#### FR‑003: Reserva de habitaciones  
```gherkin
Scenario: Reserva exitosa
  Given el usuario selecciona habitación disponible
  When confirma la reserva y realiza pago válido
  Then el sistema crea la reserva y envía email de confirmación

Scenario: Reserva fallida por race condition
  Given dos usuarios intentan reservar la misma habitación
  When el sistema procesa transacciones concurrentes
  Then uno obtiene la reserva
  And el otro recibe mensaje "Otro usuario reservó justo ahora"
```

#### FR‑004: Cancelación de reservas  
```gherkin
Scenario: Cancelación dentro de plazo permitido
  Given el usuario tiene una reserva confirmada
  When solicita cancelación 48h antes del check-in
  Then el sistema cancela la reserva sin penalización
  And envía email de confirmación

Scenario: Cancelación fuera de plazo
  Given el usuario tiene una reserva confirmada
  When solicita cancelación 12h antes del check-in
  Then el sistema aplica penalización automática
  And muestra mensaje "Se aplicará un cargo por cancelación tardía"
```

#### FR‑005: Modificación de reservas  
```gherkin
Scenario: Modificación exitosa
  Given el usuario tiene una reserva confirmada
  When solicita cambiar fechas y hay disponibilidad
  Then el sistema actualiza la reserva
  And recalcula precio y envía email de confirmación

Scenario: Modificación fallida por falta de disponibilidad
  Given el usuario tiene una reserva confirmada
  When solicita cambiar fechas y no hay disponibilidad
  Then el sistema rechaza la modificación
  And muestra mensaje "No hay disponibilidad para las nuevas fechas"
```

#### FR‑006: Procesamiento de pagos  
```gherkin
Scenario: Pago exitoso
  Given el usuario ingresa tarjeta válida
  When el gateway responde en <5s
  Then la reserva se confirma y se marca como "PAID"

Scenario: Gateway caído
  Given el usuario ingresa tarjeta válida
  When el gateway primario no responde en 10s
  Then el sistema intenta gateway secundario
  And si falla, marca orden como "PENDING_PAYMENT"
  And muestra mensaje "Tu pago está siendo procesado lentamente"
```

#### FR‑007: Notificaciones y confirmaciones  
```gherkin
Scenario: Email enviado exitosamente
  Given el sistema confirma la reserva
  When el servicio de email está disponible
  Then envía email de confirmación al usuario

Scenario: Email service caído
  Given el sistema confirma la reserva
  When el servicio de email falla
  Then la orden se crea exitosamente
  And el email se reintenta cada 5 min hasta 1 hora
```
Tenés razón, Oscar. Para que la **trazabilidad** quede completa, debemos documentar también los criterios de aceptación de **FR‑008, FR‑009 y FR‑010**. Aquí te los agrego en el mismo formato BDD/Gherkin:  


#### FR‑008: Gestión de usuarios  
```gherkin
Scenario: Registro exitoso
  Given el usuario ingresa datos válidos
  When confirma el registro
  Then el sistema crea la cuenta
  And envía email de bienvenida

Scenario: Registro fallido por email duplicado
  Given el usuario ingresa un email ya registrado
  When confirma el registro
  Then el sistema rechaza la operación
  And muestra mensaje "Este email ya está en uso"
```

#### FR‑009: Autenticación segura  
```gherkin
Scenario: Login exitoso
  Given el usuario ingresa credenciales válidas
  When solicita acceso
  Then el sistema valida credenciales
  And permite acceso al panel

Scenario: Login fallido
  Given el usuario ingresa credenciales inválidas
  When solicita acceso
  Then el sistema rechaza la autenticación
  And muestra mensaje "Usuario o contraseña incorrectos"
```

#### FR‑010: Recuperación de contraseña  
```gherkin
Scenario: Solicitud de recuperación válida
  Given el usuario solicita recuperar contraseña
  When ingresa un email registrado
  Then el sistema envía enlace de recuperación
  And registra la solicitud en logs

Scenario: Solicitud inválida
  Given el usuario solicita recuperar contraseña
  When ingresa un email no registrado
  Then el sistema rechaza la operación
  And muestra mensaje "No existe una cuenta asociada a este email"
```
