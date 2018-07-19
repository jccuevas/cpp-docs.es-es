---
title: Utilizar descriptores de acceso manuales | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- command handling, OLE DB Templates
- manual accessors
- accessors [C++], manual
ms.assetid: 29f00a89-0240-482b-8413-4120b9644672
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ee82a780690c6d5eba7b30debdc592a26ef2cbcc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33105909"
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