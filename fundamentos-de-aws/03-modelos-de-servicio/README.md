# Modelos de servicio: IaaS, PaaS, SaaS, FaaS

Cuánto gestionás vos y cuánto el proveedor.

| Modelo | Qué te dan | Qué ponés vos | Ejemplo en AWS |
| --- | --- | --- | --- |
| **IaaS** | Servidores virtuales, redes, discos | SO, runtime, app, datos | EC2 |
| **PaaS** | Plataforma lista para usar | App y datos | RDS, Elastic Beanstalk |
| **FaaS** | Un lugar para correr funciones ante eventos | Código de la función | Lambda |
| **SaaS** | Software terminado | Solo tus datos y configuración | Amazon WorkMail, Gmail (fuera de AWS) |

```
              IaaS (EC2)   PaaS (RDS)   FaaS (Lambda)   SaaS
Datos          Vos          Vos          Vos             Vos
Aplicación     Vos          Vos          Vos             Proveedor
Runtime        Vos          Proveedor    Proveedor       Proveedor
SO             Vos          Proveedor    Proveedor       Proveedor
Hardware       Proveedor    Proveedor    Proveedor       Proveedor
```

**Idea clave:** a más abstracción, menos control pero también menos trabajo operativo. Elegí según cuánto necesitás controlar.
