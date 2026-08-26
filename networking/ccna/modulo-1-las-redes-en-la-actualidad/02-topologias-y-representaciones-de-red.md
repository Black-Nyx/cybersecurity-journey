# 🗺️ Topologías y representaciones de red

## 🌐 Representaciones de red

Las redes se pueden representar mediante diagramas para entender **qué dispositivos hay y cómo están conectados**.

---

### 🔌 NIC (Network Interface Card)

La **tarjeta de interfaz de red (NIC)** Permite que un dispositivo final **se conecte a una red**.

Por ejemplo, una computadora puede tener una NIC para conectarse mediante **Ethernet o Wi-Fi**.

---

### 🔗 Puerto físico

Es el **conector físico donde se conecta un medio de red**, como un cable Ethernet.

```text
Cable Ethernet ───► [ Puerto ] Switch
```

---

### 🔀 Interfaz

Una **interfaz** es un puerto especializado que conecta un dispositivo de red con una **red individual**.

En un **router**, los puertos que permiten conectarlo a diferentes redes se denominan **interfaces de red**.
```text
Red A ─── G0/0 [ Router ] G0/1 ─── Red B
             ↑             ↑
          Interfaz       Interfaz
```
---

## 🗺️ Diagramas de topología

Los **diagramas de topología** son mapas visuales que muestran cómo está conectada una red.

Existen dos tipos:

| Topología física | Topología lógica |
|---|---|
| Muestra cómo y dónde están conectados físicamente los dispositivos. | Muestra cómo está organizada la red y cómo se comunican los dispositivos. |
| Puede mostrar cables, puertos y ubicación de equipos. | Puede mostrar direcciones IP, interfaces y redes. |

> **Física = cómo está armada físicamente.**
<img width="1177" height="697" alt="image" src="https://github.com/user-attachments/assets/f320c3ea-23da-4912-85c2-2d04cf3d8e59" />


> **Lógica = cómo funciona y se organiza la comunicación.**
<img width="1171" height="693" alt="image" src="https://github.com/user-attachments/assets/5a6a8c05-bfc5-44b1-9d49-25fc16f81be0" />


---
