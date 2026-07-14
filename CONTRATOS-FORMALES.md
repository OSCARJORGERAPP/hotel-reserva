## 📘 CONTRATOS-FORMALES.md  

### 1. Principios  
- Cada contrato define **interfaces y tipos** en TypeScript.  
- Se documentan **precondiciones, postcondiciones e invariantes** para asegurar consistencia.  
- Los contratos se vinculan con FR y NFR para trazabilidad.  

### 2. Entidades principales  

#### Hotel  
```typescript
interface Hotel {
  id: string;              // Invariante: UUID válido
  nombre: string;          // Precondición: no vacío
  ciudad: string;          // Precondición: valor válido en catálogo
  habitaciones: Habitacion[];
}
```
- **Precondición**: `nombre` y `ciudad` no pueden ser nulos.  
- **Postcondición**: cada hotel debe tener ≥ 1 habitación.  
- **Invariante**: `id` único en todo el sistema.  

#### Habitacion  
```typescript
interface Habitacion {
  id: string;              // Invariante: UUID válido
  capacidad: number;       // Precondición: > 0
  disponible: boolean;
}
```
- **Precondición**: capacidad > 0.  
- **Postcondición**: disponibilidad actualizada en cada reserva.  
- **Invariante**: `id` único dentro del hotel.  

#### Reserva  
```typescript
interface Reserva {
  id: string;              // Invariante: UUID válido
  hotelId: string;         // Precondición: hotel existente
  habitacionId: string;    // Precondición: habitación disponible
  usuarioId: string;       // Precondición: usuario autenticado
  fechas: { inicio: Date; fin: Date }; // Precondición: inicio < fin
  estado: "CONFIRMED" | "CANCELLED" | "PENDING_PAYMENT";
}
```
- **Precondición**: habitación debe estar disponible.  
- **Postcondición**: estado inicial = `CONFIRMED` o `PENDING_PAYMENT`.  
- **Invariante**: fechas no se solapan con otra reserva confirmada.  

#### Usuario  
```typescript
interface Usuario {
  id: string;              // Invariante: UUID válido
  email: string;           // Precondición: formato válido
  nombre: string;
  rol: "HUESPED" | "ADMIN";
}
```
- **Precondición**: email válido.  
- **Postcondición**: usuario autenticado con JWT.  
- **Invariante**: rol definido.  

#### Pago  
```typescript
interface Pago {
  id: string;              // Invariante: UUID válido
  reservaId: string;       // Precondición: reserva existente
  monto: number;           // Precondición: > 0
  estado: "SUCCESS" | "FAILED" | "PENDING";
}
```
- **Precondición**: monto > 0.  
- **Postcondición**: estado actualizado tras respuesta del gateway.  
- **Invariante**: cada pago vinculado a una reserva única.  
