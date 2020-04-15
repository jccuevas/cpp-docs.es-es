---
title: 'SQL: Personalizar la instrucción SQL del conjunto de registros (ODBC)'
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
ms.openlocfilehash: 083d268d2b2f2eef072809b1afde9d6ea34f6996
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374519"
---
# <a name="sql-customizing-your-recordsets-sql-statement-odbc"></a>SQL: Personalizar la instrucción SQL del conjunto de registros (ODBC)

En este tema se explica:

- Cómo el marco de trabajo construye una instrucción SQL

- Cómo invalidar la instrucción SQL

> [!NOTE]
> Esta información es aplicable a las clases ODBC de MFC. Si está trabajando con las clases DAO de MFC, vea el tema "Comparación de Microsoft Jet Database Engine SQL y ANSI SQL" en la Ayuda de DAO.

## <a name="sql-statement-construction"></a>Construcción de instrucciones SQL

El conjunto de registros basa la selección de registros principalmente en una instrucción **SELECT** de SQL. Cuando se declara la clase con un asistente, escribe `GetDefaultSQL` una versión de reemplazo de la `CAuthors`función miembro que tiene un aspecto similar al siguiente (para una clase de conjunto de registros denominada ).

```cpp
CString CAuthors::GetDefaultSQL()
{
    return "AUTHORS";
}
```

De forma predeterminada, esta invalidación devuelve el nombre de tabla que especificó con el asistente. En el ejemplo, el nombre de la tabla es "AUTHORS." Cuando más adelante se `Open` llama a `Open` la función miembro del conjunto de registros, construye una instrucción **SELECT** final del formulario:

```
SELECT rfx-field-list FROM table-name [WHERE m_strFilter]
       [ORDER BY m_strSort]
```

donde `table-name` se obtiene `GetDefaultSQL` llamando `rfx-field-list` y se obtiene de las `DoFieldExchange`llamadas de función RFX en . Esto es lo que se obtiene para una instrucción **SELECT** a menos que la reemplace por una versión de reemplazo en tiempo de ejecución, aunque también puede modificar la instrucción predeterminada con parámetros o un filtro.

> [!NOTE]
> Si especifica un nombre de columna que contenga (o pueda contener) espacios, debe incluir el nombre entre corchetes. Por ejemplo, el nombre "Nombre" debe ser "[Nombre]".

Para invalidar la instrucción **SELECT** predeterminada, pase una `Open`cadena que contenga una instrucción **SELECT** completa cuando llame a . En lugar de construir su propia cadena predeterminada, el conjunto de registros utiliza la cadena que proporciona. Si la instrucción de reemplazo contiene una `m_strFilter` cláusula **WHERE,** no especifique un filtro porque, a continuación, tendría dos instrucciones de filtro. Del mismo modo, si la instrucción de reemplazo `m_strSort` contiene una cláusula **ORDER BY,** no especifique una ordenación para que no tenga dos instrucciones de ordenación.

> [!NOTE]
> Si utiliza cadenas literales en los filtros (u otras partes de la instrucción SQL), es posible que tenga que "citar" (incluir en delimitadores especificados) dichas cadenas con un prefijo literal específico de DBMS y un carácter de sufijo literal (o caracteres).

También puede encontrar requisitos sintácticos especiales para operaciones como combinaciones externas, dependiendo de su DBMS. Utilice las funciones ODBC para obtener esta información del controlador para el DBMS. Por ejemplo, `::SQLGetTypeInfo` llame a un tipo `SQL_VARCHAR`de datos determinado, como , para solicitar los caracteres LITERAL_PREFIX y LITERAL_SUFFIX. Si está escribiendo código independiente de la base de datos, vea [Apéndice C: Gramática SQL](/sql/odbc/reference/appendixes/appendix-c-sql-grammar) en la referencia del programador [ODBC](/sql/odbc/reference/odbc-programmer-s-reference) para obtener información de sintaxis detallada.

Un objeto de conjunto de registros construye la instrucción SQL que utiliza para seleccionar registros a menos que pase una instrucción SQL personalizada. La forma en que se hace esto depende principalmente del `Open` valor que se pasa en el parámetro *lpszSQL* de la función miembro.

La forma general de una instrucción **SELECT** de SQL es:

```
SELECT [ALL | DISTINCT] column-list FROM table-list
    [WHERE search-condition][ORDER BY column-list [ASC | DESC]]
```

Una forma de agregar la palabra clave **DISTINCT** a la instrucción SQL del `DoFieldExchange`conjunto de registros es incrustar la palabra clave en la primera llamada de función RFX en . Por ejemplo:

```
...
    RFX_Text(pFX, "DISTINCT CourseID", m_strCourseID);
...
```

> [!NOTE]
> Utilice esta técnica solo con un conjunto de registros abierto como de solo lectura.

## <a name="overriding-the-sql-statement"></a>Reemplazar la instrucción SQL

En la tabla siguiente se muestran las `Open`posibilidades del parámetro *lpszSQL* en . Los casos de la tabla se explican a continuación de la tabla.

**El parámetro lpszSQL y la cadena SQL resultante**

