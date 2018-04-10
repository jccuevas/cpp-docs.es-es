---
title: 'SQL: Personalizar la instrucción de SQL del conjunto de registros (ODBC) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- recordsets, SQL statements
- ODBC recordsets, SQL statements
- SQL statements, customizing
- SQL statements, recordset
- customizing SQL statements
- overriding, SQL statements
- SQL, opening recordsets
ms.assetid: 72293a08-cef2-4be2-aa1c-30565fcfbaf9
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3099fbf6b97f3ad18a28c071fcd08ec8280fa24a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="sql-customizing-your-recordsets-sql-statement-odbc"></a>SQL: Personalizar la instrucción SQL del conjunto de registros (ODBC)
En este tema se explica:  
  
-   Cómo el marco de trabajo construye una instrucción SQL  
  
-   Cómo reemplazar la instrucción SQL  
  
> [!NOTE]
>  Esta información se aplica a las clases ODBC de MFC. Si está trabajando con las clases DAO de MFC, vea el tema "Comparación de SQL del motor de base de datos de datos Microsoft Jet y SQL ANSI" en la Ayuda de DAO.  
  
## <a name="sql-statement-construction"></a>Creación de instrucciones SQL  
 El conjunto de registros basa la selección de registros principalmente en una instancia de SQL **seleccione** instrucción. Cuando se declara la clase con un asistente, escribe una versión de reemplazo de la `GetDefaultSQL` función miembro que es algo parecido a esto (para una clase de conjunto de registros denominado `CAuthors`).  
  
```  
CString CAuthors::GetDefaultSQL()  
{  
    return "AUTHORS";  
}  
```  
  
 De forma predeterminada, este reemplazo devuelve el nombre de tabla especificado con el asistente. En el ejemplo, el nombre de tabla es "AUTHORS". Cuando se llama posteriormente el conjunto de registros **abiertos** función miembro, **abiertos** construye un final **seleccione** instrucción del formulario:  
  
```  
SELECT rfx-field-list FROM table-name [WHERE m_strFilter]   
       [ORDER BY m_strSort]  
```  
  
 donde `table-name` se obtiene mediante una llamada a `GetDefaultSQL` y `rfx-field-list` se obtiene de las llamadas de función RFX en `DoFieldExchange`. Esto es lo que se obtiene de un **seleccione** instrucción a menos que se reemplace con una versión de reemplazo en tiempo de ejecución, aunque también puede modificar la instrucción predeterminada mediante parámetros o un filtro.  
  
> [!NOTE]
>  Si especifica un nombre de columna que contiene (o podría contener) espacios, debe incluir el nombre entre corchetes. Por ejemplo, el nombre "Nombre" debe ser "[nombre]".  
  
 Para invalidar el valor predeterminado **seleccione** instrucción, pase una cadena que contiene un completo **seleccione** instrucción cuando se llama a **abiertos**. En lugar de crear su propia cadena predeterminada, el conjunto de registros utiliza la cadena proporcionada. Si la instrucción de reemplazo contiene un **donde** cláusula, no se especifica un filtro en **m_strFilter** porque, a continuación, tendría dos instrucciones de filtro. De forma similar, si la instrucción de reemplazo contiene un **ORDER BY** cláusula, no especifique una ordenación en `m_strSort` para que no tendrá que ordenación las dos instrucciones.  
  
> [!NOTE]
>  Si utiliza cadenas literales en los filtros (u otras partes de la instrucción SQL), es posible que deba "quote" (incluir entre delimitadores especificados) esas cadenas con un prefijo literal específicos del DBMS y literales sufijo caracteres (o caracteres).  
  
 También podría producir requisitos sintácticos especiales para operaciones como las combinaciones externas, según el DBMS. Usar funciones ODBC para obtener esta información desde el controlador del DBMS. Por ejemplo, llamar a **:: SQLGetTypeInfo** para un tipo de datos determinado, como **SQL_VARCHAR**, para solicitar la **caracteres LITERAL_PREFIX** y **LITERAL_SUFFIX** caracteres. Si está escribiendo código independiente de la base de datos, consulte el apéndice C en el *el SDK de ODBC**referencia del programador* en el CD de MSDN Library para obtener información de sintaxis detallada.  
  
 Un objeto de conjunto de registros crea la instrucción SQL que utiliza para seleccionar registros a menos que se pase una instrucción SQL personalizada. Cómo llevarlo a cabo depende principalmente del valor se pasa en el `lpszSQL` parámetro de la **abiertos** función miembro.  
  
 La forma general de una instancia de SQL **seleccione** instrucción es:  
  
