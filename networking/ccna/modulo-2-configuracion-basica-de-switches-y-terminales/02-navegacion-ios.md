# 🧭 Navegación en Cisco IOS

Cisco IOS utiliza diferentes **modos de comando**. Cada modo permite ejecutar determinados comandos y se identifica por el símbolo que aparece después del nombre del dispositivo.

---

## 🔐 Modos principales

### Modo EXEC de usuario

Es el nivel de acceso inicial y tiene **capacidades limitadas**. Permite realizar algunas consultas básicas, pero no modificar la configuración del dispositivo.

Se identifica por:

```text
Switch>
```

### Modo EXEC privilegiado

Proporciona acceso a más comandos de administración y permite ingresar al modo de configuración.

Se identifica por:

```text
Switch#
```

Para acceder desde el modo EXEC de usuario:

```text
Switch> enable
Switch#
```

Para volver:

```text
Switch# disable
Switch>
```

> El modo EXEC privilegiado también se conoce como **modo enable**.

---

## ⚙️ Modo de configuración global

Para comenzar a **modificar la configuración del dispositivo**, primero se debe acceder al modo de configuración global desde EXEC privilegiado:

```text
Switch# configure terminal
Switch(config)#
```

Desde este modo se puede acceder a diferentes **modos de subconfiguración**.

---

## 🔸 Modos de subconfiguración

### `config-line` — Líneas de acceso

Permite configurar las líneas utilizadas para el **acceso administrativo**, como consola, VTY (SSH/Telnet) o AUX.

Por ejemplo:

```text
Switch(config)# line console 0
Switch(config-line)#
```

### `config-if` — Interfaz

Permite configurar una **interfaz de red específica**.

Por ejemplo:

```text
Router(config)# interface gigabitEthernet 0/0
Router(config-if)#
```

---

### Comandos para regresar

| Comando | Acción |
|---|---|
| `disable` | EXEC privilegiado → EXEC de usuario |
| `exit` | Regresa al modo inmediatamente anterior |
| `end` | Vuelve directamente a EXEC privilegiado |
| `Ctrl + Z` | Vuelve directamente a EXEC privilegiado |

Por ejemplo:

```text
Switch(config-line)# exit
Switch(config)#
```

Mientras que:

```text
Switch(config-line)# end
Switch#
```
