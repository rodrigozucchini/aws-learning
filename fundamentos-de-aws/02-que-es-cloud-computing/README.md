# Qué es cloud computing

Usar cómputo, almacenamiento y red de un proveedor, **por internet**, **a demanda** y **pagando por lo que usás**.

## Las tres características clave

| Característica | Qué significa | Ejemplo |
| --- | --- | --- |
| **Autoservicio** | Pedís recursos vos mismo, sin hablar con nadie. | Lanzar un servidor desde la consola en minutos. |
| **Pago por uso** | Pagás lo que consumís (horas, GB, requests). | Apagás la instancia y deja de cobrarse el cómputo. |
| **Elasticidad** | Los recursos crecen y se achican según la demanda. | Más servidores en Black Friday, menos el lunes. |

## Infraestructura global de AWS
- **Región**: zona geográfica (ej. São Paulo, Virginia). Elegís dónde viven tus recursos.
- **Zona de disponibilidad (AZ)**: uno o más datacenters aislados dentro de una región. Usar varias AZ protege ante la caída de una.
- **Edge locations**: puntos cercanos a los usuarios para servir contenido rápido (CloudFront).

```
Región
├── AZ a  (datacenter/s)
├── AZ b  (datacenter/s)
└── AZ c  (datacenter/s)
```

**Idea clave:** la nube no es "la computadora de otro" a secas; es infraestructura de otro que pedís al instante, pagás por uso y escalás a gusto.
