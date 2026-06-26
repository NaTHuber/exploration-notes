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

El pensamiento análitico es uno de los ejes que permite entender la data del proyecto y negocio que se está usando, ya que toda transformación analítica empieza identificando **la entidad, la granularidad y la regla de unicidad de cada tabla.**. Por ejemplo una query que ayudaría a identificar que `order_id` realmente identifica una fila única de la tabla `orders` es la siguiente:

```sql
select
  order_id,
  count(*) as rows_per_order
from orders
group by order_id
having count(*) > 1;
```

## 2. Modelado de datos

Es muy importante definir un modelo de datos en donde las tablas queden organizadas para que el modelo sea confiable, entendible y reutilizable. El enfoque dimensional nos brinda:

- **Tablas de hechos:** Eventos medibles del negocio. 
- **Tablas de dimensiones:** Describen entidades del negocio. 

Una tabla de hechos suele tener métricas numéricas y llaves hacia dimensiones. 

Algunos de los conceptos clave importantes son:

- Entidad
- Granularidad
- Llave primaria
- Llave foránea
- Modelo estrella
- Data mart
- Capa semántica
- Métrica aditiva, semi-aditiva y no aditiva


## 3. Calidad de datos y validación

































