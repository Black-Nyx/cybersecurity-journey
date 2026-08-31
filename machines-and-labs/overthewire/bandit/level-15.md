# 🔐 Bandit — Level 15 → Level 16

> **Objetivo:** obtener la contraseña del siguiente nivel enviando la contraseña de `bandit15` al **puerto 30001 de localhost utilizando SSL/TLS**.

---

## 🧩 Entendiendo la consigna

En el nivel anterior había que enviar una contraseña a un puerto de `localhost`.

La diferencia importante de este nivel es que la consigna especifica:

```text
utilizando cifrado SSL/TLS
```

Por lo tanto, esta vez necesitaba establecer una **conexión TLS** con el servicio antes de enviar la contraseña.

Los datos proporcionados eran:

| Dato | Valor |
|---|---|
| Host | `localhost` |
| Puerto | `30001` |
| Tipo de conexión | SSL/TLS |
| Dato a enviar | Contraseña de `bandit15` |

---

## 🔒 ¿Qué es TLS?

TLS permite establecer una comunicación protegida entre un cliente y un servidor.

---

## 🛠️ Utilizando OpenSSL

Para conectarme al servicio TLS utilicé:

```bash
openssl s_client
```

`s_client` permite utilizar OpenSSL como un **cliente TLS**.

Su estructura básica es:

```bash
openssl s_client -connect HOST:PUERTO
```

Por lo tanto, utilicé:

```bash
openssl s_client -connect localhost:30001
```

### Partes del comando

| Parte | Función |
|---|---|
| `openssl` | Ejecuta OpenSSL |
| `s_client` | Actúa como cliente TLS |
| `-connect` | Indica el servidor y puerto al que conectarse |
| `localhost:30001` | Host y puerto del servicio |


---

## 🔑 Enviando la contraseña

Una vez establecida la conexión TLS, el servicio quedó esperando datos.

Introduje la contraseña correspondiente a `bandit15` y presioné **Enter**.


---


## 📌 Lo que aprendí

`TLS` · `OpenSSL` · `s_client` · 

- TLS permite establecer una comunicación protegida.
- `openssl s_client` permite conectarse directamente a servicios que utilizan TLS.
- Su estructura básica es `openssl s_client -connect HOST:PUERTO`.
- OpenSSL muestra información sobre la conexión TLS y el certificado presentado por el servidor.
