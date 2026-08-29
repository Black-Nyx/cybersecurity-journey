# 🔐 Bandit Level 11 → Level 12

## 🎯 Objetivo

La contraseña para el siguiente nivel se encuentra en el archivo `data.txt`, donde todas las letras minúsculas (`a-z`) y mayúsculas (`A-Z`) fueron **rotadas 13 posiciones**.

---

## 🔎 Solución

El contenido está codificado utilizando **ROT13**, un sistema que reemplaza cada letra por otra situada 13 posiciones después en el alfabeto.

Para decodificarlo utilicé:

```bash
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

### 🧩 ¿Qué hace el comando?

| Parte | Función |
|---|---|
| `cat data.txt` | Muestra el contenido del archivo |
| `\|` | Envía la salida de `cat` al siguiente comando |
| `tr` | Traduce o reemplaza caracteres |
| `'A-Za-z'` | Selecciona todas las letras mayúsculas y minúsculas |
| `'N-ZA-Mn-za-m'` | Indica por qué letras deben reemplazarse aplicando ROT13 |

---

## 🔄 ¿Por qué funciona ROT13?

El alfabeto tiene 26 letras y ROT13 las desplaza **13 posiciones**.

Por eso, aplicar ROT13 nuevamente sobre un texto que ya fue codificado permite recuperar el original:

```text
hola → ROT13 → ubyn
ubyn → ROT13 → hola
```

Al ejecutar el comando pude decodificar `data.txt` y obtener la contraseña para el siguiente nivel.
