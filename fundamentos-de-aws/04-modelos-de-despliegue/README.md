# Modelos de despliegue: pública, híbrida, on-premises

Dónde vive la infraestructura y de quién es.

| Modelo | Qué es | Cuándo conviene |
| --- | --- | --- |
| **Nube pública** | Todo corre en el proveedor (AWS). Infraestructura compartida, recursos aislados por cliente. | Proyectos nuevos, demanda variable, querer moverse rápido. |
| **Híbrida** | Parte en tu datacenter y parte en la nube, conectadas (VPN, Direct Connect). | Migraciones graduales, datos que por regulación deben quedar en casa. |
| **On-premises (nube privada)** | Todo en infraestructura propia, dedicada a tu organización. | Requisitos legales estrictos o inversión ya hecha en hardware. |

```
On-premises            Híbrida                        Pública
[ Tu datacenter ]      [ Tu datacenter ]⇄[ AWS ]      [ AWS ]
```

**Idea clave:** no es todo o nada. Muchas empresas viven en híbrido durante años mientras migran.