```  
SELECT [ALL | DISTINCT] column-list FROM table-list  
    [WHERE search-condition][ORDER BY column-list [ASC | DESC]]  
```  
  
 Una manera de agregar el **DISTINCT** palabra clave a la instrucción de SQL del conjunto de registros es incrustarla en la primera llamada de función RFX en `DoFieldExchange`. Por ejemplo:  
  
```  
...  
    RFX_Text(pFX, "DISTINCT CourseID", m_strCourseID);  
...  
```  
  
> [!NOTE]
>  Utilice esta técnica solo con un conjunto de registros abierto como de solo lectura.  
  
## <a name="overriding-the-sql-statement"></a>Reemplazar la instrucción SQL  
 La siguiente tabla muestra las posibilidades de la `lpszSQL` parámetro **abiertos**. Se explican los casos de la tabla de la tabla siguiente.  
  
 **El parámetro lpszSQL y la cadena SQL resultante**  
  
|Caso|Se pasa en lpszSQL|La instrucción SELECT resultante.|  
|----------|------------------------------|------------------------------------|  
|1|**NULL**|**Seleccione** *lista de campos de rfx* **FROM** *nombre de la tabla*<br /><br /> `CRecordset::Open`llamadas `GetDefaultSQL` para obtener el nombre de tabla. La cadena resultante es uno de los casos 2 a 5, dependiendo de lo que `GetDefaultSQL` devuelve.|  
|2|Un nombre de tabla|**Seleccione** *lista de campos de rfx* **FROM** *nombre de la tabla*<br /><br /> La lista de campos se toma de las instrucciones RFX en `DoFieldExchange`. Si **m_strFilter** y `m_strSort` no están vacíos, agrega el **donde** o **ORDER BY** cláusulas.|  
|3 *|Una completa **seleccione** instrucción pero sin un **donde** o **ORDER BY** cláusula|Tal y como se pasa. Si **m_strFilter** y `m_strSort` no están vacíos, agrega el **donde** o **ORDER BY** cláusulas.|  
|4 *|Una completa **seleccione** instrucción con un **donde** o **ORDER BY** cláusula|Tal y como se pasa. **m_strFilter** o `m_strSort` deben permanecer vacíos o un filtro de dos o se producen instrucciones de ordenación.|  
|5 *|Una llamada a un procedimiento almacenado|Tal y como se pasa.|  
  
 \*`m_nFields` debe ser menor o igual que el número de columnas especificadas en el **seleccione** instrucción. El tipo de datos de cada columna especificada en el **seleccione** instrucción debe ser el mismo que el tipo de datos de la columna de salida RFX correspondiente.  
  
### <a name="case-1---lpszsql--null"></a>Caso 1 lpszSQL = NULL  
 La selección de conjunto de registros depende de lo que `GetDefaultSQL` devuelve cuando `CRecordset::Open` lo llama. Las cadenas posibles describen los casos 2 a 5.  
  
### <a name="case-2---lpszsql--a-table-name"></a>Caso 2 lpszSQL = un nombre de tabla  
 El conjunto de registros utiliza el intercambio de campos de registros (RFX) para generar la lista de columnas de los nombres de columna proporcionados en el RFX función llama a en la invalidación de la clase de conjunto de registros de `DoFieldExchange`. Si utiliza a un Asistente para declarar la clase de conjunto de registros, este caso tiene el mismo resultado que el caso 1 (siempre que se pase el mismo nombre de tabla especificado en el asistente). Si no usa a un Asistente para escribir la clase, caso 2 es la manera más sencilla de crear la instrucción SQL.  
  
 En el ejemplo siguiente se crea una instrucción SQL que selecciona los registros de una aplicación de base de datos MFC. Cuando el marco llama a la `GetDefaultSQL` función miembro, la función devuelve el nombre de la tabla, `SECTION`.  
  
