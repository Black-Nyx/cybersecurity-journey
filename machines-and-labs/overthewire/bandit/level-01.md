# 🔐 Bandit — Level 1 → Level 2

> Trabajando con un archivo cuyo nombre comienza con un guion (`-`).

---

## 🎯 Objetivo

La contraseña para acceder al siguiente nivel se encuentra en un archivo llamado `-`, ubicado en el directorio **home**.

---

## 📂 Buscando el archivo

Primero utilicé `ls` para ver qué archivos y directorios había en la ubicación actual.

```bash
ls
```

### ¿Qué hace `ls`?

`ls` permite **listar el contenido de un directorio**.

En este caso lo utilicé para comprobar qué archivos había disponibles:

```text
bandit1@bandit:~$ ls
-
```

El resultado mostró un archivo llamado únicamente:

```text
-
```

---

## 🔎 Dashed name

Un **dashed name** es un nombre que comienza con un guion (`-`).

Esto puede generar problemas porque muchos comandos de Linux interpretan los elementos que comienzan con `-` como **opciones del comando** y no como nombres de archivos.

> 💡 Para evitar esa interpretación puedo indicar la ruta del archivo utilizando `./`.

`./` hace referencia al **directorio actual**, por lo que:

```text
./-
```
---

## 💻 Leyendo el archivo

Como ya había aprendido a utilizar `cat` para mostrar el contenido de un archivo, ejecuté:

```bash
cat ./-
```

El comando mostró en la terminal la contraseña necesaria para continuar al siguiente nivel.

```text
bandit1@bandit:~$ cat ./-
[CONTRASEÑA OCULTA]
```

> 🔒 **Contraseña omitida para evitar spoilers.**

---

## 📌 Lo que aprendí

`ls` · `Dashed names` · `./` · `cat`

* Utilizar `ls` para listar los archivos y directorios.
* Qué es un **dashed name** y por qué puede generar ambigüedad en la terminal.
* Utilizar `./` para hacer referencia a un archivo del directorio actual.
* Leer un archivo llamado `-` mediante `cat ./-`.

---

### ✅ Nivel completado

