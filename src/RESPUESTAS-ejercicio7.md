# Ejercicio 7 — `type` vs `interface`

> Este archivo no se corrige con tests automáticos: lo lee el docente.
> Respondé con tus palabras, en base a lo que probaste en `ej07-tipos-interfaces.ts`.

## ¿Qué permite hacer `interface` que `type` no (o no tan bien)?

Lo que permite hacer interface es que si declaro la misma interface 2 veces, typescript combina ambas declaraciones en 1 sola, en cambio type no permite esto, ya que si lo defino 2 veces con el mismo nombre da error

## ¿Qué permite hacer `type` que `interface` no?

Lo que permite hacer type es el poder representar cosas que no son "forma de un objeto":  
uniones (`type Estado = "activo" | "inactivo"`), tuplas (`type Par = [number, string]`), 
alias de tipos primitivos (`type ID = number`) y 
mapped types (`type Parcial<T> = { [K in keyof T]?: T[K] }`). 
`interface` solo puede describir la forma de un objeto (o función/clase), no estas variantes.

## ¿Ambas se pueden extender? ¿Cómo se hace en cada caso?

Sí, las dos. Con `interface` se extiende con `extends`:
`interface Alumno extends Persona { legajo: number }`.

Con `type` se combina con intersección (`&`):
`type Alumno = Persona & { legajo: number }`. 
El resultado es similar, pero `type` con intersección no hace merge automático si se repite el nombre.

## ¿Cuál elegirían para representar una entidad del dominio (por ejemplo, `Alumno`)? ¿Por qué?

Usaría `interface`, porque `Alumno` es una entidad con forma de objeto fija que puede necesitar extenderse (por ejemplo `AlumnoRegular extends Alumno`) o ser implementada por una clase. 

`type` lo dejaría para casos como uniones de estados, tipos utilitarios o combinaciones más complejas que no son solo la forma de un objeto.
