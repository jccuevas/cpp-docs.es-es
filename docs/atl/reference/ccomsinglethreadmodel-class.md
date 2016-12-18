---
title: "CComSingleThreadModel Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CComSingleThreadModel"
  - "CComSingleThreadModel"
  - "ATL::CComSingleThreadModel"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComSingleThreadModel class"
  - "single-threaded applications"
  - "single-threaded applications, ATL"
ms.assetid: e5dc30c7-405a-4ba4-8ae9-51937243fce8
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComSingleThreadModel Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos para aumentar y disminuir el valor de una variable.  
  
## Sintaxis  
  
```  
  
class CComSingleThreadModel  
  
```  
  
## Members  
  
### Typedefs públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComSingleThreadModel::AutoCriticalSection](../Topic/CComSingleThreadModel::AutoCriticalSection.md)|Hace referencia a la clase [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).|  
|[CComSingleThreadModel::CriticalSection](../Topic/CComSingleThreadModel::CriticalSection.md)|Hace referencia a la clase `CComFakeCriticalSection`.|  
|[CComSingleThreadModel::ThreadModelNoCS](../Topic/CComSingleThreadModel::ThreadModelNoCS.md)|hace referencia `CComSingleThreadModel`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComSingleThreadModel::Decrement](../Topic/CComSingleThreadModel::Decrement.md)|disminuye el valor de la variable especificada.  Esta implementación no es seguro para subprocesos.|  
|[CComSingleThreadModel::Increment](../Topic/CComSingleThreadModel::Increment.md)|incrementa el valor de la variable especificada.  Esta implementación no es seguro para subprocesos.|  
  
## Comentarios  
 `CComSingleThreadModel` proporciona métodos para aumentar y disminuir el valor de una variable.  A diferencia de [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) y de [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md), estos métodos no son seguros para subprocesos.  
  
 Normalmente, se utiliza `CComSingleThreadModel` a uno de los dos nombres de `typedef` , [CComObjectThreadModel](../Topic/CComObjectThreadModel.md) o [CComGlobalsThreadModel](../Topic/CComGlobalsThreadModel.md).  La clase a la que hace referencia cada `typedef` depende del modelo de subprocesos utilizado, como se muestra en la tabla siguiente:  
  
|definición de tipos|Modelo de subproceso único|modelo de subprocesos controlados|modelo de subprocesos libre|  
|-------------------------|--------------------------------|---------------------------------------|---------------------------------|  
|`CComObjectThreadModel`|S|S|M|  
|`CComGlobalsThreadModel`|S|M|M|  
  
 Breakpoint`CComSingleThreadModel`; M\=`CComMultiThreadModel`  
  
 `CComSingleThreadModel` propio define tres nombres de `typedef` .  referencias `CComSingleThreadModel`de`ThreadModelNoCS` .  `AutoCriticalSection` y `CriticalSection` hacen referencia a la clase [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md), que proporciona métodos vacíos asociado a obtener y liberar de propiedad de una sección crítica.  
  
## Requisitos  
 **encabezado:** atlbase.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)