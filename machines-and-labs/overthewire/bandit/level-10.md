# 🔐 Bandit — Level 10 → Level 11

> **Objetivo:** encontrar la contraseña almacenada en `data.txt`, sabiendo que su contenido está **codificado en Base64**.

---

## 🧩 Resolución

Primero necesitaba leer el contenido de `data.txt` y después **decodificarlo de Base64**.

Utilicé:

```bash
cat data.txt | base64 -d
```

Al decodificar el contenido apareció el texto original, donde se encontraba la contraseña del siguiente nivel.

---

## 🔎 ¿Qué es Base64?

**Base64** es un método de **codificación** que permite representar datos utilizando caracteres de texto.

Por ejemplo:

```text
Texto original
     │
     ▼
   "Hola"
     │
     │ Base64
     ▼
  SG9sYQ==
```

Algo importante es que **Base64 no es cifrado**.

```text
┌──────────────────────────────────────────┐
│              Base64                      │
├──────────────────────────────────────────┤
│ ✓ Codifica datos                         │
│ ✓ Puede revertirse fácilmente            │
│ ✗ No protege información                 │
│ ✗ No es un método de cifrado             │
└──────────────────────────────────────────┘
```

---

## 🔧 ¿Por qué utilicé `-d`?

El comando:

```bash
base64
```

por defecto **codifica** información.

Pero en este nivel `data.txt` **ya estaba codificado**, así que necesitaba hacer el proceso contrario.

Para eso utilicé:

```bash
base64 -d
```

La opción:

```text
-d  →  decode
```

indica que queremos **decodificar Base64** y recuperar los datos originales.

---

## 🧠 Lo que aprendí

```text
┌─────────────────────────────────────────────┐
│ Base64      → método de codificación        │
│                                             │             
│ base64 -d   → decodifica datos              │
│                                             │
│                                             │
└─────────────────────────────────────────────┘
```

---

### 🏁 Level 10 completado ✓

---
