---
title: "CComAggObject Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CComAggObject<contained>"
  - "ATL.CComAggObject"
  - "ATL.CComAggObject<contained>"
  - "CComAggObject"
  - "ATL::CComAggObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aggregate objects [C++], en ATL"
  - "aggregation [C++], objetos ATL"
  - "CComAggObject class"
ms.assetid: 7aa90d69-d399-477b-880d-e2cdf0ef7881
caps.latest.revision: 29
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 32
---
# CComAggObject Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

esta clase implementa la interfaz de [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) para un objeto agregado.  por definición, un objeto agregado se contiene dentro de un objeto externo.  La clase de `CComAggObject` es similar a [CComObject Class](../../atl/reference/ccomobject-class.md), salvo que expone una interfaz que es accesible directamente a los clientes externos.  
  
## Sintaxis  
  
```  
  
      template<  
   class contained  
>  
class CComAggObject :  
   public IUnknown, public CComObjectRootEx  
   < contained::_ThreadModel::ThreadModelNoCS >  
```  
  
#### Parámetros  
 `contained`  
 La clase, derivadas de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) o de [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), además de cualquier otra interfaz desea admitir en el objeto.  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComAggObject::CComAggObject](../Topic/CComAggObject::CComAggObject.md)|el constructor.|  
|[CComAggObject::~CComAggObject](../Topic/CComAggObject::~CComAggObject.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComAggObject::AddRef](../Topic/CComAggObject::AddRef.md)|Incrementa el recuento de referencias en el objeto agregado.|  
|[CComAggObject::CreateInstance](../Topic/CComAggObject::CreateInstance.md)|Esta función estática permite crear un nuevo objeto de **CComAggObject\<** `contained` **\>** sin la sobrecarga de [CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615).|  
|[CComAggObject::FinalConstruct](../Topic/CComAggObject::FinalConstruct.md)|Realiza la inicialización final de `m_contained`.|  
|[CComAggObject::FinalRelease](../Topic/CComAggObject::FinalRelease.md)|Realiza la destrucción final de `m_contained`.|  
|[CComAggObject::QueryInterface](../Topic/CComAggObject::QueryInterface.md)|recupera un puntero a la interfaz solicitada.|  
|[CComAggObject::Release](../Topic/CComAggObject::Release.md)|Decrementa en el objeto agregado.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComAggObject::m\_contained](../Topic/CComAggObject::m_contained.md)|Llamadas de `IUnknown` de delegados a desconocido externo.|  
  
## Comentarios  
 `CComAggObject` implementa [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) para un objeto agregado.  `CComAggObject` tiene su propia interfaz de **IUnknown** , independiente de la interfaz de **IUnknown** del objeto externo, y mantiene su propio número de referencias.  
  
 Para obtener más información sobre la agregación, vea el artículo [Fundamentos de objetos COM de ATL](../../atl/fundamentals-of-atl-com-objects.md).  
  
## Jerarquía de herencia  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IUnknown`  
  
 `CComAggObject`  
  
## Requisitos  
 **encabezado:** atlcom.h  
  
## Vea también  
 [CComObject Class](../../atl/reference/ccomobject-class.md)   
 [CComPolyObject Class](../../atl/reference/ccompolyobject-class.md)   
 [DECLARE\_AGGREGATABLE](../Topic/DECLARE_AGGREGATABLE.md)   
 [DECLARE\_ONLY\_AGGREGATABLE](../Topic/DECLARE_ONLY_AGGREGATABLE.md)   
 [DECLARE\_NOT\_AGGREGATABLE](../Topic/DECLARE_NOT_AGGREGATABLE.md)   
 [Class Overview](../../atl/atl-class-overview.md)