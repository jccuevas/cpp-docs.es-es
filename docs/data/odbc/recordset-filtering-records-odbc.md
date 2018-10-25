---
title: 'Conjunto de registros: Filtrar registros (ODBC) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- data [MFC], filtering
- recordsets [C++], filtering
- filtering recordsets
- ODBC recordsets [C++], filtering records
- filters [C++], recordset object
ms.assetid: 5c075f37-c837-464d-90c1-d028a9d1c175
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6cdd5882c259c2f1746d1c6f41572631da4a2788
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50079953"
---
# <a name="recordset-filtering-records-odbc"></a>Conjunto de registros: Filtrar registros (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

En este tema se explica cómo filtrar un conjunto de registros para que seleccione solo un subconjunto específico de los registros disponibles. Por ejemplo, es posible que desee seleccionar sólo las secciones de la clase para un curso determinado, como MATH101. Un filtro es una condición de búsqueda definida por el contenido de una instancia de SQL **donde** cláusula. Cuando el marco de trabajo anexa a la instrucción de SQL del conjunto de registros, la **donde** cláusula restringe la selección.

Debe establecer el filtro del objeto de un conjunto de registros después de crear el objeto, pero antes de llamar a su `Open` función miembro (o antes de llamar a la `Requery` de objeto cuya función miembro de un conjunto de registros existente `Open` tiene la función miembro se ha llamado anteriormente).

#### <a name="to-specify-a-filter-for-a-recordset-object"></a>Para especificar un filtro para un objeto de conjunto de registros

1. Cree un nuevo objeto de conjunto de registros (o prepare la llamada a `Requery` para un objeto existente).

1. Establezca el valor del objeto [m_strFilter](../../mfc/reference/crecordset-class.md#m_strfilter) miembro de datos.

   El filtro es una cadena terminada en null que contiene el contenido de la instrucción SQL **donde** cláusula pero no la palabra clave **donde**. Por ejemplo, use:

    ```
    m_pSet->m_strFilter = "CourseID = 'MATH101'";
    ```

   not

    ```
    m_pSet->m_strFilter = "WHERE CourseID = 'MATH101'";
    ```

    > [!NOTE]
    >  La cadena literal "MATH101" se muestra con comillas simples. En la especificación de ODBC SQL, se usan comillas simples para denotar un literal de cadena de caracteres. Compruebe la documentación del controlador ODBC para los requisitos de entrecomillado de DBMS en esta situación. Esta sintaxis también se explica más adelante, hacia el final de este tema.

1. Establecer otras opciones que necesite, como el criterio de ordenación, el modo de bloqueo o parámetros. Es especialmente útil si se especifica un parámetro. Para obtener información acerca de cómo parametrizar un filtro, vea [conjunto de registros: parametrizar un conjunto de registros (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md).

1. Llame a `Open` para el nuevo objeto (o `Requery` para un objeto abierto anteriormente).

> [!TIP]
>  Usar parámetros en el filtro es potencialmente el método más eficaz para recuperar los registros.

> [!TIP]
>  Filtros de conjunto de registros son útiles para [unir](../../data/odbc/recordset-performing-a-join-odbc.md) tablas y para usar [parámetros](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md) según la información obtenida o calculada en tiempo de ejecución.

El conjunto de registros selecciona solo aquellos registros que cumplen la condición de búsqueda especificada. Por ejemplo especificar el filtro de curso se ha descrito anteriormente (suponiendo que una variable `strCourseID` establecido actualmente, por ejemplo, en "MATH101"), haga lo siguiente:

```
// Using the recordset pointed to by m_pSet

// Set the filter
m_pSet->m_strFilter = "CourseID = " + strCourseID;

// Run the query with the filter in place
if ( m_pSet->Open( CRecordset::snapshot, NULL, CRecordset::readOnly ) )

// Use the recordset
```

El conjunto de registros contiene registros para todas las secciones de la clase de MATH101.

Tenga en cuenta cómo se haya establecido la cadena de filtro en el ejemplo anterior, mediante una variable de cadena. Este es el uso típico. Pero suponga que desea especificar el valor literal 100 para el identificador del curso. El código siguiente muestra cómo establecer la cadena de filtro correctamente con un valor literal:

```
m_strFilter = "StudentID = '100'";   // correct
```

Tenga en cuenta el uso de caracteres de comillas simples. Si se establece la cadena de filtro directamente, la cadena de filtro es **no**:

```
m_strFilter = "StudentID = 100";   // incorrect for some drivers
```

El uso de comillas anterior se ajusta a la especificación ODBC, pero algunos de los DBMS pueden requerir otros caracteres de comillas. Para obtener más información, consulte [SQL: SQL instrucción (ODBC de personalizar un conjunto de registros)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

> [!NOTE]
>  Si opta por reemplazar la cadena SQL predeterminada del conjunto de registros pasando su propia cadena SQL a `Open`, no debe establecer un filtro si la cadena personalizada contiene una **donde** cláusula. Para obtener más información sobre cómo invalidar el valor predeterminado SQL, consulte [SQL: SQL instrucción (ODBC de personalizar un conjunto de registros)](../../data/odbc/sql-customizing-your-recordsets-sql-statement-odbc.md).

## <a name="see-also"></a>Vea también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Conjunto de registros: Ordenar registros (ODBC)](../../data/odbc/recordset-sorting-records-odbc.md)<br/>
[Conjunto de registros: Cómo se seleccionan los registros (ODBC)](../../data/odbc/recordset-how-recordsets-select-records-odbc.md)<br/>
[Conjunto de registros: Actualizar los registros (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)<br/>
[Conjunto de registros: Bloquear registros (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)