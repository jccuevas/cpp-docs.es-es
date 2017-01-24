---
title: "Transacci&#243;n: C&#243;mo afectan las transacciones a las actualizaciones (ODBC) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CommitTrans (método)"
  - "conjuntos de registros ODBC, transacciones"
  - "Rollback (método), transacciones ODBC"
  - "transacciones, revertir"
  - "transacciones, actualizar conjuntos de registros"
ms.assetid: 9e00bbf4-e9fb-4332-87fc-ec8ac61b3f68
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Transacci&#243;n: C&#243;mo afectan las transacciones a las actualizaciones (ODBC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las actualizaciones del [origen de datos](../../data/odbc/data-source-odbc.md) se administran durante las transacciones mediante el uso de un búfer de edición \(el mismo método que el usado fuera de las transacciones\).  Los miembros de datos de campo de un conjunto de registros actúan en conjunto como un búfer de edición que contiene el registro actual, del cual el conjunto de registros crea una copia de seguridad temporal durante una operación `AddNew` o **Edit**.  Durante una operación **Delete**, no se crea una copia de seguridad del registro actual en una transacción.  Para obtener más información sobre el búfer de edición y sobre cómo se almacena el registro actual durante las actualizaciones, vea [Conjunto de registros: Actualizar los registros \(ODBC\)](../../data/odbc/recordset-how-recordsets-update-records-odbc.md).  
  
> [!NOTE]
>  Si está implementada la obtención de filas masiva, no se puede llamar a `AddNew`, **Edit** o **Delete**.  En lugar de ello debe crear sus propias funciones para realizar actualizaciones del origen de datos.  Para obtener más información sobre la obtención masiva de filas, vea [Conjunto de registros: Obtener registros de forma masiva \(ODBC\)](../../data/odbc/recordset-fetching-records-in-bulk-odbc.md).  
  
 Durante las transacciones se pueden confirmar o revertir las operaciones `AddNew`, **Edit** y **Delete**.  Los efectos de **CommitTrans** y **Rollback** pueden hacer que no se restaure el registro actual en el búfer de edición.  Para asegurarse de que se restaura correctamente el registro actual, es importante comprender cómo actúan las funciones miembro **CommitTrans** y **Rollback** de `CDatabase` con las funciones de actualización de `CRecordset`.  
  
##  <a name="_core_how_committrans_affects_updates"></a> Cómo afecta CommitTrans a las actualizaciones  
 La tabla siguiente explica los efectos de **CommitTrans** en las transacciones.  
  
### Cómo afecta CommitTrans a las actualizaciones  
  
|Operación|Estado del origen de datos|  
|---------------|--------------------------------|  
|`AddNew` y **Update**, después **CommitTrans**|Se agrega un nuevo registro al origen de datos.|  
|`AddNew` \(sin **Update**\), después **CommitTrans**|Se pierde el nuevo registro.  No se agrega el registro al origen de datos.|  
|**Edit** y **Update**, después **CommitTrans**|Se confirman las modificaciones en el origen de datos.|  
|**Edit** \(sin **Update**\), después **CommitTrans**|Se pierden los campos en el registro.  El registro permanece sin cambios en el origen de datos.|  
|**Delete** y después **CommitTrans**|Se eliminan los registros del origen de datos.|  
  
##  <a name="_core_how_rollback_affects_updates"></a> Cómo afecta Rollback a las transacciones  
 La tabla siguiente explica los efectos de **Rollback** en las transacciones.  
  
### Cómo afecta Rollback a las transacciones  
  
|Operación|Estado del registro actual|Adicionalmente, haga lo siguiente|Estado del origen de datos|  
|---------------|--------------------------------|---------------------------------------|--------------------------------|  
|`AddNew` y **Update**, después **Rollback**|Se almacena temporalmente el contenido del registro actual para dejar espacio al nuevo registro.  Éste se agrega al búfer de edición.  Después de llamar a **Update**, se restaura el registro actual en el búfer de edición.||La adición al origen de datos realizada por **Update** se anula.|  
|`AddNew` \(sin **Update**\), después **Rollback**|Se almacena temporalmente el contenido del registro actual para dejar espacio al nuevo registro.  El búfer de edición contiene el nuevo registro.|Llame de nuevo a `AddNew` para restaurar el búfer de edición en un registro nuevo y vacío.  O bien, llame a **Move**\(0\) para restaurar los valores antiguos en el búfer de edición.|Ya que no se llamó a **Update**, no hubo cambios en el origen de datos.|  
|**Edit** y **Update**, después **Rollback**|Se almacena temporalmente una versión no modificada del registro actual.  Los campos tienen lugar en el contenido del búfer de edición.  Después de llamar a **Update**, la versión no modificada del registro continúa almacenada temporalmente.|*Conjunto de registros dinámico*: desplácese fuera del registro actual y después otra vez al mismo para restaurar la versión no modificada del registro en el búfer de edición.<br /><br /> *Instantánea*: llame a **Requery** para actualizar el conjunto de registros a partir del origen de datos.|Se anulan los campos realizados por **Update** en el origen de datos.|  
|**Edit** \(sin **Update**\), después **Rollback**|Se almacena temporalmente una versión no modificada del registro actual.  Los campos tienen lugar en el contenido del búfer de edición.|Llame de nuevo a **Edit** para restaurar la versión no modificada del registro en el búfer de edición.|Ya que no se llamó a **Update**, no hubo cambios en el origen de datos.|  
|**Delete** y después **Rollback**|Se elimina el contenido del registro actual.|Llame a **Requery** para restaurar el contenido del registro actual a partir del origen de datos.|Se anula la eliminación de datos del origen de datos.|  
  
## Vea también  
 [Transacción \(ODBC\)](../../data/odbc/transaction-odbc.md)   
 [Transacción \(ODBC\)](../../data/odbc/transaction-odbc.md)   
 [Transacción: Realizar una transacción en un conjunto de registros \(ODBC\)](../../data/odbc/transaction-performing-a-transaction-in-a-recordset-odbc.md)   
 [CDatabase Class](../../mfc/reference/cdatabase-class.md)   
 [CRecordset Class](../../mfc/reference/crecordset-class.md)