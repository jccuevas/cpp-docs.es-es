---
title: "SQL: Personalizar la instrucci&#243;n SQL del conjunto de registros (ODBC) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "personalizar instrucciones SQL"
  - "conjuntos de registros ODBC, instrucciones SQL"
  - "reemplazar, instrucciones SQL"
  - "conjuntos de registros, instrucciones SQL"
  - "instrucciones SQL, personalizar"
  - "instrucciones SQL, conjunto de registros"
  - "SQL, abrir conjuntos de registros"
ms.assetid: 72293a08-cef2-4be2-aa1c-30565fcfbaf9
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SQL: Personalizar la instrucci&#243;n SQL del conjunto de registros (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En este tema se explica:  
  
-   Cómo crea el marco de trabajo una instrucción SQL.  
  
-   Cómo reemplazar la instrucción SQL.  
  
> [!NOTE]
>  Esta información es aplicable a las clases ODBC de MFC.  Si trabaja con las clases DAO de MFC, vea el tema "Comparación entre SQL del motor de bases de datos Microsoft Jet y SQL ANSI" en la Ayuda de DAO.  
  
## Creación de instrucciones SQL  
 El conjunto de registros basa la selección de registros principalmente en una instrucción SQL **SELECT**.  Al declarar la clase mediante un asistente, escribe una versión de reemplazo de la función miembro `GetDefaultSQL` que tiene un aspecto similar al siguiente \(para una clase de conjunto de registros denominada `CAuthors`\).  
  
```  
CString CAuthors::GetDefaultSQL()  
{  
    return "AUTHORS";  
}  
```  
  
 De forma predeterminada, este reemplazo devuelve el nombre de tabla especificado en el asistente.  En el ejemplo, el nombre de tabla es "AUTHORS". Al llamar más tarde a la función miembro **Open** del conjunto de registros, **Open** crea una instrucción **SELECT** final para el formulario:  
  
```  
SELECT rfx-field-list FROM table-name [WHERE m_strFilter]   
       [ORDER BY m_strSort]  
```  
  
 donde se obtiene `table-name` llamando a `GetDefaultSQL` y se obtiene `rfx-field-list` a partir de las llamadas de función RFX de `DoFieldExchange`.  Esto es lo que se obtiene con una instrucción **SELECT** a menos que se reemplace con una versión de reemplazo en tiempo de ejecución, aunque también se puede modificar la instrucción predeterminada mediante parámetros o un filtro.  
  
> [!NOTE]
>  Si especifica un nombre de columna que contiene \(o debe contener\) espacios, debe incluir el nombre entre corchetes.  Por ejemplo, el nombre "Primer apellido" debe ser "\[Primer apellido\]".  
  
 Para reemplazar la instrucción **SELECT** predeterminada, pase una cadena que contenga una instrucción **SELECT** completa al llamar a **Open**.  En lugar de crear su propia cadena predeterminada, el conjunto de registros utiliza la cadena proporcionada por el programador.  Si la instrucción de reemplazo contiene una cláusula **WHERE,** no especifique un filtro en **m\_strFilter**, ya que entonces tendría dos instrucciones de filtro.  De igual forma, si la cadena de reemplazo contiene una cláusula **ORDER BY**, no especifique ninguna ordenación en `m_strSort`, ya que tendría dos instrucciones de ordenación.  
  
> [!NOTE]
>  Si utiliza cadenas de literales en los filtros \(o en otras partes de la instrucción SQL\), debe "citarlas" \(incluirlas entre los delimitadores especificados\) incluyéndolas entre los caracteres de prefijo y sufijo de literal específicos del DBMS.  
  
 También puede que se encuentre con requisitos de sintaxis especiales para operaciones como las uniones externas, en función del DBMS.  Utilice las funciones ODBC para obtener esta información del controlador correspondiente al DMBS.  Por ejemplo, llame a **::SQLGetTypeInfo** con un tipo de datos determinado, como **SQL\_VARCHAR**, para solicitar los caracteres **LITERAL\_PREFIX** y **LITERAL\_SUFFIX**.  Si está escribiendo código independiente de la base de datos, vea el Apéndice C en la *Referencia del programador*, del *SDK de ODBC*, en el CD de MSDN Library para obtener información de sintaxis detallada.  
  
 Un objeto de conjunto de registros genera la instrucción SQL que utilizará para seleccionar registros a menos que le pase una instrucción SQL personalizada.  La forma de hacerlo depende sobre todo del valor pasado en el parámetro `lpszSQL` de la función miembro **Open**.  
  
 La forma general de una instrucción SQL **SELECT** es:  
  
