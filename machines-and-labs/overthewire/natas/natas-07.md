## 🌐 Natas — Análisis de parámetros con Burp Suite


<img width="1122" height="513" alt="image" src="https://github.com/user-attachments/assets/515d337f-f08f-4d6b-9eb4-027dc28f01b6" />

En este nivel, la página mostraba dos opciones:

- `Home`
- `About`

Al navegar entre ellas, observé que la URL utilizaba el parámetro `page` para indicar qué contenido debía mostrar el servidor.

Por ejemplo:

```text
?page=home
```

```text
?page=about
```

### 🔎 Análisis con Burp Suite

Utilicé **Burp Suite** para observar la comunicación entre el navegador y el servidor.

Al revisar la **Response**, encontré dentro del código una pista:

<img width="1253" height="420" alt="image" src="https://github.com/user-attachments/assets/6e680c1e-3e17-442a-a308-4e821eee5f7b" />



Entonces reemplacé el valor original:

```text
?page=home
```

por: /etc/natas_webpass/natas8.


Al realizar nuevamente la solicitud, el servidor devolvió otro contenido en el que se encontraba la contraseña necesaria para avanzar al siguiente nivel.
