### Arquitectura vs diseño



### Atributos de calidad y decisiones de arquitectura
- ISO 9126 - ISO 25000
- Functional Suitability
- **Performance efficiency**
- Compatibility
- Usability
- *Reliability*
- *Security*
- Maintainability
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

Event Sourcing

Message Broker

