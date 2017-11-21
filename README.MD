### Arquitectura vs diseño (Dia 1. Sesión 1) (4h)
- El conjunto de habilidades de arquitectura y de diseño detallado son complementarios.
- Arquitectura: 
	- Qué componentes / desplegables debe tener el sistema.
	- Cómo se deben relacionar dichos componentes.
		- Protocolos 
		- APIs
		- Sincronía / Asincronía
		- Consistencia
		- Seguridad
	- DDD Estratégico
		- Identificación / Descubrimiento / Destilamiento de eventos de negocio
		- Identificación / Descubrimiento / Destilamiento de lenguajes ubicuos
		- Identificación / Descubrimiento / Destilamiento de contextos delimitados
		- Elaboración de mapa de contextos
		- Identificación de estrategias de integración entre contextos (Ver sección de Integración)
- Diseño:
	- Pradigma de programación
		- OOP
		- FP
	- DDD Táctico:
		- Sustantivos del negocio: Entidades. Agregados. Objetos de valor.
		- Comportamientos del negocio: Servicios del dominio.
		- Interacción del dominio con el mundo exterior: Servicios de aplicación.

### Atributos de calidad y decisiones de arquitectura (Día 2. Sesión 1) (2h)
- ISO 9126 - ISO 25000
	- Functional Suitability
	- **Performance efficiency**
		- ¿Uso de la memoria?
		- ¿Uso del ancho de banda?
		- ¿Uso del procesador?
		- Tiempos de respuesta [Latencia]
		- High Performance Browser Applications https://hpbn.co/
	- Compatibility
	- Usability
	- **Reliability**
		- Resiliencia
		- ¿Cómo se comporta el sistema ante una partición de red? 
			- ¿Se pierden datos? (en una BD)
			- ¿Se pierden mensajes? (en un broker)
			- ¿Se duplican mensajes? (en un broker)
		- Disponibilidad
			¿Qué es disponibilidad? ¿Número de requests atendidos con éxito?
			¿Qué es atender con éxito? ¿Una respuesta lenta es considerada exitosa?
			Posibles resultados a un request: malo, meehhh, ok.
			Application Performance Index = Apdex	
			Apdex = P(Ok) + P(meeeh) / 2
		- Consistencia
			Linearizabilidad y Serializabilidad: http://www.bailis.org/blog/linearizability-versus-serializability/
			*Linearizabilidad* single-operation, single-object, real-time order2
			*Serializabilidad* multi-operation, multi-object, arbitrary total order
	- **Security**
		- Autenticación
		- Autorización
		- Cifrado
		- Tokenización
		- Manejo de secretos
	- Maintainability
		- ¿Lenguaje de programación?
	- Portability

	CAP
	- C -> Consistency (igual a Linearizability)
	- A -> Availability (every request received by a non-failing node in the system must result in a response)
	- P -> Partition tolerance
	
	ACID
	- A -> Atomic
	- C -> Consistent (Correctness)
	- I -> Isolated (Serializability)
	- D -> Durable 

### Estilos y patrones arquitectónicos (Día 2. Sesión 2 y  Día 3. Sesión 1) (4h)
- Estilo arquitectónico REST
	- Definición: Fielding, 2000 https://www.ics.uci.edu/~fielding/pubs/dissertation/rest_arch_style.htm --> El paper.
	- Derivación: null. Client/Server. Stateless. Cache. Uniform Interface. Layered System. Code on Demand. 
	- Restricciones: Identificación de recursos. Manipulación de recursos con representaciones. Mensajes auto-descriptivos. HATEOAS.

	- Tipos de hypermedia y sus diferentes capacidades (affordances)
		- Una cosa es el formato y otra cosa es la estructura
		- Formatos: txt, json, xml, yml
		- ¿Qué puede representarse en esos formatos? 
		- Estructuras: Collection+json, HAL, Siren+json, JSON API, 
		- ¿Cómo medir la capacidad de hypermedia? El factor H: http://amundsen.com/hypermedia/hfactor/ 

	- Evolución del estilo
	- Fielding, 2017 https://static.googleusercontent.com/media/research.google.com/es//pubs/archive/46310.pdf --> El paper nuevo

- Patrón arquitectónico CQRS
	- Greg Young: "A single model cannot be appropriate for reporting, searching and transactional behaviours…" 
	- C -> Command -> Comando
		- Orden al sistema
		- Verbos en infinitivo (ar, er, ir)
		- Ejecución sincrónica o asíncrona
	- Q -> Query -> Consulta
		- Consulta al estado del sistema
		- Ejecucíón sincrónica casi siempre
		- En algunas ocasiones ejecución asincrónica (consulta de payloads muy grandes o con altas latencias -smell-)

- Patrón puertos y adaptadores
	- Definición por Alistair Cockburn http://alistair.cockburn.us/Hexagonal+architecture
	- Referenciado por Vernon en Implementing Domain Driven Design en el capítulo de arquitectura
	- Puerto: Procotolo (generalmente de capa 7 OSI)
	- Adaptador: 

### Integración (Día 3. Sesión 2 y Día 4. Sesión 1) (4h)

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
	- Descripción de lo que pasa en RabbitMQ ante una partición de red. Aphyr en 2014: https://aphyr.com/posts/315-jepsen-rabbitmq

### Persistencia (Día 4. Sesión 2 y Dia 5. Sesión 1) (4h)

- Elementos de arquitectura
	- Líder. Multilíder. Sin líder. Efectos en consistencia.
	- Transacciones. Protocolos de commit (Two phase commit)
	- Consistencia
	- Pool de conexiones. Análisis sobre cómo usar correctamente un pool de conexiones -> https://github.com/brettwooldridge/HikariCP/wiki/About-Pool-Sizing
- Elementos de diseño
	- Repositorios, DAOs y DTOs
	- Event sourcing.
		- Documentación de Event Store (Greg Young) https://eventstore.org/docs/introduction/4.0.0/event-sourcing-basics/
		- Descripción de Martin Fowler en 2005. https://martinfowler.com/eaaDev/EventSourcing.html
		- Descripción de Microsoft en 2017. https://docs.microsoft.com/en-us/azure/architecture/patterns/event-sourcing
		- Descripción de Chris Richardson en 2017 http://microservices.io/patterns/data/event-sourcing.html
		- Argumentación de cuándo usarlo de Vernon en 2017 https://forcomprehension.com/2017/10/30/to-event-source-or-not/
		- Event sourcing como anti patrón. Jan Stenberg en 2016 https://www.infoq.com/news/2016/04/event-sourcing-anti-pattern
		

### Wrap up (Día 5 . Sesión 2) (2h)