```  
SELECT [ALL | DISTINCT] column-list FROM table-list  
    [WHERE search-condition][ORDER BY column-list [ASC | DESC]]  
```  
  
 Una forma de agregar la palabra clave **DISTINCT** a la instrucción SQL del conjunto de registros es incrustarla en la primera llamada de función RFX de `DoFieldExchange`.  Por ejemplo:  
  
```  
...  
    RFX_Text(pFX, "DISTINCT CourseID", m_strCourseID);  
...  
```  
  
> [!NOTE]
>  Use esta técnica sólo en un conjunto de registros abierto en modo de sólo lectura.  
  
## Reemplazar la instrucción SQL  
 La siguiente tabla muestra las posibilidades del parámetro `lpszSQL` cuando se pasa a **Open**.  Los casos de la tabla se explican a continuación de ésta.  
  
 **El parámetro lpszSQL y la cadena SQL resultante**  
  
|Case|Lo que se pasa en lpszSQL|Instrucción SELECT resultante|  
|----------|-------------------------------|-----------------------------------|  
|1|**NULL**|**SELECT** *rfx\-field\-list* **FROM** *table\-name*<br /><br /> `CRecordset::Open` llama a `GetDefaultSQL` para obtener el nombre de tabla.  La cadena resultante es uno de los casos 2 a 5, dependiendo de lo devuelto por `GetDefaultSQL`.|  
|2|Un nombre de tabla|**SELECT** *rfx\-field\-list* **FROM** *table\-name*<br /><br /> La lista de campos se toma de las instrucciones RFX de `DoFieldExchange`.  Si **m\_strFilter** y `m_strSort` no están vacíos, agrega las cláusulas **WHERE** y\/u **ORDER BY**.|  
|3 \*|Una instrucción **SELECT** completa, pero sin cláusula **WHERE** u **ORDER BY**|Tal como se pasa.  Si **m\_strFilter** y `m_strSort` no están vacíos, agrega las cláusulas **WHERE** y\/u **ORDER BY**.|  
|4 \*|Una instrucción **SELECT** completa con cláusula **WHERE** y\/u **ORDER BY**|Tal como se pasa.  **m\_strFilter** y `m_strSort` deben permanecer vacíos o se crean dos instrucciones de filtro u ordenación.|  
|5 \*|Una llamada a un procedimiento almacenado.|Tal como se pasa.|  
  
 \* `m_nFields` debe ser inferior o igual al número de columnas especificadas en la instrucción **SELECT**.  El tipo de datos de cada una de las columnas especificadas en **SELECT** debe ser el mismo que el de la columna de resultados RFX correspondiente.  
  
### Caso 1   lpszSQL \= NULL  
 La selección de conjunto de registros depende de lo que devuelve `GetDefaultSQL` al ser llamada por `CRecordset::Open`.  Los casos 2 a 5 describen las posibles cadenas.  
  
### Caso 2   lpszSQL \= un nombre de tabla  
 El conjunto de registros usa el intercambio de campos de registros \(RFX\) para compilar la lista de columnas a partir de los nombres de columna proporcionados en las llamadas de función RFX del reemplazo de `DoFieldExchange`, en la clase de conjunto de registros.  Si se utilizó un asistente para declarar la clase de conjunto de registros, este caso tiene el mismo resultado que el caso 1 \(siempre que se pase el mismo nombre de tabla especificado en el asistente\).  Si no se utiliza ningún asistente para escribir la clase, el caso 2 es la forma más sencilla de crear la instrucción SQL.  
  
 El ejemplo siguiente crea una instrucción SQL que selecciona registros de una aplicación de base de datos MFC.  Cuando el marco de trabajo llama a la función miembro `GetDefaultSQL`, la función devuelve el nombre de la tabla, `SECTION`.  
  
