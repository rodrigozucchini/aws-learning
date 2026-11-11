# Escalabilidad, elasticidad, alta disponibilidad y tolerancia a fallos

## Escalabilidad

| | **Vertical** (scale up) | **Horizontal** (scale out) |
| --- | --- | --- |
| Qué hace | Hace más grande la máquina | Suma más máquinas |
| Ejemplo | Pasar de `t3.small` a `t3.xlarge` | De 2 a 6 instancias detrás de un load balancer |
| Límite | El tamaño máximo de máquina | Prácticamente ninguno |
| Interrupción | Suele requerir reinicio | No |

```
Vertical:   [ ■ ] → [ ■■■ ]
Horizontal: [ ■ ] → [ ■ ][ ■ ][ ■ ]
```

## Elasticidad
Escalar **automáticamente** hacia arriba y hacia abajo según la demanda (ej. Auto Scaling). Escalabilidad es *poder* crecer; elasticidad es hacerlo solo y también achicarse.

## Alta disponibilidad vs tolerancia a fallos

| | **Alta disponibilidad (HA)** | **Tolerancia a fallos (FT)** |
| --- | --- | --- |
| Qué promete | Recuperarse rápido ante una falla | Seguir funcionando sin interrupción |
| Interrupción | Corta (segundos/minutos) | Ninguna |
| Ejemplo | RDS Multi-AZ: conmuta a la réplica | Varias instancias activas en distintas AZ |
| Costo | Menor | Mayor |

**Idea clave:** HA tolera un corte breve; FT no tolera ninguno. Elegí según cuánta interrupción aguanta el negocio.
