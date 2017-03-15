---
title: "Conjunto de registros: Enlazar din&#225;micamente columnas de datos (ODBC) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "columnas [C++], enlazar a conjuntos de registros"
  - "enlace de datos [C++], columnas en conjuntos de registros"
  - "enlace de datos [C++], columnas de conjuntos de registros"
  - "conjuntos de registros ODBC [C++], enlazar columnas dinámicamente"
  - "conjuntos de registros [C++], enlazar datos"
ms.assetid: bff67254-d953-4ae4-9716-91c348cb840b
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Conjunto de registros: Enlazar din&#225;micamente columnas de datos (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este tema es aplicable a las clases ODBC de MFC.  
  
 Los conjuntos de registros administran el enlace de las columnas de tabla especificadas en tiempo de diseño, pero hay casos en los que resulta conveniente enlazar columnas cuya existencia se desconoce en tiempo de diseño.  En este tema se explica:  
  
-   [Cuándo puede resultar conveniente enlazar columnas dinámicamente con un conjunto de registros](#_core_when_you_might_bind_columns_dynamically).  
  
-   [Cómo enlazar columnas dinámicamente en tiempo de ejecución](#_core_how_to_bind_columns_dynamically).  
  
> [!NOTE]
>  Este tema se aplica a objetos derivados de `CRecordset` donde no se haya implementado la obtención masiva de filas.  Las técnicas descritas no suelen recomendarse si se utiliza la obtención de filas masiva.  Para obtener más información sobre la obtención masiva de filas, vea [Conjunto de registros: Obtener registros de forma masiva \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="_core_when_you_might_bind_columns_dynamically"></a> Cuándo se pueden enlazar columnas dinámicamente  
 En tiempo de diseño, el Asistente para aplicaciones MFC o el [Asistente para consumidores ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md) \(de **Agregar clase**\) crea clases de conjunto de registros basadas en las tablas y columnas conocidas del origen de datos.  Las bases de datos pueden cambiar desde el momento de su diseño a un estado posterior en el que la aplicación utiliza sus tablas y columnas en tiempo de ejecución.  El propio usuario o cualquier otro  pueden agregar o eliminar tablas o columnas de una tabla en la que se base el conjunto de registros de la aplicación.  Probablemente no es ningún problema para todas las aplicaciones de acceso a datos, pero sí lo es para su aplicación, ¿cómo puede afrontar los cambios del esquema de la base de datos sin necesidad de rediseñar y volver a compilar?  La finalidad de este tema es responder a esta pregunta.  
  
 En este tema se describe el caso más normal en el que se pueden enlazar columnas dinámicamente: cuando se empieza por un conjunto de registros basado en un esquema de base de datos conocido y se desea trabajar con columnas adicionales en tiempo de ejecución.  Además, en este tema se supone que las columnas adicionales se corresponden con miembros de datos del campo `CString`, el caso más habitual, si bien se proporcionan sugerencias para ayudarle a trabajar con otros tipos de datos.  
  
 Con una pequeña cantidad de código extra, se puede:  
  
-   [Determinar qué columnas están disponibles en tiempo de ejecución](#_core_to_determine_the_columns_in_a_table_at_run_time).  
  
-   [Enlazar columnas adicionales con un conjunto de registros de forma dinámica en tiempo de ejecución](#_core_adding_the_columns)  
  
 El conjunto de registros seguirá conteniendo miembros de datos para las columnas conocidas en tiempo de diseño.  También contendrá una pequeña cantidad de código adicional que determina dinámicamente si se agregaron nuevas columnas a la tabla de destino y, en ese caso, enlaza estas nuevas columnas con espacio de almacenamiento asignado dinámicamente \(en lugar de hacerlo con miembros de datos del conjunto de registros\).  
  
 Este tema no abarca otros casos de enlaces dinámicos, como las tablas o columnas eliminadas.  En esos casos, deberá usar llamadas API de ODBC más directamente.  Para obtener información, vea la *Referencia del programador* del SDK de ODBC en el CD de MSDN Library.  
  
##  <a name="_core_how_to_bind_columns_dynamically"></a> Cómo enlazar columnas dinámicamente  
 Para enlazar columnas dinámicamente, debe conocer \(o poder determinar\) los nombres de las columnas adicionales.  También se debe asignar espacio de almacenamiento para los miembros de datos de campo adicionales y especificar sus nombres y tipos, así como el número de columnas que se está agregando.  
  
 La siguiente discusión menciona dos conjuntos de registros diferentes.  El primero es el conjunto de registros principal, que selecciona registros de la tabla de destino.  El segundo es un conjunto de registros de columna especial, utilizado para obtener información sobre las columnas de la tabla de destino.  
  
###  <a name="_core_the_general_process"></a> Proceso general  
 En el nivel más general, deben seguirse estos pasos:  
  
1.  Crear el objeto de conjunto de registros principal.  
  
     De forma opcional, pasar un puntero a un objeto `CDatabase` abierto o ser capaz de proporcionar información de conexión al conjunto de registros de columna de cualquier otra forma.  
  
2.  Seguir los pasos correspondientes para agregar columnas dinámicamente.  
  
     Vea el proceso que se describe a continuación en Agregar las columnas.  
  
3.  Abrir el conjunto de registros principal.  
  
     El conjunto de registros selecciona los registros y utiliza el Intercambio de campos de registros \(RFX\) para enlazar tanto las columnas estáticas \(las asignadas a miembros de datos de campo del conjunto de registros\) como las columnas dinámicas \(las asignadas a espacio de almacenamiento extra establecido para tal fin\).  
  
###  <a name="_core_adding_the_columns"></a> Agregar las columnas  
 El enlace dinámico de las columnas agregadas en tiempo de ejecución requiere los siguientes pasos:  
  
1.  Determine en tiempo de ejecución qué columnas se encuentran en la tabla de destino.  Extraiga de dicha información una lista de las columnas agregadas a la tabla desde que se diseñó la clase de conjunto de registros.  
  
     Un buen enfoque consiste en utilizar una clase de conjunto de registros de columna diseñada para consultar el origen de datos y obtener información de columna de la tabla de destino \(como el nombre de columna o el tipo de datos\).  
  
2.  Proporcione espacio de almacenamiento para los nuevos miembros de datos de campo.  Dado que la clase de conjunto de registros principal no tiene miembros de datos de campo para las columnas desconocidas, debe proporcionar un lugar para almacenar los nombres, los valores de los resultados y, posiblemente, la información de tipo de datos \(si las columnas son de tipos de datos diferentes\).  
  
     Un posible enfoque es el de compilar una o varias listas dinámicas, una para los nombres de las nuevas columnas, otra para sus valores de resultado y una tercera para sus tipos de datos \(si es necesario\).  Estas listas, en particular la lista de valores, proporcionan la información y el espacio de almacenamiento necesarios para la operación de enlace.  La siguiente ilustración muestra cómo se compilan las listas.  
  
     ![Compilar listas de columnas para enlazarlas dinámicamente](../../data/odbc/media/vc37w61.gif "vc37W61")  
Compilar listas de columnas para enlazarlas dinámicamente  
  
3.  Agregue una llamada de función RFX a la función `DoFieldExchange` del conjunto de registros principal por cada columna agregada.  Estas llamadas RFX realizan el trabajo de obtener un registro, incluidas las columnas adicionales, y enlazar éstas con los miembros de datos del conjunto de registros o con el espacio de almacenamiento asignado dinámicamente para ellas.  
  
     Un posible enfoque consiste en agregar un bucle a la función `DoFieldExchange` del conjunto de registros principal que recorra la lista de nuevas columnas llamando a la función RFX correspondiente para cada columna de la lista.  En cada llamada RFX, pase un nombre de columna de la lista de nombres de columna y una ubicación de almacenamiento en el miembro correspondiente de la lista de valores de resultado.  
  
###  <a name="_core_lists_of_columns"></a> Listas de columnas  
 Las cuatro listas con las que necesita trabajar se muestran en la tabla siguiente.  
  
 [Columnas de la tabla actual \(Lista 1 en la ilustración\)](#_core_illustration_dynamic)  
 Lista de las columnas existentes actualmente en la tabla del origen de datos.  Esta lista podría coincidir con la lista de columnas enlazadas actualmente en su conjunto de registros.  
  
 [Columnas enlazadas del conjunto de registros \(Lista 2 en la ilustración\)](#_core_illustration_dynamic)  
 Lista de las columnas enlazadas en el conjunto de registros.  Estas columnas ya contienen instrucciones RFX en la función `DoFieldExchange`.  
  
 [Columnas para enlazar dinámicamente \(Lista 3 en la ilustración\)](#_core_illustration_dynamic)  
 Lista de las columnas existentes en la tabla, pero no en el conjunto de registros.  Éstas son las columnas que conviene enlazar dinámicamente.  
  
 [Valores de columna dinámicos \(Lista 4 en la ilustración\)](#_core_illustration_dynamic)  
 Lista que contiene el espacio de almacenamiento correspondiente a los valores recuperados de las columnas enlazadas dinámicamente.  Los elementos de esta lista se corresponden uno a uno con los de la lista Columnas para enlazar dinámicamente.  
  
###  <a name="_core_building_your_lists"></a> Compilar las listas  
 Una vez decidida la forma de proceder, se puede dirigir la atención a los detalles.  Los procedimientos del resto del tema muestran cómo compilar las listas que aparecen en [Listas de columnas](#_core_lists_of_columns).  Estos procedimientos le enseñarán a:  
  
-   [Determinar los nombres de las columnas que no pertenecen al conjunto de registros](#_core_determining_which_table_columns_are_not_in_your_recordset).  
  
-   [Proporcionar espacio de almacenamiento dinámico para las columnas recién agregadas a una tabla](#_core_providing_storage_for_the_new_columns).  
  
-   [Agregar dinámicamente llamadas RFX para las nuevas columnas](#_core_adding_rfx_calls_to_bind_the_columns).  
  
###  <a name="_core_determining_which_table_columns_are_not_in_your_recordset"></a> Determinar qué columnas de tabla no se encuentran en el conjunto de registros  
 Compile una lista \(Columnas enlazadas del conjunto de registros, como en la lista 2 de la [ilustración](#_core_illustration_dynamic)\) que contenga una lista de columnas ya enlazadas en el conjunto de registros principal.  A continuación, compile una lista \(Columnas para enlazar dinámicamente, derivada de las listas Columnas de la tabla actual y Columnas enlazadas del conjunto de registros\) que contenga los nombres de columna que ya existen en la tabla del origen de datos, pero no en el conjunto de registros principal.  
  
##### Para determinar los nombres de columna que no existen en el conjunto de registros \(Columnas para enlazar dinámicamente\)  
  
1.  Compile una lista \(Columnas enlazadas del conjunto de registros\) de las columnas que ya se encuentran enlazadas en el conjunto de registros principal.  
  
     Un posible enfoque para ello es crear dicha lista en tiempo de diseño.  Se pueden examinar visualmente las llamadas de función RFX de la función `DoFieldExchange` del conjunto de registros para obtener dichos nombres.  A continuación, configure la lista como matriz inicializada con los nombres.  
  
     Por ejemplo, la [ilustración](#_core_illustration_dynamic) muestra una lista Columnas enlazadas del conjunto de registros \(Lista 2\) con tres elementos.  La lista Columnas enlazadas del conjunto de registros no aparece en la columna Teléfono de la lista Columnas de la tabla actual \(Lista 1\).  
  
2.  Compare las Columnas de la tabla actual con las Columnas enlazadas del conjunto de registros para compilar una lista \(Columnas para enlazar dinámicamente\) de las columnas aún no enlazadas en el conjunto de registros principal.  
  
     Una forma de hacerlo es recorrer en un bucle la lista de columnas de la tabla en tiempo de ejecución \(Columnas de la tabla actual\) y la lista de columnas ya enlazadas en el conjunto de registros \(Columnas enlazadas del conjunto de registros\) de forma paralela.  En la lista "Columnas para enlazar dinámicamente", coloque los nombres de "Columnas de la tabla actual" que no aparezcan en "Columnas enlazadas del conjunto de registros".  
  
     Por ejemplo, la [ilustración](#_core_illustration_dynamic) muestra la lista Columnas para enlazar dinámicamente \(Lista 3\) con un elemento: la columna Teléfono que aparece en la lista Columnas de la tabla actual \(Lista 1\), pero no en la lista Columnas enlazadas del conjunto de registros \(Lista 2\).  
  
3.  Compile una lista Valores de columna dinámicos \(como se muestra en la lista 4 de la [ilustración](#_core_illustration_dynamic)\) en la que almacenar los valores de datos correspondientes a los nombres de columna almacenados en la lista Columnas para enlazar dinámicamente.  
  
     Los elementos de esta lista juegan el rol de miembros de datos de campo del nuevo conjunto de registros.  Representan las ubicaciones de almacenamiento con las que están enlazadas las columnas dinámicas.  Para ver una descripción de estas listas, vea [Listas de columnas](#_core_lists_of_columns).  
  
###  <a name="_core_providing_storage_for_the_new_columns"></a> Proporcionar espacio de almacenamiento para las nuevas columnas  
 Lo siguiente es configurar ubicaciones de almacenamiento para las columnas que se enlazarán dinámicamente.  La idea es proporcionar un elemento de lista en el que almacenar el valor de cada columna.  Estas ubicaciones de almacenamiento se corresponden con las variables miembro del conjunto de registros, que almacenan las columnas enlazadas normalmente.  
  
##### Para proporcionar almacenamiento dinámico para nuevas columnas \(Valores de columna dinámicos\)  
  
1.  Compile una lista Valores de columna dinámicos, en paralelo con la lista Columnas para enlazar dinámicamente, que contenga el valor de los datos de cada columna.  
  
     Por ejemplo, la [ilustración](#_core_illustration_dynamic) muestra Valores de columna dinámicos \(Lista 4\) con un elemento: un objeto `CString` que contiene el número de teléfono real del registro actual: "555\-1212".  
  
     Habitualmente, la lista Valores de columna dinámicos contiene elementos de tipo `CString`.  Si trabaja con columnas de tipos de datos diferentes, necesitará una lista que contenga elementos de varios tipos.  
  
 El resultado de los procedimientos anteriores da dos listas principales: Columnas para enlazar dinámicamente, que contiene los nombres de las columnas, y Valores de columna dinámicos, que contiene los valores de las columnas correspondientes al registro actual.  
  
> [!TIP]
>  Si las nuevas columnas no son todas del mismo tipo de datos, puede que sea conveniente una lista paralela adicional con los elementos que definan de alguna forma el tipo de datos de cada elemento correspondiente de la lista de columnas. \(Se pueden utilizar los valores **AFX\_RFX\_BOOL**, **AFX\_RFX\_BYTE**, etc., si así lo desea.  Estas constantes están definidas en AFXDB.H\). Elija un tipo de lista basado en la forma de representar los tipos de datos de columna.  
  
###  <a name="_core_adding_rfx_calls_to_bind_the_columns"></a> Agregar llamadas RFX para enlazar las columnas  
 Por último, prepare la operación de enlace dinámico colocando llamadas RFX para las nuevas columnas en la función `DoFieldExchange`.  
  
##### Para agregar dinámicamente llamadas RFX para nuevas columnas  
  
1.  En la función miembro `DoFieldExchange` del conjunto de registros principal, agregue código que recorra en un bucle la lista de nuevas columnas \(Columnas para enlazar dinámicamente\).  En cada bucle, extraiga un nombre de columna de la lista Columnas para enlazar dinámicamente y un valor de resultado para la columna de la lista Valores de columna dinámicos.  Pase estos elementos a una llamada de función RFX que corresponda al tipo de datos de la columna.  Para ver una descripción de estas listas, vea [Listas de columnas](#_core_lists_of_columns).  
  
 Habitualmente, en las llamadas de función `RFX_Text` se extraen objetos `CString` de las listas, como se muestra en las siguientes líneas de código, donde la lista Columnas para enlazar dinámicamente es un objeto `CStringList` denominado `m_listName` y la lista Valores de columna dinámicos es un objeto `CStringList` denominado `m_listValue`:  
  
```  
RFX_Text( pFX,   
            m_listName.GetNext( posName ),   
            m_listValue.GetNext( posValue ));  
```  
  
 Para obtener más información acerca de las funciones RFX, vea [Macros y funciones globales](../../mfc/reference/mfc-macros-and-globals.md) en la *Referencia de la biblioteca de clases*.  
  
> [!TIP]
>  Si las nuevas columnas son de diferentes tipos de datos, use una instrucción switch en el bucle para llamar a la función RFX correspondiente a cada tipo de datos.  
  
 Cuando el marco de trabajo llama a `DoFieldExchange` durante el proceso **Open** para enlazar columnas con el conjunto de registros, las llamadas RFX correspondientes a las columnas estáticas enlazan dichas columnas.  A continuación, el bucle llama repetidamente a las funciones RFX para las columnas dinámicas.  
  
## Vea también  
 [Conjunto de registros \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [Conjunto de registros: Trabajar con grandes elementos de datos \(ODBC\)](../../data/odbc/recordset-working-with-large-data-items-odbc.md)