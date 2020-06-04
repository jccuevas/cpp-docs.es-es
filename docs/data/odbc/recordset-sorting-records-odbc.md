---
title: 'Conjunto de registros: Ordenar registros (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- sorting data, recordset data
- ODBC recordsets, sorting
- recordsets, sorting
ms.assetid: b40b152e-0a91-452e-be7b-e5bc27f744c7
ms.openlocfilehash: 8b4deea1d8cbd4abe01ccc7a4114131378abe463
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366922"
---
# <a name="recordset-sorting-records-odbc"></a>Conjunto de registros: Ordenar registros (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

En este tema se explica cómo ordenar el conjunto de registros. Puede especificar una o varias columnas en las que basar la ordenación y puede especificar el orden ascendente o descendente **(ASC** o **DESC;** **ASC** es el valor predeterminado) para cada columna especificada. Por ejemplo, si especifica dos columnas, los registros se ordenan primero en la primera columna con nombre y, a continuación, en la segunda columna con el nombre. Una cláusula **ORDER BY** de SQL define una ordenación. Cuando el marco de trabajo anexa la cláusula **ORDER BY** a la consulta SQL del conjunto de registros, la cláusula controla el orden de la selección.

Debe establecer el criterio de ordenación de un conjunto `Open` de registros después `Requery` de construir el objeto, `Open` pero antes de llamar a su función miembro (o antes de llamar a la función miembro para un objeto de conjunto de registros existente cuya función miembro se ha llamado anteriormente).

#### <a name="to-specify-a-sort-order-for-a-recordset-object"></a>Para especificar un criterio de ordenación para un objeto de conjunto de registros

1. Construir un nuevo objeto de `Requery` conjunto de registros (o prepararse para llamar a uno existente).

1. Establezca el valor del miembro de datos [m_strSort](../../mfc/reference/crecordset-class.md#m_strsort) del objeto.

   La ordenación es una cadena terminada en null. Contiene el contenido de la cláusula **ORDER BY,** pero no la palabra clave **ORDER BY**. Por ejemplo, use:

    ```
    recordset.m_strSort = "LastName DESC, FirstName DESC";
    ```

   not

    ```
    recordset.m_strSort = "ORDER BY LastName DESC, FirstName DESC";
    ```

1. Establezca cualquier otra opción que necesite, como un filtro, un modo de bloqueo o parámetros.

1. Llame `Open` al nuevo objeto `Requery` (o a un objeto existente).

Los registros seleccionados se ordenan según lo especificado. Por ejemplo, para ordenar un conjunto de registros de alumnos en orden descendente por apellido y, a continuación, nombre, haga lo siguiente:

```cpp
// Construct the recordset
CStudentSet rsStudent( NULL );
// Set the sort
rsStudent.m_strSort = "LastName DESC, FirstName DESC";
// Run the query with the sort in place
rsStudent.Open( );
```

El conjunto de registros contiene todos los registros de alumnos, ordenados en orden descendente (de Z a A) por apellido y, a continuación, por nombre.

> [!NOTE]
> Si decide invalidar la cadena SQL predeterminada del conjunto de `Open`registros pasando su propia cadena SQL a , no establezca una ordenación si la cadena personalizada tiene una cláusula **ORDER BY.**

## <a name="see-also"></a>Consulte también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Conjunto de registros: Parametrizar un conjunto de registros (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)<br/>
[Conjunto de registros: Filtrar registros (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)
