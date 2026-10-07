# Asteroids

Clon del clásico arcade **Asteroids** implementado en canvas HTML5 puro, sin dependencias ni bundler.

## Descripción

Nave espacial en un campo de asteroides con envolvimiento de bordes (el espacio es toroidal). Destruye asteroides para sumar puntos: los grandes se parten en medianos, los medianos en pequeños. Incluye power-ups especiales y tipos de asteroides únicos como la estrella fugaz.

## Tecnologías

- **HTML5 Canvas** — renderizado 2D
- **JavaScript (ES6+)** — lógica del juego en un solo archivo `game.js`
- Sin frameworks, sin bundler, sin dependencias

## Cómo correr

Abre `index.html` directamente en el navegador (doble clic), o usa un servidor local:

```bash
npx serve .
```

Luego visita `http://localhost:3000`.

## Controles

| Tecla     | Acción          |
| --------- | --------------- |
| `←` `→`   | Rotar nave      |
| `↑`       | Propulsar       |
| `Espacio` | Disparar        |
| `C`       | Cambiar de skin |

## Puntuación

| Asteroide | Puntos |
| --------- | ------ |
| Grande    | 20     |
| Mediano   | 50     |
| Pequeño   | 100    |

## Características

- 3 vidas con invencibilidad temporal al reaparecer (parpadeo)
- 4 skins de nave seleccionables con la tecla `C` (CLÁSICA, DELTA, INTERCEPTOR, EXPLORER); cambian silueta, color de trazo y llama; el icono de vidas del HUD usa la skin activa y la elección se guarda en `localStorage`
- Asteroides se parten en fragmentos más pequeños al ser destruidos
- Partículas de explosión al destruir asteroides
- Power-up «Velocidad»: al destruir un asteroide puede aparecer uno (15% de probabilidad); al recogerlo, la propulsión de la nave se duplica durante 5 segundos (se muestra barra y tiempo restante en el HUD)
- Power-up «Triple»: misma probabilidad de aparición que «Velocidad» (el tipo se elige al azar); al recogerlo, la nave dispara 3 balas paralelas durante 5 segundos (se muestra barra magenta y tiempo restante en el HUD)
- Estrellas fugaces: asteroides pequeños y muy rápidos que aparecen de vez en cuando y desaparecen al cabo de unos segundos; otorgan 250 puntos al destruirlos
