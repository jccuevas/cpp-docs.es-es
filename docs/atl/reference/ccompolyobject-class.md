---
title: "CComPolyObject Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CComPolyObject"
  - "ATL.CComPolyObject<contained>"
  - "ATL::CComPolyObject"
  - "ATL::CComPolyObject<contained>"
  - "ATL.CComPolyObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aggregate objects [C++], en ATL"
  - "aggregation [C++], objetos ATL"
  - "CComPolyObject class"
ms.assetid: eaf67c18-e855-48ca-9b15-f1df3106121b
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CComPolyObject Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

esta clase implementa **IUnknown** para un objeto agregado o nonaggregated.  
  
## Sintaxis  
  
```  
  
      template<  
   class contained   
>  
class CComPolyObject : public IUnknown, public CComObjectRootEx  
   < contained::_ThreadModel::ThreadModelNoCS >  
```  
  
#### Parámetros  
 `contained`  
 La clase, derivadas de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) o de [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), además de cualquier otra interfaz desea admitir en el objeto.  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComPolyObject::CComPolyObject](../Topic/CComPolyObject::CComPolyObject.md)|el constructor.|  
|[CComPolyObject::~CComPolyObject](../Topic/CComPolyObject::~CComPolyObject.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComPolyObject::AddRef](../Topic/CComPolyObject::AddRef.md)|Incrementa el recuento de referencias del objeto.|  
|[CComPolyObject::CreateInstance](../Topic/CComPolyObject::CreateInstance.md)|\(Estático\) Allow permite crear un nuevo objeto de **CComPolyObject\<** `contained` **\>** sin la sobrecarga de [CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615).|  
|[CComPolyObject::FinalConstruct](../Topic/CComPolyObject::FinalConstruct.md)|Realiza la inicialización final de `m_contained`.|  
|[CComPolyObject::FinalRelease](../Topic/CComPolyObject::FinalRelease.md)|Realiza la destrucción final de `m_contained`.|  
|[CComPolyObject::QueryInterface](../Topic/CComPolyObject::QueryInterface.md)|recupera un puntero a la interfaz solicitada.|  
|[CComPolyObject::Release](../Topic/CComPolyObject::Release.md)|Disminuye el recuento de referencias del objeto.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComPolyObject::m\_contained](../Topic/CComPolyObject::m_contained.md)|Llamadas de **IUnknown** de delegados a desconocido externo si se agrega el objeto o a **IUnknown** de objeto si el objeto no se agrega.|  
  
## Comentarios  
 `CComPolyObject` implementa [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) para un objeto agregado o nonaggregated.  
  
 Cuando una instancia de `CComPolyObject` se crea, el valor desconocido externo se comprueba.  si es **NULL**, **IUnknown** se implementa para un objeto nonaggregated.  Si el hecho exterior no se **NULL**, **IUnknown** se implementa para un objeto agregado.  
  
 La ventaja de utilizar `CComPolyObject` es que se evita tener [CComAggObject](../../atl/reference/ccomaggobject-class.md) y [CComObject](../../atl/reference/ccomobject-class.md) en el módulo para controlar los casos agregado y nonaggregated.  Los controladores de objeto de `CComPolyObject` ambos casos.  Esto significa que sólo una copia de vtable y una copia de las funciones existen en el módulo.  Si el vtable es grande, esto puede reducir considerablemente el tamaño del módulo.  Sin embargo, si el vtable es pequeño, mediante `CComPolyObject` pueden producir un tamaño ligeramente mayor de módulo porque no se optimiza para un objeto agregado o nonaggregated, al igual que `CComAggObject` y `CComObject`.  
  
 Si la macro de `DECLARE_POLY_AGGREGATABLE` se especifica en la definición de clase del objeto, `CComPolyObject` se utilizará para crear el objeto.  `DECLARE_POLY_AGGREGATABLE` automáticamente se declarado si utiliza el asistente para proyectos ATL para crear un control completo o un control de Internet Explorer.  
  
 Si se agrega, el objeto de `CComPolyObject` tiene su propio **IUnknown**, distinto de **IUnknown**del objeto externo, y mantiene su propio número de referencias.  `CComPolyObject` utiliza [CComContainedObject](../../atl/reference/ccomcontainedobject-class.md) para delegar el desconocido externo.  
  
 Para obtener más información sobre la agregación, vea el artículo [Fundamentos de objetos COM de ATL](../../atl/fundamentals-of-atl-com-objects.md).  
  
## Jerarquía de herencia  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IUnknown`  
  
 `CComPolyObject`  
  
## Requisitos  
 **encabezado:** atlcom.h  
  
## Vea también  
 [CComObjectRootEx Class](../../atl/reference/ccomobjectrootex-class.md)   
 [DECLARE\_POLY\_AGGREGATABLE](../Topic/DECLARE_POLY_AGGREGATABLE.md)   
 [Class Overview](../../atl/atl-class-overview.md)