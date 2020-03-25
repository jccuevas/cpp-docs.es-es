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
ms.openlocfilehash: d4e80816a131c997e9f5bfaa34f025394b05a358
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212867"
---
# <a name="recordset-locking-records-odbc"></a>Conjunto de registros: Bloquear registros (ODBC)

Este tema es aplicable a las clases ODBC de MFC.

En este tema se explica:

- [Los tipos de bloqueo de registros disponibles](#_core_record.2d.locking_modes).

- [Cómo bloquear registros en el conjunto de registros durante las actualizaciones](#_core_locking_records_in_your_recordset).

Cuando se usa un conjunto de registros para actualizar un registro en el origen de datos, la aplicación puede bloquear el registro para que ningún otro usuario pueda actualizar el registro al mismo tiempo. El estado de un registro actualizado por dos usuarios al mismo tiempo no está definido, a menos que el sistema pueda garantizar que dos usuarios no puedan actualizar un registro simultáneamente.

> [!NOTE]
>  Este tema se aplica a objetos derivados de `CRecordset` donde no se haya implementado la obtención masiva de filas. Si ha implementado la obtención masiva de filas, parte de la información no se aplica. Por ejemplo, no puede llamar a las funciones miembro `Edit` y `Update`. Para obtener más información sobre la obtención masiva de filas, vea [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).

##  <a name="record-locking-modes"></a><a name="_core_record.2d.locking_modes"></a>Modos de bloqueo de registros

Las clases de base de datos proporcionan dos [modos de bloqueo de registros](../../mfc/reference/crecordset-class.md#setlockingmode):

- Bloqueo optimista (valor predeterminado)

- Bloqueo pesimista

La actualización de un registro se produce en tres pasos:

1. La operación se inicia llamando a la función miembro [Edit](../../mfc/reference/crecordset-class.md#edit) .

1. Puede cambiar los campos correspondientes del registro actual.

1. Finaliza la operación (y normalmente confirma la actualización) mediante una llamada a la función miembro [Update](../../mfc/reference/crecordset-class.md#update) .

El bloqueo optimista bloquea el registro en el origen de datos solo durante la llamada `Update`. Si utiliza el bloqueo optimista en un entorno multiusuario, la aplicación debe controlar una condición de error de `Update`. El bloqueo pesimista bloquea el registro en cuanto se llama a `Edit` y no se libera hasta que se llama a `Update` (los errores se indican a través del mecanismo de `CDBException`, no por el valor FALSE devuelto por `Update`). El bloqueo pesimista tiene una posible penalización del rendimiento para otros usuarios, ya que es posible que el acceso simultáneo al mismo registro tenga que esperar hasta que se complete el proceso de `Update` de la aplicación.

##  <a name="locking-records-in-your-recordset"></a><a name="_core_locking_records_in_your_recordset"></a>Bloquear registros en el conjunto de registros

Si desea cambiar el [modo de bloqueo](#_core_record.2d.locking_modes) de un objeto de conjunto de registros del predeterminado, debe cambiar el modo antes de llamar a `Edit`.

#### <a name="to-change-the-current-locking-mode-for-your-recordset"></a>Para cambiar el modo de bloqueo actual del conjunto de registros

1. Llame a la función miembro [SetLockingMode](../../mfc/reference/crecordset-class.md#setlockingmode) , especificando `CRecordset::pessimistic` o `CRecordset::optimistic`.

El nuevo modo de bloqueo permanece en vigor hasta que se vuelve a cambiar o se cierra el conjunto de registros.

> [!NOTE]
>  Relativamente pocos controladores ODBC admiten actualmente el bloqueo pesimista.

## <a name="see-also"></a>Consulte también

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Conjunto de registros: Realizar una combinación (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)<br/>
[Conjunto de registros: Agregar, actualizar y eliminar registros (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)
