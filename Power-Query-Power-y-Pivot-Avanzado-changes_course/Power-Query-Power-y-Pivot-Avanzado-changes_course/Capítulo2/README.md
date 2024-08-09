# Diseño de un modelo de datos en Power Pivot y Creación de elementos visuales

En este laboratorio, comenzará a desarrollar el modelo de datos. Esto implicará crear relaciones entre tablas y configurar las propiedades de las tablas y columnas para mejorar la facilidad de uso del modelo de datos. Además, creará jerarquías y definirá medidas para análisis avanzados. Como parte adicional, también diseñará visualmente tablas dinámicas, KPI y gráficos dinámicos para presentar y analizar los datos de manera efectiva.

## Objetivo de la práctica:
Al finalizar la práctica, serás capaz de:
- Crear relaciones
- Configurar propiedades de tablas y columnas
- Crear Jerarquías y KPI
- Crear Tablas Dinámicas
- Crear Gráficos Dinámicos


## Duración aproximada:
- 70 minutos.


### Tarea 1. Creación de relaciones.

- Paso 1. De la cinta superior de opciones, seleccione la pestaña **Power Pivot** y luego, en la sección de **Modelo de datos**, seleccione **Administrar**.

    ![img](./images/imgT1P1.png) 

- Paso 2. En la ventana de Power Pivot, encontrará una pestaña para cada consulta que creamos en el laboratorio anterior. Dentro de cada una de estas pestañas, podrá ver la información correspondiente a los datos que importamos y transformamos previamente.

    ![img](./images/imgT1P2.png) 

- Paso 3. Seleccione en la parte superior, en la cinta de opciones, la pestaña **Inicio**. Luego, en la sección **Ver**, haga clic sobre el elemento **Vista de diagrama**.

    ![img](./images/imgT1P3.png) 

- Paso 4. En la vista actual del modelo, seleccione en la parte superior la pestaña **Diseñar** y luego haga clic en **Administrar relaciones**. Observe que aún no se ha definido ninguna relación. Para crear una relación, seleccione **Nueva relación**.

- Paso 5. Configure la relación de la tabla de Product a la tabla de Sales. 

    > • En la ventana de **Crear relación**, seleccione la tabla **Product** y luego seleccione la columna **ProductKey**.<br>

    > • Luego, en la lista desplegable, seleccione **Sales** y asegúrese de que se resalte la columna **ProductKey** correspondiente. <br>

    > • Asegúrese de que en la parte inferior izquierda esté marcada la casilla de **Activa**.

    ![img](./images/imgT1P5.png) 

- Paso 6. Note que en la vista del modelo, la relación ya aparece creada.

  > • El tipo de cardinalidad es de uno a varios (1:*). La cardinalidad se detectó automáticamente, ya que Power Pivot entiende que la columna **ProductKey** de la tabla **Product** contiene valores únicos. Las relaciones de uno a varios son la cardinalidad más común, y todas las relaciones que cree en este laboratorio serán de este tipo.

  > • El tipo de dirección del filtro cruzado es **Único**.En este caso, significa que los filtros aplicados a la tabla **Product** se propagarán a la tabla **Sales**, pero no en la dirección opuesta.

  > •  Hacer que esta relación esté activa. Las relaciones activas propagan filtros. Es posible marcar una relación como inactiva para que los filtros no se propaguen. Las relaciones inactivas pueden existir cuando hay varias rutas de acceso de relación entre tablas. 

    ![img](./images/imgT1P6.png) 

- Paso 7.  Para crear una nueva relación con una técnica diferente, desde la tabla **Reseller**, arrastre la columna **ResellerKey** a la columna **ResellerKey** de la tabla **Sales**.

    ![img](./images/imgT1P7.png) 

- Paso 8. Utilice la nueva técnica para crear las relaciones siguientes:

  > • Region | SalesTerritoryKey --> Sales | SalesTerritoryKey <br>

  > • Salesperson | EmployeeID --> Targets | EmployeeID


  > • Salesperson | EmployeeKey --> Sales | EmployeeKey 

