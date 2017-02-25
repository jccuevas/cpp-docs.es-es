---
title: "CHeapPtrBase Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "ATL.CHeapPtrBase"
  - "ATL::CHeapPtrBase"
  - "CHeapPtrBase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHeapPtrBase class"
ms.assetid: 501ac1b2-fb34-4c72-b7e6-a4f1fc8fda21
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CHeapPtrBase Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase forma la base para varias clases inteligentes de puntero de la pila.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
      template <  
class T,  
class Allocator= CCRTAllocator   
> class CHeapPtrBase  
```  
  
#### Parámetros  
 `T`  
 El tipo de objeto que se va a almacenar en la pila.  
  
 `Allocator`  
 La clase de asignación de memoria en uso.  De forma predeterminada las rutinas de CRT se utilizan para asignar y liberar memoria.  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CHeapPtrBase::~CHeapPtrBase](../Topic/CHeapPtrBase::~CHeapPtrBase.md)|El destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CHeapPtrBase::AllocateBytes](../Topic/CHeapPtrBase::AllocateBytes.md)|Llame a este método para asignar memoria.|  
|[CHeapPtrBase::Attach](../Topic/CHeapPtrBase::Attach.md)|Llame a este método para realizar la propiedad de un puntero existente.|  
|[CHeapPtrBase::Detach](../Topic/CHeapPtrBase::Detach.md)|Llame a este método para liberar la propiedad de un puntero.|  
|[CHeapPtrBase::Free](../Topic/CHeapPtrBase::Free.md)|Llame a este método para eliminar un objeto señala `CHeapPtrBase`.|  
|[CHeapPtrBase::ReallocateBytes](../Topic/CHeapPtrBase::ReallocateBytes.md)|Llame a este método para reasignar memoria.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CHeapPtrBase::operator T\*](../Topic/CHeapPtrBase::operator%20T*.md)|El operador de conversión.|  
|[CHeapPtrBase::operator &](../Topic/CHeapPtrBase::operator%20&.md)|y operador.|  
|[CHeapPtrBase::operator \-\>](../Topic/CHeapPtrBase::operator%20-%3E.md)|El operador de puntero a miembro.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CHeapPtrBase::m\_pData](../Topic/CHeapPtrBase::m_pData.md)|La variable miembro de datos de puntero.|  
  
## Comentarios  
 Esta clase forma la base para varias clases inteligentes de puntero de la pila.  Las clases derivadas, por ejemplo, [CHeapPtr](../../atl/reference/cheapptr-class.md) y [CComHeapPtr](../../atl/reference/ccomheapptr-class.md), agregue sus propios constructores y operadores.  Vea estas clases para obtener ejemplos de implementación.  
  
## Requisitos  
 **encabezado:** atlcore.h  
  
## Vea también  
 [CHeapPtr Class](../../atl/reference/cheapptr-class.md)   
 [CComHeapPtr Class](../../atl/reference/ccomheapptr-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)