# Examen Redes



## Índice

1. [El Mural de las Siete Capas](#el-mural-de-las-siete-capas)
2. [Los Dos Pergaminos del Mensajero](#los-dos-pregaminos-del-mensajero)
3. [El Enigma de las Subredes](#el-enigma-de-las-subredes)
4. [La Encrucijada de las Rutas](#la-encrucijada-de-las-rutas)
5. [El Guardián de la Máscara Única](#el-guardian-de-la-mascara-unica)

---

## El Mural de las Siete Capas

El mural es una representación simbólica del modelo OSI (Open Systems Interconnection), que divide el proceso de comunicación en siete capas, cada una con funciones específicas para transmitir datos de un punto a otro. A continuación, se presenta cada capa:

1. **Capa Física**  
   Representa la transmisión de bits a través de medios físicos (como cables o señales inalámbricas). Es la base que convierte la información en señales eléctricas, ópticas o de radio.

2. **Capa de Enlace de Datos**  
   Se encarga de la transmisión de tramas de datos entre nodos conectados físicamente, gestionando errores y control de flujo. Asegura la integridad de los datos al llegar a su destino inmediato.

3. **Capa de Red**  
   Determina el enrutamiento y direccionamiento de los datos para que puedan viajar a través de múltiples redes. Es responsable de la entrega correcta de paquetes, gestionando la ruta más adecuada.

4. **Capa de Transporte**  
   Asegura la transmisión fiable y ordenada de los datos entre extremos. Realiza funciones de segmentación, control de errores y control de flujo, permitiendo que la comunicación sea robusta.

5. **Capa de Sesión**  
   Establece, gestiona y termina sesiones de comunicación entre aplicaciones. Organiza la comunicación y mantiene el estado de la conexión durante el intercambio de información.

6. **Capa de Presentación**  
   Se encarga de la traducción, cifrado y compresión de los datos. Actúa como “traductor” para que la información se entienda en el formato correcto en el destino.

7. **Capa de Aplicación**  
   Es la más cercana al usuario final, proporcionando servicios y aplicaciones que permiten la interacción directa con el sistema (como correo electrónico, navegación web, etc.).

### TCP/IP vs OSI

- **TCP/IP**  
  Consta de 4 capas (Acceso a la Red, Internet, Transporte y Aplicación). Es un conjunto de protocolos prácticos y probados que sustentan la Internet moderna, combinando funciones que en OSI están separadas.
- **Complementariedad**  
  Mientras OSI ayuda a entender el proceso de comunicación de forma conceptual, TCP/IP lo implementa de manera efectiva en la práctica.

---

## Los Dos Pergaminos del Mensajero

### TCP (Mensajero Confiable)

- Inicia con un “saludo de tres pasos” (SYN, SYN-ACK, ACK) para establecer una conexión confiable.
- Se envían los datos y se espera confirmación, garantizando la fiabilidad y el orden.
- Este método introduce mayor latencia y utiliza más recursos.

### UDP (Mensajero Veloz)

- Envía los datos de manera inmediata, sin protocolo de establecimiento de conexión.
- Permite una transmisión rápida y con baja latencia.
- No ofrece garantía de entrega ni preserva el orden de los datos.

---

## El Enigma de las Subredes

Para dividir la red `192.168.50.0/24` en 4 subredes iguales se deben tomar 2 bits del campo de host para la parte de subred, lo que modifica la máscara a `/26` (255.255.255.192).

- La red original `/24` tiene 256 direcciones (0 a 255).
- Al tomar 2 bits, se crean 2² = 4 subredes.
- Cada subred tendrá 256/4 = 64 direcciones.
- De estas 64 direcciones, se restan 2 (identificador de red y dirección de broadcast), dejando 62 direcciones de host utilizables por subred.

---

## La Encrucijada de las Rutas

El tótem simboliza el proceso de enrutamiento en redes modernas, representado a través de la tabla de enrutamiento de un router. Esta tabla funciona como un mapa interno que contiene rutas o "flechas" que indican el camino óptimo para el tránsito de los datos.

### Tabla de Enrutamiento

- Es una base de datos que almacena rutas a diferentes redes.
- Cada entrada indica la dirección de destino, la máscara de red y la puerta de enlace o interfaz por la cual se debe enviar el paquete.
- Cuando un router recibe un paquete, consulta su tabla para determinar la ruta óptima y reenvía el paquete hacia su destino final.

### Enrutamiento Estático vs. Dinámico

- **Flechas Talladas en Piedra (Enrutamiento Estático)**  
  - Configuradas manualmente por un administrador.
  - No cambian a menos que se modifiquen manualmente.
  - Son confiables y predecibles, ideales para redes pequeñas o con topología estable.
  - Requieren intervención manual para ajustarse a cambios en la red.

- **Flechas Móviles (Enrutamiento Dinámico)**  
  - Se ajustan automáticamente mediante protocolos de enrutamiento (por ejemplo, OSPF, RIP o BGP).
  - Se actualizan en tiempo real en función de los cambios en la topología de la red.
  - Permiten seleccionar siempre la mejor ruta disponible.
  - Reducen la necesidad de intervención manual, aunque requieren una configuración más compleja y recursos adicionales.

---

## El Guardián de la Máscara Única

Este concepto se refiere al **Network Address Translation (NAT)**, en particular al NAT de sobrecarga o enmascaramiento.

### Funcionamiento de NAT

- Permite que múltiples dispositivos internos, con direcciones IP privadas, compartan una única dirección IP pública al comunicarse con el exterior.
- Cuando un dispositivo interno envía un paquete, el router NAT reemplaza la dirección IP privada por la dirección IP pública.
- Además, asigna un número de puerto específico para rastrear cada conexión.
- El router mantiene una tabla de traducción que asocia cada conexión saliente (dirección privada y puerto) con la dirección pública y el puerto asignado.
- Así, al recibir una respuesta, el router consulta la tabla y reenvía el paquete al dispositivo interno correcto.

### Beneficios de NAT

- Permite que muchas máquinas compartan una única dirección IP pública, algo fundamental debido a la limitación del espacio IPv4.
- Incrementa la seguridad, ya que al ocultar las direcciones internas, reduce la exposición de la red a posibles ataques.
