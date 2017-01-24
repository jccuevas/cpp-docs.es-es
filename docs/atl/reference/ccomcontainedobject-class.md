---
title: "CComContainedObject Class | Microsoft Docs"
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
  - "CComContainedObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "aggregate objects [C++], en ATL"
  - "aggregation [C++], objetos ATL"
  - "CComContainedObject class"
ms.assetid: e8616b41-c200-47b8-bf2c-fb9f713ebdad
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComContainedObject Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase implementa [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) delegando a **IUnknown**del objeto propietario.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
      template<  
class Base   
>  
class CComContainedObject :  
public Base  
```  
  
#### Parámetros  
 `Base`  
 La clase, derivadas de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) o de [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md).  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComContainedObject::CComContainedObject](../Topic/CComContainedObject::CComContainedObject.md)|el constructor.  Inicializa el puntero de miembro a `IUnknown`del objeto propietario.|  
|[CComContainedObject::~CComContainedObject](../Topic/CComContainedObject::~CComContainedObject.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComContainedObject::AddRef](../Topic/CComContainedObject::AddRef.md)|Incrementa el recuento de referencias en el objeto propietario.|  
|[CComContainedObject::GetControllingUnknown](../Topic/CComContainedObject::GetControllingUnknown.md)|Recupera `IUnknown`del objeto propietario.|  
|[CComContainedObject::QueryInterface](../Topic/CComContainedObject::QueryInterface.md)|Recupera un puntero a la interfaz solicitada en el objeto propietario.|  
|[CComContainedObject::Release](../Topic/CComContainedObject::Release.md)|Decrementa en el objeto propietario.|  
  
## Comentarios  
 ATL utiliza `CComContainedObject` en las clases [CComAggObject](../../atl/reference/ccomaggobject-class.md), [CComPolyObject](../../atl/reference/ccompolyobject-class.md), y [CComCachedTearOffObject](../../atl/reference/ccomcachedtearoffobject-class.md).  `CComContainedObject` implementa [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) delegando a **IUnknown**del objeto propietario.  \(El propietario de El es el objeto externo de una agregación, o el objeto para el que una interfaz de rasgón se está creando.\) `CComContainedObject` llama `OuterQueryInterface`, `OuterAddRef`, y `OuterRelease`de los entity\_CComObjectRootEx, heredado todo con `Base`.  
  
## Jerarquía de herencia  
 `Base`  
  
 `CComContainedObject`  
  
## Requisitos  
 **encabezado:** atlcom.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)