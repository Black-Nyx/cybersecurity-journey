# 🔐 OverTheWire Bandit — Nivel 26

## 🎯 Objetivo

Acceder como `bandit26`.

Este nivel introduce una situación particular: el usuario `bandit26` **no utiliza una shell convencional como `/bin/bash`**.  
Para resolverlo fue necesario investigar qué programa se ejecutaba al iniciar sesión y entender el comportamiento de `more` y `vi`.

---

## 🔎 1. Investigar el usuario `bandit26`

Primero consulté la información del usuario almacenada en `/etc/passwd`:

```bash
cat /etc/passwd | grep "bandit26"
```

### ¿Por qué hice esto?

`/etc/passwd` contiene información básica sobre los usuarios del sistema.

Como el archivo tiene muchas líneas, utilicé:

```bash
grep "bandit26"
```

para quedarme únicamente con la correspondiente a `bandit26`.

El resultado fue:

```text
bandit26:x:11026:11026:bandit level 26:/home/bandit26:/usr/bin/showtext
```

---

## 📖 2. Entender la entrada de `/etc/passwd`

Las entradas de `/etc/passwd` están separadas mediante `:`:

```text
bandit26:x:11026:11026:bandit level 26:/home/bandit26:/usr/bin/showtext
```

| Campo | Valor | Significado |
|---|---|---|
| Usuario | `bandit26` | Nombre de la cuenta |
| Contraseña | `x` | La contraseña no está almacenada directamente en `/etc/passwd` |
| UID | `11026` | Identificador numérico del usuario |
| GID | `11026` | Identificador de su grupo principal |
| Información | `bandit level 26` | Descripción de la cuenta |
| Home | `/home/bandit26` | Directorio personal del usuario |
| Shell | `/usr/bin/showtext` | Programa que se ejecuta al iniciar sesión |

Lo más importante fue el último campo:

```text
/usr/bin/showtext
```

Normalmente podría aparecer algo como:

```text
/bin/bash
```

pero `bandit26` tiene configurado **`/usr/bin/showtext` como login shell**.

Esto explica por qué conectarse mediante SSH no proporciona directamente una terminal Bash normal.

---

## 🔬 3. Analizar `/usr/bin/showtext`

Para saber qué hacía ese programa/script, visualicé su contenido:

```bash
cat /usr/bin/showtext
```

Contenido:

```bash
#!/bin/sh

export TERM=linux

exec more ~/text.txt
exit 0
```

### `#!/bin/sh`

```bash
#!/bin/sh
```

Es el **shebang**.

Indica que el script debe interpretarse utilizando:

```text
/bin/sh
```

---

### `export TERM=linux`

```bash
export TERM=linux
```

La variable de entorno `TERM` informa a los programas sobre el tipo de terminal que están utilizando.

Aquí se establece:

```text
TERM=linux
```

y `export` hace que esta variable también esté disponible para los programas que ejecute posteriormente el script.

---

### `exec more ~/text.txt`

```bash
exec more ~/text.txt
```

`more` es un **paginador de texto**: permite visualizar un archivo por partes cuando su contenido no entra completamente en la pantalla.

```text
~/text.txt
```

hace referencia al archivo `text.txt` situado en el directorio home del usuario.

Además, aparece:

```bash
exec
```

`exec` reemplaza el proceso actual por el programa indicado.

En este caso, el script es reemplazado por:

```bash
more ~/text.txt
```

Por eso la sesión queda dentro de `more`.


---

## 🔑 4. Obtener la clave SSH

Al listar los archivos disponibles encontré:

```bash
ls
```

```text
bandit26.sshkey
```

Visualicé su contenido:

```bash
cat bandit26.sshkey
```

Era una **clave privada SSH** que podía utilizarse para autenticarme como `bandit26`.

---

## 💾 5. Guardar la clave en Kali

Abrí otra terminal en mi máquina Kali y creé un archivo:

```bash
nano bandit26.sshkey
```

Pegué dentro el contenido de la clave y guardé el archivo.

Después modifiqué sus permisos:

```bash
chmod 600 bandit26.sshkey
```

## 🔐 6. Conectarme utilizando la clave privada

Utilicé:

```bash
ssh -i bandit26.sshkey bandit26@bandit.labs.overthewire.org -p 2220
```

---

## 🖥️ 7. Hacer que `more` permaneciera abierto

Al conectarme, `/usr/bin/showtext` ejecutaba:

```bash
more ~/text.txt
```

El problema era que, si la terminal era suficientemente grande para mostrar todo el archivo de una vez, `more` podía finalizar inmediatamente.

Para evitarlo, **reduje el tamaño de la ventana de la terminal**.

De esta manera, el contenido ya no entraba completamente en pantalla y apareció:

```text
--More--
```

Esto significaba que seguía dentro del programa `more`.

---

## ✏️ 8. Pasar de `more` a `vi`

Mientras estaba dentro de `more`, presioné:

```text
v
```

`more` permite utilizar `v` para abrir el archivo que se está visualizando en el editor `vi`.


Esto fue importante porque `vi` no sirve únicamente para editar texto: también dispone de comandos internos que permiten interactuar con una shell.

---

## 🐚 9. Configurar Bash desde `vi`

Dentro de `vi` escribí:

```vim
:set shell=/bin/bash
```

### ¿Qué hace?

El `:` permite introducir un comando interno de `vi`.

```text
set
```

modifica una opción del editor.

En este caso modifico:

```text
shell
```

para establecer:

```text
/bin/bash
```


---

## 🚪 10. Abrir la shell

Finalmente ejecuté:

```
:shell
```

Este comando le pide a `vi` que inicie una shell.

De esta manera logré ingresar a bandit26

---

