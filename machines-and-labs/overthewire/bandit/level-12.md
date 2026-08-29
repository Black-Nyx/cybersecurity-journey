# 🔐 Bandit — Level 12 → Level 13

> **Objetivo:** encontrar la contraseña dentro de `data.txt`, que contiene un **hex dump de un archivo comprimido varias veces**.

---

## 🧩 Preparando el entorno

La consigna recomendaba crear un **directorio temporal dentro de `/tmp`** para trabajar con los archivos sin modificar el original.


```bash
mktemp -d
```
<img width="341" height="80" alt="image" src="https://github.com/user-attachments/assets/5326d9b6-35e4-40cb-b568-9a1e251b350c" />

Copié `data.txt` para trabajar sobre una copia:

<img width="537" height="31" alt="image" src="https://github.com/user-attachments/assets/3df364ce-b893-4981-85b0-c0d164332f22" />


Después entré al directorio y renombré el archivo:

```bash
mv data.txt data
```

---

## 🔢 Revirtiendo el hex dump

Un **hex dump** es una representación de los bytes de un archivo utilizando hexadecimal.

En este caso, el archivo ya había sido comprimido varias veces y luego convertido en un hex dump.

Para reconstruir los datos originales utilicé:

```bash
xxd -r data > data.bin
```

- `xxd` → herramienta para trabajar con representaciones hexadecimales.
- `-r` → **reverse**, revierte el hex dump.
- `>` → guarda los bytes reconstruidos en otro archivo.

Después utilicé:

```bash
file data.bin
```

para descubrir qué tipo de archivo era realmente.

---

## 📦 Descomprimiendo las capas

El archivo había sido comprimido repetidamente utilizando distintos formatos.

| Formato | ¿Qué es? | ¿Cómo lo utilicé? |
|---|---|---|
| `gzip` | Método de compresión de archivos. Suele usar `.gz`. | `gzip -d archivo.gz` |
| `bzip2` | Otro método de compresión. Suele usar `.bz2`. | `bzip2 -d archivo.bz2` |
| `tar` | Formato que agrupa uno o varios archivos en un archivo `.tar`. | `tar -xf archivo.tar` |

En `gzip` y `bzip2`:

```text
-d → decompress
```

Es decir, indica que quiero **descomprimir**.

En TAR utilicé:

```bash
tar -xf archivo.tar
```

- `-x` → **extract**, extraer.
- `-f` → indica el archivo TAR que quiero utilizar.

---

## 🔎 Proceso que seguí

Después de cada capa utilizaba `file` para descubrir qué formato tenía el nuevo archivo:

<img width="615" height="108" alt="image" src="https://github.com/user-attachments/assets/e8c5c448-7230-44d1-979a-491e9f58a7f9" />


```text
Hex dump
   ↓ xxd -r
gzip
   ↓ gzip -d
bzip2
   ↓ bzip2 -d
gzip
   ↓ gzip -d
tar
   ↓ tar -xf
tar / bzip2 / gzip...
   ↓
ASCII text
```

También fui utilizando `mv` para colocar extensiones como `.gz`, `.bz2` o `.tar` cuando era necesario.

<img width="567" height="20" alt="image" src="https://github.com/user-attachments/assets/e085be80-06a2-45e8-951d-627d47ec14c6" />

Finalmente:

<img width="587" height="110" alt="image" src="https://github.com/user-attachments/assets/93ab1437-2ee3-4244-b955-840b50539386" />

```bash
file data8
```

me indicó:

```text
data8: ASCII text
```

Como ya era texto legible, utilicé:

```bash
cat data8
```

y encontré la contraseña.

---

## 📌 Lo que aprendí

`Hex dump` · `xxd` · `file` · `gzip` · `bzip2` · `tar` · `mktemp` · `cp` · `mv`

- Revertir un hex dump con `xxd -r`.
- Utilizar `file` para identificar el formato real de un archivo.
- Descomprimir `gzip` y `bzip2` utilizando `-d`.
- Extraer archivos TAR con `tar -xf`.
- Trabajar sobre una copia dentro de un directorio temporal.
- Identificar cada capa antes de decidir qué herramienta utilizar.

---

### 🏁 Level 12 completado ✓
