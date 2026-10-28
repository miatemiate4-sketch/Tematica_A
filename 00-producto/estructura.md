# Decisión de estructuras — WorldCave

**Contexto:** Imagínate un tipo Zelda o Genshin Impact, pero más simple y la verdadera gracia del juego es que está debajo de la tierra. Por arriba caminas por montañas y campos, pero el juego de verdad empieza cuando te metes a las cuevas. Ahí abajo hay un laberinto gigante lleno de ruinas y enemigos. Tu meta es bajar, y pelear contra 4 monstruos de los elementos (Fuego, Agua, Tierra y Viento) y conseguir sus armas y armaduras, cada que derrotes a uno de los enemigos se van sumando puntos y pasando de nivel hasta llegar hasta los jefes, cada nivel que serían 4 en total seria un enemigo y un jefe y el “Héroe” cada que derrote a un enemigo le sumara puntos. 

| Capacidad del dominio | Estructura elegida | Por qué esta | Alternativa descartada y motivo | Complejidad clave |
|---|---|---|---|---|
| Eventos del juego | Cola de prioridad / montículo | La Cola de prioridad ordena los eventos según el tiempo de ejecución o importancia. | Cola (FIFO): Los eventos (daño, efectos de sonido, animaciones) suceden en el orden exacto en que son generados. Procesar una Cola asegura que el primer evento que ocurre sea el primero en resolverse (First In, First Out). | O(log N) |

| Índice de entidades o puntajes | Árbol AVL | Mantienen los datos automáticamente ordenados. Permite realizar búsquedas, inserciones y consultas de rango en tiempo. El AVL garantiza balanceo estricto para evitar degradación | Tabla hash: Se selecciona cuando la prioridad es buscar entidades por su identificador único, aunque no sirve para obtener un ranking ordenado | O(log N) |

| Ruta de los enemigos hacia el jugador | Grafo (lista de adyacencia) | El mapa se representa como nodos y aristas (caminos). Una lista de adyacencia es eficiente en memoria para grafos dispersos (mapas de juegos) y permite ejecutar algoritmos de búsqueda de caminos | Grafo (Matriz de adyacencia): Solo se justifica si casi todos los nodos están conectados con todos los demás (grafos muy densos), ya que verificar si dos nodos están conectados toma O(1), pero consume memoria O(V2) | O( E log V) |

| Representación del mapa (mayoría de celdas vacías) | Matriz dispersa | Un mapa grande con pocas entidades o celdas ocupadas desperdiciaría mucha memoria con una matriz convencional. La matriz dispersa guarda únicamente las coordenadas de las celdas con contenido. | Tabla hash: Permite almacenar las celdas ocupadas usando una clave compuesta como "x, y". Si la clave no existe en la tabla, el juego asume de inmediato que la celda está | O(1) |

| Inventario del jugador | Arreglo / arreglo dinámico |  Permite acceso rápido por índice u ordenación fija de ítems. | Lista enlazada ): Útil solo si el inventario no tiene casillas fijas y los ítems se agregan/eliminan constantemente en medio del inventario sin dejar espacios vacíos, pues insertar o eliminar no requiere reordenar todo el arreglo. | O(1) |

| Orden de los turnos | Lista circular |  Un sistema de turnos rota continuamente entre los jugadores o entidades (Jugador 1 -> jugador 2 -> jugador 3 -> jugador 1.) | Cola: Garantiza que quien actúa pase al final de la fila. Se procesa el frente de la cola y, al terminar su turno, se reinserta al final. | O(1) |

| Deshacer y rehacer | Pila | Funciona mediante el principio LIFO (Último en entrar, primero en salir).  | Lista doble: Se utiliza si se prefiere mantener un único historial con un puntero o índice que se desplaza hacia atrás o hacia adelante a lo largo del registro de acciones. | O(1) |