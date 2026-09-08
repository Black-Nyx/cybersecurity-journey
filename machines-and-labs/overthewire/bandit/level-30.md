## 🔐 Level 30 → Level 31

### 🎯 Objetivo

En este nivel aprendí a investigar los **tags (etiquetas) de Git**.

Después de clonar el repositorio, encontré un archivo `README.md`, pero al revisar su contenido no encontré la información necesaria para avanzar.

---

### 🏷️ `git tag`

Como la información no estaba visible directamente en los archivos del repositorio, revisé si Git tenía algún **tag**:

```bash
git tag
```

Un **tag** es una etiqueta o nombre que Git utiliza para **marcar e identificar un objeto o punto específico dentro del repositorio**. 

En este caso apareció:

```text
secret
```

Esto indicaba que existía un tag llamado `secret` que podía contener o apuntar a información interesante.

---

### 🔎 `git show <tag>`

Para inspeccionar el tag utilicé:

```bash
git show secret
```
 Al inspeccionar `secret`, encontré la información necesaria para avanzar al siguiente nivel.

---

### 🧠 Lo que aprendí

- Un **tag** es una etiqueta utilizada para identificar un objeto o punto concreto del repositorio.
- `git tag` → muestra los tags existentes.
