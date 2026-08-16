# 🔐 Bandit — Level 0

> Primer contacto con **SSH** y conexión al servidor de OverTheWire.

<br>

## 🎯 Objetivo

Conectarme a la máquina de Bandit utilizando **SSH** con los datos proporcionados por OverTheWire.

| Dato | Valor |
|---|---|
| 👤 Usuario | `bandit0` |
| 🌐 Servidor | `bandit.labs.overthewire.org` |
| 🔌 Puerto | `2220` |
| 🔐 Protocolo | `SSH` |

---

## 🔑 SSH

**SSH (Secure Shell)** es un protocolo que permite conectarse de forma remota y segura a otro equipo a través de una red.

La estructura básica para realizar una conexión es:

```bash
ssh usuario@servidor
```

En este caso, el usuario proporcionado por OverTheWire es `bandit0` y el servidor es `bandit.labs.overthewire.org`:

```bash
ssh bandit0@bandit.labs.overthewire.org
```

---

## 🔌 Puerto

SSH utiliza normalmente el **puerto 22**.

Bandit utiliza el puerto `2220`, por lo que tengo que indicarlo manualmente utilizando la opción `-p`.

La estructura del comando es:

```bash
ssh -p puerto usuario@servidor
```

Para este nivel:

```bash
ssh -p 2220 bandit0@bandit.labs.overthewire.org
```

---

## 🔑 Autenticación

Después de ejecutar:

```bash
ssh -p 2220 bandit0@bandit.labs.overthewire.org
```

SSH solicita la contraseña del usuario `bandit0`.

Para este nivel, OverTheWire proporciona la contraseña:

```text
bandit0
```

Una vez ingresada la contraseña correctamente, se establece la conexión con la máquina de Bandit.

---

<img width="585" height="432" alt="image" src="https://github.com/user-attachments/assets/5b61038e-8519-482a-82f7-8258a2cae74d" />


---
## 📄 Contraseña del siguiente nivel

Una vez dentro de la máquina, el siguiente objetivo es encontrar la contraseña necesaria para acceder a `bandit1`.

> 📍 **Ubicación:** la contraseña se encuentra dentro del archivo `readme`.

---

### 🔎 Ver el contenido del archivo

Para leer el archivo utilicé el comando `cat`:

```bash
cat readme
```

| Comando  | Función                                           |
| :------- | :------------------------------------------------ |
| `cat`    | Muestra el contenido de un archivo en la terminal |
| `readme` | Archivo que quiero consultar                      |


Al ejecutar `cat readme`, la terminal mostró la contraseña necesaria para acceder al siguiente nivel.

> 🔒 **Contraseña omitida:** no muestro las credenciales obtenidas durante los niveles.

---

### 💻 Resultado

```text
bandit0@bandit:~$ cat readme
[CONTRASEÑA OCULTA]
```

<img width="633" height="50" alt="image" src="https://github.com/user-attachments/assets/b67cc96b-44c1-4efb-88dd-42ef83f538de" />


---

## 📌 Lo que aprendí

`SSH` · `Conexión remota` · `Puertos` · `Autenticación`

* Qué es SSH y para qué se utiliza.
* Cómo conectarme a una máquina mediante SSH.
* Qué información necesito para establecer la conexión.
* Que SSH utiliza el puerto `22` por defecto.
* Cómo especificar un puerto diferente mediante `-p`.
* Cómo autenticarme con un usuario y una contraseña.
* Utilizar cat para mostrar el contenido de un archivo directamente en la terminal.

✅ **Level 0 completado**
