# 🔐 Bandit — Level 7 → Level 8

> Buscando información específica dentro de un archivo con `grep`.

---

## 🎯 Objetivo

La contraseña para el siguiente nivel se encuentra en el archivo **`data.txt`**, junto a la palabra:

```text
millionth
```

---

## 🔎 Buscando con `grep`

Para realizar la búsqueda utilicé:

```bash
grep "millionth" data.txt
```

### ¿Qué es `grep`?

`grep` es un comando que permite **buscar un patrón de texto** dentro de un archivo y mostrar las líneas que contienen una coincidencia.

La estructura que utilicé fue:

```bash
grep "patrón" archivo
```

---

## 💡 ¿Por qué utilicé `grep`?

`data.txt` contenía una gran cantidad de información, por lo que revisar el archivo línea por línea no era práctico.

Como el desafío indicaba que la contraseña estaba **junto a `millionth`**, podía buscar directamente la línea que contenía esa palabra.

De esta forma, `grep` filtró el contenido y mostró únicamente la línea relevante.

---

## 📌 Lo que aprendí

**Nuevo comando:** `grep`

---

### ✅ Nivel completado

