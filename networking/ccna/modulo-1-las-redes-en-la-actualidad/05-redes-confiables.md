

## 🏗️ Arquitectura de red

La **arquitectura de red** incluye las tecnologías que permiten el funcionamiento de una red:

- **Infraestructura:** componentes físicos y lógicos que conectan los dispositivos.
- **Servicios:** funciones que ofrece la red.
- **Reglas y protocolos:** determinan cómo se trasladan los datos.

Una arquitectura confiable se basa principalmente en características como **tolerancia a fallas, escalabilidad y calidad de servicio (QoS)**.

---

## 🔄 Tolerancia a fallas

Una red tolerante a fallas está diseñada para **limitar el impacto de una falla y recuperarse rápidamente**.

Si una ruta deja de funcionar, los datos pueden utilizar **otra ruta disponible** para llegar al destino.

```text
            ┌── Router A ──┐
Origen ─────┤              ├──── Destino
            └── Router B ──┘
                 ↑
            Ruta alternativa
```

### Redundancia

La existencia de **varias rutas posibles hacia un mismo destino** se denomina **redundancia**.

Esto permite que la comunicación pueda continuar aunque falle uno de los enlaces.

### 📦 Conmutación por paquetes

La **conmutación por paquetes (packet switching)** divide los datos que se transmiten en **paquetes más pequeños**.

Por ejemplo:

```text
Mensaje
   ↓
┌────┬────┬────┬────┐
│ P1 │ P2 │ P3 │ P4 │
└────┴────┴────┴────┘
   ↓    ↓    ↓    ↓
        Red
```

Los routers pueden enviar los paquetes por **diferentes rutas según el estado de la red**.

```text
P1 ──► Ruta A ──► Destino
P2 ──► Ruta B ──► Destino
P3 ──► Ruta A ──► Destino
```

Por lo tanto, los paquetes de un mismo mensaje **no necesariamente recorren el mismo camino** para llegar al destino.

---

## 📈 Escalabilidad

Una **red escalable** puede crecer para admitir **nuevos usuarios, dispositivos y aplicaciones** sin tener que rediseñar toda la infraestructura.

```text
Red existente
     │
     ├── LAN 1
     ├── LAN 2
     │
     └── + Nueva LAN
```

La red puede expandirse manteniendo su funcionamiento y rendimiento.

---

## 🚦 Calidad de servicio (QoS)

La **calidad de servicio (QoS)** permite **administrar y priorizar el tráfico de red**, especialmente cuando existe congestión.

### Congestión

La **congestión** ocurre cuando la demanda de tráfico supera el **ancho de banda disponible**.

```text
Tráfico solicitado  ███████████████
Ancho de banda      █████████
                         ↑
                     Congestión
```

Cuando llega más tráfico del que la red puede transportar, los dispositivos pueden colocar temporalmente los **paquetes en una cola** hasta disponer de recursos para transmitirlos.

### 🎯 Priorización del tráfico

No todo el tráfico tiene la misma prioridad.

QoS permite dar preferencia a comunicaciones sensibles al retraso:

| Tráfico | Prioridad |
|---|---|
| 📞 Voz sobre IP (VoIP) | Alta |
| 🎥 Tráfico en tiempo real | Alta |
| 🌐 Navegación web | Menor |

Por ejemplo, ante una congestión, un router puede **priorizar una llamada VoIP sobre la carga de una página web**, ya que los retrasos afectan mucho más a una conversación en tiempo real.

```text
             Router
               │
      ┌────────┴────────┐
      ▼                 ▼
📞 VoIP              🌐 Web
Prioridad alta       Prioridad menor
```
