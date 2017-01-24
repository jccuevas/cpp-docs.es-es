---
title: "CComGITPtr Class | Microsoft Docs"
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
  - "ATL::CComGITPtr<T>"
  - "CComGITPtr"
  - "ATL.CComGITPtr"
  - "ATL.CComGITPtr<T>"
  - "ATL::CComGITPtr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComGITPtr class"
ms.assetid: af895acb-525a-4555-bb67-b241b7df515b
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComGITPtr Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos para tratar de punteros de interfaz y de la tabla global de la interfaz \(GIT\).  
  
## Sintaxis  
  
```  
  
      template <  
   class T   
>  
class CComGITPtr  
```  
  
#### Parámetros  
 `T`  
 El tipo de puntero de interfaz que se almacene en el GIT.  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComGITPtr::CComGITPtr](../Topic/CComGITPtr::CComGITPtr.md)|el constructor.|  
|[CComGITPtr::~CComGITPtr](../Topic/CComGITPtr::~CComGITPtr.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComGITPtr::Attach](../Topic/CComGITPtr::Attach.md)|Llame a este método para registrar el puntero de interfaz en la tabla global de la interfaz \(GIT\).|  
|[CComGITPtr::CopyTo](../Topic/CComGITPtr::CopyTo.md)|Llame a este método para copiar la interfaz de la tabla global de interfaz \(GIT\) al puntero pasado.|  
|[CComGITPtr::Detach](../Topic/CComGITPtr::Detach.md)|Llame a este método para desasociar la interfaz del objeto de `CComGITPtr` .|  
|[CComGITPtr::GetCookie](../Topic/CComGITPtr::GetCookie.md)|Llame a este método para devolver la cookie del objeto de `CComGITPtr` .|  
|[CComGITPtr::Revoke](../Topic/CComGITPtr::Revoke.md)|Llame a este método para quitar la interfaz de la tabla global de la interfaz \(GIT\).|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComGITPtr::operator DWORD](../Topic/CComGITPtr::operator%20DWORD.md)|Devuelve la cookie del objeto de `CComGITPtr` .|  
|[CComGITPtr::operator \=](../Topic/CComGITPtr::operator%20=.md)|Operador de asignación.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComGITPtr::m\_dwCookie](../Topic/CComGITPtr::m_dwCookie.md)|La cookie.|  
  
## Comentarios  
 Los objetos que agregan el contador y la necesidad roscados libres de utilizar los punteros de interfaz obtenidos de otros objetos deben tomar medidas adicionales para garantizar que las interfaces correctamente se calculen las referencias.  Esto implica normalmente el almacenamiento de punteros de interfaz en el GIT y el obtener del puntero de GIT cada vez que se utiliza.  La clase `CComGITPtr` se proporciona para ayudarle punteros de la interfaz de uso almacenados en el GIT.  
  
> [!NOTE]
>  La utilidad global de la tabla de la interfaz sólo está disponible en Windows 95 con la versión 1,1 de DCOM y después, Windows 98, Windows NT 4.0 con Service Pack 3 y versiones posteriores, y Windows 2000.  
  
## Requisitos  
 **encabezado:** atlbase.h  
  
## Vea también  
 [Contador de referencias de subprocesamiento libre](../../atl/atl-and-the-free-threaded-marshaler.md)   
 [Accessing Interfaces Across Apartments](http://msdn.microsoft.com/library/windows/desktop/ms682353)   
 [When to Use the Global Interface Table](http://msdn.microsoft.com/library/windows/desktop/ms693729)   
 [Class Overview](../../atl/atl-class-overview.md)