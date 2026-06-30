# Fundamentos de Analytics Engineering 

El objetivo de estas notas es escribir y ordenar los conceptos y fundamentos básicos que considero forman parte del área de Analytics Engineering. 

```mermaid 
    graph LR
    A[1 <br> Pensamiento analítico sobre datos]
    B[2 <br> Modelado de datos]
    C[3 <br> Calidad de datos y validación]
    A --> B
    B --> C
```

## 1. Pensamiento analítico sobre los datos

El pensamiento análitico es uno de los ejes que permite entender la data del proyecto y negocio que se está usando, ya que toda transformación analítica empieza identificando **la entidad, la granularidad y la regla de unicidad de cada tabla.** Por ejemplo una query que ayudaría a identificar que `order_id` realmente identifica una fila única de la tabla `orders` es la siguiente:

```sql
select
  order_id,
  count(*) as rows_per_order
from orders
group by order_id
having count(*) > 1;
```
> **Nota:** Una de las preguntas guía más importantes que se deben hacer es _¿Qué representa una fila en esta tabla?_

Además, SQL debe empezar con una pregunta del negocio, ya que el objetivo es traducir preguntas del negocio a lógica de datos. 
## 2. Modelado de datos

Es muy importante definir un modelo de datos en donde las tablas queden organizadas para que el modelo sea confiable, entendible y reutilizable. El enfoque dimensional nos brinda:

- **Tablas de hechos:** Eventos medibles del negocio. 
- **Tablas de dimensiones:** Describen entidades del negocio. 

Una tabla de hechos suele tener métricas numéricas y llaves hacia dimensiones. 

Algunos de los conceptos importantes son:

- Entidad
- Granularidad
- Llave primaria
- Llave foránea
- Modelo estrella
- Data mart
- Capa semántica
- Métrica aditiva, semi-aditiva y no aditiva

### Reglas importantes 

1. Antes de usar una tabla es importante definir yentender qué representa una fila 
2. No se deben hacer joins entre tablas sin antes entender si la relaciones son one-to-one, one-to-many, o many-to-may
3. Es importante no suamr o calcular métricas de un jpin si no se está segura si hay duplicidad de información. 
4. Una métrica es válida solo dentro de una **granularidad bien definidad** 
5. Se pueden reconciliar métricas entre niveles para poder veficar que los número cuadren. 

### Tipos básicos de joins
- `inner join`: conserva solo coincidencias en ambas tablas 
- `left join`: conserva todo lo de la tabla izquierda y agrega lo que coincida de la derecha
- `full outer join`: conserva todo de ambas tablas
- `cross join`: combina todo con todo

## 3. Calidad de datos y validación

## 4. Métricas de negocio

## 5. Arquitectura analítica por capas
































