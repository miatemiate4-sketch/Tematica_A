# Especificación — WorldCave
**Versión:** 1.0 · **Fecha:** 2026-10-16 · **Autor:** Maite

## 1. Propósito
que el jugador pueda explorar y combatir en laberintos subterráneos. Controlas a un héroe que desciende por 4 niveles de cuevas para derrotar a 4 jefes elementales (Fuego, Agua, Tierra y Viento), enfrentando enemigos menores en el camino para sumar puntos, subir de nivel y obtener sus armas y armaduras.

## 2. Fuera de alcance
No tiene una progresión infinita de niveles ni infinidad de jefes, son solo 4 niveles en si por pasar 
No se rescatará ni una princesa ni nada de eso, es un juego que se centra en derroten a 4 jefes elementos 

## 3. Operaciones
### `iniciarNivel(numeroNivel)`
- **Precondiciones:** numeroNivel está entre 1 y 4; el héroe está vivo salud > 0; si numeroNivel > 1, el jefe del nivel anterior fue derrotado.
- **Postcondiciones:** El nivel actual del juego cambia a numeroNivel; se cargan los enemigos menores y el jefe elemental correspondiente
- **Errores:** NivelBloqueadoError si intenta acceder a un nivel sin haber derrotado al jefe previo; NivelInvalidoError si numeroNivel no está entre 1 y 4

### `registrarDerrotaEnemigo(enemigo)`
- **Precondiciones:** enemigo no es nulo; el enemigo pertenece al nivel actual y su salud es ≤ 0
- **Postcondiciones:** Se suman los puntos del enemigo al puntaje total del héroe; se incrementa la experiencia del héroe; si la experiencia alcanza el umbral, el héroe sube de nivel.
- **Errores:** EnemigoInvalidoError si enemigo es nulo o ya había sido registrado como derrotado.

### `equiparRecompensa(item)`
- **Precondiciones:** item no es nulo; item es un arma o armadura obtenida tras derrotar a un enemigo o jefe elemental del nivel actual.
- **Postcondiciones:** El héroe equipa item; se actualizan las estadísticas de ataque o defensa del héroe según el elemento del ítem.
- **Errores:** ItemInvalidoError si item es nulo o no pertenece a las recompensas válidas del juego.

### `derrotarJefeElemental(jefe)`
- **Precondiciones:**  jefe no es nulo; jefe es uno de los 4 jefes elementales (Fuego, Agua, Tierra, Viento) del nivel actual; la salud del jefe es ≤ 0
- **Postcondiciones:** El jefe queda marcado como derrotado; se otorga el equipamiento elemental único al héroe; se desbloquea el acceso al siguiente nivel de la cueva
- **Errores:** JefeNoValidoError si jefe es nulo o no es el jefe correspondiente al nivel actual.

## 4. Invariantes
- INV-01: Límite de Niveles: El nivel actual de las cuevas siempre debe estar 1 ≤ nivelActual ≤4 en el rango 
- INV-02: Progresión de Puntaje: El puntaje total del héroe siempre debe ser ≥ 0 y no puede disminuir.
- INV-03: Integridad de jefes Elementales: El número total de jefes elementales derrotados siempre ≤ 4 nunca exceder
- INV-04: Consistencia de Nivel y jefes: Para estar en el nivel N (2), jefesDerrotados >= nivelActual - 1

## 5. Criterios de aceptación
| ID | Criterio | Verificable mediante |
|---|---|---|
| CA-01 | Derrota de Enemigo Menor y Suma de Puntos | test_derrotar_enemigo_suma_puntos |
| CA-02 | Victoria sobre jefe Elemental y Desbloqueo de Nivel | test_derrotar_jefe_siguiente_nivel |
| CA-03 | Restricción de Acceso a Niveles Bloqueados | test_nivel_bloqueado_lanza_error |
| CA-04 | Subida de Nivel por Experiencia de Combate | test_acumular_experiencia_sube_nivel |
| CA-05 | Equipamiento de Arma y Armadura Elemental | test_equipar_armadura_elemental_actualiza_stats |
| CA-06 | Manejo de Muerte del Héroe | test_game_over |
| CA-07 | Victoria Total al Derrotar al Cuarto jefe | test_completa_juego |

## 6. Casos extremos considerados
- Nivel fuera de rango
- Desapilar historial vacío
- Lista de enemigos vacía
- Muerte simultánea héroe/jefe
- Avanzar sin derrotar al jefe

## 7. Historial de cambios
| Versión | Fecha | Cambio | Motivo |
|---|---|---|---|
| 1.0 | 2026-10-12 | Versión inicial | inicioi |