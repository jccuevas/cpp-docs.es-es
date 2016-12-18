---
title: "CComObject Class | Microsoft Docs"
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
  - "ATL.CComObject<Base>"
  - "ATL::CComObject"
  - "ATL::CComObject<Base>"
  - "ATL.CComObject"
  - "CComObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComObject class"
ms.assetid: e2b6433b-6349-4749-b4bc-acbd7a22c8b0
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComObject Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

esta clase implementa **IUnknown** para un objeto nonaggregated.  
  
## Sintaxis  
  
```  
  
      template<  
   class Base   
>  
class CComObject :  
   public Base  
```  
  
#### Parámetros  
 `Base`  
 La clase, derivadas de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) o de [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), además de cualquier otra interfaz desea admitir en el objeto.  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComObject::CComObject](../Topic/CComObject::CComObject.md)|el constructor.|  
|[CComObject::~CComObject](../Topic/CComObject::~CComObject.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComObject::AddRef](../Topic/CComObject::AddRef.md)|Incrementa el recuento de referencias del objeto.|  
|[CComObject::CreateInstance](../Topic/CComObject::CreateInstance.md)|\(Estático\) crea un nuevo objeto de `CComObject` .|  
|[CComObject::QueryInterface](../Topic/CComObject::QueryInterface.md)|recupera un puntero a la interfaz solicitada.|  
|[CComObject::Release](../Topic/CComObject::Release.md)|Decrementa en el objeto.|  
  
## Comentarios  
 `CComObject` implementa [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) para un objeto nonaggregated.  Sin embargo, las llamadas a `QueryInterface`, a `AddRef`, y a **Liberar** se delegan en `CComObjectRootEx`.  
  
 Para obtener más información sobre cómo utilizar `CComObject`, vea el artículo [Fundamentos de objetos COM de ATL](../../atl/fundamentals-of-atl-com-objects.md).  
  
## Jerarquía de herencia  
 `Base`  
  
 `CComObject`  
  
## Requisitos  
 **encabezado:** atlcom.h  
  
## Vea también  
 [CComAggObject Class](../../atl/reference/ccomaggobject-class.md)   
 [CComPolyObject Class](../../atl/reference/ccompolyobject-class.md)   
 [DECLARE\_AGGREGATABLE](../Topic/DECLARE_AGGREGATABLE.md)   
 [DECLARE\_NOT\_AGGREGATABLE](../Topic/DECLARE_NOT_AGGREGATABLE.md)   
 [Class Overview](../../atl/atl-class-overview.md)