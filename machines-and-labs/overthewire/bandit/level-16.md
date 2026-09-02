# 🧩 Bandit Level 16 → 17

## 🎯 Objetivo

La contraseña del nivel actual debía enviarse a un servicio ubicado en `localhost`, dentro del rango de puertos:

```text
31000-32000
```

La consigna indicaba que había que:

- Encontrar qué puertos estaban escuchando.
- Identificar cuáles utilizaban SSL/TLS.
- Conectarse al servicio correcto.
- Obtener las credenciales del siguiente nivel.

---

## 🔎 1. Buscar puertos abiertos

Primero utilicé Nmap para escanear el rango indicado:

```bash
nmap -sT -p 31000-32000 localhost
```

### Comandos nuevos

`-sT` realiza un **TCP Connect Scan**.

Esto significa que Nmap intenta establecer una conexión TCP completa con cada puerto para comprobar si está abierto.

`-p` permite especificar los puertos que quiero escanear:

```bash
-p 31000-32000
```

El escaneo encontró 5 puertos abiertos:

```text
31046
31518
31691
31790
31960
```

---

## 🔬 2. Detectar los servicios

Como todavía no sabía qué servicio estaba funcionando detrás de cada puerto, utilicé:

```bash
nmap -sV -p 31046,31518,31691,31790,31960 localhost
```

`-sV` intenta identificar el **servicio o protocolo** que responde detrás de cada puerto.

El resultado permitió distinguir los servicios:

```text
31046/tcp  open  echo
31518/tcp  open  ssl/echo
31691/tcp  open  echo
31790/tcp  open  ssl/unknown
31960/tcp  open  echo
```

---

## 🔐 3. Identificar los puertos con SSL/TLS

Los servicios que utilizaban SSL/TLS eran:

```text
31518
31790
```

Los demás utilizaban un servicio `echo`, que simplemente devuelve los mismos datos que recibe.

---

## 🔗 4. Conectarse mediante TLS

Para interactuar con los servicios SSL/TLS utilicé `openssl s_client`.

La estructura es:

```bash
openssl s_client -connect HOST:PUERTO
```

Como el servicio estaba en la misma máquina:

```bash
openssl s_client -connect localhost:PUERTO
```

Para simplificar la interacción utilicé también:

```bash
-quiet
```

Ejemplo:

```bash
openssl s_client -connect localhost:31790 -quiet
```

`-quiet` reduce la información de diagnóstico que muestra `s_client` y permite una interacción más limpia con el servicio.

---

## 📡 5. Enviar la contraseña

Una vez establecida la conexión TLS, envié la contraseña actual.

El servidor correcto respondió:

```text
Correct!
```

En lugar de entregar una contraseña normal, devolvió una:

```text
-----BEGIN OPENSSH PRIVATE KEY-----
...
-----END OPENSSH PRIVATE KEY-----
```

Esto significa que la credencial del siguiente nivel era una **clave privada SSH**.

---

## 🔑 6. Guardar la clave privada

Guardé la clave en un archivo:

```bash
nano sshkey.private
```

El archivo debía contener el bloque completo:

```text
-----BEGIN OPENSSH PRIVATE KEY-----
...
-----END OPENSSH PRIVATE KEY-----
```

Después protegí el archivo:

```bash
chmod 600 sshkey.private
```

---

## 🔐 7. Entrar mediante la clave SSH

Finalmente utilicé la clave privada como archivo de identidad:

```bash
ssh -i sshkey.private -p 2220 bandit17@bandit.labs.overthewire.org
```

`-i` significa **identity file**.

Le indica a SSH qué archivo de clave privada debe utilizar para autenticarse.

---

## 📌 Lo que aprendí

`Nmap` · `TCP Connect Scan` · `Service Detection` · `SSL/TLS` · `OpenSSL` · `SSH Private Keys`

- Escanear un rango específico de puertos con Nmap.
- Utilizar `-sV` para detectar servicios.
- Identificar servicios que utilizan SSL/TLS.
- Conectarme manualmente a un servicio TLS con `openssl s_client`.
- Entender el comportamiento de un servicio `echo`.
- Utilizar `-quiet` para simplificar la interacción con `s_client`.
