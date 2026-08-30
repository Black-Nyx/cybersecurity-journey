# 🔐 Bandit — Level 14 → Level 15

> **Objetivo:** obtener la contraseña del siguiente nivel enviando la contraseña del nivel actual al **puerto `30000` de `localhost`**.

---

## 🧩 Entendiendo la consigna

La consigna indicaba que debía enviar la contraseña de `bandit14` a:

```text
localhost:30000
```
---

## 🏠 ¿Qué significa `localhost`?

`localhost` es un nombre utilizado para referirse a **la propia máquina desde la que estamos ejecutando el comando**.

Normalmente se asocia con la dirección IPv4:

```text
127.0.0.1
```

Esta pertenece al rango de **loopback**.

El loopback permite que una computadora se comunique consigo misma sin que el tráfico tenga que salir hacia la red externa.

---

## 🚪 ¿Qué representa el puerto 30000?

Una dirección IP o un host nos permite identificar **la máquina**, mientras que un puerto permite identificar un **punto de comunicación utilizado por un servicio** dentro de esa máquina.

En este ejercicio:

```text
localhost
    ↓
¿Dónde? → esta misma máquina

30000
    ↓
¿A qué servicio? → al que está escuchando en ese puerto
```

---

## 📡 Utilizando Netcat

Para conectarme al servicio utilicé **Netcat (`nc`)**.

Netcat es una herramienta que permite **enviar y recibir datos a través de conexiones de red**.

La estructura básica para conectarse mediante TCP es:

```bash
nc HOST PUERTO
```

En este caso:

```bash
nc localhost 30000
```
---

## 🔑 Enviando la contraseña

Una vez establecida la conexión, introduje la contraseña correspondiente a `bandit14` y presioné **Enter**.


El servicio verificó el dato enviado y respondió con la contraseña necesaria para acceder al siguiente nivel.

---

## 📌 Lo que aprendí

`localhost` · `loopback` · `puertos` · `servicios`  · `nc`

- `localhost` hace referencia a la propia máquina.
- Loopback permite que una máquina se comunique consigo misma.
- Un puerto permite distinguir servicios o puntos de comunicación dentro de un host.
- `nc` permite establecer conexiones y enviar/recibir datos.
