## 🔐 Level 27 → Level 28

### 🎯 Objetivo

En este nivel trabajé por primera vez con un **repositorio Git remoto**.

El repositorio estaba alojado en un servidor y era accesible mediante **SSH** a través de un puerto específico. El objetivo era clonarlo en mi máquina local y revisar su contenido para encontrar la información necesaria para avanzar al siguiente nivel.

---

### 🔧 Git

**Git** es un sistema de control de versiones que permite guardar, organizar y seguir los cambios realizados en archivos y proyectos a lo largo del tiempo.

Los proyectos administrados con Git se denominan **repositorios**.

---

### 📥 `git clone`

El comando:

```bash
git clone <URL>
```

permite **copiar un repositorio existente a nuestra máquina local**.

En este nivel, el repositorio estaba en un servidor remoto y se accedía mediante SSH:

```bash
git clone ssh://usuario@servidor:puerto/ruta/del/repositorio
```
---

### 🧪 Resolución

Después de clonar el repositorio, comprobé los archivos y directorios disponibles:

```bash
ls
```

Apareció el directorio del repositorio:

```text
repo
```

Entré en él:

```bash
cd repo
```

Revisé su contenido:

```bash
ls
```

Encontré un archivo `README`, por lo que leí su contenido:

```bash
cat README
```

Dentro del archivo encontré la información necesaria para acceder al siguiente nivel.

---

### 🧠 Lo que aprendí

- Qué es **Git** y para qué se utiliza.
- Qué es un **repositorio Git**.
- Cómo utilizar `git clone` para copiar un repositorio remoto.
