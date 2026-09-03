# 🔐 OverTheWire Bandit — Nivel 18 → 19

---

## 🎯 Objetivo

La contraseña para el siguiente nivel se encuentra en un archivo llamado:

```bash
readme
```

El problema es que el archivo `.bashrc` fue modificado para cerrar automáticamente la sesión cuando se intenta ingresar normalmente mediante SSH.

Por eso, al iniciar sesión de forma habitual aparecía:

```text
Byebye!
```

---

## 🧠 Concepto importante

SSH no solamente sirve para abrir una terminal remota.

También permite **ejecutar directamente un comando en otra máquina** y recibir su resultado sin mantener una terminal interactiva abierta.


En este nivel, esa sesión se cerraba debido a la configuración de `.bashrc`.

---

## 🔎 Ejecutar un comando directamente con SSH

En lugar de abrir una terminal, ejecuté `cat readme` directamente desde Kali:

```bash
ssh -p 2220 bandit18@bandit.labs.overthewire.org cat readme
```

---

## 📌 Lo que aprendí

- SSH también puede ejecutar un comando directamente en otra máquina.
