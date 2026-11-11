# On-premises y breve historia de AWS

## Qué es on-premises
Tener tus propios servidores, en tu edificio o en un datacenter que alquilás. Vos comprás, instalás, operás y reemplazás todo.

## Problemas

| Problema | Qué significa |
| --- | --- |
| **Inversión inicial grande** | Hay que pagar el hardware antes de usarlo. |
| **Tiempos largos** | Comprar, recibir e instalar un servidor lleva semanas o meses. |
| **Capacidad fija** | Comprás para el pico: el resto del tiempo sobra. Si te quedás corto, falta. |
| **Operación propia** | Energía, refrigeración, red, seguridad física, repuestos: todo es tuyo. |
| **Obsolescencia** | El hardware envejece y hay que renovarlo cada pocos años. |
| **Alcance limitado** | Llegar a otro país implica montar otro datacenter. |

```
Demanda real:   ▁▂▃▅█▅▃▂▁▂▃▆█▆▃▁
Capacidad fija: ████████████████   ← pagás todo esto, usás una parte
```

## Breve historia de AWS
- **Principios de los 2000**: Amazon arma infraestructura interna reutilizable para sus propios equipos.
- **2006**: lanza públicamente **S3** (almacenamiento) y **EC2** (servidores virtuales). Nace AWS como negocio.
- **Después**: suma bases de datos administradas (RDS), funciones sin servidor (Lambda, 2014) y cientos de servicios más.

**Idea clave:** AWS convirtió la infraestructura en algo que se pide por internet y se paga por uso, en lugar de algo que se compra.
