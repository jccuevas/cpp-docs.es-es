---
title: 'Conjunto de registros: Ordenar registros (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- sorting data, recordset data
- ODBC recordsets, sorting
- recordsets, sorting
ms.assetid: b40b152e-0a91-452e-be7b-e5bc27f744c7
ms.openlocfilehash: 831f21901186ed0ae010b0f332327eefcba94b51
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59024665"
---
# <a name="recordset-sorting-records-odbc"></a>Conjunto de registros: Ordenar registros (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

En este tema se explica cómo se ordena el conjunto de registros. Puede especificar una o varias columnas en el que se va a basar la ordenación, y puede especificar orden ascendente o descendente (**ASC** o **DESC**; **ASC** es el valor predeterminado) para cada columna especificada. Por ejemplo, si se especifican dos columnas, los registros se ordenan en primer lugar en la primera columna con nombre y, a continuación, en la segunda columna denominada. Una instancia de SQL **ORDER BY** cláusula define un criterio de ordenación. Cuando el marco de trabajo se anexa el **ORDER BY** cláusula SQL del conjunto de registros de consulta, los controles de la cláusula de orden de la selección.

Debe establecer el criterio de ordenación del conjunto de registros después de crear el objeto, pero antes de llamar a su `Open` función miembro (o antes de llamar a la `Requery` de objeto cuya función miembro de un conjunto de registros existente `Open` ha sido la función miembro se llama anteriormente).

#### <a name="to-specify-a-sort-order-for-a-recordset-object"></a>Para especificar un criterio de ordenación para un objeto de conjunto de registros

1. Cree un nuevo objeto de conjunto de registros (o prepare la llamada a `Requery` de uno existente).

1. Establezca el valor del objeto [m_strSort](../../mfc/reference/crecordset-class.md#m_strsort) miembro de datos.

   El criterio de ordenación es una cadena terminada en null. Contiene el contenido de la **ORDER BY** cláusula pero no la palabra clave **ORDER BY**. Por ejemplo, use:

    ```
    recordset.m_strSort = "LastName DESC, FirstName DESC";
    ```

   not

    ```
    recordset.m_strSort = "ORDER BY LastName DESC, FirstName DESC";
    ```

1. Establecer otras opciones que necesite, como un filtro, el modo de bloqueo o parámetros.

1. Llame a `Open` para el nuevo objeto (o `Requery` para un objeto existente).

Los registros seleccionados se ordenan según lo especificado. Por ejemplo, para ordenar un conjunto de registros de alumnos por apellido y luego por nombres en orden descendente, haga lo siguiente:

```cpp
// Construct the recordset
CStudentSet rsStudent( NULL );
// Set the sort
rsStudent.m_strSort = "LastName DESC, FirstName DESC";
// Run the query with the sort in place
rsStudent.Open( );
```

El conjunto de registros contiene todos los registros de estudiantes, ordenados en orden descendente (Z a) por apellido, a continuación, por nombre.

> [!NOTE]
>  Si opta por reemplazar la cadena SQL predeterminada del conjunto de registros pasando su propia cadena SQL a `Open`, debe establecer un orden si la cadena personalizada contiene una **ORDER BY** cláusula.

## <a name="see-also"></a>Vea también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Conjunto de registros: Parametrizar un conjunto de registros (ODBC)](../../data/odbc/recordset-parameterizing-a-recordset-odbc.md)<br/>
[Conjunto de registros: Filtrar registros (ODBC)](../../data/odbc/recordset-filtering-records-odbc.md)