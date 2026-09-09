# 🌐 OverTheWire Natas — Nivel 6

<img width="1235" height="490" alt="image" src="https://github.com/user-attachments/assets/41ee7c3d-9bfa-402e-bfa5-f36756f169e3" />


## 🎯 Objetivo del nivel

En **Natas 6**, la página mostraba un formulario donde tenía que ingresar un **secreto** para poder avanzar.

También aparecía una opción para visualizar el **código fuente** utilizado por la página, así que decidí revisarlo.
---

## 🔎 Analizando el código fuente

<img width="1346" height="653" alt="image" src="https://github.com/user-attachments/assets/8c00f7cd-07b2-42da-9776-ac2d1d5aa6be" />


## 📂 Investigando la ruta

La ruta que aparecía en el código era:

```text
includes/secret.inc
```

Probé acceder directamente a esa ruta agregándola a la URL del nivel.

<img width="610" height="211" alt="image" src="https://github.com/user-attachments/assets/f33db079-28af-45f8-a031-1ec678b5050b" />

Al acceder, pude encontrar el valor del **secreto**.

---

## 🔑 Utilizando el secreto

Después copié el secreto encontrado y volví al formulario de Natas 6.

Lo introduje en el campo correspondiente y envié el formulario.

Al enviar el secreto correcto, la página mostró la información necesaria para completar el nivel.

---
