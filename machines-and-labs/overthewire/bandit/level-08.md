# 🔐 Bandit — Level 8 → Level 9

> **Objetivo:** encontrar en `data.txt` la única línea de texto que aparece una sola vez.

---

## 🧩 Resolución

Utilicé:

```bash
sort data.txt | uniq -u
```

El comando combina dos herramientas mediante un **pipe `|`**:


---

## 📖 Comandos nuevos

| Comando   | ¿Qué hace?                                                             |
| :-------- | :--------------------------------------------------------------------- |
| `sort`    | Ordena las líneas. Esto hace que las líneas iguales queden juntas.     |
| `uniq`    | Detecta líneas repetidas **consecutivas**.                             |
| `uniq -u` | Muestra solamente las líneas que no tienen una repetición consecutiva. |
| `\|`      | Pasa la salida de `sort` como entrada de `uniq`.                       |

### 🔹 ¿Por qué necesito `sort`?

Porque `uniq` trabaja comparando líneas consecutivas.

```text
ANTES                    DESPUÉS DE sort

gato                      casa
perro                     gato
casa        ───────►      gato
gato                      perro
perro                     perro
```

Ahora `uniq` puede distinguir fácilmente:

```text
casa       ← única  ✅
gato
gato       ← repetida
perro
perro      ← repetida
```

---

## ⚠️ Un error que cometí

Primero probé:

```bash
sort -u data.txt | uniq -u
```

Y obtuve muchos resultados.

El problema estaba en `sort -u`:

> `sort -u` **ordena y elimina los duplicados**.

Por ejemplo:

```text
ORIGINAL              sort -u

gato                   casa
gato      ───────►     gato
casa                   perro
perro
perro
```

Cuando los datos llegan a `uniq -u`, las repeticiones **ya fueron eliminadas**, por lo que todas las líneas restantes parecen únicas.

```text
┌───────────────────────────────────────────┐
│ ❌ sort -u → elimina los duplicados       │
│                                           │
│ ✅ sort    → solo los ordena              │
│                                           │
│ Para este nivel necesitaba conservar las  │
│ repeticiones para que uniq pudiera        │
│ compararlas.                              │
└───────────────────────────────────────────┘
```

---

## 🧠 Lo que aprendí

```text
sort             → ordenar líneas
uniq             → comparar líneas consecutivas
uniq -u          → mostrar las que aparecen una vez
|                → conectar la salida de un comando
                   con la entrada del siguiente
```


---

### 🏁 Level 8 completado ✓


---

