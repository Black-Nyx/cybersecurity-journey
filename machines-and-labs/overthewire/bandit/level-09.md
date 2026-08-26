# 🔐 Bandit — Level 9 → Level 10

> **Objetivo:** encontrar la contraseña dentro de `data.txt`. Se encuentra entre una de las pocas cadenas legibles para humanos y está precedida por varios caracteres `=`.

---

## 🧩 Resolución

Utilicé el siguiente comando:

```bash
strings data.txt | grep "="
```

<img width="560" height="255" alt="image" src="https://github.com/user-attachments/assets/330d9222-a7c6-4f92-8ca5-f0b075affd54" />


El resultado mostró unas pocas cadenas que contenían `=` y entre ellas pude identificar la contraseña.

---

## 🔎 Nuevo comando: `strings`

`strings` busca y muestra **secuencias de caracteres legibles para humanos** dentro de un archivo.

```bash
strings archivo
```

Es especialmente útil cuando un archivo contiene muchos datos que no se pueden interpretar directamente como texto.


> 💡 **Importante:** `strings` no convierte mágicamente todo el archivo en texto. Busca dentro de sus datos las secuencias de caracteres que sí son imprimibles/legibles.

---

## 🔗 ¿Qué hice con el resultado?

La pista también indicaba que la contraseña estaba precedida por varios:

```text
=======
```

Por eso pasé el resultado de `strings` a `grep`.


---

## 🧠 Lo que aprendí

```text
┌─────────────────────────────────────────────┐
│ strings  → busca texto legible en archivos  │
│                                             │
               
└─────────────────────────────────────────────┘
```

---

### 🏁 Level 9 completado ✓
