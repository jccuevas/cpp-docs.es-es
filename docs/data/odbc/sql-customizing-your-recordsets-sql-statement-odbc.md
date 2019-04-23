---
title: 'SQL: Personalizar la instrucción de SQL del conjunto de registros (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- recordsets, SQL statements
- ODBC recordsets, SQL statements
- SQL statements, customizing
- SQL statements, recordset
- customizing SQL statements
- overriding, SQL statements
- SQL, opening recordsets
ms.assetid: 72293a08-cef2-4be2-aa1c-30565fcfbaf9
ms.openlocfilehash: eabaab019ee94b0c5617573c534d920ec710e9b2
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59036200"
---
# <a name="sql-customizing-your-recordsets-sql-statement-odbc"></a>SQL: Personalizar la instrucción de SQL del conjunto de registros (ODBC)

En este tema se explica:

- Cómo el marco de trabajo construye una instrucción SQL

- Invalidación de la instrucción SQL

> [!NOTE]
>  Esta información se aplica a las clases ODBC de MFC. Si está trabajando con las clases DAO de MFC, vea el tema "Comparación de Microsoft Jet base de datos de motor de SQL y ANSI SQL" en la Ayuda de DAO.

## <a name="sql-statement-construction"></a>Construcción de la instrucción SQL

El conjunto de registros basa la selección de registros principalmente en una instancia de SQL **seleccione** instrucción. Al declarar la clase con un asistente, escribe una versión de reemplazo de la `GetDefaultSQL` función miembro que es algo parecido a esto (para una clase de conjunto de registros denominado `CAuthors`).

```cpp
CString CAuthors::GetDefaultSQL()
{
    return "AUTHORS";
}
```

De forma predeterminada, esta invalidación devuelve el nombre de tabla especificado con el asistente. En el ejemplo, el nombre de tabla es "AUTHORS". Cuando se llama posteriormente el conjunto de registros `Open` función miembro, `Open` construye un final **seleccione** instrucción del formulario:

```
SELECT rfx-field-list FROM table-name [WHERE m_strFilter]
       [ORDER BY m_strSort]
```

donde `table-name` se obtiene mediante una llamada a `GetDefaultSQL` y `rfx-field-list` se obtiene a partir de las llamadas de función RFX en `DoFieldExchange`. Esto es lo que obtendrá de un **seleccione** instrucción a menos que se reemplace con una versión de reemplazo en tiempo de ejecución, aunque también puede modificar la instrucción predeterminada mediante parámetros o un filtro.

> [!NOTE]
>  Si especifica un nombre de columna que contiene (o podría contener) espacios, debe incluir el nombre entre corchetes. Por ejemplo, el nombre "First Name" debe ser "[nombre]".

Para invalidar el valor predeterminado **seleccione** instrucción, pase una cadena que contiene un completo **seleccione** instrucción cuando se llama a `Open`. En lugar de construir su propia cadena de forma predeterminada, el conjunto de registros usa la cadena proporcionada. Si la instrucción de reemplazo contiene un **donde** cláusula, no se especifica un filtro en `m_strFilter` ya que, a continuación, tendría dos instrucciones de filtro. De forma similar, si la instrucción de reemplazo contiene un **ORDER BY** cláusula, no especifique una ordenación en `m_strSort` para que no tendrá dos ordenación las instrucciones.

> [!NOTE]
>  Si utiliza cadenas literales en los filtros (o en otras partes de la instrucción SQL), es posible que deba "oferta" (encerrarlo entre delimitadores especificados) dichas cadenas con un prefijo literal específicos para DBMS y literal sufijo caracteres (o caracteres).

También podría producir requisitos sintácticos especiales para operaciones como las combinaciones externas, según el DBMS. Usar funciones de ODBC para obtener esta información desde el controlador para el DBMS. Por ejemplo, llamar a `::SQLGetTypeInfo` para un tipo de datos determinado, como `SQL_VARCHAR`, para solicitar los caracteres LITERAL_PREFIX y LITERAL_SUFFIX. Si está escribiendo código independiente de la base de datos, consulte [Apéndice C: Gramática de SQL](/sql/odbc/reference/appendixes/appendix-c-sql-grammar) en el [referencia del programador de ODBC](/sql/odbc/reference/odbc-programmer-s-reference) para información sobre la sintaxis detallada.

