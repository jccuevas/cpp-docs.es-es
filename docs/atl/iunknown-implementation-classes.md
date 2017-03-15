---
title: "IUnknown Implementation Classes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.atl.Iunknown"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IUnknown implementation classes"
ms.assetid: 47b69bb5-69d8-4a9c-84a8-329bdde2bb3f
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# IUnknown Implementation Classes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las clases siguientes implementan **IUnknown** y métodos relacionados:  
  
-   [CComObjectRootEx](../atl/reference/ccomobjectrootex-class.md) administra el recuento de referencias para los objetos agregados y nonaggregated.  Permite especificar un modelo de subprocesos.  
  
-   [CComObjectRoot](../atl/reference/ccomobjectroot-class.md) administra el recuento de referencias para los objetos agregados y nonaggregated.  Utiliza el modelo de subprocesos predeterminado del servidor.  
  
-   Herramientas **IUnknown** de[CComAggObject](../atl/reference/ccomaggobject-class.md) para un objeto agregado.  
  
-   Herramientas **IUnknown** de[CComObject](../atl/reference/ccomobject-class.md) para un objeto nonaggregated.  
  
-   [CComPolyObject](../atl/reference/ccompolyobject-class.md) implementa **IUnknown** para los objetos agregados y nonaggregated.  Mediante `CComPolyObject` evita tener `CComAggObject` y `CComObject` en el módulo.  Los únicos controladores de objeto de `CComPolyObject` agregados y nonaggregated los casos.  
  
-   Herramientas **IUnknown** de[CComObjectNoLock](../atl/reference/ccomobjectnolock-class.md) para un objeto nonaggregated, sin modificar el recuento de bloqueo del módulo.  
  
-   Herramientas **IUnknown** de[CComTearOffObject](../atl/reference/ccomtearoffobject-class.md) para una interfaz de rasgón.  
  
-   Ayudas de[CComCachedTearOffObject](../atl/reference/ccomcachedtearoffobject-class.md) que **IUnknown** para “almacenados en caché” rasgan la interfaz.  
  
-   Herramientas **IUnknown** de[CComContainedObject](../atl/reference/ccomcontainedobject-class.md) para el objeto interno de una agregación o interfaz de rasgón.  
  
-   [CComObjectGlobal](../atl/reference/ccomobjectglobal-class.md) administra un recuento de referencias en el módulo para proteger el objeto no se eliminará.  
  
-   [CComObjectStack](../atl/reference/ccomobjectstack-class.md) crea un objeto COM temporal, mediante una implementación básica de **IUnknown**.  
  
## artículos relacionados  
 [Fundamentos de objetos COM de ATL](../atl/fundamentals-of-atl-com-objects.md)  
  
## Vea también  
 [Class Overview](../atl/atl-class-overview.md)   
 [Aggregation and Class Factory Macros](../atl/reference/aggregation-and-class-factory-macros.md)   
 [COM Map Macros](../atl/reference/com-map-macros.md)   
 [COM Map Global Functions](../atl/reference/com-map-global-functions.md)