---
title: 'Conjunto de registros: Bloquear registros (ODBC) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- locks [C++], recordsets
- optimistic locking
- pessimistic locking in ODBC
- recordsets [C++], locking records
- optimistic locking, ODBC
- ODBC recordsets [C++], locking records
- data [C++], locking
ms.assetid: 8fe8fcfe-b55a-41a8-9136-94a7cd1e4806
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: cb6ed678cab6ecc08ac47275648c5cdd01a0cd6f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46021166"
---
# <a name="recordset-locking-records-odbc"></a>Conjunto de registros: Bloquear registros (ODBC)

Este tema es aplicable a las clases ODBC de MFC.  
  
En este tema se explica:  
  
- [Los tipos de bloqueo de registro disponibles](#_core_record.2d.locking_modes).  
  
- [Cómo bloquear registros en el conjunto de registros durante las actualizaciones](#_core_locking_records_in_your_recordset).  
  
Cuando se usa un conjunto de registros para actualizar un registro en el origen de datos, la aplicación puede bloquear el registro para que ningún otro usuario pueda actualizar el registro al mismo tiempo. El estado de un registro actualizado por dos usuarios al mismo tiempo está definido a menos que el sistema puede garantizar que dos usuarios no pueden actualizar un registro al mismo tiempo.  
  
> [!NOTE]
>  Este tema se aplica a objetos derivados de `CRecordset` donde no se haya implementado la obtención masiva de filas. Si ha implementado la obtención masiva de filas, parte de la información no es aplicable. Por ejemplo, no puede llamar a la `Edit` y `Update` funciones miembro. Para obtener más información sobre la obtención masiva de filas, vea [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="_core_record.2d.locking_modes"></a> Modos de bloqueo de registros  

Las clases de base de datos proporcionan dos [modos de bloqueo de registro](../../mfc/reference/crecordset-class.md#setlockingmode):  
  
- (El valor predeterminado) de bloqueo optimista  
  
- El bloqueo pesimista  
  
Actualizar un registro se produce en tres pasos:  
  
1. Comenzar la operación mediante una llamada a la [editar](../../mfc/reference/crecordset-class.md#edit) función miembro.  
  
1. Cambiar los campos correspondientes del registro actual.  
  
1. Finalizar la operación y normalmente se confirma la actualización, mediante una llamada a la [actualizar](../../mfc/reference/crecordset-class.md#update) función miembro.  
  
Bloqueo optimista bloquea el registro en el origen de datos solo durante el `Update` llamar. Si utiliza el bloqueo optimista en un entorno multiusuario, la aplicación debe controlar un `Update` condición de error. El bloqueo pesimista bloquea el registro, en cuanto llame a `Edit` y no lo libera hasta que llamada `Update` (errores se indican mediante el `CDBException` mecanismo, no por un valor False devuelto por `Update`). El bloqueo pesimista tiene una penalización de rendimiento potencial para otros usuarios, porque el acceso simultáneo al mismo registro podría tener que esperar hasta la finalización de la aplicación `Update` proceso.  
  
##  <a name="_core_locking_records_in_your_recordset"></a> Bloquear registros en el conjunto de registros  

Si desea cambiar un objeto recordset [modo de bloqueo](#_core_record.2d.locking_modes) del valor predeterminado, debe cambiar el modo antes de llamar a `Edit`.  
  
#### <a name="to-change-the-current-locking-mode-for-your-recordset"></a>Para cambiar el modo de bloqueo actual para el conjunto de registros  
  
1. Llame a la [SetLockingMode](../../mfc/reference/crecordset-class.md#setlockingmode) función miembro, ya sea especificando `CRecordset::pessimistic` o `CRecordset::optimistic`.  
  
El nuevo modo de bloqueo se sigue en vigor hasta que vuelva a cambiar o se cierra el conjunto de registros.  
  
> [!NOTE]
>  Relativamente pocos controladores ODBC admiten actualmente el bloqueo pesimista.  
  
## <a name="see-also"></a>Vea también  

[Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)<br/>
[Conjunto de registros: Realizar una combinación (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)<br/>
[Conjunto de registros: Agregar, actualizar y eliminar registros (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)