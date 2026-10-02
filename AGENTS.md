# AGENTS.md

## Qué es

Clon de Asteroids en HTML5 Canvas puro. Sin framework, sin bundler, sin dependencias. **No hay `package.json`**: no ejecutes `npm install` ni busques scripts de build/test/lint. Todo el juego vive en `game.js` (un solo archivo, sin módulos ES) cargado por `index.html`.

## Verificación

No hay tests automatizados ni CI. La única forma de verificar es manual:

- Abrir `index.html` en el navegador (doble clic) o `npx serve .` → http://localhost:3000.
- Probar: rotar/propulsar (flechas), disparar (Espacio), chocar contra un asteroide (pierdes vida, reaparición con invencibilidad), limpiar la pantalla (sube el nivel), llegar a GAME OVER y reiniciar con Espacio.
- Vigilar la consola del navegador: cualquier excepción mata el bucle `requestAnimationFrame` y el juego se congela en silencio.

## Arquitectura mínima

- Canvas fijo de 800x600. Las constantes `W`/`H` de `game.js` deben coincidir con los atributos `width`/`height` del `<canvas>` en `index.html`.
- Estado global en variables de nivel superior (`ship`, `bullets`, `asteroids`, `particles`, `score`, `lives`, `level`, `state`), con máquina de estados `'playing' | 'dead' | 'gameover'`. `initGame`, `nextLevel` y `killShip` son quienes mutan `state`.
- Cada entidad es una clase con `update(dt)`/`draw()` y flag `dead`; las listas se filtran con `.filter()` tras cada update. `dt` va en segundos y se limita a 0.05 s para evitar saltos al cambiar de pestaña.
- El espacio es toroidal: todo movimiento de entidades debe pasar por `wrap(v, W|H)` (las partículas no se envuelven, es intencional).

## Convenciones

- Comentarios, UI y README en español. Las secciones del archivo se delimitan con `// ── Nombre ──...`.
- El README menciona power-ups y "estrella fugaz", pero `game.js` no los implementa. Ante dudas, manda el código sobre el README.
