# 🟣 Bandit Level 22 → 23

## 🎯 Objetivo

En este nivel había nuevamente una tarea programada con `cron`.

El objetivo era revisar la configuración de `/etc/cron.d/`, identificar qué script se ejecutaba automáticamente y analizar su contenido para descubrir dónde se guardaba la contraseña del siguiente nivel.

---

## 🛠️ Resolución

Primero revisé los archivos de configuración de cron:

```bash
ls /etc/cron.d/
```

Entre ellos encontré:

```text
cronjob_bandit23
```

Entonces leí su contenido:

```bash
cat /etc/cron.d/cronjob_bandit23
```

Ahí vi que cron ejecutaba el script:

```text
/usr/bin/cronjob_bandit23.sh
```

como el usuario `bandit23`.

Después revisé el contenido del script:

```bash
cat /usr/bin/cronjob_bandit23.sh
```

El script contenía algo como:

```bash
#!/bin/bash

myname=$(whoami)
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"

cat /etc/bandit_pass/$myname > /tmp/$mytarget
```

La primera línea importante era:

```bash
myname=$(whoami)
```

`whoami` devuelve el nombre del usuario que está ejecutando el script.

Como cron ejecutaba el script como `bandit23`, el valor de:

```text
$myname
```

era:

```text
bandit23
```

Después el script calculaba un valor llamado `mytarget`:

```bash
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)
```

Para reproducir ese cálculo utilicé:

```bash
echo I am user bandit23 | md5sum | cut -d ' ' -f 1
```

Ese comando me devolvió un hash, que era el nombre del archivo donde cron copiaba la contraseña.


Luego utilicé ese resultado como nombre de archivo dentro de `/tmp/`:

```bash
cat /tmp/TARGET
```

Reemplacé `TARGET` por el hash que había obtenido.

Ese archivo contenía la contraseña del siguiente nivel.

---

## 🧠 Comandos nuevos utilizados


### `echo`

```bash
echo texto
```

Genera o muestra texto.

En este caso se utilizó para producir:

```text
I am user bandit23
```

y pasarlo mediante un pipe al siguiente comando.

---

### `md5sum`

```bash
md5sum
```

Calcula un hash MD5 a partir de los datos que recibe.

En este nivel se utilizó para generar un nombre de archivo basado en el usuario.

---

### `cut`

```bash
cut -d ' ' -f 1
```

Permite extraer una parte concreta de una línea.

- `-d ' '` → utiliza el espacio como separador.
- `-f 1` → toma el primer campo.

En este caso se utilizó para quedarse solamente con el hash generado por `md5sum`.

---

**Nivel completado: Bandit 22 → 23** ✅
