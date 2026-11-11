# Modelo de responsabilidad compartida

- **AWS: seguridad *de* la nube** → datacenters, hardware, red física, virtualización.
- **Vos: seguridad *en* la nube** → tus datos, usuarios y permisos (IAM), configuración, cifrado.

La línea se mueve según el servicio: cuanto más administrado, más hace AWS.

## Cómo cambia por servicio

| | **EC2** (IaaS) | **RDS** (PaaS) | **Lambda** (FaaS) | **S3** (almacenamiento) |
| --- | --- | --- | --- | --- |
| Hardware e infraestructura | AWS | AWS | AWS | AWS |
| Sistema operativo y parches | **Vos** | AWS | AWS | AWS |
| Motor / runtime | **Vos** | AWS (vos elegís la ventana de mantenimiento) | AWS | AWS |
| Red / firewall (security groups) | **Vos** | **Vos** | — (vos si la ponés en una VPC) | — |
| Código / aplicación | **Vos** | — | **Vos** (código y dependencias) | — |
| Permisos (IAM, políticas) | **Vos** | **Vos** (y usuarios de la base) | **Vos** (rol de ejecución) | **Vos** (bucket policies, acceso público) |
| Datos y cifrado | **Vos** | **Vos** | **Vos** | **Vos** |
| Backups / alta disponibilidad | **Vos** | Vos lo activás, AWS lo ejecuta | AWS | AWS (durabilidad); vos activás versionado |

**Idea clave:** AWS nunca se hace cargo de tus datos ni de tus permisos. Un bucket público o un usuario con permisos de más es siempre responsabilidad tuya.
