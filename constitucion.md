# Constitución del proyecto — WorldCave
**Autor:** Maite · **Temática:** A · **Repositorio:** https://github.com/miatemiate4-sketch/Tematica_A

## Principios
1. Modularidad en armas y elementos: Permite cambiar de equipamiento e interconectar elementos sin congelar ni pausar la jugabilidad
2. Procesamiento de entrada de baja latencia: Prioriza la respuesta inmediata de los botones para lograr un combate rápido y fluido.
3. Carga de mapa asíncrona: Carga los niveles subterráneos en segundo plano para explorar sin pantallas de carga interrumpiendo el flujo
4. Jerarquía y claridad visual: Modera los efectos visuales (VFX) de los ataques elementales para que la pantalla no se sature en combate.
5. Gestión centralizada de progresión: Un único gestor calcula los puntos y cambios de nivel al derrotar cada enemigo o jefe.

## Restricciones
- Bloqueo en combate: No puedes cambiar de arma mientras estás atacando, en el aire o si un enemigo te aturdió
- Debilidades fijas: La tabla de elementos es estricta (ejemplo Agua vence a Fuego) y no se puede modificar.
- Paso bloqueado por niveles: No puedes bajar al siguiente nivel subterráneo sin haber derrotado al jefe del nivel actual.
- Límite de luces: Al estar bajo tierra, hay un límite de antorchas y luces activas a la vez para evitar que el juego se ponga lento
- Reinicio por muerte: Si mueres en la cueva, pierdes el progreso del nivel actual y reapareces en el último checkpoin

## Definición de terminado
Una funcionalidad está terminada cuando:
- [ ] Todos sus criterios de aceptación tienen prueba y pasan
- [ ] La complejidad real coincide con la declarada en el plan
- [ ] Revisé el código contra la spec antes de integrarlo
- [ ] spec.md, plan.md y tasks.md reflejan el estado real

## Uso de asistentes de IA
Permitido para: Entender conceptos, depurar errores y revisar mi código contra la spec.
No permitido para: Entregar código que no pueda explicar línea por línea.
Todo aporte de IA se revisa contra la especificación antes de integrarse y se declara en BITACORA.md.