---
title: "CComPtrBase Class | Microsoft Docs"
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
  - "ATL.CComPtrBase"
  - "ATL::CComPtrBase<T>"
  - "ATL.CComPtrBase<T>"
  - "ATL::CComPtrBase"
  - "CComPtrBase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComPtrBase class"
ms.assetid: 6dbe9543-dee8-4a97-b02f-dd3a25f4a1a0
caps.latest.revision: 19
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CComPtrBase Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona una base para las clases inteligentes de puntero usando las rutinas basado en COM de memoria.  
  
## Sintaxis  
  
```  
  
      template <  
   class T   
> class CComPtrBase  
```  
  
#### Parámetros  
 `T`  
 El tipo de objeto que se hará referencia el puntero inteligente.  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComPtrBase::~CComPtrBase](../Topic/CComPtrBase::~CComPtrBase.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComPtrBase::Advise](../Topic/CComPtrBase::Advise.md)|Llame a este método para crear una conexión entre el punto de conexión de los entity\_CComPtrBase y el receptor de un cliente.|  
|[CComPtrBase::Attach](../Topic/CComPtrBase::Attach.md)|Llame a este método para realizar la propiedad de un puntero existente.|  
|[CComPtrBase::CoCreateInstance](../Topic/CComPtrBase::CoCreateInstance.md)|Llame a este método para crear un objeto de clase asociado a un identificador de clase o un identificador especificado de programa|  
|[CComPtrBase::CopyTo](../Topic/CComPtrBase::CopyTo.md)|Llame a este método para copiar el puntero de `CComPtrBase` a otra variable de puntero.|  
|[CComPtrBase::Detach](../Topic/CComPtrBase::Detach.md)|Llame a este método para liberar la propiedad de un puntero.|  
|[CComPtrBase::IsEqualObject](../Topic/CComPtrBase::IsEqualObject.md)|Llame a este método para comprobar si los puntos especificados de **IUnknown** al mismo objeto asociado al objeto de `CComPtrBase` .|  
|[CComPtrBase::QueryInterface](../Topic/CComPtrBase::QueryInterface.md)|Llame a este método para devolver un puntero a una interfaz especificada.|  
|[CComPtrBase::Release](../Topic/CComPtrBase::Release.md)|Llame a este método para liberar la interfaz.|  
|[CComPtrBase::SetSite](../Topic/CComPtrBase::SetSite.md)|Llame a este método para establecer el sitio del objeto de `CComPtrBase` a **IUnknown** del objeto primario.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComPtrBase::operator T\*](../Topic/CComPtrBase::operator%20T*.md)|El operador de conversión.|  
|[CComPtrBase::operator \!](../Topic/CComPtrBase::operator%20!.md)|El operador NOT \(exclusión\).|  
|[CComPtrBase::operator &](../Topic/CComPtrBase::operator%20&.md)|y operador.|  
|[CComPtrBase::operator \*](../Topic/CComPtrBase::operator%20*.md)|El operador \*.|  
|[CComPtrBase::operator \<](../Topic/CComPtrBase::operator%20%3C.md)|Operador menor que.|  
|[CComPtrBase::operator \=\=](../Topic/CComPtrBase::operator%20==.md)|el operador de igualdad.|  
|[CComPtrBase::operator \-\>](../Topic/CComPtrBase::operator%20-%3E.md)|El operador de la misma.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComPtrBase::p](../Topic/CComPtrBase::p.md)|La variable miembro de datos de puntero.|  
  
## Comentarios  
 Esta clase proporciona la base para otros punteros inteligentes que utilizan las rutinas de administración de memoria COM, como [CComQIPtr](../../atl/reference/ccomqiptr-class.md) y [CComPtr](../../atl/reference/ccomptr-class.md).  Las clases derivadas agregan sus propios constructores y operadores, pero se basan en los métodos proporcionados por `CComPtrBase`.  
  
## Requisitos  
 **encabezado:** atlcomcli.h  
  
## Vea también  
 [Class Overview](../../atl/atl-class-overview.md)