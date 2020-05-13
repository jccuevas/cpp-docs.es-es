---
title: 'Conjunto de registros: Bloquear registros (ODBC)'
ms.date: 11/04/2016
helpviewer_keywords:
- locks [C++], recordsets
- optimistic locking
- pessimistic locking in ODBC
- recordsets [C++], locking records
- optimistic locking, ODBC
- ODBC recordsets [C++], locking records
- data [C++], locking
ms.assetid: 8fe8fcfe-b55a-41a8-9136-94a7cd1e4806
ms.openlocfilehash: abd5f817ad321241df2d8565bd6bf346c0792088
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366956"
---
# <a name="recordset-locking-records-odbc"></a>Conjunto de registros: Bloquear registros (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

En este tema se explica:

- [Los tipos de bloqueo de registros disponibles.](#_core_record.2d.locking_modes)

- Cómo bloquear registros en el conjunto de [registros durante las actualizaciones.](#_core_locking_records_in_your_recordset)

Cuando se utiliza un conjunto de registros para actualizar un registro en el origen de datos, la aplicación puede bloquear el registro para que ningún otro usuario pueda actualizar el registro al mismo tiempo. El estado de un registro actualizado por dos usuarios al mismo tiempo es indefinido a menos que el sistema pueda garantizar que dos usuarios no pueden actualizar un registro simultáneamente.

> [!NOTE]
> Este tema se aplica a objetos derivados de `CRecordset` donde no se haya implementado la obtención masiva de filas. Si ha implementado la obtención masiva de filas, parte de la información no se aplica. Por ejemplo, no `Edit` se `Update` puede llamar a las funciones miembro y. Para obtener más información acerca de la obtención masiva de filas, vea [Conjunto de registros: obtención de registros en masa (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

## <a name="record-locking-modes"></a><a name="_core_record.2d.locking_modes"></a>Modos de bloqueo de registros

Las clases de base de datos proporcionan dos [modos de bloqueo de registros:](../../mfc/reference/crecordset-class.md#setlockingmode)

- Bloqueo optimista (valor predeterminado)

- Bloqueo pesimista

La actualización de un registro se produce en tres pasos:

1. Para iniciar la operación, llame a la función miembro [Edit.](../../mfc/reference/crecordset-class.md#edit)

1. Puede cambiar los campos adecuados del registro actual.

1. Finalizar la operación —y normalmente confirmar la actualización— mediante una llamada a la [Update](../../mfc/reference/crecordset-class.md#update) función miembro.

El bloqueo optimista bloquea el registro `Update` en el origen de datos solo durante la llamada. Si utiliza el bloqueo optimista en un entorno `Update` multiusuario, la aplicación debe controlar una condición de error. El bloqueo pesimista bloquea el registro `Edit` tan pronto como se `Update` llama y no lo `CDBException` libera hasta que se llama `Update`(los errores se indican a través del mecanismo, no por un valor de FALSE devuelto por ). El bloqueo pesimista tiene una posible penalización del rendimiento para otros usuarios, ya que `Update` el acceso simultáneo al mismo registro podría tener que esperar hasta la finalización del proceso de la aplicación.

## <a name="locking-records-in-your-recordset"></a><a name="_core_locking_records_in_your_recordset"></a>Bloqueo de registros en su conjunto de registros

Si desea cambiar el modo de [bloqueo](#_core_record.2d.locking_modes) de un objeto de conjunto `Edit`de registros del valor predeterminado, debe cambiar el modo antes de llamar a .

#### <a name="to-change-the-current-locking-mode-for-your-recordset"></a>Para cambiar el modo de bloqueo actual del conjunto de registros

1. Llame a la [SetLockingMode](../../mfc/reference/crecordset-class.md#setlockingmode) función miembro, especificando uno `CRecordset::pessimistic` o `CRecordset::optimistic`.

El nuevo modo de bloqueo permanece en vigor hasta que se cambia de nuevo o se cierra el conjunto de registros.

> [!NOTE]
> Relativamente pocos controladores ODBC admiten actualmente el bloqueo pesimista.

## <a name="see-also"></a>Consulte también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Conjunto de registros: Realizar una combinación (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)<br/>
[Conjunto de registros: Agregar, actualizar y eliminar registros (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)
