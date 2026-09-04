# 🟣 Bandit Level 20 → 21

## 🎯 Objetivo

En este nivel había un ejecutable llamado `suconnect`.

Este programa recibe un **puerto** como argumento, se conecta a `localhost` mediante ese puerto y espera recibir la contraseña del nivel actual.

Si la contraseña enviada es correcta, devuelve la contraseña necesaria para acceder al siguiente nivel.

---

## 🛠️ Resolución

### 1. Crear una sesión con `screen`

Primero creé una sesión utilizando:

```bash
screen
```

`screen` permite crear y mantener sesiones de terminal. Esto sirve para dejar un proceso ejecutándose mientras se trabaja desde otra terminal.

---

### 2. Crear un listener con Netcat

Dentro de la sesión de `screen` ejecuté:

```bash
nc -l -p 3000
```

Este comando deja a **Netcat (`nc`) escuchando conexiones entrantes** en el puerto `3000`.

---

### 3. Conectarse desde otra terminal

Abrí otra terminal y volví a conectarme como `bandit20`.

Desde esa terminal ejecuté:

```bash
./suconnect 3000
```

`./suconnect` ejecuta el programa que se encuentra en el directorio actual y `3000` indica el puerto al que debe conectarse.

Como Netcat ya estaba escuchando en ese mismo puerto, ambos programas pudieron establecer la conexión.

---

### 4. Enviar la contraseña

Una vez establecida la conexión, volví a la terminal donde estaba ejecutándose Netcat y envié la **contraseña del nivel actual**.

`suconnect` recibió la contraseña y la verificó.

Como era correcta, respondió enviando la contraseña correspondiente al siguiente nivel.

---

**Nivel completado: Bandit 20 → 21** ✅
