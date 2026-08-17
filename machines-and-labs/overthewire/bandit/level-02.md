# 🔐 Bandit — Level 2 → Level 3

> Trabajando con espacios y guiones en el nombre de un archivo.

---

## 🎯 Objetivo

La contraseña para acceder al siguiente nivel se encuentra en un archivo llamado `--spaces in this filename--`, ubicado en el directorio **home**.

---

## 📄 Spaces in filename

En Linux, un archivo puede contener **espacios en su nombre**.

El problema es que la terminal utiliza los espacios para separar los distintos argumentos de un comando. Por eso, si quiero referirme a un nombre que contiene espacios, tengo que indicarle a la terminal que esos espacios **forman parte del nombre del archivo**.

Una forma de hacerlo es utilizando `\` antes de cada espacio.

```text
--spaces\ in\ this\ filename--
```

---

## 💻 Leyendo el archivo

Como el archivo también comienza con `-`, utilicé `./` para indicar que se encuentra en el **directorio actual**, igual que en el nivel anterior.

Ejecuté:

```bash
cat ./--spaces\ in\ this\ filename--
```

El comando mostró la contraseña necesaria para continuar al siguiente nivel.

```text
bandit2@bandit:~$ cat ./--spaces\ in\ this\ filename--
[CONTRASEÑA OCULTA]
```

---

## 📌 Lo que aprendí

`Spaces in filenames` · `\` · `./`

* Cómo trabajar con archivos que contienen **espacios en su nombre**.
* Utilizar `\` para escapar espacios en la terminal.
* Combinar `./` y `\` para acceder correctamente a un archivo con guiones iniciales y espacios.

---

### ✅ Nivel completado
