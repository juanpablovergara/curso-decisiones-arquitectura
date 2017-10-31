### Arquitectura vs diseño



### Atributos de calidad y decisiones de arquitectura
- ISO 9126 - ISO 25000
- Functional Suitability
- **Performance efficiency**
	- ¿Uso de la memoria?
	- ¿Uso del ancho de banda?
	- ¿Uso del procesador?
	- Tiempos de respuesta [Latencia]
- Compatibility
- Usability
- **Reliability**
	- Disponibilidad
	- Consistencia
- **Security**
	- Autentiación
	- Autorización
	- Cifrado
- Maintainability
	- ¿Lenguaje de programación?
- Portability

#### Estilos y patrones arquitectónicos
- Estilo arquitectónico REST
- Definición: Fielding, 2000 https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm --> El paper.
- Derivación: null. Client/Server. Stateless. Cache. Uniform Interface. Layered System. Code on Demand. 
- Restricciones: Identificación de recursos. Manipulación de recursos con representaciones. Mensajes auto-descriptivos. HATEOAS.

Tipos de hipermedia y sus diferentes capacidades (affordances)
- Una cosa es el formato y otra cosa es la estructura
- Formatos: txt, json, xml, yml
- ¿Qué puede representarse en esos formatos? 
- Estructuras: Collection+json, HAL, Siren+json, JSON API, 
- ¿Cómo medir la capacidad de hypermedia? El factor H: http://amundsen.com/hypermedia/hfactor/ 

Evolución del estilo
- Fielding, 2017 https://static.googleusercontent.com/media/research.google.com/es//pubs/archive/46310.pdf --> El paper nuevo

- Patrón arquitectónico CQRS
	- C -> Command -> Comando
		- Orden al sistema
		- Verbos en infinitivo (ar, er, ir)
		- Ejecución sincrónica o asíncrona
	- Q -> Query -> Consulta
		- Consulta al estado del sistema
		- Ejecucíón sincrónica casi siempre
		- En algunas ocasiones ejecución asincrónica (consulta de payloads muy grandes o muy latentes -smell-)

### Integración

- DDD Estratégico
	- Open Host Language (OHS)
	- Published Language
	- Anticorruption Layer (ACL)
	- Customer Supplier
	- Partnership
	- Conformist
	- Shared Kernel
- EIP (Enterprise Integration Patterns). http://www.enterpriseintegrationpatterns.com/patterns/messaging/MessageBroker.html
	- Estilos de integración
	- Sistemas de mensajería
	- Canales de mensajería
	- Construcción de mensajes
	- Enrutamiento de mensajes
	- Transformación de mensajes
	- Messaging endpoints
- Message Broker. Patrón de EIP (Categoría Enrutamiento de mensajes)
- Sistemas de colas
	- Protocolos: TCP, AMQP 0.9, AMQP 1.X MQTT, STOMP
	- Productos: Apache Kafka, RabbitMQ, HornetMQ, IronMQ, ActiveMQ, HornetQ, Beanstalk, SQS, Celery, ...
- AMQP
	- Exchanges: direct, topic, fanout
	- Bindings: con o sin routing key
	- Queues
	- ACK
- RabbitMQ
	- Tolerancia a particiones de red
