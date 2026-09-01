# 🖥️ Acceso a Cisco IOS

Cisco IOS es el sistema operativo utilizado en muchos dispositivos Cisco, como **routers y switches**. Su administración se realiza principalmente mediante una **interfaz de línea de comandos (CLI)**.

---

## 🧠 Sistema operativo

Un sistema operativo funciona como intermediario entre el usuario, las aplicaciones y el hardware.

<img width="1103" height="640" alt="image" src="https://github.com/user-attachments/assets/5393ca52-dc8f-49c6-8b5c-a4ba8ed0de27" />


### Kernel

El **kernel** es el núcleo del sistema operativo. Administra los recursos del sistema y permite que el software interactúe con el **hardware**, como CPU, memoria y dispositivos.

### Shell

El **shell** es un intérprete que permite al usuario ejecutar comandos e interactuar con el sistema operativo.

Puede utilizarse mediante una **CLI (Command-Line Interface)**.

---

## 🖱️ GUI vs CLI

### GUI — Graphical User Interface

Permite interactuar con el sistema mediante elementos gráficos como:

- Ventanas
- Íconos
- Menús
- Botones

Ejemplos: **Windows, macOS, KDE Plasma y Android**.

### CLI — Command-Line Interface

Permite interactuar mediante **comandos escritos**.

```text
Usuario → CLI → comando → Sistema operativo
```

La CLI suele:

- Consumir menos recursos que una interfaz gráfica.
- Permitir configuraciones avanzadas de forma precisa.
- Ser especialmente útil para administrar dispositivos de red.

---


# 🔐 Métodos de acceso a dispositivos Cisco

Existen diferentes formas de acceder a la CLI de un router o switch.

| Método | Acceso | Cifrado | Requiere red configurada |
|---|---|---|---|
| **Consola** | Local | — | ❌ No |
| **SSH** | Remoto | ✅ Sí | ✅ Sí |
| **Telnet** | Remoto | ❌ No | ✅ Sí |
| **AUX** | Remoto mediante conexión externa | Depende del método | ❌ No necesariamente |

---

## 🔌 Consola

La **consola** es un puerto físico de administración que proporciona acceso **fuera de banda** al dispositivo.

```text
PC ─── Cable de consola ─── Router/Switch
```

No depende de la red, por lo que puede utilizarse aunque el dispositivo todavía no tenga configurados:

- Dirección IP
- SSH
- Otros servicios de red

Por esto es especialmente útil para realizar la **configuración inicial** o recuperar acceso a un dispositivo.

Para utilizarla se necesita un **cable de consola** y un programa de **emulación de terminal**.

---

## 🔒 SSH — Secure Shell

SSH permite acceder **remotamente y de forma cifrada** a la CLI de un dispositivo a través de la red.

```text
PC ───── Red ─────► Router/Switch
        SSH
```

A diferencia de la consola, requiere que exista **conectividad de red** y que SSH haya sido previamente configurado en el dispositivo.


---

## ⚠️ Telnet

Telnet también permite acceder remotamente a la CLI, pero **no cifra la comunicación**.

Esto significa que información como credenciales y comandos puede viajar por la red en **texto plano**, por lo que no debe utilizarse para administrar dispositivos en redes reales.

---
