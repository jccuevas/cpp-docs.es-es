---
title: "CComObjectNoLock Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CComObjectNoLock"
  - "ATL::CComObjectNoLock"
  - "ATL.CComObjectNoLock<Base>"
  - "CComObjectNoLock"
  - "ATL::CComObjectNoLock<Base>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComObjectNoLock class"
ms.assetid: 288c6506-7da8-4127-8d58-7f4bd779539a
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CComObjectNoLock Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase implementa **IUnknown** para un objeto nonaggregated, pero no incrementa el recuento de bloqueo del módulo en el constructor.  
  
## Sintaxis  
  
```  
  
      template<  
   class Base   
>  
class CComObjectNoLock :  
   public Base  
```  
  
#### Parámetros  
 `Base`  
 La clase, derivadas de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) o de [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), además de cualquier otra interfaz desea admitir en el objeto.  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComObjectNoLock::CComObjectNoLock](../Topic/CComObjectNoLock::CComObjectNoLock.md)|Constructor.|  
|[CComObjectNoLock::~CComObjectNoLock](../Topic/CComObjectNoLock::~CComObjectNoLock.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComObjectNoLock::AddRef](../Topic/CComObjectNoLock::AddRef.md)|Incrementa el recuento de referencias del objeto.|  
|[CComObjectNoLock::QueryInterface](../Topic/CComObjectNoLock::QueryInterface.md)|Devuelve un puntero a la interfaz solicitada.|  
|[CComObjectNoLock::Release](../Topic/CComObjectNoLock::Release.md)|Decrementa en el objeto.|  
  
## Comentarios  
 `CComObjectNoLock` es similar a [CComObject](../../atl/reference/ccomobject-class.md) en que implementa [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) para un objeto nonaggregated; sin embargo, `CComObjectNoLock` no incrementa el recuento de bloqueo del módulo en el constructor.  
  
 ATL utiliza `CComObjectNoLock` internamente para los generadores de clases.  No utilizará normalmente esta clase directamente.  
  
## Jerarquía de herencia  
 `Base`  
  
 `CComObjectNoLock`  
  
## Requisitos  
 **encabezado:** atlcom.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)