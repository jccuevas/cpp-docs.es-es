---
title: 'Conjunto de registros: Cómo se seleccionan los registros (ODBC)'
ms.date: 05/09/2019
helpviewer_keywords:
- recordsets, selecting records
- record selection, ODBC recordsets
- SQL statements, recordset
- records, selecting
- recordsets, constructing SQL statements
- ODBC recordsets, selecting records
ms.assetid: 343a6a91-aa4c-4ef7-b21f-2f2bfd0d3787
ms.openlocfilehash: 252d17fc56c13415f1068d6b16ed8b1ee663b5f1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212893"
---
# <a name="recordset-how-recordsets-select-records-odbc"></a>Conjunto de registros: Cómo se seleccionan los registros (ODBC)

> [!NOTE]
> El Asistente para consumidores ODBC de MFC no está disponible en Visual Studio 2019 ni en versiones posteriores. Aun así, puede crear un consumidor de forma manual.

Este tema es aplicable a las clases ODBC de MFC.

En este tema se explica:

- [Su rol y las opciones de selección de registros](#_core_your_options_in_selecting_records).

- [Cómo un conjunto de registros crea su instrucción SQL y selecciona los registros](#_core_how_a_recordset_constructs_its_sql_statement).

- [Qué puede hacer para personalizar la selección](#_core_customizing_the_selection).

Los conjuntos de registros seleccionan registros de un origen de datos a través de un controlador ODBC mediante el envío de instrucciones SQL al controlador. El código SQL enviado depende de cómo diseñe y abra la clase de conjunto de registros.

##  <a name="your-options-in-selecting-records"></a><a name="_core_your_options_in_selecting_records"></a> Opciones de selección de registros

En la siguiente tabla se muestran las opciones de selección de registros.

### <a name="how-and-when-you-can-affect-a-recordset"></a>Cómo y cuándo puede alterar un conjunto de registros

|Cuando|Puede|
|--------------|-------------|
|Declara la clase de conjunto de registros con el Asistente para **agregar clases**|Especificar la tabla en la que hacer la selección.<br /><br /> Especificar qué columnas se van a incluir.<br /><br /> Vea [Agregar un consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md).|
|Completa la implementación de la clase de conjunto de registros|Reemplazar funciones miembro, como `OnSetOptions` (avanzado), para establecer opciones específicas de la aplicación o cambiar valores predeterminados. Especificar los miembros de datos de parámetros si quiere un conjunto de registros parametrizado.|
|Construye un objeto de conjunto de registros (antes de llamar a `Open`)|Especificar una condición de búsqueda (posiblemente compuesta) para su uso en una cláusula **WHERE** que filtra los registros. Vea [conjunto de registros: filtrar registros (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md).<br /><br /> Especificar un criterio de ordenación para su uso en una cláusula **ORDER BY** que ordena los registros. Vea [conjunto de registros: ordenar registros (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md).<br /><br /> Especificar valores de parámetros para cualquier parámetro que haya agregado a la clase. Vea [conjunto de registros: parametrizar un conjunto de registros (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).|

|Ejecución de la consulta del conjunto de registros mediante una llamada a `Open`|Especifique una cadena SQL personalizada para reemplazar la cadena SQL predeterminada establecida por el asistente. Vea [CRecordset:: Open](../../mfc/reference/crecordset-class.md#open) en la *referencia* de la biblioteca de clases y [SQL: personalizar la instrucción SQL del conjunto de registros (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md). |

|Llamada a `Requery` para consultar el conjunto de registros con los valores más recientes del origen de datos|Especifique nuevos parámetros, filtre u ordene. Vea [conjunto de registros: reconsultar un conjunto de registros (ODBC)](../../data/odbc/recordset-requerying-a-recordset-odbc.md). |

##  <a name="how-a-recordset-constructs-its-sql-statement"></a><a name="_core_how_a_recordset_constructs_its_sql_statement"></a> Cómo un conjunto de registros crea su instrucción SQL

Cuando se llama a la función miembro [Open](../../mfc/reference/crecordset-class.md#open) de un objeto de conjunto de registros, `Open` construye una instrucción SQL mediante algunos de los elementos siguientes o todos ellos:

- El parámetro *lpszSQL* pasado a `Open`. Si no es NULL, este parámetro especifica una cadena SQL personalizada, o parte de una. El marco analiza la cadena. Si la cadena es una instrucción **SELECT** de SQL o una instrucción **CALL** de ODBC, el marco usa la cadena como instrucción SQL del conjunto de registros. Si la cadena no comienza con "SELECT" o "{CALL", el marco usa los datos proporcionados para construir una cláusula **FROM** de SQL.

- La cadena devuelta por [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql). De forma predeterminada, este es el nombre de la tabla que especificó para el conjunto de registros en el asistente, pero puede cambiar lo que devuelve la función. El marco llama a `GetDefaultSQL` y, si la cadena no comienza con "SELECT" o "{CALL", se da por supuesto que es un nombre de tabla, que se usa para construir una cadena SQL.

- Los miembros de datos de campo del conjunto de registros, que van a enlazarse a columnas específicas de la tabla. El marco enlaza las columnas de registro a las direcciones de estos miembros, que actúan como búferes. Además, el marco determina la correlación de los miembros de datos de campo con las columnas de tabla desde llamadas de función de [RFX](../../data/odbc/record-field-exchange-using-rfx.md) o RFX masivo en la función miembro [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) o [DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) del conjunto de registros.

- El [filtro](../../data/odbc/recordset-filtering-records-odbc.md) del conjunto de registros, si lo hay, contenido en el miembro de datos [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter). El marco usa esta cadena para construir una cláusula **WHERE** de SQL.

- El criterio de [ordenación](../../data/odbc/recordset-sorting-records-odbc.md) del conjunto de registros, si lo hay, contenido en el miembro de datos [m_strSort](../../mfc/reference/crecordset-class.md#m_strsort). El marco usa esta cadena para construir una cláusula **ORDER BY** de SQL.

   > [!TIP]
   > Para usar la cláusula **GROUP BY** de SQL (y posiblemente la cláusula **HAVING**), anexe las cláusulas al final de la cadena de filtro.

- Los valores de cualquiera de los [miembros de datos de parámetros](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) que especifique para la clase. Debe establecer los valores de parámetros antes de llamar a `Open` o `Requery`. El marco enlaza los valores de parámetros a marcadores de posición "?" en la cadena SQL. En tiempo de compilación, especifique la cadena con marcadores de posición. En tiempo de ejecución, el marco rellena los detalles en función de los valores de parámetros que usted pase.

`Open` construye una instrucción **SELECT** de SQL a partir de estos elementos. Vea [Personalización de la selección](#_core_customizing_the_selection) para obtener más información sobre la manera en que el marco usa los elementos.

Después de construir la instrucción, `Open` envía el código SQL al administrador de controladores ODBC (y a la biblioteca de cursores ODBC, si está en memoria), que lo envía a su vez al controlador ODBC para el DBMS (sistema de administración de bases de datos) específico. El controlador se comunica con el DBMS para llevar a cabo la selección en el origen de datos y obtiene el primer registro. El marco carga el registro en los miembros de datos de campo del conjunto de registros.

Puede usar una combinación de estas técnicas para abrir [tablas](../../data/odbc/recordset-declaring-a-class-for-a-table-odbc.md) y construir una consulta basada en una [combinación](../../data/odbc/recordset-performing-a-join-odbc.md) de varias tablas. Si lleva a cabo una mayor personalización, puede llamar a [consultas predefinidas](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md) (procedimientos almacenados), seleccionar columnas de la tabla que no se conocen en tiempo de diseño y [enlazarlas](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md) a campos del conjunto de registros, así como realizar la mayoría de tareas de acceso a datos. Las tareas que no se pueden llevar a cabo mediante la personalización de conjuntos de registros pueden realizarse igualmente mediante una [llamada a funciones de la API de ODBC](../../data/odbc/odbc-calling-odbc-api-functions-directly.md) o a través de la ejecución directa de instrucciones SQL con [CDatabase::ExecuteSQL](../../mfc/reference/cdatabase-class.md#executesql).

##  <a name="customizing-the-selection"></a><a name="_core_customizing_the_selection"></a> Personalización de la selección

Además de proporcionar un filtro, un criterio de ordenación o parámetros, puede realizar las siguientes acciones para personalizar la selección del conjunto de registros:

- Pasar una cadena SQL personalizada en *lpszSQL* al llamar a [Open](../../mfc/reference/crecordset-class.md#open) para el conjunto de registros. Cualquier dato que pase en *lpsqSQL* tendrá prioridad sobre lo que devuelva la función miembro [GetDefaultSQL](../../mfc/reference/crecordset-class.md#getdefaultsql).

   Para obtener más información, vea [SQL: personalizar la instrucción SQL del conjunto de registros (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md), que describe los tipos de instrucciones SQL (o instrucciones parciales) que puede pasar a `Open` y lo que hace el marco de trabajo con ellas.

    > [!NOTE]
    >  Si la cadena personalizada que pasa no comienza con "SELECT" o "{CALL", MFC dará por supuesto que contiene un nombre de tabla. Esto también se aplica al siguiente elemento con viñetas.

- Modificar la cadena en la que escribe el asistente en la función miembro `GetDefaultSQL` del conjunto de registros. Edite el código de la función para cambiar lo que devuelve. De forma predeterminada, el asistente escribe una función `GetDefaultSQL` que devuelve un nombre de tabla.

   Puede hacer que `GetDefaultSQL` devuelva cualquiera de los elementos que pase en el parámetro *lpszSQL* a `Open`. Si no pasa una cadena SQL personalizada en *lpszSQL*, el marco usa la cadena que `GetDefaultSQL` devuelve. Como mínimo, `GetDefaultSQL` debe devolver un nombre de tabla, pero puede hacer que devuelva varios nombres de tabla, una instrucción **SELECT** completa, una instrucción **CALL** de ODBC, etc. Para obtener una lista de lo que se puede pasar a *lpszSQL* (o que `GetDefaultSQL` Return), vea [SQL: personalizar la instrucción SQL del conjunto de registros (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

   Si va a realizar una combinación de dos o más tablas, reescriba `GetDefaultSQL` para personalizar la lista de tabla que se usa en la cláusula **FROM** de SQL. Para obtener más información, vea [conjunto de registros: realizar una combinación (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md).

- Enlazar manualmente miembros de datos de campo adicionales, quizás en función de la información que obtendrá sobre el esquema del origen de datos en tiempo de ejecución. Agregue miembros de datos de campo a la clase de conjunto de registros, llamadas de función de [RFX](../../data/odbc/record-field-exchange-using-rfx.md) o RFX masivo para ellos a la función miembro [DoFieldExchange](../../mfc/reference/crecordset-class.md#dofieldexchange) o [DoBulkFieldExchange](../../mfc/reference/crecordset-class.md#dobulkfieldexchange), e inicializaciones de los miembros de datos en el constructor de clase. Para obtener más información, vea [conjunto de registros: enlazar dinámicamente columnas de datos (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

- Reemplazar funciones miembro de conjunto de registros, como `OnSetOptions`, para establecer opciones específicas de la aplicación o reemplazar valores predeterminados.

Si quiere basar el conjunto de registros en una instrucción SQL compleja, deberá usar una combinación de estas técnicas de personalización. Por ejemplo, es posible que quiera usar cláusulas SQL y palabras clave que los conjuntos de registros no admiten directamente, o quizás va a combinar varias tablas.

## <a name="see-also"></a>Consulte también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Conjunto de registros: Actualizar los registros (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)<br/>
[Conceptos básicos de ODBC](../../data/odbc/odbc-basics.md)<br/>
[SQL](../../data/odbc/sql.md)<br/>
[Conjunto de registros: Bloquear registros (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)
