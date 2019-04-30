---
title: 'Conjunto de registros: Agregar registros de forma masiva (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC recordsets, adding records
- recordsets, adding records
- bulk record additions to recordsets
ms.assetid: 4685f656-14b9-4f10-a1c5-147b2b89a0b4
ms.openlocfilehash: a2c3eab8bb4c0e8db76fceb5a2dafd16a4a07079
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395669"
---
# <a name="recordset-adding-records-in-bulk-odbc"></a>Conjunto de registros: Agregar registros de forma masiva (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

La MFC [CRecordset](../../mfc/reference/crecordset-class.md) clase tiene una nueva optimización que mejora la eficiencia al agregar nuevos registros de forma masiva a una tabla.

> [!NOTE]
> Este tema se aplica a objetos derivados de `CRecordset` donde no se haya implementado la obtención masiva de filas. Si usas la obtención masiva de filas, vea [conjunto de registros: Obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Una opción nueva para el *dwOptions* parámetro para el [CRecordset:: Open](../../mfc/reference/crecordset-class.md#open) función miembro, `optimizeBulkAdd`, mejora el rendimiento cuando va a agregar varios registros de forma consecutiva sin llamar a `Requery` o `Close`. Solo los campos que están dañados antes del primer `Update` llamada se marcan como modificados para posteriores `AddNew` / `Update` llamadas.

Si está usando las clases de base de datos para aprovechar la `::SQLSetPos` API de ODBC de función para agregar, editar, y eliminar registros, esta optimización no es necesario.

Si se carga la biblioteca de cursores ODBC o el controlador ODBC no admite la adición, edición y eliminación a través de `::SQLSetPos`, esta optimización debe mejorar masiva agregar rendimiento. Para activar esta optimización, establezca el *dwOptions* parámetro en el `Open` llamar a para el conjunto de registros a la siguiente:

```
appendOnly | optimizeBulkAdd
```

## <a name="see-also"></a>Vea también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Conjunto de registros: agregar, actualizar y eliminar registros (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)<br/>
[Conjunto de registros: bloquear registros (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)