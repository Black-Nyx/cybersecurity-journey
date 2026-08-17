# 🔐 Bandit — Level 3 → Level 4

> Buscando un archivo oculto dentro de un directorio.

---

## 🎯 Objetivo

La contraseña para acceder al siguiente nivel se encuentra en un **archivo oculto** dentro del directorio `inhere`.

---

## 📂 Entrando al directorio

Primero cambié del directorio actual a `inhere`:

```bash
cd inhere
```

### ¿Qué hace `cd`?

`cd` (**change directory**) permite cambiar de un directorio a otro desde la terminal.

En este caso:

```text
cd inhere
```

me permitió entrar al directorio `inhere`, que es donde sabía que se encontraba el archivo oculto.

---

## 🔎 Buscando el archivo oculto

Una vez dentro de `inhere`, utilicé:

```bash
find .
```

### ¿Qué hace `find`?

`find` permite **buscar archivos y directorios**.

El `.` representa el **directorio actual**, por lo que:

```text
find .
```

le indica a `find` que realice la búsqueda comenzando desde el directorio en el que estoy.

Al ejecutarlo apareció el archivo oculto que estaba buscando.

<img width="380" height="73" alt="image" src="https://github.com/user-attachments/assets/47de325d-6c56-43e9-acdd-61d6382ee4cd" />

---

## 📄 Leyendo el archivo

Una vez que conocía el nombre del archivo, utilicé `cat` para mostrar su contenido:

<img width="524" height="29" alt="image" src="https://github.com/user-attachments/assets/358100ac-a9be-4780-a420-59d98011b26d" />


Al leerlo obtuve la contraseña necesaria para acceder al siguiente nivel.

---

## 📌 Lo que aprendí

`cd` · `find` · `.` · `Hidden files`

* Utilizar `cd` para cambiar de directorio.
* Utilizar `find` para buscar archivos y directorios.
* Que `.` puede utilizarse para hacer referencia al **directorio actual**.
* Utilizar `find .` para buscar contenido partiendo desde mi ubicación actual.
* Encontrar y leer un **archivo oculto**.

---

### ✅ Nivel completado