Un objeto recordset construye la instrucción SQL que utiliza para seleccionar registros a menos que pase una instrucción SQL personalizada. Cómo hacerlo depende principalmente del valor pasado en el *lpszSQL* parámetro de la `Open` función miembro.

La forma general de una instancia de SQL **seleccione** instrucción es:

```
SELECT [ALL | DISTINCT] column-list FROM table-list
    [WHERE search-condition][ORDER BY column-list [ASC | DESC]]
```

Una forma de agregar el **DISTINCT** palabra clave para la instrucción de SQL del conjunto de registros es insertar la palabra clave en la primera llamada de función RFX en `DoFieldExchange`. Por ejemplo:

```
...
    RFX_Text(pFX, "DISTINCT CourseID", m_strCourseID);
...
```

> [!NOTE]
>  Use esta técnica solo con un conjunto de registros abierto como de solo lectura.

## <a name="overriding-the-sql-statement"></a>Reemplazar la instrucción SQL

En la siguiente tabla muestra las posibilidades de la *lpszSQL* parámetro `Open`. Se explican los casos en la tabla de la tabla siguiente.

**El parámetro lpszSQL y la cadena resultante de SQL**

|Caso|Lo que se pasa en lpszSQL|La instrucción SELECT resultante|
|----------|------------------------------|------------------------------------|
|1|NULL|**Seleccione** *lista de campos de rfx* **FROM** *nombre de tabla*<br /><br /> `CRecordset::Open` las llamadas `GetDefaultSQL` para obtener el nombre de tabla. La cadena resultante es uno de los casos 2 a 5, dependiendo de lo que `GetDefaultSQL` devuelve.|
|2|Un nombre de tabla|**Seleccione** *lista de campos de rfx* **FROM** *nombre de tabla*<br /><br /> Se toma la lista de campos de las instrucciones de RFX en `DoFieldExchange`. Si `m_strFilter` y `m_strSort` no están vacíos, agrega el **donde** o **ORDER BY** cláusulas.|
|3 \*|Una completa **seleccione** instrucción pero sin un **donde** o **ORDER BY** cláusula|Que se pasa. Si `m_strFilter` y `m_strSort` no están vacíos, agrega el **donde** o **ORDER BY** cláusulas.|
|4 \*|Una completa **seleccione** instrucción con un **donde** o **ORDER BY** cláusula|Que se pasa. `m_strFilter` o `m_strSort` debe permanecer vacío o un filtro de dos o se producen instrucciones de ordenación.|
|5 \*|Una llamada a un procedimiento almacenado|Que se pasa.|

\* `m_nFields` debe ser menor o igual que el número de columnas especificadas en el **seleccione** instrucción. El tipo de datos de cada columna especificada en el **seleccione** instrucción debe ser el mismo que el tipo de datos de la columna de salida RFX correspondiente.

### <a name="case-1---lpszsql--null"></a>Case 1   lpszSQL = NULL

La selección de conjunto de registros depende de qué `GetDefaultSQL` devuelve cuándo `CRecordset::Open` lo llama. Los casos 2 a 5 describen las posibles cadenas.

### <a name="case-2---lpszsql--a-table-name"></a>Caso 2 lpszSQL = un nombre de tabla

El conjunto de registros usa intercambio de campos de registros (RFX) para crear la lista de columnas de los nombres de columna proporcionados en el RFX llamadas función en la invalidación de la clase de conjunto de registros de `DoFieldExchange`. Si usa a un Asistente para declarar la clase de conjunto de registros, en este caso tiene el mismo resultado que el caso 1 (siempre que se pase el mismo nombre de tabla especificado en el asistente). Si no utiliza a un Asistente para escribir la clase, caso 2 es la manera más sencilla de crear la instrucción SQL.

El ejemplo siguiente crea una instrucción SQL que selecciona los registros desde una aplicación de base de datos MFC. Cuando el marco llama a la `GetDefaultSQL` función miembro, la función devuelve el nombre de la tabla, `SECTION`.

