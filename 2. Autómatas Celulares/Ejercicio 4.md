# Análisis de Diagramas de Voronoi – Fómeque

## Introducción

En este documento se realiza un análisis espacial utilizando diagramas de Voronoi aplicados a tres tipos de servicios en el municipio de Fómeque:

- Droguerías  
- Hospitales  
- Colegios  

El diagrama de Voronoi divide el espacio en regiones donde cada punto pertenece al servicio más cercano. Esto permite evaluar cobertura, centralización y posibles necesidades de expansión.

---

# 1. Análisis de Droguerías

## Diagrama de Voronoi – Droguerías

![Voronoi Droguerías1](images/voronoi fome1.PNG)

![Voronoi Droguerías2](images/voronoi comp1.PNG)

## Observaciones

- Las droguerías están concentradas en el centro urbano.
- Se observan regiones de Voronoi amplias en sectores periféricos.
- Existe sobreconcentración en el eje central del municipio.

## Interpretación

En un diagrama de Voronoi:

- Regiones grandes → menor cobertura espacial.
- Regiones pequeñas → mayor densidad de servicio.

El diagrama muestra:
- Alta competencia en el centro.
- Baja cobertura en sectores oriental y suroccidental.

## Conclusión

Podría faltar una droguería en:
- Zona oriental.
- Sector suroccidental.

Una nueva ubicación reduciría el tamaño de las regiones grandes y equilibraría la cobertura territorial.

---

# 2. Análisis de Hospitales

## Diagrama de Voronoi – Hospitales

![Voronoi Hospitales](/images/hospitales.png)

## Observaciones

- Solo existe un hospital principal.
- El diagrama muestra una única región que cubre todo el municipio.

## Interpretación

Cuando solo hay un generador:

- Todo el plano pertenece a ese servicio.
- No existe competencia espacial.
- Se evidencia centralización total.

Esto implica:
- Dependencia estructural.
- Posible vulnerabilidad ante emergencias.
- Mayor distancia promedio en zonas periféricas.

## Conclusión

Desde el punto de vista espacial, sería recomendable considerar un segundo centro de atención básica en sectores periféricos (occidente o norte) para mejorar cobertura y tiempos de respuesta.

---

# 3. Análisis de Colegios

## Diagrama de Voronoi – Colegios

![Voronoi Colegios](/images/colegios.png)

## Observaciones

- Existen al menos dos instituciones educativas.
- Las regiones están más balanceadas que en el caso hospitalario.
- Sectores periféricos presentan regiones más amplias.

## Interpretación

- Cobertura relativamente equilibrada.
- Mejor distribución que hospitales.
- Aún existen zonas con menor proximidad.

## Conclusión

No es una necesidad crítica, pero podría considerarse una institución adicional en zonas periféricas para optimizar la cobertura educativa.

---

# Comparación General

| Servicio     | Distribución            | Cobertura Territorial | Necesidad de Expansión |
|--------------|------------------------|------------------------|------------------------|
| Droguerías  | Concentradas en centro | Media                  | Moderada               |
| Hospital    | Altamente centralizado | Baja                   | Alta                   |
| Colegios    | Relativamente balanceado | Media-Alta           | Baja-Moderada          |

---

# Conclusión General

El análisis mediante diagramas de Voronoi permite visualizar la distribución espacial de los servicios y detectar posibles desigualdades en cobertura.

- Se recomienda evaluar la expansión de servicios de salud.
- Las droguerías podrían redistribuirse estratégicamente.
- Los colegios presentan mejor equilibrio, aunque aún optimizable.

Los diagramas de Voronoi constituyen una herramienta geométrica útil para la planificación urbana y la toma de decisiones territoriales.
