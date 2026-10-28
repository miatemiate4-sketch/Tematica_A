# Historias de usuario — Temática A: WorldCave

Generado con el Constructor de historias de usuario. Fecha: 15/10/2026.

## Resumen del backlog

| ID | Historia | Prioridad | Horas | Estructura candidata |
|---|---|---|---|---|
| HU-01 | Derrotar al enemigo y se pasa de nivel | Must | 3 | Arreglo|
| HU-02 | recibir daño de los ataques enemigos y visualizar mi salud restante | Must | 4 | Arreglo / arreglo dinámico |
| HU-03 | Quiero mover a mi personaje en las 4 direcciones dentro del mapa | Must | 4 | Matriz dispersa |
| HU-04 | Quiero consultar un mapa de la cueva explorada hasta el momento | Should | 3 | Matriz dispersa |
| HU-05 | Quiero deshacer mi último acción errónea dentro de la cueva | Could | 2 | Pila |
| HU-06 | conectarme a internet e invitar a un amigo a mi partida dentro de la cueva | Won't |  | |
| HU-07 | guardar mi progreso del juego en un servidor remoto en la nube | Won't | — | — |

## HU-01 · Must

**Como** jugador, **quiero** Derrotar al enemigo y se pasa de nivel **para** llegar al jefe Elemental.

- **Estimación:** 3 h
- **Estructura candidata:** Arreglo _(se justifica en el plan.md del componente)_

**Criterios de aceptación**

- **CA-01:** Al reducir la vida del enemigo a 0, el nivelActual aumenta en 1 y carga el siguiente mapa.
- **CA-02:** Intentar pasar de nivel con el enemigo vivo lanza un error de acceso denegado.
- **CA-03:** El cambio de nivel valida que 1 ≤ nivelActual ≤
- **CA-04:** Al cambiar de nivel, el héroe mantiene sus stats, XP y equipamiento

## HU-02 · Must

**Como** jugador, **quiero** Quiero mover a mi personaje en las 4 direcciones dentro del mapa **para** explorar las salas de la cueva, evitar obstáculos y encontrar la salida o enemigos..

- **Estimación:** 4 h
- **Estructura candidata:** Matriz dispersa _(se justifica en el plan.md del componente)_

**Criterios de aceptación**

- **CA-01:**  Presionar una tecla de dirección válida actualiza las coordenadas (x, y) del personaje dentro de la matriz del mapa.
- **CA-02:** Intentar caminar hacia una pared o bloque impenetrable impide el movimiento y mantiene al personaje en su posición.

## HU-03 · Must

**Como** jugador, **quiero** recibir daño de los ataques enemigos y visualizar mi salud restante **para** saber el estado de mi héroe y reiniciar o finalizar la partida si mi vida llega a cero.

- **Estimación:** 4 h
- **Estructura candidata:** Arreglo / arreglo dinámico _(se justifica en el plan.md del componente)_

**Criterios de aceptación**

- **CA-01:** Cuando el enemigo ataca, la salud actual del personaje decrece proporcionalmente según el daño recibido
- **CA-02:** Si el HP del héroe llega a 0, la partida finaliza inmediatamente y muestra la pantalla de derrota.

## HU-04 · Should

**Como** jugador, **quiero** Quiero consultar un mapa de la cueva explorada hasta el momento **para** orientarme dentro del laberinto de túneles, ubicar salas pendientes de explorar y no perderme.

- **Estimación:** 3 h
- **Estructura candidata:** Matriz dispersa _(se justifica en el plan.md del componente)_

**Criterios de aceptación**

- **CA-05:** El minimapa actualiza y dibuja únicamente las celdas o salas que el jugador ya ha pisado.
- **CA-06:** Las áreas no descubiertas se mantienen ocultas ("niebla de guerra") mapa.
- **CA-07:**  El mapa resalta con un marcador la posición actual del héroe dentro de la cueva.

## HU-05 · Could

**Como** jugador, **quiero** Quiero deshacer mi último acción errónea dentro de la cueva **para** corregir una decisión táctica, sin perder la partida.

- **Estimación:** 2 h
- **Estructura candidata:** Por decidir _(se justifica en el plan.md del componente)_

**Criterios de aceptación**

- **CA-08:** Al presionar un botón(retroceder), la posición del jugador y el estado del mapa regresan exactamente al turno anterior.
- **CA-09:** Intentar deshacer cuando la pila de acciones está vacía no altera el juego y muestra un mensaje de aviso.
- **CA-10:** La acción de deshacer se deshabilita durante el enfrentamiento directo contra un jefe Elemental.

## HU-06 · Won't

**Como** jugador, **quiero** conectarme a internet e invitar a un amigo a mi partida dentro de la cueva **para** explorar los túneles y combatir juntos en tiempo real a los jefes Elementales.

**Razón de la exclusión:** WorldCave está planteado como un juego de exploración y combate individual por niveles

## HU-07 · Won't

**Como** jugador, **quiero** guardar mi progreso del juego en un servidor remoto en la nube **para** poder retomar mi partida desde cualquier otra computadora o terminal sin perder mis niveles ni mi inventario..

**Razón de la exclusión:** No requiere infraestructura de nube ni servidores web porque el curso evalúa estructuras de datos locales en consola, y para un juego de terminal de 4 niveles basta con un archivo local simple