```cpp
CString CEnrollSet::GetDefaultSQL()
{
    return "SECTION";
}
```

Para obtener los nombres de las columnas para el SQL **seleccione** instrucción, llama el marco del `DoFieldExchange` función miembro.

```cpp
void CEnrollSet::DoFieldExchange(CFieldExchange* pFX)
{
    pFX->SetFieldType(CFieldExchange::outputColumn);
    RFX_Text(pFX, "CourseID", m_strCourseID);
    RFX_Text(pFX, "InstructorID", m_strInstructorID);
    RFX_Text(pFX, "RoomNo", m_strRoomNo);
    RFX_Text(pFX, "Schedule", m_strSchedule);
    RFX_Text(pFX, "SectionNo", m_strSectionNo);
}
```

Cuando haya terminado, la instrucción SQL tiene este aspecto:

```sql
SELECT CourseID, InstructorID, RoomNo, Schedule, SectionNo
    FROM SECTION
```

### <a name="case-3---lpszsql--a-selectfrom-statement"></a>Caso 3 lpszSQL = una instrucción SELECT de la instrucción

Especifique manualmente la lista de columnas en lugar de depender de RFX genere automáticamente. Es posible que desee hacerlo cuando:

- Para especificar el **DISTINCT** siguiente de la palabra clave **seleccione**.

   La lista de columnas debe coincidir con los nombres de columna y tipos en el mismo orden en que aparecen en `DoFieldExchange`.

- Tiene razón para recuperar manualmente los valores de columna mediante la función ODBC `::SQLGetData` en lugar de depender de RFX enlace y recupere las columnas.

   Por ejemplo, podría dar cabida a nuevas columnas a que un cliente de la aplicación se agrega a las tablas de base de datos después de que se ha distribuido la aplicación. Deberá agregar a estos miembros de datos de campo adicional que no eran conocidos en el momento de que declarar la clase con el asistente.

   La lista de columnas debe coincidir con los nombres de columna y tipos en el mismo orden en que aparecen en `DoFieldExchange`, seguido de los nombres de las columnas enlazadas manualmente. Para obtener más información, consulte [conjunto de registros: Enlazar dinámicamente columnas de datos (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

- Desea unir tablas mediante la especificación de varias tablas en el **FROM** cláusula.

   Para obtener información y un ejemplo, vea [conjunto de registros: Realizar una combinación (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md).

### <a name="case-4---lpszsql--selectfrom-plus-where-andor-order-by"></a>Caso 4 lpszSQL = SELECT / FROM más WHERE u ORDER BY

Especifica todo: la lista de columnas (en función de las llamadas RFX en `DoFieldExchange`), la lista de tablas y el contenido de un **donde** o un **ORDER BY** cláusula. Si especifica su **donde** o **ORDER BY** cláusulas de este modo, no use `m_strFilter` o `m_strSort`.

### <a name="case-5---lpszsql--a-stored-procedure-call"></a>Caso 5 lpszSQL = una llamada de procedimiento almacenado

Si necesita llamar a una consulta predefinida (por ejemplo, un procedimiento almacenado en una base de datos de Microsoft SQL Server), debe escribir un **llamar** instrucción en la cadena que pasa a *lpszSQL*. Los asistentes no admiten declarar una clase de conjunto de registros para llamar a una consulta predefinida. No todas las consultas predefinidas devuelven registros.

Si una consulta predefinida no devuelve registros, puede usar el `CDatabase` función miembro `ExecuteSQL` directamente. Para una consulta predefinida que devuelven registros, debe escribir manualmente las llamadas RFX en `DoFieldExchange` para todas las columnas que devuelve el procedimiento. Las llamadas RFX deben estar en el mismo orden y devolver los mismos tipos, como la consulta predefinida. Para obtener más información, consulte [conjunto de registros: Declarar una clase para una consulta predefinida (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md).

## <a name="see-also"></a>Vea también

[SQL: SQL y tipos de datos de C++ (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)<br/>
[SQL: Realizar llamadas directas a SQL (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)
