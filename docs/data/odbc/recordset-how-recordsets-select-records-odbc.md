---
title: 'Conjunto de registros: ¿Cómo se seleccionan los registros (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- recordsets, selecting records
- record selection, ODBC recordsets
- SQL statements, recordset
- records, selecting
- recordsets, constructing SQL statements
- ODBC recordsets, selecting records
ms.assetid: 343a6a91-aa4c-4ef7-b21f-2f2bfd0d3787
ms.openlocfilehash: 310481a6ea6637de817bf29d528cbdfe70ae70db
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59041330"
---
# <a name="recordset-how-recordsets-select-records-odbc"></a>Conjunto de registros: ¿Cómo se seleccionan los registros (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

En este tema se explica:

- [Su rol y las opciones de selección de registros](#_core_your_options_in_selecting_records).

- [Cómo un conjunto de registros crea su instrucción SQL y selecciona los registros](#_core_how_a_recordset_constructs_its_sql_statement).

- [Lo que puede hacer para personalizar la selección](#_core_customizing_the_selection).

Conjuntos de registros seleccionan los registros de un origen de datos a través de un controlador ODBC mediante el envío de instrucciones SQL para el controlador. El código SQL enviado depende de cómo diseñar y abra la clase de conjunto de registros.

##  <a name="_core_your_options_in_selecting_records"></a> Las opciones de selección de registros

La siguiente tabla muestra las opciones de selección de registros.

### <a name="how-and-when-you-can-affect-a-recordset"></a>Cómo y cuándo puede afectar a un conjunto de registros

|Cuando se|Puede|
|--------------|-------------|
|Declare la clase de conjunto de registros con el **Agregar clase** Asistente|Especifique la tabla que desea seleccionar desde.<br /><br /> Especificar qué columnas desea incluir.<br /><br /> Consulte [agregar un consumidor ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).|
|Completar la implementación de la clase de conjunto de registros|Reemplazar funciones miembro como `OnSetOptions` (avanzado) para establecer las opciones específicas de la aplicación o para cambiar los valores predeterminados. Especifique a los miembros de datos del parámetro si desea que un conjunto de registros con parámetros.|
|Construya un objeto de conjunto de registros (antes de llamar a `Open`)|Especificar una condición de búsqueda (posiblemente compuesta) para su uso en un **donde** cláusula que filtra los registros. Consulte [conjunto de registros: Filtrar registros (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).<br /><br /> Especifique un criterio de ordenación para su uso en un **ORDER BY** cláusula que ordena los registros. Consulte [conjunto de registros: Ordenar registros (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md).<br /><br /> Especifique valores para los parámetros que agregó a la clase. Consulte [conjunto de registros: Parametrizar un conjunto de registros (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).|

| Ejecutar la consulta del conjunto de registros mediante una llamada a `Open`| Especifique una cadena SQL personalizada para reemplazar la cadena de SQL predeterminado establecida por el asistente. Consulte [CRecordset:: Open](../../mfc/reference/crecordset-class.md#open) en el *referencia de la biblioteca de clases* y [SQL: Personalizar la instrucción de SQL del conjunto de registros (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md). |

| Llame a `Requery` para consultar el conjunto de registros con los valores más recientes del origen de datos | Especifique los nuevos parámetros, filtrar u ordenar. Consulte [conjunto de registros: Volver a consultar un conjunto de registros (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md). |

##  <a name="_core_how_a_recordset_constructs_its_sql_statement"></a> Cómo crea un conjunto de registros su instrucción SQL

Cuando se llama a un objeto recordset [abierto](../../mfc/reference/crecordset-class.md#open) función miembro, `Open` construye una instrucción SQL mediante algunos o todos los elementos de los siguientes:

- El *lpszSQL* parámetro pasado a `Open`. Si no es NULL, este parámetro especifica una cadena SQL personalizada o parte de uno. El marco de trabajo analiza la cadena. Si la cadena es una instancia de SQL **seleccione** instrucción o un ODBC **llamar** instrucción, el marco de trabajo usa la cadena como instrucción de SQL del conjunto de registros. Si la cadena no comienza con "SELECT" o "{CALL", el marco de trabajo usa los datos proporcionados para construir una instancia de SQL **FROM** cláusula.

- La cadena devuelta por [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql). De forma predeterminada, este es el nombre de la tabla especificada para el conjunto de registros en el asistente, pero puede cambiar la función que devuelve. Las llamadas de framework `GetDefaultSQL` : si la cadena no comienza con "SELECT" o "{CALL", se supone que es un nombre de tabla, que se usa para construir una cadena SQL.


- El campo miembros de datos del conjunto de registros, que se van a enlazarse a columnas específicas de la tabla. El marco de trabajo enlaza las columnas de registro a las direcciones de estos miembros, que actúan como búferes. El marco de trabajo determina la correlación de los miembros de datos a columnas de tabla desde el [RFX](../../data/odbc/record-field-exchange-using-rfx.md) las llamadas de función RFX masivo en el conjunto de registros o [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) o [DoBulkFieldExchange ](../../mfc/reference/crecordset-class.md#dofieldexchange) función miembro.

- El [filtro](../../data/odbc/recordset-filtering-records-odbc.md) para el conjunto de registros, si lo hay, contenido en el [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) miembro de datos. El marco de trabajo utiliza esta cadena para construir una instancia de SQL **donde** cláusula.

- El [ordenación](../../data/odbc/recordset-sorting-records-odbc.md) orden para el conjunto de registros, si lo hay, contenido en el [m_strSort](../../mfc/reference/crecordset-class.md#m_strsort) miembro de datos. El marco de trabajo utiliza esta cadena para construir una instancia de SQL **ORDER BY** cláusula.

   > [!TIP]
   > Para usar la instrucción SQL **GROUP BY** cláusula (y posiblemente la **HAVING** cláusula), anexe las cláusulas al final de la cadena de filtro.

- Los valores de cualquier [los miembros de datos de parámetro](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) que especifique para la clase. Establecer valores de parámetro antes de llamar a `Open` o `Requery`. El marco de trabajo enlaza los valores de parámetro "?" marcadores de posición en la cadena SQL. En tiempo de compilación, especifique la cadena con marcadores de posición. En tiempo de ejecución, el marco de trabajo se rellena en los detalles en función de los valores de parámetro pasados.

`Open` Construye una instancia de SQL **seleccione** instrucción a partir de estos elementos. Consulte [personalizar la selección](#_core_customizing_the_selection) para obtener más información acerca de cómo el marco de trabajo usa los ingredientes.

Después de crear la instrucción, `Open` envía el código SQL para el Administrador de controladores ODBC (y la biblioteca de cursores ODBC, si está en memoria), que envía al controlador ODBC para DBMS específicos. El controlador se comunica con el DBMS para llevar a cabo la selección del origen de datos y obtiene el primer registro. El marco de trabajo carga el registro en los miembros de datos de campo del conjunto de registros.

Puede usar una combinación de estas técnicas para abrir [tablas](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md) y construir una consulta basada en un [combinación](../../data/odbc/recordset-performing-a-join-odbc.md) de varias tablas. Con la personalización adicional, puede llamar a [consultas predefinidas](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md) (procedimientos almacenados), seleccione las columnas que no se conoce en tiempo de diseño de tabla y [enlazar](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md) a campos de conjunto de registros o pueden realizar la mayoría otras tareas de acceso a datos. Todavía pueden realizarse mediante las tareas que no se puede realizar mediante la personalización de conjuntos de registros [llamar a funciones API de ODBC](../../data/odbc/odbc-calling-odbc-api-functions-directly.md) o ejecutar directamente las instrucciones SQL con [CDatabase:: ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql).

##  <a name="_core_customizing_the_selection"></a> Personalización de la selección

Además de proporcionar un filtro, un criterio de ordenación o parámetros, se pueden realizar las siguientes acciones para personalizar la selección del conjunto de registros:

- Pasar una cadena SQL personalizada en *lpszSQL* cuando se llama a [abierto](../../mfc/reference/crecordset-class.md#open) para el conjunto de registros. Cualquier dato que se pase en *lpsqSQL* tiene prioridad sobre lo que el [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql) devuelve la función miembro.

   Para obtener más información, consulte [SQL: Personalizar la instrucción de SQL Server (ODBC de un conjunto de registros)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md), que describen los tipos de instrucciones SQL (o instrucciones parciales) puede pasar a `Open` y lo que hace el marco de trabajo con ellos.

    > [!NOTE]
    >  Si la cadena personalizada que se pasa no comienza con "SELECT" o "{CALL", MFC supone que contiene un nombre de tabla. Esto también se aplica al elemento con viñetas siguiente.

- Modificar la cadena que el asistente escribe en el conjunto de registros `GetDefaultSQL` función miembro. Editar código de la función para cambiar lo que devuelve. De forma predeterminada, el asistente escribe un `GetDefaultSQL` función que devuelve un nombre de tabla.

   Puede tener `GetDefaultSQL` devolver cualquiera de los elementos que se pueden pasar en el *lpszSQL* parámetro `Open`. Si no pasa una cadena SQL personalizada en *lpszSQL*, el marco de trabajo usa la cadena que `GetDefaultSQL` devuelve. Como mínimo, `GetDefaultSQL` debe devolver un nombre de tabla. Pero se puede hacer que devuelva varios nombres de tabla, un completo **seleccione** instrucción, una ODBC **llamar** instrucción y así sucesivamente. Para obtener una lista de lo que se puede pasar a *lpszSQL* , o tiene `GetDefaultSQL` devolver: consulte [SQL: Personalizar la instrucción de SQL del conjunto de registros (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

   Si va a realizar una combinación de dos o más tablas, vuelva a `GetDefaultSQL` para personalizar la lista de tabla utilizada en el código SQL **FROM** cláusula. Para obtener más información, consulte [conjunto de registros: Realizar una combinación (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md).


- Enlazar manualmente los miembros de datos de campo adicional, quizás basados en información que obtendrá sobre el esquema del origen de datos en tiempo de ejecución. Agregar miembros de datos de campo a la clase de conjunto de registros, [RFX](../../data/odbc/record-field-exchange-using-rfx.md) o llamadas de función RFX masivo para que hagan el [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) o [DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange) función miembro, y inicializaciones de los miembros de datos en el constructor de clase. Para obtener más información, consulte [conjunto de registros: Enlazar dinámicamente columnas de datos (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

- Invalidar las funciones miembro de conjunto de registros, como `OnSetOptions`, para establecer las opciones específicas de la aplicación o reemplazar los valores predeterminados.

Si desea basar el conjunto de registros en una instrucción SQL compleja, deberá usar una combinación de estas técnicas de personalización. Por ejemplo, es posible que desee utilizar las cláusulas SQL y las palabras clave no admitidas directamente los conjuntos de registros o quizás que va a combinar varias tablas.

## <a name="see-also"></a>Vea también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Conjunto de registros: Cómo actualizar los registros (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)<br/>
[Conceptos básicos de ODBC](../../data/odbc/odbc-basics.md)<br/>
[SQL](../../data/odbc/sql.md)<br/>
[Conjunto de registros: Bloquear registros (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)