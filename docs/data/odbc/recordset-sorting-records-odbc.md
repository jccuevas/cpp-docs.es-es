---
title: 'Conjunto de registros: Ordenar registros (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- sorting data, recordset data
- ODBC recordsets, sorting
- recordsets, sorting
ms.assetid: b40b152e-0a91-452e-be7b-e5bc27f744c7
ms.openlocfilehash: 4bbe635cdda9152be6ba178b863147db93b7c706
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212750"
---
# <a name="recordset-sorting-records-odbc"></a>Conjunto de registros: Ordenar registros (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

En este tema se explica cómo ordenar el conjunto de registros. Puede especificar una o más columnas en las que basar la ordenación, y puede especificar orden ascendente o descendente (**ASC** o **DESC**; **ASC** es el valor predeterminado) para cada columna especificada. Por ejemplo, si se especifican dos columnas, los registros se ordenan primero en la primera columna denominada y, a continuación, en la segunda columna denominada. Una cláusula **order by** de SQL define una ordenación. Cuando el marco de trabajo anexa la cláusula **order by** a la consulta SQL del conjunto de registros, la cláusula controla la ordenación de la selección.

Debe establecer el criterio de ordenación de un conjunto de registros después de construir el objeto, pero antes de llamar a su función miembro `Open` (o antes de llamar a la función miembro `Requery` para un objeto de conjunto de registros existente cuya función miembro `Open` se haya llamado previamente).

#### <a name="to-specify-a-sort-order-for-a-recordset-object"></a>Para especificar un criterio de ordenación para un objeto de conjunto de registros

1. Construya un nuevo objeto de conjunto de registros (o Prepárese para llamar `Requery` para un existente).

1. Establezca el valor del miembro de datos [m_strSort](../../mfc/reference/crecordset-class.md#m_strsort) del objeto.

   La ordenación es una cadena terminada en NULL. Incluye el contenido de la cláusula **order by** , pero no la palabra clave **order by**. Por ejemplo, use:

    ```
    recordset.m_strSort = "LastName DESC, FirstName DESC";
    ```

   not

    ```
    recordset.m_strSort = "ORDER BY LastName DESC, FirstName DESC";
    ```

1. Establezca las demás opciones que necesite, como un filtro, el modo de bloqueo o los parámetros.

1. Llame a `Open` para el nuevo objeto (o `Requery` para un objeto existente).

Los registros seleccionados se ordenan según lo especificado. Por ejemplo, para ordenar un conjunto de registros de estudiante en orden descendente por apellidos, haga lo siguiente:

```cpp
// Construct the recordset
CStudentSet rsStudent( NULL );
// Set the sort
rsStudent.m_strSort = "LastName DESC, FirstName DESC";
// Run the query with the sort in place
rsStudent.Open( );
```

El conjunto de registros contiene todos los registros de estudiante, ordenados en orden descendente (de Z a A) por Apellido y luego por nombre.

> [!NOTE]
>  Si opta por invalidar la cadena SQL predeterminada del conjunto de registros pasando su propia cadena SQL a `Open`, no establezca una ordenación si la cadena personalizada tiene una cláusula **order by** .

## <a name="see-also"></a>Consulte también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Conjunto de registros: Parametrizar un conjunto de registros (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)<br/>
[Conjunto de registros: Filtrar registros (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)
