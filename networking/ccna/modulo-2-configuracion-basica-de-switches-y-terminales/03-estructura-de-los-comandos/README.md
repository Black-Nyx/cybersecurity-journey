# ⌨️ Estructura de los comandos de Cisco IOS

Los comandos de Cisco IOS siguen una **estructura determinada**. Entenderla permite interpretar correctamente la sintaxis de un comando y saber qué valores debemos proporcionar.

---

## 🧩 Estructura básica de un comando

Un comando puede estar formado por:

```text
Switch> show ip protocols
   │      │       │
   │      │       └── Palabra clave
   │      └────────── Comando
   └──────────────── Indicador (prompt)
```

Otro ejemplo:

```text
Switch> ping 192.168.10.5
          │       │
          │       └── Argumento
          └────────── Comando
```

### Palabra clave

Una **palabra clave (keyword)** es un parámetro definido por IOS que debe escribirse como indica la sintaxis.

Ejemplo:

```text
show ip protocols
     └─┬────────┘
   palabras clave
```

### Argumento

Un **argumento** es un valor que proporciona el usuario y puede cambiar dependiendo de lo que quiera hacer.

Por ejemplo:

```text
ping 192.168.10.5
     └────┬─────┘
       argumento
```

En este caso, la dirección IP depende del dispositivo al que quiera enviar el `ping`.

---

## 📐 Cómo leer la sintaxis de IOS

En la documentación de Cisco aparecen diferentes símbolos para indicar cómo debe escribirse un comando.

| Convención | Significado |
|---|---|
| **Negrita** | Comando o palabra clave que se escribe literalmente |
| *Cursiva* | Valor que debe proporcionar el usuario |
| `[ ]` | Elemento opcional |
| `{ }` | Elemento obligatorio |
| `x \| y` | Se debe elegir una de las opciones |

Por ejemplo:

```text
{ static | time }
```

significa que es necesario elegir **una de las dos opciones**:

---

## ⚡ Atajos útiles en la CLI

IOS proporciona combinaciones de teclas que permiten trabajar más rápido.

| Tecla | Función |
|---|---|
| `Tab` | Completa un comando escrito parcialmente |
| `Backspace` | Borra el carácter anterior |
| `Ctrl + W` | Borra la palabra anterior |
| `Ctrl + U` / `Ctrl + X` | Borra desde el cursor hasta el inicio de la línea |
| `Ctrl + K` | Borra desde el cursor hasta el final de la línea |
| `Ctrl + A` | Lleva el cursor al inicio de la línea |
| `Ctrl + E` | Lleva el cursor al final de la línea |
| `Ctrl + B` / `←` | Retrocede un carácter |
| `Ctrl + F` / `→` | Avanza un carácter |
| `Esc + B` | Retrocede una palabra |
| `Esc + F` | Avanza una palabra |

---

## 📄 Salidas largas — `--More--`

Cuando la salida de un comando es demasiado extensa para mostrarse completa en la terminal, IOS puede detenerla mostrando:

```text
--More--
```

En ese momento:

| Tecla | Acción |
|---|---|
| `Enter` | Avanza una línea |
| `Espacio` | Avanza una pantalla |
| Otra tecla | Detiene la salida |

---

## 🛑 Interrumpir comandos

Algunas combinaciones permiten detener operaciones en ejecución.

### `Ctrl + Shift + 6`

Permite interrumpir determinados procesos, como un `ping`, `traceroute` o una búsqueda DNS que está tardando demasiado.