- Paso 9. En el diagrama, organice las tablas de modo que la tabla **Sales** se coloque en el centro del diagrama y las tablas relacionadas se organicen a su alrededor. Coloque las tablas desconectadas a un lado.

    ![img](./images/imgT1P9.png) 


### Tarea 2. Cargar valores a una tabla dinámicas

- Paso 1. Desde la pestaña superior **Inicio**, seleccione **Tabla dinámica** y luego, nuevamente, haga clic en **Tabla dinámica**.

    ![img](./images/imgT2P1.png) 

- Paso 2. En la ventana que aparece, utilice los valores predeterminados y haga clic en **Aceptar**.

    ![img](./images/imgT2P2.png)  

- Paso 3. Aparecera la tabla dinamica para que pueda agregar los campos que desea mostrar.

    ![img](./images/imgT2P3.png)  

- Paso 4. Seleccione de **Salesperson** | **Salesperson** y de **Sales | Sales**, en automatico crea una suma del campo **Sales**. <br>
Puede agregar tambien los campos de **Unit Price** y **Quantity**

    ![img](./images/imgT2P4.png)  


### Tarea 3. Crear la tabla Fecha

- Paso 1. Cambie a la vista de modelo. En la pestaña de la cinta de opciones **Diseñar**, en el grupo **Calendarios**, seleccione **Tabla de fechas**.

    ![img](./images/imgT3P1.png)  

- Paso 2. Desde la vista de diagrama, notará que se creo una nueva tabla llamada **Calendario** 

- Paso 3. Relacione la taba **Calendario** con el modelo

    ![img](./images/imgT3P3.png)  

- Paso 4. Elimine todas las columnas excepto **Date**

    ![img](./images/imgT3P4.png)  

- Paso 5. Desde la pestaña de **Inicio** Cambien la vista a **Vista de Datos** 

- Paso 6. Valide la información que se creo en automatico para la tabla **Calendario**

- Paso 7. En la esquina inferior izquierda, en la barra de estado, observe las estadísticas de la tabla, que confirman que se han generado 1826 filas de datos, lo que representa datos de cinco años completos.

### Tarea 4. Creación de columnas calculadas

En esta tarea, agregará más columnas para habilitar el filtrado y la agrupación por diferentes períodos de tiempo.

- Paso 1. En la ventana de **Power Pivot**, en la sección **Ver**, seleccione **Vista de datos**.

    ![img](./images/imgT4P1.png)  

- Paso 2. En la parte inferior, seleccione la tabla **Calendario**.

- Paso 3. Agregue una nueva columna **Año** con la siguiente expresion, que concatena un texto:

   > ="FY" & YEAR('Calendario'[Date]) + IF (MONTH(Calendario[Date]) > 6; 1)

    *La fórmula utiliza el valor del año de la fecha, pero agrega uno al valor del año cuando el mes es posterior a junio. Así es como se calculan los años fiscales en este escenario.*

- Paso 4. Renombre la **Columna calculada 1** por **Año**

- Paso 5. Agregue una nueva columna con la siguiente DAX para el **Trimestre**:

    >= 'Calendario'[Año] & " T" & <br>
        >IF(MONTH(Calendario[Date]) <= 3;3; <br>
            IF(MONTH(Calendario[Date]) <= 6;4; <br>
            IF(MONTH(Calendario[Date]) <= 9;1;2
            )
        )
    )

- Paso 6. Renombre la **Columna calculada 1** por **Trimestre**

    ![img](./images/imgT4P5.png)  

- Paso 7. agregue una columna **Mes** con la siguiente DAX:

    > = FORMAT(Calendario[Date] ;"YYYY - MMM")

- Paso 8. Renombre la **Columna calculada 1** por **Mes**

- Paso 9. Para Ordenar de acuerdo a los meses dentro del Año Fiscal, agregue una columna con el numero del mes:

    >= (YEAR(Calendario[Date]) * 100) + MONTH(Calendario[Date])

- Paso 10. Renombre la  **Columna calculada 1** por **Número del mes**

    ![img](./images/imgT4P8.png)  

