---
title: "CComQIPtr Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CComQIPtr"
  - "ATL::CComQIPtr"
  - "CComQIPtr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComQIPtr class"
ms.assetid: 969cacb5-05b6-4af4-b683-24911d70242d
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 22
---
# CComQIPtr Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Una clase de puntero inteligente para administrar punteros de interfaz COM.  
  
## Sintaxis  
  
```  
  
      template<  
   class T,  
   const IID* piid = &__uuidof(T)  
>  
class CComQIPtr: public CComPtr<T>  
```  
  
#### Parámetros  
 `T`  
 Una interfaz COM que especifica el tipo de puntero que se va a almacenar.  
  
 `piid`  
 Un puntero al identificador IID de `T`.  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComQIPtr::CComQIPtr](../Topic/CComQIPtr::CComQIPtr.md)|Constructor.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComQIPtr::operator \=](../Topic/CComQIPtr::operator%20=.md)|Asigna un puntero al puntero de miembro.|  
  
## Comentarios  
 ATL utiliza `CComQIPtr` y [CComPtr](../../atl/reference/ccomptr-class.md) para administrar los punteros de interfaz COM, que derivan de [CComPtrBase](../../atl/reference/ccomptrbase-class.md).  Ambas clases realizan el recuento de referencias automático con llamadas a `AddRef` y a **Liberar**.  Operaciones sobrecargadas del puntero de identificador de los operadores.  
  
## Jerarquía de herencia  
 [CComPtrBase](../../atl/reference/ccomptrbase-class.md)  
  
 [CComPtr](../../atl/reference/ccomptr-class.md)  
  
 `CComQIPtr`  
  
## Requisitos  
 **encabezado:** atlcomcli.h  
  
## Vea también  
 [CComPtr::CComPtr](../Topic/CComPtr::CComPtr.md)   
 [CComQIPtr::CComQIPtr](../Topic/CComQIPtr::CComQIPtr.md)   
 [CComPtrBase Class](../../atl/reference/ccomptrbase-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [CComQIPtrElementTraits Class](../../atl/reference/ccomqiptrelementtraits-class.md)