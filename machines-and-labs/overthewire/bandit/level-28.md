## 🔐 Level 28 → Level 29

### 🎯 Objetivo

En este nivel trabajé con el **historial de cambios de un repositorio Git**.

Al revisar el archivo `README.md`, la contraseña no se encontraba visible en su versión actual, por lo que fue necesario investigar versiones anteriores del archivo mediante el historial de Git.

---

### 📜 `git log`

El comando:

```bash
git log
```

permite **ver el historial de commits de un repositorio Git**.

Un **commit** representa un cambio o conjunto de cambios que fue guardado en el historial del proyecto.

Al ejecutar `git log` se puede encontrar información como:

- El **hash** que identifica cada commit.
- El autor.
- La fecha.
- El mensaje que describe el cambio realizado.
  
<img width="1176" height="427" alt="image" src="https://github.com/user-attachments/assets/e4c3ea72-66bc-499e-b2e0-bf738eee2a6f" />


El **hash del commit** funciona como un identificador que permite hacer referencia a una versión concreta del repositorio.

---

### 🔎 `git show`

Después de revisar el historial, utilicé:

```bash
git show <el segundo hash>
```

`git show` permite **examinar un commit específico y ver los cambios que se realizaron en él**.

---

### 🧠 Lo que aprendí

- `git log` → permite consultar el historial de commits.
- Cada commit posee un **hash** que lo identifica.
- Los mensajes de los commits pueden dar información sobre los cambios realizados.
- `git show <hash>` → permite inspeccionar un commit y ver sus cambios.
- Aunque información haya sido modificada o eliminada de la versión actual de un archivo, puede continuar existiendo en el **historial de Git**.
