---
title: "Transacción: Cómo afectan las transacciones a las actualizaciones (ODBC) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- transactions, updating recordsets
- ODBC recordsets, transactions
- transactions, rolling back
- CommitTrans method
- Rollback method, ODBC transactions
ms.assetid: 9e00bbf4-e9fb-4332-87fc-ec8ac61b3f68
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 59eb8aecbf2dd2138c8a0469d71364b55fd82774
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="transaction-how-transactions-affect-updates-odbc"></a>Transacción: Cómo afectan las transacciones a las actualizaciones (ODBC)
Las actualizaciones a la [origen de datos](../../data/odbc/data-source-odbc.md) se administran durante las transacciones mediante el uso de un búfer de edición (el mismo método usado fuera de las transacciones). Los miembros de datos de campo de un conjunto de registros actúan en conjunto como un búfer de edición que contiene el registro actual, que el conjunto de registros se realiza una copia temporal durante un `AddNew` o **editar**. Durante una **eliminar** operación, el registro actual no se copia de seguridad dentro de una transacción. Para obtener más información sobre el búfer de edición y el modo en que las actualizaciones almacenan el registro actual, vea [conjunto de registros: actualizar los registros (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).  
  
> [!NOTE]
>  Si ha implementado la obtención masiva de filas, no se puede llamar `AddNew`, **editar**, o **eliminar**. En su lugar, debe escribir sus propias funciones para realizar actualizaciones en el origen de datos. Para obtener más información sobre la obtención masiva de filas, vea [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Durante las transacciones, `AddNew`, **editar**, y **eliminar** pueden confirmar o revertir las operaciones. Los efectos de **CommitTrans** y **reversión** podría hacer que el registro actual no puede restaurarse en el búfer de edición. Para asegurarse de que el registro actual se ha restaurado correctamente, es importante entender cómo la **CommitTrans** y **reversión** las funciones miembro de `CDatabase` funcionan con las funciones de actualización de `CRecordset`.  
  
##  <a name="_core_how_committrans_affects_updates"></a>Cómo afecta CommitTrans a las actualizaciones  
 La siguiente tabla explica los efectos de **CommitTrans** en las transacciones.  
  
### <a name="how-committrans-affects-updates"></a>Cómo afecta CommitTrans a las actualizaciones  
  
|Operación|Estado de origen de datos|  
|---------------|---------------------------|  
|`AddNew`y **actualización**y, a continuación, **CommitTrans**|Nuevo registro se agregan al origen de datos.|  
|`AddNew`(sin **actualización**) y, a continuación, **CommitTrans**|Nuevo registro se pierde. No se agregan al origen de datos de registro.|  
|**Editar** y **actualización**y, a continuación, **CommitTrans**|Confirmada las modificaciones en el origen de datos.|  
|**Editar** (sin **actualización**) y, a continuación, **CommitTrans**|Se perderán las modificaciones realizadas en el registro. Registro permanece sin cambios en el origen de datos.|  
|**Eliminar** , a continuación, **CommitTrans**|Registros eliminados del origen de datos.|  
  
##  <a name="_core_how_rollback_affects_updates"></a>Cómo afecta Rollback a las transacciones  
 La siguiente tabla explica los efectos de **reversión** en las transacciones.  
  
### <a name="how-rollback-affects-transactions"></a>Cómo afecta Rollback a las transacciones  
  
|Operación|Estado de registro actual|También debe|Estado de origen de datos|  
|---------------|------------------------------|-------------------|---------------------------|  
|`AddNew`y **actualización**, a continuación, **reversión**|Contenido del registro actual se almacena temporalmente para dejar espacio para el nuevo registro. Nuevo registro se escribe en el búfer de edición. Después de **actualización** se llama, este registro se restaura en el búfer de edición.||La adición al origen de datos realizada por **actualización** se ha invertido.|  
|`AddNew`(sin **actualización**), a continuación, **reversión**|Contenido del registro actual se almacena temporalmente para dejar espacio para el nuevo registro. Editar búfer contiene el nuevo registro.|Llame a `AddNew` nuevo para restaurar el búfer de edición en un registro nuevo y vacío. O llamar a **mover**(0) para restaurar los valores antiguos en el búfer de edición.|Dado que **actualización** no se llamó, no ha habido cambios realizados en el origen de datos.|  
|**Editar** y **actualización**, a continuación, **reversión**|Una versión no modificada del registro actual se almacena temporalmente. Se realizan modificaciones en el contenido del búfer de edición. Después de **actualización** se llama, el sin editar versión del registro continúa almacenada temporalmente.|*Conjunto de registros dinámicos*: desplácese fuera del registro actual, a continuación, volver a restaurar la versión no modificada del registro en el búfer de edición.<br /><br /> *Instantánea*: llamar a **Requery** para actualizar el conjunto de registros desde el origen de datos.|Cambios realizados por el origen de datos **actualización** están invertidas.|  
|**Editar** (sin **actualización**), a continuación, **reversión**|Una versión no modificada del registro actual se almacena temporalmente. Se realizan modificaciones en el contenido del búfer de edición.|Llame a **editar** nuevo para restaurar la versión no modificada del registro en el búfer de edición.|Dado que **actualización** no se llamó, no ha habido cambios realizados en el origen de datos.|  
|**Eliminar** , a continuación, **reversión**|Se elimina el contenido del registro actual.|Llame a **Requery** para restaurar el contenido del registro actual del origen de datos.|Eliminación de datos de origen de datos se ha invertido.|  
  
## <a name="see-also"></a>Vea también  
 [Transacción (ODBC)](../../data/odbc/transaction-odbc.md)   
 [Transacción (ODBC)](../../data/odbc/transaction-odbc.md)   
 [Transacción: Realizar una transacción en un conjunto de registros (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)   
 [CDatabase (clase)](../../mfc/reference/cdatabase-class.md)   
 [CRecordset (clase)](../../mfc/reference/crecordset-class.md)