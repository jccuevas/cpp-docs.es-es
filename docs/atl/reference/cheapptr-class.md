---
title: "CHeapPtr Class | Microsoft Docs"
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
  - "ATL::CHeapPtr"
  - "CHeapPtr"
  - "ATL.CHeapPtr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHeapPtr class"
ms.assetid: e5c5bfd4-9bf1-4164-8a83-8155fe253454
caps.latest.revision: 20
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CHeapPtr Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Una clase de puntero inteligente para administrar punteros de la pila.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
      template<  
typename T,  
class Allocator= CCRTAllocator  
> class CHeapPtr :  
public CHeapPtrBase< T, Allocator>  
```  
  
#### Parámetros  
 `T`  
 El tipo de objeto que se va a almacenar en la pila.  
  
 `Allocator`  
 La clase de asignación de memoria en uso.  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CHeapPtr::CHeapPtr](../Topic/CHeapPtr::CHeapPtr.md)|el constructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CHeapPtr::Allocate](../Topic/CHeapPtr::Allocate.md)|Llame a este método para asignar memoria en la pila para almacenar objetos.|  
|[CHeapPtr::Reallocate](../Topic/CHeapPtr::Reallocate.md)|Llame a este método para reasignar memoria en la pila.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CHeapPtr::operator \=](../Topic/CHeapPtr::operator%20=.md)|el operador de asignación.|  
  
## Comentarios  
 `CHeapPtr` es derivado de [CHeapPtrBase](../../atl/reference/cheapptrbase-class.md) y de forma predeterminada utiliza las rutinas de CRT \(en [CCRTAllocator](../../atl/reference/ccrtallocator-class.md)\) para asignar y liberar memoria.  La clase [CHeapPtrList](../../atl/reference/cheapptrlist-class.md) se puede utilizar para generar una lista de punteros de la pila.  Vea también [CComHeapPtr](../../atl/reference/ccomheapptr-class.md), que utiliza las rutinas COM de asignación de memoria.  
  
## Jerarquía de herencia  
 [CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)  
  
 `CHeapPtr`  
  
## Requisitos  
 **encabezado:** atlcore.h  
  
## Vea también  
 [CHeapPtrBase Class](../../atl/reference/cheapptrbase-class.md)   
 [CCRTAllocator Class](../../atl/reference/ccrtallocator-class.md)   
 [Class Overview](../../atl/atl-class-overview.md)