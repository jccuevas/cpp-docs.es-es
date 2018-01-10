---
title: "Determinar qué tipo de descriptor de acceso que se utilizan | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- rowsets [C++], data types
- accessors [C++], types
ms.assetid: 22483dd2-f4e0-4dcb-8e4d-cd43a9c1a3db
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: cb2e18c8b0c5ab110b9818e46e7fc68c08656274
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="determining-which-type-of-accessor-to-use"></a>Determinar qué tipo de descriptor de acceso se debe utilizar
Puede determinar los tipos de datos en un conjunto de filas en tiempo de compilación o en tiempo de ejecución.  
  
 Si necesita determinar los tipos de datos en tiempo de compilación, use un descriptor de acceso estático (como `CAccessor`). Puede determinar los tipos de datos manualmente o mediante el Asistente para consumidores OLE DB ATL.  
  
 Si necesita determinar los tipos de datos en tiempo de ejecución, use un dinámico (`CDynamicAccessor` o sus elementos secundarios) o descriptor de acceso manual (`CManualAccessor`). En estos casos, puede llamar a `GetColumnInfo` en el conjunto de filas para devolver la información de enlace de columna, desde el que se pueden determinar los tipos.  
  
 En la tabla siguiente se enumera los tipos de descriptores de acceso que se proporcionan en las plantillas de consumidor. Cada descriptor de acceso tiene ventajas y desventajas. Dependiendo de su situación, un tipo de descriptor de acceso debe adaptarse a sus necesidades.  
  
|Clase de descriptor de acceso|Enlaces|Parámetro|Comentario|  
|--------------------|-------------|---------------|-------------|  
|`CAccessor`|Cree un registro de usuario con `COLUMN_ENTRY` macros. Las macros de enlazan a un miembro de datos de ese registro en el descriptor de acceso. Cuando se crea el conjunto de filas, las columnas no pueden ser independientes.|Sí, mediante el uso de un **PARAM_MAP** entrada de macro. Una vez enlazado, parámetros no pueden ser independientes.|Descriptor de acceso más rápido debido a una cantidad pequeña de código.|  
|`CDynamicAccessor`|Automático.|No.|Resulta útil si no conoce el tipo de datos en un conjunto de filas.|  
|`CDynamicParameterAccessor`|Automática, pero puede ser [se reemplaza](../../data/oledb/overriding-a-dynamic-accessor.md).|Sí, si el proveedor admite `ICommandWithParameters`. Parámetros enlazados automáticamente.|Más lento que `CDynamicAccessor` pero útil para llamar a procedimientos almacenados genéricos.|  
|**CDynamicStringAccessor [A, W]**|Automático.|No.|Recupera los datos que se tiene acceso desde el almacén de datos como datos de cadena.|  
|`CManualAccessor`|Usar manual `AddBindEntry`.|Manualmente mediante `AddParameterEntry`.|Muy rápido; parámetros y columnas de enlazan una sola vez. Determinar el tipo de datos que se va a usar. (Consulte [DBVIEWER](http://msdn.microsoft.com/en-us/07620f99-c347-4d09-9ebc-2459e8049832) ejemplo para obtener un ejemplo.) Requiere más código que `CDynamicAccessor` o `CAccessor`. Es como llamar a OLE DB directamente.|  
|`CXMLAccessor`|Automático.|No.|Recupera los datos que se tiene acceso desde el almacén de datos como datos de cadena y formatos de datos etiquetado como XML.|  
  
## <a name="see-also"></a>Vea también  
 [Usar descriptores de acceso](../../data/oledb/using-accessors.md)