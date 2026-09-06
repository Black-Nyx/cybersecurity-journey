# Bandit Nivel 23 

En este nivel practiqué cómo crear un script Bash, darle permisos de ejecución y colocarlo en un directorio que otro proceso revisa automáticamente.

---
<img width="1908" height="656" alt="image" src="https://github.com/user-attachments/assets/c4677d66-923a-41ab-b573-05ea7e1b5373" />
<img width="972" height="221" alt="image" src="https://github.com/user-attachments/assets/168f5759-10dd-4889-8794-8cd7179a29dc" />


## Conceptos nuevos aprendidos

### `/tmp`

`/tmp` significa **temporary**.

Es un directorio de Linux utilizado para guardar archivos temporales.

En sistemas Linux, normalmente varios usuarios pueden crear archivos dentro de `/tmp`.

Sus permisos suelen verse así:

```bash
drwxrwxrwt
```

La `t` final corresponde al **sticky bit**.

Esto permite que muchos usuarios creen archivos dentro de `/tmp`, pero evita que un usuario normal borre archivos que pertenecen a otro usuario.

---

## Crear un script Bash

El script utilizado tenía esta estructura:

```bash
#!/bin/bash
cat /etc/bandit_pass/bandit24 > /tmp/password24.txt
```

### `#!/bin/bash`

Esta primera línea se llama **shebang**.

```bash
#!/bin/bash
```

Indica qué programa debe interpretar el script.

En este caso:

```bash
/bin/bash
```

es la ruta del intérprete Bash.

---

## Permiso de ejecución con `chmod +x`

Para que un script pueda ejecutarse se puede utilizar:

```bash
chmod +x /tmp/miscript.sh
```

```bash
+x
```

significa:

```text
+ = agregar
x = permiso de ejecución
```

Así que:

```bash
chmod +x archivo.sh
```

significa:

> Agregar permiso de ejecución al archivo.

---


## Copiar el script con `cp`

El comando:

```bash
cp /tmp/miscript.sh /var/spool/bandit24/foo/
```

---

## ¿Qué es `/var/spool`?

`spool` se utiliza para almacenar archivos que están esperando ser procesados por algún servicio o programa.

En este nivel, el directorio:

```bash
/var/spool/bandit24/foo/
```

es importante porque existe un proceso que revisa los archivos colocados allí.

Por eso no basta con dejar el script solamente en `/tmp`.

---

## Permisos numéricos con `chmod`

También apareció:

```bash
chmod 777 /var/spool/bandit24/foo/miscript.sh
```

es decir:

```text
7 = rwx
```
---

## ¿Por qué modificar permisos del script copiado?

El archivo fue creado inicialmente por un usuario, pero después debe poder ser procesado desde otro contexto.

---

## Idea principal del nivel


```text
los permisos dependen del usuario que ejecuta un proceso
```

Un mismo comando puede comportarse de forma diferente dependiendo de quién lo ejecuta.

Además aprendí el flujo:

```text
crear script
     │
     ▼
indicar intérprete con shebang
     │
     ▼
agregar permiso de ejecución
     │
     ▼
copiarlo al directorio correspondiente
     │
     ▼
otro proceso encuentra el archivo
     │
     ▼
lo procesa bajo su propio contexto de usuario
```
