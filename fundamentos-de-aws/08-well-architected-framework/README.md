# Well-Architected Framework: los 6 pilares

Buenas prácticas de AWS para diseñar y revisar arquitecturas.

| Pilar | Pregunta que responde | Ejemplo |
| --- | --- | --- |
| **Excelencia operativa** | ¿Cómo operamos y mejoramos el sistema? | Infraestructura como código, monitoreo, cambios chicos y reversibles. |
| **Seguridad** | ¿Cómo protegemos datos y sistemas? | Mínimo privilegio en IAM, cifrado, trazabilidad (CloudTrail). |
| **Fiabilidad** | ¿Se recupera ante fallas y cumple lo esperado? | Multi-AZ, backups probados, recuperación automática. |
| **Eficiencia del rendimiento** | ¿Usamos los recursos adecuados para la carga? | Elegir el tipo de instancia correcto, serverless, caché. |
| **Optimización de costos** | ¿Evitamos gastos innecesarios? | Rightsizing, apagar lo ocioso, Savings Plans, etiquetas. |
| **Sostenibilidad** | ¿Minimizamos el impacto ambiental? | Usar solo lo necesario, servicios administrados, regiones eficientes. |

AWS ofrece la herramienta **Well-Architected Tool** en la consola para revisar una carga de trabajo contra estos pilares.

**Idea clave:** los pilares compiten entre sí (ej. más fiabilidad suele costar más). Diseñar bien es elegir el equilibrio correcto.
