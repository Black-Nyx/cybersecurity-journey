# 🔐 OverTheWire Bandit — Level 24 → Level 25

## 🎯 Objetivo

En este nivel hay un servicio ejecutándose en `localhost` que solicita dos datos:

- La contraseña del nivel actual.
- Un **PIN de 4 dígitos**.

Como existen `10.000` combinaciones posibles (`0000`–`9999`), probar cada PIN manualmente no sería práctico.

La idea del nivel es **automatizar las pruebas utilizando un bucle `for` de Bash** y enviar las combinaciones al servicio mediante `nc`.

---

## 🔁 Bucle `for` en Bash

Para generar automáticamente todos los PIN utilicé un bucle:

```bash
for i in {0000..9999}
do
    echo "CONTRASEÑA $i"
done
```

### ¿Qué hace cada parte?

| Parte | Explicación |
|---|---|
| `for` | Inicia el bucle |
| `i` | Es una variable que irá cambiando |
| `in` | Indica los valores que recorrerá la variable |
| `{0000..9999}` | Genera los números desde `0000` hasta `9999` |
| `do` | Indica dónde comienzan las instrucciones que se repetirán |
| `$i` | Obtiene el valor actual almacenado en `i` |
| `done` | Marca el final del bucle |

---

## 💲 ¿Por qué se escribe `$i`?

`i` es el **nombre de la variable**.

El símbolo `$` permite obtener el **valor almacenado dentro de esa variable**.

Por ejemplo:

```bash
i=0042
echo "$i"
```

mostraría:

```text
0042
```

---

## 🔗 Enviar las combinaciones con `nc`

Una vez generado el bucle, envié toda su salida al servicio:

```bash
for i in {0000..9999}
do
    echo "CONTRASEÑA $i"
done | nc localhost 30002
```
---

## ✅ Completado

`STATUS: COMPLETED` ✅

> 🔐 La contraseña encontrada durante el laboratorio fue omitida intencionalmente.
