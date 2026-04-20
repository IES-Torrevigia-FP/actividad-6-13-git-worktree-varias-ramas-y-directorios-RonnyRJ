# 🧠 Reflexión: Git Worktree

### 1. Ventajas de los worktrees
Desde mi punto de vista, la mayor ventaja de **`git worktree`** es la capacidad de mantener el contexto. 

*   **Frente a cambiar de rama (`checkout`):** No tienes que andar haciendo `stash` de tus cambios a medio terminar ni preocuparte por archivos que no se pueden mover de rama. Cada tarea vive en su propio espacio.
*   **Frente a clonar varias veces:** Ahorras muchísimo espacio en disco y tiempo de red, ya que todos los worktrees comparten la misma carpeta `.git`. Además, los cambios que haces en un worktree (commits, nuevas ramas) están disponibles instantáneamente en los demás.

### 2. Situaciones reales de uso
*   **Revisión de un Pull Request urgente:** Estás en medio de una funcionalidad compleja y un compañero te pide que revises su código. En lugar de ensuciar tu rama actual, abres un worktree en una carpeta temporal, revisas el código, lo pruebas y lo cierras sin haber tocado tu trabajo principal.
*   **Prueba de Hotfixes:** Si surge un bug crítico en producción mientras trabajas en la siguiente versión, puedes abrir un worktree de la rama `main` (o `master`), aplicar el fix, subirlo y seguir con lo tuyo en el directorio original como si nada hubiera pasado.

### 3. Buenas prácticas
*   **Nomenclatura clara:** Usar un prefijo como `wt-` o `fix-` para las carpetas de los worktrees ayuda a identificarlas rápidamente en el explorador de archivos.
*   **Ubicación consistente:** Mantener los worktrees en un nivel superior al repositorio principal (como hicimos con `../wt-nombre`) evita que Git intente rastrear un repositorio dentro de otro si no se configura bien el `.gitignore`.
*   **Limpieza periódica:** Acostumbrarse a usar `git worktree remove` en lugar de borrar la carpeta a mano, y ejecutar `git worktree prune` de vez en cuando para mantener la casa limpia.
