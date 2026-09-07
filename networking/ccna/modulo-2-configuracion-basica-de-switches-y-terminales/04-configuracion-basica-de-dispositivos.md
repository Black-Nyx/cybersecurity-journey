# ⚙️ Configuración básica de dispositivos

Una de las primeras tareas al configurar un dispositivo Cisco es **identificarlo, proteger sus métodos de acceso y establecer información básica de seguridad**.

---

## 🏷️ Nombre del dispositivo — Hostname

Los dispositivos Cisco tienen inicialmente un nombre predeterminado, como:

```text
Switch>
```

En una red con varios dispositivos es importante asignarles nombres únicos para poder identificarlos fácilmente.

### Reglas para el hostname

Un nombre de host debe:

- Comenzar con una letra.
- No contener espacios.
- Terminar en una letra o número.
- Utilizar únicamente letras, números y guiones.
- Tener menos de 64 caracteres.

### Configurar el hostname

Desde el modo de configuración global:

```text
Switch# configure terminal
Switch(config)# hostname S1
S1(config)#
```

Para eliminar el hostname configurado:

```text
S1(config)# no hostname
Switch(config)#
```

> En Cisco IOS, `no` delante de muchos comandos permite eliminar o revertir una configuración.

---

## 🔌 Contraseña de consola

Para proteger el acceso mediante consola:

```text
S1(config)# line console 0
S1(config-line)# password contraseña
S1(config-line)# login
```

`password` establece la contraseña y:

```text
login
```

hace que IOS **solicite esa contraseña al intentar acceder mediante esa línea**.

El `0` identifica la línea de consola que se está configurando.

---

## 🔑 Protección del modo EXEC privilegiado

El acceso al modo EXEC privilegiado (`S1#`) puede protegerse mediante:

```text
S1(config)# enable secret contraseña
```

Después, cuando alguien intente utilizar:

```text
S1> enable
```

IOS solicitará la contraseña antes de permitir:

```text
S1#
```

`enable secret` almacena la contraseña de forma protegida mediante un **hash**, por lo que es preferible al antiguo `enable password`.

---

## 🌐 Contraseña de las líneas VTY

Las líneas **VTY (Virtual Teletype)** se utilizan para sesiones de administración remota, como las realizadas mediante **SSH o Telnet**.

En muchos equipos Cisco pueden encontrarse líneas numeradas del `0` al `15`.

Para configurarlas:

```text
S1(config)# line vty 0 15
S1(config-line)# password contraseña
S1(config-line)# login
```

Esto configura la autenticación mediante contraseña para esas líneas.

---

# 🔒 Protección de contraseñas en la configuración

Algunas contraseñas configuradas mediante `password` pueden aparecer en texto legible dentro de:

```text
running-config
startup-config
```

Para evitar que se muestren directamente se puede utilizar:

```text
S1(config)# service password-encryption
```

Después se puede comprobar la configuración con:

```text
S1# show running-config
```

### ⚠️ Importante

`service password-encryption` utiliza una **ofuscación/cifrado reversible débil** para las contraseñas compatibles almacenadas en la configuración.

Su objetivo principal es evitar que una contraseña pueda leerse inmediatamente al visualizar el archivo de configuración.

```text
Sin protección:
password cisco

Con service password-encryption:
password 7 ...
```

---

# 📢 Mensaje de aviso — MOTD

Cisco IOS permite mostrar un mensaje cuando alguien intenta acceder al dispositivo.

Se configura mediante:

```text
S1(config)# banner motd #Acceso exclusivo para personal autorizado#
```

No tiene que ser específicamente `#`. Puede utilizarse otro carácter siempre que **no aparezca dentro del propio mensaje**.

Por ejemplo:

```text
S1(config)# banner motd !Acceso solo autorizado!
```

El banner aparecerá cuando un usuario acceda al dispositivo.

---
