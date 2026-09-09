# 🌐 OverTheWire Natas — Nivel 5

<img width="1392" height="495" alt="image" src="https://github.com/user-attachments/assets/b76cfdb6-d096-4a41-9d72-099ca3973639" />


## 🎯 Objetivo del nivel

Al ingresar a **Natas 5**, la página indicaba que no tenía permitido el acceso porque supuestamente **no estaba logueada**.

En este nivel practiqué cómo una aplicación puede utilizar una **cookie** para guardar información sobre el estado de una sesión y cómo esa información puede ser inspeccionada y modificada desde **Burp Suite**.

---

## 🔎 Analizando la solicitud con Burp Suite

Recargué la página y revisé la solicitud desde:

```text
Proxy → HTTP history
```

<img width="592" height="405" alt="image" src="https://github.com/user-attachments/assets/8208350c-a2ab-4a78-8a7f-397ca6d54c6b" />


Al observar los headers de la request encontré una cookie con este valor:

```http
Cookie: loggedin=0
```

El nombre `loggedin` hacía referencia al estado de inicio de sesión.

```text
loggedin=0
         ↑
     No logueado
```

---

## 🍪 ¿Qué es una cookie?

Una **cookie** es un pequeño dato que un sitio web guarda en el navegador y que puede enviarse posteriormente al servidor dentro de las solicitudes HTTP.

---

## 🛠️ Modificación con Repeater

Envié la solicitud desde **HTTP history** hacia **Repeater** para poder modificarla manualmente.

Cambié:

```http
Cookie: loggedin=0
```

por:

```http
Cookie: loggedin=1
```

Luego envié nuevamente la solicitud.

<img width="1248" height="672" alt="image" src="https://github.com/user-attachments/assets/45e5fab5-9ec3-477c-9884-6027c9bd137c" />


---

## 🧠 ¿Qué aprendí?

- Qué es una **cookie** y cómo puede formar parte de una solicitud HTTP.
- A observar cookies utilizando **Burp Suite**.
- A enviar una request a **Repeater** y modificarla manualmente.

---
