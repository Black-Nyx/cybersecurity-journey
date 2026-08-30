# 🔐 Bandit — Level 13 → Level 14

> **Objetivo:** acceder al usuario `bandit14`.  
> En este nivel no se proporciona directamente la contraseña del siguiente usuario. En su lugar, se proporciona una **clave privada SSH** que permite autenticarse como `bandit14`.

---

## 🔎 Encontrando la clave privada

Primero revisé los archivos disponibles dentro de `bandit13`:

```bash
ls
```

Entre ellos encontré:

```text
HINT  sshkey.private
```

`sshkey.private` es una **clave privada SSH**.

Al visualizarla con:

```bash
cat sshkey.private
```

apareció un bloque largo de caracteres.

Esto no es una contraseña común, sino la información criptográfica que forma una clave privada.

---

## 🔑 ¿Qué es una clave privada SSH?

SSH puede permitir la autenticación mediante un **par de claves**:

| Clave | Función |
|---|---|
| 🔐 **Privada** | Se mantiene secreta y se utiliza para demostrar nuestra identidad |
| 🔓 **Pública** | Se encuentra autorizada en el servidor |

En lugar de escribir una contraseña, podemos indicarle a SSH que utilice una determinada **clave privada** para autenticarnos.

---

## 🧩 La opción `-i` de SSH

Para indicarle a SSH qué clave privada queremos utilizar existe la opción:

```bash
-i
```

`-i` significa **identity file**.

La estructura general es:

```bash
ssh -i <clave_privada> usuario@servidor
```

Por ejemplo, para este nivel:

```bash
ssh -i sshkey.private -p 2220 bandit14@bandit.labs.overthewire.org
```
---

## 📤 Copiando la clave a Kali con `scp`

Para transferir `sshkey.private` desde el servidor de Bandit hacia Kali utilicé `scp`.

`scp` significa **Secure Copy** y permite copiar archivos entre equipos utilizando SSH.

Desde Kali ejecuté:

```bash
scp -P 2220 bandit13@bandit.labs.overthewire.org:sshkey.private .
```

### Partes del comando

| Parte | Función |
|---|---|
| `scp` | Copia archivos de forma segura mediante SSH |
| `-P 2220` | Especifica el puerto del servidor |
| `bandit13@bandit.labs.overthewire.org` | Usuario y servidor remoto |
| `:sshkey.private` | Archivo que quiero copiar desde el servidor |
| `.` | Guarda el archivo en mi directorio actual |

---

## 🔐 Revisando los permisos de la clave

Antes de utilizar la clave revisé sus permisos:

```bash
ls -l sshkey.private
```

Inicialmente aparecían como:

```text
-rw-r-----
```

Los permisos de Linux se dividen en tres grupos:

```text
- | rw- | r-- | ---
    │     │     │
    │     │     └── otros
    │     └──────── grupo
    └────────────── propietario
```

Las letras significan:

| Permiso | Significado | Valor |
|---|---|---:|
| `r` | read → leer | `4` |
| `w` | write → escribir | `2` |
| `x` | execute → ejecutar | `1` |
| `-` | sin permiso | `0` |

Los valores se suman dentro de cada grupo.

Por ejemplo:

```text
rwx = 4 + 2 + 1 = 7
rw- = 4 + 2     = 6
r-x = 4 + 1     = 5
r-- = 4         = 4
--- =             0
```

Por lo tanto:

```text
-rw-r-----
```

equivale a:

```text
rw- | r-- | ---
 6     4     0

→ 640
```

Esto significa:

```text
Propietario → leer + escribir
Grupo       → leer
Otros       → ningún permiso
```

---

## 🛡️ Protegiendo la clave con `chmod`

Como se trata de una **clave privada**, no queremos que otros usuarios puedan leerla.

Por eso cambié sus permisos:

```bash
chmod 600 sshkey.private
```

`600` significa:

```text
rw- | --- | ---
 6     0     0
```

Esto es importante porque SSH espera que las claves privadas estén correctamente protegidas y puede rechazar claves cuyos permisos sean demasiado abiertos.


---

## 🚪 Accediendo a bandit14

Con `sshkey.private` ya copiada en Kali y con permisos adecuados, pude utilizarla para autenticarme:

```bash
ssh -i sshkey.private -p 2220 bandit14@bandit.labs.overthewire.org
```

De esta manera pude acceder a `bandit14` utilizando una **clave privada SSH en lugar de una contraseña**.

---

## 📌 Lo que aprendí

`SSH` · `Clave privada` · `Clave pública` · `scp` · `chmod` · `Permisos Linux` · `-i` · `-p` · `-P`

- SSH puede utilizar **claves criptográficas en lugar de contraseñas** para autenticarnos.
- `-i` permite indicarle a SSH qué archivo de clave privada utilizar.
- `scp` permite transferir archivos entre equipos utilizando SSH.
- En `scp`, `-P` permite especificar el puerto.
- `.` representa el directorio actual.
- Los permisos de Linux se dividen entre **propietario, grupo y otros**.
- `r`, `w` y `x` representan lectura, escritura y ejecución.
- `chmod 600` deja un archivo accesible únicamente para su propietario.
