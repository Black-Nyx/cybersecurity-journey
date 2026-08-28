# 📈 Tendencias de red

Las redes evolucionan para adaptarse a nuevas formas de trabajar, comunicarse y acceder a los servicios.

Entre las principales tendencias se encuentran:

- **BYOD**
- **Colaboración en línea**
- **Comunicaciones de video**
- **Computación en la nube**

---

## 📱 BYOD — Bring Your Own Device

**BYOD (Bring Your Own Device)** permite que los usuarios utilicen sus **dispositivos personales** para acceder a recursos de una organización.


```text
📱 Dispositivo personal
        │
        ▼
   Red empresarial
        │
        ▼
Recursos corporativos
```

BYOD facilita el acceso y la movilidad, pero también introduce **riesgos de seguridad**, ya que información corporativa puede almacenarse o consultarse desde dispositivos personales.

---

## ☁️ Computación en la nube

La **computación en la nube (Cloud Computing)** permite acceder a aplicaciones, almacenamiento y otros recursos informáticos a través de una red.

### Tipos de nube

| Tipo | Característica |
|---|---|
| ☁️ **Pública** | Servicios disponibles para múltiples clientes, gratuitos o de pago |
| 🔒 **Privada** | Infraestructura destinada a una única organización |
| 🔀 **Híbrida** | Combina dos o más tipos de nube |
| 👥 **Comunitaria** | Compartida por organizaciones con necesidades similares |

---

# 🏠 Tendencias tecnológicas en el hogar

## 🔌 Redes Powerline

**Powerline** permite transmitir datos utilizando el **cableado eléctrico existente de una vivienda**.

Se utilizan adaptadores Powerline conectados a tomacorrientes para extender la red a lugares donde **Wi-Fi tiene poca cobertura** o instalar Ethernet no es práctico.

```text
Router ── Adaptador ⚡━━ Cableado eléctrico ━━⚡ Adaptador ── PC

```
### Ventajas y desventajas

| ✅ Ventajas | ❌ Desventajas |
|---|---|
| Utiliza el cableado eléctrico existente | Puede sufrir interferencias |
| Útil donde Wi-Fi tiene poca cobertura | El rendimiento depende de la instalación eléctrica |
| No requiere instalar nuevo cableado de red | Generalmente no sustituye a Ethernet en rendimiento |

---

## 📡 Banda ancha inalámbrica

Cuando tecnologías cableadas como cable o DSL no están disponibles, puede utilizarse **banda ancha inalámbrica**.

Un **WISP (Wireless Internet Service Provider)** proporciona acceso a Internet mediante tecnologías inalámbricas.

Es especialmente útil en **zonas rurales o lugares donde resulta difícil desplegar infraestructura cableada**.

---

# 🔐 Amenazas de seguridad

Las redes pueden estar expuestas tanto a **amenazas externas como internas**.

| Amenaza | Descripción |
|---|---|
| 🕵️ **Spyware** | Recopila información del usuario sin su conocimiento |
| 📢 **Adware** | Software asociado principalmente a la presentación de publicidad y que puede incluir seguimiento |
| ⚠️ **Zero-day** | Explotación de una vulnerabilidad para la que aún no existe una corrección disponible o ampliamente implementada |
| 💥 **DoS** | Busca degradar o impedir el acceso a un sistema o servicio |
| 👤 **Amenazas internas** | Errores, abuso de acceso, dispositivos perdidos/robados o acciones maliciosas desde dentro de la organización |

---

# 🛡️ Soluciones de seguridad

## 🏠 Redes domésticas y pequeñas oficinas

Las medidas básicas incluyen:

- **Antivirus/antimalware:** ayuda a detectar y bloquear software malicioso.
- **Firewall:** controla el tráfico y ayuda a impedir conexiones no autorizadas.

---

## 🏢 Redes empresariales

Las organizaciones suelen aplicar **varias capas de seguridad** en lugar de depender de una única medida.

### 🔥 Firewall

Los **firewalls dedicados** permiten inspeccionar y filtrar grandes cantidades de tráfico mediante políticas de seguridad.

### 📋 ACL — Access Control List

Las **listas de control de acceso (ACL)** establecen reglas para **permitir o denegar determinado tráfico**.

```text
Tráfico ──► ACL ──► ¿Permitido?
                    │
              ┌─────┴─────┐
             Sí           No
              │            │
              ▼            ✕
           Continúa     Bloqueado
```

### 🚨 IPS — Intrusion Prevention System

Un **IPS** analiza el tráfico para **detectar actividad maliciosa y bloquear amenazas**.

### 🔐 VPN — Virtual Private Network

Una **VPN** permite establecer una **conexión protegida a través de una red no confiable, como Internet**, normalmente mediante cifrado y autenticación.

```text
Usuario ──🔒 Túnel VPN 🔒──► Red empresarial
              Internet
```
