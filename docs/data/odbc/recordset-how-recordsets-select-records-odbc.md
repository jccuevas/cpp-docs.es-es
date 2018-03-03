---
title: "Conjunto de registros: Cómo se seleccionan los registros (ODBC) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- recordsets, selecting records
- record selection, ODBC recordsets
- SQL statements, recordset
- records, selecting
- recordsets, constructing SQL statements
- ODBC recordsets, selecting records
ms.assetid: 343a6a91-aa4c-4ef7-b21f-2f2bfd0d3787
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8664c5732c0cdf1042b6af338ea388ab29ab7863
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-how-recordsets-select-records-odbc"></a>Conjunto de registros: Cómo se seleccionan los registros (ODBC)
Este tema es aplicable a las clases ODBC de MFC.  
  
 En este tema se explica:  
  
-   [Su rol y las opciones de selección de registros](#_core_your_options_in_selecting_records).  
  
-   [Cómo un conjunto de registros crea su instrucción SQL y selecciona los registros](#_core_how_a_recordset_constructs_its_sql_statement).  
  
-   [Lo que puede hacer para personalizar la selección](#_core_customizing_the_selection).  
  
 Conjuntos de registros seleccionen registros de un origen de datos a través de un controlador ODBC mediante el envío de instrucciones SQL para el controlador. El código SQL enviado depende de cómo diseñar y abra la clase de conjunto de registros.  
  
##  <a name="_core_your_options_in_selecting_records"></a>Las opciones en la selección de registros  
 La siguiente tabla muestra las opciones en la selección de registros.  
  
### <a name="how-and-when-you-can-affect-a-recordset"></a>Cómo y cuándo puede afectar a un conjunto de registros  
  
|Cuando se|Puede|  
|--------------|-------------|  
|Declare la clase de conjunto de registros con el **Agregar clase** Asistente|Especifique la tabla que desea seleccionar en.<br /><br /> Especificar qué columnas desea incluir.<br /><br /> Vea [agregar un consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).|  
|Completar la implementación de la clase de conjunto de registros|Reemplazar funciones miembro como `OnSetOptions` (avanzada) para establecer las opciones específicas de la aplicación o para cambiar los valores predeterminados. Si quiere que un conjunto de registros parametrizado, especifique a los miembros de datos de parámetro.|  
|Crear un objeto de conjunto de registros (antes de llamar a **abiertos**)|Especificar una condición de búsqueda (posiblemente compuesta) para su uso en un **donde** cláusula que filtra los registros. Vea [conjunto de registros: filtrar registros (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).<br /><br /> Especificar un criterio de ordenación para su uso en un **ORDER BY** cláusula que ordene los registros. Vea [conjunto de registros: ordenar registros (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md).<br /><br /> Especificar valores de parámetro para los parámetros que se agregan a la clase. Vea [conjunto de registros: parametrizar un conjunto de registros (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).|  

| Ejecutar la consulta del conjunto de registros mediante una llamada a **abiertos**| Especifique una cadena SQL personalizada para reemplazar la cadena de SQL predeterminado configurada por el asistente. Vea [CRecordset:: Open](../../mfc/reference/crecordset-class.md#open) en el *referencia de biblioteca de clases de* y [SQL: personalizar la instrucción de SQL del conjunto de registros (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md). |  

| Llame a **Requery** para volver a consultar el conjunto de registros con los valores más recientes del origen de datos | Especifique nuevos parámetros, filtrar u ordenar. Vea [conjunto de registros: volver a consultar un conjunto de registros (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md). |  
  
##  <a name="_core_how_a_recordset_constructs_its_sql_statement"></a>Cómo crea un conjunto de registros su instrucción SQL  
 Cuando se llama a un objeto de conjunto de registros [abiertos](../../mfc/reference/crecordset-class.md#open) función miembro, **abiertos** construye una instrucción SQL usando uno o varios elementos de los siguientes:  
  
-   El **lpszSQL** parámetro pasado a **abiertos**. Si no **NULL**, este parámetro especifica una cadena SQL personalizada o parte de uno. El marco de trabajo analiza la cadena. Si la cadena es una instancia de SQL **seleccione** instrucción o un ODBC **llamar a** (instrucción), el marco de trabajo usa la cadena como instrucción SQL del conjunto de registros. Si la cadena no comienza con "SELECT" o "{CALL", el marco de trabajo usa los datos proporcionados para construir una instancia de SQL **FROM** cláusula.  
  
-   La cadena devuelta por [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql). De forma predeterminada, este es el nombre de la tabla especificada para el conjunto de registros en el asistente, pero puede cambiar la función que devuelve. Las llamadas de framework `GetDefaultSQL` : si la cadena no comienza con "SELECT" o "{CALL", se supone que sea un nombre de tabla, que se usa para construir una cadena de SQL.  
  

-   El campo miembros de datos del conjunto de registros, que se van a enlazarse a columnas específicas de la tabla. El marco de trabajo enlaza las columnas de registro para las direcciones de dichos miembros, usándolas como búferes. El marco de trabajo determina la correlación de miembros de datos de campo para columnas de la tabla de la [RFX](../../data/odbc/record-field-exchange-using-rfx.md) las llamadas de función RFX masivo en el conjunto de registros o [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) o [DoBulkFieldExchange ](../../mfc/reference/crecordset-class.md#dofieldexchange) función miembro.  
  
-   El [filtro](../../data/odbc/recordset-filtering-records-odbc.md) para el conjunto de registros, si lo hay, contenido en el [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) miembro de datos. El marco de trabajo usa esta cadena para construir una instancia de SQL **donde** cláusula.  
  
-   El [ordenación](../../data/odbc/recordset-sorting-records-odbc.md) criterio para el conjunto de registros, si lo hay, contenido en el [m_strSort](../../mfc/reference/crecordset-class.md#m_strsort) miembro de datos. El marco de trabajo usa esta cadena para construir una instancia de SQL **ORDER BY** cláusula.  

  
    > [!TIP]
    >  Para usar la instrucción SQL **GROUP BY** cláusula (y posiblemente la **HAVING** cláusula), anexe las cláusulas al final de la cadena de filtro.  
  
-   Los valores de cualquier [miembros de datos de parámetro](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) que especifique para la clase. Establecer valores de parámetro antes de llamar a **abiertos** o **Requery**. El marco de trabajo enlaza los valores de parámetro "?" marcadores de posición en la cadena de SQL. En tiempo de compilación, especifique la cadena con marcadores de posición. En tiempo de ejecución, el marco de trabajo se rellena en los detalles en función de los valores de parámetro pasados.  
  
 **Abra** construye una instancia de SQL **seleccione** instrucción partir de estos elementos. Vea [personalizar la selección](#_core_customizing_the_selection) para obtener más información acerca de cómo el marco de trabajo usa los ingredientes.  
  
 Después de crear la instrucción, **abiertos** envía el código SQL en el Administrador de controladores ODBC (y la biblioteca de cursores ODBC, si está en memoria), que envía al controlador ODBC para DBMS específico. El controlador se comunica con el DBMS para llevar a cabo la selección en el origen de datos y obtiene el primer registro. El marco de trabajo carga el registro en los miembros de datos de campo del conjunto de registros.  
  
 Puede usar una combinación de estas técnicas para abrir [tablas](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md) y para crear una consulta basada en una [combinación](../../data/odbc/recordset-performing-a-join-odbc.md) de varias tablas. Mediante personalización adicional, se puede llamar a [consultas predefinidas](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md) (procedimientos almacenados), no se conoce en tiempo de diseño de columnas de la tabla de select y [enlazar](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md) a campos de conjunto de registros o pueden llevar a cabo resto tareas de acceso a datos. Todavía pueden realizarse las tareas que no se puede realizar mediante la personalización de conjuntos de registros por [al llamar a funciones de la API de ODBC](../../data/odbc/odbc-calling-odbc-api-functions-directly.md) o ejecutando directamente instrucciones SQL con [CDatabase:: ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql).  
  
##  <a name="_core_customizing_the_selection"></a>Personalizar la selección  
 Además de proporcionar un filtro, un criterio de ordenación o parámetros, puede realizar las siguientes acciones para personalizar la selección del conjunto de registros:  
  
-   Pasar una cadena SQL personalizada en **lpszSQL** cuando se llama a [abiertos](../../mfc/reference/crecordset-class.md#open) para el conjunto de registros. Cualquier dato que se pase en **lpsqSQL** tiene prioridad sobre lo que la [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql) función miembro devuelve.  
  
     Para obtener más información, vea [SQL: SQL instrucción (ODBC de personalizar un conjunto de registros)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md), que describe los tipos de instrucciones SQL (o instrucciones parciales) puede pasar a **abrir** y lo que hace el marco de trabajo con ellos.  
  
    > [!NOTE]
    >  Si la cadena personalizada que se pasa no comienza con "SELECT" o "{CALL", MFC supone que contiene un nombre de tabla. Esto también se aplica al elemento con viñetas siguiente.  
  
-   Modificar la cadena que el asistente escribe en el conjunto de registros `GetDefaultSQL` función miembro. Modifique el código de la función para cambiar lo que devuelve. De forma predeterminada, el asistente escribe una `GetDefaultSQL` función que devuelve un nombre de tabla única.  
  
     Puede tener `GetDefaultSQL` devolver cualquiera de los elementos que se pueden pasar en el **lpszSQL** parámetro **abiertos**. Si no pasa una cadena SQL personalizada en **lpszSQL**, el marco de trabajo usa la cadena que `GetDefaultSQL` devuelve. Como mínimo, `GetDefaultSQL` debe devolver un nombre de tabla única. Pero se puede hacer que devuelva varios nombres de tabla, una completa **seleccione** (instrucción), un ODBC **llamar** instrucción y así sucesivamente. Para obtener una lista de lo que se puede pasar a **lpszSQL** , o tener `GetDefaultSQL` devolver: vea [SQL: SQL instrucción (ODBC de personalizar un conjunto de registros)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).  
  
     Si va a realizar una combinación de dos o más tablas, vuelva a escribir `GetDefaultSQL` para personalizar la lista de tablas usada en el código SQL **FROM** cláusula. Para obtener más información, consulte [conjunto de registros: realizar una combinación (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md).  
  

-   Enlazar manualmente miembros de datos de campo adicionales, quizás basados en información que obtener información sobre el esquema del origen de datos en tiempo de ejecución. Agregar miembros de datos de campo a la clase de conjunto de registros, [RFX](../../data/odbc/record-field-exchange-using-rfx.md) o de las llamadas de función RFX masivo para que hagan el [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) o [DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) función miembro, y código de inicialización de los miembros de datos en el constructor de clase. Para obtener más información, consulte [conjunto de registros: enlazar dinámicamente columnas de datos (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).  
  
-   Reemplazar funciones de miembro de conjunto de registros, como `OnSetOptions`, para establecer las opciones específicas de la aplicación o reemplazar los valores predeterminados.  
  
 Si desea basar el conjunto de registros en una instrucción SQL compleja, debe usar una combinación de estas técnicas de personalización. Por ejemplo, es posible que desee utilizar cláusulas SQL y palabras clave no es directamente compatible con conjuntos de registros, o quizás prefiera va a combinar varias tablas.  
  
## <a name="see-also"></a>Vea también  
 [Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Conjunto de registros: Actualizar los registros (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)   
 [Conceptos básicos de ODBC](../../data/odbc/odbc-basics.md)   
 [SQL](../../data/odbc/sql.md)   
 [Conjunto de registros: Bloquear registros (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)