# Fundamentos de AWS y Cloud Computing

Antes de tocar un servicio de AWS conviene entender **qué problema resuelve la nube** y **con qué vocabulario se habla de ella**. Este proyecto explica ese vocabulario (on-premise, IaaS/PaaS/SaaS/FaaS, CAPEX/OPEX, escalabilidad, alta disponibilidad, responsabilidad compartida) y lo aterriza en cuatro servicios concretos: **EC2, RDS, Lambda y S3**.

No hay código: todo son conceptos, diagramas y errores típicos.

```
ON-PREMISE                                    CLOUD (AWS)
──────────                                    ───────────
Comprás servidores  ──► los instalás          Pedís un recurso  ──► en minutos
Pagás todo antes        en tu datacenter      Pagás por lo que usás
Vos hacés todo                                AWS opera el hardware
        │                                              │
        ▼                                              ▼
 Capacidad fija (sobra o falta)               Capacidad que crece y se achica
```

## Conceptos clave

| Concepto | Qué es |
| --- | --- |
| **On-premise** | Infraestructura propia, en tu edificio o datacenter. Vos comprás, instalás, operás y reemplazás todo. |
| **Cloud computing** | Usar recursos de cómputo, almacenamiento y red de un proveedor, por internet, a demanda y pagando por uso. |
| **Región** | Zona geográfica de AWS (ej. São Paulo, Virginia). Contiene varias AZ. |
| **Zona de disponibilidad (AZ)** | Uno o más datacenters aislados dentro de una región, con energía y red propias. |
| **IaaS** | Te dan la infraestructura (servidores virtuales, redes, discos). Vos ponés SO y aplicación. |
| **PaaS** | Te dan la plataforma lista. Vos ponés tu aplicación y tus datos. |
| **SaaS** | Te dan el software terminado. Vos lo usás. |
| **FaaS** | Te dan un lugar donde correr funciones sueltas, disparadas por eventos. |
| **Nube pública / privada / híbrida** | De quién es la infraestructura y quién la comparte. |
| **CAPEX** | Gasto de capital: inversión grande al inicio (comprar servidores). |
| **OPEX** | Gasto operativo: pago recurrente por uso (la factura mensual). |
| **TCO** | Costo total de propiedad: todo lo que cuesta tener algo funcionando, no solo el precio de lista. |
| **Escalabilidad vertical** | Hacer más grande la máquina que ya tenés. |
| **Escalabilidad horizontal** | Sumar más máquinas. |
| **Alta disponibilidad (HA)** | El sistema se recupera rápido ante una falla; puede haber una interrupción corta. |
| **Tolerancia a fallos (FT)** | El sistema sigue funcionando sin interrupción aunque falle un componente. |
| **Responsabilidad compartida** | AWS se encarga *de* la nube; vos de lo que ponés *en* la nube. |

## Los modelos de servicio de un vistazo

Cuanto más arriba en la lista, más cosas hacés vos. Cuanto más abajo, más hace el proveedor.

```
              On-premise    IaaS (EC2)    PaaS (RDS)    FaaS (Lambda)   SaaS
Tu código/datos    Vos         Vos           Vos            Vos          Vos (solo datos)
Aplicación         Vos         Vos           Vos            Vos          Proveedor
Runtime / motor    Vos         Vos           Proveedor      Proveedor    Proveedor
Sistema operativo  Vos         Vos           Proveedor      Proveedor    Proveedor
Virtualización     Vos         Proveedor     Proveedor      Proveedor    Proveedor
Hardware y red     Vos         Proveedor     Proveedor      Proveedor    Proveedor
Datacenter         Vos         Proveedor     Proveedor      Proveedor    Proveedor
```

> La frontera exacta varía según el servicio. Es una guía, no una regla absoluta (ver `implementaciones/08`).

## Los cuatro servicios de ejemplo

| Servicio | Qué es | Modelo | Escala | Ejemplo de uso |
| --- | --- | --- | --- | --- |
| **EC2** | Servidores virtuales | IaaS | Vertical y horizontal | Una API propia, un servidor con configuración a medida |
| **RDS** | Bases de datos relacionales administradas | PaaS | Vertical (+ réplicas de lectura) | PostgreSQL o MySQL sin administrar el servidor |
| **Lambda** | Funciones que corren ante un evento | FaaS | Horizontal automática | Procesar una imagen cuando se sube a S3 |
| **S3** | Almacenamiento de objetos | Servicio administrado | Prácticamente ilimitada | Archivos, backups, sitios estáticos, data lake |

## Errores comunes

### 1. Creer que la nube siempre es más barata
Pasar de CAPEX a OPEX no baja el costo por sí solo. Un servidor encendido 24/7 durante años puede salir más caro que uno propio. → Comparar con TCO, no con el precio por hora.

