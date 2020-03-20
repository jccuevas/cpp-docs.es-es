---
title: 'Transacción: Cómo afectan las transacciones a las actualizaciones (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- transactions, updating recordsets
- ODBC recordsets, transactions
- transactions, rolling back
- CommitTrans method
- Rollback method, ODBC transactions
ms.assetid: 9e00bbf4-e9fb-4332-87fc-ec8ac61b3f68
ms.openlocfilehash: d03ec3f71c38f7790d66fbf6f800b7647e080147
ms.sourcegitcommit: 0e3da5cea44437c132b5c2ea522bd229ea000a10
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/12/2019
ms.locfileid: "79544427"
---
# <a name="transaction-how-transactions-affect-updates-odbc"></a>Transacción: Cómo afectan las transacciones a las actualizaciones (ODBC)

Las actualizaciones del [origen de datos](../../data/odbc/data-source-odbc.md) se administran durante las transacciones mediante el uso de un búfer de edición (el mismo método que se usa fuera de las transacciones). Los miembros de datos de campo de un conjunto de registros actúan colectivamente como un búfer de edición que contiene el registro actual, del que se realiza una copia de seguridad del conjunto de registros temporalmente durante una `AddNew` o `Edit`. Durante una operación de `Delete`, no se realiza una copia de seguridad del registro actual dentro de una transacción. Para obtener más información sobre el búfer de edición y cómo almacena las actualizaciones el registro actual, vea conjunto de registros [: Cómo actualizar los registros (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

> [!NOTE]
>  Si ha implementado la obtención masiva de filas, no puede llamar a `AddNew`, `Edit`o `Delete`. En su lugar, debe escribir sus propias funciones para realizar actualizaciones en el origen de datos. Para obtener más información sobre la obtención masiva de filas, vea [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Durante las transacciones, se pueden confirmar o revertir las operaciones de `AddNew`, `Edit`y `Delete`. Los efectos de `CommitTrans` y `Rollback` pueden hacer que el registro actual no se restaure en el búfer de edición. Para asegurarse de que el registro actual se restaure correctamente, es importante comprender cómo funcionan las funciones miembro de `CommitTrans` y `Rollback` de `CDatabase` con las funciones de actualización de `CRecordset`.

##  <a name="how-committrans-affects-updates"></a><a name="_core_how_committrans_affects_updates"></a>Cómo afecta CommitTrans a las actualizaciones

En la tabla siguiente se explican los efectos de `CommitTrans` en las transacciones.

### <a name="how-committrans-affects-updates"></a>Cómo afecta CommitTrans a las actualizaciones

|Operación|Estado del origen de datos|
|---------------|---------------------------|
|`AddNew` y `Update`y, a continuación, `CommitTrans`|El nuevo registro se agrega al origen de datos.|
|`AddNew` (sin `Update`) y, a continuación, `CommitTrans`|Se pierde el nuevo registro. No se agregó el registro al origen de datos.|
|`Edit` y `Update`y, a continuación, `CommitTrans`|Edita confirmada en el origen de datos.|
|`Edit` (sin `Update`) y, a continuación, `CommitTrans`|Se pierden las modificaciones en el registro. El registro permanece inalterado en el origen de datos.|
|`Delete` `CommitTrans`|Registros eliminados del origen de datos.|

##  <a name="how-rollback-affects-transactions"></a><a name="_core_how_rollback_affects_updates"></a>Cómo afecta la reversión a las transacciones

En la tabla siguiente se explican los efectos de `Rollback` en las transacciones.

### <a name="how-rollback-affects-transactions"></a>Cómo afecta la reversión a las transacciones

|Operación|Estado del registro actual|También debe|Estado del origen de datos|
|---------------|------------------------------|-------------------|---------------------------|
|`AddNew` y `Update`, `Rollback`|El contenido del registro actual se almacena temporalmente para dejar espacio para el nuevo registro. El nuevo registro se escribe en el búfer de edición. Una vez que se llama a `Update`, el registro actual se restaura en el búfer de edición.||Se invierte la adición al origen de datos realizado por `Update`.|
|`AddNew` (sin `Update`), `Rollback`|El contenido del registro actual se almacena temporalmente para dejar espacio para el nuevo registro. El búfer de edición contiene un nuevo registro.|Vuelva a llamar a `AddNew` para restaurar el búfer de edición en un registro nuevo vacío. O llame a `Move`(0) para restaurar los valores antiguos en el búfer de edición.|Dado que no se ha llamado a `Update`, no se realizaron cambios en el origen de datos.|
|`Edit` y `Update`, `Rollback`|Una versión sin editar del registro actual se almacena temporalmente. Las modificaciones se realizan en el contenido del búfer de edición. Una vez que se llama a `Update`, la versión sin editar del registro sigue estando almacenada temporalmente.|*Dynaset*: Desplácese fuera del registro actual y vuelva a restaurar la versión sin editar del registro en el búfer de edición.<br /><br /> *Snapshot*: llame a `Requery` para actualizar el conjunto de registros desde el origen de datos.|Se invierten los cambios realizados en el origen de datos realizado por `Update`.|
|`Edit` (sin `Update`), `Rollback`|Una versión sin editar del registro actual se almacena temporalmente. Las modificaciones se realizan en el contenido del búfer de edición.|Vuelva a llamar a `Edit` para restaurar la versión sin editar del registro en el búfer de edición.|Dado que no se ha llamado a `Update`, no se realizaron cambios en el origen de datos.|
|`Delete` `Rollback`|Se elimina el contenido del registro actual.|Llame a `Requery` para restaurar el contenido del registro actual del origen de datos.|Se invierte la eliminación de datos del origen de datos.|

## <a name="see-also"></a>Consulte también

[Transacción (ODBC)](../../data/odbc/transaction-odbc.md)<br/>
[Transacción: Realizar una transacción en un conjunto de registros (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)<br/>
[CDatabase (clase)](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordset (clase)](../../mfc/reference/crecordset-class.md)
