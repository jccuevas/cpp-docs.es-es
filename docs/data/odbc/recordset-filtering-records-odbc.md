---
title: 'Conjunto de registros: Filtrar registros (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- data [MFC], filtering
- recordsets [C++], filtering
- filtering recordsets
- ODBC recordsets [C++], filtering records
- filters [C++], recordset object
ms.assetid: 5c075f37-c837-464d-90c1-d028a9d1c175
ms.openlocfilehash: 56b8c4f52ec294f58a760e1309d32aa81286ddec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367013"
---
# <a name="recordset-filtering-records-odbc"></a>Conjunto de registros: Filtrar registros (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

En este tema se explica cómo filtrar un conjunto de registros para que seleccione solo un subconjunto determinado de los registros disponibles. Por ejemplo, es posible que desee seleccionar solo las secciones de clase para un curso determinado, como MATH101. Un filtro es una condición de búsqueda definida por el contenido de una cláusula **WHERE** de SQL. Cuando el marco de trabajo lo anexa a la instrucción SQL del conjunto de registros, la cláusula **WHERE** restringe la selección.

Debe establecer el filtro de un objeto de conjunto de `Open` registros después de `Requery` construir el objeto, `Open` pero antes de llamar a su función miembro (o antes de llamar a la función miembro para un objeto de conjunto de registros existente cuya función miembro se ha llamado anteriormente).

#### <a name="to-specify-a-filter-for-a-recordset-object"></a>Para especificar un filtro para un objeto de conjunto de registros

1. Construir un nuevo objeto de `Requery` conjunto de registros (o prepararse para llamar a un objeto existente).

1. Establezca el valor del miembro de datos [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) del objeto.

   El filtro es una cadena terminada en null que contiene el contenido de la cláusula **WHERE** de SQL, pero no la palabra clave **WHERE**. Por ejemplo, use:

    ```
    m_pSet->m_strFilter = "CourseID = 'MATH101'";
    ```

   not

    ```
    m_pSet->m_strFilter = "WHERE CourseID = 'MATH101'";
    ```

    > [!NOTE]
    >  La cadena literal "MATH101" se muestra con comillas simples arriba. En la especificación SQL ODBC, las comillas simples se utilizan para denotar un literal de cadena de caracteres. Compruebe la documentación del controlador ODBC para conocer los requisitos de cotización de su DBMS en esta situación. Esta sintaxis también se describe más cerca del final de este tema.

1. Establezca cualquier otra opción que necesite, como el criterio de ordenación, el modo de bloqueo o los parámetros. Especificar un parámetro es especialmente útil. Para obtener información sobre cómo parametrizar el filtro, vea [Conjunto de registros: parametrizar un conjunto de registros (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

1. Llame `Open` al nuevo objeto `Requery` (o a un objeto abierto previamente).

> [!TIP]
> El uso de parámetros en el filtro es potencialmente el método más eficaz para recuperar registros.

> [!TIP]
> Los filtros de conjunto de registros son útiles para [unir](../../data/odbc/recordset-performing-a-join-odbc.md) tablas y para usar [parámetros basados](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) en la información obtenida o calculada en tiempo de ejecución.

El conjunto de registros selecciona solo los registros que cumplen la condición de búsqueda especificada. Por ejemplo, para especificar el filtro de `strCourseID` curso descrito anteriormente (suponiendo que una variable establecida actualmente, por ejemplo, en "MATH101"), haga lo siguiente:

```
// Using the recordset pointed to by m_pSet

// Set the filter
m_pSet->m_strFilter = "CourseID = " + strCourseID;

// Run the query with the filter in place
if ( m_pSet->Open( CRecordset::snapshot, NULL, CRecordset::readOnly ) )

// Use the recordset
```

El conjunto de registros contiene registros para todas las secciones de clase para MATH101.

Observe cómo se estableció la cadena de filtro en el ejemplo anterior, utilizando una variable de cadena. Este es el uso típico. Pero supongamos que desea especificar el valor literal 100 para el identificador del curso. El código siguiente muestra cómo establecer la cadena de filtro correctamente con un valor literal:

```
m_strFilter = "StudentID = '100'";   // correct
```

Tenga en cuenta el uso de caracteres de comillas simples; si establece la cadena de filtro directamente, la cadena de filtro **no**es:

```
m_strFilter = "StudentID = 100";   // incorrect for some drivers
```

La cita mostrada anteriormente se ajusta a la especificación ODBC, pero algunos DBMS pueden requerir otros caracteres de comillas. Para obtener más información, vea SQL: personalizar la [instrucción SQL (ODBC) del](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)conjunto de registros .

> [!NOTE]
> Si decide invalidar la cadena SQL predeterminada del conjunto de `Open`registros pasando su propia cadena SQL a , no debe establecer un filtro si la cadena personalizada tiene una cláusula **WHERE.** Para obtener más información acerca de cómo reemplazar el SQL predeterminado, vea SQL: personalizar la [instrucción SQL (ODBC) del](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md)conjunto de registros .

## <a name="see-also"></a>Consulte también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Conjunto de registros: Ordenar registros (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)<br/>
[Conjunto de registros: Cómo se seleccionan los registros (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)<br/>
[Conjunto de registros: Actualizar los registros (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)<br/>
[Conjunto de registros: Bloquear registros (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)
