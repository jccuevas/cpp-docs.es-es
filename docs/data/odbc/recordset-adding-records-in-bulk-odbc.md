---
title: 'Conjunto de registros: Agregar registros de forma masiva (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets, adding records
- recordsets, adding records
- bulk record additions to recordsets
ms.assetid: 4685f656-14b9-4f10-a1c5-147b2b89a0b4
ms.openlocfilehash: f561cb0275933a973e97ef0518148e81e14a0234
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213023"
---
# <a name="recordset-adding-records-in-bulk-odbc"></a>Conjunto de registros: Agregar registros de forma masiva (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

La clase [CRecordset](../../mfc/reference/crecordset-class.md) de MFC tiene una nueva optimización que mejora la eficacia al agregar nuevos registros de forma masiva a una tabla.

> [!NOTE]
> Este tema se aplica a objetos derivados de `CRecordset` donde no se haya implementado la obtención masiva de filas. Si usa la obtención masiva de filas, vea [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Una nueva opción para el parámetro *dwOptions* de la función miembro [CRecordset:: Open](../../mfc/reference/crecordset-class.md#open) , `optimizeBulkAdd`, mejora el rendimiento cuando se agregan varios registros consecutivamente sin llamar a `Requery` o `Close`. Solo los campos que se han modificado antes de la primera llamada a `Update` se marcan como modificados para las llamadas posteriores a `Update` de /de `AddNew`.

Si utiliza las clases de base de datos para aprovechar las ventajas de la función de la API de ODBC `::SQLSetPos` para agregar, editar y eliminar registros, esta optimización no es necesaria.

Si se carga la biblioteca de cursores ODBC o el controlador ODBC no permite agregar, editar y eliminar a través de `::SQLSetPos`, esta optimización debe mejorar el rendimiento de la adición masiva. Para activar esta optimización, establezca el parámetro *dwOptions* en la `Open` llamada del conjunto de registros a lo siguiente:

```
appendOnly | optimizeBulkAdd
```

## <a name="see-also"></a>Consulte también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Conjunto de registros: Agregar, actualizar y eliminar registros (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)<br/>
[Conjunto de registros: Bloquear registros (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)
