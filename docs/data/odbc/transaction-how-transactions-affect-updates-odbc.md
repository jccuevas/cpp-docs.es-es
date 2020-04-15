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
ms.openlocfilehash: 8a87176ecb20beaf46583e1190b0ad458d508b31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376431"
---
# <a name="transaction-how-transactions-affect-updates-odbc"></a>Transacción: Cómo afectan las transacciones a las actualizaciones (ODBC)

Las actualizaciones del origen de [datos](../../data/odbc/data-source-odbc.md) se administran durante las transacciones mediante el uso de un búfer de edición (el mismo método utilizado fuera de las transacciones). Los miembros de datos de campo de un conjunto de registros sirven colectivamente como `AddNew` `Edit`un búfer de edición que contiene el registro actual, que el conjunto de registros realiza una copia de seguridad temporalmente durante un archivo o . Durante `Delete` una operación, no se realiza una copia de seguridad del registro actual dentro de una transacción. Para obtener más información sobre el búfer de edición y cómo las actualizaciones almacenan el registro actual, vea Conjunto de registros: cómo los conjuntos de [registros actualizan registros (ODBC)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).

> [!NOTE]
> Si ha implementado la obtención masiva `AddNew`de `Edit`filas, no puede llamar a , , o `Delete`. En su lugar, debe escribir sus propias funciones para realizar actualizaciones en el origen de datos. Para obtener más información acerca de la obtención masiva de filas, vea [Conjunto de registros: obtención de registros en masa (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

Durante las `AddNew`transacciones, , `Edit`, y `Delete` las operaciones se pueden confirmar o revertir. Los efectos de `CommitTrans` y `Rollback` pueden hacer que el registro actual no se restaure en el búfer de edición. Para asegurarse de que el registro actual se restaura `CommitTrans` `Rollback` correctamente, `CDatabase` es importante comprender `CRecordset`cómo las funciones miembro y de trabajo con las funciones de actualización de .

## <a name="how-committrans-affects-updates"></a><a name="_core_how_committrans_affects_updates"></a>Cómo afecta CommitTrans a las actualizaciones

En la tabla siguiente `CommitTrans` se explican los efectos de las transacciones.

### <a name="how-committrans-affects-updates"></a>Cómo afecta CommitTrans a las actualizaciones

|Operación|Estado de la fuente de datos|
|---------------|---------------------------|
|`AddNew`y `Update`, y luego`CommitTrans`|Se agrega un nuevo registro al origen de datos.|
|`AddNew`(sin `Update`), y luego`CommitTrans`|Se pierde un nuevo récord. Registro no agregado al origen de datos.|
|`Edit`y `Update`, y luego`CommitTrans`|Edita confirmada en el origen de datos.|
|`Edit`(sin `Update`), y luego`CommitTrans`|Las ediciones del registro se pierden. El registro permanece sin cambios en el origen de datos.|
|`Delete`Entonces`CommitTrans`|Registros eliminados del origen de datos.|

## <a name="how-rollback-affects-transactions"></a><a name="_core_how_rollback_affects_updates"></a>Cómo afecta la reversión a las transacciones

En la tabla siguiente `Rollback` se explican los efectos de las transacciones.

### <a name="how-rollback-affects-transactions"></a>Cómo afecta la reversión a las transacciones

|Operación|Estado del registro actual|También debe|Estado de la fuente de datos|
|---------------|------------------------------|-------------------|---------------------------|
|`AddNew`y `Update`, entonces`Rollback`|El contenido del registro actual se almacena temporalmente para dejar espacio para el nuevo registro. El nuevo registro se introduce en el búfer de edición. Después `Update` de llamarse, el registro actual se restaura en el búfer de edición.||La adición al `Update` origen de datos realizada por se invierte.|
|`AddNew`(sin `Update`), entonces`Rollback`|El contenido del registro actual se almacena temporalmente para dejar espacio para el nuevo registro. El búfer de edición contiene un nuevo registro.|Vuelva `AddNew` a llamar para restaurar el búfer de edición en un nuevo registro vacío. O `Move`llame al (0) para restaurar los valores antiguos en el búfer de edición.|Dado `Update` que no se llamó, no se realizaron cambios en el origen de datos.|
|`Edit`y `Update`, entonces`Rollback`|Una versión sin editar del registro actual se almacena temporalmente. Las ediciones se realizan en el contenido del búfer de edición. Después `Update` de llamarse, la versión sin editar del registro todavía se almacena temporalmente.|*Dynaset*: Desplácese fuera del registro actual y, a continuación, vuelva a restaurar la versión sin editar del registro en el búfer de edición.<br /><br /> *Instantánea:* `Requery` llame para actualizar el conjunto de registros desde el origen de datos.|Los cambios realizados en el origen de datos por `Update` se invierten.|
|`Edit`(sin `Update`), entonces`Rollback`|Una versión sin editar del registro actual se almacena temporalmente. Las ediciones se realizan en el contenido del búfer de edición.|Llame `Edit` de nuevo para restaurar la versión sin editar del registro en el búfer de edición.|Dado `Update` que no se llamó, no se realizaron cambios en el origen de datos.|
|`Delete`Entonces`Rollback`|Se elimina el contenido del registro actual.|Llame `Requery` para restaurar el contenido del registro actual desde el origen de datos.|La eliminación de datos del origen de datos se invierte.|

## <a name="see-also"></a>Consulte también

[Transacción (ODBC)](../../data/odbc/transaction-odbc.md)<br/>
[Transacción: Realizar una transacción en un conjunto de registros (ODBC)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)<br/>
[Clase CDatabase](../../mfc/reference/cdatabase-class.md)<br/>
[Clase CRecordset](../../mfc/reference/crecordset-class.md)
