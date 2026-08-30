# 🔐 Bandit — Level 13 → Level 14

> **Objetivo:** acceder al usuario `bandit14`.  
> En este nivel no se proporciona directamente la contraseña, sino una **clave privada SSH** que permite autenticarse como el siguiente usuario.

---

## 🔎 Explorando los archivos

Primero listé los archivos disponibles:

```bash
ls
```

Entre ellos se encontraba:

```text
sshkey.private
```

Al visualizar su contenido:

```bash
cat sshkey.private
```

apareció un bloque largo de letras y números.

Esto se debe a que `sshkey.private` contiene una **clave privada SSH**, no una contraseña común.

---

## 🔑 ¿Qué es una clave privada SSH?

SSH puede autenticarnos utilizando un **par de claves**:

| Clave | Función |
|---|---|
| 🔐 **Privada** | Se mantiene secreta y permite demostrar nuestra identidad |
| 🔓 **Pública** | Se encuentra autorizada en el servidor |

---

## 🧩 Usar una clave privada con SSH

Para indicarle a `ssh` qué clave privada utilizar se usa la opción:

```bash
-i
```

`-i` significa **identity file** y permite especificar el archivo que contiene la clave privada.

La estructura general es:

```bash
ssh -i <clave_privada> usuario@servidor
```

En Bandit también necesitamos indicar el puerto `2220`:

```bash
ssh -i sshkey.private -p 2220 bandit14@bandit.labs.overthewire.org
```


Al ejecutar el comando, SSH utiliza `sshkey.private` para autenticarse como `bandit14` sin que tengamos que introducir su contraseña.

---

## 📌 Lo que aprendí

`SSH` · `Clave privada` · `Clave pública` · `-i` · 

- SSH puede utilizar una **clave privada en lugar de una contraseña** para autenticarnos.
- `-i` permite especificar el archivo que contiene la clave privada.
