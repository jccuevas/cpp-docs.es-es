---
title: 'Transacción: Cómo afectan las transacciones a las actualizaciones (ODBC) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- transactions, updating recordsets
- ODBC recordsets, transactions
- transactions, rolling back
- CommitTrans method
- Rollback method, ODBC transactions
ms.assetid: 9e00bbf4-e9fb-4332-87fc-ec8ac61b3f68
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c83b7683e843be1f7e5f8d935fcaf9d6141aa214
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50066765"
---
# <a name="transaction-how-transactions-affect-updates-odbc"></a>Transacción: Cómo afectan las transacciones a las actualizaciones (ODBC)

Actualiza a la [origen de datos](../../data/odbc/data-source-odbc.md) se administran durante las transacciones mediante el uso de un búfer de edición (el mismo método usado fuera de las transacciones). Los miembros de datos de campo de un conjunto de registros actúan en conjunto como un búfer de edición que contiene el registro actual, que el conjunto de registros realiza copias de seguridad temporal durante una `AddNew` o `Edit`. Durante una `Delete` operación, el registro actual no se copia en una transacción. Para obtener más información sobre el búfer de edición y cómo las actualizaciones de almacenan el registro actual, vea [conjunto de registros: actualizar los registros (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

> [!NOTE]
>  Si ha implementado la obtención masiva de filas, no puede llamar a `AddNew`, `Edit`, o `Delete`. En su lugar, debe escribir sus propias funciones para realizar actualizaciones en el origen de datos. Para obtener más información sobre la obtención masiva de filas, vea [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Durante las transacciones `AddNew`, `Edit`, y `Delete` operaciones pueden ser confirmadas o revertidas. Los efectos de `CommitTrans` y `Rollback` puede provocar que el registro no debe restaurarse en el búfer de edición actual. Para asegurarse de que el registro actual se ha restaurado correctamente, es importante comprender cómo el `CommitTrans` y `Rollback` funciones miembro de `CDatabase` funcionan con las funciones de actualización de `CRecordset`.

##  <a name="_core_how_committrans_affects_updates"></a> Cómo afecta CommitTrans a las actualizaciones

La siguiente tabla explica los efectos de `CommitTrans` en transacciones.

### <a name="how-committrans-affects-updates"></a>Cómo afecta CommitTrans a las actualizaciones

|Operación|Estado del origen de datos|
|---------------|---------------------------|
|`AddNew` y `Update`y, a continuación, `CommitTrans`|Nuevo registro se agregan al origen de datos.|
|`AddNew` (sin `Update`) y, a continuación, `CommitTrans`|Nuevo registro se pierde. No se agregan al origen de datos de registro.|
|`Edit` y `Update`y, a continuación, `CommitTrans`|Modificaciones de compromiso de origen de datos.|
|`Edit` (sin `Update`) y, a continuación, `CommitTrans`|Realizar ediciones en el registro se pierden. Registro permanece sin cambios en el origen de datos.|
|`Delete` A continuación `CommitTrans`|Registros eliminados desde el origen de datos.|

##  <a name="_core_how_rollback_affects_updates"></a> Cómo deshacer afecta a las transacciones

La siguiente tabla explica los efectos de `Rollback` en transacciones.

### <a name="how-rollback-affects-transactions"></a>Cómo deshacer afecta a las transacciones

|Operación|Estado de registro actual|También debe|Estado del origen de datos|
|---------------|------------------------------|-------------------|---------------------------|
|`AddNew` y `Update`, a continuación, `Rollback`|Contenido del registro actual se almacena temporalmente para dejar espacio para el nuevo registro. Nuevo registro se escribe en el búfer de edición. Después de `Update` se denomina actual se restaura el registro en el búfer de edición.||La adición al origen de datos realizada por `Update` se invierte.|
|`AddNew` (sin `Update`), a continuación, `Rollback`|Contenido del registro actual se almacena temporalmente para dejar espacio para el nuevo registro. Editar búfer contiene el nuevo registro.|Llamar a `AddNew` nuevo para restaurar el búfer de edición en un registro nuevo y vacío. O llame a `Move`(0) para restaurar los valores antiguos en el búfer de edición.|Dado que `Update` no se llamó, no había cambios realizados en el origen de datos.|
|`Edit` y `Update`, a continuación, `Rollback`|Una versión no modificada del registro actual se almacena temporalmente. Las modificaciones se realizan en el contenido del búfer de edición. Después de `Update` se llama, el no editado versión del registro continúa almacenada temporalmente.|*Conjunto de registros dinámicos*: desplácese fuera del registro actual y después volver a restaurar la versión no modificada del registro en el búfer de edición.<br /><br /> *Instantánea*: llamar a `Requery` para actualizar el conjunto de registros del origen de datos.|Los cambios realizados por el origen de datos `Update` están invertidas.|
|`Edit` (sin `Update`), a continuación, `Rollback`|Una versión no modificada del registro actual se almacena temporalmente. Las modificaciones se realizan en el contenido del búfer de edición.|Llamar a `Edit` nuevo para restaurar la versión no modificada del registro en el búfer de edición.|Dado que `Update` no se llamó, no había cambios realizados en el origen de datos.|
|`Delete` A continuación `Rollback`|Se elimina el contenido del registro actual.|Llame a `Requery` para restaurar el contenido del registro actual del origen de datos.|Se invierte la eliminación de datos de origen de datos.|

## <a name="see-also"></a>Vea también

[Transacción (ODBC)](../../data/odbc/transaction-odbc.md)<br/>
[Transacción (ODBC)](../../data/odbc/transaction-odbc.md)<br/>
[Transacción: Realizar una transacción en un conjunto de registros (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)<br/>
[CDatabase (clase)](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordset (clase)](../../mfc/reference/crecordset-class.md)