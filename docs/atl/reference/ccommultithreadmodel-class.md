---
title: "CComMultiThreadModel Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CComMultiThreadModel"
  - "ATL.CComMultiThreadModel"
  - "ATL::CComMultiThreadModel"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, multithreading"
  - "CComMultiThreadModel class"
  - "subprocesamiento [ATL]"
ms.assetid: db8f1662-2f7a-44b3-b341-ffbfb6e422a3
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CComMultiThreadModel Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`CComMultiThreadModel` proporciona métodos seguros para subprocesos para aumentar y disminuir el valor de una variable.  
  
## Sintaxis  
  
```  
  
class CComMultiThreadModel  
  
```  
  
## Members  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComMultiThreadModel::AutoCriticalSection](../Topic/CComMultiThreadModel::AutoCriticalSection.md)|Hace referencia a la clase [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md).|  
|[CComMultiThreadModel::CriticalSection](../Topic/CComMultiThreadModel::CriticalSection.md)|Hace referencia a la clase [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md).|  
|[CComMultiThreadModel::ThreadModelNoCS](../Topic/CComMultiThreadModel::ThreadModelNoCS.md)|Hace referencia a la clase [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComMultiThreadModel::Decrement](../Topic/CComMultiThreadModel::Decrement.md)|\(Estático\) disminuye el valor de la variable especificada de una manera segura para subprocesos.|  
|[CComMultiThreadModel::Increment](../Topic/CComMultiThreadModel::Increment.md)|\(Estático\) incrementa el valor de la variable especificada de una manera segura para subprocesos.|  
  
## Comentarios  
 Normalmente, se utiliza `CComMultiThreadModel` a uno de los dos nombres de `typedef` , [CComObjectThreadModel](../Topic/CComObjectThreadModel.md) o [CComGlobalsThreadModel](../Topic/CComGlobalsThreadModel.md).  La clase a la que hace referencia cada `typedef` depende del modelo de subprocesos utilizado, como se muestra en la tabla siguiente:  
  
|definición de tipos|subproceso único|subproceso controlado|subprocesamiento libre|  
|-------------------------|----------------------|---------------------------|----------------------------|  
|`CComObjectThreadModel`|S|S|M|  
|`CComGlobalsThreadModel`|S|M|M|  
  
 Breakpoint`CComSingleThreadModel`; M\=`CComMultiThreadModel`  
  
 `CComMultiThreadModel` propio define tres nombres de `typedef` .  `AutoCriticalSection` y clases de referencia de `CriticalSection` que proporcionan métodos para obtener y liberar la propiedad de una sección crítica.  clase [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)de las referencias de`ThreadModelNoCS` .  
  
## Requisitos  
 **encabezado:** atlbase.h  
  
## Vea también  
 [CComSingleThreadModel Class](../../atl/reference/ccomsinglethreadmodel-class.md)   
 [CComAutoCriticalSection Class](../../atl/reference/ccomautocriticalsection-class.md)   
 [CComCriticalSection Class](../../atl/reference/ccomcriticalsection-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)