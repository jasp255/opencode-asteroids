---
description: Crea un git worktree en .worktrees/NN-nombre a partir de la descripción dada
agent: build
---

Worktrees existentes en este repositorio:

!`git worktree list`

TAREA: crear un nuevo worktree de git. No hagas NADA más de lo indicado aquí.

1. Argumento del usuario: "$ARGUMENTS"
   - Si está vacío, NO ejecutes ningún comando: responde pidiendo el nombre
     (ejemplo: /worktree arreglar colisiones) y detente.
2. Deriva el nombre base en kebab-case a partir del argumento:
   - minúsculas, sin tildes (á→a, ñ→n, ...), espacios/guiones bajos → guion,
     elimina caracteres que no sean letras, números o guion, colapsa guiones
     repetidos, sin guion inicial ni final.
   - Ejemplos: "Triple Shot" → triple-shot | "arreglar bug de colisiones" →
     arreglar-bug-de-colisiones | "¡Mi Feature!" → mi-feature
3. Determina el número a partir de la lista de worktrees de arriba: busca el
   mayor prefijo NN en entradas `.worktrees/NN-*` y súmale 1 con dos dígitos
   (01, 02, ...). Si no hay ninguno, usa 01.
4. Ejecuta EXACTAMENTE este comando desde el directorio actual, sin cambiar de
   directorio y sin crear la rama manualmente (git la crea con el mismo nombre):

   git worktree add .worktrees/<NN>-<nombre>

5. PROHIBIDO: editar o crear archivos, commit, push, u otros comandos git/shell.
   Termina confirmando en una sola línea el comando ejecutado y el resultado.
