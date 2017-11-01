### Arquitectura vs diseño (Dia 1. Sesión 1) (2h)



### Atributos de calidad y decisiones de arquitectura (Día 1. Sesión 2) (2h)
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
	- Autenticación
	- Autorización
	- Cifrado
- Maintainability
	- ¿Lenguaje de programación?
- Portability

### Estilos y patrones arquitectónicos (Día 2. Sesión 1 y 2) (4h)
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

### Integración (Día 3. Sesión 1 y 2) (4h)

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

### Persistencia (Día 4. Sesión 1)

- Elementos de arquitectura
	- Transacciones. Protocolos de commit (Two phase commit)
	- Consistencia
	- Pool de conexiones. Análisis sobre cómo usar correctamente un pool de conexiones -> https://github.com/brettwooldridge/HikariCP/wiki/About-Pool-Sizing
- Elementos de diseño
	- Repositorios
	- DAOs y DTOs
	- Event sourcing.
		- Descripción de Martin Fowler en 2005. https://martinfowler.com/eaaDev/EventSourcing.html
		- Descripción de Microsoft en 2017. https://docs.microsoft.com/en-us/azure/architecture/patterns/event-sourcing
		- Descripción de Chris Richardson en 2017 http://microservices.io/patterns/data/event-sourcing.html
		- Argumentación de cuándo usarlo de Vernon en 2017 https://forcomprehension.com/2017/10/30/to-event-source-or-not/
		

