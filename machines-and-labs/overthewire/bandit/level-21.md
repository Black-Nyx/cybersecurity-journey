# 🟣 Bandit Level 21 → 22

## 🎯 Objetivo

En este nivel había una tarea programada con `cron`.

El objetivo era revisar la configuración ubicada en `/etc/cron.d/` para descubrir qué comando se estaba ejecutando automáticamente.

---

## 🛠️ Resolución

Primero listé el contenido del directorio de configuraciones de cron:

```bash
ls /etc/cron.d/
```

Entre los archivos encontré:

```text
cronjob_bandit22
```

Entonces revisé su contenido:

```bash
cat /etc/cron.d/cronjob_bandit22
```

<img width="622" height="72" alt="image" src="https://github.com/user-attachments/assets/d6746f2d-4cca-422e-b28f-0b1b6e05fe98" />


En la configuración vi que cron ejecutaba el siguiente script como el usuario `bandit22`:

```text
/usr/bin/cronjob_bandit22.sh
```

Después revisé el contenido de ese script:

```bash
cat /usr/bin/cronjob_bandit22.sh
```

El script contenía:

```bash
#!/bin/bash
chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
```

Esto mostraba que la contraseña de `bandit22` se copiaba a un archivo dentro de `/tmp/`.

Además, `chmod 644` hacía que ese archivo pudiera ser leído por otros usuarios.

Por último, leí ese archivo:

```bash
cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
```

Y obtuve la contraseña del siguiente nivel.

---

## 🧠 Comandos nuevos utilizados

### `cron`

`cron` es un servicio de Linux que ejecuta comandos o scripts automáticamente en determinados intervalos de tiempo.

En este nivel, la tarea estaba configurada para ejecutarse cada minuto.

---

## 📌 Lo que aprendí

- `cron` puede ejecutar scripts automáticamente en intervalos regulares.

---

**Nivel completado: Bandit 21 → 22** ✅