### 2. Confundir alta disponibilidad con tolerancia a fallos
Tener dos copias no significa que nunca se corte. Una base Multi-AZ tarda un rato en conmutar: es HA, no FT. → Definir cuánta interrupción tolera el negocio.

### 3. Creer que AWS se encarga de todo
AWS protege el datacenter; no protege tus contraseñas, tus permisos ni tus datos. → Saber qué parte es tuya en cada servicio.

### 4. Escalar vertical y esperar que no tenga techo
Una máquina más grande tiene un límite, cuesta más que proporcionalmente y suele requerir un reinicio. → Diseñar para escalar horizontal cuando se pueda.

### 5. Dejar un bucket de S3 público
Es la fuente clásica de filtraciones de datos. → Bloquear el acceso público salvo que haya un motivo claro.

### 6. Usar Lambda para todo
Tiene límite de duración, arranques en frío y puede salir caro con tráfico constante y alto. → Elegirla por el patrón de uso, no por moda.

### 7. RDS sin Multi-AZ ni backups
Una sola instancia es un punto único de falla. → Multi-AZ para disponibilidad, backups para recuperar datos: son cosas distintas.

### 8. Recursos olvidados
Instancias encendidas, discos sin usar, IPs sin asociar. Se siguen cobrando. → Etiquetar y revisar.

### 9. No medir costos
La factura llega a fin de mes. → Presupuestos y alertas desde el día uno.

## Estructura

- [`implementaciones/`](implementaciones): cada tema explicado con un diagrama y ejemplos.
  1. [`01-on-premise`](implementaciones/01-on-premise): cómo era antes y qué problemas tenía.
  2. [`02-cloud-computing`](implementaciones/02-cloud-computing): qué es, sus características y la infraestructura global de AWS.
  3. [`03-iaas-paas-saas-faas`](implementaciones/03-iaas-paas-saas-faas): los modelos de servicio.
  4. [`04-nube-publica-privada-hibrida`](implementaciones/04-nube-publica-privada-hibrida): modelos de despliegue.
  5. [`05-capex-opex-tco`](implementaciones/05-capex-opex-tco): cómo cambia el modelo económico.
  6. [`06-escalabilidad`](implementaciones/06-escalabilidad): vertical vs horizontal.
  7. [`07-alta-disponibilidad-vs-tolerancia-a-fallos`](implementaciones/07-alta-disponibilidad-vs-tolerancia-a-fallos): dos formas de resistir fallas.
  8. [`08-responsabilidad-compartida`](implementaciones/08-responsabilidad-compartida): quién cuida qué.
  9. [`09-ec2`](implementaciones/09-ec2): servidores virtuales.
  10. [`10-rds`](implementaciones/10-rds): bases de datos administradas.
  11. [`11-lambda`](implementaciones/11-lambda): funciones sin servidor.
  12. [`12-s3`](implementaciones/12-s3): almacenamiento de objetos.
- [`errores/`](errores): cada error común, cómo se ve y cómo se evita.
  1. [`01-la-nube-siempre-es-mas-barata`](errores/01-la-nube-siempre-es-mas-barata)
  2. [`02-confundir-ha-con-tolerancia-a-fallos`](errores/02-confundir-ha-con-tolerancia-a-fallos)
  3. [`03-creer-que-aws-se-encarga-de-todo`](errores/03-creer-que-aws-se-encarga-de-todo)
  4. [`04-escalar-vertical-y-esperar-infinito`](errores/04-escalar-vertical-y-esperar-infinito)
  5. [`05-bucket-s3-publico`](errores/05-bucket-s3-publico)
  6. [`06-lambda-para-todo`](errores/06-lambda-para-todo)
  7. [`07-rds-sin-multi-az-ni-backups`](errores/07-rds-sin-multi-az-ni-backups)
  8. [`08-recursos-olvidados-y-ebs`](errores/08-recursos-olvidados-y-ebs)
  9. [`09-no-medir-costos`](errores/09-no-medir-costos)

## Plan del proyecto

1. **Cuenta de AWS**: crear una cuenta con presupuesto y alerta de costos antes de lanzar nada.
2. **EC2**: lanzar una instancia, cambiarle el tamaño y ver qué pasa al detenerla.
3. **S3**: crear un bucket, subir archivos y revisar sus permisos.
4. **RDS**: crear una base, activar Multi-AZ y probar un failover.
5. **Lambda**: disparar una función desde un evento de S3.
6. **Romperlo a propósito**: reproducir los errores de arriba en un entorno de prueba.

> Los límites, regiones y precios de AWS cambian. Para cifras actuales, la fuente es la documentación oficial de AWS.
