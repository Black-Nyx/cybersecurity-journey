# 🌐 Componentes de red

> En esta sección documento los conceptos que aprendí sobre los componentes básicos de una red: hosts, clientes y servidores, redes entre pares, dispositivos finales e intermediarios y medios de transmisión.

---

## 🖥️ Hosts

Un **host** es cualquier dispositivo conectado a una red que puede **enviar o recibir información**.

Algunos ejemplos de hosts son:

- Computadoras
- Smartphones
- Servidores
- Impresoras de red
- Cámaras IP

Los hosts utilizan direcciones para poder identificarse y comunicarse dentro de una red.


---

## 🗄️ Cliente y servidor

En una arquitectura **cliente-servidor**, un dispositivo solicita información o un servicio y otro se encarga de proporcionarlo.

```text
Cliente  ───── solicitud ─────►  Servidor
Cliente  ◄──── respuesta ─────  Servidor
```
Cliente: solicita y utiliza un servicio.
Servidor: proporciona servicios o información a otros dispositivos de la red.

Los servidores utilizan diferentes tipos de software de servidor dependiendo del servicio que proporcionen.
---

## 🔄 Redes entre pares (Peer-to-Peer)

Una red **Peer-to-Peer (P2P)** es una forma de comunicación en la que **dos o más computadoras se conectan entre sí sin depender de un servidor central dedicado**.

En este tipo de red, cada dispositivo puede funcionar como **cliente y servidor al mismo tiempo**:

- Como **cliente**, puede solicitar recursos.
- Como **servidor**, puede proporcionar recursos a otros dispositivos.

```text
PC A  ◄────────────────►  PC B
Cliente / Servidor        Cliente / Servidor
```

| ✅ Ventajas                               | ❌ Desventajas                                  |
| ----------------------------------------- | ------------------------------------------------ |
| Fácil de configurar                       | La administración no está centralizada           |
| Menor complejidad                         | Menor seguridad                                  |
| Puede tener un menor costo                | No es adecuada para redes muy grandes            |
| Útil para compartir archivos e impresoras | Puede afectar el rendimiento de los dispositivos |

¿Por qué una red P2P no es muy escalable?

Con pocos dispositivos es fácil de utilizar y administrar. Sin embargo, cuando aumenta mucho la cantidad de equipos, se vuelve más difícil controlar usuarios, permisos, recursos y seguridad, ya que no existe un servidor central encargado de administrarlos.

---

## 💻 Dispositivos finales

Los **dispositivos finales** son los equipos que actúan como **origen o destino de los datos** dentro de una red.

Algunos ejemplos son:

- Computadoras
- Notebooks
- Smartphones
- Servidores
- Impresoras de red
- Teléfonos IP
- Cámaras IP

Cuando un dispositivo final inicia una comunicación, utiliza la **dirección del dispositivo de destino** para indicar dónde debe llegar la información.

```text
PC A  ───────────── mensaje ─────────────►  PC B
Origen                                      Destino
```
## 🔀 Dispositivos intermediarios

Los **dispositivos intermediarios** son los equipos que se encargan de **conectar los dispositivos finales** y permitir que los datos puedan viajar a través de la red.

También pueden conectar **diferentes redes entre sí**, formando redes más grandes.

### Algunos ejemplos

<img width="1103" height="315" alt="image" src="https://github.com/user-attachments/assets/115e0eeb-b3be-4169-9b8f-71327d9ea23f" />


```text
PC ───► Switch ───► Router ───► Red ───► Servidor
          ↑            ↑
        Dispositivos intermediarios
```

### ¿Qué funciones pueden realizar?

Dependiendo del dispositivo, pueden:

- **Regenerar y retransmitir señales** de comunicación.
- Determinar por dónde deben continuar los datos.
- Informar sobre **fallas de comunicación**.
- Utilizar una **ruta alternativa** si un enlace falla.
- **Permitir o bloquear tráfico** según reglas de seguridad.

> 💡 **Lo que entendí:** los dispositivos finales son los que originan o reciben la información, mientras que los dispositivos intermediarios están en el medio y ayudan a que esa información pueda llegar hasta su destino.

---

## 🔗 Medios de red

Los **medios de red** son los medios por los cuales se transmite la comunicación entre los dispositivos.

Las redes modernas utilizan principalmente tres tipos:

| Medio | ¿Cómo se transmiten los datos? |
|---|---|
| 🔌 **Cables metálicos** | Impulsos eléctricos |
| 💡 **Fibra óptica** | Pulsos de luz |
| 📡 **Inalámbrico** | Ondas electromagnéticas |

<img width="1127" height="711" alt="image" src="https://github.com/user-attachments/assets/fec437ca-e014-436d-ae81-4a79c4b80b2b" />

---


