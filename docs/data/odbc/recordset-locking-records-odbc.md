---
title: "Conjunto de registros: Bloquear registros (ODBC) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "datos [C++], bloquear"
  - "bloqueos [C++], conjuntos de registros"
  - "conjuntos de registros ODBC [C++], bloquear registros"
  - "bloqueo optimista"
  - "bloqueo optimista, ODBC"
  - "bloqueo pesimista en ODBC"
  - "conjuntos de registros [C++], bloquear registros"
ms.assetid: 8fe8fcfe-b55a-41a8-9136-94a7cd1e4806
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Conjunto de registros: Bloquear registros (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este tema es aplicable a las clases ODBC de MFC.  
  
 En este tema se explica:  
  
-   [Los tipos de bloqueo de registros disponibles](#_core_record.2d.locking_modes).  
  
-   [Cómo bloquear registros en un conjunto de registros durante las actualizaciones](#_core_locking_records_in_your_recordset).  
  
 Al utilizar un conjunto de registros para actualizar un registro en el origen de datos, la aplicación puede bloquear el registro para que ningún otro usuario pueda actualizarlo al mismo tiempo.  El estado de un registro actualizado por dos usuarios al mismo tiempo no está definido a menos que el sistema pueda garantizar que dos usuarios no puedan actualizar un registro simultáneamente.  
  
> [!NOTE]
>  Este tema se aplica a objetos derivados de `CRecordset` donde no se haya implementado la obtención masiva de filas.  Si está implementada la obtención de filas masiva, parte de esta información no es aplicable.  Por ejemplo, no se puede llamar a las funciones miembro **Edit** y **Update**.  Para obtener más información sobre la obtención masiva de filas, vea [Conjunto de registros: Obtener registros de forma masiva \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
##  <a name="_core_record.2d.locking_modes"></a> Modos de bloqueo de registros  
 Las clases de base de datos proporcionan dos [modos de bloqueo de registros](../Topic/CRecordset::SetLockingMode.md):  
  
-   Bloqueo optimista \(el predeterminado\)  
  
-   Bloqueo pesimista  
  
 La actualización de un registro tiene lugar en tres pasos:  
  
1.  La operación comienza llamando a la función miembro [Edit](../Topic/CRecordset::Edit.md).  
  
2.  Se modifican los campos correspondientes del registro actual.  
  
3.  La operación termina, y normalmente se confirma la actualización, llamando a la función miembro [Update](../Topic/CRecordset::Update.md).  
  
 El bloqueo optimista bloquea el registro en el origen de datos sólo durante la llamada a **Update**.  Si se utiliza el bloqueo optimista en un entorno de varios usuarios, la aplicación debe ser capaz de controlar un posible error en **Update**.  El bloqueo pesimista bloquea el registro nada más llamar a **Edit** y no lo libera hasta que se llama a **Update** \(los errores se comunican mediante el mecanismo `CDBException`, no por un valor **FALSE** devuelto por **Update**\).  El bloqueo pesimista tiene una penalización de rendimiento potencial para otros usuarios, ya que el acceso simultáneo al mismo registro puede tener que esperar a la finalización del proceso **Update** de la aplicación.  
  
##  <a name="_core_locking_records_in_your_recordset"></a> Bloquear registros en el conjunto de registros  
 Si desea modificar el [modo de bloqueo](#_core_record.2d.locking_modes) de un objeto de conjunto de registros respecto al modo predeterminado, debe cambiarlo antes de llamar a **Edit.**  
  
#### Para cambiar el modo de bloqueo actual del conjunto de registros  
  
1.  Llame a la función miembro [SetLockingMode](../Topic/CRecordset::SetLockingMode.md) especificando **CRecordset::pessimistic** o **CRecordset::optimistic**.  
  
 El nuevo modo de bloqueo permanece en vigor hasta que se cambia de nuevo o se cierra el conjunto de registros.  
  
> [!NOTE]
>  Hay relativamente pocos controladores ODBC que admitan actualmente el bloqueo pesimista.  
  
## Vea también  
 [Conjunto de registros \(ODBC\)](../../data/odbc/recordset-odbc.md)   
 [Conjunto de registros: Realizar una combinación \(ODBC\)](../../data/odbc/recordset-performing-a-join-odbc.md)   
 [Conjunto de registros: Agregar, actualizar y eliminar registros \(ODBC\)](../../data/odbc/recordset-adding-updating-and-deleting-records-odbc.md)