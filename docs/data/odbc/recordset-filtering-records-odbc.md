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
ms.openlocfilehash: 2e742ee02e142fd87df3f149379d9971c4acd166
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212918"
---
# <a name="recordset-filtering-records-odbc"></a>Conjunto de registros: Filtrar registros (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

En este tema se explica cómo filtrar un conjunto de registros para que seleccione solo un subconjunto determinado de los registros disponibles. Por ejemplo, puede que desee seleccionar solo las secciones de la clase para un curso determinado, como MATH101. Un filtro es una condición de búsqueda definida por el contenido de una cláusula **Where** de SQL. Cuando el marco de trabajo lo anexa a la instrucción SQL del conjunto de registros, la cláusula **Where** restringe la selección.

Debe establecer el filtro de un objeto de conjunto de registros después de construir el objeto, pero antes de llamar a su función miembro `Open` (o antes de llamar a la función miembro `Requery` para un objeto de conjunto de registros existente cuya función miembro `Open` se haya llamado previamente).

#### <a name="to-specify-a-filter-for-a-recordset-object"></a>Para especificar un filtro para un objeto de conjunto de registros

1. Construya un nuevo objeto de conjunto de registros (o Prepárese para llamar `Requery` para un objeto existente).

1. Establezca el valor del miembro de datos [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) del objeto.

   El filtro es una cadena terminada en null que incluye el contenido de la cláusula **Where** de SQL, pero no la palabra clave **Where**. Por ejemplo, use:

    ```
    m_pSet->m_strFilter = "CourseID = 'MATH101'";
    ```

   not

    ```
    m_pSet->m_strFilter = "WHERE CourseID = 'MATH101'";
    ```

    > [!NOTE]
    >  La cadena literal "MATH101" se muestra con las comillas simples anteriores. En la especificación SQL de ODBC, se usan comillas simples para denotar un literal de cadena de caracteres. Consulte la documentación del controlador ODBC para conocer los requisitos de Comillas de su DBMS en esta situación. Esta sintaxis también se describe con más detalle cerca del final de este tema.

1. Establezca las demás opciones que necesite, como el criterio de ordenación, el modo de bloqueo o los parámetros. Especificar un parámetro es especialmente útil. Para obtener información sobre cómo parametrizar el filtro, vea [conjunto de registros: parametrizar un conjunto de registros (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

1. Llame a `Open` para el nuevo objeto (o `Requery` para un objeto abierto previamente).

> [!TIP]
>  El uso de parámetros en el filtro es potencialmente el método más eficaz para recuperar registros.

> [!TIP]
>  Los filtros de conjunto de registros son útiles para [combinar](../../data/odbc/recordset-performing-a-join-odbc.md) tablas y usar [parámetros](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) basados en la información obtenida o calculada en tiempo de ejecución.

El conjunto de registros selecciona solo los registros que cumplen la condición de búsqueda especificada. Por ejemplo, para especificar el filtro del curso descrito anteriormente (suponiendo que una variable `strCourseID` establecida actualmente, por ejemplo, a "MATH101"), haga lo siguiente:

```
// Using the recordset pointed to by m_pSet

// Set the filter
m_pSet->m_strFilter = "CourseID = " + strCourseID;

// Run the query with the filter in place
if ( m_pSet->Open( CRecordset::snapshot, NULL, CRecordset::readOnly ) )

// Use the recordset
```

El conjunto de registros contiene los registros de todas las secciones de clase para MATH101.

Observe cómo se estableció la cadena de filtro en el ejemplo anterior, con una variable de cadena. Este es el uso típico. Pero supongamos que desea especificar el valor literal 100 para el ID. de curso. El código siguiente muestra cómo establecer correctamente la cadena de filtro con un valor literal:

```
m_strFilter = "StudentID = '100'";   // correct
```

Tenga en cuenta el uso de caracteres de comillas simples; Si establece la cadena de filtro directamente, la cadena de filtro **no**es:

```
m_strFilter = "StudentID = 100";   // incorrect for some drivers
```

La cotización mostrada anteriormente se ajusta a la especificación de ODBC, pero algunos DBMS pueden requerir otros caracteres de Comillas. Para obtener más información, vea [SQL: personalizar la instrucción SQL del conjunto de registros (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

> [!NOTE]
>  Si opta por invalidar la cadena SQL predeterminada del conjunto de registros pasando su propia cadena SQL a `Open`, no debe establecer un filtro si la cadena personalizada tiene una cláusula **Where** . Para obtener más información sobre cómo invalidar el SQL predeterminado, vea [SQL: personalizar la instrucción SQL del conjunto de registros (ODBC)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

## <a name="see-also"></a>Consulte también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Conjunto de registros: Ordenar registros (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)<br/>
[Conjunto de registros: Cómo se seleccionan los registros (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)<br/>
[Conjunto de registros: Actualizar los registros (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)<br/>
[Conjunto de registros: Bloquear registros (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)
