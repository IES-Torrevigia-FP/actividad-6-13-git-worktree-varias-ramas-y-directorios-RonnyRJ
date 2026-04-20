# Reflexión – Actividad 6.13

## 1. Ventajas de `git worktree`
- **Frente a cambiar de rama (`checkout`)**: No es necesario hacer `stash` de los cambios actuales ni preocuparse por archivos no commiteados que puedan entrar en conflicto. Además, permite ejecutar el código de dos ramas distintas al mismo tiempo (por ejemplo, para comparar comportamientos).
- **Frente a clonar varias veces**: Se ahorra mucho espacio en disco y ancho de banda, ya que todos los worktrees comparten la misma base de datos de objetos (`.git`). Además, los cambios realizados en un worktree (como un nuevo commit) son visibles instantáneamente para el resto sin necesidad de hacer `push`/`pull`.

## 2. Situaciones reales de uso
1. **Revisión de Code Reviews (PRs)**: Mientras estás en mitad de una tarea compleja en tu rama, te piden revisar el código de un compañero. En lugar de interrumpir tu flujo, creas un worktree para la rama del compañero, haces la revisión (pruebas, ejecución), y cuando terminas simplemente lo borras, sin haber tocado tu directorio principal.
2. **Corrección de Hotfixes urgentes**: Si surge un bug crítico en producción mientras trabajas en una funcionalidad de larga duración, puedes abrir un worktree para la rama `main` o `production`, aplicar el parche, subirlo, y seguir trabajando en tu feature en el directorio original sin distracciones.

## 3. Buenas prácticas
- **Nombramiento**: Usar un prefijo claro para los directorios de worktrees (como `wt-` o `worktree-`) y situarlos fuera del repositorio principal para evitar que git intente trackearlos por error (aunque git suele ignorarlos si están fuera, es más limpio).
- **Limpieza**: Ejecutar periódicamente `git worktree list` para ver qué tareas tenemos "colgadas" y usar `git worktree remove` para liberar espacio.
- **Ubicación**: Mantener los worktrees en una carpeta dedicada (ej. `~/dev/project-worktrees/`) para que sea fácil identificarlos y gestionarlos globalmente.
