## 🔐 Level 29 → Level 30

### 🎯 Objetivo

En este nivel aprendí a investigar las **ramas de un repositorio Git**.

La información que buscaba no se encontraba en la rama principal (`master`), por lo que fue necesario revisar qué otras ramas existían y cambiar a una de ellas.

---

### 🌿 `git branch -a`

El comando:

```bash
git branch -a
```

permite **mostrar todas las ramas disponibles**, incluyendo las ramas locales y las ramas del repositorio remoto.


Diferencia:

```bash
git branch
```

Muestra principalmente las ramas locales.

---

### 🔄 `git switch`

El comando:

```bash
git switch <rama>
```

permite **cambiar de una rama a otra** dentro del repositorio.

<img width="456" height="152" alt="image" src="https://github.com/user-attachments/assets/90f978a2-25b8-4bfc-ad76-13ec37ee3be2" />


En este nivel, después de cambiar a `dev`, revisé nuevamente los archivos:

```bash
ls
```

y encontré:

```text
code
README.md
```

Luego revisé el `README.md`:

```bash
cat README.md
```

y encontré la información necesaria para avanzar al siguiente nivel.

---

### 🧠 Lo que aprendí

- Un repositorio Git puede tener **varias ramas**.
- Las distintas ramas pueden contener versiones o cambios diferentes del proyecto.
- `git branch -a` → muestra las ramas locales y remotas disponibles.
- `git switch <rama>` → permite cambiar a otra rama.
