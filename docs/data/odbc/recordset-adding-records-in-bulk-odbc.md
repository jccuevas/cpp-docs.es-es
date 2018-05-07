---
title: 'Conjunto de registros: Agregar registros de forma masiva (ODBC) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ODBC recordsets, adding records
- recordsets, adding records
- bulk record additions to recordsets
ms.assetid: 4685f656-14b9-4f10-a1c5-147b2b89a0b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 7bb39b910eae797f360513954ad0c32d5e99bb86
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="recordset-adding-records-in-bulk-odbc"></a>Conjunto de registros: Agregar registros de forma masiva (ODBC)
Este tema es aplicable a las clases ODBC de MFC.  
  
 La MFC [CRecordset](../../mfc/reference/crecordset-class.md) clase tiene nuevas características de optimización que mejoran la eficiencia al agregar nuevos registros de forma masiva a una tabla.  
  
> [!NOTE]
>  Este tema se aplica a objetos derivados de `CRecordset` donde no se haya implementado la obtención masiva de filas. Si se usa la obtención masiva de filas, vea [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Una opción nueva para el **dwOptions** parámetro a la [CRecordset:: Open](../../mfc/reference/crecordset-class.md#open) función miembro, **optimizeBulkAdd**, mejora el rendimiento al agregar varios registros consecutivamente sin llamar a **Requery** o **cerrar**. Solo los campos que están desfasados antes del primer **actualización** llamada están marcados como modificados para posteriores `AddNew` / **actualización** llamadas.  
  
 Si está usando las clases de base de datos para aprovechar la **:: SQLSetPos** función de API de ODBC para agregar, editar, y eliminar registros, esta optimización no es necesario.  
  
 Si se carga la biblioteca de cursores ODBC o el controlador ODBC no admite la adición, edición y eliminación a través de **:: SQLSetPos**, esta optimización debe mejorar masiva agregar rendimiento. Para activar esta optimización, establezca el **dwOptions** parámetro en el **abiertos** llamar a para el conjunto de registros a la siguiente:  
  
```  
appendOnly | optimizeBulkAdd  
```  
  
## <a name="see-also"></a>Vea también  
 [Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Conjunto de registros: Agregar, actualizar y eliminar registros (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)   
 [Conjunto de registros: Bloquear registros (ODBC)](../../data/odbc/recordset-locking-records-odbc.md)