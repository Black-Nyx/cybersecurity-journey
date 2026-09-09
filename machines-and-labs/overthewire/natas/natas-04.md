# 🌐 OverTheWire Natas — Nivel 4

## 🎯 Objetivo del nivel

En este nivel, la página no permitía acceder al contenido porque esperaba que la visita proviniera de una página específica.

Al acceder normalmente a **Natas4**, el servidor indicaba que el usuario debía llegar desde **Natas5**.

La idea del nivel fue entender que una aplicación web puede tomar decisiones basándose en información enviada dentro de una **solicitud HTTP**, en este caso el header `Referer`.

---

## 🧪 Resolución con Burp Suite

Para analizar la solicitud utilicé **Burp Suite**.

Primero abrí el nivel y recargué la página con Burp Suite funcionando como proxy.

Después fui a:

```text
Proxy → HTTP history
```

Ahí pude observar la solicitud HTTP que el navegador había enviado al servidor.

Entre los headers encontré:

```http
Referer: http://natas4.natas.labs.overthewire.org/
```

---

## 🔎 ¿Qué es `Referer`?

`Referer` es un **header HTTP** que puede indicar desde qué página llegó una solicitud.

Por ejemplo:

```http
Referer: http://natas4.natas.labs.overthewire.org/
```

---

## 🛠️ Modificación de la solicitud

Desde **HTTP history**, envié la solicitud a **Repeater**.

En Repeater pude modificar manualmente la solicitud antes de volver a enviarla.

Cambié el valor de:

```http
Referer: http://natas4.natas.labs.overthewire.org/
```

por:

```http
Referer: http://natas5.natas.labs.overthewire.org/
```

Después envié nuevamente la solicitud.

---

## 📩 Resultado

Al modificar el header `Referer`, el servidor interpretó que la solicitud provenía de la página que esperaba.

En la **Response** de Burp Repeater apareció entonces la información necesaria para completar el nivel.


---

## 🧠 ¿Qué aprendí?

- A utilizar **HTTP history** de Burp Suite para observar las solicitudes realizadas por el navegador.
- Qué función cumple el header `Referer`.
- A enviar una solicitud desde **HTTP history** hacia **Repeater**.
- A modificar manualmente una solicitud HTTP con Burp Repeater.
- A volver a enviar una request y analizar su **response**.

---

## 🔐 Relación con seguridad web

Este nivel me ayudó a entender algo importante para seguir aprendiendo seguridad web: **lo que envía el navegador puede inspeccionarse y, en determinados casos, modificarse antes de llegar al servidor**.

```

Esto sirve como base para aprender posteriormente cómo analizar el comportamiento de aplicaciones web y comprobar si el servidor confía incorrectamente en información controlable por el cliente.
