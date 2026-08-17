# 🔐 Bandit — Level 4 → Level 5

> Identificando el único archivo legible para humanos.

---

## 🎯 Objetivo

La contraseña para acceder al siguiente nivel se encuentra en el único archivo **legible para humanos** dentro del directorio `inhere`.

| 📌 Dato           | Valor                                    |
| :---------------- | :--------------------------------------- |
| 👤 Usuario actual | `bandit4`                                |
| 📁 Directorio     | `inhere`                                 |
| 📄 Archivo        | Desconocido                              |
| 🔎 Pista          | Es el único archivo legible para humanos |
| 🎯 Objetivo       | Encontrar la contraseña de `bandit5`     |

---

## 📂 Entrando al directorio

Primero entré al directorio `inhere`:

```bash id="30fhqw"
cd inhere
```
---

## 🔎 Buscando los archivos

Una vez dentro utilicé:

```bash id="y36j1v"
find .
```

| Parte  | Significado                  |
| :----- | :--------------------------- |
| `find` | Busca archivos y directorios |
| `.`    | Directorio actual            |

Al ejecutarlo pude ver los archivos disponibles dentro de `inhere`.

<img width="458" height="262" alt="image" src="https://github.com/user-attachments/assets/a9bb3f7f-38ef-466b-84f2-43d6b62ceb52" />


---

## 🔬 Identificando el tipo de archivo

Como necesitaba encontrar cuál de ellos era **legible para humanos**, utilicé el comando `file`:

```bash id="9gftbe"
file ./*
```

### ¿Qué hace `file`?

`file` permite identificar el **tipo de contenido** de un archivo.

En este comando también utilicé:

```text id="vgnl55"
./*
```

* `./` → hace referencia al directorio actual.
* `*` → es un comodín que representa todos los nombres que coincidan en esa ubicación.

Por lo tanto:

```bash id="esq8jj"
file ./*
```

analiza los archivos del directorio actual e indica qué tipo de contenido tiene cada uno.

<img width="583" height="244" alt="image" src="https://github.com/user-attachments/assets/794e59a9-109f-40f8-96bf-fb21fd8a6a2b" />

---

## 📄 ASCII text

Entre los resultados observé que `-file07` aparecía identificado como:

```text id="v4fz39"
ASCII text
```

**ASCII text** indica que el archivo contiene texto representado mediante caracteres ASCII, por lo que su contenido puede ser leído como texto.

Esto lo diferenciaba de los demás archivos y coincidía con la pista de que la contraseña estaba almacenada en un archivo **legible para humanos**.

---

## 🔑 Leyendo el archivo

Una vez identificado `-file07`, utilicé `cat` para mostrar su contenido:

```bash id="6q5c4b"
cat ./-file07
```

---

## 📌 Lo que aprendí

`find` · `file` · `*` · `ASCII text` · `./`

* Utilizar `find .` para buscar desde el directorio actual.
* Utilizar `file` para identificar el tipo de contenido de un archivo.
* Utilizar `*` como comodín para aplicar un comando a los archivos de una ubicación.
* Reconocer `ASCII text` como contenido de texto legible.

---

### ✅ Nivel completado

