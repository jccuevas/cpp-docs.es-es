---
title: 'Conjunto de registros: Bloquear registros (ODBC) | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- locks [C++], recordsets
- optimistic locking
- pessimistic locking in ODBC
- recordsets [C++], locking records
- optimistic locking, ODBC
- ODBC recordsets [C++], locking records
- data [C++], locking
ms.assetid: 8fe8fcfe-b55a-41a8-9136-94a7cd1e4806
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 76d7ab2df01e485ffff70120609227b9fbae6ac5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="recordset-locking-records-odbc"></a>Conjunto de registros: Bloquear registros (ODBC)
Este tema es aplicable a las clases ODBC de MFC.  
  
 En este tema se explica:  
  
-   [Los tipos de bloqueos disponibles de registro](#_core_record.2d.locking_modes).  
  
-   [Cómo bloquear registros en el conjunto de registros durante las actualizaciones](#_core_locking_records_in_your_recordset).  
  
 Cuando se utiliza un conjunto de registros para actualizar un registro en el origen de datos, la aplicación puede bloquear el registro para que ningún otro usuario pueda actualizar el registro al mismo tiempo. El estado de un registro actualizado por dos usuarios al mismo tiempo es indefinido, a menos que el sistema pueda garantizar que dos usuarios no pueden actualizar un registro simultáneamente.  
  
> [!NOTE]
>  Este tema se aplica a objetos derivados de `CRecordset` donde no se haya implementado la obtención masiva de filas. Si ha implementado la obtención masiva de filas, parte de la información no se aplica. Por ejemplo, no se puede llamar a la **editar** y **actualización** funciones miembro. Para obtener más información sobre la obtención masiva de filas, vea [conjunto de registros: obtener registros de forma masiva (ODBC)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="_core_record.2d.locking_modes"></a>Modos de bloqueo de registros  
 Las clases de base de datos proporcionan dos [modos de bloqueo de registro](../../mfc/reference/crecordset-class.md#setlockingmode):  
  
-   (El valor predeterminado) de bloqueo optimista  
  
-   el bloqueo pesimista  
  
 Actualizar un registro se produce en tres pasos:  
  
1.  Comenzar la operación mediante una llamada a la [editar](../../mfc/reference/crecordset-class.md#edit) función miembro.  
  
2.  Cambiar los campos correspondientes del registro actual.  
  
3.  Finalizar la operación y normalmente se confirma la actualización, mediante una llamada a la [actualizar](../../mfc/reference/crecordset-class.md#update) función miembro.  
  
 Bloqueo optimista bloquea el registro en el origen de datos solo durante la **actualización** llamar. Si se utiliza el bloqueo optimista en un entorno multiusuario, la aplicación debe controlar un **actualización** condición de error. El bloqueo pesimista bloquea el registro en cuanto se llama a **editar** y no lo libera hasta que llamada **actualización** (se indican errores a través de la `CDBException` mecanismo, no por un valor de **FALSE** devuelto por **actualización**). El bloqueo pesimista tiene una penalización de rendimiento potencial para otros usuarios, porque el acceso simultáneo al mismo registro podría tener que esperar hasta la finalización de la aplicación **actualización** proceso.  
  
##  <a name="_core_locking_records_in_your_recordset"></a>Bloquear registros en el conjunto de registros  
 Si desea cambiar un objeto de conjunto de registros [modo de bloqueo](#_core_record.2d.locking_modes) de manera predeterminada, debe cambiar el modo antes de llamar a **editar**.  
  
#### <a name="to-change-the-current-locking-mode-for-your-recordset"></a>Para cambiar el modo de bloqueo actual para el conjunto de registros  
  
1.  Llame a la [SetLockingMode](../../mfc/reference/crecordset-class.md#setlockingmode) función miembro, especificar **CRecordset:: pessimistic** o **CRecordset:: OPTIMISTIC**.  
  
 El nuevo modo de bloqueo permanece en vigor hasta que vuelva a cambiarlo o se cierra el conjunto de registros.  
  
> [!NOTE]
>  Relativamente pocos controladores ODBC admiten actualmente el bloqueo pesimista.  
  
## <a name="see-also"></a>Vea también  
 [Conjunto de registros (ODBC)](../../data/odbc/recordset-odbc.md)   
 [Conjunto de registros: Realizar una combinación (ODBC)](../../data/odbc/recordset-performing-a-join-odbc.md)   
 [Conjunto de registros: Agregar, actualizar y eliminar registros (ODBC)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)