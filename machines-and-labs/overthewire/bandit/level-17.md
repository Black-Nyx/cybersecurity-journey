# 🔐 OverTheWire Bandit — Nivel 17 → 18

---

## 🎯 Objetivo

En el directorio principal hay dos archivos:

```bash
passwords.old
passwords.new
```

La contraseña para el siguiente nivel está en `passwords.new` y corresponde a **la única línea que cambió** respecto de `passwords.old`.

---

## 🔎 Comparar los archivos

Para comparar ambos archivos usé:

```bash
diff passwords.old passwords.new
```

`diff` compara los archivos línea por línea y muestra las diferencias.

La salida:

<img width="375" height="85" alt="image" src="https://github.com/user-attachments/assets/e78c04d2-53e8-485e-92fa-9117520d9261" />


---

## 📌 Cómo interpretar la salida

| Símbolo | Significado |
|---|---|
| `<` | Línea que pertenece al primer archivo: `passwords.old` |
| `>` | Línea que pertenece al segundo archivo: `passwords.new` |
| `c` | La línea fue modificada |
| `a` | Se agregó una línea |
| `d` | Se eliminó una línea |

Como la contraseña está en:

```text
passwords.new
```

la línea marcada con:

```text
>
```

es la nueva línea y, por lo tanto, la contraseña del siguiente nivel.

---

## 🧠 ¿Qué hace `diff`?

`diff` permite comparar dos archivos de texto y detectar qué líneas fueron:

- modificadas
- agregadas
- eliminadas

---

## 📌 Lo que aprendí

`diff` · comparación de archivos · diferencias entre líneas

- Comparar dos archivos desde la terminal.
- Interpretar los símbolos `<` y `>`.
- Identificar una línea modificada entre dos archivos.
- Entender que `diff` muestra las diferencias tomando como referencia el orden de los archivos que se le pasan.
