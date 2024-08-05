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

- Paso 4. Seleccione de **Salesperson** | **Salesperson** y de **Sales | Sales**, en automatico crea una suma del campo **Sales**

    ![img](./images/imgT2P4.png)  


### Tarea 3. Crear la tabla Fecha

- Paso 1. Cambie a la vista de modelo. En la pestaña de la cinta de opciones **Diseñar**, en el grupo **Calendarios**, seleccione **Tabla de fechas**.

    ![img](./images/imgT3P1.png)  

- Paso 2. Desde la vista de diagrama, notará que se creo una nueva tabla llamada **Date** 

- Paso 3. Relacione la taba **Date** con el modelo

    ![img](./images/imgT3P3.png)  

- Paso 4. Desde la pestaña de **Inicio** Cambien la vista a **Vista de Datos** 

- Paso 5. Valide la información que se creo en automatico para la tabla **Date**

- Paso 6. En la esquina inferior izquierda, en la barra de estado, observe las estadísticas de la tabla, que confirman que se han generado 1826 filas de datos, lo que representa datos de cinco años completos.

### Resultado esperado
En esta sección se debe mostrar el resultado esperado de nuestro laboratorio
![imagen resultado](../images/img3.png)
