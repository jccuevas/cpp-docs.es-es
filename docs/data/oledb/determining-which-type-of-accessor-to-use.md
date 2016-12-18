---
title: "Determinar qu&#233; tipo de descriptor de acceso se debe utilizar | Microsoft Docs"
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
  - "descriptores de acceso [C++], tipos"
  - "conjuntos de filas [C++], tipos de datos"
ms.assetid: 22483dd2-f4e0-4dcb-8e4d-cd43a9c1a3db
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Determinar qu&#233; tipo de descriptor de acceso se debe utilizar
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Se puede determinar los tipos de datos de un conjunto de filas en tiempo de compilación o en tiempo de ejecución.  
  
 Si necesita determinar los tipos de datos en tiempo de compilación, use un descriptor de acceso estático, como `CAccessor`.  Es posible determinar los tipos de datos manualmente o mediante el Asistente para consumidores OLE DB ATL.  
  
 Si necesita determinar los tipos de datos en tiempo de ejecución, use un descriptor de acceso dinámico \(`CDynamicAccessor` o sus objetos derivados\) o manual \(`CManualAccessor`\).  En estos casos, se puede llamar a `GetColumnInfo` en el conjunto de filas para devolver la información de enlaces de columna, con la que se pueden determinar los tipos.  
  
 La tabla siguiente enumera los tipos de descriptor de acceso incluidos en las plantillas de consumidores.  Cada descriptor de acceso tiene sus ventajas y desventajas.  Según cuál sea su situación, un descriptor de acceso servirá para atender sus necesidades.  
  
|Clase de descriptores de acceso|Enlaces|Parámetro|Comment|  
|-------------------------------------|-------------|---------------|-------------|  
|`CAccessor`|Cree un registro de usuario con macros `COLUMN_ENTRY`.  Las macros enlazan un miembro de datos de ese registro con el descriptor de acceso.  Una vez creado el conjunto de filas, no se pueden desenlazar las columnas.|Sí, mediante una entrada de macro **PARAM\_MAP**.  Una vez enlazados, no se pueden desenlazar los parámetros.|El descriptor de acceso más rápido por su pequeño volumen de código.|  
|`CDynamicAccessor`|Automático.|No.|Útil si no se conoce el tipo de datos de un conjunto de filas.|  
|`CDynamicParameterAccessor`|Automático, pero se puede [reemplazar](../../data/oledb/overriding-a-dynamic-accessor.md).|Sí, si el proveedor admite `ICommandWithParameters`.  Parámetros enlazados automáticamente.|Más lento que `CDynamicAccessor`, pero útil para llamar a procedimientos almacenados genéricos.|  
|**CDynamicStringAccessor\[A,W\]**|Automático.|No.|Recupera datos a los se tiene acceso del almacén de datos como datos de cadena.|  
|`CManualAccessor`|Manual, mediante `AddBindEntry`.|Manual, mediante `AddParameterEntry`.|Muy rápido; los parámetros y columnas sólo se enlazan una vez.  El programador determina el tipo de datos que usará. Vea el ejemplo [DBVIEWER](http://msdn.microsoft.com/es-es/07620f99-c347-4d09-9ebc-2459e8049832). Requiere más código que `CDynamicAccessor` o `CAccessor`.  Es como llamar a OLE DB directamente.|  
|`CXMLAccessor`|Automático.|No.|Recupera datos a los que se tiene acceso desde el almacén de datos como datos de cadena y los formatea como texto XML.|  
  
## Vea también  
 [Utilizar descriptores de acceso](../../data/oledb/using-accessors.md)