|Caso|Lo que se pasa en lpszSQL|La instrucción SELECT resultante|
|----------|------------------------------|------------------------------------|
|1|NULL|**SELECT** *rfx-field-list* **FROM** nombre de *tabla*<br /><br /> `CRecordset::Open`llamadas `GetDefaultSQL` para obtener el nombre de la tabla. La cadena resultante es uno de los casos `GetDefaultSQL` 2 a 5, dependiendo de lo que devuelve.|
|2|Un nombre de tabla|**SELECT** *rfx-field-list* **FROM** nombre de *tabla*<br /><br /> La lista de campos se toma `DoFieldExchange`de las instrucciones RFX en . Si `m_strFilter` `m_strSort` y no están vacíos, agrega las cláusulas **WHERE** y/o **ORDER BY.**|
|3\*|Una instrucción **SELECT** completa pero sin una cláusula **WHERE** u **ORDER BY**|A medida que pasa. Si `m_strFilter` `m_strSort` y no están vacíos, agrega las cláusulas **WHERE** y/o **ORDER BY.**|
|4\*|Una instrucción **SELECT** completa con una cláusula **WHERE** y/o **ORDER BY**|A medida que pasa. `m_strFilter`y/o `m_strSort` deben permanecer vacíos, o se producen dos sentencias de filtro y/o de ordenación.|
|5\*|Una llamada a un procedimiento almacenado|A medida que pasa.|

\*`m_nFields` debe ser menor o igual que el número de columnas especificado en la instrucción **SELECT.** El tipo de datos de cada columna especificada en la instrucción **SELECT** debe ser el mismo que el tipo de datos de la columna de salida RFX correspondiente.

### <a name="case-1---lpszsql--null"></a>Caso 1 lpszSQL - NULL

La selección del `GetDefaultSQL` conjunto `CRecordset::Open` de registros depende de lo que se devuelve cuando se llama. Los casos 2 a 5 describen las posibles cadenas.

### <a name="case-2---lpszsql--a-table-name"></a>Caso 2 lpszSQL - un nombre de tabla

El conjunto de registros utiliza el intercambio de campos de registros (RFX) para crear la `DoFieldExchange`lista de columnas a partir de los nombres de columna proporcionados en las llamadas de función RFX en la invalidación de la clase de conjunto de registros de . Si ha utilizado un asistente para declarar la clase de conjunto de registros, este caso tiene el mismo resultado que el caso 1 (siempre que pase el mismo nombre de tabla que especificó en el asistente). Si no utiliza un asistente para escribir la clase, el caso 2 es la forma más sencilla de construir la instrucción SQL.

En el ejemplo siguiente se construye una instrucción SQL que selecciona registros de una aplicación de base de datos MFC. Cuando el marco `GetDefaultSQL` de trabajo llama a la función miembro, la función devuelve el nombre de la tabla, `SECTION`.

```cpp
CString CEnrollSet::GetDefaultSQL()
{
    return "SECTION";
}
```

Para obtener los nombres de **SELECT** las columnas de la `DoFieldExchange` instrucción SELECT de SQL, el marco de trabajo llama a la función miembro.

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

Cuando se completa, la instrucción SQL tiene este aspecto:

```sql
SELECT CourseID, InstructorID, RoomNo, Schedule, SectionNo
    FROM SECTION
```

### <a name="case-3---lpszsql--a-selectfrom-statement"></a>Caso 3 lpszSQL - una instrucción SELECT/FROM

Especifique la lista de columnas a mano en lugar de confiar en RFX para construirla automáticamente. Es posible que desee hacer esto cuando:

- Desea especificar la palabra clave **DISTINCT** después de **SELECT**.

   La lista de columnas debe coincidir con los nombres y `DoFieldExchange`tipos de columna en el mismo orden en que se enumeran en .

- Tiene motivos para recuperar manualmente los `::SQLGetData` valores de columna mediante la función ODBC en lugar de depender de RFX para enlazar y recuperar columnas por usted.

   Por ejemplo, es posible que desee dar cabida a nuevas columnas que un cliente de la aplicación haya agregado a las tablas de base de datos después de distribuir la aplicación. Debe agregar estos miembros de datos de campo adicionales, que no se conocían en el momento en que declaró la clase con un asistente.

   La lista de columnas debe coincidir con los nombres y `DoFieldExchange`tipos de columna en el mismo orden en que se enumeran, seguido de los nombres de las columnas enlazadas manualmente. Para obtener más información, vea [Conjunto de registros: enlazar dinámicamente columnas de datos (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).

- Desea combinar tablas especificando varias tablas en la cláusula **FROM.**

   Para obtener información y un ejemplo, vea [Conjunto de registros: realizar una combinación (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md).

### <a name="case-4---lpszsql--selectfrom-plus-where-andor-order-by"></a>Caso 4 lpszSQL - SELECT/FROM Plus WHERE y/u ORDER BY

Especifique todo: la lista de columnas (basada `DoFieldExchange`en las llamadas RFX en ), la lista de tablas y el contenido de una cláusula **WHERE** y/o **ORDER BY.** Si especifica las cláusulas **WHERE** y/o **ORDER** BY `m_strFilter` de `m_strSort`esta manera, no utilice y/o .

### <a name="case-5---lpszsql--a-stored-procedure-call"></a>Caso 5 lpszSQL - una llamada a procedimiento almacenado

Si necesita llamar a una consulta predefinida (por ejemplo, un procedimiento almacenado en una base de datos de Microsoft SQL Server), debe escribir una instrucción **CALL** en la cadena que pase a *lpszSQL*. Los asistentes no admiten la declaración de una clase de conjunto de registros para llamar a una consulta predefinida. No todas las consultas predefinidas devuelven registros.

Si una consulta predefinida no devuelve registros, puede usar la `CDatabase` función `ExecuteSQL` miembro directamente. Para una consulta predefinida que devuelve registros, también debe `DoFieldExchange` escribir manualmente las llamadas RFX para las columnas que devuelve el procedimiento. Las llamadas RFX deben estar en el mismo orden y devolver los mismos tipos, como la consulta predefinida. Para obtener más información, vea [Conjunto de registros: declarar una clase para una consulta predefinida (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md).

## <a name="see-also"></a>Consulte también

[SQL: Tipos de datos de SQL y C++ (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)<br/>
[SQL: Realizar llamadas directas a SQL (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)
