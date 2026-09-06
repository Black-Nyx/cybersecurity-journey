# 🔐 OverTheWire Bandit — Nivel 26

## 🎯 Objetivo

Encontrar la contraseña necesaria para acceder al usuario `bandit27`.

---

## 🔎 1. Revisar los archivos disponibles

Una vez que conseguí acceder como `bandit26`, utilicé:

```bash
ls
```

para ver qué archivos había disponibles en el directorio actual.

El resultado fue:

```text
bandit27-do
text.txt
```

Encontré dos archivos:

- `text.txt`: el archivo de texto que había aparecido en el nivel anterior.
- `bandit27-do`: un ejecutable que permite ejecutar un comando con los permisos necesarios para este nivel.

---

## ⚙️ 2. Ejecutar `bandit27-do`

Utilicé:

```bash
./bandit27-do cat /etc/bandit_pass/bandit27
```

Esto mostró la contraseña correspondiente a `bandit27`.

---


