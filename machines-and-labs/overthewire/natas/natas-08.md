# 🌐 OverTheWire Natas — Nivel 8

En este nivel practiqué el análisis de código PHP para entender cómo una aplicación transformaba un valor antes de compararlo con la entrada del usuario.

El objetivo fue identificar las transformaciones aplicadas y realizar el **proceso inverso** para recuperar el valor original.

<img width="1002" height="472" alt="image" src="https://github.com/user-attachments/assets/65ec3b81-5871-4e82-a7eb-40e7c075f606" />

---

## 🔎 Análisis del código

En el código fuente aparecía la siguiente función:

<img width="1152" height="657" alt="image" src="https://github.com/user-attachments/assets/dd8951ef-7520-436a-b75d-2ae789361d9e" />


```php
function encodeSecret($secret) {
    return bin2hex(strrev(base64_encode($secret)));
}
```

Como las funciones están anidadas, se ejecutan **desde adentro hacia afuera**.

Por lo tanto:

1. `base64_encode()` codifica el valor en Base64.
2. `strrev()` invierte el orden de los caracteres.
3. `bin2hex()` convierte el resultado a hexadecimal.

---

## 🔄 Revertir el proceso

Para recuperar el valor original tuve que realizar las operaciones contrarias **en orden inverso**.
---

## 🔢 `bin2hex()`

`bin2hex()` convierte los bytes de un valor a una representación hexadecimal.

Ejemplo:

```text
hola → 686f6c61
```

Aquí, `bin2hex()` aparece como la **última transformación aplicada** dentro de la función.

El orden de transformación es:

```text
Secreto original
      ↓
base64_encode()
      ↓
strrev()
      ↓
bin2hex()
      ↓
Valor transformado
```
---
