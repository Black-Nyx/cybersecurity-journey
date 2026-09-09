## 🌐 Natas Level 3

En este nivel volví a inspeccionar el **código HTML** de la página.

Dentro del código encontré un comentario que daba una pista:

```html
<!-- No more information leaks!! Not even Google will find it this time... -->
```

La parte importante era la referencia a **Google** y a que no podría encontrar determinado contenido.

---

### 🤖 ¿Por qué busqué `robots.txt`?

Los buscadores como Google utilizan programas llamados **crawlers** o **bots** para recorrer páginas web y descubrir contenido.

Los sitios pueden tener un archivo especial llamado:

```text
robots.txt
```

que se encuentra normalmente en la raíz del sitio:

```text
/robots.txt
```

Este archivo proporciona instrucciones a los crawlers sobre qué partes del sitio deberían o no deberían rastrear.

Por eso, al encontrar una pista que decía que **“ni siquiera Google podrá encontrarlo”**, pensé en comprobar:

```text
/robots.txt
```

---

### 🔎 Revisando `robots.txt`

Agregué a la URL:

```text
/robots.txt
```

y encontré una entrada similar a:

```text
Disallow: /s3cr3t/
```

`Disallow` indica a los crawlers que **no deberían rastrear esa ruta**.

---

### 📂 Accediendo al directorio

Después agregué esa ruta a la URL:

```text
/s3cr3t/
```

Al acceder al directorio apareció un archivo:

```text
users.txt
```

Entré en él y encontré la información necesaria para acceder al siguiente nivel.


---

## 🧠 ¿Qué aprendí?

- Que los motores de búsqueda utilizan **crawlers/bots** para descubrir contenido web.
- Que `Disallow` **no protege ni bloquea el acceso** a un directorio.
- Que `robots.txt` solamente indica a crawlers compatibles que no deberían rastrear determinadas rutas.
- Que `robots.txt` puede terminar **revelando nombres de directorios o recursos interesantes**.

---
