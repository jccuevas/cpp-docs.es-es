---
title: "Conjunto de registros: C&#243;mo se seleccionan los registros (ODBC) | Microsoft Docs"
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
  - "conjuntos de registros ODBC, seleccionar registros"
  - "selección de registros, conjuntos de registros ODBC"
  - "registros, seleccionar"
  - "conjuntos de registros, crear instrucciones SQL"
  - "conjuntos de registros, seleccionar registros"
  - "instrucciones SQL, conjunto de registros"
ms.assetid: 343a6a91-aa4c-4ef7-b21f-2f2bfd0d3787
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Conjunto de registros: C&#243;mo se seleccionan los registros (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este tema es aplicable a las clases ODBC de MFC.  
  
 En este tema se explica:  
  
-   [Su rol y las opciones del programador al seleccionar registros](#_core_your_options_in_selecting_records).  
  
-   [Cómo crea un conjunto de registros su instrucción SQL y selecciona los registros](#_core_how_a_recordset_constructs_its_sql_statement).  
  
-   [Qué se puede hacer para personalizar la selección](#_core_customizing_the_selection).  
  
 Los conjuntos de registros seleccionan los registros de un origen de datos a través de un controlador ODBC, enviando instrucciones SQL al controlador.  El código SQL enviado depende de cómo se diseñe y abra la clase de conjunto de registros.  
  
##  <a name="_core_your_options_in_selecting_records"></a> Opciones disponibles al seleccionar los registros  
 La siguiente tabla muestra las opciones disponibles al seleccionar registros.  
  
### Cómo y cuándo es posible realizar modificaciones en un conjunto de registros  
  
|Al hacer lo siguiente|Se puede|  
|---------------------------|--------------|  
|Declarar la clase de conjunto de registros con el asistente **Agregar clase**|Especificar la tabla de la cual se seleccionan registros.<br /><br /> Especificar las columnas que se incluirán.<br /><br /> Vea [Agregar un consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).|  
|Completar la implementación de la clase de conjunto de registros|Reemplazar las funciones miembro como `OnSetOptions` \(avanzada\) para establecer opciones específicas de la aplicación o cambiar la configuración predeterminada.  Especificar los miembros de datos de parámetro si se desea un conjunto de registros parametrizado.|  
|Crear un objeto de conjunto de registros \(antes de llamar a **Open**\)|Especificar una condición de búsqueda \(posiblemente compuesta\) para su uso en una cláusula **WHERE** que filtre los registros.  Vea [Conjunto de registros: filtrar registros \(ODBC\)](../../data/odbc/recordset-filtering-records-odbc.md)<br /><br /> Especificar un criterio de ordenación para su uso en una cláusula **ORDER BY** que ordene los registros.  Vea [Conjunto de registros: ordenar registros \(ODBC\)](../../data/odbc/recordset-sorting-records-odbc.md).<br /><br /> Especificar los valores de parámetro para cualquier parámetro agregado a la clase.  Vea [Conjunto de registros: Parametrizar un conjunto de registros \(ODBC\)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).|  
|Ejecutar la consulta del conjunto de registros llamando a **Open**|Especificar una cadena SQL personalizada que reemplace la cadena SQL predeterminada creada por el asistente.  Vea [CRecordset::Open](../Topic/CRecordset::Open.md) en la *Referencia de la biblioteca de clases* y [SQL: personalizar la instrucción SQL del conjunto de registros \(ODBC\)](../../data/odbc/sql-customizing-your-recordset’s-sql-statement-odbc.md).|  
|Llamar a **Requery** para realizar una nueva consulta al conjunto de registros con los valores más recientes del origen de datos|Especificar nuevos parámetros, filtrar u ordenar.  Vea [Conjunto de registros: realizar una nueva consulta a un conjunto de registros \(ODBC\)](../../data/odbc/recordset-requerying-a-recordset-odbc.md).|  
  
##  <a name="_core_how_a_recordset_constructs_its_sql_statement"></a> Cómo crea un conjunto de registros su instrucción SQL  
 Al llamar a la función miembro [Open](../Topic/CRecordset::Open.md) del objeto de conjunto de registros, **Open** crea una instrucción SQL usando uno o varios elementos de los siguientes:  
  
-   El parámetro **lpszSQL** pasado a **Open**.  Si es distinto de **NULL**, este parámetro especifica una cadena SQL personalizada o parte de una.  El marco de trabajo analiza la cadena.  Si la cadena es una instrucción SQL **SELECT** o una instrucción ODBC **CALL**, el marco de trabajo usa la cadena como instrucción SQL del conjunto de registros.  Si la cadena no comienza por "SELECT" o "{CALL", el marco de trabajo usa los datos proporcionados para generar una cláusula SQL **FROM**.  
  
-   La cadena devuelta por [GetDefaultSQL](../Topic/CRecordset::GetDefaultSQL.md).  De forma predeterminada, éste es el nombre de la tabla especificada para el conjunto de registros en el asistente, pero se puede cambiar el valor devuelto por la función.  El marco de trabajo llama a `GetDefaultSQL`; si la cadena no comienza con "SELECT" o "{CALL", se supone que es un nombre de tabla, que se utiliza para generar una cadena SQL.  
  
-   Los miembros de datos de campo del conjunto de registros que se enlazarán con columnas específicas de la tabla.  El marco de trabajo enlaza las columnas de registro con las direcciones de dichos miembros, usándolas como búferes.  El marco de trabajo determina la correlación de miembros de datos de campo con las columnas de las llamadas de función [RFX](../../data/odbc/record-field-exchange-using-rfx.md) o RFX masivo existentes en la función miembro [DoFieldExchange](../Topic/CRecordset::DoFieldExchange.md) o [DoBulkFieldExchange](../Topic/CRecordset::DoBulkFieldExchange.md) del conjunto de registros.  
  
-   El [filtro](../../data/odbc/recordset-filtering-records-odbc.md) del conjunto de registros, si lo hay, contenido en el miembro de datos [m\_strFilter](../Topic/CRecordset::m_strFilter.md).  El marco de trabajo usa esta cadena para crear una cláusula SQL **WHERE**.  
  
-   El tipo de [ordenación](../../data/odbc/recordset-sorting-records-odbc.md) del conjunto de registros, si lo hay, contenido en el miembro de datos [m\_strSort](../Topic/CRecordset::m_strSort.md).  El marco de trabajo usa esta cadena para crear una cláusula SQL **ORDER BY**.  
  
    > [!TIP]
    >  Para poder usar la cláusula SQL **GROUP BY** \(y posiblemente la cláusula **HAVING**\), anexe las cláusulas al final de la cadena de filtro.  
  
-   Los valores de cualquier [miembro de datos de parámetro](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) que se especifique para la clase.  Se establecen los valores de parámetro justo antes de llamar a **Open** o a **Requery**.  El marco de trabajo enlaza los valores de parámetro a los marcadores de posición "?" en la cadena SQL.  En tiempo de compilación, se especifica la cadena mediante marcadores de posición.  En tiempo de ejecución, el marco de trabajo completa los detalles basándose en los valores de parámetro pasados.  
  
 **Open** crea una instrucción SQL **SELECT** a partir de estos elementos.  Vea [Personalizar la selección](#_core_customizing_the_selection) para conocer los detalles sobre cómo utiliza dichos elementos el marco de trabajo.  
  
 Después de crear la instrucción, **Open** envía el código SQL al Administrador de controladores ODBC \(y a la biblioteca de cursores ODBC, si está en memoria\), el cual lo envía al controlador ODBC del sistema de administración de bases de datos \(DBMS\) específico.  El controlador se comunica con el DBMS para realizar la selección en el origen de datos y obtiene el primer registro.  El marco de trabajo carga el registro en los miembros de datos de campo del conjunto de registros.  
  
 Se puede usar una combinación de estas técnicas para abrir [tablas](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md) y para crear una consulta basada en una [combinación](../../data/odbc/recordset-performing-a-join-odbc.md) de múltiples tablas.  Mediante personalización adicional, se puede llamar a [consultas predefinidas](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md) \(procedimientos almacenados\), seleccionar columnas de tabla desconocidas en tiempo de diseño y [enlazarlas](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md) con campos de conjunto de registros, o realizar casi todas las demás tareas comunes de acceso a datos.  Las tareas que no se pueden llevar a cabo personalizando los conjuntos de registros se pueden realizar a pesar de todo [llamando a funciones de la API de ODBC](../../data/odbc/odbc-calling-odbc-api-functions-directly.md) o ejecutando directamente instrucciones SQL mediante [CDatabase::ExecuteSQL](../Topic/CDatabase::ExecuteSQL.md).  
  
##  <a name="_core_customizing_the_selection"></a> Personalizar la selección  
 Además de proporcionar un filtro, un criterio de ordenación o parámetros, se pueden realizar las siguientes acciones para personalizar la selección del conjunto de registros:  
  
-   Pasar una cadena SQL personalizada en **lpszSQL** al llamar a [Open](../Topic/CRecordset::Open.md) para el conjunto de registros.  Cualquier dato que se pase en **lpsqSQL** tiene prioridad sobre lo devuelto por la función miembro [GetDefaultSQL](../Topic/CRecordset::GetDefaultSQL.md).  
  
     Para obtener más información, vea [SQL: Personalizar la instrucción SQL del conjunto de registros \(ODBC\)](../../data/odbc/sql-customizing-your-recordset’s-sql-statement-odbc.md), que describe los tipos de instrucciones SQL \(o instrucciones parciales\) que se pueden pasar a **Open** y lo que hace con ellas el marco de trabajo.  
  
    > [!NOTE]
    >  Si la cadena personalizada que se pasa no comienza por "SELECT" o "{CALL", MFC supone que contiene un nombre de tabla.  Esto también se aplica a lo expuesto en el siguiente elemento con viñeta.  
  
-   Modificar la cadena que escribe el asistente en la función miembro `GetDefaultSQL` del conjunto de registros.  Editar el código de la función para cambiar lo que devuelve.  De forma predeterminada, el asistente escribe una función `GetDefaultSQL` que devuelve un solo nombre de tabla.  
  
     Es posible hacer que `GetDefaultSQL` devuelva cualquiera de los elementos que se pueden pasar en el parámetro **lpszSQL** a **Open.** Si no se pasa ninguna cadena SQL personalizada de **lpszSQL**, el marco de trabajo usa la cadena devuelta por `GetDefaultSQL`.  Como mínimo, `GetDefaultSQL` debe devolver un nombre de tabla.  Pero se puede hacer que devuelva varios nombres de tabla, una instrucción **SELECT** completa, una instrucción ODBC **CALL**, etc.  Para obtener una lista de los valores que se pueden pasar a **lpszSQL** \(o hacer que `GetDefaultSQL` devuelva\), vea [SQL: Personalizar la instrucción SQL del conjunto de registros \(ODBC\)](../../data/odbc/sql-customizing-your-recordset’s-sql-statement-odbc.md).  
  
     Si realiza una combinación de dos o más tablas, vuelva a escribir `GetDefaultSQL` para personalizar la lista de tablas usada en la cláusula SQL **FROM.** Para obtener más información, vea [Conjunto de registros: Realizar una combinación \(ODBC\)](../../data/odbc/recordset-performing-a-join-odbc.md).  
  
-   Enlazar manualmente miembros de datos de campo adicionales, basándose quizás en información sobre el esquema del origen de datos obtenida en tiempo de ejecución.  Se pueden agregar miembros de datos de campo a la clase de conjunto de registros, así como las llamadas de función [RFX](../../data/odbc/record-field-exchange-using-rfx.md) o RFX masivo relacionadas a las funciones miembro [DoFieldExchange](../Topic/CRecordset::DoFieldExchange.md) o [DoBulkFieldExchange](../Topic/CRecordset::DoBulkFieldExchange.md), y código de inicialización de los miembros de datos de campo en el constructor de la clase.  Para obtener más información, vea [Conjunto de registros: Enlazar dinámicamente columnas de datos \(ODBC\)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).  
  
-   Reemplazar funciones miembro de conjunto de registros, como `OnSetOptions`, para establecer opciones específicas de la aplicación o reemplazar los valores predeterminados.  
  
 Si desea basar el conjunto de registros en una instrucción SQL compleja, debe usar una combinación de estas técnicas de personalización.  Por ejemplo, puede que desee utilizar cláusulas y palabras clave de SQL no admitidas directamente por los conjuntos de registros, o quizás prefiera combinar tablas múltiples.  
  
## Vea también  
 [Conjunto de registros \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [Conjunto de registros: Actualizar los registros \(ODBC\)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)   
 [Conceptos básicos de ODBC](../../data/odbc/odbc-basics.md)   
 [SQL](../../data/odbc/sql.md)   
 [Conjunto de registros: Bloquear registros \(ODBC\)](../../data/odbc/recordset-locking-records-odbc.md)