## 🔐 Level 31 → Level 32

### 🎯 Objetivo

En este nivel tuve que crear un archivo dentro de un repositorio Git, agregarlo al control de versiones, crear un commit y enviar el cambio al repositorio remoto.

Al leer el archivo:

```bash
cat README.md
```

encontré las instrucciones que debía seguir:

```text
File name: key.txt
Content: May I come in?
Branch: master
```
---

### 📄 Crear el archivo

Creé `key.txt` y escribí el contenido solicitado:

```bash
echo 'May I come in?' > key.txt
```

---

### ➕ `git add`

Para indicarle a Git que quería incluir `key.txt` en el próximo commit utilicé:

```bash
git add -f key.txt
```

`git add` prepara un archivo para que sus cambios puedan incluirse en el próximo commit.

En este caso utilicé:

```text
-f → force
```

porque el archivo estaba configurado para ser ignorado por Git. Esta opción permite agregarlo de todas formas.

---

### 💾 `git commit`

Después intenté guardar el cambio en el historial:

```bash
git commit -m "Add key.txt"
```

Un **commit** registra los cambios preparados en el historial del repositorio.

En este caso Git no me permitió crear inicialmente el commit porque no tenía configurada una identidad de autor.

---

### 👤 `git config`

Git necesita un nombre y un correo para identificar al autor de los commits.

Los configuré únicamente para este repositorio:

```bash
git config user.name "BlackNyx"
git config user.email "BlackNyx@example.com"
```

Después pude volver a ejecutar:

```bash
git commit -m "Add key.txt"
```

y registrar correctamente el cambio.

---

### ⬆️ `git push`

Finalmente envié el commit al repositorio remoto:

```bash
git push origin master
```

`git push` permite **enviar los commits realizados localmente hacia un repositorio remoto**.


- `origin` → nombre que Git utiliza normalmente para identificar el repositorio remoto del que se realizó el clone.
- `master` → rama que debía enviar según las instrucciones del nivel.

Al enviar el cambio, el servidor procesó el archivo y devolvió la información necesaria para avanzar al siguiente nivel.

---

### 🧠 Lo que aprendí

- `git add archivo` → preparar un archivo para el próximo commit.
- `git add -f archivo` → agregarlo incluso si Git lo está ignorando.
- `git commit -m "mensaje"` → registrar los cambios preparados en el historial.
- `git config user.name` → configurar el nombre del autor.
- `git config user.email` → configurar el correo del autor.
- `git push origin master` → enviar los commits locales a la rama `master` del repositorio remoto.