- Paso 11. Agregue los años y meses en una tabla dinámica y observe que los meses no tienen un orden correcto.

    ![img](./images/imgT4P9.png) 

- Paso 12. Para ordenarlos, utilizaremos la columna que creamos anteriormente con el número del mes. En la ventana de **Power Pivot**, seleccione el encabezado de la columna **Mes** y, en la parte superior, en la pestaña **Inicio**, seleccione **Ordenar Por**.

    ![img](./images/imgT4P10.png) 

- Paso 11. En la nueva ventana, seleccione la columna **Numero de mes** y luego seleccione **Aceptar**

- Paso 12. Reguese a la tabla dinamica y verifique el orden correcto de acuerdo con el año fiscal

    ![img](./images/imgT4P12.png) 


### Tarea 5. Crear Jerarquia

- Paso 1. En Power Pivot regrese a la vista de diagrama y seleccione la tabla **Calendario**

- Paso 2. Note que en la parte superiro derecha aparece un icono de jerarquia, seleccione este elemento.

    ![img](./images/imgT5P2.png) 

- Paso 3. Nombre la jerarquia con **Fiscal** y luego dentro de ese elemento arrastre los campos de **Año**, **Trimestre** y **Mes** 

    ![img](./images/imgT5P3.png) 


### Tarea 6. Cree medidas sencillas

- Paso 1. En Excel, en la parte superior en la pestaña de **Power Pivot**, seleccione **Medidas** y **Nueva medida**

    ![img](./images/imgT6P1.png) 

- Paso 2.Seleccione en:

    > Nombre de la tabla: **Sales** <br> 
    > Nombre de la medida: **Promedio Precio**<br> 
    > DAX:  = AVERAGE(Sales[Unit Price]).
    > Categoría: **Moneda**

    ![img](./images/imgT6P2.png) 

- Paso 4. Realice el mismo proceso para las siguientes medidas:

    > - Precio Medio =MEDIAN(Sales[Unit Price]) <br>
    > - Precio mínimo =MIN(Sales[Unit Price]) <br>
    > - Precio máximo =MAX(Sales[Unit Price])<br>
    > - Órdenes = DISTINCTCOUNT(Sales[SalesOrderNumber])<br>
    > - Líneas de pedido =COUNTROWS(Sales) <br>
    > - Doble de Ordenes = 2 * CALCULATE( DISTINCTCOUNT(Sales[SalesOrderNumber]); SAMEPERIODLASTYEAR(Calendario[Date]))

    ![img](./images/imgT6P4.png) 

   
- Paso 5. agregue cada medida a la tabla dinamica.

    ![img](./images/imgT6P5.png) 

### Tarea 7. Crear KPI

- Paso 1. En Excel, en la parte superior en la pestaña de **Power Pivot**, seleccione **KPI** y **Nuevo KPI**

- Paso 2. Utilizaremos la medida que configuramos en el paso anterior **Doble de Ordenes** para generar un KPI que me permita como objetivo o destino considerar el doble de ordenes frente al año anterior

- Paso 3. En el KPI seleccione en los campos:

    >- Campo base de KPI: **Órdenes**
    >- Medida: Doble de Ordenes

    Las demas configuraciones puede dejarlas por default y seleccione **Aceptar**.

- Paso 4. Agregue el KPI al inicio en la tabla dinamica y podra ver los iconos correspondientes

    ![img](./images/imgT7P4.png) 

### Tarea 8. Crear Gráficos dinámicos

- Paso 1. En Excel, en la pestaña de **Insertar** en la sección de **Gráficos**  seleccione **Gráfico dinámico**. 

    ![img](./images/imgT8P1.png) 

- Paso 2. En el elemento agregado, seleccione los campos para exponer la información. En ejes seleccione el **Category**  y en Valores agregue a **Sales**

    ![img](./images/imgT8P2.png) 

- Paso 3. Agregue una segmentación por Años y editela para que pueda filtrar ambos objetos visuales.



### Resultado esperado
Con lo realizado, tendremos un modelo relacional que nos permite crear diferentes objetos visuales para analizar la información de manera más detallada y eficiente.

![img](./images/imgT8P3.png) 
