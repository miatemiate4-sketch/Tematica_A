# Plan técnico — WorldCave
**Especificación de referencia:** `spec.md` v1.0

## 1. Estructura de datos elegida
Arreglo. es ideal porque los niveles son fijos (1 a 4) y te permite cargar el siguiente nivel de forma inmediata por su número de índice.

## 2. Alternativas consideradas
| Alternativa | Ventaja | Por qué se descartó |
|---|---|---|
| Lista Enlazada | Permite insertar o eliminar nodos dinámicamente en tiempo de ejecución sin definir un tamaño límite inicial. | El acceso a un nivel específico no es directo (requiere recorrido secuencial O(n) y consume memoria adicional guardando punteros. |
| Arreglo dinamico | Se expande automáticamente si se agregan más elementos durante la ejecución. | Innecesario para este caso de uso, ya que la cantidad total de niveles (4) es constante y conocida desde el diseño; la redimensión dinámica generaría sobrecosto en memoria sin aportar beneficio |

## 3. Complejidad esperada
| Operación | Tiempo | Espacio | Justificación |
|---|---|---|---|
| obtenerNivelActualnto | O(1) | O(1) | Acceso directo al mapa del nivel actual mediante la posición niveles[nivelActual] |
| desbloquearSiguienteNivel | O(1) | O(1) | Incrementa el índice (nivelActual++) tras derrotar al enemigo y accede al siguiente mapa al instante. |
| consultarNivelPorIndice | O(1) | O(1) | Retorna los datos de cualquiera de los 4 niveles en tiempo constante gracias al direccionamiento por índice |
| buscarEnemigoEnNivel | O(n) | O(1) | Recorre las casillas o la lista interna de entidades del mapa asignado en ese índice del arreglo. |
| reiniciarProgreso | O(1) | O(1) | Restringir las asignaciones del índice mediante un método encapsulado con validación de rango estricto. |

## 4. Diseño interno
un arreglo estático niveles de tamaño $4$ (índices $0$ a $3$). Una variable entera nivelActual actúa como índice de control, indicando la cueva activa. La invariante del sistema asegura que 0 ≤ nivelActual ≤ tamañoTotal(4). Si nivelActual == 3 y se derrota al jefe Elemental, el juego reconoce la condición de victoria final.

## 5. Riesgos técnicos
| Riesgo | Impacto | Mitigación |
|---|---|---|
| Acceso fuera de los límites del arreglo | Alto | Validar antes de cada cambio de nivel que nivelActual + 1 < niveles.Length |
| Intento de cargar un nivel inexistente ($<0$ o $>3$) | Medio | Validar que tamanio > 0 o que tope != null antes de realizar la operación de desapilar. |