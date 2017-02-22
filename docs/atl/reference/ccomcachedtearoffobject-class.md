---
title: "CComCachedTearOffObject Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL::CComCachedTearOffObject"
  - "ATL.CComCachedTearOffObject"
  - "ATL.CComCachedTearOffObject<contained>"
  - "CComCachedTearOffObject"
  - "ATL::CComCachedTearOffObject<contained>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "caché, ATL cached tear-off objects"
  - "CComCachedTearOffObject class"
ms.assetid: ae19507d-a1de-4dbc-a988-da9f75a50c95
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CComCachedTearOffObject Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase implementa [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) para una interfaz de rasgón.  
  
## Sintaxis  
  
```  
  
      template <  
   class contained  
>  
class CComCachedTearOffObject : public IUnknown,  
   public CComObjectRootEx< contained::_ThreadModel::ThreadModelNoCS >  
```  
  
#### Parámetros  
 `contained`  
 La clase de rasgón, derivadas de `CComTearOffObjectBase` e interfaces desea que el objeto de rasgón admitir.  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComCachedTearOffObject::CComCachedTearOffObject](../Topic/CComCachedTearOffObject::CComCachedTearOffObject.md)|el constructor.|  
|[CComCachedTearOffObject::~CComCachedTearOffObject](../Topic/CComCachedTearOffObject::~CComCachedTearOffObject.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComCachedTearOffObject::AddRef](../Topic/CComCachedTearOffObject::AddRef.md)|Incrementa el recuento de referencias de un objeto de `CComCachedTearOffObject` .|  
|[CComCachedTearOffObject::FinalConstruct](../Topic/CComCachedTearOffObject::FinalConstruct.md)|Llama a `m_contained::FinalConstruct` \(método de las clases de rasgón\).|  
|[CComCachedTearOffObject::FinalRelease](../Topic/CComCachedTearOffObject::FinalRelease.md)|Llama a `m_contained::FinalRelease` \(método de las clases de rasgón\).|  
|[CComCachedTearOffObject::QueryInterface](../Topic/CComCachedTearOffObject::QueryInterface.md)|Devuelve un puntero a `IUnknown` del objeto de `CComCachedTearOffObject` , o a la interfaz solicitada en la clase de rasgón \(la clase `contained`\).|  
|[CComCachedTearOffObject::Release](../Topic/CComCachedTearOffObject::Release.md)|Decrementa para un objeto de `CComCachedTearOffObject` y destruir si el recuento de referencias es 0.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComCachedTearOffObject::m\_contained](../Topic/CComCachedTearOffObject::m_contained.md)|Un objeto de `CComContainedObject` derivado de la clase de rasgón \(la clase `contained`\).|  
  
## Comentarios  
 `CComCachedTearOffObject` implementa [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) para una interfaz de rasgón.  Esta clase diferencia de `CComTearOffObject` en que `CComCachedTearOffObject` tiene su propio **IUnknown**, distinto de **IUnknown** del objeto owner \(el propietario es el objeto para el que se crea el rasgón\).  `CComCachedTearOffObject` mantiene su propio número de referencias del **IUnknown** y se elimina una vez que el recuento de referencias es cero.  Sin embargo, si ve para cualquiera del rasgue interfaces, el recuento de referencias del propietario que **IUnknown** de objeto se incrementa.  
  
 Si el objeto de `CComCachedTearOffObject` que implementa el rasgón se crea instancias todavía, y la interfaz de rasgón se consulta para otra vez, se reutiliza el mismo objeto de `CComCachedTearOffObject` .  En cambio, si una interfaz de rasgón implementada por `CComTearOffObject` se consulta de nuevo con a través del objeto owner, otro `CComTearOffObject` se con instancias.  
  
 La clase propietaria debe implementar `FinalRelease` y llamar a **Liberar** en **IUnknown** almacenado en caché para `CComCachedTearOffObject`, que disminuirán el recuento de referencias.  Esto hará `FinalRelease` de los entity\_CComCachedTearOffObject que se denomine y eliminará el rasgón.  
  
## Jerarquía de herencia  
 `CComObjectRootBase`  
  
 [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)  
  
 `IUnknown`  
  
 `CComCachedTearOffObject`  
  
## Requisitos  
 **encabezado:** atlcom.h  
  
## Vea también  
 [CComTearOffObject Class](../../atl/reference/ccomtearoffobject-class.md)   
 [CComObjectRootEx Class](../../atl/reference/ccomobjectrootex-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)