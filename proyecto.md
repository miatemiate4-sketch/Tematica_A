# Especificación del sistema — WorldCave
**Temática:** A · **Autor:** Maite · **Fecha:** 2026-10-16

## 1. Descripción del sistema
WorldCave es un juego de exploración y combate desde la consola. El jugador empieza en la superficie (montañas) y luego desciende a un laberinto subterráneo de 4 niveles. Su objetivo es derrotar a 4 monstruos elementales (Fuego, Agua, Tierra, Viento), conseguir su equipamiento y acumular puntos hasta completar el juego.
Inicio: El jugador ejecuta la consola y empieza en la superficie (nivel de aprendizaje).
Descenso a las cuevas: Accede al laberinto subterráneo (niveles 1 al 4).
Exploración y equipamiento: Navega por los mapas, elige y cambia entre sus armas según el elemento del enemigo.
Combate: Enfrenta al enemigo y al jefe de cada nivel aprovechando las debilidades elementales.
Progreso: Al derrotar un monstruo, el Héroe gana puntos, sube de nivel y obtiene nuevas armas y armaduras.
Victoria: Tras derrotar a los 4 jefes elementales, la consola muestra la puntuación total y finaliza la partida.

## 2. Componentes
| Carpeta | Componente | Capacidad que resuelve |
|---|---|---|
| proyecto | WorldCave | — |

## 3. Cómo encajan los contratos
Componente 01 (Consola/Interfaz): Captura las acciones del usuario (moverse, atacar, cambiar arma) y muestra la interfaz visual.
Componente 02 (Niveles y Mapa): Controla la posición del jugador en la superficie y los 4 niveles subterráneos.
Componente 03 (Combate y Elementos): Calcula el daño del ataque según el arma elegida y la fortaleza del elemento (Fuego, Agua, Tierra, Viento).
Componente 04 (Inventario y Héroe): Administra las armas y armaduras equipadas, actualiza las estadísticas del personaje y suma los puntos ganados.
Componente 05 (Progreso y Datos): Guarda el estado de la partida, los jefes derrotados y gestiona el cambio de nivel.
El Componente 01 recibe el comando del jugador y llama al Componente 02 para moverlo por el mapa. Al encontrar un enemigo, el Componente 02 inicia la batalla llamando al Componente 03. El Componente 03 consulta al Componente 04 para saber qué arma tiene equipada el Héroe y calcula el daño elemental. Al ganar la batalla, el Componente 03 avisa al Componente 04 para entregar el botín (armas/armaduras) y sumar puntos. Finalmente, el Componente 04 notifica al Componente 05 para registrar el jefe derrotado y desbloquear el siguiente nivel.