```  
CString CEnrollSet::GetDefaultSQL()  
{  
    return "SECTION";  
}  
```  
  
 Para obtener los nombres de las columnas de la instrucción SQL **seleccione** instrucción, las llamadas de framework la `DoFieldExchange` función miembro.  
  
```  
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
  
 Cuando haya finalizado, la instrucción SQL tiene este aspecto:  
  
```  
SELECT CourseID, InstructorID, RoomNo, Schedule, SectionNo   
    FROM SECTION  
```  
  
### <a name="case-3---lpszsql--a-selectfrom-statement"></a>Caso 3 lpszSQL = una instrucción SELECT de la instrucción  
 Especifique manualmente la lista de columnas en lugar de confiar en que RFX para construir de forma automática. Puede hacerlo cuando:  
  
-   Desea especificar el **DISTINCT** siguiente de la palabra clave **seleccione**.  
  
     La lista de columnas debe coincidir con los nombres de columna y los tipos en el mismo orden que aparecen en `DoFieldExchange`.  
  
-   Tiene razón para recuperar manualmente los valores de columna mediante la función ODBC **:: SQLGetData** en lugar de confiar en que RFX enlace y recupere las columnas por usted.  
  
     Por ejemplo, podría adaptarse a nuevas columnas de que un cliente de la aplicación se agrega a las tablas de base de datos después de que se distribuya la aplicación. Debe agregar a estos miembros de datos de campo adicional, lo que no se conocían en el momento de que declarar la clase con un asistente.  
  
     La lista de columnas debe coincidir con los nombres de columna y los tipos en el mismo orden que aparecen en `DoFieldExchange`, seguido de los nombres de las columnas enlazadas manualmente. Para obtener más información, consulte [conjunto de registros: enlazar dinámicamente columnas de datos (ODBC)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).  
  
-   Desea combinar las tablas especificando varias tablas en el **FROM** cláusula.  
  
     Para obtener información y un ejemplo, vea [conjunto de registros: realizar una combinación (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md).  
  
### <a name="case-4---lpszsql--selectfrom-plus-where-andor-order-by"></a>Caso 4 lpszSQL = SELECT / FROM más WHERE u ORDER BY  
 Especifica todo: la lista de columnas (basada en las llamadas RFX en `DoFieldExchange`), la lista de tabla y el contenido de un **donde** o un **ORDER BY** cláusula. Si especifica la **donde** o **ORDER BY** cláusulas de este modo, no use **m_strFilter** o `m_strSort`.  
  
### <a name="case-5---lpszsql--a-stored-procedure-call"></a>Caso 5 lpszSQL = una llamada de procedimiento almacenado  
 Si necesita llamar a una consulta predefinida (por ejemplo, un procedimiento almacenado en una base de datos de Microsoft SQL Server), debe escribir una **llamar a** instrucción en la cadena se pasa a `lpszSQL`. Los asistentes no admiten declarar una clase de conjunto de registros para llamar a una consulta predefinida. No todas las consultas predefinidas devuelven registros.  
  
 Si una consulta predefinida no devuelve registros, puede usar el `CDatabase` función miembro `ExecuteSQL` directamente. Para una consulta predefinida que devuelve registros, debe escribir manualmente las llamadas RFX en `DoFieldExchange` de todas las columnas que devuelve el procedimiento. Las llamadas RFX deben estar en el mismo orden y devolver los mismos tipos, como la consulta predefinida. Para obtener más información, consulte [conjunto de registros: declarar una clase para una consulta predefinida (ODBC)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md).  
  
## <a name="see-also"></a>Vea también  
 [SQL: SQL y tipos de datos de C++ (ODBC)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)   
 [SQL: Realizar llamadas directas a SQL (ODBC)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)
