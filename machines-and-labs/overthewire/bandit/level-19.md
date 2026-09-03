# 🐧 OverTheWire Bandit — Nivel 19 → 20

## 🎯 Objetivo

En este nivel encontré un archivo especial llamado:

```bash
bandit20-do
```

El objetivo era utilizarlo para ejecutar un comando con los permisos de otro usuario y así poder acceder a la contraseña del siguiente nivel.

---

## 🔎 Exploración

Primero observé los archivos disponibles en el directorio:

```bash
ls 
```

Entre ellos se encontraba:

```text
bandit20-do
```

Al ejecutarlo:

```bash
./bandit20-do
```

el programa indicaba que permitía:

```text
Run a command as another user.
```

También mostraba que debía pasarle un comando.

---

## 🔑 Acceder a la contraseña del siguiente nivel

Las contraseñas de Bandit se encuentran dentro de:

```text
/etc/bandit_pass/
```

Normalmente, `bandit19` no tiene permisos para leer directamente el archivo correspondiente a `bandit20`.

Sin embargo, utilizando `bandit20-do` pude ejecutar `cat` con los permisos necesarios:

```bash
./bandit20-do cat /etc/bandit_pass/bandit20
```

Esto mostró la contraseña necesaria para continuar al siguiente nivel.

---

## 📌 Lo que aprendí

 `SUID` · `Ejecución como otro usuario`  

- Un ejecutable con permisos especiales puede permitir realizar determinadas acciones con los privilegios de otro usuario.
- `bandit20-do` recibe otro comando como argumento y lo ejecuta con los permisos para los que fue configurado.
- Los permisos y propietarios de los ejecutables son importantes al analizar un sistema Linux.
