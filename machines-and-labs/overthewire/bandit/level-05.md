# 🔐 Bandit — Level 5 → Level 6

> Buscando un archivo a partir de sus características.

---

## 🎯 Objetivo

La contraseña se encuentra en algún lugar dentro del directorio `inhere`.

Esta vez no conozco el nombre ni la ubicación exacta del archivo, pero Bandit proporciona algunas características para identificarlo:

| 🔎 Propiedad  | Valor                |
| :------------ | :------------------- |
| 📄 Tipo       | Archivo              |
| 👁️ Contenido | Legible para humanos |
| 📦 Tamaño     | `1033 bytes`         |
| 🚫 Ejecución  | No ejecutable        |

---

## 📂 Entrando al directorio

Primero entré en `inhere`:

```bash
cd inhere
```

---

## 🔎 Buscando por tamaño

Como sabía que el archivo tenía exactamente **1033 bytes**, utilicé `find` junto con la opción `-size`:

```bash
find . -size 1033c
```

### ¿Qué significa?

| Parte   | Función                                         |
| :------ | :---------------------------------------------- |
| `find`  | Busca archivos y directorios                    |
| `.`     | Comienza la búsqueda desde el directorio actual |
| `-size` | Filtra los resultados según su tamaño           |
| `1033c` | Busca elementos de exactamente `1033 bytes`     |

> 💡 En `find`, el sufijo `c` representa bytes.

El resultado fue:

```text
./maybehere07/.file2
```

<img width="437" height="46" alt="image" src="https://github.com/user-attachments/assets/6ca4656f-79de-41b3-bca1-b27b0513711e" />


---

## 🧩 Completando los filtros

Aunque buscar solamente por tamaño me llevó al archivo correcto, el nivel también indicaba que debía ser un **archivo no ejecutable**.

Una búsqueda más específica sería:

```bash
find . -type f -size 1033c ! -executable
```

| Filtro          | Significado                         |
| :-------------- | :---------------------------------- |
| `-type f`       | Busca únicamente archivos regulares |
| `-size 1033c`   | Tamaño exacto de `1033 bytes`       |
| `! -executable` | Excluye los archivos ejecutables    |

El símbolo `!` funciona como una negación, por lo que:

```text
! -executable
```

significa **“que no sea ejecutable”**.

---

## 👁️ Comprobando si es legible

La condición *human-readable* se refiere a que el contenido pueda interpretarse como texto.

Para comprobar el tipo del archivo puedo utilizar:

```bash
file ./maybehere07/.file2
```

`file` analiza el contenido del archivo e indica qué tipo de datos contiene.

Si el resultado indica texto, como `ASCII text`, significa que su contenido puede ser leído directamente.

---

## 🔑 Leyendo el archivo

Una vez identificado el archivo, utilicé `cat`:

```bash
cat ./maybehere07/.file2
```

El contenido mostró la contraseña necesaria para acceder al siguiente nivel.


---

## 📌 Lo que aprendí

`find` · `-size` · `-type f` · `! -executable` · `file`

* Utilizar `find` con condiciones para reducir una búsqueda.
* Buscar un archivo por su tamaño exacto mediante `-size`.
* Que `1033c` representa exactamente `1033 bytes`.
* Utilizar `-type f` para limitar la búsqueda a archivos.
* Utilizar `! -executable` para excluir archivos ejecutables.
* Utilizar `file` para comprobar si el contenido de un archivo es texto.

---

### ✅ Nivel completado
