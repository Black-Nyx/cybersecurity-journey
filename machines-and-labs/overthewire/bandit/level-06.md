# 🔐 Bandit — Level 6 → Level 7

> Buscando un archivo en el servidor a partir de su propietario, grupo y tamaño.

---

## 🎯 Objetivo

La contraseña para el siguiente nivel se encuentra **en algún lugar del servidor** y el archivo cumple con estas características:

| 🔎 Propiedad   | Valor      |
| :------------- | :--------- |
| 👤 Propietario | `bandit7`  |
| 👥 Grupo       | `bandit6`  |
| 📦 Tamaño      | `33 bytes` |

---

## 🔎 Buscando el archivo

En los niveles anteriores sabía en qué directorio se encontraba el archivo. Esta vez la ubicación era desconocida, así que realicé la búsqueda desde:

```text
/
```

`/` representa el **directorio raíz**, el punto más alto de la estructura de directorios de Linux.

Utilicé:

```bash
find / -user bandit7 -group bandit6 -size 33c
```
<img width="626" height="276" alt="image" src="https://github.com/user-attachments/assets/8247b72b-42fe-4d22-b7af-f4e30191aae5" />

---

## 🧩 Filtros utilizados

Ya había utilizado `find` y `-size` anteriormente, pero en este nivel agregué dos filtros nuevos:

### 👤 `-user`

```bash
-user bandit7
```

Filtra los resultados según el **usuario propietario del archivo**.

En este caso solo me interesaban archivos cuyo propietario fuera `bandit7`.

### 👥 `-group`

```bash
-group bandit6
```

Filtra según el **grupo propietario del archivo**.


---

## ⚠️ Permission denied

Al ejecutar el comando aparecieron muchos "Permission denied".


Entre esos mensajes apareció un resultado que cumplía con las condiciones:

```text
/var/lib/dpkg/info/bandit7.password
```
<img width="627" height="99" alt="image" src="https://github.com/user-attachments/assets/77106556-639a-4fb2-85ef-d6be3466e988" />


---

## 🔑 Leyendo el archivo

Una vez que `find` me mostró la ruta completa, utilicé `cat` para leer su contenido:

```bash
cat /var/lib/dpkg/info/bandit7.password
```

Esto mostró la contraseña necesaria para acceder al siguiente nivel.

---

## 📌 Lo que aprendí

`/` · `-user` · `-group` · `Permission denied`

* Utilizar `/` como punto de inicio para realizar una búsqueda más amplia en el sistema.
* Filtrar archivos según su propietario utilizando `-user`.
* Filtrar archivos según su grupo utilizando `-group`.
* Combinar varios criterios de `find` en una misma búsqueda.

---

### ✅ Nivel completado

