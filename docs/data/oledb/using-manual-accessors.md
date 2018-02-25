---
title: Utilizar descriptores de acceso manuales | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- command handling, OLE DB Templates
- manual accessors
- accessors [C++], manual
ms.assetid: 29f00a89-0240-482b-8413-4120b9644672
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e7d6bd8f0228103e4899e6bc24f6d67af0f3fdb4
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="using-manual-accessors"></a>Utilizar descriptores de acceso manuales
Hay cuatro tareas a realizar al controlar un comando desconocido:  
  
-   Determinar los parámetros  
  
-   Ejecute el comando  
  
-   Determinar las columnas de salida  
  
-   Si hay varios conjuntos de filas devuelto  
  
 Para hacer esto con las plantillas de consumidor OLE DB, use la `CManualAccessor` clase y siga estos pasos:  
  
1.  Abra un `CCommand` objeto con `CManualAccessor` como un parámetro de plantilla.  
  
    ```  
    CCommand<CManualAccessor, CRowset, CMultipleResults> rs;  
    ```  
  
2.  Consultar la sesión para la **IDBSchemaRowset** interfaz y el conjunto de filas de parámetros de procedimiento. Si el **IDBSchemaRowset** interfaz no está disponible, consultar la `ICommandWithParameters` interfaz. Llame a `GetParameterInfo` para obtener información. Si ninguna de estas interfaces está disponible, puede asumir que hay ningún parámetro.  
  
3.  Para cada parámetro, llame a `AddParameterEntry` para agregar los parámetros y establecerlos.  
  
4.  Abra el conjunto de filas, pero establece el parámetro de enlace en **false**.  
  
5.  Llame a `GetColumnInfo` para recuperar las columnas de salida. Use `AddBindEntry` para agregar la columna de salida para el enlace.  
  
6.  Llame a `GetNextResult` para determinar si hay más conjuntos de filas. Repita los pasos del 2 al 5.  
  
 Para obtener un ejemplo de un descriptor de acceso manual, vea **CDBListView:: CallProcedure** en el [DBVIEWER](http://msdn.microsoft.com/en-us/07620f99-c347-4d09-9ebc-2459e8049832) ejemplo.  
  
## <a name="see-also"></a>Vea también  
 [Usar descriptores de acceso](../../data/oledb/using-accessors.md)