```  
CString CEnrollSet::GetDefaultSQL()  
{  
    return "SECTION";  
}  
```  
  
 Para obtener los nombres de las columnas de la instrucción SQL **SELECT**, el marco de trabajo llama a la función miembro `DoFieldExchange`.  
  
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
  
 Al finalizar, la instrucción tiene el siguiente aspecto:  
  
```  
SELECT CourseID, InstructorID, RoomNo, Schedule, SectionNo   
    FROM SECTION  
```  
  
### Caso 3   lpszSQL \= una instrucción SELECT\/FROM  
 Se especifica manualmente la lista de columnas en lugar de hacer que RFX la genere automáticamente.  Puede resultar conveniente hacerlo cuando:  
  
-   Se desea especificar la palabra clave **DISTINCT** que sigue a **SELECT**.  
  
     La lista de columnas debe coincidir con los nombres y tipos de columna en el mismo orden en que aparecen en `DoFieldExchange`.  
  
-   Hay razones para recuperar manualmente los valores de columna mediante la función de ODBC **::SQLGetData** en lugar de confiar en que RFX enlace y recupere las columnas.  
  
     Puede resultar conveniente, por ejemplo, acomodar las nuevas columnas que agregó un cliente de la aplicación a las tablas de la base de datos después de distribuirse la aplicación.  Es necesario agregar estos miembros de datos de campo adicionales, que no se conocían en el momento de declarar la clase con el asistente.  
  
     La lista de columnas debe coincidir con los nombres y tipos de columna en el mismo orden en que aparecen en `DoFieldExchange`, seguidos de las columnas enlazadas manualmente.  Para obtener más información, vea [Conjunto de registros: Enlazar dinámicamente columnas de datos \(ODBC\)](../../data/odbc/recordset-dynamically-binding-data-columns-odbc.md).  
  
-   Es conveniente combinar las tablas especificando varias tablas en la cláusula **FROM**.  
  
     Para obtener información y un ejemplo, vea [Conjunto de registros: Realizar una combinación \(ODBC\)](../../data/odbc/recordset-performing-a-join-odbc.md).  
  
### Caso 4   lpszSQL \= SELECT\/FROM más WHERE u ORDER BY  
 Se especifica todo: la lista de columnas \(basada en las llamadas RFX de `DoFieldExchange`\), la lista de tablas y el contenido de una cláusula **WHERE** y\/u **ORDER BY**.  Si se especifican las cláusulas **WHERE** y\/u **ORDER BY** de esta forma, no se debe utilizar **m\_strFilter** ni `m_strSort`.  
  
### Caso 5   lpszSQL \= una llamada a un procedimiento almacenado  
 Si necesita llamar a una consulta predefinida \(como por ejemplo, un procedimiento almacenado en una base de datos de Microsoft SQL Server\), debe escribir una instrucción **CALL** en la cadena que pase a `lpszSQL`.  Los asistentes no admiten la declaración de una conjunto de registros para llamar a una consulta predefinida.  No todas las consultas predefinidas devuelven registros.  
  
 Si una consulta predefinida no devuelve ningún registro, se puede utilizar directamente `ExecuteSQL` de la función miembro `CDatabase`.  Para una consulta predefinida que sí devuelve registros, se deben escribir manualmente las llamadas RFX en `DoFieldExchange` para cualquier columna que devuelva el procedimiento.  Las llamadas RFX deben hallarse en el mismo orden y devolver los mismos tipos que la consulta predefinida.  Para obtener más información, vea [Conjunto de registros: Declarar una clase para una consulta predefinida \(ODBC\)](../../data/odbc/recordset-declaring-a-class-for-a-predefined-query-odbc.md).  
  
## Vea también  
 [SQL: tipos de datos de SQL y C\+\+ \(ODBC\)](../../data/odbc/sql-sql-and-cpp-data-types-odbc.md)   
 [SQL: Realizar llamadas directas a SQL \(ODBC\)](../../data/odbc/sql-making-direct-sql-calls-odbc.md)