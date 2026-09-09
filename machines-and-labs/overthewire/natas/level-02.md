## 🌐 Natas Level 2

En este nivel la página indicaba:

```text
There is nothing on this page
```

Aunque aparentemente no había nada útil visible, inspeccioné nuevamente el **HTML de la página**.

---

### 🔎 Inspección del HTML

Dentro del código encontré una referencia a una imagen:

```html
<img src="files/pixel.png">
```

Esta línea indica que el navegador está cargando el archivo:

```text
pixel.png
```

desde una ruta llamada:

```text
files/
```
---

### 📂 Explorando la ruta


probé acceder directamente al directorio:

```text
/files/
```

El servidor mostró un **listado de los archivos contenidos en ese directorio**.

Esto se conoce como:

> **Directory Listing**

El servidor estaba configurado para permitir visualizar los archivos existentes dentro de esa carpeta.

Entre los archivos disponibles encontré:

```text
users.txt
```

---

### 📄 Archivo expuesto

Accedí a:

```text
/files/users.txt
```

El archivo contenía información de usuarios y entre ella se encontraba la información necesaria para acceder al siguiente nivel.

---

## 🧠 ¿Qué aprendí?

- Que una página puede hacer referencia a **archivos y directorios que no aparecen como enlaces visibles**.
- A identificar rutas a partir de atributos HTML como:

  ```html
  src="files/pixel.png"
  ```

- Qué es **Directory Listing**: una configuración del servidor que permite visualizar el contenido de un directorio web.
- Que un archivo no aparezca visible o enlazado en la página **no significa que no sea accesible**.

---
